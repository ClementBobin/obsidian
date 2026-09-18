---
tags: [veille, backend, kotlin, ktor, api, jetbrains, coroutines]
date: 2025-09-11
source: https://ktor.io
---

# 🔷 Ktor — Framework backend Kotlin asynchrone par JetBrains

> [!info] 📌 Veille Technologique — DIIAGE 2028
> Framework web Kotlin pour construire des serveurs et des clients HTTP asynchrones, coroutine-native.

---

## 🧭 Pourquoi c'est pertinent

Si tu fais du Kotlin Android (Compose), tu connais déjà le langage — autant l'utiliser **aussi en backend**. Ktor, maintenu par JetBrains, est le framework Kotlin de référence pour les APIs légères : pas d'annotation magic, pas de réflexion à runtime, juste des fonctions et des coroutines.

À comparer avec Spring Boot : **Ktor est volontairement minimaliste**. Tu assembles ce dont tu as besoin, pas une usine à gaz. Idéal pour des microservices et des APIs companion d'apps mobiles.

---

## ⚙️ Exemple d'API REST

```kotlin
import io.ktor.server.application.*
import io.ktor.server.engine.*
import io.ktor.server.netty.*
import io.ktor.server.routing.*
import io.ktor.server.response.*
import io.ktor.server.request.*
import io.ktor.http.*

fun main() {
    embeddedServer(Netty, port = 8080) {
        install(ContentNegotiation) { json() }
        install(Authentication) { bearer("auth-bearer") { /* ... */ } }
        
        routing {
            route("/api/articles") {
                get {
                    val articles = articleRepository.findAll()
                    call.respond(articles)
                }
                
                post {
                    val dto = call.receive<CreateArticleDto>()
                    val created = articleRepository.create(dto)
                    call.respond(HttpStatusCode.Created, created)
                }
            }
        }
    }.start(wait = true)
}
```

---

## 🧩 Plugins clés

| Plugin | Rôle |
|---|---|
| `ContentNegotiation` | Sérialisation JSON (kotlinx.serialization ou Gson) |
| `Authentication` | JWT, OAuth2, Basic, Bearer |
| `CORS` | Politique cross-origin configurable |
| `StatusPages` | Gestion centralisée des erreurs |
| `Locations` | Routes typées à la compilation |
| `WebSockets` | Support natif ws:// |
| `Ktor Client` | Client HTTP asynchrone côté mobile ou serveur |

---

## 💡 Pourquoi c'est utile pour nous

Pour un projet comme CYNA où l'on a déjà un front Kotlin/Compose Android, **partager des modèles de données** entre le client et un backend Ktor via Kotlin Multiplatform devient possible. C'est aussi une excellente illustration du modèle **asynchrone non-bloquant** avec les coroutines — un pattern d'architecture à maîtriser pour le MSc.

> Ktor est disponible en multiplateforme (JVM, Native) et intègre le plugin Kotlin Multiplatform pour du code client/serveur partagé.

---

## 🔗 Ressources

- 🌐 [Site officiel — ktor.io](https://ktor.io)
- 📖 [Documentation](https://ktor.io/docs/)
- 🎮 [Playground interactif](https://start.ktor.io)
- 🐙 [GitHub — ktorio/ktor](https://github.com/ktorio/ktor)
- 📺 [KotlinConf — Ktor 3.0 (JetBrains)](https://www.youtube.com/watch?v=IOMqI8FEXQg)
