---
title: « Notes de mise à jour d’[!DNL AEM Forms] as a Cloud Service »
description: « Notes de mise à jour d’[!DNL AEM Forms] as a Cloud Service »
exl-id: 35950b81-6e45-4a75-bd27-8c28fd68e42e
source-git-commit: bc4da79735ffa99f8c66240bfbfd7fcd69d8bc13
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 99%

---


# Note mise à jour d’[!DNL Experience Manager Forms] as a Cloud Service {#overview}

Adobe Experience Manager [!DNL AEM Forms] as a Cloud Service fait l’objet régulièrement d’améliorations. Pour vous tenir au courant des dernières nouveautés, consultez régulièrement cette page. Cette page vous fournit les informations suivantes :

- Nouvelles fonctionnalités
- Améliorations
- Fonctionnalités de pré-version
- Fonctionnalités bêta
- Correctifs
- Fonctionnalités obsolètes
- Instructions spéciales
- Changements prévus

>[!NOTE]
>
>Pour les notes de mise à jour de tous les autres composants de mise à jour d’AEM as a Cloud Service, consultez [Notes de mise à jour actuelles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## 2021.10.0 {#sep-2021-10-0}

### Nouveautés de [!DNL Forms] {#what-is-new-forms-oct-2021}

- **Analytics pour formulaires adaptatifs** : vous pouvez désormais capturer et suivre le comportement des utilisateurs connectés et non connectés (anonymes) par le biais d’Adobe Analytics pour formulaires adaptatifs en vue de recueillir des informations relatives aux utilisateurs finaux. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms-oct-2021}

- **Externaliser les données des workflows AEM pour un traitement sécurisé** : vous pouvez stocker les données de workflows AEM (données de variables de workflows AEM) qui contiennent des éléments de données à caractère personnel dans un référentiel géré par le client pour un traitement sécurisé. Les éléments de données et les variables de workflows ne sont pas stockés dans le référentiel AEM et sont récupérés à la demande à partir d’un référentiel géré par le client lors du traitement du workflow.

### Fonctionnalités bêta de [!DNL Forms] {#sep-what-is-new-forms-oct-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API Communications](aem-forms-cloud-service-communications.md) vous permettent de combiner un modèle et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents dans les modes synchrone et par lots. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   - Générer des documents en renseignant les fichiers de modèle (PDF et XDP) avec des données XML
   - Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs

Vous pouvez écrire à [!DNL formscsbeta@adobe.com] pour vous inscrire au programme bêta.

## 2021.9.0 {#sep-2021-09-0}

### Nouveautés de [!DNL Forms] {#what-is-new-forms-sep-2021}

- **Utilisation des rôles Adobe Sign dans un formulaire adaptatif** : les niveaux de service professionnel et entreprise d’Adobe Sign offrent la possibilité d’étendre les rôles des destinataires du contrat au-delà du simple signataire, afin de mieux répondre aux exigences de leur workflow. Vous pouvez désormais [permettre à chaque destinataire de contrat de configurer son rôle dans un formulaire adaptatif](working-with-adobe-sign.md#addsignerstoanadaptiveform), avec le rôle Signer par défaut.

- **Analytics pour les formulaires adaptatifs** : vous pouvez désormais capturer et [suivre le comportement de l’utilisateur final via Adobe Analytics](integrate-aem-forms-with-adobe-analytics.md) pour les formulaires adaptatifs afin de rassembler les informations sur l’utilisateur final. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

- **Connectez facilement AEM Forms à Microsoft Dynamics et à Salesforce** : le service fournit des modèles de données et de configuration de source de données prêts à l’emploi pour Microsoft Dynamics et Salesforce, ce qui permet aux développeurs de configurer [plus rapidement et plus facilement Microsoft Dynamics et Salesforce en tant que sources de données pour un formulaire adaptatif](configure-msdynamics-salesforce.md).

- **Signature électronique d’un formulaire adaptatif à l’aide de DocuSign :** [vous pouvez utiliser DocuSign pour signer électroniquement un formulaire adaptatif](integrate-docusign-adaptive-forms.md). Le service fournit une action d’envoi personnalisée pour utiliser DocuSign avec un formulaire adaptatif.

### Fonctionnalités bêta de [!DNL Forms] {#sep-what-is-new-forms-prerelease}

- **Connecteur de stockage unifié :** utilisez le connecteur de stockage unifié pour externaliser les données en cours de traitement dans les référentiels gérés par le client. Par exemple, vous pouvez effectuer les actions suivantes :  Stocker les données de workflows AEM en cours (données des variables de workflows AEM) qui contiennent des données personnelles sensibles (SPD) dans un référentiel géré par le client.
   <!--* Enable Forms Portal’s save and resume functionality and store adaptive forms drafts in a customer-managed data repository.-->

- **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API de communication](aem-forms-cloud-service-communications.md) vous permettent de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :
   - Générer des documents en complétant des fichiers de modèle avec des données XML
   - Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs
   - Générer des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat

