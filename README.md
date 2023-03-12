# webapp

Ce fichier Dockerfile contient des instructions pour la création d'une image Docker. Voici une explication de chaque ligne:

1.  **`FROM ubuntu:18.04`** Cette ligne indique que l'image de base de cette image est Ubuntu version 18.04.
    
2.  **`MAINTAINER afa (afa@gmail.com)`** Cette ligne spécifie le nom et l'adresse e-mail de la personne ou de l'équipe responsable de la maintenance de cette image. Notez que l'instruction `MAINTAINER` est désormais considérée comme obsolète et est remplacée par `LABEL`.
    
3.  **`RUN apt-get update`** Cette ligne exécute la commande `apt-get update` pour mettre à jour les référentiels de packages.
    
4.  **`RUN DEBIAN_FRONTED=noninteractive apt-get install -y nginx git`** Cette ligne installe les packages Nginx et Git en utilisant apt-get. L'option `-y` indique à apt-get de répondre "yes" à toutes les questions posées pendant l'installation. La variable d'environnement `DEBIAN_FRONTED` est utilisée pour définir le mode "non interactif" pour que l'installation se fasse sans interaction de l'utilisateur.
    
5.  **`EXPOSE 80`** Cette ligne spécifie que le conteneur écoutera sur le port 80. Cela ne publie pas automatiquement le port sur l'hôte, mais indique simplement que le conteneur est configuré pour écouter sur ce port.
    
6.  **`ADD static-website-example/ /var/www/html/ Cette ligne est actuellement commentée, ce qui signifie qu'elle est ignorée. Si elle était décommentée, elle ajouterait les fichiers du répertoire `static-website-example/` dans le répertoire `/var/www/html/` du conteneur.
    
7.  **`RUN rm -Rf /var/www/html/*`** Cette ligne supprime tout contenu qui se trouve actuellement dans le répertoire `/var/www/html/`.
    
8.  **`RUN git clone https://github.com/diranetafen/static-website-example.git /var/www/html/`** Cette ligne clone un dépôt Git de `https://github.com/diranetafen/static-website-example.git` dans le répertoire `/var/www/html/` du conteneur.
    
9.  **`ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]`** Cette ligne définit la commande par défaut à exécuter lorsque le conteneur est démarré. Dans ce cas, la commande est `nginx` avec les arguments **`-g daemon off;`**. Cette commande démarre le serveur web Nginx et le maintient en cours d'exécution en arrière-plan.

<p align="center">
<img src="https://user-images.githubusercontent.com/40942166/224547004-c71c1274-cc72-44a4-8d7f-4caa5a1c84fc.jpg" width=50% height=50%>
</p>

