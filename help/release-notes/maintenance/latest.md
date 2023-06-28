---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: fd0b8ca281f35a92876f3c31baa4e17884f23948
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 39%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 12441 {#release-12441}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 12441, publiée publiquement le 27 juin 2023. Cette mise à jour de maintenance est une mise à jour de la version de maintenance 12255 précédente.

L’activation des fonctionnalités de la version 2023.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-12441}

- SITES-8769 : Amélioration des appels StyleImpl dans ResponsiveGrid

### Problèmes résolus {#fixed-issues-12441}

- Diverses mises à jour liées à l’accessibilité
- SITES-12688 : Éditeur de page : Opérateur logique OU ne fonctionnant pas correctement dans la recherche de l’outil de recherche de ressources
- SITES-4951 : Éditeur de page : La recherche de balises dans l’éditeur de page ne trouve pas de sous-balises.
- SITES-12465 : Fragments d’expérience : Touches de flèches ne fonctionnant pas dans la boîte de dialogue du composant Fragment d’expérience
- SITES-12893 : Fragments d’expérience : Application d’une validation de référence circulaire aux fragments d’expérience
- SITES-12715 : Fragments d’expérience : Les configurations de service Cloud appliquées au dossier de fragments Experience ne sont pas conservées.
- SITES-13097 : Fragments d’expérience : Impossible d’ajouter des fragments d’expérience à un projet de traduction
- SITES-13165 : GraphQL : Restaurer le comportement par défaut pour le filtrage des valeurs nulles
- SITES-12577 : Vérificateur de lien : Le transformateur ne réécrit pas les liens par intermittence
- SITES-13559 : MSM : Exception &quot;N’est pas modifiable&quot; générée lors du déploiement du composant
- SITES-11757 : MSM : La configuration du déploiement hérité de Parent n’est pas rétablie pour les pages enfants.
- SITES-14073 : Administration des sites : Le rapport CSV échoue avec 500 lors de la sélection d’aucune propriété à exporter

### Problèmes connus {#known-issues-12441}

Aucun.

### Technologies intégrées {#embedded-tech-12441}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.50-T20230405052634-f9df4aa | [API Oak 1.50.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| API SLING AEM | Version 2.27.0 | [API Apache Sling 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
