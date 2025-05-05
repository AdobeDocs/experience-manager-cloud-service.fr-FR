---
title: Enregistrement, connexion et profil utilisateur
description: En savoir plus sur l’enregistrement, la connexion, les données utilisateur et la synchronisation de groupe pour AEM as a Cloud Service
exl-id: a991e710-a974-419f-8709-ad86c333dbf8
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '1343'
ht-degree: 65%

---

# Enregistrement, connexion et profil utilisateur {#registration-login-and-userprofile}

## Présentation {#introduction}

Les applications web offrent souvent des fonctions de gestion de compte permettant aux utilisateurs finaux de s’inscrire sur un site web. Ils peuvent ainsi conserver leurs informations de données utilisateur pour se connecter ultérieurement et bénéficier d’une expérience cohérente. Cet article décrit les concepts suivants pour AEM as a Cloud Service :

* L’enregistrement
* La connexion
* Le stockage des données du profil utilisateur
* L’appartenance à un groupe
* La synchronisation des données.

## L’enregistrement {#registration}

Lorsqu’un utilisateur final s’enregistre pour un compte sur une application AEM, un compte d’utilisateur est créé sur le service de publication d’AEM, tel qu’il est reflété sur une ressource d’utilisateur sous `/home/users` dans le référentiel JCR.

La mise en œuvre de l’enregistrement repose sur deux approches, décrites ci-dessous.

### Gestion par AEM {#aem-managed-registration}

Il est possible d’écrire un code d’enregistrement personnalisé qui prend, au minimum, le nom d’utilisateur et le mot de passe de l’utilisateur et crée un enregistrement de l’utilisateur dans AEM qui peut ensuite être utilisé pour s’authentifier lors de la connexion. Les étapes suivantes sont généralement utilisées pour construire ce mécanisme d’enregistrement :

1. Affichez un composant d’AEM personnalisé qui collecte les informations d’enregistrement.
1. Lors de l’envoi, un utilisateur de service correctement configuré est utilisé pour :
   1. vérifier qu’un utilisateur n’existe pas déjà, en utilisant l’une des méthodes `findAuthorizables()` de l’API UserManager ;
   1. créer un enregistrement utilisateur à l’aide de l’une des méthodes `createUser()` de l’API UserManager ;
   1. conserver toutes les données de profil capturées à l’aide des méthodes `setProperty()` de l’interface Authorizable.
1. Flux facultatifs, comme l’obligation pour l’utilisateur de valider son courrier électronique.

**Condition préalable requise :**

