---
tags:
- bash
- ci-cd
- scripting
- unix
---

## Dépendances

Le script n'utilise que des **outils Unix standard** — aucune installation requise sur un runner CI Linux/macOS :

| Outil     | Pourquoi                                                                            |
| --------- | ----------------------------------------------------------------------------------- |
| `bash`    | Le shell lui-même (`#!/usr/bin/env bash`)                                           |
| `curl`    | Effectue les requêtes HTTP et récupère le code de réponse + le temps                |
| `awk`     | Convertit les secondes décimales en millisecondes entières (insensible à la locale) |
| `cut`     | Découpe la sortie de curl sur le délimiteur `\|`                                    |
| `grep`    | Filtre le fichier rapport pour trouver les lignes en échec à la fin                 |
| `python3` | Encode les noms de styles en URL (ex: `Hip-Hop` → `Hip-Hop`, `R&B` → `R%26B`)       |
| `date`    | Écrit un horodatage UTC dans l'en-tête du rapport                                   |
| `cat`     | Écrit des blocs heredoc dans le fichier rapport                                     |

---

## Détail ligne par ligne

### Shebang & configuration initiale

```bash
#!/usr/bin/env bash
```

Trouve `bash` via le `PATH` plutôt que de coder `/bin/bash` en dur — plus portable sur NixOS, macOS, etc.

```bash
set -euo pipefail
```

- `-e` — quitte immédiatement si une commande échoue
- `-u` — traite les variables non définies comme des erreurs
- `-o pipefail` — si une commande dans un pipe échoue, tout le pipe échoue (pas seulement la dernière commande)

```bash
BASE_URL="${1:-http://localhost:5038}"
MAX_MS="${2:-1000}"
RAPPORT_FICHIER="/tmp/webzine_rapport_endpoints.txt"
ECHECS=0
TOTAL=0
```

- `${1:-...}` — utilise le premier argument, ou la valeur par défaut si absent
- `ECHECS` et `TOTAL` sont des compteurs incrémentés tout au long du script
- Le rapport va dans `/tmp` pour ne pas avoir besoin qu'un dossier existe au préalable

---

### Codes couleur

```bash
ROUGE='\033[0;31m'   # Rouge
JAUNE='\033[1;33m'   # Jaune (gras)
VERT='\033[0;32m'    # Vert
CYAN='\033[0;36m'    # Cyan
GRAS='\033[1m'       # Gras uniquement
RESET='\033[0m'      # Réinitialise tout le formatage
```

Ce sont des séquences d'échappement ANSI. `\033[` démarre l'échappement, le nombre sélectionne le style, et `m` le termine. `RESET` est indispensable — sans lui, la couleur déborde sur la suite de l'affichage.

---

### Fonctions utilitaires

```bash
log()     { echo -e "$*"; }
```

`echo -e` interprète les séquences d'échappement comme `\033[...]`. `$*` joint tous les arguments en une seule chaîne.

```bash
succes()  { log "${VERT}[OK]${RESET} $*"; }
echec()   { log "${ROUGE}[ÉCHEC]${RESET} $*"; ECHECS=$((ECHECS + 1)); }
lent()    { log "${JAUNE}[LENT]${RESET} $*"; ECHECS=$((ECHECS + 1)); }
info()    { log "${CYAN}$*${RESET}"; }
```

À noter : `echec` **et** `lent` incrémentent tous les deux `ECHECS` — un endpoint trop lent est traité comme un échec pour la CI, au même titre qu'une erreur 5xx.

---

### `verifier_endpoint` — la fonction principale

```bash
verifier_endpoint() {
  local METHODE="${1:-GET}"
  local URL="$2"
  local LIBELLE="$3"
  local CORPS="${4:-}"
  local TYPE_CONTENU="${5:-application/x-www-form-urlencoded}"
```

`local` limite la portée des variables à la fonction — elles ne polluent pas l'espace global. Les valeurs par défaut utilisent à nouveau `:-`.

```bash
  TOTAL=$((TOTAL + 1))
```

Expansion arithmétique — incrémente le compteur global à chaque test.

#### L'appel curl (chemin GET)

```bash
    REPONSE=$(curl -s -o /dev/null \
      -w "%{http_code}|%{time_total}" \
      -X GET \
      --max-time 10 \
      --location \
      "$URL" 2>&1) || REPONSE="000|9.999"
```

|Option|Signification|
|---|---|
|`-s`|Silencieux — supprime la barre de progression|
|`-o /dev/null`|Jette le corps de la réponse (inutile ici)|
|`-w "%{http_code}\|%{time_total}"`|Produit `200\|0.043` — la seule chose qui nous intéresse|
|`-X GET`|Méthode explicite (redondant pour GET, mais auto-documenté)|
|`--max-time 10`|Timeout dur de 10 secondes pour éviter que le script se bloque|
|`--location`|Suit les redirections HTTP (301, 302…)|
|`2>&1`|Redirige stderr dans stdout pour capturer les erreurs curl|
|`\| REPONSE="000\|9.999"`|Si curl échoue complètement (connexion refusée, DNS…), repli sur un code `000` fictif et 9,9s|

