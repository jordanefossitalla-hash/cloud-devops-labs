# Niveau 02Plus — Docker sur Alpine + FastAPI

## Objectif d’apprentissage
Passer à une image plus légère (`alpine`) pour comprendre l’impact du choix d’image de base sur la taille, la rapidité de build et la maintenance d’un conteneur applicatif.

## Ce que fait ce niveau
- Utilise `alpine:3.18` comme image de base
- Définit le dossier de travail avec `WORKDIR /app`
- Copie le code applicatif dans le conteneur
- Installe Python 3 et pip via `apk`
- Installe les dépendances Python depuis `requirements.txt`
- Expose le port `8000`
- Démarre l’API FastAPI avec Uvicorn

## Compétences pratiquées
- Utilisation d’une image Linux minimale (Alpine)
- Gestion des paquets système avec `apk`
- Construction d’une API FastAPI conteneurisée
- Exposition de port avec `EXPOSE`
- Validation d’un endpoint de santé (`/health`)

## Structure du niveau
- `dockerfile` : image Alpine + installation Python + lancement Uvicorn
- `app/main.py` : API FastAPI minimale
- `app/requirements.txt` : dépendances Python

## Commandes de test (depuis la racine du repo)
```bash
docker build -t fastapi-02plus -f docker/02Plus/dockerfile docker/02Plus
docker run --rm -p 8000:8000 fastapi-02plus
```

Puis tester :
```bash
curl http://localhost:8000/health
```

Réponse attendue :
```json
{"status":"ok"}
```

## Ce que j’ai appris
Ce niveau m’a appris à utiliser une image plus compacte et à adapter l’installation système à Alpine (`apk`), tout en gardant le même comportement applicatif côté API.


