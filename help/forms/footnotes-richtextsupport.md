---
title: Prise en charge des notes de bas de page
description: Prise en charge de l’éditeur de texte enrichi pour les notes de bas de page.
source-git-commit: 6f6cf5657bf745a2e392a8bfd02572aa864cc69c
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Composant de note de bas de page {#footnotecomponent}

**[!UICONTROL Note de bas de page]** est le texte supplémentaire d’informations ou de notes qui apparaît à la fin de la page. [!UICONTROL Note de bas de page] comprend les notes qui sont indiquées dans votre texte avec des nombres comme exposant.

Les notes de bas de page sont numérotées de manière séquentielle dans l’ordre dans lequel elles apparaissent sur la page. Chaque note de bas de page comporte un numéro unique en tant qu’exposant qui correspond au numéro placé en bas de la page. En regard du nombre apparaît les informations complémentaires sous forme de description de la note de bas de page.

![Description de la note](/help/forms/assets/footnote_description.png)


## Utilisation de la note de bas de page {#usesoffootnotes}

* Aide à fournir des citations.
* Fournit des informations supplémentaires qui peuvent interrompre le flux normal des informations principales.
* Fournit des informations entre parenthèses ou des droits d’auteur.

Dans Adaptive Forms, [!UICONTROL note] est utilisé pour afficher les informations sur la manière de remplir ou d’utiliser le formulaire. Pour plus d’informations sur la création d’un Forms adaptatif, voir [Création d’un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html).

## Remarque dans Adaptive Forms {#using-footnote-adaptiveforms}

Pour ajouter une note de bas de page dans Adaptive Forms, procédez comme suit :
1. Ouvrir un formulaire adaptatif dans **Modifier** mode .
1. Dans l’explorateur de composants, faites glisser et déposez le composant **[!UICONTROL Texte]** sur le formulaire adaptatif.
1. Sélectionnez la **[!UICONTROL Texte]** composant que vous avez ajouté et appuyez sur ![cmppr](assets/configure-icon.svg) pour modifier ses propriétés.

   ![Remarque dans Adaptive Forms](/help/forms/assets/footnote_rte.png)

1. Sélectionnez le texte pour lequel vous souhaitez ajouter une description de note de bas de page, puis cliquez sur  ![star](/help/forms/assets/asterisk.svg) pour appliquer un style au **[!UICONTROL Note de bas de page]** composant.

1. Cliquez sur ![check](/help/forms/assets/save_icon.svg) pour enregistrer les modifications et les styles.

   >[!NOTE]
   >
   >* Les notes de bas de page sont numérotées automatiquement et s’affichent de la manière dont elles sont créées dans le formulaire adaptatif.
   >* S’il existe des notes de bas de page en double, le nombre est le même pour toutes les notes de bas de page en double.


1. Dans l’explorateur de composants, faites glisser et déposez le composant **[!UICONTROL Espace réservé de la note de bas de page]** sur le formulaire adaptatif.
   >[!NOTE]
   >
   >* Sur l’instance de publication, les notes de bas de page s’affichent à l’emplacement où **[!UICONTROL Espace réservé de la note de bas de page]** est placé sur le formulaire adaptatif.
   >* Lorsque vous naviguez entre différents panneaux, seules les notes de bas de page visibles apparaissent dans la variable **[!UICONTROL Espace réservé de la note de bas de page]** qui sont présents dans le panneau navigated.


1. Enregistrez les propriétés.

Au moment de l’exécution, le nombre apparaît sur le texte sous forme d’exposant et sa description correspondante apparaît dans la variable **[!UICONTROL Note de bas de page]** à l’emplacement où [!UICONTROL Espace réservé de la note de bas de page] est placé sur le formulaire adaptatif. Vous pouvez accéder directement à la description de la note de bas de page en cliquant sur son numéro correspondant dans la [!UICONTROL Note de bas de page].