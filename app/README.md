# Laravel Instagram-Inspired Application 📷

## Introduction 🌟
Welcome to our Laravel Instagram-Inspired Application! This project is a modern implementation focused on creating a social media platform similar to Instagram. We're leveraging the principles of Clean Architecture and Domain-Driven Design (DDD), and implementing CQRS patterns for efficient and scalable data handling.

## Features 🚀
- **User Profile Management** 🙍‍♂️🙍‍♀️: Users can create, update, and manage their profiles, along with adjusting privacy settings.
- **Media Publishing** 🖼️🎥: Allows for uploading, editing, and deleting photos, videos, stories, and reels.
- **Social Interactions** 💬❤️: Engage with the community through comments, likes, and viewing stories/reels.
- **Messaging** 📬: A secure, private messaging system to communicate with other users.
- **Notifications and Following** 🔔👥: Manage notifications and follow/unfollow other users.
- **Authentication** 🔒: Secure signup, login, and password management.
- **Profile Customization** 🎨: Personalize user profiles including username, email, password, and profile picture.

## Architecture & Technologies 🏗️
- **Laravel Framework**: Utilized for its robust ecosystem, efficient routing, built-in security, and effective database management.
- **Clean Architecture**: Ensures separation of concerns, making the application more maintainable, scalable, and adaptable to changing business requirements.
- **Domain-Driven Design (DDD)**: Focuses on modeling the domain and defining clear domain logic.
- **Command Query Responsibility Segregation (CQRS)**: Separates read and write operations for improved performance and scalability.

## Getting Started 🚀
1. **Clone the Repository**
   ```
   git clone [repo-link]
   ```
2. **Set Up Environment**
   - Configure your `.env` file with necessary database and application settings.
3. **Install Dependencies**
   ```
   composer install
   ```
4. **Run Migrations**
   ```
   php artisan migrate
   ```
5. **Seed Database (optional)**
   ```
   php artisan db:seed
   ```
6. **Run the Application**
   ```
   php artisan serve
   ```
   The application will be available at `http://localhost:8000`.

## Contributing 🤝
Contributions are welcome! Please feel free to submit pull requests, open issues, or suggest new features.

## License ⚖️
This project is licensed under the MIT License - see the LICENSE file for details.

---

We hope you enjoy exploring and contributing to this Laravel Instagram-Inspired Application! Happy coding! 🎉👩‍💻👨‍💻

---
## Specifications 🌟

| Contextes                     | Core/Supporting/Generic | Agrégats             | Entités                             | Use Cases                                                     |
|-------------------------------|-------------------------|----------------------|-------------------------------------|---------------------------------------------------------------|
| Gestion de Profils            | Core                    | Profil Utilisateur   | Utilisateur, Paramètres de confidentialité | Créer/Modifier un profil, Changer la confidentialité (privé/public) |
| Publications                  | Core                    | Publication          | Photo/Vidéo, Story, Reel, Commentaires, Likes | Publier/Supprimer une photo/vidéo, Publier/Supprimer une story/reel, Liker/Commenter |
| Interactions Sociales         | Core                    | Interaction          | Commentaire, Like, Vue             | Commenter/Liker une publication, Voir une story/reel          |
| Messagerie                    | Core                    | Conversation         | Message, Utilisateur               | Envoyer/Lire un message, Gérer les conversations              |
| Notification et Suivi         | Supporting              | Notification         | Notification, Utilisateur          | Recevoir/Gérer les notifications, Suivre/Désabonner des utilisateurs |
| Authentification              | Core                    | Compte Utilisateur   | Utilisateur, Credentials           | Inscription, Connexion, Réinitialisation du mot de passe      |
| Gestion du Profil             | Core                    | Profil Utilisateur   | Utilisateur, Informations du Profil | Modifier le pseudo, Changer le mot de passe, Mettre à jour l'email, Modifier la photo de profil |

### Explications :

- **Gestion de Profils et Authentification** : Ces deux domaines sont au cœur de l'application, permettant aux utilisateurs de créer et de gérer leurs comptes, ainsi que de contrôler leur confidentialité et leurs informations d'identification.

