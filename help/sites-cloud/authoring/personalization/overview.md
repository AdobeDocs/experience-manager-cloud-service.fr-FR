---
title: Personnalisation et ciblage de contenu
description: Découvrez comment AEM peut créer du contenu personnalisé
translation-type: ht
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Personnalisation et ciblage de contenu {#personalization}

## Personnalisation et ciblage de contenu {#personalization-and-content-targeting}

AEM propose un ensemble d’outils permettant de créer du contenu ciblé et de présenter des expériences personnalisées.

## Mode Ciblage   {#targeting-mode}

[Créez du contenu ciblé à l’aide du mode Ciblage d’AEM. ](/help/sites-cloud/authoring/personalization/targeted-content.md) Le mode Ciblage et le composant Cible fournissent des outils permettant de créer du contenu pour les expériences de vos activités de marketing.

## Activités   {#activities}

Les activités définissent et organisent vos efforts de marketing. Les activités englobent les audiences ciblées et la période pendant laquelle le ciblage est appliqué.

Par exemple, votre catalogue de produits peut inclure des teasers qui mettent l’accent sur les produits saisonniers. L’activité de sports d’été définit les segments de marketing que les teasers ciblent pendant les mois d’été.

Les activités identifient également le [moteur de ciblage](#targeting-engine) que vos pages utilisent.

Utilisez la [console Activités](/help/sites-cloud/authoring/personalization/activities.md) pour créer et gérer les activités de vos marques. Vous pouvez également créer des activités tout en [créant du contenu ciblé](/help/sites-cloud/authoring/personalization/targeted-content.md).

## Expériences {#experiences}

Pour chaque activité, vous définissez une ou plusieurs expériences qui identifient les audiences que vous ciblez. AEM vous permet de contrôler le contenu qui constitue chaque expérience.

Les audiences sont basées sur les segments de marketing créés dans AEM ou Adobe Target. Lorsqu’un visiteur ouvre une page web, la logique de la page détermine l’audience à laquelle ce visiteur appartient et affiche le contenu que vous avez créé pour cette audience.

Par exemple, une activité définit les expériences destinées à deux audiences distinctes : les femmes âgées de moins de 30 ans et les femmes âgées de plus de 30 ans. La page réservée aux femmes sur un site web peut présenter différents produits pour chaque expérience.

Vous définissez des expériences pour une activité. Vous pouvez utiliser la [console Activités](/help/sites-cloud/authoring/personalization/activities.md#adding-editing-an-activity-using-the-activities-console) ou le [mode de ciblage](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode) pour ajouter des expériences à une activité.

## Offres   {#offers}

Une offre constitue du contenu qui s’affiche à un endroit d’une page pour créer une expérience. Utilisez différentes offres pour différentes expériences afin d’optimiser l’efficacité du contenu destiné à vos audiences.

Par exemple, la page pour les femmes de l’exemple peut utiliser des offres en tant qu’image de teaser apparaissant en haut de la page. L’offre utilisée en tant que teaser de l’expérience destinée aux femmes de plus de 30 ans n’est pas la même que celle utilisée pour les femmes de moins de 30 ans.

Utilisez la [console Offres](/help/sites-cloud/authoring/personalization/offers.md) pour créer des offres que vous pouvez utiliser dans plusieurs expériences. Créez des offres à utiliser une seule fois ou ajoutez des offres issues d’une bibliothèque d’offres lors de la [création de contenu ciblé](/help/sites-cloud/authoring/personalization/targeted-content.md).

## Moteur de ciblage   {#targeting-engine}

Le moteur de ciblage est le mécanisme sous-jacent à la logique du contenu ciblé. Les [activités](/help/sites-cloud/authoring/personalization/activities.md) sont configurées pour utiliser l’un des deux moteurs de ciblage disponibles : AEM et Adobe Target.

### AEM {#aem}

AEM fournit un moteur de ciblage intégré qui traite les requêtes de page et détermine le contenu à afficher. Lorsque vous utilisez le moteur de ciblage AEM, vous êtes limité aux segments créés dans AEM pour définir les audiences de vos expériences.

### Adobe Target {#adobe-target}

Avec le moteur de ciblage Adobe Target, les informations recueillies suite aux visites de page font l’objet d’un suivi dans Adobe Target.

* Avec ce moteur de ciblage, vous utilisez les segments que vous importez à partir d’Adobe Target pour définir les audiences de vos expériences.
* Les activités qui utilisent le moteur Adobe Target sont [synchronisées sur Target](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target).

Vous pouvez utiliser ce moteur lorsque vous avez intégré Adobe Target. <!--You can use this engine when you have [integrated with Adobe Target](/help/sites-administering/opt-in.md).-->
