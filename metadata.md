---
product: adobe experience manager
description: Documentation Adobe Experience Manager as a Cloud Service.
git-repo: https://github.com/AdobeDocs/experience-manager-cloud-service.fr-FR
index: y
type: Documentation
solution: Experience Manager
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
source-git-commit: a7a8b14c6d95f704c6ea4ee0d1424e77df045a4c
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 77%

---


# Métadonnées pour utilisation interne

Les métadonnées figurant dans le système de création GitHub sont hiérarchisées et définies selon les niveaux de précédents croissants suivants.

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