- **Publications et Interactions Sociales** : Ce sont des domaines essentiels pour une application de type Instagram, permettant aux utilisateurs de partager du contenu et d'interagir avec celui des autres.

- **Messagerie** : Permet une communication directe entre les utilisateurs, élément clé pour l'engagement social.

- **Notification et Suivi** : Supporte l'interaction et l'engagement en permettant aux utilisateurs de suivre les activités et de rester connectés.

Cette structure offre une vue d'ensemble organisée des composants et fonctionnalités clés de votre application, alignée avec les principes de la Clean Architecture et DDD. Si vous avez d'autres questions ou besoin de précisions, n'hésitez pas à demander.
### Use Cases Détaillés pour la Gestion des Profils

#### 1. Créer un Profil
- **User Story :** En tant que nouvel utilisateur, je veux créer un profil pour pouvoir interagir avec l'application.
- **Entités :** Utilisateur (informations de base), Paramètres de confidentialité.
- **Règles Métier :** 
  - Validation des données d'inscription (email, nom d'utilisateur, mot de passe).
  - Choix initial des paramètres de confidentialité.
- **Critères d'Acceptation :** 
  - L'utilisateur peut s'inscrire avec un email et un mot de passe valides.
  - L'utilisateur peut définir un nom d'utilisateur.
  - Les paramètres de confidentialité initiaux sont établis.

#### 2. Modifier un Profil
- **User Story :** En tant qu'utilisateur, je veux modifier mon profil pour mettre à jour mes informations personnelles.
- **Entités :** Utilisateur (informations personnelles).
- **Règles Métier :** 
  - Vérification de l'authenticité de l'utilisateur avant la modification.
  - Validation des nouvelles informations.
- **Critères d'Acceptation :** 
  - L'utilisateur peut changer son nom d'utilisateur, son adresse email, sa photo de profil, et d'autres informations personnelles.
  - Les changements sont effectués et sauvegardés correctement.

#### 3. Changer la Confidentialité (Privé/Public)
- **User Story :** En tant qu'utilisateur, je veux pouvoir changer la confidentialité de mon profil pour contrôler qui peut voir mes publications.
- **Entités :** Paramètres de confidentialité.
- **Règles Métier :** 
  - Choix entre un profil public et privé.
  - Application des paramètres de confidentialité aux informations du profil et aux publications.
- **Critères d'Acceptation :** 
  - L'utilisateur peut basculer entre un profil public et privé.
  - Les modifications de confidentialité affectent la visibilité des informations du profil et des publications.

#### Définition de l'Agrégat "Profil Utilisateur"

- **Agrégat :** Profil Utilisateur
- **Description :** L'agrégat "Profil Utilisateur" englobe toutes les informations et les fonctionnalités liées à la gestion du profil d'un utilisateur. Il inclut les informations de base de l'utilisateur, les paramètres de confidentialité, et les fonctionnalités permettant de modifier ces informations. 
- **Raison d'être :** Cet agrégat est crucial car il représente l'identité de l'utilisateur au sein de l'application et sert de point central pour la gestion de toutes les informations et paramètres personnels.

Mise à jour des Use Cases Détaillés pour les Publications :

### Use Cases Détaillés pour les Publications

#### 1. Publier une Photo/Vidéo
- **User Story :** En tant qu'utilisateur, je veux publier des photos ou des vidéos pour les partager avec ma communauté.
- **Entités :** Photo/Vidéo (fichier, description, tags).
- **Règles Métier :** 
  - Validation du format et de la taille du fichier multimédia.
  - Possibilité d'ajouter une description et des tags.
- **Critères d'Acceptation :** 
  - L'utilisateur peut télécharger et publier une photo ou une vidéo.
  - La publication est visible sur le profil de l'utilisateur et dans le fil d'actualités.

#### 2. Supprimer une Photo/Vidéo
- **User Story :** En tant qu'utilisateur, je veux pouvoir supprimer mes photos ou vidéos publiées.
- **Entités :** Photo/Vidéo.
- **Règles Métier :** 
  - Permettre à l'utilisateur de supprimer ses propres publications.
