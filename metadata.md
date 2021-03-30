---
product: adobe experience manager
description: Adobe Experience Manager en tant que documentation Cloud Service.
git-repo: https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.fr-FR
index: y
type: Documentation
solution: Experience Manager
translation-type: tm+mt
source-git-commit: 1140a05a137ecebb443f69c9c93d9d82f5d4815c
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 69%

---


# Métadonnées pour utilisation interne

Les métadonnées figurant dans le système de création GitHub sont hiérarchisées et définies selon les niveaux de précédents croissants suivants.

1. metadata.md
1. Table des matières
1. Article

Les métadonnées définies dans le fichier metadata.md s’appliquent à l’intégralité du référentiel, mais peuvent être remplacées aux niveaux de la table des matières et de l’article. Tout remplacement des métadonnées doit être effectué au niveau le plus bas possible.

Les métadonnées du repo experience-manager-cloud-service.en sont le minimum requis.

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
* `contentOwner` (uniquement sur le contenu des ressources de base sous  `/help/assets`)