Le chemin POST est identique mais ajoute :

```bash
      -H "Content-Type: $TYPE_CONTENU" \
      -d "$CORPS" \
```

`-d` envoie le corps de la requête ; `-H` définit l'en-tête pour que le serveur sache comment le parser.

#### Découpage de la réponse

```bash
  CODE_HTTP=$(echo "$REPONSE" | cut -d'|' -f1)
  TEMPS_TOTAL=$(echo "$REPONSE" | cut -d'|' -f2)
```

`cut -d'|' -f1` découpe sur `|` et prend le champ 1 (le code HTTP). Le champ 2 est le temps décimal en secondes, par exemple `0.127`.

```bash
  TEMPS_MS=$(awk "BEGIN {printf \"%.0f\", $TEMPS_TOTAL * 1000}")
```

C'est ici qu'**awk** justifie sa présence. Le problème avec `bc` ou l'arithmétique bash : la **locale**. Sur un système français, le séparateur décimal est `,` et non `.`, donc `0.127` serait mal interprété. `awk` utilise toujours `.` en interne quelle que soit la locale — donc `0.127 * 1000 = 127` fonctionne partout. `%.0f` arrondit à l'entier le plus proche.

#### Logique d'évaluation

```bash
  if [ "${CODE_HTTP:-0}" -ge 500 ] 2>/dev/null; then
    echec "..."
  elif [ "${TEMPS_MS:-99999}" -gt "$MAX_MS" ] 2>/dev/null; then
    lent "..."
  else
    succes "..."
  fi
```

- `${CODE_HTTP:-0}` — si CODE_HTTP est vide, on replie sur `0` pour éviter une erreur de comparaison
- `2>/dev/null` — supprime l'erreur si la valeur n'est pas numérique (ex: le repli `000`)
- L'ordre est important : un 500 qui est aussi lent est signalé comme `[ÉCHEC]`, pas `[LENT]`
- `TEMPS_MS:-99999` — si le parsing a échoué et la variable est vide, on replie sur une valeur très haute qui déclenchera correctement `lent`

---

### Programme principal

```bash
> "$RAPPORT_FICHIER"
```

Tronque (ou crée) le fichier rapport avant d'écrire. Le `>` sans commande à gauche est un raccourci bash équivalent à `true > fichier`.

```bash
cat >> "$RAPPORT_FICHIER" <<EOF
...
EOF
```

Un **heredoc** — tout ce qui se trouve entre `<<EOF` et `EOF` est écrit tel quel dans le fichier. `>>` ajoute à la suite plutôt que d'écraser.

---

### Blocs de tests des endpoints

```bash
for ID in 1 2 3 4 5; do
  verifier_endpoint GET "$BASE_URL/titre/$ID" "GET  /titre/$ID"
done
```

Itère sur une liste statique — teste les 5 premières pages de détail de titre.

```bash
STYLES=("Rock" "Pop" "Rap" ...)
for STYLE in "${STYLES[@]}"; do
  ENCODE=$(python3 -c "import urllib.parse; print(urllib.parse.quote('$STYLE'))" 2>/dev/null || echo "$STYLE")
  verifier_endpoint GET "$BASE_URL/titre/style/$ENCODE" "GET  /titre/style/$STYLE"
done
```

`"${STYLES[@]}"` développe le tableau en toute sécurité (les guillemets préserveraient les espaces dans les noms). **python3** gère l'encodage URL — `Hip-Hop` reste `Hip-Hop` mais `R&B` deviendrait `R%26B`. Le `|| echo "$STYLE"` assure le repli si python3 n'est pas disponible.

---

### Récapitulatif & code de sortie

```bash
REUSSIS=$((TOTAL - ECHECS))
```

Simple arithmétique — pas besoin de compteur séparé pour les succès.

```bash
grep -E "^\[(ÉCHEC|LENT)\]" "$RAPPORT_FICHIER" | while IFS= read -r ligne; do
  log "  ${ROUGE}→${RESET} $ligne"
done
```

`grep -E` utilise les regex étendues. `^\[` ancre au début de ligne suivi d'un `[` littéral. `IFS=` et `-r` dans `read` empêchent la suppression des espaces et l'interprétation des antislashs — important si les lignes contiennent des caractères spéciaux.

```bash
exit "$ECHECS"
```

Le point clé de l'intégration CI. Si `ECHECS=0`, le code de sortie est `0` (succès). Si un endpoint a échoué ou était trop lent, le code de sortie non nul fait échouer le job CI et bloque le merge de la PR.