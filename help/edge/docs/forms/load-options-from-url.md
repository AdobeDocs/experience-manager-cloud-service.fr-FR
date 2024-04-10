---
title: Charger les options de liste déroulante à partir de l’URL
description: Les options de liste déroulante sont incluses dans une feuille de calcul distincte, puis importées dans la feuille de calcul principale via l’URL fournie.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 2%

---


# Charger les options de liste déroulante à partir de l’URL

Dans les formulaires Edge Delivery Services, les utilisateurs ont la possibilité de sélectionner une valeur dans un ensemble prédéfini d’options. Les auteurs de formulaires utilisent `select` , qui fournit une liste de choix.
Par exemple, le `enquiry` le formulaire propose un menu déroulant pour sélectionner les pays, offrant ainsi aux utilisateurs une gamme de pays prédéfinis. Vous pouvez voir que cette liste comprend une longue liste de pays séparés par des virgules.

![Options des listes déroulantes](/help/forms/assets/drop-down-options.png)

La gestion de longues listes d’options pour les menus déroulants peut s’avérer fastidieuse lors de leur ajout direct dans la feuille contenant la définition du formulaire. La création d’une feuille distincte pour stocker ces options de liste déroulante peut simplifier et rationaliser le processus. Cette feuille agit comme un référentiel centralisé pour toutes les options de liste déroulante, organisées dans un format structuré. Chaque option est répertoriée dans sa propre ligne, ce qui facilite sa gestion et ses mises à jour.

Explorons l’amélioration du processus de création de formulaires en chargeant la liste d’options à partir d’une autre feuille de calcul via une URL.

À la fin de cet article, vous saurez :

* [Définir des options dans une feuille de calcul distincte](#define-options)
* [Ajouter une URL pour charger les options de liste déroulante](#add-url)

## Définition des options dans une feuille séparée {#define-options}

Créez une feuille à deux colonnes :`Option` et `Value`, pour définir les options :

1. Accédez au dossier Projet AEM sur Microsoft® SharePoint ou au dossier Google Drive.
2. Ajoutez une feuille nommée . `shared-country` sur le site Microsoft® SharePoint ou dans votre dossier Google Drive, ajoutez les éléments suivants :

   * **Option**: représente les valeurs d’affichage des options du menu déroulant.
   * **Valeur**: représente la valeur envoyée lorsqu’un utilisateur ou une utilisatrice sélectionne l’option.

   >[!NOTE]
   >
   > Si la valeur et l’option d’une option déroulante sont identiques, la feuille de calcul ne peut contenir que les **Option** colonne.

   Ajoutons une nouvelle feuille, [pays partagé](/help/forms/assets/enquiry-options.xlsx) pour les options affichées dans `Destination` liste déroulante dans le `enquiry` formulaire.

   Reportez-vous à l’illustration ci-dessous, qui représente le `shared-country` feuille de calcul :

   ![Liste déroulante par pays](/help/forms/assets/drop-down-country-options.png)
3. Prévisualiser et publier le `shared-country` feuille utilisant [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   Reportez-vous à l’URL qui présente le `shared-country` feuille : https://main--wefinance--wkndforms.hlx.live/enquiry.json?sheet=country

>[!NOTE]
>
> `?sheet=country` est un paramètre de requête ajouté à l’URL. Ce paramètre indique le filtre JSON en fonction de `shared-country` feuille. Il redirige vers le fichier JSON contenant des informations relatives aux différents pays.

## Ajouter une URL pour charger les options de liste déroulante{#add-url}

Le `Options` propriété d&#39;un `select` Le champ accepte une URL. L’URL renvoie un tableau JSON utilisé comme options pour la variable `Destination` liste déroulante. Pour ajouter l&#39;URL pour charger les options de liste déroulante :

1. Accédez au dossier de votre projet AEM sur Microsoft® SharePoint ou Google Drive et ouvrez votre feuille de calcul. Vous pouvez également créer une feuille de calcul pour un formulaire.
1. Copiez l’URL de `shared-country` feuille et collez-la dans le `Options` colonne pour le `Destination` champ .

   ![Feuille de calcul de demande](/help/forms/assets/drop-down-enquiry.png)

1. Prévisualiser et publier la feuille à l’aide de [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).


   ![Liste déroulante par pays](/help/forms/assets/load-dropdown-options-form.png)

Vous pouvez vous reporter au [feuille de calcul des demandes](/help/forms/assets/enquiry-options.xlsx) pour ajouter l’URL pour charger les options de liste déroulante.

Après l’intégration de l’URL dans la définition du formulaire pour charger les options de liste déroulante, les options de la `Destination` La liste déroulante commence à apparaître à partir de l’URL.

Reportez-vous à l’URL ci-dessous, qui affiche le `enquiry` formulaire affichant les options enregistrées dans la feuille séparée :

https://main--wefinance--wkndforms.hlx.live/enquiry-form

## Voir également

{{see-more-forms-eds}}


