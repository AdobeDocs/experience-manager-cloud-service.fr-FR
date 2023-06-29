---
title: Fragments de contenu - Navigateur de configurations
description: Découvrez comment activer la fonctionnalité Fragment de contenu et GraphQL dans l’explorateur de configurations afin d’utiliser AEM fonctionnalités de diffusion sans interface utilisateur.
feature: Content Fragments
role: User
exl-id: 55d442ae-ae06-4dfa-8e4e-b415385ccea5
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 34%

---

# Fragments de contenu – Explorateur de configurations{#content-fragments-configuration-browser}

Découvrez comment activer certaines fonctionnalités de fragments de contenu dans le navigateur de configurations.

## Activation de la fonctionnalité de fragments de contenu pour votre instance {#enable-content-fragment-functionality-instance}

Avant d’utiliser des fragments de contenu, vous devez utiliser la variable **Explorateur de configuration** pour activer :

* **Modèles de fragment de contenu** – obligatoire
* **Requêtes persistantes GraphQL** – facultatif

>[!CAUTION]
>
>Si vous n’activez pas les **modèles de fragment de contenu** :
>
>* la valeur **Créer** n’est pas disponible pour la création de modèles.
>* vous ne pouvez pas [sélectionnez la configuration Sites pour créer le point de terminaison associé.](/help/headless/graphql-api/graphql-endpoint.md).

Pour activer la fonctionnalité de fragment de contenu, procédez comme suit :

* activer l’utilisation de la fonctionnalité de fragments de contenu par le biais de l’explorateur de configurations ;
* appliquer la configuration à votre dossier de ressources.

### Activation de la fonctionnalité de fragments de contenu dans l’explorateur de configurations {#enable-content-fragment-functionality-in-configuration-browser}

Pour utiliser certains [Fonctionnalité de fragment de contenu](#creating-a-content-fragment-model), vous **must** Activez-les d’abord au moyen de l’option **Explorateur de configuration**:

>[!NOTE]
>
>Pour plus d’informations, voir [Explorateur de configuration](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>[Sous-configurations](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (configuration imbriquée dans une autre configuration) sont entièrement prises en charge pour une utilisation avec des fragments de contenu, des modèles de fragment de contenu et des requêtes GraphQL.
>
>Il faut juste noter que :
>
>
>* Après la création de modèles dans une sous-configuration, il n’est PAS possible de déplacer ou de copier le modèle dans une autre sous-configuration.
>
>* Un point de terminaison GraphQL est (toujours) basé sur une configuration parent (racine).
>
>* Les requêtes persistantes sont (toujours) enregistrées en fonction de la configuration parent (racine).


1. Accédez à **Outils**, **Général**, puis ouvrez l’**Explorateur de configurations**.

1. Utilisez le bouton **Créer** pour ouvrir la boîte de dialogue.

   1. Spécifiez un **Titre**.
   1. Le **Nom** devient le nom du noeud dans le référentiel.
      * Il est généré automatiquement en fonction du titre et ajusté en fonction des [Conventions de dénomination AEM](/help/implementing/developing/introduction/naming-conventions.md).
      * Vous pouvez l’ajuster si nécessaire.
   1. Pour activer leur utilisation, sélectionnez
      * **Modèles de fragment de contenu**
      * **Requêtes persistantes GraphQL**

      ![Définir la configuration](assets/cfm-conf-01.png)

1. Sélectionnez **Créer** pour enregistrer la définition.

<!-- 1. Select the location appropriate to your website. -->

### Appliquer la configuration à votre dossier {#apply-the-configuration-to-your-folder}

Lorsque la configuration **global** est activé pour la fonctionnalité de fragment de contenu, il s’applique à tout dossier de ressources accessible par le biais de la **Ressources** console.

Pour utiliser d’autres configurations (c’est-à-dire, à l’exclusion de global) avec un dossier de ressources comparable, vous devez définir la connexion. Cette connexion s’effectue en sélectionnant la **Configuration** dans le **Cloud Services** de l’onglet **Propriétés du dossier** du dossier approprié.

![Appliquer la configuration](assets/cfm-conf-02.png)
