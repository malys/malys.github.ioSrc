title: Convertir les appels aux dépôts du type git:// en https://
date: 2014-06-25 09:16:30
categories:
	- Git
tags:
    - Astuces
---

Les checkout **Git** peuvent se faire par l'intermédiare d'une adresse du type *git://* ou *https://*.
Le flux utilisant les adresses *git://* utilise le port *9418*.
Parfois, le firewall bloque l'accès à ce port.

La solution est de convertir à la volet l'adresse *git:/*/ en *https://*.

Elle est décrite sur le wiki suivant : [Firewall_Blocks_Port_9418](http://http://www.itk.org/Wiki/Git/Trouble#Firewall_Blocks_Port_9418)

Voici, la ligne de commande pour github :
``` bash
$ git config --global url.https://github.com/.insteadOf git://github.com/
```