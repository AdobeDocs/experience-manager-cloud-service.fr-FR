---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c58e4645ddc9390728d6ac5cf92588caaeffae01
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 20%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 23320 {#23320}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 23320, publiée le jeudi 12 novembre 2025. La version de maintenance précédente était la version 22943.

L’activation des fonctionnalités de la version 2025.11.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Consultez [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

>[!NOTE]
>
>La version 23122 a été rendue privée le 3 novembre.

### Améliorations {#enhancements-23320}

* CQ-4361363 : dernières traductions AEM et Granite.
* FORMS-21594 : permet d’activer le verrouillage du contenu et de la disposition du modèle de communications interactives pour les auteurs de contenu.
* FORMS-20385 : prise en charge de l’édition XDP dans l’éditeur de communications interactives.
* FORMS-10883 : prise en charge de JSON avec les balises d’espace de noms XHTML dans la génération du document d’enregistrement pour assurer le rendu précis des données de texte enrichi envoyées via les API.
* FORMS-21751 : fonctions de zone de travail - débordement de texte, interface utilisateur pour le saut de page.
* FORMS-22049 : éditeur de communications interactives - Migration vers le spectre 2.
* FORMS-22050 : prise en charge de la numérotation dynamique des pages dans l’éditeur de communications interactives.
* FORMS-21606 : SPI de rendu OSGi publiques pour les communications interactives.
* FORMS-21613 : rapport de transaction et journalisation des performances pour le rendu des SPI de communications interactives.
* GRANITE-62394 : mise à jour de joda-time vers 2.12.7.
* GRANITE-36205 : mise à jour d’Oak vers la version 1.88.0.
* GRANITE-62020 : amélioration de la politique de reprise sur `RepositoryServiceHttpClient`.
* GRANITE-62169 : mettez à jour commons-lang vers la version 3.19.0.
* SITES-35092 : fragments de contenu - Nouvelle procédure de mixin et de mise à niveau pour la recherche sémantique.
* SITES-32319 : OpenAPI de diffusion - Références de page de support.
* SITES-20123 : GraphQL : prend en charge les éléments d’exposant dans la réponse JSON.
* SITES-34744 : nouvelle propriété « card » dans la réponse de fragment de contenu, qui contient des données qui peuvent être utilisées pour le rendu d’une miniature.
* SITES-34571 : permet aux champs d’énumération d’être vides.
* SITES-34812 : possibilité supplémentaire de récupérer un fragment de contenu sans ses références, à l’aide du paramètre « references » avec la valeur « none ».
* SITES-35176 : l’extraction d’un fragment de contenu via l’interface utilisateur tactile empêche désormais la modification du fragment de contenu dans le nouvel éditeur par d’autres utilisateurs.
* SITES-30371 : ajout de la prise en charge des champs de référence basés sur l’uuid.
* SITES-19309 : récupérez un maximum de 150 références lors de l’ouverture de l’assistant de déplacement de page.
* SITES-32515 : Edge Delivery avec éditeur universel - Ajoutez la prise en charge de plusieurs champs et de plusieurs champs composites (accès anticipé).
* SITES-33784 : Edge Delivery avec éditeur universel - Ajoutez la prise en charge de ld-json dans les métadonnées de page.
* SITES-34832 : Edge Delivery avec éditeur universel - Ajoutez le chemin d’accès public d’une page à la réponse du servlet d’informations sur la page.
* SITES-25893 : Edge Delivery avec éditeur universel - Ajoutez la prise en charge de forts et de mettent l’accent sur le rendu de texte par blocs.
* SITES-26158 : Edge Delivery avec éditeur universel - Ajouter la prise en charge du balisage de tableau en blocs et en colonnes (accès anticipé).
* SITES-27949 : Edge Delivery avec éditeur universel - Rendez le mappage de chemin facultatif.
* SITES-35811 : utilisez le nouvel index dans les requêtes de fragments de contenu.
* SKYOPS-120857 : mise à jour de filevault vers la version 4.1.4.
* SKYOPS-118390 : mise à jour de la ressource JCR vers la version 3.3.6.
* SKYOPS-121082 : mise à jour des versions des lots Sling `org.apache.sling.discovery.standalone`, `org.apache.sling.jcr.packageinit` et `org.apache.sling.commons.fsclassloader`.

### Problèmes résolus {#fixed-issues-23320}

* ASSETS-58926 : correction de la fonctionnalité de miniature de modification vidéo dans DM.
* ASSETS-58623 : correction d’un npe dans omnisearch lorsque la configuration existe.
* CQ-4361144 : correction d’un problème en raison duquel les fragments de contenu étaient ignorés des tâches de traduction.
* CQ-4355446 : correction d’une chaîne non localisée dans le projet de traduction qui se produisait dans la boîte de dialogue Annuler la tâche de traduction .
* CQ-4360747 : correction d’un problème en raison duquel les tâches de traduction répétables créent des payloads vides et se déclenchent trop souvent.
* GRANITE-61318 : correction d’un problème en raison duquel l’assistant de création de page ne met en surbrillance que les champs obligatoires dans l’onglet de base.
* GRANITE-60514 : correction d’un problème en raison duquel les publications planifiées étaient arrêtées lors de l’exécution du pipeline full stack.
* GRANITE-61019 : correction d’un problème lié au GC lors de la première exécution après le redémarrage d’AEM.
* GRANITE-60456 : correction d’un problème lorsque l’administrateur ouvre la page de propriétés d’un utilisateur.
* SITES-34555 : GraphQL - QueryValidationError après les déploiements.
* SITES-35077 : fragments de contenu - La dépublication échoue pour les fragments entre parenthèses en raison d’un codage d’URL incorrect.
* SITES-35374 : fragments de contenu - Le fragment de contenu modifié disparaît après avoir renavigué.
* SITES-36130 : NPE en `EditorRestrictionsStatusImpl`.
* SITES-35810 : NullPointerException dans Launches bloque la file d’attente publishEdgeDeliverySubscriber.
* SITES-34368 : AEM CIF génère 12 alias GraphQL - dépasse la limite de 10 dans la version 2.4.6-P12 de Magento.
* SITES-36193 : correctifs du connecteur CCS.
* SITES-35169 : résolution d’un problème qui entraînait une pagination incorrecte lorsque des ressources de fragment non valides étaient renvoyées par la recherche.
* SITES-34574 : correction d’un problème en raison duquel le curseur n’était pas renvoyé par l’API de recherche de fragments de contenu dans certains cas.
* SITES-35520 : correction d’un problème qui provoquait une ClassCastException ou des délais d’expiration lors de la tentative de publication de contenu.
* SITES-35210 : correction d’une exception NullPointerException qui se produisait lors de la tentative de publication d’un fragment rompu avec un filtre de références vide.
* SITES-35933 : correction d’un bug en raison duquel des workflows « Demande d’activation » vides étaient déclenchés après la publication du fragment de contenu.
* SITES-35925 : correction d’un bug lié à l’application de correctifs aux modèles de fragment de contenu qui supprimait les propriétés « traduisible » et « showThumbnail » du modèle.
* SITES-35409 : correction d’un bug qui empêchait la republication des fragments ajustés lors du déplacement d’une page.
* SITES-15757 : correction d’un bug qui empêchait la republication des pages modifiées lors du déplacement d’une page.
* SITES-34638 : correction d’un bug en raison duquel les propriétés des pages grands-parents n’étaient pas incluses lors de la création de nouvelles versions.
* SITES-35071 : l’exportation CSV renvoie des résultats non filtrés lorsque l’omni-recherche utilise une expression entre guillemets.
* SITES-32182 : Edge Delivery avec éditeur universel - correction des problèmes de codage avec les URL contenant des paramètres de requête déjà codés.
* SITES-34324 : Edge Delivery avec éditeur universel - correction du rendu des liens avec un tel : protocole.
* SITES-35333 : Edge Delivery avec éditeur universel - correction de la sélection du rendu de ressource pour les images dans les métadonnées de page.
* SITES-35549 : Edge Delivery avec éditeur universel - correction des entités html codées en double dans les métadonnées de page.

#### AEM Guides {#guides-23320}

* GUIDES-33597 : Si un élément de `prop` vide sans attribut ni valeur est ajouté à un fichier DITAVAL, les éléments de `prop` supplémentaires ne peuvent pas être ajoutés.
* GUIDES-33693 : lorsque vous chargez à nouveau une image modifiée via l’interface utilisateur de Experience Manager Guides, le rendu original de l’image est mis à jour, mais le contenu DITA associé continue d’afficher la version précédente de l’image.
* GUIDES-35607 : Les journaux d’erreurs générés lors du chargement d’une ressource via l’interface utilisateur d’Assets ou de la création d’un nouveau fichier à partir de l’interface utilisateur de l’éditeur utilisent incorrectement le terme `predecessor` au lieu de `successor` dans le message du journal.
* GUIDES-37649 : lors de la publication d&#39;un plan DITA à l&#39;aide de la ligne de base sur AEM Sites (avec le mappage de composant hérité), les éléments de plan avec l&#39;attribut `processing-role = resource-only` sont également publiés.

Pour plus d’informations sur les fonctionnalités nouvelles et améliorées, ainsi que sur les problèmes résolus dans la version, consultez la [Feuille de route de publication d’Experience Manager Guides](https://experienceleague.adobe.com/fr/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).


### Problèmes connus {#known-issues-23320}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-23320}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-23320}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 31 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-23320}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1,88,0 | [API Oak 1.88.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.88/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Serveur HTTP Apache | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| Composants principaux d’AEM | 2.30.2 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (par défaut) | [Versions de Node.js prises en charge](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
