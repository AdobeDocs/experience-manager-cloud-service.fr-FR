---
Title: How to configure submit to Rest Endpoint submit action for an Adaptive Form?
Description: Discover the steps to set up Rest Endpoint when submitting an Adaptive Form.
keywords: Point d’entrée REST AEM Forms, envoyer au point d’entrée REST, publier les données dans l’URL REST, configurer l’action de point d’entrée REST
feature: Adaptive Forms, Core Components
title: Comment configurer une action Envoyer pour un formulaire adaptatif ?
role: User, Developer
source-git-commit: c20b8909bb884f14bd7fe59f190de3cd375a7111
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 56%

---

# Configuration d’un formulaire adaptatif pour l’action d’envoi de point d’entrée REST

Utilisez l’action **[!UICONTROL Envoyer vers le point d’entrée REST]** pour transmettre les données envoyées à l’URL REST. L’URL peut être celle d’un serveur interne (le serveur sur lequel le formulaire est rendu) ou externe.

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaires. Pour en savoir plus sur ces options, consultez l’article [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md).

## Avantages

Voici quelques avantages de la configuration de l’action d’envoi **[!UICONTROL Envoyer vers le point d’entrée REST]** pour le Forms adaptatif :

* Il permet une intégration transparente des données de formulaire aux systèmes et services externes par le biais d’API RESTful.
* Il offre une certaine flexibilité pour gérer les envois de données à partir de Forms adaptatif, en prenant en charge les structures de données dynamiques et complexes.
* Il prend en charge le mappage dynamique des champs de formulaire aux paramètres de l’URL du point d’entrée REST, ce qui permet des envois de données adaptables et personnalisables.


## Configuration de l’action d’envoi Envoyer vers le point d’entrée REST {#steps-to-configure-submit-to-restendpoint-submit-action}

Pour configurer l’action d’envoi en fonction de la spécification de l’API Open Swagger :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Action Envoyer]**, sélectionnez **[!UICONTROL Envoyer vers le point d’entrée REST]**.
   ![Configuration de l’action Envoyer vers le point d’entrée Rest](/help/forms/assets/submit-action-restendpoint.png)

   Pour publier des données sur un serveur interne, indiquez le chemin de la ressource. Les données sont publiées avec le chemin de la ressource. Par exemple, `/content/restEndPoint`. Pour ces requêtes de publication, les informations d’authentification de la requête d’envoi sont utilisées.

   Pour publier des données sur un serveur externe, indiquez une URL. Le format d’URL est le suivant : `https://host:port/path_to_rest_end_point`. Assurez-vous de configurer le chemin pour que la requête POST soit traitée anonymement.

   ![Mappage pour la transmission des valeurs de champs sous forme de paramètres de page de remerciement](assets/post-enabled-actionconfig.png)

   Dans l’exemple ci-dessus, les informations saisies par l’utilisateur dans `textbox` sont capturées au moyen du paramètre `param1`. La syntaxe permettant de publier les données capturées au moyen de `param1` est :

   `String data=request.getParameter("param1");`

   De même, les paramètres que vous utilisez pour publier des données XML et des pièces jointes sont `dataXml` et `attachments`.

   Par exemple, vous utilisez ces deux paramètres dans votre script pour analyser les données à un point d’entrée REST. Vous utilisez la syntaxe suivante pour stocker et analyser les données :

   `String data=request.getParameter("dataXml");`
   `String att=request.getParameter("attachments");`

   Dans cet exemple, `data` contient les données XML et `att` les données des pièces jointes.

   L’option d’envoi **[!UICONTROL Envoyer vers le point d’entrée REST]** transmet les données renseignées dans le formulaire à une page de confirmation configurée dans le cadre de la requête HTTP GET. Vous pouvez ajouter le nom du champ à demander. Le format de la requête est :

   `{fieldName}={request parameter name}`

   Comme illustré ci-dessous, `param1` et `param2` sont transmis en tant que paramètres avec des valeurs copiées à partir des champs **textbox** et **numericbox** pour la prochaine action.

   ![Configuration de l’action Envoyer vers le point d’entrée REST](assets/action-config.png)

   Vous pouvez également **[!UICONTROL Activer la requête POST]** et fournir une URL pour la publication de la requête. Pour envoyer des données au serveur AEM qui héberge le formulaire, utilisez un chemin d’accès relatif correspondant au chemin racine du serveur AEM. Par exemple, `/content/forms/af/SampleForm.html`. Pour envoyer des données vers un autre serveur, utilisez un chemin d’accès absolu.

1. Cliquez sur **[!UICONTROL Terminé]**.

### Configurer l’action d’envoi en fonction du point d’entrée Rest du service {#config-service-endpoint-auth}

<span class="preview"> La fonctionnalité Point d’entrée du service fait partie du programme des utilisateurs et utilisatrices précoces et s’applique uniquement aux composants principaux. Vous pouvez écrire à aem-forms-ea@adobe.com à partir de votre identifiant e-mail officiel pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité. </span>

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la liste déroulante **[!UICONTROL Action Envoyer]**, sélectionnez **[!UICONTROL Envoyer vers le point d’entrée REST]**.
1. Activez la requête de POST.
1. Spécifiez l’URL du point d’entrée REST.
1. Sélectionnez la configuration que vous avez créée pour votre type d’authentification de point d’entrée Rest de service et les types de contenu. Pour en savoir plus sur le type d’authentification et les types de contenu, consultez [configuration des sources de données](/help/forms/configure-data-sources.md#configure-restful-services-using-service-endpoint-configure-restful-services-service-endpoint).
   ![Configuration du point d’entrée Rest](assets/rest-service-endpoint-config.png)
1. Cliquez sur Terminé.

## Bonnes pratiques

* Lors de la publication de données sur un serveur externe, assurez-vous que l’URL est sécurisée et configurez le chemin d’accès pour gérer la demande du POST de manière anonyme afin de protéger les informations sensibles.
* Pour transmettre les champs en tant que paramètres dans une URL REST, tous les champs doivent avoir des noms d’éléments différents, même s’ils sont placés sur différents panneaux.

## Articles connexes

{{af-submit-action}}
