+++
draft = false
date = "2016-10-12T15:47:48+02:00"
title = "rappels archi"

+++

![php](/img/nginxphpfcgi.png)

* Browser (navigateur client)

ENVOI requete HTTP via paquets TCP/IP sur le réseau internet

* Requete HTTP
* Serveur WEB
* ----- VOTRE APPLI --------
* Moteur PHP (zend, HHVM)
  * BDD
  * Filesystem
  * webservice
  * ... what else ? ...
* ----- VOTRE APPLI --------
* Serveur WEB
* Reponse HTTP

RETOUR REPONSE au navigateur client (avec dans la réponse eventuellement du code JS à éxecuter)
