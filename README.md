# Mini Projet Docker – Infrastructure DevOps

## Présentation

Ce projet consiste à déployer une infrastructure conteneurisée complète basée sur Docker et Docker Compose.

Il inclut :
- une API Python
- une application web PHP
- un registry Docker privé avec authentification

Objectif : mettre en pratique les concepts DevOps (conteneurisation, orchestration, gestion d’images et registry privé).

---

## Stack technique

- Docker / Docker Compose
- Python (API REST)
- PHP / Apache (Frontend)
- Docker Registry (privé)
- Linux / Vagrant

---

## Architecture du projet

mini-projet-docker/  
├── simple_api/                  # API Python  
├── website/                     # Application web PHP  
├── docker-compose.yml           # Déploiement API + Web  
├── docker-compose-registry.yml  # Registry Docker privé  
├── .gitignore  

---

## Architecture globale

              Navigateur  
                  |  
        -----------------------  
        |                     |  
   Web (PHP)           API (Python)  
   (port 80)           (port 5000)  
        |                     |  
        -------- Docker Network --------  
                       |  
               Docker Registry  
                  (privé)  
                       |  
                 Registry UI  
                  (port 8080)  

---

## Services

| Service       | Image                    | Port | Description                  |
|--------------|--------------------------|------|------------------------------|
| API          | api:v1.0                 | 5000 | API Python                   |
| Web          | php:apache               | 80   | Application web              |
| Registry     | registry:2               | 5000 | Registry Docker privé        |
| Registry UI  | joxit/docker-registry-ui | 8080 | Interface du registry        |

---

## Lancement du projet

### 1. Lancer les services applicatifs

docker compose up -d

Accès :
- Web : http://localhost
- API : http://localhost:5000

---

### 2. Lancer le registry Docker

docker compose -f docker-compose-registry.yml up -d

Accès :
- Registry : http://localhost:5000
- Interface : http://localhost:8080

---

## Authentification

Le registry est protégé par authentification basique.

| Paramètre | Valeur |
|----------|--------|
| Username | pozos  |
| Password | pozos  |

Connexion :

docker login http://localhost:5000

---

## Gestion des images Docker

### Tag d'une image

docker tag api:v1.0 localhost:5000/api:v1.0

### Push vers le registry

docker push localhost:5000/api:v1.0

---

## Compétences développées

- Déploiement d’applications conteneurisées
- Orchestration avec Docker Compose
- Mise en place d’un registry Docker privé sécurisé
- Gestion des réseaux Docker
- Debugging et résolution de problèmes Docker

---

## Bonnes pratiques

- Séparation des services (API / Web / Registry)
- Utilisation de Docker Compose pour l’orchestration
- Mise en place d’un registry privé avec authentification
- Exclusion des données sensibles via `.gitignore`

---

## Auteur

Evane Lipou
