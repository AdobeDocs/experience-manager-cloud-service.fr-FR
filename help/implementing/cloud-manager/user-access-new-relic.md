---
title: New Relic One
description: Découvrez le service de surveillance des performances de l’application New Relic One (APM) pour AEM as a Cloud Service et comment y accéder.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 8ae52afc366c6607cfc806f68bec2069a2e93f94
workflow-type: tm+mt
source-wordcount: '1612'
ht-degree: 10%

---


# Nouvelle relique {#user-access}

Découvrez le service de surveillance des performances de l’application New Relic One (APM) pour AEM as a Cloud Service et comment y accéder.

## Présentation {#introduction}

Adobe met l’accent sur la surveillance, la disponibilité et les performances de votre application. AEM as a Cloud Service permet d’accéder à une suite de surveillance Nouvelle Relique Un personnalisée dans le cadre de l’offre de produits standard afin de garantir à vos équipes une visibilité maximale sur vos mesures de performances d’environnement et de système as a Cloud Service.

Ce document décrit comment gérer l’accès aux fonctionnalités de surveillance des performances de la nouvelle application Relic One (APM) activées sur vos environnements as a Cloud Service AEM afin de vous aider à prendre en charge les performances et de tirer le meilleur parti d’AEM as a Cloud Service.

Lorsqu’un nouveau programme de production est créé, le sous-compte Nouvelle Relique Un associé à votre programme as a Cloud Service AEM est automatiquement créé.

## Fonctions {#transaction-monitoring}

Nouvelle version Une APM pour AEM as a Cloud Service comporte de nombreuses fonctionnalités.

* Accès direct à un compte Nouvelle relique (accès géré par l’assistance Adobe) dédié

* Un nouvel agent APM de Relic One qui affiche des appels de méthode exacts avec des numéros de ligne, y compris des dépendances externes et des bases de données

* Optimisation holistique des performances en combinant des mesures clés issues de la surveillance au niveau de l’infrastructure ainsi que de la surveillance des applications (Adobe Experience Manager).

* Exposition des Mbeans JMX as a Cloud Service AEM et contrôles de l’intégrité directement dans les mesures New Relic Insights , ce qui permet une inspection approfondie des performances de la pile d’applications et des mesures d’intégrité.

## Gérer les nouveaux utilisateurs Relatif à un {#manage-users}

Suivez ces étapes pour définir les utilisateurs de votre sous-compte Nouvelle Relique Un associé à votre programme as a Cloud Service AEM.

>[!NOTE]
>
>Un utilisateur dans **Propriétaire de l’entreprise** ou **Responsable de déploiement** doit être connecté pour gérer les utilisateurs Nouvelle Relique Un .

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez gérer vos nouveaux utilisateurs Relic One.

1. Au bas de la **Environnements** sur la page présentation du programme, cliquez sur le bouton représentant des points de suspension et sélectionnez **Gestion des utilisateurs**.

   ![Gestion des utilisateurs](assets/newrelic-manage-users.png)

   * Vous pouvez également accéder au **Gestion des utilisateurs** via le bouton représentant des points de suspension situé en haut de la page **Environnements** écran de votre programme.

1. Dans le **Gérer les nouveaux utilisateurs de la version** , saisissez le prénom et le nom de l’utilisateur que vous souhaitez ajouter, puis cliquez sur le bouton **Ajouter** bouton . Répétez cette étape pour tous les utilisateurs que vous souhaitez ajouter.

   ![Ajout d’utilisateurs](assets/newrelic-add-users.png)

1. Pour supprimer un nouvel utilisateur Relic One, cliquez sur le bouton de suppression à droite de la ligne représentant l’utilisateur.

1. Cliquez sur **Enregistrer** pour créer les utilisateurs.

Une fois les utilisateurs définis, Nouvelle Relique envoie un email de confirmation à chaque utilisateur auquel vous avez accordé l’accès afin que l’utilisateur puisse terminer le processus de configuration et se connecter.

>[!NOTE]
>
>Si vous gérez les utilisateurs Nouvelle Relique Un , vous devez également vous ajouter en tant qu’utilisateur afin d’y accéder. Être le **Propriétaire de l’entreprise** ou **Responsable de déploiement** ne suffit pas pour avoir accès à la Nouvelle Relique 1. Vous devez également vous créer en tant qu’utilisateur.

