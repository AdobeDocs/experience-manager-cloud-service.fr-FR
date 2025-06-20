---
title: Publication de contenu avec l’éditeur de page
description: Découvrez comment l’éditeur de page publie du contenu.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 5871e04d3bd78bdd8df55d42e7619c98ea3f38ca
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 50%

---


# Publication de contenu avec l’éditeur de sites {#publishing}

Découvrez comment l’éditeur de page publie du contenu.

## Publication à partir de l’éditeur de page {#publishing-from-the-page-editor}

Si vous modifiez une page dans l’[éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md), elle peut être publiée directement à partir de l’éditeur.

1. Sélectionnez l’icône **Informations sur la page** pour ouvrir le menu, puis sélectionnez l’option **Publier la page**.

   ![Publication d’une page via les options de page](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. Selon que la page comporte des références qui doivent être publiées :

   * La page est publiée directement, s’il n’y a aucune référence à publier.
   * Si la page comporte des références à publier, celles-ci sont répertoriées dans l’assistant **Publier**, où vous pourrez accomplir ce qui suit :
      * Indiquez les ressources, balises ou autres que vous souhaitez publier avec la page, puis utilisez **Publier** pour terminer le processus.
      * Sélectionner **Annuler** pour abandonner l’opération.

   ![Publication de références avec la page](/help/sites-cloud/authoring/assets/publishing-references.png)

1. L’option **Publier** réplique la page dans l’environnement de publication. Une bannière d’informations est affichée dans l’éditeur de page pour confirmer l’opération de publication.

   ![Bannière d’informations sur l’état de publication](/help/sites-cloud/authoring/assets/publishing-info.png)

   Lorsque vous affichez la même page dans la console, l’état de publication mis à jour est visible.

   ![État de publication de la page dans le mode d’affichage Colonnes de la console Sites](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>Une publication à partir de l’éditeur de page est une publication superficielle, c’est-à-dire que seules la ou les pages sélectionnées sont publiées alors que les pages enfants ne le sont pas.

>[!NOTE]
>
>Les pages accessibles par [alias](/help/sites-cloud/authoring/sites-console/page-properties.md#advanced) dans l’éditeur ne peuvent pas être publiées. Les options de publication dans l’éditeur ne sont disponibles que pour les pages auxquelles vous pouvez accéder à partir de leur chemin d’accès réel.

## Dépublication à partir de l’éditeur de page {#unpublishing}

Lorsque vous modifiez une page à l’aide de l’éditeur de page, pour la dépublier, sélectionnez **Dépublier la page** dans le menu **Informations sur la page** comme vous le feriez [publier la page](#publishing-from-the-editor).

>[!NOTE]
>
>Les pages accessibles par [alias](/help/sites-cloud/authoring/sites-console/page-properties.md#advanced) dans l’éditeur ne peuvent pas être publiées. Les options de publication dans l’éditeur ne sont disponibles que pour les pages auxquelles vous pouvez accéder à partir de leur chemin d’accès réel.

## Publication et dépublication à partir de la console Sites {#publishing-sites-console}

Vous pouvez également publier [à partir de la console Sites](/help/sites-cloud/authoring/sites-console/publishing-pages.md) ce qui peut s’avérer utile lorsque vous souhaitez publier plusieurs pages de contenu ou planifier la publication ou la dépublication.
