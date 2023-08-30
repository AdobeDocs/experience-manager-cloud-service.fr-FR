---
title: New Relic One
description: Découvrez le service de surveillance des performances de l’application New Relic One (APM) pour AEM as a Cloud Service et comment y accéder.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 8ce7c26c6552c77bc845f76a805768a931b9d532
workflow-type: tm+mt
source-wordcount: '1627'
ht-degree: 77%

---


# New Relic One {#user-access}

Découvrez le service de surveillance des performances de l’application New Relic One (APM) pour AEM as a Cloud Service et comment y accéder.

## Présentation  {#introduction}

Adobe accorde une importance considérable à la surveillance, la disponibilité et les performances de votre application. AEM as a Cloud Service permet d’accéder à une suite de surveillance New Relic personnalisée dans le cadre de l’offre de produit standard. Vos équipes bénéficient ainsi d’une visibilité maximale sur les mesures de performances de votre système et de votre environnement AEM as a Cloud Service.

Ce document décrit comment gérer l’accès aux fonctionnalités de surveillance des performances de l’application (APM) New Relic One activées dans vos environnements AEM as a Cloud Service afin de vous aider à prendre en charge les performances et de tirer le meilleur parti d’AEM as a Cloud Service.

Lorsqu’un nouveau programme de production est créé, le sous-compte New Relic One associé à votre programme AEM as a Cloud Service est automatiquement créé.

## Fonctionnalités {#transaction-monitoring}

Les fonctionnalités de surveillance des performances (APM) de l’application New Relic One d’AEM as a Cloud Service sont nombreuses.

* Accès direct à un compte New Relic One dédié

* Un agent APM New Relic One instrumenté qui illustre les appels de méthode exacts avec les numéros de ligne, y compris les dépendances externes et les bases de données

* Optimisation holistique des performances en combinant des mesures clés issues de la surveillance au niveau de l’infrastructure et de la surveillance des applications (Adobe Experience Manager)

* Exposition de JMX Mbeans d’AEM as a Cloud Service et des contrôles d’intégrité directement dans les mesures Insights de New Relic, ce qui permet une inspection approfondie des performances de la pile d’applications et des mesures d’intégrité.

## Gérer les utilisateurs New Relic One {#manage-users}

Suivez ces étapes pour définir les utilisateurs de votre sous-compte New Relic One relatifs à votre programme AEM as a Cloud Service.

>[!NOTE]
>
>Un utilisateur ayant le rôle de **propriétaire de l’entreprise** ou de **responsable de déploiement** doit être connecté pour gérer les utilisateurs New Relic One.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez gérer vos utilisateurs New Relic One.

1. Au bas de la vignette **Environnements** sur la page de présentation du programme, cliquez sur le bouton représentant des points de suspension et sélectionnez **Gérer les utilisateurs**.

   ![Gérer les utilisateurs](assets/newrelic-manage-users.png)

   * Vous pouvez également accéder à l’option **Gérer les utilisateurs** via le bouton représentant des points de suspension situé en haut de l’écran **Environnements** de votre programme.

1. Dans la boîte de dialogue **Gérer les utilisateurs New Relic**, saisissez le prénom et le nom de l’utilisateur que vous souhaitez ajouter, puis cliquez sur le bouton **Ajouter**. Répétez cette étape pour tous les utilisateurs que vous souhaitez ajouter.

   ![Ajouter des utilisateurs](assets/newrelic-add-users.png)

1. Pour supprimer un utilisateur New Relic One, cliquez sur le bouton de suppression à l’extrémité droite de la ligne représentant l’utilisateur.

1. Cliquez sur **Enregistrer** pour créer les utilisateurs.

Une fois les utilisateurs définis, New Relic envoie un e-mail de confirmation à chaque utilisateur auquel vous avez accordé l’accès afin que l’utilisateur puisse terminer le processus de configuration et se connecter.

>[!NOTE]
>
>Si vous gérez les utilisateurs de New Relic One, vous devez également vous ajouter en tant qu’utilisateur pour y avoir accès. Être le **propriétaire de l’entreprise** ou le **responsable de déploiement** ne suffit pas pour avoir accès à New Relic One. Vous devez également vous créer en tant qu’utilisateur.

## Activer votre compte d’utilisateur New Relic One {#activate-account}

