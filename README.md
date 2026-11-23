# E-stage — Gestion des stages

Application web de gestion des stages destinée aux stagiaires, aux entreprises et aux responsables. E-stage centralise la consultation des offres, le suivi des candidatures et la gestion des documents dans une interface web.

## Fonctionnalités

- Gestion des comptes et connexion selon le profil utilisateur.
- Publication et consultation d'offres de stage.
- Dépôt et suivi des candidatures.
- Gestion des documents liés aux stages.
- Suivi des stagiaires et des candidatures par les responsables.
- Messagerie en temps réel.

## Technologies

| Partie | Technologies |
| --- | --- |
| Frontend | React 18, Vite, Tailwind CSS, Redux |
| Backend | Node.js, Express, Socket.IO |
| Base de données | MongoDB avec Mongoose |

## Prérequis

- Node.js et npm.
- Une instance MongoDB accessible (locale ou hébergée).
- Git.

## Installation

Clonez le dépôt, puis installez les dépendances de chaque partie :

```bash
git clone https://github.com/mehdi0123347/gestion-des-stages-main.git
cd gestion-des-stages-main

cd backend
npm install

cd ../frontend
npm install
```

## Configuration

Créez un fichier `backend/.env` et renseignez les paramètres nécessaires :

```env
MONGO_URL=mongodb://127.0.0.1:27017/gestion-des-stages
JWT_SECRET=remplacer-par-une-cle-secrete-longue-et-aleatoire
PORT_ONE=5000

# Configuration utilisée par l'envoi de courriels
EMAIL_USER=votre-adresse-email
EMAIL_PASS=votre-mot-de-passe-application

# Certaines routes de courriel utilisent ces noms de variables
EMAIL=votre-adresse-email
PASSWORD=votre-mot-de-passe-application
```

Adaptez l'URI MongoDB et les paramètres de courriel à votre environnement. Ne publiez jamais de fichier `.env`, de mot de passe ou de clé privée.

## Démarrage en développement

Lancez le backend et le frontend dans deux terminaux distincts.

Backend :

```bash
cd backend
npm start
```

Frontend :

```bash
cd frontend
npm run dev
```

Par défaut, Vite sert l'interface sur `http://localhost:5173` et l'API Express écoute sur le port `5000` (ou la valeur définie par `PORT_ONE`). MongoDB doit être démarré et accessible avant le lancement du backend.

## Scripts disponibles

Dans `frontend/` :

| Commande | Description |
| --- | --- |
| `npm run dev` | Démarre le serveur de développement Vite. |
| `npm run build` | Génère la version de production dans `dist/`. |
| `npm run preview` | Prévisualise la version compilée. |
| `npm run lint` | Vérifie le code avec ESLint. |

Dans `backend/` :

| Commande | Description |
| --- | --- |
| `npm start` | Démarre le serveur avec Nodemon. |

## Structure du dépôt

```text
.
├── backend/
│   ├── config/          # Configuration de la base de données
│   ├── controllers/     # Logique métier
│   ├── middlewares/    # Middlewares Express
│   ├── models/          # Modèles Mongoose
│   ├── routes/          # Routes de l'API
│   └── server.js        # Point d'entrée du serveur
└── frontend/
    └── src/
        ├── components/  # Composants réutilisables
        ├── layouts/     # Mises en page
        └── pages/       # Pages de l'application
```

## API

Les principales routes sont préfixées par `/api` :

| Préfixe | Domaine |
| --- | --- |
| `/api/auth` | Authentification et comptes |
| `/api/stage` | Offres de stage |
| `/api/candidature` | Candidatures |
| `/api/suivi` | Suivi |
| `/api/responsable` | Responsables |
| `/api/documents` | Documents |
| `/api/mail` | Courriels |

## Sécurité et données

- Les fichiers téléversés contenant des documents personnels ne sont pas inclus dans le dépôt.
- Les fichiers d'environnement et les identifiants doivent rester locaux ou être configurés comme secrets dans l'environnement de déploiement.
- Avant tout déploiement, configurez les origines CORS, les URL de l'interface et de l'API, ainsi que les paramètres de messagerie pour l'environnement cible.

## Contribution

1. Créez une branche dédiée à votre modification.
2. Décrivez clairement les changements dans vos commits.
3. Vérifiez le frontend avec `npm run lint` et `npm run build` depuis `frontend/`.
4. Ouvrez une pull request en résumant les changements et les vérifications effectuées.
