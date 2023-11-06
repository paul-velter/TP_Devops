# Build
# Définit une image de base pour la construction de l'application avec Maven et Amazon Corretto JDK 17 en tant qu'environnement de développement
FROM maven:3.8.6-amazoncorretto-17 AS myapp-build
# Définit la variable d'environnement MYAPP_HOME avec le répertoire racine de l'application
ENV MYAPP_HOME /opt/myapp
# Définit le répertoire de travail de l'image comme répertoire racine de l'application
WORKDIR $MYAPP_HOME
# Copie le fichier pom.xml dans le répertoire de travail (le répertoire racine de l'application)
COPY pom.xml .
# Copie le code source dans le répertoire de travail, créant ainsi un répertoire src à l'intérieur du répertoire racine de l'application
COPY src ./src
# Exécute la commande Maven pour empaqueter l'application. L'option -DskipTests indique à Maven de ne pas exécuter les tests pendant le processus de construction.
RUN mvn package -DskipTests

# Run
# Spécifie une nouvelle image de base pour l'exécution de l'application avec Amazon Corretto JDK 17
FROM amazoncorretto:17
# Redéfinit la variable d'environnement MYAPP_HOME avec le répertoire racine de l'application pour la nouvelle image
ENV MYAPP_HOME /opt/myapp
# Définit le répertoire de travail de la nouvelle image comme le répertoire racine de l'application
WORKDIR $MYAPP_HOME
# Copie le fichier JAR compilé à partir de l'étape précédente dans le répertoire racine de l'application pour cette image
COPY --from=myapp-build $MYAPP_HOME/target/*.jar $MYAPP_HOME/myapp.jar

# Définit le point d'entrée de l'application Docker, exécutant le fichier JAR avec la commande java -jar.
ENTRYPOINT java -jar myapp.jar



