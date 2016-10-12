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

> _On reconnait instinctivement du code "propre", Cependant, être capable de faire cette différence ne signifie pas automatiquement qu'on est capable d'ecrire du code propre._

### Nom des variables et fonctions

Le nom d’une variable, d’une fonction ou d’une classe doit répondre à certaines gran-
des questions : la raison de son existence, son rôle et son utilisation. Si un nom exige un
commentaire, c’est qu’il ne répond pas à ces questions.

```php
$d; // Temps écoulé en jours.

// V.S.

$elapsedTimeInDays;

// Pour les fonctions, nous devons choisir des verbes ou des groupes verbaux comme postPayment ,  deletePage ou  save

```

### Indentation du code et coding standards

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

http://www.phptherightway.com/#code_style_guide
demo de http://cs.sensiolabs.org/ ?

### Fonctions

Une fonction devrait faire UNE SEULE chose et le faire BIEN !

### Commentaires

Un commentaire devrait expliquer le "pourquoi" d'une ou plusieurs lignes de code et pas le "comment". Si vous devez expliquer "comment" chaque ligne fonctionne, c'est surement que votre code est trop complexe.

#### Commentaires comme Meta-donnée

##### PHPDoc

```
/** <--- Commence par
*/  <--- Se termine par
```

```php
/**
 * Counts the number of items in the provided array.
 *
 * @param mixed[] $items Array structure to count the elements of.
 *
 * @return int Returns the number of elements.
 */
function count(array $items)
{
    // <...CODE ...>
}
```

**Exercice ajouter PHPDoc dans une fonction que vous avez déja ecrite**

##### Annotations

```php
/**
 * Lieu
 *
 * @ORM\Table()
 * @ORM\Entity
 */
class Lieu
{
    /**a tu
     * @var integer
     *
     * @ORM\Column(name="id", type="integer")
     * @ORM\Id
     * @ORM\GeneratedValue(strategy="AUTO")
     */
    private $id;

    /**
     * @var string
     * @ORM\Column(name="nom", type="string", length=255)
     */
    private $nom;

	// ...

}
```



### Utilisez UTF-8

### Conclusion : Comment ecrire du bon code

![xkcd](http://imgs.xkcd.com/comics/good_code.png)