Pour que la logique décrite ci-dessus fonctionne correctement, activez la [synchronisation des données](#data-synchronization-data-synchronization) en envoyant
une demande au service clientèle indiquant le programme et les environnements appropriés.

### Externe {#external-managed-registration}

Dans certains cas, l’enregistrement ou la création d’utilisateurs a déjà été effectué(e) dans des infrastructures situées en dehors d’AEM. Dans ce scénario, l’enregistrement utilisateur est créé dans AEM lors de la connexion.

## La connexion {#login}

Une fois un utilisateur final enregistré sur le service de publication AEM, il peut se connecter pour disposer d’un accès authentifié (à l’aide de mécanismes d’autorisation AEM) et obtenir des données persistantes, spécifiques à l’utilisateur, comme les données de profil.

## Mise en œuvre {#implementation}

La connexion peut être mise en œuvre selon les deux approches suivantes :

### Gestion par AEM {#aem-managed-implementation}

Les clients peuvent écrire leurs propres composants personnalisés. Pour en savoir plus, envisagez de vous familiariser avec :

* La [structure d’authentification Sling](https://sling.apache.org/documentation/the-sling-engine/authentication/authentication-framework.html)
* Envisagez aussi de [demander une session d’experts de la communauté AEM](https://bit.ly/ATACEFeb15) à propos de la connexion.

**Condition préalable requise :**

Pour que la logique décrite ci-dessus fonctionne correctement, activez la [synchronisation des données](#data-synchronization-data-synchronization) en envoyant
une demande au service clientèle indiquant le programme et les environnements appropriés.

### Intégration à un fournisseur d’identités {#integration-with-an-idp}

Les clients peuvent intégrer un IdP (fournisseur d’identités), chargé d’authentifier l’utilisateur. Les technologies d’intégration incluent SAML et OAuth/SSO, comme décrit ci-dessous.

**BASÉ SUR SAML**

Les clients peuvent utiliser l’authentification SAML par le biais de leur IdP SAML préféré. Lors de l’utilisation d’un IdP avec AEM, l’IdP est chargé d’authentifier les informations d’identification de l’utilisateur et d’arbitrer l’authentification de l’utilisateur avec AEM, de créer l’enregistrement de l’utilisateur dans l’ selon les besoins et de gérer l’appartenance de l’utilisateur au groupe dans, comme décrit par l’assertion SAML.

>[!NOTE]
>
>Seule l’authentification initiale des informations d’identification de l’utilisateur est authentifiée par l’IdP et les demandes d’AEM ultérieures sont exécutées à l’aide d’un cookie de jeton de connexion AEM, à condition que ce cookie soit disponible.

Voir la documentation pour plus d’informations sur le [gestionnaire d’authentification SAML 2.0](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/authentication/saml-2-0.html?lang=fr).

**OAuth/SSO**

Pour plus d’informations sur l’utilisation du service de gestionnaire d’authentification unique d’AEM, consultez la [documentation relative à la connexion unique (SSO)](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/single-sign-on.html?lang=fr).

L’interface `com.adobe.granite.auth.oauth.provider` peut être implémentée avec le fournisseur OAuth de votre choix.

**Condition préalable requise :**

En règle générale, il est recommandé de toujours s’appuyer sur le fournisseur d’identité (idP) comme un seul point de vérité lors du stockage de données spécifiques à l’utilisateur. Si les informations utilisateur supplémentaires sont stockées dans le référentiel local, qui ne fait pas partie de l’idP, activez la [synchronisation des données](#data-synchronization-data-synchronization) en envoyant une demande au service clientèle indiquant le programme et les environnements appropriés. En plus de la [synchronisation des données](#data-synchronization-data-synchronization), dans le cas du fournisseur d’authentification SAML, assurez-vous que l’[appartenance à un groupe dynamique](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) est activée.

### Sessions réactives et jetons encapsulés {#sticky-sessions-and-encapsulated-tokens}

AEM as a Cloud Service active les sessions persistantes basées sur des cookies, en s’assurant qu’un utilisateur final est redirigé vers le même noeud de publication à chaque demande. Dans certains cas particuliers, tels que les pics de trafic utilisateur, la fonction de jeton encapsulé peut améliorer les performances afin que l’enregistrement utilisateur dans le référentiel ne doive pas être référencé pour chaque requête. Si le noeud de publication auquel un utilisateur final a une affinité est remplacé, son enregistrement d’ID utilisateur est disponible sur le nouveau noeud de publication, comme décrit dans la section [synchronisation des données](#data-synchronization-data-synchronization) ci-dessous.

Pour tirer parti de la fonctionnalité de jeton encapsulé, veuillez envoyer une demande au service clientèle indiquant le programme et les environnements appropriés. Plus important encore, le jeton encapsulé ne peut pas être activé sans [synchronisation des données](#data-synchronization-data-synchronization) et doit être activé ensemble. Par conséquent, passez soigneusement en revue le cas d’utilisation avant d’activer et de vérifier que la fonctionnalité est essentielle.

## Profil utilisateur {#user-profile}

Il existe différentes approches pour conserver les données, selon la nature de ces données.

### Référentiel AEM {#aem-repository}

Les informations de profil utilisateur peuvent être écrites et lues de deux manières :

* Utilisation côté serveur avec l’interface `com.adobe.granite.security.user` UserPropertiesManager, qui place les données sous le nœud de l’utilisateur dans `/home/users`. Assurez-vous que les pages uniques par utilisateur ne soient pas mises en cache.
* Utilisation côté client avec ContextHub, comme décrit dans [la documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/personalization/contexthub.html?lang=fr#personalization).

**Condition préalable requise :**

Pour que la logique de persistance du profil utilisateur côté serveur fonctionne correctement, activez la [synchronisation des données](#data-synchronization-data-synchronization) en envoyant
une demande au service clientèle indiquant le programme et les environnements appropriés.

### Magasins de données tiers {#third-party-data-stores}

Les données de la personnes utilisatrice finale peuvent être envoyées à des fournisseurs tiers, comme les systèmes de gestion de la relation client (CRM). Elles sont récupérées par le biais d’API lors de la connexion de l’utilisateur ou de l’utilisatrice à AEM et conservées (ou actualisées) sur le nœud de profil de l’utilisateur ou de l’utilisatrice AEM, puis utilisées le cas échéant par AEM.

Il est possible d’accéder en temps réel à des services tiers pour récupérer des attributs de profil. Toutefois, il est important de s’assurer que cela n’ait pas d’impact significatif sur le traitement des demandes dans AEM.

**Condition préalable requise :**

Pour que la logique décrite ci-dessus fonctionne correctement, activez la [synchronisation des données](#data-synchronization-data-synchronization) en envoyant
une demande au service clientèle indiquant le programme et les environnements appropriés.

## Autorisations (groupes d’utilisateurs fermés) {#permissions-closed-user-groups}

Les stratégies d’accès de niveau Publish, également appelées groupes d’utilisateurs fermés (CUG), sont définies dans l’AEM de l’auteur, voir [Création d’un groupe d’utilisateurs fermé](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/cug.html?lang=fr#applying-your-closed-user-group-to-content-pages). Pour limiter certaines sections ou pages d’un site web à certains utilisateurs ou certaines utilisatrices, appliquez les CUG selon les besoins à l’aide de l’instance de création AEM, comme décrit ici, et dupliquez-les au niveau Publication.

* Si les utilisateurs se connectent en s’authentifiant auprès d’un fournisseur d’identités (IdP) à l’aide de SAML, le gestionnaire d’authentification identifie les appartenances de groupe de l’utilisateur (qui doivent correspondre aux CUG pour le niveau Publication) et maintient l’association entre l’utilisateur et le groupe par le biais d’un enregistrement de référentiel.
* Si la connexion est établie sans intégration IdP, le code personnalisé peut appliquer les mêmes relations de structure de référentiel.

Indépendamment de la connexion, le code personnalisé peut également être conservé et gérer les appartenances d’un groupe d’utilisateurs en fonction des besoins uniques de l’entreprise.

## La synchronisation des données. {#data-synchronization}

Les utilisateurs finaux du site web attendent une expérience cohérente pour chaque requête de page web ou même lorsqu’ils se connectent à l’aide d’un navigateur différent. Même s’ils ne le savent pas, ils sont conduits vers différents nœuds de serveur de l’infrastructure du niveau Publication. Pour ce faire, AEM as a Cloud Service synchronise rapidement la hiérarchie de dossiers `/home` (informations de profil utilisateur, appartenance à un groupe, etc.) sur tous les noeuds du niveau publication.

Contrairement à d’autres solutions AEM, la synchronisation des utilisateurs et de l’appartenance à un groupe dans AEM as a Cloud Service n’utilise pas une approche de messagerie point à point, mais plutôt une approche publication-abonnement qui ne nécessite pas de configuration client.

>[!NOTE]
>
>Par défaut, la synchronisation des profils d’utilisateurs et des membres de groupes n’est pas activée et les données ne seront donc pas synchronisées ni même conservées de manière permanente au niveau Publication. Pour activer la fonction, adressez une demande au service d’assistance clientèle pour lui indiquer le programme et les environnements appropriés.

>[!IMPORTANT]
>
>Testez l’implémentation à grande échelle avant d’activer la synchronisation des données dans l’environnement de production. Selon le cas d’utilisation et les données conservées, des problèmes de cohérence et de latence peuvent se produire.

## Considérations relatives au cache {#cache-considerations}

Les requêtes HTTP authentifiées peuvent être difficiles à mettre en cache à la fois sur le CDN et sur le Dispatcher, car elles comportent la possibilité de transférer un état spécifique à l’utilisateur dans le cadre de la réponse de la requête. La mise en cache accidentelle de requêtes authentifiées et leur diffusion vers d’autres navigateurs demandeurs peuvent entraîner des expériences incorrectes, voire la fuite de données protégées ou appartenant à des utilisateurs.

Un certain nombre de méthodes permettent de conserver une capacité élevée de mise en cache des requêtes tout en prenant en charge les réponses spécifiques à l’utilisateur :

* Mise en cache sensible aux autorisations du Dispatcher AEM
* Service Sling Dynamic Include
* AEM ContextHub
