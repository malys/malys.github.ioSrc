title: Redirection de port en SSH
date: 2014/8/05 07:00:00
categories:
	- DevOps
tags:
	- SSH
	- ProxMox
	- Astuce
	- Putty
---

# Définition 

La redirection de port ou port forwarding ou port mapping en anglais, consiste à rediriger des paquets réseaux reçus sur un port donné d'un ordinateur ou un équipement réseau vers un autre ordinateur ou équipement réseau sur un port donné. Cela permet entre autres de proposer à des ordinateurs extérieurs à un réseau d'accéder à des services répartis sur plusieurs ordinateurs de ce réseau. Voir [Wikipedia](http://fr.wikipedia.org/wiki/Redirection_de_port).

# Objectif

Nous souhaitons via une connexion SSH comsommer des services hébergées en local et des services locaux à distance

Dans notre cas, nous aurons un serveur Proxmox qui mettra à disposition des containers ou des machines virtuelles.

{% limg  portforwarding.png %}

# Redirection de port

## Putty

Dans ce cas, nous voulons avoir accès au port 80 de la VM sous CentOS avec le serveur web.

Pour cela, nous devons créer un tunnel SSH. Dans notre cas, nous utiliserons Putty comme client SSH (les commandes ssh sous Windows ou Linux sont quasiment identiques).

{% limg  Putty1.png %}

et configurer le tunnel dans SSH/Tunnels

{% limg  Putty2.png %}

```
Source Port : le port local à votre poste sur lequel le service web distant sera accessible

Destination: IP Locale de la VM:Port à rediriger

Local: Permet de définir le sens de la redirection du port dans ce cas là distant -> local
```

Il faut sauvegarder la configuration.

{% limg  Putty3.png %}

## Ligne de commande
```bash
plink.exe -ssh proxmoxPublicIP -P 22 -l user -L 8080:CentOSLocalIP:80 -N
```
*-N* permet d'ouvrir exclusivement le tunnel sans ouvrir la console.
*-L* peuvent être multiple pour ajouter autant de port que vous souhaitez


Exemples:
```bash
rem HTTP
plink.exe -ssh proxmoxPublicIP -P 22 -l user -L 8080:CentOSLocalIP:80 -N
```
```bash
rem RDP Bureau distant Windows
plink.exe -ssh proxmoxPublicIP -P 22 -l user -L 33389:CentOSLocalIP:3389 -N
```

## Utilisation

Ouvrons sur votre poste votre navigateur préféré à l'acdresse suivante:
*http://localhost:8080*


# Redirection inverse de port

## Putty

Dans ce cas, nous voulons avoir accès au port 80 de notre poste sur le serveur Windows 2003 avec IE8.
Nous pourrons alors tester notre site web avec IE8 par exemple.

Pour cela, nous devons créer un tunnel SSH. Nous allons utliser celui que nous avons précédemment configuré.

Configurons le tunnel dans SSH/Tunnels 

{% limg  Putty4.png %}

```
Source Port : le port local au serveur Win 2003 sur lequel votre site web sera accessible

Destination: IP Locale de votre poste sur lequel le serveur web écoute

Remote: Permet de définir le sens de la redirection du port dans ce cas là  local -> distant
```

Il faut sauvegarder la configuration.

{% limg  Putty3.png %}

## Ligne de commande
```bash
plink.exe -ssh proxmoxPublicIP -P 22 -l user -R *:1080:localhost:80 -N
```

\*:1080 permet de préciser que ce port sera accessible pour toutes les interfaces réseaux.

-R peuvent être multiple pour ajouter autant de port que vous souhaitez.


## Configuration du serveur SSH

Il faut préciser au serveur proxmox que le port redirigé sera accessible sur toutes les interfaces si le client le demande (**:1080* de la ligne de commande)

Sur le serveur Proxmox,

```bash
sudo nano /etc/ssh/sshd_config

```
Ajouter la ligne et sauvegarder: 

```
Match User `user`
   GatewayPorts yes
```

Recharger la configuration du serveur SSH
```
/etc/init.d/ssh reload 
```

## Utilisation

Ouvrons sur le serveur Win 2003 avec IE8 l'adresse suivante:

*http://IpLocaleServeurProxmox:8080*

Exemple:

*http://192.168.0.254:8080*

Avec le bridge Proxmox configuré ainsi:

{% limg  Putty5.png %}



## Ressources

[Reverse Forwarding](http://askubuntu.com/questions/50064/reverse-port-tunnelling)

[Reload SSH](http://www.cyberciti.biz/faq/howto-restart-ssh/)

[Tutoriel Putty](http://marc.terrier.free.fr/docputty/Chapter3.html#using-cmdline)

[Check Reverse Port Forwarding](http://serverfault.com/questions/387772/ssh-reverse-port-forwarding-with-putty-how-to-specify-bind-address)




