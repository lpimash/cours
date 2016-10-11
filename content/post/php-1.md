+++
date = "2016-09-28T15:19:02+02:00"
title = "Bonne pratiques"
draft = false
+++

## Zen coding

* Beautiful is better than ugly.
* Explicit is better than implicit.
* Simple is better than complex.
* Complex is better than complicated.
* Flat is better than nested.
* Sparse is better than dense.
* Readability counts.
* Special cases aren't special enough to break the rules.
* Although practicality beats purity.
* Errors should never pass silently.
* Unless explicitly silenced.
* In the face of ambiguity, refuse the temptation to guess.
* There should be one— and preferably only one —obvious way to do it.
* Although that way may not be obvious at first unless you're Dutch.
* Now is better than never.
* Although never is often better than right now.
* If the implementation is hard to explain, it's a bad idea.
* If the implementation is easy to explain, it may be a good idea.
* Namespaces are one honking great idea—let's do more of those!

## Quelques principes pour coder proprement

> _On reconnait instinctivement du code "propre", Cependant, être capable de faire cette différence ne signifie pas être capable de le faire._

### Nom des variables et fonctions

Le nom d’une variable, d’une fonction ou d’une classe doit répondre à certaines gran-
des questions : la raison de son existence, son rôle et son utilisation. Si un nom exige un
commentaire, c’est qu’il ne répond pas à ces questions.

```php
$d; // Temps écoulé en jours.

// V.S.

$elapsedTimeInDays;

// Pour les focntions, nous devons choisir des verbes ou des groupes verbaux comme postPayment ,  deletePage ou  save

```

### Indentation du code
```php
$Count = 1;while ($Count <= 3)
{print('Hello World!');$Count = $Count + 1;
}

// V.S.

$Count = 1;
while ($Count <= 3) {
  print('Hello World!');
  $Count = $Count + 1;
}
```

fonctions
commentaire
gestion de erreurs
