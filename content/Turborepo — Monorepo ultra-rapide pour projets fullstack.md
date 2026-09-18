---
tags: [veille, tooling, monorepo, build, frontend, backend]
date: 2025-09-11
source: https://turbo.build/repo
---

# 🏎️ Turborepo — Monorepo ultra-rapide pour projets fullstack

> [!info] 📌 Veille Technologique — DIIAGE 2028
> Outil de build et d'orchestration de tâches pour monorepos JavaScript/TypeScript.

---

## 🧭 Pourquoi c'est pertinent

Quand on jongle entre une app React, une API Node, un SDK partagé et des scripts CI, le monorepo devient vite le chaos. Turborepo résout ça avec du **cache intelligent et de l'exécution parallèle** — sans changer ton stack.

Ce qui le différencie concrètement :

- **Cache local et distant** : une tâche déjà exécutée sur la même entrée n'est jamais relancée. Build en 30s la 1ère fois → 0.3s les suivantes.
- **Graphe de dépendances automatique** : Turbo analyse ton `package.json` pour savoir dans quel ordre lancer `build`, `test`, `lint`.
- **Remote caching** (Vercel ou self-hosted) : le cache est partagé entre les devs et la CI — plus jamais "ça marche sur ma machine".

---

## ⚙️ Configuration minimale

```json
// turbo.json
{
  "$schema": "https://turbo.build/schema.json",
  "pipeline": {
    "build": {
      "dependsOn": ["^build"],
      "outputs": [".next/**", "dist/**"]
    },
    "test": {
      "dependsOn": ["build"],
      "cache": false
    },
    "lint": {}
  }
}
```

```bash
# Lancer build + test en parallèle sur tous les packages
turbo run build test --parallel
```

---

## 🧩 Écosystème

| Outil | Rôle |
|---|---|
| `turbo run` | Orchestration des tâches avec cache |
| `turbo prune` | Génère un sous-ensemble du monorepo pour Docker |
| Vercel Remote Cache | Partage du cache entre CI et local |
| `create-turbo` | Starter kit avec apps Next.js + packages partagés |

---

## 💡 Pourquoi c'est utile pour nous

Dans un contexte MSc Architecture Logicielle, Turborepo illustre parfaitement les **patterns d'architecture modulaire** : séparation claire des packages, contrats d'interface via des libs partagées, pipeline de build reproductible. C'est exactement ce qu'on attend dans un livrable professionnel multi-composants.

> Compatible avec npm, yarn, pnpm. S'intègre nativement avec GitHub Actions, GitLab CI, et Vercel.

---

## 🔗 Ressources

- 🌐 [Site officiel — turbo.build](https://turbo.build/repo)
- 📖 [Documentation complète](https://turbo.build/repo/docs)
- 🎬 [Vidéo d'intro officielle](https://www.youtube.com/watch?v=YX5yoApjI3M)
- 🐙 [GitHub — vercel/turbo](https://github.com/vercel/turbo)
