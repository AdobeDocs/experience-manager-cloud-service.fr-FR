---
title: Publication d’un formulaire AEM Forms Edge Delivery Services
description: Publication d’un formulaire AEM Forms Edge Delivery Services
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 3b24d0cd4099e0b8eb48c977f460b25c168af220
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Publier le formulaire

Une fois que vous êtes prêt à partager votre formulaire avec vos clients pour la collecte ou l’envoi de données, vous pouvez simplement le publier, ce qui rend le formulaire facilement disponible pour que vos clients l’utilisent.

## Prérequis

* La variable [Le bloc de formulaire est activé pour votre projet EDS sur Github.](/help/edge/docs/forms/create-forms.md).
* Votre formulaire est entièrement testé et prêt à l’emploi.
* Votre [la feuille de calcul est configurée.](/help/edge/docs/forms/submit-forms.md) pour accepter les données.

## Publier le formulaire

Pour publier le formulaire :

1. Accédez à votre compte Microsoft SharePoint ou Google Drive et accédez à votre `[AEM Edge Delivery project directory]`.

1. Ouvrez un fichier document dans lequel vous avez l’intention d’incorporer le formulaire. Par exemple, vous pouvez ouvrir le fichier d’index ou créer un nouveau document.

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

1. Utilisation [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) pour prévisualiser la page. La page affiche désormais le formulaire. Par exemple, voici le formulaire basé sur le [feuille de calcul d&#39;enquête](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![Exemple de formulaire EDS](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

   Désormais, vos clients peuvent remplir le formulaire et l’envoyer.

## Résolution des problèmes

+++ Impossible d’envoyer les données au formulaire

Si vous rencontrez une erreur ressemblant au message suivant, cela indique que la feuille de calcul n’est pas encore configurée pour accepter les données envoyées.

![erreur lors de l’envoi du formulaire](/help/edge/assets/form-error.png)

+++


## En savoir plus

* [Créer et prévisualiser un formulaire](/help/edge/docs/forms/create-forms.md)
* [Activer le formulaire pour envoyer des données](/help/edge/docs/forms/submit-forms.md)
* [Publier un formulaire sur la page de sites](/help/edge/docs/forms/publish-eds-forms.md)
* [Ajouter des validations à des champs de formulaire](/help/edge/docs/forms/validate-forms.md)
* [Modifier les thèmes et le style du formulaire](/help/edge/docs/forms/style-theme-forms.md)