---
title: Configurer le trafic sur le réseau CDN
description: Découvrez comment configurer le trafic CDN en déclarant les règles et les filtres dans un fichier de configuration et en les déployant sur le CDN à l’aide du pipeline de configuration de Cloud Manager.
feature: Dispatcher
exl-id: e0b3dc34-170a-47ec-8607-d3b351a8658e
source-git-commit: 1e2d147aec53fc0f5be53571078ccebdda63c819
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configurer le trafic sur le réseau CDN {#cdn-configuring-cloud}

>[!NOTE]
>Cette fonctionnalité n’est pas encore disponible pour l’ensemble de la population. Pour rejoindre le programme d’adoption précoce, envoyez un email à `aemcs-cdn-config-adopter@adobe.com` et décrivez votre cas d’utilisation.

AEM as a Cloud Service propose un ensemble de fonctionnalités configurables dans la [Réseau de diffusion de contenu géré par Adobe](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) qui modifient la nature des requêtes entrantes ou des réponses sortantes. Les règles suivantes, décrites en détail dans cette page, peuvent être déclarées pour obtenir le comportement suivant :

* [Transformations de requêtes](#request-transformations) - modifier les aspects des requêtes entrantes, notamment les en-têtes, les chemins et les paramètres ;
* [Conversion des réponses](#response-transformations) : modifiez les en-têtes qui reviennent au client (par exemple, un navigateur web).
* [Redirecteurs côté client](#client-side-redirectors) : déclenche une redirection du navigateur.
* [Sélecteurs d’origine](#origin-selectors) - proxy vers un serveur principal d’origine différent.

Les règles de filtrage du trafic (dont le WAF), qui contrôlent le trafic autorisé ou refusé par le CDN, peuvent également être configurées sur le CDN. Cette fonctionnalité est déjà disponible et vous pouvez en savoir plus dans la section [Règles de filtre de trafic incluant des règles WAF](/help/security/traffic-filter-rules-including-waf.md) page.

En outre, si le réseau de diffusion de contenu ne peut pas contacter son origine, vous pouvez écrire une règle qui fait référence à une page d’erreur personnalisée auto-hébergée (qui est alors rendue). En savoir plus à ce sujet en lisant la section [Configuration des pages d’erreur CDN](/help/implementing/dispatcher/cdn-error-pages.md) article.

Toutes ces règles, déclarées dans un fichier de configuration dans le contrôle de code source, sont déployées à l’aide de [Pipeline de configuration de Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline). Gardez à l’esprit que la taille cumulée du fichier de configuration ne peut pas dépasser 100 Ko.

## Ordre d’évaluation {#order-of-evaluation}

Fonctionnellement, les différentes fonctionnalités mentionnées précédemment sont évaluées dans l’ordre suivant :

![image](/help/implementing/dispatcher/assets/order.png)

## Configuration {#initial-setup}

Avant de pouvoir configurer le trafic sur le réseau de diffusion de contenu, vous devez effectuer les opérations suivantes :

* Créez tout d’abord cette structure de dossiers et de fichiers dans le dossier de niveau supérieur de votre projet Git :

```
config/
     cdn.yaml
```

* Deuxièmement, le `cdn.yaml` Le fichier de configuration doit contenir à la fois des métadonnées et les règles décrites dans les exemples ci-dessous.

## Syntaxe {#configuration-syntax}

Les types de règle dans les sections ci-dessous partagent une syntaxe commune.

Une règle est référencée par un nom, une &quot;clause de condition&quot; et des actions.

La clause when détermine si une règle sera évaluée, en fonction de propriétés telles que le domaine, le chemin, les chaînes de requête, les en-têtes et les cookies. La syntaxe est la même pour tous les types de règle. Pour plus d’informations, voir la section [Section Structure de condition](/help/security/traffic-filter-rules-including-waf.md#condition-structure) dans l’article Règles de filtrage du trafic .

Les détails du noeud actions diffèrent par type de règle et sont décrits dans les sections individuelles ci-dessous.

## Demander des transformations {#request-transformations}

Les règles de transformation de requêtes vous permettent de modifier les requêtes entrantes. Les règles prennent en charge les chemins d’accès, paramètres de requête et en-têtes (y compris les cookies) de définition, de dédéfinition et de modification en fonction de diverses conditions de correspondance, y compris des expressions régulières. Vous pouvez également définir des variables qui pourront être référencées ultérieurement dans la séquence d’évaluation.

Les cas d’utilisation sont variés et incluent des réécritures d’URL pour simplifier l’application ou mapper les URL héritées.

Comme nous l’avons mentionné plus haut, le fichier de configuration est limité en termes de taille, de sorte que les organisations ayant des exigences plus importantes doivent définir des règles dans la variable `apache/dispatcher` calque.

Exemple de configuration :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
data:  
  experimental_requestTransformations:
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
| **set** | (reqProperty ou reqHeader ou queryParam ou reqCookie), value | Définit un paramètre de requête spécifié (seule la propriété &quot;path&quot; est prise en charge), ou un en-tête de requête, un paramètre de requête ou un cookie, sur une valeur donnée. |
|     | var, value | Définit une propriété de requête spécifiée sur une valeur donnée. |
| **unset** | reqProperty | Supprime un paramètre de requête spécifié (seule la propriété &quot;path&quot; est prise en charge), ou un en-tête de requête, un paramètre de requête ou un cookie, à une valeur donnée. |
|         | var | Supprime une variable spécifiée. |
|         | queryParamMatch | Supprime tous les paramètres de requête correspondant à une expression régulière spécifiée. |
| **transform** | op:replace, (reqProperty ou reqHeader ou queryParam ou reqCookie), match, remplacement | Remplace une partie du paramètre de requête (seule la propriété &quot;path&quot; est prise en charge) ou l’en-tête de requête, le paramètre de requête ou le cookie de requête par une nouvelle valeur. |
|              | op:tolower, (reqProperty ou reqHeader ou queryParam ou reqCookie) | Définit le paramètre de requête (seule la propriété &quot;path&quot; est prise en charge) ou l’en-tête de requête, le paramètre de requête ou le cookie de requête sur sa valeur en minuscules. |

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

Vous pouvez définir des variables pendant la transformation de requête, puis les référencer ultérieurement dans la séquence d’évaluation. Voir [ordre d’évaluation](#order-of-evaluation) pour plus de détails.

Exemple de configuration :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:   
  experimental_requestTransformations:
    rules:
      - name: set-variable-rule
        when:
          reqProperty: path
          equals: /set-variable
        actions:
          - type: set
            var: some_var_name
            value: some_value
 
  experimental_responseTransformations:
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
  experimental_responseTransformations:
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
  experimental_originSelectors:
    rules:
      - name: example-com
        when: { reqProperty: path, like: /proxy-me* }
        action:
          type: selectOrigin
          originName: example-com
          # useCache: false
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
|     | useCache (facultatif, la valeur par défaut est true) | Indiquez si la mise en cache doit être utilisée pour les requêtes correspondant à cette règle. |

**Origines**

Les connexions aux origines sont uniquement SSL et utilisent le port 443.

| Propriété | Signification |
|------------------|--------------------------------------|
| **name** | Nom pouvant être référencé par &quot;action.originName&quot;. |
| **domain** | Nom de domaine utilisé pour se connecter au serveur principal personnalisé. Il est également utilisé pour l’interface SNI SSL et la validation. |
| **ip** (facultatif, iv4 et ipv6 pris en charge) | S’il est fourni, il est utilisé pour se connecter au serveur principal au lieu de &quot;domaine&quot;. Toujours &quot;domain&quot; est utilisé pour l’interface SNI SSL et la validation. |
| **forwardHost** (facultatif, la valeur par défaut est false) | Si la valeur est définie sur true, l’en-tête &quot;Host&quot; de la requête client est transmis au serveur principal, sinon la valeur &quot;domain&quot; est transmise dans l’en-tête &quot;Host&quot;. |
| **forwardCookie** (facultatif, la valeur par défaut est false) | S’il est défini sur true, l’en-tête &quot;Cookie&quot; de la requête client est transmis au serveur principal, sinon l’en-tête du cookie est supprimé. |
| **forwardAuthorization** (facultatif, la valeur par défaut est false) | S’il est défini sur true, l’en-tête &quot;Authorization&quot; de la requête client est transmis au serveur principal, sinon l’en-tête Authorization est supprimé. |
| **timeout** (facultatif, en secondes, la valeur par défaut est de 60) | Nombre de secondes pendant lesquelles le CDN doit attendre qu’un serveur principal diffuse le premier octet d’un corps de réponse HTTP. Cette valeur est également utilisée comme délai d’expiration entre les octets pour le serveur principal. |

## Redirecteurs côté client {#client-side-redirectors}

Vous pouvez utiliser des règles de redirection côté client pour les redirections 301, 302 et les redirections côté client similaires. Si une règle correspond, le CDN répond avec une ligne d’état qui inclut le code d’état et le message (par exemple, HTTP/1.1 301 Déplacé définitivement), ainsi que le jeu d’en-têtes d’emplacement.

Les emplacements absolus et relatifs avec des valeurs fixes sont autorisés.

Exemple de configuration :

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_redirects:
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
| **rediriger** | location | Valeur de l’en-tête &quot;Emplacement&quot;. |
|     | status (facultatif, 301 par défaut) | Statut HTTP à utiliser dans le message de redirection, 301 par défaut, les valeurs autorisées sont : 301, 302, 303, 307, 308. |
