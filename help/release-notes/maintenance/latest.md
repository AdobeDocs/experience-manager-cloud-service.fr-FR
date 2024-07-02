---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 90b4cf269fc8be36d90f398d1696fc40f89f5142
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 87%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 16799 {#release-16799}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 16799, publiée le 18 juin 2024. La version de maintenance précédente était la version 16544.

L’activation des fonctionnalités de la version 2024.6.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-16799}

* ASSETS-31977 : amélioration des opérations de déplacement, de copie et de suppression de ressources.
* ASSETS-33618 : fonctionnalité de transcription automatique et de traduction pour les vidéos dans Dynamic Media.
* ASSETS-35185 : action d’approbation pour ContentHub et DM et ajout de propriétés aux propriétés damAssetLucene.
* ASSETS-35533 : ajout des propriétés DRM et CAI à l’index damAssetLucene.
* ASSETS-37280 : gestion séquentielle des traitements pour la traduction lorsque le sous-titre source (vtt) est toujours en cours de traitement.
* ASSETS-37559 : amélioration d’un événement de suppression de ressource.
* ASSETS-37723 : implémentation d’un événement de publication de ressource.
* ASSETS-37724 : implémentation d’un événement de dépublication de ressource.
* ASSETS-38614 : améliorations de l’interface d’utilisation de partage de lien.
* ASSETS-39601 : application automatique de l’expression régulière de validation au nom de la Live Copy de la ressource.
* ASSETS-39454 : mise à niveau vers les visionneuses 2024.5.0 dans Quickstart.
* CNTBF-184 : chemins d’accès de support sous `/conf` dans le retour de contenu.

### Problèmes résolus {#fixed-issues-16799}

* ASSETS-37335 : la modification du panneau Rechercher dans le filtre décoche toutes les cases.
* ASSETS-38069 : problème d’aperçu du PDF de gestion des ressources numériques AEM lors de la sélection du filtre de la chronologie.
* ASSETS-38215 : bouton de licence Adobe Stock grisé dans AEM as a Cloud Service pour l’abonnement Entreprise.
* ASSETS-38578 : liens hypertexte incorrects dans le rapport Partage de liens de ressources.
* ASSETS-38678 : dysfonctionnement des paramètres d’affichage dans Détails de la collection.
* ASSETS-39071 : la diffusion optimisée pour le web peut générer une exception si le type MIME de rendu d’origine est nul.
* ASSETS-39316 : le tri par nom ne fonctionne pas dans les collections.
* ASSETS-39377 : l’import en masse à partir de OneDrive peut échouer lors de la réception de backpressure provenant d’une API distante.
* ASSETS-39428 : problèmes de rendu dans l’interface d’utilisation de la gestion des droits d’auteur.
* CQ-4357150 : Guava dans le lot cq-content-sync.
* GRANITE-52573 : les requêtes contenant une double barre oblique `//` sont refusées avec le code d’état 400.
* SCRNS-4194 : suppression de la dépendance aux API Google Guava.
* SCRNS-4360 : absence du bouton Gérer la publication et Publication rapide pour les personnes ne faisant pas partie de l’équipe d’administration dans le fournisseur de contenu pour les canaux.
* SCRNS-4323 : masquer/désactiver les lancements à partir de screens.html.

#### Forms

* FORMS-14844 : Forms adaptatif autorise l’envoi de formulaire malgré l’échec de la vérification reCAPTCHA.
* FORMS-14984 : Forms avec CAPTCHA ignore la validation si &quot;submitMetaData&quot; est absent des données envoyées.
* FORMS-14477 : Les options &quot;Après&quot; et &quot;Avant&quot; de l’éditeur de règles ne fonctionnent pas dans la validation du sélecteur de date.
* FORMS-14019 : la fonctionnalité &quot;Invoke Service&quot; de l’éditeur de règles ne fonctionne pas dans Universal Editor.
* FORMS-14336 : lorsqu’aucun champ de formulaire n’est sélectionné, l’éditeur doit s’ouvrir en mettant l’accent sur l’ensemble de l’élément de formulaire.
* FORMS-15061 : le cercle de chargeur persiste indéfiniment lors de l’utilisation de l’option d’appel du service dans l’éditeur de règles.

### Problèmes connus {#known-issues-16799}

>[!NOTE]
> L’équipe d’ingénierie AEM a identifié une régression pour la fonctionnalité de lancements qui affecte les versions d’AEM actuelles à partir de la version 16461. En raison de cette régression, les nouveaux lancements (créés après l’application de nouvelles versions) qui incluent des pages non profondes ne seront pas correctement promus en raison de configurations manquantes.
> Si vos environnements sont affectés, un script shell permettant d’identifier et de mettre à jour les configurations manquantes est disponible via le service clientèle (référence interne SITES-22457).
> Un correctif à plus long terme sera disponible pour garantir que de nouveaux lancements sont créés avec toutes les configurations appropriées. D’ici là, un correctif interne est également disponible à la demande.

#### Forms

1. Si un utilisateur ou une utilisatrice télécharge la version du SDK AEM Forms supérieure à `AEM Forms add-on v2024.05.04.00-240400`, le fichier de lot ne démarre pas le service Docker. Pour résoudre ce problème, procédez comme suit :
   1. Téléchargez le [dossier](/help/forms/assets/sdk_hotfix.zip).
   1. Extrayez le contenu du dossier téléchargé et copiez les fichiers `sdk.sh` et `sdk.bat`.
   1. Remplacez les fichiers `sdk.sh` et `sdk.bat` existants par les nouveaux fichiers dans votre SDK AEM Forms.

### Avis de modification {#change-notice-16799}

* Cette version contient les nouvelles versions de l’index de produit suivantes :
   * **damAssetLucene-11**
   * **fragments-11**

  Les versions personnalisées des versions d’index précédentes seront automatiquement fusionnées avec la nouvelle version de l’index de produit. Appliquez d’autres mises à jour personnalisées à la version fusionnée.

* À compter de septembre 2024, AEM as a Cloud Service désactivera la sérialisation des résolveurs de ressources via le framework de l’exportateur de modèle Sling. Voir la [documentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) pour plus d’informations.

### Fonctionnalités et API obsolètes {#deprecated-16799}

Pour savoir ce qui est obsolète ou supprimé dans AEM as a Cloud Service, voir [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Technologies intégrées {#embedded-tech-16799}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.64.0 | [API Oak 1.64.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| API SLING AEM | 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.25.4 | [Composants principaux de la gestion de contenu Web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
