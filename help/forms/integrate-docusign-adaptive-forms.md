---
title: Comment intégrer DocuSign à un formulaire adaptatif ?
description: Découvrez comment utiliser DocuSign avec un formulaire adaptatif pour collecter des signatures électroniques.
exl-id: fb2e75d6-e454-4999-a079-f663af79051f
feature: Adaptive Forms, Acrobat Sign
role: User, Developer
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 88%

---

# Utilisation de DocuSign avec un formulaire adaptatif {#integrate-aem-forms-with-DocuSign}

DocuSign est une solution de signature électronique de premier plan. Vous pouvez l’utiliser pour signer un contrat électroniquement. Vous pouvez intégrer DocuSign à un formulaire adaptatif. Il vous permet d’envoyer un formulaire adaptatif à plusieurs destinataires pour qu’ils le signent électroniquement. L’utilisation des signatures électroniques vous permet d’effectuer les opérations suivantes :

- Vous pouvez établir des contrats à partir de tout appareil à l’aide de processus entièrement automatisés d’offre, de devis et de contrat.
- Vous pouvez exécuter plus rapidement les processus de ressources humaines et offrir à vos employés une expérience digitale plus satisfaisante.
- Vous pouvez réduire considérablement les durées des cycles de mise en œuvre des contrats et intégrer plus rapidement vos fournisseurs.

