---
title: Comment prévisualiser un formulaire adaptatif ?
description: Les utilisateurs peuvent prévisualiser le formulaire avant de le publier ou de l’activer, afin de s’assurer qu’il répond aux attentes. Les options d’aperçu peuvent varier selon les types de formulaire pris en charge.
topic-tags: author
role: Admin, Developer, User
feature: Adaptive Forms
source-git-commit: 6511c4273ca3d394d98a61e8acb4d3cb03c243d5
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 27%

---


# Prévisualisation d’un formulaire {#previewing-a-form}

## Présentation {#overview}

Dans [!DNL AEM Forms], vous pouvez prévisualiser les formulaires et les documents figurant dans le référentiel. L’aperçu permet de savoir exactement à quoi ressemblent les formulaires lorsqu’ils sont publiés pour les utilisateurs finaux.

Lors de la prévisualisation de formulaires, ils sont rendus dans l’interface interactive et l’utilisateur peut les remplir avec des données. Lors de la prévisualisation de documents, ils sont rendus en mode non interactif et l’utilisateur peut uniquement afficher le document. Pour les formulaires, une option supplémentaire d’aperçu personnalisé est disponible. Grâce à cette option, vous pouvez prévisualiser le formulaire à l’aide des données d’un fichier XML. Les données remplissent certains champs ou tous les champs du formulaire prévisualisé.

Le tableau ci-dessous répertorie les options d’aperçu disponibles pour les différents types de formulaire pris en charge :

<table>
 <tbody>
  <tr>
   <td><strong>Type de ressource</strong><br /> </td>
   <td><strong>Options d’aperçu disponibles</strong><br /> </td>
  </tr>
  <!--<tr>
   <td>Document</td>
   <td>PDF preview</td>
  </tr>-->
  <tr>
   <td>Formulaire PDF</td>
   <td>Aperçu au format PDF et aperçu avec des données<br /> </td>
  </tr>
  <tr>
   <td>Formulaire adaptatif</td>
   <td>Aperçu des HTMLs et aperçu des HTMLS avec des données</td>
  </tr>
  <!--<tr>
   <td>Form Template</td>
   <td>PDF preview, PDF preview with Data, HTML preview, HTML preview with Data<br /> </td>
  </tr>-->
 </tbody>
</table>

## Prévisualisation d’un formulaire {#previewing-a-form-1}

1. Sélectionnez une ressource à prévisualiser, puis cliquez sur Aperçu. ![aem6forms_preview](assets/aem6forms_preview.png) dans la barre d’outils actions.

   >[!NOTE]
   >
   >Pour sélectionner une ressource, basculez vers la vue Liste à partir de la vue Carte par défaut. Cliquez sur ![aem6forms_viewlist](assets/aem6forms_viewlist.png) ou ![aem6forms_viewcard](assets/aem6forms_viewcard.png) pour changer de vue.

1. Cliquez sur Aperçu pour afficher la liste des options d’aperçu applicables au type de ressource sélectionné. Cliquez sur l’option souhaitée pour effectuer le rendu de la ressource sélectionnée dans un nouvel onglet.

   Vous avez le choix entre :

   * Prévisualiser au format HTML
   * Aperçu avec des données
     <!--* Preview as PDF (available for form templates)-->

## Aperçu avec des données {#preview-with-data}

Lorsque vous sélectionnez **Aperçu avec des données**, vous pouvez voir à quoi ressemble le formulaire avec des données réelles saisies. L&#39;option Aperçu avec données permet de télécharger un fichier XML contenant des exemples de données utilisateur. Les exemples de données utilisateur sont utilisés pour remplir le formulaire d’aperçu au format que vous choisissez.

1. Sélectionnez une ressource, cliquez sur Aperçu ![aem6forms_preview](assets/aem6forms_preview.png), puis sélectionnez **Aperçu avec des données**.
1. Dans la boîte de dialogue Aperçu du formulaire, fournissez FormData en tant que fichier XML. Cliquez sur Aperçu pour effectuer le rendu du formulaire avec les données fusionnées du code XML.

