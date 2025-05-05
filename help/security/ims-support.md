---
title: Prise en charge IMS d’Adobe Experience Manager as a Cloud Service
description: Prise en charge du système de gestion des images pour Adobe Experience Manager as a Cloud Service.
exl-id: fb563dbd-a761-4d83-9da1-58f8e462b383
feature: Security
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: ht
source-wordcount: '1941'
ht-degree: 100%

---

# Prise en charge IMS d’Adobe Experience Manager as a Cloud Service {#ims-support-for-aem-as-a-cloud-service}

## Introduction {#introduction}

* AEM as a Cloud Service inclut la prise en charge des instances AEM et de l’authentification basée sur Adobe IMS (Identity Management System) par Admin Console.
* Admin Console permet aux administrateurs de gérer de manière centralisée tous les utilisateurs d’Experience Cloud.
* Les utilisateurs, les utilisatrices et les groupes peuvent être affectés aux profils de produit associés à une instance AEM as a Cloud Service, ce qui leur permet de se connecter à cette instance.

>[!TIP]
>
>Voir [Configuration de l’accès à AEM pour les administrateurs et administratrices](https://experienceleague.adobe.com/?lang=fr&recommended=ExperienceManager-A-1-2020.1.aem) pour découvrir comment les utilisateurs et utilisatrices s’authentifient à l’aide d’Adobe IMS pour AEM as a Cloud Service. Découvrez également comment les utilisateurs, utilisatrices, groupes d’utilisateurs et d’utilisatrices et profils de produits Adobe IMS sont utilisés pour contrôler l’accès à AEM et à ses fonctionnalités. Adobe ID requis.

## Principales caractéristiques {#key-highlights}

AEM as a Cloud Service ne prend en charge l’authentification IMS que pour les utilisateurs et utilisatrices ayant les droits de création, d’administration et de développement. Il n’offre pas de prise en charge pour les personnes utilisatrices finales externes de sites clients, telles que les visiteurs et les visiteuses du site.

* Admin Console représente les clients et clientes en tant qu’organisations IMS, et les instances de création et de publication dans un environnement en tant qu’instances de contexte du produit. Cette représentation permet aux administrateurs et administratrices système et produit de gérer l’accès aux instances.
* Les profils de produit d’Admin Console déterminent les instances auxquelles un utilisateur ou une utilisatrice peut accéder.
* Les clients et clientes peuvent utiliser leurs propres fournisseurs d’identité (IDP) compatibles avec SAML 2 pour une authentification unique.
* Seuls les ID Enterprise ou Federated pour l’authentification unique du client ou de la cliente sont pris en charge, contrairement aux Adobe ID.

## Architecture {#architecture}

L’authentification IMS fonctionne à l’aide du protocole OAuth entre AEM et le point d’entrée Adobe IMS. Une fois qu’un utilisateur a été ajouté à IMS et possède une identité Adobe, il peut se connecter au service de création AEM à l’aide des informations d’identification IMS.

Le flux d’identifiant de connexion utilisateur est indiqué ci-dessous. La personne utilisatrice sera redirigée vers IMS et éventuellement vers le fournisseur d’identité client pour la SSO, puis redirigée vers AEM.

![Architecture IMS](/help/security/assets/ims1.png)

## Méthode de configuration {#how-to-set-up}

### Intégration des organisations dans Adobe Admin Console {#onboarding-orgs-to-adobe-admin-console}

L’intégration du client à l’Adobe Admin Console est un prérequis pour utiliser Adobe IMS pour l’authentification AEM.

Pour commencer, les clientes et clients doivent avoir une organisation configurée dans Adobe IMS. Les clients et clientes Adobe Enterprise sont représentés en tant qu’organisations IMS dans [Adobe Admin Console](https://helpx.adobe.com/fr/enterprise/using/admin-console.html). Cette zone est le portail utilisé par les clients et clientes Adobe pour gérer les droits de leurs produits pour leurs utilisateurs, utilisatrices et groupes.

Une organisation doit déjà être configurée pour les clientes et clients AEM. De plus, dans le cadre de l’approvisionnement IMS, les instances des clientes et clients seront mise à disposition dans Admin Console pour gérer les droits et accès des utilisateurs et utilisatrices.

Dès qu’un client ou une cliente existe en tant qu’organisation IMS, il ou elle doit configurer son système comme suit :

![Intégration IMS](/help/security/assets/ims2.png)

1. La personne chargée de l’administration système désignée reçoit une invitation à se connecter à Cloud Manager. Une fois connectée à Cloud Manager, la personne chargée de l’administration système peut soit configurer les programmes et environnements AEM, soit accéder à Admin Console pour effectuer des tâches d’administration.
1. L’administrateur ou l’administratrice système demande à un domaine de confirmer la propriété du domaine concerné (acme.com, par exemple).
1. L’administrateur ou l’administratrice système configure les répertoires d’utilisateur ou d’utilisatrice.
1. L’administrateur ou l’administratrice système effectue la configuration IDP dans Admin Console afin de configurer l’authentification unique.
1. L’administration AEM gère les groupes locaux, les autorisations et les droits comme d’habitude.

Les principes de base d’Adobe Identity Management, y compris la configuration des fournisseurs d’identité, sont abordés dans la section [Configurer l’identité et l’authentification unique](https://helpx.adobe.com/fr/enterprise/using/set-up-identity.html).

L’utilisation d’Enterprise Administration et d’Admin Console est abordée dans le [guide d’administration Bienvenue dans l’entreprise et les équipes](https://helpx.adobe.com/fr/enterprise/admin-guide.html).

### Intégrer des utilisateurs et des utilisatrices dans l’Admin Console {#onboarding-users-in-admin-console}

Il existe trois façons d’intégrer des utilisateurs et utilisatrices. Chaque méthode dépend de la taille du client ou de la cliente et de ses préférences. Vous pouvez créer manuellement des utilisateurs et utilisatrices dans Admin Console, charger un fichier .csv ou synchroniser des utilisateurs et utilisatrices à partir de l’annuaire Active Directory d’entreprise du client ou de la cliente.

**Ajout manuel via l’interface utilisateur de l’Admin Console**

Les utilisateurs et les groupes peuvent être créés manuellement dans l’interface utilisateur d’Admin Console. Cette méthode peut être utilisée s’il y a un nombre réduit d’utilisateurs et d’utilisatrices à gérer. Par exemple, il y a moins de 50 utilisateurs ou utilisatrices AEM ou vous utilisez déjà cette méthode pour administrer d’autres produits Adobe tels que les applications Analytics, Target ou Creative Cloud.

![Intégration des utilisateurs](/help/security/assets/ims3.png)

**Chargement de fichiers dans l’interface utilisateur d’Admin Console**

Pour gérer facilement la création d’utilisateurs, un fichier `.csv` peut être chargé afin de permettre l’ajout groupé des utilisateurs :

![Téléchargement du fichier](/help/security/assets/ims4.png)

**Outil de synchronisation des utilisateurs**

L’outil de synchronisation des utilisateurs et utilisatrices (ou UST, User Sync Tool) permet aux clients et aux clientes d’entreprise de créer ou de gérer des utilisateurs et utilisatrices Adobe utilisant Active Directory. Cet outil fonctionne également pour d’autres services d’annuaire OpenLDAP testés. Les utilisateurs et utilisatrices cibles sont les administrateurs et administratrices d’identité informatique (administrateurs et administratrices d’annuaire d’entreprise ou système) qui pourront installer et configurer l’outil. Cet outil open source est personnalisable, de telle sorte que les clients et clientes puissent le modifier en fonction de leurs exigences spécifiques.

Lorsque la synchronisation des utilisateurs et utilisatrices s’exécute, elle récupère une liste d’utilisateurs et d’utilisatrices à partir de l’annuaire Active Directory de l’organisation et la compare à celle dans Admin Console. Elle appelle ensuite l’API Adobe User Management pour synchroniser Admin Console avec l’annuaire de l’organisation. Le flux des modifications est entièrement unidirectionnel. Les modifications effectuées dans Admin Console ne sont pas transférées vers l’annuaire.

Cet outil permet à l’administration système de mapper les groupes d’utilisateurs et d’utilisatrices dans l’annuaire du client ou de la cliente avec la configuration de produits et les groupes d’utilisateurs et d&#39;utilisatrices dans Admin Console.

Pour configurer la synchronisation des utilisateurs et utilisatrices, l’organisation doit créer un ensemble d’informations d’identification de la même manière qu’avec l’[API User Management](https://developer.adobe.com/umapi/).

![Outil de synchronisation des utilisateurs et des utilisatrices](/help/security/assets/ims5.png)

L’outil de synchronisation des utilisateurs et utilisatrices est distribué via le référentiel Adobe GitHub [à cet emplacement](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.9.0rc2).

>[!NOTE]
>
>Une version préliminaire **2.4RC1** avec prise en charge de la création de groupe dynamique est disponible sous [User Sync Tool v2.4rc1 sur GitHub](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1).

Cette version a pour principales fonctionnalités la possibilité de mapper de manière dynamique les nouveaux groupes LDAP pour l’abonnement des utilisateurs et utilisatrices à Admin Console, ainsi que la création dynamique de groupes d’utilisateurs et utilisatrices.

Vous trouverez davantage d’informations sur les nouvelles fonctionnalités de groupe dans [User Sync Tool d’Adobe - Options de groupe supplémentaires](https://adobe-apiplatform.github.io/user-sync.py/en/user-manual/advanced_configuration.html#additional-group-options).

**Documentation de synchronisation des utilisateurs et utilisatrices**

Voir :

* [Documentation UST](https://adobe-apiplatform.github.io/user-sync.py/fr/)

* User Sync Tool doit s’enregistrer en tant qu’UMAPI client d’Adobe Developer en suivant la procédure d’[authentification pour l’accès à l’API](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html).

* [Documentation Adobe Developer Console](https://developer.adobe.com/developer-console/)

* [API User Management utilisée par User Sync Tool](https://adobe-apiplatform.github.io/user-sync.py/fr/)

## Configuration d’Adobe Experience as a Cloud Service {#aem-configuration}

>[!NOTE]
>
>La configuration IMS requise pour AEM est automatiquement définie lorsque les environnements et instances AEM sont fournis. Cependant, l’équipe d’administration peut effectuer des modifications selon ses besoins, voir la section [Déployer sur AEM as a Cloud Service](/help/implementing/deploying/overview.md).

La configuration IMS requise pour AEM est automatiquement définie lorsque les environnements et instances AEM sont fournis. Les administrateurs du client peuvent modifier une partie de la configuration en fonction de leurs besoins.

L’approche globale consiste à configurer Adobe IMS en tant que fournisseur OAuth. Le **gestionnaire de synchronisation par défaut Apache Jackrabbit Oak** peut être modifié comme pour la synchronisation LDAP.

Vous trouverez ci-dessous les principales configurations OSGI qui doivent être modifiées afin de changer des propriétés telles que l’abonnement automatique des utilisateurs et utilisatrices ou les mappages de groupes.

<!-- Arun to provide list of osgi configs -->

## Utilisation {#how-to-use}

### Gestion des produits et accès utilisateur dans Admin Console {#managing-products-and-user-access-in-admin-console}

Lorsque l’administrateur ou l’administratrice du produit se connecte à Admin Console, il ou elle voit plusieurs instances de contexte du produit AEM as a Cloud Service, comme illustré ci-dessous. Par exemple, sélectionnez l’un des produits de la page **Vue d’ensemble** :

![Connexion aux instances](/help/security/assets/ims6.png)

La liste des instances existantes s’affiche :

![Connexion aux instances 2](/help/security/assets/ims7.png)

Sous chaque instance de contexte de produit, il y a des instances couvrant les services de création ou de publication dans les environnements de production, d’évaluation ou de développement. Chaque instance est associée aux rôles Profils de produit ou Cloud Manager. Ces profils de produits servent à attribuer l’accès aux utilisateurs et utilisatrices et aux groupes avec le privilège requis.

Le profil **Administrateurs/administratrices_xxx AEM** est utilisé pour accorder des privilèges d’administration à l’instance AEM associée, tandis que le profil **Utilisateurs/utilisatrices_xxx AEM** est utilisé pour ajouter des utilisatrices et utilisateurs réguliers.

Tous les utilisateurs et utilisatrices, et les groupes ajoutés au profil de ce produit pourront se connecter à cette instance, comme illustré dans l’exemple suivant :

![Profil du produit](/help/security/assets/ims8.png)

>[!WARNING]
>
>Ne modifiez pas le nom du profil de produit **Administrateurs/administratrices AEM**. La modification du nom du profil de produit **Administrateurs/administratrices AEM** supprime les droits d’administration de toutes les personnes affectées à ce profil.

### Connexion à Adobe Experience Manager as a Cloud Service {#logging-in-to-aem}

**Connexion de l’administration locale**

AEM peut continuer à prendre en charge les connexions locales pour les administrateurs et administratrices. L’écran de connexion vous permet de vous connecter localement :

![Connexion locale](/help/security/assets/ims9.png)

<!-- the above image must be updated for skyline -->

**Connexion via IMS**

Pour les autres utilisateurs et utilisatrices, la connexion IMS est utilisée une fois qu’IMS est configuré sur l’instance. L’utilisateur ou l’utilisatrice clique sur le bouton Se connecter avec Adobe comme illustré ci-dessous :

![Connexion IMS](/help/security/assets/ims10.png)


>[!NOTE]
>
>Tout utilisateur peut être créé dans IMS à l’aide d’un Adobe ID ou d’un Federated ID. Si la configuration d’un utilisateur ou d’une utilisatrice est effectuée à l’aide d’un Federated ID, leur authentification est effectuée à l’aide du fournisseur d’identité de son entreprise lors de la connexion.

La personne utilisatrice est redirigée vers l’écran de connexion IMS et doit saisir ses informations d’identification :

![Connexion IMS 2](/help/security/assets/ims11.png)

![Connexion IMS 3](/help/security/assets/ims12.png)

Si un fournisseurde Federated ID est configuré lors de la configuration initiale de l’Admin Console, la personne utilisatrice est redirigée vers le fournisseur d’identité client pour SSO :

![Connexion IMS 4](/help/security/assets/ims13.png)

Une fois l’authentification terminée, la personne utilisatrice est redirigée vers AEM et connectée :

![Connexion IMS 5](/help/security/assets/ims14.png)

### Gestion des autorisations et des listes de contrôle d’accès dans Adobe Experience Manager as a Cloud Service {#managing-permissions-in-aem}

Les listes de contrôle d’accès et les autorisations continuent d’être gérées dans AEM. Les groupes d’utilisateurs et d’utilisatrices synchronisés à partir d’IMS peuvent être affectés à des groupes locaux dans lesquels des listes de contrôle d’accès et des privilèges sont définis.

Dans l’exemple ci-dessous, des groupes synchronisés sont ajoutés au groupe local **Dam_Users**.

L’utilisateur fait partie des groupes suivants dans IMS :

![ACL1](/help/security/assets/ims15.png)

Lorsque l’utilisateur se connecte, ses adhésions de groupes sont synchronisées, comme illustré ci-dessous :

![ACL2](/help/security/assets/ims16.png)

Dans AEM, les groupes d’utilisateurs synchronisés à partir d’IMS peuvent être ajoutés en tant que membres aux groupes locaux existants, tels que **DAM User**.

![ACL3](/help/security/assets/ims17.png)

Comme illustré ci-dessous, le groupe **AEM-GRP_008** hérite des autorisations et droits des **utilisateurs et utilisatrices DAM**. Cet héritage est un moyen efficace de gérer les autorisations pour les groupes synchronisés. Il est généralement utilisé dans la méthode d’authentification LDAP.

![ACL3.](/help/security/assets/ims18.png)


### Accès à Cloud Manager {#accessing-cloud-manager}

Pour pouvoir accéder à Cloud Manager ou à des environnements sur AEM as a Cloud Service, les profils du produit Cloud Manager doivent vous être attribués.

Consultez Définitions de rôle pour en savoir plus sur les rôles des utilisateurs et utilisatrices qui régissent la disponibilité de fonctionnalités spécifiques dans Cloud Manager.

>[!NOTE]
>Cloud Manager dispose de rôles préconfigurés avec les autorisations appropriées. Pour en savoir plus sur les rôles dotés d’autorisations spécifiques, de tâches préconfigurées ou d’autorisations associées à chaque rôle, consultez [Autorisations basées sur les rôles](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-manager/content/requirements/role-based-permissions).

**Procédure d’ajout d’un utilisateur**

1. Vous pouvez ajouter un utilisateur à un profil particulier, soit à partir d’un écran d’utilisateur existant, soit à partir d’un nouvel écran d’utilisateur.

1. Vous pouvez également ajouter un utilisateur à partir de l’écran **Aperçu**, comme illustré dans la figure ci-dessous.

   ![ACL3](/help/security/assets/ims23.png)

   >[!NOTE]
   >Vous pouvez affecter plusieurs profils à un utilisateur, comme le montre la figure ci-dessous.

   ![ACL3](/help/security/assets/ims22.png)


1. Une fois votre ajout au profil approprié effectué, vous devez pouvoir accéder à la clientèle respective dans Cloud Manager via [Adobe Experience Cloud](https://my.cloudmanager.adobe.com) en utilisant l’angle supérieur droit de l’interface utilisateur.


### Accès à une instance dans AEM as a Cloud Service {#accessing-instance-cloud-service}

>[!IMPORTANT]
>Les étapes mentionnées dans la section précédente doivent avoir déjà été effectuées pour pouvoir accéder à une instance d’AEM as a Cloud Service.

Pour avoir accès à une instance AEM dans l’**Admin Console**, vous devez voir le programme Cloud Manager et les environnements du programme dans la liste de produits de l’**Admin Console**.

Par exemple, dans la capture d’écran ci-dessous, vous voyez deux environnements disponibles : *dev author* (création) et *publish* (publication).

![ACL3.](/help/security/assets/ims19.png)

Pour accéder aux instances AEM, la personne utilisatrice doit être ajoutée à un groupe du produit Cloud Service approprié.

Chaque instance de création possède un profil d’administration AEM et de personnes utilisatrices AEM, et chaque instance de publication possède un profil de personnes utilisatrices AEM. Si nécessaire, vous pouvez ajouter d’autres profils.

Pour obtenir un accès de niveau administrateur à l’instance AEM, ajoutez l’utilisateur au profil Administrateurs AEM pour ce produit particulier.
