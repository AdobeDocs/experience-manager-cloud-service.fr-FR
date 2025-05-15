---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 088d470333d8f5a26f1a938380028541a1e945a1
workflow-type: tm+mt
source-wordcount: '1750'
ht-degree: 12%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 20783 {#20783}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 20783, rendue publique le mercredi 13 mai 2025. La version de maintenance précédente était la version 20626.

L’activation des fonctionnalités de la version 2025.5.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-20783}

* FORMS-18455 : l’éditeur de formulaires adaptatifs des composants principaux d’AEM Forms a été amélioré pour afficher des indicateurs visuels (points) pour les objets de données déjà utilisés ou mappés dans le formulaire dans l’arborescence de la source de données. Cette fonctionnalité permet aux auteurs d’identifier facilement les éléments de données utilisés.
* FORMS-18450 : le produit est amélioré en migrant la logique de domaine reCaptcha V2 vers le `AdaptiveFormConfigurationServiceImpl`. Cette modification vise à centraliser la configuration et peut s’aligner sur l’ajout de la prise en charge de reCaptcha V2 invisible dans les composants principaux.
* FORMS-19630 : l’uber-jar de démarrage rapide d’AEM 6.5 est mis à jour pour inclure le dernier package de composants principaux de Forms adaptatif, ce qui garantit que l’environnement de démarrage rapide reflète les fonctionnalités les plus récentes d’Adaptive Forms et remplace le code hérité.
* FORMS-19125 : l’éditeur de formulaire adaptatif des composants principaux a été amélioré afin de prendre en charge le mappage automatique des fragments de formulaire adaptatif disponibles lorsqu’une section correspondante de l’arborescence de la source de données est déposée dans la zone de travail du formulaire. Cela apporte une fonctionnalité de productivité clé de l’éditeur de base aux composants principaux.
* FORMS-17887 : AEM Forms permet désormais de générer des documents au format AFP (Advanced Function Presentation) par le biais de son service de sortie. Cette amélioration répond aux besoins des clients pour les environnements d’impression à grande vitesse et à volume élevé utilisant généralement l’AFP.
* FORMS-15089 : AEM Forms offre désormais la possibilité de créer des versions pour un formulaire lors de sa publication, de sorte que tous ses fragments constitutifs soient intégrés (incorporés) dans cette version publiée spécifique. Cela permet d’obtenir une représentation exacte et autonome du formulaire tel qu’il s’affichait au moment de la publication, ce qui peut s’avérer essentiel à des fins d’archivage, juridiques ou de conformité.
* FORMS-17107 : AEM Forms offre désormais une analyse améliorée des fonctions personnalisées côté client. Cela inclut la prise en charge des fonctionnalités JavaScript modernes (ECMAScript ES10+), telles que le chaînage facultatif, et introduit la possibilité d’utiliser des imports statiques dans des scripts de fonction personnalisée. Cela permet aux développeurs de mieux organiser le code, d’utiliser les modules ESM et de supprimer les limitations précédentes rencontrées avec les fonctions personnalisées dans Adaptive Forms v2 et Edge Delivery Services, en particulier pour les utilisateurs qui avaient précédemment besoin de solutions de contournement pour ces fonctionnalités.
* SITES-27775 : recherche de référence optimisée lors de la publication.
* SITES-30885 : traitement JSON optimisé dans les requêtes persistantes.
* SITES-25433 : Edge Delivery avec éditeur universel : prend en charge le rendu de page complet lors de la comparaison d’anciennes versions.
* SITES-27792 : Edge Delivery avec éditeur universel : ajoutez un modèle spécifique pour les configurations de service Edge Delivery.
* SITES-19754 : Edge Delivery avec éditeur universel : message d’erreur incontournable lorsque la configuration est interrompue.
* SITES-30328 : Edge Delivery avec éditeur universel : aperçu à partir de la prise en charge de Sidekick.
* SITES-23499 : Edge Delivery avec éditeur universel : permet l’utilisation de plusieurs champs pour les options de bloc.
* SITES-29987 : permet de définir des `previewUrlPattern` lors de la création de modèles de fragment de contenu.
* SITES-29874 : ajout de la prise en charge des références LongTextField dans l’API Content Fragment.
* SITES-29601 : ajoute une validation pour les fragments de contenu référencés via les champs de texte long.
* SITES-24623 : rendre les ETags renvoyés par GET et l’API des fragments de RECHERCHE utilisables pour le correctif.
* SITES-28557 : autorise la `references` du paramètre d’URL dans le fragment de contenu PATCH.
* SITES-5358 : [OpenAPI] copier des fragments de contenu avec des enfants.
* SITES-29614 : point d’entrée du workflow GET.
* SITES-29615 : point d’entrée de l’API de requêtes par lots de listes.
* SITES-25130 : mettre à niveau les composants principaux vers la version 2.28.0
* SITES-10575 : « MSM Blueprint Bloomfilter Loader » tente de charger > 100 000 lignes.
* SITES-26711 : les liens des champs de texte de l’éditeur de texte enrichi ne sont pas mis à jour pour pointer vers la Live Copy lors du déploiement de MSM.
* SITES-25976 : les liens au sein des fragments d’expérience ne s’adaptent pas après le déploiement de MSM.

