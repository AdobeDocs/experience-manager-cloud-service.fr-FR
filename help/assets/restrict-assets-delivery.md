---
title: Limitation de la diffusion des ressources dans Experience Manager
description: Découvrez comment restreindre la diffusion des ressources dans [!DNL Experience Manager].
role: User
exl-id: 3fa0b75d-c8f5-4913-8be3-816b7fb73353
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 2%

---

# Limitation de l’accès aux ressources dans [!DNL Experience Manager] {#restrict-access-to-assets}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [ Bonnes pratiques en matière de métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Dynamic Media avec fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation destinée aux développeurs AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

La gouvernance centrale des ressources dans Experience Manager permet à l’administrateur DAM ou aux responsables de marque de gérer l’accès aux ressources. Ils peuvent restreindre l’accès en configurant des rôles pour les ressources approuvées du côté création, en particulier sur l’instance d’auteur AEM as a Cloud Service.

Les utilisateurs [qui effectuent une recherche](search-assets-api.md) ou qui utilisent [des URL de diffusion](deliver-assets-apis.md) peuvent accéder à des ressources restreintes lorsqu’ils réussissent à passer le processus d’autorisation.

![Accès restreint aux ressources](/help/assets/assets/restricted-access.png)

## Diffusion restreinte utilisant un jeton IMS {#restrict-delivery-ims-token}

Dans Experience Manager Assets, la diffusion limitée via IMS implique deux étapes clés :

* Création
* Diffusion

### Création {#authoring}

Vous pouvez restreindre la diffusion des ressources dans [!DNL Experience Manager] en fonction des rôles. Pour configurer les rôles, procédez comme suit :

1. Accédez à [!DNL Experience Manager] en tant qu’administrateur DAM.
1. Sélectionnez la ressource pour laquelle vous devez configurer le rôle.
1. Accédez à **[!UICONTROL Propriétés]** > **[!UICONTROL Avancé]**, puis assurez-vous que le champ **[!UICONTROL Rôles]** existe dans l’onglet [!UICONTROL Métadonnées avancées].

   ![Métadonnées de rôles](/help/assets/assets/roles_metadata.jpg)
Si le champ n’est pas disponible, procédez comme suit pour ajouter le champ :

   1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
   1. Sélectionnez le schéma de métadonnées et cliquez sur **[!UICONTROL Modifier _(e)_]**.
   1. Ajoutez un champ **[!UICONTROL Texte à plusieurs valeurs]** de la section **[!UICONTROL Créer le formulaire]** dans la partie droite de la section Métadonnées dans le formulaire.
   1. Cliquez sur le champ nouvellement ajouté, puis effectuez les mises à jour suivantes dans le panneau **[!UICONTROL Paramètres]** :
      1. Remplacez le **[!UICONTROL libellé du champ]** par _rôles_.
      1. Mettez à jour la **[!UICONTROL map to property]** vers _./jcr:content/metadata/dam:rôles_.

