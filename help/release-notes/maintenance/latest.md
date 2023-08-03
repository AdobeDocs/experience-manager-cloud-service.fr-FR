---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: acaed9eed20e8134574fd326e23ac68130ac019b
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 11%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 12874 {#release-12874}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 12874, qui a été publiée publiquement le 2 août 2023. Cette mise à jour de maintenance est une mise à jour de la version de maintenance 12790 précédente.

2023.8.0 Feature Activation fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-12874}

- Nouvelle version de la définition d’index : `/oak:index/damAssetLucene-9`
- ASSETS-18351 : passe aux facettes non sécurisées pour améliorer les performances de recherche.
- ASSETS-17896 : supprime les vecteurs de fonctionnalités de l’index - recherche par analogie basée sur les balises intelligentes.
- ASSETS-8715 : ajoute un contrôle null/not null pour la propriété &quot;jcr:content/metadata/dam:status&quot;
- GRANITE-45138 : supprime l’index de propriété de la propriété dynamic boost des balises prédites.
- ASSETS-17614 : ajoute l’Scene7 ID en tant que propriété indexée (vérification nulle et vérification non nulle activée).
- ASSETS-14516 : ajoute des propriétés pour la fonctionnalité de corbeille de &quot;nouvelle interface utilisateur&quot; à l’index
- ASSETS-16270 : ajoute la propriété de titre fusionnée à l’index (à utiliser dans le tri).
- ASSETS-24478 : Supprimez 5 propriétés potentiellement importantes de l’index (en fonction de l’analyse des données d’index client).
- ASSETS-3383 : ajoute une balise supplémentaire &quot;assetsOmnisearch&quot;

AEM versions 12874 et ultérieures contiennent une nouvelle version de l’index damAssetLucene (damAssetLucene-9). Afin de fournir l’expérience de recherche la plus réactive, damAssetLucene-9 modifie le comportement de la facette de résultat Oak Query pour ne plus évaluer le contrôle d’accès sur les comptes de facettes renvoyés par l’index de recherche sous-jacent (appelé mode &quot;non sécurisé&quot;).

Ainsi, il est possible que les utilisateurs se voient présenter des valeurs de nombre de facettes qui incluent des ressources auxquelles l’utilisateur actuel n’a pas accès. Cela ne permet pas à l’utilisateur d’accéder à ces ressources, de les télécharger ou de les lire, et ne lui permet pas non plus d’obtenir des informations supplémentaires sur leur existence.

Si vous souhaitez appliquer le comportement précédent, les clients doivent suivre la procédure décrite à la section [Recherche et indexation de contenu](/help/operations/indexing.md) pour créer une version personnalisée de l’index damAssetLucene-9 avec le mode de facette &quot;statistique&quot; précédent.

### Problèmes résolus {#fixed-issues-12874}

