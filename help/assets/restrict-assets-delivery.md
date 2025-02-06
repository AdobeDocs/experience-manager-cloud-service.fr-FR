---
title: Limiter la diffusion des ressources avec Dynamic Media avec les fonctionnalités OpenAPI
description: Découvrez comment restreindre la diffusion des ressources à l’aide des fonctionnalités OpenAPI.
role: User
exl-id: 3fa0b75d-c8f5-4913-8be3-816b7fb73353
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 5%

---

# Limiter la diffusion des ressources avec Dynamic Media avec les fonctionnalités OpenAPI {#restrict-access-to-assets}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Le guide de Dynamic Media avec fonctionnalités OpenAPI est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Dynamic Media avec fonctionnalités OpenAPI]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

La gouvernance centrale des ressources dans Experience Manager permet à l’administrateur de gestion des ressources numériques ou aux Brand Manager de gérer l’accès aux ressources disponibles via Dynamic Media avec les fonctionnalités OpenAPI. Ils peuvent restreindre la diffusion des ressources approuvées (jusqu’à une ressource individuelle) à des utilisateurs ou groupes d’[systèmes Identity Management (IMS) d’Adobe sélectionnés](https://helpx.adobe.com/in/enterprise/using/users.html#user-mgt-strategy) en configurant certaines métadonnées sur les ressources sur leur service de création AEM as a Cloud Service.

Une fois qu’une ressource est restreinte via Dynamic Media avec des API ouvertes, seuls les utilisateurs (intégrés à Adobe IMS) autorisés à accéder à cette ressource se voient accorder l’accès. Pour accéder à la ressource, l’utilisateur doit tirer parti des fonctionnalités [Recherche](search-assets-api.md) et [Diffusion](deliver-assets-apis.md) de Dynamic Media avec OpenAPI.

![Accès limité aux ressources](/help/assets/assets/restricted-access.png)

Dans Experience Manager Assets, la diffusion restreinte via IMS implique deux étapes importantes :

* Création
* Diffusion

## Création {#authoring}

### Diffusion restreinte à l’aide d’un jeton porteur IMS {#restrict-delivery-ims-token}

Vous pouvez restreindre la diffusion des ressources dans [!DNL Experience Manager] en fonction des identités d’utilisateur et de groupe IMS .

>[!NOTE]
>
Cette fonctionnalité n’est actuellement pas en libre-service. Pour restreindre la diffusion des ressources pour IMS [utilisateurs](https://helpx.adobe.com/in/enterprise/using/manage-directory-users.html) et [groupes](https://helpx.adobe.com/in/enterprise/using/user-groups.html), contactez votre équipe d’assistance aux entreprises pour obtenir des conseils sur la manière de récupérer les informations requises pour restreindre l’accès à partir du portail [Adobe Admin Console](https://adminconsole.adobe.com/) et sur la manière de configurer l’accès dans le service de création AEM as a Cloud Service.

### Limiter la diffusion des ressources à l’aide des dates et heures d’activation et de désactivation {#restrict-delivery-assets-date-time}

Les auteurs de gestion des ressources numériques peuvent également limiter la diffusion des ressources en définissant une heure d’activation ou de désactivation pour l’activation disponible dans les propriétés des ressources.

Si vous définissez une Heure d’activation pour l’activation d’une ressource, une URL de diffusion est générée pour la ressource à l’heure définie. La ressource reste inactive avant l’heure définie. De même, si vous définissez une Heure de désactivation pour une ressource, la ressource est désactivée à l’heure définie et l’URL de diffusion de la ressource cesse de l’afficher.

Pour définir les heures d’activation et de désactivation de la ressource, procédez comme suit :

1. Sélectionnez la ressource et cliquez sur **[!UICONTROL Propriétés]**.

1. Dans la section **[!UICONTROL Activation planifiée (de)]** de l’onglet **[!UICONTROL De base]**, définissez l’Heure d’activation ou l’Heure de désactivation en fonction de vos besoins.

De même, dans la vue Assets, vous pouvez sélectionner la ressource et cliquer sur **[!UICONTROL Détails]** pour afficher les propriétés de la ressource et définir l’heure d’activation et l’heure de désactivation.

Le champ est disponible dans le formulaire de métadonnées par défaut. Si votre ressource n’est pas basée sur le schéma de métadonnées par défaut et que les champs Heure d’activation et Heure de désactivation ne sont pas disponibles dans les propriétés de la ressource, procédez comme suit dans la vue Administration :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
1. Sélectionnez le schéma de métadonnées et cliquez sur **[!UICONTROL Modifier]**.
1. Ajoutez un champ **[!UICONTROL Date]** de la section **[!UICONTROL Créer le formulaire]** sur le côté droit à la section Métadonnées du formulaire.
1. Cliquez sur le champ nouvellement ajouté, puis effectuez les mises à jour suivantes dans le panneau **[!UICONTROL Paramètres]** :
   1. Remplacez **[!UICONTROL Libellé du champ]** par **Heure d’activation** ou **Heure de désactivation**.
   1. Mettez à jour **[!UICONTROL Mappez à la propriété]** sur _./jcr:content/onTime_ pour le champ **On Time** et le _.Champ /jcr:content/offTime_ pour **Heure de désactivation**.
1. Cliquez sur **[!UICONTROL Enregistrer]**.

De même, pour la vue Assets, si votre ressource n’est pas basée sur le schéma de métadonnées par défaut et que les champs Heure d’activation et Heure de désactivation ne sont pas disponibles dans les propriétés de la ressource, procédez comme suit :

1. Cliquez sur **[!UICONTROL Forms de métadonnées]** dans la section **[!UICONTROL Paramètres]**.
1. Sélectionnez le formulaire de métadonnées et cliquez sur **[!UICONTROL Modifier]**.
1. Ajoutez au formulaire un champ **[!UICONTROL Date]** de la section **[!UICONTROL Composants]** dans le volet de gauche.
1. Cliquez sur le champ nouvellement ajouté et remplacez le **[!UICONTROL Libellé]** par **Heure d’activation** ou **Heure de désactivation**.
1. Mettez à jour la **[!UICONTROL propriété de métadonnées]** en _./jcr:content/onTime_ pour le champ **On Time** et le _.Champ /jcr:content/offTime_ pour **Heure de désactivation**.
1. Cliquez sur **[!UICONTROL Enregistrer]**.



## Diffusion de ressources restreintes {#delivery-restricted-assets}

La diffusion des ressources restreintes repose sur l’obtention d’autorisations d’accès aux ressources. L’autorisation se fait soit par l’intermédiaire de [Jetons du porteur IMS](https://developer.adobe.com/developer-console/docs/guides/authentication/UserAuthentication/IMS/) (application pour les demandes initiées à partir du [sélecteur de ressources AEM](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector)), soit par l’intermédiaire d’un cookie sécurisé (si des fournisseurs d’identité personnalisés sont configurés sur vos services AEM Publish/Preview et que vous avez configuré la création et l’inclusion de cookies sur les pages).

### Diffusion pour les requêtes de l’auteur ou du sélecteur de ressources AEM {#delivery-aem-author-asset-selector}

Pour permettre la diffusion de ressources restreintes dans le cas où la requête est envoyée par le service de création AEM ou le sélecteur de ressources AEM, un jeton porteur IMS valide est essentiel.\
Sur les services de création AEM Cloud Service et le sélecteur de ressources, le jeton du porteur IMS est automatiquement généré et utilisé pour les requêtes après une connexion réussie.

>[!NOTE]
>
Pour plus d’informations sur la manière d’activer l’authentification IMS sur les intégrations basées sur le sélecteur de ressources AEM, contactez l’assistance aux entreprises

1. Pour les expériences non basées sur le sélecteur de ressources, AEM as a Cloud Service et Dynamic Media avec les fonctionnalités OpenAPI prennent actuellement en charge les intégrations d’api côté serveur et peuvent générer des jetons porteur IMS.
   * Suivez les instructions [ici](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#the-server-to-server-flow) pour effectuer des intégrations d’API service à serveur qui peuvent récupérer les jetons du porteur IMS via [AEM as a Cloud Service Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console)
   * Pour une durée limitée, l’accès développeur local (non destiné aux cas d’utilisation de production) et les jetons porteur IMS de courte durée pour l’utilisateur authentifié sur [AEM as a Cloud Service Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#crxde-lite-and-developer-console) peuvent être générés en suivant les instructions [ici](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis#developer-flow)

1. Lors de l’exécution des requêtes d’API [Search](search-assets-api.md) et [Delivery](deliver-assets-apis.md), ajoutez le jeton du porteur IMS obtenu à l’en-tête **[!UICONTROL Authorization]** de la requête HTTP (assurez-vous que sa valeur comporte le préfixe **[!UICONTROL Bearer]**).

1. Pour valider la restriction d’accès, lancez une requête API de diffusion avec et sans l’en-tête **[!UICONTROL Authorization]**.
   * La réponse renvoie un code d’état d’erreur `404` dans les cas où il n’existe aucun jeton porteur IMS ou si le jeton porteur IMS fourni n’appartient pas à l’utilisateur à qui l’accès à la ressource a été accordé (soit directement, soit par l’intermédiaire de l’appartenance à un groupe).
   * La réponse génère un code de statut de succès `200` avec le contenu binaire de la ressource si le jeton porteur IMS est l’un des utilisateurs ou groupes auxquels l’accès à la ressource a été accordé.

### Diffusion pour les fournisseurs d’identité personnalisée sur le service Publish {#delivery-custom-identity-provider}

AEM Sites, AEM Assets et Dynamic Media AEM avec licences OpenAPI peuvent être utilisés conjointement, ce qui permet de configurer une diffusion restreinte des ressources sur les sites web hébergés sur Publish ou le service d’aperçu. Le flux de diffusion sécurisé utilise des cookies de navigateur pour établir l’accès de l’utilisateur. Pour mettre en œuvre ce cas d’utilisation, vous devez disposer d’un domaine personnalisé pour le niveau de diffusion qui est un sous-domaine du domaine de publication. Dans le cas où les services Publish et Aperçu d’AEM Sites sont configurés pour utiliser un [fournisseur d’identité personnalisé (IdP)](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0), un nouveau cookie appelé `delivery-token` encapsulant l’appartenance à un groupe de l’utilisateur doit être défini sur le domaine de publication après l’authentification de l’utilisateur. Le niveau de diffusion extrait le matériel d’autorisation du cookie sécurisé et valide l’accès. Enregistrez un [ticket d’assistance pour les entreprises](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities) pour plus d’informations.
