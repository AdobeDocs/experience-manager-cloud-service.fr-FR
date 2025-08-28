---
title: Traduire et localiser un Edge Delivery Services pour AEM Forms
description: Traduire et localiser un Edge Delivery Services pour AEM Forms
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 8a0c826f-8acc-4a00-bd84-7b0df9a82457
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: ht
source-wordcount: '544'
ht-degree: 100%

---


# Traduire et localiser un Edge Delivery Services pour AEM Forms

Dans Edge Delivery Services, la traduction d’un formulaire implique de convertir le contenu du formulaire d’une langue à une autre en mettant l’accent sur la précision, la clarté et la cohérence. Les formulaires traduits ou localisés permettent d’atteindre une audience plus large répartie sur différents emplacements géographiques, améliorant ainsi l’expérience d’utilisation et permettant une meilleure communication entre les différentes préférences linguistiques.


À la fin de cet article, vous saurez accomplir ce qui suit :

- [Traduire des formulaires dans Google Drive](#translate-form-google-drive)
- [Traduire des formulaires dans un site SharePoint](#translate-form-sharepoint)

## Traduire des formulaires dans Google Drive {#translate-form-google-drive}

La fonction `GOOGLETRANSLATE` dans Google Sheets traduit les formulaires en s’appuyant sur un outil de traduction intégré, en traduisant le texte d’une langue à une autre directement dans une feuille Google Sheets. Pour traduire des formulaires dans Google Drive, effectuez les actions suivantes :

1. Accédez à votre dossier de projet AEM dans Google Drive et ouvrez votre feuille Google Sheets.
2. Renommez la feuille existante (`shared-default`) en `shared-en`.
3. Ajoutez une feuille nommée `shared-default`. La feuille `shared-default` contient le contenu pour une localisation vers une langue spécifique.
4. Ajoutez le contenu localisé dans la feuille `shared-default` à l’aide de la fonction `GOOGLETRANSLATE`.
Vous pouvez utiliser une formule pour traduire en français le contenu de la cellule D2 de la feuille `shared-en` dans la feuille `shared-default`. Voici la formule à utiliser :
   `=GOOGLETRANSLATE('shared-en'!D2,"en","fr")`

   ![Feuille de calcul de traduction de demande](/help/forms/assets/translate-enquiry-spreadsheet.png)

5. Prévisualisez et publiez la feuille à l’aide d’[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Vous pouvez vous référer à la [feuille de calcul](/help/forms/assets/enquirytranslate.xlsx) qui contient la définition du formulaire pour un formulaire `enquiry` traduit de l’anglais vers le français.

![Formulaire de demande traduit](/help/forms/assets/translate-form-french.png)

Reportez-vous à l’URL ci-dessous pour consulter le formulaire ainsi que sa traduction en français : https://main--portal--wkndforms.hlx.live/enquirytranslate

## Traduire des formulaires dans un site SharePoint{#translate-form-sharepoint}

Pour traduire les formulaires dans un site Microsoft® SharePoint, vous devez modifier manuellement les libellés des champs à l’aide de n’importe quel service de traduction. Pour traduire les formulaires dans un site SharePoint, effectuez les actions suivantes :

1. Accédez à votre dossier de projet AEM sur Microsoft® SharePoint et ouvrez votre feuille de calcul.
2. Renommez la feuille existante (`shared-default`) en `shared-en`.
3. Ajoutez une feuille nommée `shared-default`. La feuille `shared-default` contient le contenu pour une localisation vers une langue spécifique.
4. Ajoutez manuellement le contenu localisé dans la feuille `shared-default`.

   ![Feuille de calcul de traduction de demande](/help/forms/assets/translate-enquiry-sp-spreadsheet.png)

5. Prévisualisez et publiez la feuille à l’aide d’[AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Vous pouvez vous référer à la [feuille de calcul](/help/forms/assets/enquirytranslate-sp.xlsx) qui contient la définition de formulaire pour un formulaire `enquiry` traduit de l’anglais vers le français.

![Formulaire de demande traduit](/help/forms/assets/translate-form-french.png)

Reportez-vous à l’URL ci-dessous pour consulter le formulaire ainsi que sa traduction en français : https://main--wefinance--wkndforms.hlx.live/enquirytranslate

## Problèmes connus {#known-issues}

- Les libellés du formulaire sont traduits dans la langue localisée spécifiée dans la feuille `shared-default`, mais les messages d’erreur s’affichent dans la langue par défaut du navigateur.

  ![Message d’erreur](/help/forms/assets/translate-error-message.png)

- Lorsque vous ouvrez le calendrier, la liste déroulante du calendrier s’affiche dans la langue par défaut du navigateur.

  ![Message d’erreur](/help/forms/assets/translate-calender-display.png)


## Questions fréquentes {#faq}

**Question** : comment saisir une entrée dans la langue localisée spécifiée d’un formulaire ?

**Réponse** : pour saisir du texte dans une langue localisée spécifique, ajustez les paramètres du clavier de votre appareil. Reportez-vous aux liens suivants pour obtenir des instructions sur la manière de procéder :

- [Configurer votre appareil Mac pour saisir des données dans une autre langue](https://support.apple.com/fr-fr/guide/mac-help/mchlp1406/mac)
- [Configurer votre appareil Windows pour saisir des données dans une autre langue](https://support.microsoft.com/fr-fr/windows/manage-the-input-and-display-language-settings-in-windows-12a10cb4-8626-9b77-0ccb-5013e0c7c7a2#:~:text=Select%20the%20Start%20%3E%20Settings%20%3E%20Time,you%20want%2C%20then%20select%20Options)
- [Configurer votre appareil Android ou votre iPhone/iPad pour saisir des données dans une autre langue](https://support.google.com/gboard/answer/7068494?hl=fr&co=GENIE.Platform%3DAndroid)


**Question** : comment puis-je récupérer une liste de paramètres régionaux utilisés dans la fonction `GOOGLETRANSLATE` ?

**Réponse** : vous pouvez vous reporter à la [documentation officielle de Google](https://cloud.google.com/translate/docs/languages) pour obtenir une liste complète des paramètres régionaux utilisés dans GOOGLETRANSLATE.


