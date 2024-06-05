---
title: Création d’un site
description: Découvrez comment utiliser AEM pour créer un site à l’aide de modèles de site afin de définir le style et la structure de votre site.
feature: Administering
role: Admin
exl-id: 9c71c167-2934-4210-abd9-ab085b36593b
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 80%

---

# Création d’un site {#creating-site}

Découvrez comment utiliser AEM pour créer un site à l’aide de modèles de site afin de définir le style et la structure de votre site.

## Vue d’ensemble {#overview}

Pour que les auteurs de contenu puissent créer des pages avec du contenu, le site doit d’abord être créé. Cette opération est généralement effectuée par un administrateur AEM qui définit la structure initiale du site. L’utilisation de modèles de site rend la création de site rapide et flexible.

L’outil de création rapide de site permet aux non-développeurs de créer rapidement un site à partir de zéro à l’aide de modèles de site.

Une fois créé, l’outil de création rapide de site permet également une personnalisation rapide du thème et du style du site AEM (JavaScript, CSS et ressources statiques). Cela permet au développeur front-end, qui n’a besoin d’aucune connaissance d’AEM, de travailler séparément et parallèlement aux créateurs de contenu. L’administrateur d’AEM télécharge simplement le thème du site et le fournit au développeur front-end, qui le personnalise à l’aide de ses outils favoris, puis valide les modifications dans le référentiel de code AEM, qui est ensuite déployé.

Ce document se concentre sur la création de site à l’aide de l’outil de création rapide de site. Pour une vue d’ensemble du workflow de création et de personnalisation des sites, reportez-vous à la section [Parcours de création rapide de site AEM](/help/journey-sites/quick-site/overview.md)

## Planification de la structure du site {#structure}

Prenez le temps d’examiner à l’avance l’objectif et le contenu planifié de votre site. Cela vous permettra de concevoir la structure du site. Une structure de site bien conçue facilite la navigation et la découverte du contenu pour les personnes accédant à de votre site et prend en charge diverses fonctionnalités AEM telles que la [gestion multisite et la traduction](/help/sites-cloud/administering/msm-and-translation.md).

>[!TIP]
>
>[Le site de référence WKND](https://wknd.site) fournit une implémentation des bonnes pratiques d’un site web de marque entièrement fonctionnel proposant des expériences en plein air. Explorez-le pour découvrir la structure d’un site d’AEM bien conçu.

## Modèles de site {#site-templates}

La structure du site étant si importante pour le succès d’un site, il est pratique de disposer de structures prédéfinies pour déployer rapidement un nouveau site en fonction d’un ensemble de normes existantes. Les modèles de site permettent de combiner du contenu de site de base dans un package pratique et réutilisable.

Les modèles de site contiennent généralement le contenu et la structure du site de base, ainsi que des informations de style pour démarrer rapidement un nouveau site. Les modèles, réutilisables et personnalisables, sont d’une grande efficacité. De plus, comme vous pouvez avoir plusieurs modèles disponibles dans votre installation AEM, vous avez la possibilité de créer différents sites pour répondre à divers besoins professionnels.

>[!TIP]
>
>Pour plus d’informations sur les modèles de site, voir [Modèles de site](site-templates.md).

>[!NOTE]
>
>Le modèle de site ne doit pas être confondu avec les modèles de page. Les modèles de site définissent la structure globale d’un site. Un modèle de page définit la structure et le contenu initial d’une page individuelle.

## Création d’un site {#create-site}

L’utilisation d’un modèle pour créer un site est simple.

1. Connectez-vous à votre environnement de création AEM et accédez à la console Sites.

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Appuyez ou cliquez sur **Créer** en haut à droite de l’écran et, dans le menu déroulant, sélectionnez **Site à partir d’un modèle**.

   ![Création d’un site à partir d’un modèle](../assets/create-site-from-template.png)

1. Dans l’assistant Créer un site , sélectionnez un modèle existant dans le panneau de gauche ou sur **Importer** en haut de la colonne gauche pour importer un nouveau modèle.

   ![Assistant Création de site](../assets/site-creation-wizard.png)

   1. Si vous choisissez d’importer, recherchez le modèle à utiliser dans l’explorateur de fichiers, puis sélectionnez **Télécharger**.

   1. Une fois chargé, il s’affiche dans la liste des modèles disponibles.

1. Lors de la sélection d’un modèle, il affiche des informations sur le modèle dans la colonne de droite. Avec le modèle sélectionné, sélectionnez **Suivant**.

   ![Sélectionner un modèle](../assets/select-site-template.png)

1. Indiquez un titre pour votre site. Un nom de site peut être fourni ou généré à partir du titre s’il est omis.

   * Le titre du site s’affiche dans la barre de titre des navigateurs.
   * Le nom du site fait alors partie de l’URL.
   * Le nom du site doit respecter les [conventions de dénomination des pages d’AEM](/help/sites-cloud/authoring/sites-console/organizing-pages.md#page-name-restrictions-and-best-practices).

1. Sélectionner **Créer** et le site est créé à partir du modèle de site.

   ![Détails du nouveau site.](../assets/create-site-details.png)

1. Dans la boîte de dialogue de confirmation qui s’affiche, sélectionnez **Terminé**.

   ![Boîte de dialogue Succès](../assets/success.png)

1. Dans la console Sites, le nouveau site est visible et vous pouvez y accéder pour explorer sa structure de base telle que définie par le modèle.

   ![Nouvelle structure du site](../assets/new-site.png)

Les auteurs de contenu peuvent maintenant commencer la création !

## Personnalisation du site {#site-customization}

Si votre site nécessite une personnalisation au-delà des modèles disponibles, vous disposez de plusieurs options.

* Si la structure du site ou le contenu initial doit être ajusté, [le modèle de site peut être personnalisé en fonction de vos besoins.](site-templates.md).
* Si le style du site doit être adapté, [le thème du site peut être téléchargé et personnalisé.](/help/journey-sites/quick-site/overview.md).
* Si la fonctionnalité du site doit être ajustée, [le site peut être entièrement personnalisé.](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

Toute personnalisation doit être effectuée avec l’aide d’une équipe de développement.
