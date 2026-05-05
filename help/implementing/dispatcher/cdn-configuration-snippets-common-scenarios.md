---
title: Fragments de code de configuration de réseau CDN pour les scénarios courants
description: Modèles YAML prêts pour la copie pour les configurations de réseau CDN géré par Adobe et de réseau CDN géré par le client, y compris l’authentification Edge, les redirections, la variation de cache, la mise en forme du trafic et les limites de débit.
feature: Dispatcher
role: Admin
source-git-commit: ab43facbd4c34c92878e303acf2fef9cc127e28a
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# Fragments de code de configuration de réseau CDN pour les scénarios courants {#cdn-configuration-snippets}

Cet article collecte des modèles de `cdn.yaml` pratiques pour AEM as a Cloud Service. Utilisez-les avec la documentation des fonctionnalités pour les [règles de trafic CDN](/help/implementing/dispatcher/cdn-configuring-traffic.md), [informations d’identification CDN gérées par le client](/help/implementing/dispatcher/cdn-credentials-authentication.md) et [règles de filtrage de trafic, y compris WAF](/help/security/traffic-filter-rules-including-waf.md). Déployez des fragments de code avec un pipeline Cloud Manager [config](/help/operations/config-pipeline.md).

>[!NOTE]
>
>Remplacez les noms d’hôte, les chemins, les plages d’adresses IP, les clés et les seuils par des valeurs correspondant à votre programme. Testez les modifications dans un environnement hors production avant de les promouvoir.

## Réseau CDN géré par le client {#customer-managed-cdn}

### Configuration de l’authentification par clé Edge pour certains domaines uniquement {#edge-auth-selected-hosts}

