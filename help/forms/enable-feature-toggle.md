---
title: Activer la fonction d’activation/désactivation des fonctionnalités pour intégrer les fonctionnalités destinées aux utilisateurs et utilisatrices précoces et en version préliminaire
description: La fonction d’activation/désactivation des fonctionnalités est une fonctionnalité d’AEM qui permet aux administrateurs et administratrices d’activer de nouvelles fonctionnalités dans un environnement d’exécution.
feature: Adaptive Forms, Foundation Components, Core Components
role: User, Developer
exl-id: 3ad1370a-a399-4fbe-8168-c3a1cee06336
source-git-commit: c1d62f0dd5a25da7fbeef537e1c28fa8421f42cd
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 45%

---

# Activer le bouton (bascule) des fonctionnalités sur le kit de développement logiciel Adobe Experience (AEM SDK)

Le bouton bascule des fonctionnalités dans AEM permet aux administrateurs d’activer ou de désactiver des fonctionnalités au moment de l’exécution, ce qui est idéal pour gérer les fonctionnalités d’adoption précoce et de version préliminaire sans changement de code. Il prend en charge les déploiements progressifs, les tests A/B et la désactivation rapide des fonctionnalités instables.

Cet article explique comment activer les bascules de fonctionnalités dans la configuration locale d’AEM SDK, qui simule AEM as a Cloud Service à l’aide de SDK et de Dispatcher. Cette configuration permet aux équipes de tester dans un environnement de production avant le déploiement sur le cloud.

## Pourquoi utiliser les bascules de fonctionnalités dans une configuration AEM SDK ?

Lorsque vous travaillez dans une configuration AEM SDK, la fonctionnalité active/désactive l’aide dans :

* Tester des fonctionnalités expérimentales en toute sécurité.

* Déployer de nouveaux composants en plusieurs phases.

* Disposer d’une base de code unique pour plusieurs environnements.

* Réduire les risques lors des déploiements et des mises à niveau.

## Prérequis

Avant d’activer les bascules de fonctionnalité dans votre configuration d’AEM SDK, vérifiez les points suivants :

* L’utilisateur ou l’utilisatrice est membre du groupe `forms-users`.

* Accédez à `http://<author-instance-url>:portnumber/system/console/bundles` et vérifiez si le lot **(com.adobe.granite.toggle.impl.dev-1.1.2.jar)** est présent ou non. S’il n’est pas présent, [téléchargez le lot à partir de ce lien](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]s/cq650/hotfix/com.adobe.granite.toggle.impl.dev-1.1.8.jar).

  ![Fonction d’activation/désactivation des fonctionnalités](/help/forms/assets/aem-web-console-bundle.png)

### Bouton (bascule) Activer la fonction

Pour activer les bascules de fonctionnalité dans votre instance AEM SDK, procédez comme suit :

1. Connectez-vous à votre instance AEM Forms.

1. Accédez à `http://author-instance-url:portnumber/system/console/configMgr`.

1. Recherchez le fournisseur de basculement dynamique Adobe Granite dans le gestionnaire de configuration.

   ![Fonction d’activation/désactivation des fonctionnalités](/help/forms/assets/aem-web-console-confi.png)

1. Cliquez sur l’icône ✏️ .
1. Dans la section Activation des bascules , cliquez sur ➕ .
1. Ajoutez l’identifiant du bouton d’activation de fonctionnalités, comme illustré dans l’image ci-dessous.
   ![Fonction d’activation/désactivation des fonctionnalités](/help/forms/assets/feature-toggle.png)

1. Cliquez sur Enregistrer.

>[!NOTE]
>
> Vous trouverez l’identifiant de la fonction d’activation/désactivation des fonctionnalités dans le document spécifique aux fonctions destinées aux utilisateurs et aux utilisatrices précoces.


### Désactiver la fonction d’activation/désactivation des fonctionnalités

Pour désactiver la fonction d’activation/désactivation des fonctionnalités pour les fonctionnalités sur lesquelles celle-ci est activée, procédez comme suit :

1. Connectez-vous à votre instance AEM Forms.
1. Accédez à `http://author-instance-url:portnumber/system/console/configMgr`.
1. Recherchez le fournisseur de basculement dynamique Adobe Granite dans le gestionnaire de configuration.
1. Cliquez sur l’icône ✏️.
1. Dans la section Désactiver les bascules, cliquez sur ➕.
1. Ajoutez le numéro de la fonction bascule pour désactiver la fonction.

   ![Fonction d’activation/désactivation des fonctionnalités](/help/forms/assets/disable-toggle-feature.png)

### Considérations techniques

Les bascules de fonctionnalités sont gérées lors de l’exécution et conviennent mieux aux configurations de développement ou de test. Dans une configuration AEM SDK, assurez-vous que les bascules sont contrôlées par version et synchronisées avec CI/CD. Il peut être nécessaire d’actualiser la page ou d’effacer le cache pour que les modifications soient prises en compte.

>[!NOTE]
>
> Pour activer cette fonctionnalité dans l’environnement de production, contactez l’équipe d’assistance Adobe.
