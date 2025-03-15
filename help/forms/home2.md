---
title: Présentation d’ [!DNL AEM Forms]  as a Cloud Service
description: Découvrez AEM Forms pour créer des formulaires prêts à l’emploi et des workflows de gestion commerciale, et utiliser les services de document pour produire et protéger des documents.
landing-page-description: Découvrez comment utiliser les formulaires dans AEM as a Cloud Service.
role: Admin, Developer, User
feature: Adaptive Forms, Release Information
hide: true
hidefromtoc: true
source-git-commit: 2c41fae87821a28af1fd00701780e9fc52b5577d
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 12%

---


# AEM Forms as a Cloud Service {#introduction}

<!-- Version Navigation -->
<div class="version-selector">
  <p><strong>Vous recherchez de la documentation pour une autre version ?</strong></p>
  <ul>
    <li><a href="https://experienceleague.adobe.com/docs/experience-manager-65/forms/home.html">Documentation d’AEM 6.5 Forms</a></li>
    <li><strong>AEM Forms as a Cloud Service</strong> (Actif)</li>
  </ul>
</div>

## Qu’est-ce qu’AEM Forms as a Cloud Service ?

AEM Forms as a Cloud Service est une solution native d’Adobe dans le cloud permettant la création, la gestion et la diffusion de formulaires numériques et de communications. Il permet aux entreprises de transformer des transactions complexes en expériences digitales simples sur l’ensemble du parcours client. Vous pouvez utiliser le service pour effectuer les opérations suivantes :

* Numériser et rationaliser l’expérience d’inscription et d’intégration
* Diffuser des communications personnalisées
* Automatiser les workflows back-office
* Intégrer des formulaires et des expériences de communication aux sources de données
* Suivi et optimisation des performances des formulaires

Le service est toujours à jour, toujours disponible et évolue sans cesse. Les organisations peuvent utiliser [!DNL AEM Forms] as a Cloud Service et obtenir toutes ces fonctionnalités dans le cloud sans avoir besoin d’infrastructure locale. Ce service libère également les entreprises de cycles de mise à niveau complexes, car il est toujours à jour avec les dernières fonctionnalités.

Adobe [!DNL Experience Manager Forms as a Cloud Service] est une solution axée sur les clients et clientes qui prend en charge chaque étape du parcours client :

