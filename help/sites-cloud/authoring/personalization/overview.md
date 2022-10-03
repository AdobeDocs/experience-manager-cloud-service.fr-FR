---
title: Personnalisation et ciblage de contenu
description: Découvrez comment créer du contenu personnalisé et ciblé avec AEM
exl-id: b9b5dbf6-d491-48a6-99b1-19bc1b651b8c
source-git-commit: d2975ec84745f9520ead89588ab727af8e43b740
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 12%

---


# Personnalisation et ciblage de contenu {#personalization-and-content-targeting}

La personnalisation du contenu web que vous fournissez aux clients implique de personnaliser ces expériences en fonction de leurs intérêts et besoins. Vous pouvez le faire en fonction des informations que vous avez à leur sujet ; par exemple, résumé des achats, âge, sexe, zone géographique, etc.

Avec Adobe Experience Manager as a Cloud Service (AEM), vous pouvez créer une sélection de contenu, puis spécifier les audiences (groupes d’utilisateurs finaux) qui verront chaque expérience individuelle. Cela signifie que vous ciblez vos expériences personnalisées vers des audiences spécifiques.

Lorsque votre lecteur est en ligne, votre moteur de ciblage examine les informations disponibles sur l’utilisateur final et les compare aux définitions de l’expérience. Le moteur *&quot;décide&quot;* l’expérience personnalisée à afficher.

AEM fournit un ensemble d’outils pour :

* Création de contenu ciblé, adapté à un large éventail d’audiences, en fonction des informations sur les clients disponibles.
* Définition des règles utilisées pour résoudre les informations utilisateur connues par rapport à une définition d’audience.
* Configuration de vos pages pour présenter des expériences personnalisées ciblées ; pour rendre le contenu spécifique applicable à l’utilisateur final actuel.

L’aperçu suivant présente certains termes utilisés pour la personnalisation dans AEM as a Cloud Service, suivis d’un ordre d’action recommandé.

## Expérience {#experience}

Une expérience est un contenu que vous souhaitez présenter à vos utilisateurs finaux.

## Expérience personnalisée {#personalized-experience}

Une expérience personnalisée est une expérience présentée à une audience limitée. L’audience est définie par vous et le contenu n’est affiché que lorsque les informations connues sur l’utilisateur final actuel correspondent à cette définition d’audience.

Lors de la création de pages, vous définissez plusieurs expériences, chaque expérience se résolvant sur une ou plusieurs audiences. Si aucune audience n’est résolue, l’expérience par défaut s’affiche.

### Offre {#offer}

Une offre est une expérience personnalisée, souvent disponible pendant une période limitée.

Par exemple, une page d’un exemple de site web peut utiliser des offres comme image de teaser qui apparaît en haut de la page. Une personne de plus de 30 ans et une personne de moins de 30 ans verront différentes offres comme teaser d’expérience.

## Public {#audience}

Une audience est un groupe d’utilisateurs finaux que vous souhaitez cibler avec du contenu personnalisé. Lorsqu’un visiteur ouvre une page web, la logique de page détermine l’audience à laquelle il appartient en fonction d’informations connues. Selon cette évaluation, AEM affiche le contenu que vous avez créé pour cette audience.

Les audiences sont basées sur des segments marketing. Ils sont créés dans AEM ou dans Adobe Target ; vous pouvez créer des audiences Adobe Target directement dans AEM à l’aide de la console Audiences .

### Segment {#segment}

Dans AEM ContextHub, une audience est définie sous la forme d’un segment, selon des règles (conditions). Ils sont ensuite résolus pour effectuer le rendu du contenu requis.

## Activité {#activity}

Une activité :

