---
tags: [veille, typescript, validation, schema, backend, frontend]
date: 2025-09-11
source: https://zod.dev
---

# 🛡️ Zod v4 — Validation de schémas TypeScript-first, maintenant 14× plus rapide

> [!info] 📌 Veille Technologique — DIIAGE 2028
> Librairie de validation et de parsing de données pour TypeScript — côté client, serveur, edge.

---

## 🧭 Pourquoi c'est pertinent

Zod est déjà la librairie de validation TypeScript la plus téléchargée (>10M downloads/semaine). La v4 sort en 2025 avec des breaking changes ciblés et des gains de performance radicaux — le bon moment pour bien comprendre ce qu'elle apporte.

**Performances v4 vs v3 :**

| Opération | v3 | v4 |
|---|---|---|
| Parse string | 1× | **14×** |
| Parse object | 1× | **7×** |
| Bundle size | 57 Ko | **32 Ko** |

---

## ⚙️ Ce que Zod fait concrètement

```typescript
import { z } from 'zod/v4'

// Définition du schéma = source de vérité unique
const ArticleSchema = z.object({
  id: z.uuid(),
  title: z.string().min(3).max(120),
  tags: z.array(z.string()).max(5),
  publishedAt: z.iso.datetime().optional(),
})

// Type TypeScript inféré automatiquement — zéro duplication
type Article = z.infer<typeof ArticleSchema>

// Parse + validation en une ligne, avec message d'erreur structuré
const result = ArticleSchema.safeParse(req.body)
if (!result.success) {
  return res.status(400).json(result.error.flatten())
}
```

---

## 🧩 Nouveautés v4

- **`z.iso.*`** : utilitaires dédiés pour les dates ISO 8601, semaines, durées
- **`z.file()`** : validation native de `File` / `Blob` — utile pour les uploads
- **Métadonnées sur les champs** : `.meta({ description: "..." })` pour générer de la doc OpenAPI
- **`ZodMinimals`** : version allégée sans les méthodes chaînables pour les edge runtimes
- **Meilleure gestion des erreurs** : `z.prettifyError()` pour des messages lisibles

---

## 💡 Pourquoi c'est utile pour nous

Dans un projet comme CYNA (ASP.NET Core + React), Zod côté front garantit que les données envoyées à l'API sont **valides avant même l'appel réseau**. Combiné avec React Hook Form ou TanStack Form, c'est la combinaison de facto pour des formulaires robustes et typés. En backend Node/Hono, c'est la validation de middleware naturelle.

---

## 🔗 Ressources

- 🌐 [Site officiel — zod.dev](https://zod.dev)
- 📖 [Changelog v4](https://zod.dev/changelog)
- 🐙 [GitHub — colinhacks/zod](https://github.com/colinhacks/zod)
- 📝 [Blog post — Zod 4 Beta (par Colin McDonnell)](https://v4.zod.dev/v4)
