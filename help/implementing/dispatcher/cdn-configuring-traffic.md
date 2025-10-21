---
title: Configurer le trafic sur le réseau CDN
description: Découvrez comment configurer le trafic CDN en déclarant des règles et des filtres dans un fichier de configuration et en les déployant sur le réseau CDN à l’aide d’un pipeline de configuration Cloud Manager.
feature: Dispatcher
exl-id: e0b3dc34-170a-47ec-8607-d3b351a8658e
role: Admin
source-git-commit: a8c313c3b1324e4195c2aeb70a5a56e4ef66fcf3
workflow-type: tm+mt
source-wordcount: '1698'
ht-degree: 1%

---


# Configurer le trafic sur le réseau CDN {#cdn-configuring-cloud}

AEM as a Cloud Service propose un ensemble de fonctionnalités configurables au niveau de la couche [CDN géré par Adobe](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) qui modifient la nature des requêtes entrantes ou des réponses sortantes. Les règles suivantes, décrites en détail sur cette page, peuvent être déclarées pour obtenir le comportement suivant :

* [Transformations de requête](#request-transformations) - modifiez certains aspects des requêtes entrantes, y compris les en-têtes, les chemins et les paramètres.
* [Transformations de réponse](#response-transformations) - modifiez les en-têtes qui sont en train de revenir au client (par exemple, un navigateur web).
* [Redirections côté serveur](#server-side-redirectors) - déclenchez une redirection de navigateur.
* [Sélecteurs d’origine](#origin-selectors) : proxy vers un autre serveur principal d’origine.

Vous pouvez également configurer sur le réseau CDN les règles de filtrage du trafic (y compris WAF), qui contrôlent le trafic autorisé ou refusé par le réseau CDN. Cette fonctionnalité est déjà disponible et vous pouvez en savoir plus à ce sujet sur la page [Règles de filtrage de trafic , y compris les règles WAF](/help/security/traffic-filter-rules-including-waf.md).

De plus, si le réseau CDN ne peut pas contacter son origine, vous pouvez créer une règle qui fait référence à une page d’erreur personnalisée auto-hébergée (qui est ensuite rendue). Pour en savoir plus à ce sujet, consultez l’article [Configuration des pages d’erreur du réseau CDN](/help/implementing/dispatcher/cdn-error-pages.md).

Toutes ces règles, déclarées dans un fichier de configuration dans le contrôle de code source, sont déployées à l’aide du pipeline Cloud Manager [config](/help/operations/config-pipeline.md). Notez que la taille cumulée du fichier de configuration, y compris les règles de filtrage du trafic, ne peut pas dépasser 100KB.

## Ordre d&#39;évaluation {#order-of-evaluation}

Fonctionnellement, les différentes fonctionnalités mentionnées précédemment sont évaluées dans l&#39;ordre suivant:

![Ordre d’évaluation](/help/implementing/dispatcher/assets/order.png)

## Configuration {#initial-setup}

Avant de pouvoir configurer le trafic sur le réseau CDN, vous devez effectuer les opérations suivantes :

1. Créez un fichier nommé `cdn.yaml` ou similaire, en référençant les différents fragments de code de configuration dans les sections ci-dessous.

   Tous les fragments de code possèdent ces propriétés communes, qui sont décrites sous [Pipeline de configuration](/help/operations/config-pipeline.md#common-syntax). La valeur de la propriété `kind` doit être *CDN* et la propriété `version` doit être définie sur *1*.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   ```

1. Placez le fichier quelque part sous un dossier de niveau supérieur nommé *config* ou similaire, comme décrit sous [Pipeline de configuration](/help/operations/config-pipeline.md#folder-structure).

1. Créez un Pipeline de configuration dans Cloud Manager, comme décrit dans [Pipeline de configuration](/help/operations/config-pipeline.md#managing-in-cloud-manager).

1. Déployez la configuration.

## Syntaxe des règles {#configuration-syntax}

Les types de règle des sections ci-dessous partagent une syntaxe commune.

Une règle est référencée par un nom, une « clause de quand » conditionnelle et des actions.

La clause « quand » détermine si une règle sera évaluée en fonction des propriétés, notamment le domaine, le chemin, les chaînes de requête, les en-têtes et les cookies. La syntaxe est identique pour tous les types de règle ; pour plus d’informations, consultez la section [Structure de condition](/help/security/traffic-filter-rules-including-waf.md#condition-structure) de l’article Règles de filtrage du trafic .

Les détails du nœud d’actions diffèrent selon le type de règle et sont décrits dans les sections individuelles ci-dessous.

Dans les règles de configuration, vous pouvez référencer des secrets définis comme variables d’environnement (voir [Secrets de configuration](/help/implementing/dispatcher/cdn-credentials-authentication.md)).

## Transformations de requête {#request-transformations}

Les règles de transformation des requêtes vous permettent de modifier les requêtes entrantes. Les règles prennent en charge la définition, la suppression et la modification de chemins, de paramètres de requête et d’en-têtes (y compris les cookies) en fonction de diverses conditions correspondantes, y compris des expressions régulières. Vous pouvez également définir des variables, qui peuvent ensuite être référencées plus loin dans la séquence d’évaluation.

Les cas d’utilisation sont variés et incluent des réécritures d’URL pour simplifier l’application ou mapper des URL héritées.

Comme mentionné précédemment, le fichier de configuration est soumis à une limite de taille. Les entreprises ayant des besoins plus importants doivent donc définir des règles dans la couche de `apache/dispatcher`.

Exemple de configuration :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
data:
  requestTransformations:
    removeMarketingParams: true
    rules:
      - name: set-header-rule
        when:
          reqProperty: path
          like: /set-header
        actions:
          - type: set
            reqHeader: x-some-header
            value: some value
      - name: set-header-with-reqproperty-rule
        when:
          reqProperty: path
          like: /set-header
        actions:
          - type: set
            reqHeader: x-some-header
            value: {reqProperty: path}
      - name: unset-header-rule
        when:
          reqProperty: path
          like: /unset-header
        actions:
          - type: unset
            reqHeader: x-some-header
      - name: unset-matching-query-params-rule
        when:
          reqProperty: path
          equals: /unset-matching-query-params
        actions:
          - type: unset
            queryParamMatch: ^removeMe_.*$
      - name: unset-all-query-params-except-exact-two-rule
        when:
          reqProperty: path
          equals: /unset-all-query-params-except-exact-two
        actions:
          - type: unset
            queryParamMatch: ^(?!leaveMe$|leaveMeToo$).*$
      - name: multi-action
        when:
          reqProperty: path
          like: /multi-action
        actions:
          - type: set
            reqHeader: x-header1
            value: body set by transformation rule
          - type: set
            reqHeader: x-header2
            value: '201'
      - name: replace-html
        when:
          reqProperty: path
          like: /mypath
        actions:
          - type: transform
            reqProperty: path
            op: replace
            match: \.html$
            replacement: ""
      - name: log-on-request
        when: "*"
        actions:
          - type: set
            logProperty: forwarded_host
            value:
              reqHeader: x-forwarded-host
```

**Actions**

Les actions disponibles sont expliquées dans le tableau ci-dessous.

| Nom | Propriétés | Signification |
|-----------|--------------------------|-------------|
| **défini** | reqProperty, value | Définit un paramètre de requête spécifié (seule la propriété « path » est prise en charge) |
|     | reqHeader, valeur | Définit un en-tête de requête spécifié sur une valeur donnée. |
|     | queryParam, valeur | Définit un paramètre de requête spécifié sur une valeur donnée. |
|     | reqCookie, valeur | Définit un cookie de requête spécifié sur une valeur donnée. |
|     | logProperty, valeur | Définit une propriété de journal CDN spécifiée sur une valeur donnée. |
|     | var, valeur | Définit une variable spécifiée sur une valeur donnée. |
| **désactivé** | reqProperty | Supprime un paramètre de requête spécifié (seule la propriété « path » est prise en charge) |
|     | reqHeader, valeur | Supprime un en-tête de requête spécifié. |
|     | queryParam, valeur | Supprime un paramètre de requête spécifié. |
|     | reqCookie, valeur | Supprime un cookie spécifié. |
|     | logProperty, valeur | Supprime une propriété de journal CDN spécifiée. |
|     | var | Supprime une variable spécifiée. |
|     | queryParamMatch | Supprime tous les paramètres de requête qui correspondent à une expression régulière spécifiée. |
|     | queryParamDoesNotMatch | Supprime tous les paramètres de requête qui ne correspondent pas à une expression régulière spécifiée. |
| **transformation** | op:replace, (reqProperty ou reqHeader ou queryParam ou reqCookie ou var), correspondance, remplacement | Remplace une partie du paramètre de requête (seule la propriété « path » est prise en charge), ou de l’en-tête de requête, ou du paramètre de requête, ou du cookie, ou de la variable par une nouvelle valeur . |
|              | op:tolower, (reqProperty ou reqHeader ou queryParam ou reqCookie ou var) | Définit le paramètre de requête (seule la propriété « path » est prise en charge), ou l’en-tête de requête, ou le paramètre de requête, ou le cookie, ou la variable sur sa valeur en minuscules. |

Remplacez les actions qui prennent en charge les groupes de capture, comme illustré ci-dessous :

```
      - name: extract-country-code-from-path
        when:
          reqProperty: path
          matches: ^/([a-zA-Z]{2})(/.*|$)
        actions:
          - type: set
            var: country-code
            value:
              reqProperty: path
          - type: transform
            var: country-code
            op: replace
            match: ^/([a-zA-Z]{2})(/.*|$)
            replacement: \1
      - name: replace-jpg-with-jpeg
        when:
          reqProperty: path
          like: /mypath
        actions:
          - type: transform
            reqProperty: path
            op: replace
            match: (.*)(\.jpg)$
            replacement: "\1\.jpeg"
```

Les actions peuvent être enchaînées. Par exemple :

```
actions:
    - type: transform
      reqProperty: path
      op: replace
      match: \.html$
      replacement: ""
    - type: transform
      reqProperty: path
      op: tolower
```

### Variables {#variables}

Vous pouvez définir des variables pendant la transformation de la requête, puis les référencer ultérieurement dans la séquence d’évaluation. Voir le diagramme [ordre d’évaluation](#order-of-evaluation) pour plus de détails.

Exemple de configuration :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:
  requestTransformations:
    rules:
      - name: set-variable-rule
        when:
          reqProperty: path
          equals: /set-variable
        actions:
          - type: set
            var: some_var_name
            value: some_value

  responseTransformations:
    rules:
      - name: set-response-header-while-variable
        when:
          var: some_var_name
          equals: some_value
        actions:
          - type: set
            respHeader: x-some-header
            value: some header value
```

### Propriété de journal {#logproperty}

Vous pouvez ajouter vos propres propriétés de journal dans vos journaux CDN à l’aide de transformations de requête et de réponse.

Exemple de configuration :

```
requestTransformations:
  rules:
    - name: log-on-request
      when: "*"
      actions:
        - type: set
          logProperty: forwarded_host
          value:
            reqHeader: x-forwarded-host
responseTransformations:
  rules:
    - name: log-on-response
      when: '*'
      actions:
        - type: set
          logProperty: cache_control
          value:
            respHeader: cache-control
```

Exemple de journal :

```
{
"timestamp": "2025-03-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/content/hello.png",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 200,
"res_age": 0,
"pop": "PAR",
"rules": "",
"forwarded_host": "example.com",
"cache_control": "max-age=300"
}
```

## Transformations de réponse {#response-transformations}

Les règles de transformation de réponse vous permettent de définir et de dédéfinir des en-têtes, des cookies et le statut des réponses sortantes du réseau CDN. Consultez également l’exemple ci-dessus pour référencer une variable précédemment définie dans une règle de transformation de requête.

Exemple de configuration :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:
  responseTransformations:
    rules:
      - name: set-response-header-rule
        when:
          reqProperty: path
          like: /set-response-header
        actions:
          - type: set
            value: value-set-by-resp-rule
            respHeader: x-resp-header
      - name: unset-response-header-rule
        when:
          reqProperty: path
          like: /unset-response-header
        actions:
          - type: unset
            respHeader: x-header1
      - name: multi-action-response-header-rule
        when:
          reqProperty: path
          like: /multi-action-response-header
        actions:
          - type: set
            respHeader: x-resp-header-1
            value: value-set-by-resp-rule-1
          - type: set
            respHeader: x-resp-header-2
            value: value-set-by-resp-rule-2
      - name: status-code-rule
        when:
          reqProperty: path
          like: status-code
        actions:
          - type: set
            respProperty: status
            value: '410'
      - name: set-response-cookie-with-attributes-as-object
        when: '*'
        actions:
          - type: set
            respCookie: first-name
            value: first-value
            attributes:
              expires: '2025-08-29T10:00:00'
              domain: example.com
              path: /some-path
              secure: true
              httpOnly: true
              extension: ANYTHING
      - name: unset-response-cookie
        when: '*'
        actions:
          - type: unset
            respCookie: third-name
```

**Actions**

Les actions disponibles sont expliquées dans le tableau ci-dessous.

| Nom | Propriétés | Signification |
|-----------|--------------------------|-------------|
| **défini** | respProperty, valeur | Définit une propriété de réponse. Prend uniquement en charge la propriété « status » afin de définir le code d’état. |
|     | respHeader, valeur | Définit un en-tête de réponse spécifié sur une valeur donnée. |
|     | respCookie, attributs (expires, domain, path, secure, httpOnly, extension), valeur | Définit un cookie de requête spécifié avec des attributs spécifiques sur une valeur donnée. |
|     | logProperty, valeur | Définit une propriété de journal CDN spécifiée sur une valeur donnée. |
|     | var, valeur | Définit une variable spécifiée sur une valeur donnée. |
| **désactivé** | respHeader | Supprime un en-tête spécifié de la réponse. |
|     | respCookie, valeur | Supprime un cookie spécifié. |
|     | logProperty, valeur | Supprime une propriété de journal CDN spécifiée. |
|     | var | Supprime une variable spécifiée. |

## Sélecteurs d’origine {#origin-selectors}

Vous pouvez tirer parti du réseau CDN d’AEM pour acheminer le trafic vers différents serveurs principaux, y compris les applications non Adobe (par chemin d’accès ou sous-domaine, par exemple).

Exemple de configuration :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  originSelectors:
    rules:
      - name: example-com
        when: { reqProperty: path, like: /proxy* }
        action:
          type: selectOrigin
          originName: example-com
          # skipCache: true
          # headers:
          #   Authorization: ${{AUTH_TOKEN}}
    origins:
      - name: example-com
        domain: www.example.com
        # ip: '1.1.1.1'
        # forwardHost: true
        # forwardCookie: true
        # forwardAuthorization: true
        # timeout: 20
```

**Actions**

L’action disponible est expliquée dans le tableau ci-dessous.

| Nom | Propriétés | Signification |
|---------------------|--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **selectOrigin** | originName | Nom de l’une des origines définies. |
|                     | skipCache (facultatif, la valeur par défaut est false) | Indique s’il faut utiliser la mise en cache pour les requêtes correspondant à cette règle. Par défaut, les réponses sont mises en cache en fonction de l’en-tête de mise en cache des réponses (par exemple, Cache-Control ou Expires) |
|                     | en-têtes (facultatif, la valeur par défaut est `{}`) | Paires clé-valeur contenant des en-têtes HTTP supplémentaires à envoyer au serveur principal sélectionné lorsque la règle est déclenchée. Avec des clés correspondant aux noms des en-têtes et des valeurs correspondant aux valeurs des en-têtes |
| **selectAemOrigin** | originName | Nom de l’une des origines AEM prédéfinies (valeur prise en charge : `static`). |
|                     | skipCache (facultatif, la valeur par défaut est false) | Indique s’il faut utiliser la mise en cache pour les requêtes correspondant à cette règle. Par défaut, les réponses sont mises en cache en fonction de l’en-tête de mise en cache des réponses (par exemple, Cache-Control ou Expires) |
|                     | en-têtes (facultatif, la valeur par défaut est `{}`) | Paires clé-valeur contenant des en-têtes HTTP supplémentaires à envoyer au serveur principal sélectionné lorsque la règle est déclenchée. Avec des clés correspondant aux noms des en-têtes et des valeurs correspondant aux valeurs des en-têtes |

**Origines**

Les connexions aux origines sont SSL uniquement et utilisent le port 443.

| Propriété | Signification |
|------------------|--------------------------------------|
| **name** | Nom qui peut être référencé par « action.originName ». |
| **domaine** | Nom de domaine utilisé pour la connexion au serveur principal personnalisé. Il est également utilisé pour le SNI SSL et la validation. |
| **ip** (facultatif, compatible iv4 et ipv6) | Le cas échéant, il est utilisé pour se connecter au serveur principal au lieu du « domaine ». Toujours « domaine » est utilisé pour le SNI SSL et la validation. |
| **forwardHost** (facultatif, la valeur par défaut est false) | Si la valeur est définie sur true, l’en-tête « Host » de la requête client est transmis au serveur principal, sinon la valeur « domain » est transmise dans l’en-tête « Host ». |
| **forwardCookie** (facultatif, la valeur par défaut est false) | Si la valeur est définie sur true , l’en-tête « Cookie » de la requête client est transmis au serveur principal. Dans le cas contraire, l’en-tête Cookie est supprimé. |
| **forwardAuthorization** (facultatif, la valeur par défaut est false) | Si la valeur est définie sur true , l’en-tête « Authorization » de la requête client est transmis au serveur principal. Dans le cas contraire, l’en-tête d’autorisation est supprimé. |
| **timeout** (facultatif, en secondes, la valeur par défaut est de 60) | Nombre de secondes que le réseau CDN doit attendre pour qu’un serveur principal fournisse le premier octet d’un corps de réponse HTTP. Cette valeur est également utilisée comme délai d’expiration entre octets pour le serveur principal. |

### Proxy d’un domaine personnalisé vers le niveau statique AEM {#proxy-custom-domain-static}

Les sélecteurs d’origine peuvent être utilisés pour acheminer le trafic de publication AEM vers le contenu statique d’AEM déployé à l’aide du [pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md). Les cas d’utilisation incluent la diffusion de ressources statiques sur le même domaine que la page (par exemple, example.com/static) ou sur un domaine explicitement différent (par exemple, static.example.com).

Voici un exemple de règle de sélecteur d’origine qui peut accomplir cela :

```
kind: CDN
version: '1'
metadata:
  envTypes: ["dev"]
data:
  originSelectors:
    rules:
      - name: select-aem-static-origin
        when:
          reqProperty: domain
          equals: static.example.com
        action:
          type: selectAemOrigin
          originName: static
```

### Proxy vers Edge Delivery Services {#proxying-to-edge-delivery}

Il existe des scénarios où les sélecteurs d’origine doivent être utilisés pour acheminer le trafic via l’instance de publication AEM vers AEM Edge Delivery Services :

* Certains contenus sont diffusés par un domaine géré par l’instance de publication AEM, tandis que d’autres contenus du même domaine sont diffusés par Edge Delivery Services.
* Le contenu diffusé par Edge Delivery Services bénéficie des règles déployées via le pipeline de configuration, y compris les règles de filtrage du trafic ou les transformations de requête/réponse.
* Le pipeline de configuration Edge Delivery vous permet de configurer les paramètres du réseau CDN géré par Adobe en définissant des règles telles que `trafficFilters`, `originSelectors` et `redirects`. <!-- https://wiki.corp.adobe.com/pages/editpage.action?pageId=3610084282 -->

Voici un exemple de règle de sélecteur d’origine qui peut accomplir cela :

```
kind: CDN
version: '1'
metadata:
  envTypes: ["dev"]
data:
  originSelectors:
    rules:
      - name: select-edge-delivery-services-origin
        when:
          allOf:
            - reqProperty: tier
              equals: publish
            - reqProperty: domain
              equals: <Production Host>
            - reqProperty: path
              matches: "^(/scripts/.*|/styles/.*|/fonts/.*|/blocks/.*|/icons/.*|.*/media_.*|/favicon.ico)"
        action:
          type: selectOrigin
          originName: aem-live
    origins:
      - name: aem-live
        domain: main--repo--owner.aem.live
```

>[!NOTE]
>
>Étant donné que le réseau CDN géré par Adobe est utilisé, veillez à configurer l’invalidation des notifications push en mode **géré**, en suivant la documentation relative à l’[ des notifications push de Edge Delivery Services ](https://www.aem.live/docs/byo-dns#setup-push-invalidation).


## Redirections côté serveur {#server-side-redirectors}

Vous pouvez utiliser des règles de redirection côté client pour les redirections 301, 302 et autres redirections côté client similaires. Si une règle correspond, le réseau CDN répond avec une ligne d’état qui inclut le code d’état et le message (par exemple, HTTP/1.1 301 Moved Permanency), ainsi que l’ensemble d’en-têtes d’emplacement.

Les emplacements absolus et relatifs avec des valeurs fixes sont autorisés.

Notez que la taille cumulée du fichier de configuration, y compris les règles de filtrage du trafic, ne peut pas dépasser 100KB.

Exemple de configuration :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  redirects:
    rules:
      - name: redirect-absolute
        when: { reqProperty: path, equals: "/page.html" }
        action:
          type: redirect
          status: 301
          location: https://example.com/page
      - name: redirect-relative
        when: { reqProperty: path, equals: "/anotherpage.html" }
        action:
          type: redirect
          location: /anotherpage
```

| Nom | Propriétés | Signification |
|-----------|--------------------------|-------------|
| **redirection** | location | Valeur pour l’en-tête « Emplacement ». |
|     | Statut (facultatif, la valeur par défaut est 301) | Statut HTTP à utiliser dans le message de redirection, 301 par défaut, les valeurs autorisées sont : 301, 302, 303, 307, 308. |

Les emplacements d’une redirection peuvent être des littéraux de chaîne (par exemple, https://www.example.com/page) ou le résultat d’une propriété (par exemple, path) qui est éventuellement transformée, avec la syntaxe suivante :

```
redirects:
  rules:
    - name: country-code-redirect
      when: { reqProperty: path, like: "/" }
      action:
        type: redirect
        location:
          reqProperty: clientCountry
          transform:
            - op: replace
              match: '^(.*)$'
              replacement: 'https://www.example.com/\1/home'
            - op: tolower
    - name: www-redirect
      when: { reqProperty: domain, equals: "example.com" }
      action:
        type: redirect
        location:
          reqProperty: url
          transform:
            - op: replace
              match: '^/(.*)$'
              replacement: 'https://www.example.com/\1'
```
