---
title: API OpenAPI
description: Découvrez la prise en charge d’AEM as a Cloud Service pour les API basées sur OpenAPI
feature: Developing
role: Admin, Architect, Developer
exl-id: 4aeafba9-8f9e-4ecb-9e37-8d048b0474cc
source-git-commit: e735f7d2a39e3165907969d2e27565639499a636
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 1%

---

# API OpenAPI {#openapi-based-apis}

>[!NOTE]
>
>Les API ouvertes sont disponibles dans le cadre d’un programme d’accès anticipé. Si vous souhaitez y accéder, nous vous encourageons à envoyer un e-mail à l’adresse [aem-apis@adobe.com](mailto:aem-apis@adobe.com) avec une description de votre cas d’utilisation.

Les nouvelles API d’AEM as a Cloud Service suivent la spécification OpenAPI et produisent ainsi des API cohérentes, bien documentées et conviviales. Des informations détaillées sont disponibles dans les pages suivantes :

* Un [tutoriel complet](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) sur la configuration et l’appel des API AEM basées sur OpenAPI à l’aide de l’authentification serveur à serveur.
* Informations [Guides](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/), y compris [ concepts et syntaxe d’API](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/).
* Point d’entrée de l’API [documentation de référence](https://developer.adobe.com/experience-cloud/experience-manager-apis/), où certaines API sont basées sur OpenAPI, comme [cette API Sites](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/). La documentation de référence comprend également un laboratoire d’API, qui facilite l’essai d’un point d’entrée à l’aide d’un jeton porteur généré avec le Adobe Developer Console.

Un cas d’utilisation courant d’API implique des intégrations à des systèmes tels qu’un CRM ou un PIM, où les API d’AEM sont appelées pour récupérer les données ou les conserver. Dans le cadre de la mise en œuvre de l’intégration, les applications peuvent s’abonner à [des événements émis par AEM](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-eventing/overview), ce qui peut déclencher une logique commerciale dans Adobe App Builder ou une autre infrastructure.

Les types d’authentification d’API pris en charge varient en fonction du point d’entrée, mais peuvent être OAuth de serveur à serveur, OAuth Web App et OAuth Single Page App (SPA).

>[!NOTE]
>
> Le [tutoriel complet](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) est une ressource recommandée pour apprendre à configurer et à appeler les API AEM basées sur OpenAPI.


## Configuration de l’accès à l’API {#configuring-api-access}

De nombreuses API AEM basées sur OpenAPI nécessitent une authentification, ce qui nécessite que les informations d&#39;identification soient générées à l&#39;aide de [Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/). La configuration comprend les étapes suivantes :

1. Assurez-vous que les [profils de produit de votre programme AEM sont mis à jour](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles) et qu’un service approprié est activé pour accéder à l’API souhaitée.
1. Créez un projet dans Adobe Developer Console et ajoutez-y la ou les API souhaitées, en sélectionnant également le type d’authentification approprié.
1. Générez les informations d’identification qui seront ensuite utilisées pour échanger un jeton du porteur lors de l’appel de l’API.
1. Enregistrez l’identifiant client avec l’environnement en configurant un fichier YAML, qui est déployé à l’aide du pipeline de configuration (ou de la ligne de commande pour les RDE).

Pour obtenir des instructions détaillées, consultez le tutoriel [Configurer des API basées sur OpenAPI](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/setup) .

## Enregistrement d’un ID client {#registering-a-client-id}

Les identifiants client définissent la portée des API dans un projet Adobe Developer Console pour des environnements AEM spécifiques. Pour ce faire, procédez comme suit :

1. Créez un fichier nommé `api.yaml` ou similaire avec une configuration telle que le fragment de code ci-dessous, y compris les niveaux souhaités (création, publication, prévisualisation). `Client_id` valeurs doivent provenir de votre ou vos projet(s) d’API Adobe Developer Console.

   Les propriétés `kind`, `version` et `metadata` sont décrites dans l’article [Pipeline de configuration](/help/operations/config-pipeline.md#common-syntax). La valeur de la propriété `kind` doit être définie sur *API* et la propriété `version` doit être définie sur *1*.

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

1. Placez le fichier quelque part sous un dossier de niveau supérieur nommé `config` ou similaire, comme décrit sous [Pipeline de configuration](/help/operations/config-pipeline.md#folder-structure).
1. Pour les types d’environnements autres que le RDE (qui utilise l’outil de ligne de commande), créez un pipeline de configuration de déploiement ciblé dans Cloud Manager, comme indiqué dans [cette section](/help/operations/config-pipeline.md#creating-and-managing) dans l’article Pipeline de configuration . Notez que les pipelines de pile complète et de niveau web ne déploient pas le fichier de configuration.
1. Déployez la configuration.
