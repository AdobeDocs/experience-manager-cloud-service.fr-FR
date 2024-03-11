---
title: Publication d’un formulaire AEM Forms Edge Delivery Services
description: Publication d’un formulaire AEM Forms Edge Delivery Services
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: dcb16da1-dcc2-4529-8859-0716e727b54d
source-git-commit: 4144f9704aaf17ea684be147395adc3aa31641f2
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 2%

---

# Publier le formulaire

Une fois que vous êtes prêt à partager votre formulaire avec vos clients pour la collecte ou l’envoi de données, vous pouvez simplement le publier, ce qui rend le formulaire facilement disponible pour que vos clients l’utilisent.

![Écosystème de création basé sur les documents](/help/edge/assets/document-based-authoring-workflow-publish-form.png)

## Prérequis

* La variable [Le bloc Forms adaptatif est activé pour votre projet EDS sur GitHub.](/help/edge/docs/forms/create-forms.md).
* Votre formulaire est entièrement testé et prêt à l’emploi.
* Votre [la feuille de calcul est configurée.](/help/edge/docs/forms/submit-forms.md) pour accepter les données.

## Publier le formulaire

+++ 1. Publiez votre feuille de calcul

1. Ouvrez votre compte Microsoft SharePoint ou Google Drive et accédez au répertoire de votre projet Edge Delivery AEM.

1. Ouvrez la feuille de calcul qui comporte votre formulaire. Par exemple, la variable `enquiry` formulaire classeur Excel Microsoft.

1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser la feuille.

   ![Utilisez AEM Sidekick pour prévisualiser la feuille](/help/edge/assets/preview-form.png)

   Une fois l’opération d’aperçu terminée, le contenu de la feuille de calcul est converti au format JSON. La page d’aperçu présente ensuite ce contenu dans un format de tableau structuré. Par exemple, l&#39;image qui l&#39;accompagne illustre le contenu d&#39;un formulaire de &quot;demande&quot;.

   ![Forms Preview JSON Format](/help/edge/assets/forms-preview-json-format.png)

1. Utilisez AEM Sidekick pour publier la feuille. Veillez à capturer l’URL de publication, car cela est nécessaire pour le rendu du formulaire dans la section suivante. Le format d’URL se présente comme suit :


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   ```

   * `<branch>` fait référence à la branche de votre référentiel GitHub.
   * `<repository>` indique votre référentiel GitHub.
   * `<owner>` fait référence au nom d’utilisateur de votre compte GitHub qui héberge votre référentiel GitHub.

   Par exemple, si le référentiel de votre projet est nommé &quot;portal&quot;, il se trouve sous le compte &quot;wkndforms&quot; et que vous utilisez la branche &quot;main&quot;, l’URL ressemble à ce qui suit :

   `https://main--portal--wkndforms.hlx.page/enquiry.json`

+++

+++ 2. Ajoutez le formulaire à votre page web

Ajoutez la variable `<form>.json` sur une page web pour faciliter l’interaction client, ce qui permet aux utilisateurs de remplir et envoyer le formulaire sans effort.


Pour ajouter le formulaire à votre page web :

1. Accédez à votre compte Microsoft SharePoint ou Google Drive et accédez à votre `[AEM Edge Delivery project directory]`.

1. Ouvrez un fichier document dans lequel vous avez l’intention d’incorporer le formulaire. Vous pouvez, par exemple, ouvrir le `index.docx` ou créer un document.

1. Identifiez la section souhaitée dans le document où vous souhaitez insérer le formulaire et accédez-y en conséquence.

1. Ajoutez un bloc nommé &quot;Form&quot; au fichier, comme dans l&#39;exemple ci-dessous :

   | Formulaire |
   |---|
   | [https://main—portal—wkndforms.hlx.live/enquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json) |

   Ce bloc sert d’espace réservé où le formulaire est incorporé. Dans la deuxième ligne du bloc, ajoutez l’URL de votre `<form>.json` comme lien hypertexte.

   >[!IMPORTANT]
   >
   >
   > Assurez-vous que l’URL est formatée en tant que lien hypertexte plutôt que sous la forme de texte brut.

   Utilisez l’URL d’aperçu (.page URL) à des fins de développement ou de test, ou l’URL de publication (.live) en production. Voici quelques exemples d’URL de prévisualisation et de publication :

   **URL de prévisualisation**
| Formulaire | |— | [https://main—portal—wkndforms.hlx.page/enquiry.json](https://main--portal--wkndforms.hlx.page/enquiry.json)  |


   **URL de publication**
| Formulaire | |— | [https://main—portal—wkndforms.hlx.live/enquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json)  |

1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser la page web. La page affiche désormais le formulaire. Par exemple, voici le formulaire basé sur le [feuille de calcul d&#39;enquête](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![Exemple de formulaire EDS](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

1. Utilisez AEM Sidekick pour publier le formulaire. Désormais, vos clients peuvent remplir le formulaire et l’envoyer.

+++

## Résolution des problèmes

+++ Impossible d’envoyer les données au formulaire

Si vous rencontrez une erreur ressemblant au message suivant, cela indique que la feuille de calcul n’est pas configurée pour [accepter les](/help/edge/docs/forms/submit-forms.md) données pour l’instant.

![erreur lors de l’envoi du formulaire](/help/edge/assets/form-error.png)

+++


## Voir également

{{see-more-forms-eds}}
