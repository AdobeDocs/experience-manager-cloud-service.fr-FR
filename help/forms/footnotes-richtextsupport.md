---
title: Comment ajouter une note de bas de page à un formulaire adaptatif ?
description: Utilisez l’éditeur de texte enrichi (RTE) pour les notes de bas de page dans un formulaire adaptatif.
feature: Adaptive Forms, Foundation Components
exl-id: f04dae84-daab-42f8-876f-02fe426f62be
role: User, Developer
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 80%

---

# Composant de note de bas de page. {#footnotecomponent}

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.

La **[!UICONTROL Note de bas de page]** est le texte d’informations ou les notes supplémentaires qui apparaissent à la fin de la page. La [!UICONTROL Note de bas de page] comprend les notes qui sont indiquées dans votre texte avec des nombres sous forme d’exposant.

Les notes de bas de page sont numérotées de manière séquentielle dans l’ordre dans lequel elles apparaissent sur la page. Chaque note de bas de page comporte un numéro unique sous la forme d’un exposant qui correspond au numéro placé en bas de la page. À côté du nombre apparaissent les informations complémentaires sous forme de note de bas de page descriptive.

![Note de bas de page descriptive.](/help/forms/assets/footnote_description.png)


## Utilisation de la note de bas de page. {#usesoffootnotes}

* Aide à fournir des citations.
* Fournit des informations supplémentaires qui peuvent interrompre le flux normal des informations principales.
* Fournit des informations entre parenthèses ou des droits d’auteur.

Dans les formulaires adaptatifs, [!UICONTROL la note de bas de page] est utilisée pour afficher les informations sur la manière de remplir ou d’utiliser le formulaire. Pour plus d’informations sur la création d’un formulaire adaptatif, voir [Création d’un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html?lang=fr).

## Note de bas de page dans les formulaires adaptatifs. {#using-footnote-adaptiveforms}

Pour ajouter une note de bas de page dans les formulaires adaptatifs, procédez comme suit :
1. Ouvrez un formulaire adaptatif en mode **Édition**.
1. À partir du navigateur de composant, faites glisser et déposez le composant **[!UICONTROL Texte]** sur le formulaire adaptatif.
1. Sélectionnez le composant **[!UICONTROL Texte]** que vous avez ajouté, puis sélectionnez ![cmppr](assets/configure-icon.svg) pour modifier ses propriétés.

   ![Note de bas de page dans les formulaires adaptatifs.](/help/forms/assets/footnote_rte.png)

1. Sélectionnez le texte pour lequel vous souhaitez ajouter une note de bas de page descriptive, puis cliquez sur le bouton ![étoile](/help/forms/assets/asterisk.svg) pour appliquer un style au composant **[!UICONTROL Note de bas de page]**.

1. Cliquez sur ![check](/help/forms/assets/save_icon.svg) pour enregistrer les modifications et les styles.

   >[!NOTE]
   >
   >* Les notes de bas de page sont numérotées automatiquement et s’affichent de la manière dont elles sont créées dans le formulaire adaptatif.
   >* S’il existe des notes de bas de page en double, le nombre est le même pour toutes les notes de bas de page en double.

1. À partir de l’explorateur des composants, glissez-déposez le composant **[!UICONTROL Espace réservé pour la note de bas de page]** sur le formulaire adaptatif.

   >[!NOTE]
   >
   >* Sur l’instance de publication, les notes de bas de page s’affichent à l’emplacement où le composant **[!UICONTROL Espace réservé de la note de bas de page]** est placé sur le formulaire adaptatif.
   >* Lorsque vous naviguez entre différents panneaux, seules les notes de bas de page visibles apparaissent dans l’**[!UICONTROL Espace réservé de la note de bas de page]** présent dans le panneau de navigation.

1. Enregistrez les propriétés.

Au moment de l’exécution, le nombre apparaît sur le texte sous forme d’exposant et sa description correspondante apparaît dans le composant **[!UICONTROL Note de bas de page]** à l’emplacement où l’[!UICONTROL Espace réservé de la note de bas de page] est placé sur le formulaire adaptatif. Vous pouvez accéder directement à la note de bas de page descriptive en cliquant sur son numéro correspondant dans la [!UICONTROL Note de bas de page].


## Voir également {#see-also}

{{see-also}}