---
title: Comment configurer un environnement [!DNL AEM Forms] as a Cloud Service ?
description: Découvrez comment configurer un environnement [!DNL AEM Forms] as a Cloud Service
exl-id: 42f53662-fbcf-4676-9859-bf187ee9e4af
source-git-commit: b6dcb6308d1f4af7a002671f797db766e5cfe9b5
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 90%

---

# Intégration d’[!DNL AEM Forms] as a Cloud Service {#overview}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html) |
| AEM as a Cloud Service | Cet article |


## Choix des rôles {#personas-aem-forms-project}

<!-- When you sign up for the service, Adobe creates an Organization identifier for your company in the Adobe Identity Management System (IMS), where your users and their permissions can be managed. So, --> Avant de vous inscrire à un [!DNL AEM Forms] Environnement as a Cloud Service, déterminez les personnages et structurez une équipe pour votre projet. Un [!DNL AEM Forms] l’équipe de projet a les personnages suivants :

* **Concepteur d’expérience utilisateur** : il définit le style, la disposition et le branding des ressources [!DNL AEM Forms].

* **Professionnel Forms** : il crée des formulaires adaptatifs, des thèmes et des modèles en fonction du style, de la disposition et du branding fournis par le concepteur d’expérience utilisateur. Il crée et intègre également un formulaire adaptatif à un modèle de données de formulaire et des processus AEM. Il effectue généralement des tâches front-end.

* **Développeur Forms** : il développe une solution de formulaires personnalisée.  Il s’occupe généralement du développement back-end, tel que le développement de composants personnalisés, de processus AEM, de services de préremplissage, etc.

* **Administrateur AEM**: Un administrateur d’AEM aide à la configuration globale, comme la configuration des utilisateurs, le renforcement de l’environnement, la configuration des sources de données, la configuration des courriers électroniques et des logiciels tiers. Il aide également à réaliser les intégrations à Adobe Analytics, Adobe Target et Adobe Sign.

* **Utilisateur final** : il interagit avec le formulaire publié et l’envoie, signe les formulaires envoyés, suit les demandes envoyées via le portail web et reçoit des communications personnalisées.

<!-- While onboarding to the service, assign the following AEM groups to [!DNL AEM Forms] as a Cloud Service based on their role:

| User type | AEM group |
|---|---|
| Form Practitioner | forms-users (AEM Forms Users), template-authors, workflow-user, workflow-editors, and fdm-author  |
| UX Designer| forms-users, template-authors|
| End-User| <ul> <li>When a user must login to view and submit an Adaptive Form, add such users to forms-users group. </li> <li>When no user authentication is required to access Adaptive Forms, do not assign any group to such users. </li> </ul>| -->

## Intégration du service {#onboarding}

* [Intégrez](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html?lang=fr) [!DNL Adobe Experience Manager] as a Cloud Service.