1. Procurez-vous les groupes IMS à ajouter dans les métadonnées Rôles de la ressource. Pour récupérer les groupes IMS, procédez comme suit :
   1. Se connecter à `https://adminconsole.adobe.com/.`
   1. Accédez à votre organisation respective et accédez à **[!UICONTROL Groupes d’utilisateurs]**.
   1. Sélectionnez le **[!UICONTROL groupe d&#39;utilisateurs]** à ajouter et extrayez les **[!UICONTROL orgID]** et **[!UICONTROL userGroupID]** depuis l&#39;URL ou utilisez votre ID d&#39;organisation tel que `{orgID}@AdobeOrg:{usergroupID}`.

1. Ajoutez l’ID de groupe au champ **[!UICONTROL Rôles]** des propriétés Asset. <br>
Les ID de groupe définis dans le champ **[!UICONTROL Rôles]** sont les seuls utilisateurs qui peuvent accéder à la ressource. Outre l&#39;identifiant de groupe IMS, vous pouvez également ajouter l&#39;identifiant utilisateur IMS et l&#39;identifiant de profil IMS dans le champ **[!UICONTROL Rôles]** . Par exemple, `{orgId}@AdobeOrg:{profileId}`.

   >[!NOTE]
   >
   >Pour la nouvelle vue Assets, vous ne pouvez autoriser l’accès qu’aux niveaux de dossier, et exclusivement aux groupes plutôt qu’aux utilisateurs individuels. En savoir plus sur la [gestion des autorisations dans Experience Manager Assets](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/get-started-admins/folder-access/manage-permissions).

   >[!VIDEO](https://video.tv.adobe.com/v/3427429)

#### Limitation de la diffusion des ressources à l’aide de la date et de l’heure d’activation et de désactivation {#restrict-delivery-assets-date-time}

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



### Diffusion de ressources restreintes {#delivery-restricted-assets}

La diffusion des ressources restreintes repose sur une autorisation réussie d’accès aux ressources. L’autorisation est basée sur un jeton IMS si la requête est envoyée à partir d’une instance d’auteur AEM ou d’un sélecteur de ressources ou sur un cookie spécial si des fournisseurs d’identité personnalisés sont configurés sur votre instance Publish ou Preview.

#### Diffusion pour les demandes d’AEM auteur ou de sélecteur de ressources {#delivery-aem-author-asset-selector}

Pour activer la diffusion de ressources restreintes au cas où la requête serait envoyée à partir de l’instance d’auteur AEM ou du sélecteur de ressources, un jeton IMS valide est essentiel. Procédez comme suit :

1. [Générer un jeton d’accès](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token).
   * Connectez-vous à la console de développement de votre environnement AEM as a Cloud Service.

   * Accédez à **[!UICONTROL Environnement]** > **[!UICONTROL Intégrations]** > **[!UICONTROL Jeton local]** > **[!UICONTROL Obtenir un jeton de développement local]** > **[!UICONTROL Copier la valeur accessToken]**. En savoir plus sur [comment accéder au jeton et aux aspects connexes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token)

1. Intégrez le jeton d’accès obtenu à l’en-tête **[!UICONTROL Authorization]**, en veillant à ce que sa valeur soit précédée du préfixe **[!UICONTROL Bearer]**.

1. Validez la fonctionnalité du jeton d’accès en initiant une requête. Elle doit générer une erreur 404 dans les cas où il n’existe pas de jeton d’accès IMS, ou le jeton d’accès fourni n’a pas les mêmes entités ou groupes que ceux ajoutés dans les métadonnées de la ressource.

#### Diffusion pour les fournisseurs d’identité personnalisés sur une instance Publish {#delivery-custom-identity-provider}

Dans le cas d’un fournisseur d’identité personnalisé configuré sur votre instance Publish ou Preview, vous pouvez mentionner le groupe qui doit avoir accès aux ressources sécurisées dans l’attribut `groupMembership` pendant le processus de configuration. Lorsque vous vous connectez au fournisseur d’identité personnalisé via l’ [intégration SAML](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0), l’attribut `groupMembership` est lu et utilisé pour construire un cookie, qui est envoyé dans toutes les demandes d’authentification, similaire à un jeton IMS en cas de demande de l’auteur AEM ou du sélecteur de ressources.

Lorsqu’une ressource sécurisée est disponible sur une page et qu’une demande est envoyée à l’URL de diffusion pour effectuer le rendu de la ressource, AEM vérifie les rôles présents dans le cookie ou le jeton IMS et la compare à l’élément `dam:roles property` appliqué lors de la création de la ressource. S’il existe une correspondance, la ressource s’affiche.

>[!NOTE]
>
> Dans le [ticket de support pour activer Dynamic Media avec les fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md#how-to-enable-the-dynamic-media-with-openapi-capabilities), mentionnez la diffusion limitée dans le cas d’utilisation. L’ingénierie d’Adobe aidera à apporter les clarifications nécessaires et/ou à mettre en place un processus pour une diffusion limitée.
