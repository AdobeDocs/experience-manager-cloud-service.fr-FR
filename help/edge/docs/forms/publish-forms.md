---
title: Publier un Edge Delivery Services pour AEM Forms
description: Publier un Edge Delivery Services pour AEM Forms
feature: Edge Delivery Services
exl-id: dcb16da1-dcc2-4529-8859-0716e727b54d
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 100%

---

# Publier votre formulaire et commencer à collecter des données

Une fois que vous êtes en mesure de partager votre formulaire avec vos clientes et clients pour la collecte ou l’envoi de données, vous pouvez simplement le publier, ce qui le rend instantanément disponible pour une utilisation par vos clientes et clients.

![Écosystème de création basé sur des documents](/help/edge/assets/document-based-authoring-workflow-publish-form.png)

## Conditions préalables

- Vous disposez d’un projet AEM basé sur [le modèle standard AEM Forms](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) ou vous avez [ajouté un bloc de formulaire adaptatif à votre projet AEM existant](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project)
- Votre formulaire a été entièrement testé et est prêt à l’emploi.
- Votre [feuille de calcul est configurée](/help/edge/docs/forms/submit-forms.md) pour accepter les données.


## Publier votre formulaire

+++ &#x200B;1. Publier votre feuille de calcul

1. Ouvrez votre compte Microsoft SharePoint ou votre compte Google Drive et accédez au répertoire de votre projet AEM Edge Delivery.

1. Ouvrez la feuille de calcul qui contient votre formulaire. Par exemple, le classeur Microsoft Excel de formulaires [enquiry](/help/edge/assets/enquiry.xlsx).

1. Utilisez [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser la feuille.

   ![Utilisation d’AEM Sidekick pour prévisualiser la feuille](/help/edge/assets/preview-form.png)

   Une fois la prévisualisation réussie, le contenu de la feuille de calcul est converti au format JSON. La page de prévisualisation affiche ensuite ce contenu sous forme de tableau structuré. Par exemple, l’image ci-contre illustre le contenu d’un formulaire de type « demande ».

   ![Prévisualisation de formulaire au format JSON](/help/edge/assets/forms-preview-json-format.png)

1. Utilisez AEM Sidekick pour publier la feuille. Assurez-vous de noter l’URL de publication, car elle est nécessaire pour le rendu du formulaire dans la section suivante. Le format de l’URL se présente comme suit :


   ```JSON
       https://<branch>--<repository>--<owner>.aem.live/<form>.json
   ```

   - `<branch>` fait référence à la branche de votre référentiel GitHub.
   - `<repository>` indique votre référentiel GitHub.
   - `<owner>` fait référence au nom d’utilisateur ou d’utilisatrice de votre compte GitHub qui héberge votre référentiel GitHub.

   Par exemple, si le référentiel de votre projet est nommé « wefinance », qu’il se trouve dans le compte « wkndform », que vous utilisez la branche « main » et le formulaire « enquiry », l’URL ressemble à ceci :

   `https://main--wefinance--wkndform.aem.live/enquiry.json`
&lt;!—(https://main--wefinance--wkndform.aem.live/enquiry.json)-->

+++

+++ &#x200B;2. Ajouter le formulaire à votre page web

Ajoutez `<form>.json` à une page web pour faciliter l’interaction client, ce qui permet aux utilisateurs et aux utilisatrices de remplir et d’envoyer le formulaire sans effort.


Pour ajouter le formulaire à votre page web :

1. Accédez à votre compte Microsoft SharePoint ou à votre compte Google Drive et accédez à votre `[AEM Edge Delivery project directory]`.

1. Ouvrez un document dans lequel vous avez l’intention d’incorporer le formulaire. Vous pouvez, par exemple, ouvrir le fichier [enquiry-form.docx](/help/edge/assets/enquiry-form.docx) ou créer un nouveau document.

1. Identifiez la section du document dans laquelle vous souhaitez insérer le formulaire puis accédez-y.

1. Ajoutez un bloc nommé « Formulaire » au fichier. Par exemple, si le référentiel de votre projet s’appelle « wefinance », la personne propriétaire du compte est « wkndforms » et vous utilisez la branche « main ».

   | Formulaire |
   |---|
   | `https://main--wefinance--wkndform.aem.live/enquiry.json` |

   ![Ajout d’un bloc nommé « Formulaire » au fichier](/help/edge/assets/enquiry-doc-to-embed-form.png)

   Ce bloc sert d’espace réservé à l’emplacement où le formulaire est incorporé. Dans la deuxième ligne du bloc, ajoutez l’URL de votre fichier `<form>.json` comme lien hypertexte.

   >[!IMPORTANT]
   >
   >
   > Assurez-vous que l’URL est formatée en tant que lien hypertexte et non sous forme de texte brut.

   Utilisez l’URL de prévisualisation (URL .page) à des fins de développement ou de test, ou l’URL de publication (.live) pour la production.

   Par exemple, si le référentiel de votre projet s’appelle « wefinance », la personne propriétaire du compte est « wkndforms » et vous utilisez la branche « main ».

   Voici quelques exemples d’URL de prévisualisation et de publication :

   **URL de prévisualisation**

   | Formulaire |
   |---|
   | `https://main--wefinance--wkndform.aem.page/enquiry.json` |


   **URL de publication**

   | Formulaire |
   |---|
   | `https://main--wefinance--wkndform.aem.live/enquiry.json` |

1. Utilisez [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser la page web. La page affiche désormais le formulaire. Par exemple, voici le formulaire basé sur la [feuille de calcul de demande](/help/edge/assets/enquiry-form.docx) :


   ![Exemple de formulaire EDS](/help/edge/assets/updated-form.png)

1. Utilisez AEM Sidekick pour publier le formulaire. Désormais, vos clientes et clients peuvent remplir le formulaire et l’envoyer.

+++ 

## Résolution des problèmes

+++ Impossible d’envoyer les données au formulaire

Si vous rencontrez une erreur similaire au message suivant, cela indique que la feuille de calcul n’est pas encore configurée pour [accepter les données envoyées](/help/edge/docs/forms/submit-forms.md).

![Erreur lors de l’envoi du formulaire](/help/edge/assets/form-error.png)

+++



