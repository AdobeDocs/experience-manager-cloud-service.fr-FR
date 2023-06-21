---
title: Prise en charge IMS d’Adobe Experience Manager as a Cloud Service
description: Prise en charge IMS d’Adobe Experience Manager as a Cloud Service
exl-id: fb563dbd-a761-4d83-9da1-58f8e462b383
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '2035'
ht-degree: 78%

---

# Prise en charge IMS d’Adobe Experience Manager as a Cloud Service {#ims-support-for-aem-as-a-cloud-service}

## Présentation {#introduction}

* AEM as a Cloud Service inclut la prise en charge des instances AEM et de l’authentification basée sur Adobe IMS (Identity Management System) par Admin Console.
* Admin Console permet aux administrateurs de gérer de manière centralisée tous les utilisateurs d’Experience Cloud.
* Les utilisateurs et les groupes peuvent être affectés aux profils de produit associés à une instance AEM as a Cloud Service, ce qui leur permet de se connecter à cette instance.

>[!TIP]
>
>Consultez notre cours Experience League [Configuration de l’accès AEM pour les administrateurs](https://experienceleague.adobe.com/?recommended=ExperienceManager-A-1-2020.1.aem). Vous y trouverez une présentation de la manière dont les utilisateurs s’authentifient à l’aide d’Adobe IMS pour AEM as a Cloud Service et dont les utilisateurs, groupes d’utilisateurs et profils de produits d’Adobe sont utilisés pour contrôler l’accès à AEM et à ses fonctionnalités. Adobe ID requis.

>[!NOTE]
>
>AEM ne prend actuellement pas en charge l’affectation de groupes à des profils. Les utilisateurs doivent être ajoutés individuellement.

## Principales caractéristiques {#key-highlights}

AEM as a Cloud Service ne prend en charge l’authentification IMS que pour les utilisateurs Auteur, Admin et Dev. Il n’offre pas de prise en charge pour les utilisateurs finaux externes de sites clients, tels que les visiteurs du site.

* Admin Console représente les clients en tant qu’organisations IMS, et les instances d’auteur et de publication dans un environnement en tant qu’instances de contexte du produit. Cela permet aux administrateurs système et produit de gérer l’accès aux instances.
* Les profils de produit d’Admin Console déterminent les instances auxquelles un utilisateur peut accéder.
* Les clients peuvent utiliser leurs propres fournisseurs d’identité (IDP) compatibles avec SAML 2 pour l’authentification unique.
* Seuls les Enterprise ID ou Federated ID pour l’authentification unique du client sont pris en charge, pas d’ID d’Adobe personnel.

## Architecture {#architecture}

L’authentification IMS fonctionne à l’aide du protocole OAuth entre AEM et le point d’entrée Adobe IMS. Une fois qu’un utilisateur a été ajouté à IMS et possède une identité Adobe, il peut se connecter au service de création AEM à l’aide des informations d’identification IMS.

Le flux de connexion de l’utilisateur s’affiche ci-dessous, l’utilisateur est redirigé vers IMS et éventuellement vers le fournisseur d’identité du client pour SSO, puis redirigé vers AEM.

![Architecture d’IMS](/help/security/assets/ims1.png)

## Méthode de configuration {#how-to-set-up}

### Intégration des organisations dans Adobe Admin Console {#onboarding-orgs-to-adobe-admin-console}

L’intégration du client à Adobe Admin Console est un prérequis pour utiliser Adobe IMS pour l’authentification AEM.

Pour commencer, une organisation doit être configurée pour les clients dans Adobe IMS. Les clients Adobe Enterprise sont représentés en tant qu’organisations IMS dans [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html). Il s’agit du portail que les clients Adobe utilisent pour gérer les droits de leurs produits pour leurs utilisateurs et groupes.

AEM clients doivent déjà avoir une organisation configurée et, dans le cadre de la mise en service IMS, les instances de client sont mises à disposition dans Admin Console pour gérer les droits et accès des utilisateurs.

Dès qu’un client existe en tant qu’organisation IMS, il doit configurer son système comme suit :

![Intégration IMS](/help/security/assets/ims2.png)

1. L’administrateur système désigné reçoit une invitation à se connecter à Cloud Manager. Une fois connecté à Cloud Manager, l’administrateur système peut soit configurer les programmes et environnements AEM, soit accéder à Admin Console pour effectuer des tâches d’administration.
1. L’administrateur système demande à un domaine de confirmer la propriété du domaine concerné (acme.com, par exemple).
1. L’administrateur système configure les répertoires utilisateur.
1. L’administrateur système effectue la configuration IDP dans Admin Console pour configurer l’authentification unique.
1. L’administrateur AEM gère les groupes locaux, les autorisations et les droits comme d’habitude.

Pour plus d’informations sur les bases d’Adobe IMS, y compris sur la configuration des fournisseurs d’identité, consultez [cette page](https://helpx.adobe.com/fr/enterprise/using/set-up-identity.html).

Pour en savoir plus sur l’utilisation d’Enterprise Administration et d’Admin Console, consultez [cette page](https://helpx.adobe.com/fr/enterprise/managing/user-guide.html).

### Intégration d’utilisateurs dans Admin Console {#onboarding-users-in-admin-console}

Il existe trois méthodes d’intégration des utilisateurs en fonction de la taille du client et de ses préférences : création manuelle d’utilisateurs dans Admin Console, chargement d’un fichier CSV ou synchronisation des utilisateurs depuis l’annuaire Active Directory d’entreprise du client.

**Ajout manuel via l’interface utilisateur de l’Admin Console**

Les utilisateurs et les groupes peuvent être créés manuellement dans l’interface utilisateur d’Admin Console. Cette méthode peut être utilisée s’il y a un nombre réduit d’utilisateurs à gérer. Par exemple, il y a moins de 50 utilisateurs AEM ou vous utilisez déjà cette méthode pour administrer d’autres produits Adobe tels que les applications Analytics, Target ou Creative Cloud.

![Intégration des utilisateurs](/help/security/assets/ims3.png)

**Chargement de fichiers dans l’interface utilisateur d’Admin Console**

Pour gérer facilement la création d’utilisateurs, un fichier `.csv` peut être chargé afin de permettre l’ajout groupé des utilisateurs :

![Téléchargement du fichier](/help/security/assets/ims4.png)

**Outil de synchronisation des utilisateurs**

L’outil de synchronisation des utilisateurs (ou UST, User Sync Tool) permet aux clients d’entreprise de créer ou de gérer des utilisateurs Adobe utilisant Active Directory. Cela fonctionne également pour d’autres services d’annuaire OpenLDAP testés. Les utilisateurs cibles sont les administrateurs d’identité informatique (administrateurs d’annuaire d’entreprise ou système) qui peuvent installer et configurer l’outil. Cet outil Open Source est personnalisable, de telle sorte que les clients puissent le modifier en fonction de vos exigences spécifiques.

Lorsque la synchronisation des utilisateurs s’exécute, elle récupère une liste d’utilisateurs du Principal Directory de l’entreprise et la compare à la liste des utilisateurs dans le Admin Console.  Il appelle ensuite l’API de gestion des utilisateurs Adobe afin que le Admin Console soit synchronisé avec le répertoire de l’organisation. Le flux des modifications est entièrement unidirectionnel. Les modifications effectuées dans Admin Console ne sont pas transférées vers l’annuaire.

L’outil permet à l’administrateur système de mapper les groupes d’utilisateurs dans l’annuaire du client avec la configuration de produit et les groupes d’utilisateurs dans le Admin Console.

Pour configurer la synchronisation des utilisateurs, l’organisation doit créer un ensemble d’informations d’identification de la même manière qu’avec l’[API User Management](https://www.adobe.io/apis/experienceplatform/umapi-new.html).

![Outil de synchronisation des utilisateurs](/help/security/assets/ims5.png)

L’outil de synchronisation des utilisateurs est distribué via le référentiel Adobe GitHub [à cet emplacement](https://github.com/adobe-apiplatform/user-sync.py/releases/latest).

>[!NOTE]
>
>Une version préliminaire **2.4RC1** avec prise en charge de la création de groupe dynamique est disponible [ici](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1).

Cette version a pour principales fonctionnalités la possibilité de mapper de manière dynamique les nouveaux groupes LDAP pour l’appartenance des utilisateurs à Admin Console, ainsi que la création dynamique de groupes d’utilisateurs.

Vous trouverez plus d’informations sur les nouvelles fonctionnalités de groupe [à cet emplacement](https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/en/user-manual/advanced_configuration.md#additional-group-options).

**Documentation de synchronisation des utilisateurs**

Pour plus d’informations, consultez la [documentation de l’outil UST](https://adobe-apiplatform.github.io/user-sync.py/en/).

L’outil de synchronisation des utilisateurs doit s’enregistrer en tant que UMAPI client d’Adobe I/O en suivant la procédure décrite [ici](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html).

La documentation relative à la console Adobe I/O est disponible [ici](https://www.adobe.io/apis/cloudplatform/console.html).

Le fonctionnement de l’API User Management utilisée par l’outil de synchronisation des utilisateurs est abordé en détail [ici](https://www.adobe.io/apis/cloudplatform/umapi-new.html).

## Configuration d’Adobe Experience as a Cloud Service {#aem-configuration}

>[!NOTE]
>
>La configuration IMS AEM requise est automatiquement configurée lorsque les environnements et instances AEM sont configurés. Cependant, l’administrateur peut la modifier en fonction de ses besoins à l’aide de la méthode décrite [ici](/help/implementing/deploying/overview.md).

La configuration IMS AEM requise est automatiquement configurée lorsque les environnements et instances AEM sont configurés.  Les administrateurs du client peuvent modifier une partie de la configuration en fonction de leurs besoins.

L’approche globale consiste à configurer Adobe IMS en tant que fournisseur OAuth. Le **gestionnaire de synchronisation par défaut Apache Jackrabbit Oak** peut être modifié comme pour la synchronisation LDAP.

Vous trouverez ci-dessous les principales configurations OSGI qui doivent être modifiées pour modifier des propriétés telles que l’adhésion automatique des utilisateurs ou les mappages de groupes.

<!-- Arun to provide list of osgi configs -->

## Utilisation {#how-to-use}

### Gestion des produits et accès utilisateur dans Admin Console {#managing-products-and-user-access-in-admin-console}

Lorsque l’administrateur du produit se connecte à Admin Console, il voit plusieurs instances de contexte du produit AEM as a Cloud Service, comme illustré ci-dessous. Par exemple, sélectionnez l’un des produits de la page **Aperçu** :

![Connexion aux instances](/help/security/assets/ims6.png)

La liste des instances existantes s’affiche :

![Instances login2](/help/security/assets/ims7.png)

Sous chaque instance Product Context, il existe des instances couvrant les services Auteur ou Publication dans les environnements de production, d’évaluation ou de développement. Chaque instance est associée aux rôles Profils de produit ou Cloud Manager. Ces profils de produits servent à attribuer l’accès aux utilisateurs et aux groupes avec le privilège requis.

Le **AEM Administrateurs_xxx** Le profil est utilisé pour accorder des privilèges d’administrateur dans l’instance d’AEM associée pendant que la fonction **AEM Users_xxx** profile est utilisé pour ajouter des utilisateurs réguliers.

Tous les utilisateurs et groupes ajoutés sous ce profil de produit peuvent se connecter à cette instance particulière, comme illustré dans l’exemple ci-dessous :

![Profil du produit](/help/security/assets/ims8.png)

>[!WARNING]
>
>Le **Administrateurs AEM** le nom du profil de produit ne doit pas être modifié. Modification du nom de la variable **Administrateurs AEM** product profile supprime les droits d’administrateur de tous les utilisateurs affectés à ce profil.

### Connexion à Adobe Experience Manager as a Cloud Service {#logging-in-to-aem}

**Connexion de l’administrateur local**

AEM peut continuer à prendre en charge les connexions locales pour les utilisateurs administrateurs. L’écran de connexion dispose d’une option de connexion locale :

![Connexion locale](/help/security/assets/ims9.png)

<!-- the above image needs to be updated for skyline -->

**Connexion via IMS**

Pour les autres utilisateurs, la connexion via IMS peut être utilisée une fois qu’IMS est configuré sur l’instance. L’utilisateur doit d’abord cliquer sur le bouton Se connecter avec Adobe comme illustré ci-dessous :

![Connexion IMS](/help/security/assets/ims10.png)


>[!NOTE]
>
>Tout utilisateur peut être créé dans IMS à l’aide d’un Adobe ID ou d’un Federated ID. Si un utilisateur est configuré à l’aide d’un Federated ID, il est authentifié lors de la connexion à l’aide du fournisseur d’identité de son entreprise.

Il est alors redirigé vers l’écran de connexion IMS et il doit saisir ses informations d’identification :

![Connexion IMS 2](/help/security/assets/ims11.png)

![Connexion IMS 3](/help/security/assets/ims12.png)

Si un fournisseur d’identité fédéré est configuré lors de la configuration initiale du Admin Console, l’utilisateur est redirigé vers le fournisseur d’identité client pour SSO :

![Connexion IMS 4](/help/security/assets/ims13.png)

Une fois l’authentification terminée, l’utilisateur est redirigé vers AEM et connecté :

![Connexion IMS 5](/help/security/assets/ims14.png)

### Gestion des autorisations et des listes de contrôle d’accès dans Adobe Experience Manager as a Cloud Service {#managing-permissions-in-aem}

Les listes de contrôle d’accès et les autorisations continueront d’être gérées dans AEM. Les groupes d’utilisateurs synchronisés à partir d’IMS peuvent être affectés à des groupes locaux dans lesquels des listes de contrôle d’accès et des privilèges sont définis.

Dans l’exemple ci-dessous, nous ajoutons des groupes synchronisés au groupe local **Dam_Users** comme exemple.

L’utilisateur fait partie des groupes suivants dans IMS :

![ACL1](/help/security/assets/ims15.png)

Lorsque l’utilisateur se connecte, ses adhésions de groupes sont synchronisées, comme illustré ci-dessous :

![ACL2](/help/security/assets/ims16.png)

Dans AEM, les groupes d’utilisateurs synchronisés à partir d’IMS peuvent être ajoutés en tant que membres aux groupes locaux existants, tels que **DAM User**.

![ACL3](/help/security/assets/ims17.png)

Comme illustré ci-dessous, le groupe **AEM-GRP_008** hérite des autorisations et des privilèges du groupe **DAM Users**. C’est un moyen efficace de gérer les autorisations pour les groupes synchronisés. Il est généralement utilisé dans les méthodes d’authentification par LDAP.

![ACL3](/help/security/assets/ims18.png)


### Accès à Cloud Manager {#accessing-cloud-manager}

Pour pouvoir accéder à Cloud Manager ou à AEM as a Cloud Service, vous devez être affecté aux profils du produit Cloud Manager.

Reportez-vous à Définitions de rôle pour en savoir plus sur les rôles des utilisateurs qui régissent la disponibilité de fonctionnalités spécifiques dans Cloud Manager.

>[!NOTE]
>Cloud Manager dispose de rôles préconfigurés avec les autorisations appropriées. Pour en savoir plus sur les rôles dotés d’autorisations spécifiques, de tâches préconfigurées ou d’autorisations associées à chaque rôle, consultez [Autorisations basées sur les rôles](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/role-based-permissions.html?lang=fr).

**Procédure d’ajout d’un utilisateur**

1. Vous pouvez ajouter un utilisateur à un profil particulier, soit à partir d’un écran d’utilisateur existant, soit à partir d’un nouvel écran d’utilisateur.

1. Vous pouvez également ajouter un utilisateur à partir de l’écran **Aperçu**, comme illustré dans la figure ci-dessous.

   ![ACL3](/help/security/assets/ims23.png)

   >[!NOTE]
   >Vous pouvez affecter plusieurs profils à un utilisateur, comme le montre la figure ci-dessous.

   ![ACL3](/help/security/assets/ims22.png)


1. Une fois que vous avez été ajouté au profil approprié, vous devez pouvoir accéder aux clients respectifs dans Cloud Manager via [Adobe Experience Cloud](https://my.cloudmanager.adobe.com) en utilisant l’angle supérieur droit de l’interface utilisateur.


### Accès à une instance dans AEM as a Cloud Service {#accessing-instance-cloud-service}

>[!IMPORTANT]
>Les étapes mentionnées dans la section précédente doivent avoir déjà été effectuées pour pouvoir accéder à une instance d’AEM as a Cloud Service.

Pour avoir accès à une instance d’AEM au sein du **Admin Console**, le programme Cloud Manager et les environnements du programme doivent s’afficher dans la liste des produits sur la page **Admin Console**.

Par exemple, dans la capture d’écran ci-dessous, vous voyez deux environnements disponibles : *dev author* (création) et *publish* (publication).

![ACL3](/help/security/assets/ims19.png)

Pour accéder aux instances AEM, l’utilisateur doit être ajouté à un groupe du produit Cloud Service approprié.

Chaque instance de création possède un profil Administrateurs AEM et Utilisateurs AEM, et chaque instance de publication possède un profil Utilisateurs AEM. Si nécessaire, vous pouvez ajouter d’autres profils.

Pour obtenir un accès de niveau administrateur à l’instance AEM, ajoutez l’utilisateur au profil Administrateurs AEM pour ce produit particulier.
