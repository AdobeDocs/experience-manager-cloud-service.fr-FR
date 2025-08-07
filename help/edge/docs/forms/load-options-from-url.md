---
title: Charger les options de liste déroulante à partir d’une URL ou une autre feuille d’Edge Delivery Services pour AEM Forms as a Cloud Service
description: Les options de la liste déroulante sont incluses dans une feuille de calcul distincte, puis importées dans la feuille de calcul principale via l’URL fournie.
feature: Edge Delivery Services
exl-id: 5b0bc1b6-6e33-41f3-b7c1-4d997787b6cd
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 100%

---


# Options d’une URL ou d’une autre feuille d’Edge Delivery Services pour AEM Forms as a Cloud Service

Les formulaires comprennent souvent des menus déroulants que les utilisateurs et utilisatrices peuvent sélectionner parmi des options prédéfinies. Ces options sont généralement définies dans le formulaire lui-même, mais la gestion de longues listes peut être difficile. Ce guide explique comment améliorer la création de formulaires en chargeant les options de liste déroulante à partir d’une feuille de calcul distincte via une URL.


Les avantages du chargement des options de liste déroulante depuis une feuille de calcul distincte sont les suivants :

- Gestion simplifiée : conserver les options de liste déroulante dans un emplacement centralisé facilite les mises à jour et les ajouts.
- Efficacité améliorée : vous évitez de devoir ajouter manuellement de longues listes d’options dans la définition du formulaire.

![Options de liste déroulante](/help/forms/assets/drop-down-options.png)


À la fin de cet article, vous saurez accomplir ce qui suit :

- [Définir les options dans une feuille de calcul distincte](#define-options)
- [Ajouter l’URL pour charger les options de liste déroulante](#add-url)

## Définir les options dans une feuille distincte {#define-options}

Définir les options dans une feuille de calcul distincte

1. Créez une feuille de calcul :
   1. Accédez au dossier de votre projet AEM sur Microsoft® SharePoint ou dans le dossier Google Drive.
   1. Ajoutez une nouvelle feuille. Par exemple, « shared-country ».
1. Définissez les colonnes d’options :
ajoutez deux colonnes : « Option » et « Valeur ».
   - « Option » définit le texte affiché dans le menu déroulant.
   - La « Valeur » définit la valeur envoyée lorsqu’une personne sélectionne l’option.

   >[!NOTE]
   >
   >Si l’option et la valeur sont identiques, seule la colonne « Option » est requise.

1. Renseignez la feuille de calcul :
saisissez les options de votre pays dans la colonne « Option » (et la colonne « Valeur » si nécessaire).

   Reportez-vous à l’exemple ci-dessous pour la structure.

   ![Liste déroulante de pays](/help/forms/assets/drop-down-country-options.png)

1. Prévisualisez et publiez la feuille `shared-country` à l’aide d’[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   Par exemple, si le référentiel de votre projet s’appelle « wefinance », que la personne propriétaire du compte est « wkndform » et que vous utilisez la branche « main », l’URL affiche la feuille `shared-country` :
   `https://main--wefinance--wkndform.aem.live/enquiry.json?sheet=country`
   <!--(https://main--wefinance--wkndform.aem.live/enquiry.json?sheet=country)  -->

>[!NOTE]
>
> `?sheet=country` est un paramètre de requête ajouté à l’URL. Ce paramètre indique le code JSON filtré en fonction de la feuille `shared-country`. Il redirige vers le fichier JSON contenant des informations relatives à différents pays.

## Ajouter l’URL pour charger les options de liste déroulante{#add-url}

La propriété `Options` d’un champ `select` accepte une URL. L’URL renvoie un tableau JSON qui présente les options de la liste déroulante `Destination`. Pour ajouter l’URL aux options de liste déroulante de chargement, procédez comme suit :

1. Accédez au dossier de votre projet AEM sur Microsoft® SharePoint ou Google Drive et ouvrez votre feuille de calcul. Vous pouvez également créer une feuille de calcul pour un formulaire.
1. Copiez l’URL de la feuille `shared-country` et collez-la dans la colonne `Options` du champ `Destination`.

   ![Feuille de calcul de demande](/help/forms/assets/drop-down-enquiry.png)

1. Prévisualisez et publiez la feuille à l’aide d’[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).


   ![Liste déroulante de pays](/help/forms/assets/load-dropdown-options-form.png)

Vous pouvez faire référence à la [feuille de calcul de demande](/help/edge/assets/enquiry.xlsx) pour ajouter l’URL aux options de liste déroulante de chargement.

Après l’intégration de l’URL dans la définition de formulaire pour charger les options de liste déroulante, les options de la liste déroulante `Destination` commencent à s’afficher à partir de l’URL.

Par exemple, si le référentiel de votre projet s’appelle « wefinance », que la personne propriétaire du compte est « wkndforms » et que vous utilisez la branche « main », l’URL ci-dessous affiche le formulaire `enquiry` avec les options enregistrées dans une feuille séparée :

`https://main--wefinance--wkndform.aem.live/enquiry-form`



