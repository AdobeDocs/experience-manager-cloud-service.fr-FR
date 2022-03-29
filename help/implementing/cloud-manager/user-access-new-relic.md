---
title: Nouvelle relique
description: Découvrez le service de surveillance des performances de l’application New Relic One (APM) pour AEM as a Cloud Service et comment y accéder.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 6cf164093cc543fe4847859b248e70efd86efbb1
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 18%

---


# Nouvelle relique {#user-access}

Découvrez le service de surveillance des performances de l’application New Relic One (APM) pour AEM as a Cloud Service et comment y accéder.

## Présentation {#introduction}

Adobe met l’accent sur la surveillance, la disponibilité et les performances de votre application. Pour atteindre cet objectif, AEM as a Cloud Service permet d’accéder à une suite de surveillance Nouvelle Relique Un personnalisée dans le cadre de l’offre de produits standard afin de vous assurer que vos équipes disposent d’une visibilité maximale sur vos mesures de performances de système et d’environnement as a Cloud Service.

Ce document décrit les fonctionnalités de surveillance des performances de la nouvelle application Relic One (APM) activées dans vos environnements as a Cloud Service AEM afin de vous aider à prendre en charge les performances et de tirer le meilleur parti d’AEM as a Cloud Service.

## Fonctions {#transaction-monitoring}

Nouvelle version Une APM pour AEM as a Cloud Service comporte de nombreuses fonctionnalités.

* Accès direct à un compte Nouvelle relique (accès géré par l’assistance Adobe) dédié

* Un nouvel agent APM de Relic One qui affiche des appels de méthode exacts avec des numéros de ligne, y compris des dépendances externes et des bases de données

* Optimisation holistique des performances en combinant des mesures clés issues de la surveillance au niveau de l’infrastructure ainsi que de la surveillance des applications (Adobe Experience Manager).

* Exposition des Mbeans JMX as a Cloud Service AEM et contrôles de l’intégrité directement dans les mesures New Relic Insights , ce qui permet une inspection approfondie des performances de la pile d’applications et des mesures d’intégrité.

## Accès à la nouvelle relique {#accessing-new-relic}

Suivez ces étapes pour accéder à votre sous-compte Nouvelle Relique Un associé à votre programme as a Cloud Service AEM.

1. Ouvrez une demande en accédant à l’onglet Assistance de l’Admin Console.
1. Dans votre requête, incluez les détails de votre ID de programme, ainsi que la liste des utilisateurs qui ont besoin d’accéder à Nouvelle Relique.
   * Les noms complets et adresses email valides de tous les utilisateurs doivent être fournis.

Reportez-vous au document [Portail d’assistance AEM pour les Experience Cloud](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour plus d’informations sur l’ouverture de tickets.

Une fois l’accès fourni, New Relic envoie un e-mail de confirmation à chaque utilisateur, afin que ce dernier puisse terminer le processus de configuration et se connecter.

Si l’utilisateur ne parvient pas à localiser l’e-mail de confirmation du compte d’origine, procédez comme suit.

1. Accédez à la page de connexion de Nouvelle Relique à l’adresse [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Sélectionnez **Mot de passe oublié?**.

   ![Nouvelle connexion Relative](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Saisissez l’adresse e-mail du compte, puis sélectionnez **Envoyer mon lien de réinitialisation**.

   ![Entrez l’adresse électronique](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. La nouvelle relique enverra à l’utilisateur un e-mail contenant un lien pour confirmer le compte.

Si vous avez terminé le processus d’inscription et que vous ne parvenez pas à vous connecter à votre compte en raison de messages d’erreur relatifs aux courriers électroniques ou aux mots de passe, enregistrez un ticket d’assistance via le [Admin Console](https://adminconsole.adobe.com/).

>[!TIP]
>
>Si vous ne recevez pas d’e-mail de New Relic :
>
>* Vérifiez vos [filtres anti-spam](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
>* Le cas échéant, [ajoutez New Relic à votre liste d’e-mails autorisés](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
>* Si aucune suggestion n’est d’une quelconque aide, veuillez fournir un commentaire sur le ticket d’assistance et l’équipe d’assistance Adobe vous aidera davantage.


### Vérification de votre email {#verify-email}

Si vous êtes invité à vérifier votre adresse électronique lors de la connexion, cela signifie que celle-ci est associée à plusieurs comptes. Vous pouvez ainsi choisir le compte auquel accéder.

Si vous ne vérifiez pas votre adresse e-mail, New Relic tentera de vous connecter avec l’enregistrement utilisateur le plus récemment créé associé à votre adresse e-mail. Pour éviter de vérifier votre email lors de chaque connexion, cliquez sur le bouton **Mémoriser** dans l’écran de connexion.

Pour obtenir de l’aide, veuillez ouvrir un ticket d’assistance via le [Portail d’assistance AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Exceptions {#exceptions}

AEM as a Cloud Service ne propose que la nouvelle solution Relic One APM et ne prend pas en charge les intégrations d’alertes, de journalisation ou d’API.

Pour obtenir de l’aide ou des conseils supplémentaires sur les nouvelles offres Relic One de votre programme as a Cloud Service AEM, veuillez ouvrir un ticket d’assistance via le [Portail d’assistance AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Questions fréquemment posées sur le compte New Relic {#faqs}

### Qu’est-ce qu’Adobe surveille avec la nouvelle relique ? {#adobe-monitor}

Adobe surveille les services as a Cloud Service de création, de publication et d’aperçu (le cas échéant) AEM par le biais du module externe Java de New Relic One. Adobe active la télémétrie et la surveillance personnalisées New Relic One APM dans les environnements as a Cloud Service de non-production et de production AEM.

Votre nouveau compte Relic One est associé à un Principal compte géré par l’Adobe et comporte plusieurs rapports d’applications : trois par environnement as a Cloud Service AEM.

* Une application pour le service de création par environnement
* Une application pour le service de publication par environnement (y compris la publication en or)
* Une application pour le service de prévisualisation par environnement

Remarque :

* Chaque application utilise une clé de licence.
* AEM les environnements as a Cloud Service ne signalent qu’un seul compte Nouvelle Relique Un .
* Les mesures et événements de surveillance complets pour la nouvelle version 1 sont conservés pendant 7 jours.

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
