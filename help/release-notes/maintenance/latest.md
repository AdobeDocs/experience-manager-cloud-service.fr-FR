---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9303ecadea38d83bd71ed0d440067bae5c419940
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 20%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 16971 {#release-16971}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 16971, publiée le jeudi 3 juillet 2024. La version de maintenance précédente était la version 16799.

L’activation des fonctionnalités de la version 2024.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-16971}

* SITES-22948 : supprimez les références commerciales dans le contenu de base d’AEM CS.
* SITES-22141 : [Fragments de contenu] SegmentNotFoundException de CFM ModelChangeRepositoryImpl après OnRC.
* SITES-21893 : problème de recadrage d’image sur l’instance d’auteur.
* SITES-21788 : [Fragments de contenu] Afficher le REMARQUE dans l’éditeur de modèles CF et CF lorsque uiSchema est activé pour le modèle.
* SITES-21688 : le déploiement MSM ne met pas à jour le chemin d’accès au fragment d’expérience (XF) sur les pages Live Copy.
* SITES-21659 : renvoie le nom complet de l’utilisateur créant/modifiant/répliquant une ressource de modèle.
* SITES-21609 : point d’entrée OpenAPI pour migrer les fragments de contenu d’un modèle à un autre.
* SITES-21598 : [Ouvrir l’API] Create CFM - return error si le chemin de configuration donné n’existe pas.
* SITES-21491 : [Ouvrir l’API] Le point de terminaison PATCH des Forces canadiennes doit respecter les relations en direct au niveau du terrain.
* SITES-21434 : [Ouvrir l’API] Le point de GET des Forces canadiennes doit respecter les relations en direct au niveau du terrain.
* SITES-21415 : Éditeur CF - Prise en charge des références UUID.
* SITES-21326 : [Ouvrir l’API] Fournissez des informations sur la présence de références pour un fragment de contenu.
* SITES-21310 : [Ouvrir l’API] Ajoutez l’identifiant du fragment de contenu dans la réponse de l’API de traduction.
* SITES-20859 : API d’ouverture du FC - Renvoi de références lors de la récupération d’un fragment par chemin d’accès.
* SITES-20687 : [Ouvrir l’API] Point de terminaison pour la récupération de l’état du traitement par lot.
* SITES-20657 : [Ouvrir l’API] Permet d’indiquer une option pour le mot entier match lors du remplacement d’une chaîne à l’aide de `FindAndReplace` point de terminaison .
* SITES-20587 : [Ouvrir l’API] Créer `COPY` point de terminaison pour les fragments de contenu.
* SITES-20584 : [Ouvrir l’API] Optimiser la récupération des références.
* SITES-20308 : [Ouvrir l’API] Activez le traitement par lot sur l’API .
* SITES-19976 : [Ouvrir l’API] Schéma d’interface utilisateur générique pour les champs conditionnels.
* SITES-19556 : [Fragments de contenu] Mettez à jour uiSchema s’il existe lorsque le modèle est modifié.
* SITES-18056 : [Ouvrir l’API] Lorsque vous publiez un fragment de contenu à prévisualiser, incluez des références.
* SITES-16898 : [Schéma] Point d’entrée OpenAPI pour migrer les fragments de contenu d’un modèle à un autre.
* SITES-16609 : Point de terminaison List Launches.
* SITES-16606 : Créez un point de terminaison Launch.
* SITES-21617 : [Xwalk] Rendre les propriétés/métadonnées de page modifiables dans l’UE.
* SITES-19614 : [Xwalk] Pagination de l’éditeur de feuilles de calcul et défilement infini.
* SITES-22163 : [Xwalk] Amélioration de la prise en charge du contenu diffusé à partir du niveau de publication pour Edge Delivery Sites.
* SITES-22109 : [Xwalk] Amélioration de la gestion du post-traitement des balises richtext.
* SITES-22035 : [Xwalk] Amélioration de la gestion de MSM et des lancements.
* SITES-21839 : [Xwalk] Amélioration du mappage et de l’assainissement des chemins pour le contenu non fourni par Edge Delivery.

### Problèmes résolus {#fixed-issues-16971}

