---
title: Comment utiliser l’éditeur de règles pour appliquer des règles aux champs de formulaire, ce qui permet un comportement dynamique et une logique complexe pour les formulaires créés avec la création WYSIWYG ?
description: L’éditeur de règles de l’éditeur universel vous permet d’ajouter un comportement dynamique et de créer une logique complexe dans des formulaires sans codage ni script.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: c27b8e413c060de601a72a669d86c4add2a4167d
workflow-type: tm+mt
source-wordcount: '2111'
ht-degree: 11%

---


# Présentation de l’éditeur de règles dans l’éditeur universel

Vous pouvez ajouter un comportement de formulaire dynamique à l’aide de l’éditeur de règles, qui permet de créer des règles. Ces règles permettent une visibilité conditionnelle des champs, automatisent les calculs en fonction des entrées de l’utilisateur et améliorent l’expérience globale de l’utilisateur. En rationalisant le processus de remplissage des formulaires, l’éditeur de règles garantit à la fois précision et efficacité.

L’éditeur de règles offre une interface visuelle intuitive pour la création et la gestion des règles. Son approche conviviale le rend accessible à tous les utilisateurs et utilisatrices, même ceux et celles qui ne disposent pas d’une vaste expertise technique, ce qui leur permet d’implémenter la logique sans effort dans leurs formulaires.

## Présentation d’une règle

Les règles sont des instructions qui guident les utilisateurs et utilisatrices sur les actions à effectuer dans des conditions spécifiques.

* **Condition** : une condition est une vérification ou une règle qui évalue si un élément est vrai ou faux. Cela répond à la question suivante : « Est-ce que cela répond aux exigences ? »

* **Action** : une action est ce qui se produit lorsque la condition est vraie. Il s’agit de la tâche ou du comportement déclenché(e) en fonction de l’évaluation de la condition.

Une règle suit généralement l’un des concepts suivants :

* **Condition-Action** : vérifiez d’abord une condition, puis effectuez une action. Dans l’éditeur de règles, le type de règle `When` applique le concept de `condition-action`.
* **Action-Condition** : effectuez d’abord une action, puis vérifiez une condition. Les types de règle `Set Value Of` et `Validate` dans l’éditeur de règles appliquent le concept de `action-condition`.
* **Action-Condition-Action alternative** : exécutez une action, vérifiez une condition, puis exécutez l’action principale ou une action alternative en fonction de la condition. Par exemple, par défaut, l’action alternative pour `Show` est `Hide` et, par `Enable`, `Disable`.

Par exemple, une condition peut vérifier si un utilisateur ou une utilisatrice a saisi une certaine valeur dans un champ et l’action peut consister à afficher ou masquer un champ.
* **Condition** : vérifiez si le revenu est supérieur à 50 000 $.
* **Action** : si la condition est vraie, afficher le champ `Additional Deduction` ; sinon, effectuer l&#39;action alternative : masquer le champ `Additional Deduction`.

Pour obtenir des instructions détaillées, reportez-vous à la [ajout d’une règle conditionnelle](#2-add-a-conditional-rule).

## Comment activer l’extension de l’éditeur de règles ?

Dans l’éditeur universel, l’éditeur de règles n’est pas activé par défaut. Pour activer l’extension Éditeur de règles pour votre environnement, envoyez un e-mail à partir de votre adresse officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) avec votre demande.

Une fois que l’extension de l’éditeur de règles est activée pour votre environnement, l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg) s’affiche dans le coin supérieur droit de l’éditeur.

![Éditeur universel de règles](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)

Sélectionnez l’objet de formulaire pour lequel vous souhaitez créer une règle, puis cliquez sur l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg). L’interface utilisateur de l’éditeur de règles s’affiche.

![Interface utilisateur de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-for-field.png)

Vous pouvez maintenant commencer à créer des règles ou une logique métier pour le champ de formulaire sélectionné en utilisant les [types de règles disponibles dans l’éditeur de règles](#available-rule-types-in-rule-editor).

## Présentation de l’interface utilisateur de l’éditeur de règles

L’éditeur visuel de l’éditeur de règles s’ouvre lorsque vous cliquez sur l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg) :

![Interface utilisateur de l’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-interface.png)

