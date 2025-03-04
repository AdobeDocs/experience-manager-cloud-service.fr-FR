---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 30b5d5838087a35a457939cdbaa13c5735df144e
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 53%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 19823 {#19823}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 19823, publiée le mercredi 4 mars 2025. La version de maintenance précédente était la version 19687.

L’activation des fonctionnalités de la version 2025.3.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-19823}

* ASSETS-46491 : gestionnaire d’événements OSGI pour le changement de statut du traitement des ressources.
* ASSETS-45613 : envoi d’événements de dépublication lorsque des ressources sont supprimées ou déplacées.
* ASSETS-45131 : prise en charge de la propriété de balise personnalisée dans Content Hub.

### Problèmes résolus {#fixed-issues-19823}

* ASSETS-20433 : problèmes d’ingestion Dynamic Media avec les fichiers PDF protégés par mot de passe.
* ASSETS-24675 : les options de traitement des images ne sont pas affichées pour le profil d’image de nuance uniquement.
* ASSETS-41257 : la comparaison des versions des ressources effectue le rendu des ressources avec des proportions incorrectes. Les versions des ressources ne s’affichent pas dans le bon ordre dans le journal.
* ASSETS-44894 : il est possible que vous ne puissiez pas cliquer sur les signets de vue Assets.
* ASSETS-45015 : largeur et hauteur de recadrage intelligent définies sur zéro si le gestionnaire de ressource de recadrage intelligent est introuvable.
* ASSETS-45192 : réduction de la fréquence des demandes d’impulsions.
* ASSETS-45724 : assurez-vous que le chargement DM est repris si la tâche de chargement n’est pas affectée.
* ASSETS-46425 : problèmes de recherche de l’intégration Adobe Stock.
* ASSETS-27400 : le générateur d’aperçu de dossier peut tenter d’ouvrir l’original.
* CQ-4358722 : gérer différents codes de paramètres régionaux dans Java 11 et Java 17.
* SITES-29369 : événements publiés/dépubliés de page déclenchés lors de l’activation/la désactivation de la ressource.
* SITES-24074 : correction de l’accessibilité du clavier sous Unified Shell.
* SITES-28058 : titre du dossier Assets non transféré à la Live Copy.

### Problèmes connus {#known-issues-19823}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-19823}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-19823}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 6 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-19823}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.76.0 | [API Oak 1.76.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