* CQ-4356898 : [Traduction] Erreur outOfMemory pour CF contenant un nombre inhabituellement élevé de liens.
* CQ-4357055 : [Traduction] La traduction automatique ne fonctionne pas à l’aide de l’API REST.
* CQ-4353931 : [Traduction] Ajoutez jcr:uuid dans la page source de traduction/xf/asset lorsqu’il manque.
* CQ-4357591 : [Traduction] Modifiez le workflow &quot;Associer JCR:UUID&quot; pour qu’il fonctionne pour Pages/XF.
* FORMS-14844 : Forms adaptatif autorise l’envoi de formulaire malgré l’échec de la vérification reCAPTCHA.
* FORMS-14984 : Forms avec CAPTCHA ignore la validation si &quot;submitMetaData&quot; est absent des données envoyées.
* FORMS-14477 : Les options &quot;Après&quot; et &quot;Avant&quot; de l’éditeur de règles ne fonctionnent pas dans la validation du sélecteur de date.
* FORMS-14019 : la fonctionnalité &quot;Invoke Service&quot; de l’éditeur de règles ne fonctionne pas dans Universal Editor.
* FORMS-14336 : lorsqu’aucun champ de formulaire n’est sélectionné, l’éditeur doit s’ouvrir en mettant l’accent sur l’ensemble de l’élément de formulaire.
* FORMS-15061 : le cercle de chargeur persiste indéfiniment lors de l’utilisation de l’option d’appel du service dans l’éditeur de règles.
* SITES-22457 : La promotion d’un lancement qui n’est pas profond ne met pas à jour le contenu source.
* SITES-22748 : [Fragments de contenu] Amélioration de la gestion des erreurs pour la tâche de mise à jour de fragment de contenu
* SITES-22349 : [Fragments de contenu] ContentType pour les éléments cf multilignes vides ne peut pas être modifié.
* SITES-22343 : [Fragments de contenu] Le type sémantique &quot;énumération&quot; est rompu.
* SITES-22194 : après avoir défini la redirection, model.json ne fonctionne plus.
* SITES-21953 : [Ouvrir l’API] La balise Etag est modifiée en fonction de l’ordre de validationStatus.
* SITES-21894 : [Ouvrir l’API] Améliorez la validation du chemin parent lors de la création de CF.
* SITES-21887 : [Ouvrir l’API] ETag non valide renvoyé par le point de terminaison des variations du POST.
* SITES-21657 : [Ouvrir l’API] Améliorez la validation sur la propriété Chemin de recherche CF.
* SITES-21949 : le curseur non valide des API de recherche renvoie 500.
* SITES-20927 : les API de recherche renvoient un 500 lorsque la requête est manquante.
* SITES-20544 : [Ouvrir l’API] Modifiez la génération des noms de modules de publication afin d’éviter les conflits Oak.
* SITES-19710 : CVE-2022-47937 - Supprimez toutes les utilisations de org.apache.sling.commons.json dans l’éditeur de page.
* SITES-11992 : [Accessibilité] Un nom accessible est manquant dans le bouton du sélecteur d’échantillon d’annotation.
* SITES-10979 : [Accessibilité] Le libellé n’est pas persistant.
* SITES-10962 : [Accessibilité] Bouton : le bouton n’a pas de rôle.
* SITES-10905 : [Accessibilité] L’état du composant actif ne présente pas de rapport de contraste de 3 à 1.
* SITES-2974 :  [Accessibilité] - Défilement horizontal à 320 px de largeur.
* SITES-22026 : impossible de déplacer les fragments d’expérience entre les dossiers dans AEM
* SITES-22106 : Problème de fonctionnalité de changement de langue dans le nouvel éditeur de fragments de contenu
* SITES-21980 : gestion incohérente des types de référence UUID.
* SITES-7257 : NPE dans ThumbnailServlet.

### Problèmes connus {#known-issues-16971}

Aucun.

### Avis de modification {#change-notice-16971}

* À compter de septembre 2024, AEM as a Cloud Service désactivera la sérialisation des résolveurs de ressources via le framework de l’exportateur de modèle Sling. Voir la [documentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) pour plus d’informations.

### Fonctionnalités et API obsolètes {#deprecated-16971}

Pour savoir ce qui est obsolète ou supprimé dans AEM as a Cloud Service, voir [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Technologies intégrées {#embedded-tech-16971}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.64.0 | [API Oak 1.64.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| API SLING AEM | 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.25.4 | [Composants principaux de la gestion de contenu Web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
