---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.7.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.7.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: 05adf79b66c36e6354fe95fe4d5f654b49980589
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 23%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.7.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.7.0.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.30 de l’analyseur des bonnes pratiques est le 27 juillet 2022.

### Nouveautés {#what-is-new-bpa}

* Le BPA peut désormais détecter et générer des rapports sur la taille totale de l’index Lucene migable, qui est l’index Lucene total à l’exclusion de `/oak:index/lucene` et `/oak:index/damAssetLucene`.
* Nouveau modèle ajouté dans l’application d’une seule page pour détecter et rapporter l’utilisation d’un dictionnaire i18n personnalisé. Translator.html n’est pas disponible dans AEM dictionnaire i18n as a Cloud Service et personnalisé doit être déployé à partir de Git via le pipeline CI/CD de Cloud Manager.

### Correctifs {#bug-fixes-bpa}

* BPA signalait l’absence de rendus originaux pour les fragments de contenu. Comme les fragments de contenu n’ont pas de rendus, cette vérification est désormais ignorée pour les fragments de contenu.
* L’option permettant de filtrer les résultats d’ACS Commons était absente de l’interface utilisateur de BPA. Ce problème a été résolu.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v2.0.12 est le 19 juillet 2022.

### Nouveautés {#what-is-new-ctt}

* Les utilisateurs connectés via LDAP peuvent désormais exécuter les fonctions de vérification de taille et de mappage des utilisateurs dans CTT.
* Pour aider à déboguer les problèmes de connexion SSL/TLS lors des extractions, les utilisateurs peuvent désormais activer la journalisation SSL.
* Pour aider à déboguer les problèmes de connectivité source, les noms de sous-domaine sont désormais imprimés dans les journaux lorsque la connexion à Azure échoue.
* Pour résoudre les problèmes de débogage lors de la pré-copie, les journaux AzCopy sont maintenant ajoutés aux journaux d’extraction en cas d’échec de la pré-copie.
* Pour éviter que la taille de contrôle ne soit obsolète, les utilisateurs ne pourront réexécuter la taille de contrôle qu’une fois la taille de contrôle précédente terminée.

### Correctifs {#bug-fixes-ctt}

* Les journaux d’extraction précédents s’affichaient après la suppression et la recréation d’un jeu de migration. Ce problème a été résolu.
* Le bouton d’action Afficher la progression n’était pas disponible pour les jeux de migration avec l’état STOPPED. Ce problème a été résolu.
* Le bouton Supprimer l’action n’était pas disponible pour les jeux de migration avec une clé d’extraction expirée. Ce problème a été résolu.
* Plusieurs bogues de l’interface utilisateur ont été corrigés.

## Cloud Acceleration Manager {#cam-release}

### Date de publication {#release-date-cam}

La date de publication de la mise à jour de Cloud Acceleration Manager est le 15 juillet 2022.

### Nouveautés {#what-is-new-cam}

* Cloud Acceleration Manager permet désormais aux utilisateurs de récupérer manuellement le jeton de migration pour pouvoir démarrer une ingestion en cas d’échec de récupération automatique. La récupération automatique peut échouer si les clients ont configuré une liste autorisée IP qui bloque la gestion des données cumulatives ou si un utilisateur non-administrateur tente de démarrer une ingestion. Voir [Dépannage](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#troubleshooting) pour plus d’informations.
* Les tables longues de la page Complexité de la migration sont désormais réductibles pour faciliter leur utilisation.
