## Projet Docker 1 - Stack Applicative WordPress et MariaDB

**Objectif :** Mettre en place une stack applicative composée d'une application frontend WordPress et d'une base de données MariaDB, utilisant Docker et Docker Compose.

Voici le lien vers les [images](https://hub.docker.com/repositories/guillaumedupuy) docker

### **Structure du projet**

```
📦 Project-1
 ┣ 📂mysql
 ┃ ┣ 📜 Dockerfile
 ┃ ┗ 📜 my.cnf
 ┣ 📂wordpress
 ┃ ┗ 📜 Dockerfile
 ┣ 📜 .env
 ┣ 📜 docker-compose.yml
 ┗ 📜 README.md
```

### **Configuration Docker compose**

Le fichier **docker-compose.yml** définit deux services principaux, **mariadb** (base de données MariaDB) et **wordpress** (application WordPress), avec des configurations spécifiques pour chaque service.

#### **Mariadb Service**

Le service MariaDB utilise l'image **guillaumedupuy/mariadb:latest** et expose le port **3306**. Les données de la base de données sont persistantes grâce au volume **db_data**. La configuration personnalisée est spécifiée dans le fichier **my.cnf**, qui est monté dans le conteneur.

#### **WordPress Service**

Le service WordPress utilise l'image **guillaumedupuy/wordpress:latest** et expose le port **8080**. Il dépend du service MariaDB. Les configurations sensibles sont définies dans le fichier **.env**.

#### **Réseaux**

Deux réseaux distincts sont créés, **frontend_network** et **backend_network**, pour isoler les services en fonction de leur rôle.

### **Personnalisation des Images Docker**

#### **MariaDB (mysql/Dockerfile et mysql/my.cnf)**

L'image MariaDB est personnalisée en copiant le fichier my.cnf dans le conteneur, ce qui permet de configurer des paramètres spécifiques du serveur MariaDB, tels que le jeu de caractères et la mémoire tampon InnoDB.

#### **WordPress (wordpress/Dockerfile)**

L'image WordPress est étendue pour installer le module PHP GD, répondant aux besoins spécifiques de l'application.

### **Utilisation des Variables d'Environnement**

Les fichiers **.env** sont utilisés pour stocker des variables d'environnement sensibles, garantissant une séparation claire des configurations de l'infrastructure.

### **Exposition des Ports**

Les ports **3306:3306** (MariaDB) et **8080:80** (WordPress) sont exposés pour permettre l'accès aux services depuis l'extérieur.