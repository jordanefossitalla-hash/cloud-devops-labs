# Niveau Basique — Docker + FastAPI

## Objectif d’apprentissage
Construire et exécuter un premier conteneur Docker pour une API Python (FastAPI), afin de comprendre le cycle complet : image → conteneur → endpoint accessible.

## Ce que fait ce niveau
- Utilise une image de base `debian:12`
- Installe Python et pip dans le conteneur
- Copie l’application FastAPI dans `/app`
- Installe les dépendances depuis `requirements.txt`
- Lance l’API avec Uvicorn sur le port `8000`
- Expose un endpoint de santé : `GET /health`

## Compétences pratiquées
- Lecture et écriture d’un `Dockerfile`
- Compréhension des instructions `FROM`, `RUN`, `WORKDIR`, `COPY`, `CMD`
- Création d’une image Docker
- Lancement d’un conteneur et mapping de port
- Vérification d’un service via endpoint de santé

## Structure du niveau
- `dockerfile` : construction de l’image
- `app/main.py` : API FastAPI minimale
- `app/requirements.txt` : dépendances Python

## Commandes de test (depuis la racine du repo)
```bash
docker build -t fastapi-basique -f docker/basique/dockerfile docker/basique
docker run --rm -p 8000:8000 fastapi-basique
```

Puis tester dans un autre terminal :
```bash
curl http://localhost:8000/health
```

Réponse attendue :
```json
{"status":"ok"}
```

## Points d’amélioration (prochaine étape)
- Réduire le nombre de couches Docker en chaînant les commandes `RUN`
- Ajouter un `.dockerignore`


## Ce que j’ai appris
Ce niveau m’a permis de maîtriser les bases du packaging d’une API Python dans Docker et de valider qu’un service conteneurisé répond correctement via un endpoint de santé.
