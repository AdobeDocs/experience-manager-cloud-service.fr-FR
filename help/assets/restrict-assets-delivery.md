---
title: Limitation de la diffusion des ressources avec Dynamic Media avec les fonctionnalités OpenAPI
description: Découvrez comment restreindre la diffusion des ressources avec les fonctionnalités OpenAPI.
role: User
exl-id: 3fa0b75d-c8f5-4913-8be3-816b7fb73353
source-git-commit: 03e13d29629c5e0305401179502cd1fc24f9ad75
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 2%

---

# Limitation de la diffusion des ressources avec Dynamic Media avec les fonctionnalités OpenAPI {#restrict-access-to-assets}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

La gouvernance centrale des ressources dans Experience Manager permet à l’administrateur DAM ou aux responsables de marque de gérer l’accès aux ressources disponibles via Dynamic Media avec les fonctionnalités OpenAPI. Ils peuvent restreindre la diffusion des ressources approuvées (jusqu’à une ressource individuelle) à l’utilisateur ou aux groupes [ Adobe Identity Management System (IMS) sélectionnés en configurant certaines métadonnées sur les ressources dans leur service de création AEM as a Cloud Service.](https://helpx.adobe.com/in/enterprise/using/users.html#user-mgt-strategy)

Une fois qu’une ressource est limitée via Dynamic Media avec OpenAPI, seuls les utilisateurs (intégrés à Adobe IMS) autorisés à accéder à cette ressource se voient accorder l’accès. Pour accéder à la ressource, l’utilisateur doit exploiter les fonctionnalités [Search](search-assets-api.md) et [Delivery](deliver-assets-apis.md) de Dynamic Media avec OpenAPI.

![Accès restreint aux ressources](/help/assets/assets/restricted-access.png)

Dans Experience Manager Assets, la diffusion limitée via IMS implique deux étapes clés :

* Création
* Diffusion

## Création {#authoring}

### Diffusion restreinte utilisant un jeton porteur IMS {#restrict-delivery-ims-token}

Vous pouvez restreindre la diffusion des ressources dans [!DNL Experience Manager] en fonction des identités d’utilisateur et de groupe IMS .

>[!NOTE]
>
> Cette fonctionnalité n’est actuellement pas en libre-service. Pour restreindre la remise des ressources pour les [utilisateurs](https://helpx.adobe.com/in/enterprise/using/manage-directory-users.html) et [groupes](https://helpx.adobe.com/in/enterprise/using/user-groups.html) IMS, contactez votre équipe d’assistance entreprise pour obtenir des instructions sur la manière de récupérer les informations requises pour limiter l’accès au portail [Adobe Admin Console](https://adminconsole.adobe.com/) et de configurer l’accès dans le service de création AEM as a Cloud Service.

### Limitation de la diffusion des ressources à l’aide de la date et de l’heure d’activation et de désactivation {#restrict-delivery-assets-date-time}

Les auteurs DAM peuvent également restreindre la diffusion des ressources en définissant une heure d’activation ou de désactivation pour l’activation disponible dans les propriétés de la ressource.

Si vous définissez une heure d’activation pour l’activation d’une ressource, une URL de diffusion est générée pour la ressource à l’heure définie. La ressource reste inactive avant l’heure définie. De même, si vous définissez une heure de désactivation pour une ressource, celle-ci est désactivée à l’heure définie et l’URL de diffusion de la ressource cesse d’afficher la ressource.

Pour définir l’heure d’activation et de désactivation de la ressource, procédez comme suit :

1. Sélectionnez la ressource et cliquez sur **[!UICONTROL Propriétés]**.

1. Dans la section **[!UICONTROL Activation planifiée (de)]** de l’onglet **[!UICONTROL De base]** , définissez l’heure d’activation ou l’heure de désactivation en fonction de vos besoins.

De même, dans la vue Assets, vous pouvez sélectionner la ressource et cliquer sur **[!UICONTROL Détails]** pour afficher les propriétés de la ressource et définir l’heure d’activation et l’heure de désactivation.

Le champ est disponible dans le formulaire de métadonnées par défaut. Si votre ressource n’est pas basée sur le schéma de métadonnées par défaut et que les champs Heure d’activation et Heure de désactivation ne sont pas disponibles dans les propriétés de la ressource, exécutez les étapes suivantes dans la vue Admin :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
1. Sélectionnez le schéma de métadonnées et cliquez sur **[!UICONTROL Modifier]**.
1. Ajoutez un champ **[!UICONTROL Date]** de la section **[!UICONTROL Créer le formulaire]** dans la partie droite de la section Métadonnées dans le formulaire.
1. Cliquez sur le champ nouvellement ajouté, puis effectuez les mises à jour suivantes dans le panneau **[!UICONTROL Paramètres]** :
   1. Remplacez le **[!UICONTROL libellé du champ]** par **Heure d’activation** ou **Heure de désactivation**.
   1. Mettez à jour la **[!UICONTROL map to property]** vers _./jcr:content/onTime_ pour le champ **Heure d’activation** et _./jcr:content/offTime_ pour le champ **Heure de désactivation** .
1. Cliquez sur **[!UICONTROL Enregistrer]**.

De même, pour la vue Assets, si votre ressource n’est pas basée sur le schéma de métadonnées par défaut et que les champs Heure d’activation et Heure de désactivation ne sont pas disponibles dans les propriétés de la ressource, exécutez les étapes suivantes :

1. Cliquez sur **[!UICONTROL Forms de métadonnées]** dans la section **[!UICONTROL Paramètres]** .
1. Sélectionnez le formulaire de métadonnées et cliquez sur **[!UICONTROL Modifier]**.
1. Ajoutez un champ **[!UICONTROL Date]** de la section **[!UICONTROL Components]** du volet de gauche au formulaire.
1. Cliquez sur le champ nouvellement ajouté et remplacez **[!UICONTROL Libellé]** par **Heure d’activation** ou **Heure de désactivation**.
1. Mettez à jour la **[!UICONTROL propriété de métadonnées]** vers _./jcr:content/onTime_ pour le champ **Heure d’activation** et _./jcr:content/offTime_ pour le champ **Heure de désactivation** .
1. Cliquez sur **[!UICONTROL Enregistrer]**.



## Diffusion de ressources restreintes {#delivery-restricted-assets}

La diffusion des ressources restreintes repose sur une autorisation réussie d’accès aux ressources. L’autorisation est soit par l’intermédiaire de [jetons de porteur IMS](https://developer.adobe.com/developer-console/docs/guides/authentication/UserAuthentication/IMS/) (application pour les demandes initiées à partir de [AEM Sélecteur de ressources](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector)), soit par un cookie sécurisé (si des fournisseurs d’identité personnalisés sont configurés sur vos services Publish/Preview d’AEM et que vous avez configuré la création et l’inclusion de cookies sur les pages).

### Diffusion pour les demandes d’AEM auteur ou de sélecteur de ressources {#delivery-aem-author-asset-selector}

Pour activer la diffusion de ressources restreintes au cas où la requête serait envoyée à partir du service de création AEM ou du sélecteur de ressources AEM, un jeton porteur IMS valide est essentiel.\
Sur les services de création AEM Cloud Service ainsi que sur le sélecteur de ressources, le jeton de porteur IMS est automatiquement généré et utilisé pour les demandes après une connexion réussie.

>[!NOTE]
>
>Pour plus d’informations sur l’activation de l’authentification IMS sur les intégrations basées sur AEM Sélecteur de ressources, contactez le support aux entreprises.

1. Pour les expériences autres que celles basées sur un sélecteur de ressources, AEM as a Cloud Service et Dynamic Media avec des fonctionnalités OpenAPI prennent actuellement en charge les intégrations d’api côté serveur et peuvent générer des jetons de porteur IMS.
   * Suivez les instructions [ici](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#the-server-to-server-flow) pour effectuer des intégrations API service à serveur qui peuvent récupérer les jetons de porteur IMS via [AEM as a Cloud Service Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console)
   * Pour une durée limitée, les jetons de porteur IMS de courte durée pour l’utilisateur authentifié sur [AEM as a Cloud Service Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console) peuvent être générés en suivant les instructions [ici](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#developer-flow) :

1. Lors de la création de requêtes d’API [Search](search-assets-api.md) et [Delivery](deliver-assets-apis.md), ajoutez le jeton de porteur IMS obtenu à l’en-tête **[!UICONTROL Authorization]** de la requête HTTP (assurez-vous que sa valeur est précédée du préfixe **[!UICONTROL Bearer]**).

1. Pour valider la restriction d’accès, lancez une requête d’API de diffusion avec et sans l’en-tête **[!UICONTROL Authorization]** .
   * La réponse produira un code d’état d’erreur `404` dans les cas où il n’existe aucun jeton porteur IMS, ou le jeton porteur IMS fourni n’appartient pas à l’utilisateur qui s’est vu accorder l’accès à la ressource (directement ou par l’intermédiaire de l’appartenance à un groupe).
   * La réponse génère un code d’état de réussite `200` avec le contenu binaire de la ressource si le jeton porteur IMS est l’un des utilisateurs ou groupes auxquels l’accès à la ressource a été accordé.

### Diffusion pour les fournisseurs d’identité personnalisés sur le service Publish {#delivery-custom-identity-provider}

Il est possible d’utiliser conjointement AEM Sites, AEM Assets et Dynamic Media avec des licences OpenAPI, ce qui permet de configurer la diffusion limitée des ressources sur des sites web hébergés sur AEM service Publish ou Preview. Le flux de diffusion sécurisé utilise des cookies de navigateur pour établir l’accès de l’utilisateur et disposer d’un domaine personnalisé pour le niveau de diffusion qui est un sous-domaine du domaine de publication est un prérequis pour mettre en oeuvre ce cas d’utilisation. Si les services Publish et Aperçu d’AEM Sites sont configurés pour utiliser un [fournisseur d’identité personnalisé (IdP)](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0), un nouveau cookie appelé `delivery-token` encapsulant l’appartenance à un groupe d’utilisateurs doit être défini sur l’authentification de l’utilisateur après l’entrée du domaine de publication. Le niveau de diffusion extrait le matériel d’autorisation du cookie sécurisé et valide l’accès. Pour plus d’informations, enregistrez un [ticket d’assistance aux entreprises](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities).
