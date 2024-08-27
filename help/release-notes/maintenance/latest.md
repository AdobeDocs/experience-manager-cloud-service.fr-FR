---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 82be9b2b328343e827b90bd8266d93127757f477
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 37%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 17569 {#release-17569}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 17569, publiée le mercredi 27 août 2024. La version de maintenance précédente était la version 17465.

L’activation des fonctionnalités de la version 2024.9.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-17569}

* CQ-4353778 : Événements de processus de traduction.
* CQ-4354583 : Envoyez des événements de processus de traduction via Adobe Pipeline.
* CQ-4356479 : Autorisez uniquement le code d’Adobe à utiliser le contexte de servlet /adobe.
* CQ-4358133 : optimisation de l’utilisation du worker Jenkins.
* CQ-4358226 : La fonctionnalité Enregistrer le mot-clé de traduction ne fonctionne pas pour un format de chaîne particulier.
* CQ-4358270 : AEM Kit de traduction : août 08.
* CQ-4358310 : Ajoutez oak-compat-query-spi-1.2 au démarrage rapide.
* GRANITE-36205 : mise à jour automatisée pour la version interne de Oak dans QS.
* GRANITE-49833 : Prise en charge par lot de l’expéditeur et du proxy d’événement.
* GRANITE-52053 : Suppression des usages des collections Commons 3 : Plateforme d&#39;autres formes.
* GRANITE-52492 : rattrapage asynchrone en cas de restauration PIT.
* GRANITE-53086 : mettez à jour la version du module externe jacoco vers la version 0.8.12 dans AEMaaCS.
* GRANITE-53099 : Mise à jour vers Apache Felix Http Jetty 5.1.24.
* GRANITE-53125 : Ajoutez une classification à CloudEvent.
* GRANITE-53328 : mise à jour de Filevault vers la version 3.8.0-T20240726111512-3cc11d50 contenant des améliorations de journalisation de hachage.
* GRANITE-53340 : AEM660 : Contrôle de version et embranchement appropriés pour 660 CQ/Platform.
* GRANITE-53341 : N’avertissez pas sur l’utilisation d’ACS Commons 6.
* GRANITE-53453 : mettez à jour commons-lang vers 3.15.0.
* GRANITE-53473 : Paramètres Sling non obsolètes.
* GRANITE-53478 : mettez à jour Filevault vers la version 3.8.0.
* GRANITE-53505 : mettez à jour QS vers commons-collections-3.2.2-adobe-2.
* GRANITE-53528 : Mise à jour de la version des artefacts de plateforme .
* GRANITE-53547 : proposez une autre API pour éviter l’utilisation d’Apache Commons Lang 2.
* GRANITE-53575 : utilisez BSAFE 6.2.5 dans CS.
* GRANITE-53608 : Mise à jour d’Oak vers la dernière version publique (1.68.0).
* SITES-23583 : les tests Evergreen de sites échouent sur Java 17.
* SKYOPS-79535 : mise à jour vers le script de rhum v2.
* SKYOPS-79816 : activez la tâche Sling Feature Analyzer pour les mappages des utilisateurs de service dans l’outil FACT.
* SKYOPS-81179 : AEM tester les versions pour le basculement des lots.
* SKYOPS-81866 : signale les avertissements concernant les lots connus comme incompatibles avec Java 21.
* SKYOPS-82660 : mise à jour de l’API Sling vers la version 2.27.6.
* SKYOPS-82961 : mise à jour de Sling ResourceResolver 1.12.0-T20240723153354-a0270a0.
* SKYOPS-83356 : créez un tableau de bord global pour le suivi des versions JVM utilisées dans AEM déploiements.
* SKYOPS-83436 : le déploiement du Runtime Java 21 interrompt la création d’AEM Forms de formulaires adaptatifs.
* SKYOPS-84272 : consigne la version Java utilisée au démarrage du lanceur AEM.

### Problèmes résolus {#fixed-issues-17569}

* CMGR-60225 : échec de l’exécution du pipeline identifié sur le client AEM Sites CS lors de la validation de la mise à jour vers AEM version 17486.
* GRANITE-45919 : Liste des pays incorporés dans la région/pays dans Modifier les paramètres utilisateur.
* GRANITE-51715 : le sélecteur ne saisit pas parfois la sélection dans le champ de texte.
* GRANITE-53290 : vérifiez correctement le protocole lors de l’analyse de l’URL dans la vérification XSS.
* GRANITE-53576 : définition incorrecte du classement des services dans les configurations OSGi.
* SKYOPS-82129 : Période de mémoire dans les modèles Sling.

### Problèmes connus {#known-issues-17569}

Aucun.

### Avis de modification {#change-notice-17569}

* À compter de septembre 2024, AEM as a Cloud Service désactivera la sérialisation des résolveurs de ressources via le framework de l’exportateur de modèle Sling. Voir la [documentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) pour plus d’informations.

### Fonctionnalités et API obsolètes {#deprecated-17569}

Nous actualisons en ce moment `com.day.cq.wcm.api`. Dans la version actuelle, nous avons déclaré certaines de ses méthodes et classes comme `@Deprecated`. Celles-ci seront supprimées des prochaines versions. Envisagez donc de passer à leurs alternatives qui sont suggérées si vous utilisez l’une d’elles.

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-17569}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 4 vulnérabilités identifiées, renforçant notre engagement envers une protection système robuste.

### Technologies intégrées {#embedded-tech-17569}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.68.0 | [API Oak 1.68.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6 ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.26.0 | [Composants principaux de la gestion de contenu Web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
