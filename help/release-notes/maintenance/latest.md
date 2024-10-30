---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9278ec9bb5bccd7b40cd65a120f296faba454b9c
workflow-type: ht
source-wordcount: '569'
ht-degree: 100%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 18311 {#18311}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 18311, publiée le 22 octobre 2024. La version de maintenance précédente était la version 18175.

L’activation des fonctionnalités de la version 2024.10.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-18311}

* ASSETS-41820 : améliorations de l’indexation pour le traitement Watchdog.
* ASSETS-43720 : améliorations fonctionnelles du traitement Watchdog.
* ASSETS-42554 : améliorations des performances pour les dossiers volumineux.
* SKYOPS-77603 : gestion des redirections par les utilisateurs et utilisatrices professionnels.

### Problèmes résolus {#fixed-issues-18311}

* ASSETS-37534 : modifications de la recherche pour ne pas exposer la propriété utilisée pour la cible de l’approbation.
* ASSETS-38322 : suppression de la configuration du fournisseur de critères de publication et de la fonctionnalité d’événement de publication.
* ASSETS-40482 : problème d’accessibilité dans les boutons de lecture/pause et de désactivation/activation du son dans le lecteur vidéo Scene7.
* ASSETS-40593 : production d’une page d’erreur après avoir cliqué sur le bouton « Propriétés » dans Ressources > Fichiers.
* ASSETS-40598 : synchronisation des recadrages intelligents lors du déplacement d’une ressource non synchronisée vers un dossier synchronisé.
* ASSETS-40743 : problèmes de déclenchement de la boîte de dialogue Remplacer les ressources lorsque certains caractères existent dans le nom du fichier.
* ASSETS-40825 : disparition des facettes de recherche des ressources après modification du formulaire de recherche.
* ASSETS-41007 : suppression dans AEM laissant parfois des ressources orphelines lors de la diffusion.
* ASSETS-41172 : caractères spéciaux non autorisés dans le nom des modèles Dynamic Media.
* ASSETS-41896 : ressources indiquées dans la propriété cq:discarded du dossier à ne PAS publier sur Brand Portal.
* ASSETS-42067 : modèles Dynamic Media - téléchargement générant une erreur.
* ASSETS-42070 : modèles Dynamic Media - les utilisateurs et les utilisatrices n’appartenant pas à l’administration doivent avoir accès à la création et à la modification des modèles.
* ASSETS-42344 : déconnexion de la synchronisation des ressources connectées - reconnexion et conseil au client ou à la cliente.
* ASSETS-42620 : problème avec l’option de prévisualisation des versions de ressources - affiche une prévisualisation vide lors de l’ouverture de la ressource.
* ASSETS-42701 : problème de diffusion et de recadrage des images optimisées pour le web.
* ASSETS-42966 : la barricade asynchrone peut se débloquer par erreur si plusieurs traitements partagent le même chemin.
* ASSETS-43072 : modèles Dynamic Media - la recherche de références de modèle dans les modèles Dynamic Media échoue lorsqu’une référence n’est pas valide.
* ASSETS-43212 : problèmes d’internationalisation dans l’éditeur de schéma de métadonnées.
* ASSETS-43202 : corrections pour la sélection des annotations à imprimer depuis la chronologie.
* ASSETS-43502 : le nom du paramètre d’image prédéfini existant dans AEM CS ne s’affiche pas sur Modifier la page.
* ASSETS-43538 : traitement de copie asynchrone des ressources utilisant une propriété incorrecte pour le chemin source.
* ASSETS-43798 : vérification du chemin de destination avant la copie des ressources.
* ASSETS-43945 : augmentation du délai de nouvelle tentative à 20 minutes pour la file d’attente des traitements asynchrones de ressources.
* ASSETS-44025 : échec du traitement de suppression asynchrone des ressources lorsque des ressources individuelles sont sélectionnées.
* SITES-26128 : exception de conversion de classe dans CreateLiveCopyStep.
* SCRNS-4551 : le canal Screens dans [SG Pools] contenant un composant vidéo affiche « Erreur de page générale » dans la prévisualisation du navigateur et le lecteur.

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
