---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 3686697c85273ccc13e80b8d7f4ad1ff3c79845d
workflow-type: ht
source-wordcount: '632'
ht-degree: 100%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 21706 {#21706}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 21706, publiée le 24 juillet 2025. La version de maintenance précédente était la version 21570.

>[!NOTE]
>
>La version 21644 a été rendue privée et remplacée par la version 21706.

L’activation des fonctionnalités de la version 2025.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-21706}

* ASSETS-39377 : amélioration de la gestion de 429s à partir du stockage distant dans l’importateur de ressources en bloc.
* ASSETS-46026 : profondeur maximale configurable pour l’exporteur de métadonnées.
* ASSETS-49172 : les ressources de modèle Dynamic Media doivent hériter des métadonnées du dossier.
* ASSETS-50209 : prise en charge de la sous-chaîne dans les modèles DM.
* ASSETS-52326 : page de configuration d’AEM Assets pour définir les préférences d’affichage du titre pour les ressources.
* ASSETS-52805 : ajoute la prise en charge du téléchargement/de la sortie CSV pour le traitement des opérations en bloc.
* ASSETS-52873 : ajout d’une nouvelle configuration dans les propriétés du dossier pour désactiver le traitement par l’IA de ce dossier.
* ASSETS-53535 : amélioration des performances de chargement vidéo de YouTube.
* ASSETS-53612 : contrôle de la recherche hybride dans Assets Omnisearch.
* GRANITE-60183 : mise à jour de la dépendance commons-fileupload vers la version 1.6.0.
* GRANITE-60287 : mise à jour de QS vers Jackrabbit 2.22.1.
* SITES-30452 : API de contenu avec ASO - Suggestions de titre et de description.
* SITES-31677 : l’espace de travail personnalisé prend en charge l’export de fragments de contenu AEM vers Target.
* SKYOPS-112741 : suppression du lot `com.adobe.granite.product.support` du SDK AEM-CS.

### Problèmes résolus {#fixed-issues-21706}

* ASSETS-12882 : problèmes d’alignement de l’UI après ouverture des paramètres prédéfinis de l’affichage.
* ASSETS-48958 : problème de modification du statut de publication de la synchronisation des ressources dans la version locale d’AEM Sites.
* ASSETS-50856 : réinitialisation non effectuée de `dam:processingAttempts` sur completeUpload.
* ASSETS-51604 : rapport de partage de lien CSV ne contenant pas les données « Partagé avec ».
* ASSETS-51783 : sauvegarde vers la configuration DM sous `/conf/global` lorsqu’aucune configuration n’est trouvée à l’aide de la requête.
* ASSETS-51857 : les éléments du tableau des ressources ne peuvent pas être réorganisés.
* ASSETS-52169 : le nouveau rendu automatique de BAT est inclus par erreur dans les téléchargements de ressources.
* ASSETS-52229 : notifications de boîte de réception manquantes pour les rapports de ressources dans AEM as a Cloud Service.
* ASSETS-52399 : le bogue de version dans com.day.cq.dam.api peut endommager le code du client ou de la cliente.
* ASSETS-52780 : la ressource peut être marquée pour prévisualisation, même si elle n’est pas activée.
* ASSETS-52866 : les vidéos DM migrées restent à l’état de traitement sous le dossier avec la synchronisation DM désactivée.
* ASSETS-53237 : liste déroulante Profil colorimétrique vide dans l’éditeur de paramètres prédéfinis d’image.
* ASSETS-53240 : Rapport sur les ressources - L’utilisation du disque échoue lors de l’obtention de la taille de rendu de la ressource à partir de Dynamic Media.
* ASSETS-53446 : échecs d’actualisation intermittente du jeton d’authentification YouTube en raison du NPE.
* ASSETS-53827 : la validation de l’ACL bloque l’enregistrement des visionneuses de médias mixtes.
* ASSETS-5403 : les bibliothèques clientes Dynamicmedia utilisées sur l’instance de publication doivent avoir `allowProxy=true`.
* ASSETS-54261 : l’import de métadonnées provoque des fuites de connexions et est bloqué si le téléchargement du fichier échoue.
* CQ-4359863 : la recherche de balises est interrompue pour des mots-clés inopérants dans l’éditeur de fragments de contenu/l’éditeur de ressources.
* CQ-4359958 : rendre la prise en charge d’openapi compatible avec AEM 6.5.22.0 et versions ultérieures.
* CQ-4360256 : inclure le chemin d’accès au contexte du servlet dans le chemin d’accès de la requête pour les requêtes HTTP gérées via le contexte du servlet `/adobe`.
* CQ-4360317 : ajouter une méthode pour définir l’en-tête Date d’expiration lors de la création de réponses.
* GRANITE-60311 : SDK de démarrage rapide AEM - NPE sur « Imprimante de configuration du programme d’installation OSGi ».
* GS-15285 : les utilisateurs et utilisatrices apparaissent comme étant désactivés.

### Problèmes connus {#known-issues-21706}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-21706}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-21706}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige quatre vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-21706}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.80.0 | [API Oak 1.80.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.63 | [Apache Httpd 2.4.63](https://github.com/apache/httpd/blob/2.4.63/CHANGES) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
