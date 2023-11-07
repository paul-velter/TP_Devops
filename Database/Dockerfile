FROM postgres:14.1-alpine

ENV POSTGRES_DB=db \
   POSTGRES_USER=usr \
   POSTGRES_PASSWORD=pwd

#On déclare les variables d'environnement contenant le nom de la base de donnée, l'nom de son utilisateur et le mot de passe associé

COPY /SQL /docker-entrypoint-initdb.d

#On copie le dossier SQL qui contient les fichiers de création de la base de donnée
#dans le dossier docker-entrypoint-initdb.d. Cela permet d'éxécuter tous les fichier contenu par ce
#dossier lors de la construction d'un conteneur à partir de cette image.

