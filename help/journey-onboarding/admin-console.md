---
title: Accès au Admin Console
description: Une fois que vous avez compris la préparation nécessaire à l’intégration et les bases de la structure AEMaaCS, vous êtes prêt à vous connecter pour la première fois au Admin Console.
exl-id: 0ccce328-a356-4ba9-b7fe-f67abc25b924
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 9%

---

# Accès au Admin Console {#accessing-admin-console}

Dans cette partie du [parcours d&#39;intégration,](overview.md) vous découvrirez la préparation nécessaire avant de vous connecter pour la première fois au système.

## Objectif {#objective}

Maintenant que vous avez lu l&#39;article [Terminologie as a Cloud Service AEM](terminology.md) et comprenez les principes de base de la structure AEMaaCS, vous êtes prêt à vous connecter pour la première fois au Admin Console.

En tant qu’administrateur système, vous êtes responsable de la gestion des utilisateurs au sein de votre entreprise. Pour ce faire, utilisez le Admin Console . Après avoir lu cette section, vous devez :

* Comprendre ce qu’est Adobe ID.
* Vous pouvez vous connecter à Admin Console.
* Découvrez comment vérifier vos privilèges en tant qu’administrateur système via Admin Console.
* Découvrez comment contacter l’assistance Adobe pour obtenir de l’aide.

## Le Admin Console {#admin-console}

Adobe Admin Console est un emplacement central pour administrer et gérer vos licences de produit et utilisateurs Adobe. Le Admin Console vous permet de créer et de gérer des utilisateurs à un seul emplacement plutôt qu’au sein de vos différentes solutions individuelles.

## Adobe ID {#adobe-id}

Pour vous connecter au Admin Console, vous aurez besoin d’une Adobe ID. Adobe ID est un compte lié à une adresse électronique spécifique qui est nécessaire pour se connecter et accéder à AEM as a Cloud Service ou à l’une de vos solutions d’Adobe. En utilisant votre Adobe ID, vous conservez tous vos plans et produits Adobe associés à un compte donné.

Lorsque vous, en tant qu’administrateur système, configurez votre équipe dans le Admin Console, vous indiquez l’adresse électronique qui sera utilisée comme Adobe ID.

Il existe trois types d’ID d’Adobe :

* **Identifiant personnel**: Il s’agit du type par défaut d’Adobe ID qui est créé sur adobe.com. Ce compte est géré par Adobe et tout le monde peut créer un compte de ce type.

* **Enterprise ID**: Les entreprises souhaitent généralement accroître le contrôle des comptes d’utilisateurs. Seuls les administrateurs système peuvent créer des Enterprise ID et l’entreprise possède ces comptes, avec un Adobe servant uniquement d’hôte.

* **Federated ID**: Avec les Federated ID, l’organisation prend la possession et le contrôle complets des comptes. Pour ce faire, votre entreprise doit intégrer Adobe Experience Cloud à votre système de connexion unique (SSO) SAML2. Cela permet aux utilisateurs de s’authentifier sur le système d’authentification unique de leur entreprise plutôt que sur un compte hébergé par Adobe.

En tant qu’administrateur système, vous pouvez décider d’intégrer votre équipe et vous-même à AEM as a Cloud Service à l’aide d’identifiants personnels avant la configuration des Enterprise ID ou des Federated ID. Une fois les Enterprise ID ou les Federated ID configurés, les membres peuvent passer à l’utilisation de ces ID.

## Connexion à Admin Console {#steps-admin-console}

Avant de pouvoir utiliser le Admin Console pour administrer les utilisateurs au sein de votre équipe, vous devez vous assurer que vous-même pouvez y accéder correctement et disposer des autorisations appropriées.

1. En tant qu’administrateur système, vous recevrez plusieurs courriers électroniques d’Adobe dans le cadre du processus d’intégration. Recherchez l’e-mail de bienvenue qui fournit des informations sur le nom de l’organisation auquel vous avez accès.

1. Cliquez sur le bouton **Prise en main** dans votre e-mail de bienvenue pour accéder à Admin Console. Si vous ne trouvez pas l’adresse électronique, ouvrez un navigateur directement sur le Admin Console à l’adresse [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

   ![E-mail de bienvenue](/help/journey-onboarding/assets/get-started-email.png)

1. Connectez-vous à l’aide de votre Adobe ID. Une fois la connexion établie, le **Présentation** de Adobe Admin Console.

   ![Le Admin Console](/help/journey-onboarding/assets/get-started1.png)

1. Si vous avez accès à plusieurs organisations, veillez à vous être connecté à la bonne organisation. Pour modifier votre organisation, cliquez sur le nom de l’organisation dans le coin supérieur droit et sélectionnez l’organisation à laquelle vous avez besoin d’accéder.

   ![Change org](/help/journey-onboarding/assets/admin-console-orgswitch.png)

1. Sélectionner **Administrateurs** de la **Utilisateurs** pour vérifier que vous êtes un administrateur système.

   ![Révision des administrateurs](/help/journey-onboarding/assets/get-started2.png)

1. Une fois que vous avez cliqué sur **Administrateurs** de la **Utilisateurs** , vous pouvez effectuer une recherche en saisissant votre adresse électronique, votre nom d’utilisateur, votre prénom ou votre nom Adobe ID.

   ![Rechercher des utilisateurs](/help/journey-onboarding/assets/get-started3.png)

1. Si tout fonctionne correctement, la recherche renvoie votre enregistrement. Si la valeur de la variable **RÔLE D’ADMINISTRATION** la colonne affiche **Système**, vous savez que vous (ou l’utilisateur affiché) êtes un administrateur système.

   ![État du système](/help/journey-onboarding/assets/get-started4.png)

Félicitations, administrateur système !

## Système Adobe Identity Management {#ims}

AEM as a Cloud Service est préconfiguré avec Adobe Identity Management System (également appelé IMS) pour l’authentification. Pour activer cette fonctionnalité, vous n’avez rien à faire en tant qu’administrateur système.

En utilisant IMS, AEM as a Cloud Service consolide l’expérience de connexion entre AEM et le reste de Adobe Experience Cloud. Les entreprises qui disposent de plusieurs produits Adobe en bénéficient notamment en créant des groupes basés sur les rôles dans le Admin Console, puis en attribuant l’accès à plusieurs produits, y compris AEM as a Cloud Service via IMS.

Vous en apprendrez plus sur les profils de produit et l’affectation d’utilisateurs dans la prochaine partie de ce parcours d’intégration.

## Contacter le support technique d’Adobe {#support}

Si vous rencontrez des problèmes, vous pouvez accéder à la prise en charge des Adobes via le Admin Console. Le **Assistance** vous permet d’accéder à différentes fonctions de prise en charge des Adobes grâce à une interface simple et conviviale.

![Onglet Assistance](/help/journey-onboarding/assets/support-menu.png)

L’onglet permet de créer et de gérer des cas, de discuter directement avec des représentants de l’assistance clientèle Adobe et de planifier des sessions avec des experts. Les administrateurs système et les administrateurs du support doivent se connecter pour accéder aux dossiers d’assistance et aux options de session d’experts.

## Prochaines étapes {#whats-next}

Maintenant que vous avez lu ce document, vous devez :

* Comprendre ce qu’est Adobe ID.
* Vous pouvez vous connecter à Admin Console.
* Découvrez comment vérifier vos privilèges en tant qu’administrateur système via Admin Console.
* Découvrez comment contacter l’assistance Adobe pour obtenir de l’aide.

Vous êtes prêt à poursuivre votre parcours d’intégration en apprenant à [affecter des membres de l’équipe aux profils de produit Cloud Manager](assign-profiles-cloud-manager.md) afin que vos collègues puissent également accéder à AEMaaCS.

## Ressources supplémentaires {#additional-resources}

* [Présentation du Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html) - Présentation complète du Admin Console
* [Création ou mise à jour de votre Adobe ID](https://helpx.adobe.com/fr/manage-account/using/create-update-adobe-id.html#HowtocreateorupdateyourAdobeID) - Découvrez comment créer une Adobe ID, la modifier et gérer plusieurs identifiants d’Adobe.
* [Gestionnaire d’authentification SAML 2.0](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/saml-2-0-authenticationhandler.html) - AEM est fourni avec un gestionnaire d’authentification SAML. Ce gestionnaire fournit la prise en charge du protocole de requête d’authentification SAML 2.0 (profil web-SSO) à l’aide de la liaison HTTP POST.
* [Rôles administratifs](https://helpx.adobe.com/fr/enterprise/using/admin-roles.ug.html) - Grâce à Adobe Admin Console, les entreprises peuvent définir une hiérarchie administrative flexible qui permet une gestion affinée de l’accès et de l’utilisation des produits Adobe.
* [Sessions d’assistance et d’experts](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) - Découvrez comment accéder aux options d’assistance sur le Admin Console, gérer vos cas d’assistance, planifier une session d’experts, etc.