<table border="1">
  <thead>
    <tr>
      <th>Composant de l’éditeur de règles</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1. Affichage composant-règle</td>
      <td>Affiche le titre de l’objet de formulaire par lequel vous avez lancé l’éditeur de règles et le type de règle actuellement sélectionné.</td>
    </tr>
    <tr>
      <td>2. Objets de formulaire et fonctions</td>
      <td>L’onglet <b>Objets Forms</b> affiche une vue hiérarchique de tous les objets contenus dans le formulaire. L’onglet <b>Fonctions</b> comprend un ensemble de fonctions intégrées.</td>
    </tr>
    <tr>
      <td>3. Basculement entre les objets de formulaire et les fonctions</td>
      <td>Le bouton Basculer, lorsqu’il est sélectionné, permet de basculer entre le volet des objets de formulaire et celui des fonctions.</td>
    </tr>
    <tr>
      <td>4. Éditeur visuel de règles</td>
      <td>L’éditeur de règles visuel est la zone de l’interface utilisateur de l’éditeur de règles en mode éditeur visuel dans laquelle vous créez des règles.</td>
    </tr>
    <tr>
      <td>5. boutons Terminé et Annuler</td>
      <td>Le bouton <b>Terminé</b> permet d’enregistrer une règle. Le bouton <b>Annuler</b> ignore toutes les modifications que vous avez apportées à une règle et ferme l’éditeur de règles.</td>
    </tr>
  </tbody>
</table>

Toutes les règles existantes sur un objet de formulaire sont répertoriées lorsque vous sélectionnez l’objet . Vous pouvez afficher le titre et prévisualiser le résumé de la règle dans l’éditeur de règles visuel. De plus, vous pouvez modifier l’ordre des règles, modifier des règles, activer/désactiver des règles ou en supprimer.

![afficher les règles disponibles de l’objet de formulaire](/help/edge/docs/forms/assets/rule-editor15.png)

## Types de règle disponibles

L’éditeur de règles fournit un ensemble de types de règle prédéfinis que vous pouvez utiliser pour créer des règles, comme illustré dans le tableau ci-dessous :

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
      <td>Définit la valeur d’un objet de formulaire selon que la condition spécifiée est remplie ou non.</td>
    </tr>
    <tr>
      <td>Effacer la valeur de</td>
      <td>Efface la valeur de l'objet spécifié.</td>
    </tr>
    <tr>
      <td>Masquer/Afficher</td>
      <td>Masque ou affiche un objet de formulaire selon qu’une condition est remplie ou non.</td>
    </tr>
    <tr>
      <td>Activer/Désactiver</td>
      <td>Active ou désactive un objet de formulaire selon qu’une condition est remplie ou non.</td>
    </tr>
    <tr>
      <td>Valider</td>
      <td>Valide le formulaire ou un objet spécifié.</td>
    </tr>
    <tr>
      <td>Quand</td>
      <td>Suit le concept de règle d’action <i>condition-action-alternative</i> ou <i>condition-action</i>. Il spécifie une condition à évaluer, suivie d’une action à déclencher si la condition est remplie.</td>
    </tr>
    <tr>
      <td>Format</td>
      <td>Met en forme un objet de formulaire à partir d’une fonction ou d’une expression régulière.</td>
    </tr>
    <tr>
      <td>Appel du service </td>
      <td>Appelle un service configuré dans un modèle de données de formulaire (FDM).</td>
    </tr>
    <tr>
      <td>Définir la propriété</td>
      <td>Définit la valeur d’une propriété de l’objet spécifié en fonction d’une condition.</td>
    </tr>
    <tr>
      <td>Définir la cible d'action</td>
      <td>Définit le focus sur l’objet spécifié.</td>
    </tr>
    <tr>
      <td>Enregistrer le formulaire</td>
      <td>Enregistre le formulaire.</td>
    </tr>
    <tr>
      <td>Envoyer/Réinitialiser le formulaire</td>
      <td>Envoie ou réinitialise le formulaire.</td>
    </tr>
    <tr>
      <td>Ajouter/Supprimer une instance</td>
      <td>Ajoute ou supprime une instance de la ligne de panneau ou de tableau répétable spécifiée.</td>
    </tr>
    <tr>
      <td>Accéder À</td>
      <td>Permet d’accéder à d’autres ressources, telles que des images ou des fragments de document ou une URL externe Forms adaptative.</td>
    </tr>
    <tr>
      <td>Distribuer l’événement</td>
      <td>Déclenche des actions spécifiques en fonction de conditions ou d’événements prédéfinis.</td>
    </tr>
    <tr>
      <td>Naviguer parmi les panneaux</td>
      <td>Permet de déplacer la sélection entre différents panneaux d’un formulaire.</td>
    </tr>
  </tbody>
</table>


