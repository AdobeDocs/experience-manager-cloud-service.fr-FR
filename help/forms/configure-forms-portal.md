---
title: Comment créer un portail Formulaires sur une page Experience Manager Sites
description: Découvrez comment créer un portail Formulaires et utiliser les composants principaux prêts à l’emploi sur une page AEM Sites.
exl-id: 13cfe3ba-2e85-46bf-a029-2673de69c626
source-git-commit: 05bdc24974d2b82c1350bf6f75873cd7027f7d4a
workflow-type: ht
source-wordcount: '1764'
ht-degree: 100%

---

# Création d’une liste de formulaires adaptatifs sur un portail {#publish-forms-on-portal}

Dans les scénarios typiques de déploiement de portail basés sur l’utilisation de formulaires, le développement des formulaires et le développement du portail sont deux activités bien distinctes. Tandis que les créateurs de formulaires créent des formulaires et les stockent dans un référentiel, les développeurs Web créent une application Web permettant de répertorier les formulaires et de gérer leurs envois. Les formulaires sont copiés sur la plateforme Web car il n’existe aucune communication entre le référentiel des formulaires et l’application Web.

Ces scénarios entraînent généralement des problèmes de gestion et des retards de production. Par exemple, lorsqu’une nouvelle version d’un formulaire est disponible dans le référentiel, vous devez remplacer le formulaire sur la plateforme Web, modifier l’application Web, puis déployer à nouveau le formulaire sur le site public. Le redéploiement de l’application Web risque d’entraîner un temps d’arrêt au niveau du serveur. En règle générale, les temps d’arrêt de serveur sont dus à une activité planifiée et, par conséquent, les modifications ne peuvent pas être transférées au site public instantanément.

AEM Forms fournit des composants de portail qui réduisent les frais de gestion et les délais de production. Les composants permettent aux développeurs Web de créer et de personnaliser un portail Formulaires sur les sites Web créés à l’aide d’Adobe Experience Manager (AEM).

Les composants du portail Formulaires vous permettent d’ajouter les fonctionnalités suivantes :

* Créez une liste de formulaires dans des mises en page personnalisées. D’emblée, les mises en page Vue Liste et Vue Vignette sont fournies. Vous pouvez créer vos propres mises en page personnalisées.
* Vous permet d’afficher des métadonnées et des actions personnalisées tout en les répertoriant.
* Créez des listes de formulaires publiés par l’interface utilisateur d’AEM Forms sur l’instance de publication où sont utilisés les composants du portail Formulaires.
* Autorisez les utilisateurs finaux à afficher les formulaires aux formats HTML et PDF.
* Recherchez des formulaires en fonction du titre et de la description.
* Utilisez des feuilles CSS personnalisées pour la personnalisation de l’apparence du portail.
* Créez des liens vers des formulaires.
* Énumèrez les versions préliminaires et les envois associés aux formulaires adaptatifs créés par l’utilisateur final.

## Composants d’une page du portail Formulaires {#forms-portal-components}

AEM Forms fournit les composants de portail suivants prêts à l’emploi :

* Recherche et énumérateur : ce composant vous permet d’énumérer les formulaires du référentiel de formulaires sur la page du portail et propose des options de configuration pour énumérer les formulaires selon des critères spécifiés.

* Brouillons et envois : alors que le composant Recherche et énumérateur affiche les formulaires rendus publics par l’auteur de formulaires, le composant Brouillons et envois affiche les formulaires enregistrés en tant que brouillons en vue d’être remplis ultérieurement et les formulaires envoyés. Ce composant offre un environnement personnalisé à tout utilisateur connecté.

* Link : ce composant vous permet de créer un lien vers un formulaire depuis n’importe quel emplacement sur la page.

