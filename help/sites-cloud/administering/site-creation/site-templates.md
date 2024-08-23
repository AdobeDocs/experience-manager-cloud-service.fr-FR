---
title: Modèles de site
description: Découvrez comment les modèles de site AEM peuvent être utilisés pour prédéfinir la structure du site et le contenu initial afin de vous permettre de créer rapidement des sites.
feature: Administering
role: Admin
exl-id: 42eec922-b02e-4f2c-8107-7336192919c7
solution: Experience Manager Sites
source-git-commit: 7adfe0ca7fbab1f8a5bd488e524a48be62584966
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 94%

---

# Modèles de site {#site-templates}

Découvrez comment les modèles de site AEM peuvent être utilisés pour prédéfinir la structure du site et le contenu initial afin de vous permettre de créer rapidement des sites.

## Vue d’ensemble {#overview}

Il est pratique de disposer de structures prédéfinies pour déployer rapidement un nouveau site en fonction d’un ensemble de normes existantes. Les modèles de site permettent de combiner du contenu de site de base dans un package pratique et réutilisable.

Les modèles de site contiennent généralement le contenu et la structure du site de base et des informations sur le style du site, connues sous le nom de [thème de site,](site-themes.md) pour permettre à un nouveau site de démarrer rapidement. Les administrateurs et administratrices sélectionnent un modèle de site sur lequel baser le site [pendant le processus de création du site.](create-site.md)

Les modèles, réutilisables et personnalisables, sont d’une grande efficacité. De plus, comme vous pouvez avoir plusieurs modèles disponibles dans votre installation AEM, vous avez la possibilité de créer différents sites pour répondre à divers besoins professionnels.

>[!NOTE]
>
>Les modèles de site AEM ne doivent pas être confondus avec les [modèles de page](/help/sites-cloud/authoring/page-editor/templates.md). Les modèles de site définissent la structure globale d’un site. Un modèle de page définit la structure et le contenu initial d’une page individuelle.
>
>Les modèles de site AEM ne doivent pas être confondus avec les [thèmes de site AEM](site-themes.md). Les thèmes de site AEM contiennent uniquement les informations de style d’un site AEM. Les modèles de site AEM définissent la structure du site et le contenu initial et contiennent un thème de site AEM afin de permettre une [création rapide de site](create-site.md).

## Ajout d’un modèle de site à AEM {#adding}

Vous pouvez ajouter plusieurs modèles à AEM, qui peuvent ensuite être utilisés pour [créer des sites](create-site.md).

1. Connectez-vous à votre environnement de création AEM et accédez à la console Sites.

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Appuyez ou cliquez sur **Créer** en haut à droite de l’écran et, dans le menu déroulant, sélectionnez **Site à partir d’un modèle**.

   ![Création d’un site à partir d’un modèle](../assets/create-site-from-template.png)

1. Dans l’assistant Créer un site, appuyez ou cliquez sur **Importer** en haut de la colonne de gauche.

   ![Assistant Création de site](../assets/site-creation-wizard.png)

1. Dans l’explorateur de fichiers, recherchez le modèle que vous souhaitez utiliser et sélectionnez **Télécharger**.

1. Une fois chargé, il s’affiche dans la liste des modèles disponibles.

Votre modèle est chargé et peut être utilisé pour [créer des sites](create-site.md).

Lors de la sélection d’un modèle existant, il affiche des informations sur le modèle dans la colonne de droite.

![Sélectionner un modèle](../assets/select-site-template.png)

## Structure de modèle de site {#structure}

Les modèles de site sont simplement des packages avec une structure logique qui reflète clairement l’objectif du contenu du package. Un modèle de site possède la structure suivante.

* `files` : dossier contenant le kit d’interface utilisateur, le fichier XD et éventuellement d’autres fichiers.
* `previews` : dossier contenant des captures d’écran du modèle de site.
* `site` : package de contenu du contenu copié pour chaque site créé à partir de ce modèle, tel que des modèles de page, des pages, etc.
* `theme` : sources du [thème du site](site-themes.md) pour modifier l’aspect du site, y compris CSS, JavaScript, etc.

## Modèle de site standard {#standard-site-template}

Adobe fournit un modèle de référence des bonnes pratiques que vous pouvez utiliser comme référence pour créer vos propres modèles. [Le modèle de site standard est disponible sur GitHub.](https://github.com/adobe/aem-site-template-standard)

[La dernière version du modèle de site standard](https://github.com/adobe/aem-site-template-standard/releases) peut être téléchargée et utilisée directement pour [créer de nouveaux sites](create-site.md).

## Développement de modèles de site {#developing-templates}

Adobe fournit un Créateur de modèles de site AEM sous la forme d’un ensemble de scripts permettant de créer de nouveaux modèles de sites.

[Le Créateur de modèles de site AEM est disponible ainsi que la documentation d’utilisation sur GitHub](https://github.com/adobe/aem-site-template-builder). Une expérience de développement front-end est requise pour personnaliser le [thème de site](site-themes.md) et des connaissances de développement AEM sont nécessaires pour personnaliser la structure ainsi que le contenu du site.
