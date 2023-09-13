---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 8a1ed1e44db0154854af73a96339d8e416afd3b4
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 36%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 13420 {#release-13420}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 13420, publiée publiquement le 12 septembre 2023. Cette version de maintenance remplace la version 13323.

2023.9.0 Feature Activation fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-13420}

- ASSETS-19544 : les ressources modifiées en dernier par propriété sont désormais définies sur l’utilisateur demandant le traitement.

### Problèmes résolus {#fixed-issues-13420}

- ASSETS-27628 : Noeud &quot;canaux&quot; en erreur créé lors de la personnalisation du panneau de recherche Assets
- ASSETS-27539 : mise en correspondance des expressions régulières de restrictions de chargement.
- ASSETS-26530 : Le Shell unifié ne ramène pas les utilisateurs à la page d’origine.
- ASSETS-22719 : les crochets dans le nom du point d’arrêt de recadrage intelligent rompent la fonction d’édition de recadrage intelligent.
- ASSETS-27726 : linkshare.html ne doit pas être indexé par Google.
- ASSETS-27791 : la validation du schéma de métadonnées se produit uniquement pour le premier champ.
- ASSETS-25544 : correction du bouton d’invalidation du cache CDN désactivé.
- ASSETS-26575 : correction de la troncation des noms lors de la création de visionneuses d’images.
- ASSETS-26705 : correction d’un traitement inutile sur les ressources de dossier et les fragments de contenu non DM.
- ASSETS-25740 : correction des lecteurs d’écran qui ne narraient pas le nom et le rôle des commandes Modifier/Recadrer sur la page &quot;Modifier les recadrages intelligents&quot; à l’aide des touches fléchées vers le bas.
- CQ-4354266 : impossible d’ouvrir les éléments de boîte de réception.
- CQ-4354347 : Mise à jour AEM traductions.
- DISP-1009 : User-Agent en tant que non-premier en-tête coupe X-Forwarded-Host.
- Divers correctifs liés à l’accessibilité et à la sécurité.

### Problèmes connus {#known-issues-13420}

Aucun.

### Technologies intégrées {#embedded-tech-13420}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.54-T20230817132355-3800a65 | [API Oak 1.54.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
