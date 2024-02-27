---
title: Expressions regex courantes d’AEM Forms Edge Delivery Service pour la validation des champs de formulaire
description: Expressions regex courantes d’AEM Forms Edge Delivery Service pour la validation des champs de formulaire
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 78d40574e6fea8dde22414e43fd77215b9e7d2a1
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 4%

---


# Expressions regex couramment utilisées pour les validations

Voici quelques expressions régulières que vous pouvez utiliser pour améliorer la validation des formulaires au-delà de ce que proposent les navigateurs modernes :

## Mot de passe fort

```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

Garantit au moins 8 caractères avec :

* Lettre minuscule (a-z)
* Lettre majuscule (A-Z)
* Chiffre (0-9)
* Caractère spécial (@$)%*?&amp;)


## Adresse électronique


```regex
^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$
```

Autorise les lettres, les chiffres et les caractères spéciaux dans le nom d’utilisateur et le nom de domaine.


## Numéro de téléphone (format US)

```regex
^\(?([0-9]{3})\)?[-. ]([0-9]{3})[-. ]([0-9]{4})$
```

Valide les numéros de téléphone au format (XXX) XXX-XXXX.



## URL

```regex
^(http|https)://.*$
```

Vérifie une URL valide commençant par http ou https.



## Date (AAAA-MM-JJ)

```regex
^\d{4}-(0[1-9]|1[0-2])-(0[1-9]|[12][0-9]|3[01])$
```

Valide les dates au format AAAA-MM-JJ.


## Heure (HH:MM)

```regex
^([01][0-9]|2[0-3]):[0-5][0-9]$
```

Valide les heures au format HH:MM (format 24 heures).


## Code postal (format US)

```regex
^\d{5}(?:[-\ ]\d{4})?$
```

Valide les codes postaux américains à 5 chiffres avec un trait d’union facultatif et une extension à 4 chiffres.


## Nom d’utilisateur (alphanumérique et trait de soulignement)

```regex
^[a-zA-Z0-9_]+$
```

Autorise les lettres, les chiffres et les traits de soulignement.


## Code hexadécimal

```regex
^#[0-9a-fA-F]{6}$
```

Valide les codes couleur hexadécimaux à 6 chiffres. Par exemple, #FFFFFF.


## Adresse IP

```regex
^(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})$
```

Valide les adresses IPv4.



## Numéro de sécurité sociale (format US)

```regex
^\d{3}-\d{2}-\d{4}$
```



## Numéro de carte de crédit

```regex
^(?:4[0-9]{12}(?:[0-9]{3})?|[25][1-7][0-9]{14}$
```

Valide les numéros de téléphone au format (XXX) XXX-XXXX.



## Numéro de téléphone (format US) :

```regex
^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$
```

Valide les numéros de téléphone au format (XXX) XXX-XXXX.
