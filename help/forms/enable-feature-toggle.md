---
title: Activer le bouton (bascule) de fonctionnalités pour intégrer les fonctionnalités destinées aux utilisateurs et utilisatrices précoces et en version préliminaire
description: Le bouton (bascule) des fonctionnalités est une fonctionnalité d’AEM qui permet aux administrateurs d’activer de nouvelles fonctionnalités dans un environnement d’exécution.
feature: Adaptive Forms, Foundation Components, Core Components
role: User, Developer
source-git-commit: cc4fccc51f487170bf6c14e4b302a8d5912c33a0
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 6%

---

# Activer le bouton (bascule) des fonctionnalités sur le kit de développement logiciel Adobe Experience (AEM SDK)

Le bouton bascule des fonctionnalités dans AEM permet aux administrateurs d’activer ou de désactiver des fonctionnalités au moment de l’exécution, ce qui est idéal pour gérer les fonctionnalités d’adoption précoce et de version préliminaire sans changement de code. Il prend en charge les déploiements progressifs, les tests A/B et la désactivation rapide des fonctionnalités instables.

Cet article explique comment activer les bascules de fonctionnalités dans la configuration locale d’AEM SDK, qui simule AEM as a Cloud Service à l’aide de SDK et de Dispatcher. Cette configuration permet aux équipes de tester dans un environnement de production avant le déploiement sur le cloud.

## Pourquoi utiliser les bascules de fonctionnalités dans une configuration AEM SDK ?

Lorsque vous travaillez dans une configuration AEM SDK, la fonctionnalité active/désactive l’aide dans :

* Tester les caractéristiques expérimentales en toute sécurité.

* Déploiement de nouveaux composants par phases.

* Gestion d’une base de code unique dans plusieurs environnements.

* Réduction des risques lors des déploiements et des mises à niveau.

## Prérequis

Avant d’activer les bascules de fonctionnalité dans votre configuration d’AEM SDK, vérifiez les points suivants :

* L’utilisateur est membre du groupe `forms-users`.

* Accédez à `http://<author-instance-url>:portnumber/system/console/bundles` et vérifiez si le lot **(com.adobe.granite.toggle.impl.dev-1.1.2.jar)** est présent ou non. S’il n’est pas présent [téléchargez le lot à partir du lien](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/com.adobe.granite.toggle.impl.dev-1.1.2%20.jar).

  ![Basculement de fonction](/help/forms/assets/aem-web-console-bundle.png)

### Bouton (bascule) Activer la fonction

Pour activer les bascules de fonctionnalité dans votre instance AEM SDK, procédez comme suit :

1. Connectez-vous à l’instance AEM Forms.

1. Accédez à `http://author-instance-url:portnumber/system/console/configMgr`.

1. Recherchez le fournisseur de basculement dynamique Adobe Granite dans le gestionnaire de configuration.

   ![Basculement de fonction](/help/forms/assets/aem-web-console-confi.png)

1. Cliquez sur l’icône ✏️ .
1. Dans la section Activation des bascules , cliquez sur ➕ .
1. Ajoutez l’ID de basculement de la fonctionnalité, comme illustré dans l’image ci-dessous.
   ![Basculement de fonction](/help/forms/assets/feature-toggle.png)

1. Cliquez sur Enregistrer.

>[!NOTE]
>
> Vous trouverez l’ID de basculement de fonction dans le document spécifique aux fonctions destinées aux utilisateurs et utilisatrices précoces.


### Désactiver le bouton (bascule) des fonctionnalités

Pour désactiver la ou les fonctionnalités dont le ou les boutons d’activation sont activés, procédez comme suit :

1. Connectez-vous à l’instance AEM Forms.
1. Accédez à `http://author-instance-url:portnumber/system/console/configMgr`.
1. Recherchez le fournisseur de basculement dynamique Adobe Granite dans le gestionnaire de configuration.
1. Cliquez sur l’icône ✏️.
1. Dans la section Désactiver les bascules, cliquez sur ➕.
1. Ajoutez le numéro du bouton (bascule) de la fonction à désactiver.

   ![Basculement de fonction](/help/forms/assets/disable-toggle-feature.png)

### Considérations Techniques

Les bascules de fonctionnalités sont gérées lors de l’exécution et conviennent mieux aux configurations de développement ou de test. Dans une configuration AEM SDK, assurez-vous que les bascules sont contrôlées par version et synchronisées avec CI/CD. Il peut être nécessaire d’actualiser la page ou d’effacer le cache pour que les modifications soient prises en compte.

>[!NOTE]
>
> Pour activer cette fonctionnalité dans l’environnement de production, contactez l’équipe d’assistance Adobe.

