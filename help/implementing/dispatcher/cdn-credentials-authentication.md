---
title: Configurer les informations d’identification et l’authentification du réseau CDN
description: Découvrez comment configurer les informations d’identification et l’authentification du réseau de diffusion de contenu en déclarant les règles dans un fichier de configuration qui est ensuite déployé à l’aide du pipeline de configuration de Cloud Manager.
feature: Dispatcher
exl-id: a5a18c41-17bf-4683-9a10-f0387762889b
source-git-commit: e6059a1109ca93452f80440744338b809279db9b
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 2%

---

# Configurer les informations d’identification et l’authentification du réseau CDN {#cdn-credentials-authentication}

>[!NOTE]
>Cette fonctionnalité n’est pas encore disponible pour l’ensemble de la population. Pour rejoindre le programme d’adoption précoce, envoyez un email à `aemcs-cdn-config-adopter@adobe.com`.

Le réseau de diffusion de contenu fourni par l’Adobe dispose de plusieurs fonctionnalités et services, dont certains dépendent des informations d’identification et de l’authentification afin d’assurer un niveau approprié de sécurité de l’entreprise. En déclarant des règles dans un fichier de configuration déployé à l’aide de la variable [Pipeline de configuration de Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline), les clients peuvent configurer, en libre-service, les éléments suivants :

* La valeur d’en-tête HTTP utilisée par le réseau de diffusion de contenu Adobe pour valider les requêtes provenant d’un réseau de diffusion de contenu géré par le client.
* Jeton API utilisé pour purger les ressources dans le cache CDN.

Chacune d’elles, y compris la syntaxe de configuration, est décrite dans sa propre section ci-dessous. La variable [Configuration commune](#common-setup) La section illustre la configuration commune aux deux environnements, ainsi qu’au déploiement. Enfin, il y a une section sur la façon de [rotation des clés](#rotating-secrets), qui est considéré comme une bonne pratique de sécurité.

## Valeur d’en-tête HTTP CDN gérée par le client {#CDN-HTTP-value}

Comme décrit dans la section [Réseau de diffusion de contenu dans AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) , les clients peuvent choisir d’acheminer le trafic par le biais de leur propre réseau de diffusion de contenu, appelé réseau de diffusion de contenu client (parfois appelé BYOCDN).

Dans le cadre de la configuration, le réseau de diffusion de contenu Adobe et le réseau de diffusion de contenu client doivent s’entendre sur une valeur de la variable `X-AEM-Edge-Key` En-tête HTTP. Cette valeur est définie sur chaque requête, sur le réseau de diffusion de contenu client, avant d’être acheminée vers le réseau de diffusion de contenu Adobe, qui valide ensuite que la valeur est comme prévu, de sorte qu’il puisse faire confiance à d’autres en-têtes HTTP, y compris ceux qui aident à acheminer la demande vers l’origine AEM appropriée.

La variable `X-AEM-Edge-Key` est déclarée avec la syntaxe ci-dessous. Voir [Configuration commune](#common-setup) pour savoir comment le déployer.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_authentication:
    authenticators:
      - name: edge-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_052824}}
        edgeKey2: ${{CDN_EDGEKEY_041425}}
    rules:
      - name: edge-auth-rule
        when: { reqProperty: tier, equals: "publish" }
        action:
          type: authenticate
          authenticator: edge-auth
```

La syntaxe de la variable `X-AEM-Edge-Key` La valeur inclut :

* Type, version et métadonnées.
* Noeud de données contenant un enfant `experimental_authentication` (le préfixe expérimental sera supprimé lorsque la fonction sera publiée).
* Sous la fonction &quot;expérimental_authentication&quot;, avec un noeud d’authentificateur et un noeud de règles, qui sont tous deux des tableaux.
* Authentificateurs : vous permet de déclarer un type de jeton ou d’informations d’identification, qui dans ce cas est une clé de périphérie. Elle comprend les propriétés suivantes :
   * name : chaîne descriptive.
   * type : doit être edge.
   * edgeKey1 : sa valeur doit référencer un jeton secret, qui ne doit pas être stocké dans git, mais plutôt déclaré en tant que [Variable d’environnement Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) de type secret. Pour le champ Service appliqué, sélectionnez Tous. Il est recommandé que la valeur (par exemple,`${{CDN_EDGEKEY_052824}}`) reflète le jour où il a été ajouté.
   * edgeKey2 : utilisé pour la rotation des secrets, qui est décrite dans la section [section secrets rotatifs](#rotating-secrets) ci-dessous Au moins un des `edgeKey1` et `edgeKey2` doivent être déclarées.
<!--   * OnFailure - defines the action, either `log` or `block`, when a request doesn't match either `edgeKey1` or `edgeKey2`. For `log`, request processing will continue, while `block` will serve a 403 error. The `log` value is useful when testing a new token on a live site since you can first confirm that the CDN is correctly accepting the new token before changing to `block` mode; it also reduces the chance of lost connectivity between the customer CDN and the Adobe CDN, as a result of an incorrect configuration. -->
* Règles : vous permet de déclarer quels authentificateurs doivent être utilisés et s’il s’agit du niveau de publication et/ou d’aperçu.  Il comprend :
   * name : chaîne descriptive.
   * When : condition qui détermine le moment où la règle doit être évaluée, selon la syntaxe de la variable [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) article. En règle générale, il comprend une comparaison du niveau actuel (par exemple, publication) afin que tout le trafic en direct soit validé en tant que routage via le réseau de diffusion de contenu du client.
   * action : doit spécifier &quot;authenticate&quot;, avec l’authentificateur prévu référencé.

>[!NOTE]
>La clé Edge doit être configurée comme [Variable d’environnement Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) variable de type `secret`, avant que la configuration référençant son déploiement.

## Purge du jeton API {#purge-API-token}

Les clients peuvent [purge du cache CDN](/help/implementing/dispatcher/cdn-cache-purge.md) en utilisant un jeton API de purge déclaré. Le jeton est déclaré avec la syntaxe ci-dessous.  Voir [Configuration commune](#common-setup) pour savoir comment le déployer.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_authentication:
    authenticators:
       - name: purge-auth
         type: purge
         purgeKey1: ${{CDN_PURGEKEY_031224}}
         purgeKey2: ${{CDN_PURGEKEY_021225}}
    rules:
     - name: purge-auth-rule
       when: { reqProperty: tier, equals: "publish" }
       action:
         type: authenticate
         authenticator: purge-auth
```

