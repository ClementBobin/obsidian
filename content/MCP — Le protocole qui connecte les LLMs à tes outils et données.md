---
tags: [veille, ia, llm, mcp, anthropic, agent, intégration, protocol]
date: 2025-09-11
source: https://modelcontextprotocol.io
---

# 🔌 MCP — Le protocole qui connecte les LLMs à tes outils et données

> [!info] 📌 Veille Technologique — DIIAGE 2028
> Model Context Protocol (MCP) : standard open source d'Anthropic pour brancher des agents IA sur n'importe quelle source de données ou outil externe.

---

## 🧭 Pourquoi c'est pertinent

Les LLMs comme Claude ou GPT-4 sont puissants mais isolés — ils ne savent rien de ton code, ta base de données, ton Jira ou ton Slack. MCP est le protocole qui change ça : c'est l'**USB-C des agents IA**, un standard unique pour connecter un modèle à n'importe quelle source de contexte ou outil.

Lancé par Anthropic en novembre 2024, il est aujourd'hui supporté par Claude, Cursor, Windsurf, et une communauté de centaines de serveurs open source.

---

## ⚙️ Architecture MCP

```
┌─────────────────────────────────────────────┐
│                  Host (Claude Desktop, Cursor…)         │
│                                             │
│  ┌──────────┐    MCP Protocol    ┌────────────────────┐ │
│  │  LLM     │◄──────────────────►│  MCP Client        │ │
│  │ (Claude) │                    └────────┬───────────┘ │
└─────────────────────────────────────────────┘
                                            │ stdio / HTTP+SSE
                              ┌─────────────▼──────────────┐
                              │       MCP Server           │
                              │  (ton propre serveur ou    │
                              │   GitHub, Postgres, Slack…)│
                              └────────────────────────────┘
```

Un serveur MCP expose 3 types de primitives :
- **Resources** : données accessibles en lecture (fichiers, tables DB, pages…)
- **Tools** : actions que le modèle peut déclencher (créer un ticket, envoyer un mail…)
- **Prompts** : templates de prompts réutilisables

---

## ⚙️ Créer un serveur MCP minimal (TypeScript)

```typescript
import { McpServer } from '@modelcontextprotocol/sdk/server/mcp.js'
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js'
import { z } from 'zod'

const server = new McpServer({ name: 'mon-serveur', version: '1.0.0' })

// Expose un outil que le LLM peut appeler
server.tool(
  'get_article',
  { id: z.number().describe("L'ID de l'article à récupérer") },
  async ({ id }) => {
    const article = await db.articles.findUnique({ where: { id } })
    return { content: [{ type: 'text', text: JSON.stringify(article) }] }
  }
)

await server.connect(new StdioServerTransport())
```

---

## 🧩 Serveurs MCP notables (open source)

| Serveur | Ce qu'il expose |
|---|---|
| `@modelcontextprotocol/server-github` | Repos, PRs, issues, code |
| `@modelcontextprotocol/server-postgres` | Schéma + requêtes SQL |
| `@modelcontextprotocol/server-filesystem` | Lecture/écriture de fichiers |
| `@modelcontextprotocol/server-slack` | Messages, canaux |
| Maestro MCP | Génération + exécution de tests UI |

---

## 💡 Pourquoi c'est utile pour nous

MCP est directement lié à la veille sur Maestro (qui expose un serveur MCP pour les tests). Mais au-delà, c'est un **pattern d'intégration agent-outil** qui va devenir incontournable en architecture logicielle : comment exposer tes services à des agents IA de façon sécurisée, typée et standardisée. C'est exactement le genre de sujet qui fera la différence dans un mémoire de fin d'études MSc.

---

## 🔗 Ressources

- 🌐 [Site officiel — modelcontextprotocol.io](https://modelcontextprotocol.io)
- 📖 [Documentation](https://modelcontextprotocol.io/docs)
- 🐙 [GitHub — modelcontextprotocol](https://github.com/modelcontextprotocol)
- 📝 [Blog Anthropic — Introducing MCP](https://www.anthropic.com/news/model-context-protocol)
- 🗂️ [Registre de serveurs MCP communautaires](https://github.com/modelcontextprotocol/servers)
