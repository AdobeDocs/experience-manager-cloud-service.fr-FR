---
title: Présenter l’installation du module complémentaire de démonstration de référence
description: Découvrez Cloud Manager et comment il est utilisé pour installer le module complémentaire.
exl-id: 9418aac6-a8c4-43f7-b329-b02149fe2d53
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 100%

---

# Présenter l’installation du module complémentaire de démonstration de référence {#understand-installation}

Découvrez Cloud Manager et comment il est utilisé pour installer le module complémentaire.

>[!TIP]
>
>Si vous connaissez déjà Cloud Manager ou si vous souhaitez passer directement à la configuration et à l’utilisation du module complémentaire, vous pouvez passer à [Créer un programme et un pipeline](create-program.md)
>
>Si vous souhaitez découvrir comment Cloud Manager et AEM fonctionnent ensemble pour créer vos environnements de démonstration ainsi que pour configurer et utiliser les vôtres, poursuivez la lecture du présent document.

## Objectif {#objective}

Ce document vous aide à comprendre le fonctionnement du processus d’installation du module complémentaire de démonstration de référence, en illustrant le fonctionnement des différents éléments. Après avoir lu ce document, vous devriez :

* Posséder une compréhension de base de Cloud Manager.
* Découvrez comment les pipelines diffusent du contenu et une configuration à AEM.
* Savoir comment les modèles peuvent créer de nouveaux sites préremplis avec du contenu de démonstration en quelques clics seulement.

Ce document se concentre sur la compréhension de ces éléments fondamentaux du module complémentaire de démonstration de référence d’AEM avant de passer à l’étape suivante du parcours, où vous commencez l’installation.

Bien qu’il soit recommandé de procéder étape par étape, si vous avez déjà de l’expérience avec Cloud Manager ou si vous souhaitez passer directement à la configuration et à l’utilisation du module complémentaire, vous pouvez passer à [Créer un programme et un pipeline](create-program.md).

## Rôle responsable {#responsible-role}

Ce parcours s’applique à un administrateur système qui est membre du rôle de **Propriétaire de l’entreprise** dans Cloud Manager pour votre organisation.

## Exigences et conditions préalables {#requirements-prerequisites}

Un minimum de conditions sont requises pour découvrir et commencer à utiliser le module complémentaire de démonstration de référence.

### Connaissances {#knowledge}

* Connaissances de base de Cloud Manager

### Outils {#tools}

* Être membre du rôle de **Propriétaire de l’entreprise** dans Cloud Manager pour votre organisation

## Présentation de Cloud Manager {#cloud-manager}

Cloud Manager est un composant essentiel d’AEM as a Cloud Service et sert de point d’entrée unique pour la plateforme.

Cloud Manager est utilisé pour administrer les ressources cloud qui prennent en charge vos projets AEM, y compris les environnements et les outils nécessaires. Pour les besoins de ce parcours, une compréhension complète de Cloud Manager n’est pas nécessaire. Cependant, vous devez connaître certains concepts de base.

