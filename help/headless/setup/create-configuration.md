---
title: Création d’une configuration - Configuration découplée
description: Créez une configuration comme première étape de prise en main d’AEM as a Cloud Service en mode découplé.
exl-id: 48801599-f279-4e55-8033-9c418d2af5bb
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 38a4bf89e099432163163e90e08aa0f47407724f
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 68%

---

# Création d’une configuration - Configuration découplée {#create-configuration}

Pour commencer à utiliser le découplage dans AEM as a Cloud Service, vous devez créer une configuration.

## Qu’est-ce qu’une configuration ?  {#what-is-a-configuration}

L’explorateur de configurations fournit une API de configuration générique, une structure de contenu et un mécanisme de résolution pour les configurations dans AEM.

Dans le contexte d’une gestion de contenu découplée dans AEM, considérez une configuration comme un espace de travail dans AEM où vous pouvez créer vos modèles de contenu, qui définissent la structure de votre futur contenu et des fragments de contenu. Vous pouvez avoir plusieurs configurations pour séparer ces modèles.

Si vous connaissez les modèles de page [&#x200B; dans une implémentation AEM full stack](/help/sites-cloud/authoring/page-editor/templates.md), l’utilisation des configurations pour la gestion des modèles de contenu est similaire.

## Création d’une configuration {#how-to-create-a-configuration}

Un administrateur n’a besoin de créer une configuration qu’une seule fois, ou très rarement lorsqu’un nouvel espace de travail est nécessaire pour organiser vos modèles de contenu. Pour les besoins de ce guide de prise en main, il suffit de créer une configuration.

Pour obtenir des détails détaillés, voir [Activation de la fonctionnalité de fragment de contenu dans l’explorateur de configurations](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser).

>[!NOTE]
>
>Des options de configuration en plus des **Modèles de fragments de contenu** et des **Requêtes persistantes GraphQL** peuvent être nécessaires en fonction de vos exigences d’implémentation.

## Étapes suivantes {#next-steps}

Cette configuration vous permet maintenant de passer à la deuxième partie du guide de prise en main et de [créer des modèles de fragment de contenu](create-content-model.md).

>[!TIP]
>
>Pour plus d’informations sur l’explorateur de configurations, consultez la [documentation relative à l’explorateur de configurations](/help/implementing/developing/introduction/configurations.md).
