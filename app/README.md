# Laravel Instagram-Inspired Application 📷

## Introduction 🌟
Welcome to our Laravel Instagram-Inspired Application! We aim to recreate the essence of Instagram with a focus on user engagement and media sharing. Our approach is grounded in Clean Architecture and Domain-Driven Design (DDD), with an emphasis on efficient data handling through CQRS patterns.

## Features 🚀
- **User Profile Management**: Essential for user interaction, offering features like account creation, login, profile editing, and privacy settings.
- **Media Publishing**: The heart of the app, enabling users to upload, view, and manage photos, videos, and stories.
- **Social Interactions**: Facilitates community engagement through following, liking, commenting, and receiving notifications.
- **Content Management**: A generic but vital feature for tagging posts, categorizing content, and filtering media.
- **Analytics**: Supports business and user engagement insights, tracking statistics and user activity.

## Architecture & Technologies 🏗️
- **Laravel Framework**: Chosen for its comprehensive features and robustness.
- **Clean Architecture & DDD**: Ensures maintainable, scalable, and adaptable solutions.
- **CQRS**: Enhances performance by segregating read and write operations.

## Getting Started 🚀
Guidelines for initial setup, installation, and application launch.

## Contributing 🤝
Inviting contributions to the project.

## License ⚖️
Information about the project's MIT License.

We hope this Laravel Instagram-Inspired Application brings an exciting coding journey! 🎉👩‍💻👨‍💻

---

## Specifications 🌟

| Contextes                           | Core/Supporting/Generic | Agrégats              | Entités                                           | Use Cases                                                                          |
|-------------------------------------|-------------------------|-----------------------|---------------------------------------------------|------------------------------------------------------------------------------------|
| **Contexte Utilisateur**            | Core                    | Compte Utilisateur    | Utilisateur, UserProfile, UserSettings            | Inscription, Connexion, Modification du Profil, Réinitialisation du Mot de Passe, Paramètres de Confidentialité |
| **Contexte Média**                  | Core                    | Média                 | Post, MediaItem, Story                            | Téléchargement de Post, Visualisation de Post, Modification de Post, Création de Story, Visualisation de Story, Expiration de Story |
| **Contexte Interaction Sociale**    | Core                    | Interaction Sociale   | Follow, Like, Comment, Notification               | Follow/Unfollow, Liker un Post, Commenter un Post, Notification d'Interaction      |
| **Contexte Gestion de Contenu**     | Generic                 | Contenu               | Tags, Catégories, Filtrage de Contenu             | Taguer des Posts, Organiser par Catégories, Filtrer le Contenu                      |
| **Contexte Analytique**             | Supporting              | Analyse des Données   | Statistiques Utilisateur, Engagement             | Suivre l'Engagement et les Statistiques des Utilisateurs                            |

---

### Use Cases Détaillés pour la Gestion des Profils (Contexte Utilisateur)

#### 1. Inscription
- **User Story :** En tant que nouvel utilisateur, je veux m'inscrire pour accéder à l'application.
- **Entités :** Utilisateur (informations de base), UserSettings.
- **Règles Métier :** 
  - Validation de l'email et du mot de passe.
  - Confirmation d'email nécessaire pour finaliser l'inscription.
- **Critères d'Acceptation :** 
  1. L'utilisateur fournit un email et un mot de passe valides.
  2. Le système envoie un email de confirmation.
  3. L'utilisateur confirme son inscription via l'email.
  4. Le compte utilisateur est créé avec succès.
  5. L'utilisateur peut se connecter avec ses nouvelles informations d'identification.

#### 2. Connexion
- **User Story :** En tant qu'utilisateur, je veux me connecter pour accéder à mon compte.
- **Entités :** Utilisateur, UserSettings.
- **Règles Métier :** 
  - Correspondance entre l'email/mot de passe et la base de données.
  - Gestion des tentatives de connexion infructueuses.
- **Critères d'Acceptation :** 
  1. L'utilisateur saisit son email et son mot de passe.
  2. Le système vérifie les informations.
  3. L'utilisateur est connecté en cas de succès.
  4. Un message d'erreur est affiché en cas de données incorrectes.
  5. Après plusieurs tentatives échouées, l'accès peut être temporairement bloqué.

### Use Cases Détaillés pour le

 Contexte Média

#### 1. Téléchargement de Post
- **User Story :** En tant qu'utilisateur, je veux télécharger un post pour partager des médias.
- **Entités :** Post, MediaItem.
- **Règles Métier :** 
  - Vérification du format et de la taille du fichier média.
  - Possibilité d'ajouter des légendes et des tags.
- **Critères d'Acceptation :** 
  1. L'utilisateur sélectionne une photo/vidéo à télécharger.
  2. Le fichier est validé par le système (format, taille).
  3. L'utilisateur ajoute une légende et des tags (optionnel).
  4. Le post est publié sur le profil de l'utilisateur.
  5. Le post apparaît dans le fil d'actualités des abonnés.

### Use Cases Détaillés pour le Contexte Interaction Sociale

#### 1. Liker un Post
- **User Story :** En tant qu'utilisateur, je veux liker des posts pour montrer mon appréciation.
- **Entités :** Like, Post.
- **Règles Métier :** 
  - Un utilisateur ne peut liker un post qu'une seule fois.
  - Mise à jour du nombre total de likes sur le post.
- **Critères d'Acceptation :** 
  1. L'utilisateur clique sur le bouton "like" d'un post.
  2. Le like est enregistré et associé au post et à l'utilisateur.
  3. Le compteur de likes du post est mis à jour.
  4. Le post liké apparaît dans la section des favoris de l'utilisateur.
  5. L'auteur du post reçoit une notification du like.
