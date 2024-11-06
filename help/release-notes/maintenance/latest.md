---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: dc7f95ac98fd300a803e307ce11a51937d604a07
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 32%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 18459 {#18459}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 18459, publiée le mercredi 5 novembre 2024. La version de maintenance précédente était la version 18311.

L’activation des fonctionnalités de la version 2024.11.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-18459}

* CQ-4357471 : Ajout de la prise en charge de la traduction des dictionnaires i18n dans AEMaaCS.
* SITES-23591 : fragments de contenu : mise à niveau de fragment de contenu pour la prise en charge de l’UUID.
* SITES-25440 : Fragments de contenu : API de recherche CFM pour afficher l’état de réplication.
* SITES-24369 : Fragments de contenu : améliorations de la documentation OpenAPI.
* SITES-25478 : Fragments de contenu : Ajoutez la prise en charge principale pour les références de ressources externes.
* SITES-26119 : Fragments de contenu : ajout de la prise en charge des références de ressources externes dans le type de référence.
* SITES-21199 : Edge Delivery avec Universal Editor : ajoutez la prise en charge des modèles créés à partir de pages.
* SITES-20311 : Edge Delivery avec Universal Editor : ajout de la prise en charge de l’importation de CSV dans les feuilles de calcul.
* SITES-24821 : Edge Delivery avec Universal Editor : faites d’aem.page / aem.live la valeur par défaut à intégrer à Edge Delivery.

### Problèmes résolus {#fixed-issues-18459}

* CQ-4358730 : CQPagePreviewGenerator échoue lorsqu’il y a plus de 10 clés à traduire.
* FORMS-14978 : activation du chargement de page pour un formulaire basé sur les composants principaux pour l’éditeur de thème.
* FORMS-16596 : Problème d’accessibilité : boutons désactivés non reconnus par le Reader d’écran.
* SITES-10575 : MSM : Blueprint Bloomfilter Loader tente de charger plus de 100 000 lignes.
* SITES-20755 : Fragments de contenu : la référence de ressource avec actualisation de l’UUID n’affiche pas la miniature.
* SITES-26253 : Fragments de contenu : migration UUID : remplacez la rubrique de tâche Sling par générique.
* SITES-21338 : Fragments de contenu : le point de terminaison referencedBy ne renvoie pas la référence de page correcte.
* SITES-24421 : Fragments de contenu : la modification du point de terminaison CF ne fonctionne pas pour les fichiers CF récupérés via GET CF.
* SITES-25461 : Fragments de contenu : le filtrage par modèle dans la recherche de CF ne doit pas être sensible à la casse.
* SITES-25471 : Fragments de contenu : correction de la validation des modèles globaux dans ModelValidatorServlet.
* SITES-25795 : Fragments de contenu : l’API du modèle CF échoue lorsqu’aucune date cq n’est définie.
* SITES-25817 : Fragments de contenu : améliorer promoteLaunch : mettre à jour la dernière promotion pour les lancements CF.
* SITES-26030 : Fragments de contenu : Endpoint /referenceTree ne renvoie pas l’en-tête nécessaire.
* SITES-26031 : Fragments de contenu : l’état de réplication n’est pas renvoyé sur le point de terminaison de recherche CFM.
* SITES-26213 : Fragments de contenu : l’annulation de la publication des fragments de contenu ne doit valider que les références publiées.
* SITES-26226 : Fragments de contenu : problème de démarrage du workflow lorsqu’aucun des chemins donnés n’est utilisable.
* SITES-26238 : Fragments de contenu : les références de ressources renvoyées par l’API ont un ordre différent de celui renvoyé par JCR.
* SITES-25456 : Événements : lors du déplacement d’une page, un événement de suppression de page est généré en plus de l’événement de déplacement de page.
* SITES-25658 : Événements : le niveau et la sourceUrl ne sont pas renseignés dans les événements d’état du contenu de la page.
* SITES-6497 : Lancements : la page de création du lancement ne fonctionne pas.
* SITES-25393 : Edge Delivery avec Universal Editor : noeuds de texte perdus lors du rendu de texte enrichi formaté avec un seul paragraphe.
* SITES-24643 : Edge Delivery avec Universal Editor : les attributs de métadonnées OpenGraph et twitter ne fonctionnent pas dans le modèle de métadonnées de page.

### Problèmes connus {#known-issues-18459}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-18459}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-18459}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 21 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-18459}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.70.0 | [API Oak 1.70.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
