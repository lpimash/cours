+++
date = "2016-10-11T16:43:43+02:00"
title = "revision bases"
draft = true

+++

## Une bonne référence
https://daylerees.com/php-pandas/

## Opérateur de comparaison

```
<?php
$a = 5;   // 5 as an integer

var_dump($a == 5);       // compare value; return true
var_dump($a == '5');     // compare value (ignore type); return true
var_dump($a === 5);      // compare type/value (integer vs. integer); return true
var_dump($a === '5');    // compare type/value (integer vs. string); return false

//Equality comparisons
if (strpos('testing', 'test')) {    // 'test' is found at position 0, which is interpreted as the boolean 'false'
    // code...
}

// vs. strict comparisons
if (strpos('testing', 'test') !== false) {    // true, as strict comparison was made (0 !== false)
    // code...
}
```

Ex. Que renvoi l'expression :

```
<?php
substr("12345", 1, 1) === 2;
substr("12345", 1, 1) === '2';

// on pourra utiliser var_dump() pour tester l'expression.

```

## Type casting

* (int), (integer) : modification en integer
* (bool), (boolean) : modification en boolean
* (float), (double), (real) : modification en float
* (string) : modification en string
* (array) : modification en array

```
<?php
$i = 10;
var_dump($i === "10");
var_dump( (string)$i === "10");
// le casting ne modifie pas $i, c'est toujours un int après l'instruction ci-dessus
// si on veux modifier le type il faut faire $i = (string)$i

$s = "chaine de caractère";
var_dump( (int)$s );

$s = "5 chaine de caractère";
var_dump( (int)$s );
```

RESULTAT :

```
bool(false)
bool(true)
int(0)
int(5)
```

## Conditions

Vous pourrez rencontrer, notamment dans une fonction un bloc "if" sans le "else"  :

```
<?php
function test($a)
{
    if ($a) {
        return true;
    } else {
        return false;
    }
}

// vs.

function test($a)
{
    if ($a) {
        return true;
    }
    return false;    // else is not necessary
}

// or even shorter:

function test($a)
{
    return (bool) $a;
}
```

## Switch

```
<?php
$answer = test(2);    // the code from both 'case 2' and 'case 3' will be implemented

function test($a)
{
    switch ($a) {
        case 1:
            // code...
            break;             // break is used to end the switch statement
        case 2:
            // code...         // with no break, comparison will continue to 'case 3'
        case 3:
            // code...
            return $result;    // within a function, 'return' will end the function
        default:
            // code...
            return $error;
    }
}
```

## Concatenation de chaine

```
<?php
$a  = 'Multi-line example';    // concatenating assignment operator (.=)
$a .= "\n";
$a .= 'of what not to do';

// vs

$a = 'Multi-line example'      // concatenation operator (.)
    . "\n"                     // indenting new lines
    . 'of what to do';
```

## Double quote

```
<?php
echo 'phptherightway is ' . $adjective . '.'     // a single quotes example that uses multiple concatenating for
    . "\n"                                       // variables and escaped string
    . 'I love learning' . $code . '!';

// vs

echo "phptherightway is $adjective.\n I love learning $code!"  // Instead of multiple concatenating, double quotes
                                                               // enables us to use a parsable string
```

## Chaine multiligne
```
<?php
$var = "some text";
$text = <<<EOT
  Place your text between the EOT. It's
  the delimiter that ends the text
  of your multiline string.
  $var
EOT;

echo $text;

```

## Tenary operator

```
<?php
$a = 5;
echo ($a == 5) ? 'yay' : 'nay';

// dans une fonction on pourrais ecrire un return comme ça
return ($a == 3) ? true : false;

```

## Tableaux

```
<?php

// Create an array.
$pandas = array('Lushui', 'Jasmina', 'Pali');

// Create an array as well.
$pandas = ['Lushui', 'Jasmina', 'Pali'];
```

```
<?php

// Create an of pandas.
$pandas = ['Lushui', 'Jasmina', 'Pali'];

// Fetch our pandas into separate variables.
$lushui     = $pandas[0];
$jasmina    = $pandas[1];
$pali       = $pandas[2];
```

```
<?php

// Create an of pandas.
$pandas = ['Lushui', 'Jasmina', 'Pali'];

// Fetch a panda that doesn't exist.
$fakePanda = $pandas[3];

// Dump the result.
echo $fakePanda;

// ==> PHP Notice:  Undefined offset: 3
```

```
<?php

// Create an associative array.
$numbers = [
    'one'       => 1,
    'two'       => 2,
    'three'     => 3,
    'four'      => 4,
    'five'      => 5,
    'six'       => 6
];
```

```
<?php

// Create a multi-dimensional array.
$numbers = [
    'prime'         => [2, 3, 5, 7, 11],
    'fibonacci'     => [1, 1, 2, 3, 5],
    'triangular'    => [1, 3, 6, 10, 15]
];
```
## Boucles

### while

```
<?php

// Set the panda counter to zero.
$pandas = 0;

// Iterate while $pandas less than 50.
while ($pandas < 50) {

    // Output the number of panda butlers.
    echo "We have {$pandas} panda butlers!\n";

    // Increment the counter.
    $pandas++;
}
```

### Do while

Le bloc est executé au moins une fois !

```
<?php

// Set the panda counter to zero.
$pandas = 0;

// Iterate...
do {

    // Output the number of panda butlers.
    echo "We have {$pandas} panda butlers!\n";

    // Increment the counter.
    $pandas++;

// ... while $pandas less than 50.
} while ($pandas < 50);
```

### for
```
<?php

// Iterate for 50 repetitions.
for ($i = 0; $i < 50; $i++) {

    // Output the number of panda butlers.
    echo "We have {$i} panda butlers!\n";
}
```

### Foreach

```
<?php

// Create an array of pandas.
$pandas = ['Lushui', 'Pali', 'Jasmina'];

// Iterate our panda array.
foreach ($pandas as $panda) {
    echo "Hello there {$panda}!\n";
}
```

## Exercice CodeInGame