La syntaxe comprend :

* type, version et métadonnées.
* noeud de données contenant un enfant `experimental_authentication` (le préfixe expérimental sera supprimé lorsque la fonction sera publiée).
* Sous `experimental_authentication`, avec un seul noeud d’authentificateurs.
* Authentificateurs : vous permet de déclarer un type de jeton ou d’informations d’identification, qui dans ce cas est une clé de purge. Elle comprend les propriétés suivantes :
   * name : chaîne descriptive.
   * type : doit être purge.
   * purgeKey1 : sa valeur doit référencer un jeton secret, qui ne doit pas être stocké dans git, mais plutôt déclaré comme [Variables d’environnement Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) de type `secret`.
   * Pour le champ Service appliqué, sélectionnez Tous. Il est recommandé que la valeur (par exemple, `${{CDN_PURGEKEY_031224}}`) reflète le jour où il a été ajouté.
   * purgeKey2 : utilisé pour la rotation des secrets, qui est décrite dans la section [section secrets rotatifs](#rotating-secrets) ci-dessous. Au moins un des `purgeKey1` et `purgeKey2` doivent être déclarées.
* Règles : vous permet de déclarer quels authentificateurs doivent être utilisés et s’il s’agit du niveau de publication et/ou d’aperçu.  Il comprend :
   * name - chaîne descriptive
   * When : condition qui détermine le moment où la règle doit être évaluée, selon la syntaxe de la variable [Règles de filtrage du trafic](/help/security/traffic-filter-rules-including-waf.md) article. En règle générale, il comprend une comparaison du niveau actuel (par exemple, publication).
   * action : doit spécifier &quot;authenticate&quot;, avec l’authentificateur prévu référencé.

>[!NOTE]
>La clé Edge doit être configurée comme [Variable d’environnement Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) variable de type `secret`, avant que la configuration référençant son déploiement.

## Configuration commune {#common-setup}

Tous les authentificateurs sont configurés comme suit :

* Tout d’abord, créez la structure de dossiers et de fichiers suivante dans le dossier de niveau supérieur de votre projet Git :

```
config/
     cdn.yaml
```

* Deuxièmement, le `cdn.yaml` Le fichier de configuration doit contenir les noeuds décrits dans les exemples ci-dessous. La variable `kind` doit être définie sur `CDN` et la version doit être définie sur la version du schéma, qui est actuellement `1`. Le noeud de métadonnées possède une propriété &quot;envTypes&quot;, qui indique sur quels types d’environnement (développement, évaluation, production) cette configuration sera évaluée.

* Enfin, créez un pipeline de configuration de déploiement ciblé dans Cloud Manager. Voir [configuration des pipelines de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) et [configuration des pipelines hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

Notez que :

* Les RDE ne prennent actuellement pas en charge le pipeline de configuration.
* Vous pouvez utiliser `yq` pour valider localement le format YAML de votre fichier de configuration (par exemple, `yq cdn.yaml`).

## Rotation des secrets {#rotating-secrets}

Il est recommandé de modifier occasionnellement les informations d’identification en toute sécurité. Vous pouvez y parvenir comme illustré ci-dessous en utilisant l’exemple d’une clé de périphérie, bien que la même stratégie soit utilisée pour les clés de purge.

* Initialement juste `edgeKey1` a été défini, dans ce cas référencé comme `${{CDN_EDGEKEY_052824}}`, qui, comme convention recommandée, reflète la date à laquelle elle a été créée.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
```

* Lorsque le temps est venu de faire pivoter la clé, créez un secret Cloud Manager, par exemple `${{CDN_EDGEKEY_041425}}`.
* Dans la configuration, référencez-la à partir de `edgeKey2` et déployez.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* Une fois que vous êtes certain que l’ancienne clé Edge n’est plus utilisée, supprimez-la en supprimant `edgeKey1` de la configuration.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* Supprimer l’ancienne référence secrète (`${{CDN_EDGEKEY_052824}}`) de Cloud Manager et de déployer.
* Lorsque vous êtes prêt pour la rotation suivante, procédez de la même manière. Toutefois, cette fois, vous allez ajouter `edgeKey1` à la configuration, en référençant un nouveau secret d’environnement Cloud Manager nommé, par exemple : `${{CDN_EDGEKEY_031426}}`.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
      edgeKey1: ${{CDN_EDGEKEY_031426}}
```
