+++
draft = false
date = "2016-10-11T16:55:48+02:00"
title = "exceptions"

+++

## S*** happens

Erreurs et Excpetions : Les erreurs existent depuis longtemps dans php elles arretent le scripts et une fonction globale traite les erreurs.
certaines erreurs sont "unrecoverable". Certaines vielles fonctions PHP (comme fopen()) renvoient toujours des erreurs au lieu d'envoyer des exceptions.

Les exceptions sont une évolutions "orientée objet" des anciennes erreurs.

```
<?php

$exception = new Exception("OMG c'est affreux !!!");
$message = $exception->getMessage();

echo $message;

```

Elles sont envoyé (thrown) est récupérés (catch).

Vous envoyez une exception quand quelque chose ne se passe pas comme prévu.

```
<?php
echo ("jusqu'ici tout va bien ...");
throw new Exception('Something went wrong. Time for lunch!');
echo (" ??? ");
```

Les framework et composants envoie des Exceptions et laisse au développeur le soin d'agir en conséquence ...

## Attrapez-les tous!!!

```
<?php
try {

    $pdo = new PDO('mysql://host=wrong_host;dbname=wrong_name');

} catch (PDOException $e) {

    $message = $e->getMessage(); // logger le message d'erreur dans un ficheir de log ou en BDD par exemple
     // Afficher un joli message à l'utilisateur
    echo 'Something went wrong. Check back soon, please.';
    exit;

}


```

## Attrapper plusieurs exceptions

```
<?php
try {
    throw new Exception('Not a PDO exception');
    $pdo = new PDO('mysql://host=wrong_host;dbname=wrong_name');
} catch (PDOException $e) {
    // Handle PDO exception
    echo "Caught PDO exception";
} catch (Exception $e) {
    // Handle all other exceptions
    echo "Caught generic exception";
} finally {
    // Always do this
    echo "Always do this";
}

```

### Exception Handler

On ne peut pas attrapper toutes les exceptions possibles. il faut mettre en place un "Exception Handler"

```
<?php

set_exception_handler(function (Exception $e) {
    echo "Erreur : " .  $e->getMessage();
});

echo ("jusqu'ici tout va bien ...");
throw new Exception('Something went wrong. Time for lunch!');
echo (" ??? ");
```


## Erreurs

Les erreurs classiques sont plutot déclanchés lors d'une erreur de syntaxe par exemple.


```
# Here are my error-reporting php.ini settings for development:
; Display errors
display_startup_errors = On
display_errors = On
; Report all errors
error_reporting = -1
; Turn on error logging
log_errors = On


# Here are my error-reporting php.ini settings for production:
; DO NOT display errors
display_startup_errors = Off
display_errors = Off
; Report all errors EXCEPT notices
error_reporting = E_ALL & ~E_NOTICE
; Turn on error logging
log_errors = On
```


## En developpement utiliser des composents comme Whoops

https://github.com/filp/whoops
