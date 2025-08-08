---
title: Créer des environnements
description: Découvrez comment utiliser Cloud Manager pour créer vos premiers environnements.
role: Admin, User, Developer
exl-id: 31940e1e-fe27-4c5f-b67f-41affebea63a
feature: Onboarding
source-git-commit: 9c5838a01ceecf094aea19578e6560a5e5ca8c4c
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 62%

---

# Création d’environnements {#create-environments}

Dans cette partie du [parcours d’intégration](overview.md), vous apprendrez comment utiliser Cloud Manager pour créer vos premiers environnements.

## Objectif {#objective}

Suite à la lecture du document précédent de ce parcours d’intégration, [Créer des programmes](create-program.md), vous disposez désormais de votre propre programme Cloud Manager. Vous pouvez maintenant apprendre à utiliser Cloud Manager pour créer vos premiers environnements pour ce programme.

Après avoir lu ce document, vous pourrez :

* Comprendre à quoi renvoie un environnement.
* Connaître la différence entre les différents environnements.
* Être en mesure de créer votre propre environnement.

## Qu’est-ce qu’un environnement ? {#environments}

Les environnements se trouvent sous les programmes dans la hiérarchie de Cloud Manager. Les programmes vous permettent d’organiser votre solution et d’accorder à certains membres de l’équipe l’accès à ces programmes, tandis que les environnements appartiennent à des programmes spécifiques et sont les instances individuelles des solutions d’Adobe au sein de ces programmes. Les environnements sont utilisés à des fins spécifiques, telles que la création de contenu ou le test de nouveaux développements. Les pipelines CI/CD de Cloud Manager facilitent le déploiement de code vers ces environnements à partir de référentiels Git.

Si vous vous souvenez de l’exemple de la théorie des entreprises de voyage et d’aventure WKND, il s’agit d’un client qui se concentre sur les médias liés au voyage. Il a peut-être deux programmes. Autrement dit, un programme Sites pour sa division WKND Magazine et un programme Assets pour la division WKND Media. Chaque programme aurait probablement deux environnements, par exemple un environnement de production qui sert le trafic réel du site et un environnement de développement pour tester le nouveau code de l’application.

Il existe cinq types d’environnements différents :

* **Production et évaluation** : les environnements de production et d’évaluation sont disponibles par paire et sont utilisés respectivement à des fins de production et de test.
* **Développement** : vous pouvez créer un environnement de développement à des fins de développement et de test qui sera associé uniquement aux pipelines hors production.
* **Développement rapide** - Un environnement de développement rapide (RDE) permet à l’équipe de développement de déployer et d’examiner rapidement les modifications. Cela réduit le temps nécessaire pour tester les fonctionnalités qui fonctionnent dans un environnement de développement local.
* **Environnement de test spécialisé** - Fournit un espace dédié pour valider les fonctionnalités dans des conditions de quasi-production, idéal pour les tests de résistance et les contrôles avancés avant déploiement.

Dans le cadre de ce parcours d’intégration, vous pouvez commencer par créer un environnement de développement que vous pouvez utiliser pour explorer les fonctionnalités d’AEM as a Cloud Service.

## Création d’un environnement {#creating-environments}

>[!NOTE]
>
>Le système enregistre l’utilisateur qui crée un environnement en tant que son créateur. Étant donné que les utilisateurs supprimés peuvent parfois être restaurés, choisissez soigneusement le créateur d’environnement.

**Pour créer un environnement, procédez comme suit**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez ajouter un environnement.

1. Pour ajouter un environnement, à partir de la page **Aperçu du programme**, sur la carte **Environnements**, sélectionnez l’option **Ajouter un environnement**.

   ![Carte Environnements](/help/implementing/cloud-manager/assets/no-environments.png)

   * L’option **Ajouter un environnement** est également disponible dans l’onglet **Environnements**.

     ![Onglet Environnements](/help/implementing/cloud-manager/assets/environments-tab.png)

   * L’option **Ajouter un environnement** peut être désactivée en raison d’un niveau d’autorisation insuffisant ou de ressources sous licence.

1. Dans la boîte de dialogue **Ajouter un environnement**, procédez comme suit :

   * Sélectionnez un **type d’environnement**.
      * Le nombre d’environnements disponibles/utilisés est indiqué entre parenthèses derrière le type d’environnement de développement.
   * Fournissez un **Nom de l’environnement**.
   * Fournissez une **Description de l’environnement**.
   * Sélectionnez une **Région Cloud**.

   ![Boîte de dialogue Ajouter un environnement](/help/implementing/cloud-manager/assets/add-environment2.png)

1. Cliquez sur **Enregistrer** pour ajouter l’environnement spécifié.

Une fois l’environnement disponible, les membres de votre organisation affectés au profil de produit **Développeur** peuvent se connecter à Cloud Manager et gérer les référentiels Git de Cloud Manager.

## Prochaines étapes {#whats-next}

Maintenant que vous avez lu cette partie du parcours d’intégration, vous devriez :

* Comprendre à quoi renvoie un environnement.
* Connaître la différence entre les différents environnements.
* Être en mesure de créer votre propre environnement.

Votre équipe peut désormais accéder aux ressources cloud que vous avez créées. En tant qu’administrateur ou administratrice système, vous devez d’abord affecter les membres de votre équipe aux profils de produits dans AEM as a Cloud Service à partir d’Adobe Admin Console afin qu’ils puissent accéder à ces ressources.

Par conséquent, continuez votre parcours d’intégration en consultant le document [Affecter des membres de l’équipe aux profils de produits AEM as a Cloud Service](assign-profiles-aem.md). Dans ce document, vous apprendrez comment accorder des droits aux membres de votre équipe pour vos nouveaux environnements.

## Ressources supplémentaires {#additional-resources}

Vous trouverez ci-dessous des ressources facultatives supplémentaires si vous souhaitez aller au delà du contenu du parcours d’intégration.

* [Gérer les environnements](/help/implementing/cloud-manager/manage-environments.md) : découvrez les types d’environnements que vous pouvez créer et comment les créer pour votre projet Cloud Manager.
* [Utiliser Adobe Cloud Manager - Environnements](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/environments) : les environnements Cloud Manager sont composés de services de création, de publication et de Dispatcher AEM. Découvrez comment différents environnements prennent en charge les rôles et peuvent être utilisés à l’aide de différents pipelines CI/CD.
* [Environnements de développement rapide](/help/implementing/developing/introduction/rapid-development-environments.md) : consultez cette documentation pour plus d’informations sur l’utilisation d’un RDE.
<!-- ERROR: Not Found (HTTP error 404) FIND AN ALTERNATE RESOURCE? * [AEM Champion Tips and Tricks - Cloud Manager Environment Types](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/environment-types.md) - Watch this video for an overview of Cloud Manager environment types from an AEM champion. -->