- ASSETS-24379 : améliorations apportées à ReplicateOnModifyListener.
- ASSETS-25794 : résolution d’un problème avec S7ConfigResolverImpl en raison duquel il exécutait une requête coûteuse au démarrage.
- ASSETS-25473 : correction d’un bogue en raison duquel l’option Publication rapide était visible par les utilisateurs sans autorisation de réplication.
- ASSETS-24803 : Correction d’une vulnérabilité XSS dans la fonctionnalité Visionneuses .
- ASSETS-25489 : correction d’un problème en raison duquel les recadrages intelligents étaient téléchargés avec le mauvais suffixe.
- ASSETS-25435 : correction d’une erreur en raison de laquelle les champs LargeurHauteur étaient absents dans le rapport Téléchargement pour les rendus dynamiques.
- ASSETS-25741 : correction de l’absence d’astérisque visuel (`*`) pour le champ d’édition &quot;largeur&quot; obligatoire dans la section de l’onglet &quot;De base&quot;.
- ASSETS-25759 : amélioration de la visibilité de la mise au point sur les éléments de liste déroulante en modes noir/blanc à contraste élevé.
- ASSETS-25749 : correction d’un problème en raison duquel la sélection ne se déplaçait pas vers plusieurs commandes sous la vidéo lors de la navigation à l’aide de l’onglet clavier, ce qui les rendait inaccessibles.
- ASSETS-26074 : restauration de la limite de 127 caractères pour les noms de ressources non vidéo.
- ASSETS-21428 : correction d’un problème en raison duquel un champ multiligne dans l’éditeur de schéma de métadonnées chevauchait le champ suivant.
- ASSETS-21989 : correction d’un problème en raison duquel les en-têtes CORS pouvaient être écrasés sur les réponses 302 et 401, ce qui empêchait la connexion DAM distante
- ASSETS-22603 : résolution de problèmes affectant les noms et valeurs de colonne lors de l’affichage des rapports Téléchargement de ressources
- ASSETS-23120 : correction d’un problème dans AssetSetLastModifiedProcess lié aux fuites des résolveurs de ressources.
- ASSETS-24938 : correction d’un problème en raison duquel le bouton Enregistrer de la boîte de dialogue Propriétés du dossier de ressources se comportait comme Enregistrer + Fermer
- ASSETS-25456 : correction d’un problème en raison duquel une ressource portant un nom long empêchait les clics sur les actions dans l’éditeur de propriétés des ressources.
- ASSETS-25832 : correction d’un problème en raison duquel les ressources d’un dossier d’accès complet étaient liées à un dossier d’accès en lecture seule.
- ASSETS-25397 : correction d’un problème en raison duquel le nouveau nom d’une ressource renommée dans la nouvelle interface utilisateur n’était pas reflété dans les résultats de recherche.
- ASSETS-26102 : correction d’un problème qui empêchait les chargements à partir du connecteur CI Hub.
- ASSETS-26172 : réduction de la taille du contenu du journal de progression de l’importation en bloc enregistré dans les noeuds de tâche Sling persistants.
- ASSETS-26292 : méthodes obsolètes AssetManager createOrUpdateAsset() et createOrReplaceAsset() dans l’API Java
- ASSETS-26399 : correction d’un problème qui empêchait la publication de collections sur Brand Portal
- ASSETS-26533 : correction d’un problème dans l’intégration d’InDesign Server qui entraînait un délai d’expiration pour les demandes de traitement long.
- ASSETS-26549 : correction d’un problème en mode Liste des ressources en raison duquel &quot;Utilisateur externe&quot; s’affichait comme le dernier utilisateur modifié pour toutes les ressources chargées.
- ASSETS-26551 : résolution d’un problème en raison duquel les ressources supprimées sur l’auteur n’étaient pas dépubliées
- ASSETS-26571 : correction d’un problème lié à la page Rapports de ressources en raison duquel la page ne se chargeait pas si plusieurs tâches de rapport échouaient dans la liste.
- ASSETS-26147 : correction d’un problème en raison duquel le Shell unifié tentait de rediriger un iframe dans /ui lorsque window.top.opener était défini mais pas window.opener.
- ASSETS-26576 : correction d’un problème lié à l’importation de Dropbox en raison duquel une hiérarchie de dossiers incorrecte était créée.
- ASSETS-26671 : correction d’un problème empêchant l’importation en bloc d’inclure les fichiers situés dans un dossier DCIM.
- ASSETS-26700 : correction d’un problème en raison duquel l’enregistrement de la page des propriétés d’un dossier public sans modification créait 3 groupes inutiles.
- CQ-4353449 : correction d’un problème en raison duquel les utilisateurs disposant de droits de balisage en lecture seule pouvaient créer des balises à l’aide de l’interface utilisateur de balisage.
- GRANITE-46601 : correction d’un problème qui empêchait le démarrage du SDK Quickstart sur JDK 11.0.20
- SKYOPS-33168 : correction d’un problème dans CM Developer Console qui empêchait le chargement de /content/dam pour les noms de ressources sans extension.
- SKYOPS-61484 : correction d’un problème dans le service RDEProvider qui autorisait la persistance des jetons ${sling.home} non substitués dans les configurations OSGi fusionnées.
- Divers correctifs de sécurité, d’accessibilité et de localisation

### Problèmes connus {#known-issues-12874}

- GRANITE-46851 : Le test de la connexion dans la distribution de contenu ne fonctionne pas

### Technologies intégrées {#embedded-tech-12874}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [API Oak 1.52.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
