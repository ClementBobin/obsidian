---
tags: [veille, devops, self-hosted, déploiement, docker, infra, paas]
date: 2025-09-11
source: https://coolify.io
---

# 🚀 Coolify — Alternative self-hosted à Vercel et Heroku

> [!info] 📌 Veille Technologique — DIIAGE 2028
> Plateforme PaaS open source pour déployer des apps, des bases de données et des services sur ton propre VPS.

---

## 🧭 Pourquoi c'est pertinent

Vercel et Railway sont excellents mais payants au-delà d'un certain seuil. Coolify te donne **exactement la même expérience DX** (push → deploy automatique, HTTPS, variables d'environnement, logs en temps réel) mais sur ton propre serveur, gratuitement.

C'est l'outil idéal pour un dev qui a un VPS sous la main et veut arrêter de payer des plateformes cloud pour des projets perso ou d'apprentissage.

---

## ⚙️ Installation en 5 minutes

```bash
# Sur un VPS Ubuntu/Debian avec Docker installé
curl -fsSL https://cdn.coollabs.io/coolify/install.sh | bash
```

Ensuite : interface web sur `:8000`, connect ton repo GitHub/GitLab, configure ton domaine → c'est déployé.

---

## 🧩 Ce que Coolify gère pour toi

| Fonctionnalité | Détail |
|---|---|
| **Déploiement automatique** | Push sur `main` → rebuild + redeploy via webhook |
| **Bases de données** | PostgreSQL, MySQL, MongoDB, Redis, MariaDB en 1 clic |
| **Services** | Plume, Plausible, Ghost, n8n, Minio, Uptime Kuma… |
| **SSL automatique** | Let's Encrypt via Traefik intégré |
| **Logs & métriques** | Live logs, resource monitoring par conteneur |
| **Preview deployments** | Déploiement d'une branche PR sur un sous-domaine dédié |
| **Buildpacks & Dockerfiles** | Détection auto ou config manuelle |

---

## 💡 Pourquoi c'est utile pour nous

Dans un contexte d'apprentissage, pouvoir **déployer soi-même** ses projets (API, front, base de données) sur un VPS à 5€/mois sans passer par AWS ou Vercel, c'est une compétence architecturale directe. Coolify illustre aussi parfaitement les patterns Docker Compose, reverse proxy (Traefik), et gestion de secrets en production.

> Compatible avec les images Docker, les repos GitHub/GitLab, Nixpacks et Buildpacks.

---

## 🔗 Ressources

- 🌐 [Site officiel — coolify.io](https://coolify.io)
- 📖 [Documentation](https://coolify.io/docs)
- 🐙 [GitHub — coollabsio/coolify](https://github.com/coollabsio/coolify)
- 🎬 [Vidéo — Self-host Everything with Coolify (Fireship)](https://www.youtube.com/watch?v=taJlPG82Ucw)
