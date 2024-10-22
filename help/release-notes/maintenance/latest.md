---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9278ec9bb5bccd7b40cd65a120f296faba454b9c
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 38%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 18311 {#18311}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 18311, publiée le mercredi 22 octobre 2024. La version de maintenance précédente était la version 18175.

L’activation des fonctionnalités de la version 2024.10.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-18311}

* ASSETS-41820 : améliorations de l’indexation pour le contrôle du traitement.
* ASSETS-43720 : améliorations fonctionnelles du contrôle du traitement.
* ASSETS-42554 : améliorations des performances pour les dossiers volumineux.
* SKYOPS-77603 : gestion des redirections par les utilisateurs professionnels.

### Problèmes résolus {#fixed-issues-18311}

* ASSETS-37534 : modifications de la recherche pour ne pas exposer la propriété utilisée pour la cible d’approbation.
* ASSETS-38322 : suppression de la configuration du fournisseur de critères de publication Supprimer la fonction d’événement de publication.
* ASSETS-40482 : problème d’accessibilité dans le bouton de lecture/pause et d’arrêt/d’annulation dans le lecteur vidéo Scene7.
* ASSETS-40593 : la page d’erreur se produit après avoir cliqué sur le bouton &quot;Propriétés&quot; dans Assets > Fichiers.
* ASSETS-40598 : Synchronisation des recadrages intelligents lorsque la ressource non synchronisée est déplacée vers un dossier compatible avec la synchronisation.
* ASSETS-40743 : problèmes de déclenchement de la boîte de dialogue Remplacer les ressources lorsque certains caractères existent dans le nom du fichier.
* ASSETS-40825 : Les Facettes De Recherche Assets Disparaissent Après La Modification Du Formulaire De Recherche.
* ASSETS-41007 : la suppression sur AEM laisse parfois Assets orphelin à la livraison.
* ASSETS-41172 : les caractères spéciaux des modèles Dynamic Media ne sont pas autorisés dans le nom.
* ASSETS-41896 : Assets mentionné dans la propriété cq:discarded du dossier ne doit PAS être publié sur Brand Portal.
* ASSETS-42067 : Dynamic Media Templates - Download (Modèles - Téléchargement) renvoie une erreur.
* ASSETS-42070 : Modèles Dynamic Media - Les utilisateurs non-administrateurs doivent disposer d’un accès de création/modification de modèles.
* ASSETS-42344 : Synchronisation d’Assets connectée déconnectée - Reconnectez et donnez des conseils au client.
* ASSETS-42620 : problème lié à l’option d’aperçu des versions de ressources : affiche un aperçu vide lors de l’ouverture de la ressource.
* ASSETS-42701 : problème de livraison et de recadrage d’images optimisées pour le web.
* ASSETS-42966 : la barricade asynchrone peut être débloquée en erreur si plusieurs tâches partagent le même chemin.
* ASSETS-43072 : Modèles Dynamic Media - Sauts de recherche de références de modèle sur une référence non valide.
* ASSETS-43212 : problèmes d’internationalisation dans l’éditeur de schéma de métadonnées.
* ASSETS-43202 : correctifs permettant de sélectionner des annotations à imprimer à partir de la chronologie.
* ASSETS-43502 : AEM nom du paramètre d’image prédéfini existant de CS non affiché sur la page de modification.
* ASSETS-43538 : la tâche de copie asynchrone des ressources utilise une propriété incorrecte pour le chemin d’accès source.
* ASSETS-43798 : recherchez d’abord le chemin de destination avant de copier les ressources.
* ASSETS-43945 : augmentez le délai de reprise à 20 minutes pour la file d’attente des tâches de ressources asynchrones.
* ASSETS-44025 : la tâche de suppression asynchrone des ressources échoue lorsque des ressources individuelles sont sélectionnées.
* SITES-26128 : la classe projette une exception dans CreateLiveCopyStep.
* SCRNS-4551 : [Pools SG] Le canal Screens contenant le composant vidéo affiche &quot;Erreur générale de page&quot; sur l’aperçu du navigateur et du lecteur

### Problèmes connus {#known-issues-18311}

* FORMS-15818 : entrée du descripteur de composant `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` introuvable dans les journaux de serveur. Ce sont des instructions de journal inoffensives.

### Fonctionnalités et API obsolètes {#deprecated-18311}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-18311}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 3 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-18311}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.70.0 | [API Oak 1.70.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.27.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
