---
title: Accès de l’utilisateur à la nouvelle version
description: Accès de l’utilisateur à la nouvelle version
source-git-commit: 82ec1283bfa8cc5ff48801521c291d438ff24122
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 1%

---


# Accès de l’utilisateur à la nouvelle version {#user-access}

## Présentation {#introduction}

Adobe met l’accent sur la surveillance, la disponibilité et les performances de votre application. Pour atteindre cet objectif, AEM as a Cloud Service permet d’accéder à une suite de surveillance Nouvelle relique personnalisée dans le cadre de l’offre de produits standard afin de garantir à vos équipes une visibilité maximale sur vos mesures de performances du système Cloud Service Adobe Experience Manager et de l’environnement. Cette section décrit les nouvelles fonctionnalités de surveillance des nouvelles relations activées sur vos environnements as a Cloud Service AEM afin de vous aider à améliorer les performances et à tirer le meilleur parti d’AEM as a Cloud Service.

## AEM Surveillance as a Cloud Service des transactions via une nouvelle relique - Proposition de valeur {#transaction-monitoring}

Voici le résumé de la proposition de valeur de la surveillance des performances des applications nouvelles pour AEM as a Cloud Service :

* Accès direct dans un compte Nouvelle Relique un dédié (accès géré par l’assistance Adobe).

* Nouvel agent APM Relic qui illustre les appels de méthode exacts avec des numéros de ligne, y compris les dépendances externes et les bases de données.

* Optimisation holistique des performances en combinant des mesures clés issues de la surveillance au niveau de l’infrastructure ainsi que de la surveillance des applications (Adobe Experience Manager).

* Exposition de AEM Mbeans JMX as a Cloud Service et contrôles de l’intégrité directement dans les mesures New Relic Insights, ce qui permet une inspection approfondie des performances de la pile d’applications et des mesures d’intégrité.

## Accès à votre compte as a Cloud Service New Relic AEM {#accessing-new-relic}

Votre compte Nouvelle Relique dédié sera configuré et géré par Adobe via l’engagement de l’assistance clientèle. Adobe restera le propriétaire et l’administrateur et fournira le compte en votre nom pour permettre l’accès à votre sous-compte dédié.

Pour accéder à votre nouveau sous-compte Relic associé à votre programme as a Cloud Service AEM :

* Ouvrez une demande en accédant à l’onglet Assistance du Admin Console.
* Assurez-vous que votre ticket comprend les détails de votre ID de programme, ainsi que la liste des utilisateurs auxquels vous demandez aux équipes d’Adobe d’ouvrir l’accès Nouvelle relique à .
* Tous les utilisateurs doivent disposer d’un nom complet et d’une adresse électronique valide.

   >[!NOTE]
   >Voir [Portail d’assistance AEM pour les Experience Cloud](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) pour plus d’informations.

Une fois l’accès fourni, New Relic envoie un courrier électronique de confirmation à chaque utilisateur afin que celui-ci puisse terminer le processus de configuration et se connecter.

Si l’utilisateur ne parvient pas à localiser l’e-mail de confirmation du compte d’origine :

