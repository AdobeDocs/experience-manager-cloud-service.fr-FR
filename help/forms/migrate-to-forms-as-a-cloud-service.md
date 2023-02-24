---
title: Comment migrer d’un environnement AEM 6.5 Forms et AEM 6.4 Forms vers un environnement [!DNL AEM Forms] as a Cloud Service ?
description: Migration d’un environnement [!DNL AEM Forms] On-Premise vers un environnement [!DNL AEM Forms] as a Cloud Service
contentOwner: khsingh
feature: Adaptive Forms
role: User, Developer
level: Intermediate
topic: Migration
exl-id: 090e77ff-62ec-40cb-8263-58720f3b7558
source-git-commit: b11979acc23efe5f1af690443180a6b456d589ed
workflow-type: tm+mt
source-wordcount: '1816'
ht-degree: 74%

---

# Migration vers [!DNL AEM Forms] as a Cloud Service  {#Harden-your-AEM-Forms-as-a-Cloud-Service-environment}

Vous pouvez migrer vos formulaires adaptatifs, thèmes, modèles et configurations de cloud d’<!-- AEM 6.3 Forms--> AEM 6.4 Forms on OSGi et AEM 6.5 Forms on OSGi vers [!DNL AEM] as a Cloud Service. Avant de migrer ces ressources, utilisez l’utilitaire de migration pour convertir le format utilisé dans les versions antérieures au format utilisé dans [!DNL AEM] as a Cloud Service. Lorsque vous exécutez l’utilitaire de migration, les ressources ci-dessous sont mises à jour :

* Composants personnalisés pour les formulaires adaptatifs
* Modèles et thèmes de formulaires adaptatifs
* Configurations cloud
* Les scripts de l’éditeur de code sont convertis en fonctions réutilisables et appliqués aux règles visuelles.

## Considérations {#consideration}

* Ce service ne permet de migrer du contenu d’[!DNL AEM Forms] que dans les environnements OSGi. La migration de contenu d’[!DNL AEM Forms] on JEE vers un environnement Cloud Service n’est pas prise en charge.

* (Uniquement pour un environnement AEM 6.3 Forms ou d’une version antérieure mise à niveau vers AEM 6.4 Forms ou AEM 6.5 Forms) Les formulaires adaptatifs reposant sur des modèles et des thèmes prêts à l’emploi disponibles dans AEM 6.3 Forms ou une version antérieure ne sont pas pris en charge dans [!DNL AEM Forms] as a Cloud Service.

* L’étape de vérification n’est pas disponible. Supprimez l’étape de vérification de vos formulaires adaptatifs existants avant de déplacer ces formulaires vers un environnement Cloud Service.

* L’étape de signature d’Adaptive Forms n’est pas disponible. Supprimez l’étape Signature d’un formulaire adaptatif existant. Configurez votre formulaire adaptatif pour utiliser l’expérience de signature dans le navigateur. Il affichera ainsi l’accord Adobe Sign permettant de signer l’accord dans le navigateur lors de l’envoi d’un formulaire adaptatif. L’expérience de signature dans le navigateur permet d’accélérer le processus et de faire gagner du temps au signataire.

## Différence avec AEM 6.5 Forms

