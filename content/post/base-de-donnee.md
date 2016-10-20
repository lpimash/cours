+++
title = "base de donnee"
draft = false
date = "2016-10-12T09:44:24+02:00"

+++

## PDO

Interface orientée objet qui fourni une couche d'abstraction aux drivers de base de données.
Ne partez pas en courant ... En fait c'est très simple ... :)

```
<?php
try {

  $pdo = new PDO(
    'mysql:host=127.0.0.1;dbname=c9;port=3306;charset=utf8', // DSN a.k.a Data Source Name
    'o_revollat',
    ''
  );

} catch (PDOException $e) { // Gérer le erreur de connexion avec un message bien présenté et eviter la divulgation d'informations sensibles
    echo "Connexion à la base de donnée échouée";
    exit;
}
```

## Requetes préparées (prepared statements)

**Ne pas faire !!!! Risque d'injection SQL**

```
<?php
$sql = sprintf('SELECT id FROM users WHERE email = "%s"', $_GET['email']);
```

Faire

```
<?php
$sql = 'SELECT id FROM users WHERE email = :email';
$statement = $pdo->prepare($sql);
$email = filter_input(INPUT_GET, 'email');
$statement->bindValue(':email', $email);
```

## Resultat de la requete

on utilise la methode fetch de l'objet requete

```
<?php
$sql = 'SELECT id, email FROM users WHERE email = :email';
$statement = $pdo->prepare($sql);
$email = filter_input(INPUT_GET, 'email');
$statement->bindValue(':email', $email);

$statement->execute();

// Itération sur le résultat
while (($result = $statement->fetch(PDO::FETCH_ASSOC)) !== false) { // FETCH_ASSOC permet de renvoyer un tableau associatif [nomChamp => valeur]
    echo $result['email'];
}

```

## Transactions

Pour garder la consistence de la base de donnée on utlise des transactions : toutes les requetes s'executent ou bien aucune ne s'execute (si une a échouée par exemple)