Maintenant, découvrons comment [écrire des règles dans l’éditeur de règles](#write-rules).

## Règles d’écriture

Pour comprendre comment écrire des règles dans l’éditeur visuel de règles, prenons l’exemple simple d’un formulaire de calcul des taxes :

![Exemple d’éditeur de règles](/help/edge/docs/forms/assets/rule-editor-1.png)

Dans le formulaire décrit ci-dessus, l&#39;utilisateur saisit le salaire brut. En fonction de cette entrée, le champ conditionnel s’affiche et la taxe à payer est calculée.

**Champs de formulaire :**
* Salaire brut (saisie utilisateur)
* Déduction supplémentaire (champ conditionnel)
* Revenu imposable (champ calculé)
* Taxe à payer (champ calculé)

**Règle conditionnelle :**
* Condition : Salaire Brut > 50 000
* Action : afficher le champ Déduction supplémentaire

**Règles de calcul:**

* Revenu imposable = Salaire brut - Déduction supplémentaire (le cas échéant)
* Impôt à payer = Revenu imposable * Taux d&#39;imposition (pour plus de simplicité, supposons un taux fixe de 10 %)

Pour créer des règles :

### 1. Créer un formulaire

Pour créer un formulaire dans l’éditeur universel :

1. Ouvrez un formulaire dans l’éditeur universel pour le modifier.
1. Ajoutez les composants de formulaire suivants :
   * Formulaire De Calcul Des Taxes (Titre)
   * Salaire Brut (Entrée De Texte)
   * Déduction supplémentaire (entrée de texte)
   * Revenu Imposable (Entrée De Texte)
   * Impôt À Payer (Entrée De Texte)
   * Envoyer (Bouton Envoyer)
1. Masquez le champ de formulaire `Additional Deduction` en ouvrant son `Properties`.

   ![Exemple d’éditeur de règles](/help/edge/docs/forms/assets/rule-editor2.png)

### 2. Ajouter une règle conditionnelle pour un champ de formulaire

Une fois que vous avez créé le formulaire, écrivez la première règle pour n’afficher le champ `Additional Deduction` que si le salaire brut dépasse 50 000 $. Pour ajouter une règle conditionnelle, procédez comme suit :

1. Ouvrez un formulaire dans l’éditeur universel pour le modifier.
1. Sélectionnez le composant **[!UICONTROL Salaire brut]** dans l’arborescence de contenu et sélectionnez ![edit-rules](/help/forms/assets/edit-rules-icon.svg).
   ![Exemple d’éditeur de règles1](/help/edge/docs/forms/assets/rule-editor3.png)
L’interface visuelle de l’éditeur de règles s’affiche.
1. Cliquez sur **[!UICONTROL Créer]** pour lancer l’éditeur de règles.
   ![Exemple d’éditeur de règles2](/help/edge/docs/forms/assets/rule-editor4.png)
Par défaut, le type de règle `Set Value Of` est sélectionné. Bien que vous ne puissiez pas modifier l’objet sélectionné, vous pouvez utiliser la liste déroulante des règles pour sélectionner un autre type de règle.\
   ![Exemple d’éditeur de règles3](/help/edge/docs/forms/assets/rule-editor5.png)
1. Ouvrez la liste déroulante de type de règle et sélectionnez le type de règle **[!UICONTROL Lorsque]**.
   ![Exemple d’éditeur de règles4](/help/edge/docs/forms/assets/rule-editor6.png)
1. Sélectionnez **[!UICONTROL Sélectionner l’état]** dans le menu déroulant et sélectionnez **[!UICONTROL est supérieur à]**. Le champ **[!UICONTROL Saisir un nombre]** s’affiche.
   ![Exemple d’éditeur de règles5](/help/edge/docs/forms/assets/rule-editor7.png)
1. Saisissez `50000` dans le champ **[!UICONTROL Saisissez un nombre]** de la règle.
   ![Exemple d’éditeur de règles6](/help/edge/docs/forms/assets/rule-editor8.png)
Vous avez défini la condition comme `When Gross Salary is greater than 50000`. Définissez ensuite l’action à effectuer si cette condition est `True`.
1. Dans l’instruction `Then`, sélectionnez **[!UICONTROL Afficher]** dans le menu déroulant **[!UICONTROL Sélectionner une action]**.
   ![Exemple d’éditeur de règles7](/help/edge/docs/forms/assets/rule-editor9.png)
1. Faites glisser et déposez le champ **[!UICONTROL Déduction supplémentaire]** de l’onglet Objets de formulaire vers le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**. Vous pouvez également sélectionner le champ **[!UICONTROL Déposer l’objet ou sélectionner ici]** et sélectionner le champ **[!UICONTROL Déduction supplémentaire]** dans le menu pop-up, qui répertorie tous les objets de formulaire dans le formulaire.
   ![Exemple d’éditeur de règles8](/help/edge/docs/forms/assets/rule-editor10.png)
1. Cliquez sur **[!UICONTROL Ajouter une section Autre]** pour ajouter une autre condition pour le champ **[!UICONTROL Salaire brut]**, au cas où vous saisissez un salaire inférieur à `50000`.
   ![Exemple d’éditeur de règles9](/help/edge/docs/forms/assets/rule-editor11.png)
1. Sélectionnez **[!UICONTROL Masquer]** dans le menu déroulant **[!UICONTROL Sélectionner une action]** de l’instruction `Else`.
   ![Exemple d’éditeur de règles10](/help/edge/docs/forms/assets/rule-editor12.png)
1. Faites glisser et déposez le champ **[!UICONTROL Déduction supplémentaire]** de l’onglet Objets de formulaire vers le champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**. Vous pouvez également sélectionner le champ **[!UICONTROL Déposer l’objet ou sélectionner ici]** et sélectionner le champ **[!UICONTROL Déduction supplémentaire]** dans le menu pop-up, qui répertorie tous les objets de formulaire dans le formulaire.
   ![Exemple d’éditeur de règles11](/help/edge/docs/forms/assets/rule-editor13.png)
1. Sélectionnez **[!UICONTROL Terminé]** pour enregistrer la règle.
La règle s’affiche comme suit dans l’éditeur de règles.
   ![Exemple d’éditeur de règles12](/help/edge/docs/forms/assets/rule-editor14.png)

>[!NOTE]
>
> Vous pouvez également créer une règle Afficher dans le champ Déduction supplémentaire au lieu d&#39;une règle Lorsque dans le champ Salaire brut pour appliquer le même comportement.

### 3. Ajouter des règles de calcul pour les champs du formulaire

Ensuite, créez une règle pour calculer la `Taxable Income`, qui est la différence entre `Gross Salary` et `Additional Deduction` (le cas échéant). Pour ajouter une règle de calcul dans le champ **[!UICONTROL Revenu imposable]**, procédez comme suit :

1. En mode création, sélectionnez le champ **[!UICONTROL Revenu imposable]** et sélectionnez l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Sélectionnez ensuite **[!UICONTROL Créer]** pour lancer l’éditeur de règles.
   ![Exemple d’éditeur de règles13](/help/edge/docs/forms/assets/rule-editor16.png)
1. Choisissez **[!UICONTROL Sélectionner l’option]** et sélectionnez **[!UICONTROL Expression mathématique]**. Un champ permettant de saisir l’expression mathématique s’ouvre.
   ![Exemple d’éditeur de règles14](/help/edge/docs/forms/assets/rule-editor17.png)

1. Dans le champ Expression mathématique :

   * Sélectionnez ou faites glisser et déposez depuis le champ **[!UICONTROL Salaire brut]** de l’onglet Objet Forms vers le premier champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.

   * Sélectionnez **[!UICONTROL Moins]** dans le champ **[!UICONTROL Sélectionner un opérateur]**.

   * Sélectionnez ou faites glisser et déposez depuis le champ **[!UICONTROL Déduction supplémentaire]** de l’onglet Objet Forms vers l’autre champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.
     ![Exemple d’éditeur de règles15](/help/edge/docs/forms/assets/rule-editor18.png)

1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

   Ajoutez à présent une règle pour le champ `Tax Payable `, qui est déterminée en multipliant le revenu imposable par le taux d’imposition. Pour plus de simplicité, supposons un taux d’imposition fixe de `10%`.

1. En mode création, sélectionnez le champ **[!UICONTROL Taxe à payer]** et sélectionnez l’icône ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Sélectionnez ensuite **[!UICONTROL Créer]** pour lancer l’éditeur de règles.
   ![Exemple d’éditeur de règles16](/help/edge/docs/forms/assets/rule-editor19.png)
1. Choisissez **[!UICONTROL Sélectionner l’option]** et sélectionnez **[!UICONTROL Expression mathématique]**. Un champ permettant de saisir l’expression mathématique s’ouvre.
   ![Exemple d’éditeur de règles17](/help/edge/docs/forms/assets/rule-editor20.png)
1. Dans le champ Expression mathématique :

   * Sélectionnez ou faites glisser et déposez depuis le champ **[!UICONTROL Revenu imposable]** de l’onglet Objet Forms vers le premier champ **[!UICONTROL Déposez l’objet ou sélectionnez ici]**.

   * Sélectionnez **[!UICONTROL Multiplié par]** dans le champ **[!UICONTROL Sélectionner un opérateur]**.

   * Sélectionnez **Nombre** dans le champ **[!UICONTROL Sélectionner une option]** et saisissez la valeur telle qu’`10` dans le champ **[!UICONTROL Saisir un nombre]**.
     ![Exemple d’éditeur de règles18](/help/edge/docs/forms/assets/rule-editor21.png)
1. Ensuite, sélectionnez la zone en surbrillance autour du champ Expression et choisissez **[!UICONTROL Étendre l’expression]**.
   ![Exemple d’éditeur de règles19](/help/edge/docs/forms/assets/rule-editor22.png)
1. Dans le champ d’expression étendue, sélectionnez **[!UICONTROL divisé par]** dans le champ **[!UICONTROL Sélectionner un opérateur]** et **[!UICONTROL Nombre]** dans le champ **[!UICONTROL Sélectionner une option]**. Indiquez ensuite `100` dans le champ numérique.
   ![Exemple d’éditeur de règles20](/help/edge/docs/forms/assets/rule-editor23.png)
1. Cliquez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

### 4. Prévisualiser un formulaire

Désormais, lorsque vous prévisualisez le formulaire et saisissez le **Salaire brut** comme `60,000`, le champ **Déduction supplémentaire** s’affiche et les **Revenu imposable** et **Impôt à payer** sont calculés en conséquence.

![Prévisualiser un formulaire](/help/edge/docs/forms/assets/rule-editor-form.png)

Outre les fonctions prêtes à l’emploi telles que Somme, Moyenne qui sont répertoriées sous Fonctions, vous pouvez [créer des fonctions personnalisées](#create-a-custom-function) pour implémenter des logiques commerciales complexes.

## Fonction personnalisée dans l’éditeur de règles

Forms Edge Delivery Services prend en charge les fonctions personnalisées qui permettent aux utilisateurs de définir des fonctions JavaScript pour l’implémentation de règles métier complexes. Les fonctions personnalisées étendent les fonctionnalités des formulaires en facilitant la manipulation et le traitement des données saisies afin de répondre à des exigences spécifiques.

### Création d’une fonction personnalisée

Pour créer des fonctions personnalisées, modifiez le fichier `../[blocks]/form/functions.js`. Le processus de création comprend généralement les étapes suivantes :

* **Déclaration de fonction** : définissez le nom de la fonction et ses paramètres (les entrées qu’elle accepte).
* **Implémentation logique** : écrivez le code qui décrit les calculs ou manipulations spécifiques effectués par la fonction.
* **Exportation de fonction** : rendez la fonction accessible dans vos règles en l’exportant à partir du fichier approprié.


Cet exemple illustre deux fonctions personnalisées telles que `getFullName` et `days` :

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
![Ajouter une fonction personnalisée](/help/edge/docs/forms/assets/create-custom-function.png)

### Utilisation d’une fonction personnalisée dans l’éditeur de règles

Pour utiliser la fonction personnalisée dans l’éditeur de règles :

1. **Ajouter la fonction** : incluez votre fonction personnalisée dans le fichier `../[blocks]/form/functions.js`. N’oubliez pas de l’ajouter à l’instruction `export` dans le fichier .
1. **Déployer le fichier** : déployez le fichier `functions.js` mis à jour dans votre projet GitHub et vérifiez la création.
1. **Utilisation de la fonction** : accédez à la fonction dans l’éditeur de règles de votre formulaire en sélectionnant l’option `Function Output` dans le champ **[!UICONTROL Sélectionner une action]**.

   ![Fonction personnalisée dans l’éditeur de règles](/help/edge/docs/forms/assets/custom-function-rule-editor.png)

1. **Prévisualiser le formulaire** : prévisualisez votre formulaire avec la fonction nouvellement implémentée.

## Articles connexes

{{see-also-rule-editor}}

## Voir également

* [Commencer avec Edge Delivery Services pour AEM Forms](/help/edge/docs/forms/tutorial.md)
* [Créer un formulaire à l’aide de Google Sheets ou de Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Configurer vos fichiers Google Sheets ou Microsoft Excel pour accepter des données](/help/edge/docs/forms/submit-forms.md)
* [Publier votre formulaire et commencer à collecter des données](/help/edge/docs/forms/publish-forms.md)
* [Personnaliser l’apparence de vos formulaires](/help/edge/docs/forms/style-theme-forms.md)
* [Ajouter des sections répétables à un formulaire](/help/edge/docs/forms/repeatable-forms.md)
* [Afficher un message de remerciement personnalisé après l’envoi du formulaire](/help/edge/docs/forms/thank-you-page-form.md)
* [Composants de bloc de formulaire adaptatif et leurs propriétés](/help/edge/docs/forms/form-components.md)
* [Surveillance d’utilisation réelle](https://www.aem.live/developer/rum#authentication)