- **Critères d'Acceptation :** 
  - L'utilisateur peut supprimer une photo ou une vidéo qu'il a publiée.
  - La publication est retirée du profil et du fil d'actualités.

#### 3. Publier une Story/Reel
- **User Story :** En tant qu'utilisateur, je veux publier des stories ou des reels pour partager des moments éphémères ou des clips créatifs.
- **Entités :** Story/Reel (fichier multimédia, durée, effet visuel/audio).
- **Règles Métier :** 
  - Limitation de la durée de la story/reel.
  - Choix des effets visuels ou audio.
- **Critères d'Acceptation :** 
  - L'utilisateur peut créer et partager une story ou un reel.
  - La story/reel est visible temporairement sur le profil et dans le fil d'actualités.

#### 4. Supprimer une Story/Reel
- **User Story :** En tant qu'utilisateur, je veux pouvoir supprimer mes stories ou reels publiés.
- **Entités :** Story/Reel.
- **Règles Métier :** 
  - Permettre la suppression de stories/reels par l'utilisateur.
- **Critères d'Acceptation :** 
  - L'utilisateur peut supprimer une story ou un reel qu'il a publié.
  - La story/reel est retirée du profil et du fil d'actualités.

#### 5. Liker une Publication
- **User Story :** En tant qu'utilisateur, je veux liker les publications des autres pour montrer mon appréciation.
- **Entités :** Like (utilisateur, publication).
- **Règles Métier :** 
  - Enregistrement d'un like sur une publication.
  - Limitation à un like par utilisateur pour chaque publication.
- **Critères d'Acceptation :** 
  - L'utilisateur peut liker une publication.
  - Le like est affiché sur la publication.

#### 6. Commenter une Publication
- **User Story :** En tant qu'utilisateur, je veux commenter les publications pour interagir avec les autres utilisateurs.
- **Entités :** Commentaire (texte, utilisateur, publication).
- **Règles Métier :** 
  - Permettre l'ajout de commentaires sur les publications.
  - Validation de la longueur et du contenu approprié du commentaire.
- **Critères d'Acceptation :** 
  - L'utilisateur peut ajouter un commentaire à une publication.
  - Le commentaire est visible sous la publication.

Cette mise à jour offre une vue détaillée et spécifique des actions et fonctionnalités associées aux publications, essentielles pour l'engagement et l'interaction des utilisateurs au sein de l'application.
#### Définition de l'Agrégat "Publication"

- **Agrégat :** Publication
- **Description :** L'agrégat "Publication" comprend toutes les fonctionnalités et informations liées à la création, la gestion et l'interaction avec les publications sous divers formats (photos, vidéos, stories, reels). Il inclut les fichiers multimédias, les commentaires, et les likes associés à chaque publication.
- **Raison d'être :** Cet agrégat est central pour l'expérience utilisateur de l'application, car il permet aux utilisateurs de partager du contenu et d'interagir avec celui des autres, créant ainsi un réseau social dynamique.
Mise à jour des Use Cases Détaillés pour les Interactions Sociales :

### Use Cases Détaillés pour les Interactions Sociales

#### 1. Commenter une Publication
- **User Story :** En tant qu'utilisateur, je veux commenter les publications pour interagir avec les auteurs et les autres membres de la communauté.
- **Entités :** Commentaire (texte, auteur, publication ciblée).
- **Règles Métier :** 
  - Permettre l'ajout de commentaires sur les publications.
  - Validation de la longueur et du contenu approprié du commentaire.
- **Critères d'Acceptation :** 
  - L'utilisateur peut ajouter un commentaire à une publication.
  - Le commentaire est affiché sous la publication concernée.

#### 2. Liker une Publication
- **User Story :** En tant qu'utilisateur, je veux liker des publications pour exprimer mon appréciation ou mon soutien.
- **Entités :** Like (utilisateur, publication ciblée).
- **Règles Métier :** 
  - Enregistrement d'un like pour une publication spécifique.
  - Limitation à un like par utilisateur pour chaque publication.
