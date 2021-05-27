---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 740b710cf21ef967f140ef1984268d9e82ea4059
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 13%

---


# Notes de la mise à jour actuelle d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes. par exemple, pour ceux de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2021.5.0 est le 27 mai 2021.
La version suivante (2021.6.0) sera publiée le 24 juin 2021.

## AEM as a Cloud Service Foundation {#foundation}

### Nouveautés d’AEM as a Cloud Service Foundation {#what-is-new-foundation}

* [Canal de version préliminaire](/help/release-notes/prerelease.md) : Prévisualisez les fonctionnalités à venir pendant un mois complet avant qu’elles ne soient mises en production.

* [Obsolescence](/help/release-notes/deprecated-apis.md) des API : une liste des dernières API obsolètes pour AEM as a Cloud Service est disponible.

* [Module externe Maven AEM as a Cloud Service SDK Build Analyzer](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html) : Mettez à jour vos projets Maven vers la dernière version, qui inclut une vérification d’API Java obsolète et d’autres améliorations.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouveautés d’[!DNL Sites] {#what-is-new-sites}

* Vous pourrez bientôt vérifier le contenu sur un nouveau [niveau d’aperçu](/help/sites-cloud/authoring/fundamentals/previewing-content.md) pour simuler l’aspect final de l’expérience comme vous le feriez sur le niveau Publication. Cette fonctionnalité est activée par l’assistant de publication gérée d’AEM Sites qui vous permet désormais de choisir une destination de publication entre Publier ou Aperçu. Les expériences sur la prévisualisation sont ensuite accessibles via une URL dédiée. Après la validation sur l’aperçu, le contenu peut être publié de l’auteur à la publication comme d’habitude. L’activation du service de prévisualisation dans AEM en tant qu’environnements de Cloud Service sera progressivement déployée au cours des prochaines semaines.

## [!DNL Adobe Experience Manager Assets] as a  [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire {#what-is-new-assets-prerelease}

* Les schémas de métadonnées peuvent être appliqués directement aux propriétés du dossier.

   ![Ajout d’un schéma de métadonnées à partir des propriétés du dossier](/help/assets/assets/metadata-schema-folder-properties.png)

* L’outil d’ingestion en bloc de ressources vous permet d’ajouter des métadonnées lors d’une ingestion en masse.

* Une amélioration de l’expérience utilisateur affiche le nombre de ressources présentes dans un dossier. Pour plus de 1 000 ressources dans un dossier, [!DNL Assets] affiche plus de 1 000 ressources.

   ![Nombre de ressources dans un dossier affichées dans l’interface](/help/assets/assets/browse-folder-number-of-assets.png)

### Correctifs d’[!DNL Assets] {#assets-bugs-fixed}

* Le téléchargement de fichiers très volumineux bloque le [!DNL Experience Manager desktop app]. (CQ-4320942)
* Les options de la barre d’outils sont différentes lorsque la même collection est sélectionnée à partir d’un dossier et lorsqu’elle est sélectionnée à partir d’un résultat de recherche. (CQ-4321406)

#### Nouveautés de Dynamic Media {#what-is-new-dm}

* L’imagerie dynamique RGPD (Device Pixel Ratio) et l’optimisation de la bande passante du réseau vous permettent de diffuser des images de meilleure qualité de manière efficace, sur des appareils dotés d’écrans haute résolution et d’une bande passante réseau limitée. Pour plus d’informations, voir [FAQ sur l’imagerie dynamique](/help/assets/dynamic-media/imaging-faq.md).

   >[!NOTE]
   >
   >La date de publication des améliorations de l’imagerie dynamique ci-dessus est la suivante :
   >
   >* Amérique du Nord, le 24 mai 2021, dans l&#39;Alliance du Nord,
      >
      >
   * Europe, Moyen-Orient et Afrique, 25 juin 2021,
      >
      >
   * Asie-Pacifique 19 juillet 2021.


* Prise en charge du format d’image AVIF nouvelle génération dans la diffusion Dynamic Media (modificateur d’URL fmt).

   >[!NOTE]
   >
   >La date de publication de la prise en charge d’AVIF est la suivante :
   >
   >* Amérique du Nord, 10 mai 2021,
      >
      >
   * Europe, Moyen-Orient et Afrique 24 mai 2021,
      >
      >
   * Asie-Pacifique 24 juin 2021.


## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0.

### Date de publication {#release-date-cm-may}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.5.0 est le 6 mai 2021.
La prochaine version est prévue pour le 3 juin 2021.

### Nouveautés {#what-is-new-may}

* La règle de qualité PackageOverlaps détecte désormais les cas où le même package a été déployé plusieurs fois, c’est-à-dire dans plusieurs emplacements incorporés, dans le même ensemble de packages déployé.

* Le point de terminaison du référentiel dans l’API publique inclut désormais l’URL Git.

* Le journal de déploiement téléchargé par un utilisateur de Cloud Manager sera plus informatif et comprendra désormais des détails sur les échecs et les scénarios de succès.

* Les échecs intermittents rencontrés lors de la publication du code vers le git d’Adobe ont maintenant été résolus.

* Le module complémentaire Commerce peut désormais être appliqué aux programmes Sandbox pendant le workflow Modifier le programme .

* L’expérience de modification du programme a été actualisée.

* Le tableau Noms de domaine de la page Détails de l’environnement affiche jusqu’à 250 noms de domaine par pagination.

* L’onglet Solutions des workflows Ajouter un programme et Modifier le programme affiche la solution, même si une seule solution est disponible pour le programme.

* Le message d’erreur dans le journal de l’étape de génération lorsque la version ne produisait aucun module de contenu déployé n’était pas clair.

### Correctifs {#bug-fixes-cm-may}

* Parfois, l’utilisateur peut voir un état &quot;principal&quot; vert en regard d’une Liste autorisée IP même lorsque cette configuration n’a pas été déployée.

* Au lieu de supprimer des variables &quot;supprimées&quot;, l’API des variables de pipelines ne les marquerait que avec le statut **DELETED**.

* Certains problèmes de qualité du type d’odeur de code affectaient incorrectement l’évaluation de fiabilité.

* Comme les domaines génériques ne sont pas pris en charge, l’interface utilisateur ne permet pas à l’utilisateur d’envoyer un domaine de caractères génériques.

* Lorsqu’une exécution de pipeline était lancée entre minuit et 1h du matin (UTC), il n’était pas garanti que la version d’artefact générée par Cloud Manager était supérieure à une version créée le jour précédent.

* Lors de la configuration du programme Sandbox, une fois que le projet avec un exemple de code a été créé, Gérer Git s’affiche sous la forme d’un lien à partir de la carte principale de la page Aperçu.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.4.0 est le 11 mai 2021.

### Nouveautés {#what-is-new-ctt-may}

* Cette version de l’outil de transfert de contenu crée des rendus de texte pour les ressources migrées vers Cloud Service. Les rendus de texte sont nécessaires pour prendre en charge la recherche de texte intégral sur les ressources ingérées.
* Le nombre maximal de jeux de migration de l’outil de transfert de contenu qu’un utilisateur peut créer a été augmenté de 4 à 10.

### Correctifs {#bug-fixes-ctt-may}

* Plusieurs correctifs de bogues liés à la fonction d’actualisation automatique dans l’interface utilisateur de l’outil de transfert de contenu.
* L’outil de transfert de contenu avec `wipe=true` générait un index de compteur incorrect sur la cible. Ce problème a été résolu.

## Module complémentaire Commerce {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Prise en charge de la pagination pour le contenu associé dans les propriétés de la console de produit

### Correctifs {#bug-fixes-commerce}

* Miniatures des ressources non affichées dans l’onglet Ressource des propriétés du produit

* Le chemin de navigation réinitialise les données d’aperçu dans la console de produit.
