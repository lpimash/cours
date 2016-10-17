+++
title = "authentification et enregistrement"
draft = true
date = "2016-10-14T14:25:39+02:00"

+++

## Formulaire d'enregistrement des utilisateurs

```sql
CREATE TABLE `utilisateur` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `nom` varchar(1000) NOT NULL,
  `prenom` varchar(1000) NOT NULL,
  `mail` varchar(1000) NOT NULL,
  `password` varchar(1000) NOT NULL,
  PRIMARY KEY (`id`)
) DEFAULT CHARSET=utf8;
```

Pour le code cf. Exo registration-1,2,....php
