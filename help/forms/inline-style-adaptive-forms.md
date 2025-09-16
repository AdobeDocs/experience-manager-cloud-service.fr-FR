---
title: Comment appliquer des styles intégrés aux composants de formulaire adaptatif ?
description: Découvrez comment appliquer des styles personnalisés à un formulaire adaptatif. Vous pouvez également appliquer des propriétés CSS intégrées sur les composants individuels d’un formulaire adaptatif.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: 25adabfb-ff19-4cb2-aef5-0a8086d2e552
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 78%

---

# Styles intégrés des composants de formulaire adaptatif {#inline-styling-of-adaptive-form-components}

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/inline-style-adaptive-forms.html) |
| AEM as a Cloud Service | Cet article |

Vous pouvez définir l’aspect général et le style d’un formulaire adaptatif en spécifiant les styles à l’aide d’un [éditeur de thèmes](themes.md). En outre, vous pouvez appliquer des styles CSS intégrés à différents composants de formulaire adaptatif et prévisualiser les modifications apportées à la volée. Les styles intégrés remplacent les styles fournis dans le thème.

## Application des propriétés de style CSS intégré {#apply-inline-css-properties}

Pour ajouter des styles intégrés à un composant :

1. Ouvrez votre formulaire dans le créateur de formulaires, puis choisissez le mode Style. Pour passer au mode Style, dans la barre d’outils de la page, sélectionnez ![canvas-drop-down](assets/Smock_ChevronDown.svg) > **[!UICONTROL Style]**.
1. Sélectionnez un composant dans la page, puis sélectionnez le bouton Modifier ![edit-button](assets/edit.svg). Les propriétés de style s’ouvrent dans la barre latérale.

   Vous pouvez également sélectionner des composants dans l’arborescence de hiérarchie de formulaire dans la barre latérale. L’arborescence de hiérarchie de formulaires est disponible sous forme d’objets de formulaire dans la barre latérale.

   Dans le mode [!UICONTROL Style,] vous pouvez afficher les composants répertoriés sous Objets de formulaire. Toutefois, la liste Objets de formulaire dans la barre latérale répertorie les composants tels que les champs et les panneaux. Les champs et les panneaux sont des composants génériques qui peuvent contenir des composants tels que des zones de texte et des boutons radio.

   Lorsque vous sélectionnez un composant dans la barre latérale, vous voyez tous les sous-composants répertoriés et les propriétés du composant sélectionné. Vous pouvez sélectionner un sous-composant spécifié et lui appliquer une mise en forme.

1. Cliquez sur un onglet de la barre latérale pour spécifier les propriétés CSS. Vous pouvez définir des propriétés telles que les suivantes :

   * [!UICONTROL Dimensions et position] (paramètre d’affichage, remplissage, hauteur, largeur, marge, position, index z, flottant, clair, débordement)
   * [!UICONTROL Texte] (famille de polices, épaisseur, couleur, taille, hauteur de ligne et alignement)
   * [!UICONTROL Arrière-plan] (image et gradient, couleur d’arrière-plan)
   * [!UICONTROL Bordure] (largeur, style, couleur, rayon)
   * [!UICONTROL Effets] (ombre, opacité)
   * [!UICONTROL Avancé] (permet de saisir un CSS personnalisé pour le composant)

1. De même, vous pouvez appliquer des styles pour d’autres parties d’un composant tels que [!UICONTROL Widget], [!UICONTROL Légende] et [!UICONTROL Aide].
1. Sélectionnez **[!UICONTROL Terminé]** pour confirmer les modifications ou sur **[!UICONTROL Annuler]** pour annuler les modifications.

## Exemple : styles intégrés pour un composant de champ {#example-inline-styles-for-a-field-component}

Les images suivantes illustrent une zone de texte avant et après l’application des styles intégrés.

![Composant de zone de texte avant l’application du style intégré](assets/no-style.png)

Composant de zone de texte avant d’appliquer les propriétés de style intégrées

Notez la modification du style de la zone de texte comme illustré ci-dessous après l’application des propriétés CSS suivantes.

