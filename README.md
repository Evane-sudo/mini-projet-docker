
---

```markdown
# Mini Projet Docker - Infrastructure DevOps

## Description

Ce projet a pour objectif de mettre en place une infrastructure conteneurisée simple basée sur Docker et Docker Compose.  
Il inclut une API Python, une application web en PHP ainsi qu’un registry Docker privé avec authentification.

L’ensemble permet de comprendre les bases du déploiement d’applications conteneurisées et de la gestion d’images Docker.

---

## Architecture du projet

```

mini-projet-docker/
├── simple_api/                  # API Python
├── website/                     # Application web PHP
├── docker-compose.yml           # Déploiement API + Web
├── docker-compose-registry.yml  # Registry Docker privé
├── .gitignore

```

```markdown

## Architecture globale (schéma)


          Navigateur
              |
    -----------------------
    |                     |
```

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

````

---

## Services

| Service       | Image                      | Port hôte | Description                   |
|--------------|---------------------------|----------|-------------------------------|
| API          | api:v1.0                  | 5000     | API Python                    |
| Web          | php:apache                | 80       | Application web               |
| Registry     | registry:2                | 5000     | Registry Docker privé         |
| Registry UI  | joxit/docker-registry-ui  | 8080     | Interface du registry         |

---

## Lancement du projet

### 1. Lancer les services applicatifs

```bash
docker compose up -d
````

Accès :

* Web : [http://localhost:80](http://localhost:80)
* API : [http://localhost:5000](http://localhost:5000)

---

### 2. Lancer le registry Docker

```bash
docker compose -f docker-compose-registry.yml up -d
```

Accès :

* Registry : [http://localhost:5000](http://localhost:5000)
* Interface : [http://localhost:8080](http://localhost:8080)

---

## Authentification

Le registry est protégé par authentification basique.

| Paramètre | Valeur |
| --------- | ------ |
| Username  | pozos  |
| Password  | pozos  |

Connexion :

```bash
docker login http://localhost:5000
```

---

## Gestion des images Docker

### Tag d'une image

```bash
docker tag api:v1.0 localhost:5000/api:v1.0
```

### Push vers le registry

```bash
docker push localhost:5000/api:v1.0
```

---

## Bonnes pratiques appliquées

* Utilisation de Docker Compose pour orchestrer plusieurs services
* Séparation des environnements (application / registry)
* Mise en place d’un registry privé sécurisé
* Utilisation d’un fichier `.gitignore` pour exclure :

  * les données du registry (`registry-data/`)
  * les fichiers sensibles (`auth/htpasswd`)

---

## Technologies utilisées

| Domaine          | Technologies    |
| ---------------- | --------------- |
| Conteneurisation | Docker          |
| Orchestration    | Docker Compose  |
| Backend          | Python          |
| Frontend         | PHP (Apache)    |
| Registry         | Docker Registry |
| Environnement    | Linux / Vagrant |

---

## Objectifs pédagogiques

Ce projet permet de comprendre :

* Le fonctionnement de Docker
* La création et l’utilisation d’images
* L’orchestration avec Docker Compose
* Le fonctionnement d’un registry Docker privé
* Les bonnes pratiques DevOps

---

## Auteur

Evane Lipou

```

---

