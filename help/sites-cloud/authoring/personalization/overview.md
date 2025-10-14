---
title: Personnalisation et ciblage de contenu
description: Découvrez comment créer du contenu personnalisé et ciblé avec AEM
exl-id: b9b5dbf6-d491-48a6-99b1-19bc1b651b8c
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 89%

---


# Personnalisation et ciblage de contenu {#personalization-and-content-targeting}

La personnalisation du contenu web que vous fournissez aux client(e)s implique de personnaliser ces expériences en fonction de leurs intérêts et besoins. Vous pouvez faire ceci en fonction des informations que vous avez à leur sujet ; par exemple, le résumé des achats, l’âge, le sexe, la zone géographique, etc.

Avec Adobe Experience Manager as a Cloud Service (AEM), vous pouvez créer une sélection de contenu, puis spécifier les audiences (groupes d’utilisateurs finaux) qui voient chaque expérience individuelle. Cela signifie que vous ciblez vos expériences personnalisées vers des audiences spécifiques.

Lorsque votre lecteur ou lectrice est en ligne, votre moteur de ciblage examine les informations disponibles sur l’utilisateur final et les compare aux définitions de l’expérience. Le moteur *« décide »* alors de l’expérience personnalisée à afficher.

AEM fournit un framework d’outils pour :

* La création de contenu ciblé, adapté à un large éventail d’audiences, en fonction des informations disponibles sur les client(e)s.
* La définition de règles utilisées pour résoudre les informations utilisateur connues par rapport à une définition d’audience.
* La configuration de vos pages pour présenter des expériences personnalisées ciblées ; pour rendre le contenu spécifique applicable à l’utilisateur final actuel.

L’aperçu suivant présente certains des termes utilisés pour la personnalisation dans AEM as a Cloud Service, suivis d’un ordre d’action recommandé.

## Expérience {#experience}

Une expérience est un contenu que vous souhaitez présenter à vos utilisateurs finaux.

## Expérience personnalisée {#personalized-experience}

Une expérience personnalisée est une expérience présentée à une audience limitée. L’audience est définie par vous et le contenu n’est affiché que lorsque les informations connues sur l’utilisateur final actuel correspondent à cette définition d’audience.

Lors de la création de pages, vous définissez plusieurs expériences, chaque expérience se résolvant sur une ou plusieurs audiences. Si aucune audience n’est résolue, l’expérience par défaut s’affiche.

### Offre {#offer}

Une offre est une expérience personnalisée, souvent disponible pendant une période limitée.

Par exemple, une page d’un exemple de site web peut utiliser des offres comme image de teaser qui apparaît en haut de la page. Une personne de plus de 30 ans et une personne de moins de 30 ans peuvent voir différentes offres comme teaser d’expérience.

## Audience {#audience}

Une audience est un groupe d’utilisateurs finaux que vous souhaitez cibler avec un contenu personnalisé. Lorsqu’un visiteur ou une visiteuse ouvre une page web, la logique de page détermine l’audience à laquelle il ou elle appartient en fonction d’informations connues. Selon cette évaluation, AEM affiche le contenu que vous avez créé pour cette audience.

Les audiences sont basées sur des segments marketing. Ils sont créés dans AEM ou dans Adobe Target ; vous pouvez créer des audiences Adobe Target directement dans AEM, à l’aide de la console Audiences.

### Segment {#segment}

Dans AEM ContextHub, une audience est définie sous la forme d’un segment, selon des règles (conditions). Ils sont ensuite résolus pour effectuer le rendu du contenu requis.

## Activité {#activity}

Une activité :