<div class="card-container">
  <div class="card">
    <div class="card-header">
      <h3>Formulaires adaptatifs</h3>
    </div>
    <div class="card-body">
      <p>Créez des formulaires dynamiques et réactifs qui s’adaptent aux entrées utilisateur et au type d’appareil :</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components">Créer un Forms adaptatif</a> - Créez des formulaires qui s’adaptent automatiquement à différentes tailles d’écran et entrées utilisateur</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type">Bibliothèque de composants riche</a> - Utilisez divers champs de saisie et composants d’interface utilisateur</li>
        <li><a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components">Style de Forms adaptative</a> - Appliquez une valorisation de marque et un design visuel cohérents à vos formulaires</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components">Utiliser des thèmes et des modèles préconfigurés</a> - Accélérez le développement avec des composants prêts à l’emploi</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/rule-editor-core-components/rule-editor-core-components">Validation de formulaire</a> - Implémentez des règles de validation côté client et côté serveur</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/configure-submit-actions-core-components">Actions Envoyer</a> - Configurer ce qui se passe lorsque les utilisateurs envoient des formulaires</li>
        <li><a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/generate-document-of-record-core-components">Document d’enregistrement</a> - Créez des enregistrements permanents des données de formulaire envoyées</li>
        <li><a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/create-or-add-an-adaptive-form-to-aem-sites-page">Ajouter Forms aux pages AEM Sites</a> - Intégrez facilement des formulaires à votre site web</li>
        <li><a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/integrate/services/embed-adaptive-form-core-components-external-web-page">Ajouter Forms à des pages de sites web tiers</a> - Intégrez facilement des formulaires à votre site web</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>API de communication</h3>
    </div>
    <div class="card-body">
      <p>Générer, manipuler et sécuriser des documents par programmation :</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#document-generation"> Générer des communications personnalisées </a> - Créez des documents personnalisés basés sur des modèles et des données</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#document-manipulation">Assembler et manipuler des fichiers PDF</a> - Combiner, fractionner et modifier des documents PDF</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#convert-to-and-validate-pdfa-compliant-documents">Créer des documents PDF/A</a> - Générer des documents de qualité archivée</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#signature-apis">Appliquer les signatures</a> - Sécuriser les documents avec des signatures</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#encryption-apis">Chiffrer et déchiffrer des PDF</a> - Protéger le contenu de documents sensibles</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#create-PS-PCL-ZPL-documents">Convertir XDP en PostScript</a> - Transformer des documents XDP au format PostScript</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#create-PS-PCL-ZPL-documents">Convertir XDP en PCL</a> - Transformer des documents XDP en langage de commande d’imprimante.</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#create-PS-PCL-ZPL-documents">Convertir XDP en ZPL</a> - Transformer des documents XDP en langage d’impression Zebra</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#convert-to-and-validate-pdfa-compliant-documents">Convertir PDF en normes PDF/A</a> - Créer des documents PDF conformes à l’archivage</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#convert-pdf-documents-to-pdf-x-standards">Ajouter des signatures numériques</a> - Signer numériquement des documents pour authentification</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Forms découplé</h3>
    </div>
    <div class="card-body">
      <p>Diffusez des expériences de formulaire sur n’importe quel canal ou framework frontal :</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-headless-adaptive-forms/using/overview">Présentation de Headless Forms</a> - Découvrez l’approche découplée des formulaires</li>
        <li>Créer des formulaires à l’aide de React ou d’autres frameworks frontend</li>
        <li>Intégrer des formulaires dans des applications mobiles, des sites web et des applications de chat</li>
        <li>Tirez parti des composants existants de l’interface utilisateur avec la fonctionnalité de formulaires.</li>
        <li>Conserver la logique de formulaire du serveur principal tout en offrant une flexibilité frontale</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Edge Delivery Services pour Forms</h3>
    </div>
    <div class="card-body">
      <p>Créez et diffusez des formulaires à l’aide de Edge Delivery Services :</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/overview">Présentation d’Edge Delivery Forms </a> - En savoir plus sur les formulaires avec Edge Delivery Services</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/universal-editor/getting-started-universal-editor">Éditeur universel pour Forms</a> - Créez des formulaires à l’aide de l’éditeur universel WYSIWYG</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial">Création basée sur des documents</a> - Créez des formulaires à l’aide de Microsoft Word ou Google Docs.</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/universal-editor/style-theme-forms">Style Edge Delivery Forms</a> - Appliquez un style personnalisé à vos formulaires</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Automatisation des workflows</h3>
    </div>
    <div class="card-body">
      <p>Automatisez les processus métier impliquant des formulaires et des documents :</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#assign-task-step">Créer des processus métier</a> - Acheminez les formulaires à des fins d’approbation ou de commentaires, les workflows après envoi ou les workflows principaux pour gérer les processus d’inscription</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#sign-document-step">Utiliser Adobe Sign dans un workflow AEM</a> - Envoyez un document pour signature </li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#generate-document-of-record-step">Générer un document d’enregistrement </a> - Générer un envoi à la demande ou sur formulaire</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Signatures électroniques</h3>
    </div>
    <div class="card-body">
      <p>Ajoutez des signatures électroniques juridiquement contraignantes à vos formulaires et documents :</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/integrate/services/adobe-sign-integration-adaptive-forms">Intégration Adobe Sign</a> - Activer les signatures électroniques dans le Forms adaptatif</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#sign-document-step">Ajouter des signatures électroniques aux workflows</a> - Inclure les étapes de signature dans les processus d’entreprise</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#generate-document-of-record-step">Document d’enregistrement avec signatures</a> - Génère des enregistrements signés des envois de formulaire</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Analyses et informations</h3>
    </div>
    <div class="card-body">
      <p>Obtenez des informations sur l’utilisation et les performances des formulaires :</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation">Activer Adobe Analytics</a> - Suivre l’utilisation et les performances des formulaires</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-aem-forms-with-adobe-analytics">Intégration manuelle d’Analytics</a> - Configuration d’Analytics pour le suivi détaillé</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/view-understand-aem-forms-analytics-reports">Afficher les rapports Analytics</a> - Analysez les performances des formulaires et le comportement des utilisateurs.</li>
      </ul>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Intégration de données </h3>
    </div>
    <div class="card-body">
      <p>Connectez les formulaires à vos sources de données et systèmes existants :</p>
      <h4>Écosystème Adobe</h4>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign">Adobe Sign</a> - Envoyez des signatures électroniques via Adobe Sign</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-adaptive-form-with-market-engage/integrate-form-to-marketo-engage">Marketo Engage</a> - Intégrer des formulaires à Adobe Marketo Engage</li>
        <li><a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#invoke-an-aem-workflow">Workflow AEM </a> - Déclenchez des workflows AEM avec des envois de formulaires.</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#workfront-fusion">Workfront</a> - Envoyer un formulaire adaptatif à Adobe Workfront Fusion</li>
      </ul>
      <h4>Intégrations Microsoft</h4>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-msdynamics">Microsoft Dynamics 365</a> - Intégration au CRM Microsoft</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage">Stockage Blob Azure</a> - Stockage des données de formulaire dans l’espace de stockage cloud Microsoft</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/connect-to-sharepoint/connect-forms-to-sharepoint-document-library">Bibliothèque de documents SharePoint </a> - Connexion aux bibliothèques de documents Microsoft SharePoint</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#connect-af-sharepoint-list">Liste SharePoint </a> - Connexion à la liste Microsoft SharePoint</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#submit-to-onedrive">OneDrive</a> - Connexion à Microsoft OneDrive</li>
        <li><a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/integrate/services/forms-microsoft-power-automate-integration">Microsoft Power Automate </a> - Déclencher les flux Microsoft Power Automate</li>
      </ul>
      <h4>Autres sources de données et services</h4>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/aem-forms-salesforce-integration">Salesforce</a> - Intégration à Salesforce CRM</li>
        <li><a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#submit-to-rest-endpoint">Services RESTful</a> - Se connecter à un point d’entrée de l’API REST</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-data-sources">Bases de données SGBDR</a> - Connexion aux bases de données relationnelles</li>
        <li><a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#send-email">E-mail</a> - Envoi de données de formulaire par e-mail</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/introduction-to-forms-portal/save-core-component-based-form-as-draft">Portail Forms </a> - Envoyer au portail Forms pour enregistrer le brouillon</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#send-pdf-via-email">Envoyer PDF par e-mail</a> - Envoyez par e-mail une version PDF du formulaire envoyé</li>
        <li><a href="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#submit-using-form-data-model">Envoyer à l’aide du modèle de données de formulaire</a> - Envoyer des données à l’aide d’un modèle de données de formulaire</li>
      </ul>
    </div>
  </div>
