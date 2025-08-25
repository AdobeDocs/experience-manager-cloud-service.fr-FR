---
title: Créer une communication interactive
description: Créez des communications personnalisées basées sur les données. Explorez les fonctionnalités clés, les étapes d’intégration et les cas d’utilisation réels à l’aide de guides et de tutoriels.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: 5dd94d22a2a1a2ddbfd7dee44e93e6ea0c4b7ad9
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 2%

---


# Créer une communication interactive

La communication interactive vous permet de créer, de gérer et de diffuser des communications personnalisées et interactives, notamment le service client, la facturation, les documents d’intégration, les lettres d’offre, les mises à jour de compte, etc. Il est conçu pour prendre en charge tout scénario où un contenu dynamique et spécifique à l’utilisateur améliore l’expérience de communication entre les secteurs d’activité.

Imaginez que vous ayez besoin d’envoyer un relevé bancaire, une police d’assurance ou une facture de services publics à des milliers de clients. Chacune a la même disposition, mais des données personnalisées. La communication interactive (IC) rend cela possible de manière efficace.

![Rechercher un document IC](/help/forms/interactive-communication/assets/Picture1.png)

La production manuelle de ces documents peut prendre du temps et entraîne souvent des incohérences, en particulier lorsque la personnalisation et l’intégration des données sont requises. Avec l’éditeur de communication interactive, les utilisateurs et utilisatrices peuvent rationaliser le processus de création d’une communication interactive.

## Prérequis

* [Assurez-vous que l’auteur est membre du groupe forms-users](/help/forms/setup-forms-cloud-service.md#configure-users)

## Créer une communication interactive

Choisissez parmi différents scénarios pour créer une communication interactive, en fonction du niveau de réutilisation et d’intégration de données requis :

+++ Créer une communication interactive vierge

La création d’une communication interactive vierge vous permet de commencer à zéro, ce qui est idéal lorsque vous souhaitez un contrôle total de la disposition, de la structure et de la logique.
Étapes à suivre :

1. Ouvrez votre instance as a Cloud Service **Adobe Experience Manager (AEM) Forms**.
1. Accédez à **Forms > Forms et documents**.
1. Cliquez sur **Créer > Communication interactive**.

   ![Rechercher un document IC](/help/forms/interactive-communication/assets/comm.png)

1. Dans l’écran de création, laissez le champ **Modèle** vide.

   ![Rechercher un document IC](/help/forms/interactive-communication/assets/create-ic-document.png)

1. Renseignez d’autres détails tels que le titre, le nom, l’auteur, etc.
1. Cliquez sur **Créer** pour accéder à l’interface utilisateur de l’éditeur de communication interactive et commencer la conception.
1. Cela ouvre l’éditeur d’IC, où vous pouvez commencer à concevoir votre communication.
+++

+++ Créer une communication interactive basée sur un modèle

L’utilisation d’un modèle permet d’accélérer la conception en réutilisant des éléments de disposition cohérents tels que des en-têtes, des pieds de page, des logos ou une mise en forme standard.
Les modèles garantissent la cohérence de la marque et gagnent du temps pour les types de communication couramment utilisés. Effectuez les étapes suivantes :

1. Ouvrez l’instance AEM Forms as a Cloud Service.
1. Accédez à **Forms > Forms et documents**, puis cliquez sur **Créer > Communication interactive**.
1. Dans le formulaire de création, **sélectionnez** un modèle activé dans la liste déroulante.
1. Renseignez d’autres détails tels que le titre, le nom, l’auteur, etc.
1. Cliquez sur **Créer** pour concevoir votre communication avec la structure de modèle sélectionnée.
1. Cela ouvre l’éditeur d’IC, où vous pouvez commencer à concevoir votre communication.
+++

+++ Créer une communication interactive avec des données interactives

Les communications avec interactions de données personnalisent automatiquement le contenu à l’aide des données principales.
Idéal pour les relevés, factures ou avis dont la structure reste constante, mais dont les données varient selon le destinataire. Étapes à suivre :

1. Ouvrez l’instance AEM Forms as a Cloud Service.
1. Accédez à **Forms > Forms et documents**, puis cliquez sur **Créer > Communication interactive**.
1. Dans le champ **Modèle de données de formulaire**, liez votre **FDM (modèle de données de formulaire)** prédéfini.
1. Renseignez d’autres détails tels que le titre, le nom, l’auteur, etc.
1. Utilisez le **modèle de données** à l’intérieur de l’éditeur pour lier les champs aux données dynamiques (par exemple, nom du client, solde, numéro de compte).
1. Utilisez les **zones de contenu** sous-formulaires et **fragments** pour structurer et répéter les données si nécessaire.
1. Prévisualisez à l’aide de la prévisualisation **PDF** et finalisez la communication pour la diffusion.
1. Cela ouvre l’éditeur d’IC, où vous pouvez commencer à concevoir votre communication.

![Rechercher un document IC](/help/forms/interactive-communication/assets/ic-ui.png)
+++

Commencez à créer des communications interactives pour rationaliser vos workflows et offrir des expériences percutantes et spécifiques aux utilisateurs et utilisatrices.

## Étapes suivantes

[Créer un modèle de communication interactive](/help/forms/interactive-communication/create-interactive-communication-template.md)
[Créer un fragment de communication interactive](/help/forms/interactive-communication/create-interactive-communication-fragment.md)
