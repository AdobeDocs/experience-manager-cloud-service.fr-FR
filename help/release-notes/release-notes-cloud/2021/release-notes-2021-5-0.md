---
title: Notes de mise à jour de la version 2021.5.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2021.5.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 3f9d7339-7e37-4702-821e-f2b03cd7e224
feature: Release Information
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1355'
ht-degree: 92%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2021.5.0 est le 27 mai 2021.
La version suivante (2021.6.0) sera publiée le 28 juin 2021.

## AEM as a Cloud Service Foundation {#foundation}

### Nouveautés d’AEM as a Cloud Service Foundation {#what-is-new-foundation}

* [Canal de version préliminaire](/help/release-notes/prerelease.md) : prévisualisez les fonctionnalités à venir pendant un mois complet avant qu’elles ne soient mises en production.

* [Obsolescence des API](/help/release-notes/deprecated-removed-features.md) : une liste des dernières API obsolètes pour AEM as a Cloud Service est disponible.

* [Module externe Maven Build Analyzer SDK AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=fr) : mettez à jour vos projets Maven vers la dernière version, qui inclut une vérification d’API Java obsolète et d’autres améliorations.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouveautés d’[!DNL Sites]  {#what-is-new-sites}

* Vous pourrez bientôt vérifier le contenu sur un nouveau [niveau Aperçu](/help/sites-cloud/authoring/sites-console/previewing-content.md) pour simuler l’aspect final de l’expérience comme vous le feriez sur le niveau Publication. Cette fonctionnalité est activée par l’assistant de publication gérée d’AEM Sites qui vous permet désormais de choisir une destination de publication entre Publication ou Aperçu. Les expériences sur la prévisualisation sont ensuite accessibles via une URL dédiée. Après la validation sur Aperçu, le contenu peut être publié d’Auteur vers Publication, comme d’habitude. L’activation du service d’aperçu dans des environnements AEM as a Clou Service sera progressivement déployée au cours des prochaines semaines.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouveautés d’[!DNL Assets]  {#what-is-new-assets}

* Vous pouvez télécharger les ressources partagées à l’aide de la fonctionnalité Partage de liens. Ce téléchargement utilise désormais un service asynchrone qui offre des téléchargements plus rapides et ininterrompus, même pour les téléchargements très volumineux. Voir la section [Téléchargement de ressources](/help/assets/download-assets-from-aem.md#link-share-download).

  ![Boîte de réception de téléchargement](/help/assets/assets/download-inbox.png)

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire {#what-is-new-assets-prerelease}

* Les schémas de métadonnées peuvent être appliqués directement aux propriétés du dossier.

  ![Ajout d’un schéma de métadonnées à partir des propriétés du dossier](/help/assets/assets/metadata-schema-folder-properties.png)

* L’outil d’ingestion en masse de ressources vous permet d’ajouter des métadonnées lors d’une ingestion en masse.

* Une amélioration de l’expérience utilisateur affiche le nombre de ressources présentes dans un dossier. Pour plus de 1 000 ressources dans un dossier, [!DNL Assets] affiche 1000+.

  ![Nombre de ressources dans un dossier affichées dans l’interface](/help/assets/assets/browse-folder-number-of-assets.png)

### Correctifs d’[!DNL Assets]  {#assets-bugs-fixed}

* Le téléchargement de fichiers très volumineux bloque le [!DNL Experience Manager desktop app]. (CQ-4320942)
* Les options de la barre d’outils sont différentes lorsque la même collection est sélectionnée à partir d’un dossier et lorsqu’elle est sélectionnée à partir d’un résultat de recherche. (CQ-4321406)

#### Nouveautés Dynamic Media {#what-is-new-dm}

* L’imagerie dynamique DPR (Device Pixel Ratio) et l’optimisation de la bande passante du réseau vous permettent de diffuser des images de meilleure qualité de manière efficace, sur des appareils dotés d’écrans haute résolution et une bande passante réseau limitée. Pour plus d’informations, consultez [FAQ sur l’imagerie dynamique](/help/assets/dynamic-media/imaging-faq.md) et [Optimisation des images avec les formats d’image de nouvelle génération WebP et AVIF](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4).
* Prise en charge du format d’image AVIF nouvelle génération dans la diffusion Dynamic Media (modificateur d’URL fmt).

## [!DNL Adobe Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* **Aide contextuelle** : ajout d’une aide contextuelle pour l’éditeur de formulaires adaptatifs, l’éditeur de modèles et l’éditeur de thèmes afin d’aider les auteurs à mieux comprendre les différentes fonctionnalités des éditeurs.
* **Messages d’erreur dans le navigateur Propriétés** : ajout de messages d’erreur pour chaque propriété dans le navigateur Propriétés des formulaires adaptatifs. Ces messages aident à comprendre les valeurs autorisées pour un champ.

### Fonctionnalité bêta à venir de [!DNL Forms] {#what-is-new-forms-prerelease}

Output as a Cloud service : le service Output vous permet de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode par lots synchrones et asynchrones. Le service de sortie permet de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

* Générer des documents de formulaire définitifs en complétant des fichiers de modèle avec des données XML.
* Générez des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs.
* Générer des fichiers PDF d’impression à partir de fichiers PDF de formulaire XFA.

Vous pouvez écrire à l’adresse formscsbeta@adobe.com pour vous inscrire au programme bêta.

### Correctifs de [!DNL Forms] {#forms-bugs-fixed}

* Dans une étape Affecter une tâche des workflows AEM Forms, lorsque vous remplacez l’icône par défaut des boutons d’action par une icône corail, le workflow cesse de fonctionner et consigne une exception. Le workflow fonctionne comme prévu lorsque des icônes par défaut sont utilisées.
* Dans le calque de mise en page, lorsque vous modifiez le nombre de colonnes, ouvrez le calque d’édition et faites glisser certains composants dans un panneau, les zones bleues carrées apparaissent dans la zone de contenu de l’éditeur de formulaires adaptatifs et l’éditeur ne répond plus.
* Le message d’erreur d’une option d’éditeur de règles liée à la fourniture de l’URL d’une ressource adaptative ou externe est trop long et n’est pas convivial.


## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.5.0.

### Date de publication {#release-date-cm-may}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.5.0 est le 6 mai 2021.
La prochaine version est prévue pour le 3 juin 2021.

### Nouveautés {#what-is-new-may}

* La règle de qualité PackageOverlaps détecte désormais les cas où le même package a été déployé plusieurs fois, c’est-à-dire dans plusieurs emplacements incorporés, dans le même ensemble de packages déployé.

* Le point d’entrée du référentiel dans l’API publique inclut désormais l’URL de Git.

* Les journaux de déploiement téléchargés par un utilisateur de Cloud Manager sont plus informatifs et incluent des détails sur les scénarios d’échecs et de succès.

* Les échecs intermittents rencontrés lors de la publication du code vers le git d’Adobe ont maintenant été résolus.

* Le module complémentaire Commerce peut désormais être appliqué aux programmes Sandbox au cours du processus Modifier le programme.

* L’expérience de modification du programme a été actualisée.

* Le tableau Noms de domaine de la page Détails de l’environnement affiche jusqu’à 250 noms de domaine par pagination.

* L’onglet Solutions des processus Ajouter un programme et Modifier le programme affiche la solution, même si une seule solution est disponible pour le programme.

* Le message d’erreur dans le journal de l’étape de génération lorsque la version ne produisait aucun package de contenu déployé n’était pas clair.

### Correctifs {#bug-fixes-cm-may}

* Il peut arriver que l’utilisateur voit un état « actif » vert en regard d’une liste d’adresses IP autorisées même si cette configuration n’a pas été déployée.

* Au lieu de supprimer des variables marquées comme « deleted », l’API des variables de pipelines se contentait de les marquer avec le statut **DELETED**.

* Certains problèmes de qualité de type Code Smell (conception inappropriée du logiciel) affectaient incorrectement l’évaluation de fiabilité.

* Comme les domaines génériques ne sont pas pris en charge, l’interface utilisateur ne permet pas à l’utilisateur d’envoyer un domaine de caractères génériques.

* Lorsqu’une exécution de pipeline était lancée entre minuit et 1 h du matin (UTC), il n’était pas garanti que la version d’artefact générée par Cloud Manager était supérieure à une version créée le jour précédent.

* Lors de la configuration du programme Sandbox, une fois que le projet doté d’un exemple de code a été créé, Gérer Git s’affiche sous la forme d’un lien à partir de la carte principale de la page Aperçu.

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu version v1.4.6 est le 27 mai 2021.

### Nouveautés {#what-is-new-ctt-latest}

* Une nouvelle instruction de journalisation a été ajoutée au journal des erreurs du démarrage rapide si l’utilisateur ne dispose pas de l’autorisation d’exécution sur le fichier exécutable Java.

* Lorsqu’un utilisateur supprime un jeu de migration de l’interface utilisateur de CTT, où une extraction a été effectuée, le dossier `tmp` associé à ce jeu de migration est supprimé afin d’économiser de l’espace.

### Correctifs {#bug-fixes-ctt-latest}

* Lors de la suppression d’un jeu de migration, un message d’erreur peut parfois s’afficher dans l’interface utilisateur de CTT. Ce problème a été résolu.

* Lors de l’exécution du mappage des utilisateurs, si les utilisateurs avaient la même adresse électronique sur la cible et l’hôte, mais des noms d’utilisateur différents, l’ingestion entière échouait. Ce problème a été résolu. Dans un scénario de conflit de ce type, l’utilisateur/le groupe est ignoré et consigné comme conflit dans le fichier journal.

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.4.0 est le 11 mai 2021.

### Nouveautés {#what-is-new-ctt-may}

* Cette version de l’outil de transfert de contenu crée des rendus de texte pour les ressources qui ont bénéficié d’une migration vers Cloud Service. Les rendus de texte sont nécessaires pour prendre en charge la recherche de texte intégral sur les ressources ingérées.
* Le nombre maximal de jeux de migration de l’outil de transfert de contenu qu’un utilisateur peut créer a été augmenté de 4 à 10.

### Correctifs {#bug-fixes-ctt-may}

* Plusieurs correctifs de bogues liés à la fonction d’actualisation automatique dans l’interface utilisateur de l’outil de transfert de contenu ont été appliqués.
* L’outil de transfert de contenu avec `wipe=true` générait un index de compteur incorrect sur la cible. Ce problème a été résolu.

## Module complémentaire Commerce {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Prise en charge de la pagination pour le contenu associé dans les propriétés de la console de produit

### Correctifs {#bug-fixes-commerce}

* Miniatures des ressources non affichées dans l’onglet Ressource des propriétés du produit

* Le chemin de navigation réinitialise les données d’aperçu dans la console de produit
