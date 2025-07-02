---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 080a79cdc0e48a54570ea53618b1f0be164d5156
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 83%

---


# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 21331 {#21331}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 21331, publiée le 24 juin 2025. La version de maintenance précédente était la version 21193.

L’activation des fonctionnalités de la version 2025.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-21331}

* CQ-4356522 : optimisation de `WorkflowResourceStatusProvider`.
* FORMS-16458 : interface d’utilisation permettant de choisir les propriétés de la police.
* FORMS-17707 : le connecteur AEP ne fonctionne pas pour l’étape de la plateforme AEP.
* FORMS-19125 : prise en charge du mappage automatique de fragments dans l’éditeur AF.
* FORMS-19336 : ajout de la recherche dans l’arborescence de source de données dans l’éditeur AF.
* FORMS-19417 : prise en charge des cases d’option dans la vue Hiérarchie.
* FORMS-19603 : prise en charge des gabarits de page et des pages de conception dans l’éditeur de règles.
* SITES-5358 : API REST de fragments de contenu : copie de CF avec enfants.
* SITES-10575 : « Chargeur Bloomfilter de plan directeur MSM » tente de charger plus de 100 000 lignes.
* SITES-14542 : le changement de nom/le déplacement d’une page source de Live Copy doit déclencher la publication de la page Live Copy renommée/déplacée, si elle a déjà été publiée.
* SITES-19754 : Edge Delivery avec l’éditeur universel : ajout d’un message d’erreur clair pour les utilisateurs et utilisatrices lorsque l’intégration rencontre des problèmes.
* SITES-23499 : Edge Delivery avec l’éditeur universel : ajout de la prise en charge de plusieurs champs à utiliser pour les options de bloc.
* SITES-23518 : Edge Delivery avec l’éditeur universel : ajout de la prise en charge des rendus de ressources spécifiques Edge Delivery.
* SITES-24436 : API REST de fragments de contenu : introduction du cache local pour accélérer la récupération des références en double.
* SITES-25155 : API REST de fragments de contenu : supprimez le paramètre de requête « enabledForFolder » obsolète dans la liste Modèles .
* SITES-25913 : API REST de fragments de contenu : validation temporelle des ressources avant le démarrage du workflow de publication.
* SITES-25976 : les liens au sein des fragments d’expérience ne s’adaptent pas après le déploiement de MSM.
* SITES-26271 : API REST de fragments de contenu : passage à une traversée BFS pour le point d’entrée de variation GET.
* SITES-27486 : éditeur universel - intégration AEM.
* SITES-27775 : optimisation de la recherche de référence pendant la publication (chargement différé des métadonnées).
* SITES-27782 : Edge Delivery avec l’éditeur universel : ajout d’une implémentation éditeur-abonné spécifique pour publier du contenu vers Edge Delivery (accès anticipé).
* SITES-27792 : Edge Delivery avec l’éditeur universel : ajout d’un modèle de configuration de service Edge Delivery dédié.
* SITES-28557 : API REST de fragments de contenu : autorisez l’utilisation des ETags récupérés en appelant `/cf/fragments/{fragmentId}` avec `references=direct` pour corriger un fragment de contenu.
* SITES-28683 : permet aux recherches MSM LiveRelationship d’ignorer le statut avancé.
* SITES-29601 : API REST de fragments de contenu : validation des références de fragment de contenu de champs de texte long.
* SITES-29614 : API REST de fragments de contenu : récupérez un workflow à l’aide du point d’entrée `/cf/workflows/{workflowInstanceId}`, où workflowInstanceIda est l’identifiant renvoyé par la demande de publication.
* SITES-29615 : API REST de fragments de contenu : répertoriez toutes les requêtes par lots créées via les `/cf/batch` POST à l’aide de `GET /cf/batch`.
* SITES-29874 : API REST de fragments de contenu : les références des champs de texte longs des fragments de contenu sont désormais récupérées et hydratées.
* SITES-29930 : API REST de fragments de contenu : ajout de métriques pour le workflow de publication de fragments de contenu.
* SITES-29986 : API REST de fragments de contenu : prise en charge de la dénomination technique du modèle CF.
* SITES-30088 : API REST de fragments de contenu : publication CF : récupération des références ignorée lorsque filterReferencesByStatus est vide.
* SITES-30126 : API REST de fragments de contenu : amélioration des performances de publication CF : a remplacé la vérification si une ressource est un fragment par une vérification minimale.
* SITES-30328 : Edge Delivery avec l’éditeur universel : ajout de la prise en charge pour la prévisualisation à partir du sidekick.
* SITES-30445 : API REST de fragments de contenu : schéma d’interface d’utilisation du modèle CF : ajout d’une option pour contrôler l’état initial des réductibles.
* SITES-30604 : API REST de fragments de contenu : prise en charge de l’adoption du schéma de métadonnées de modèle dans la nouvelle interface d’utilisation.
* SITES-30885 : optimisation du traitement JSON dans les requêtes persistantes.
* SITES-30886 : API REST de fragments de contenu : workflows GET pour le point d’entrée de fragment de contenu basé sur les UUID de fragment stockés dans les métadonnées de workflow.
* SITES-31005 : amélioration de l’interface d’utilisation des tâches de déploiement afin d’afficher la progression.
* SITES-31020 : amélioration de l’interface d’utilisation de création d’une tâche de Live Copy afin d’afficher la progression.
* SITES-31111 : API REST de fragments de contenu : autorisez l’API de correctif de variation à accepter les références de fragments de contenu dans les lancements de fragments de contenu.
* SITES-31343 : API REST de fragments de contenu : ajoutez le filtrage et la pagination par date au point d’entrée qui répertorie les requêtes par lots.
* SITES-31472 : la suppression du lancement peut entraîner une interruption du référentiel en cas de lancement massif.
* SITES-31641 : API REST de fragments de contenu : ajoutez une propriété aux champs de modèle pour stocker les mappages dynamiques liés aux extensions.
* SITES-31677 : l’espace de travail personnalisé prend en charge l’exportation de fragments de contenu AEM vers Target.
* SITES-31770 : API REST de fragments de contenu : améliorations des performances de PATCH.
* SITES-31782 : API REST de fragments de contenu : ajout d’une description pour les ressources locales.
* SITES-32175 : autorisation des validations intermédiaires pour la création de Live Copy et le déploiement de pages MSM.

