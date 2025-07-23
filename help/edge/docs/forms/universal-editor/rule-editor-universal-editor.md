---
title: Comment utiliser l’éditeur de règles pour appliquer des règles aux champs de formulaire, ce qui permet un comportement dynamique et une logique complexe pour les formulaires créés avec la création WYSIWYG ?
description: L’éditeur de règles dans l’éditeur universel permet d’ajouter un comportement dynamique et de créer une logique complexe dans des formulaires, sans code ni script.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: 9ef4c5638c2275052ce69406f54dda3ea188b0ef
workflow-type: ht
source-wordcount: '2216'
ht-degree: 100%

---


# Présentation de l’Éditeur de règles dans la création WYSIWYG

<span class="preview"> Il s’agit d’une fonctionnalité de version préliminaire accessible par le biais de notre <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=fr#new-features">canal de version préliminaire</a>. </span>


Vous pouvez ajouter un comportement de formulaire dynamique à l’aide de l’éditeur de règles, qui permet de créer des règles. Ces règles permettent une visibilité conditionnelle des champs, automatisent les calculs en fonction des entrées des utilisateurs et utilisatrices et améliorent l’expérience globale d’utilisation. En rationalisant le processus de remplissage des formulaires, l’éditeur de règles garantit à la fois précision et efficacité.

L’éditeur de règles offre une interface visuelle intuitive pour la création et la gestion des règles. Son approche conviviale le rend accessible à tous les utilisateurs et utilisatrices, même ceux et celles qui ne disposent pas d’une vaste expertise technique, ce qui leur permet d’implémenter la logique facilement dans leurs formulaires.

## Présentation d’une règle

Les règles sont des instructions qui guident les utilisateurs et utilisatrices sur les actions à effectuer dans des conditions spécifiques.

* **Condition** : une condition est une vérification ou une règle qui évalue si un élément est vrai ou faux. Elle répond à la question suivante : « Est-ce que cela répond aux exigences ? »

* **Action** : une action est ce qui se produit lorsque la condition est vraie. Il s’agit de la tâche ou du comportement déclenché en fonction de l’évaluation de la condition.

Une règle suit généralement l’un des concepts suivants :

* **Condition-Action** : vérifiez d’abord une condition, puis effectuez une action. Dans l’éditeur de règles, le type de règle `When` applique le concept de `condition-action`.
* **Action-Condition** : effectuez d’abord une action, puis vérifiez une condition. Les types de règle `Set Value Of` et `Validate` dans l’éditeur de règles appliquent le concept de `action-condition`.
* **Action-Condition-Action alternative** : exécutez une action, vérifiez une condition, puis exécutez l’action principale ou une action alternative en fonction de la condition. Par exemple, par défaut, l’action alternative pour `Show` est `Hide`, et pour `Enable`, il s’agit de `Disable`.

Par exemple, une condition peut vérifier si un utilisateur ou une utilisatrice a saisi une certaine valeur dans un champ et l’action peut consister à afficher ou à masquer un champ.
* **Condition** : vérifiez si le revenu est supérieur à 50 000 $.
* **Action** : si la condition est vraie, affichez le champ `Additional Deduction`. Sinon, effectuez l’action alternative : masquer le champ `Additional Deduction`.

Pour obtenir des instructions détaillées, reportez-vous à [Ajouter une règle conditionnelle](#2-add-a-conditional-rule).

## Comment activer l’extension de l’éditeur de règles ?

Dans l’éditeur universel, l’extension Éditeur de règles n’est pas activée par défaut. Pour activer l’extension Éditeur de règles, envoyez-nous un e-mail à l’adresse [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) à partir de votre ID d’e-mail officiel.

Une fois que l’extension de l’éditeur de règles est activée pour votre environnement, l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg) s’affiche dans le coin supérieur droit de l’éditeur.

![Éditeur de règles de l’éditeur universel](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)

