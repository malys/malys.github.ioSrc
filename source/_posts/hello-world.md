title: Hello Hexo
categories:
	- Technologie
tags:
	- Hexo
	- Blog
---


Welcome to [Hexo](http://hexo.io/)! This is your very first post. Check [documentation](http://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [trobuleshooting](http://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/tommy351/hexo/issues).


## Quick Start

### Créer une nouvelle entrée dans le blog

``` bash
$ hexo new "My New Post"
```

More info: [Writing](http://hexo.io/docs/writing.html)

### Lancer le serveur

``` bash
$ hexo server
```

Plus d'informations : [Server](http://hexo.io/docs/server.html)

### Générer le site

``` bash
$ hexo generate
```

Plus d'informations : [Generating](http://hexo.io/docs/generating.html)

### Déploiement

``` bash
$ hexo deploy
```

More info: [Deployment](http://hexo.io/docs/deployment.html)

## Configuration avancée

### GitHub

Créer un dépôt sur GitHub.
``` bash
git clone https://github.com/xxxx/xxxx.github.io.git
cd xxxx.github.io.git
```

Créer une nouvelle branche `gh-pages`.
``` bash
$ git branch gh-pages
$ git push origin gh-pages
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
  branch: gh-pages
```
Au final, le code source du site sera sur la branche `master` et le code généré sur `gh-pages`.

Générer le site.
``` bash
$ hexo generate
```

Déployer le site sur Github Pages.
``` bash
$ hexo deploy
```
Au bout de 5mn le site est disponible sur `http://xxxx.github.io`.


### UML

Suivre les instructions sur [Jumly plugin](https://github.com/akfish/hexo-tag-uml)

On décrit le diagramme en ajoutant les balises `uml` `enduml`.

```
@found "You", ->
  @message "Think", ->
    @message "Write your idea", "JUMLY", ->
      @create "Diagram"
jumly.css "background-color":"#8CC84B"
```
Le code est alors interprété :
```
{% uml %}
@found "Malys", ->
  @message "Think", ->
    @message "Write his post", "HEXO", ->
      @create "Post"
jumly.css "background-color":"#8CC84B"
{% enduml %}
```