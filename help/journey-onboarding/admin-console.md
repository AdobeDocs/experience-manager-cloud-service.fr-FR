---
title: Accéder à Admin Console
description: Une fois que vous avez compris la préparation nécessaire à l’intégration et les principes de base de la structure d’AEM as a Cloud Service, vous êtes prêt à vous connecter pour la première fois à Admin Console.
exl-id: 0ccce328-a356-4ba9-b7fe-f67abc25b924
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 8ed13eb6f476bab07da07549a83ab9ac16bdea72
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 55%

---

# Accéder à Admin Console {#accessing-admin-console}

Dans cette partie du [parcours d’intégration](overview.md), vous découvrirez la préparation nécessaire avant de vous connecter pour la première fois au système.

## Objectif {#objective}

Maintenant que vous avez lu l’article [Terminologie d’AEM as a Cloud Service](terminology.md) et comprenez les principes de base de la structure AEMaaCS, vous êtes prêt à vous connecter pour la première fois à Admin Console.

En tant qu’administrateur système, vous êtes responsable de la gestion des utilisateurs au sein de votre organisation à l’aide d’Admin Console. Après avoir lu cette section, vous devriez être en mesure d’effectuer les opérations suivantes :

* Comprendre ce qu’est un Adobe ID.
* Pouvoir se connecter à l’Admin Console.
* Découvrez comment vérifier vos privilèges en tant qu’administrateur système au moyen d’Admin Console.
* Savoir comment contacter l’assistance d’Adobe pour obtenir de l’aide.

## À propos d’Admin Console {#admin-console}

Adobe Admin Console désigne un emplacement central pour administrer et gérer vos utilisateurs et licences de produits Adobe. Admin Console vous permet de créer et gérer des utilisateurs dans un seul emplacement plutôt qu’au sein de vos différentes solutions individuelles.

### Adobe ID {#adobe-id}

Pour vous connecter à Admin Console, vous aurez besoin d’un Adobe ID. Un Adobe ID est un compte lié à une adresse e-mail spécifique. C’est nécessaire pour se connecter et accéder à AEM as a Cloud Service ou à l’une de vos solutions Adobe. En utilisant votre Adobe ID, vous conservez tous vos plans et produits Adobe associés à un seul compte.

En tant qu’administrateur ou administratrice système, lorsque vous configurez votre équipe dans l’Admin Console, vous indiquez l’adresse e-mail qui est utilisée comme Adobe ID.

Il existe trois types d’Adobe ID :

* **Personal ID** : type par défaut d’Adobe ID, qui est créé sur adobe.com. Géré par Adobe et accessible à tous.

* **Enterprise ID** : les entreprises souhaitent généralement accroître le contrôle des comptes des utilisateurs. Seuls les administrateurs système peuvent créer des Enterprise ID. L’entreprise possède ces comptes, Adobe servant uniquement d’hôte.

* **Federated ID** : avec les Federated ID, l’organisation prend pleinement possession et le contrôle des comptes. Votre entreprise doit intégrer Adobe Experience Cloud à votre système d’authentification unique (SSO) SAML2. Cela permet aux utilisateurs de s’authentifier sur le système d’authentification unique de leur entreprise plutôt que sur un compte hébergé par Adobe.

En tant qu’administrateur système, vous pouvez intégrer votre équipe et vous-même à AEM as a Cloud Service avec des ID personnels. Effectuez cette tâche avant que les Enterprise ID ou les Federated ID ne soient en place. Une fois les Enterprise ID ou les Federated ID configurés, les membres peuvent être transférés à l’utilisation de ces ID.

### Connexion directe à Admin Console {#steps-admin-console}

Avant de pouvoir utiliser Admin Console pour administrer les utilisateurs au sein de votre équipe, vous devez vous assurer de pouvoir vous-même y accéder correctement et de disposer des autorisations appropriées.

1. En tant qu’administrateur système, vous recevez plusieurs e-mails d’Adobe dans le cadre du processus d’intégration. Recherchez l’e-mail de bienvenue qui fournit des informations sur le nom de l’organisation à laquelle vous avez accès.

