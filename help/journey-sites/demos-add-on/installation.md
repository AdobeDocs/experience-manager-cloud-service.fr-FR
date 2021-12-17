---
title: Présentation de l’installation du module complémentaire de démonstration de référence
description: Découvrez Cloud Manager et comment il est utilisé pour installer le module complémentaire.
source-git-commit: 52d65251744ce0ae5cf7a7e0a45b39d8fe78f13a
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 1%

---


# Présentation de l’installation du module complémentaire de démonstration de référence {#understand-installation}

Découvrez Cloud Manager et comment il est utilisé pour installer le module complémentaire.

>[!TIP]
>
>Si vous connaissez déjà Cloud Manager ou que vous souhaitez accéder directement à la configuration et à l’utilisation du module complémentaire, vous pouvez passer à [Création d’un programme et d’un pipeline](create-program.md)
>
>Si vous souhaitez découvrir comment Cloud Manager et AEM fonctionnent ensemble pour créer vos environnements de démonstration, ainsi que comment configurer et utiliser les vôtres, continuez à lire le document en cours.

## Objectif {#objective}

Ce document vous aide à comprendre le fonctionnement du processus d’installation du module complémentaire de démonstration de référence, en illustrant le fonctionnement des différents éléments. Après l’avoir lu, vous devriez :

* posséder une compréhension de base de Cloud Manager.
* Découvrez comment les pipelines diffusent du contenu et une configuration à AEM.
* Découvrez comment les modèles peuvent créer des sites préremplis avec du contenu de démonstration en quelques clics seulement.

Ce document se concentre sur la compréhension de ces éléments fondamentaux du module complémentaire de démonstration de référence d’AEM avant de passer à l’étape suivante du parcours où vous commencez l’installation.

Bien qu’il soit recommandé de passer par cette étape parcours, si vous avez déjà l’expérience de Cloud Manager ou souhaitez passer directement à la configuration et à l’utilisation du module complémentaire, vous pouvez passer à [Création d’un programme et d’un pipeline](create-program.md)

## Rôle responsable {#responsible-role}

Ce parcours s’applique à un administrateur système qui est membre de la **Propriétaire de l’entreprise** rôle dans Cloud Manager pour votre organisation.

## Exigences et conditions préalables {#requirements-prerequisites}

Il existe des exigences minimales pour en savoir plus et commencer à utiliser le module complémentaire de démonstration de référence.

### Connaissances {#knowledge}

* Connaissances de base de Cloud Manager

### Outils {#tools}

* Être membre de **Propriétaire de l’entreprise** rôle dans Cloud Manager pour votre organisation

## Présentation de Cloud Manager {#cloud-manager}

Cloud Manager est un composant essentiel d’AEM as a Cloud Service et constitue le point d’entrée unique de la plateforme.

Cloud Manager est utilisé pour administrer les ressources cloud qui prennent en charge vos projets AEM, y compris les environnements et les outils nécessaires. Pour les besoins de ce parcours, une compréhension complète de Cloud Manager n’est pas nécessaire. Cependant, vous devez connaître certains concepts de base.

>[!TIP]
>
>Si vous souhaitez en savoir plus sur Cloud Manager, reportez-vous à la section [Ressources supplémentaires](#additional-resources) pour obtenir des liens vers d’autres informations.

### Programmes {#programs}

Lorsque vous vous connectez à Cloud Manager, vous avez accès à une ou plusieurs **programmes**. Un programme peut être défini de différentes manières, mais il est plus facile de le considérer comme associé aux sites et expériences associés à une seule identité de marque.

Si vous vous connectez à Cloud Manager en représentant **Entreprises de voyage et d’aventure WKND**, vous pouvez créer une **La vie nocturne de WKND** programme et un **Projets d’arrière-cour WKND** programme. Ces deux programmes auraient des environnements AEM pour gérer les sites associés.

### Environnements de test {#sandboxes}

Les programmes peuvent être des programmes de production ou des programmes Sandbox.

* **Un programme de production** est créé pour autoriser le trafic en direct lorsque votre programme est prêt à être mis en service.
* **Un programme d’environnement de test** est créé pour la formation, l’exécution de démonstrations, l’activation, les points ciblés, etc. et n’est pas destiné au trafic en direct.

Pour installer le module complémentaire de démonstration de référence d’AEM, vous devez créer un nouveau programme d’environnement de test.

>[!NOTE]
>
>Le module complémentaire de démonstration de référence d’AEM n’est disponible que dans les programmes Sandbox.

## Flux d’installation et d’utilisation {#installation-flow}

Maintenant que vous comprenez certains concepts fondamentaux de Cloud Manager, l’installation du module complémentaire de démonstration de référence d’AEM est conceptuellement simple.

1. Connectez-vous à Cloud Manager.
1. Créez un nouveau programme d’AEM d’environnement de test, en activant l’option du module complémentaire de démonstration de référence d’AEM pour le programme.
1. Le contenu et la configuration de la démonstration sont déployés dans le programme. Le contenu de démonstration contient :
   * Modèles de site utilisés pour créer divers sites d’AEM à l’aide des fonctionnalités d’AEM, prérenseignés avec des exemples de bonnes pratiques.
   * Outils de configuration pour gérer votre contenu de démonstration.
1. Connectez-vous à AEM dans votre nouveau programme Sandbox, utilisez l’outil de création rapide de site et créez des sites de démonstration en fonction des modèles.
1. Utilisez les outils de configuration pour gérer ces sites de démonstration et ces modèles, y compris les supprimer lorsque cela n’est plus nécessaire.

## AEM Modèles de site {#site-templates}

Les modèles de site AEM sont des modules qui contiennent du contenu et une structure prédéfinis pour un site. Les modèles de site peuvent être personnalisés pour répondre aux besoins de projets spécifiques. Ainsi, lorsque AEM administrateurs créent des sites, ils peuvent choisir parmi des modèles qui s’appliquent à leurs cas d’entreprise.

Le module complémentaire de démonstration de référence d’AEM comprend plusieurs modèles pour divers besoins de test et de démonstration. Une fois que vous avez créé votre programme et déployé le pipeline pour installer le module complémentaire, vous pouvez vous connecter à AEM et créer des sites basés sur de nombreux modèles de démonstration.

## Et après ? {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours du module complémentaire de démonstration de référence d’AEM, vous devez :

* posséder une compréhension de base de Cloud Manager.
* Découvrez comment les pipelines diffusent du contenu et une configuration à AEM.
* Découvrez comment les modèles peuvent créer des sites préremplis avec du contenu de démonstration en quelques clics seulement.

Tirez parti de ces connaissances et poursuivez votre parcours de création rapide de site AEM en consultant le document. [Création d’un programme et d’un pipeline,](create-program.md) où vous apprendrez à configurer un nouveau programme et pipeline pour déployer le module complémentaire.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de création de site rapide en consultant le document [Création d’un programme et d’un pipeline,](create-program.md) vous trouverez ci-dessous des ressources facultatives supplémentaires qui approfondissent certains concepts mentionnés dans ce document, mais qui ne sont pas nécessaires pour continuer sur le parcours.

* [Présentation des programmes et des types de programmes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/understand-program-types.html) - Commencez ici pour comprendre les différences entre les programmes en direct et les programmes Sandbox.
* [Modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md) - Si vous souhaitez en savoir plus sur la structure des modèles de site et leur utilisation pour créer des sites, consultez ce document.
* [Documentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Si vous souhaitez plus de détails sur les fonctionnalités de Cloud Manager, vous pouvez consulter directement la documentation technique détaillée.
