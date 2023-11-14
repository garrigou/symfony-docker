# Symfony Docker
***
Projet standard pour installer une application Symfony 6 dockérisée.

## Table des matières
1. [Installation](#installation)

## Installation

Il faut tout d'abord cloner le projet :

```
$ git clone git@github.com:garrigou/symfony-docker.git
```

Il faut éditer le fichier *.env* pour indiquer le nom de l'application :

```
#.env
APP_NAME=symfony
```

Il est possible de modifier également dans ce fichier les ports par défaut du nginx (7777) et de phpMyAdmin (8888).

Puis lancer les conteneurs :

```
$ make docker-up-build
```

Cette commande va lancer :

- Un conteneur nginx : 1.25-alpine
- Un conteneur php-fpm : 8.2
- Un conteneur MySQL : 5.7
- Un conteneur phpMyAdmin : 5.2

Pour installer le projet il faut supprimer le fichier *.gitkeep* du répertoire *app* et lancer la commande :

```
$ make sf-install-XXX
```

en précisant XXX pour la version de Symfony souhaitée (6.3 ou 6.4).

Le site est accessible par défaut [ici](http://localhost:7777) et le phpMyAdmin [là](http://localhost:8888).