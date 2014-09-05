title: Tail avec coloration syntaxique
date: 2014/09/04 21:46:25
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

Nous avons lancé une commande *tail* sur le serveur et nous souhaiterions colorer les lignes de log selon leur catégorie (par exemple, lecture d'un fichier de log généré par [Log4J](Log4J).

## Solution

Nous allons donc lancer la commande *tail* et utiliser [AWK](http://www.shellunix.com/awk.html) pour appliquer une couleur contenant un mot-clé.

```bash
tail -F myLog.log | awk '/INFO/ {print "\033[32m" $0 "\033[39m"}/ERROR/ {print "\033[31m" $0 "\033[39m"}/FATAL/ {print "\033[31m" $0 "\033[39m"}/WARN/ {print "\033[33m" $0 "\033[39m"}'
```
Voici un exemple de résultat extrait de l'article de référence:
![](https://udaraliyanage.files.wordpress.com/2013/05/clour-log.png?w=300&h=132)

## Ressources

[Article de référence]( https://udaraliyanage.wordpress.com/2013/05/09/view-filter-logs-in-colour/)

