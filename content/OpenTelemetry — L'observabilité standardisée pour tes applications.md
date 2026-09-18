---
tags: [veille, observabilité, monitoring, traces, metrics, logs, devops, opentelemetry]
date: 2025-09-11
source: https://opentelemetry.io
---

# 🔭 OpenTelemetry — L'observabilité standardisée pour tes applications

> [!info] 📌 Veille Technologique — DIIAGE 2028
> Standard open source pour collecter traces, métriques et logs depuis n'importe quelle application, vers n'importe quel backend d'observabilité.

---

## 🧭 Pourquoi c'est pertinent

L'observabilité est souvent négligée dans les projets étudiants — et c'est exactement là que les architectes se distinguent en entreprise. OpenTelemetry (OTel) est **le** standard CNCF pour l'instrumentation : tu instrumentes une fois, tu exportes vers Jaeger, Grafana Tempo, Datadog, ou NewRelic selon le contexte.

Le problème qu'il résout : chaque vendor avait son propre SDK de monitoring. OTel casse ce vendor lock-in avec un protocole unique (**OTLP**).

---

## ⚙️ Instrumentation automatique (Node.js)

```typescript
// otel.ts — à charger AVANT tout le reste
import { NodeSDK } from '@opentelemetry/sdk-node'
import { getNodeAutoInstrumentations } from '@opentelemetry/auto-instrumentations-node'
import { OTLPTraceExporter } from '@opentelemetry/exporter-trace-otlp-http'

const sdk = new NodeSDK({
  traceExporter: new OTLPTraceExporter({
    url: 'http://localhost:4318/v1/traces',
  }),
  instrumentations: [getNodeAutoInstrumentations()], // HTTP, DB, Redis auto-instrumentés
})

sdk.start()
```

```bash
# Lance ton app avec l'instrumentation
node --require ./otel.js server.js
```

Résultat : **chaque requête HTTP, chaque query SQL, chaque appel Redis** génère automatiquement des traces distribuées sans modifier le code métier.

---

## 🧩 Les 3 piliers d'OTel

```
Traces ──────────── Visualise le chemin complet d'une requête (latence par étape)
                    → Jaeger, Grafana Tempo, Zipkin

Metrics ─────────── Compteurs, histogrammes, jauges (requêtes/s, latence P99...)
                    → Prometheus, Grafana

Logs ────────────── Logs structurés corrélés aux traces (même trace_id)
                    → Loki, Elastic, Datadog
```

---

## 💡 Pourquoi c'est utile pour nous

Dans une architecture microservices ou même une API monolithique, OTel permet de répondre à la question : **"pourquoi cette requête a mis 3 secondes ?"** sans déboguer à l'aveugle. C'est un prérequis pour tout projet qui sera mis en production réelle. À connaître pour un rôle d'architecte logiciel.

> OTel est un projet CNCF de niveau "Graduated" — le même niveau que Kubernetes et Prometheus.

---

## 🔗 Ressources

- 🌐 [Site officiel — opentelemetry.io](https://opentelemetry.io)
- 📖 [Getting Started (Node.js)](https://opentelemetry.io/docs/languages/js/getting-started/nodejs/)
- 🐙 [GitHub — open-telemetry](https://github.com/open-telemetry)
- 📝 [OTel vs Prometheus vs Jaeger — comparatif](https://opentelemetry.io/docs/concepts/observability-primer/)
- 🎬 [OpenTelemetry in 5 minutes](https://www.youtube.com/watch?v=dfpGRmF_gno)