Sélectionnez le composant de formulaire pour lequel vous voulez créer une règle, puis cliquez sur l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg). L’interface d’utilisation de l’éditeur de règles s’affiche.

![Interface d’utilisation de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-for-field.png)

Dans cet article, `form object` et `form component` sont utilisés de manière interchangeable.

Vous pouvez maintenant commencer à créer des règles ou une logique métier pour le champ de formulaire sélectionné en utilisant les [types de règles disponibles dans l’éditeur de règles](#available-rule-types-in-rule-editor).

## Présentation de l’interface d’utilisation de l’éditeur de règles

L’Éditeur de règles s’ouvre lorsque vous cliquez sur l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg) :

![Interface d’utilisation de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-interface.png)

<table border="1">
  <thead>
    <tr>
      <th>Composant de l’éditeur de règles</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1. Titre</td>
      <td>Affiche le titre du composant de formulaire et le type de règle sélectionné. Par exemple, « Saisir le salaire brut » est un composant de zone de texte pour lequel le type de règle « Quand » est sélectionné. </td>
    </tr>
    <tr>
      <td>2. Objets de formulaire et fonctions</td>
      <td>L’onglet <b>Objets de formulaire</b> affiche une arborescence hiérarchique de tous les composants contenus dans le formulaire. L’onglet <b>Fonctions</b> comprend un ensemble de fonctions intégrées dans l’éditeur de règles.</td>
    </tr>
    <tr>
      <td>3. Bouton (bascule) des objets de formulaire et des fonctions</td>
      <td>Le bouton bascule permet d’afficher ou de masquer le volet des objets de formulaire et celui des fonctions. </td>
    </tr>
    <tr>
      <td>4. Éditeur de règles visuel</td>
      <td>L’Éditeur de règles visuel est l’interface qui permet de créer des règles pour les composants de formulaire.</td>
    </tr>
    <tr>
      <td>5. Boutons Terminé et Annuler</td>
      <td>Le bouton <b>Terminé</b> permet d’enregistrer une règle. Le bouton <b>Annuler</b> annule tous les changements apportés à une règle et ferme l’éditeur de règles.</td>
    </tr>
  </tbody>
</table>

Les règles existantes sur un composant de formulaire sont répertoriées lorsque vous sélectionnez le composant. Vous pouvez afficher le titre et prévisualiser le résumé de la règle dans l’Éditeur de règles. De plus, vous pouvez modifier l’ordre des règles, modifier des règles, activer/désactiver des règles ou en supprimer.

![afficher les règles disponibles de l’objet de formulaire](/help/edge/docs/forms/assets/rule-editor15.png)

## Types de règle disponibles

L’éditeur de règles fournit un ensemble de types de règle prédéfinis que vous pouvez utiliser pour créer des règles, comme indiqué dans le tableau ci-dessous :