Problème : sur un [réseau CDN géré par le client](/help/implementing/dispatcher/cdn.md#point-to-point-cdn), vous devez appliquer l’authentification pour certains noms d’hôtes client, tandis que d’autres noms d’hôtes qui atteignent l’étape de publication doivent rester disponibles sans cet en-tête (par exemple, pendant le déploiement ou lorsqu’un seul domaine de marque se trouve derrière votre réseau CDN).

Solution : exigez une authentification `X-AEM-Edge-Key` uniquement lorsque le premier nom d’hôte de `X-Forwarded-Host` est égal à votre nom d’hôte cible (par exemple `example.com`). La règle utilise la propriété de requête `forwardedDomain` pour effectuer cette correspondance et exécute l’action `authenticate` sur votre authentificateur Edge. Remplacez les noms d’hôtes, les noms d’authentificateur et les espaces réservés des clés pour votre programme.

```yaml
kind: "CDN"
version: "1"
data:
  authentication:
    authenticators:
      - name: edge-key-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_1}}
        edgeKey2: ${{CDN_EDGEKEY_2}}
    rules:
      - name: edge-key-auth-rule
        when: { reqProperty: forwardedDomain, equals: "example.com" }
        action:
          type: authenticate
          authenticator: edge-key-auth
```

### Configuration de l’authentification par clé Edge pour les requêtes ne provenant pas des adresses IP VPN {#edge-auth-trusted-ips}

Problème : configurez l’authentification par clé Edge pour BYOCDN, mais autorisez l’accès direct au domaine de publication uniquement pour les adresses IP VPN

Solution : Exigez l’authentification X-AEM-Edge-Key uniquement lorsque l’adresse IP du client n’est pas dans la liste des adresses IP VPN

```yaml
kind: "CDN"
version: "1"
data:
  authentication:
    authenticators:
      - name: edge-key-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_1}}
        edgeKey2: ${{CDN_EDGEKEY_2}}
    rules:
      - name: edge-key-auth-rule
        when: { reqProperty: clientIp, notIn: ["10.0.0.1", "11.0.0.0/24", "<other VPN IPs>"] }
        action:
          type: authenticate
          authenticator: edge-key-auth
```

## Redirections {#redirects}

### Redirection du domaine APEX vers www {#apex-to-www}

```yaml
kind: "CDN"
version: "1"
data:
 redirects:
   rules:
     - name: non-www-to-www-redirect
       when:
         reqProperty: domain
         doesNotMatch: '^www\.'
       action:
         type: redirect
         status: 301
         location:
           join:
             format: 'https://www.%s%s'
             args:
               - reqProperty: domain
               - reqProperty: url
```

### Modification de la clé de cache {#cache-key}

Le réseau CDN n’expose pas de champ « clé de cache » distinct. Comme l’URL participe à la mise en cache, vous pouvez fractionner les entrées de cache en modifiant l’URL, par exemple en ajoutant un paramètre de requête par le biais d’une [&#x200B; transformation de requête](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations).

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: set-request-different-cache-curl
        when:
          allOf:
            - reqProperty: tier
              equals: publish
            - reqHeader: user-agent
              matches: curl
        actions:
          - type: set
            queryParam: cache
            value: 'curl'
```

### Redirection vers un chemin normalisé {#trailing-slash}

Envoyez une redirection permanente lorsqu’un navigateur demande une barre oblique de fin lors de la publication, par exemple de `https://www.example.com/path/` vers `https://www.example.com/path`.

```yaml
kind: "CDN"
version: "1"
data:
  redirects:
    rules:
      - name: remove-trailing-slash
        when:
          allOf:
            - reqProperty: tier
              equals: publish
            - reqProperty: domain
              equals: www.example.com
            - reqProperty: originalPath
              matches: ^/(.+)/$
        action:
          type: redirect
          status: 301
          location:
            reqProperty: originalPath
            transform:
              - op: replace
                match: ^/(.+)/$
                replacement: https://www.example.com/\1
```

### Extraction d’informations à partir d’un cookie JSON {#json-cookie}

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: options-response
        when: { reqProperty: tier, equals: publish }
        actions:
        - type: set
          reqHeader: x-mycookie-info
          value:
            reqCookie: mycookie
            transform: 
            - 'base64decode'
            - { op: 'replace', match: '"info":\s*"([^"]*)"', replacement: '\1'} 
```

## Configuration de l&#39;origine croisée {#cross-origin}

### Traitement des requêtes OPTIONS à partir du réseau CDN {#options-from-cdn}

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: options-response
        when:
          allOf: 
            - { reqProperty: path, like: /mypathi*  }
            - { reqProperty: method, equals: "OPTIONS" }
            - { reqHeader: Origin, equals: "https://example.com" }
        actions:
          - type: respond
            status: 200
            reason: "OK"
            headers:
              content-type: 'text/plain'
              access-control-allow-origin: { reqHeader: Origin }
              access-control-allow-methods: "*"
              access-control-allow-headers: "*"
```

## Filtres de trafic {#traffic-filters}

### ASN de limitation de débit {#rate-limit-asn}

Problème : les limites de débit par adresse IP peuvent ne pas correspondre à un modèle de déni de service distribué (DDoS) : chaque adresse reste inférieure au seuil, de sorte que le trafic légitime et abusif ressemble à la couche IP.

Solution : Comptez les requêtes par nom de système autonome (`clientAsName`) afin que le limiteur agrège les hôtes partageant le même nom de réseau. Le fragment de code écrit des `clientAsName` dans une propriété de journal pour chaque requête, puis applique une limite de taux à l’auteur et à la publication, regroupés selon cette valeur. De nombreux utilisateurs peuvent partager un seul réseau ASN (par exemple, un grand FAI ou une sortie VPN d’entreprise). Ajustez donc soigneusement les limites et surveillez les journaux CDN pour détecter les faux positifs.

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: log-on-request
        when: "*"
        actions:
          - type: set
            logProperty: client_as_name
            value:
              reqProperty: clientAsName
  trafficFilters:
    rules:
    - name: limit-requests-client-as-name
      when:
        reqProperty: tier
        matches: "author|publish"
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        count: all
        groupBy:
          - reqProperty: clientAsName
      action: block
```
