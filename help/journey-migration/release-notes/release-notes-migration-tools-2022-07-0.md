---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.7.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.7.0
feature: Release Information
exl-id: bc8f1a80-867e-423a-9c03-4a53b1ebc57c
source-git-commit: a878afbfc3531ae1779ca16851bbda43cbc20b90
workflow-type: ht
source-wordcount: '430'
ht-degree: 100%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.7.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.7.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.30 est le 27 juillet 2022.

### Nouveautés {#what-is-new-bpa}

* L’outil BPA peut désormais détecter et générer des rapports sur la taille totale de l’index Lucene pouvant être migré, qui est l’index Lucene total à l’exclusion de `/oak:index/lucene` et de `/oak:index/damAssetLucene`.
* Nouveau modèle ajouté à l’outil BPA pour détecter et générer des rapports sur l’utilisation d’un dictionnaire i18n personnalisé. Translator.html n’est pas disponible dans AEM as a Cloud Service et le dictionnaire i18n personnalisé doit être déployé à partir de Git via le pipeline CI/CD de Cloud Manager.

### Correctifs {#bug-fixes-bpa}

* BPA signalait l’absence de rendus originaux pour les fragments de contenu. Comme les fragments de contenu n’ont pas de rendus, cette vérification est désormais ignorée pour les fragments de contenu.
* L’option permettant de filtrer les résultats d’ACS Commons était absente de l’interface utilisateur de l’outil BPA. Ce problème a été résolu.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v2.0.12 est le 19 juillet 2022.

### Nouveautés {#what-is-new-ctt}

* Les utilisateurs connectés via LDAP peuvent désormais exécuter les fonctions de vérification de taille et de mappage des utilisateurs dans CTT.
* Pour aider à déboguer les problèmes de connexion SSL/TLS lors des extractions, les utilisateurs peuvent désormais activer la journalisation SSL.
* Pour aider à déboguer les problèmes de connectivité source, les noms de sous-domaines sont désormais imprimés dans les journaux lorsque la connexion à Azure échoue.
* Pour aider à déboguer les problèmes qui surviennent lors de la pré-copie, les journaux AzCopy sont désormais ajoutés aux journaux d’extraction en cas d’échec de la pré-copie.
* Pour éviter que les résultats de vérification de la taille ne soient obsolètes, les utilisateurs ne pourront réexécuter la vérification de la taille qu’une fois la vérification précédente terminée.

### Correctifs {#bug-fixes-ctt}

* Les journaux d’extraction précédents s’affichaient après la suppression et la recréation d’un jeu de migration. Ce problème a été résolu.
* Le bouton d’action Afficher la progression n’était pas disponible pour les jeux de migration au statut STOPPED. Ce problème a été résolu.
* Le bouton Supprimer n’était pas disponible pour les jeux de migration avec une clé d’extraction expirée. Ce problème a été résolu.
* Plusieurs bugs de l’interface utilisateur ont été corrigés.

## Cloud Acceleration Manager {#cam-release}

### Date de publication {#release-date-cam}

La date de publication de Cloud Acceleration Manager est le 15 juillet 2022.

### Nouveautés {#what-is-new-cam}

* Cloud Acceleration Manager permet désormais aux utilisateurs de récupérer manuellement le jeton de migration pour pouvoir démarrer une ingestion en cas d’échec de récupération automatique. La récupération automatique peut échouer si les clients ont configuré une liste autorisée d’adresses IP qui bloque CAM ou si un utilisateur non administrateur tente de démarrer une ingestion. Consultez la section [Dépannage](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#troubleshooting) pour plus d’informations.
* Les grands tableaux de la page Complexité de la migration sont désormais réductibles pour faciliter leur utilisation.
