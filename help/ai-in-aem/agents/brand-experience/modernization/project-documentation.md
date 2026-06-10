---
title: Compétence en documentation de projet
description: Découvrez comment les compétences de documentation de l’agent de modernisation d’expérience peuvent vous aider à accélérer les transferts de projet.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 111cc47d-085f-4cf4-81bc-332e6a31bbeb
source-git-commit: c4f6edf58710aa03410e1828a2d8b61db0052255
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 1%

---

# Compétence en documentation de projet {#project-documentation}

Découvrez comment les compétences de documentation de l’agent de modernisation d’expérience peuvent vous aider à accélérer les transferts de projet.

## Accélération des transferts de projet {#project-handovers}

[L’agent de modernisation de l’expérience](/help/ai-in-aem/agents/brand-experience/modernization/overview.md) peut générer automatiquement des guides de documentation de projet pour les projets AEM Edge Delivery Services avec les éléments suivants :

* **Présentation du projet** - Explication de la configuration, de la structure et des conventions du projet, générées sans effort manuel
* **Organisation des modules et des composants** - Une documentation claire sur l’organisation des blocs, modules et composants et sur la manière dont ils sont liés les uns aux autres
* **Guides basés sur les rôles** - Documentation ciblée pour les auteurs, les développeurs et les administrateurs, afin que chaque membre de l’équipe obtienne exactement ce dont il a besoin

Cela simplifie les transferts de projet pour les projets AEM Edge Delivery Services.

## Conditions préalables {#prerequisites}

Assurez-vous des points suivants avant d’utiliser cette compétence.

* Votre projet doit être extrait de l’espace de travail dans la console.
* Vous devez disposer d’autorisations d’administrateur pour le projet pour lequel vous créez de la documentation.
* Les autorisations de l’agent doivent être autorisées dans la console.
   * Sélectionnez l’option **Autoriser LLM à accéder à admin.hlx.page en mon nom** [dans les paramètres de la console.](/help/ai-in-aem/agents/brand-experience/modernization/console.md#settings-view)
   * Si cette option n’est pas activée, l’agent génère la documentation en fonction de la base de code qui lui est accessible.

## Création de la documentation d&#39;un projet {#creating-documentation}

Une fois les conditions préalables remplies, il vous suffit de demander à l’agent de créer la documentation de votre projet.

1. Dans la conversation, demandez `Create documentation for this project`.
1. Indiquez le nom de l’organisation du projet si l’agent le demande.
1. L’agent vous demandera quelle documentation vous souhaitez créer. En règle générale, vous devez sélectionner **Tous**.

   ![Créer une documentation](assets/select-documentation.png)

1. Une fois créés, les guides sont placés dans votre espace de travail. Sélectionnez-en un pour afficher une description et cliquez sur le lien pour télécharger l’intégralité du PDF.

   ![Documentation créée](assets/documentation-created.png)

Vous pouvez enregistrer le PDF directement pour le fournir à vos équipes ou le charger dans le cadre du reste du contenu de la DA.

![&#x200B; Guide de l’administrateur &#x200B;](assets/admin-guide.png)

>[!NOTE]
>
>Si vous n’êtes pas autorisé à accéder à l’API d’administration Edge Delivery Services ou à l’option **Autoriser LLM à accéder à admin.hlx.page en mon nom** [dans les paramètres de la console.](/help/ai-in-aem/agents/brand-experience/modernization/console.md#settings-view) n’est pas activé, l’agent génère la documentation en fonction de la base de code qui lui est accessible.

## Résolution des problèmes {#troubleshooting}

Vous trouverez ci-dessous les messages d’erreur courants rencontrés lors de l’utilisation des compétences de documentation de projet et comment les résoudre.

### « Accès refusé » ou « Non autorisé » {#unauthorized}

* **Cause :** autorisations d’administrateur manquantes ou autorisations d’agent non activées
* **Solution :**
   1. Vérifiez que vous disposez d’un accès administrateur au projet
   1. Sélectionnez l’option **Autoriser LLM à accéder à admin.hlx.page en mon nom** [dans les paramètres de la console.](/help/ai-in-aem/agents/brand-experience/modernization/console.md#settings-view)

### « Projet Introuvable » {#not-found}

* **Cause :** référentiel non extrait dans l’espace de travail
* **Solution :**
   1. Extraire le référentiel du projet
   1. Vérifiez que vous vous trouvez dans l’espace de travail approprié.

### « Erreur de l’API de configuration » {#api-error}

* **Cause :** impossible d’accéder à l’API du service de configuration Edge Delivery Services
* **Solution :**
   1. Sélectionnez l’option **Autoriser LLM à accéder à admin.hlx.page en mon nom** [dans les paramètres de la console.](/help/ai-in-aem/agents/brand-experience/modernization/console.md#settings-view)
   1. Vérifiez votre connexion réseau/VPN
   1. Confirmer l’accès administrateur au projet
