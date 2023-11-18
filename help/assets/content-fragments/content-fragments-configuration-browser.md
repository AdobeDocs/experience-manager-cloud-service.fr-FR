---
title: Fragments de contenu - Navigateur de configurations (Ressources - Fragments de contenu)
description: Découvrez comment activer certaines fonctionnalités de fragments de contenu dans le navigateur de configurations.
exl-id: 9fc911de-1d33-4811-8f58-ea21ce94bedb
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 99%

---

# Fragments de contenu - Explorateur de configurations{#content-fragments-configuration-browser}

Découvrez comment activer certaines fonctionnalités de fragments de contenu dans l’explorateur de configurations afin d’utiliser les puissantes fonctionnalités de diffusion en mode découplé d’AEM.

## Activer la fonctionnalité de fragments de contenu pour votre instance {#enable-content-fragment-functionality-instance}

Avant d’utiliser les fragments de contenu, vous devez utiliser l’**explorateur de configurations** pour activer les éléments suivants :

* **Modèles de fragment de contenu** – obligatoire
* **Requêtes persistantes GraphQL** – facultatif

>[!CAUTION]
>
>Si vous n’activez pas les **modèles de fragment de contenu** :
>
>* l’option **Créer** n’est pas disponible pour la création de modèles.
>* vous ne pouvez pas [sélectionner la configuration Sites pour créer le point d’entrée associé](/help/headless/graphql-api/graphql-endpoint.md).

Pour activer la fonctionnalité de fragment de contenu, procédez comme suit :

* activer l’utilisation de la fonctionnalité de fragments de contenu par le biais de l’explorateur de configurations ;
* appliquer la configuration à votre dossier de ressources

### Activation de la fonctionnalité de fragments de contenu dans l’explorateur de configurations {#enable-content-fragment-functionality-in-configuration-browser}

Pour utiliser certaines [fonctionnalités de fragments de contenu](#creating-a-content-fragment-model), vous **devez** d’abord les activer par le biais de l’**explorateur de configurations** :

>[!NOTE]
>
>Voir [Explorateur de configuration](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>Les [sous-configurations](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (une configuration imbriquée dans une autre) sont entièrement prises en charge pour une utilisation avec les fragments de contenu, les modèles de fragment de contenu et les requêtes GraphQL.
>
>Il faut juste noter que :
>
>
>* Après la création de modèles dans une sous-configuration, il N’est PAS possible de déplacer ou de copier le modèle vers une autre sous-configuration.
>
>* Un point d’entrée GraphQL est (toujours) basé sur une configuration parent (racine).
>
>* Les requêtes persistantes sont (toujours) enregistrées en fonction de la configuration parent (racine).


1. Accédez à **Outils**, **Général**, puis ouvrez l’**Explorateur de configurations**.

1. Utilisez le bouton **Créer** pour ouvrir la boîte de dialogue.

   1. Spécifiez un **Titre**.
   1. Le **nom** devient le nom du nœud dans le référentiel.
      * Il sera généré automatiquement en fonction du titre et ajusté selon les [conventions de nommage AEM](/help/implementing/developing/introduction/naming-conventions.md).
      * Vous pouvez l’ajuster si nécessaire.
   1. Pour activer leur utilisation, sélectionnez
      * **Modèles de fragment de contenu**
      * **Requêtes persistantes GraphQL**

      ![Définir la configuration](assets/cfm-conf-01.png)

1. Sélectionnez **Créer** pour enregistrer la définition.

<!-- 1. Select the location appropriate to your website. -->

### Application de la configuration à votre dossier de ressources {#apply-the-configuration-to-your-assets-folder}

Lorsque la configuration **globale** est activée pour la fonctionnalité de fragments de contenu, elle s’applique à tout dossier de ressources.

Pour utiliser d’autres configurations (c.-à-d. avec une exclusion globale) avec un dossier de ressources comparable, vous devez définir la connexion. Pour ce faire, sélectionnez la **configuration** appropriée dans l’onglet **services cloud** des **propriétés du dossier** du dossier concerné.

![Appliquer la configuration](assets/cfm-conf-02.png)
