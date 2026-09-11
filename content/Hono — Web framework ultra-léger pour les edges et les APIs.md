---
tags: [veille, backend, framework, typescript, edge, api]
date: 2025-09-11
source: https://hono.dev
---

# ⚡ Hono — Web framework ultra-léger pour les edges et les APIs

> [!info] 📌 Veille Technologique — DIIAGE 2028
> Framework web TypeScript minimaliste, pensé pour tourner partout : Cloudflare Workers, Bun, Node.js, Deno, AWS Lambda.

---

## 🧭 Pourquoi c'est pertinent

On a Express.js depuis 2010, Fastify depuis 2016 — mais aucun des deux n'était pensé pour les **runtimes edge** (Cloudflare Workers, Vercel Edge Functions…). Hono comble ce vide avec une API familière mais une architecture résolument moderne.

**Benchmark comparatif (requêtes/sec, runtime Bun) :**

| Framework | Req/sec |
|---|---|
| Hono | ~400 000 |
| Fastify | ~180 000 |
| Express | ~60 000 |

---

## ⚙️ Exemple minimal

```typescript
import { Hono } from 'hono'

const app = new Hono()

app.get('/api/users/:id', async (c) => {
  const id = c.req.param('id')
  return c.json({ id, name: 'Clément' })
})

app.post('/api/articles', async (c) => {
  const body = await c.req.json()
  // validation, persistance...
  return c.json({ created: true }, 201)
})

export default app
```

```bash
# Déploiement sur Cloudflare Workers en une commande
wrangler deploy
```

---

## 🧩 Ce qui se démarque

- **Zéro dépendance** — le bundle fait < 14 Ko
- **Middleware first-class** : auth, CORS, logger, rate-limit, JSX rendering — tout est là
- **RPC client** : génération automatique d'un client TypeScript typé depuis les routes du serveur (comme tRPC mais plus léger)
- **Multi-runtime** : un seul code, deploy sur Node, Bun, Deno, Cloudflare, Lambda

---

## 💡 Pourquoi c'est utile pour nous

Pour des projets DIIAGE avec des contraintes de déploiement variables (VPS, serverless, edge), Hono permet d'**abstraire le runtime** et de livrer une API performante sans sur-ingénierie. Idéal pour prototyper un backend de microservice ou une API companion d'une app mobile Kotlin.

---

## 🔗 Ressources

- 🌐 [Site officiel — hono.dev](https://hono.dev)
- 📖 [Documentation](https://hono.dev/docs)
- 🐙 [GitHub — honojs/hono](https://github.com/honojs/hono)
- 📺 [Fireship — Hono in 100 seconds](https://www.youtube.com/watch?v=acygaIhkM4s)
