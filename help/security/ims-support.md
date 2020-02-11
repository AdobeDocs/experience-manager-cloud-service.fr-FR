---
title: Prise en charge IMS d’Adobe Experience Manager en tant que service Cloud
description: 'Prise en charge IMS d’Adobe Experience Manager en tant que service Cloud '
translation-type: tm+mt
source-git-commit: bef17376f0b7de79511f9ad6ceb00e9f084f45d2

---


# Prise en charge IMS d’Adobe Experience Manager en tant que service Cloud {#ims-support-for-aem-as-a-cloud-service}

## Présentation {#introduction}

* AEM as a Cloud Service inclut la prise en charge de la console d’administration pour les instances AEM et l’authentification basée sur Adobe Identity Management System (IMS pour abréviation).
* La console d’administration permet aux administrateurs de gérer de manière centralisée tous les utilisateurs d’Experience Cloud.
* Les utilisateurs et les groupes peuvent être affectés aux profils de produits associés à AEM en tant qu’instances de service Cloud, ce qui leur permet de se connecter à cette instance.

## Principales caractéristiques {#key-highlights}

AEM as a Cloud Service offre la prise en charge de l’authentification IMS uniquement pour les utilisateurs Auteur, Admin et Dev. Il ne prend pas en charge les utilisateurs finaux externes des sites clients tels que les visiteurs du site.

* La console d’administration représente les clients en tant qu’organisations IMS, instances d’auteur et de publication dans un environnement en tant qu’instances de contexte de produit. Les administrateurs système et produit pourront ainsi gérer l’accès aux instances.
* Les profils de produit dans la Console d’administration déterminent les instances auxquelles un utilisateur peut accéder.
* Les clients pourront utiliser leurs propres fournisseurs d’identité (IDP) conformes SAML 2 pour la connexion unique.
* Seuls les ID d’entreprise ou fédérés pour la connexion unique du client sont pris en charge, aucun ID Adobe personnel.

## Architecture {#architecture}

L’authentification IMS fonctionne à l’aide du protocole OAuth entre AEM et le point de fin IMS Adobe. Une fois qu’un utilisateur a été ajouté à IMS et qu’il possède une identité Adobe, il peut se connecter au service de création AEM à l’aide des informations d’identification IMS.

Le flux d’identifiant de connexion utilisateur est indiqué ci-dessous, l’utilisateur sera redirigé vers IMS et éventuellement vers le fournisseur d’identité client pour la SSO, puis redirigé vers AEM.

![Architecture IMS](/help/security/assets/ims1.png)

## Méthode de configuration {#how-to-set-up}

### Onboarding Organizations to Adobe Admin Console {#onboarding-orgs-to-adobe-admin-console}

L’intégration du client à Adobe Admin Console est une condition préalable à l’utilisation d’Adobe IMS pour l’authentification AEM.

