---
title: Configurer le trafic sur le réseau CDN
description: Découvrez comment configurer le trafic CDN en déclarant les règles et les filtres dans un fichier de configuration et en les déployant sur le CDN à l’aide d’un pipeline de configuration Cloud Manager.
feature: Dispatcher
exl-id: e0b3dc34-170a-47ec-8607-d3b351a8658e
role: Admin
source-git-commit: e5e0606c83f144f92f9ae57e5380a30389e8df1b
workflow-type: tm+mt
source-wordcount: '1351'
ht-degree: 2%

---


# Configurer le trafic sur le réseau CDN {#cdn-configuring-cloud}

AEM as a Cloud Service propose un ensemble de fonctionnalités configurables au niveau de la couche [CDN gérée par Adobe](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) qui modifient la nature des requêtes entrantes ou des réponses sortantes. Les règles suivantes, décrites en détail dans cette page, peuvent être déclarées pour obtenir le comportement suivant :

* [Transformations de requêtes](#request-transformations) : modifiez les aspects des requêtes entrantes, y compris les en-têtes, les chemins et les paramètres.
* [transformations de réponse](#response-transformations) - modifiez les en-têtes qui reviennent au client (par exemple, un navigateur web).
* [Redirections côté client](#client-side-redirectors) - déclenchez une redirection du navigateur.
* [Sélecteurs d’origine](#origin-selectors) - proxy vers un autre serveur principal d’origine.

Sur le réseau de diffusion de contenu, vous pouvez également configurer des règles de filtrage du trafic (y compris WAF) qui contrôlent le trafic autorisé ou refusé par le réseau de diffusion de contenu. Cette fonctionnalité est déjà disponible et vous pouvez en savoir plus à ce sujet sur la page [Règles de filtrage du trafic incluant les règles WAF](/help/security/traffic-filter-rules-including-waf.md) .

En outre, si le réseau de diffusion de contenu ne peut pas contacter son origine, vous pouvez écrire une règle qui fait référence à une page d’erreur personnalisée auto-hébergée (qui est alors rendue). Pour en savoir plus à ce sujet, consultez l’article [Configuration des pages d’erreur CDN](/help/implementing/dispatcher/cdn-error-pages.md) .

Toutes ces règles, déclarées dans un fichier de configuration dans le contrôle de code source, sont déployées à l’aide du pipeline de configuration Cloud Manager [config .](/help/operations/config-pipeline.md) Gardez à l’esprit que la taille cumulée du fichier de configuration, y compris les règles de filtrage du trafic, ne peut pas dépasser 100 Ko.

## Ordre d’évaluation {#order-of-evaluation}

Fonctionnellement, les différentes fonctionnalités mentionnées précédemment sont évaluées dans l’ordre suivant :

![Ordre d’évaluation](/help/implementing/dispatcher/assets/order.png)

## Configuration {#initial-setup}

Avant de pouvoir configurer le trafic sur le réseau de diffusion de contenu, vous devez effectuer les opérations suivantes :

1. Créez un fichier nommé `cdn.yaml` ou similaire, référençant les différents fragments de code de configuration dans les sections ci-dessous.

   Tous les fragments de code possèdent ces propriétés communes, décrites sous [Config Pipeline](/help/operations/config-pipeline.md#common-syntax). La valeur de la propriété `kind` doit être *CDN* et la propriété `version` doit être définie sur *1*.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   ```

1. Placez le fichier quelque part sous un dossier de niveau supérieur nommé *config* ou similaire, comme décrit sous [Config Pipeline](/help/operations/config-pipeline.md#folder-structure).

1. Créez un pipeline de configuration dans Cloud Manager, comme décrit sous [Config Pipeline](/help/operations/config-pipeline.md#managing-in-cloud-manager).

1. Déployez la configuration.

## Syntaxe des règles {#configuration-syntax}

Les types de règle dans les sections ci-dessous partagent une syntaxe commune.

Une règle est référencée par un nom, une &quot;clause de condition&quot; et des actions.

La clause when détermine si une règle sera évaluée, en fonction de propriétés telles que le domaine, le chemin, les chaînes de requête, les en-têtes et les cookies. La syntaxe est la même pour tous les types de règles. Pour plus d’informations, reportez-vous à la [section Structure de condition](/help/security/traffic-filter-rules-including-waf.md#condition-structure) de l’article Règles de filtrage du trafic .

Les détails du noeud actions diffèrent par type de règle et sont décrits dans les sections individuelles ci-dessous.

## Demander des transformations {#request-transformations}

Les règles de transformation de requêtes vous permettent de modifier les requêtes entrantes. Les règles prennent en charge les chemins d’accès, paramètres de requête et en-têtes (y compris les cookies) de définition, de dédéfinition et de modification en fonction de diverses conditions de correspondance, y compris des expressions régulières. Vous pouvez également définir des variables qui pourront être référencées ultérieurement dans la séquence d’évaluation.

Les cas d’utilisation sont variés et incluent des réécritures d’URL pour simplifier l’application ou mapper les URL héritées.

Comme mentionné précédemment, il existe une limite de taille au fichier de configuration, de sorte que les organisations ayant des exigences plus importantes doivent définir des règles dans la couche `apache/dispatcher`.

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
```

**Actions**

Les actions disponibles sont expliquées dans le tableau ci-dessous.

| Nom | Propriétés | Signification |
|-----------|--------------------------|-------------|
| **set** | (reqProperty ou reqHeader ou queryParam ou reqCookie), value | Définit un paramètre de requête spécifié (seule la propriété &quot;path&quot; est prise en charge), ou un en-tête de requête, un paramètre de requête ou un cookie, sur une valeur donnée, qui peut être un littéral de chaîne ou un paramètre de requête. |
|     | var, value | Définit une propriété de requête spécifiée sur une valeur donnée. |
| **unset** | reqProperty | Supprime un paramètre de requête spécifié (seule la propriété &quot;path&quot; est prise en charge), ou un en-tête de requête, un paramètre de requête ou un cookie, à une valeur donnée, qui peut être un littéral de chaîne ou un paramètre de requête. |
|         | var | Supprime une variable spécifiée. |
|         | queryParamMatch | Supprime tous les paramètres de requête correspondant à une expression régulière spécifiée. |
| **transform** | op:replace, (reqProperty ou reqHeader ou queryParam ou reqCookie ou var), match, remplacement | Remplace une partie du paramètre de requête (seule la propriété &quot;path&quot; est prise en charge), ou l’en-tête de requête, le paramètre de requête, le cookie ou la variable par une nouvelle valeur. |
|              | op:tolower, (reqProperty ou reqHeader ou queryParam ou reqCookie ou var) | Définit le paramètre de requête (seule la propriété &quot;path&quot; est prise en charge), l’en-tête de requête, le paramètre de requête, le cookie ou la variable sur sa valeur en minuscules. |

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

Les actions peuvent être liées ensemble. Par exemple :

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

Vous pouvez définir des variables pendant la transformation de requête, puis les référencer ultérieurement dans la séquence d’évaluation. Pour plus d’informations, consultez le diagramme [ordre d’évaluation](#order-of-evaluation) .

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

## Transformations de réponse {#response-transformations}

Les règles de transformation de réponse vous permettent de définir et de désinitialiser des en-têtes des réponses sortantes du CDN. Consultez également l’exemple ci-dessus pour référencer une variable précédemment définie dans une règle de transformation de requête.

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

      # Example: Multi-action on response header
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
```

**Actions**

Les actions disponibles sont expliquées dans le tableau ci-dessous.

| Nom | Propriétés | Signification |
|-----------|--------------------------|-------------|
| **set** | reqHeader, valeur | Définit un en-tête spécifié sur une valeur donnée dans la réponse. |
| **unset** | respHeader | Supprime un en-tête spécifié de la réponse. |

## Sélecteurs d’origine {#origin-selectors}

Vous pouvez utiliser le réseau de diffusion de contenu AEM pour acheminer le trafic vers différents serveurs principaux, y compris les applications non Adobes (par chemin ou sous-domaine, par exemple).

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
|-----------|--------------------------|-------------|
| **selectOrigin** | originName | Nom de l’une des origines définies. |
|     | skipCache (facultatif, la valeur par défaut est false) | Indiquez si la mise en cache doit être utilisée pour les requêtes correspondant à cette règle. Par défaut, les réponses seront mises en cache en fonction de l’en-tête de mise en cache de la réponse (par exemple, Cache-Control ou Expires). |

**Origines**

Les connexions aux origines sont uniquement SSL et utilisent le port 443.

| Propriété | Signification |
|------------------|--------------------------------------|
| **name** | Nom pouvant être référencé par &quot;action.originName&quot;. |
| **domain** | Nom de domaine utilisé pour se connecter au serveur principal personnalisé. Il est également utilisé pour l’interface SNI SSL et la validation. |
| **ip** (facultatif, pris en charge iv4 et ipv6) | S’il est fourni, il est utilisé pour se connecter au serveur principal au lieu de &quot;domaine&quot;. Toujours &quot;domain&quot; est utilisé pour l’interface SNI SSL et la validation. |
| **forwardHost** (facultatif, la valeur par défaut est false) | Si la valeur est définie sur true, l’en-tête &quot;Host&quot; de la requête client est transmis au serveur principal, sinon la valeur &quot;domain&quot; est transmise dans l’en-tête &quot;Host&quot;. |
| **forwardCookie** (facultatif, la valeur par défaut est false) | S’il est défini sur true, l’en-tête &quot;Cookie&quot; de la requête client est transmis au serveur principal, sinon l’en-tête du cookie est supprimé. |
| **forwardAuthorization** (facultatif, la valeur par défaut est false) | S’il est défini sur true, l’en-tête &quot;Authorization&quot; de la requête client est transmis au serveur principal, sinon l’en-tête Authorization est supprimé. |
| **timeout** (facultatif, en secondes, la valeur par défaut est 60) | Nombre de secondes pendant lesquelles le CDN doit attendre qu’un serveur principal diffuse le premier octet d’un corps de réponse HTTP. Cette valeur est également utilisée comme délai d’expiration entre les octets pour le serveur principal. |

### Proxys vers les Edge Delivery Services {#proxying-to-edge-delivery}

Dans certains cas, des sélecteurs d’origine doivent être utilisés pour acheminer le trafic AEM Publish vers AEM Edge Delivery Services :

* Certains contenus sont diffusés par un domaine géré par AEM Publish, tandis que d’autres du même domaine le sont par des Edge Delivery Services.
* Le contenu diffusé par les Edge Delivery Services bénéficierait des règles déployées via le pipeline de configuration, y compris les règles de filtrage du trafic ou les transformations de requête/réponse.

Voici un exemple de règle de sélecteur d’origine qui peut accomplir ceci :

```
kind: CDN
version: '1'
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
> Puisque le réseau de diffusion de contenu géré par l’Adobe est utilisé, veillez à configurer l’invalidation push en mode **managed** , en suivant la [documentation sur la configuration de l’invalidation push](https://www.aem.live/docs/byo-dns#setup-push-invalidation) des Edge Delivery Services.


## Redirections côté client {#client-side-redirectors}

Vous pouvez utiliser des règles de redirection côté client pour les redirections 301, 302 et les redirections côté client similaires. Si une règle correspond, le CDN répond avec une ligne d’état qui inclut le code d’état et le message (par exemple, HTTP/1.1 301 Déplacé définitivement), ainsi que le jeu d’en-têtes d’emplacement.

Les emplacements absolus et relatifs avec des valeurs fixes sont autorisés.

Gardez à l’esprit que la taille cumulée du fichier de configuration, y compris les règles de filtrage du trafic, ne peut pas dépasser 100 Ko.

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
| **redirect** | location | Valeur de l’en-tête &quot;Emplacement&quot;. |
|     | status (facultatif, 301 par défaut) | Statut HTTP à utiliser dans le message de redirection, 301 par défaut, les valeurs autorisées sont : 301, 302, 303, 307, 308. |

Les emplacements d’une redirection peuvent être soit des littéraux de chaîne (par exemple, https://www.example.com/page), soit le résultat d’une propriété (par exemple, un chemin) qui est éventuellement transformée, avec la syntaxe suivante :

```
experimental_redirects:
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
          reqProperty: path
          transform:
            - op: replace
              match: '^/(.*)$'
              replacement: 'https://www.example.com/\1'
```