- **Critères d'Acceptation :** 
  - L'utilisateur peut liker une publication.
  - Le like est enregistré et visible sur la publication.

#### 3. Voir une Story/Reel
- **User Story :** En tant qu'utilisateur, je veux voir les stories et reels pour rester informé et engagé avec le contenu partagé par les autres.
- **Entités :** Vue (utilisateur, story/reel visionné).
- **Règles Métier :** 
  - Enregistrement des vues sur les stories et reels.
  - Limitation de la durée de visibilité des stories et reels.
- **Critères d'Acceptation :** 
  - L'utilisateur peut visualiser des stories et reels.
  - Les vues sont comptabilisées pour chaque story/reel.

#### Définition de l'Agrégat "Interaction"

- **Agrégat :** Interaction
- **Description :** L'agrégat "Interaction" regroupe toutes les fonctionnalités et informations liées aux interactions sociales sur les publications, telles que les commentaires, les likes, et les vues. Il inclut les données sur les interactions, les participants, et le contenu concerné.
- **Raison d'être :** Cet agrégat est essentiel pour l'expérience sociale de l'application, car il permet aux utilisateurs de s'engager avec le contenu partagé et de tisser des liens avec la communauté.

### Use Cases Détaillés pour la Messagerie

#### 1. Envoyer un Message
- **User Story :** En tant qu'utilisateur, je veux envoyer des messages à d'autres utilisateurs pour communiquer de manière privée.
- **Entités :** Message (texte, auteur, destinataire).
- **Règles Métier :** 
  - Permettre l'envoi de messages entre utilisateurs.
  - Validation du contenu du message.
  - Notification au destinataire de l'arrivée d'un nouveau message.
- **Critères d'Acceptation :** 
  - L'utilisateur peut envoyer un message à un autre utilisateur.
  - Le message est livré au destinataire et une notification est envoyée.

#### 2. Lire un Message
- **User Story :** En tant qu'utilisateur, je veux lire les messages reçus pour rester en contact avec mes amis et ma communauté.
- **Entités :** Message (texte, auteur, destinataire).
- **Règles Métier :** 
  - Accès à la boîte de réception pour lire les messages reçus.
  - Marquage des messages comme lus.
- **Critères d'Acceptation :** 
  - L'utilisateur peut accéder et lire les messages dans sa boîte de réception.
  - Les messages lus sont marqués comme tels.

#### 3. Gérer les Conversations
- **User Story :** En tant qu'utilisateur, je veux gérer mes conversations pour organiser mes échanges et maintenir la clarté de ma messagerie.
- **Entités :** Conversation (ensemble de messages, participants).
- **Règles Métier :** 
  - Permettre la suppression ou l'archivage de conversations.
  - Regroupement des messages par conversation.
  - Recherche et tri des conversations.
- **Critères d'Acceptation :** 
  - L'utilisateur peut supprimer ou archiver des conversations.
  - L'utilisateur peut rechercher et trier ses conversations.

#### Définition de l'Agrégat "Conversation"

- **Agrégat :** Conversation
- **Description :** L'agrégat "Conversation" englobe toutes les fonctionnalités liées à la messagerie, incluant l'envoi et la réception de messages, ainsi que la gestion des conversations entre utilisateurs. Il inclut la structure des conversations, les messages échangés, et les informations sur les participants.
- **Raison d'être :** Cet agrégat est crucial pour le système de messagerie de l'application, facilitant la communication privée entre utilisateurs et jouant un rôle clé dans l'engagement et l'interaction au sein de la communauté.

### Use Cases Détaillés pour Notification et Suivi

#### 1. Recevoir des Notifications
- **User Story :** En tant qu'utilisateur, je veux recevoir des notifications pour être informé des activités liées à mon compte et aux interactions avec d'autres utilisateurs.
- **Entités :** Notification (type, contenu, utilisateur concerné).
- **Règles Métier :** 
  - Génération de notifications pour des événements spécifiques (nouveaux followers, likes, commentaires, messages).
  - Notification en temps réel ou à intervalles réguliers selon les préférences de l'utilisateur.
