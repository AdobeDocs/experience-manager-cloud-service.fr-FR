---
title: Charger les options de liste déroulante depuis l’URL
description: Les options de la liste déroulante sont incluses dans une feuille de calcul distincte, puis importées dans la feuille de calcul principale via l’URL fournie.
feature: Edge Delivery Services
source-git-commit: 2affe155b285986128487043fcc4f2938fc15842
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 3%

---


# Options de la liste déroulante Charger à partir de l’URL

Forms comprend souvent des menus déroulants que les utilisateurs peuvent sélectionner parmi des options prédéfinies. Ces options sont généralement définies dans le formulaire lui-même, mais la gestion de listes longues peut être encombrante. Ce guide explique comment améliorer la création de formulaires en chargeant les options de liste déroulante à partir d’une feuille de calcul distincte via une URL.


Les avantages du chargement d’une liste déroulante depuis une feuille de calcul distincte sont les suivants :

* Gestion simplifiée : conservez les options de liste déroulante dans un emplacement centralisé pour des mises à jour et des ajouts plus simples.
* Efficacité améliorée : évitez d’ajouter manuellement de longues listes d’options dans la définition de formulaire.




![Options de liste déroulante](/help/forms/assets/drop-down-options.png)


À la fin de cet article, vous saurez :

* [Définition des options dans une feuille de calcul distincte](#define-options)
* [Ajout d’une URL pour charger les options de liste déroulante](#add-url)

## Définition des options dans une feuille distincte {#define-options}

Définition des options dans une feuille de calcul distincte

1. Créer une feuille de calcul :
   1. Recherchez votre dossier de projet AEM dans Microsoft® SharePoint ou Google Drive.
   1. Ajoutez une nouvelle feuille. Par exemple, &quot;pays partagé&quot;.
1. Définir les colonnes d’options : ajoutez deux colonnes : &quot;Option&quot; et &quot;Valeur&quot;.
   * &quot;Option&quot; définit le texte affiché dans le menu déroulant.
   * &quot;Valeur&quot; définit la valeur envoyée lorsqu’un utilisateur sélectionne l’option.

   >[!NOTE]
   >
   >Si l’option et la valeur sont identiques, seule la colonne &quot;Option&quot; est requise.

1. Renseignez la feuille de calcul : saisissez les options de votre pays dans la colonne &quot;Option&quot; (et la colonne &quot;Valeur&quot; si nécessaire).

   Reportez-vous à l’exemple ci-dessous pour la structure.

   ![Liste déroulante pour le pays](/help/forms/assets/drop-down-country-options.png)

1. Prévisualiser et publier le `shared-country` feuille utilisant [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   Reportez-vous à l’URL qui présente la variable `shared-country` sheet : https://main—wefinance—wkndforms.hlx.live/enquiry.json?sheet=country

>[!NOTE]
>
> `?sheet=country` est un paramètre de requête ajouté à l’URL. Ce paramètre indique le code JSON filtré en fonction de la variable `shared-country` feuille. Il redirige vers le fichier JSON contenant des informations relatives à différents pays.

## Ajout d’une URL pour charger les options de liste déroulante{#add-url}

La variable `Options` d’une propriété `select` accepte une URL. L’URL renvoie un tableau JSON utilisé comme options pour la variable `Destination` liste déroulante. Pour ajouter les options de liste déroulante URL à charger :

1. Accédez à votre dossier de projet AEM sur Microsoft® SharePoint ou Google Drive et ouvrez votre feuille de calcul. Vous pouvez également créer une feuille de calcul pour un formulaire.
1. Copiez l’URL de `shared-country` et collez-la dans la feuille `Options` de la colonne `Destination` champ .

   ![Feuille de calcul de demande](/help/forms/assets/drop-down-enquiry.png)

1. Prévisualiser et publier la feuille à l’aide de [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).


   ![Liste déroulante pour le pays](/help/forms/assets/load-dropdown-options-form.png)

Vous pouvez consulter la section [feuille de calcul d&#39;enquête](/help/forms/assets/enquiry-options.xlsx) pour ajouter les options de liste déroulante URL à charger.

Après l’intégration de l’URL dans la définition de formulaire pour charger les options de liste déroulante, les options de la variable `Destination` début de la liste déroulante à partir de l’URL.

Reportez-vous à l’URL ci-dessous, qui affiche la variable `enquiry` formulaire affichant les options enregistrées dans la feuille distincte :

https://main--wefinance--wkndforms.hlx.live/enquiry-form

## Voir également

{{see-more-forms-eds}}


