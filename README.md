# Favorites App - Docker Setup

Ce projet configure une application de gestion des favoris avec Node.js et MongoDB, en utilisant Docker pour la containerisation.

## Prérequis
- [Docker](https://www.docker.com/get-started) doit être installé sur votre machine.

### Construire l'image Docker pour l'application Node.js
```bash
  docker build -t favorites-node .
```
### Créer un réseau Docker pour permettre la communication entre les conteneurs
```bash
  docker network create favorites-net
```
### Démarrer un conteneur MongoDB sur le réseau Docker :
```bash
  docker run -d --name mongodb --network favorites-net mongo
```
### Démarrer le conteneur de l'application Node.js et l'exposer sur le port 3000 :
```bash
  docker run --name favorites --network favorites-net -d -p 3000:3000 favorites-node
```
### Vérifier les détails du conteneur MongoDB (facultatif) :
```bash
  docker container inspect mongodb
```

