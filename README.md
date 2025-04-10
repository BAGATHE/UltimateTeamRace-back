# Ultimate Race - Backend Django

Ce projet est une application backend développée avec Django 5.2 et PostgreSQL, conteneurisée avec Docker pour faciliter le développement et le déploiement.

## Description

Ultimate Race est une application de gestion de courses automobiles qui permet de :
- Gérer les pilotes et les équipes
- Suivre les résultats des courses
- Gérer les circuits et les événements
- Analyser les statistiques de course

## Prérequis

- Docker
- Docker Compose
- Git

## Installation

1. **Cloner le dépôt**
   ```bash
   git clone [URL_DU_REPO]
   cd ultimate-race-back
   ```

2. **Configurer l'environnement**
   ```bash
   cp .env.example .env
   ```
   Modifiez le fichier `.env` avec vos configurations :
   - SECRET_KEY : Une clé secrète pour Django
   - Les identifiants de la base de données si nécessaire

3. **Construire et démarrer les conteneurs**
   ```bash
   docker-compose up --build
   ```

4. **Appliquer les migrations**
   Dans un nouveau terminal :
   ```bash
   docker-compose exec web python manage.py migrate
   ```

5. **Créer un superutilisateur**
   ```bash
   docker-compose exec web python manage.py createsuperuser
   ```

## Accès à l'application

- Interface web : http://localhost:8000
- Interface d'administration : http://localhost:8000/admin/
- Base de données PostgreSQL : localhost:5433

## Structure du projet

```
ultimate_race/
├── manage.py
├── ultimate_race/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── venv/
├── .env
├── .env.example
├── docker-compose.yml
├── Dockerfile
└── README.md
```

## Commandes Docker utiles

- **Démarrer les conteneurs** : `docker-compose up`
- **Démarrer en arrière-plan** : `docker-compose up -d`
- **Arrêter les conteneurs** : `docker-compose down`
- **Voir les logs** : `docker-compose logs -f`
- **Exécuter une commande dans le conteneur web** : `docker-compose exec web [commande]`
- **Reconstruire les conteneurs** : `docker-compose up --build`

## Développement

Pour développer sur le projet :

1. Les modifications de code sont reflétées en temps réel grâce au volume monté
2. Les migrations sont appliquées automatiquement au démarrage
3. Les fichiers statiques sont servis par WhiteNoise
4. La base de données est persistante grâce au volume Docker

## Sécurité

- Ne jamais commiter le fichier `.env`
- Changer la clé secrète en production
- Désactiver DEBUG en production
- Utiliser HTTPS en production

## Licence

Ce projet est sous licence MIT.