| Fonctionnalité | Différence avec AEM 6.5 Forms |
|--------------|-----------|
| HTML5 Forms (Forms mobile) | Le service ne prend pas en charge HTML5 Forms (Mobile Forms). Si vous effectuez le rendu de vos formulaires basés sur XDP sous HTML5 Forms, vous pouvez continuer à utiliser la fonctionnalité sur AEM 6.5 Forms. |
| Formulaires adaptatifs | <li><b>Forms adaptatif basé sur XSD :</b> Le service ne prend pas en charge HTML5 Forms (Mobile Forms). Si vous effectuez le rendu de vos formulaires basés sur XDP sous HTML5 Forms, vous pouvez continuer à utiliser la fonctionnalité sur AEM 6.5 Forms. </li> <li><b> Modèles de formulaire adaptatif :</b> Utilisez le pipeline de génération et le référentiel Git correspondant de votre programme pour importer les modèles de formulaire adaptatif existants. </li><li><b>Éditeur de règles :</b> AEM Forms as a Cloud Service offre une fonction renforcée [Éditeur de règles](rule-editor.md#visual-rule-editor). L’éditeur de code n’est pas disponible sur Forms as a Cloud Service. L’utilitaire de migration vous permet de migrer les formulaires dotés de règles personnalisées (créées dans l’éditeur de code). L’utilitaire convertit ces règles en fonctions personnalisées prises en charge sur Forms as a Cloud Service. Vous pouvez utiliser les fonctions réutilisables avec l’éditeur de règles pour continuer à obtenir les résultats obtenus avec les scripts de règle. `onSubmitError` ou `onSubmitSuccess` Les fonctions sont désormais disponibles en tant qu’actions dans l’éditeur de règles. </li> <li><b>Brouillons et envois :</b> Le service ne conserve pas les métadonnées des brouillons et des Forms adaptatives envoyées. </li> <li><b> Service de préremplissage :</b> Par défaut, le service de préremplissage fusionne les données avec un formulaire adaptatif au niveau du client plutôt que de fusionner les données sur le serveur dans AEM Forms 6.5. Cette fonctionnalité permet d’améliorer le temps nécessaire au préremplissage d’un formulaire adaptatif. Vous pouvez toujours configurer pour exécuter l’action de fusion sur le serveur Adobe Experience Manager Forms. </li><li><b>Actions Envoyer :</b> Le **Email en tant que PDF** n’est pas disponible. L’action d’envoi **Email** fournit des options pour envoyer des pièces jointes et joindre un document d’enregistrement (DE) par email. </li> |
| Modèle de données de formulaire | <li>Le modèle de données Forms ne prend en charge que les points de terminaison HTTP et HTTP pour envoyer des données. </li><li>Forms as a Cloud Service permet d’utiliser Microsoft Azure Blob, Microsoft SharePoint, Microsoft OneDrive et les services prenant en charge les opérations CRUD (Créer, lire, mettre à jour et supprimer) générales en tant que entrepôts de données. Le service ne prend pas en charge le connecteur JDBC, le protocole SSL mutuel pour le connecteur REST et l’authentification par certificat x509 pour les sources de données SOAP. </li> |
| Service de conversion automatisée de formulaires | Le service ne fournit pas de métamodèle pour Automated forms conversion Service. Vous pouvez [téléchargez-le à partir de la documentation d’Automated forms conversion Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=en#default-meta-model). |
| Configurations | <li>Par défaut, seuls les protocoles HTTP et HTTPs sont pris en charge. [Contactez l’équipe d’assistance](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=fr#sending-email) pour activer les ports pour l’envoi d’e-mails et pour activer le protocole SMTP pour votre environnement. </li> <li>Si vous utilisez des lots personnalisés, recompilez votre code avec la dernière version d’adobe-aemfd-docmanager avant d’utiliser ces lots avec Forms as a Cloud Service.</li> |
| API de manipulation de documents (service Assembler) | Le service ne prend pas en charge les opérations qui dépendent d’autres services ou applications : <li>La conversion de documents dans un format autre qu’un PDF au format PDF n’est pas prise en charge. Par exemple, Microsoft Word vers PDF, Microsoft Excel vers PDF et HTML vers PDF ne sont pas pris en charge.</li><li>Les conversions basées sur Distiller Adobe ne sont pas prises en charge. Par exemple, PostScript(PS) vers PDF</li><li>Les conversions basées sur le service Forms ne sont pas prises en charge. Par exemple, XDP aux PDF forms.</li><li>Le service ne prend pas en charge la conversion d’un PDF signé ou d’un PDF transparent dans un autre format de PDF.</li> |

## Prérequis {#prerequisites}

* [Activer Forms - Inscription numérique](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/setting-up-program.html?lang=fr#editing-program) activée pour votre programme Forms de Cloud Service et [exécution du pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=fr).

   ![Résultat de l’exécution d’essai](assets/enable-add-on.png)

* Dans un environnement Cloud Service, l’utilitaire de migration fonctionne conjointement avec l’outil de mappage utilisateur et l’outil de transfert de contenu. L’utilitaire de migration rend les ressources [!DNL AEM Forms] compatibles avec Cloud Service et l’outil de transfert de contenu migre le contenu de votre environnement [!DNL AEM Forms] vers un environnement [!DNL AEM] as a Cloud Service. Avant d’utiliser l’utilitaire de migration, découvrez comment [passer à AEM en tant que Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/home.html?lang=fr). La procédure comporte deux phases :
   * [Outil de mappage d’utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr#cloud-migration) : l’outil de mappage d’utilisateurs permet de mapper vos utilisateurs aux comptes utilisateur Adobe IMS correspondants.
   * [Outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr#cloud-migration) : l’outil de transfert de contenu permet de préparer et de transférer du contenu d’un environnement existant vers un environnement Cloud Service.
* Comptes disposant de droits d’administrateur sur [!DNL AEM Forms] as a Cloud Service et votre environnement local [!DNL AEM Forms].
* Téléchargez et installez Best Practice Analyzer, l’outil de transfert de contenu et l’utilitaire de migration d’[!DNL AEM Forms] à partir du [portail de distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

* Exécutez l’outil [Best Practices Analyzer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=fr#cloud-migration) et corrigez le problème signalé.

<!-- * Download the latest [compatibility package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#aem-65-forms-releases) for your [!DNL AEM Forms] version. -->

## Migration des ressources [!DNL AEM Forms]  {#use-the-migration-utility}

Pour rendre vos ressources [!DNL AEM Forms] compatibles avec Cloud Service et les transférer vers un environnement [!DNL AEM] as a Cloud Service, procédez comme suit.

1. Créez un [clone](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/correct-method-to-clone-the-aem-environment/td-p/363487?profile.language=fr) de votre environnement [!DNL AEM Forms] existant.

   Utilisez toujours l’environnement cloné pour exécuter l’outil de transfert de contenu et l’utilitaire de migration. L’outil de transfert de contenu et l’utilitaire de migration apportent des modifications au contenu et aux ressources. Par conséquent, n’exécutez pas l’outil de transfert de contenu et l’utilitaire de migration dans un environnement de production.

1. Connectez-vous à votre environnement cloné avec des droits d’administrateur.

1. Exécutez l’[outil de mappage d’utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr#cloud-migration) pour mapper vos utilisateurs aux comptes utilisateur Adobe IMS correspondants. Vous avez besoin de comptes utilisateur Adobe IMS pour vous connecter à une instance [!DNL AEM Forms] as a Cloud Service.

1. Téléchargez et installez l’outil [Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr#cloud-migration) et l’utilitaire de migration [!DNL AEM Forms] as a Cloud Service à partir du [portail de distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) dans l’environnement cloné. Vous pouvez utiliser AEM Package Manager pour installer l’outil et l’utilitaire.

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Opérations]** > **[!UICONTROL Migration du contenu]**.

1. Ouvrez la carte **[!UICONTROL Préparer Forms pour la migration]**. Le navigateur affiche cinq options :
   * **[!UICONTROL Migration des ressources d’AEM Forms]**
   * **[!UICONTROL Migration de composants personnalisés de formulaires adaptatifs]**
   * **[!UICONTROL Migration de modèles de formulaire adaptatif]**
   * **[!UICONTROL Migration des configurations cloud AEM Forms]**
   * **[!UICONTROL Migration du script de l’éditeur de code]**

1. Utilisez l’option une après l’autre pour rendre vos ressources [!DNL AEM Forms] compatibles avec [!DNL AEM] as a Cloud Service :

   1. Appuyez sur **[!UICONTROL Migration de ressources AEM Forms]** et, dans l’écran suivant, appuyez sur **[!UICONTROL Commencer la migration]**. Cela rend les formulaires adaptatifs et les thèmes dans votre environnement [!DNL AEM Forms] compatible avec [!DNL AEM] as a Cloud Service.

   1. Appuyez sur **[!UICONTROL Migration des composants de formulaire adaptatif personnalisés]** et, dans la page Migration des composants personnalisés, appuyez sur **[!UICONTROL Lancer la migration]**. Cela rend les composants personnalisés développés pour des formulaires adaptatifs et les superpositions de composants dans votre environnement [!DNL AEM Forms] compatibles avec [!DNL AEM] as a Cloud Service.

   1. Appuyez sur **[!UICONTROL Migration de modèles de formulaire adaptatif]** et dans la page Migration des composants personnalisés, appuyez sur **[!UICONTROL Lancer la migration]**. Cela rend les modèles de formulaire adaptatif dans /apps ou /conf et créés à l’aide de l’éditeur de modèles AEM compatibles avec [!DNL AEM] as a Cloud Service.

   1. Appuyez sur **[!UICONTROL Migration des configurations cloud AEM Forms]**, puis dans la page Migration de la configuration, appuyez sur **[!UICONTROL Commencer la migration]**. Il met à jour et déplace les Cloud Services suivants vers un nouvel emplacement :

      * Cloud Service de modèle de données de formulaire
      * Google reCAPTCHA Cloud Service
      * [!DNL Adobe Sign] Cloud Service
      * Adobe Fonts Cloud Service
   1. Appuyez sur **[!UICONTROL Migration des scripts de l’éditeur de code]**, spécifiez un emplacement pour enregistrer les fonctions réutilisables, puis appuyez sur **[!UICONTROL Commencer la migration].

   Cloud Service ne prend pas en charge les scripts de l’éditeur de règles. L’outil **[!UICONTROL Migration des scripts de l’éditeur de code]** convertit tous les scripts de règle de votre environnement en fonctions réutilisables et applique les fonctions réutilisables à l’éditeur visuel à l’emplacement approprié. Ces fonctions réutilisables sont enregistrées sous forme de bibliothèques clientes et vous aident à conserver les fonctionnalités existantes intactes. L’outil applique automatiquement les fonctions réutilisables générées aux formulaires adaptatifs correspondants.

   Utilisez le [gestionnaire de packages](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=fr#contentmanagement) pour exporter les fonctions réutilisables (bibliothèques clientes) vers un package.

1. [Déployez](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=fr#deploying-content-packages-via-cloud-manager-and-package-manager) le package de fonctions réutilisables (bibliothèques clientes), le [code personnalisé, les composants, les configurations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html?lang=fr#cloud-manager), les bibliothèques personnalisées spécifiques aux paramètres régionaux dans votre environnement [!DNL AEM] as a Cloud Service.

   <!-- 1. Install the latest [Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?#cloud-migration) to your cloned [!DNL AEM Forms] environment. -->

1. Exécutez l’[outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr#cloud-migration). Lors de la spécification des paramètres dans l’écran **[!UICONTROL Créer un jeu de migration]**, spécifiez le chemin d’accès aux formulaires adaptatif, thèmes, modèles, modèles de données de formulaire, Cloud Services, composants personnalisés et autres ressources spécifiques à AEM Forms sur l’option **[!UICONTROL Chemins à inclure]**. Cela ajoute les ressources [!DNL AEM Forms] spécifiées au jeu de migration.

## Chemins d’accès à différentes ressources spécifiques à AEM Forms

* **Formulaires adaptatifs** : vous trouverez les formulaires adaptatifs sous `/content/dam/formsanddocuments/`et /content/forms/af. Par exemple, pour un formulaire adaptatif appelé « Enregistrement WKND », ajoutez des chemins `/content/dam/formsanddocuments/wknd-registration` et `/content/forms/af/wknd-registration`.
* **Mode des données de formulaire** : vous trouverez tous les modèles de données de formulaire sous `/content/dam/formsanddocuments-fdm`. Par exemple, `/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`.

* **Bibliothèques clientes** : le chemin d’accès par défaut aux bibliothèques clientes est `/etc/clientlibs/fd/theme`.

* **Modèles de formulaire adaptatif** : le chemin d’accès par défaut aux modèles est `/conf/<template folder>`. Par exemple, pour un modèle appelé « chemin d’ajout de base » `/conf/ReferenceEditableTemplates/settings/wcm/templates/basic`.

* **Thèmes de formulaires adaptatifs et bibliothèques clientes** : le chemin d’accès par défaut aux thèmes est ` /content/dam/formsanddocuments-themes/` et chemin d’accès par défaut aux bibliothèques clientes est `/etc/clientlibs/fd/theme`. Par exemple, pour un modèle appelé « Thème WKND », ajoutez le chemin d’accès ` /content/dam/formsanddocuments-themes/wkndtheme` et les bibliothèques clientes pour le thème sous `/etc/clientlibs/reference-themes/wkndtheme-3-0`. Vous pouvez également utiliser des thèmes et des bibliothèques clientes sur d’autres chemins d’accès personnalisés.

* **Configurations du cloud** : vous trouverez les configurations de cloud sous `/conf/`. Par exemple, la configuration du cloud de modèles de données de formulaire se trouve sous `/conf/global/settings/cloudconfigs/fdm`.

* **Modèle de processus** : vous trouverez des modèles de processus AEM sous `/conf/global/settings/workflow/models/`. Par exemple, pour un modèle de processus appelé « Enregistrement WKND », ajoutez le chemin d’accès `/conf/global/settings/workflow/models/wknd-registration`.

Vous pouvez ajouter des chemins d’accès aux dossiers de niveau supérieur répertoriés ci-dessous ou des chemins d’accès aux dossiers spécifiques, comme indiqué ci-dessous. Cela permet de migrer simultanément certaines ressources et l’ensemble des ressources et des formulaires.

* /content/dam/formsanddocuments-fdm
* /content/dam/formsanddocuments/themes
* /content/forms/af
* /etc/clientlibs/fd/theme

Pour migrer des modèles de processus AEM, spécifiez les chemins d’accès suivants :

* /conf/global/settings/workflow/models/
* /conf/global/settings/workflow/launcher
* /var/workflow/models
