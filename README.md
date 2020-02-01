# Guide de déploiement
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=AppPointage&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=AppPointage) [![Bugs](https://sonarcloud.io/api/project_badges/measure?project=AppPointage&metric=bugs)](https://sonarcloud.io/dashboard?id=AppPointage) 

Ce document est un guide de déploiement du logiciel issu du projet de qualité logiciel **gestion de stock**. Les auteurs sont Guillaume Bouchard et Colin Troisemaine.

## Qu'est-ce que c'est ?

Cette application est un projet Maven écrit en Java et permet de gérer des stocks de magasin. Le but de ce projet était d'utiliser un maximum d'outils visant à améliorer la qualité du logiciel.

## Installation

Le projet Maven permet de générer un exécutable JAR qui contient toutes les dépendances dont le logiciel a besoin. Le logiciel étant écrit avec java 11, il faut que cette version soit installée puis il suffit de le lancer en double cliquant sur le JAR. Néanmoins cette application a besoin d'une base de données MySQL qui part défaut est locale et se nomme **projet_gestion_de_stocks** avec l'utilisateur root sans mot de passe. L'application permet néanmoins de changer cette adresse depuis la fenêtre de connexion. 

Il est conseillé de changer ces paramètres directement dans le fichier ./src/main/resources/META-INF/persistence.xml dans le persistence-unit **classique** et régénérer le JAR en recompilant le projet car le programme revient toujours à ces paramètres "par défaut" au lancement du JAR.

## Tests d'intégration 

Les tests d'intégration s'effectuent sur une base de données différente de celle de production. Elle est par défaut nommée **projet_gestion_de_stocks_TEST**, comme pour la base de données classique elle est située en local avec l'utilisateur root et sans mot de passe. Vous pouvez modifier ses paramètres directement dans le fichier persistence.xml.

Voici une commande docker qui permet de lancer une base de données en local (sur le port 3306) pour effectuer les tests d'intégrations : 


	docker run --name testDB -e MYSQL_ALLOW_EMPTY_PASSWORD=yes -d -p 3306:3306 -e MYSQL_DATABASE=projet_gestion_de_stocks_TEST mysql

 