>[!TIP]
>
>Si vous souhaitez en savoir plus sur Cloud Manager, reportez-vous à la section [Ressources supplémentaires](#additional-resources) de cet article qui contient des liens pour des informations complémentaires.

### Programmes {#programs}

Lorsque vous vous connectez à Cloud Manager, vous avez accès à un ou plusieurs **programmes**. Un programme peut être défini de différentes manières, mais il est plus facile de le considérer comme étant associé aux sites et expériences associés à une identité de marque.

Si vous vous connectez à Cloud Manager en représentant **Entreprises de voyage et d’aventure WKND**, vous pouvez créer un programme **La vie nocturne de WKND** et un programme **Projets d’arrière-cour de WKND**. Ces deux programmes auraient des environnements AEM pour gérer leurs sites associés.

### Sandboxes {#sandboxes}

Les programmes peuvent être des programmes d’exploitation ou des programmes sandbox.

* **Un programme d’exploitation** est créé pour permettre éventuellement un trafic réel lorsque votre programme est prêt à être lancé.
* **Un programme sandbox** est créé pour la formation, l’exécution de démonstrations, l’activation, les POC, etc. et n’est pas destiné au trafic réel.

Pour installer le module complémentaire de démonstration de référence d’AEM, vous devez créer un nouveau programme sandbox.

>[!NOTE]
>
>Le module complémentaire de démonstration de référence d’AEM n’est disponible que dans les programmes Sandbox.

## Flux d’installation et d’utilisation {#installation-flow}

Maintenant que vous comprenez certains concepts fondamentaux de Cloud Manager, l’installation du module complémentaire de démonstration de référence d’AEM est conceptuellement simple.

1. Connectez-vous à Cloud Manager.
1. Créez un nouveau programme sandbox d’AEM, en activant le module complémentaire de démonstration de référence d’AEM comme une option pour le programme.
1. Le contenu et la configuration de la démonstration sont déployés dans le programme. Le contenu de la démonstration contient :
   * Des modèles de site utilisés pour créer divers sites AEM à l’aide des fonctionnalités d’AEM, préremplis avec des exemples de bonnes pratiques.
   * Des outils de configuration pour gérer votre contenu de démonstration.
1. Connectez-vous à AEM dans votre nouveau programme sandbox, utilisez l’outil de création rapide de sites et créez des sites de démonstration en fonction des modèles.
1. Utilisez les outils de configuration pour gérer ces sites de démonstration et ces modèles, y compris les supprimer lorsque cela n’est plus nécessaire.

## Modèles de site AEM {#site-templates}

Les modèles de site AEM sont des packages qui contiennent du contenu et une structure prédéfinis pour un site. Les modèles de site peuvent être personnalisés pour répondre aux besoins de projets spécifiques. Ainsi, lorsque les administrateurs AEM créent de nouveaux sites, ils peuvent choisir parmi les modèles qui s&#39;appliquent à leurs cas professionnels.

Le Module complémentaire de démonstration de référence d’AEM comprend plusieurs modèles pour divers besoins de test et de démonstration. Une fois que vous avez créé votre programme et déployé le pipeline pour installer le module complémentaire, vous pouvez vous connecter à AEM et créer des sites basés sur de nombreux modèles de démonstration.

## Prochaines étapes {#what-is-next}

Maintenant que vous avez terminé cette partie du parcours du module complémentaire de démonstration de référence d’AEM, vous devez :

* Posséder une compréhension de base de Cloud Manager.
* Découvrez comment les pipelines diffusent du contenu et une configuration à AEM.
* Savoir comment les modèles peuvent créer de nouveaux sites préremplis avec du contenu de démonstration en quelques clics seulement.

Tirez parti de ces connaissances et poursuivez votre parcours de création rapide de site AEM en consultant le document [Création d’un programme et d’un pipeline,](create-program.md) où vous apprendrez à configurer un nouveau programme et pipeline pour déployer le module complémentaire.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de création de site rapide en consultant le document [Création d’un programme et d’un pipeline,](create-program.md) vous trouverez ci-après quelques ressources facultatives supplémentaires pour approfondir un certain nombre de concepts mentionnés dans ce document, mais non obligatoires pour poursuivre le parcours.

* [Présentation des programmes et des types de programmes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/programs/program-types.html?lang=fr) - Commencez ici pour comprendre les différences entre les programmes en direct et les programmes Sandbox.
* [Modèles de site](/help/sites-cloud/administering/site-creation/site-templates.md) - Si vous souhaitez en savoir plus sur la structure des modèles de site et leur utilisation pour créer des sites, consultez ce document.
* [Documentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=fr) - Pour obtenir plus de détails sur les fonctionnalités de Cloud Manager, vous pouvez consulter directement la documentation technique détaillée.
