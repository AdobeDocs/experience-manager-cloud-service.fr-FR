---
title: 'Inscription, connexion et Profil utilisateur '
description: En savoir plus sur l’abonnement, la connexion et le Profil d’utilisateur dans le volet Publier
translation-type: tm+mt
source-git-commit: 2c00c3723c3c84365044b5cd2fe6779de0360736
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 0%

---


# Inscription, connexion et Profil utilisateur {#registration-login-and-userprofile}

## Présentation {#introduction}

Les Applications web offrent souvent des fonctions de gestion de compte permettant aux utilisateurs finaux de s’enregistrer sur un site Web, ce qui permet de conserver leurs informations de profil d’utilisateur, leur permettant de se connecter ultérieurement et de bénéficier d’une expérience cohérente. Cet article décrit :

* Enregistrement
* Connexion
* Stockage des données de profil utilisateur
* Appartenance au groupe
* Synchronisation des données

>[!IMPORTANT]
>
>Pour que la fonctionnalité décrite dans cet article fonctionne, la fonction de synchronisation des données utilisateur doit être activée, ce qui nécessite pour le moment une demande au service clientèle indiquant le programme et les environnements appropriés. Si elles ne sont pas activées, les informations des utilisateurs seront conservées pendant une courte période (1 à 24 heures) avant de disparaître.

## Enregistrement {#registration}

Lorsqu’un utilisateur final s’enregistre pour un compte sur une application AEM, un compte d’utilisateur est créé sur le service de publication AEM, tel qu’il est reflété sur une ressource d’utilisateur sous `/home/users` dans le référentiel JCR.

La mise en oeuvre de l&#39;enregistrement repose sur deux approches, décrites ci-dessous.

### aem géré {#aem-managed-registration}

Il est possible d’écrire un code d’enregistrement personnalisé qui prend, au minimum, le nom d’utilisateur et le mot de passe de l’utilisateur final et crée un enregistrement d’utilisateur dans AEM qui peut ensuite être utilisé pour s’authentifier lors de la connexion. Les étapes suivantes sont généralement utilisées pour construire ce mécanisme d’enregistrement :

1. Affichage d’un composant d’AEM personnalisé qui collecte les informations d’enregistrement
1. Lors de l’envoi, un utilisateur de service correctement configuré est utilisé pour
   1. Vérifiez qu’un utilisateur existant n’existe pas déjà, en utilisant l’une des méthodes `findAuthorizables()` de l’API UserManager.
   1. Créez un enregistrement d&#39;utilisateur à l&#39;aide de l&#39;une des méthodes `createUser()` de l&#39;API UserManager.
   1. Persister toutes les données de profil capturées à l&#39;aide des méthodes `setProperty()` de l&#39;interface autorisée
1. Flux facultatifs, comme l’obligation pour l’utilisateur de valider son courrier électronique.

### Externe {#external-managed-registration}

Dans certains cas, l&#39;enregistrement ou la création d&#39;utilisateurs s&#39;est déjà produit dans des infrastructures en dehors de l&#39;AEM. Dans ce scénario, l’enregistrement utilisateur est créé dans AEM lors de la connexion.

## Connexion {#login}

Une fois qu’un utilisateur final est enregistré sur le service de publication AEM, ces utilisateurs peuvent se connecter pour disposer d’un accès authentifié (à l’aide de mécanismes d’autorisation AEM) et de données spécifiques persistantes à l’utilisateur, telles que les données de profil.

## Mise en œuvre {#implementation}

La connexion peut être mise en oeuvre selon les deux approches suivantes :

### aem géré {#aem-managed-implementation}

Les clients peuvent écrire leurs propres composants personnalisés. Pour en savoir plus, pensez à vous familiariser avec :

