---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c8a798e1f1b7234f91682b6e5ef7072e024df022
workflow-type: ht
source-wordcount: '693'
ht-degree: 100%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 18751 {#18751}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 18751, publiée le 11 décembre 2024. La version de maintenance précédente était la version 18598.

L’activation des fonctionnalités de la version 2025.1.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-18751}

* SKYOPS-88509 : prise en charge de Java 21 pour le SDK AEM.

### Problèmes résolus {#fixed-issues-18751}

* ASSETS-42802 : le bouton Précédent de MFE ne fonctionne pas toujours et affiche une boîte de dialogue supplémentaire.
* ASSETS-44148 : la correction de l’événement NODE_MOVED dans AEM peut entraîner un NPE.
* ASSETS-44418 : correction du problème où l’environnement correct n’est pas configuré sur Skyline.
* ASSETS-44821 : correction du filtre d’événement de mise à jour pour inclure des données codées avec l’URL du formulaire pour les événements de chargement.
* CNTBF-298 : la copie de contenu corrigé échoue avec des conflits d’UUID.
* CNTBF-331 : [content-copy-bundle] version 2.0.14.
* FORMS-16572 : suppression des échecs de test de workflow pour la version de SDK java 21.
* GRANITE-36205 : mise à jour automatisée pour la version Oak interne dans QS.
* GRANITE-53704 : réévaluation de la découverte Sling sur le service de référentiel.
* GRANITE-54300 : mise à jour Oak vers la dernière version publique (1.70.0).
* GRANITE-54416 : mettre à jour Filevault vers la version 3.8.2.
* GRANITE-54462 : configuration de SubscriberAgents pour utiliser hc.tags de « systemready ».
* GRANITE-54542 : mise à jour de la dépendance commons-io vers la version 2.17.0.
* GRANITE-54658 : ajout de configurations OSGi delayFactor et de taille de lot pour fullGC dans QS.
* GRANITE-54696 : élargissement de la plage d’import pour l’API Jackrabbit.
* GRANITE-54803 : désactivation de ClusterAtExchange dans AEM lorsqu’imsauth est actif.
* GRANITE-55095 : mise à jour Oak vers la dernière version publique (1.72.0).
* GUIDES-20006 : le document marqué comme Terminé revient à l’état Brouillon avant d’enregistrer une nouvelle version. Par conséquent, l’état Terminé n’est conservé dans aucune version du document.
* GUIDES-21840 : dans la sortie du PDF natif, les titres des chapitres sont absents de la table des matières, ce qui entraîne une hiérarchie incorrecte.
* GUIDES-19558 : la modification et l’enregistrement d&#39;une ligne de base sur une configuration cloud expirent au bout d&#39;une minute si la ligne de base comporte un grand nombre de rubriques ou de cartes.
* GUIDES-19733 : la traduction des cartes à l’aide de la ligne de base devient lente et ne parvient pas à charger la liste de toutes les rubriques et de tous les fichiers de cartes associés.
* SITES-26798 : la promotion automatique de lancement ne met pas à jour le statut de la promotion (date de promotion).
* SITES-27137 : suppression de la dépendance aux mesures Sling commons du cœur de MSM.
* SKYOPS-75446 : l’espace AEM corrigé renvoie parfois une erreur 404 ou des pages avec du contenu manquant.
* SKYOPS-76366 : aucune mesure Jetty Threadpool dans les versions 15977 et ultérieures d’AEM.
* SKYOPS-82371 : échec de java.io.IOException: classFile.delete().
* SKYOPS-83369 : les déploiements AEM ne démarrent pas si l’exécution de la tâche de transformation ne génère pas de lots.
* SKYOPS-83910 : correction des problèmes de simultanéité détectés dans SKYOPS-82371.
* SKYOPS-84821 : définition de la configuration sling.includes.checkcontenttype du servlet principal Sling sur true.
* SKYOPS-85798 : la tâche de transformation corrigée génère des définitions d’index vides.
* SKYOPS-86251 : mise à niveau vers AEM Analyzer core 1.5.6 et activation de l’analyseur d’import de package de produit dans la tâche de transformation.
* SKYOPS-86710 : suppression des échecs de test de minimisation pour la version du sdk java 21.
* SKYOPS-86745 : mise à jour vers Sling ResourceResolver 1.12.2.
* SKYOPS-89616 : correction de l’impossibilité de créer un compte technique dans Adobe Developer Console.
* SKYOPS-89691 : correction de l’ID d’artefact incorrect utilisé pour les avertissements AEM.
* SKYOPS-89699 : avertissements manquants pour les anciennes versions de Groovy intégrées à la version « orbinson » de la console Groovy.
* SKYOPS-88664 : journalisation et protection contre le cas où le fichier de carte téléchargé contient une ligne dépassant la limite de 1024.
* SKYOPS-89734 : publication de l’image du dispatcher 2.0.235.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans Experience Manager Guides, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Problèmes connus {#known-issues-18751}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-18751}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-18751}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 3 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-18751}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.72.0 | [API Oak 1.72.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