- **Critères d'Acceptation :** 
  - L'utilisateur reçoit des notifications pertinentes en fonction des activités liées à son compte.
  - Les notifications sont visibles et accessibles depuis l'interface utilisateur.

#### 2. Gérer les Notifications
- **User Story :** En tant qu'utilisateur, je veux gérer mes notifications pour contrôler les alertes que je reçois et maintenir l'ordre dans mon espace de notification.
- **Entités :** Notification.
- **Règles Métier :** 
  - Permettre aux utilisateurs de personnaliser les paramètres de notifications (activation/désactivation de types spécifiques).
  - Marquage des notifications comme lues ou suppression de notifications.
- **Critères d'Acceptation :** 
  - L'utilisateur peut personnaliser les types de notifications reçues.
  - L'utilisateur peut marquer les notifications comme lues ou les supprimer.

#### 3. Suivre/Désabonner des Utilisateurs
- **User Story :** En tant qu'utilisateur, je veux suivre d'autres utilisateurs pour voir leur contenu dans mon fil d'actualités et me désabonner si je ne souhaite plus voir leur contenu.
- **Entités :** Utilisateur (suiveur et suivi).
- **Règles Métier :** 
  - Permettre aux utilisateurs de suivre ou se désabonner d'autres comptes.
  - Mise à jour du fil d'actualités en fonction des abonnements.
- **Critères d'Acceptation :** 
  - L'utilisateur peut suivre d'autres utilisateurs, ce qui ajoute leur contenu à son fil d'actualités.
  - L'utilisateur peut se désabonner, retirant ainsi le contenu de ces utilisateurs de son fil.

#### Définition de l'Agrégat "Notification"

- **Agrégat :** Notification
- **Description :** L'agrégat "Notification" comprend toutes les fonctionnalités liées à la réception et à la gestion des notifications, ainsi qu'aux fonctionnalités de suivi et de désabonnement des utilisateurs. Il inclut la création, la personnalisation et la gestion des notifications, ainsi que la logique de suivi/désabonnement.
- **Raison d'être :** Cet agrégat joue un rôle de soutien essentiel dans l'engagement des utilisateurs en les tenant informés des interactions pertinentes et en leur permettant de gérer leurs réseaux sociaux au sein de l'application.

### Use Cases Détaillés pour l'Authentification

#### 1. Inscription
- **User Story :** En tant que nouvel utilisateur, je veux créer un compte pour accéder aux fonctionnalités de l'application.
- **Entités :** Utilisateur (informations de base), Credentials (email, mot de passe).
- **Règles Métier :** 
  - Validation de l'email et du mot de passe.
  - Vérification de l'unicité de l'email et du nom d'utilisateur.
  - Enregistrement des informations de l'utilisateur dans la base de données.
- **Critères d'Acceptation :** 
  - L'utilisateur peut s'inscrire avec un email et un mot de passe valides.
  - Un email de confirmation est envoyé après l'inscription.

#### 2. Connexion
- **User Story :** En tant qu'utilisateur enregistré, je veux me connecter à mon compte pour accéder à mes informations personnelles et interagir avec l'application.
- **Entités :** Credentials (email, mot de passe).
- **Règles Métier :** 
  - Vérification de l'existence du compte utilisateur.
  - Correspondance entre l'email et le mot de passe fournis et ceux enregistrés.
- **Critères d'Acceptation :** 
  - L'utilisateur peut se connecter avec son email et mot de passe enregistrés.
  - En cas d'erreur, des messages appropriés sont affichés.

#### 3. Réinitialisation du Mot de Passe
- **User Story :** En tant qu'utilisateur, je veux pouvoir réinitialiser mon mot de passe si je l'oublie pour maintenir la sécurité de mon compte.
- **Entités :** Utilisateur (email pour la réinitialisation), Credentials (nouveau mot de passe).
- **Règles Métier :** 
  - Vérification de l'email de l'utilisateur.
  - Envoi d'un lien ou d'un code de réinitialisation à l'email enregistré.
  - Validation et enregistrement du nouveau mot de passe.
