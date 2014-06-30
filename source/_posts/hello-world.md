title: Hello Hexo
date: 2014/5/01 20:46:25
categories:
	- Technologie
tags:
	- Hexo
	- Blog
---

[Hexo](http://hexo.io/) est une plateforme de blog 'statique'.
Le code est généré et déployé par la suite. Il est très orienté *Geek* mais très facile à mettre en oeuvre, à utiliser et à héberger.

Il est basé sur la technologie *NodeJS*.

## Quick Start

### Créer une nouvelle entrée dans le blog

``` bash
$ hexo new "My New Post"
```

Plus d'informations : [Ecriture](http://hexo.io/docs/writing.html)

### Lancer le serveur

``` bash
$ hexo server
```

Plus d'informations : [Serveur](http://hexo.io/docs/server.html)

### Générer le site

``` bash
$ hexo generate
```

Plus d'informations : [Génération](http://hexo.io/docs/generating.html)

### Déploiement

``` bash
$ hexo deploy
```

Plus d'informations : [Déploiement](http://hexo.io/docs/deployment.html)

## Configuration avancée

### GitHub

Créer un dépôt sur GitHub.
``` bash
git clone https://github.com/xxxx/xxxx.github.ioSrc.git
cd xxxx.github.io.gitSrc
```

``` bash
$ npm install
```

Installer hexo.
``` bash
$ npm install hexo -g
```
et suivre les instructions de cette page [Hexo Setup](http://hexo.io/docs/setup.html).

Configurer Hexo : [Hexo Configuration](http://hexo.io/docs/configuration.html)

 Configurer le déploiement sur GitHub.

```
deploy:
  type: github
  repo: https://github.com/xxxx/xxxx.github.io.git
  branch: master
```
Au final, le code source du site sera sur la branche `master` de *github.com/xxxx/xxxx.github.ioSrc* et le code généré sur `master` de *github.com/xxxx/xxxx.github.io*

Générer le site.
``` bash
$ hexo generate
```

Déployer le site sur Github Pages.
``` bash
$ hexo deploy
```

### UML

Suivre les instructions sur [Jumly plugin](https://github.com/akfish/hexo-tag-uml)

On décrit le diagramme en ajoutant les balises `uml` `enduml`.

```
@found "Malys", ->
  @message "Think", ->
    @message "Write your idea", "JUMLY", ->
      @create "Diagram"
jumly.css "background-color":"#8CC84B"
```
Le code est alors interprété :

{% uml %}
@found "Malys", ->
  @message "Think", ->
    @message "Write your idea", "JUMLY", ->
      @create "Diagram"
jumly.css "background-color":"#8CC84B"
{% enduml %}