### Problèmes résolus {#fixed-issues-20783}

* ASSETS-50994 : trafic entrant bloqué à AemRequestEventFilter.
* CQ-4358591 : projets manquants pour quelques langues lorsque des copies de langue sont créées à partir du panneau de référence des sites avec l’option « Créer des projets de traduction ».
* CQ-4359108 : Échec du format XLIFF 2.0 lors de l’utilisation de l’importation/exportation de traduction humaine.
* CQ-4358722 : la localisation ne fonctionne pas pour les codes ISO hérités en raison de différents codes de paramètres régionaux dans Java 11 et Java 17.
* FORMS-19808 : lors de l’enregistrement d’un formulaire volumineux contenant des fragments activés avec le chargement différé, l’utilisateur ne peut pas extraire les brouillons.
* FORMS-19887 : un champ déroulant d’un formulaire XFA, initialement défini sur accès en lecture seule, ne passe pas à un statut ouvert/modifiable lorsque le formulaire est rendu dans HTML5. Le champ reste en lecture seule et empêche toute interaction de l’utilisateur, contrairement au rendu PDF où il fonctionne comme prévu.
* FORMS-19651 : dans l’éditeur de règles, une règle ne fonctionne pas correctement lorsqu’un clic sur un bouton est utilisé dans une condition binaire et que le même bouton est également utilisé dans l’instruction « then » de cette règle.
* FORMS-19628 : dans le document d’enregistrement (DoR) généré automatiquement pour le Forms adaptatif basé sur les composants principaux, l’exclusion du titre d’un panneau imbriqué du document d’enregistrement masque également incorrectement le titre du panneau racine si l’option Autoriser le texte enrichi pour le titre est activée pour le panneau racine.
* FORMS-18977 : les fichiers PDF générés par le service de document d’enregistrement (DE) ne contiennent pas le titre du document. Cela peut entraîner une non-conformité aux normes d’accessibilité PDF/UA et WCAG 2.1, car le titre du document est un attribut obligatoire pour les PDF accessibles.
* FORMS-18526 : lorsqu’une règle contenant plusieurs champs dans ses conditions est copiée d’un champ à un autre, une référence de champ fixe dans ces conditions conserve incorrectement sa référence au champ source d’origine au lieu de la mettre à jour vers le nouveau champ dans lequel la règle est copiée.
* FORMS-19047 : après la modification et la republication d’un formulaire adaptatif sur AEM Forms (en particulier 6.5.22.0), les traductions de certains éléments de formulaire, en particulier les zones de texte, peuvent être manquantes.
* FORMS-19234 : la fonctionnalité de chronologie pour les PDF dans AEM Forms, qui permet aux utilisateurs d’afficher les détails sur la création et le contrôle de version d’un PDF, cesse de fonctionner une fois qu’un PDF est chargé dans la section « Forms et documents ».
* FORMS-19373 : les erreurs de réplication sont signalées de manière incorrecte lors d’un processus de publication Golden dans les environnements où aucun agent de réplication n’est configuré.
* FORMS-18196 : l’API HTTP de synchronisation `generatePrintedOutput` (ou `generatePdfOutput`) renvoie incorrectement un code de réponse 200 (Succès) au lieu du code d’erreur 400 (Requête incorrecte) attendu lorsque les données de champ facultatives requises par le modèle XDP restent vides dans la requête.
* FORMS-19336 : dans l’éditeur de formulaires adaptatifs des composants principaux (éditeur AF2), la fonctionnalité de recherche dans l’arborescence de Source de données ne fonctionne pas correctement ou comme prévu, ce qui empêche les utilisateurs de rechercher facilement des éléments de données spécifiques.
* FORMS-19629 : l’analyseur de schéma JSON génère des résultats non valides ou interprète mal certains schémas JSON fournis par le client. Ce problème peut avoir une incidence négative sur les fonctionnalités qui reposent sur une analyse correcte des schémas, telles que le mappage automatique des fragments.
* FORMS-19380 : l’introduction de la prise en charge des versions pour le Forms adaptatif des composants principaux a involontairement activé les fonctionnalités de version pour divers autres types de ressources (par exemple, Forms Foundation, fichiers PDF, Thèmes, FDM) sans conception ni test spécifiques pour ces types de ressources. Cet effet indésirable non intentionnel est en cours d’étude.
* FORMS-17707 : le connecteur AEP (Adobe Experience Platform) ne fonctionne pas correctement lorsqu’il est configuré pour se connecter aux environnements d’évaluation de la plateforme AEP.
FORMS-18526 : lors de la copie d’une règle qui comporte des conditions basées sur plusieurs champs, un champ référencé dans les conditions ou actions de la règle (qui n’est pas le champ principal déclenchant la règle) n’est pas mis à jour pour référencer correctement le nouveau champ vers lequel la règle est copiée. Au lieu de cela, il continue à référencer le champ source d’origine à partir duquel la règle a été copiée.
FORMS-18474 : règle conçue pour définir le focus sur un panneau ou un composant spécifique lorsque la valeur d’un champ particulier change (par exemple, le champ « A ») et qu’elle est déclenchée de manière incorrecte par une modification apportée à un champ du formulaire. Par exemple, si le champ « B » est modifié, le focus est toujours placé sur le panneau désigné, même si la règle a été configurée uniquement pour les modifications apportées au champ « A ».
* GRANITE-58276 : les cycles de dépendance OSGi empêchent le fonctionnement correct de la fabrique de moteurs de script HTL.
* OAK-11673 : augmentation du CPU Oak-segment-azure v12 causée par refreshLease.
* SITES-30752 : n’utilisez pas d’en-têtes `If-modified-since`/`last-modified` lors de la génération d’une réponse de requête persistante.
* SITES-30353 : GraphQL DataFetchingExceptions pour le champ « src » dans les fragments de contenu AEM.
* SITES-30333 : lisez les métadonnées des ressources à partir du jcr pour éviter les problèmes d’analyse xmp.
* SITES-30140 : problème de double fenêtre lors de la création d’une référence de fragment de contenu.
* SITES-29748 : conditions de rendu correctes pour afficher les actions de gestion de publication/publication rapide dans l’éditeur CF.
* SITES-15452 : les éléments CF uniques ne doivent pas être comparés à leurs copies dans le lancement.
* SITES-30386 : Edge Delivery avec éditeur universel : lorsque le fichier cors.js d’UE est dupliqué, l’UE duplique les sections lors de l’ajout de contenu.
* SITES-29745 : correction d’un rare problème en raison duquel les variantes des références n’étaient pas hydratées.
* SITES-30585 : impossible de définir « previewUrlPattern » lors de la création de modèles avec des références.
* SITES-30327 : la publication de fragments de contenu sans autorisations crée des workflows distincts pour chaque ressource de payload.
* SITES-29528 : ETag ne peut pas être utilisé pour la mise en cache sur l’instance de publication.
* SITES-30583 : outil Rechercher et remplacer qui convertit tous les caractères en minuscules.
* SITES-31157 : échec du correctif en raison d’une ETag incohérente.
* SITES-31327 : [OpenAPI] la requête Get de fragment de contenu sur l’instance d’auteur peut répondre par la mention 304.
* SITES-29691 : NullPointerException lors de la tentative de déplacement de la page.
* SITES-30728 : OnTime/OffTime ne publie pas comme prévu les éléments lorsqu’ils sont configurés sur les propriétés des ressources.
* SITES-29789 : modification du lien du composant sur les pages racine copiées dans AEM.
* SITES-29191 : impossible d’ajouter plus de 20 SKU au composant Liste de produits.
* SITES-30372 : le recadrage intelligent ne fonctionne pas sur le composant principal Image AEM (V2).
* SITES-28693 : le composant Teaser effectue le rendu d’HTML endommagé lorsque le titre est vide.
* SITES-28668 : impossible de promouvoir le lancement avec LaunchPromotionParameters.
* SITES-31005 : amélioration de l’interface utilisateur de la tâche de déploiement pour afficher la progression au client.
* SITES-31020 : améliorez l’interface utilisateur de création d’une tâche de Live Copy pour afficher la progression au client.
* SITES-29816 : erreur « Ressource introuvable » lors de la création d’une Live Copy de fragment d’expérience.
* SITES-29363 : le bouton Réinitialiser la Live Copy ne fonctionne pas pour la hiérarchie de contenu de la Live Copy imbriquée.
* SKYOPS-106509 : ajout d’indicateurs d’ouverture de module complémentaire pour prendre en charge l’accès réfléchissant GSON sur Java 21.

### Problèmes connus {#known-issues-20783}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-20783}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-20783}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 19 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-20783}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.78.1-T20250429061757 | [API Oak 1.78.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
