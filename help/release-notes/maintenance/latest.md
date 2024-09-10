---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9323464610b804ff407f5eedf404ab2cca93a8da
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 50%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 17689 {#release-17689}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 17689, publiée le mercredi 10 septembre 2024. La version de maintenance précédente était la version 17569.

L’activation des fonctionnalités de la version 2024.9.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-17689}

* ASSETS-41404 : modifications pour la prise en charge des améliorations de DRM.
* ASSETS-41621 : mise à jour de la tâche de copie de ressource asynchrone.
* ASSETS-32166 : mise à jour de la tâche de déplacement asynchrone des ressources.
* ASSETS-41429 : prise en charge des paramètres d’image prédéfinis dans DM OpenAPI.
* ASSETS-38968 : amélioration de la représentation des références de fragments de contenu.
* ASSETS-41787, ASSETS-41183 : améliorations de la structure des opérations en bloc d’Assets.
* GRANITE-52917 : optimisations pour améliorer les temps d’installation du package de copie de contenu.
* SCRNS-3980 : écran de détection des gris sur les lecteurs ayant des séquences sans ressources planifiées.

### Problèmes résolus {#fixed-issues-17689}

* ASSETS-40875 : NPE intelligent consigné par AssetDeleteHandler.
* ASSETS-42422 : évitez de déclencher une tâche asynchrone pour un déplacement de ressource unique.
* ASSETS-41234 : Shell unifié - La navigation globale peut ne pas fonctionner si elle est ouverte lorsque la barre de recherche est ouverte.
* ASSETS-42256 : Shell unifié - Balise/Badge indiquant que l’environnement ne fonctionne que par intermittence.
* ASSETS-41271 : évitez la republication inutile d’Assets lors des opérations de déplacement.
* ASSETS-38894 : Limitez les reprises en traitant watchdog.
* ASSETS-40815 : utilisez le rendu du PDF d’aperçu pour afficher le fichier PPT dans l’ interface utilisateur du partage de liens .
* ASSETS-37123 : impossible de charger l’aperçu de la ressource dans la boîte de dialogue Partage de lien.
* CQ-4358156 : mettre à jour les liens renvoyant de la balise en cours de suppression.
* SCRNS-4495 : correction du bouton Coller qui ne fonctionnait pas correctement pour différents groupes d’utilisateurs.
* SCRNS-4512 : suppression des composants associés à l’appareil des écrans AEMaaCS.
* SCRNS-4466 : dans Tableau de bord des canaux, masquer - Afficher le manifeste, générer du contenu hors ligne, mettre à jour le cache de manifeste, afficher le panneau.
* SCRNS-4513 : Ajout d’en-têtes de colonne pour la page des résultats de recherche en mode Liste.

### Problèmes connus {#known-issues-17689}

* FORMS-14340 : Erreur lors de l’instanciation de FormsAndDocumentOmniSearchHandler et CloudStorageSubmitActionInserter. Ce sont des instructions de journal inoffensives.
* FORMS-15818 : entrée du descripteur de composant &quot;OSGI-INF/com.adobe.aemfd.docmanager.impl.Les instructions *.xml’ sont introuvables dans les journaux du serveur. Ce sont des instructions de journal inoffensives.
* SITES-23662 : l’utilisateur qui déclenche une publication ne peut pas être extrait des instructions de journal JCR dans les journaux du serveur. Il s’agit d’une fonctionnalité en cours de développement qui peut provoquer des erreurs intermittentes et inoffensives &quot;Impossible de trouver un ID utilisateur valide dans le lot d’événements OSGI&quot; dans le journal.

### Avis de modification {#change-notice-17689}

* À compter de septembre 2024, AEM as a Cloud Service désactivera la sérialisation des résolveurs de ressources via le framework de l’exportateur de modèle Sling. Voir la [documentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) pour plus d’informations.

### Fonctionnalités et API obsolètes {#deprecated-17689}

Nous actualisons en ce moment `com.day.cq.wcm.api`. Dans la version actuelle, nous avons déclaré certaines de ses méthodes et classes comme `@Deprecated`. Celles-ci seront supprimées des prochaines versions. Envisagez donc de passer à leurs alternatives qui sont suggérées si vous utilisez l’une d’elles.

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-17689}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige quatre vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-17689}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.68.0 | [API Oak 1.68.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.26.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
