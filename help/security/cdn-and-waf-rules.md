---
title: Configuration des règles de filtre de trafic (avec des règles WAF)
description: Utilisation de règles de filtrage du trafic (avec des règles WAF) pour filtrer le trafic
source-git-commit: dc0c7e77bb4bc5423040364202ecac3c59adced0
workflow-type: tm+mt
source-wordcount: '2690'
ht-degree: 2%

---


# Configuration des règles de filtrage du trafic (avec des règles WAF) pour filtrer le trafic {#configuring-cdn-and-waf-rules-to-filter-traffic}

>[!NOTE]
>
>Cette fonctionnalité n’est pas encore disponible pour l’ensemble de la population. Pour rejoindre le programme d’adoption précoce en cours, envoyez un courrier électronique à l’adresse **aemcs-waf-adopter@adobe.com**, notamment le nom de votre organisation et le contexte de votre intérêt pour la fonctionnalité.

Adobe tente d’atténuer les attaques contre les sites web des clients, mais il peut s’avérer utile de filtrer de manière proactive le trafic correspondant à certains modèles afin que le trafic malveillant ne parvienne pas à votre application. Les approches possibles sont les suivantes :

* Modules de calque Apache tels que `mod_security`
* Configuration des règles de filtrage du trafic déployées sur le réseau de diffusion de contenu via le pipeline de configuration de Cloud Manager

Cet article décrit l’approche des règles de filtrage du trafic. La plupart de ces règles bloquent ou autorisent les requêtes en fonction des propriétés de requête et des en-têtes de requête, y compris l’adresse IP, les chemins et l’agent utilisateur. Ces règles peuvent être configurées par tous les clients as a Cloud Service de Sites et Forms AEM.

Les clients qui disposent d’une licence pour le module complémentaire WAF (Web Application Firewall) peuvent également configurer une catégorie supplémentaire de règles appelée &quot;règles de filtrage du trafic WAF&quot; (ou règles WAF, en abrégé). Ces règles WAF bloquent les demandes correspondant à différents modèles connus pour être associés à un trafic malveillant. Contactez votre équipe de compte d’Adobe pour plus d’informations sur les licences de cette fonctionnalité à venir. Notez qu’aucune licence supplémentaire n’est requise lors du programme des premiers adopteurs.

Les règles de filtrage du trafic peuvent être déployées sur tous les types d’environnements cloud (RDE, dev, stage, prod) dans les programmes de production (non sandbox).

## Configuration {#setup}

1. Créez tout d’abord la structure de dossiers et de fichiers suivante dans le dossier de niveau supérieur dans Git :

   ```
   config/
        cdn/
           cdn.yaml
   ```

1. `cdn.yaml` doit contenir des métadonnées ainsi qu’une liste de règles de filtres de trafic et de règles WAF.

   ```
   kind: "CDN"
   version: "1"
   envType: "dev"
   data:
     trafficFilters:
       rules:
         ...
   ```

Le paramètre &quot;type&quot; doit être défini sur &quot;CDN&quot; et la version doit être définie sur la version du schéma, qui est actuellement &quot;1&quot;. Voir les exemples ci-dessous.