* définit le mappage d’une audience spécifique (segment) avec une expérience spécifique
* définit la période pendant laquelle le ciblage est appliqué
* identifie le [moteur de ciblage](#targeting-engine) que vos pages utilisent

L’activité peut être soit une activité de personnalisation, soit une activité de test A/B (dans le cas du workflow de personnalisation AEM et Adobe Target).

Par exemple, une activité définit les expériences destinées à deux audiences distinctes : les personnes âgées de moins de 30 ans et les personnes âgées de plus de 30 ans. Une page de votre site web peut alors afficher différents produits pour chaque audience.

Ou, comme autre exemple, votre catalogue de produits peut inclure des teasers qui mettent l’accent sur les produits saisonniers. Ainsi, une activité de sports d’été peut définir les audiences que les teasers ciblent pendant les mois d’été.

Utilisez la [console Activités](/help/sites-cloud/authoring/personalization/activities.md) pour créer et gérer les activités de vos [marques](#brand). Vous pouvez également créer des activités à mesure que vous créez votre [contenu ciblé](/help/sites-cloud/authoring/personalization/targeted-content.md) à l’aide du [mode Ciblage](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode).

### Marque {#brand}

Une marque contient une sélection d’activités et de domaines marketing.

Lorsque vous créez une marque à l’aide de la console Activités, elle apparaît également dans la console Offres.

### Domaine {#area}

Un domaine est une subdivision d’une marque.

## Mode Ciblage {#targeting-mode}

Lors de la création, il s’agit du mode de modification utilisé pour activer et configurer les composants à personnaliser.

Vous pouvez [créer du contenu ciblé](/help/sites-cloud/authoring/personalization/targeted-content.md) à l’aide du mode Ciblage d’AEM. Le mode Ciblage et le composant Cible fournissent des outils permettant de créer du contenu pour les expériences de vos activités de marketing.

## Fragment d’expérience {#experience-fragments}

Un ensemble groupé de composants qui constituent une expérience.

Les [fragments d’expérience](/help/sites-cloud/authoring/fragments/content-fragments.md#personalization-experience-fragment) sont constitués de contenu et d’informations (mise en forme, etc.) pour créer une expérience ; ils peuvent être utilisés directement lors de la création de pages. Ils peuvent être considérés comme un sous-ensemble d’une page AEM. Ils permettent aux auteurs et aux autrices de contenu de réutiliser du contenu sur plusieurs canaux, y compris les pages Sites et les systèmes tiers.

À titre d’exemple de personnalisation, un titre, une image, une description et un bouton d’appel à l’action peuvent être combinés pour former une expérience de teaser. L’utilisation des Fragments d’expérience est un élément clé de l’utilisation de la personnalisation d’Adobe Target.

## Moteur de ciblage {#targeting-engine}

Le moteur de ciblage est le mécanisme qui résout la logique du contenu ciblé. Les [activités](/help/sites-cloud/authoring/personalization/activities.md) sont configurées pour utiliser l’un des deux moteurs de ciblage disponibles : AEM et Adobe Target.

Le moteur de ciblage est la plateforme ou le mécanisme qui décide du système de personnalisation à utiliser.

Actuellement, AEM peut utiliser les systèmes suivants :

* [AEM ContextHub](#aem-contexthub) (AEM standard)
* le moteur de personnalisation [Adobe Target](#adobe-target)

>[!CAUTION]
>
>Une page AEM unique ne peut pas utiliser les deux moteurs en même temps.
>
>Vous pouvez utiliser les deux moteurs sur des pages distinctes du même site.

### AEM ContextHub {#aem-contexthub}

AEM fournit le moteur de ciblage intégré [ContextHub](/help/implementing/developing/personalization/contexthub.md) qui traite les requêtes de page et détermine le contenu à afficher. Lorsque vous utilisez le moteur de ciblage AEM, vous êtes limité(e) aux segments créés dans AEM pour définir les audiences de vos expériences.

### Adobe Target {#adobe-target}

Avec le moteur de ciblage [Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md), les informations recueillies suite aux visites de page font l’objet d’un suivi dans Adobe Target.

* Avec ce moteur de ciblage, vous utilisez les segments que vous importez à partir d’Adobe Target pour définir les audiences de vos expériences.
* Les activités qui utilisent le moteur Adobe Target sont [synchronisées avec Target](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target).

Vous pouvez utiliser ce moteur lorsque vous avez [intégré Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md).

## Configurer votre contenu personnalisé {#how-to-setup-personalized-content}

Plusieurs étapes et définitions sont nécessaires pour diffuser votre contenu personnalisé :

1. Configurez votre moteur de ciblage en effectuant l’une des opérations suivantes :

   1. Configuration de [ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md)
   1. Intégration avec [Adobe Target &#x200B;](/help/sites-cloud/integrating/integrating-adobe-target.md)

1. Configurer les audiences.

   1. Selon votre moteur de ciblage, définissez l’[audience cible](https://experienceleague.adobe.com/docs/target/using/audiences/target.html?lang=fr) ou le [segment ContextHub](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md), ainsi que les règles.

1. Créer votre [Marque et vos activités](/help/sites-cloud/authoring/personalization/activities.md).

1. Créez la gamme d’expériences que vous souhaitez afficher aux différentes audiences.

1. Personnalisez ces expériences en les [ciblant](/help/sites-cloud/authoring/personalization/targeted-content.md) à des audiences spécifiques (segments).