Vous pouvez écrire à [!DNL formscsbeta@adobe.com] pour vous inscrire au programme bêta.

### Limites {#limitations}

- Adobe Analytics peut uniquement effectuer le suivi des mesures de formulaire pour les utilisateurs authentifiés.

<!--

### New features available in [!DNL Forms] prerelease channel {#prerelease-features-forms-sep-2021}

* **Forms Portal:**  In a typical forms-centric portal deployment scenario, forms development and portal development are two disjoint activities. While Form Designers design and store forms in a repository, Web Developers create a web application to list forms and handle submission of forms. Forms are copied over to the web tier as there is no communication between the forms repository and the web application.

  Such scenarios often result in management issues and production delays. For example, if there is a newer version of a form available in the repository, you need to replace the form on the web tier, modify the web application, and redeploy the form on the public site. Redeploying the web application might cause some server downtime. Typically, the server downtime is a planned activity and therefore the changes cannot be pushed to the public site instantaneously.

  AEM Forms provides portal components that reduce management overheads and production delays. The components equip Web Developers to create and customize a forms portal on websites authored using Adobe Experience Manager (AEM). The form portal components allow you to add the following functionality:

  * List forms in customized layouts. Out of the box, List view and Card view are provided.

  * List published adaptive forms on an AEM Sites page.

  * Enable searching of forms based on a various criteria, such as form properties, metadata, and tags.

  * Lists drafts and submissions related to Adaptive Form created by end user.

  -->

## 2021.8.0 {#aug-2021-08-0}

### Nouveautés de [!DNL Forms] {#what-is-new-forms-aug-2021}

<!-- * Automated Forms Conversion service can [convert PDF Forms in Italian and Portuguese language](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) to Adaptive Forms. -->

- Le projet d’archétype AEM pour Forms as a Cloud Service comprend désormais [des modèles de données de formulaire pour Microsoft Dynamics et Salesforce](setup-local-development-environment.md).

- **Document d’enregistrement basé sur Acrobat** : AEM Forms as a Cloud Service prend en charge l’utilisation d’[Adobe Acrobat Form PDF (Acrobat PDF)](generate-document-of-record-for-non-xfa-based-adaptive-forms.md) comme modèle de document d’enregistrement en plus des modèles de formulaire basés sur XFA.

- **Connecteur de magasin de données Microsoft Azure** : vous pouvez désormais [connecter le modèle de données de formulaire au stockage Microsoft Azure](configure-azure-storage.md). Ceci vous permet de récupérer et de stocker des données de formulaire adaptatif dans le stockage Microsoft Azure en tant que BLOB.

### Fonction bêta de [!DNL Forms] {#aug-what-is-new-forms-prerelease}

- **Connecteur de stockage unifié :** utilisez le connecteur de stockage unifié pour externaliser les données en cours de traitement dans les référentiels gérés par le client. Par exemple, vous pouvez effectuer les actions suivantes :

   - Activer la fonctionnalité d’enregistrement et de reprise de Forms Portal et stocker les brouillons de formulaires adaptatifs dans un référentiel de données géré par le client.
   - Stocker les données de workflows AEM en cours (données des variables de workflows AEM) qui contiennent des données personnelles sensibles (SPD) dans un référentiel géré par le client.

- **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API de communication](aem-forms-cloud-service-communications.md) vous permettent de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :
   - Générer des documents en complétant des fichiers de modèle avec des données XML
   - Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs
   - Générer des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat

Vous pouvez écrire à [!DNL formscsbeta@adobe.com] pour vous inscrire au programme bêta.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms-aug-2021}

