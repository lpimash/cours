+++
title = "espace de noms et autoloading"
draft = false
date = "2016-10-11T16:44:19+02:00"

+++

## Namespaces : Intro

Organise le code PHP en hiérarchie comme le ferais un système de fichier.

Chaque composant ou framework PHP est organisé sous son propre nom global unique (Ex: League\Plates) On evite ainsi les conflits (Ex. on peut avoir des nom de classe (ou de functions, de constantes, ) générique comme Template, Request ou Response)


Avant les namespaces **`Zend_Cloud_DocumentService_Adapter_WindowsAzure_Query`** correspondais au fichier **`Zend/Cloud/DocumentService/Adapter/WindowsAzure/Query.php`**

### Exemple

```
<?php

// app.php
include 'exemples.php';
include 'fonctions.php';

// exemples.php
function test(){
    // faire qqc de passionnant :)
}

//fonctions.php
function test(){
    // faire qqc de complètement différent de l'autre fonction test() !!! :)
}
```

RESULTAT :
```
Fatal error: Cannot redeclare test()
```

AVEC LES ESPACE DE NOMS :

```
<?php

// app.php
include 'exemples.php';
include 'fonctions.php';

MesFonctions\test();
MesExemples\test();

// exemples.php
namespace MesExemples;

function test(){
    // faire qqc de passionnant :)
}

//fonctions.php
namespace MesFonctions;

function test(){
    // faire qqc de complètement différent de l'autre fonction test() !!! :)
}

```


## Utilisation

### L'import avec "use"

```
<?php
use Symfony\Component\HttpFoundation\Response;

$response = new Response('Oops', 400);
$response->send();
```

## L'autoloading
