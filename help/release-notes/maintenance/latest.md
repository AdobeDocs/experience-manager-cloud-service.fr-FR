---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 573de431328650778b3ef0979a24190477382310
workflow-type: ht
source-wordcount: '332'
ht-degree: 100%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 17098 {#release-17098}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 17098, publiée le 16 juillet 2024. La version de maintenance précédente était la version 16971.

L’activation des fonctionnalités de la version 2024.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-17098}

- SKYOPS-79817 : activation de la tâche Sling Feature Analyzer pour les mappages d’utilisation du service

### Problèmes résolus {#fixed-issues-17098}

- ASSETS-39665 : la synchronisation des recadrages intelligents ne fonctionne pas après la migration de la version 6.5 vers AEMCS.
- FORMS-14993 : API Forms renvoyant 500 pour le matériel précédemment en service
- GRANITE-52120 : CRXDE renvoyant 500 lors de l’affichage des données de contrôle d’accès
- GRANITE-52573 : demandes renvoyant 400 lors de l’utilisation de // dans des URL réécrites
- GRANITE-52746 : tous les types de nœud ne sont pas chargés dans la boîte de dialogue Créer un nœud.
- GRANITE-52777 : gestion interrompue des 404 lorsque la demande est encapsulée
- GRANITE-52871 : assurez-vous que publish-worker est synchronisé avec golden-publish et qu’il est terminée avant la compression.
- SKYOPS-79173 : réplicateur ne répliquant pas sur plusieurs agents correspondant à un AgentIdFilter donné
- SKYOPS-80075 : problèmes liés aux Umlauts (trémas) dans les noms de ressources, entraînant le blocage de la file d’attente de publication (Mac)
- SKYOPS-81032 : filtrage des journaux générés par les demandes d’obtention de journaux lors de l’utilisation de la journalisation améliorée

### Problèmes connus {#known-issues-17098}

Aucun

### Avis de modification {#change-notice-17098}

- À compter de septembre 2024, AEM as a Cloud Service désactivera la sérialisation des résolveurs de ressources via le framework de l’exportateur de modèle Sling. Voir la [documentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) pour plus d’informations.

### Fonctionnalités et API obsolètes {#deprecated-17098}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées ](/help/release-notes/deprecated-removed-features.md).

### Technologies intégrées {#embedded-tech-17098}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.66.0 | [API Oak 1.66.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| API SLING AEM | 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.25.4 | [Composants principaux de la gestion de contenu Web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