* La structure d&#39;authentification [Sling](https://sling.apache.org/documentation/the-sling-engine/authentication/authentication-framework.html)
* Et pensez à [demander à l&#39;AEM session d&#39;experts de la communauté](http://bit.ly/ATACEFeb15) de se connecter.

### Intégration à un fournisseur d&#39;identité {#integration-with-an-idp}

Les clients peuvent intégrer un IdP (fournisseur d&#39;identité), qui authentifie l&#39;utilisateur. Les technologies d’intégration incluent SAML et OAuth/SSO, comme décrit ci-dessous.

**BASÉ SUR SAML**

Les clients peuvent utiliser l’authentification SAML via leur IdP SAML préféré. Lors de l’utilisation d’un IdP avec AEM, l’IdP est chargé d’authentifier les informations d’identification de l’utilisateur final et de négocier l’authentification de l’utilisateur avec AEM, de créer l’enregistrement de l’utilisateur dans l’AEM, le cas échéant, et de gérer l’appartenance de groupe de l’utilisateur dans les , comme décrit par l’assertion SAML.

>[!NOTE]
>
>Seule l’authentification initiale des informations d’identification de l’utilisateur est authentifiée par l’IdP et les demandes d’AEM ultérieures sont exécutées à l’aide d’un cookie de jeton de connexion AEM, à condition que le cookie soit disponible.

Voir la documentation pour plus d’informations sur le [gestionnaire d’authentification SAML 2.0](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/saml-2-0-authenticationhandler.html?lang=en#saml-authentication-handler).

**OAuth/SSO**

Pour plus d’informations sur l’utilisation du service de gestionnaire d’authentification unique AEM, consultez la [documentation relative à la connexion unique (SSO)](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/single-sign-on.html).

L&#39;interface `com.adobe.granite.auth.oauth.provider` peut être implémentée avec le fournisseur OAuth de votre choix.

### Sessions réactives et jetons encapsulés {#sticky-sessions-and-encapsulated-tokens}

aem en tant que Cloud Service, les sessions d’affinité basées sur les cookies sont activées, ce qui garantit qu’un utilisateur final est dirigé vers le même noeud de publication pour chaque requête. Afin d’améliorer les performances, la fonction de jeton encapsulé est activée par défaut, de sorte que l’enregistrement utilisateur dans le référentiel n’ait pas besoin d’être référencé pour chaque requête. Si le noeud de publication auquel l’utilisateur final a une affinité est remplacé, son enregistrement d’ID utilisateur est disponible sur le nouveau noeud de publication, comme décrit dans la section de synchronisation des données ci-dessous.

## Profil utilisateur {#user-profile}

Il existe différentes approches pour conserver les données, selon la nature de ces données.

### Référentiel AEM {#aem-repository}

Les informations du profil utilisateur peuvent être écrites et lues de deux manières :

* Utilisation côté serveur avec l&#39;interface `com.adobe.granite.security.user` UserPropertiesManager, qui place les données sous le noeud de l&#39;utilisateur dans `/home/users`. Assurez-vous que les pages uniques par utilisateur ne sont pas mises en cache.
* côté client à l’aide de ContextHub, comme décrit par [la documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/personalization/contexthub.html?lang=en#personalization).

### Stockages de données tiers {#third-party-data-stores}

Les données de l’utilisateur final peuvent être envoyées à des fournisseurs tiers, tels que des systèmes de gestion de la relation client, et récupérées par le biais d’API lors de la connexion de l’utilisateur à l’AEM et conservées (ou actualisées) sur le noeud de profil de l’utilisateur AEM, et utilisées par l’utilisateur le cas échéant par l’AEM.

Il est possible d’accéder en temps réel à des services tiers pour récupérer des attributs de profil. Toutefois, il est important de s’assurer que cela n’a pas d’impact significatif sur le traitement des demandes dans AEM.

## Autorisations (groupes d’utilisateurs fermés) {#permissions-closed-user-groups}

Les stratégies d’accès de la publication, également appelées CUG (Closed User Groups), sont définies dans l’auteur de l’AEM comme [décrites ici](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/cug.html?lang=en#applying-your-closed-user-group-to-content-pages). Afin de limiter certains sections ou pages d’un site Web à certains utilisateurs, appliquez les CUG selon les besoins à l’aide de l’auteur de l’AEM, comme décrit ici, et dupliquez-les au niveau de publication.

* Si les utilisateurs se connectent en s&#39;authentifiant auprès d&#39;un fournisseur d&#39;identité (IdP) à l&#39;aide de SAML, le gestionnaire d&#39;authentification identifie les appartenances de groupe de l&#39;utilisateur (qui doivent correspondre aux CUG sur la couche de publication) et maintient l&#39;association entre l&#39;utilisateur et le groupe via un enregistrement de référentiel.
* Si la connexion est établie sans intégration IdP, le code personnalisé peut appliquer les mêmes relations de structure de référentiel.

Indépendamment de la connexion, le code personnalisé peut également persister et gérer les appartenances d’un groupe d’utilisateurs en fonction des besoins uniques de l’entreprise.

## Synchronisation des données {#data-synchronization}

Les utilisateurs finaux du site Web attendent une expérience cohérente pour chaque requête de page Web ou même lorsqu’ils se connectent à l’aide d’un navigateur différent, même s’ils ne le savent pas, ils sont amenés à différents noeuds de serveur de l’infrastructure de la couche Publication. aem en tant que Cloud Service effectue cette opération en synchronisant rapidement la hiérarchie de dossiers `/home` (informations de profil d&#39;utilisateur, appartenance à un groupe, etc.) sur tous les noeuds de la couche de publication.

Contrairement à d’autres solutions AEM, la synchronisation des membres d’utilisateurs et de groupes dans AEM en tant que Cloud Service n’utilise pas une approche de messagerie point à point, mais met en oeuvre une approche de publication-abonnement qui ne nécessite pas de configuration client.

>[!NOTE]
>
>Par défaut, la synchronisation des profils d’utilisateurs et des membres de groupes n’est pas activée et les données ne seront donc pas synchronisées ni même conservées de manière permanente sur la couche de publication. Pour activer la fonction, envoyez une demande au service d’assistance clientèle pour lui indiquer le programme et les environnements appropriés.

## Considérations sur le cache {#cache-considerations}

Les requêtes HTTP authentifiées peuvent être difficiles à mettre en cache à la fois sur le CDN et sur le Répartiteur, car elles comportent la possibilité de transférer un état spécifique à l’utilisateur dans le cadre de la réponse de la requête. La mise en cache accidentelle de requêtes authentifiées et leur diffusion sur d’autres navigateurs demandeurs peuvent entraîner des expériences incorrectes, voire la fuite de données protégées ou d’utilisateurs.

Voici quelques-unes des méthodes permettant de conserver une capacité élevée de mémoire cache des requêtes tout en prenant en charge les réponses spécifiques à l’utilisateur :

* Mise en cache sensible des autorisations du répartiteur AEM
* Inclure dynamique Sling
* aem ContextHub