---
title: Utilisation de règles pour ajouter un comportement dynamique à un formulaire
description: Les Edge Delivery Services AEM Forms conçus pour des performances optimales vous permettent d’envisager l’avenir de la collecte de données rationalisée et de l’engagement des utilisateurs. Utilisez des règles pour ajouter un comportement dynamique à vos formulaires.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 58042016-e655-446f-a2bf-83f1811525e3
source-git-commit: 61c8d08a21ad81a74e1093838b38f22af94751c3
workflow-type: tm+mt
source-wordcount: '2216'
ht-degree: 0%

---

# Utilisation de règles pour ajouter un comportement dynamique à vos formulaires

L’une des puissantes fonctionnalités de création de formulaires à l’aide d’une feuille de calcul est la possibilité d’utiliser des fonctions de feuille de calcul intégrées pour créer des règles, ce qui vous permet d’afficher ou de masquer de manière conditionnelle les champs de formulaire, d’automatiser les calculs en fonction des entrées de l’utilisateur et de créer une expérience utilisateur plus dynamique.

Cet article vous guide tout au long de l’utilisation de diverses propriétés de bloc de formulaire adaptatif. [`Visible`](#visible-property), [`Visibility Expression`](#visible-expression-property) et [`Value Expression`](#value-expression-property) propriétés avec [fonctions de feuille de calcul](#spreadsheet-functions-for-rules) pour créer des règles efficaces pour vos formulaires. Nous allons également explorer quelques exemples pour illustrer comment ces règles peuvent être mises en oeuvre dans la pratique.

## Comprendre les concepts d’une règle

Les règles sont comme des instructions qui nous disent quoi faire dans différentes situations. Une règle contient généralement les éléments suivants :

* Conditions : ces conditions indiquent les circonstances dans lesquelles la règle s’applique. Considérez-les comme une question à laquelle il faut répondre (oui ou non).

* Actions : ces actions définissent ce qui se passe lorsque la condition est remplie (true) ou non (false).


Par exemple, pour afficher une zone de courrier électronique, lorsqu’une case à cocher est sélectionnée :

* Condition : &quot;Aimez-vous vous abonner à Magazine &amp; Activities ?&quot; est sélectionnée. (Oui ou non ?). Cette condition est définie dans la variable `Visible` de formulaire.
* Action (True) : la boîte de messagerie s’affiche. (Que se passe-t-il si oui). La variable `Visibility Expression`  utilisez la condition définie pour la variable `visible` pour afficher dynamiquement les champs.
* Action (False) : la zone de courrier électronique est masquée. (Que se passe-t-il si non). La variable `Visibility Expression`  utilisez la condition définie pour la variable `Value` pour masquer dynamiquement les champs.

Pour obtenir des instructions détaillées, reportez-vous à la section [afficher/masquer un champ d’email en fonction d’une condition ;](#example-1-conditional-email-field)


## Présentation des propriétés Valeur, Visible, Expression de visibilité et Expression de valeur

### Propriété visible

Imaginez un interrupteur pour votre champ de formulaire. La variable `Visible` est identique à ce commutateur, en contrôlant si le champ est initialement visible sur le formulaire lors de son premier chargement.

* True (comme si l’interrupteur était activé) : le champ s’affiche sur le formulaire.
* False (comme si l’interrupteur était &quot;désactivé&quot;) : le champ est masqué sur le formulaire.

Vous pouvez utiliser la formule de feuille de calcul (y compris la balise = ) pour écrire une formule à l’aide d’une logique de type feuille de calcul afin de déterminer la visibilité du champ. Vous pouvez utiliser les valeurs d’autres champs de votre formulaire dans cette formule. Par exemple, si un utilisateur sélectionne &quot;Individuel&quot; dans un champ de type d’enregistrement, vous pouvez masquer le champ de l’email à l’aide d’une formule qui vérifie cette valeur.

### Propriété d’expression visible (afficher/masquer un champ)

La variable `Visible Expression` vous permet d’utiliser la règle ajoutée à `Visible` pour décider d’afficher ou de masquer le champ en fonction des interactions utilisateur.

Utilisez la variable `=FORMULATEXT("Address of the corresponding Visible property)` pour inclure la formule mentionnée dans la variable `Visible` Propriété sous forme de chaîne à la propriété `Visible Expression` Champ de propriété. Cela est nécessaire pour afficher/masquer dynamiquement les champs d’un formulaire publié.

![Forumaltext](/help/edge/assets/aem-forms-formulatext.png)

### Propriété Value (définition des données initiales)

Imaginez une valeur prédéfinie sur un interrupteur pour la lumière d&#39;une pièce. La variable `Value` est similaire, ce qui détermine l’état initial des données que voit l’utilisateur dans le champ.  Il définit ou récupère les données actives affichées dans le champ de formulaire.

Lorsque le formulaire se charge pour la première fois, la variable `Value` détermine ce que l’utilisateur voit dans le champ avant d’apporter des modifications. Contrairement à `Visible` et `Visible Expression` propriétés qui contrôlent la visibilité, la propriété Value affecte directement les données. Les utilisateurs peuvent modifier cette valeur en saisissant, en sélectionnant des options (menus déroulants) ou en interagissant avec le champ.

Vous pouvez utiliser la formule Excel (y compris la balise = ) pour écrire une formule à l’aide d’une logique semblable à une feuille de calcul afin de déterminer la valeur affichée dans le champ. Vous pouvez utiliser les valeurs d’autres champs de votre formulaire dans cette formule. Vous pouvez par exemple calculer automatiquement une remise en fonction du montant de la commande renseigné dans un autre champ.


### Propriété d’expression de valeur (calculer les valeurs à afficher dans un champ)

Cette propriété permet de contrôler la valeur affichée dans un champ à partir d’une formule, similaire à l’expression visible. Imaginez une calculatrice intégrée au champ.

Utilisez la variable `=FORMULATEXT("Address of the corresponding Value property)` pour inclure la formule mentionnée dans la variable `Value` Propriété sous forme de chaîne à la propriété `Value Expression` Champ de propriété. Cela est nécessaire pour calculer et afficher dynamiquement les valeurs calculées dans un formulaire publié.

![Forumaltext](/help/edge/assets/aem-forms-formulatext-value.png)

Voici une analogie pour consolider ces concepts :

* Visible : imaginez un formulaire comme une maison. La propriété &quot;Visible&quot; est semblable à l’interrupteur pour chaque pièce (champ). Vous décidez si la pièce est initialement éclairée (visible) ou sombre (cachée) lorsque quelqu’un entre dans la maison (ouvre le formulaire).
* Expression visible : C&#39;est comme un interrupteur de capteur de mouvement. La pièce (champ) peut être initialement sombre (cachée), mais une formule (capteur de mouvement) peut l’activer (afficher le champ) si quelqu’un passe (modifie la valeur dans un autre champ).
* Valeur : il s’agit d’un interrupteur à espacement prédéfini pour la lumière (données initiales dans le champ). Les utilisateurs peuvent ensuite régler la luminosité (modifier la valeur).
* Expression de valeur : il s’agit d’une calculatrice fantaisiste intégrée à la balise de prix d’un produit de la maison (formulaire). La balise price (champ) indique le prix final en fonction d’une formule (par exemple, l’ajout de la taxe au prix de base) qui utilise d’autres informations comme le prix de base (valeur d’un autre champ).

En combinant ces propriétés à [fonctions de feuille de calcul](#spreadsheet-functions-for-rules), vous pouvez créer un large éventail de comportements dynamiques dans vos formulaires.

## Fonctions de feuille de calcul pour les règles

Le bloc Forms adaptatif prend en charge diverses fonctions de feuille de calcul qui peuvent être utilisées pour créer des règles. Voici les fonctions disponibles prêtes à l’emploi :

### Fonctions logiques

* [NOT()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018452_715980110): inverse l’état logique (TRUE devient FALSE et vice versa).
* [AND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#AND): renvoie TRUE uniquement si toutes les conditions spécifiées sont TRUE.
* [OR()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#OR): renvoie TRUE si au moins l’une des conditions spécifiées est TRUE.

### Fonctions conditionnelles

* [IF()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018446_715980110): évalue une condition et renvoie une valeur spécifique si TRUE, et une autre valeur si FALSE.

### Fonctions mathématiques

* [SUM()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#SUM): ajoute des valeurs d’une plage de cellules spécifiée.
* [ROUND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#ROUND): arrondit un nombre à un nombre spécifié de décimales.
* [MIN()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#MIN): renvoie la valeur la plus petite d’une plage de cellules spécifiée.

## Créer une règle

Examinons quelques exemples pratiques pour illustrer l’utilisation des règles pour améliorer vos formulaires :

## Exemple 1 : champ de courrier électronique conditionnel

Cet exemple illustre le fonctionnement de la case à cocher en tant que condition. Lorsqu’elle est sélectionnée (la condition est vraie), la zone de courrier électronique s’affiche (action pour vraie). Si elle n’est pas sélectionnée (la condition est false), la zone de courrier électronique reste masquée (action pour false).

Créez un formulaire avec une case à cocher et une case d’email, comme illustré ci-dessous :

![Formulaire de courrier électronique conditionnel](/help/edge/assets/aem-forms-conditional-email-form.png)


Voici comment utiliser une règle pour afficher le champ d’email lors de la sélection d’une case à cocher :

1. Définissez la variable `Value` de la case à cocher `TRUE`.
1. Définissez la variable `Checked` de la case à cocher `FALSE`. Ainsi, la case à cocher n’est pas cochée par défaut.
1. Définissez la variable `Visible` de la propriété du champ email à `=[address of Checked property of the checkbox field] = true()`. Par exemple `=Q11=TRUE()`. La formule est évaluée si la case à cocher est sélectionnée ou non. Si la case est cochée, la formule renvoie TRUE. Si la case à cocher n’est pas sélectionnée, la formule renvoie FALSE.



   La variable `TRUE()` , renvoie la valeur logique lorsque vous la définissez sur le point `Checked` , si la propriété `checked = false` elle renvoie false. If `checked=true`, elle renvoie `true`. Par défaut, le champ de l&#39;email est masqué.


1. Définissez la variable `Visible Expression` de la case à cocher `=FORMULATEXT ((address of Visible property of the checkbox field))`. Par exemple, `=FORMULATEXT((G12))`. La fonction FORMULATEXT() utilise une formule comme entrée et renvoie la formule elle-même sous forme de chaîne de texte. Elle permet d’utiliser la formule dans le formulaire.

   ![Champ de courrier électronique conditionnel](/help/edge/assets/aem-forms-visible-expression-formula-text.png)

1. Prévisualisez et publiez votre formulaire. Désormais, lorsque vous cochez la case, le champ de l’email s’affiche, tandis que la désélection masque le champ, offrant ainsi une expérience utilisateur dynamique.

   ![Email conditionnel](/help/edge/assets/aem-forms-coditional-email.gif)


## Exemple 2 : calcul automatique

Cet exemple montre comment un formulaire calcule automatiquement le coût estimé du voyage lors de la sélection des dates de voyage dans un formulaire.

Créez un formulaire avec un champ de date, un budget de la salle, des champs Coût estimé du voyage comme affichés ci-dessous et une zone d&#39;email, comme illustré ci-dessous :

![Formulaire de courrier électronique conditionnel](/help/edge/assets/aem-forms-automatic-calculations-form.png)

Voici comment utiliser un calcul automatique pour afficher le coût estimé du voyage :

1. Définissez la variable `Value` de la propriété `amount` champ à `=F6*DAYS(F3,F2)`. Cette formule calcule le nombre de jours à partir de `Start Date`  et `End Date`, nombre de jours avec le budget de la chambre et affiche le résultat en `Estimated Trip Cost` champ .

1. Définissez la variable `Value Expression` de la propriété `Estimated Trip Cost` champ à `=FORMULATEXT ((address of value property of the amount field))`. Par exemple, `=FORMULATEXT(F7)`. La fonction FORMULATEXT() utilise une formule comme entrée et renvoie la formule elle-même sous forme de chaîne de texte. Elle permet d’utiliser la formule dans le formulaire.

1. Prévisualisez et publiez votre formulaire. Maintenant, lors de la spécification d’une `Start Date`, `End Date`et Budget de la chambre. La variable `Estimated Trip Cost` est calculé automatiquement.

## Exemples de fonctions de feuille de calcul


Voici quelques exemples des fonctions de feuille de calcul les plus courantes :

**Fonctions logiques :**

* **NOT() :** Annule l’état logique (TRUE devient FALSE et vice versa).

  Exemple : masquer un champ &quot;Confirmer l’email&quot; si le champ de l’email n’est pas renseigné.

   1. Définissez la variable `Visible` de la propriété du champ &quot;Confirmer l’email&quot; à `=NOT(if('address of email field'=""))`.

      ![AEM Forms - Masquer le champ Confirmer l’email](/help/edge/assets/aem-forms-not-function-hide-email-field.png)


   1. Définissez l’expression visible du champ &quot;Confirmer l’email&quot; sur `=FORMULATEXT ((address of visible property of the Confirm Email field))`

      ![Formule d’expression visible AEM Forms](/help/edge/assets/aem-forms-visible-expression-formula-text.png)


* AND() : renvoie TRUE uniquement si toutes les conditions spécifiées sont TRUE.

   * Exemple : activer un bouton &quot;Envoyer&quot; uniquement si tous les champs obligatoires sont renseignés.

   1. Définissez la variable `Visible` du bouton &quot;soumettre&quot; à :



      ```JavaScript
      =AND(NOT(address of `value` property of the `name` field = ""), NOT(address of `value` property of the `email` field = ""), NOT(address of `value` property of the `phone` field))
      ```

      par exemple,

      ```JavaScript
      =AND(NOT(F9=""), NOT(F12=""), NOT(F10=""))
      ```

   1. Définissez l’expression visible du champ &quot;Confirmer l’email&quot; sur

      ```JavaScript
      =FORMULATEXT ((address of visible property of the Confirm Email field))
      ```

      par exemple,

      ```JavaScript
      =FORMULATEXT(G14)
      ```

      Cette formule affiche le bouton &quot;Envoyer&quot; (TRUE) uniquement si tous les champs (nom, email, téléphone) sont renseignés (NOT()) renvoie TRUE pour chacun), sinon elle masque le bouton (AND(multiple FALSES) = FALSE).

* OR() : renvoie TRUE si au moins l’une des conditions spécifiées est TRUE.

   * Exemple : application d’une remise si un utilisateur saisit l’un des codes de coupon de remise applicables.

   1. Définissez la variable `Visible` de la propriété du champ &quot;montant final&quot; sur :


  ```JavaScript
     =IF(OR(F14="BlackFridaySale", F14="NewYearDiscount"), (F6*DAYS(F3,F2)* 0.7) , (F6*DAYS(F3,F2)))
  ```

   1. Définissez l’expression de valeur du champ &quot;Confirmer l’email&quot; sur

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      par exemple,

      ```JavaScript
      =FORMULATEXT(F7)
      ```

      Cette formule calcule une remise de 30 %, si l’utilisateur saisit un code de coupon (couponCode = &quot;NewYearDiscount&quot;) OU (couponCode = &quot;BlackFridaySale&quot;), sinon elle définit la remise sur 0.

**Fonctions de texte :**

* IF() : évalue une condition et renvoie une valeur spécifique si TRUE, et une autre valeur si FALSE.

   * Exemple : affichage d’un message personnalisé en fonction d’une catégorie de produits sélectionnée.

   1. Définissez la variable `Value` de la propriété `message` champ à `Only upto 7 kg check-in lagguage is allowed!`:

   1. Définissez la variable `Visible` de la propriété `message` à :


      ```JavaScript
      =if(address of value property of chosen product category ="Economy", TRUE(), FALSE())
      ```

      par exemple,

      ```JavaScript
      =if(F5="Economy", TRUE(), FALSE())
      ```

   1. Définissez l’expression de valeur de la variable `message` champ à

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      par exemple,

      ```JavaScript
      =FORMULATEXT(G15)
      ```

      Cette formule affiche le message &quot;Seuls les bagages d’enregistrement de 7 kg maximum sont autorisés&quot;. si la classe choisie est &quot;Economie&quot;, sinon le champ du message reste vide.

**Fonctions mathématiques :**

* SUM() : ajoute des valeurs d’une plage de cellules spécifiée.

  Exemple : Calcul du coût total des articles d’un panier.

  Dans l&#39;expression de la valeur du champ &quot;coût total&quot; : SUM(price * quantity)

  Cette formule suppose que vous disposez de champs distincts pour le &quot;prix&quot; et la &quot;quantité&quot; de chaque élément. Il les multiplie et utilise SUM() pour additionner le coût total de tous les articles du panier.

* ROUND() : arrondit un nombre à un nombre spécifié de décimales.

  Exemple : arrondir un montant de remise calculé à deux décimales.

  Dans l&#39;expression de la valeur du champ &quot;Montant de la remise&quot; (en supposant qu&#39;une remise soit calculée ailleurs) : ROUND(réduction, 2)

  Cette formule arrondit la valeur de remise à deux décimales.

* MIN() : renvoie la plus petite valeur d’une plage de cellules spécifiée.

  Exemple : trouver l’âge minimum requis pour un formulaire d’inscription en fonction d’un pays sélectionné.

  Dans l&#39;expression de la valeur d&#39;un champ &quot;âge minimum&quot; : MIN(ageLimits[&quot;US&quot;], ageLimits[&quot;UK&quot;], ageLimits[&quot;France&quot;])

  Cette formule suppose que vous ayez un tableau nommé &quot;ageLimits&quot; qui stocke les exigences d’âge minimum pour différents pays. Il utilise MIN() pour trouver la plus petite valeur parmi celles-ci.


En outre, le bloc de Forms adaptatif vous permet de prendre en charge entièrement vos formulaires en créant des [fonctions personnalisées](#creating-custom-functions). Les fonctions personnalisées vous permettent de définir vos propres règles et logiques, ce qui vous permet de contrôler entièrement le comportement de vos formulaires.


## Création et déploiement de fonctions personnalisées

Le bloc Forms adaptatif prêt à l’emploi fournit des mises en oeuvre pour de nombreuses [fonctions de feuille de calcul courantes](#spreadsheet-functions-for-rules). Cependant, pour un contrôle plus précis sur vos formulaires, vous pouvez utiliser n’importe quelle fonction prête à l’emploi disponible dans Microsoft® Excel ou Google Sheets dans vos blocs Adaptive Forms. Le bloc Forms adaptatif ne contient pas d’implémentation pour toutes les fonctions prêtes à l’emploi disponibles dans Microsoft® Excel ou Google Sheets. Si vous avez besoin de l’une de ces fonctions, vous pouvez développer une fonction personnalisée avec une syntaxe similaire afin d’obtenir les fonctionnalités fournies par Microsoft® Excel ou Google Sheets. Par exemple, vous pouvez implémenter la variable [Fonction Year() de Microsoft® Excel](https://support.microsoft.com/en-us/office/calculate-age-113d599f-5fea-448f-a4c3-268927911b37#) pour calculer l’âge à partir de la date de naissance.


### Création d’une fonction personnalisée

Les fonctions personnalisées résident dans la variable `[Adaptive form block]/functions.js` fichier . Le processus de création comprend généralement les étapes suivantes :

* Déclaration de fonction : définissez le nom de la fonction et ses paramètres (entrées qu’elle accepte).
* Mise en oeuvre logique : écrivez le code qui décrit les calculs ou les manipulations spécifiques effectués par la fonction.
* Exportation de fonction : rendez la fonction accessible dans vos règles en l’exportant à partir du fichier approprié.

### Exemple : fonction Year

Cet exemple illustre deux fonctions personnalisées qui imitent la fonction YEAR() de Microsoft® Excel pour calculer l’âge :


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

### Utilisation d’une fonction personnalisée dans votre formulaire

Pour utiliser la fonction personnalisée dans votre formulaire :

1. **Ajout de la fonction**: incluez votre fonction personnalisée dans la variable `[Adaptive form block]/functions.js` fichier . N’oubliez pas de l’ajouter à l’instruction d’exportation dans le fichier .
1. **Déploiement du fichier**: Déployer la mise à jour `functions.js` dans votre projet GitHub et vérifiez la création.
1. **Utilisation des fonctions**: accédez à la fonction de la feuille de calcul de votre formulaire à l’aide de la fonction `Value`, `Value Expression`, `Visible`, ou `Visible Expression` propriétés, comme toute autre fonction de feuille de calcul compatible avec la prêtes à l’emploi.
1. **Aperçu du formulaire**: utilisez AEM Sidekick pour prévisualiser votre formulaire avec la fonction nouvellement mise en oeuvre.