- **Utilisation des rôles Adobe Sign dans un formulaire adaptatif** : les niveaux de service professionnel et entreprise d’Adobe Sign offrent la possibilité d’étendre les rôles des destinataires du contrat au-delà du simple signataire, afin de mieux répondre aux exigences de leur workflow. Vous pouvez désormais [permettre à chaque destinataire de contrat de configurer son rôle dans un formulaire adaptatif](working-with-adobe-sign.md#addsignerstoanadaptiveform), avec le rôle Signer par défaut.

- **Analytics pour les formulaires adaptatifs** : vous pouvez désormais capturer et suivre le comportement de l’utilisateur final via Adobe Analytics pour les formulaires adaptatifs afin de rassembler les informations sur l’utilisateur final. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

- **Connectez facilement AEM Forms à Microsoft Dynamics et à Salesforce** : le service fournit des modèles de données et de configuration de source de données prêts à l’emploi pour Microsoft Dynamics et Salesforce, ce qui permet aux développeurs de configurer [plus rapidement et plus facilement Microsoft Dynamics et Salesforce en tant que sources de données pour un formulaire adaptatif](configure-msdynamics-salesforce.md).

## 2021.7.0 {#july-2021-07-0}

### Nouveautés de [!DNL Forms] {#july-what-is-new-forms}

- Vous pouvez désormais utiliser le service de conversion automatisée de formulaires pour [convertir les formulaires PDF en français, en allemand et en espagnol](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=fr#language-specific-meta-model) en formulaires adaptatifs.
- Ajout d’un panneau distinct à l’éditeur de modèles pour afficher les erreurs liées aux composants de formulaire adaptatif. Cela permet de consolider toutes les erreurs de formulaire adaptatif à un seul emplacement et de réduire le temps de résolution.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#july-prerelease-features-forms}

- **Document d’enregistrement basé sur Acrobat** : vous pouvez également [utiliser Adobe Acrobat Form PDF (Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=fr) comme modèle de document d’enregistrement en plus du modèle de formulaire basé sur XFA.

- **Connecteur de magasin de données Microsoft Azure** : vous pouvez désormais [connecter le modèle de données de formulaire au stockage Microsoft Azure](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html?lang=fr). Ceci vous permet de récupérer et de stocker des données de formulaire adaptatif dans le stockage Microsoft Azure en tant que BLOB.

- **Externalisateur de données variables** : vous pouvez enregistrer les données variables des workflows AEM sur un système de stockage externe géré par votre entreprise.

### Fonction bêta de [!DNL Forms] {#july-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API de communication](aem-forms-cloud-service-communications.md) vous permettent de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :
   - Générer des documents en complétant des fichiers de modèle avec des données XML
   - Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs
   - Générer des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat

## 2021.6.0 {#july-2021-06-0}

### Nouveautés de [!DNL Forms] {#june-what-is-new-forms}

- Possibilité de filtrer les colonnes personnalisées dans la boîte de réception AEM.
- Possibilité d’utiliser l’éditeur de thèmes et le calque de style de l’éditeur de formulaires adaptatifs pour appliquer un style au composant Captcha.
- Amélioration de la vitesse et de la précision de la détection automatique des sections logiques dans les formulaires PDF sources et de leur conversion en panneaux de formulaires adaptatifs correspondants.
- Ajout d’une action de déplacement pour déplacer un fichier PDF ou XDP d’un dossier à un autre.

### Fonction bêta de [!DNL Forms] {#june-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]** : les API de communication vous permettent de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   - Générer des documents de formulaire définitifs en complétant des fichiers de modèle avec des données XML.
   - Générez des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs.
   - Générer des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat (AcroForm).

- **Externalisateur de données variables** : vous pouvez enregistrer les données variables des workflows AEM sur un système de stockage externe géré par votre entreprise.

Vous pouvez écrire sur [!DNL formscsbeta@adobe.com] pour vous inscrire au programme bêta.

### Correctifs de [!DNL Forms] {#june-forms-bugs-fixed}

- Lorsqu’un champ est validé avant l’envoi des données au service principal via le modèle de données de formulaire (FDM), les validations réussissent, mais le service de modèle de données de formulaire ne parvient pas à appeler après validation.
- Lorsque vous envoyez un formulaire contenant un champ de chargement HTML standard d’un appareil iOS d’Apple, le contenu du fichier n’est parfois pas envoyé et un fichier de 0 octet est reçu à l’autre bout. Apple iOS 15.1 apporte un correctif pour le problème.

## 2021.5.0 {#may-2021-05-0}

## [!DNL Adobe Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#may-what-is-new-forms}

- **Aide contextuelle** : ajout d’une aide contextuelle pour l’éditeur de formulaires adaptatifs, l’éditeur de modèles et l’éditeur de thèmes afin d’aider les auteurs à mieux comprendre les différentes fonctionnalités des éditeurs.
- **Messages d’erreur dans le navigateur Propriétés** : ajout de messages d’erreur pour chaque propriété dans le navigateur Propriétés des formulaires adaptatifs. Ces messages aident à comprendre les valeurs autorisées pour un champ.

### Fonctionnalité bêta à venir de [!DNL Forms] {#may-what-is-new-forms-prerelease}

Output as a Cloud service : le service Output vous permet de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode batch synchrone et asynchrone. Le service Output vous permet de créer des applications qui vous permettent :

- Générer des documents de formulaire définitifs en complétant des fichiers de modèle avec des données XML.
- Générez des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs.
- Générer des fichiers PDF d’impression à partir de fichiers PDF de formulaire XFA.

Vous pouvez écrire à l’adresse formscsbeta@adobe.com pour vous inscrire au programme bêta.

### Correctifs de [!DNL Forms] {#may-forms-bugs-fixed}

- Dans une étape Affecter une tâche des workflows AEM Forms, lorsque vous remplacez l’icône par défaut des boutons d’action par une icône corail, le workflow cesse de fonctionner et consigne une exception. Le workflow fonctionne comme prévu lorsque des icônes par défaut sont utilisées.
- Dans le calque de mise en page, lorsque vous modifiez le nombre de colonnes, ouvrez le calque d’édition et faites glisser certains composants dans un panneau, les zones bleues carrées apparaissent dans la zone de contenu de l’éditeur de formulaires adaptatifs et l’éditeur ne répond plus.
- Le message d’erreur d’une option d’éditeur de règles liée à la fourniture de l’URL d’une ressource adaptative ou externe est trop long et n’est pas convivial.

## 2021.4.0 {#april-2021-04-0}

### Nouveautés de [!DNL Forms] {#april-what-is-new-forms}

- **Utilisation de la méthode d’authentification d’identité ID gouvernement dans les formulaires adaptatifs prenant en charge Adobe Sign**

   Optimisé par des algorithmes d’apprentissage automatique avancés, le processus d’ID gouvernement d’Adobe Sign permet aux entreprises du monde entier de sécuriser une authentification de grande qualité de l’identité de leur destinataire. Vous pouvez maintenant utiliser la méthode d’authentification d’identité ID gouvernement dans les formulaires adaptatifs prenant en charge Adobe Sign.

   ID gouvernement est une méthode d’authentification d’identité Premium qui demande au destinataire de [charger l’image d’un document d’identité émis par le gouvernement (permis de conduire, carte d’identité nationale, passeport)](https://helpx.adobe.com/fr/sign/using/adobesign-authentication-government-id.html), puis qui évalue ce document pour s’assurer qu’il est authentique.

- **Prise en charge de l’utilisation de l’expérience de signature dans les formulaires pour les envois asynchrones de formulaires adaptatifs**

   Vous pouvez maintenant utiliser l’expérience de signature dans les formulaires pour les envois asynchrones de formulaires adaptatifs. Vous avez également la possibilité d’incorporer un formulaire adaptatif dans une page [!DNL Experience Manager Sites] et d’utiliser l’expérience de signature dans les formulaires pour les envois de formulaires adaptatifs.

- **Prise en charge de l’utilisation d’une variable pour spécifier une pièce jointe lors du remplissage préalable d’un formulaire adaptatif pour une étape d’affectation d’une tâche**

   Lors du remplissage préalable d’un formulaire adaptatif pour une étape d’affectation d’une tâche, vous pouvez désormais utiliser une variable de type document pour sélectionner une pièce jointe d’entrée pour le formulaire adaptatif.

- **Prise en charge de l’utilisation de l’option littérale pour définir la valeur d’une variable de type JSON**

   Vous pouvez utiliser l’option littérale pour définir la valeur d’une variable de type JSON à l’étape de définition de la variable d’un processus AEM. L’option littérale vous permet de spécifier un fichier JSON sous la forme d’une chaîne.

- **Utilisation de l’environnement de développement local pour créer un document d’enregistrement**

   Vous pouvez utiliser un fichier XDP comme modèle de document d’enregistrement sur les instances de Cloud Service et dans le SDK AEM Forms as a Cloud Service (environnement de développement local). Auparavant, la prise en charge était limitée uniquement aux instances de Cloud Service.

### Bogues corrigés dans [!DNL Forms] {#april-bug-fixes-forms}

- Lorsqu’un formulaire adaptatif configuré pour ne pas générer de document d’enregistrement est envoyé à un workflow AEM configuré pour générer un document d’enregistrement, aucun message d’erreur ne s’affiche et la tâche ne parvient pas à effectuer l’envoi.
