---
title: Créer des environnements
description: Découvrez comment utiliser Cloud Manager pour créer vos premiers environnements.
role: Admin, User, Developer
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 26%

---


# Créer des environnements {#create-environments}

Dans cette partie du [parcours d&#39;intégration,](overview.md) vous apprendrez à utiliser Cloud Manager pour créer vos premiers environnements.

## Objectif {#objective}

Après avoir lu le document précédent dans ce parcours d&#39;intégration, [Créer des programmes,](create-program.md) vous disposez désormais de votre propre programme Cloud Manager. Vous pouvez maintenant apprendre à utiliser Cloud Manager pour créer vos premiers environnements pour ce programme.

Après avoir lu ce document, vous allez :

* Comprendre ce qu’est un environnement.
* Connaître la différence entre les différents environnements.
* Soyez en mesure de créer votre propre environnement.

## Qu&#39;est-ce qu&#39;un environnement ? {#environments}

Les environnements se trouvent sous les programmes dans la hiérarchie de Cloud Manager. Bien que les programmes vous permettent d’organiser votre solution et d’accorder l’accès à certains membres de l’équipe à ces programmes, les environnements appartiennent à des programmes spécifiques et sont des instances individuelles des solutions d’Adobe de ces programmes. Les environnements sont utilisés à des fins spécifiques, telles que la création de contenu ou le test de nouveaux développements. Les pipelines CI/CD de Cloud Manager facilitent le déploiement de code vers ces environnements à partir de référentiels Git.

Si vous vous souvenez de l’exemple de la théorie des entreprises de voyages et d’aventure WKND, qui est un client qui se concentre sur les médias liés au voyage, il se peut qu’il y ait deux programmes : un programme Sites pour sa division WKND Magazine et un programme Ressources pour la division WKND Media. Chaque programme aurait probablement deux environnements, tels qu’un environnement de production qui sert le trafic réel du site et un environnement de développement pour tester le nouveau code de l’application.

Il existe trois types d’environnements différents :

* **Production et évaluation** - Les environnements de production et d’évaluation sont disponibles par paire et sont utilisés respectivement à des fins de production et de test.
* **Développement** - Un environnement de développement peut être créé à des fins de développement et de test et sera associé uniquement aux pipelines qui ne sont pas en production.

Pour les besoins de ce parcours d’intégration, vous allez créer un environnement de développement.

## Créer des environnements {#creating-environments}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez ajouter un environnement.

1. Dans la page **Aperçu du programme**, cliquez sur **Ajouter un environnement** dans la carte **Environnements** pour ajouter un environnement.

   ![Carte Environnements](/help/implementing/cloud-manager/assets/no-environments.png)

   * L’option **Ajouter un environnement** est également disponible dans l’onglet **Environnements**.

      ![Onglet Environnements](/help/implementing/cloud-manager/assets/environments-tab.png)

   * L’option **Ajouter un environnement** peut être désactivée en raison d’un niveau d’autorisation insuffisant ou de ressources sous licence.

1. Dans la boîte de dialogue **Ajouter un environnement** qui s’affiche :

   * Sélectionnez un **type d’environnement**.
      * Le nombre d’environnements disponibles/utilisés est indiqué entre parenthèses derrière le type Environnement de développement .
   * Fournissez un **Nom de l’environnement**.
   * Fournissez une **Description de l’environnement**.
   * Sélectionnez une **Région Cloud**.

   ![Boîte de dialogue Ajouter un environnement](/help/implementing/cloud-manager/assets/add-environment2.png)

1. Cliquez sur **Enregistrer** pour ajouter l’environnement spécifié.

Une fois l’environnement disponible, les membres de votre organisation affectés à la fonction **Développeur** Le profil de produit peut se connecter à Cloud Manager et gérer les référentiels Git de Cloud Manager.

## Prochaines étapes {#whats-next}

Maintenant que vous avez lu cette partie du parcours d’intégration, vous devez :

* Comprendre ce qu’est un environnement.
* Connaître la différence entre les différents environnements.
* Soyez en mesure de créer votre propre environnement.

Vos ressources cloud ont été créées et sont prêtes à être consultées par votre équipe. En tant qu’administrateur système, vous devez d’abord affecter des membres de votre équipe à AEM des profils de produit as a Cloud Service de Adobe Admin Console pour qu’ils puissent accéder à ces ressources.

Par conséquent, vous devez continuer votre parcours d’intégration en consultant le document. [Affectation de membres d’équipe à AEM des profils de produit as a Cloud Service.](assign-profiles-aem.md)  Dans ce document, vous apprendrez à accorder aux membres de votre équipe les droits dont ils ont besoin pour accéder à vos nouveaux environnements.

## Ressources supplémentaires {#additional-resources}

Suivez les autres ressources pour en savoir plus sur les aspects suivants :

* [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) - Découvrez les types d’environnements que vous pouvez créer et comment les créer pour votre projet Cloud Manager.
* [Utilisation d’Adobe Cloud Manager - Environnements](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=fr) - Les environnements Cloud Manager sont composés de services de création, de publication et de Dispatcher AEM. Découvrez comment différents environnements prennent en charge les rôles et peuvent être utilisés à l’aide de différents pipelines CI/CD.
