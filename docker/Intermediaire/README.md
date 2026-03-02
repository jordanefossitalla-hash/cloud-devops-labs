# Niveau Intermédiaire — Optimisation Dockerfile

## Objectif d’apprentissage
Améliorer un premier Dockerfile pour appliquer de meilleures pratiques : moins de couches, installation plus propre des paquets système et image plus maintenable.

## Ce que fait ce niveau
- Démarre depuis `debian:12`
- Exécute les opérations système dans une seule instruction `RUN`
- Utilise `--no-install-recommends` pour limiter les paquets inutiles
- Nettoie le cache APT (`/var/lib/apt/lists/*`) pour alléger l’image
- Copie l’application FastAPI et installe les dépendances Python
- Lance Uvicorn sur `0.0.0.0:8000`

## Différence clé vs niveau basique
Le niveau basique utilise plusieurs instructions `RUN`, alors qu’ici elles sont fusionnées dans un seul bloc. Cela réduit le nombre de couches, améliore la lisibilité et optimise la taille finale de l’image.

## Compétences pratiquées
- Optimisation d’un `Dockerfile`
- Bonnes pratiques APT (`--no-install-recommends`, nettoyage cache)
- Compréhension de l’impact des couches Docker sur la performance
- Comparaison entre version initiale et version améliorée

## Structure du niveau
- `dockerfile` : version optimisée
- `app/main.py` : API FastAPI avec endpoint `GET /health`
- `app/requirements.txt` : dépendances Python

## Commandes de test (depuis la racine du repo)
```bash
docker build -t fastapi-intermediaire -f docker/Intermediaire/dockerfile docker/Intermediaire
docker run --rm -p 8000:8000 fastapi-intermediaire
```

Puis tester :
```bash
curl http://localhost:8000/health
```

Réponse attendue :
```json
{"status":"ok"}
```

## Bonnes pratiques à appliquer ensuite (niveau avancé)
- Utiliser une image Python officielle légère (ex: `python:3.12-slim`)
- Mettre en place un build multi-stage
- Ajouter un utilisateur non privilégié
- Ajouter un `HEALTHCHECK` Docker
- Ajouter `.dockerignore` et versionner les dépendances avec plus de précision

## Ce que j’ai appris
Ce niveau m’a appris à transformer un Dockerfile fonctionnel en Dockerfile plus propre et plus efficace, en me concentrant sur l’optimisation des couches et l’hygiène de build.
