# Symfony Docker
***
Projet standard pour installer une application Symfony 5 & 6 dockérisée.

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

Puis lancer les conteneurs :

```
$ make docker-up-build
```

Cette commande va lancer :

- Un conteneur nginx : 1.20-alpine
- Un conteneur php-fpm : 8.0
- Un conteneur MySQL : 5.7
- Un conteneur phpMyAdmin : 5.1

Pour installer le projet il faut supprimer le fichier *.gitkeep* du répertoire *app* et lancer la commande :

```
$ make sf-install-5.4
```

ou

```
$ make sf-install-6.0
```

en fonction de la version de Symfony souhaitée.

Le site est accessible [ici](http://localhost:7000) et le phpMyAdmin [là](http://localhost:8080).