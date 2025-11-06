---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 45%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

>[!NOTE]
>
>La version 23122 a été rendue privée le 3 novembre.

## Version 22943 {#22943}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 22943, publiée le mercredi 14 octobre 2025. La version de maintenance précédente était la version 22758.

L’activation des fonctionnalités de la version 2025.10.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-22943}

* ASSETS-57809 : mise à jour de la définition d’index pour damAssetLucene-13.
* ASSETS-36521 : Workflow de rechargement DM amélioré pour assurer un post-traitement cohérent.
* ASSETS-56400 : ajout d’un nouveau rendu PNG de zoom prêt à l’emploi pour les ressources avec transparence.
* ASSETS-55326 : activation de la vue de configuration du dossier de métadonnées d’IA via des événements HTTP.
* ASSETS-56905 : prend en charge la connexion à Indesign via proxy.
* ASSETS-48286 : ajout de propriétés CAI à Algolia pour GenStudio.
* ASSETS-48653 : application du filigrane invisible dans la phase de prétraitement.
* ASSETS-55874 : migration du paramètre prédéfini d’image de scene7 vers DMWithOpenapi.
* SITES-30452 : améliorations de l’API de contenu pour ASO sur le point d’entrée /content/definition.

### Problèmes résolus {#fixed-issues-22943}

* ASSETS-56301 : correction de l’exportation sélective de métadonnées pour inclure les balises prédites dans le fichier CSV.
* ASSETS-55543 : refonte de la logique de traitement asynchrone en un lot réutilisable.
* ASSETS-54789 : correction de NPE dans ACLPermissionsValidator lorsque la liste de contrôle d’accès de DM est activée.
* ASSETS-55888 : correction d’un rendu de programme malveillant qui apparaissait dans le panneau Rendus de l’interface utilisateur.
* GRANITE-62236 : correction d’un problème de localisation par mot-clé dans les recherches enregistrées de collections dynamiques.
* GRANITE-61875 : correction d’un problème de correctif « évaluation d’expression non valide » empêchant l’enregistrement des fragments de contenu et des téléchargements de ressources.
* SITES-24074 : navigation mobile fixe masquée recevant le focus lors de la navigation par onglets au clavier.
* SITES-33611 : correction d’un problème d’aperçu de Live Copy pour les marchés à volume élevé.

#### AEM Guides {#guides-22943}

* GUIDES-31421 : lorsque plusieurs plans ou rubriques DITA sont ouverts et que l&#39;une des rubriques est fermée, le bouton **>>** qui affiche tous les onglets ouverts est chevauché par les onglets ouverts restants dans la barre d&#39;onglets.
* GUIDES-33229 : lors de la génération de PDF, les règles de filtrage d’un fichier DITAVAL sont ignorées si un nom de propriété contient un point.
* GUIDES-33720 : lors du zoom sur l’écran de l’interface utilisateur de traduction, le bouton Envoyer pour traduction se déplace sous les points de suspension et devient activé même si aucune ressource n’est sélectionnée.
* GUIDES-33590 : Lorsqu’un réviseur termine une tâche de révision ou qu’un initiateur met à jour la tâche de révision sans saisir de commentaires, l’e-mail de notification envoyé affiche le dernier commentaire précédent.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Fonctionnalités et API obsolètes {#deprecated-22943}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-22943}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 14 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Avis de modification

* Cette version contient les nouvelles versions de l’index de produit suivantes :
* **damAssetLucene-13**

### Technologies intégrées {#embedded-tech-22943}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.86.0 | [API Oak 1.86.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.86/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
