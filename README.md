# TP Devops

## Questions TP part 01 - Docker

**1-1 Document your database container essentials: commands and Dockerfile.**

Les commandes principales :

Commande pour construire l'image :
```
docker build -t azorus/my-database .
```
Commande pour exécuter l'imade :
```
docker run -d -p 5432:5432 --network app-network --name my-database -v /var/lib/postgresql/data azorus/my-database
```
-d éxécuter le conteneur hors du terminal

-p 5432:5432 attribuer les ports

après avoir créer un nouveau network, on l'associ au conteneur (pour pouvoir utiliser l'adminer)

--name on nomme le conteneure

-v permet de rendre les données persistant dans le conteneur

On défini ensuite l'image à partir de la quelle on contruit le conteneur

Voir le [Dockerfile](Database%2FDockerfile) commenté du dossier Base de donnée

**1-2 Why do we need a multistage build? And explain each step of this dockerfile.**

Une construction multistage permet de séparer l'environnement de construction de l'environnement d'exécution. Cela permet d'avoir une image finale plus légère en gardant uniquement les dépendances nécessaire à l'exécution et en retirant
toutes celle qui sont nécéssaires à la construction mais inutile à l'exécution.

Voir le [Dockerfile](Backend%2FDockerfile) commenté dans le dossier Backend

**1-3 Document docker-compose most important commands.**

Commande pour démarrer tous les conteneurs spécifiés dans le fichier docker-compose.yml :
```
docker-compose up 
```
Commande pour arrêter et supprime tous les conteneurs, réseaux et volumes créés par docker-compose up :
```
docker-compose down 
```
Commande pour construir ou reconstruit les images des services spécifiés dans le fichier docker-compose.yml :
```
docker-compose build 
```
Commande pour démarrer les conteneurs existants pour les services spécifiés :
```
docker-compose start 
```
Commande pour arrêter les conteneurs en cours d'exécution pour les services spécifiés sans les supprimer :
```
docker-compose stop 
```
Comande pour er les conteneurs arrêtés pour les services spécifiés :
```
docker-compose rm 
```
**1-4 Document your docker-compose file**

Voir le [docker-compose.yml](docker-compose.yml) commenté

**1-5 Document your publication commands and published images in dockerhub.**

Se connecter à Docker Hub
```
docker login
```
Attribuer une étiquette à l'image Docker, avec la version (ici 1.0)
```
docker tag my-httpd azorus/my-httpd:1.0
```
Pousser l'image sur Docker Hub
```
docker push azorus/my-httpd:1.0
```

Cela rend les images public et accéssible par d'autres machines.

## Questions TP part 02 - Guithub Actions

**2-1 What are testcontainers?**


Les tests containers sont utilisés pour gérer et exécuter des tests d'intégration. 
Ils créent des environnements isolés et temporaires pour exécuter les dépendances dans des conteneurs Docker.

**2-2 Document your Github Actions configurations.**

Voir le fichier [main.yml](.github%2Fworkflows%2Fmain.yml) de configuration Github Actions commenté.

**2-3 Document your quality gate configuration.**

Voir les lignes 22-23 du fichier [main.yml](.github%2Fworkflows%2Fmain.yml)

## Questions TP part 03 - Ansible

**3-1 Document your inventory and base commands**

Voir le fichier de configuration [setup.yml](ansible%2Finventories%2Fsetup.yml) de l'inventory commenté

Tester l'inventory :
```
ansible all -i inventories/setup.yml -m ping
```
Exécuter le playbook :
```
ansible-playbook -i inventories/setup.yml playbook.yml
```
**3-2 Document your playbook**

Voir le playbook [playbook.yml](ansible%2Fplaybook.yml) commenté 

**3-3 Document your docker_container tasks configuration.**

Voir les différents [roles](ansible%2Froles)