Dans un premier temps, les clients doivent disposer d’une organisation configurée dans Adobe IMS. Les clients Adobe Enterprise sont représentés sous forme d’organisations IMS dans la Console [d’administration](https://helpx.adobe.com/enterprise/using/admin-console.html) Adobe. Il s’agit du portail utilisé par les clients Adobe pour gérer les droits des produits pour leurs utilisateurs et groupes.

Les clients AEM doivent déjà disposer d’une organisation configurée et, dans le cadre de l’approvisionnement IMS, les instances de client seront rendues disponibles dans la Console d’administration pour la gestion des droits d’accès et des droits d’utilisateur.

Une fois qu’un client existe en tant qu’organisation IMS, il devra configurer son système comme suit :

![Intégration IMS](/help/security/assets/ims2.png)

1. L’administrateur système désigné reçoit une invitation à se connecter à Cloud Manager. Une fois connecté à Cloud Manager, les administrateurs système peuvent choisir de configurer les programmes et environnements AEM ou accéder à la console d’administration pour les tâches d’administration.
1. L’administrateur système demande à un domaine de confirmer la propriété du domaine concerné (par exemple acme.com).
1. L’administrateur système configure les annuaires utilisateur
1. L’administrateur système effectue la configuration IDP dans la Console d’administration afin de configurer l’authentification unique.
1. L’administrateur AEM gère les groupes locaux, les autorisations et les privilèges comme d’habitude.

Les bases de la gestion des identités Adobe, y compris la configuration des IDP, sont abordées [ici](https://helpx.adobe.com/enterprise/using/set-up-identity.html).

L’utilisation de la Console d’administration et d’administration d’entreprise est traitée [ici](https://helpx.adobe.com/enterprise/managing/user-guide.html).

### Onboarding Users in Admin Console {#onboarding-users-in-admin-console}

Il existe trois méthodes pour embarquer les utilisateurs en fonction de la taille du client et de leurs préférences : créez manuellement des utilisateurs dans la Console d’administration, téléchargez un fichier .csv ou synchronisez des utilisateurs à partir de l’entreprise Active Directory du client.

**Ajout manuel via l’interface utilisateur de l’Admin Console**

Les utilisateurs et les groupes peuvent être créés manuellement dans l’interface utilisateur de l’Admin Console. Cette méthode peut être utilisée si vous n’avez pas un grand nombre d’utilisateurs à gérer. Par exemple, moins de 50 utilisateurs d’AEM ou si vous utilisez déjà cette méthode pour administrer d’autres produits Adobe tels que les applications Analytics, Target ou Creative Cloud.

![Intégration des utilisateurs](/help/security/assets/ims3.png)

**Téléchargement de fichier dans l’interface utilisateur de la Console d’administration**

For easy handling of user creation, a `.csv` file can be uploaded for adding users in bulk.

![Téléchargement du fichier](/help/security/assets/ims4.png)

**Outil de synchronisation des utilisateurs**

L&#39;outil de synchronisation des utilisateurs (UST en bref) permet à nos clients d&#39;entreprise de créer et de gérer des utilisateurs Adobe utilisant Active Directory. Cela fonctionne également pour d’autres services d’annuaire OpenLDAP testés. Les utilisateurs cibles sont les administrateurs d’identité informatique (Enterprise Directory ou System Admins) qui pourront installer et configurer l’outil. L&#39;outil open source est personnalisable de sorte que les clients que vous modifiez le soient en fonction de vos besoins.

Lorsque User Sync s’exécute, il récupère une liste d’utilisateurs à partir d’Active Directory de l’entreprise et la compare à la liste des utilisateurs dans la Console d’administration.  Elle appelle ensuite l’API de gestion des utilisateurs Adobe pour synchroniser l’Admin Console avec le répertoire de l’organisation. Le flux de changement est entièrement une façon. Les modifications effectuées dans la console d’administration ne sont pas répercutées dans le répertoire.

L’outil permet à l’administrateur système de mapper les groupes d’utilisateurs du répertoire du client avec la configuration du produit et les groupes d’utilisateurs dans la console d’administration.

To set up User Sync, the organization needs to create a set of credentials in the same way they would use the [User Management API](https://www.adobe.io/apis/experienceplatform/umapi-new.html).

![Outil de synchronisation des utilisateurs](/help/security/assets/ims5.png)

User Sync Tool is distributed through the Adobe Github repository [at this location](https://github.com/adobe-apiplatform/user-sync.py/releases/latest).

>[!NOTE]
>
> Une version bêta **2.4RC1** est disponible avec la prise en charge de la création de groupe dynamique et peut être trouvée [ici](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1).

Cette version a pour principales fonctionnalités la possibilité de mapper de manière dynamique les nouveaux groupes LDAP pour l’appartenance des utilisateurs à l’Admin Console, ainsi que la création dynamique de groupes d’utilisateurs.

Vous trouverez plus d’informations sur les nouvelles fonctionnalités du groupe [à cet emplacement](https://github.com/adobe-apiplatform/user-sync.py/blob/v2/docs/en/user-manual/advanced_configuration.md#additional-group-options).

**Documentation de synchronisation des utilisateurs**

Consultez la documentation [](https://adobe-apiplatform.github.io/user-sync.py/en/) UST pour plus de détails.

The User Sync Tool needs to register as an Adobe I/O client UMAPI using the procedure [here](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html).

Adobe I/O Console Documentation can be found [here](https://www.adobe.io/apis/cloudplatform/console.html).

The User Management API that is used by the User Sync Tool is covered [here](https://www.adobe.io/apis/cloudplatform/umapi-new.html).

## Adobe Experience as a Cloud Service Configuration {#aem-configuration}

> [!NOTE]
>
>La configuration IMS AEM requise sera automatiquement configurée lorsque les environnements et instances AEM seront configurés. Toutefois, l’administrateur peut le modifier selon ses besoins en utilisant la méthode décrite [ici](/help/implementing/deploying/overview.md).

La configuration IMS AEM requise sera automatiquement configurée lorsque les environnements et instances AEM seront configurés.  Les administrateurs clients peuvent modifier une partie de la configuration en fonction de leurs besoins

L’approche globale consiste à configurer Adobe IMS en tant que fournisseur OAuth. Le gestionnaire **de synchronisation par défaut** Apache Jackrabbit Oak peut être modifié comme pour la synchronisation LDAP.

Vous trouverez ci-dessous les principales configurations OSGI qui doivent être modifiées afin de modifier les propriétés telles que l’adhésion automatique des utilisateurs ou les mappages de groupes.

<!-- Arun to provide list of osgi configs -->

## Procédure d’utilisation {#how-to-use}

### Gestion des produits et accès utilisateur dans l’Admin Console {#managing-products-and-user-access-in-admin-console}

Lorsque l’administrateur du produit se connecte à Admin Console, plusieurs instances du contexte de produit des services gérés AEM s’affichent, comme illustré ci-dessous :

![Connexion aux instances](/help/security/assets/ims6.png)

In this example, the org **AEM-MS-Onboard** has 32 instances spanning different topologies and environments like Stage or Prod.

![Instances login2](/help/security/assets/ims7.png)

Sous chaque instance Product Context, des profils de produit sont associés. Ces profils de produit sont utilisés pour affecter l’accès aux utilisateurs et aux groupes avec le privilège requis.

Le profil **Administrator_xxx** sera utilisé pour accorder des privilèges d’administrateur à l’instance AEM associée, tandis que le profil **User_xxx** sera utilisé pour ajouter des utilisateurs réguliers.

Les utilisateurs et les groupes ajoutés sous ce profil de produit pourront se connecter à cette instance particulière, comme illustré dans l’exemple ci-dessous :

![Profil du produit](/help/security/assets/ims8.png)

### Connexion à Adobe Experience Manager en tant que service Cloud (#login-in-to-aem)

**Connexion administrateur locale**

AEM peut continuer à prendre en charge les connexions locales pour les utilisateurs administrateurs. L’écran de connexion permet de se connecter localement :

![Connexion locale](/help/security/assets/ims9.png)

<!-- the above image needs to be updated for skyline -->

**Connexion via IMS**

Pour les autres utilisateurs, la connexion via IMS peut être utilisée une fois qu’IMS est configuré sur l’instance. L’utilisateur doit d’abord cliquer sur le bouton Se connecter avec Adobe comme illustré ci-dessous :

![Connexion IMS](/help/security/assets/ims10.png)

Ils seront ensuite redirigés vers l’écran de connexion IMS et devront saisir leurs informations d’identification :

![Connexion IMS2](/help/security/assets/ims11.png)

![Connexion IMS3](/help/security/assets/ims12.png)

Si un fournisseur d’identité fédéré est configuré lors de la configuration initiale de l’Admin Console, l’utilisateur est redirigé vers le fournisseur d’identité client pour SSO:

![Connexion IMS4](/help/security/assets/ims13.png)

Une fois l’authentification terminée, l’utilisateur est redirigé vers AEM et connecté :

![Connexion IMS5](/help/security/assets/ims14.png)

### Gestion des autorisations et des listes de contrôle d’accès dans Adobe Experience Manager en tant que service Cloud {#managing-permissions-in-aem}

Les listes de contrôle d’accès et les autorisations continueront d’être gérées dans AEM. Les groupes d’utilisateurs synchronisés à partir d’IMS peuvent être affectés à des groupes locaux où des ACL et des privilèges sont définis.

In the example below, we are adding synced groups to the local **Dam_Users** group as an example.

L’utilisateur fait partie des groupes suivants dans IMS :

![ACL1](/help/security/assets/ims15.png)

Lorsque l’utilisateur se connecte, ses adhésions de groupes sont synchronisées, comme illustré ci-dessous :

![ACL2](/help/security/assets/ims16.png)

In AEM, the User Groups synced from IMS can be added as members to existing local groups, like **DAM Users**.

![ACL3](/help/security/assets/ims17.png)

Comme illustré ci-dessous, le groupe **AEM-GRP_008** hérite des autorisations et des privilèges des utilisateurs **de** DAM. Il s’agit d’un moyen efficace de gérer les autorisations pour les groupes synchronisés et il est couramment utilisé dans la méthode d’authentification LDAP.

![ACL3](/help/security/assets/ims18.png)