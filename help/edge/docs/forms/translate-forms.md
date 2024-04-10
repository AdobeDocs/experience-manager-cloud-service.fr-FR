---
title: Traduire et localiser un formulaire AEM Forms Edge Delivery Services
description: Traduire et localiser un formulaire AEM Forms Edge Delivery Services
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 8a0c826f-8acc-4a00-bd84-7b0df9a82457
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 6%

---


# Traduire et localiser un formulaire AEM Forms Edge Delivery Services

Chez les Edge Delivery Services, la traduction de formulaires implique la conversion du contenu d’un formulaire d’une langue à une autre avec un accent mis sur la précision, la clarté et la cohérence. Les formulaires traduits ou localisés permettent à une audience plus large de s’étendre sur différents emplacements géographiques, améliorant ainsi l’expérience utilisateur et facilitant une meilleure communication entre les différentes préférences linguistiques.


À la fin de l’article, vous apprenez à :

* [Traduction de formulaires sur Google Drive](#translate-form-google-drive)
* [Traduction de formulaires dans le site SharePoint](#translate-form-sharepoint)

## Traduction de formulaires sur Google Drive {#translate-form-google-drive}

Le `GOOGLETRANSLATE` La fonction dans les feuilles Google traduit des formulaires en appuyant sur dans un outil de traduction intégré, ce qui permet de passer d’une langue à une autre directement dans une feuille Google. Pour traduire des formulaires dans Google Drive :

1. Accédez au dossier Projet AEM sur Google Drive et ouvrez votre feuille Google.
2. Renommer la feuille existante (`shared-default`) à `shared-en`.
3. Ajoutez une feuille nommée . `shared-default`. Le `shared-default` La feuille contient le contenu à localiser dans une langue spécifique.
4. Ajouter le contenu localisé dans le `shared-default` feuille utilisant `GOOGLETRANSLATE` fonction.
Vous pouvez utiliser une formule pour traduire le contenu de la cellule D2 à partir du `shared-en` feuille en français au sein du `shared-default` feuille. Voici la formule à utiliser :
   `=GOOGLETRANSLATE('shared-en'!D2,"en","fr")`

   ![Feuille de calcul de traduction de la recherche](/help/forms/assets/translate-enquiry-spreadsheet.png)

5. Prévisualiser et publier la feuille à l’aide de [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Vous pouvez vous reporter au [feuille de calcul](/help/forms/assets/enquirytranslate.xlsx) contenant la définition du formulaire pour une `enquiry` formulaire traduit de l&#39;anglais vers le français.

![Formulaire de demande traduit](/help/forms/assets/translate-form-french.png)

Reportez-vous à l’URL ci-dessous, où vous pouvez consulter le formulaire avec sa traduction en français : https://main--portal--wkndforms.hlx.live/enquirytranslate

## Traduction de formulaires dans le site SharePoint{#translate-form-sharepoint}

Pour traduire les formulaires sur le site Microsoft® SharePoint, vous devez modifier manuellement les libellés des champs à l’aide d’un service de traduction. Pour traduire les formulaires dans SharePoint Site :

1. Accédez au dossier Projet AEM sur Microsoft® SharePoint et ouvrez votre feuille de calcul.
2. Renommer la feuille existante (`shared-default`) à `shared-en`.
3. Ajoutez une feuille nommée . `shared-default`. Le `shared-default` La feuille contient le contenu à localiser dans une langue spécifique.
4. Ajouter le contenu localisé dans le `shared-default` feuille manuellement.

   ![Feuille de calcul de traduction de la recherche](/help/forms/assets/translate-enquiry-sp-spreadsheet.png)

5. Prévisualiser et publier la feuille à l’aide de [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Reportez-vous à la section [feuille de calcul](/help/forms/assets/enquirytranslate-sp.xlsx) contenant la définition du formulaire pour une `enquiry` formulaire traduit de l&#39;anglais vers le français.

![Formulaire de demande traduit](/help/forms/assets/translate-form-french.png)

Reportez-vous à l’URL ci-dessous, où vous pouvez consulter le formulaire avec sa traduction en français : https://main--wefinance--wkndforms.hlx.live/enquirytranslate

## Problèmes connus {#known-issues}

* Les libellés du formulaire sont traduits dans la langue localisée spécifiée dans le `shared-default` , mais les messages d’erreur s’affichent dans la langue par défaut du navigateur.

  ![Message d’erreur](/help/forms/assets/translate-error-message.png)

* Lorsque vous ouvrez le calendrier, la liste déroulante Calendrier s’affiche dans la langue par défaut du navigateur.

  ![Message d’erreur](/help/forms/assets/translate-calender-display.png)


## Questions fréquentes  {#faq}

**Q**: comment saisir une entrée dans la langue localisée spécifiée dans un formulaire ?

**A**: pour saisir du texte dans une langue localisée spécifique, ajustez les paramètres du clavier sur votre appareil. Consultez les liens suivants pour obtenir des instructions sur la manière de procéder :

* [Configurer votre Mac pour qu’il accepte les entrées dans une autre langue](https://support.apple.com/en-in/guide/mac-help/mchlp1406/mac)
* [Configurer Windows pour qu&#39;il accepte les entrées dans une autre langue](https://support.microsoft.com/en-us/windows/manage-the-input-and-display-language-settings-in-windows-12a10cb4-8626-9b77-0ccb-5013e0c7c7a2#:~:text=Select%20the%20Start%20%3E%20Settings%20%3E%20Time,you%20want%2C%20then%20select%20Options)
* [Configurez votre Android ou iPhone/iPad pour saisir des données dans une autre langue](https://support.google.com/gboard/answer/7068494?hl=en&amp;co=GENIE.Platform%3DAndroid)


**Q**: comment récupérer une liste de paramètres régionaux utilisés dans `GOOGLETRANSLATE` fonction ?

**A**: vous pouvez vous reporter au [documentation officielle de Google](https://cloud.google.com/translate/docs/languages) pour obtenir la liste complète des paramètres régionaux utilisés dans GOOGLETRANSLATE.

## Voir également

{{see-more-forms-eds}}