<!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (e.g., "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. Pour configurer les règles WAF, elles doivent être activées dans Cloud Manager, comme décrit ci-dessous pour les scénarios de programme nouveaux et existants. Notez qu’une licence distincte doit être achetée pour WAF.

   1. Pour configurer la fonction WAF sur un nouveau programme, cochez la case **Protection WAF-DDOS** dans la variable **Sécurité** comme illustré ci-dessous. Suivez ensuite les étapes décrites dans la section [Ajout d’un programme de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) pour créer votre programme

   1. Pour configurer le WAF sur un programme existant, sélectionnez l’option **Modifier le programme** en suivant les étapes décrites dans la section [Modification de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) la documentation. Ensuite, dans la variable **Sécurité** de l’assistant, vous pouvez décocher ou cocher l’option WAF-DDOS à tout moment.

1. Pour les types d’environnements autres que RDE, exécutez le pipeline de configuration de Cloud Manager, qui peut être configuré comme décrit ci-dessous.

   1. Dans la carte de pipeline de votre page d’accueil de Cloud Manager, sélectionnez **Ajout d’un pipeline de production** ou **Ajout d’un pipeline hors production** pour lancer l’assistant d’ajout de pipeline
   1. Sélectionner **Pipeline de déploiement** dans l’onglet configuration

      ![Sélection de l’option Pipeline de déploiement](/help/security/assets/deployment.png)

   1. Attribuez un nom à votre pipeline et sélectionnez des déclencheurs de déploiement, puis sélectionnez **Continuer**
   1. Dans le **Code source** onglet, sélectionnez **Déploiement ciblé**, puis sélectionnez **Config**

      ![Sélectionner le déploiement ciblé](/help/security/assets/target-deployment.png)

   1. Sélectionnez le référentiel et la branche selon les besoins. S’il existe un pipeline de configuration pour l’environnement sélectionné, cette sélection est désactivée.

      ![Présentation d’un pipeline de configuration](/help/security/assets/config-pipeline.png)

      >[!NOTE]
      >
      > Les utilisateurs doivent être connectés en tant que Deployment Manager pour configurer ou exécuter ces pipelines.
      > Vous pouvez également configurer et exécuter un seul pipeline de configuration par environnement.

   1. Sélectionnez **Enregistrer**. Votre nouveau pipeline s’affiche dans la carte du pipeline et peut être exécuté lorsque vous êtes prêt.
   1. Pour les RDE, la ligne de commande sera utilisée, mais RDE n’est pas pris en charge pour le moment.

## Syntaxe des règles de filtre de trafic {#rules-syntax}

Vous pouvez configurer `traffic filter rules` pour établir une correspondance sur des modèles tels que les adresses IP, l’agent utilisateur, les en-têtes de requête, le nom d’hôte, la zone géographique et l’URL.

Les clients qui accordent une licence à l’offre WAF peuvent également configurer une catégorie spéciale de règles de filtrage du trafic appelée `WAF traffic filter rules` (ou règles WAF pour abréger) qui font référence à un ou plusieurs indicateurs WAF, répertoriés dans sa propre section ci-dessous.

Voici un exemple d’un ensemble de règles de filtrage du trafic, qui incluent également une règle WAF.

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action: 
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

Le format des règles de filtrage du trafic dans le fichier cdn.yaml est décrit ci-dessous. Consultez quelques exemples dans une section ultérieure.


| **Propriété** | **La plupart des règles de filtrage de trafic** | **Règles de filtre de trafic WAF** | **Type** | **Valeur par défaut** | **Description** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Nom de règle (64 caractères, ne peut contenir que des caractères alphanumériques et - ) |
| when | X | X | `Condition` | - | La structure de base est la suivante :<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>Voir la syntaxe de structure de condition ci-dessous, qui décrit les getters, les prédicats et comment combiner plusieurs conditions. |
| action | X | X | `Action` | log | log, allow, block, log ou action object La valeur par défaut est log |
| rateLimit | X |   | `RateLimit` | non défini | Configuration de limitation de débit. La limitation de débit est désactivée si elle n’est pas définie.<br><br>Vous trouverez ci-dessous une section distincte décrivant la syntaxe rateLimit, ainsi que des exemples. |

### Structure de condition {#condition-structure}

Une condition peut être soit une simple condition, soit un groupe de conditions.

**Condition simple**

Une condition simple est composée d’un getter et d’un prédicat.

```
{ <getter>: <value>, <predicate>: <value> }
```

**Conditions du groupe**

Un groupe de conditions est composé de plusieurs conditions simples et/ou de groupe.

```
<allOf|anyOf>:
  - { <getter>: <value>, <predicate>: <value> }
  - { <getter>: <value>, <predicate>: <value> }
  - <allOf|anyOf>:
    - { <getter>: <value>, <predicate>: <value> }
```

| **Propriété** | **Type** | **Signification** |
|---|---|---|
| **allOf** | `array[Condition]` | **et** opération. true si toutes les conditions répertoriées renvoient true |
| **anyOf** | `array[Condition]` | **ou** opération. true si l’une des conditions répertoriées renvoie true (vrai) |

**Getter**

| **Propriété** | **Type** | **Description** |
|---|---|---|
| reqProperty | `string` | Propriété de requête.<br><br>L’une des : `path` , `queryString`, `method`, `tier`, `domain`, `clientIp`, `clientCountry`<br><br>La propriété domain correspond à une transformation en minuscules de l’en-tête hôte de la requête. Elle est utile pour les comparaisons de chaînes, de sorte que les correspondances ne soient pas omises en raison du respect de la casse.<br><br>La variable `clientCountry` utilise deux codes à lettres affichés à l’adresse [https://en.wikipedia.org/wiki/Regional_indicator_symbol](https://en.wikipedia.org/wiki/Regional_indicator_symbol) |
| reqHeader | `string` | Renvoie l’en-tête de requête avec le nom spécifié |
| queryParam | `string` | Renvoie le paramètre de requête avec le nom spécifié |
| cookie | `string` | Renvoie le cookie avec le nom spécifié |

**Prédicat**

| **Propriété** | **Type** | **Signification** |
|---|---|---|
| **est égal à** | `string` | true si le résultat getter est égal à la valeur fournie |
| **doesNotEqual** | `string` | true si le résultat getter n’est pas égal à la valeur fournie |
| **j’aime** | `string` | true si le résultat getter correspond au modèle fourni |
| **notLike** | `string` | true si le résultat getter ne correspond pas au modèle fourni |
| **correspond à** | `string` | true si le résultat getter correspond à l’expression régulière fournie |
| **doesNotMatch** | `string` | true si le résultat getter ne correspond pas à l’expression régulière fournie |
| **dans** | `array[string]` | true si la liste fournie contient le résultat getter |
| **notIn** | `array[string]` | true si la liste fournie ne contient pas le résultat getter |

### Structure d’action {#action-structure}

Spécifié par `action` qui peut être soit une chaîne spécifiant le type d’action (autoriser, bloquer, consigner) et prenant des valeurs par défaut pour toutes les autres options, soit un objet pour lequel le type de règle est défini via `type` champ obligatoire avec d’autres options applicables à ce type.

**Types d’actions**

Les actions sont classées par ordre de priorité en fonction de leurs types dans le tableau suivant, dans l’ordre d’exécution des actions :

| **Nom** | **Propriétés autorisées** | **Signification** |
|---|---|---|
| **autoriser** | `wafFlags` (facultatif) | si wafFlags n’est pas présent, arrête le traitement des règles et passe à la réponse de diffusion. Si wafFlags est présent, il désactive les protections WAF spécifiées et poursuit le traitement des règles plus poussé. |
| **block** | `status, wafFlags` (facultatif et mutuellement exclusif) | si wafFlags n’est pas présent, renvoie une erreur HTTP en contournant toutes les autres propriétés, le code d’erreur est défini par la propriété status ou la valeur par défaut 406. Si wafFlags est présent, il active les protections WAF spécifiées et poursuit le traitement des règles plus poussé. |
| **log** | `wafFlags` (facultatif) | consigne le fait que la règle a été déclenchée, sinon n’affecte pas le traitement. wafFlags n’a aucun effet |

### Liste des indicateurs WAF {#waf-flags-list}

La variable `wafFlag` peut contenir les éléments suivants :

| **Identifiant d’indicateur** | **Nom de l’indicateur** | **Description** |
|---|---|---|
| SQLI | Injection SQL | SQL Injection est une tentative d’accès à une application ou d’obtention d’informations privilégiées en exécutant des requêtes de base de données arbitraires. |
| ARRIÈRE-PLAN | backdoor | Un signal backdoor est une requête qui tente de déterminer si un fichier backdoor commun est présent sur le système. |
| CMDEXE | Exécution de commande | L’exécution de commande est une tentative de contrôle ou d’endommagement d’un système cible par le biais de commandes système arbitraires par le biais d’entrées utilisateur. |
| XSS | Scripts intersites | Les scripts intersites consistent à tenter de détourner un compte d’utilisateur ou une session de navigation Web par le biais d’un code JavaScript malveillant. |
| TRAVERSAL | Directory Traversal | Directory Traversal est une tentative de navigation dans des dossiers privilégiés à travers un système dans l’espoir d’obtenir des informations sensibles. |
| USERAGENT | Outils d’attaque | L’outil d’attaque est l’utilisation de logiciels automatisés pour identifier des vulnérabilités de sécurité ou pour tenter d’exploiter une vulnérabilité découverte. |
| LOG4J-JNDI | JNDI Log4J | Les attaques JNDI de Log4J tentent d’exploiter la variable [Vulnérabilité de Log4Shell](https://en.wikipedia.org/wiki/Log4Shell) présente dans les versions de Log4J antérieures à la version 2.16.0 |
| AWS SSRF | AWS-SSRF | SSRF (Server Side Request Forgery) est une requête qui tente d’envoyer des requêtes effectuées par l’application web pour cibler les systèmes internes. Les attaques SSRF AWS utilisent SSRF pour obtenir les clés Amazon Web Services (AWS) et accéder aux compartiments S3 et à leurs données. |
| BHH | En-têtes de saut inappropriés | Les en-têtes de saut incorrects indiquent une tentative de contrebande HTTP via un en-tête de transcodage (TE) ou de longueur de contenu (CL) mal formé, ou un en-tête de TE et de CL bien formé. |
| ABNORMALPATH | Chemin anormal | Chemin anormal indique que le chemin d’origine diffère du chemin normalisé (par exemple, `/foo/./bar` est normalisé en `/foo/bar`) |
| COMPRESSÉ | Compression détectée | Le corps de la requête du POST est compressé et ne peut pas être inspecté. Par exemple, si un en-tête de requête &quot;Content-Encoding: gzip&quot; est spécifié et que le corps du POST ne contient pas de texte brut. |
| DOUBLEENCODING | Codage double | Le codage double vérifie la technique d’évasion du double encodage des caractères HTML. |
| NAVIGATION FORCEFULBROWSING | Navigation forcée | La navigation forcée est la tentative d’accès aux pages d’administration qui a échoué. |
| NOTUTF8 | Codage non valide | Un encodage non valide peut entraîner la traduction par le serveur de caractères malveillants d’une requête dans une réponse, provoquant un déni de service ou un XSS. |
| JSON-ERROR | Erreur de codage JSON | Corps de requête de POST, de PUT ou de PATCH spécifié comme contenant JSON dans l’en-tête de requête &quot;Content-Type&quot;, mais contenant des erreurs d’analyse JSON. Cela est souvent lié à une erreur de programmation ou à une requête automatisée ou malveillante. |
| MALFORMED-DATA | Données incorrectes dans le corps de la requête | Corps de requête de POST, de PUT ou de PATCH incorrect selon l’en-tête de requête &quot;Content-Type&quot;. Par exemple, si un en-tête de requête &quot;Content-Type: application/x-www-form-urlencoded&quot; est spécifié et contient un corps de POST qui est json. Il s’agit souvent d’une erreur de programmation, d’une requête automatisée ou malveillante. Nécessite l’agent 3.2 ou version ultérieure. |
| SANS | Trafic IP malveillant | [Centre des tempêtes sur Internet SANS](https://isc.sans.edu/) liste des adresses IP qui ont été signalées comme ayant participé à une activité malveillante |
| SIGSCI-IP | Effet réseau | IP marquée par SignalSciences : chaque fois qu’une adresse IP est marquée en raison d’un signal malveillant du moteur de décision, cette adresse IP est propagée à tous les clients. Les demandes suivantes provenant de ces adresses IP qui contiennent un signal supplémentaire pour la durée de l’indicateur sont ensuite consignées. |
| NO-CONTENT-TYPE | En-tête de requête &quot;Content-Type&quot; manquant | Requête de POST, de PUT ou de PATCH ne comportant pas d’en-tête de requête &quot;Content-Type&quot;. Par défaut, les serveurs d’applications doivent assumer &quot;Content-Type: text/plain; charset=us-ascii&quot; dans ce cas. De nombreuses demandes automatisées et malveillantes peuvent ne pas disposer du &quot;type de contenu&quot;. |
| NOUA | Aucun agent utilisateur | De nombreuses requêtes automatisées et malveillantes utilisent des agents utilisateur faux ou manquants pour rendre difficile l’identification du type d’appareil qui effectue les requêtes. |
| TORNODE | Trafic Tor | Tor est un logiciel qui cache l&#39;identité d&#39;un utilisateur. Un pic de trafic Tor peut indiquer qu’un attaquant essaie de masquer sa localisation. |
| DATACENTER | Trafic du centre de données | Le trafic du centre de données est du trafic non organique provenant de fournisseurs d’hébergement identifiés. Ce type de trafic n’est généralement pas associé à un utilisateur final réel. |
| NULLBYTE | Octet nul | Les octets nuls n’apparaissent généralement pas dans une requête et indiquent que la requête est incorrecte et potentiellement malveillante. |
| IMPOSTOR | SearchBot Impostor | L’imposteur de robots de recherche est quelqu’un qui prétend être un robot de recherche Google ou Bing, mais qui n’est pas légitime. Remarque : ne dépend pas d’une réponse seule, mais doit être résolu dans le cloud en premier. Elle ne doit donc pas être utilisée dans une règle précédente. |
| PRIVATEFILE | Fichiers privés | Les fichiers privés sont généralement de nature confidentielle, par exemple un Apache `.htaccess` ou un fichier de configuration susceptible de faire fuiter des informations sensibles. |
| SCANNER | Scanner | Identifie les services et outils d’analyse les plus utilisés |
| RESPONSESPLIT | Fractionnement des réponses HTTP | Identifie le moment où les caractères CRLF sont envoyés en entrée de l’application pour injecter des en-têtes dans la réponse HTTP. |
| XML-ERROR | Erreur de codage XML | Corps de requête de POST, de PUT ou de PATCH spécifié comme contenant du code XML dans l’en-tête de requête &quot;Content-Type&quot;, mais contenant des erreurs d’analyse XML. Cela est souvent lié à une erreur de programmation ou à une requête automatisée ou malveillante. |

## Remarques {#considerations}

* Lorsque deux règles en conflit sont créées, les règles d’autorisation ont toujours la priorité sur les règles de blocage. Par exemple, si vous créez une règle pour bloquer un chemin spécifique et une règle pour autoriser une adresse IP spécifique, les demandes de cette adresse IP sur le chemin bloqué seront autorisées.

* Si une règle est mise en correspondance et bloquée, le réseau de diffusion de contenu répond par une `406` code de retour.

* Les fichiers de configuration ne doivent pas contenir de secrets, car ils seront lisibles par toute personne ayant accès au référentiel git.

## Exemples de règles {#examples}

Voici quelques exemples de règles. Voir [section limite de taux](#rules-with-rate-limits) plus bas pour des exemples de limitation de débit.

**Exemple 1**

Cette règle bloque les demandes provenant d’IP 192.168.1.1 :

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
     rules:
       - name: "block-request-from-ip"
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
         action: 
           type: block
```

**Exemple 2**

Cette règle bloque les requêtes sur le chemin d’accès `/helloworld` lors de la publication avec un User-Agent contenant Chrome :

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
     rules:
       - name: "block-request-from-chrome-on-path-helloworld-for-publish-tier"
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
           allOf:
            - { reqProperty: path, equals: /helloworld }
            - { reqProperty: tier, equals: publish }
            - { reqHeader: user-agent, matches: '.*Chrome.*'  }
           action: 
             type: block
```

**Exemple 3**

Cette règle bloque les requêtes qui contiennent le paramètre de requête `foo`, mais autorise chaque requête provenant d’IP 192.168.1.1 :

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: "block-request-that-contains-query-parameter-foo"
        when: { queryParam: url-param, equals: foo }
        action: 
          type: block
      - name: "allow-all-requests-from-ip"
        when: { reqProperty: clientIp, equals: 192.168.1.1 }
        action: 
          type: allow
```

**Exemple 4**

Cette règle bloque les requêtes de chemin /block-me et bloque chaque requête correspondant à un modèle SQLI ou XSS :

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action: 
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

**Exemple 4**

Cette règle bloque l&#39;accès aux pays de l&#39;OFAC :

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: block-ofac-countries
        when:
          allOf:
            - { reqProperty: tier, equals: publish }
            - reqProperty: clientCountry
              in:
                - SY
                - BY
                - MM
                - KP
                - IQ
                - CD
                - SD
                - IR
                - LR
                - ZW
                - CU
                - CI
        action: block
```

## Règles avec limites de taux {#rules-with-rate-limits}

Il est parfois souhaitable de bloquer le trafic correspondant à une règle uniquement si la correspondance dépasse un certain taux au fil du temps. Définir une valeur pour la variable `rateLimit` limite le taux de requêtes correspondant à la condition de la règle.

### Structure rateLimit {#ratelimit-structure}

| **Propriété** | **Type** | **Par défaut** | **SIGNIFICATION** |
|---|---|---|---|
| limit | entier compris entre 10 et 10 000 | obligatoire | Taux de requêtes de requêtes par seconde pour lesquelles la règle est déclenchée |
| window | nombre entier : 1, 10 ou 60 | 10 | Fenêtre d’échantillonnage en secondes pour laquelle le taux de requête est calculé |
| pénalité | entier compris entre 60 et 3 600 | 300 (5 minutes) | Une période en secondes pendant laquelle les requêtes correspondantes sont bloquées (arrondie à la minute la plus proche). |

### Exemples {#ratelimiting-examples}

**Exemple 1**

Cette règle bloque un client pendant 5 m lorsqu’il dépasse 100 req/s dans les 60 dernières secondes

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    - name: limit-requests-client-ip
      when:
        reqProperty: path
        like: '*'
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: block
```

**Exemple 2**

Bloquer les demandes pendant 60 s sur le chemin /critique/resource lorsqu’il dépasse 100 req/s dans les 60 dernières secondes

```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: rate-limit-example
        when: { reqProperty: path, equals: /critical/resource }
        action: 
          type: block
        rateLimit: { limit: 100, window: 60, penalty: 60 }
```

## Journaux du réseau de diffusion de contenu {#cdn-logs}

AEM as a Cloud Service permet d’accéder aux journaux du réseau de diffusion de contenu, qui sont utiles pour les cas d’utilisation, notamment l’optimisation du taux d’accès au cache et la configuration des règles CDN et WAF. Les journaux CDN s’affichent dans Cloud Manager **Journaux de téléchargement** lors de la sélection du service Auteur ou Publier.

La propriété &quot;rules&quot; décrit les règles de filtre de trafic correspondantes et présente le modèle suivant :

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

Par exemple :

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

Les règles se comportent comme suit :

* le nom de règle déclaré par le client de toute règle correspondante sera répertorié dans l’attribut matches .
* l’attribut action indique si les règles ont eu pour effet de bloquer, autoriser ou consigner
* si le WAF est sous licence et activé, l’attribut waf répertorie toutes les règles waf (par exemple, SQLI ; notez qu’elles sont indépendantes du nom déclaré par le client) qui ont été détectées, que les règles waf aient été répertoriées ou non dans la configuration.
* si aucune correspondance de règles déclarées par le client et aucune correspondance de règles waf, la propriété d’attribut rules est vide.

En règle générale, les règles correspondantes apparaissent dans l’entrée de journal pour toutes les requêtes sur le réseau de diffusion de contenu, qu’il s’agisse d’un accès, d’une transmission ou d’une absence sur le réseau de diffusion de contenu. Toutefois, les règles WAF apparaissent dans l’entrée de journal uniquement pour les requêtes au réseau de diffusion de contenu qui sont considérées comme des échecs ou des réussites CDN, mais pas pour les accès CDN.

L’exemple ci-dessous illustre un exemple de cdn.yaml et deux entrées de journal CDN :


```
kind: "CDN"
version: "1"
envType: "dev"
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS ]
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/block-me",
"method": "GET",
"res_ctype": "",
"cache": "PASS",
"status": 406,
"res_age": 0,
"pop": "PAR",
"rules": "match=path-rule,action=blocked"
}
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"rid": "974e67f6",
"host": "example.com",
"url": "/?sqli=%27%29%20UNION%20ALL%20SELECT%20NULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL--%20fAPK",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 406,
"res_age": 0,
"pop": "PAR",
"rules": "match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked"
}
```

### Format du journal {#cdn-log-format}

Vous trouverez ci-dessous une liste des noms de champ utilisés dans les journaux CDN, ainsi qu’une brève description.

| **Nom du champ** | **Description** |
|---|---|
| *timestamp* | Heure à laquelle la demande a commencé, après la fin de TLS |
| *ttfb* | Abréviation de *Time To First Byte*. Intervalle entre le démarrage de la requête et le début de la diffusion du corps de la réponse. |
| *cli_ip* | Adresse IP du client. |
| *cli_country* | Deux lettres [ISO 3166-1](https://fr.wikipedia.org/wiki/ISO_3166-1) code de pays alpha-2 pour le pays client. |
| *rid* | La valeur de l’en-tête de requête utilisé pour identifier la requête de manière unique. |
| *req_ua* | L’agent utilisateur responsable de l’exécution d’une requête HTTP donnée. |
| *host* | Autorité à laquelle la demande est destinée. |
| *url* | Chemin d’accès complet, y compris les paramètres de requête. |
| *method* | méthode HTTP envoyée par le client, telle que &quot;GET&quot; ou &quot;POST&quot;. |
| *res_ctype* | Type de contenu utilisé pour indiquer le type de média d’origine de la ressource. |
| *cache* | État du cache. Les valeurs possibles sont HIT, MISS ou PASS |
| *status* | Le code d’état HTTP sous la forme d’une valeur entière. |
| *res_age* | Durée (en secondes) pendant laquelle une réponse a été mise en cache (dans tous les noeuds). |
| *pop* | Centre de données du serveur de cache CDN. |
| *règles* | Nom de toute règle correspondante.<br><br>Indique également si la correspondance a entraîné un bloc. <br><br>Par exemple, &quot;`match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked`&quot;<br><br>Vide si aucune règle ne correspondait. |
