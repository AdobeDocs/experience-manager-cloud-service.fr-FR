---
title: Comment créer un portail Forms sur une page Experience Manager Sites ?
description: Découvrez comment créer un portail Forms et utiliser les composants principaux d’usine sur une page AEM Sites.
source-git-commit: 4c42abfe2cc1b11aefb2b298e883406ca5c17fd2
workflow-type: tm+mt
source-wordcount: '1753'
ht-degree: 26%

---


# Liste des Forms adaptatives sur un portail {#publish-forms-on-portal}

Dans les scénarios typiques de déploiement de portail basés sur l’utilisation de formulaires, le développement des formulaires et le développement du portail sont deux activités bien distinctes. Tandis que les créateurs de formulaires créent des formulaires et les stockent dans un référentiel, les développeurs Web créent une application Web permettant de répertorier les formulaires et de gérer leurs envois. Les formulaires sont copiés sur la plateforme Web car il n’existe aucune communication entre le référentiel des formulaires et l’application Web.

Ces scénarios entraînent généralement des problèmes de gestion et des retards de production. Par exemple, lorsqu’une nouvelle version d’un formulaire est disponible dans le référentiel, vous devez remplacer le formulaire sur la plateforme Web, modifier l’application Web, puis déployer à nouveau le formulaire sur le site public. Le redéploiement de l’application Web risque d’entraîner un temps d’arrêt au niveau du serveur. En règle générale, les temps d’arrêt de serveur sont dus à une activité planifiée et, par conséquent, les modifications ne peuvent pas être transférées au site public instantanément.

AEM Forms fournit des composants de portail qui réduisent les surcharges de gestion et les délais de production. Les composants permettent aux développeurs web de créer et de personnaliser un portail Forms sur les sites web créés à l’aide d’Adobe Experience Manager (AEM).

Les composants du portail de formulaires vous permettent d’ajouter les fonctionnalités suivantes :

* Création d’une liste de formulaires dans des mises en page personnalisées Les mises en page en mode Liste et Carte sont prêtes à l’emploi. Vous pouvez créer vos propres mises en page personnalisées.
* Permet d’afficher des métadonnées et des actions personnalisées lors de leur mise en liste.
* Création d’une liste des formulaires publiés par l’interface utilisateur d’AEM Forms sur l’instance de publication où sont utilisés les composants de portail de formulaires.
* Permet aux utilisateurs finaux d’effectuer le rendu des formulaires au format HTML et PDF.
* Permet de rechercher des formulaires en fonction du titre et de la description.
* Utilisation de feuilles CSS pour la personnalisation de l’apparence du portail.
* Création de liens vers des formulaires.
* Répertorie les brouillons et les envois liés à la Forms adaptative créée par l’utilisateur final.

## Composants d’une page Forms Portal {#forms-portal-components}

AEM Forms fournit les composants de portail suivants prêts à l’emploi :

* Search &amp; Lister : Ce composant vous permet de répertorier les formulaires du référentiel de formulaires sur votre page de portail et fournit des options de configuration pour répertorier les formulaires selon des critères spécifiés.

* Brouillons et envois : Tandis que le composant Search &amp; Lister affiche les formulaires rendus publics par l’auteur Forms, le composant Drafts &amp; Submissions (Brouillons et envois) affiche les formulaires enregistrés en tant que brouillons en vue de les compléter ultérieurement et les formulaires envoyés. Ce composant offre un environnement personnalisé à tout utilisateur connecté.

* Link: Ce composant permet de créer un lien vers un formulaire n’importe où sur la page.