</div>

## Prise en main d’AEM Forms as a Cloud Service

<div class="card-container">
  <div class="card">
    <div class="card-header">
      <h3>Pour les utilisateurs professionnels</h3>
    </div>
    <div class="card-body">
      <ol>
        <li><strong>En savoir plus sur les principes de base </strong> : découvrez <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components">le Forms adaptatif</a> et comment il peut vous aider à numériser vos processus d’entreprise.</li>
        <li><strong>Explorer les modèles</strong> : parcourez les <a href="https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components">modèles et thèmes préconfigurés</a> pour vous familiariser avec les projets de formulaires.</li>
        <li><strong>En savoir plus sur la création de formulaires</strong> : suivez le <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/introduction-forms-authoring">guide de création de formulaires</a> pour créer votre premier formulaire.</li>
      </ol>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Pour les développeurs</h3>
    </div>
    <div class="card-body">
      <ol>
        <li><strong>Configuration de votre environnement</strong> : configurez votre <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-local-development-environment">environnement de développement local</a> pour AEM Forms.</li>
        <li><strong>Découvrir l’architecture</strong> : comprendre l’<a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/forms-overview/aem-forms-cloud-service-architecture">architecture d’AEM Forms as a Cloud Service</a>.</li>
        <li><strong>Explorer les API</strong> : familiarisez-vous avec <a href="https://developer-stage.adobe.com/experience-cloud/experience-manager-apis/api/stable/forms/"> les </a> d’API et les SDK disponibles pour étendre et intégrer Forms.</li>
      </ol>
    </div>
  </div>

