---
product: adobe experience manager
description: Documentation Adobe Experience Manager as a Cloud Service.
git-repo: https://github.com/AdobeDocs/experience-manager-cloud-service.fr-FR
index: y
type: Documentation
solution: Experience Manager, Experience Manager as a Cloud Service
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
recommendations: noDisplay
source-git-commit: 2b2469382fa8adfbf8a0625a90f92e27cdf53d63
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 51%

---


# Métadonnées pour utilisation interne

Les métadonnées du système de création GitHub sont hiérarchisées et définies comme les niveaux de précédent croissants suivants.

1. metadata.md
1. Table des matières
1. Article

Les métadonnées définies dans le fichier metadata.md s’appliquent à l’intégralité du référentiel, mais peuvent être remplacées aux niveaux de la table des matières et de l’article. Tout remplacement des métadonnées doit être effectué au niveau le plus bas possible.

Les métadonnées du référentiel experience-manager-cloud-service.en sont le minimum requis.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

Tables des matières

* `sub-product`
* `user-guide-title`

Article

* `title`
* `description`
* `contentOwner` (uniquement sur le contenu de la ressource principale sous `/help/assets`)
