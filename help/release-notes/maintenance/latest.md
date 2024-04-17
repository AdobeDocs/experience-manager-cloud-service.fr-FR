---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 5e216e45a1400299efcc418007ddbe93f0c571a1
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 39%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 15939 {#release-15939}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 15939, rendue publique le jeudi 17 avril 2024. La version de maintenance précédente était la version 15860.

L’activation des fonctionnalités de la version 2024.4.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-15939}

* GRANITE-39892 : mettez à jour la distribution pour la limite de taille de file d’attente et la publication prête.
* GRANITE-48777 : mise à jour de QS vers com.adobe.granite.security.user-0.4.84 terminée.
* GRANITE-49421 : ajout de propriétés pour l’entité de service de segment.
* GRANITE-49855 : Rédigez un analyseur de modèle de fonctionnalité qui échoue à la version de démarrage rapide en cas de nouvelle utilisation de commons.json.
* GRANITE-47995 : Permet de changer l’écriture de cq:isDelivered.
* GRANITE-36205 : mettez à jour la version interne de oak vers la dernière version.
* GRANITE-50156 Liez l’affinité AEMCS à l’identifiant utilisateur IMS pour Universal Editor.
* GRANITE-50556 : mettez à niveau le lot de passage à la version 0.1.18.
* GRANITE-50728 : mettez à jour FileVault vers la version 3.7.3-T20240308111857-81fa88f1.
* GRANITE-50957 : mettez à jour QS vers com.adobe.granite.repository vers 1.8.114.
* GRANITE-50158 : Ajoutez la prise en charge du flux OAuth Server au flux d’informations d’identification du serveur dans le chargeur YAML.
* GRANITE-51327 : Mise à jour d’Oak vers la dernière version publique (1.62.0).
* SKYOPS-68091 Mise à jour des images d’exécution Java 11 vers la version 3.0.0.
* SKYOPS-70421 : mettez à niveau le lot org.apache.sling.servlet-helpers .
* SKYOPS-73483 : Autoriser le jeton de journalisation sur AEM.

### Problèmes résolus {#fixed-issues-15939}

* GRANITE-46901 : Ajoutez des mesures au client de messagerie.
* GRANITE-48793 : mettez à jour QS vers com.adobe.granite.crx-explorer-1.1.28.
* GRANITE-48937 : Omni-recherche ne fonctionne pas sur la page aem/start.html.
* GRANITE-49638 : correction d’une configuration de type de contenu incorrecte pour la fabrique de transformateurs RUM.
* GRANITE-50141 : IMSProviderImpl spamme le journal.
* SITES-20949 : Échec de ComponentsIT.testEmbed après l’ajout par YouTube de referrerpolicy=&quot;strict-origin-when-cross-origin&quot;.
* SITES-21233 : Mise à jour des composants principaux - Fix Accordion pour GS1 US après la mise à niveau vers 15860.
* SKYOPS-74819 : compatibilité descendante rompue pour les clés en double dans Apache Commons.
* SKYOPS-67087 : l’agrégation de bibliothèques clientes ne fonctionne pas dans certains cas.
* CQ-4355415 : AEM liens Notifications ne fonctionne pas dans la version 6.5 SP18.

### Problèmes connus {#known-issues-15939}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-15939}

* [Obsolescence des informations d’identification JWT dans Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

Consultez les [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md) pour savoir ce qui est obsolète ou supprimé dans AEM as a Cloud Service.

### Technologies intégrées {#embedded-tech-15939}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.62.0 | [API Oak 1.62.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| API SLING AEM | 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.24.6 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
