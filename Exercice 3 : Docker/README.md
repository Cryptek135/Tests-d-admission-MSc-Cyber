# Exercice 03 : Déploiement WordPress avec Docker Compose

Mettre en place un site WordPress en utilisant une architecture micro-services avec **Docker**.

## 🚀 Structure de l'Architecture
Pour ce qui est de l'environnement, on a :
1. **Nginx (Serveur Web)** : Il gère les requêtes HTTP et redirige le PHP vers le conteneur dédié.
2. **WordPress** : Le moteur PHP qui exécute le code WordPress.
3. **MariaDB (Base de données)** : Stocke tout le contenu du site.

## 📂 Contenu du dépôt
* `docker-compose.yaml` : Fichier d'orchestration des services.
* `nginx.conf` : Configuration spécifique pour permettre à Nginx de communiquer avec PHP-FPM.
* `README.md` : Explication du processus.

## 🛠️ Processus d'installation

1. **Préparation des volumes** :
   J'ai créé deux dossiers (`wordpress/` et `db_data/`). Le dossier `wordpress/` est le **volume commun** partagé entre les conteneurs Nginx et PHP
   pour que les deux puissent accéder aux fichiers du site.

3. **Configuration réseau** :
   Dans le `docker-compose.yaml`, j'ai lié les services pour que WordPress puisse trouver la base de données via le nom d'hôte `mariadb`.

4. **Lancement des services** :
   Le démarrage se fait avec la commande suivante :
   ```bash
   docker-compose up -d
