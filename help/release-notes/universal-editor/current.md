---
title: Notes de mise à jour d’Universal Editor 2024.08.13
description: Il s’agit des notes de mise à jour de la version 2024.08.13 d’Universal Editor.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: aad4d0353fb5e2eacb518b72e935def931d0798a
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# Notes de mise à jour d’Universal Editor 2024.08.13 {#release-notes}

Il s’agit des notes de mise à jour de la version d’Universal Editor du 13 août 2024.

>[!TIP]
>
>Pour consulter les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, reportez-vous à [cette page.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Nouveautés {#what-is-new}

* **Types de données personnalisés** : personnalisez l’éditeur en fonction de vos besoins de données uniques avec la possibilité de créer des champs personnalisés dans le panneau des propriétés.
   * Que vous développiez un sélecteur de produits personnalisé pour des cas d’utilisation commerciaux ou que vous remplissiez une liste déroulante avec des valeurs issues de vos arrière-plans, cette fonctionnalité vous donne le contrôle nécessaire sur les données que les auteurs utilisent pour composer du contenu.
* **Glisser-déposer inter-conteneurs** : profitez d’une plus grande flexibilité dans la composition des mises en page avec la possibilité de [déplacer des composants sur différents conteneurs par glisser-déposer](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components) dans le [panneau Arborescence de contenu.](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode)
* **Intégration GitHub optimisée** : la mise en cache des réponses GitHub a été introduite, ce qui accélère considérablement la récupération des balises et de `universal-editor-cors-library`, ce qui se traduit par une expérience utilisateur plus rapide et plus fluide.
* **Package Managed Services RPM** : Adobe propose désormais un package RPM pour rationaliser le déploiement et la gestion du service d’éditeur universel, ce qui simplifie la maintenance et réduit les frais opérationnels pour les services gérés.
* **Validation des jetons IMS configurable** : pour accroître la flexibilité de la gestion des jetons, la validation des jetons IMS est désormais facultative.
   * Cette option de configuration vous permet de désactiver la validation si nécessaire, ce qui simplifie les configurations de la passerelle cloud.
* **Intégration Splunk** : la journalisation Splunk a été intégrée dans le [service d’éditeur universel pour le développement local,](/help/implementing/universal-editor/local-dev.md) améliorant la surveillance et les diagnostics.
   * Cette intégration garantit un suivi efficace des logs, des opérations plus fluides et un dépannage plus rapide.

## Correctifs {#bug-fixes}

* **Commentaires sur la publication améliorés** : si la publication échoue en raison d’autorisations insuffisantes, les commentaires envoyés à l’utilisateur lors de la publication ont été améliorés afin d’afficher un avertissement clair au lieu de simplement signaler un échec.
* **Amélioration de la gestion des URL** : les problèmes de codage/décodage d’URL incorrect qui provoquaient des échecs de publication ont été résolus.
* **Gestion précise des données** : correction d’un problème en raison duquel les nombres flottants étaient incorrectement stockés en tant qu’entiers, ce qui permet d’assurer une gestion précise des données dans votre contenu.
* **Sécurité et stabilité** : les vulnérabilités de la sécurité dans les images Docker ont été corrigées et la couverture de test pour les composants critiques tels que le sélecteur de composants et le chemin de navigation ont été implémentés, ce qui a permis d’offrir une expérience d’éditeur plus sécurisée, stable et fiable.
