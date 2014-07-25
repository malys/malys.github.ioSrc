title: Autocompletion des tâches Grunt dans la console
date: 2014/7/29 07:00:00
categories:
	- NodeJS
tags:
	- Grunt
	- Bash
	- Astuce
---

Dans %HOME%/.bashrc , en ajoutant :

```
	eval "$(grunt --completion=bash)"
```

La console Bash va alors évaluer les tâches *Grunt* associées à ce projet en pressant la touche *tab*.

Cette astuce fonctionne sous Windows et Linux. Voir page de [Grunt](https://github.com/gruntjs/grunt-cli) pour plus de détails.


