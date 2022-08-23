---
title: Création d’un programme
description: Découvrez comment utiliser Cloud Manager pour créer votre premier programme.
role: Admin, User, Developer
exl-id: ade4bb43-5f48-4938-ac75-118009f0a73b
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 25%

---

# Création d’un programme {#create-program}

Dans cette partie du [parcours d&#39;intégration,](overview.md) vous apprendrez à utiliser Cloud Manager pour créer votre premier programme.

## Objectif {#objective}

Après avoir consulté le document précédent dans ce parcours d’intégration, [Accès à Cloud Manager,](cloud-manager.md) vous avez garanti un accès approprié à Cloud Manager. Vous pouvez maintenant créer votre premier programme.

Après avoir lu ce document, vous allez :

* Comprendre ce qu&#39;est un programme.
* Découvrez la différence entre les programmes de production et les programmes Sandbox.
* Sois en mesure de créer ton propre programme.

## Qu&#39;est-ce qu&#39;un programme ? {#programs}

Les programmes constituent le niveau d’organisation le plus élevé de Cloud Manager. En fonction de votre licence avec Adobe, les programmes vous permettent d’organiser votre solution et d’accorder l’accès à des membres de l’équipe en particulier à ces programmes.

Les programmes Cloud Manager représentent des ensembles d’environnements Cloud Manager. Ces programmes prennent en charge des ensembles logiques d’initiatives commerciales, correspondant généralement à un contrat de niveau de service (SLA) sous licence. Par exemple, un programme peut représenter les ressources AEM pour prendre en charge un site web public mondial pour une organisation, tandis qu’un autre programme représente un DAM central interne.

Si vous vous souvenez de l’exemple de la théorie des entreprises de voyages et d’aventure WKND, qui est un client qui se concentre sur les médias liés au voyage, il se peut qu’il y ait deux programmes : un programme Sites pour sa division WKND Magazine et un programme Ressources pour la division WKND Media. Différents membres de l&#39;équipe auraient alors accès aux différents programmes en raison de leur propre division du travail.

Il existe deux types de programmes différents :

* Un **programme de production** est créé pour activer le trafic en direct pour votre site. C&#39;est votre environnement &quot;réel&quot;.
* Un **programme Sandbox** est généralement créé pour les besoins de formation, à des fins de démonstration, d’activation, de preuve de concept ou de documentation.

Étant donné qu’ils servent des objectifs différents, les différents environnements disposent d’options différentes. Cependant, le processus de création de ces fichiers est similaire. Pour ce parcours d’intégration, nous allons créer un environnement de test.

## Création d’un programme Sandbox {#create-sandbox}

Pour créer un programme Sandbox, procédez comme suit.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Dans la page de destination de Cloud Manager, cliquez sur **Ajouter un programme** dans le coin supérieur droit de l’écran.

   ![Page de destination de Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

1. Dans l’assistant de création de programme, sélectionnez **Configurer un environnement de test**, indiquez un nom de programme, puis cliquez sur **Créer**.

   ![Création d’un type de programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/create-sandbox.png)

Une nouvelle carte de programme sandbox s’affiche sur la page d’entrée avec un indicateur de statut au fur et à mesure que le processus de configuration progresse.

![Création d’un sandbox à partir de la page d’aperçu](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/program-create-setupdemo2.png)

Une fois le programme terminé, les membres de votre organisation affectés au **Développeur** Le profil de produit peut se connecter à Cloud Manager et gérer les référentiels Git de Cloud Manager.

## Prochaines étapes {#whats-next}

Maintenant que votre premier programme est créé, vous pouvez créer des environnements pour celui-ci. Continuez votre parcours d’intégration en consultant le document. [Création d’environnements.](create-environments.md)

## Ressources supplémentaires {#additional-resources}

Suivez les autres ressources pour en savoir plus sur les aspects suivants :

* [Programmes et types de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) - Découvrez la hiérarchie de Cloud Manager et comment les différents types de programmes s’intègrent dans sa structure et en quoi ils diffèrent.
* [Création de programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) - Découvrez comment utiliser Cloud Manager pour créer votre propre programme d’environnement de test à des fins de formation, de démonstration, de preuves de concept ou à d’autres fins hors production.
* [Création de programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) - Découvrez comment utiliser Cloud Manager pour créer votre propre programme de production afin d’héberger le trafic en direct.
* [Utilisation d’Adobe Cloud Manager - Programmes](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=fr) - Les programmes Cloud Manager représentent des ensembles d’environnements AEM prenant en charge des ensembles logiques d’initiatives commerciales, correspondant généralement à un contrat de niveau de service (SLA) acheté.
