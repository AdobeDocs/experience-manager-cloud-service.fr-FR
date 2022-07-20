---
title: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.7.0
description: Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.7.0
feature: Release Information
source-git-commit: f84327096951772e1bed8656334841e1292d6bcf
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 28%

---

# Notes de mise à jour pour les outils de migration dans AEM as a Cloud Service version 2022.7.0 {#release-notes}

Cette page présente les notes de mise à jour pour les outils de migration dans AEM as a Cloud Service 2022.7.0.

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

