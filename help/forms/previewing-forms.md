---
title: Comment prévisualiser un formulaire adaptatif ?
description: Les utilisateurs peuvent prévisualiser le formulaire avant de le publier ou de l’activer, afin de s’assurer qu’il répond aux attentes. Les options de prévisualisation peuvent varier selon les types de formulaire pris en charge.
topic-tags: author
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 72235277-6c34-4341-9a10-02afa753e7f5
source-git-commit: 05548d56d791584781606b02839c5602b4469f7b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 84%

---

# Prévisualisation d’un formulaire {#previewing-a-form}

## Présentation {#overview}

Dans [!DNL AEM Forms], vous pouvez prévisualiser les formulaires et les documents figurant dans le référentiel. La prévisualisation permet de savoir exactement à quoi ressemblent les formulaires lorsqu’ils sont publiés pour les utilisatrices et utilisateurs finaux.

Lors de la prévisualisation de formulaires, ils sont rendus dans l’interface interactive et l’utilisateur ou l’utilisatrice peut les remplir avec des données. Lors de la prévisualisation de documents, ils sont rendus en mode non interactif et l’utilisateur ou l’utilisatrice peut uniquement les afficher. Pour les formulaires, une option supplémentaire de prévisualisation personnalisée est disponible. Grâce à cette option, vous pouvez prévisualiser le formulaire à l’aide des données d’un fichier XML. Les données remplissent certains champs ou tous les champs du formulaire prévisualisé.

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
   <td>Prévisualisation HTML et prévisualisation HTML avec des données</td>
  </tr>
  <!--<tr>
   <td>Form Template</td>
   <td>PDF preview, PDF preview with Data, HTML preview, HTML preview with Data<br /> </td>
  </tr>-->
 </tbody>
</table>

## Prévisualiser un formulaire {#previewing-a-form-1}

1. Sélectionnez une ressource à prévisualiser, puis cliquez sur Aperçu ![aem6forms_preview](assets/aem6forms_preview.png) dans la barre d’outils des actions.

   >[!NOTE]
   >
   >Pour sélectionner une ressource, basculez vers la vue Liste à partir de la vue Carte par défaut. Cliquez sur ![aem6forms_viewlist](assets/aem6forms_viewlist.png) ou ![aem6forms_viewcard](assets/aem6forms_viewcard.png) pour changer de vue.

1. Lorsque vous cliquez sur Aperçu, les options d’aperçu applicables pour le type d’actif sélectionné sont affichées. Cliquez sur l’option souhaitée pour effectuer le rendu de la ressource sélectionnée dans un nouvel onglet.

   Vous avez le choix entre :

   * Prévisualiser au format HTML
   * Aperçu avec des données
     <!--* Preview as PDF (available for form templates)-->

## Aperçu avec des données {#preview-with-data}

Lorsque vous sélectionnez **Aperçu avec des données**, vous pouvez voir à quoi ressemble le formulaire avec des données réelles saisies. L&#39;option Aperçu avec des données vous permet de charger un fichier XML contenant des exemples de données utilisateur. Les exemples de données utilisateur sont utilisés pour remplir le formulaire prévisualisé au format que vous choisissez.

1. Sélectionnez une ressource, cliquez sur Aperçu ![aem6forms_preview](assets/aem6forms_preview.png), puis sélectionnez **Aperçu avec des données**.
1. Dans la boîte de dialogue Aperçu du formulaire, fournissez FormData en tant que fichier XML. Cliquez sur Aperçu pour effectuer le rendu du formulaire avec les données fusionnées du fichier XML.
