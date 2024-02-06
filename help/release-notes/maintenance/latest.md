---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 0b4c820159f918cb9b3a93d9ab36dc26b1d8da47
workflow-type: ht
source-wordcount: '381'
ht-degree: 100%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 14697 {#release-14697}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 14697, publiée le 18 décembre 2023. Elle remplace la version 14538 qui présentait un problème. La version de maintenance précédente était la version 14227.

L’activation des fonctionnalités de la version 2023.12.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-14697}

* GRANITE-46723 : synchronisation des utilisateurs et utilisatrices – Migration SAML de la synchronisation par défaut vers la synchronisation basée sur IDP.
* OAK-10311 : réplication – Optimisation de la comparaison blob pour réduire le temps de réplication d’un lot volumineux de ressources dans AEM.
* OAK-10511 : réplication – Réduction des allers-retours réseau pour réduire le temps de réplication des ressources volumineuses dans AEM.
* GRANITE-48334 : publication – Le script de collection est manquant pour RUM.

### Problèmes résolus {#fixed-issues-14697}

* CQ-4354867 : la référence ToggleCondition fait référence à un champ inexistant dans InstanceActionServlet.
* CQ-4349948 : localisation des chaînes Propriétés du profil dans Modifier les paramètres utilisateur sous Outils → Sécurité → Utilisateurs et utilisatrices.
* GRANITE-44541 : localisation des boîtes de dialogue d’erreur lors de l’ajout d’un fichier de clé privée dans l’écran Modifier l’utilisateur ou l’utilisatrice > Fichier de clé sous Outils → Sécurité → Utilisateurs et utilisatrices.
* GRANITE-45341 : localisation des chaînes de succès/échec pour activer/désactiver l’action de l’utilisateur ou de l’utilisatrice sous Outils → Sécurité → Utilisateurs et utilisatrices.
* GRANITE-46650 : localisation du message d’erreur Non concordance entre l’ID d’utilisateur ou d’utilisatrice et le mot de passe sous Outils → Sécurité → Boîte de dialogue Créer des utilisateurs et des utilisatrices.
* GRANITE-47764 : mise à jour de l’API des modèles Sling 1.5.0 : l’injection d’une variable statique dans un modèle Sling entraînera des erreurs de compilation (SLING-11507).
* GRANITE-48452 : envoi de bibliothèques clientes vides avec le code de statut 200.
* GRANITE-48410 : ResourceResolver n’est pas fermé.
* ASSETS-31297 : blocage de la suppression de la ressource copiée dans Dynamic Media.
* ASSETS-30811 : mises à jour de référence pour le lien du service Blocktag.
* GRANITE-46418 : mise à jour des événements Sling dans AEM : GaugeSupport a une récursion infinie dans registerWithSuffix (SLING-11918).
* GRANITE-48937 : régression des correctifs de la version de maintenance 14538 où Omnisearch ne fonctionne pas sur la page aem/start.html.

### Problèmes connus {#known-issues-14697}

* GRANITE-49031 : régression selon laquelle l’annotation `@JsonIgnore` est ignorée sur les champs transitoires.

### Technologies intégrées {#embedded-tech-14697}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.58-T20231123092841-619e1bd | [API Oak 1.58.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.58.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
