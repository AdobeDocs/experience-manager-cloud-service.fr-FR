---
title: Résolution des problèmes liés à MSM et FAQ
description: Découvrez comment résoudre les problèmes les plus courants liés à MSM et obtenir des réponses aux questions les plus courantes relatives à MSM.
feature: Multi Site Manager
role: Administrator
exl-id: 50f02f4f-a347-4619-ac90-b3136a7b1782
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# Résolution des problèmes liés à MSM et FAQ {#troubleshooting-msm}

## Dépannage des premières étapes {#first-steps}

Si vous constatez un comportement ou une erreur incorrect selon vous dans MSM, veillez à :

* Consultez la [FAQ sur la gestion multisite](#faq) car vos problèmes ou questions peuvent déjà y être abordés.
* Consultez l’ [article sur les bonnes pratiques MSM](best-practices.md) car plusieurs conseils y sont proposés, ainsi que des clarifications sur un certain nombre de fausses idées.

## Recherche d’informations avancées sur votre plan directeur et l’état de Live Copy {#advanced-info}

MSM enregistre plusieurs servlets qui peuvent être demandés avec des sélecteurs sur les URL des ressources. Ils sont utilisés par l’interface utilisateur, mais peuvent également être demandés directement pour afficher directement des états MSM calculés supplémentaires pour vos pages :

1. `http://<host>:<port>/content/path/to/bluprint/page.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`
   * Utilisez-le sur une page de plan directeur pour récupérer la liste de toutes les Live Copies qui y sont liées, avec des informations supplémentaires sur l’état de Live Copy.
1. `http://<host>:<port>/content/path/to/livecopy/page.msm.json`
   * Utilisez-le sur les pages Live Copy pour récupérer des informations avancées sur leur connexion à leurs pages de plan directeur. Si la page n’est pas une Live Copy, rien n’est renvoyé.

Ces servlets génèrent des messages de journal DEBUG via le journal `com.day.cq.wcm.msm` qui peuvent également s’avérer utiles.

## Vérification des informations spécifiques à MSM dans le référentiel {#checking-repo}

Les servlets précédents renvoyaient des informations calculées en fonction des noeuds et des mixins spécifiques à MSM. Les informations sont stockées dans le référentiel de la manière suivante.

* `cq:LiveSync` type de mixin
   * Il est défini sur les noeuds `jcr:content` et définit les pages Live Copy racine.
   * Ces pages auront un noeud enfant `cq:LiveSyncConfig` de type `cq:LiveCopy` qui contiendra des informations de base et obligatoires sur la Live Copy via les propriétés suivantes :
      * `cq:master` pointe vers la page de plan directeur de la Live Copy.
      * `cq:rolloutConfigs` indique les principales configurations de déploiement appliquées à la Live Copy.
      * `cq:isDeep` est définie sur true si les pages enfants de cette page Live Copy racine sont incluses dans la Live Copy.
* `cq:LiveRelationship` type de mixin
   * Toute page Live Copy possède un tel type de mixin sur son noeud `jcr:content`.
   * Si ce n’est pas le cas, la page a à un moment donné été désolidarisée ou créée manuellement via l’interface de création en dehors d’une action Live Copy (création ou déploiement).
* `cq:LiveSyncCancelled` type de mixin
   * Ajout aux noeuds `jcr:content` des pages Live Copy qui ont été suspendus.
   * Si la suspension est également effective pour les pages enfants, une propriété `cq:isCancelledForChildren` est définie sur true sur le même noeud.

Les informations présentes dans ces propriétés doivent être reflétées dans l’interface utilisateur. Toutefois, lors de la résolution des problèmes, il peut s’avérer utile d’observer le comportement de MSM directement dans le référentiel au fur et à mesure que des actions MSM se produisent.

Connaître ces propriétés peut également s’avérer utile pour interroger votre référentiel et découvrir des ensembles de pages qui se trouvent dans des états particuliers. Par exemple :

* `select * from cq:LiveSync` renvoie toutes les pages racine Live Copy.

## FAQ {#faq}

Voici quelques questions fréquemment posées relatives à MSM et Live Copy.

### Pourquoi certaines propriétés (titre, annotations, par exemple) ne sont-elles pas mises à jour lors d’un déploiement MSM ? {#missing-properties}

Les actions de synchronisation MSM sont hautement configurables. Les propriétés ou composants qui sont modifiés lors des déploiements dépendent directement des propriétés de ces configurations.

Voir [cet article](best-practices.md) pour plus d’informations sur cette rubrique.

### Comment supprimer les autorisations de déploiement d’un groupe d’auteurs ? {#remove-rollout-permissions}

Il n’existe aucun privilège **rollout** pouvant être défini ou supprimé pour AEM entités principales (utilisateurs ou groupes).

Vous pouvez également effectuer l’une des opérations suivantes :

* Personnalisation de l’interface utilisateur du produit pour masquer les actions de déploiement pour une entité de sécurité donnée.
* Supprimez les privilèges d’écriture de l’arborescence de Live Copy pour les auteurs qui ne sont pas autorisés à se déployer.

### Pourquoi les pages Live Copy avec le suffixe &quot;_msm_moved&quot; s’affichent-elles ? {#moved-pages}

Si une page de plan directeur est déployée, elle met à jour sa page Live Copy ou crée une page Live Copy si elle n’existe pas encore (par exemple, lorsqu’elle est déployée pour la première fois ou que la page Live Copy a été supprimée manuellement).

Dans ce dernier cas, cependant, si une page sans propriété `cq:LiveRelationship` existe avec le même nom, cette page sera renommée en conséquence, avant la création de la page Live Copy.

Par défaut, le déploiement attend soit une page Live Copy liée, sur laquelle les mises à jour des plans directeurs seront déployées, soit aucune page à l’emplacement, lors de la création d’une page Live Copy.

Si une page &quot;autonome&quot; est trouvée, MSM choisit de renommer cette page et de créer une page Live Copy distincte liée.

Une telle page autonome dans une sous-arborescence de Live Copy est généralement le résultat d’une opération **Désolidariser**, ou l’ancienne page de Live Copy a été supprimée manuellement par un auteur, puis recréée avec le même nom.

Pour éviter cela, utilisez la fonction Live Copy **Suspendre** au lieu de **Désolidariser**. Pour plus d’informations sur l’action **Désolidariser** dans [cet article.](creating-live-copies.md)
