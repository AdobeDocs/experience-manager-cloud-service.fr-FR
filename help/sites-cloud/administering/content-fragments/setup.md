---
title: Fragments de contenu - Configuration
description: Découvrez comment activer les fonctionnalités de fragment de contenu et de GraphQL à utiliser avec AEM fonctionnalités de diffusion sans interface utilisateur et de création de pages.
feature: Content Fragments
role: Developer, Architect
exl-id: 3974d698-1e7d-4a5f-a6d5-cbf8d96b4095
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 39%

---

# Fragments de contenu - Configuration {#content-fragments-setup}

Les fragments de contenu as a Cloud Service Adobe Experience Manager (AEM) vous permettent de préparer le contenu prêt à être utilisé à plusieurs emplacements et sur plusieurs canaux. Idéal pour la diffusion sans interface utilisateur et la création de pages.

Pour activer votre instance pour la fonctionnalité de fragment de contenu, vous devez activer :

* **Modèles de fragment de contenu** – obligatoire

  >[!CAUTION]
  >
  >Si vous n’activez pas les **modèles de fragment de contenu** :
  >
  >* L’option **Créer** ne sera pas disponible pour la création de modèles.
  >* Vous ne pourrez pas [sélectionner la configuration Sites pour créer le point d’entrée](/help/headless/graphql-api/graphql-endpoint.md) associé.

* **Requêtes persistantes GraphQL** – facultatif

La configuration de votre instance est terminée :

* par [activation de la fonctionnalité dans l’explorateur de configurations](#enable-content-fragment-functionality-configuration-browser)
* ensuite [appliquer la configuration à vos dossiers Assets individuels](#apply-the-configuration-to-your-folder)

## Activation de la fonctionnalité de fragment de contenu dans l’explorateur de configurations {#enable-content-fragment-functionality-configuration-browser}

Pour utiliser la fonctionnalité Fragment de contenu des modèles de fragment de contenu et des requêtes persistantes GraphQL, vous **devez** d’abord les activer via le **navigateur de configuration** :

>[!NOTE]
>
>Pour plus d’informations, voir [Navigateur de configuration](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>Les [sous-configurations](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (une configuration imbriquée dans une autre) sont entièrement prises en charge pour une utilisation avec les fragments de contenu, les modèles de fragment de contenu et les requêtes GraphQL.
>
>Il faut juste noter que :
>
>* Après la création de modèles dans une sous-configuration, il N’est PAS possible de déplacer ou de copier le modèle vers une autre sous-configuration.
>
>* Un point d’entrée GraphQL est (toujours) basé sur une configuration parent (racine).
>
>* Les requêtes persistantes sont (toujours) enregistrées en fonction de la configuration parent (racine).

1. Accédez à **Outils**, **Général**, puis ouvrez l’**Explorateur de configurations**.

1. Utilisez le bouton **Créer** pour ouvrir la boîte de dialogue.

   1. Spécifiez un **Titre**.
   1. Lors de la création, le **nom** devient le nom du noeud dans le référentiel.
Vous pouvez saisir un nom. Si vous laissez le champ vide, il est généré automatiquement en fonction du titre, puis ajusté en fonction des [conventions d’appellation d’AEM](/help/implementing/developing/introduction/naming-conventions.md) ; vous pouvez ajuster le résultat si nécessaire.
   1. Pour activer leur utilisation, sélectionnez
      * **Modèles de fragment de contenu**
      * **Requêtes persistantes GraphQL**

      ![Définir la configuration](assets/cf-setup-create-conf.png)

1. Sélectionnez **Créer** pour enregistrer la définition.

## Appliquer la configuration à votre dossier {#apply-the-configuration-to-your-folder}

Lorsque la configuration **global** est activée pour la fonctionnalité de fragment de contenu, elle s’applique ensuite à tout dossier Assets, accessible par le biais de la console **Assets**.

Pour utiliser d’autres configurations (excluant donc global) avec un dossier Assets comparable, vous devez définir la connexion. Pour ce faire, sélectionnez la **configuration** appropriée dans l’onglet **Cloud Service** des **propriétés du dossier** du dossier approprié.

![Appliquer la configuration](assets/cf-setup-apply-conf.png)
