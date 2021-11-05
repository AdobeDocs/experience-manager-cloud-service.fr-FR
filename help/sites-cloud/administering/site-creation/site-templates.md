---
title: Modèles de site
description: Découvrez comment AEM modèles de site peuvent être utilisés pour prédéfinir la structure du site et le contenu initial afin de vous permettre de créer rapidement des sites.
feature: Administering
role: Admin
source-git-commit: 2dd35f1ea25f6bfc515d7b50fd53cf4638af4026
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 1%

---


# Modèles de site {#site-templates}

Découvrez comment AEM modèles de site peuvent être utilisés pour prédéfinir la structure du site et le contenu initial afin de vous permettre de créer rapidement des sites.

>[!CAUTION]
>
>L’outil de création de site rapide est actuellement un aperçu technique. Il est mis à disposition à des fins de test et d’évaluation et n’est pas destiné à un usage en production sauf accord avec le support Adobe.

## Présentation {#overview}

Il est pratique de disposer de structures prédéfinies pour déployer rapidement un nouveau site en fonction d’un ensemble de normes existantes. Les modèles de site permettent de combiner du contenu de site de base dans un package pratique et réutilisable.

Les modèles de site contiennent généralement le contenu et la structure du site de base, ainsi que des informations de style de site, connues sous le nom de [thème du site,](site-themes.md) pour démarrer rapidement un nouveau site. Les administrateurs sélectionnent un modèle de site sur lequel baser le site. [pendant le processus de création du site.](create-site.md)

Les modèles sont puissants, car ils sont réutilisables et personnalisables. De plus, comme vous pouvez avoir plusieurs modèles disponibles dans votre installation AEM, vous avez la possibilité de créer différents sites pour répondre à divers besoins professionnels.

>[!NOTE]
>
>AEM les modèles de site ne doivent pas être confondus avec [modèles de page.](/help/sites-cloud/authoring/features/templates.md) Les modèles de site définissent la structure globale d’un site. Un modèle de page définit la structure et le contenu initial d’une page individuelle.
>
>AEM les modèles de site ne doivent pas être confondus avec [AEM thèmes du site.](site-themes.md) Les thèmes AEM site contiennent uniquement les informations de style d’un site AEM. AEM modèles de site définissent la structure du site et le contenu initial, ainsi qu’un thème de site AEM afin de permettre [création rapide de site.](create-site.md)

## Ajout d’un modèle de site à AEM {#adding}

Vous pouvez ajouter plusieurs modèles à AEM, qui peuvent ensuite être utilisés pour [créer des sites ;](create-site.md)

1. Connectez-vous à votre environnement de création AEM et accédez à la console Sites.

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Appuyez ou cliquez sur **Créer** en haut à droite de l’écran et, dans le menu déroulant, sélectionnez **Site à partir du modèle**.

   ![Créer un site à partir d&#39;un modèle](../assets/create-site-from-template.png)

1. Dans l’assistant Créer un site , appuyez ou cliquez sur **Importer** en haut de la colonne de gauche.

   ![Assistant de création de site](../assets/site-creation-wizard.png)

1. Dans l’explorateur de fichiers, recherchez le modèle que vous souhaitez utiliser, puis appuyez ou cliquez sur **Télécharger**.

1. Une fois chargé, il apparaît dans la liste des modèles disponibles.

Votre modèle est chargé et peut être utilisé pour [créer des sites.](create-site.md)

Lors de la sélection d’un modèle existant, il affiche les informations le concernant dans la colonne de droite.

![Sélectionner un modèle](../assets/select-site-template.png)

## Structure de modèle de site {#structure}

Les modèles de site sont simplement des packages avec une structure logique qui reflète clairement l’objectif du contenu du package. Un modèle de site possède la structure suivante.

* `files`: Dossier contenant le kit d’interface utilisateur, le fichier XD et éventuellement d’autres fichiers
* `previews`: Dossier contenant des captures d’écran du modèle de site
* `site`: Package de contenu du contenu copié pour chaque site créé à partir de ce modèle, tel que des modèles de page, des pages, etc.
* `theme`: Sources de [thème du site](site-themes.md) pour modifier l’aspect du site, y compris CSS, JavaScript, etc.

## Modèle de site standard {#standard-site-template}

Adobe fournit un modèle de référence des bonnes pratiques que vous pouvez utiliser comme base pour créer vos propres modèles. [Le modèle de site standard est disponible sur GitHub.](https://github.com/adobe/aem-site-template-standard)

[Dernière version du modèle de site standard](https://github.com/adobe/aem-site-template-standard/releases) peut être téléchargé et utilisé directement pour [création de sites.](create-site.md)

## Développement de modèles de site {#developing-templates}

Adobe fournit et AEM le Créateur de modèles de site en tant qu’ensemble de scripts pour la création de modèles de site.

[AEM Créateur de modèles de site est disponible avec la documentation d’utilisation sur GitHub.](https://github.com/adobe/aem-site-template-builder) L’expérience du développeur front-end est requise pour personnaliser le [thème du site](site-themes.md) et AEM connaissances des développeurs sont requises pour personnaliser la structure et le contenu du site.