Vous pouvez [importer les composants Forms Portal prêts à l’emploi ;](#import-forms-portal-components-aem-archetype) à partir de l’archétype de projet AEM. Après l’importation, effectuez les configurations suivantes :
* [Configuration d’un stockage externe](#configure-azure-storage-adaptive-forms)
* [Activation des composants du portail Forms](#enable-forms-portal-components)
* [Configuration des composants du portail Forms](#configure-forms-portal-components)

## Importation des composants du portail Forms {#import-forms-portal-components-aem-archetype}

Pour importer des composants Forms Portal prêts à l’emploi sur AEM Forms as a Cloud Service, procédez comme suit :

1. **Clonez le référentiel Git Cloud Manager sur votre instance de développement locale** : votre référentiel Git Cloud Manager contient un projet AEM par défaut. Il est basé sur l’[archétype AEM](https://github.com/adobe/aem-project-archetype/). Clonez votre référentiel Git Cloud Manager à l’aide de la gestion de compte Git en libre-service depuis l’interface utilisateur de Cloud Manager pour intégrer le projet à votre environnement de développement local. Pour plus d’informations sur l’accès au référentiel, voir [Accès aux référentiels](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html?lang=fr).

1. **Créer [!DNL Experience Manager Forms] as a [Cloud Service] project :** Créer [!DNL Experience Manager Forms] as a [Cloud Service] projet basé sur [AEM Archetype 27](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-27) ou plus tard. L’archétype permet aux développeurs de commencer facilement le développement pour [!DNL AEM Forms] as a Cloud Service. Il comprend également des exemples de thème et de modèle pour vous permettre de commencer rapidement votre projet.

   Pour créer [!DNL Experience Manager Forms] as a Cloud Service projet, ouvrez l’invite de commande et exécutez la commande ci-dessous. Pour inclure des configurations, des thèmes et des modèles spécifiques à [!DNL Forms], définissez `includeForms=y`.

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=30 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   Modifiez également `appTitle`, `appId` et `groupId` dans la commande ci-dessus pour refléter votre environnement.

1. **Déployez le projet dans votre environnement de développement local :** Vous pouvez utiliser la commande suivante pour effectuer un déploiement dans votre environnement de développement local.

   `mvn -PautoInstallPackage clean install`

   Pour obtenir la liste complète des commandes, voir [Création et installation](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=fr#building-and-installing).

1. [Inclure les artefacts de composant principal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html#embeddeds) et la dépendance comme suit :

   ```shell
   <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>{TBD}</artifactId>
               <type>content-package</type>
               <version>{TBD}</version>
   </dependency>
   ```

1. [Déployez le code dans votre environnement [!DNL AEM Forms] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html#embeddeds).


## Configuration du stockage Azure pour le Forms adaptatif {#configure-azure-storage-adaptive-forms}

[[!DNL Experience Manager Forms] Intégration de données](data-integration.md) fournit [!DNL Azure] configuration de stockage pour intégrer des formulaires à [!DNL Azure] services de stockage. Le modèle de données de formulaire peut être utilisé pour créer des formulaires adaptatifs qui interagissent avec un serveur [!DNL Azure] pour activer des processus métier.

### Créer une configuration de stockage Azure {#create-azure-storage-configuration}

Avant d’exécuter ces étapes, assurez-vous de disposer d’un [!DNL Azure] compte de stockage et clé d’accès pour autoriser l’accès à [!DNL Azure] compte de stockage.

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Stockage Azure]**.
1. Sélectionnez un dossier pour créer la configuration et appuyez sur **[!UICONTROL Créer]**.
1. Indiquez un titre pour la configuration dans le champ **[!UICONTROL Titre]**.
1. Indiquez le nom du compte de stockage [!DNL Azure] dans le champ **[!UICONTROL Compte de stockage Azure]**.

### Configuration du connecteur de stockage unifié pour Forms Portal {#configure-usc-forms-portal}

Suivez les étapes suivantes pour configurer le connecteur de stockage unifié pour les workflows AEM :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Connecteur de stockage unifié]**.
1. Dans le **[!UICONTROL Portail Forms]** , sélectionnez **[!UICONTROL Azure]** de la **[!UICONTROL Stockage]** liste déroulante.
1. Spécifiez le [chemin de configuration pour la configuration de stockage Azure](#create-azure-storage-configuration) dans le champ **[!UICONTROL Chemin de configuration de stockage]**.
1. Appuyez sur **[!UICONTROL Publier]**, puis sur **[!UICONTROL Enregistrer]** pour enregistrer la configuration.

## Activation des composants du portail Forms {#enable-forms-portal-components}

Pour utiliser n’importe quel composant principal (y compris les composants de portail prêts à l’emploi) dans un site Adobe Experience Manager (AEM), vous devez créer un composant proxy et l’activer pour votre site. Pour créer un composant proxy et activer les composants de portail, voir [Utilisation des composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html?lang=en#create-proxy-components).

Une fois qu’un composant de portail est activé, vous pouvez l’utiliser dans l’instance de création de votre page de sites.

## Ajout et configuration de composants Forms Portal {#configure-forms-portal-components}

Vous pouvez créer et personnaliser Forms Portal sur les sites web créés à l’aide d’AEM en ajoutant et en configurant les composants du portail. Assurez-vous que la variable [les composants sont activés.](#enable-forms-portal-components) avant de les utiliser dans Forms Portal.

Pour ajouter un composant, faites-le glisser du panneau Composants vers le conteneur de mises en page sur la page ou appuyez sur l’icône Ajouter du conteneur de mises en page et ajoutez-le depuis l’ [!UICONTROL Insérer un nouveau composant] boîte de dialogue.

### Configuration du composant Drafts &amp; Submissions {#configure-drafts-submissions-component}

Le composant Drafts &amp; Submissions (Drafts &amp; Submissions) affiche les formulaires enregistrés en tant que brouillons en vue de leur remplissage ultérieur et les formulaires envoyés. Pour configurer, appuyez sur le composant, puis appuyez sur le bouton ![Icône Configurer](assets/configure_icon.png). Dans le [!UICONTROL Brouillons et envois] spécifiez le titre pour indiquer la liste des formulaires sous forme de brouillons ou de formulaires envoyés. Indiquez également si le composant doit répertorier les brouillons de formulaires ou les formulaires envoyés au format carte ou liste.

![Icône Brouillons](assets/drafts-component.png)

![Icône Envois](assets/submission-listing.png)

### Configuration du composant Search &amp; Lister {#configure-search-lister-component}

Le composant Search &amp; Lister est utilisé pour répertorier les formulaires adaptatifs sur une page et pour implémenter la recherche sur les formulaires répertoriés.

![Icône Search &amp; Lister](assets/search-and-lister-component.png)

Pour configurer, appuyez sur le composant, puis appuyez sur le bouton ![Icône Configurer](assets/configure_icon.png). Le [!UICONTROL Search and Lister] s’ouvre.

1. Dans le [!UICONTROL Affichage] , configurez les éléments suivants :
   * Dans **[!UICONTROL Titre]**, spécifiez le titre du composant Search &amp; Lister. Un titre indicatif permet aux utilisateurs d’effectuer une recherche rapide dans la liste des formulaires.
   * Dans la **[!UICONTROL Disposition]** sélectionnez la mise en page représentant les formulaires au format carte ou liste.
   * Sélectionner **[!UICONTROL Masquer la recherche]** et **[!UICONTROL Masquer le tri]** pour masquer la recherche et trier par fonctions.
   * Dans **[!UICONTROL Info-bulle]**, fournissez l’info-bulle qui s’affiche lorsque vous placez le pointeur de la souris sur le composant.
1. Dans le [!UICONTROL Dossier de ressources] , indiquez l’emplacement d’extraction et de liste des formulaires sur la page. Vous pouvez configurer plusieurs emplacements de dossiers.
1. Dans le [!UICONTROL Résultats] , configurez le nombre maximal de formulaires à afficher par page. La valeur par défaut est de huit formulaires par page.

### Configuration du composant Link {#configure-link-component}

Le composant Link vous permet de fournir des liens vers un formulaire adaptatif sur la page. Pour configurer, appuyez sur le composant, puis appuyez sur le bouton ![Icône Configurer](assets/configure_icon.png). Le [!UICONTROL Modifier le composant Lien] s’ouvre.

1. Dans le [!UICONTROL Affichage] , fournissez la légende du lien et l’info-bulle pour faciliter l’identification des formulaires représentés par le lien.
1. Dans le [!UICONTROL Informations sur les ressources] , spécifiez le chemin du référentiel où la ressource est stockée.
1. Dans le [!UICONTROL Paramètres de requête] , spécifiez les paramètres supplémentaires au format de paire clé-valeur. Lorsque le lien est activé, ces paramètres supplémentaires sont transmis avec le formulaire.

## Configuration de l’envoi de formulaire asynchrone à l’aide d’Adobe Sign {#configure-asynchronous-form-submission-using-adobe-sign}

Vous pouvez configurer pour envoyer un formulaire adaptatif uniquement lorsque tous les destinataires ont terminé la cérémonie de signature. Suivez les étapes ci-dessous pour configurer le paramètre à l’aide d’Adobe Sign.

1. Dans l’instance d’auteur, ouvrez un formulaire adaptatif en mode d’édition.
1. Dans le volet de gauche, appuyez sur l’icône Propriétés et développez la **[!UICONTROL SIGNTAGE ÉLECTRONIQUE]** .
1. Sélectionner **[!UICONTROL Activer Adobe Sign]**. Différentes options de configuration s’affichent.
1. Dans le [!UICONTROL Envoyer le formulaire] , sélectionnez **[!UICONTROL une fois que chaque destinataire a terminé la cérémonie de signature]** pour configurer l’action Envoyer le formulaire, où le formulaire est d’abord envoyé à tous les destinataires pour signature. Une fois que tous les destinataires ont signé le formulaire, le formulaire est envoyé.

## Enregistrement d’un Forms adaptatif en tant que brouillons {#save-adaptive-forms-as-drafts}

Vous pouvez enregistrer les formulaires en tant que brouillons pour les compléter ultérieurement. Un formulaire est enregistré en tant que brouillon de deux manières différentes :
* Créez une règle &quot;Enregistrer le formulaire&quot; sur un composant de formulaire, par exemple un bouton. Lorsque vous cliquez sur le bouton, la règle se déclenche et le formulaire est enregistré dans un brouillon.
* Activez la fonction d’enregistrement automatique, qui enregistre le formulaire selon l’événement spécifié ou après un intervalle de temps configuré.

### Création de règles pour enregistrer un formulaire adaptatif en tant que brouillon {#rule-to-save-adaptive-form-as-draft}

Pour créer une règle &quot;Enregistrer le formulaire&quot; sur un composant de formulaire, par exemple un bouton, procédez comme suit :

1. Dans l’instance d’auteur, ouvrez un formulaire adaptatif en mode d’édition.
1. Dans le volet de gauche, appuyez sur ![Icône Composants](assets/components_icon.png) et faites glisser le [!UICONTROL Bouton] du formulaire.
1. Appuyez sur le bouton [!UICONTROL Bouton] , puis appuyez sur ![Icône Configurer](assets/configure_icon.png).
1. Appuyez sur le bouton [!UICONTROL Modifier des règles] pour ouvrir l’éditeur de règles.
1. Appuyer **[!UICONTROL Créer]** pour configurer et créer la règle.
1. Dans le [!UICONTROL When] , sélectionnez &quot;est cliqué&quot; et dans la variable [!UICONTROL Alors] , sélectionnez les options &quot;Enregistrer le formulaire&quot;.
1. Appuyez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

### Activation de l’enregistrement automatique {#enable-auto-save}

Vous pouvez configurer la fonction d’enregistrement automatique d’un formulaire adaptatif comme suit :

1. Dans l’instance d’auteur, ouvrez un formulaire adaptatif en mode d’édition.
1. Dans le volet de gauche, appuyez sur ![Icône Propriétés](assets/configure_icon.png) et développez la variable [!UICONTROL ENREGISTREMENT AUTOMATIQUE] .
1. Sélectionnez la **[!UICONTROL Activer]** pour activer l’enregistrement automatique du formulaire. Vous pouvez configurer les éléments suivants :
* Par défaut, la variable [!UICONTROL Événement de formulaire adaptatif] est définie sur &quot;true&quot;, ce qui implique que le formulaire est automatiquement enregistré après chaque événement.
* Dans [!UICONTROL Déclencheur], configurez pour déclencher l’enregistrement automatique en fonction de l’occurrence d’un événement ou d’un intervalle de temps spécifique.