## Activation de votre nouveau compte d’utilisateur Relic One {#activate-account}

Une fois qu’un nouveau compte utilisateur Relic One est créé, comme décrit dans la section d’aperçu [Gérer les nouveaux utilisateurs Relatif à un](#manage-users), Nouvelle relique envoie à ces utilisateurs un email de confirmation à l’adresse fournie. Pour utiliser ces comptes, les utilisateurs doivent d’abord activer leurs comptes avec la nouvelle relique en réinitialisant leurs mots de passe.

Suivez ces étapes pour activer votre compte en tant que nouvel utilisateur Relic.

1. Cliquez sur le lien fourni dans l’e-mail à partir de Nouvelle Relique. Cela ouvre votre navigateur à la page de connexion Nouvelle relique .

1. Sur la page de connexion Nouvelle relique, sélectionnez **Vous avez oublié votre mot de passe ?**.

   ![Nouvelle connexion Relative](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Saisissez l’adresse email à laquelle vous avez reçu l’email de confirmation, puis sélectionnez **Envoyer mon lien de réinitialisation**.

   ![Entrez l’adresse électronique](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. Une nouvelle relique vous enverra un e-mail contenant un lien pour confirmer le compte.

Si vous ne recevez pas de courrier électronique de confirmation de la part de New Relic, reportez-vous à la section [section de dépannage .](#troubshooting)

## Accès à la nouvelle relique {#accessing-new-relic}

Une fois que vous avez [a activé votre compte Nouvelle relique,](#activate-account) vous pouvez accéder à Nouvelle Relique Un via Cloud Manager ou directement.

Pour accéder à la nouvelle version via Cloud Manager :

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez accéder à la Nouvelle Relique Un.

1. Au bas de la **Environnements** sur la page présentation du programme, cliquez sur le bouton représentant des points de suspension et sélectionnez **Ouvrir une nouvelle relique**.

   ![Gestion des utilisateurs](assets/newrelic-access.png)

   * Vous pouvez également accéder à Nouvelle relique à l’aide du bouton représentant des points de suspension situé en haut de la page **Environnements** écran de votre programme.

1. Dans le nouvel onglet du navigateur qui s’ouvre, connectez-vous à Nouvelle Relique Un.

Pour accéder directement à la Nouvelle Relique :

1. Accédez à la page de connexion de Nouvelle Relique à l’adresse [`https://login.newrelic.com/login`](https://login.newrelic.com/login)

1. Connectez-vous à la nouvelle Relique 1.

### Vérification de votre email {#verify-email}

Si vous êtes invité à vérifier votre adresse électronique lors de la connexion à la nouvelle Relique Un, cela signifie que votre adresse électronique est associée à plusieurs comptes. Vous pouvez ainsi choisir le compte auquel accéder.

Si vous ne vérifiez pas votre adresse e-mail, New Relic tentera de vous connecter avec l’enregistrement utilisateur le plus récemment créé associé à votre adresse e-mail. Pour éviter de vérifier votre email lors de chaque connexion, cliquez sur le bouton **Mémoriser** dans l’écran de connexion.

Pour obtenir de l’aide, veuillez ouvrir un ticket d’assistance via le [Portail d’assistance AEM](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

## Dépannage du nouvel accès Relic One {#troubleshooting}

Si vous avez été ajouté en tant que nouvel utilisateur Relic One , comme décrit dans la section . [Gérer les nouveaux utilisateurs Relatif à un](#manage-users) et ne parvient pas à localiser l’e-mail de confirmation de compte d’origine, procédez comme suit.

1. Accédez à la page de connexion de Nouvelle Relique à l’adresse [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Sélectionnez **Mot de passe oublié?**.

   ![Nouvelle connexion Relative](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Saisissez l’adresse électronique utilisée pour créer votre compte, puis sélectionnez **Envoyer mon lien de réinitialisation**.

   ![Entrez l’adresse électronique](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. Une nouvelle relique vous enverra un e-mail contenant un lien pour confirmer le compte.

Si vous avez terminé le processus d’inscription et que vous ne parvenez pas à vous connecter à votre compte en raison de messages d’erreur relatifs aux courriers électroniques ou aux mots de passe, enregistrez un ticket d’assistance via le [Admin Console.](https://adminconsole.adobe.com/)

Si vous ne recevez pas d’e-mail de New Relic :

* Vérifiez vos [filtres anti-spam](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* Le cas échéant, [ajoutez New Relic à votre liste d’e-mails autorisés](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
* Si aucune suggestion n’est d’une quelconque aide, veuillez fournir un commentaire sur le ticket d’assistance et l’équipe d’assistance Adobe vous aidera davantage.

## Limites {#limitations}

Les restrictions suivantes s’appliquent à l’ajout d’utilisateurs à la nouvelle version :

* 25 utilisateurs au maximum peuvent être ajoutés. Si le nombre maximal d’utilisateurs a été atteint, supprimez les utilisateurs afin de pouvoir ajouter de nouveaux utilisateurs.
* Les utilisateurs ajoutés à Nouvelle Relique seront du type **Restricted** voir [Pour plus d’informations, consultez la documentation Nouvelle relique .](https://docs.newrelic.com/docs/accounts/original-accounts-billing/original-users-roles/users-roles-original-user-model/#:~:text=In%20general%2C%20Admins%20take%20responsibility,Restricted%20Users%20can%20use%20them.&amp;text=One%20or%20more%20individual%20who,change)%20any%20New%20Relic%20features.)
* AEM as a Cloud Service ne propose que la nouvelle solution Relic One APM et ne prend pas en charge les intégrations d’alertes, de journalisation ou d’API.

Pour obtenir de l’aide ou des conseils supplémentaires sur les nouvelles offres Relic One de votre programme as a Cloud Service AEM, veuillez ouvrir un ticket d’assistance via le [Portail d’assistance AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Questions fréquentes sur la nouvelle relique {#faqs}

### Qu’est-ce qu’Adobe surveille avec la nouvelle relique ? {#adobe-monitor}

Adobe surveille les services as a Cloud Service de création, de publication et d’aperçu (le cas échéant) AEM par le biais du module externe Java de New Relic One. Adobe active la télémétrie et la surveillance personnalisées New Relic One APM dans les environnements as a Cloud Service de non-production et de production AEM.

Votre nouveau compte Relic One est associé à un Principal compte géré par l’Adobe et comporte plusieurs rapports d’applications : trois par environnement as a Cloud Service AEM.

* Une application pour le service de création par environnement
* Une application pour le service de publication par environnement (y compris la publication en or)
* Une application pour le service de prévisualisation par environnement

Remarque :

* Chaque application utilise une clé de licence.
* AEM les environnements as a Cloud Service ne signalent qu’un seul compte Nouvelle Relique Un .
* Les mesures et événements de surveillance complets pour la nouvelle version 1 sont conservés pendant sept jours.

### Qui peut accéder aux données du service cloud New Relic One ? {#access-new-relic-cloud}

Un accès complet en lecture est accordé à un maximum de 10 membres de votre équipe. L’accès en lecture comprend toutes les mesures APM collectées par l’agent Nouvelle Relique Un.

### La configuration SSO personnalisée est-elle prise en charge ? {#custom-sso}

La configuration SSO personnalisée n’est pas prise en charge pour le compte Nouvelle Relique Un fourni par Adobe.

### Que se passe-t-il si je dispose déjà d’un nouvel abonnement Relic sur site ? {#new-relic-subscription}

La nouvelle Relique Un est la nouvelle plateforme d’observabilité de Nouvelle Relique. Elle permet à l’assistance aux Adobes et à vos équipes d’observer, de surveiller et d’afficher les mesures et les événements, le tout à un seul endroit.

New Relic One offre aux utilisateurs la possibilité d’effectuer des recherches dans tous les comptes auxquels ils ont accès et de visualiser les données de tous les services et hôtes en une seule vue.

Bien que la prise en charge d’Adobe contrôle l’application as a Cloud Service AEM à l’aide de la nouvelle version et d’autres outils internes dans le cadre de votre service, vos équipes peuvent continuer à tirer parti de la nouvelle version pour les services hébergés sur site et l’infrastructure. Ils pourront visualiser les données provenant à la fois du compte Nouvelle Relique un Adobe et des comptes Nouvelle Relique gérés par le client.

>[!NOTE]
>
>Pour afficher les deux jeux de données dans la Nouvelle Relique Un, un utilisateur doit disposer des autorisations appropriées et utiliser la même méthodologie de connexion pour les deux comptes (Adobe la Nouvelle Relique Un et les nouveaux comptes gérés par le client).