1. Accédez à la page de connexion de Nouvelle Relique à l’adresse [login.newrelic.com/login](https://login.newrelic.com/login).

1. Sélectionner **Mot de passe oublié**.

   ![](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Saisissez l’adresse électronique du compte, puis sélectionnez **Envoyer mon lien de réinitialisation**.

   ![](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. Lorsque le système de Nouvelle relique renvoie un message électronique, sélectionnez le lien dans celui-ci pour confirmer à nouveau votre compte.

   >[!NOTE]
   >Si vous ne recevez pas d’e-mail de Nouvelle Relique :
   >Vérifiez vos [filtres anti-spam](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/). Le cas échéant, [ajouter une nouvelle relique à votre liste autorisée de messagerie](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
   >Veuillez nous faire part de vos commentaires sur le ticket d’assistance et nos équipes vous aideront à poursuivre

1. Si vous avez terminé le processus d’inscription et que vous ne parvenez pas à vous connecter à votre compte en raison de messages d’erreur relatifs aux courriers électroniques ou aux mots de passe, veuillez enregistrer un ticket d’assistance via [Admin Console](https://adminconsole.adobe.com/).

### Vérification de votre email {#verify-email}

Si vous êtes invité à vérifier votre adresse électronique au cours de la connexion, cela signifie que votre adresse électronique est associée à plusieurs comptes et qu’elle vous donnera la possibilité de vérifier votre adresse électronique lors de la connexion. Vous pourrez ainsi choisir le compte auquel accéder. Si vous ne vérifiez pas votre adresse électronique, la Nouvelle Relique tentera de vous connecter avec l’enregistrement d’utilisateur créé le plus récemment associé à votre adresse électronique. Pour éviter de vérifier votre adresse électronique à chaque connexion, cochez la case Mémoriser dans l’écran de connexion.

Pour obtenir de l’aide, veuillez ouvrir un ticket d’assistance via [Portail d’assistance AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Exceptions {#exceptions}

AEM as a Cloud Service concentre uniquement l’offre sur la nouvelle solution APM Relic et ne fournit pas de prise en charge des fonctionnalités d’alerte, de journalisation ou d’intégration d’API.

Pour obtenir de l’aide ou des conseils supplémentaires sur les nouvelles offres Relic pour votre programme as a Cloud Service AEM, veuillez ouvrir un ticket d’assistance via [Portail d’assistance AEM](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) pour obtenir de l’aide.

## Questions fréquentes sur un nouveau compte de redirection {#faqs}

### Qu’est-ce qu’Adobe surveille avec Nouvelle Relique ? {#adobe-monitor}

Adobe surveille les services as a Cloud Service Auteur, Publier et Aperçu (le cas échéant) AEM par l’intermédiaire du plug-in Java New Relic APM. Adobe active la nouvelle télémétrie APM de redirection personnalisée et la surveillance dans les environnements as a Cloud Service de non-production et de production AEM. Votre compte Nouvelle relique est associé à un compte Principal géré par Adobe et comporte plusieurs rapports d’applications.

Trois par environnement as a Cloud Service AEM :

* Une application pour le service Auteur par environnement
* Une application pour le service de publication par environnement (y compris la publication en or)
* Une application pour le service Preview par environnement
   >[!IMPORTANT]
   >Chaque application utilise une clé de licence. AEM environnements as a Cloud Service ne signaleront qu’un seul compte Nouvelle relique. Les mesures et événements de surveillance complets pour la nouvelle API relative et l’infrastructure sont conservés pendant 7 jours.

### Qui peut accéder aux données du nouveau Cloud Service Relic ? {#access-new-relic-cloud}

L’accès en lecture complète sera accordé à 10 membres au maximum de votre équipe. L’accès en lecture comprend toutes les mesures APM collectées par le nouvel agent Relic.

### La configuration SSO personnalisée est-elle prise en charge ? {#custom-sso}

La configuration d’authentification unique personnalisée n’est actuellement pas prise en charge pour le compte Nouvelle relique configuré par Adobe.

### Que se passe-t-il si vous disposez déjà d’un nouvel abonnement Relic sur site ? {#new-relic-subscription}

La nouvelle plateforme d’observabilité de Nouvelle Relique, appelée Nouvelle Relique Un, permet aux groupes d’assistance Adobe et à vos équipes d’observer, de surveiller et d’afficher les mesures et les événements, le tout à un seul endroit. La nouvelle relique 1 permet aux utilisateurs de rechercher dans tous les comptes sur lesquels ils ont accès et de visualiser les données de tous les services et hôtes dans une seule vue. Bien que les équipes d’assistance à l’Adobe surveillent l’application as a Cloud Service d’AEM à l’aide de New Relic et d’autres outils internes dans le cadre de votre service, vos équipes peuvent continuer à tirer parti de New Relic pour les services hébergés sur site et l’infrastructure. Ils pourront visualiser les données des nouveaux comptes Relic gérés par les Adobes et les clients.

>[!NOTE]
>L’utilisateur doit disposer des autorisations appropriées et utiliser la même méthodologie de connexion pour les deux comptes (compte Nouvelle Relique géré par le client et Adobe).