<table border="1">
  <thead>
    <tr>
      <th>Type de règle</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Définir la valeur de</td>
      <td>Définit la valeur d’un composant de formulaire selon que la condition spécifiée est remplie ou non.</td>
    </tr>
    <tr>
      <td>Effacer la valeur de</td>
      <td>Efface la valeur du composant de formulaire spécifié.</td>
    </tr>
    <tr>
      <td>Masquer/Afficher</td>
      <td>Masque ou affiche un composant de formulaire selon qu’une condition est remplie ou non.</td>
    </tr>
    <tr>
      <td>Activer/Désactiver</td>
      <td>Active ou désactive un composant de formulaire selon qu’une condition est remplie ou non.</td>
    </tr>
    <tr>
      <td>Valider</td>
      <td>Vérifie le composant de formulaire en fonction d’une condition et affiche une erreur si la condition n’est pas remplie. </td>
    </tr>
    <tr>
      <td>Quand</td>
      <td>Cela spécifie une condition à évaluer, suivie d’une action à déclencher si la condition est remplie. Suit la construction de règle d’action <i>condition-action-alternative</i> ou la construction de règle <i>condition-action</i>. </td>
    </tr>
    <tr>
      <td>Format</td>
      <td> Modifie la valeur d’affichage du composant de formulaire à l’aide de l’expression donnée lorsque sa valeur change.</td>
    </tr>
    <tr>
      <td>Appel du service</td>
      <td>Appelle un service configuré à l’aide d’API externes, d’un modèle de données de formulaire ou de services web RESTful.</td>
    </tr>
    <tr>
      <td>Définir la propriété</td>
      <td>Définit la valeur d’une propriété du composant de formulaire spécifié en fonction d’une condition.</td>
    </tr>
    <tr>
      <td>Définir la cible d’action</td>
      <td>Définit la cible d’action sur le composant de formulaire spécifié.</td>
    </tr>
    <tr>
      <td>Enregistrer le formulaire</td>
      <td>Cela permet à l’utilisateur ou l’utilisatrice d’enregistrer le formulaire en tant que brouillon à l’aide du composant Brouillons et envois du Portail Formulaires. </td>
    </tr>
    <tr>
      <td>Envoyer le formulaire</td>
      <td>Envoie le formulaire.</td>
    </tr>
    <tr>
      <td>Réinitialiser le formulaire</td>
      <td>Réinitialise le formulaire.</td>
    </tr>
    <tr>
      <td>Ajouter/Supprimer une instance</td>
      <td>Ajoute ou supprime une instance de la ligne de panneau ou de tableau répétable spécifiée.</td>
    </tr>
    <tr>
      <td>Accéder à</td>
      <td>Accède à d’autres formulaires adaptatifs, d’autres ressources, comme des images ou des fragments de document ou une URL externe.</td>
    </tr>
    <tr>
      <td>Distribuer l’événement</td>
      <td>Déclenche des actions spécifiques en fonction de conditions ou d’événements prédéfinis.</td>
    </tr>
    <tr>
      <td>Naviguer dans les panneaux</td>
      <td>Permet de déplacer la cible d’action entre différents panneaux d’un formulaire.</td>
    </tr>
  </tbody>
</table>