1. Cliquez sur le lien **Commencer** dans l’e-mail de bienvenue pour accéder à Admin Console. Si vous ne retrouvez pas l’e-mail en question, ouvrez un navigateur directement sur Admin Console à l’adresse [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

   ![E-mail de bienvenue](/help/journey-onboarding/assets/get-started-email.png)

1. Connectez-vous à l’aide de votre Adobe ID. Une fois la connexion établie, la page **Aperçu** d’Adobe Admin Console s’affiche.

   ![Admin Console.](/help/journey-onboarding/assets/get-started1.png)

1. Si vous avez accès à plusieurs organisations, vérifiez que vous vous êtes connecté à la bonne organisation. Pour modifier votre organisation, cliquez sur le nom de l’organisation dans le coin supérieur droit de l’écran et sélectionnez l’organisation à laquelle vous avez besoin d’accéder.

   ![Modifier l’organisation](/help/journey-onboarding/assets/admin-console-orgswitch.png)

1. Sélectionnez **Administrateurs** dans la vignette **Utilisateurs** pour vérifier que vous êtes bien administrateur système.

   ![Consulter la liste des administrateurs](/help/journey-onboarding/assets/get-started2.png)

1. Une fois que vous avez cliqué sur **Administrateurs** à partir de la vignette **Utilisateurs**, vous pouvez effectuer une recherche en saisissant votre adresse e-mail Adobe ID, votre nom d’utilisateur, votre prénom ou votre nom.

   ![Rechercher des utilisateurs](/help/journey-onboarding/assets/get-started3.png)

1. Si tout fonctionne correctement, la recherche renvoie votre enregistrement. Si la valeur qui s’affiche dans la colonne **RÔLE D’ADMINISTRATEUR** est **Système**, alors vous savez que vous (ou l’utilisateur affiché) êtes un administrateur système.

   ![Statut du système](/help/journey-onboarding/assets/get-started4.png)

Félicitations, vous êtes administrateur système !

## Accès à Admin Console via Experience Hub  {#access-admin-console-via-experience-hub}

[Experience Hub](/help/experience-hub.md) est la page d’accueil personnalisée et unifiée d’AEM. AEM Tools et Admin Console sont ainsi réunis en un seul endroit.

![Option Admin Console telle qu&#39;elle apparaît sur la page d&#39;accueil Experience Hub](/help/journey-onboarding/assets/experiencehub-adminconsole1.png)

**Pour accéder à Admin Console via Experience Hub :**

1. Cliquez sur [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home) pour ouvrir la page d’accueil d’Experience Hub.

1. Dans le regroupement **Accès rapide**, cliquez sur [**Admin Console**](https://experience.adobe.com).

## Système Adobe Identity Management {#ims}

Pour l’authentification, AEM as a Cloud Service est préconfiguré avec le système Identity Management (IMS) d’Adobe. En tant qu’administrateur système, vous n’avez rien à faire pour activer cette fonctionnalité.

En utilisant IMS, AEM as a Cloud Service consolide l’expérience de connexion entre AEM et le reste des applications et services d’Adobe Experience Cloud. Les entreprises qui disposent de nombreux produits Adobe y gagnent le plus. Créez des groupes basés sur les rôles dans Admin Console et accordez l’accès aux produits par le biais d’IMS, comme AEM as a Cloud Service.

Vous en apprendrez plus sur les profils de produit et l’affectation d’utilisateurs dans la prochaine partie de ce parcours d’intégration.

## Contactez l’assistance Adobe {#support}

Si vous rencontrez des problèmes, l’assistance d’Adobe est accessible via Admin Console. L’onglet **Assistance** permet d’accéder à diverses fonctions d’assistance Adobe par le biais d’une interface simple et facile à utiliser.

![Onglet Assistance](/help/journey-onboarding/assets/support-menu.png)

L’interface vous permet de créer et de gérer des cas, de discuter directement avec des représentants de l’assistance clientèle d’Adobe et de planifier des sessions avec des experts. Les administrateurs système et les administrateurs de l’assistance doivent se connecter pour accéder aux cas d’assistance et aux options de session d’experts.

## Prochaines étapes {#whats-next}

Maintenant que vous avez lu ce document, vous devriez :

* Comprendre ce qu’est un Adobe ID.
* Pouvoir se connecter à l’Admin Console.
* Découvrez comment vérifier vos privilèges en tant qu’administrateur système à l’aide d’Admin Console.
* Savoir comment contacter l’assistance d’Adobe pour obtenir de l’aide.

Vous êtes prêt à poursuivre votre parcours d’intégration en apprenant à [affecter des membres de l’équipe aux profils de produit Cloud Manager](assign-profiles-cloud-manager.md) afin que vos collègues puissent également accéder à AEMaaCS.

## Ressources supplémentaires {#additional-resources}

Vous trouverez ci-dessous des ressources facultatives supplémentaires si vous souhaitez aller au delà du contenu du parcours d’intégration.

* [Présentation d’Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) - Présentation complète d’Admin Console
* [Créer ou mettre à jour votre Adobe ID](https://helpx.adobe.com/fr/manage-account/using/create-update-adobe-id.html#HowtocreateorupdateyourAdobeID) - Découvrez comment créer un Adobe ID, le modifier et gérer plusieurs Adobe ID.
* [Gestionnaire d’authentification SAML 2.0](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/security/saml-2-0-authenticationhandler#) - AEM est fourni avec un gestionnaire d’authentification SAML. Ce gestionnaire fournit la prise en charge du protocole de requête d’authentification SAML 2.0 (profil web-SSO) à l’aide de la liaison HTTP POST.
* [Rôles administratifs](https://helpx.adobe.com/fr/enterprise/using/admin-roles.html) - Grâce à Adobe Admin Console, les entreprises peuvent définir une hiérarchie administrative flexible qui permet une gestion affinée de l’accès et de l’utilisation des produits Adobe.
* [Sessions d’assistance et d’experts](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.html) - Découvrez comment accéder aux options d’assistance sur Admin Console, gérer vos cas d’assistance, planifier une session d’experts, etc.
