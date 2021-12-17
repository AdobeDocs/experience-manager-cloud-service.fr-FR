---
title: Gestion de vos sites de démonstration
description: Découvrez les outils disponibles pour vous aider à gérer vos sites de démonstration et comment les supprimer.
source-git-commit: cb04570664188635d6dc0237eb4ab0a9d347aaf2
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 1%

---


# Gestion de vos sites de démonstration {#manage-demo-sites}

Découvrez les outils disponibles pour vous aider à gérer vos sites de démonstration et comment les supprimer.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent du parcours de création rapide de site AEM, [Créer un site,](create-site.md) vous avez créé un nouveau site de démonstration basé sur les modèles du module complémentaire de démonstration de référence. Vous devez maintenant :

* Découvrez comment accéder à l’environnement de création AEM.
* Découvrez comment créer un site à partir d’un modèle.
* Découvrez les principes de base de la navigation dans la structure du site et de la modification d’une page.

Maintenant que vous avez votre propre site de démonstration à explorer, cet article décrit les outils disponibles pour vous aider à gérer vos sites de démonstration et comment les supprimer.

## Objectif {#objective}

Ce document vous aide à comprendre comment gérer les sites de démonstration que vous avez créés. Après l’avoir lu, vous devriez :

* Découvrez comment accéder aux utilitaires de démonstration en libre-service.
* Sachez quels utilitaires vous avez à votre disposition.
* Comment supprimer un site ou un modèle de démonstration existant.

## Accès aux utilitaires de démonstration en libre-service {#accessing-utilities}

Maintenant que vous disposez de vos propres sites de démonstration, vous souhaitez probablement savoir comment les gérer. Le pipeline a non seulement déployé les modèles de site pour fournir le contenu de vos sites de démonstration, mais il a également déployé un ensemble d’utilitaires pour gérer ces sites.

1. Dans la barre de navigation globale AEM, sélectionnez **Outils** -> **Démonstrations de référence** -> **Utilitaires de démonstration de référence**.

   ![Utilitaires de démonstration en libre-service](assets/demo-utilities.png)

1. Reference Demo Utilities est un ensemble de fonctionnalités utiles qui aideront à configurer et à surveiller votre environnement Adobe Experience Manager. La vue initiale est la **Tableau de bord**, qui sert de vérification de l’état de l’environnement et de sa fonctionnalité de démonstration.

   ![Tableau de bord](assets/dashboard.png)

Les utilitaires de démonstration en libre-service fournissent un certain nombre d’outils.

* **Supprimer des sites** - Sélectionnez le site que vous souhaitez supprimer dans cette instance Adobe Experience Manager. Gardez à l’esprit qu’il s’agit d’une action destructrice qui ne peut pas être annulée une fois lancée.
* **Suppression de modèles de site** - Sélectionnez le modèle de site que vous souhaitez supprimer dans cette instance Adobe Experience Manager. Avant de supprimer un modèle de site, assurez-vous que tous les sites qui y font référence sont également supprimés. Gardez à l’esprit qu’il s’agit d’une action destructrice qui ne peut pas être annulée une fois lancée.
* **Cache de l’auteur principal** - Plusieurs ressources seront récupérées dans l’instance Adobe Experience Manager, ce qui accélérera leurs temps de récupération. Cela peut prendre plusieurs secondes.
* **Application Android** - Outils d’installation et de lancement de l’application Android de démonstration. Créez un site basé sur la variable **Application monopage WKND** pour renseigner cette page. Utilisation à partir d’un appareil Android, d’un émulateur ou de Bluestacks.
* **Préférences utilisateur** - Désactivez les boîtes de dialogue contextuelles de tutoriel.
* **Configuration de GraphQL** - Configurez rapidement le point d’entrée GraphQL global.

## Suppression de sites et de modèles de démonstration {#deleting}

Après avoir testé un ensemble de fonctionnalités d’AEM, vous n’avez peut-être plus besoin de votre site de démonstration ni même du modèle sur lequel il est basé. Il est facile de supprimer les sites de démonstration et les modèles de site.

1. Accédez au **Utilitaires de démonstration de référence** et appuyez ou cliquez sur **Supprimer des sites**.

   ![Suppression de sites](assets/delete-sites.png)

1. Les sites disponibles sont présentés dans une liste. Vérifiez le ou les sites que vous souhaitez supprimer, puis appuyez ou cliquez sur **Supprimer**.

   >[!CAUTION]
   >
   >La suppression de site et de modèle est une action destructrice qui ne peut pas être annulée une fois lancée.

1. Confirmez la suppression du site dans la boîte de dialogue.

   ![Confirmer la suppression du site](assets/confirm-site-delete.png)

1. AEM supprime le ou les sites sélectionnés et affiche leur progression lorsque la variable **Supprimer** précédemment.

   ![Supprimer la progression](assets/delete-progress.png)

Le site est maintenant supprimé.

Vous pouvez supprimer des modèles de la même manière sous l’en-tête . **Suppression de modèles de site** dans le **Utilitaires de démonstration de référence**.

>[!CAUTION]
>
>Avant de supprimer un modèle de site, assurez-vous que tous les sites qui y font référence sont également supprimés.

## Fin du Parcours ? {#end-of-journey}

Félicitations ! Vous avez terminé le parcours du module complémentaire de démonstration de référence AEM ! Vous devez maintenant :

* posséder une compréhension de base de Cloud Manager et comprendre comment les pipelines diffusent du contenu et une configuration à AEM.
* Découvrez comment utiliser Cloud Manager pour créer un programme.
* Découvrez comment activer le module complémentaire de démonstration de référence pour le nouveau programme et être en mesure d’exécuter un pipeline pour déployer le contenu du module complémentaire.
* Découvrez comment accéder à l’environnement de création AEM pour créer un site à partir d’un modèle.
* Découvrez comment accéder aux utilitaires de démonstration en libre-service.
* Découvrez comment supprimer un site ou un modèle de démonstration existant.

Vous êtes maintenant prêt à explorer les fonctionnalités d’AEM à l’aide de vos propres sites de démonstration. Cependant, AEM est un outil puissant et de nombreuses autres options sont disponibles. Extrayez certaines des ressources supplémentaires disponibles dans le [Section Ressources supplémentaires](#additional-resources) pour en savoir plus sur les fonctionnalités que vous avez vues dans ce parcours.

## Ressources supplémentaires {#additional-resources}

* [Documentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Si vous souhaitez plus de détails sur les fonctionnalités de Cloud Manager, vous pouvez consulter directement la documentation technique détaillée.
* [Créer un site](/help/sites-cloud/administering/site-creation/create-site.md) - Découvrez comment utiliser AEM pour créer un site à l’aide de modèles de site afin de définir le style et la structure de votre site.
* [AEM les conventions d’appellation des pages.](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#page-name-restrictions-and-best-practices) - Reportez-vous à cette page pour comprendre les conventions d’organisation AEM pages.
* [AEM Manipulation de base](/help/sites-cloud/authoring/getting-started/basic-handling.md) - Explorez ce document si vous découvrez que vous AEM les concepts de base tels que la navigation et l’organisation des consoles.
* [AEM documentation technique as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr) - Si vous maîtrisez déjà les AEM, vous pouvez consulter directement les documents techniques détaillés.
* [Modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md) - Si vous souhaitez en savoir plus sur la structure des modèles de site et leur utilisation pour créer des sites, consultez ce document.
