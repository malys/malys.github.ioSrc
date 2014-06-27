title: NPM Link avec Windows et UAC
categories:
	- nodeJS
tags:
	- Symlinks
	- Astuce
---

Avec l'OS Windows et l'UAC actif, il faut passer en mode administrateur pour pouvoir utiliser  [NPM Link](https://www.npmjs.org/doc/cli/npm-link.html)

Une alternative est d'utiliser [npm-junction](https://bitbucket.org/jaguard/npm-junction).
Basé sur *SysInternals Junction*, il permet de créer des symlinks facilement avec le UAC actif ou sous Windows (XP,2000,2003).

``` bash
$ npm install -g npm-junction
```

Dans le répertoire du module à partager localement:
``` bash
$ nlink
==> Link [rekuirify@XXXXXXXXXXXXX] => C:\Users\malys\AppData\Roaming\npm\node_modules\rekuirify*
```

Dans le répertoire du projet qui va  utiliser la dépendances
``` bash
$ nlink rekuirify
```

Idem pour la command *nunlink*.