<table>
 <tbody>
  <tr>
   <td><p>Sélecteur</p> </td>
   <td><p>Propriété CSS</p> </td>
   <td><p>Valeur</p> </td>
   <td><p>Effet</p> </td>
  </tr>
  <tr>
   <td><p>Champ</p> </td>
   <td><p>bordure</p> </td>
   <td><p>Largeur de la bordure = 2 px</p> <p>Style de bordure = plein</p> <p>Couleur de la bordure = #1111</p> </td>
   <td><p>Crée une bordure large noire 2-px autour du champ</p> </td>
  </tr>
  <tr>
   <td><p>Zone de texte</p> </td>
   <td><p>background-color</p> </td>
   <td><p>#6495ED</p> </td>
   <td><p>Modifie la couleur d’arrière-plan en CornflowerBlue (#6495ED).</p> <p>Remarque : vous pouvez spécifier un nom de couleur ou son code hexadécimal dans le champ Valeur.</p> </td>
  </tr>
  <tr>
   <td><p>Libellé</p> </td>
   <td><p>Dimensions et position &gt; largeur</p> </td>
   <td><p>100 px</p> </td>
   <td><p>Définit la largeur sur 100 px pour le libellé.</p> </td>
  </tr>
  <tr>
   <td>Icône d’aide du champ</td>
   <td>Texte &gt; Couleur de police</td>
   <td>#2ECC40</td>
   <td>Modifie la couleur de la face de l’icône d’aide.</td>
  </tr>
  <tr>
   <td><p>Description longue</p> </td>
   <td><p>text-align</p> </td>
   <td><p>center</p> </td>
   <td><p>Aligne la description longue pour faciliter le centrage.</p> </td>
  </tr>
 </tbody>
</table>

![Style de zone de texte après l’application du style intégré](assets/applied-style.png)

Composant de zone de texte après application des propriétés de style intégré

En suivant les étapes ci-dessus, vous pouvez sélectionner et mettre en forme d’autres composants, tels que les panneaux, les boutons d’envoi et les boutons radio.

>[!NOTE]
>
>Les propriétés de style varient en fonction du composant sélectionné.

## Copie et collage de styles {#copy-paste-styles}

Vous pouvez également copier un style et le coller d’un composant à un autre dans un formulaire adaptatif. En mode **[!UICONTROL Style]**, sélectionnez le composant, puis sélectionnez l’icône Copier ![Copier](assets/property-copy-icon.svg).

Sélectionnez l’autre composant du même type et sélectionnez l’icône Coller ![Copier](assets/Smock_Paste_18_N.svg) pour coller le style copié. Vous pouvez également sélectionner l’icône Effacer le style ![Copier](assets/clear-style-icon.svg) pour effacer le style appliqué.

## Définition des styles pour les différents états d’un composant {#set-styles-for-states}

Vous pouvez définir des styles pour différents états d’un type de composant. Les différents états sont les suivants : [!UICONTROL Activé], [!UICONTROL Désactivé], [!UICONTROL Survol], [!UICONTROL Erreur], [!UICONTROL Succès] et [!UICONTROL Obligatoire].

Pour définir la mise en forme d’un état d’un composant :

1. En mode **[!UICONTROL Style]**, sélectionnez le composant, puis sélectionnez l’icône Modifier ![Modifier](assets/Smock_Edit_18_N.svg).

1. Sélectionnez l’état du composant à l’aide de la liste déroulante **[!UICONTROL État]**.

   ![Sélectionner l’état](assets/select-state.png)

1. Définissez la mise en forme de l’état sélectionné du composant et sélectionnez ![Enregistrer](assets/save_icon.svg) pour enregistrer les propriétés.

Vous pouvez également simuler les états de succès et d’erreur. Sélectionnez l’icône Développer pour afficher les options **[!UICONTROL Simuler la réussite]** et **[!UICONTROL Simuler une erreur]**.

![Simuler les états](assets/simulate-states.png)


## Voir également {#see-also}

{{see-also}}


<!--

>[!MORELIKETHIS]
>
>* [Use themes in Adaptive Form Core Components ](/help/forms/using-themes-in-core-components.md)

-->