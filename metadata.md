---
product: adobe experience manager
git-repo: https://github.com/AdobeDocs/experience-manager-cloud-service.en
index: y
solution-title: Adobe Experience Manager en tant que service Cloud
solution-hub-url: https://docs.adobe.com/content/help/en/experience-manager-cloud-service/landing/home.html
getting-started-title: Prise en main
getting-started-url: https://docs.adobe.com/content/help/en/experience-manager-cloud-service/overview/home.html
tutorials-title: Tutoriels
tutorials-url: https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html
translation-type: tm+mt
source-git-commit: 99dce041a6d7554785fd43eb82c671643e903f23

---


# Métadonnées pour utilisation interne

Les métadonnées dans le système de création GitHub sont hiérarchisées et sont définies comme les niveaux de précédents croissants suivants.

1. metadata.md
1. ToC
1. Article

Les métadonnées définies dans le fichier metadata.md s’appliquent à l’intégralité du référentiel, mais peuvent être remplacées aux niveaux de la table des matières et de l’article. Tout remplacement des métadonnées doit être effectué au niveau le plus bas possible.

Les métadonnées dans le référentiel experience-manager-cloud-service.en sont le minimum requis.

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

ToCs

* `sub-product`
* `user-guide-title`

Article

* `title`
* `description`
* `contentOwner` (uniquement sur le contenu des ressources de base sous `/help/assets`)

Vous trouverez des informations supplémentaires sur les métadonnées dans le guide de création [interne.](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/markdown/metadata.html#solution-metadata)