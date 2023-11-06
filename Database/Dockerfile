FROM postgres:14.1-alpine

ENV POSTGRES_DB=db \
   POSTGRES_USER=usr \
   POSTGRES_PASSWORD=pwd

COPY /SQL /docker-entrypoint-initdb.d

#1-1 Document your database container essentials: commands and Dockerfile.

#On copie le dossier SQL qui contient les fichiers de création de la base de donnée
#dans le dossier docker-entrypoint-initdb.d. Cela permet d'éxécuter tous les fichier contenu par ce
#dossier lors de la construction d'un conteneur à partir de cette image.

#Les commandes
# docker run -d -p 5432:5432 --network app-network --name my-database -v /var/lib/postgresql/data azorus/my-database
#-d éxécuter le conteneur hors du terminal
#-p 5432:5432 attribuer les ports
#après avoir créer un nouveau network, on l'associ au conteneur (pour pouvoir utiliser l'adminer)
#--name on nomme le conteneure
#-v permet de rendre les données persistant dans le conteneur
#On défini ensuite l'image à partir de la quelle on contruit le conteneur
