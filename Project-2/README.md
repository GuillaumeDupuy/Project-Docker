# Projet Docker 2 - Cluster Elasticsearch avec Kibana

**Objectif :** Mettre en place un cluster Elasticsearch composé de trois nœuds et un conteneur Kibana qui a accès au cluster.

Voici le lien vers les [images](https://hub.docker.com/repositories/guillaumedupuy) docker

## ** Comment lancer ? ** 

Se mettre dans le dossier et lancer la commande suivante : 

```docker composer up```


## **Structure du projet**

```
📦 Project-2
 ┣ 📂es-cluster
 ┃ ┣ 📜 elasticsearch.yml
 ┃ ┗ 📜 kibana.yml
 ┣ 📜 .env
 ┣ 📜 docker-compose.yml
 ┗ 📜 README.md
```

## **Configuration Docker Compose pour Elastic Stack**

Le fichier **docker-compose.yml** définit plusieurs services pour déployer un cluster Elasticsearch et un service Kibana pour la visualisation des données.

### **Services Elasticsearch (es01, es02, es03)**

Chaque service Elasticsearch utilise l'image **docker.elastic.co/elasticsearch/elasticsearch:${ES_VERSION}** et expose le port **9200** avec une configuration spécifique. Les nœuds Elasticsearch **(es01, es02, es03)** forment un cluster, et la configuration est partagée via les fichiers **elasticsearch.yml**. Les données sont persistantes grâce aux volumes **esdata01, esdata02, et esdata03**.

### **Service Kibana (kibana)**

Le service Kibana utilise l'image **docker.elastic.co/kibana/kibana:${ES_VERSION}** et expose le port **5601**. Il est configuré pour se connecter au cluster Elasticsearch via l'URL **http://es01:9200**. La configuration de Kibana est gérée dans le fichier **kibana.yml**.

### **Réseaux**

Un réseau nommé **elastic** est créé pour connecter les services Elasticsearch et Kibana, permettant la communication entre eux.

### **Volumes**

Trois volumes **(esdata01, esdata02, esdata03)** sont créés pour stocker les données persistantes d'Elasticsearch.

## **Configuration Elasticsearch (es-cluster/elasticsearch.yml)**

Le fichier elasticsearch.yml configure des paramètres importants du cluster Elasticsearch, tels que la mémoire, les noms de nœuds, la découverte des nœuds, etc.

## **Configuration Kibana (es-cluster/kibana.yml)**

Le fichier kibana.yml configure Kibana avec les hôtes Elasticsearch auxquels il doit se connecter.