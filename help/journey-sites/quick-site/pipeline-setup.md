---
title: Configuration de votre pipeline
description: Créez un pipeline frontal pour gérer la personnalisation du thème de votre site.
exl-id: 0d77d1a6-98f3-4961-9283-f52c1b5b2a7b
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 2%

---

# Configuration de votre pipeline {#set-up-your-pipeline}

Créez un pipeline frontal pour gérer la personnalisation du thème de votre site.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent du parcours de création rapide de site AEM, [Créer un site à partir d’un modèle,](create-site.md) vous avez appris à utiliser un modèle de site pour créer rapidement un site AEM qui peut être personnalisé à l’aide d’outils front-end. vous devez maintenant :

* Découvrez comment obtenir des modèles de site AEM.
* Découvrez comment créer un site à l’aide d’un modèle.
* Découvrez comment télécharger le modèle sur votre nouveau site pour le fournir au développeur front-end.

Cet article s’appuie sur ces principes de base afin que vous puissiez configurer un pipeline frontal, que le développeur front-end utilisera ultérieurement dans le parcours pour déployer les personnalisations front-end.

## Objectif {#objective}

Ce document vous aide à comprendre les pipelines front-end et comment en créer un pour gérer le déploiement du thème personnalisé de votre site. Après l’avoir lu, vous devriez :

* Comprendre ce qu’est un pipeline frontal.
* Découvrez comment configurer un pipeline frontal dans Cloud Manager.

## Rôle responsable {#responsible-role}

Cette partie du parcours s’applique à l’administrateur de Cloud Manager.

## Conditions requises {#requirements}

* Vous devez avoir accès à Cloud Manager.
* Vous devez être membre du **Responsable de déploiement** dans Cloud Manager.
* Un référentiel git pour l’environnement AEM doit être configuré dans Cloud Manager.
   * C&#39;est généralement déjà le cas pour tout projet principal. Si ce n’est pas le cas, reportez-vous à la documentation des référentiels Cloud Manager disponible sous le [Ressources supplémentaires](#additional-resources) .

## Présentation d’un pipeline front-end {#front-end-pipeline}

Le développement front-end implique la personnalisation de ressources JavaScript, CSS et statiques qui définissent le style de votre site AEM. Le développeur front-end travaille dans ses propres environnements locaux pour effectuer ces personnalisations. Une fois qu’elles sont prêtes, les modifications sont validées dans le référentiel git d’AEM. Mais ils ne sont engagés que dans le code source. Ils ne sont pas encore en vie.

Le pipeline frontal prend ces personnalisations validées et les déploie dans un environnement AEM, généralement dans des environnements de production ou hors production.

Ainsi, le développement front-end peut fonctionner séparément et parallèlement à tout développement back-end en pile complète sur AEM, qui possède ses propres pipelines de déploiement.

>[!NOTE]
>
>Les pipelines front-end peuvent uniquement déployer des ressources JavaScript, CSS et statiques pour appliquer un style à votre site AEM. Le contenu du site, tel que les pages ou les ressources, ne peut pas être déployé dans un pipeline.

## L’accès à Cloud Manager {#login}

1. Connectez-vous à Adobe Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

1. Cloud Manager répertorie les différents programmes disponibles. Appuyez ou cliquez sur celui que vous souhaitez gérer. Si vous commencez à utiliser AEM as a Cloud Service, il est probable qu’un seul programme soit disponible.

   ![Sélection d’un programme dans Cloud Manager](assets/cloud-manager-select-program.png)

Vous voyez maintenant un aperçu de votre programme. Votre page sera différente, mais similaire à cet exemple.

![Présentation de Cloud Manager](assets/cloud-manager-overview.png)

Notez le nom du programme auquel vous avez accédé ou copiez l’URL. Vous devrez fournir cette information au développeur front-end ultérieurement.

## Création d’un pipeline front-end {#create-front-end-pipeline}

Maintenant que vous avez accédé à Cloud Manager, vous pouvez créer un pipeline pour le déploiement frontal.

1. Dans le **Pipelines** de la page Cloud Manager, appuyez ou cliquez sur l’icône **Ajouter** bouton .

   ![Pipelines](assets/pipelines-add.png)

1. Dans le menu contextuel qui s’affiche sous **Ajouter** bouton , sélectionnez **Ajout d’un pipeline hors production** aux fins du présent parcours.

1. Sur le **Configuration** de l’onglet **Ajout d’un pipeline hors production** qui s’ouvre :
   * Sélectionner **Pipeline de déploiement**.
   * Attribuez un nom au pipeline dans la variable **Nom du pipeline hors production** champ .

   ![Ajout de la configuration du pipeline](assets/add-pipeline-configuration.png)

1. Appuyez ou cliquez sur **Continuer**.

1. Sur le **Code source** tab :
   * Sélectionner **Code front-end** comme type de code à déployer.
   * Assurez-vous que l’environnement approprié est sélectionné sous **Environnements de déploiement éligibles**.
   * Sélectionnez la **Référentiel**.
   * Définissez la variable **Branche Git** le pipeline doit être associé à .
   * Définissez la variable **Emplacement du code** si le développement front-end se trouve sous un chemin particulier dans le référentiel sélectionné. La valeur par défaut est la racine du référentiel, mais le développement frontal et le back-end se font souvent sous différents chemins.

   ![Informations sur le code source pour l’ajout de pipeline](assets/add-pipeline-source-code.png)

1. Cliquez ou appuyez sur **Enregistrer**.

Le nouveau pipeline est créé et visible dans le **Pipelines** de la fenêtre Cloud Manager . Lorsque vous cliquez sur les points de suspension après le nom du pipeline, les options s’affichent pour modifier ou afficher les détails, si nécessaire.

![Options de pipeline](assets/new-pipeline.png)

>[!TIP]
>
>Si vous connaissez déjà les pipelines dans AEMaaCS et souhaitez en savoir plus sur les différences entre les différents types de pipelines, y compris des détails supplémentaires sur le pipeline frontal, reportez-vous à la section Configuration du pipeline CI/CD - Cloud Services liés dans la section [Ressources supplémentaires](#additional-resources) ci-dessous.

## Et après ? {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours de création rapide de site AEM, vous devez :

* Comprendre ce qu’est un pipeline frontal.
* Découvrez comment configurer un pipeline frontal dans Cloud Manager.

Tirez parti de ces connaissances et poursuivez votre parcours de création rapide de site AEM en consultant le document. [Accorder l’accès au développeur front-end,](grant-access.md) où vous embarquez les développeurs front-end dans Cloud Manager afin qu’ils aient accès à votre référentiel git et à votre pipeline d’AEM site.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de création de site rapide en consultant le document [Personnaliser le thème du site,](customize-theme.md) vous trouverez ci-dessous des ressources facultatives supplémentaires qui approfondissent certains concepts mentionnés dans ce document, mais qui ne sont pas nécessaires pour continuer sur le parcours.

* [Documentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Si vous souhaitez plus de détails sur les fonctionnalités de Cloud Manager, vous pouvez consulter directement la documentation technique détaillée.
* [Référentiels Cloud Manager](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) - Si vous avez besoin d’informations supplémentaires sur la configuration et la gestion des référentiels Git pour votre projet AEMaaCS, reportez-vous à ce document.
* [Configuration du pipeline CI/CD - Cloud Services](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) - Pour plus d’informations sur la configuration des pipelines, à la fois pile complète et frontale, consultez ce document.