Vous pouvez [importer les composants prêts à l’emploi du portail Formulaires](#import-forms-portal-components-aem-archetype) à partir de l’archétype de projet AEM. Après l’importation, effectuez les configurations suivantes :
* [Configuration d’un stockage externe](#configure-azure-storage-adaptive-forms)
* [Activation des composants du portail Formulaires](#enable-forms-portal-components)
* [Configuration des composants du portail Formulaires](#configure-forms-portal-components)

## Importation des composants du portail Formulaires {#import-forms-portal-components-aem-archetype}

Pour importer des composants du portail Formulaires prêts à l’emploi sur AEM Forms as a Cloud Service, procédez comme suit :

1. **Clonez le référentiel Git Cloud Manager sur votre instance de développement locale** : votre référentiel Git Cloud Manager contient un projet AEM par défaut. Il est basé sur l’[archétype AEM](https://github.com/adobe/aem-project-archetype/). Clonez votre référentiel Git Cloud Manager à l’aide de la gestion de compte Git en libre-service depuis l’interface utilisateur de Cloud Manager pour intégrer le projet à votre environnement de développement local. Pour plus d’informations sur l’accès au référentiel, consultez [Accès aux référentiels](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html?lang=fr).

1. **Créez un projet [!DNL Experience Manager Forms] as a [Cloud Service] :** créez un projet [!DNL Experience Manager Forms] as a [Cloud Service] basé sur [AEM Archetype 27](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-27) ou une version ultérieure. L’archétype permet aux développeurs de commencer facilement le développement pour [!DNL AEM Forms] as a Cloud Service. Il comprend également des exemples de thème et de modèle pour vous aider à démarrer rapidement.

   Pour créer un projet [!DNL Experience Manager Forms] as a Cloud Service, ouvrez l’invite de commande et exécutez la commande ci-dessous. Pour inclure des configurations, des thèmes et des modèles spécifiques à [!DNL Forms], définissez `includeForms=y`.

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=30 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   Modifiez également `appTitle`, `appId` et `groupId` dans la commande ci-dessus pour refléter votre environnement.

   Une fois que le projet est prêt, mettez à jour la propriété `<core.forms.components.version>x.y.z</core.forms.components.version>` dans le niveau supérieur `pom.xml` de l’archétype du projet pour refléter la dernière version des [core-forms-components](https://github.com/adobe/aem-core-forms-components) dans votre `AEM Archetype` projet.

1. **Déploiement du projet dans votre environnement de développement local :** vous pouvez utiliser la commande suivante pour effectuer un déploiement dans votre environnement de développement local.

   `mvn -PautoInstallPackage clean install`

   Pour obtenir la liste complète des commandes, voir [Création et installation](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=fr#building-and-installing).

1. [Déployez le code dans votre environnement [!DNL AEM Forms] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=fr#embeddeds).


## Configurer le stockage Azure pour les formulaires adaptatifs {#configure-azure-storage-adaptive-forms}

[[!DNL Experience Manager Forms] Intégration de données](data-integration.md) fournit une configuration de stockage [!DNL Azure] pour intégrer des formulaires aux services de stockage [!DNL Azure]. Le modèle de données de formulaire peut être utilisé pour créer des formulaires adaptatifs qui interagissent avec un serveur [!DNL Azure] pour activer des workflows d’entreprise.

### Créer une configuration de stockage Azure {#create-azure-storage-configuration}

Avant d’exécuter ces étapes, vérifiez que vous disposez d’un compte de stockage Azure et d’une clé d’accès pour autoriser l’accès au compte de stockage [!DNL Azure].

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Stockage Azure]**.
1. Sélectionnez un dossier pour créer la configuration et appuyez sur **[!UICONTROL Créer]**.
1. Indiquez un titre pour la configuration dans le champ **[!UICONTROL Titre]**.
1. Indiquez le nom du compte de stockage [!DNL Azure] dans le champ **[!UICONTROL Compte de stockage Azure]**.

### Configurer le connecteur de stockage unifié pour le portail Formulaires {#configure-usc-forms-portal}

Suivez les étapes suivantes pour configurer le connecteur de stockage unifié pour les workflows AEM :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Connecteur de stockage unifié]**.
1. Dans la section **[!UICONTROL Portail Formulaires]**, sélectionnez **[!UICONTROL Azure]** dans la liste déroulante **[!UICONTROL Stockage]**.
1. Spécifiez le [chemin de configuration pour la configuration de stockage Azure](#create-azure-storage-configuration) dans le champ **[!UICONTROL Chemin de configuration de stockage]**.
1. Appuyez sur **[!UICONTROL Publier]**, puis sur **[!UICONTROL Enregistrer]** pour enregistrer la configuration.

## Activer les composants du Portail Formulaires {#enable-forms-portal-components}

Pour utiliser n’importe quel composant principal (y compris les composants de portail prêts à l’emploi) dans un site Adobe Experience Manager (AEM), vous devez créer un composant proxy et l’activer pour votre site. Pour créer un composant proxy et activer les composants de portail, voir [Utilisation des composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html?lang=fr#create-proxy-components).

Une fois qu’un composant de portail est activé, vous pouvez l’utiliser dans l’instance de création de votre page de sites.

## Ajouter et configurer des composants du Portail Formulaires {#configure-forms-portal-components}

Vous pouvez créer et personnaliser le Portail Formulaires sur les sites web créés à l’aide d’AEM en ajoutant et en configurant les composants du portail. Assurez-vous que les [composants sont activés](#enable-forms-portal-components) avant de les utiliser dans le Portail Formulaires.

Pour ajouter un composant, faites-le glisser du panneau Composants vers le conteneur de dispositions sur la page ou appuyez sur l’icône Ajouter du conteneur de dispositions et ajoutez-le depuis la boîte de dialogue [!UICONTROL Insérer un nouveau composant].

### Configuration du composant Brouillons et envois {#configure-drafts-submissions-component}

Le composant Brouillons et envois affiche les formulaires enregistrés en tant que brouillons en vue d’être remplis ultérieurement et les formulaires envoyés. Pour configurer, appuyez sur le composant, puis sur l’![icône Configurer](assets/configure_icon.png). Dans la boîte de dialogue [!UICONTROL Brouillons et envois], spécifiez le titre pour indiquer la liste des formulaires en tant que brouillons ou formulaires envoyés. Indiquez également si le composant doit énumérer les brouillons de formulaires ou les formulaires envoyés au format vignette ou liste.

![Icône Brouillons](assets/drafts-component.png)

![Icône Envois](assets/submission-listing.png)

### Configuration du composant Recherche et énumérateur {#configure-search-lister-component}

Le composant Recherche et énumérateur est utilisé pour énumérer les formulaires adaptatifs sur une page et pour implémenter la recherche sur les formulaires énumérés.

![Icône Recherche et énumérateur](assets/search-and-lister-component.png)

Pour configurer, appuyez sur le composant, puis appuyez sur l’![icône Configurer](assets/configure_icon.png). La boîte de dialogue [!UICONTROL Recherche et énumérateur] s’ouvre.

1. Dans l’onglet [!UICONTROL Affichage], configurez ce qui suit :
   * Dans **[!UICONTROL Titre]**, spécifiez le titre du composant Recherche et énumérateur. Un titre indicatif permet aux utilisateurs d’effectuer une recherche rapide dans la liste des formulaires.
   * Dans la liste **[!UICONTROL Disposition]**, sélectionnez la disposition pour représenter les formulaires au format vignette ou liste.
   * Sélectionnez **[!UICONTROL Masquer la recherche]** et **[!UICONTROL Masquer le tri]** pour masquer les fonctionnalités de recherche et de tri.
   * Dans **[!UICONTROL Info-bulle]**, fournissez l’info-bulle qui s’affiche lorsque vous placez le pointeur de la souris sur le composant.
1. Dans l’onglet [!UICONTROL Dossier de ressources], indiquez l’emplacement à partir duquel les formulaires sont extraits et énumérés sur la page. Vous pouvez configurer plusieurs emplacements de dossiers.
1. Dans l’onglet [!UICONTROL Résultats], configurez le nombre maximum de formulaires à afficher par page. La valeur par défaut est de huit formulaires par page.

### Configurer le composant Lien {#configure-link-component}

Le composant Lien vous permet de fournir des liens vers un formulaire adaptatif sur la page. Pour configurer, appuyez sur le composant, puis appuyez sur l’![icône Configurer](assets/configure_icon.png). La boîte de dialogue [!UICONTROL Modifier le composant Lien] s’ouvre.

1. Dans l’onglet [!UICONTROL Affichage], fournissez la légende du lien et l’info-bulle pour faciliter l’identification des formulaires représentés par le lien.
1. Dans l’onglet [!UICONTROL Informations sur les ressources], spécifiez le chemin d’accès au référentiel où la ressource est stockée.
1. Dans l’onglet [!UICONTROL Paramètres de requête], spécifiez les paramètres supplémentaires au format de paire clé-valeur. Lorsqu’un clic est effectué sur le lien, ces paramètres supplémentaires sont transmis avec le formulaire.

## Configuration de l’envoi de formulaire asynchrone à l’aide d’Adobe Sign {#configure-asynchronous-form-submission-using-adobe-sign}

Vous pouvez configurer pour envoyer un formulaire adaptatif uniquement lorsque tous les destinataires ont terminé la cérémonie de signature. Suivez les étapes ci-dessous pour configurer le paramètre à l’aide d’Adobe Sign.

1. Dans l’instance de création, ouvrez un formulaire adaptatif en mode d’édition.
1. Dans le volet de gauche, appuyez sur l’icône Propriétés et développez l’option **[!UICONTROL SIGNATURE ÉLECTRONIQUE]**.
1. Sélectionnez **[!UICONTROL Activer Adobe Sign]**. Différentes options de configuration s’affichent.
1. Dans la section [!UICONTROL Envoyer le formulaire], sélectionnez l’option **[!UICONTROL après que chaque destinataire a terminé la cérémonie de signature]** pour configurer l’action Envoyer le formulaire, où le formulaire est d’abord envoyé à tous les destinataires pour signature. Une fois que tous les destinataires ont signé le formulaire, le formulaire est envoyé.

## Enregistrement des formulaires adaptatifs en tant que brouillons {#save-adaptive-forms-as-drafts}

Vous pouvez enregistrer les formulaires en tant que brouillons en vue de les remplir ultérieurement. Un formulaire est enregistré en tant que brouillon de deux manières différentes :
* Créez une règle « Enregistrer le formulaire » sur un composant de formulaire, par exemple un bouton. Lorsque vous cliquez sur le bouton, la règle se déclenche et le formulaire est enregistré en tant que brouillon.
* Activez la fonctionnalité d’enregistrement automatique, qui enregistre le formulaire selon l’événement spécifié ou après un intervalle de temps configuré.

### Création de règles pour enregistrer un formulaire adaptatif en tant que brouillon {#rule-to-save-adaptive-form-as-draft}

Pour créer une règle « Enregistrer le formulaire » sur un composant de formulaire, par exemple un bouton, procédez comme suit :

1. Dans l’instance de création, ouvrez un formulaire adaptatif en mode d’édition.
1. Dans le volet de gauche, appuyez sur ![Icône Composants](assets/components_icon.png) et faites glisser le composant [!UICONTROL Bouton] vers le formulaire.
1. Appuyez sur le composant [!UICONTROL Bouton], puis appuyez sur le bouton ![Icône Configurer](assets/configure_icon.png).
1. Appuyez sur l’icône [!UICONTROL Modifier des règles] pour ouvrir l’éditeur de règles.
1. Appuyer sur **[!UICONTROL Créer]** pour configurer et créer la règle.
1. Dans la section [!UICONTROL Quand], sélectionnez « est cliqué » et dans la section [!UICONTROL Après], sélectionnez les options « Enregistrer le formulaire ».
1. Appuyez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

### Activation de l’enregistrement automatique {#enable-auto-save}

Vous pouvez configurer la fonction d’enregistrement automatique d’un formulaire adaptatif comme suit :

1. Dans l’instance de création, ouvrez un formulaire adaptatif en mode d’édition.
1. Dans le volet de gauche, appuyez sur ![Icône Propriétés](assets/configure_icon.png) et développez l’option [!UICONTROL ENREGISTREMENT AUTOMATIQUE].
1. Sélectionnez la case à cocher **[!UICONTROL Activer]** pour activer l’enregistrement automatique du formulaire. Vous pouvez configurer les éléments suivants :
* Par défaut, l’[!UICONTROL Événement de formulaire adaptatift] est défini sur « true », ce qui implique que le formulaire est enregistré automatiquement après chaque événement.
* Dans [!UICONTROL Déclencheur], configurez l’option pour déclencher l’enregistrement automatique en fonction de l’occurrence d’un événement ou d’un intervalle de temps spécifique.
