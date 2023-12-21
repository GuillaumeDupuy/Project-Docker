## Projet Docker 1 - Stack Applicative WordPress et MariaDB

**Objectif :** Mettre en place une stack applicative composée d'une application frontend WordPress et d'une base de données MariaDB, utilisant Docker et Docker Compose.

**Instructions :**

1. **Application WordPress :**

J'ai choisi wordpress:latest comme image de base, car elle est largement utilisée, bien maintenue et optimisée pour exécuter WordPress. Elle est également basée sur php:7.4-apache, ce qui est une bonne base pour exécuter WordPress. Et l'utilisation d'une image officielle de WordPress simplifie la configuration et garantit une compatibilité élevée.

2. **Base de données MariaDB :**

J'ai choisi mariadb:latest comme image de base, car elle est largement utilisée, bien maintenue et optimisée pour exécuter MariaDB. Elle est également basée sur debian:buster, ce qui est une bonne base pour exécuter MariaDB. Et l'utilisation d'une image officielle de MariaDB garantit une base stable et sécurisée pour notre application WordPress.