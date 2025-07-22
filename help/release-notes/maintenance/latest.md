---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a4e023ca44c93124627912bae08dc3535d48400c
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 34%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 21644 {#21644}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 21644, publiée le mercredi 22 juillet 2025. La version de maintenance précédente était la version 21570.

L’activation des fonctionnalités de la version 2025.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-21644}

* ASSETS-39377 : amélioration de la gestion des 429 à partir du stockage distant dans l’importateur en bloc Assets.
* ASSETS-46026 : profondeur maximale configurable pour l’exportateur de métadonnées.
* ASSETS-49172 : les ressources de modèle Dynamic Media doivent hériter des métadonnées du dossier .
* ASSETS-50209 : prise en charge de la sous-chaîne dans les modèles DM.
* ASSETS-52326 : page de configuration d’AEM Assets pour définir les préférences d’affichage du titre pour Assets.
* ASSETS-52805 : ajoute la prise en charge du téléchargement/de la sortie CSV pour le traitement des opérations en bloc.
* ASSETS-52873 : ajoutez une nouvelle configuration dans les propriétés du dossier pour désactiver le traitement par l’IA de ce dossier.
* ASSETS-53535 : amélioration des performances de chargement vidéo YouTube.
* ASSETS-53612 : contrôle de la recherche hybride dans Assets Omnisearch.
* GRANITE-60183 : mettez à jour la dépendance commons-fileupload vers la version 1.6.0.
* GRANITE-60287 : mise à jour de QS vers Jackrabbit 2.22.1.
* SITES-30452 : API de contenu avec ASO - Suggestions de titre et de description.
* SITES-31677 : l’espace de travail personnalisé prend en charge l’export de fragments de contenu AEM vers Target.
* SKYOPS-112741 : suppression du lot `com.adobe.granite.product.support` du SDK AEM-CS.

### Problèmes résolus {#fixed-issues-21644}

* ASSETS-12882 : problèmes d’alignement de l’interface utilisateur après ouverture des paramètres prédéfinis de visionneuse.
* ASSETS-48958 : problème de modification du statut de publication de la synchronisation des ressources dans l’AEM locale Sites.
* ASSETS-50856 : `dam:processingAttempts` réinitialisation n’est pas en cours lors du chargement complet.
* ASSETS-51604 : rapport de partage de lien CSV avec des données manquantes « Partagé avec ».
* ASSETS-51783 : basculement vers la configuration de gestion des ressources numériques sous `/conf/global` si aucune configuration n’est trouvée à l’aide de la requête.
* ASSETS-51857 : éléments du tableau des ressources ne peuvent pas être réorganisés.
* ASSETS-52169 : le nouveau rendu de machine BAT est inclus par erreur dans les téléchargements de ressources.
* ASSETS-52229 : notifications de boîte de réception manquantes pour les rapports de ressources dans AEM as a Cloud Service.
* ASSETS-52399 : le bogue de version dans com.day.cq.dam.api peut endommager le code client.
* ASSETS-52780 : la ressource peut être marquée pour l’aperçu même si elle n’est pas activée.
* ASSETS-52866 : les vidéos DM migrées restent à l’état de traitement sous le dossier avec la synchronisation DM désactivée.
* ASSETS-53237 : liste déroulante Profil colorimétrique vide dans l’éditeur de paramètres prédéfinis d’image.
* ASSETS-53240 : Rapport sur les ressources - L’utilisation du disque échoue lors de l’obtention de la taille de rendu de la ressource à partir de Dynamic Media.
* ASSETS-53446 : échecs d’actualisation intermittente du jeton d’authentification YouTube en raison de NPE.
* ASSETS-53827 : la validation de l’ACL bloque l’enregistrement des visionneuses de médias mixtes.
* ASSETS-5403 : les bibliothèques clientes Dynamicmedia utilisées sur l’instance de publication doivent avoir le `allowProxy=true` .
* ASSETS-54261 : l’importation de métadonnées fuit les connexions et est bloquée si le téléchargement du fichier échoue.
* CQ-4359863 : La recherche de balises est interrompue pour des mots-clés dans l’éditeur de fragment de contenu/l’éditeur de ressources.
* CQ-4359958 : Rendre la prise en charge d’openapi compatible avec AEM 6.5.22.0 et versions ultérieures.
* CQ-4360256 : incluez le chemin d’accès au contexte du servlet dans le chemin d’accès de la requête pour les requêtes HTTP gérées via le contexte du servlet `/adobe`.
* CQ-4360317 : ajoutez une méthode pour définir l’en-tête Date de fin lors de la création de réponses.
* GRANITE-60311 : démarrage rapide AEM SDK - NPE sur « Imprimante de configuration du programme d’installation OSGi ».
* GS-15285 : les utilisateurs sont marqués comme désactivés.

### Problèmes connus {#known-issues-21644}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-21644}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-21644}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige quatre vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-21644}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.80.0 | [API Oak 1.80.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2,4,63 | [Apache Httpd 2.4.63](https://github.com/apache/httpd/blob/2.4.63/CHANGES) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