<div class="card">
    <div class="card-header">
      <h3>Pour les administrateurs</h3>
    </div>
    <div class="card-body">
      <ol>
        <li><strong>Intégration à Cloud Service</strong> : suivez le <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-forms-cloud-service">guide d’intégration</a> pour configurer AEM Forms as a Cloud Service.</li>
        <li><strong>Configuration des services</strong> : configurez les <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation">intégrations à d’autres services Adobe</a> comme Adobe Analytics.</li>
        <li><strong>Migration depuis AEM 6.5</strong> : si vous venez d’AEM 6.5, suivez le <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html?lang=fr">guide de migration</a> pour migrer vers Cloud Service.</li>
      </ol>
    </div>
  </div>
</div>

## Fonctionnalités des premiers utilisateurs

<div class="card">
  <div class="card-header">
    <h3>Programme d’accès anticipé AEM Forms</h3>
  </div>
  <div class="card-body">
    <p>Le <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/forms-overview/early-access-ea-features">programme d’accès anticipé d’AEM Forms</a> offre un accès exclusif à des fonctionnalités de pointe avant qu’elles ne soient généralement disponibles, notamment :</p>
    <ul>
      <li><strong>Assistant AEM Forms AI (Gen AI)</strong> - Créez des formulaires plus rapidement avec des suggestions optimisées par l’IA</li>
      <li><strong>AEM Forms Workfront Fusion Connector </strong> - Automatisez les workflows déclenchés par les envois de formulaires</li>
      <li><strong>Conversational Forms</strong> - Créez des expériences de formulaire de style conversation sur n’importe quelle page AEM Sites.</li>
      <li><strong>Création WYSIWYG pour Edge Delivery </strong> - Créer des formulaires avec l’éditeur universel pour Edge Delivery Services</li>
      <li><strong>Connecteur AEM Forms vers Marketo </strong> - Intégrez les envois de formulaire à Marketo Engage.</li>
    </ul>
    <p>Pour obtenir une liste complète des innovations en matière d’accès anticipé et une documentation détaillée, consultez la page <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/forms-overview/early-access-ea-features">Programme d’accès anticipé AEM Forms</a>.</p>
  </div>
</div>

<div class="cta-card">
  <h3>Prêt à démarrer ?</h3>
  <p><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-forms-cloud-service">Intégrez AEM Forms as a Cloud Service</a> dès aujourd’hui et transformez l’expérience des formulaires numériques de votre entreprise.</p>
</div>

<style>
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  margin-bottom: 30px;
}

.card {
  flex: 1 1 calc(50% - 20px);
  min-width: 300px;
  border: 1px solid #e1e1e1;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
}

.card-header {
  background-color: #f5f5f5;
  padding: 15px 20px;
  border-bottom: 1px solid #e1e1e1;
}

.card-header h3 {
  margin: 0;
  color: #2c2c2c;
  font-size: 1.25rem;
}

.card-body {
  padding: 20px;
  background-color: #ffffff;
}

.card-body ul, .card-body ol {
  margin-top: 10px;
  padding-left: 25px;
}

.card-body li {
  margin-bottom: 8px;
}

.cta-card {
  background-color: #f0f7ff;
  border-left: 4px solid #1473e6;
  padding: 20px;
  margin: 30px 0;
  border-radius: 4px;
}

.cta-card h3 {
  margin-top: 0;
  color: #1473e6;
}

.cta-card a {
  font-weight: bold;
  color: #1473e6;
}

@media (max-width: 768px) {
  .card {
    flex: 1 1 100%;
  }
}
</style>
