## 🖥️ Description de la réalisation

Ce projet a pour objectif de **concevoir une infrastructure centralisée de collecte et de traitement de données IoT** pour la surveillance de ressources industrielles (ex : silos à grains), en lien avec les systèmes **Actemium/Vinci**. Il inclut le développement d’une API backend, une interface de visualisation et une passerelle de communication en temps réel.

## 💻 Environnement technologique

- **Langages** : C#, TypeScript
    
- **Frameworks** :
    
    - .NET (phase initiale)
        
    - Node.js avec Express (post-migration)
        
- **Base de données** : PostgreSQL (via Prisma ORM)
    
- **Validation de schéma** : Zod
    
- **Communication temps réel** : WebSocket
    
- **Visualisation frontend** : Web app (React ou équivalent)
    
- **Autres outils** :
    
    - Logging structuré
        
    - API auto-documentée
        

## ⚙️ Fonctionnalités principales

- 📡 **Collecte des données IoT** via passerelle unique
    
- 🔁 **Migration de l’API** C# vers Node.js pour plus de souplesse
    
- 🧱 **Validation stricte des schémas** d’entrée avec Zod
    
- 🧾 **Documentation dynamique** de l’API (OpenAPI/Swagger-like)
    
- 📊 **Web app de visualisation des capteurs** (données + statuts en temps réel)
    
- 📶 **Communication WebSocket** pour les mises à jour en direct
    
- 🧩 **Système de logs structuré** avec niveau de sévérité, timestamp, module, méthode, etc.
    
- 🗂️ **Fichiers de logs mensuels**
    
- ⚙️ **Configuration des logs** via `app-settings.json`
    
- 🧼 Suppression automatique des logs de plus de 6 mois
    
- ⏱️ **Planification automatique** des vérifications tous les 10 jours
    

## 🧠 Compétences mobilisées

> [!info]+ Développement Backend
> 
> - Création d’API RESTful avec .NET et Express
>     
> - Migration backend C# vers Node.js + TypeScript
>     
> - Structuration de projets Node.js (routes, middlewares, services)
>     

> [!check]+ Validation et Sécurité
> 
> - Utilisation de **Zod** pour la validation des schémas
>     
> - Sécurisation des entrées API
>     

> [!bug]+ Logging structuré
> 
> - Implémentation d’un système de logs conforme à une norme interne :
>     
>     - Date/Heure, timestamp Unix, niveau de log, composant appelant, méthode, message
>         
>     - Configuration via `app-settings.json`
>         

> [!example]+ Communication temps réel
> 
> - Intégration de **WebSocket** pour les mises à jour live depuis les capteurs
>     
> - Gestion d’événements (connect/disconnect/update)
>     

> [!tip]+ Frontend Web
> 
> - Développement d’une interface web de **visualisation des données IoT**
>     
> - Suivi du statut des capteurs et représentation des valeurs collectées
>     

> [!star]+ Architecture & DevOps
> 
> - Étude de solutions de **passerelle unique** IoT
>     
> - Organisation modulaire de l’API pour faciliter les évolutions futures
>     

## 📦 Éléments produits

- 🔧 **[API Backend](https://dev.azure.com/SIO2025ClementBobin/Other/_git/Api%20IOT%20Express)** (v1 en C#, v2 en Node.js avec Express, Prisma, Zod)
    
- 🌐 **[Application web](https://github.com/ClementBobin/iot_vision)** de visualisation des données capteurs
    
- 📃 **Documentation de l’API** générée dynamiquement
    
- 🗂️ **Fichiers de logs** mensuels auto-nettoyés
    
- 📄 **app-settings.json** configurable
    
- 🧪 **Rapports de tests** : couverture API, validation WebSocket
    
- 📸 **Captures d'écran** :
    
    - Interface capteurs en temps réel
        
    - Journalisation des événements
        

## 📈 Bilan de la situation

> [!important]+ Apports pour l’entreprise
> 
> - Intégration transparente avec les systèmes Actemium/Vinci
>     
> - Centralisation et automatisation de la collecte de données
>     
> - Réduction des erreurs humaines et meilleure traçabilité
>     
> - Temps réel pour l’analyse et la réactivité
>     

> [!star]+ Acquis personnels
> 
> - Maîtrise du **passage d’une API .NET vers Node.js/TypeScript**
>     
> - Compétences avancées en **logging structuré et validation de schémas**
>     
> - Expérience concrète en **architecture IoT** et communication WebSocket
>     
> - Mise en œuvre d’une approche **temps réel + visualisation frontend**
>     

![[IoT Test Jest.jpg]]
![[IoT Test Jest 2.jpg]]
![[IoT Node-RED.png]]
![[IoT Error.png]]
![[IoT Graph.png]]
![[IoT Config.png]]
![[IoT Scalar.png]]