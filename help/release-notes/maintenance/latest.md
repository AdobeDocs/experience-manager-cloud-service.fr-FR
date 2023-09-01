---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: a1686d7796bb1e310b776195bd19df98f6f10650
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 35%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 13323 {#release-13323}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 13323, qui a été publiée publiquement le 1er septembre 2023. Cette version de maintenance remplace la version 13239.

2023.9.0 Feature Activation fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-13323}

- GRANITE-46784 : Ajouter une option pour désactiver BearerAuthenticationHandler
- GRANITE-36205 : mettez à jour la version interne de oak vers la dernière version
- ASSETS-26713 : Touch UI Lien externe vers le nouveau tableau de bord de l’interface utilisateur d’Experience - unifié-shell-intégration et IU optimisée pour les écrans tactiles mis à niveau
- SKYOPS-63302 : effectuez une mise à niveau com.adobe.granite:com.adobe.granite.auth.saml vers la version 1.0.54
- GRANITE-46634 : mise à niveau vers le client eventing 1.4.0
- GRANITE-46788 : Mise à jour des bibliothèques vers Apache Commons IO 2.13.0, Commons Lang 3.13.0, Commons Code 1.16.0 et Commons Compress 1.23.0
- GRANITE-46705 : Mise à jour vers Apache Felix Http Jetty 4.1.14
- GRANITE-46631 : mise à jour de la version Jackrabbit vers la version 2.20.11
- SKYOPS-61895 : mise à jour vers Jackrabbit Filevault 3.7.0

### Problèmes résolus {#fixed-issues-13323}

- SKYOPS-63290 : correction d’une évolution incorrecte des compartiments
- SKYOPS-54607 : calcul de la charge du serveur de l’outil de limitation de vitesse incorrect pour une requête qui a échoué.
- ASSETS-27648 : ContentModelIT ne parvient pas à lire les fichiers d’exclusion d’autres lots
- GRANITE-43744 : L’authentificateur Sling ne fonctionne pas correctement en cas de configuration incorrecte avec l’exigence d’authentification et le chemin d’accès Vanity.
- GRANITE-46419 : problème d’intégration AEM avec l’Idp Auth0
- GRANITE-46292 : la configuration SAML Okta ne fonctionne pas après la mise à jour AEM Cloud
- GRANITE-47059 : Suppression du lot SSL Granite Jetty

### Problèmes connus {#known-issues-13323}

- SITES-15622 : GraphQL - Problème avec les requêtes persistantes avec les paramètres numériques et booléens.
- SITES-15654 : GraphQL - Problèmes liés aux unions et propriétés du même nom.

### Technologies intégrées {#embedded-tech-13323}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.54-T20230817132355-3800a65 | [API Oak 1.54.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
