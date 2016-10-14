+++
date = "2016-10-14T10:47:36+02:00"
draft = true
title = "gestion des dates"

+++

## Timezone

Pour prendre en compte le bon fuseai horaore dans le calcul sur les dates

```
<?php
date_default_timezone_set('Europe/Paris');

```

## La classe DatTime

Interface orientée objet pour manipuler les dates et heures

```
<?php
$datetime = new DateTime(); // Date et heure courante

$datetime = new DateTime('2014-04-27 5:03 AM');

$datetime = DateTime::createFromFormat('M j, Y H:i:s', 'Jan 2, 2014 23:04:12'); // cf liste : https://secure.php.net/manual/fr/datetime.createfromformat.php

```

## La classe  DateInterval

```
<?php
$datetime = new DateTime('2014-01-01 14:00:00');

// L'intervalle commence toujours par un "P" pour "Period"
$interval = new DateInterval('P2W'); // ici intervalle de 2 semaines

/*
Y	Années
M	Mois
D	Jours
W	Semaine.
H	Heures
M	Minutes
S	Secondes
*/


// Ajoute l'intervalle et affiche la date formatée

$datetime->add($interval);
echo $datetime->format('Y-m-d H:i:s');

```


**Exercice  Ajouter 45 jours à la date courante et afficher le résultat**

## Classe DatePeriod

```
<?php

$start = new DateTime();
$interval = new DateInterval('P2W');

// iterateur (sur lequel on peut boucler avec foreach) et renvoi 3 dates séparés de 2 semaine chacunes
$period = new DatePeriod($start, $interval, 3);

foreach ($period as $nextDateTime) {
  echo $nextDateTime->format('Y-m-d H:i:s'), "<br>";
}

```


Pour des fonctionnalités évoluées sur les dates, utiliser le composant https://packagist.org/packages/nesbot/carbon
