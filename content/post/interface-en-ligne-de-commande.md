+++
title = "interface en ligne de commande"
draft = true
date = "2016-10-11T16:43:36+02:00"

+++

```php
<?php
if ($argc != 2) {
    echo "Usage: php hello.php [nom].\n";
    exit(1);
}
$nom = $argv[1];
echo "Hello, $nom\n";
```

```
> php hello.php
Usage: php hello.php [nom]
> php hello.php world
Hello, world
```

**Exercice** lister les images dans un dossier
