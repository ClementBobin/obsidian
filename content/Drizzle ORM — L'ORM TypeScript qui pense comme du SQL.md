---
tags: [veille, orm, typescript, sql, backend, base-de-données, drizzle]
date: 2025-09-11
source: https://orm.drizzle.team
---

# 🌧️ Drizzle ORM — L'ORM TypeScript qui pense comme du SQL

> [!info] 📌 Veille Technologique — DIIAGE 2028
> ORM TypeScript léger, type-safe, qui génère du SQL prévisible sans magie cachée — compatible edge runtimes.

---

## 🧭 Pourquoi c'est pertinent

Prisma est excellent mais lourd : il nécessite un moteur Rust en binaire, ne tourne pas sur Cloudflare Workers, et génère des requêtes SQL difficiles à déboguer. Drizzle prend le parti inverse : **si tu connais SQL, tu connais Drizzle**. L'API est un mirror de SQL en TypeScript.

Prisma = ORM "magique" qui cache le SQL  
Drizzle = couche TypeScript fine au-dessus du SQL, 100% prévisible

---

## ⚙️ Définition de schéma et requêtes

```typescript
import { pgTable, serial, text, varchar, timestamp } from 'drizzle-orm/pg-core'
import { drizzle } from 'drizzle-orm/node-postgres'
import { eq, like, and } from 'drizzle-orm'

// Schéma = source de vérité pour le type ET la migration
const articles = pgTable('articles', {
  id: serial('id').primaryKey(),
  title: varchar('title', { length: 120 }).notNull(),
  content: text('content'),
  authorId: serial('author_id').references(() => users.id),
  createdAt: timestamp('created_at').defaultNow(),
})

// Requête typée — TypeScript infère le type de retour
const db = drizzle(pool)

const results = await db
  .select({ id: articles.id, title: articles.title })
  .from(articles)
  .where(and(
    like(articles.title, '%Drizzle%'),
    eq(articles.authorId, 42)
  ))
  .limit(10)
// results : { id: number, title: string }[]
```

```bash
# Migrations basées sur le schéma TS
npx drizzle-kit generate
npx drizzle-kit migrate
```

---

## 🧩 Pourquoi Drizzle vs les autres

| Critère | Prisma | Drizzle | TypeORM |
|---|---|---|---|
| Bundle size | ~40 Mo (binaire) | ~350 Ko | ~5 Mo |
| Edge runtimes | ❌ | ✅ | ❌ |
| SQL prévisible | ❓ | ✅ | ❓ |
| TypeScript strict | ✅ | ✅ | Partiel |
| Relations typées | ✅ | ✅ (v2) | Partiel |

---

## 💡 Pourquoi c'est utile pour nous

Pour un backend Hono ou Next.js API Routes déployé sur Cloudflare Workers ou un edge runtime, Drizzle est **la seule option ORM viable**. C'est aussi un bon exercice d'architecture : comprendre ce qu'un ORM fait réellement vs ce qu'il cache, c'est une compétence d'architecte logiciel directement évaluée en MSc.

---

## 🔗 Ressources

- 🌐 [Site officiel — orm.drizzle.team](https://orm.drizzle.team)
- 📖 [Documentation](https://orm.drizzle.team/docs/overview)
- 🐙 [GitHub — drizzle-team/drizzle-orm](https://github.com/drizzle-team/drizzle-orm)
- 📝 [Drizzle vs Prisma — comparaison officielle](https://orm.drizzle.team/docs/prisma)
