+++
title = "nettoyer valider les donnes"
draft = true
date = "2016-10-13T16:07:50+02:00"

+++

La régle numéro 1 du Developper Club est : ne Jamais faire confiance aux données qui ne sont pas sous votre controle !
La régle numéro 2 du Developper Club est : ne Jamais faire confiance aux données qui ne sont pas sous votre controle !

* $_GET
* $_POST
* $_REQUEST
* $_COOKIE
* $argv
* php://stdin
* php://input
* file_get_contents()
* Bases de données distantes
* API's

Ces sources de données sont des vecteurs d'attaque potentiels. Elle doivent etre nettoyés (sanitize), validées (validate) , Echapées pour l'affichage (output escape)

## Nettoyage (Sanitize)

Avant d'engregistrer une donnée dans votre base de donnée il faut supprimer ou echapper les caractères dangereux.

Si qqn a la possibilité de laisser un commentaire HTML dans votre blog, vous risquez une faille XSS :

```html
<p>
This was a helpful article!
</p>
<script>window.location.href='http://example.com';</script>
```

### HTML

Utilisez htmlentities()

```
<?php
$input = '<p><script>alert("You won the Nigerian lottery!");</script></p>';
echo htmlentities($input, ENT_QUOTES, 'UTF-8');

```

Si vous voulez un filtrage plus fin i.e. autoriser que certaine balise html dans vos commentaires par exemple, il faudra utiliser une librairie comme http://htmlpurifier.org/

### Requete SQL

Certaine requetes SQL soivent etre construites avec les données postés via un formulaire par exmemple. Ne JAMAIS concaténer tel quel les données pour construire votre requete SQL !!!
```
<?php
$sql = sprintf(
'UPDATE users SET password = "%s" WHERE id = %s',
$_POST['password'],
$_GET['id']
);

```


Si qqn envoi la requete HTTP suivante :

```
POST /user?id=1 HTTP/1.1
Content-Length: 17
Content-Type: application/x-www-form-urlencoded

password=abc";--
```

Les passe de TOUS les utilisateurs seront initialisés à "abc" car "-- " est considérer comme un commentaire en SQL (MySQL)

Il faudra utiliser une requete préparée (prepared statment).

### Données d'un formulaire

filter_var()  nous permet de valier email, entiers, plages de valeurs, ...

```
<?php
$email = 'john@exa/\mpl e.com';
$mail = filter_var($email, FILTER_SANITIZE_EMAIL);
var_dump($mail);
```

## Validation

La validation contrairement au netoyage ne supprime pas des caractères mais dit seulement si la donnée est valide ou pas.

La validation peremt d'eviter des erreurs à l'enregistrement en base de donnée : par exemple si un champs est de type Date et que l'utilisateur entre dans l'input "l'année prochaine".

```
<?php
$email = 'john@exa/\mpl e.com';
$isEmail = filter_var($email, FILTER_VALIDATE_EMAIL);
var_dump($isEmail);

$email = filter_var($email, FILTER_SANITIZE_EMAIL);
$isEmail = filter_var($email, FILTER_VALIDATE_EMAIL);
var_dump($isEmail);

```

```
bool(false)

string(16) "john@example.com"
```
