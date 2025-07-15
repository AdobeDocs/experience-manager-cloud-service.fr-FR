---
title: API OpenAPI
description: Découvrez la prise en charge d’AEM as a Cloud Service pour les API basées sur OpenAPI
feature: Developing
role: Admin, Architect, Developer
exl-id: 4aeafba9-8f9e-4ecb-9e37-8d048b0474cc
source-git-commit: 320fe55d652b94cd63dfe82d4165c1f957653a63
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# API OpenAPI {#openapi-based-apis}

Les nouvelles API d’AEM as a Cloud Service suivent la spécification OpenAPI et offrent donc un ensemble cohérent et bien documenté d’API.

>[!NOTE]
>
> Un [tutoriel complet](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) est une ressource recommandée pour apprendre à configurer et à appeler les API AEM basées sur OpenAPI.

Pour les points d’entrée qui nécessitent une authentification, l’approche d’authentification diffère en fonction du point d’entrée, mais peut utiliser OAuth de serveur à serveur, l’application web OAuth ou l’application d’une seule page (SPA) OAuth. Les informations d&#39;identification sont configurées via les projets dans [Adobe Developer Console](https://developer.adobe.com/developer-console/).

Les cas d’utilisation courants des API impliquent des intégrations à des systèmes tels qu’un CRM ou un PIM, où les API d’AEM sont appelées pour récupérer les données ou les conserver. Dans le cadre de la mise en œuvre de l’intégration, les applications peuvent s’abonner à [des événements émis par AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-eventing/overview), ce qui peut déclencher une logique commerciale dans Adobe App Builder ou une autre infrastructure.

Ce document sert de présentation, mais une documentation plus approfondie est disponible dans les pages suivantes :

* Les liens de la section API basée sur OpenAPI de la [documentation de référence](https://developer.adobe.com/experience-cloud/experience-manager-apis/). La documentation de référence de chaque API comprend également un playground d’API, qui permet de tester facilement un point d’entrée à l’aide d’un jeton porteur généré avec le Adobe Developer Console.

* Informations [Guides](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/), y compris [ concepts et syntaxe d’API](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/).

* Tutoriel de niveau supérieur décrivant [les approches d’authentification](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/openapis/overview#authentication-support) et d’autres concepts.

* Tutoriel vidéo sur [comment configurer les API basées sur OpenAPI](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup).

* [Tutoriel complet](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) sur la configuration et l’appel des OpenAPI avec la stratégie d’authentification serveur à serveur. Vous trouverez des tutoriels similaires pour les approches Authentification par application web et Application d’une seule page .

## Configuration de l’accès à l’API {#configuring-api-access}

Certaines API d&#39;AEM basées sur OpenAPI nécessitent une authentification, qui nécessite que les informations d&#39;identification soient générées à l&#39;aide de [Adobe Developer Console](https://developer.adobe.com/developer-console/). La configuration comprend les étapes suivantes :

1. Modernisation de l’environnement AEM as a Cloud Service. Pour plus d’informations, consultez [Étape du tutoriel Modernisation de l’environnement AEM as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup?#modernization-of-aem-as-a-cloud-service-environment).
1. Activez l’accès aux API AEM à l’aide des profils de produit. Les profils de produit sont associés aux services qui représentent les groupes d’utilisateurs AEM avec des listes de contrôle d’accès (ACL) prédéfinies. Bien que certains services soient associés par défaut à des profils de produit spécifiques, d’autres doivent être associés explicitement ; par exemple, le service Utilisateurs de l’API AEM Assets n’est associé à aucun [profil de produit](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles), vous devez donc l’activer pour utiliser l’API AEM Assets. Pour plus d’informations, voir [Étape du tutoriel Activer l’accès aux API AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#enable-aem-apis-access).
1. Pour ajouter l’authentification de serveur à serveur, l’utilisateur configurant l’intégration doit être l’administrateur système de l’entreprise dans Adobe Admin Console ou ajouté en tant que développeur au profil de produit auquel le service est associé. Pour plus d’informations, voir [Étape du tutoriel Activer l’accès aux API AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#enable-aem-apis-access).
1. Créez un projet Adobe Developer Console (ADC).
1. Configurez le projet ADC. Cela génère des informations d’identification qui seront utilisées ultérieurement pour échanger contre un jeton du porteur lors de l’appel de l’API.
1. Configurez l’instance AEM pour activer la communication de projet ADC. Cela implique l’enregistrement de l’ID client avec l’environnement en configurant et en déployant un fichier YAML, comme décrit dans la section [Enregistrement d’un ID client](#registering-a-client-id) ci-dessous.

Pour obtenir des instructions détaillées, reportez-vous au tutoriel [Configurer des API basées sur OpenAPI](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup).

### Enregistrement d’un ID client {#registering-a-client-id}

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