### Problèmes résolus {#fixed-issues-21331}

* CQ-4359756 : les règles de traduction incluent désormais des propriétés de filtre au niveau du composant.
* CQ-4359826 : résout l’incohérence du statut dans le panneau de référence du fragment de contenu.
* CQ-4359866 : la classe LanguageUtils prend désormais en charge le test unitaire sans ajouter de dépendance supplémentaire.
* FORMS-13990 : API du service de formulaires : génération de document : lorsque le champ de données est vide après avoir été sélectionné, il donne 200 au lieu de la valeur attendue de 400.
* FORMS-14309 : API du service de formulaires : rectification du code de réponse d’extraction de données.
* FORMS-18526 : lors de la copie d’une règle avec plusieurs champs dans des conditions, le champ fixe ne change pas.
* FORMS-18977 : le service DOR ne transmet pas le titre du document.
* FORMS-19047 : traductions manquantes après la publication d’un formulaire adaptatif sur AEM Forms, pack de services 22.
* FORMS-19234 : impossible d’utiliser la fonction de chronologie des PDF dans les formulaires AEM.
* FORMS-19628 : dans le document d’enregistrement généré automatiquement, l’exclusion du titre du panneau imbriqué masque également le titre du panneau racine.
* FORMS-19651 : correction d’une règle lorsqu’un utilisateur ou une utilisatrice clique sur un bouton dans une condition binaire et que le même bouton est également utilisé dans l’instruction « then ».
* FORMS-19808 : portail des formulaires : les brouillons ne peuvent pas être extraits lorsque le chargement différé est activé.
* FORMS-19887 : la propriété d’accès ne fonctionne pas dans l’aperçu HTML5.
* SITES-15452 : les éléments CF uniques ne doivent pas être comparés à leurs copies dans le lancement.
* SITES-24492 : la liste d’onglets ARIA n’a pas de nom accessible.
* SITES-24623 : API REST de fragments de contenu : correction d’une incohérence d’ETag entre les points d’entrée du même CF.
* SITES-24668 : la fonctionnalité Rail Références échouet lorsque le zoom est augmenté à 400 %.
* SITES-24678 : le message de statut du rail Références n’est pas annoncé par le lecteur d’écran.
* SITES-24697 : le lecteur d’écran n’annonce pas le statut de chargement du modèle d’image.
* SITES-24708 : la fonctionnalité Rail Filtres échoue lorsque le zoom est porté à 400 %.
* SITES-25235 : le message de chargement du contenu du rail Filtres n’est pas annoncé par le lecteur d’écran.
* SITES-25254 : la barre de défilement horizontale s’affiche dans la fenêtre modale du carrousel lorsque le contenu est affiché à 320 px.
* SITES-25433 : Edge Delivery avec éditeur universel : correction du rendu des versions de page pour les structures de site multilingues.
* SITES-26064 : API REST de fragments de contenu : correction du code de statut renvoyé lors de la création d’un fragment et de l’obtention d’un `AccessDeniedException` sur le serveur principal.
* SITES-26890 : lors de l’utilisation du clavier, le focus au clavier Portée « En-têtes de tableau » n’est pas visible dans la page Gérer la publication.
* SITES-29075 : l’aperçu de la Live Copy ne fonctionne pas pour les sites web à volume élevé.
* SITES-29514 : Edge Delivery avec éditeur universel : rendez l’URL GitHub/de projet obligatoire lors de la création d’un site.
* SITES-29691 : impossible de déplacer la page dans un cas spécifique lié aux lancements.
* SITES-29745 : API REST de fragments de contenu : implémentation de l’hydratation des variations de références dans la traversée BFS.
* SITES-29748 : conditions de rendu correctes pour afficher les actions de gestion de publication/publication rapide dans l’éditeur CF.
* SITES-29789 : problème de modification du lien du composant sur les pages racine copiées.
* SITES-29987 : API REST de fragments de contenu : la fonctionnalité Créer et modifier un modèle de fragment de contenu ne prend pas en charge `previewUrlPattern`.
* SITES-30140 : problème de double fenêtre lors de la création d’une référence de fragment de contenu.
* SITES-30327 : API REST de fragments de contenu : la publication de fragments de contenu sans autorisation crée des workflows distincts pour chaque ressource de payload.
* SITES-30333 : lisez les métadonnées des ressources à partir du jcr pour éviter les problèmes d’analyse xmp.
* SITES-30353 : erreurs GraphQL DataFetchingExceptions pour le champ « src » dans les fragments de contenu AEM.
* SITES-30377 : Edge Delivery avec éditeur universel : nettoyage des noms d’organisation et de site.
* SITES-30386 : Edge Delivery avec éditeur universel : permet de supprimer les `cors.js` UE hérités et dupliqués.
* SITES-30583 : API REST de fragments de contenu : outil de recherche et de remplacement modifiant tous les caractères en minuscules.
* SITES-30585 : API REST de fragments de contenu : `previewUrlPattern` non défini lors de la création de CFM avec des références.
* SITES-30634 : le texte de remplacement et l&#39;alignement du RTE ne fonctionnent pas de manière cohérente.
* SITES-30660 : problème de conformité ADA avec le composant AEM personnalisé.
* SITES-30695 : Edge Delivery avec éditeur universel : augmentation du classement du pipeline de réécriture pour ne pas interférer avec le code personnalisé.
* SITES-30727 : impossible de faire glisser et de déposer des composants dans l’éditeur de création en production.
* SITES-30752 : n’utilisez pas d’en-têtes `If-modified-since`/`last-modified` lors de la génération d’une réponse de requête persistante.
* SITES-30871 : mises à jour DOM après le déclenchement du détecteur afteredit.
* SITES-30877 : statut de déploiement de page enfant incorrect.
* SITES-30899 : l’option Déployer « plus tard » permet de continuer sans aucune date sélectionnée.
* SITES-30947 : exception de pointeur nul en raison d’une propriété « behavior » manquante sur le plan directeur pendant le déploiement.
* SITES-31157 : API REST de fragments de contenu : échec du correctif dans une situation particulière.
* SITES-31162 : API REST de fragments de contenu : correction d’un problème de casting pour `DateTimeField` champ dans `ModelFieldMapper`.
* SITES-31174 : API REST de fragments de contenu : les balises n’ont pas été publiées avec la demande de publication.
* SITES-31272 : impossible de créer une copie linguistique des ressources via PageManager.copy.
* SITES-31327 : API REST de fragments de contenu : suppression de la validation ETag dans la requête de fragment GET.
* SITES-31387 : erreur JavaScript « ns.ui.alert n’est pas une fonction » lors de la réactivation de l’héritage du composant fantôme.
* SITES-31454 : API REST de fragments de contenu : relâchez le modèle pour que les champs de référence de fragment acceptent également les UUID.
* SITES-31455 : API REST de fragments de contenu : correction d’une incohérence d’ETag entre les points d’entrée d’un même modèle de fragment de contenu.
* SITES-31459 : API REST de fragments de contenu : impossible de modifier la Live Copy CF en présence d’un champ référence de contenu.
* SITES-31467 : js-errors de contexthub.authoring-hook.js dans l’éditeur de page.
* SITES-31487 : API REST de fragments de contenu : autorisez l’appel du point d’entrée des autorisations pour le dossier racine.
* SITES-31621 : Edge Delivery avec éditeur universel : suppression des lignes vides des feuilles de calcul qui sont des Live Copies.
* SITES-31676 : la création ou la suppression de composants laisse un espace vide au bas de la page.
* SITES-31822 : libellé de case à cocher ClassicUI manquant et HTML codé.
* SITES-31857 : la création du CF échoue dans les dossiers contenant des guillemets simples.
* SITES-31888 : la suppression de fragments de contenu ne se propage pas à l’aperçu.
* SITES-31922 : API REST de fragments de contenu : les références de page ne sont pas renvoyées par le point d’entrée referenceBy.
* SITES-31987 : les URL d’aperçu des fragments de contenu ne s’affichent pas lors de leur publication dans l’aperçu.
* SITES-32095 : l’actualisation automatique échoue sur le détecteur d’événement afterchilddelete dans la Live Copy.
* SITES-32237 : Edge Delivery avec éditeur universel : correction du rendu des composants de texte vides/malformés.

### Problèmes connus {#known-issues-21331}

* SITES-33177 : les styles de section stockés sous forme de chaînes séparées par des virgules sont rompus.

### Fonctionnalités et API obsolètes {#deprecated-21331}

Les fonctionnalités et API obsolètes et supprimées dans AEM as a Cloud Service sont présentées dans le document [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Correctifs de sécurité {#security-21331}

AEM as a Cloud Service est dédié à l’optimisation de la sécurité et des performances de votre plateforme. Cette version de maintenance corrige 21 vulnérabilités identifiées, renforçant ainsi notre engagement envers une protection robuste des systèmes.

### Technologies intégrées {#embedded-tech-21331}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.80.0 | [API Oak 1.80.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| API SLING AEM | 2.27.6 | [API Apache Sling 2.27.6](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.29.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
