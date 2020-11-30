---
title: Intégration à Adobe Target
description: 'Intégration à Adobe Target '
translation-type: tm+mt
source-git-commit: 7d3b5199333a60d69957819d874f8ce1bafdd797
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 15%

---


# Intégration à Adobe Target{#integrating-with-adobe-target}

Dans le cadre d’Adobe Marketing Cloud, Adobe Target vous permet d’améliorer la pertinence du contenu en effectuant un ciblage et des mesures sur tous les canaux. L&#39;intégration de l&#39;Adobe Target et de l&#39;AEM en tant que Cloud Service nécessite :

* à l’aide de l’interface utilisateur tactile pour créer une configuration de Cible dans AEM en tant que Cloud Service (configuration IMS requise).
* adding and configuring Adobe Target as an extension in [Adobe Launch](https://docs.adobe.com/content/help/fr-FR/launch/using/intro/get-started/quick-start.html).

Le lancement d’Adobe est nécessaire pour gérer les propriétés côté client pour Analytics et la Cible dans les pages AEM (bibliothèques/balises JS). Ceci dit, l’intégration avec le lancement est nécessaire pour le &quot;ciblage d’expérience&quot;. Pour l’exportation des fragments d’expérience vers la Cible, vous n’avez besoin que de la configuration Adobe Target et IMS.

>[!NOTE]
>
>Les clients Adobe Experience Manager as a Cloud Service qui ne disposent pas d’un compte Target existant peuvent demander l’accès au package Target Foundation pour Experience Cloud. Le package Foundation offre une utilisation limitée en volume de Target.

## Creating the Adobe Target Configuration {#create-configuration}

1. Accédez à **Outils** 	 **Cloud Services**.
   ![](assets/cloudservice1.png "NavigationNavigation")
2. Sélectionnez **Adobe Target**.
3. Cliquez sur le bouton **Créer**.
   ![](assets/tenant1.png "CreateCreate")
4. Fill in the details (see below), and select **Connect**.
   ![](assets/open_screen1.png "ConnectConnect")

### Configuration IMS

Une configuration IMS pour le lancement et la Cible est nécessaire pour intégrer correctement la Cible à AEM et au lancement. Bien que la configuration IMS pour Launch soit préconfigurée en AEM en tant que Cloud Service, la configuration IMS de Cible doit être créée (une fois la Cible configurée). Reportez-vous à [cette vidéo](https://helpx.adobe.com/experience-manager/kt/sites/using/aem-sites-target-standard-technical-video-understand.html) et à [cette page](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/integration-ims-adobe-io.html) pour savoir comment créer la configuration IMS de la Cible.

### Modification de la configuration de la Cible {#edit-target-configuration}

Pour modifier la configuration de la Cible, procédez comme suit :

1. Sélectionnez une configuration existante et cliquez sur **Propriétés**.
2. Modifiez les propriétés.
3. Select **Re-connect to Adobe Target**.
   ![Re-](assets/edit_config_page1.png "connectRe-connect")
4. Sélectionnez **Enregistrer et fermer**.

### Ajout d’une configuration à un site {#add-configuration}

To apply a Touch UI configuration to a site, go to: **Sites** → **Select any site page** → **Properties** → **Advanced** → **Configuration** → Select the configuration tenant.

## Integrating Adobe Target on AEM sites by using Adobe Launch {#integrate-target-launch}

aem offres et intégration immédiate avec l’Experience Platform Launch. En ajoutant l&#39;extension Adobe Target à l&#39;Experience Platform Launch, vous pouvez utiliser les fonctionnalités de Adobe Target sur AEM page Web.Les bibliothèques de Cible ne seront rendues qu&#39;à l&#39;aide de Launch.

>[!NOTE]
>
>Les frameworks existants (hérités) fonctionnent toujours, mais ne peuvent pas être configurés dans l’interface utilisateur tactile. Il est conseillé de recréer les configurations de mappage de variables dans Launch.

En général, les étapes d’intégration sont les suivantes :

1. Créer une propriété Launch
2. Ajouter les extensions requises
3. Création d’un élément de données (pour capturer les paramètres du hub contextuel)
4. Créer une règle de page
5. Création et publication

### Creating a Launch Property {#create-property}

Une propriété est un conteneur qui sera rempli d’extensions, de règles et d’éléments de données.

1. Sélectionnez le bouton **Nouvelle propriété** .
2. Attribuez un nom à votre propriété.
3. Au fur et à mesure que le domaine entre l’adresse IP/l’hôte sur lequel vous souhaitez charger la bibliothèque de lancement.
4. Select the **Save** button.
   ![](assets/properties_newproperty1.png "LaunchpropertyLaunchproperty")

### Ajouter les extensions requises {#add-extension}

**Les extensions** sont le conteneur qui gère les paramètres de bibliothèque principaux. L’extension Adobe Target prend en charge les implémentations côté client en utilisant le SDK JavaScript Cible pour le Web moderne at.js. Vous devez ajouter les extensions **Adobe Target** et **Adobe ContextHub** .

1. Sélectionnez l’option Catalogue des extensions, puis recherchez la Cible dans le filtre.
2. Sélectionnez **Adobe Target** at.js et cliquez sur l’option Installer.
   ![Cible Recherche](assets/search_ext1.png "SearchTarget")
3. Select the **Configure** button. Notez la fenêtre de configuration avec les informations d’identification du compte de Cible importées et la version at.js de cette extension.
4. Sélectionnez **Enregistrer** pour ajouter l’Extension de la cible à votre propriété Launch. Vous devriez être en mesure de voir l’Extension de la cible répertoriée sous la liste Extensions **** installées.
   ![Enregistrer](assets/configure_extension1.png "l&#39;extensionEnregistrer l&#39;extension")
5. Répétez les étapes ci-dessus pour rechercher l’extension **Adobe ContextHub** et l’installer (ceci est nécessaire pour l’intégration avec les paramètres contextuels, en fonction desquels le ciblage sera effectué).

### Création d’un élément de données {#data-element}

**Les éléments** de données sont des espaces réservés vers lesquels vous pouvez mapper les paramètres du hub de contexte.

1. Sélectionnez Éléments **** de données.
2. Sélectionnez **Ajouter l’élément** de données.
3. Fournissez le nom de l’élément de données et mappez-le à un paramètre de hub de contexte.
4. sélectionnez **Enregistrer**.
   ![Elément](assets/data_elem1.png "DataElementData")

### Création d’une règle de page {#page-rule}

En **règle** , nous définissons et ordonnons une séquence d’actions qui sera exécutée sur le site, pour atteindre le ciblage.

1. Ajoutez un ensemble d’actions comme illustré dans la capture d’écran.
   ![](assets/rules1.png "ActionsActions")
2. Dans Ajouter les paramètres à toutes les mbox, ajoutez l’élément de données configuré précédemment (voir l’élément de données ci-dessus) au paramètre qui sera envoyé dans l’appel de mbox.
   ![](assets/map_data1.png "MboxActions")

### Création et publication {#build-publish}

Pour savoir comment créer et publier, veuillez consulter cette [page](https://docs.adobe.com/content/help/en/experience-manager-learn/aem-target-tutorial/aem-target-implementation/using-launch-adobe-io.html).

## Modifications de la structure de contenu entre les configurations d’interface utilisateur classique et tactile {#changes-content-structure}

| **Modifier** | **Configuration classique de l’interface utilisateur** | **Configuration de l’interface utilisateur tactile** | **Conséquences** |
|---|---|---|---|
| Emplacement de la configuration de la Cible. | /etc/cloudservices/testandtarget/ | /conf/locataire/settings/cloudservices/cible | Auparavant, plusieurs configurations étaient présentes sous /etc/cloudservices/testandtarget, mais désormais une configuration unique sera présente sous un client. |

>[!NOTE]
>
>Les configurations héritées sont toujours prises en charge pour les clients existants (sans possibilité de modifier ou de créer de nouvelles configurations). Les configurations héritées feront partie des packages de contenu téléchargés par le client à l’aide de VSTS.
