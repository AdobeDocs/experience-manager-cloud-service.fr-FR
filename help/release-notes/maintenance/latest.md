---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: cf8b5d8b11452268b2839053c1e05cc2ec107a91
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 53%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 13173 {#release-13173}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 13173, qui a été publiée publiquement le 18 août 2023. Cette mise à jour de maintenance est une mise à jour de la version de maintenance 13099 précédente.

2023.8.0 Feature Activation fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-13173}

Aucun.

### Problèmes résolus {#fixed-issues-13173}

- SITES-15463 : Modèles de sites - Les modèles ne peuvent pas être publiés.

### Problèmes connus {#known-issues-13173}

- SITES-15359 : Fragments de contenu - Le modèle de nom de variation ne parvient pas à faire correspondre correctement les variations qui ont ```'_'``` dans leurs noms de ressources.
- FORMS-10444 : Modèles Forms adaptatifs - Les modèles ne peuvent pas être publiés (solution : utilisez la console de distribution).
- CQ-4354191 : Workflows : le lanceur personnalisé peut se déclencher de nombreuses fois en raison des métadonnées de réplication présentes sur les noeuds non structurés nt:unstructured (solution : mise à jour des lanceurs pour exclure les propriétés de métadonnées de réplication afin d’éviter les chevauchements).

### Technologies intégrées {#embedded-tech-13173}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [API Oak 1.52.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
