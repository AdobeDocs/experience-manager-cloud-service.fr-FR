---
title: Edge Delivery Services pour les expressions regex d’AEM Forms fréquemment utilisées pour valider les champs de formulaire
description: Edge Delivery Services pour les expressions regex d’AEM Forms fréquemment utilisées pour valider les champs de formulaire
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
exl-id: 5cfe23bb-155f-4639-b7b7-5edc172ba92a
source-git-commit: 4a8153ffbdbc4da401089ca0a6ef608dc2c53b22
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 85%

---

# Expressions regex couramment utilisées pour les validations

Voici quelques expressions régulières que vous pouvez utiliser pour améliorer la validation des formulaires au-delà de ce que proposent les navigateurs modernes :

## Mot de passe sécurisé

```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

Garantit au moins 8 caractères avec :

* Lettre minuscule (a-z)
* Lettre majuscule (A-Z)
* Chiffre (0-9)
* Caractère spécial (@$!%*?&amp;)


## Adresse e-mail


```regex
^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$
```

Autorise les lettres, les chiffres et les caractères spéciaux dans le nom d’utilisateur ou d’utilisatrice et le nom de domaine.


## Numéro de téléphone (format américain)

```regex
^\(?([0-9]{3})\)?[-. ]([0-9]{3})[-. ]([0-9]{4})$
```

Valide les numéros de téléphone au format (XXX) XXX-XXXX.



## URL

```regex
^(http|https)://.*$
```

Garantit une URL valide commençant par http ou https.



## Date (AAAA-MM-JJ)

```regex
^\d{4}-(0[1-9]|1[0-2])-(0[1-9]|[12][0-9]|3[01])$
```

Valide les dates au format AAAA-MM-JJ.


## Heure (HH:MM)

```regex
^([01][0-9]|2[0-3]):[0-5][0-9]$
```

Valide les heures au format HH:MM (format 24 heures).


## Code postal (format américain)

```regex
^\d{5}(?:[-\ ]\d{4})?$
```

Valide les codes postaux américains à 5 chiffres avec un trait d’union facultatif et une extension à 4 chiffres.


## Nom d’utilisateur ou d’utilisatrice (caractères alphanumériques et traits de soulignement)

```regex
^[a-zA-Z0-9_]+$
```

Autorise les lettres, les chiffres et les traits de soulignement.


## Code hexadécimal

```regex
^#[0-9a-fA-F]{6}$
```

Valide les codes couleur hexadécimaux à 6 chiffres. Par exemple : #FFFFFF.


## Adresse IP

```regex
^(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})\.(25[0-5]|2[0-4][0-9]|1[0-9][0-9]|[0-9]{2,3})$
```

Valide les adresses IPv4.



## Numéro de sécurité sociale (format américain)

```regex
^\d{3}-\d{2}-\d{4}$
```



## Numéro de carte de crédit

```regex
^(?:4[0-9]{12}(?:[0-9]{3})?|[25][1-7][0-9]{14}$
```

Valide les numéros de téléphone au format (XXX) XXX-XXXX.



## Numéro de téléphone (format américain) :

```regex
^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$
```

Valide les numéros de téléphone au format (XXX) XXX-XXXX.
