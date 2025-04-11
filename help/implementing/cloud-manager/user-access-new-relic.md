---
title: New Relic One
description: Découvrez le service de surveillance des performances de l’application New Relic One (APM) pour AEM as a Cloud Service et comment y accéder.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 3323da83584c4511b15145c0106031df4597891c
workflow-type: tm+mt
source-wordcount: '1833'
ht-degree: 40%

---


# New Relic One {#user-access}

Découvrez le service de surveillance des performances de l’application New Relic One (APM) pour AEM as a Cloud Service et comment y accéder.

## À propos de l’établissement New Relic One {#introduction}

Adobe accorde une importance considérable à la surveillance, la disponibilité et les performances de votre application. AEM en tant que Cloud Service inclut l’accès à la surveillance New Relic One, offrant aux équipes une visibilité complète sur les mesures de performance du système et de l’environnement dans le cadre de l’offre de produits standard.

Ce document explique comment gérer l’accès aux fonctionnalités de surveillance des performances des applications (APM) de New Relic One dans AEM en tant qu’environnements Cloud Service. La gestion efficace de ces fonctionnalités assure des performances optimales et maximise les avantages de la AEM en tant que Cloud Service.

Lorsqu’un nouveau programme de production est créé, le sous-compte New Relic One associé à votre AEM en tant que programme Cloud Service est automatiquement créé. [Ce sous-compte doit être activé](#activate-sub-account) pour commencer l’ingestion des données.

## Fonctionnalités {#transaction-monitoring}

Les fonctionnalités de surveillance des performances (APM) de l’application New Relic One d’AEM as a Cloud Service sont nombreuses.

* Accès direct à un compte New Relic One dédié

* Un agent APM New Relic One instrumenté qui illustre les appels de méthode exacts avec les numéros de ligne, y compris les dépendances externes et les bases de données

* Optimisation holistique des performances combinant des mesures clés issues de la surveillance au niveau de l’infrastructure et de la surveillance de l’application (Adobe Experience Manager)

* AEM en tant que Cloud Service expose les MBeans JMX (Java Management Extensions) et les contrôles d’intégrité directement dans New Relic Insights, ce qui permet une inspection approfondie des performances des applications et des mesures d’intégrité.

## Activation de votre sous-compte New Relic One {#activate-sub-account}

Pour un programme nouvellement créé, un sous-compte New Relic One est créé pour vous. Cependant, vous devez l’activer pour qu’il puisse ingérer des données. Cette activation n’est pas automatique. Pour activer votre sous-compte, procédez comme suit.

>[!NOTE]
>
>Un utilisateur avec le rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** doit être connecté pour gérer le sous-compte New Relic One.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Dans la **[console Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)** , cliquez sur le programme pour lequel vous souhaitez gérer vos utilisateurs New Relic One.

1. Au bas de la **carte Environnements** sur la page d’aperçu du programme, cliquez sur ![l’icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Plus et sélectionnez **Activer New Relic**.

   ![Gérer les utilisateurs](assets/newrelic-activate-sub-account.png)

   * Vous pouvez également accéder à l’option **Gérer les utilisateurs**. En haut de l’écran **Environnements** de votre programme, cliquez sur ![l’icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Smock more.

1. [Exécutez un pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines) pour le même environnement jusqu’à la fin réussie de l’activation du sous-compte.

Lorsque le sous-compte est désactivé, il n’y a pas d’ingestion de données.

## Gérer les utilisateurs de New Relic One {#manage-users}

Suivez ces étapes pour définir les utilisateurs de votre sous-compte New Relic One relatifs à votre programme AEM as a Cloud Service.

>[!NOTE]
>
>Un utilisateur du rôle Propriétaire **de l’entreprise** ou **Gestionnaire de** déploiement doit être connecté pour gérer les utilisateurs de New Relic One.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez gérer vos utilisateurs New Relic One.

1. Au bas de la vignette **Environnements** sur la page de présentation du programme, cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) et sélectionnez **Gérer les utilisateurs**.

   ![Gérer les utilisateurs](assets/newrelic-manage-users.png)

   * Vous pouvez également accéder à l’option **Gérer les utilisateurs**. Dans la partie supérieure de l’écran **Environnements** de votre programme, cliquez sur ![Icône en forme d’icône en plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

1. Dans la boîte de dialogue **Gérer les utilisateurs New Relic**, saisissez le prénom et le nom de l’utilisateur que vous souhaitez ajouter, puis cliquez sur le bouton **Ajouter**. Répétez cette étape pour tous les utilisateurs que vous souhaitez ajouter.

   ![Ajouter des utilisateurs](assets/newrelic-add-users.png)

1. Pour supprimer un utilisateur New Relic One, cliquez sur le bouton de suppression à l’extrémité droite de la ligne représentant l’utilisateur.

1. Cliquez sur **Enregistrer** pour créer les utilisateurs.

Une fois les utilisateurs définis, New Relic envoie un e-mail de confirmation à chaque utilisateur auquel vous avez accordé l’accès afin que l’utilisateur puisse terminer le processus de configuration et se connecter.

>[!NOTE]
>
>Si vous gérez les utilisateurs de New Relic One, vous devez également vous ajouter en tant qu’utilisateur pour avoir accès vous-même. Être le **propriétaire de l’entreprise** ou le **responsable de déploiement** ne suffit pas pour avoir accès à New Relic One. Vous devez également créer vous-même en tant qu’utilisateur.

## Activez votre compte utilisateur New Relic One {#activate-user-account}

Une fois qu’un compte d’utilisateur New Relic One est créé, comme décrit dans la section d’aperçu [Gérer les utilisateurs New Relic One](#manage-users), New Relic envoie à ces utilisateurs un e-mail de confirmation à l’adresse fournie. Pour utiliser ces comptes, les utilisateurs doivent d’abord activer leurs comptes avec New Relic en réinitialisant leurs mots de passe.

**Pour activer votre compte utilisateur New Relic One :**

1. Cliquez sur le lien fourni dans l’e-mail de New Relic.

1. Sur la page de connexion New Relic, cliquez sur **Mot de passe oublié ?**

   ![Nom d’utilisateur New Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Saisissez l’adresse e-mail à laquelle vous avez reçu l’e-mail de confirmation, puis sélectionnez **Envoyer mon lien de réinitialisation**.

   ![Entrer l’adresse e-mail](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic vous envoie un e-mail contenant un lien pour confirmer le compte.

Si vous ne recevez pas d’e-mail de confirmation de New Relic, consultez la [section](#troubshooting) dépannage.

## Accéder à New Relic One {#accessing-new-relic}

Une fois que vous avez [activé votre compte New Relic](#activate-account), vous pouvez accéder à New Relic One par le biais de Cloud Manager ou directement.

**Pour accéder à New Relic One par le biais de Cloud Manager :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez accéder à New Relic One.

1. Au bas de la **carte Environnements** de la page d’aperçu du programme, cliquez sur ![l’icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Plus et sélectionnez **Ouvrir New Relic**.

   ![Gérer les utilisateurs](assets/newrelic-access.png)

   * Vous pouvez également accéder à New Relic. En haut de l’écran **Environnements** de votre programme, cliquez sur ![l’icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Smock more.

1. Dans le nouvel onglet du navigateur qui s’ouvre, connectez-vous à New Relic One.

**Pour accéder directement à New Relic One, procédez comme suit**

1. Accédez à la page de connexion de New Relic à l’adresse [`https://login.newrelic.com/login`](https://login.newrelic.com/login)

1. Connectez-vous à New Relic One.

### Vérifier votre adresse électronique {#verify-email}

Si vous êtes invité à vérifier votre adresse e-mail lors de la connexion à New Relic One, cela signifie que votre adresse e-mail est associée à plusieurs comptes. Vous pouvez choisir le compte auquel accéder.

Si vous ne vérifiez pas votre adresse e-mail, New Relic tente de vous connecter avec l’enregistrement utilisateur le plus récemment créé associé à votre adresse e-mail. Pour éviter de vérifier votre e-mail à chaque connexion, cochez la case **Mémoriser mon adresse** dans l’écran de connexion.

Pour obtenir de l’aide, ouvrez un ticket de support via le [Portail d’assistance AEM](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

## Résolution des problèmes liés à l’accès utilisateur de New Relic One {#troubleshooting}

Si vous avez été ajouté en tant qu’utilisateur New Relic One, comme décrit dans [Gérer les utilisateurs](#manage-users) de New Relic One, et que vous ne trouvez pas l’e-mail de confirmation de compte d’origine, vous pouvez suivre les étapes de dépannage suivantes.

**Pour résoudre les problèmes d’accès utilisateur à New Relic One :**

1. Accédez à la page de connexion de New Relic à l’adresse [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Cliquez sur **[!UICONTROL Mot de passe oublié ?]**.

   ![Nom d’utilisateur New Relic](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Saisissez l’adresse e-mail utilisée pour créer votre compte, puis sélectionnez **Envoyer mon lien de réinitialisation**.

   ![Saisir l’adresse e-mail](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic vous envoie un e-mail contenant un lien pour confirmer le compte.

Si vous avez terminé le processus d’inscription et que vous ne parvenez pas à vous connecter à votre compte en raison de messages d’erreur relatifs à votre e-mail ou à votre mot de passe, enregistrez un ticket d’assistance par le biais de [Admin Console](https://adminconsole.adobe.com/).

Si vous ne recevez pas d’e-mail de New Relic, procédez comme suit :

* Vérifiez vos [filtres anti-spam](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* Le cas échéant, [ajoutez New Relic à votre liste](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist) d’autorisation de courriels.
* Si aucune de ces suggestions n’aide, indiquez vos commentaires sur le ticket d’assistance.

## Restrictions {#limitations}

Les restrictions suivantes s’appliquent à l’ajout d’utilisateurs à New Relic One :

* 30 utilisateurs ou utilisatrices au maximum peuvent être ajouté(e)s. Si le nombre maximal d’utilisateurs et utilisatrices a été atteint, supprimez des utilisateurs et utilisatrices pour pouvoir en ajouter de nouveaux.
* Les utilisateurs ajoutés à New Relic sont de type **Basic**. Consultez la documentation New Relic pour plus de [détails](https://docs.newrelic.com/docs/accounts/accounts-billing/new-relic-one-user-management/user-type/).
* AEM as a Cloud Service ne propose que la solution New Relic One APM et ne prend pas en charge les intégrations d’alertes, de journalisation ou d’API.

>[!NOTE]
>
>Si aucune activité de connexion **utilisateur n’est** détectée dans votre sous-compte New Relic One pendant 30 jours ou plus, l’agent APM est arrêté et les données ne seront pas envoyées de AEM Cloud Service à New Relic.  **Les données ne seront plus envoyées tant que votre sous-compte n’aura pas été réactivé.**
>
>Suivez les mêmes étapes que celles de la section [ Activer votre sous-compte New Relic One ](#activate-sub-account) de ce document pour réactiver votre sous-compte New Relic One.

Pour obtenir de l’aide ou des conseils supplémentaires sur les offres New Relic One pour votre programme AEM as a Cloud Service, ouvrez un ticket de support au moyen du Portail d’assistance AEM [](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).

## Questions fréquentes {#faqs}

+++**Que surveille Adobe avec New Relic One ?**

Adobe contrôle les services de création, de publication et de prévisualisation (le cas échéant) d’AEM as a Cloud Service via le plug-in Java de New Relic One. Adobe active la télémétrie et la surveillance personnalisées de New Relic One APM dans les environnements de production et hors production d’AEM as a Cloud Service.

Votre compte New Relic One est attaché à un compte principal Adobe géré et comporte plusieurs applications qui lui sont rapportées ; trois par AEM en tant qu’environnement Cloud Service.

* Une application pour le service de création par environnement.
* Une application pour le `Publish` service par environnement (y compris Golden Publish)
* Une application pour le service de prévisualisation par environnement.

Remarque :

* Chaque application utilise une clé de licence.
* Les environnements AEM as a Cloud Service ne signalent qu’un seul compte New Relic One.
* Les mesures et événements de surveillance complète pour New Relic One sont conservés pendant trois mois.

+++

+++**Envoyez-Adobe de notifications d’alerte depuis New Relic One ?**

Adobe fournit un accès New Relic One à des fins d’observabilité uniquement et ne l’utilise pas pour les alertes client ou les alertes opérationnelles internes. Les notifications d’incidents sont envoyées à l’aide de [profils](/help/journey-onboarding/notification-profiles.md) de notification utilisateur.
+++

+++**Qui peut accéder aux données du service cloud New Relic One ?**

Un accès complet en lecture est accordé à un maximum de 30 membres de votre équipe. L’accès en lecture inclut toutes les mesures APM collectées par l’agent New Relic One.
+++

+++**La configuration SSO personnalisée est-elle prise en charge ?**

La configuration personnalisée de la fonction SSO n’est pas prise en charge pour le compte New Relic One fourni par Adobe.
+++

+++**Que faire si je dispose déjà d’un abonnement New Relic local ?**

New Relic One est la nouvelle plateforme d’observabilité de New Relic. Elle permet à l’assistance d’Adobe et à vos équipes d’observer, de surveiller et d’afficher les mesures et les événements, le tout à un seul endroit.

New Relic One offre aux utilisateurs la possibilité d’effectuer des recherches dans tous les comptes auxquels ils ont accès et de visualiser les données de tous les services et hôtes en une seule vue.

L’assistance Adobe surveille AEM as a Cloud Service avec New Relic One et d’autres outils, tandis que vos équipes peuvent toujours utiliser New Relic pour les services et infrastructures sur site. Elles pourront visualiser les données provenant à la fois du compte New Relic One d’Adobe et des comptes New Relic gérés par le client ou la cliente.

>[!NOTE]
>
>Pour afficher les deux jeux de données dans New Relic One, un utilisateur ou une utilisatrice doit disposer des autorisations appropriées et utiliser la même méthodologie de connexion pour les deux comptes (New Relic One d’Adobe et les comptes New Relic gérés par le client ou la cliente).

+++

+++**L&#39;agent APM pour mon compte New Relic One est arrêté. Que s’est-il passé?**

[Les agents APM sont arrêtés si aucune activité n’est détectée](#limitations) pendant 30 jours ou plus. Suivez les mêmes étapes dans la [section Activer votre sous-compte](#activate-sub-account) New Relic One de ce document pour réactiver votre sous-compte New Relic One.
+++