Une fois qu’un compte d’utilisateur New Relic One est créé, comme décrit dans la section d’aperçu [Gérer les utilisateurs New Relic One](#manage-users), New Relic envoie à ces utilisateurs un e-mail de confirmation à l’adresse fournie. Pour utiliser ces comptes, les utilisateurs doivent d’abord activer leurs comptes avec New Relic en réinitialisant leurs mots de passe.

Suivez ces étapes pour activer votre compte en tant qu’utilisateur New Relic.

1. Cliquez sur le lien fourni dans l’e-mail à partir de New Relic. Cela ouvre votre navigateur à la page de connexion New Relic.

1. Sur la page de connexion New Relic, sélectionnez **Mot de passe oublié ?**.

   ![Nom d’utilisateur New Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Saisissez l’adresse e-mail à laquelle vous avez reçu l’e-mail de confirmation, puis sélectionnez **Envoyer mon lien de réinitialisation**.

   ![Entrer l’adresse e-mail](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic vous enverra un e-mail contenant un lien pour confirmer le compte.

Si vous ne recevez pas de courrier électronique de confirmation de New Relic, reportez-vous à la section [section de dépannage .](#troubshooting)

## Accéder à New Relic One {#accessing-new-relic}

Une fois que vous avez [activé votre compte New Relic,](#activate-account) vous pouvez accéder à New Relic One via Cloud Manager ou directement.

Pour accéder à New Relic One via Cloud Manager :

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez accéder à New Relic One.

1. Au bas de la vignette **Environnements** sur la page de présentation du programme, cliquez sur le bouton représentant des points de suspension, puis sélectionnez **Ouvrir New Relic**.

   ![Gérer les utilisateurs](assets/newrelic-access.png)

   * Vous pouvez également accéder à New Relic à l’aide du bouton représentant des points de suspension situé en haut de l’écran **Environnements** de votre programme.

1. Dans le nouvel onglet du navigateur qui s’ouvre, connectez-vous à New Relic One.

Pour accéder directement à New Relic One :

1. Accédez à la page de connexion de New Relic à l’adresse [`https://login.newrelic.com/login`](https://login.newrelic.com/login)

1. Connectez-vous à New Relic One.

### Vérification de votre e-mail {#verify-email}

Si vous êtes invité(e) à vérifier votre e-mail lors de la connexion à la New Relic One, cela signifie que celui-ci est associé à plusieurs comptes. Vous pouvez ainsi choisir le compte auquel accéder.

Si vous ne vérifiez pas votre adresse électronique, New Relic tente de vous connecter avec l’enregistrement d’utilisateur créé le plus récemment associé à votre adresse électronique. Pour éviter de vérifier votre e-mail à chaque connexion, cochez la case **Mémoriser mon adresse** dans l’écran de connexion.

Pour obtenir de l’aide, ouvrez un ticket d’assistance au moyen de l’option [Portail d’assistance AEM](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

## Dépanner l’accès à New Relic One {#troubleshooting}

Si vous avez été ajouté en tant qu’utilisateur New Relic One comme décrit dans la section [Gestion des utilisateurs New Relic One](#manage-users) et ne parvient pas à localiser l’e-mail de confirmation de compte d’origine, procédez comme suit.

1. Accédez à la page de connexion de New Relic à l’adresse [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Sélectionnez **Mot de passe oublié ?**.

   ![Nom d’utilisateur New Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Saisissez l’adresse e-mail utilisée pour créer votre compte, puis sélectionnez **Envoyer mon lien de réinitialisation**.

   ![Saisir l’adresse e-mail](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic vous enverra un e-mail contenant un lien pour confirmer le compte.

Si vous avez terminé le processus d’inscription et que vous ne parvenez pas à vous connecter à votre compte en raison de messages d’erreur relatifs au courrier électronique ou au mot de passe, enregistrez un ticket d’assistance au moyen de l’option [Admin Console.](https://adminconsole.adobe.com/)

Si vous ne recevez pas de courrier électronique de New Relic :

* Vérifiez vos [filtres anti-spam](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* Le cas échéant, [ajoutez New Relic à votre liste d’e-mails autorisés](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
* Si aucune suggestion n’est utile, fournissez des commentaires sur le ticket d’assistance et l’équipe d’assistance Adobe peut vous aider.

## Restrictions {#limitations}

Les restrictions suivantes s’appliquent à l’ajout d’utilisateurs à New Relic One :

* 30 utilisateurs ou utilisatrices au maximum peuvent être ajouté(e)s. Si le nombre maximal d’utilisateurs a été atteint, supprimez les utilisateurs pour pouvoir ajouter de nouveaux utilisateurs.
* Les utilisateurs ajoutés à New Relic sont du type **Restricted**, voir [pour plus d’informations, consultez la documentation de New Relic .](https://docs.newrelic.com/docs/accounts/original-accounts-billing/original-users-roles/users-roles-original-user-model/#:~:text=In%20general%2C%20Admins%20take%20responsibility,Restricted%20Users%20can%20use%20them.&amp;text=One%20or%20more%20individuals%20who,change)
* AEM as a Cloud Service ne propose que la solution New Relic One APM et ne prend pas en charge les intégrations d’alertes, de journalisation ou d’API.

Pour obtenir de l’aide ou des conseils supplémentaires sur les offres New Relic One de votre programme as a Cloud Service AEM, ouvrez un ticket d’assistance via le [Portail d’assistance AEM](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

## Questions fréquentes sur New Relic One {#faqs}

### Que surveille Adobe avec New Relic One ? {#adobe-monitor}

Adobe contrôle les services de création, de publication et de prévisualisation (le cas échéant) d’AEM as a Cloud Service via le plug-in Java de New Relic One. Adobe active la télémétrie et la surveillance personnalisées de New Relic One APM dans les environnements de production et hors production d’AEM as a Cloud Service.

Votre compte New Relic One est associé à un compte principal géré par Adobe et comporte plusieurs rapports d’applications : trois par environnement AEM as a Cloud Service.

* Une application pour le service de création par environnement.
* Une application pour le service de publication par environnement (y compris la publication Golden).
* Une application pour le service de prévisualisation par environnement.

Remarque :

* Chaque application utilise une clé de licence.
* Les environnements AEM as a Cloud Service ne signalent qu’un seul compte New Relic One.
* Les mesures et événements de surveillance complets pour chaque New Relic One sont conservés pendant sept jours.

### Adobe envoie-t-il des notifications d’alerte à partir de New Relic One ? {#alerting-new-relic}

Adobe fournit un accès à New Relic One à des fins d’observabilité uniquement et ne l’utilise pas pour les alertes client ou les alertes opérationnelles internes. Des notifications pour tout incident sont envoyées à l’aide de [profils de notification utilisateur.](/help/journey-onboarding/notification-profiles.md)

### Qui peut accéder aux données du service cloud de New Relic One ? {#access-new-relic-cloud}

L’accès en lecture complète est accordé à 30 membres au maximum de votre équipe. L’accès en lecture comprend toutes les mesures APM collectées par l’agent New Relic One.

### La configuration personnalisée de la fonction SSO est-elle prise en charge ? {#custom-sso}

La configuration personnalisée de la fonction SSO n’est pas prise en charge pour le compte New Relic One fourni par Adobe.

### Que se passe-t-il si vous disposez déjà d’un abonnement New Relic sur site ? {#new-relic-subscription}

New Relic One est la nouvelle plateforme d’observabilité de New Relic. Elle permet à l’assistance d’Adobe et à vos équipes d’observer, de surveiller et d’afficher les mesures et les événements, le tout à un seul endroit.

New Relic One offre aux utilisateurs la possibilité d’effectuer des recherches dans tous les comptes auxquels ils ont accès et de visualiser les données de tous les services et hôtes en une seule vue.

Bien que la prise en charge d’Adobe contrôle l’application as a Cloud Service AEM à l’aide de New Relic One et d’autres outils internes dans le cadre de votre service, vos équipes peuvent continuer à utiliser New Relic pour les services hébergés sur site et l’infrastructure. Ils peuvent visualiser les données provenant des comptes New Relic One Adobe et New Relic gérés par le client.

>[!NOTE]
>
>Pour afficher les deux jeux de données dans New Relic One, un utilisateur doit disposer des autorisations appropriées et utiliser la même méthodologie de connexion pour les deux comptes (New Relic One d’Adobe et les comptes New Relic gérés par le client).
