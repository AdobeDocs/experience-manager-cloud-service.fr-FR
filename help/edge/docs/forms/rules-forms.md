---
title: Utiliser les règles pour ajouter un comportement dynamique à un formulaire
description: Les Edge Delivery Services d’AEM Forms sont conçus pour des performances élevées, ce qui vous permet d’envisager l’avenir de la collecte de données rationalisée et de l’engagement des utilisateurs. Utiliser les règles pour ajouter un comportement dynamique à vos formulaires.
feature: Edge Delivery Services
exl-id: 58042016-e655-446f-a2bf-83f1811525e3
role: Admin, Architect, Developer
source-git-commit: 4a8153ffbdbc4da401089ca0a6ef608dc2c53b22
workflow-type: tm+mt
source-wordcount: '2218'
ht-degree: 98%

---

# Utiliser les règles pour ajouter un comportement dynamique à vos formulaires

La possibilité d’utiliser des fonctions de feuille de calcul intégrées pour créer des règles constitue une fonctionnalité puissante. Vous pouvez ainsi afficher ou masquer de manière conditionnelle les champs de formulaire, automatiser les calculs en fonction des entrées de la personne et créer une expérience client plus dynamique.

Cet article vous guide dans l’utilisation des diverses propriétés du bloc de formulaire adaptatif, notamment les propriétés [`Visible`](#visible-property), [`Visibility Expression`](#visible-expression-property) et [`Value Expression`](#value-expression-property), avec les [fonctions de feuille de calcul](#spreadsheet-functions-for-rules), afin de créer des règles efficaces pour vos formulaires. Nous allons également explorer quelques exemples pour illustrer comment ces règles peuvent être mises en œuvre dans la pratique.

## Comprendre les concepts d’une règle

Les règles sont comme des instructions qui nous disent quoi faire dans différentes situations. Une règle contient généralement les éléments suivants :

* Conditions : indiquent les circonstances dans lesquelles la règle s’applique. Considérez-les comme une question à laquelle il faut répondre (oui ou non).

* Actions : définissent ce qui se passe lorsque la condition est remplie (true) ou non (false).


Par exemple, pour afficher une zone d’e-mail, lorsqu’une case à cocher est sélectionnée :

* Condition : la case Aimez-vous vous abonner à Magazine et Activités ? est cochée. (Oui ou non ?). Cette condition est définie dans la propriété `Visible` du formulaire.
* Action (True) : la zone d’e-mail s’affiche. (Que se passe-t-il si Oui ?). L’`Visibility Expression` utilise la condition définie pour la propriété `visible` afin d’afficher dynamiquement les champs.
* Action (False) : la zone d’e-mail est masquée. (Que se passe-t-il si Non) ? L’`Visibility Expression` utilise la condition définie pour la `Value` pour masquer dynamiquement les champs.

Pour obtenir des instructions détaillées, reportez-vous à la section [Afficher/masquer un champ d’e-mail en fonction d’une condition](#example-1-conditional-email-field)


## Comprendre les propriétés Valeur, Visible, Expression de visibilité et Expression de valeur

### Propriété Visible

Imaginez un interrupteur pour votre champ de formulaire. La propriété `Visible` est identique à ce commutateur, en ce qu’elle contrôle si le champ est initialement visible sur le formulaire lors de son premier chargement.

* True (comme si l’interrupteur était activé) : le champ s’affiche sur le formulaire.
* False (comme si l’interrupteur était désactivé) : le champ est masqué sur le formulaire.

Vous pouvez utiliser la formule de feuille de calcul (y compris la balise = ) pour écrire une formule à l’aide d’une logique de type feuille de calcul afin de déterminer la visibilité du champ. Vous pouvez utiliser les valeurs d’autres champs de votre formulaire dans cette formule. Par exemple, si une personne sélectionne « Individu » dans un champ de type d’enregistrement, vous pouvez masquer le champ de l’e-mail à l’aide d’une formule qui vérifie cette valeur.

### Propriété Expression visible (afficher/masquer un champ)

La propriété `Visible Expression` vous permet d’utiliser la règle ajoutée à la propriété `Visible` pour décider d’afficher ou de masquer le champ en fonction des interactions utilisateur.

Utilisez la propriété `=FORMULATEXT("Address of the corresponding Visible property)` pour inclure la formule mentionnée dans la propriété `Visible` sous forme de chaîne au champ de propriété `Visible Expression`. Cette étape est nécessaire pour afficher/masquer dynamiquement les champs d’un formulaire publié.

![Forumaltext](/help/edge/assets/aem-forms-formulatext.png)

### Propriété Valeur (définir les données initiales)

Imaginez une valeur prédéfinie sur un interrupteur pour allumer une pièce. La propriété `Value` est similaire, en ce qu’elle détermine l’état initial des données qui s’affichent dans le champ.  Elle définit ou récupère les données actuelles affichées dans le champ de formulaire.

Lorsque le formulaire se charge pour la première fois, la propriété `Value` détermine ce que l’utilisateur ou l’utilisatrice voit dans le champ avant que des modifications soient apportées. Contrairement aux propriétés `Visible` et `Visible Expression` qui contrôlent la visibilité, la propriété Valeur affecte directement les données. Les utilisateurs et utilisatrices peuvent modifier cette valeur en saisissant et en sélectionnant des options (menus déroulants) ou en interagissant avec le champ.

Vous pouvez utiliser la formule Excel (y compris la balise = ) pour écrire une formule à l’aide d’une logique semblable à une feuille de calcul afin de déterminer la valeur affichée dans le champ. Vous pouvez utiliser les valeurs d’autres champs de votre formulaire dans cette formule. Vous pouvez par exemple calculer automatiquement une remise en fonction du montant de la commande renseigné dans un autre champ.


### Propriété Expression de valeur (calculer les valeurs à afficher dans un champ)

Cette propriété permet de contrôler la valeur affichée dans un champ à partir d’une formule similaire à l’expression visible. Imaginez une calculatrice intégrée au champ.

Utilisez la variable `=FORMULATEXT("Address of the corresponding Value property)` pour inclure la formule mentionnée dans la propriété `Value` sous forme de chaîne au champ de la propriété `Value Expression`. Cela est nécessaire pour calculer et afficher dynamiquement les valeurs calculées dans un formulaire publié.

![Forumaltext](/help/edge/assets/aem-forms-formulatext-value.png)

Voici une analogie pour consolider ces concepts :

* Visible : imaginez un formulaire comme une maison. La propriété « Visible » est semblable à l’interrupteur pour chaque pièce (champ). Vous décidez si la pièce est initialement éclairée (visible) ou éteinte (masquée) lorsque quelqu’un entre dans la maison (ouvre le formulaire).
* Expression visible : elle fonctionne comme un interrupteur avec détecteur de mouvement. La pièce (champ) peut être initialement éteinte (masquée), mais une formule (détecteur de mouvement) peut l’allumer (afficher le champ) si quelqu’un entre (modifie la valeur dans un autre champ).
* Valeur : elle fonctionne comme un interrupteur variateur de lumière prédéfini (données initiales dans le champ). Les utilisateurs et utilisatrices peuvent alors régler la luminosité (modifier la valeur).
* Expression de valeur : elle fonctionne comme une calculatrice fantaisiste intégrée à la balise de prix d’un produit de la maison (formulaire). La balise de prix (champ) indique le prix final en fonction d’une formule (par exemple, l’ajout de la taxe au prix de base) qui utilise d’autres informations comme le prix de base (valeur d’un autre champ).

En combinant ces propriétés à des [fonctions de feuille de calcul](#spreadsheet-functions-for-rules), vous pouvez créer un large éventail de comportements dynamiques dans vos formulaires.

## Fonctions de feuille de calcul pour les règles

Le bloc de formulaires adaptatifs prend en charge diverses fonctions de feuille de calcul qui peuvent être utilisées pour créer des règles. Voici les fonctions disponibles prêtes à l’emploi :

### Fonctions logiques

* [NOT()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018452_715980110) : inverse l’état logique (TRUE devient FALSE et vice versa).
* [AND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#AND) : renvoie TRUE uniquement si toutes les conditions spécifiées sont TRUE.
* [OR()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#OR) : renvoie TRUE si au moins l’une des conditions spécifiées est TRUE.

### Fonctions conditionnelles

* [IF()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018446_715980110) : évalue une condition et renvoie une valeur spécifique si TRUE, et une autre valeur si FALSE.

### Fonctions mathématiques

* [SUM()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#SUM) : ajoute des valeurs d’une plage de cellules spécifiée.
* [ROUND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#ROUND) : arrondit un nombre à un nombre spécifié de décimales.
* [MIN()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#MIN) : renvoie la valeur la plus petite d’une plage de cellules spécifiée.

## Créer une règle

Examinons quelques exemples pratiques pour illustrer l’utilisation des règles afin d’améliorer vos formulaires :

## Exemple 1 : champ d’e-mail conditionnel

Cet exemple illustre le fonctionnement de la case à cocher en tant que condition. Lorsqu’elle est sélectionnée (la condition est true), la zone d’e-mail s’affiche (action pour true). Si elle n’est pas sélectionnée (la condition est false), la zone d’e-mail reste masquée (action pour false).

Créez un formulaire avec une case à cocher et une zone d’e-mail comme illustré ci-dessous :

![Formulaire d’e-mail conditionnel](/help/edge/assets/aem-forms-conditional-email-form.png)


Voici comment utiliser une règle pour afficher le champ d’e-mail lors de la sélection d’une case à cocher :

1. Définissez la propriété `Value` du champ de case à cocher sur `TRUE`.
1. Définissez la propriété `Checked` du champ de case à cocher sur `FALSE`. Ainsi, la case à cocher n’est pas cochée par défaut.
1. Définissez la propriété `Visible` du champ d’e-mail sur `=[address of Checked property of the checkbox field] = true()`. Par exemple `=Q11=TRUE()`. La formule évalue si la case à cocher est sélectionnée ou non. Si la case est cochée, la formule renvoie TRUE. Dans le cas contraire, la formule renvoie FALSE.



   La fonction `TRUE()` renvoie la valeur logique lorsque vous la définissez afin qu’elle pointe sur la propriété `Checked`, s’il s’agit de `checked = false`, elle renvoie false. Si `checked=true`, elle renvoie `true`. Par défaut, cela garantit que le champ de l’e-mail est masqué.


1. Définissez la propriété `Visible Expression` du champ de case à cocher sur `=FORMULATEXT ((address of Visible property of the checkbox field))`. Par exemple, `=FORMULATEXT((G12))`. La fonction FORMULATEXT() utilise une formule comme entrée et renvoie la formule elle-même sous forme de chaîne de texte. Elle permet d’utiliser la formule dans le formulaire.

   ![Champ d’e-mail conditionnel](/help/edge/assets/aem-forms-visible-expression-formula-text.png)

1. Prévisualisez et publiez votre formulaire. Désormais, lorsque vous cochez la case, le champ de l’e-mail s’affiche, tandis que si vous la décochez, le champ est masqué, offrant ainsi une expérience utilisateur dynamique.

   ![E-mail conditionnel](/help/edge/assets/aem-forms-coditional-email.gif)


## Exemple 2 : calcul automatique

Cet exemple montre comment un formulaire calcule automatiquement le coût estimé du voyage lors de la sélection des dates de voyage dans un formulaire.

Créez un formulaire avec des champs de date, de budget de salle, de Coût estimé du voyage, tels que ceux affichés ci-dessous et avec une zone d’e-mail, comme illustré dans l’image ci-dessous :

![Formulaire d’e-mail conditionnel](/help/edge/assets/aem-forms-automatic-calculations-form.png)

Procédez comme suit pour utiliser un calcul automatique pour afficher le coût estimé du voyage :

1. Définissez la propriété `Value` du champ `amount` sur `=F6*DAYS(F3,F2)`. Cette formule calcule le nombre de jours entre la `Start Date` et la `End Date`, multiplie le nombre de jours par le budget de la salle et affiche le résultat dans le champ `Estimated Trip Cost`.

1. Définissez la propriété `Value Expression` du champ `Estimated Trip Cost` sur `=FORMULATEXT ((address of value property of the amount field))`. Par exemple, `=FORMULATEXT(F7)`. La fonction FORMULATEXT() utilise une formule comme entrée et renvoie la formule elle-même sous forme de chaîne de texte. Elle permet d’utiliser la formule dans le formulaire.

1. Prévisualisez et publiez votre formulaire. Maintenant, spécifiez une `Start Date`, une `End Date` et le budget de la salle. Le `Estimated Trip Cost` est calculé automatiquement.

## Exemples de fonctions de feuille de calcul


Voici quelques exemples des fonctions de feuille de calcul les plus courantes :

**Fonctions logiques :**

* **NOT() :** inverse l’état logique (TRUE devient FALSE et vice versa).

  Exemple : masquer un champ « Confirmer l’e-mail » si le champ de l’e-mail n’est pas renseigné.

   1. Définissez la propriété `Visible` du champ « Confirmer l’e-mail » sur `=NOT(if('address of email field'=""))`.

      ![AEM Forms - Masquer le champ Confirmer l’e-mail](/help/edge/assets/aem-forms-not-function-hide-email-field.png)


   1. Définir l’expression visible du champ « Confirmer l’e-mail » sur `=FORMULATEXT ((address of visible property of the Confirm Email field))`

      ![AEM Forms - Formule d’expression visible](/help/edge/assets/aem-forms-visible-expression-formula-text.png)


* AND() : renvoie TRUE uniquement si toutes les conditions spécifiées valent TRUE.

   * Exemple : activer un bouton « Envoyer » uniquement si tous les champs obligatoires sont renseignés.

   1. Définissez la propriété `Visible` du bouton « Envoyer » sur :



      ```JavaScript
      =AND(NOT(address of `value` property of the `name` field = ""), NOT(address of `value` property of the `email` field = ""), NOT(address of `value` property of the `phone` field))
      ```

      Par exemple,

      ```JavaScript
      =AND(NOT(F9=""), NOT(F12=""), NOT(F10=""))
      ```

   1. Définir l’expression visible du champ « Confirmer l’e-mail » sur

      ```JavaScript
      =FORMULATEXT ((address of visible property of the Confirm Email field))
      ```

      Par exemple,

      ```JavaScript
      =FORMULATEXT(G14)
      ```

      Cette formule affiche le bouton « Envoyer » (TRUE) uniquement si tous les champs (nom, e-mail, téléphone) sont renseignés (NOT(()) renvoie TRUE pour chacun), sinon elle masque le bouton (AND(multiple FALSES) = FALSE).

* OR() : renvoie TRUE si au moins l’une des conditions spécifiées vaut TRUE.

   * Exemple : appliquer une remise si une personne saisit l’un des codes de coupon de remise applicables.

   1. Définissez la propriété `Visible` du champ « montant final » sur :


  ```JavaScript
     =IF(OR(F14="BlackFridaySale", F14="NewYearDiscount"), (F6*DAYS(F3,F2)* 0.7) , (F6*DAYS(F3,F2)))
  ```

   1. Définir l’expression de valeur du champ « Confirmer l’e-mail » sur

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      Par exemple,

      ```JavaScript
      =FORMULATEXT(F7)
      ```

      Cette formule calcule une remise de 30 %, si la personne saisit un code de coupon (couponCode = &quot;NewYearDiscount&quot;) OU (couponCode = &quot;BlackFridaySale&quot;). Autrement, la remise est définie sur 0.

**Fonctions de texte :**

* IF() : évalue une condition et renvoie une valeur spécifique si TRUE, et une autre valeur si FALSE.

   * Exemple : affichage d’un message personnalisé en fonction d’une catégorie de produits sélectionnée.

   1. Définissez la propriété `Value` du champ `message` sur `Only upto 7 kg check-in lagguage is allowed!` :

   1. Définissez la propriété `Visible` du champ `message` sur :


      ```JavaScript
      =if(address of value property of chosen product category ="Economy", TRUE(), FALSE())
      ```

      Par exemple,

      ```JavaScript
      =if(F5="Economy", TRUE(), FALSE())
      ```

   1. Définissez l’expression de valeur du champ `message` sur

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      Par exemple,

      ```JavaScript
      =FORMULATEXT(G15)
      ```

      Cette formule affiche le message « Les bagages enregistrés ne doivent pas excéder 7 kg » si la classe choisie est Économie, sinon le champ du message reste vide.

**Fonctions mathématiques :**

* SUM() : ajoute des valeurs d’une plage de cellules spécifiée.

  Exemple : calcul du coût total des articles d’un panier.

  Dans l’expression de la valeur du champ Coût total :
SUM(price * quantity)

  Cette formule suppose que vous disposiez de champs distincts pour le « prix » et la « quantité » de chaque élément. Elle les multiplie et utilise SUM() pour additionner le coût total de tous les articles du panier.

* ROUND() : arrondit un nombre à un nombre spécifié de décimales.

  Exemple : arrondissement d’un montant de remise calculé à deux décimales.

  Dans l’expression de la valeur du champ Montant de la remise (en supposant qu’une remise soit calculée ailleurs) : 
ROUND(discount, 2)

  Cette formule arrondit la valeur de remise à deux décimales.

* MIN() : renvoie la plus petite valeur d’une plage de cellules spécifiée.

  Exemple : recherche de l’âge minimum requis pour un formulaire d’inscription en fonction d’un pays sélectionné.

  Dans l’expression de valeur d’un champ Âge minimum : MIN(ageLimits[&quot;US&quot;], ageLimits[&quot;UK&quot;], ageLimits[&quot;France&quot;])

  Cette formule suppose que vous ayez un tableau nommé « ageLimits » qui stocke les exigences d’âge minimum pour différents pays. Il utilise MIN() pour trouver la plus petite valeur parmi celles-ci.


En outre, le bloc de formulaires adaptatifs vous permet de prendre en charge entièrement vos formulaires en créant des [fonctions personnalisées](#creating-custom-functions). Les fonctions personnalisées vous permettent de définir vos propres règles et logiques, ce qui vous permet de contrôler entièrement le comportement de vos formulaires.


## Créer et déployer des fonctions personnalisées

Le bloc de formulaires adaptatifs prêt à l’emploi fournit des mises en œuvre pour de nombreuses [fonctions de feuille de calcul courantes](#spreadsheet-functions-for-rules). Cependant, pour un contrôle davantage granulaire sur vos formulaires, vous pouvez utiliser n’importe quelle fonction prête à l’emploi disponible dans Microsoft® Excel ou Google Sheets dans vos blocs de formulaires adaptatifs. Le bloc de formulaires adaptatifs ne contient pas de mise en œuvre pour toutes les fonctions prêtes à l’emploi disponibles dans Microsoft® Excel ou Google Sheets. Si vous avez besoin de l’une de ces fonctions, vous pouvez développer une fonction personnalisée avec une syntaxe similaire afin d’obtenir les fonctionnalités fournies par Microsoft® Excel ou Google Sheets. Par exemple, vous pouvez mettre en œuvre la [fonction Year() de Microsoft® Excel](https://support.microsoft.com/fr-fr/office/calculate-age-113d599f-5fea-448f-a4c3-268927911b37#) pour calculer l’âge à partir de la date de naissance.


### Créer une fonction personnalisée

Les fonctions personnalisées résident dans le fichier `[Adaptive form block]/functions.js`. Le processus de création comprend généralement les étapes suivantes :

* Déclaration de fonction : définissez le nom de la fonction et ses paramètres (entrées qu’elle accepte).
* Mise en œuvre logique : écrivez le code qui décrit les calculs ou les manipulations spécifiques effectués par la fonction.
* Export de fonction : rendez la fonction accessible dans vos règles en l’exportant à partir du fichier approprié.

### Exemple : fonction Year

Cet exemple illustre deux fonctions personnalisées qui imitent la fonction YEAR() de Microsoft® Excel pour calculer l’âge :


```JavaScript
/**
 * Get the current date and time
 * @name now
 * @returns {Date} The current date and time as a Date object
 */
function now() {
  const today = new Date();
  return today;
}

/**
 * Get the year from a Date object
 * @name year
 * @param {Date} date The date object
 * @throws {TypeError} If the input is not a Date object
 * @returns {number} The year as a number
 */
function year(date) {
  let inputDate = new Date(date)

  if (!(inputDate instanceof Date)) {
    throw new TypeError("Input must be a Date object");
  }

  const year = inputDate.getFullYear();

  return year;
}

// Make the function accessible for use in rules
export { now, year };
```

### Utiliser une fonction personnalisée dans votre formulaire

Pour utiliser la fonction personnalisée dans votre formulaire, procédez comme suit :

1. **Ajouter la fonction** : incluez votre fonction personnalisée dans le fichier `[Adaptive form block]/functions.js`. N’oubliez pas de l’ajouter à l’instruction d’export dans le fichier.
1. **Déployer le fichier** : déployez le fichier `functions.js` mis à jour dans votre projet GitHub et vérifiez la création.
1. **Utilisation des fonctions** : accédez à la fonction de la feuille de calcul de votre formulaire à l’aide des propriétés `Value`, `Value Expression`, `Visible` ou `Visible Expression`, comme toute autre fonction prête à l’emploi prise en charge.
1. **Prévisualiser le formulaire** : utilisez AEM Sidekick pour prévisualiser votre formulaire avec la fonction nouvellement mise en œuvre.

