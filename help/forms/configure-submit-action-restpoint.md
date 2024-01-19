---
Title: How to configure submit to Rest Endpoint submit action for an Adaptive Form?
Description: Discover the steps to set up Rest Endpoint when submitting an Adaptive Form.
keywords: Point de terminaison REST AEM Forms, Envoyer au point de terminaison REST, Publier les données vers l’URL REST, Configuration de l’action REST Endpoint
feature: Adaptive Forms, Core Components
source-git-commit: 8784c0bcd05eeae41a472faa5ecad03cbdd8a9b6
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 62%

---


# Configuration d’un formulaire adaptatif pour une action d’envoi point de fin REST

Utilisez la variable **[!UICONTROL Envoyer vers le point de fin REST]** action pour publier les données envoyées vers une URL REST. L’URL peut être celle d’un serveur interne (le serveur sur lequel le formulaire est rendu) ou externe.

AEM as a Cloud Service propose différentes actions d’envoi prêtes à l’emploi pour gérer les envois de formulaire. Pour en savoir plus sur ces options, voir [Action d’envoi de formulaire adaptatif](/help/forms/configure-submit-actions-core-components.md)  article.

## Avantages

Certains des avantages de la configuration de la variable **[!UICONTROL Envoyer vers le point de fin REST]** les actions d’envoi pour Adaptive Forms sont les suivantes :

* Il permet une intégration transparente des données de formulaire avec des systèmes et services externes via les API RESTful.
* Il offre une certaine flexibilité pour gérer les envois de données depuis Forms adaptatif, en prenant en charge des structures de données dynamiques et complexes.
* Il prend en charge le mappage dynamique des champs de formulaire aux paramètres dans l’URL du point de terminaison REST, ce qui permet les envois de données adaptables et personnalisables.


## Configuration de l’action d’envoi Envoyer vers le point de fin REST {#steps-to-configure-submit-to-restendpoint-submit-action}

Pour configurer l’action d’envoi :

1. Ouvrez l’explorateur de contenu, puis sélectionnez le composant **[!UICONTROL Conteneur de guide]** de votre formulaire adaptatif.
1. Cliquez sur l’icône des propriétés du conteneur de guide ![Propriétés du guide](/help/forms/assets/configure-icon.svg). La fenêtre du conteneur de formulaires adaptatifs s’ouvre.
1. Cliquez sur l’onglet **[!UICONTROL Envoi]**.
1. Dans la **[!UICONTROL Action Envoyer]** liste déroulante, sélectionnez **[!UICONTROL Envoyer vers le point de terminaison REST]**.
   ![Configuration des actions du point de fin Submit to Rest](/help/forms/assets/submit-action-restendpoint.png)

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

## Bonnes pratiques

* Lorsque vous publiez des données sur un serveur externe, assurez-vous que l’URL est sécurisée et configurez le chemin pour gérer anonymement la demande du POST afin de protéger les informations sensibles.
* Pour transmettre les champs en tant que paramètres dans une URL REST, tous les champs doivent avoir des noms d’éléments différents, même s’ils sont placés sur différents panneaux.

## Articles connexes

{{af-submit-action}}

