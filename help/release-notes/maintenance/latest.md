---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: eb01b6982578ad1300163c2fd536e844afc815fa
workflow-type: ht
source-wordcount: '736'
ht-degree: 100%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 17569 {#release-17569}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 17569, publiée le 27 août 2024. La version de maintenance précédente était la version 17465.

L’activation des fonctionnalités de la version 2024.9.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-17569}

* CQ-4353778 : événements de processus de traduction.
* CQ-4354583 : envoyer des événements de processus de traduction via Adobe Pipeline.
* CQ-4356479 : autoriser uniquement le code Adobe pour utiliser le contexte de servlet /adobe.
* CQ-4358226 : la fonctionnalité Enregistrer le mot-clé de traduction ne fonctionne pas pour un format de chaîne particulier.
* CQ-4358270 : kit de traduction AEM : 8 août.
* CQ-4358310 : ajouter oak-compat-query-spi-1.2 au démarrage rapide.
* GRANITE-49833 : prise en charge par lot de l’expéditeur et du proxy d’événement.
* GRANITE-52053 : supprimer des usages de Commons Collections 3 : autres plateformes.
* GRANITE-52492 : rattrapage asynchrone élastique en cas de restauration PIT.
* GRANITE-53099 : mettre à jour vers Apache Felix Http Jetty 5.1.24.
* GRANITE-53125 : ajouter une classification à CloudEvent.
* GRANITE-53328 : mettre à jour Filevault vers la version 3.8.0-T20240726111512-3cc11d50 contenant des améliorations de la journalisation de masquage.
* GRANITE-53453 : mettre à niveau commons-lang vers la version 3.15.0.
* GRANITE-53478 : mettre à jour Filevault vers la version 3.8.0.
* GRANITE-53505 : mettre à jour QS vers commons-collections-3.2.2-adobe-2.
* GRANITE-53528 : mettre à jour la version des artefacts de plateforme.
* GRANITE-53547 : fournir une autre API pour éviter l’utilisation d’Apache Commons Lang 2.
* GRANITE-53575 : utiliser BSAFE 6.2.5 dans CS.
* GRANITE-53608 : mettre à jour Oak vers la dernière version publique (1.68.0).
* SITES-23583 : les tests Evergreen de sites échouent sur Java 17.
* SKYOPS-79535 : mettre à jour vers RUM script v2.
* SKYOPS-79816 : activer la tâche Sling Feature Analyzer pour les mappages d’utilisation du service dans FACT Tool.
* SKYOPS-81179 : tester les constructions AEM pour le basculement des lots.
* SKYOPS-81866 : signaler les avertissements concernant les lots connus comme incompatibles avec Java 21.
* SKYOPS-82660 : mettre à jour l’API Sling vers la version 2.27.6.
* SKYOPS-82961 : mettre à jour vers Sling ResourceResolver 1.12.0-T20240723153354-a0270a0.
* SKYOPS-83356 : créer un tableau de bord global pour le suivi des versions JVM utilisées dans les déploiements AEM.
* SKYOPS-83436 : le déploiement Java Runtime 21 interrompt la création des formulaires adaptatifs AEM Forms.
* SKYOPS-84272 : consigner la version Java utilisée au démarrage du lanceur AEM.

### Problèmes résolus {#fixed-issues-17569}

* CMGR-60225 : échec de l’exécution du pipeline identifié sur le client CS d’AEM Sites lors de la validation de la mise à jour vers AEM version 17486.
* GRANITE-45919 : pays sous embargo dans la liste des régions/pays dans Modifier les paramètres d’utilisation.
* GRANITE-51715 : le sélecteur ne saisit pas toujours la sélection dans le champ de texte.
* GRANITE-53290 : vérifier correctement le protocole lors de l’analyse de l’URL dans la vérification XSS.
* GRANITE-53576 : définition incorrecte du classement des services dans les configurations OSGi.
* SKYOPS-82129 : perte de mémoire dans les modèles Sling.

### Problèmes connus {#known-issues-17569}

* ASSETS-40875 - La classe AssetDeleteHandler écoute les événements de suppression de ressources et exécute des actions spécifiques en fonction du type d’événement de suppression (PRE_DELETE ou POST_DELETE). Dans certains scénarios, le type d’événement POST_DELETE provoque une exception NullPointerException.
* FORMS-14340 - Erreur lors de l’instanciation de FormsAndDocumentOmniSearchHandler et CloudStorageSubmitActionInserter. Ce sont des instructions de journal inoffensives.
* FORMS-15818 - Entrée du descripteur de composant « OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml ». Instructions introuvables dans les journaux du serveur. Ce sont des instructions de journal inoffensives.
* SITES-23662 - La personne qui déclenche une publication ne peut pas être extraite des instructions de journal JCR dans les journaux du serveur. Il s’agit d’une fonctionnalité en cours de développement qui peut provoquer les erreurs intermittentes et inoffensives « Impossible de trouver un ID d’utilisateur ou d’utilisatrice valable dans le lot d’événements OSGI » dans le journal.

### Avis de modification {#change-notice-17569}

* À compter de septembre 2024, AEM as a Cloud Service désactivera la sérialisation des résolveurs de ressources via le framework de l’exportateur de modèle Sling. Voir la [documentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) pour plus d’informations.

### Fonctionnalités et API obsolètes {#deprecated-17569}

Nous actualisons en ce moment `com.day.cq.wcm.api`. Dans la version actuelle, nous avons déclaré certaines de ses méthodes et classes comme `@Deprecated`. Celles-ci seront supprimées des prochaines versions. Envisagez donc de passer à leurs alternatives qui sont suggérées si vous utilisez l’une d’elles.

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-17569}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige quatre vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-17569}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.68.0 | [API Oak 1.68.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.26.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
