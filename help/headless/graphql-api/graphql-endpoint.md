---
title: Gérer les points d’entrée GraphQL dans AEM
description: Découvrez comment gérer les points d’entrée GraphQL dans Adobe Experience Manager as a Cloud Service pour la diffusion de contenu découplé.
feature: Content Fragments,GraphQL API
exl-id: f7164ae3-4074-4db7-8c43-a79cc2ef00b1
source-git-commit: d6b98559e7cbe5fc5bd05d9cf37225e960e668e7
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 87%

---

# Gérer les points d’entrée GraphQL dans AEM {#graphql-aem-endpoint}

Le point d’entrée est le chemin utilisé pour accéder à GraphQL pour AEM. Avec ce chemin, vous (ou votre application) pouvez :

* accéder au schéma GraphQL ;
* envoyer vos requêtes GraphQL ;
* recevoir les réponses (à vos requêtes GraphQL).

Dans AEM, il existe deux types de points d’entrée :

* Global
   * Disponible pour tous les sites.
   * Ce point d’entrée peut utiliser tous les modèles de fragment de contenu de toutes les configurations Sites (définis dans l’[explorateur de configurations](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser)).
   * S’il existe des modèles de fragment de contenu à partager entre les configurations Sites, ils doivent être créés sous les configurations Sites globales.
* Configurations Sites :
   * Correspond à une configuration Sites, comme défini dans l’[explorateur de configurations](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser).
   * Spécifique à un site/projet spécifique.
   * Un point d’entrée spécifique à la configuration Sites utilisera les modèles de fragment de contenu de cette configuration Sites spécifique, ainsi que ceux de la configuration Sites globale.

>[!CAUTION]
>
>L’éditeur de fragment de contenu peut permettre à un fragment de contenu d’une configuration Sites de référencer un fragment de contenu d’une autre configuration Sites (à l’aide de stratégies).
>
>Dans ce cas, tout le contenu ne peut pas être récupéré à l’aide d’un point de terminaison spécifique à la configuration Sites.
>
>L’auteur du contenu doit contrôler ce scénario ; par exemple, il peut être utile de placer des modèles de fragment de contenu partagés sous la configuration de sites globaux.

Le chemin d’accès au référentiel du point d’entrée global GraphQL pour AEM est :

`/content/cq:graphql/global/endpoint`

Pour lequel votre application peut utiliser le chemin d’accès suivant dans l’URL de la requête :

`/content/_cq_graphql/global/endpoint.json`

Pour activer le point d’entrée de GraphQL pour AEM, vous devez procéder comme suit :

* [Activation de votre point d’entrée GraphQL](#enabling-graphql-endpoint)
* [Publication de votre point d’entrée GraphQL](#publishing-graphql-endpoint)

## Activation de votre point d’entrée GraphQL {#enabling-graphql-endpoint}

Pour activer un point d’entrée GraphQL, vous devez d’abord disposer d’une configuration appropriée. Voir [Fragments de contenu – Explorateur de configurations](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser).

>[!CAUTION]
>
>Si l’[utilisation des modèles de contenu du fragment n’a pas été activée](/help/sites-cloud/administering/content-fragments/setup.md#enable-content-fragment-functionality-configuration-browser), l’option **Créer** n’est pas disponible.

Pour activer le point d’entrée correspondant :

1. Accédez à **Outils**, **Général**, puis sélectionnez **GraphQL**.
1. Sélectionnez **Créer**.
1. La boîte de dialogue **Créer un point d’entrée GraphQL** s’ouvre. Vous pouvez spécifier ici les éléments suivants :
   * **Nom** : nom du point d’entrée ; vous pouvez saisir du texte.
   * **Utiliser le schéma GraphQL fourni par** : utilisez la liste déroulante pour sélectionner le site/projet requis.

   >[!NOTE]
   >
   >L’avertissement suivant s’affiche dans la boîte de dialogue :
   >
   >* *Les points de terminaison GraphQL peuvent introduire des problèmes de sécurité et de performances des données s’ils ne sont pas gérés avec précaution. Assurez-vous que les autorisations appropriées sont définies après la création d’un point de fin.*

1. Confirmez en sélectionnant **Créer**.
1. La variable **Étapes suivantes** La boîte de dialogue fournit un lien direct vers la console Sécurité afin que vous puissiez vous assurer que le nouveau point de terminaison créé dispose des autorisations appropriées.

   >[!CAUTION]
   >
   >Le point d’entrée est accessible à tous. Cela peut entraîner un problème de sécurité, en particulier pour les instances de publication, car les requêtes GraphQL peuvent imposer une charge importante au serveur.
   >
   >Vous pouvez configurer des listes de contrôle d’accès pour le point d’entrée en fonction de votre cas d’utilisation.

## Publication de votre point d’entrée GraphQL {#publishing-graphql-endpoint}

Sélectionnez le nouveau point d’entrée et **Publier** pour le rendre entièrement disponible dans tous les environnements.

>[!CAUTION]
>
>Le point d’entrée est accessible à tous.
>
>Cela peut entraîner un problème de sécurité sur les instances de publication, car les requêtes GraphQL peuvent imposer une charge importante au serveur.
>
>Vous devez configurer des [listes de contrôle d’accès](/help/headless/security/permissions.md) pour le point d’entrée en fonction de votre cas d’utilisation
