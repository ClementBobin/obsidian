---
tags: [veille, tooling, linter, formatter, typescript, javascript, dx]
date: 2025-09-11
source: https://biomejs.dev
---

# 🦁 Biome — Linter et formatter JS/TS tout-en-un, 10× plus rapide qu'ESLint

> [!info] 📌 Veille Technologique — DIIAGE 2028
> Outil de qualité de code unique pour JavaScript, TypeScript, JSX, JSON — sans dépendances Node lourdement chaînées.

---

## 🧭 Pourquoi c'est pertinent

La toolchain JS classique, c'est : ESLint + Prettier + typescript-eslint + des plugins + une config qui se bat avec elle-même. **Biome remplace tout ça** avec un seul binaire natif écrit en Rust.

Résultat concret sur un projet de ~500 fichiers :

| Outil | Temps de lint + format |
|---|---|
| ESLint + Prettier | ~12s |
| Biome | ~0.3s |

---

## ⚙️ Setup en 2 minutes

```bash
npm install --save-dev --save-exact @biomejs/biome
npx biome init
```

```json
// biome.json — configuration minimale
{
  "$schema": "https://biomejs.dev/schemas/1.9.0/schema.json",
  "organizeImports": { "enabled": true },
  "linter": {
    "enabled": true,
    "rules": { "recommended": true }
  },
  "formatter": {
    "enabled": true,
    "indentStyle": "space",
    "indentWidth": 2
  }
}
```

```bash
# Lint + format en une passe
npx biome check --write ./src
```

---

## 🧩 Ce qui se démarque

- **270+ règles de lint** incluses — couvre le scope d'ESLint + eslint-plugin-react + typescript-eslint
- **Formatter compatible Prettier** à 97% — migration sans douleur
- **Un seul binaire** — pas de Node_modules qui polluent, fonctionne en CI sur des runners légers
- **LSP natif** — intégration VS Code sans config, feedback en temps réel ultra-rapide
- **Safe fixes** : distingue les corrections auto-applicables des modifications qui peuvent changer le comportement

---

## 💡 Pourquoi c'est utile pour nous

Pour des projets React (comme CYNA) avec des équipes en apprentissage, une toolchain unifiée réduit le **setup time** et les conflits de config. Le gain de vitesse en CI est immédiat. À recommander dans tout projet qui veut du **DevEx propre dès le départ**.

> Biome est le successeur spirituel de Rome Tools, racheté et réécrit par la communauté open source.

---

## 🔗 Ressources

- 🌐 [Site officiel — biomejs.dev](https://biomejs.dev)
- 📖 [Docs — Getting Started](https://biomejs.dev/guides/getting-started/)
- 🐙 [GitHub — biomejs/biome](https://github.com/biomejs/biome)
- 🔄 [Guide de migration depuis ESLint + Prettier](https://biomejs.dev/guides/migrate-eslint-prettier/)
