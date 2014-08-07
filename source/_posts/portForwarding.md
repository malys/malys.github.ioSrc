title: Redirection de port sous Windows
date: 2014/8/07 07:00:00
categories:
	- DevOps
tags:
	- Astuce
	- Windows
---

# Objectif
Dans notre cas, nous souhaitons rediriger une requête vers un autre serveur.

	https://localhost:8443/monsite -> https://serveur_de_test/monsite


Vous pouvez utiliser un utilitaire du type *SPI Port Forward 1.0* ou encore mieux la ligne de commande:

```bash
netsh interface portproxy add v4tov4 listenport=fromport listenaddress=fromip connectport=toport connectaddress=toip

```

Dans mon cas,
`fromport`: 8443
`fromip`: localhost
`toport`: 443
`toip`: serveur_de_test

Pour la supprimer,
```bash
netsh interface portproxy delete v4tov6 listenport= {Integer | ServiceName} [[listenaddress=] {IPv4Address| HostName}] [[protocol=]tcp
```]

En redirigeant les requêtes, vous pouvez également les analyser et voir les paquets circulés (voir les ressources)

#Ressources

[Windows Port Forwarding](http://blog.mobzystems.com/2013/08/23/windows-server-port-forwarding-from-the-command-line/)

[Technet](http://technet.microsoft.com/fr-fr/library/cc731068%28v=ws.10%29.aspx)

[Http Sniffer](http://www.nirsoft.net/utils/http_network_sniffer.html)

[Membrane](http://www.membrane-soa.org/soap-monitor/)