---
title: Limitation de la diffusion des ressources dans Experience Manager
description: Découvrez comment restreindre la diffusion des ressources dans [!DNL Experience Manager].
role: User
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 1%

---

# Limitation de l’accès aux ressources dans [!DNL Experience Manager] {#restrict-access-to-assets}

La gouvernance centrale des ressources en Experience Manager permet à l’administrateur DAM ou aux responsables de marque de gérer l’accès aux ressources. Ils peuvent restreindre l’accès en configurant des rôles pour les ressources approuvées du côté création, en particulier sur l’instance d’auteur as a Cloud Service AEM.

Utilisateurs [recherche](search-assets-api.md) ou en utilisant [URL de diffusion](deliver-assets-apis.md) peuvent accéder aux ressources restreintes une fois le processus d’autorisation réussi.

![Accès limité aux ressources](/help/assets/assets/restricted-access.png)

## Diffusion restreinte utilisant un jeton IMS {#restrict-delivery-ims-token}

En Experience Manager, la diffusion limitée via IMS implique deux étapes clés :

* Création
* Diffusion

### Création {#authoring}

Pour limiter la diffusion des ressources, des rôles doivent être configurés pour les ressources dans la variable [!DNL Experience Manager] ou [!DNL Experience Manager Assets]. Pour configurer des rôles dans [!DNL Experience Manager], procédez comme suit :

1. Accédez au [!DNL Experience Manager] en tant qu’administrateur DAM.
1. Sélectionnez la ressource pour laquelle vous devez configurer le rôle.
1. Accédez à **[!UICONTROL Propriétés]** > **[!UICONTROL Avancé]**, et assurez-vous que la variable **[!UICONTROL Rôles]** existe dans le champ [!UICONTROL Métadonnées avancées] .

   ![Métadonnées des rôles](/help/assets/assets/roles_metadata.jpg)
Si le champ n’est pas disponible, procédez comme suit pour ajouter le champ :

   1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
   1. Sélectionnez le schéma de métadonnées et cliquez sur **[!UICONTROL Modifier _(e)_]**.
   1. Ajouter un **[!UICONTROL Texte à plusieurs valeurs]** du champ **[!UICONTROL Créer un formulaire]** dans la partie droite de la section Métadonnées du formulaire.
   1. Cliquez sur le champ nouvellement ajouté, puis effectuez les mises à jour suivantes dans la variable  **[!UICONTROL Paramètres]** panel :
      1. Modifiez la variable **[!UICONTROL Libellé du champ]** to _Rôles_.
      1. Mettez à jour le **[!UICONTROL Associer à la propriété]** to _./jcr:content/metadata/dam:rôles_.

1. Procurez-vous les groupes IMS à ajouter dans les métadonnées Rôles de la ressource. Pour récupérer les groupes IMS, procédez comme suit :
   1. Connectez-vous à https://adminconsole.adobe.com/.
   1. Accédez à votre organisation respective et accédez à **[!UICONTROL Groupes d’utilisateurs]**.
   1. Sélectionnez la variable **[!UICONTROL Groupe d’utilisateurs]** vous devez ajouter et extraire la variable **[!UICONTROL orgID]** et **[!UICONTROL userGroupID]** à partir de l’URL ou utilisez votre ID d’organisation comme `{orgID}@AdobeOrg:{usergroupID}`.

1. Ajoutez l’ID de groupe au **[!UICONTROL Rôles]** champ des propriétés Asset. <br>
Les ID de groupe définis dans la variable **[!UICONTROL Rôles]** sont les seuls utilisateurs qui peuvent accéder à la ressource. Vous pouvez également ajouter l’identifiant du client IMS et l’identifiant du profil IMS dans la variable **[!UICONTROL Rôles]** champ . Par exemple, `{orgId}@AdobeOrg:{profileId}`.

   >[!NOTE]
   >
   >Pour la nouvelle vue Assets, vous ne pouvez autoriser l’accès qu’aux dossiers, et exclusivement aux groupes plutôt qu’aux utilisateurs individuels. En savoir plus sur [gestion des autorisations dans Experience Manager Assets](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

   >[!VIDEO](https://video.tv.adobe.com/v/3427429)

### Diffusion de ressources restreintes {#delivery-restricted-assets}

La diffusion des ressources restreintes repose sur une autorisation réussie d’accès aux ressources. L’autorisation est basée sur un jeton IMS si la requête est envoyée à partir d’une instance d’auteur AEM ou d’un sélecteur de ressources ou sur un cookie spécial si des fournisseurs d’identité personnalisés sont configurés sur votre instance de publication ou d’aperçu.

#### Diffusion pour AEM auteur ou sélecteur de ressources {#delivery-aem-author-asset-selector}

Pour activer la diffusion de ressources restreintes au cas où la requête serait envoyée à partir de l’instance d’auteur AEM ou du sélecteur de ressources, un jeton IMS valide est essentiel. Procédez comme suit :

1. [Générer un jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token).
   * Connectez-vous à la console de développement de votre environnement as a Cloud Service AEM.

   * Accédez à **[!UICONTROL Environnement]** > **[!UICONTROL Intégrations]** > **[!UICONTROL Jeton local]** > **[!UICONTROL Obtention du jeton de développement local]** > **[!UICONTROL Copier la valeur accessToken]**. En savoir plus sur [comment accéder au jeton et aux aspects connexes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token)

1. Intégrez le jeton d’accès obtenu à la variable **[!UICONTROL Autorisation]** en-tête , en veillant à ce que sa valeur contienne le préfixe **[!UICONTROL Porteur]**.

1. Validez la fonctionnalité du jeton d’accès en initiant une requête. Elle doit générer une erreur 404 dans les cas où il n’existe pas de jeton d’accès IMS, ou le jeton d’accès fourni n’a pas les mêmes entités ou groupes que ceux ajoutés dans les métadonnées de la ressource.

#### Diffusion pour les fournisseurs d’identité personnalisés {#delivery-custom-identity-provider}

Dans le cas d’un fournisseur d’identité personnalisé configuré sur votre instance de publication ou d’aperçu, vous pouvez mentionner le groupe qui doit avoir accès aux ressources sécurisées dans `groupMembership` pendant le processus de configuration. Lorsque vous vous connectez à un fournisseur d’identité personnalisé via [Intégration SAML](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0), la variable `groupMembership` est lu et utilisé pour construire un cookie, qui est envoyé dans toutes les demandes d’authentification, similaire à un jeton IMS en cas de demande de l’auteur AEM ou du sélecteur de ressources.

Lorsqu’une ressource sécurisée est disponible sur une page et qu’une demande est envoyée à l’URL de diffusion pour effectuer le rendu de la ressource, AEM vérifie les rôles présents dans le cookie ou le jeton IMS et la compare au `dam:roles property` appliquée lors de la création de la ressource. S’il existe une correspondance, la ressource s’affiche.
