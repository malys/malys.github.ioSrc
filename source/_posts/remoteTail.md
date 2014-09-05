title: Tail distant à travers SSH
date: 2014/09/04 20:46:25
categories:
	- DevOps
tags:
	- Tail
	- SSH
	- Putty
	- Astuce
	- Linux
---

## Objectif

Notre but est de scruter un fichier de log hébergé sur un serveur Linux. De plus, pour plus de confort, nous souhaitons utiliser un outil de monitoring de fichier de log en temps réel [BareTail](https://www.baremetalsoft.com/baretail/) (vous pouvez tout autant utiliser un autre logiciel ou la ligne de commande)

## Solution

Nous allons utiliser [Putty](http://www.putty.org/) pour créer un tunnel ssh.
Nous allons ouvrir une session non intéractive avec plink pour laisser la main au tail distant. Nous dirigerons le flux du fichier de log sur le disque local que nous traiterons avec notre logiciel de tail sous Windows.

```bash
plink.exe" -pw %PW% %USER%@SERVER tail -F my.log > %TEMP%\my.log|"D:\util\Chocolatey\bin\baretail.exe" %TEMP%\my.log
```

Nous pouvons donc lire en temps les logs distants ainsi que mettre en place des filtres ou de la coloration syntaxique.

## Ressources


[Article de référence]( http://bravedavesmusings.blogspot.fr/2012/12/tailing-logs-over-ssh.html)

