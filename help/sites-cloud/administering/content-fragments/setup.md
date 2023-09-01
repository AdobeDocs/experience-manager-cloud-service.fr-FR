---
title: Fragments de contenu - Configuration
description: Découvrez comment activer la fonctionnalité Fragment de contenu et GraphQL pour utiliser AEM fonctionnalités de diffusion sans interface utilisateur.
feature: Content Fragments
role: Developer, Architect
source-git-commit: 676173813b6ea4defeafe25c95be9668d32aac38
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 27%

---


# Fragments de contenu - Configuration {#content-fragments-setup}

Les fragments de contenu dans Adobe Experience Manager (AEM) as a Cloud Service vous permettent de préparer le contenu prêt à être utilisé à plusieurs emplacements et sur plusieurs canaux. Idéal pour la diffusion sans interface utilisateur et la création de pages.

Pour activer votre instance pour la fonctionnalité de fragment de contenu, vous devez activer :

* **Modèles de fragment de contenu** – obligatoire

  >[!CAUTION]
  >
  >Si vous n’activez pas les **modèles de fragment de contenu** :
  >
  >* la valeur **Créer** ne sera pas disponible pour la création de modèles.
  >* Vous ne pourrez pas [sélectionner la configuration Sites pour créer le point d’entrée](/help/headless/graphql-api/graphql-endpoint.md) associé.

* **Requêtes persistantes GraphQL** – facultatif

La configuration de votre instance est terminée :

* par [Activation de la fonctionnalité dans l’explorateur de configurations](#enable-content-fragment-functionality-configuration-browser)
* then [application de la configuration à vos dossiers de ressources individuels](#apply-the-configuration-to-your-folder)

## Activation de la fonctionnalité de fragment de contenu dans l’explorateur de configurations {#enable-content-fragment-functionality-configuration-browser}

Pour utiliser la fonctionnalité Fragment de contenu des modèles de fragment de contenu et des requêtes persistantes GraphQL, vous devez **must** les activer d’abord à l’aide de l’option **Explorateur de configuration**:

>[!NOTE]
>
>Pour plus d’informations, voir [Explorateur de configuration](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>[Sous-configurations](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (une configuration imbriquée dans une autre configuration) sont entièrement prises en charge pour une utilisation avec des fragments de contenu, des modèles de fragment de contenu et des requêtes GraphQL.
>
>Il faut juste noter que :
>
>* Après la création de modèles dans une sous-configuration, il n’est PAS possible de déplacer ou de copier le modèle dans une autre sous-configuration.
>
>* Un point d’entrée GraphQL est (toujours) basé sur une configuration parent (racine).
>
>* Les requêtes persistantes sont (toujours) enregistrées en fonction de la configuration parent (racine).

1. Accédez à **Outils**, **Général**, puis ouvrez l’**Explorateur de configurations**.

1. Utilisez le bouton **Créer** pour ouvrir la boîte de dialogue.

   1. Spécifiez un **Titre**.
   1. À la création, la variable **Nom** devient le nom du noeud dans le référentiel.
Vous pouvez saisir un nom. Si vous laissez le champ vide, il est généré automatiquement en fonction du titre, puis ajusté en fonction de [Conventions de dénomination AEM](/help/implementing/developing/introduction/naming-conventions.md); vous pouvez ajuster le résultat si nécessaire.
   1. Pour activer leur utilisation, sélectionnez
      * **Modèles de fragment de contenu**
      * **Requêtes persistantes GraphQL**

      ![Définir la configuration](assets/cf-setup-create-conf.png)

1. Sélectionnez **Créer** pour enregistrer la définition.

## Appliquer la configuration à votre dossier {#apply-the-configuration-to-your-folder}

Lorsque la configuration **global** est activé pour la fonctionnalité de fragment de contenu, il s’applique ensuite à tout dossier de ressources accessible par le biais du **Ressources** console.

Pour utiliser d’autres configurations (excluant donc global) avec un dossier de ressources comparable, vous devez définir la connexion. Pour ce faire, sélectionnez la **Configuration** dans le **Cloud Service** de la **Propriétés du dossier** du dossier approprié.

![Appliquer la configuration](assets/cf-setup-apply-conf.png)