Maintenant, découvrons comment [écrire des règles dans l’éditeur de règles](#write-rules).

## Règles d’écriture

Pour comprendre comment écrire des règles dans l’éditeur visuel de règles, prenons l’exemple simple d’un formulaire de calcul des taxes :

![Capture d’écran de l’interface de l’éditeur de règles présentant la création d’une règle conditionnelle avec la logique WHEN-THEN (LORSQUE-ALORS) pour la visibilité des champs de formulaire](/help/edge/docs/forms/assets/rule-editor-1.png)

Dans le formulaire décrit ci-dessus, l’utilisateur ou l’utilisatrice saisit le salaire brut. En fonction de cette entrée, le champ conditionnel s’affiche et la taxe à payer est calculée.

**Champs de formulaire :**
* Salaire brut (saisie utilisateur)
* Déduction supplémentaire (champ conditionnel)
* Revenu imposable (champ calculé)
* Impôt à payer (champ calculé)

**Règle conditionnelle :**
* Condition : salaire brut > 50 000
* Action : afficher le champ Déduction supplémentaire

**Règles de calcul :**

* Revenu imposable = Salaire brut - Déduction supplémentaire (le cas échéant)
* Impôt à payer = Revenu imposable * Taux d’imposition (pour plus de simplicité, supposons un taux fixe de 10 %)

Pour créer des règles :

### 1. Créer un formulaire

Pour créer un formulaire dans l’éditeur universel :

1. Ouvrez un formulaire dans l’éditeur universel pour le modifier.
1. Ajoutez les composants de formulaire suivants :
   * Formulaire de calcul des impôts (Titre)
   * Salaire brut (entrée numérique)
   * Déduction supplémentaire (entrée numérique)
   * Revenu imposable (Entrée numérique)
   * Impôt à payer (Entrée numérique)
   * Envoyer (bouton Envoyer)
1. Masquez le champ de formulaire `Additional Deduction` en ouvrant ses `Properties`.

   ![Capture d’écran d’un formulaire de calcul des impôts avec des champs de saisie pour le salaire brut, la situation de famille et les enfants à charge, présentant la structure du formulaire avant l’application des règles](/help/edge/docs/forms/assets/rule-editor2.png)

### 2. Ajouter une règle conditionnelle pour un champ de formulaire

Une fois que vous avez créé le formulaire, écrivez la première règle pour n’afficher le champ `Additional Deduction` que si le salaire brut dépasse 50 000 $. Pour ajouter une règle conditionnelle, procédez comme suit :

1. Ouvrez un formulaire dans l’éditeur universel pour le modifier, puis sélectionnez le champ **[!UICONTROL Salaire brut]** dans l’arborescence de contenu et sélectionnez ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Vous pouvez également sélectionner le champ **[!UICONTROL Salaire brut]** directement dans le volet **[!UICONTROL Objet Forms]**.
   ![Exemple 1 de l’Éditeur de règles](/help/edge/docs/forms/assets/rule-editor3.png)
L’interface visuelle de l’Éditeur de règles s’affiche.
1. Cliquez sur **[!UICONTROL Créer]** pour créer des règles.
   ![Exemple 2 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor4.png)
Par défaut, le type de règle `Set Value Of` est sélectionné. Bien que vous ne puissiez pas changer ou modifier l’objet sélectionné, vous pouvez utiliser la liste déroulante de règles pour sélectionner un autre type de règle.\
   ![Exemple 3 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor5.png)
1. Ouvrez la liste déroulante des types de règles et sélectionnez le type de règle **[!UICONTROL Lorsque]**.
   ![Exemple 4 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor6.png)
1. Sélectionnez le menu déroulant **[!UICONTROL Sélectionner l’état]** et choisissez **[!UICONTROL est supérieur à]**. Le champ **[!UICONTROL Saisissez un nombre]** s’affiche.
   ![Exemple 5 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor7.png)
1. Saisissez `50000` dans le champ **[!UICONTROL Saisissez un nombre]** de la règle.
   ![Exemple 6 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor8.png)
Vous avez défini la condition comme `When Gross Salary is greater than 50000`. Définissez ensuite l’action à effectuer si cette condition est `True`.
1. Dans l’instruction `Then`, sélectionnez **[!UICONTROL Afficher]** dans le menu déroulant **[!UICONTROL Sélectionner une action]**.
   ![Exemple 7 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor9.png)
1. Faites glisser et déposez le champ **[!UICONTROL Déduction supplémentaire]** de l’onglet Objets de formulaire vers le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**. Vous pouvez également sélectionner le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**, puis le champ **[!UICONTROL Déduction supplémentaire]** dans le menu contextuel, qui répertorie tous les objets de formulaire dans le formulaire.
   ![Exemple 8 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor10.png)
1. Cliquez sur **[!UICONTROL Ajouter une section Else]** pour ajouter une autre condition pour le champ **[!UICONTROL Salaire brut]**, au cas où vous saisissez un salaire inférieur à `50000`.
   ![Exemple 9 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor11.png)
1. Sélectionnez **[!UICONTROL Masquer]** dans le menu déroulant **[!UICONTROL Sélectionner une action]** de l’instruction `Else`.
   ![Exemple 10 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor12.png)
1. Faites glisser et déposez le champ **[!UICONTROL Déduction supplémentaire]** de l’onglet Objets de formulaire vers le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**. Vous pouvez également sélectionner le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**, puis le champ **[!UICONTROL Déduction supplémentaire]** dans le menu contextuel, qui répertorie tous les objets de formulaire dans le formulaire.
   ![Exemple 11 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor13.png)
1. Sélectionnez **[!UICONTROL Terminé]** pour enregistrer la règle.
La règle s’affiche comme suit dans l’éditeur de règles.
   ![Exemple 12 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor14.png)

>[!NOTE]
>
> Vous pouvez également créer une règle Afficher dans le champ Déduction supplémentaire, au lieu d’une règle Lorsque dans le champ Salaire brut pour mettre en œuvre le même comportement.

### &#x200B;3. Ajouter des règles de calcul pour les champs du formulaire

Ensuite, créez une règle pour calculer le `Taxable Income`, qui est la différence entre `Gross Salary` et `Additional Deduction` (le cas échéant). Pour ajouter une règle de calcul dans le champ **[!UICONTROL Revenu imposable]**, procédez comme suit :

1. En mode Création, sélectionnez le champ **[!UICONTROL Revenu imposable]**, puis l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Vous pouvez également sélectionner le champ **[!UICONTROL Revenu imposable]** directement à partir du volet **[!UICONTROL Objet Forms]**.
1. Sélectionnez ensuite **[!UICONTROL Créer]** pour créer la règle.
   ![Exemple 13 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor16.png)
1. Choisissez **[!UICONTROL Sélectionner l’option]** et sélectionnez **[!UICONTROL Expression mathématique]**. Un champ permettant de saisir l’expression mathématique s’ouvre.
   ![Exemple 14 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor17.png)

1. Dans le champ de l’expression mathématique :

   * Sélectionnez ou glissez-déposez, depuis l’onglet Objets de formulaire, le champ **[!UICONTROL Salaire brut]** dans le premier champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.

   * Sélectionnez **[!UICONTROL Moins]** dans le champ **[!UICONTROL Sélectionner un opérateur]**.

   * Sélectionnez ou faites glisser et déposez, depuis l’onglet Objet de formulaire, le champ **[!UICONTROL Déduction supplémentaire]** dans l’autre champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.
     ![Exemple 15 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor18.png)

1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

   Ajoutez à présent une règle pour le champ `Tax Payable `, qui est déterminée en multipliant le revenu imposable par le taux de taxation. Pour plus de simplicité, prenons un taux de taxation fixe de `10%`.

1. En mode Création, sélectionnez le champ **[!UICONTROL Impôt à payer]**, puis l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Sélectionnez ensuite **[!UICONTROL Créer]** pour créer des règles.
   ![Exemple 16 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor19.png)
1. Choisissez **[!UICONTROL Sélectionner l’option]** et sélectionnez **[!UICONTROL Expression mathématique]**. Un champ permettant de saisir l’expression mathématique s’ouvre.
   ![Exemple 17 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor20.png)
1. Dans le champ de l’expression mathématique :

   * Sélectionnez ou glissez-déposez, depuis l’onglet Objets de formulaire, le champ **[!UICONTROL Revenu imposable]** dans le premier champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.

   * Sélectionnez **[!UICONTROL Multiplié par]** dans le champ **[!UICONTROL Sélectionner un opérateur]**.

   * Sélectionnez **Nombre** dans le champ **[!UICONTROL Sélectionner une option]** et saisissez la valeur `10` dans le champ **[!UICONTROL Saisir un nombre]**.
     ![Exemple 18 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor21.png)
1. Ensuite, sélectionnez la zone en surbrillance autour du champ Expression et choisissez **[!UICONTROL Étendre l’expression]**.
   ![Exemple 19 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor22.png)
1. Dans le champ d’expression étendue, sélectionnez **[!UICONTROL divisé par]** dans le champ **[!UICONTROL Sélectionner un opérateur]** et **[!UICONTROL Nombre]** dans le champ **[!UICONTROL Sélectionner une option]**. Spécifiez ensuite la valeur `100` dans le champ Nombre.
   ![Exemple 20 de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor23.png)
1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

### &#x200B;4. Prévisualiser un formulaire

Désormais, lorsque vous prévisualisez le formulaire et saisissez `60,000` pour le **Salaire brut**, le champ **Déduction supplémentaire** s’affiche et les champs **Revenu imposable** et **Impôt à payer** sont calculés en conséquence.

![Prévisualiser un formulaire](/help/edge/docs/forms/assets/rule-editor-form.png)

Outre les fonctionnalités prêtes à l’emploi, comme Somme ou Moyenne, qui sont répertoriées sous Fonctions, vous pouvez [créer des fonctions personnalisées](#create-a-custom-function) pour implémenter les logiques métier complexes.

## Fonctions personnalisées dans l’éditeur de règles

Forms Edge Delivery Services prend en charge les fonctions personnalisées qui permettent aux utilisateurs et utilisatrices de définir des fonctions JavaScript pour l’implémentation de règles métier complexes. Les fonctions personnalisées étendent les capacités des formulaires en facilitant la manipulation et le traitement des données saisies pour répondre aux exigences spécifiées.

### Création d’une fonction personnalisée

Pour créer des fonctions personnalisées, modifiez le fichier `../[blocks]/form/functions.js`. Le processus de création comprend généralement les étapes suivantes :

* **Déclaration de fonction** : définissez le nom de la fonction et ses paramètres (entrées qu’elle accepte).
* **Mise en œuvre logique** : écrivez le code qui décrit les calculs ou les manipulations spécifiques effectués par la fonction.
* **Export de fonction** : rendez la fonction accessible dans vos règles en l’exportant à partir du fichier approprié.


Cet exemple illustre les deux fonctions personnalisées `getFullName` et `days` :

```JavaScript
/**
 * Get Full Name
 * @name getFullName Concats first name and last name
 * @param {string} firstname in Stringformat
 * @param {string} lastname in Stringformat
 * @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

/**
 * Calculate the number of days between two dates.
 * @param {*} endDate
 * @param {*} startDate
 * @name days Calculates the numebr of days between two dates
 * @returns {number} returns the number of days between two dates
 */
function days(endDate, startDate) {
  const start = typeof startDate === 'string' ? new Date(startDate) : startDate;
  const end = typeof endDate === 'string' ? new Date(endDate) : endDate;

  // return zero if dates are valid
  if (Number.isNaN(start.getTime()) || Number.isNaN(end.getTime())) {
    return 0;
  }

  const diffInMs = Math.abs(end.getTime() - start.getTime());
  return Math.floor(diffInMs / (1000 * 60 * 60 * 24));
}

// eslint-disable-next-line import/prefer-default-export
export { getFullName, days };
```
![Ajout d’une fonction personnalisée](/help/edge/docs/forms/assets/create-custom-function.png)

### Utiliser une fonction personnalisée dans l’éditeur de règles

Pour utiliser la fonction personnalisée dans l’éditeur de règles, procédez comme suit :

1. **Ajouter la fonction** : incluez votre fonction personnalisée dans le fichier `../[blocks]/form/functions.js`. N’oubliez pas de l’ajouter à l’instruction `export` dans le fichier.
1. **Déployer le fichier** : déployez le fichier `functions.js` mis à jour dans votre projet GitHub et vérifiez la création.
1. **Utilisation des fonctions** : accédez à la fonction dans l’éditeur de règles de votre formulaire en sélectionnant l’option `Function Output` dans le champ **[!UICONTROL Sélectionner une action]**.

   ![Fonctions personnalisées dans l’éditeur de règles](/help/edge/docs/forms/assets/custom-function-rule-editor.png)

1. **Prévisualiser le formulaire** : prévisualisez votre formulaire avec la fonction nouvellement mise en œuvre.

## Informations supplémentaires

>[!NOTE]
>
> Dans l’éditeur universel, les imports statiques et dynamiques ne sont pas pris en charge dans les scripts des fonctions personnalisées. Vous devez ajouter le code complet dans le fichier `../[blocks]/form/functions.js`.

Cet article fournit des informations limitées sur l’Éditeur de règles disponible dans l’éditeur universel. Pour en savoir plus sur l’Éditeur de règles et les fonctions personnalisées, consultez les articles suivants :

{{see-also-rule-editor}}

## Voir également

{{universal-editor-see-also}}