- **Critères d'Acceptation :** 
  - L'utilisateur reçoit un lien ou un code pour réinitialiser son mot de passe.
  - Le mot de passe peut être changé via le processus de réinitialisation.

#### Définition de l'Agrégat "Compte Utilisateur"

- **Agrégat :** Compte Utilisateur
- **Description :** L'agrégat "Compte Utilisateur" regroupe toutes les fonctionnalités liées à l'authentification des utilisateurs, y compris l'inscription, la connexion et la réinitialisation des mots de passe. Il comprend les informations d'identification et les mécanismes de validation nécessaires pour assurer la sécurité des comptes utilisateurs.
- **Raison d'être :** Cet agrégat est essentiel pour l'accès sécurisé et la gestion des comptes utilisateurs, constituant un aspect fondamental de l'expérience utilisateur au sein de l'application.

### Use Cases Détaillés pour la Gestion du Profil

#### 1. Modifier le Pseudo
- **User Story :** En tant qu'utilisateur, je veux changer mon pseudo pour refléter ma personnalité ou mon identité actuelle.
- **Entités :** Utilisateur (pseudo actuel, nouveau pseudo).
- **Règles Métier :** 
  - Vérification de l'unicité du nouveau pseudo.
  - Mise à jour du pseudo dans le profil utilisateur.
- **Critères d'Acceptation :** 
  - L'utilisateur peut modifier son pseudo.
  - Le nouveau pseudo est unique et mis à jour dans le profil.

#### 2. Changer le Mot de Passe
- **User Story :** En tant qu'utilisateur, je veux changer mon mot de passe pour améliorer la sécurité de mon compte.
- **Entités :** Utilisateur (ancien mot de passe, nouveau mot de passe).
- **Règles Métier :** 
  - Vérification de l'ancien mot de passe avant la mise à jour.
  - Validation de la force du nouveau mot de passe.
- **Critères d'Acceptation :** 
  - L'utilisateur peut changer son mot de passe après avoir fourni l'ancien.
  - Le nouveau mot de passe est sécurisé et mis à jour.

#### 3. Mettre à Jour l'Email
- **User Story :** En tant qu'utilisateur, je veux mettre à jour mon adresse email pour assurer la continuité de la communication ou refléter un changement d'email.
- **Entités :** Utilisateur (ancien email, nouveau email).
- **Règles Métier :** 
  - Vérification de l'unicité du nouvel email.
  - Confirmation du changement via un email de vérification.
- **Critères d'Acceptation :** 
  - L'utilisateur peut changer son adresse email.
  - Le système valide le nouvel email et le met à jour dans le profil.

#### 4. Modifier la Photo de Profil
- **User Story :** En tant qu'utilisateur, je veux modifier ma photo de profil pour la garder à jour ou changer mon image visible par les autres utilisateurs.
- **Entités :** Utilisateur (photo de profil actuelle, nouvelle photo).
- **Règles Métier :** 
  - Validation du format et de la taille de la nouvelle photo.
  - Mise à jour de la photo de profil dans le compte utilisateur.
- **Critères d'Acceptation :** 
  - L'utilisateur peut télécharger et changer sa photo de profil.
  - La nouvelle photo est affichée correctement sur le profil.

#### Définition de l'Agrégat "Profil Utilisateur"

- **Agrégat :** Profil Utilisateur
- **Description :** L'agrégat "Profil Utilisateur" comprend toutes les fonctionnalités liées à la gestion et à la personnalisation du profil de l'utilisateur. Il englobe les informations de base, les paramètres de confidentialité, et les options de personnalisation telles que le pseudo, l'email, le mot de passe, et la photo de profil.
- **Raison d'être :** Cet agrégat est crucial pour permettre aux utilisateurs de personnaliser leur expérience sur l'application, en offrant un contrôle sur leur identité numérique et la sécurité de leur compte.