* (Pour les sandbox uniquement) Après l’intégration du service, [créez](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=fr#how-to-use) et [exécutez](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=fr) les pipelines de production et hors production. Les dernières fonctionnalités d’[!DNL AEM Forms] as a Cloud Service sont ainsi activées et intégrées à votre environnement.

Vous pouvez utiliser Forms as a Cloud Service pour créer un formulaire adaptatif (inscription numérique) ou pour générer une communication client. Après avoir terminé l’[Intégration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html?lang=fr) à [!DNL Adobe Experience Manager] as a Cloud Service, effectuez l’une des actions suivantes pour activer les fonctionnalités d’inscription numérique ou de communication client. Vous pouvez également activer les deux fonctionnalités :

1. Connectez-vous à Cloud Manager et ouvrez votre instance AEM Forms as a Cloud Service.

1. Ouvrez l’option Modifier le programme, accédez à l’onglet Solutions et modules complémentaires, puis sélectionnez l’option **[!UICONTROL Formulaires - Communications]**.

   ![Communications](assets/communications.png)

   Si vous avez déjà activé l’option **[!UICONTROL Forms - Inscription numérique]**, sélectionnez l’option **[!UICONTROL Forms - Module complémentaire Communications]**.

   ![Module complémentaire](assets/add-on.png)

1. Cliquez sur **[!UICONTROL Mettre à jour]**.

1. Exécutez le pipeline de build. Une fois que le pipeline de build a réussi, les API Communications sont activées pour votre environnement.

>[!NOTE]
>
> Pour activer et configurer les API de manipulation de documents, ajoutez la règle suivante à la [Configuration du Dispatcher](setup-local-development-environment.md#forms-specific-rules-to-dispatcher) :
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

## Configuration des utilisateurs {#config-users}

Une fois l’intégration du service terminée, connectez-vous à votre environnement [!DNL AEM Forms] as a Cloud Service, ouvrez les instances d’auteur et de publication et ajoutez des utilisateurs aux [groupes AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=fr#accessing) spécifiques à Forms, en fonction de leur rôle. Le tableau ci-après répertorie les groupes AEM spécifiques à Forms prêts à l’emploi et les types d’utilisateurs correspondants. Le tableau fournit également un type d’instance AEM pour chaque type d’utilisateur :

| Types d’utilisateurs (rôles) | Groupes d’utilisateurs | Instance AEM |
|---|---|---|
| Professionnel Forms / Développeur Forms | <ul> <li> [!DNL forms-users] </li><li> [!DNL template-author] </li><li> [!DNL workflow-users] </li><li> [!DNL workflow-editors] </li><li> [!DNL fdm-authors] </li></ul> | Instance d’auteur |
| Concepteur d’expérience client (UX) | <ul> <li> [!DNL forms-users]</li><li> [!DNL template-author] </li></ul> | Instance d’auteur |
| Administrateur AEM | <ul> <li>[!DNL aem-administrators],</li> <li>[!DNL fd-administrators] </li> </ul> | Instances d’auteur et de publication |
| Utilisateur final | <ul> <li>Lorsqu’un utilisateur doit se connecter pour afficher et envoyer un formulaire adaptatif, ajoutez-le au groupe [!DNL forms-users]. </li> <li>Si aucune authentification utilisateur n’est requise pour accéder aux formulaires adaptatifs, n’attribuez aucun groupe à ces utilisateurs. </li> </ul> | Instances d’auteur et de publication |

Pour plus d’informations sur les groupes AEM spécifiques à Forms et les autorisations correspondantes, voir [Groupes et autorisations](forms-groups-privileges-tasks.md).

<!-- You can also create  [user groups](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) specific  to your organization, assign policies, and [users](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html#accessing) to the groups. The policies help control permissions of the users that are part of the group. For information a -->

## Étape suivante {#next-steps}

[Configuration d’un environnement de développement local](setup-local-development-environment.md). Vous pouvez utiliser l’environnement de développement local pour créer un formulaire adaptatif et des ressources connexes (thèmes, modèles, actions Envoyer personnalisées, service de préremplissage, etc.) et [convertir les formulaires PDF en formulaires adaptatifs](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/introduction.html?lang=fr) sans vous connecter à l’environnement de développement cloud.

<!-- ### Business unit and end-users {#business-unit-and-end-users}

| Role| Organization| Description|
|-----|-------|-----|
| UX Designer                  | Customer/System Integrator/Partner | Defines user experience design (style, layout, branding) as per organizational requirements for Adaptive Forms to allow AEM Forms practitioners to design the corresponding themes and templates.                                     |
| Forms Practitioner           | Customer                           | Authors Adaptive Forms, creates Form Data Model integrations, and creates business workflows using the Experience Manager Workflows. Typically undertakes the front-end work.                                                         |
| Business Executive - Digital | Customer                           | Responsible for business unit’s product marketing strategy and revenues, main business stakeholders for digital use cases, solutions, and service offerings for the end-users, signs off on the use case implementation and delivery. |
| Customer Experience Lead     | Customer                           | Business user persona. Authors, personalizes and updates Adaptive Forms fields/rules/styling, identifies, and prioritizes business needs. Validates business use-case with SI/Partner developers/practitioners during UAT.            |
| Forms Back-Office User       | Customer                           | End-user internal to organization filling forms, participating in back-office Forms workflows such as review/approval of applications etc.                                                                                            |
| Forms End-User               | External to customer               | Interacts with and submits the published form as end customer or citizen, signs submitted forms, tracks her applications through web portal, receives personalized interactive communications.                                        |

### Project team {#project-team}

| Role | Org | Description|
|-----|-----|-----|
| Experience Manager Administrator | System Integrator /Partner/Customer | Helps with overall installation, configures SSL certificates, configures data sources, email, and other third-party software, integrations like Adobe Analytics, Adobe Target, Automated Forms Conversion Services with Experience Manager instance. |
| Project Manager                  | System Integrator /Partner/Customer | Converts customer use-case into technical requirements, manages schedule/cost/scope for overall project.                                                                                                                                             |
| Product Owner                    | System Integrator /Partner/Customer | Prioritizes and evaluates scrum team's work for high-quality delivery on time.                                                                                                                                                                       |
| Scrum Master                     | System Integrator /Partner/Customer | Ensures agile values and processes in place to deliver on defined requirements as per prioritization by PO.                                                                                                                                          |
| Infrastructure / security expert | System Integrator /Partner/Customer | Provisions and configures best possible infrastructure, security controls and infra processes to address current and projected RASP requirements.                                                                                                    |
| Technical Architect              | System Integrator /Partner/Customer | Provides best high-level architecture and infrastructure guidance for use-case implementation and address RASP (Reliability, Availability, Scalability, and Performance) and security challenges.                                                    | -->

<!-- ## Onboard to the service {#onboarding}

[Onboard](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html) to the [!DNL Adobe Experience Manager] as a Cloud Service. 

After you onboard the service, configure a [local development environment](setup-local-development-environment.md). 

Administrators are responsible for managing Adobe software and services for their organization. Administrators grant access to developers in their organization to connect and use your [!DNL AEM Forms] as a Cloud Service program. When an administrator is provisioned for an organization, the administrator receives an email with title ‘You now have administrator rights to manage Adobe software and services for your organization’. If you are an administrator, check your mailbox for email with previously mentioned title and proceed to [add users](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#onboarding-users-in-admin-console) via IMS and assign [form-specific groups](forms-groups-privileges-tasks.md) to users based on their role.

## Next step {#next-steps} -->

<!-- ## Prerequisites {#prerequisites}

If you are new to AEM as a cloud service, contact your Adobe representative to create an organization identifier for your company in the Adobe Identity Management System (IMS). Once Adobe has created an organization for your company, your designated administrator is added as the first member of the organization. The administrator can setup an [!DNL AEM Forms] as a Cloud Service instance. 

## Onboard and set up a new environment {#onboard-and-setup-a-new-environment}

Log in to Cloud Manager and create a program. After the program is ready, create environments, add developers or users to environments, and run the pipeline to get the latest version of [!DNL AEM Forms] as a Cloud Service and start developing for your environment. The detailed steps are:

1. Contact your Adobe representative to create an organization identifier for your company in the Adobe Identity Management System (IMS) and provide access to an administrator in your organization.
1. Configure [Automated Forms Conversion Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html?lang=en). After a configuration is complete, a profile for Automated Forms Conversion Service is available in [Admin Console](https://adminconsole.adobe.com/).

    If the service is not available, log in to [Admin Console](https://adminconsole.adobe.com/). Use Adobe ID of administrator provisioned to use Automated Forms Conversion Service to login. Do not use any other ID or Federated ID to login.
    1. Click **[!UICONTROL Automated Forms Conversion Service]** option.
    1. Click **[!UICONTROL New Profile]** in the Products tab.
    1. Specify **[!UICONTROL Name]**, **[!UICONTROL Display Name]**, and **[!UICONTROL Description]** for the profile. Click **[!UICONTROL Done]**. A profile is created. 
1. Log in to [Cloud Manager](https://experience.adobe.com/#/@marketinghub/experiencemanager) and [create a program](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) for your organization.
1. [Create environments](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#adding-environments) within your program.
1. Log in to [Admin console](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/what-is-required/add-users-roles.html) and add developers or users to your organization.
1. Run the [build pipeline](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/how-to-use/deploying-code.html). It brings latest [!DNL Experience Manager Forms] as a Cloud Service features to your environment.
1. [Start developing](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) and creating Adaptive Forms on [!DNL Experience Manager Forms] as a Cloud Service environment.
1. Configure the [local development environment](setup-local-development-environment.md) for rapid development

## Configure dispatcher caching {#caching}

You can make dispatcher caching related configuration changes to code on your local development instance and deploy the changes to your [!DNL AEM Forms] as a Cloud Service instance. For details, see [update dispatcher configuration](setup-local-development-environment.md).
 -->