* définit le mappage d’une audience (segment) spécifique avec une expérience spécifique ;
* définit la période pendant laquelle le ciblage est appliqué ;
* identifie la variable [moteur de ciblage](#targeting-engine) que vos pages utilisent

L’activité peut être soit une activité de personnalisation, soit une activité de test A/B (dans le cas du workflow de personnalisation AEM et Adobe Target).

Par exemple, une activité peut définir des expériences pour deux audiences distinctes : les personnes de plus de 30 ans et les personnes de moins de 30 ans. Une page de votre site web peut alors afficher différents produits pour chaque audience.

Ou, par exemple, votre catalogue de produits peut inclure des teasers qui mettent l’accent sur les produits saisonniers. Une activité de sports d’été peut définir les audiences que les teasers ciblent pendant les mois d’été.

Utilisez la variable [Console Activités](/help/sites-cloud/authoring/personalization/activities.md) pour créer et gérer les activités de votre [Marques](#brand). Vous pouvez également créer des activités à mesure que vous créez votre [contenu ciblé](/help/sites-cloud/authoring/personalization/targeted-content.md) avec [Mode Ciblage](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode).

### Brand Portal. {#brand}

Une marque contient une sélection d’activités et de domaines marketing.

Lorsque vous créez une marque à l’aide de la console Activités, elle apparaît également dans la console Offres.

### Domaine {#area}

Une zone est une subdivisions d’une marque.

## Mode Ciblage {#targeting-mode}

Lors de la création, il s’agit du mode de modification utilisé pour activer et configurer les composants à personnaliser.

Vous pouvez [Création de contenu ciblé](/help/sites-cloud/authoring/personalization/targeted-content.md) en utilisant le mode Ciblage d&#39;AEM. Le mode Ciblage et le composant Cible fournissent des outils permettant de créer du contenu pour les expériences de vos activités de marketing.

## Fragment d’expérience {#experience-fragments}

Ensemble groupé de composants qui constituent une expérience.

[Fragments d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#personalization-experience-fragment) sont constitués de contenu et d’informations (style, etc.) pour créer une expérience ; ils peuvent être utilisés directement lors de la création de pages. Ils peuvent être considérés comme un sous-ensemble d’une page AEM. Ils permettent aux auteurs de contenu de réutiliser du contenu sur plusieurs canaux, y compris les pages Sites et les systèmes tiers.

Pour un exemple de personnalisation, un titre, une image, une description et un bouton d’appel à l’action peuvent être combinés afin de former une expérience de teaser. L’utilisation des fragments d’expérience est un élément clé de l’utilisation de la personnalisation Adobe Target.

## Moteur de ciblage {#targeting-engine}

Le moteur de ciblage est le mécanisme qui résout la logique du contenu ciblé. Les [activités](/help/sites-cloud/authoring/personalization/activities.md) sont configurées pour utiliser l’un des deux moteurs de ciblage disponibles : AEM et Adobe Target.

Le moteur de ciblage est la plateforme ou le mécanisme qui décide du système de personnalisation à utiliser.

Actuellement, AEM peut utiliser :

* [AEM ContextHub](#aem-contexthub) (AEM standard)
* la valeur [Adobe Target](#adobe-target) moteur de personnalisation

>[!CAUTION]
>
>Une seule page AEM ne peut pas utiliser les deux moteurs en même temps.
>
>Vous pouvez utiliser les deux moteurs sur des pages distinctes du même site.

### AEM ContextHub {#aem-contexthub}

AEM fournit le moteur de ciblage intégré ContextHub qui traite les requêtes de page et détermine le contenu à afficher. Lorsque vous utilisez le moteur de ciblage AEM, vous êtes limité aux segments créés dans AEM pour définir les audiences de vos expériences.

### Adobe Target {#adobe-target}

Avec le moteur de ciblage Adobe Target, les informations recueillies suite aux visites de page font l’objet d’un suivi dans Adobe Target.

* Avec ce moteur de ciblage, vous utilisez les segments que vous importez à partir d’Adobe Target pour définir les audiences de vos expériences.
* Les activités qui utilisent le moteur Adobe Target sont [synchronisées sur Target](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target).

Vous pouvez utiliser ce moteur lorsque vous avez [intégré à Adobe Target](/help/sites-cloud/integrating/integration-adobe-target-ims.md).

## Comment configurer votre contenu personnalisé {#how-to-setup-personalized-content}

Plusieurs étapes et définitions sont nécessaires pour diffuser votre contenu personnalisé :

1. Intégrez AEM à votre moteur de ciblage.

1. Configurez les audiences.

   1. Selon votre moteur de ciblage, définissez l’audience ou le segment, ainsi que les règles.

1. Créez votre marque et vos activités.

1. Créez la sélection d’expériences que vous souhaitez afficher aux différentes audiences.

1. Personnalisez ces expériences en les ciblant sur des audiences spécifiques (segments).