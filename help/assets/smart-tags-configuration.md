---
title: Balises intelligentes améliorées
description: Appliquez des balises commerciales contextuelles et descriptives à l’aide du service AI et ML d’Adobe Sensei afin d’améliorer la découverte de ressources et la vitesse du contenu.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c24fa22178914b1186b7f29bdab64d3bca765fe5
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 97%

---


# Configuration d’Experience Manager pour le balisage intelligent des ressources {#configure-aem-for-smart-tagging}

Le balisage des ressources avec vocabulaire contrôlé par taxonomie permet de s’assurer qu’elles peuvent être facilement identifiées et récupérées au moyen de recherches sur les balises. Adobe fournit des balises intelligentes qui utilisent l’intelligence artificielle et des algorithmes de machine learning pour entraîner des images. Le service de balises intelligentes utilise le framework d’intelligence artificielle d’[Adobe Sensei](https://www.adobe.com/fr/sensei/experience-cloud-artificial-intelligence.html) pour entraîner son algorithme de reconnaissance d’images par rapport à votre structure de balises et votre taxonomie métier.

La fonctionnalité est disponible à l’achat sous la forme d’un module complémentaire d’[!DNL Experience Manager]. Suite à l’achat, un email contenant un lien vers Adobe Developer Console est envoyé à l’administrateur de votre organisation. Celui-ci accède au lien pour intégrer les balises intelligentes dans [!DNL Experience Manager] à l’aide d’Adobe Developer Console.

<!-- TBD: 
1. Can a similar flowchart be created about how training works in CS? ![flowchart](assets/flowchart.gif)
2. Is there a link to buy SCS or initiate a sales call.
3. Keystroke all steps and check all screenshots.
-->

## Intégration avec Adobe Developer Console {#aio-integration}

Avant de pouvoir baliser les images à l’aide de SCS, intégrez [!DNL Adobe Experience Manager] avec le service de balises intelligentes à l’aide d’Adobe Developer Console. En arrière-plan, le serveur [!DNL Experience Manager] authentifie vos informations d’identification du service auprès de la passerelle Adobe Developer Console avant de transférer votre demande au service de balises intelligentes.

* Créez une configuration dans [!DNL Experience Manager] pour générer une clé publique. [Obtenez un certificat public pour l’intégration d’OAuth.](#obtain-public-certificate)
* [Créez une intégration dans Adobe Developer Console et chargez la clé publique générée.](#create-aio-integration)
* [Configurez les balises](#configure-smart-content-service) dynamiques dans votre [!DNL Experience Manager] instance à l’aide de la clé d’API et d’autres informations d’identification d’Adobe Developer Console.
* [Testez la configuration](#validate-the-configuration).
* [Reconfigurer après l’expiration](#certrenew)du certificat.

### Conditions préalables pour l’intégration d’Adobe Developer Console {#prerequisite-for-aio-integration}

Avant de pouvoir utiliser les balises intelligentes, veillez à respecter les conditions suivantes pour créer une intégration sur Adobe Developer Console :

* L’organisation doit disposer d’un compte Adobe ID pourvu de droits d’administrateur.
* Le service de balises intelligentes est activé pour votre organisation.

### Obtention d’un certificat public {#obtain-public-certificate}

Un certificat public permet d’authentifier votre profil sur Adobe Developer Console. Vous créez un certificat dans [!DNL Experience Manager].

1. Dans l’interface utilisateur [!DNL Experience Manager], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Configurations d’Adobe IMS]**.

1. Dans la page [!UICONTROL Configurations d’Adobe IMS], cliquez sur **[!UICONTROL Créer]**. Dans le menu **[!UICONTROL Solution cloud]**, sélectionnez **[!UICONTROL Balises intelligentes]**.

1. Sélectionnez **[!UICONTROL Créer un certificat]**. Indiquez un nom et cliquez sur **[!UICONTROL Créer un certificat]**. Cliquez sur **[!UICONTROL OK]**.

1. Cliquez sur **[!UICONTROL Télécharger la clé publique]**.

   ![Le service de balises intelligentes d’Experience Manager crée une clé publique](assets/aem_smarttags-config1.png)

### Création d’une intégration {#create-aio-integration}

Pour utiliser les balises intelligentes, créez une intégration dans Adobe Developer Console afin de générer une clé API, un identifiant de compte technique, un identifiant d’organisation et un secret de client.

1. Accédez à l’URL [https://console.adobe.io](https://console.adobe.io/) dans un navigateur. Sélectionnez le compte approprié et vérifiez que le rôle d’organisation associé est administrateur système.
1. Créez un projet portant le nom de votre choix. Cliquez sur **[!UICONTROL Add API]** (Ajouter une API).
1. Sur la page **[!UICONTROL Add API]**, sélectionnez **[!UICONTROL Experience Cloud]** puis **[!UICONTROL Smart Content]** (Contenu dynamique). Cliquez sur **[!UICONTROL Next]** (Suivant).
1. Sélectionnez **[!UICONTROL Upload your public key]** (Charger votre clé publique). Fournissez le fichier de certificat téléchargé depuis [!DNL Experience Manager]. Le message [!UICONTROL Public key(s) uploaded successfully] (La ou les clés publiques ont été chargées) s’affiche. Cliquez sur **[!UICONTROL Next]** (Suivant).
1. La page [!UICONTROL Create a new Service Account (JWT) credential] (Créer des informations d’identification de compte de service (JWT)) affiche la clé publique du compte de service qui vient d’être configuré. Cliquez sur **[!UICONTROL Next]** (Suivant).
1. Dans la page **[!UICONTROL Select product profiles]** (Sélectionner les profils de produits), sélectionnez **[!UICONTROL Smart Content Services]** (Services de contenu dynamique). Cliquez sur **[!UICONTROL Save configured API]** (Enregistrer l’API configurée). Une page affiche davantage d’informations sur la configuration. Gardez cette page ouverte pour copier et ajouter ces valeurs lors de la configuration ultérieure des balises intelligentes dans [!DNL Experience Manager].

   ![Dans l’onglet Overview (Aperçu), vous pouvez consulter les informations fournies pour l’intégration.](assets/integration_details.png)

### Configuration des balises intelligentes {#configure-smart-content-service}

Pour configurer l’intégration, utilisez les valeurs des champs Payload (Charge utile), Client Secret (Secret du client), Authorization Server (Serveur d’autorisation) et API key (Clé d’API) de l’intégration Adobe Developer Console.

1. Dans l’interface utilisateur [!DNL Experience Manager], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Configurations d’Adobe IMS]**.
1. Accédez à la page **[!UICONTROL Configuration du compte technique Adobe IMS]** et indiquez le **[!UICONTROL titre]** souhaité.
1. Dans le champ **[!UICONTROL Serveur d’autorisation]**, indiquez l’URL `https://ims-na1.adobelogin.com`.
1. Dans le champ **[!UICONTROL Clé API]**, indiquez l’**[!UICONTROL ID client]** provenant d’[!DNL Adobe Developer Console].
1. Dans le champ **[!UICONTROL Secret du client]**, indiquez le **[!UICONTROL Secret du client]** provenant d’[!DNL Adobe Developer Console]. Cliquez sur l’option **[!UICONTROL Retrieve Client Secret]** (Récupérer le secret du client) pour l’afficher.
1. Dans [!DNL Adobe Developer Console], dans votre projet, cliquez sur **[!UICONTROL Service Account (JWT)]** (Compte de service (JWT)) dans la marge de gauche. Cliquez sur l’onglet **[!UICONTROL Generate JWT]** (Générer le jeton JWT). Cliquez sur **[!UICONTROL Copy]** (Copier) pour copier la **[!UICONTROL JWT Payload]** (Charge utile JWT) affichée. Indiquez cette valeur dans le champ **[!UICONTROL Charge utile]** d’[!DNL Experience Manager]. Cliquez sur **[!UICONTROL Créer]**.

### Validation de la configuration {#validate-the-configuration}

Une fois la configuration terminée, procédez comme suit pour la valider.

1. Dans l’interface utilisateur [!DNL Experience Manager], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Configurations d’Adobe IMS]**.

1. Sélectionnez la configuration des balises intelligentes. Cliquez sur **[!UICONTROL Contrôle de l’intégrité]** dans la barre d’outils. Cliquez sur **[!UICONTROL Vérifier]**. Une boîte de dialogue contenant le message [!UICONTROL Configuration intègre] confirme que la configuration fonctionne.

![Validation de la configuration des balises intelligentes](assets/smart-tag-config-validation.png)

### Reconfiguration si un certificat atteint sa date d’expiration {#certrenew}

Lorsque le certificat expire, il n’est plus approuvé. Pour ajouter un nouveau certificat, procédez comme suit. Vous ne pouvez pas renouveler un certificat ayant expiré.

1. Connectez-vous en tant qu’administrateur à votre déploiement [!DNL Experience Manager]. Cliquez sur **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Utilisateurs]**.

1. Recherchez et cliquez sur l’utilisateur **[!UICONTROL dam-update-service]**. Cliquez sur l’onglet **[!UICONTROL KeyStore]**.
1. Supprimez le fichier de stockage de clés **[!UICONTROL similaritysearch]** existant avec le certificat arrivé à expiration. Cliquez sur **[!UICONTROL Enregistrer et fermer]**.

   ![Suppression d’une entrée similaritysearch existante dans le Keystore pour ajouter un nouveau certificat de sécurité](assets/smarttags_delete_similaritysearch_keystore.png)

   *Figure : Suppression d’une entrée existante`similaritysearch`dans le Keystore pour ajouter un nouveau certificat de sécurité.*

1. Dans l’interface utilisateur [!DNL Experience Manager], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Sécurité]** > **[!UICONTROL Configurations d’Adobe IMS]**. Ouvrez la configuration des balises intelligentes disponible. Pour télécharger un certificat public, cliquez sur **[!UICONTROL Télécharger le certificat public]**.

1. Accédez à [https://console.adobe.io](https://console.adobe.io), puis au service existant dans le projet. Chargez le nouveau certificat et configurez-le. Pour plus d’informations sur la configuration, voir les instructions contenues dans [Création d’une intégration dans Adobe Developer Console](#create-aio-integration).

## Activation du balisage intelligent pour les ressources qui viennent d’être chargées (facultatif) {#enable-smart-tagging-for-uploaded-assets}

1. Dans [!DNL Experience Manager], accédez à **[!UICONTROL Outils > Processus > Modèles]**.
1. Sur la page **[!UICONTROL Modèles de processus]**, sélectionnez le modèle de processus **[!UICONTROL Ressources de mise à jour de gestion des actifs numériques]**.
1. Cliquez sur **[!UICONTROL Modifier]** dans la barre d’outils.
1. Développez le panneau latéral pour afficher les étapes. Faites glisser l’étape **[!UICONTROL Balisage intelligent de la ressource]** disponible dans la section Processus de DAM (gestion des actifs numériques) et placez-la après l’étape **[!UICONTROL Miniatures des processus]**.

   ![Ajout de l’étape Balisage intelligent de la ressource après l’étape Miniatures des processus dans le processus Ressources de mise à jour de gestion des actifs numériques](assets/chlimage_1-105.png)

   *Figure : Ajout de l’étape Balisage intelligent de la ressource après l’étape Miniatures des processus dans le processus Ressources de mise à jour de gestion des actifs numériques.*

1. Ouvrez l’étape à configurer. Dans **[!UICONTROL Paramètres avancés]**, vérifiez que l’option **[!UICONTROL Avance du gestionnaire]** est sélectionnée.

   ![Paramétrage pour permettre au gestionnaire d’avancer à l’étape suivante du processus.](assets/smart-tags-workflow-handler-setting.png)

1. Dans l’onglet **[!UICONTROL Arguments]**, sélectionnez **[!UICONTROL Ignorer les erreurs]** si vous souhaitez que le processus ignore les échecs lors de la prédiction des balises. Pour baliser les ressources lors de leur chargement, et ce, que le balisage intelligent soit activé ou non dans les dossiers, cochez la case **[!UICONTROL Ignorer l’indicateur de balise intelligente]**.

1. Cliquez sur **[!UICONTROL OK]** pour fermer l’étape du processus, puis enregistrez ce dernier. Cliquez sur **[!UICONTROL Synchroniser]**.

>[!MORELIKETHIS]
>
>* [Balisage de ressources à l’aide du service de balises intelligentes](smart-tags.md)

