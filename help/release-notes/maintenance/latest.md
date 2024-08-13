---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a1baa7f29c6e15af11347debdd341f9972c06e83
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 100%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 17258 {#release-17258}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 17258, publiée le 30 juillet 2024. La version de maintenance précédente était la version 17098.

L’activation des fonctionnalités de la version 2024.8.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-17258}

* ASSETS-31445 : fonctionnalités de modèle Dynamic Media initiales.
* ASSETS-40399 : mise à jour des paramètres de la file d’attente de transcription automatique de DM.
* ASSETS-40873 : autorisation de la définition des lignes maximales d’export de métadonnées via la configuration OSGI.

### Problèmes résolus {#fixed-issues-17258}

* ASSETS-30613 : le remplacement de la ressource ne supprime pas et n’ajoute pas de ressource dans le nouveau niveau de diffusion.
* ASSETS-31882 : l’accès au fichier de manifeste en flux continu dans l’auteur est interdit.
* ASSETS-39598 : l’importation en masse ne peut pas supprimer des ressources dont le nom contient des caractères spéciaux du serveur principal S3.
* CNTBF-209 : améliorations de l’annulation des tâches de retour.
* SCRNS-3762 : amélioration de playerLogger dans le canal de séquence pour placer les journaux sur la console lors de la prévisualisation du canal sur le navigateur.
* SCRNS-4360 : absence du bouton Gérer la publication et Publication rapide pour les personnes ne faisant pas partie de l’équipe d’administration dans le fournisseur de contenu pour les canaux.
* SITES-22940 : impossible d’afficher le fragment de contenu en tant que payload de workflow.

### Problèmes connus {#known-issues-17258}

Aucun

### Avis de modification {#change-notice-17258}

* À compter de septembre 2024, AEM as a Cloud Service désactivera la sérialisation des résolveurs de ressources via le framework de l’exportateur de modèle Sling. Voir la [documentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) pour plus d’informations.

### Fonctionnalités et API obsolètes {#deprecated-17258}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées ](/help/release-notes/deprecated-removed-features.md).

### Technologies intégrées {#embedded-tech-17258}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.66.0 | [API Oak 1.66.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| API SLING AEM | 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.25.4 | [Composants principaux de la gestion de contenu Web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