AEM Forms as a Cloud Service fournit une [action d’envoi personnalisée pour DocuSign](#deploy-custom-submit-action). L’action d’envoi vous permet d’envoyer des formulaires adaptatifs pour les signatures électroniques à l’aide des API DocuSign.

| Vous pouvez également utiliser la solution de signature électronique d’Adobe, Adobe Sign, pour signer électroniquement un formulaire adaptatif. AEM Forms est bien plus intégré à Adobe Sign et offre des contrôles bien plus précis tels que la signature séquentielle et parallèle, plusieurs méthodes d’authentification, l’expérience de signature dans un formulaire, etc. Pour plus d’informations, voir [Utilisation d’Adobe Sign dans un formulaire adaptatif](working-with-adobe-sign.md). |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## Conditions préalables {#prerequisites}

Les éléments suivants sont requis pour intégrer DocuSign à AEM Forms :

- un [compte développeur](https://developers.docusign.com/platform/account/) DocuSign ;
- une application DocuSign ;
- les informations d’identification (ID client et clé secrète client) de l’application API DocuSign ;
- une [action d’envoi personnalisée et un service cloud pour DocuSign](https://github.com/adobe/aem-forms-docusign-sample) ;
- une [configuration prédéfinie pour les documents d’enregistrement](setup-local-development-environment.md#docker-microservices) (pour l’environnement de développement local uniquement).

## Configuration d’une action d’envoi personnalisée et du service cloud pour DocuSign {#deploy-custom-submit-action}

AEM Forms as a Cloud Service fournit une action d’envoi personnalisée pour DocuSign. L’action d’envoi vous permet d’envoyer des formulaires adaptatifs pour les signatures électroniques à l’aide des API DocuSign. Le code de l’action d’envoi personnalisée est disponible dans le [référentiel git public des exemples d’AEM Forms](https://github.com/adobe/aem-forms-docusign-sample). Vous pouvez déployer le code tel qu’il se présente dans votre environnement AEM Forms ou le personnaliser selon les besoins de votre entreprise.

Suivez les étapes suivantes pour configurer l’action d’envoi personnalisée prête à l’emploi et le service cloud DocuSign :

1. [Clonez votre projet AEM Forms as a Cloud Service](setup-local-development-environment.md#forms-cloud-service-local-development-environment) ou créez un projet [!DNL Experience Manager Forms] as a [!DNL Cloud Service] basé sur l’[archétype AEM 27](https://github.com/adobe/aem-project-archetype) ou une version supérieure. Pour créer un projet [!DNL Experience Manager Forms] as a [!DNL Cloud Service] basé sur l’archétype AEM, suivez les étapes suivantes :
   </br> Ouvrez l’invite de commandes et exécutez la commande ci-après pour créer un projet [!DNL Experience Manager Forms] as a Cloud Service :

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=27 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   Modifiez également `appTitle`, `appId` et `groupId` dans la commande ci-dessus pour refléter votre environnement.

1. Clonez le référentiel [aem-forms-samples](https://github.com/adobe/aem-forms-docusign-sample). Ce référentiel contient une action d’envoi personnalisée pour DocuSign et des détails de configuration pour se connecter au serveur DocuSign.

1. Ouvrez le projet AEM Forms as a Cloud Service créé à l’étape 1 pour le modifier dans l’IDE de votre choix.

1. Ouvrez le projet `[AEM Forms as a Cloud Service project]\pom.xml` pour le modifier et opérer les changements suivants :

   1. Ajoutez le texte suivant à la fin de la balise `<properties>` :

      ```shell
      <repository.location>maven_repository</repository.location>
      ```

   1. Ajoutez le texte suivant à la fin de la balise `<repositories>` :

      ```shell
       <repository>
          <id>project-repository</id>
          <url>file://${project.basedir}/${repository.location}</url>
       </repository>
      ```

      Si la balise `<repositories>` n’existe pas, créez-la sous la balise `<properties>`.

   1. Ajoutez le texte suivant à la fin de la balise `<dependencyManagement>` :

      ```shell
       <dependency>
         <groupId>com.adobe.aemforms.samples</groupId>
         <artifactId>forms.integration.docusign.all</artifactId>
         <type>zip</type>
         <version>1.0.0</version>
       </dependency>
      ```

1. Procédez comme suit dans le fichier `all/pom.xml` disponible dans le dossier du projet Cloud Service :

   1. Ajoutez le texte suivant à la fin de la balise `<embeddeds>` :

      ```shell
       <embedded>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
          <target>/apps/moonlightprodprogram-vendor-packages/application/install</target>
       </embedded>
      ```

   1. Ajoutez le texte suivant à la fin de la balise `<dependencies>` :

      ```shell
       <dependency>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
       </dependency>
      ```

1. Ouvrez l’invite de commandes, accédez à `aem-forms-samples\forms-integration-docusign` (cloné à l’étape 3) et exécutez la commande suivante :

   ```shell
   mvn clean install -Dinstall.dir="<AEM Forms as a Cloud Service project path>/maven_repository"
   ```

   `<AEM Forms as a Cloud Service project path>` fait référence au nom du dossier créé à l’étape 1 de cette procédure.

1. Déployez le projet sur votre environnement de développement local. Vous pouvez utiliser la commande suivante pour effectuer un déploiement sur votre environnement de développement local :

   `mvn -PautoInstallPackage clean install`

   Après avoir suivi ces étapes, vous pouvez afficher une nouvelle action d’envoi personnalisée [Envoyer avec les signatures électroniques DocuSign](#enabledocusign) disponible dans la liste des options d’envoi d’un formulaire adaptatif et d’une [configuration du service cloud DocuSign](#configure-docusign-with-aem-forms) dans votre environnement de développement local.

1. Compilez et [déployez le code sur votre environnement [!DNL AEM Forms] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=fr#customer-releases).

## Intégration de [!DNL DocuSign] à [!DNL AEM Forms] {#configure-docusign-with-aem-forms}

Une fois les prérequis réunis, procédez comme suit pour intégrer [!DNL DocuSign] à [!DNL AEM Forms] sur les instances de création.

1. Accédez à **[!UICONTROL Outils]** ![marteau](assets/hammer.png) > **[!UICONTROL Services cloud]** > **[!UICONTROL DocuSign]** et sélectionnez un dossier pour héberger la configuration.

1. Sur la page des configurations, sélectionnez **[!UICONTROL Créer]** pour créer [!DNL DocuSign] configuration dans AEM Forms.
1. Dans l’onglet **[!UICONTROL Général]** de la page **[!UICONTROL Créer une configuration DocuSign]**, spécifiez un **[!UICONTROL Nom]** pour la configuration, puis sélectionnez **[!UICONTROL Suivant]**. Vous pouvez éventuellement spécifier un **[!UICONTROL Titre]**.

1. Copiez l’URL dans la fenêtre active du navigateur dans un bloc-notes. L’URL est nécessaire pour configurer l’application [!DNL DocuSign] avec [!DNL AEM Forms] à une étape ultérieure.

1. Configurez les paramètres OAuth pour l’application [!DNL DocuSign] :

   1. Ouvrez une fenêtre de navigateur et connectez-vous au [compte de développeur [!DNL DocuSign]](https://admindemo.docusign.com/apps-and-keys).
   1. Ouvrez l’application configurée pour [!DNL AEM Forms].
   1. Dans la zone **[!UICONTROL URL de redirection]**, ajoutez l’URL copiée à l’étape précédente et cliquez sur **[!UICONTROL Enregistrer]**.
   1. Notez la clé d’intégration et la clé secrète.

   Pour obtenir des informations détaillées sur la configuration des paramètres OAuth pour une application [!DNL DocuSign] et l’obtention des clés, voir [Configuration des paramètres oAuth pour l’application](https://support.docusign.com/guides/ndse-admin-guide-api-and-keys) dans la documentation du développeur.

1. Revenez à la page **[!UICONTROL Créer une configuration DocuSign]**. Dans l’onglet **[!UICONTROL Paramètres]**, le champ **[!UICONTROL URL OAuth]** indique l’URL suivante par défaut :

   `https://account-d.docusign.com/oauth/auth`

1. Spécifiez l’**[!UICONTROL ID client]** (la clé d’intégration DocuSign) et la **[!UICONTROL Secret client]** (clé secrète DocuSign).

1. Sélectionnez **[!UICONTROL Connexion à DocuSign]**. Lorsque vous êtes invité à fournir vos informations d’identification, indiquez le nom d’utilisateur et le mot de passe du compte utilisé lors de la création de l’application [!DNL DocuSign]. Lorsque vous êtes invité à confirmer l’accès à `your developer account`, cliquez sur **[!UICONTROL Autoriser l’accès]**. Si les informations d’identification sont correctes, un message de réussite s’affiche.

1. Sélectionnez **[!UICONTROL Créer]** pour créer la configuration [!DNL DocuSign].

1. Sélectionnez la configuration, cliquez sur **[!UICONTROL Publier]**, sélectionnez la configuration, puis cliquez sur **[!UICONTROL Publier]**. La configuration sera ainsi répliquée sur les environnements de publication correspondants.

1. Répétez toutes les étapes ci-dessus sur vos instances de développement, d’évaluation ou de production (toutes celles non encore configurées) pour terminer la configuration d’[!DNL DocuSign] avec [!DNL AEM Forms] pour votre environnement.

Désormais, votre environnement AEM Forms est configuré pour utiliser DocuSign. Veillez à ajouter le conteneur de configurations utilisé pour le service cloud à tous les formulaires adaptatifs activés pour [!DNL DocuSign]. Vous pouvez spécifier un conteneur de configurations à partir des propriétés d’un formulaire adaptatif.

### Utilisation de [!DNL DocuSign] dans un formulaire adaptatif {#enabledocusign}

Vous pouvez activer [!DNL DocuSign] pour un formulaire adaptatif existant ou créer un formulaire adaptatif prenant en charge [!DNL DocuSign]. Choisissez l’une des méthodes suivantes :

- [Création d’un formulaire adaptatif prenant en charge [!DNL DocuSign] &#x200B;](#create-an-adaptive-form-for-docusign)
- [Activation d’ [!DNL DocuSign]  pour un formulaire adaptatif existant](#editafsign)

#### Création d’un formulaire adaptatif pour DocuSign {#create-an-adaptive-form-for-docusign}

Pour créer un formulaire adaptatif prenant en charge les signatures :

1. Accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Sélectionnez **[!UICONTROL Créer]** et **[!UICONTROL Formulaire adaptatif]**. Une liste de modèles s’affiche. Sélectionnez un modèle, puis sélectionnez **[!UICONTROL Suivant]**.
1. Dans l’onglet **[!UICONTROL De base]** :

   1. Précisez les **[!UICONTROL Nom]** et **[!UICONTROL Titre]** pour le formulaire adaptatif.

   1. Sélectionnez le [conteneur de configurations](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) créé lors de l’ [!DNL DocuSign] intégration d’[&#x200B; à [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).

   Le conteneur de configurations contient les services [!DNL DocuSign] Cloud Services configurés pour votre environnement. Ces services peuvent être sélectionnés dans le créateur de formulaires adaptatifs.

1. Dans l’onglet **[!UICONTROL Modèle de formulaire]**, sélectionnez l’une des options suivantes :

   - Si vous disposez d’un modèle de formulaire personnalisé et que vous avez besoin d’un document d’enregistrement basé sur le modèle de formulaire, sélectionnez l’option **[!UICONTROL Associer le modèle de formulaire en tant que modèle de document d’enregistrement]**, puis un modèle de document d’enregistrement. Lorsque vous utilisez cette option, les documents envoyés pour signature n’affichent que les champs basés sur le modèle de formulaire associé. Ils n’affichent pas tous les champs du formulaire adaptatif.

   - Si vous ne disposez pas d’un modèle de formulaire personnalisé, sélectionnez l’option **[!UICONTROL Générer un document d’enregistrement]**. Lorsque vous utilisez cette option, le document envoyé pour signature affiche tous les champs du formulaire adaptatif.

1. Sélectionnez **[!UICONTROL Créer]**. Un formulaire adaptatif prenant en charge les signatures est créé. Vous pouvez y ajouter vos champs [!DNL DocuSign] et envoyer le formulaire pour signature.
1. Ouvrez le formulaire adaptatif en mode d’édition. Dans l’onglet **[!UICONTROL Contenu]**, sélectionnez le **[!UICONTROL Conteneur de formulaires]** et sélectionnez ![Configurer](assets/configure-icon.svg).

1. Dans la section **[!UICONTROL Envoi]**, sélectionnez **[!UICONTROL Envoyer avec les signatures électroniques DocuSign]** dans la liste déroulante **[!UICONTROL Action d’envoi]**.

1. Dans la section **[!UICONTROL Configuration d’action]**, sélectionnez **[!UICONTROL Ajouter]** pour ajouter un destinataire et indiquer son adresse e-mail. Sélectionnez à nouveau **[!UICONTROL Ajouter]** pour ajouter d’autres destinataires.

1. Indiquez l’objet de l’e-mail dans le champ **[!UICONTROL Objet du message]**. Sélectionnez **Inclure des pièces jointes** pour inclure des pièces jointes à l’e-mail.

1. Sélectionnez ![Enregistrer](assets/save_icon.svg) pour enregistrer les propriétés.

#### Activation d’[!DNL DocuSign] pour un formulaire adaptatif {#editafsign}

Pour utiliser [!DNL DocuSign] dans un formulaire adaptatif existant :

1. Accédez à **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents]**.
1. Sélectionnez le formulaire adaptatif, puis sélectionnez **[!UICONTROL Propriétés]**.
1. Dans l’onglet **[!UICONTROL De base]**, sélectionnez le [conteneur de configurations](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) créé lors de l’intégration d’[!DNL DocuSign] à [!DNL AEM Forms].
1. Dans l’onglet **[!UICONTROL Modèle de formulaire]**, sélectionnez l’une des options suivantes :

   - Si vous disposez d’un modèle de formulaire personnalisé et que vous avez besoin d’un document d’enregistrement basé sur le modèle de formulaire, sélectionnez l’option **[!UICONTROL Associer le modèle de formulaire en tant que modèle de document d’enregistrement]**, puis un modèle de document d’enregistrement. Lorsque vous utilisez cette option, les documents envoyés pour signature n’affichent que les champs basés sur le modèle de formulaire associé. Ils n’affichent pas tous les champs du formulaire adaptatif.

   - Si vous ne disposez pas d’un modèle de formulaire personnalisé, sélectionnez l’option **[!UICONTROL Générer un document d’enregistrement]**. Lorsque vous utilisez cette option, le document envoyé pour signature affiche tous les champs du formulaire adaptatif.

1. Sélectionnez **[!UICONTROL Enregistrer et fermer]**. Le formulaire adaptatif est activé pour [!DNL DocuSign]. Vous pouvez maintenant y ajouter vos champs [!DNL DocuSign] et envoyer le formulaire pour signature.

1. Ouvrez le formulaire adaptatif en mode d’édition. Dans l’onglet **[!UICONTROL Contenu]**, sélectionnez le **[!UICONTROL Conteneur de formulaires]** et sélectionnez ![Configurer](assets/configure-icon.svg).

1. Dans la section **[!UICONTROL Envoi]**, sélectionnez **[!UICONTROL Envoyer avec les signatures électroniques DocuSign]** dans la liste déroulante **[!UICONTROL Action d’envoi]**.

1. Dans la section **[!UICONTROL Configuration d’action]**, sélectionnez **[!UICONTROL Ajouter]** pour ajouter un destinataire et indiquer son adresse e-mail. Sélectionnez à nouveau **[!UICONTROL Ajouter]** pour ajouter d’autres destinataires.

1. Indiquez l’objet de l’e-mail dans le champ **[!UICONTROL Objet du message]**. Sélectionnez **Inclure des pièces jointes** pour inclure des pièces jointes à l’e-mail.

1. Sélectionnez ![Enregistrer](assets/save_icon.svg) pour enregistrer les propriétés.
