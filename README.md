# Mon Projet de Microservices

Ce projet contient une architecture de microservices avec PostgreSQL, MongoDB, et d'autres services.

## Services inclus

- PostgreSQL avec pgAdmin pour la gestion
- MongoDB avec mongo-express pour l'interface web
- MailDev pour le développement d'emails

## Comment démarrer le projet

1. Assurez-vous d'avoir Docker et Docker Compose installés
2. Clonez ce dépôt
3. Lancez `docker-compose up -d`
4. Accédez aux différentes interfaces :
    - pgAdmin : http://localhost:5050
    - mongo-express : http://localhost:8081
    - MailDev : http://localhost:1080

## Configuration

Les identifiants par défaut sont définis dans le fichier docker-compose.yml.
Pour la production, pensez à les changer et à utiliser des variables d'environnement.