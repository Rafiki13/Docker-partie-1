# But de ce répertoire
Dans ce répertoire, vous retrouverez les fichiers 
nécessaires à la création de plusieurs serveurs conteneurisés 
et prêts à l'usage.

Voici la liste des serveurs :
- Site internet (port 8080)
- Postgres (port 8081)
- PgAdmin (port 8082)
- Minetest (port 25565)

# Prérequis
Avant de pouvoir lancer le conteneur, vous devez installer Docker ainsi que 
[Docker Desktop](https://www.docker.com/products/docker-desktop/).

# Configuration
Vous retrouverez un fichier d'environnement `.env` à la racine du dépôt.<br/>
Vous pourrez ainsi personnaliser les éléments suivants :

| Nom variables | Description                                                       |
|---------------|-------------------------------------------------------------------|
| NOM_PROJET    | Correspond au nom qui sera intégré au nom des conteneurs          |
| DB_NAME       | Nom de la base de données Postgresql                              |
| USER_POSTGRES | Nom de l'utilisateur par défaut dans Postgresql                   |
| MDP_POSTGRES  | Mot de passe utilisé par l'utilisateur par défaut dans Postgresql |
| EMAIL_PGADMIN | Email du compte PgAdmin                                           |
| MDP_PGADMIN   | Mot de passe du compte PgAdmin                                    |

# Mise en place et lancement du projet
Lors de la première exécution, créez les images de nos conteneurs :
```shell
docker compose build
```
Puis, il ne reste plus qu'à démarrer les conteneurs :
```shell
docker compose up -d
```
# Détails du docker
## Volumes
Un premier volume a été créé afin de garder les données de la base de données
persistentes.
Un second volume s'occupe de rendre accessible les fichiers du site au serveur
web. Ainsi, toute modification dans le dossier `web/html` se répercutent directement
sur le serveur web.
## Networks
Un réseau propre au projet a été créé avec pour driver bridge. Celui-ci fait le
lien entre les différents conteneurs afin qu'ils puissent communiquer.