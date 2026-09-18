---
tags:
- android
- architecture
- kotlin
- mvvm
- viewmodel
---

## 🧭 Overview
> Comprendre profondément comment le ViewModel organise la logique, gère l'état et simplifie l’UI dans une application Android, en structurant la communication Screen ↔ ViewModel à travers UI State, UI Actions et Events.

---

## ✨ Features
- Séparation totale entre UI et logique métier
- Gestion robuste et prévisible de l’état
- Réduction drastique du code dans les Screens
- Communication standardisée (actions, états, événements)
- Architecture plus testable et maintenable

---

## 🚀 Getting Started

### 🎬 Introduction
La complexité arrive vite dans un écran Android : callbacks, états, affichages conditionnels…  
Le **ViewModel** agit comme un pivot central : il absorbe l’ensemble de la logique et ne laisse à l’UI que l’affichage.  
Ce modèle rend la structure très lisible et limite l'apparition d’un "écran fourre-tout".

---

## 🎛️ 1. Le Rôle Central du ViewModel  
Le ViewModel sépare clairement *présentation* et *logique*. Il prend le contrôle de trois aspects essentiels :

> [!info] Responsabilités du ViewModel
> **1. Gestion de l’état (UI State)**  
> - Représente exactement ce que l’utilisateur voit.  
> - Peut inclure : *isLoading*, messages d’erreur, liste de données, etc.
>
> **2. Gestion de la logique métier**  
> - Appels API  
> - Initialisation (services, données)  
> - Transformation interne
>
> **3. Gestion des actions utilisateurs**  
> - Clics  
> - Saisies  
> - Événements de cycle de vie

> [!tip]  
> Le Screen ne fait *rien d’autre* que lire le State et envoyer des Actions.

---

## 🔗 2. Communication entre Screen et ViewModel

### 📍 2.1 UI State — La Source de Vérité
Le State décrit l’écran à un instant donné.  
Le Screen ne *modifie jamais* le State : il l’observe seulement.

> [!example] Exemple  
> Si `isLoading = true`, le Screen affiche un loader.  
> Aucun calcul dans l’UI, juste une lecture.

---

### 📍 2.2 UI Action — Le Messager
Les actions représentent ce que l’utilisateur fait.

Exemples d’actions :
- `onLoginClicked`
- `onUsernameChanged`
- `onSplashCompleted`

> [!info]  
> Le ViewModel reçoit une UI Action, exécute la logique, puis met à jour le State.

---

### 🧾 Résumé de la communication

| Concept     | Rôle                                   | Direction             | Exemple |
|-------------|-----------------------------------------|------------------------|---------|
| UI State    | Décrit ce qu’il faut afficher           | ViewModel → Screen     | isLoading = true |
| UI Action   | Informe d’une interaction utilisateur   | Screen → ViewModel     | Clic « Connexion » |

---

## 🧪 3. Mise en Pratique : Deux Exemples Concrets

---

### 3.1 Exemple 1 : Splash Screen — Le Pilote Automatique
Le Splash Screen est simple : aucune interaction.

Processus complet :

> [!steps]
> 1. Le Screen s’affiche.  
> 2. Le ViewModel démarre une tâche (ex : timer, fetch, initialisation).  
> 3. Une fois terminé, il met à jour le State (`isLoading = false`).  
> 4. Il déclenche une navigation vers l’écran suivant.

> [!note]  
> Le Screen reste *entièrement passif*. Il *attend* que le ViewModel dicte la suite.

---

### 3.2 Exemple 2 : Login — Interaction + Logique
Cet écran illustre parfaitement la séparation logique/UI.

> [!info] Ce que gère le ViewModel :
> - Validation automatique (ex : bouton actif si texte ≥ 3 caractères)  
> - Gestion du clic “Connexion” via une UI Action  
> - Passage en mode chargement  
> - Appel API  
> - Mise à jour du State (succès ou erreur)  
> - Navigation en cas de succès

Le Screen :
- affiche un loader quand `isLoading = true`
- affiche un message si `errorMessage` existe
- active/désactive le bouton selon l’état
- ne contient aucune logique de validation ou de réseau

---

## 🧩 4. Bonne Pratique : L’Interface Contrat

Le **Contrat** regroupe :
- Le State (tout ce que l’UI doit afficher)
- Les Actions (tout ce que l’utilisateur peut faire)
- Les Events (navigation, feedback unique)

> [!tip]  
> Centraliser un Contrat rend le Screen et le ViewModel cohérents et lisibles.

---

### 📌 Pourquoi Interface vs Data Class ?

| Interface (State éphémère) | Data Class (State persistant) |
|-----------------------------|-------------------------------|
| Durée de vie limitée à l’écran | Peut être réutilisé sur plusieurs écrans |
| Exemple : loader, erreurs temporaires | Exemple : token, identifiants, données globales |

Le choix dépend de la **portée** des données.

---

## 🏁 Conclusion

Adopter le ViewModel permet :

> [!success] Bénéfices Clés  
> - UI claire et minimaliste  
> - Logique bien isolée  
> - Code plus lisible  
> - Tests plus simples  
> - Maintenance beaucoup plus facile

La compréhension devient complète lorsqu’on l’applique.  
N’hésitez pas à structurer vos prochains écrans autour du trio **State + Actions + ViewModel**.

---

## ⚙️ Customization and Configuration
- Définir systématiquement :  
  - une interface de State  
  - une interface d’Actions  
  - un ViewModel qui mappe Action → State  
- Garder les Screens 100 % passifs

---

## 🔗 Related
- MVVM Android
- StateFlow & coroutines
- LiveData (moins moderne mais encore répandu)
- Navigation Component

---

## 🌍 Explore More
- [Documentation Android ViewModel](https://developer.android.com/topic/libraries/architecture/viewmodel)
- [Codelabs Architecture Components](https://developer.android.com/courses/pathways/android-basics-compose-unit-4-pathway-1)
- [Github Template](https://github.com/ClementBobin/KotlinComposeTemplate)