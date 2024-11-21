---
title: API OpenAPI
description: En savoir plus sur la prise en charge d’AEM as a Cloud Service pour les API OpenAPI
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 9259b064a0a03db67333c522ebd918883859018f
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---


# API OpenAPI {#openapi-based-apis}

>[!NOTE]
>
>Les API ouvertes sont disponibles dans le cadre d’un programme d’accès anticipé. Si vous souhaitez y accéder, nous vous encourageons à envoyer un email [aem-apis@adobe.com](mailto:aem-apis@adobe.com) avec une description de votre cas d’utilisation.

Les nouvelles API AEM as a Cloud Service suivent la spécification OpenAPI et génèrent ainsi des API cohérentes, bien documentées et conviviales. Des informations détaillées sont disponibles dans les pages suivantes :

* Un [ tutoriel complet](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) sur la configuration et l’appel des API d’AEM OpenAPI.
* [Guides](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/) d&#39;informations, y compris [ concepts et syntaxe d&#39;API](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/).
* La [documentation de référence](https://developer.adobe.com/experience-cloud/experience-manager-apis/) du point d’entrée API, où certaines des API sont basées sur OpenAPI, comme [cette API Sites](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/). La documentation de référence comprend également un terrain de lecture API qui facilite l’essai d’un point de terminaison à l’aide d’un jeton porteur généré avec Adobe Developer Console.

Un cas d’utilisation d’API courant implique des intégrations avec des systèmes tels qu’un CRM ou un PIM, où AEM API sont invoquées pour récupérer ou conserver des données. Dans le cadre de la mise en oeuvre de l’intégration, les applications peuvent s’abonner à [événements AEM émis](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-eventing/overview), ce qui peut déclencher une logique métier dans Adobe App Builder ou dans d’autres infrastructures.

Les types d’authentification d’API pris en charge diffèrent selon le point de terminaison, mais il peut s’agir d’une application OAuth serveur à serveur, d’une application web OAuth et d’une application monopage OAuth (SPA).

>[!NOTE]
>
> Le [tutoriel de bout en bout](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) est une ressource recommandée pour apprendre à configurer et à appeler les API d’AEM basées sur OpenAPI.


## Configuration de l’accès aux API {#configuring-api-access}

De nombreuses API d’AEM basées sur OpenAPI nécessitent une authentification, qui nécessite que les informations d’identification soient générées à l’aide de [Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/). La configuration comprend les étapes suivantes, illustrées dans le tutoriel :

1. Assurez-vous que les profils de produit [ de votre programme AEM sont mis à jour ](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles) et qu’un service approprié est activé pour accéder à l’API souhaitée.
1. Créez un projet dans Adobe Developer Console et ajoutez les API souhaitées au projet, en sélectionnant également le type d’authentification approprié.
1. Générez les informations d’identification, qui seront ensuite utilisées pour exchange un jeton porteur lors de l’appel de l’API.
1. Enregistrez l’ID client avec l’environnement en configurant un fichier YAML, qui est déployé à l’aide du pipeline de configuration (ou ligne de commande pour les RDE).

## Enregistrement d’un ID de client {#registering-a-client-id}

Les identifiants client étendent les API d’un projet Adobe Developer Console à des environnements AEM spécifiques. Pour ce faire, procédez comme suit :

1. Créez un fichier nommé `api.yaml` ou similaire avec une configuration comme le fragment de code ci-dessous, y compris les niveaux souhaités (auteur, publication, aperçu). Les valeurs `Client_id` doivent provenir de vos projets d’API Adobe Developer Console.

   Les propriétés `kind`, `version` et `metadata` sont décrites dans l’article [Config Pipeline](/help/operations/config-pipeline.md#common-syntax) . La valeur de la propriété `kind` doit être définie sur *API* et la propriété `version` doit être définie sur *1*.

   ```
   kind: "API"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     allowedClientIDs:
       author:
         - "<client_id>"
       publish:
         - "<client_id>"
       preview:
         - "<client_id>"
   ```

1. Placez le fichier quelque part sous un dossier de niveau supérieur nommé `config` ou similaire, comme décrit sous [Config Pipeline](/help/operations/config-pipeline.md#folder-structure).
1. Pour les types d’environnements autres que RDE (qui utilise des outils de ligne de commande), créez un pipeline de configuration de déploiement ciblé dans Cloud Manager, comme référencé par [cette section](/help/operations/config-pipeline.md#creating-and-managing) dans l’article Config Pipeline . Notez que les pipelines de pile complète et les pipelines de niveau web ne déploient pas le fichier de configuration.
1. Déployez la configuration.





