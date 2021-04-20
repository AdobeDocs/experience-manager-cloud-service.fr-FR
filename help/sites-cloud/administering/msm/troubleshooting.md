---
title: Résolution des problèmes et questions fréquentes liés aux modules multimédias
description: Découvrez comment résoudre les problèmes les plus courants liés aux MSM et obtenir des réponses aux questions les plus courantes liées aux MSM.
feature: Multi Site Manager
role: Administrator
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Dépannage des problèmes liés aux MSM et FAQ {#troubleshooting-msm}

## Dépannage des premières étapes {#first-steps}

Si vous constatez un comportement incorrect ou une erreur dans le module multisite, avant de commencer et de procéder à un dépannage détaillé, veillez à :

* Consultez la [FAQ sur les médias multimédias](#faq) car vos problèmes ou questions peuvent déjà y être abordés.
* Consultez l&#39;article [Meilleures pratiques en matière de gestion multidisciplinaire](best-practices.md) car un certain nombre de conseils y sont proposés ainsi que des clarifications sur un certain nombre de fausses idées.

## Recherche d&#39;informations avancées sur votre plan et l&#39;état de Live Copy {#advanced-info}

MSM enregistre plusieurs servlets qui peuvent être demandés avec des sélecteurs sur les URL de ressource. Elles sont utilisées par l’interface utilisateur, mais peuvent également être demandées directement pour afficher des états MSM calculés supplémentaires pour vos pages :

1. `http://<host>:<port>/content/path/to/bluprint/page.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`
   * Utilisez-le sur une page de plan pour récupérer la liste de toutes les Live Copies qui y sont liées, avec des informations supplémentaires sur l&#39;état de Live Copy.
1. `http://<host>:<port>/content/path/to/livecopy/page.msm.json`
   * Utilisez-le sur les pages Live Copy pour récupérer des informations avancées sur leur connexion à leurs pages de plan. Si la page n’est pas une Live Copy, rien n’est renvoyé.

Ces servlets génèrent des messages du journal DEBUG via le journal `com.day.cq.wcm.msm` qui peuvent également être utiles.

## Vérification des informations spécifiques au module MSM dans le référentiel {#checking-repo}

Les servlets précédents renvoyaient des informations calculées basées sur les noeuds et mixins spécifiques au MSM. Les informations sont stockées dans le référentiel de la manière suivante.

* `cq:LiveSync` type de mixin
   * Il est défini sur les noeuds `jcr:content` et définit les pages racine Live Copy.
   * Ces pages auront un noeud enfant `cq:LiveSyncConfig` de type `cq:LiveCopy` qui contiendra des informations de base et obligatoires sur la Live Copy via les propriétés suivantes :
      * `cq:master` pointe vers la page de plan de la Live Copy.
      * `cq:rolloutConfigs` indique les configurations de déploiement principal appliquées à Live Copy.
      * `cq:isDeep` est true si les pages enfants de cette page racine Live Copy sont incluses dans Live Copy.
* `cq:LiveRelationship` type de mixin
   * Toute page Live Copy a un tel type de mixin sur son noeud `jcr:content`.
   * Si tel n’est pas le cas, la page a à un moment donné été détachée ou créée manuellement via l’interface de création en dehors d’une action Live Copy (création ou déploiement).
* `cq:LiveSyncCancelled` type de mixin
   * Ajouté aux noeuds `jcr:content` des pages Live Copy suspendues.
   * Si la suspension s’applique également aux pages enfants, une propriété `cq:isCancelledForChildren` est définie sur true sur le même noeud.

Les informations présentes dans ces propriétés doivent être reflétées dans l’interface utilisateur. Toutefois, lors de la résolution des problèmes, il peut s’avérer utile d’observer directement le comportement des MSM dans le référentiel lorsque des actions MSM se produisent.

La connaissance de ces propriétés peut également s’avérer utile pour requête de votre référentiel et découvrir des jeux de pages qui se trouvent dans des états particuliers. Par exemple :

* `select * from cq:LiveSync` renvoie toutes les pages racine Live Copy.

## FAQ {#faq}

Vous trouverez ci-dessous quelques questions fréquentes sur les médias sociaux et la Live Copy.

### Pourquoi certaines propriétés (par exemple le titre, les annotations) ne sont-elles pas mises à jour lors d’un déploiement MSM ? {#missing-properties}

Les actions de synchronisation MSM sont hautement configurables. Les propriétés ou composants qui sont modifiés lors des déploiements dépendent directement des propriétés de ces configurations.

Consultez [cet article](best-practices.md) pour plus d&#39;informations sur ce sujet.

### Comment puis-je supprimer les autorisations de déploiement pour un groupe d’auteurs ? {#remove-rollout-permissions}

Aucun privilège **rollout** ne peut être défini ou supprimé pour les entités d&#39;AEM (utilisateurs ou groupes).

Vous pouvez également :

* Personnalisation de l’interface utilisateur du produit pour masquer les actions de déploiement pour une entité de sécurité donnée.
* Supprimez les privilèges d’écriture de l’arborescence Live Copy pour les auteurs qui ne sont pas autorisés à se déployer.

### Pourquoi vois-je les pages Live Copy avec le suffixe &quot;_msm_move&quot; ? {#moved-pages}

Si une page de plan est déployée, elle mettra à jour sa page Live Copy ou créera une nouvelle page Live Copy si elle n&#39;existait pas encore (par exemple, lorsqu&#39;elle est déployée pour la première fois ou que la page Live Copy a été supprimée manuellement).

Dans ce dernier cas, cependant, si une page sans propriété `cq:LiveRelationship` porte le même nom, cette page sera renommée en conséquence, avant la création de la page Live Copy.

Par défaut, le déploiement attend soit une page Live Copy liée, sur laquelle les mises à jour des plans détaillés seront déployées, soit une page vide au moment de la création d&#39;une page Live Copy.

Si une page &quot;autonome&quot; est trouvée, MSM choisit de renommer cette page et de créer une page Live Copy distincte et liée.

Une telle page autonome dans une sous-arborescence de Live Copy est généralement le résultat d’une opération **Détach**, ou l’ancienne page de Live Copy a été supprimée manuellement par un auteur, puis recréée sous le même nom.

Pour éviter cela, utilisez la fonction Live Copy **Suspendre** au lieu de **Détacher**. Plus d&#39;informations sur l&#39;action **Détacher** dans [cet article.](creating-live-copies.md)
