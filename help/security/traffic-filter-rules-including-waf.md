---
title: Règles de filtre de trafic incluant des règles WAF
description: Configurer des règles de filtre de trafic incluant des règles de pare-feu d’application web (WAF).
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
feature: Security
role: Admin
source-git-commit: d1f3c63c50368dffb2ff5c41c401a5b050495cdd
workflow-type: tm+mt
source-wordcount: '4257'
ht-degree: 70%

---


# Règles de filtre de trafic incluant des règles WAF {#traffic-filter-rules-including-waf-rules}

Les règles de filtrage du trafic bloquent ou autorisent les requêtes au niveau de la couche CDN, ce qui s’avère utile dans les scénarios tels que les suivants :

* Limiter l’accès à des domaines spécifiques au trafic interne de l’entreprise avant la mise en ligne d’un nouveau site.
* Pour être moins sensible aux attaques par déni de service volumétriques, fixez des limites de débit.
* Empêcher les adresses IP connues pour être malveillantes de cibler vos pages.

La plupart de ces règles de filtrage de trafic sont disponibles pour l’ensemble des clientes et clients d’AEM as a Cloud Service Sites et Forms. En tant que *règles de filtrage du trafic standard*, elles fonctionnent sur les propriétés de la requête : adresse IP, nom d’hôte, chemin d’accès et agent utilisateur. Les règles de filtrage de trafic standard incluent des règles de limite de débit, permettant de se prémunir contre les pics de trafic.

Une sous-catégorie de règles de filtrage du trafic nécessite une licence Extended Security (anciennement appelée Protection WAF-DDoS) ou Extended Security for Healthcare (anciennement appelée Sécurité renforcée). Ces puissantes règles sont connues sous le nom de règles de filtrage du trafic WAF (Pare-feu d’application web) (ou *règles de WAF*) et ont accès aux [indicateurs WAF](#waf-flags-list) décrits plus loin dans cet article.

Les règles de filtrage du trafic peuvent être déployées par le biais de pipelines de configuration de Cloud Manager vers des types d’environnements de développement, d’évaluation et de production. Le fichier de configuration peut être déployé dans des environnements de développement rapide (RDE) à l’aide de l’outil de ligne de commande.

Pour acquérir rapidement des connaissances sur cette fonctionnalité, [suivez un tutoriel](#tutorial).

>[!NOTE]
>Pour obtenir des options supplémentaires de configuration du trafic sur le réseau CDN, telles que la modification des requêtes/réponses, la déclaration des redirections et la création d’un proxy vers des origines non AEM, consultez l’article [Configuration du trafic sur le réseau CDN](/help/implementing/dispatcher/cdn-configuring-traffic.md).


## Organisation de cet article {#how-organized}

Cet article comprend les sections suivantes :

* **Vue d’ensemble de la protection du trafic :** découvrez votre protection contre le trafic malveillant.
* **Processus suggéré pour la configuration des règles :** découvrez une méthodologie de haut niveau pour la protection de votre site web.
* **Configuration :** découvrez comment configurer et déployer des règles de filtrage du trafic, y compris les règles WAF avancées.
* **Syntaxe des règles :** découvrez comment déclarer des règles de filtre de trafic dans le fichier de configuration `cdn.yaml`. Cela inclut les règles de filtre de trafic disponibles pour l’ensemble de la clientèle Sites et Forms, ainsi que la sous-catégorie des règles WAF pour les personnes qui détiennent une licence pour cette fonctionnalité.
* **Exemples de règles :** pour commencer, consultez les exemples de règles déclarées.
* **Règles de limite de débit :** découvrez comment utiliser des règles de limitation de débit pour protéger votre site contre les attaques à volume élevé.
* **Alertes relatives aux règles de filtrage du trafic :** permet de configurer les alertes qui seront averties lorsque vos règles seront déclenchées.
* **Alerte de pic de trafic par défaut à l’origine :** recevez des notifications en cas de forte augmentation du trafic à l’origine, suggérant une attaque DDoS.
* **Journaux du réseau CDN :** découvrez les règles déclarées et les indicateurs WAF qui correspondent à votre trafic.
* **Outils de tableau de bord :** analysez vos journaux du réseau CDN pour obtenir de nouvelles règles de filtre de trafic.
* **Règles de démarrage recommandées :** ensemble de règles avec lesquelles commencer.
* **Tutoriel :** informations sur la fonctionnalité, y compris sur l’utilisation des outils de tableau de bord pour déclarer les règles appropriées.

## Vue d’ensemble de la protection du trafic {#traffic-protection-overview}

Dans le paysage numérique actuel, le trafic malveillant est une menace omniprésente. Adobe reconnaît la gravité du risque et propose plusieurs approches pour protéger les applications clientes et atténuer les attaques lorsqu’elles se produisent.

À la périphérie, le réseau CDN géré par Adobe absorbe les attaques DoS sur la couche réseau (couches 3 et 4), y compris les attaques par inondation et par réflexion/amplification.

Par défaut, Adobe prend des mesures pour empêcher la dégradation des performances en raison de l’explosion inattendue d’un trafic élevé au-delà d’un certain seuil. En cas d’attaque DoS qui affecte la disponibilité du site, les équipes d’exploitation d’Adobe sont alertées et prennent des mesures pour atténuer les attaques.

Les clients prennent des mesures proactives pour atténuer les attaques de couche d’application (couche 7) en configurant des règles à différents niveaux du flux de diffusion de contenu.

Par exemple, au niveau de la couche Apache, les clients configurent le module [](https://experienceleague.adobe.com/fr/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration#configuring-access-to-content-filter) ou [ModSecurity](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/foundation/security/modsecurity-crs-dos-attack-protection) pour limiter l’accès à certains contenus.

Comme cet article le décrit, les règles de filtrage du trafic sont déployées sur le réseau CDN géré par Adobe à l’aide de Cloud Manager [pipelines de configuration](/help/operations/config-pipeline.md). Au-delà des *règles standard de filtrage du trafic* (adresse IP, chemin, en-têtes, limites de débit), les licences client *règles WAF*.

## Processus suggéré {#suggested-process}

Voici un processus de bout en bout recommandé et détaillé pour déterminer les règles de filtrage du trafic appropriées :

1. Configurez les pipelines de configuration hors production et en production, comme décrit dans la section [Configuration](#setup).
1. Les clients qui disposent d’une licence pour les règles de filtrage du trafic ** les activent dans Cloud Manager.

   >[!IMPORTANT]
   >
   >Les règles de licence WAF ne les activent pas. La fonctionnalité reste inactive jusqu&#39;à ce que la protection **WAF-DDOS** soit cochée dans l&#39;onglet **Sécurité** de Cloud Manager.

1. Lisez et terminez le tutoriel pour savoir comment utiliser les règles de filtrage du trafic, y compris les règles WAF si elles ont fait l’objet d’une licence. Ce tutoriel vous guide tout au long des étapes du déploiement de règles dans un environnement de développement, de la simulation du trafic malveillant et du téléchargement des [journaux du réseau CDN](#cdn-logs) à leur analyse dans les [outils du tableau de bord](#dashboard-tooling).
1. Copiez les règles de démarrage recommandées dans `cdn.yaml` et déployez la configuration dans l’environnement de production, en plaçant certaines règles en mode journal.
1. Après avoir collecté du trafic, analysez les résultats à l’aide des [outils du tableau de bord](#dashboard-tooling) pour voir s’il y a des correspondances. Recherchez les faux positifs et effectuez les ajustements nécessaires, pour finalement activer toutes les règles de démarrage en mode bloc.
1. Si nécessaire, ajoutez des règles personnalisées basées sur l’analyse des journaux du CDN, d’abord en les testant avec du trafic simulé sur des environnements de développement, avant de procéder au déploiement dans des environnements d’évaluation et de production en mode journal, puis en mode bloc.
1. Surveillez le trafic de manière continue, en modifiant les règles à mesure que le paysage de la menace évolue.

## Configuration {#setup}

1. Créez un fichier `cdn.yaml` avec un ensemble de règles de filtrage de trafic, y compris les règles WAF. Par exemple :

   ```
   kind: "CDN"
   version: "1"
   data:
     trafficFilters:
       rules:
       # Block simple path
       - name: block-path
         when:
           allOf:
             - reqProperty: tier
               matches: "author|publish"
             - reqProperty: path
               equals: '/block/me'
         action: block
   ```

   Voir la section [Utiliser les pipelines de configuration](/help/operations/config-pipeline.md#common-syntax) pour obtenir une description des propriétés situées au-dessus du nœud `data`. La valeur de la propriété `kind` doit être définie sur *CDN* et la version doit être définie sur `1`.


1. Si des règles WAF sont sous licence, vous *devez* activer la fonction dans Cloud Manager. Les règles de WAF sous licence ne sont pas actives et ne fournissent aucune protection tant que la protection **WAF-DDOS** n&#39;est pas cochée. Activez la fonctionnalité pour les scénarios de programme nouveaux et existants, comme décrit ci-dessous :

   1. Pour configurer WAF sur un nouveau programme, cochez la case **Protection WAF-DDOS** dans l&#39;onglet **Sécurité** lorsque vous [créez un programme de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).

   1. Pour configurer WAF sur un programme existant, [modifiez votre programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md). Dans l’onglet **Sécurité**, cochez l’option **Protection WAF-DDOS** pour activer la fonctionnalité, ou décochez-la pour la désactiver. Vous pouvez modifier ce paramètre à tout moment.

      Pour confirmer que la fonctionnalité est *active* après son activation, examinez les [journaux du réseau CDN](#cdn-logs) une fois que le trafic circule sur le site. Recherchez les entrées de journal qui incluent une propriété `rules` contenant un attribut `waf`. Par exemple :

      `"rules": "waf=SQLI" `

      Cet attribut apparaît une fois que WAF est actif, avant même le déploiement des règles WAF.

1. Créez un pipeline de configuration dans Cloud Manager, comme décrit dans l’[article sur le pipeline de configuration](/help/operations/config-pipeline.md#managing-in-cloud-manager). Le pipeline fait référence à un dossier de `config` de niveau supérieur avec le fichier `cdn.yaml` placé quelque part en dessous, voir [Utilisation des pipelines de configuration](/help/operations/config-pipeline.md#folder-structure).

## Syntaxe des règles de filtrage de trafic {#rules-syntax}

Pour faire correspondre des modèles tels que l’adresse IP, l’agent utilisateur, les en-têtes, le nom d’hôte, la zone géographique ou l’URL, vous pouvez configurer des *règles de filtrage du trafic*.

Les clients disposant d’une licence de niveau Sécurité étendue ou Sécurité étendue pour les soins de santé configurent des *règles* qui font référence à des [indicateurs WAF](#waf-flags-list).

Voici un exemple d’un ensemble de règles de filtrage du trafic, qui incluent également une règle WAF.

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when:
          allOf:
            - { reqProperty: path, equals: /block-me }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

Format des règles de filtrage du trafic dans le fichier `cdn.yaml` décrit ci-dessous. Voir quelques [autres exemples](#examples) dans une section ultérieure, ainsi qu’une section distincte sur les [Règles de limite de taux](#rate-limit-rules).


| **Propriété** | **La plupart des règles de filtrage de trafic** | **Règles de filtre de trafic WAF** | **Type** | **Valeur par défaut** | **Description** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Nom de règle (64 caractères, ne peut contenir que des caractères alphanumériques et -) |
| lorsque | X | X | `Condition` | - | La structure de base est la suivante : <br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>consultez la section [Structure de conditions](/help/implementing/dispatcher/cdn-configuring-traffic.md#condition-structure) dans *Configuration du trafic sur le réseau CDN* pour obtenir des getters, des prédicats et comment combiner plusieurs conditions. |
| action | X | X | `Action` | journal | Objet journal, autoriser, bloquer ou action. Par défaut, il s’agit de journal. |
| rateLimit | X |   | `RateLimit` | non défini | Configuration de limite de débit. La limite de débit est désactivée si elle n’est pas définie.<br><br>Vous trouverez ci-dessous une section distincte décrivant la syntaxe rateLimit, ainsi que des exemples. |

### Structure d’action {#action-structure}

Une `action` peut être soit une chaîne spécifiant l’action (autoriser, bloquer ou consigner), soit un objet composé à la fois du type d’action (autoriser, bloquer ou consigner) et d’options telles que wafFlags et/ou le statut.

**Types d’actions**

Les actions sont classées par ordre de priorité en fonction de leurs types dans le tableau suivant, dans l’ordre d’exécution des actions :

| **Nom** | **Propriétés autorisées** | **Signification** |
|---|---|---|
| **autoriser** | `wafFlags` (facultatif), `alert` (facultatif) | Si wafFlags n’est pas présent, arrête le traitement des règles et passe à la diffusion de la réponse. Si wafFlags est présent, désactive les protections WAF spécifiées et poursuit le traitement des règles. <br>Si une alerte est spécifiée, une notification du Centre d’actions est envoyée si la règle est déclenchée 10 fois dans un intervalle de 5 minutes. Une fois qu’une alerte est déclenchée pour une règle spécifique, elle ne se redéclenche pas avant le lendemain (UTC). |
| **bloquer** | `status, wafFlags` (facultatif et mutuellement exclusif), `alert` (facultatif) | Si wafFlags n’est pas présent, renvoie une erreur HTTP en contournant toutes les autres propriétés, le code d’erreur est défini par la propriété de statut ou sur la valeur par défaut 406. Si wafFlags est présent, active les protections WAF spécifiées et poursuit le traitement des règles. <br>Si une alerte est spécifiée, une notification du Centre d’actions est envoyée si la règle est déclenchée 10 fois dans un intervalle de 5 minutes. Une fois qu’une alerte est déclenchée pour une règle spécifique, elle ne se redéclenche pas avant le lendemain (UTC). |
| **consigner** | `wafFlags` (facultatif), `alert` (facultatif) | Consigne le fait que la règle a été déclenchée, sinon n’affecte pas le traitement. wafFlags n’a aucun effet. <br>Si une alerte est spécifiée, une notification du Centre d’actions est envoyée si la règle est déclenchée 10 fois dans un intervalle de 5 minutes. Une fois qu’une alerte est déclenchée pour une règle spécifique, elle ne se redéclenche pas avant le lendemain (UTC). |

### Liste des indicateurs WAF {#waf-flags-list}

La propriété `wafFlags` , utilisée dans les règles de filtrage du trafic WAF sous licence, fait référence aux éléments suivants :

#### Trafic malveillant

| **ID d’indicateur** | **Nom de l’indicateur** | **Description** |
|---|---|---|
| ATTACK | Attaque | Agrégation des indicateurs liés au trafic malveillant (SQLI, CMDEXE, XSS, etc.). Consultez la [section Règles WAF recommandées](#recommended-waf-starter-rules) pour savoir comment utiliser cet indicateur efficacement. |
| ATTACK-FROM-BAD-IP | Attaque provenant d’une adresse IP incorrecte | Similaire à l’indicateur ATTACK, mais avec un « ET logique » avec l’indicateur `BAD-IP`, afin qu’une requête soit marquée si elle correspond à la fois à ATTACK et à BAD-IP. Consultez la [section Règles WAF recommandées](#recommended-waf-starter-rules) pour savoir comment utiliser cet indicateur efficacement. |
| SQLI | Injection SQL | L’injection SQL est une tentative d’accès à une application ou d’obtention d’informations privilégiées en exécutant des requêtes de base de données arbitraires. |
| BACKDOOR | Backdoor | Un signal backdoor est une requête qui tente de déterminer si un fichier backdoor commun est présent sur le système. |
| CMDEXE | Exécution de commande | L’exécution de commande est une tentative de contrôle ou d’endommagement d’un système cible par le biais de commandes système arbitraires au moyen d’entrées de l’utilisateur ou de l’utilisatrice. |
| CMDEXE-NO-BIN | Exécution de commande, sauf sur `/bin/` | Fournit le même niveau de protection que `CMDEXE` lors de la désactivation du faux positif sur `/bin` en raison de l’architecture AEM. |
| XSS | Scripts intersites | Les scripts intersites consistent à tenter de détourner un compte d’utilisateur ou d’utilisatrice ou une session de navigation web par le biais d’un code JavaScript malveillant. |
| TRAVERSÉE | Traversée de répertoire | La traversée de répertoire est une tentative de navigation dans des dossiers privilégiés à travers un système dans l’espoir d’obtenir des informations sensibles. |
| USERAGENT | Outils d’attaque | Les outils d’attaque consistent à utiliser des logiciels automatisés pour identifier des vulnérabilités de sécurité ou pour tenter d’exploiter une vulnérabilité découverte. |
| LOG4J-JNDI | Log4J JNDI | Les attaques Log4J JNDI tentent d’exploiter la [Vulnérabilité Log4Shell](https://fr.wikipedia.org/wiki/Log4Shell) présente dans les versions de Log4J antérieures à la version 2.16.0 |
| CVE | CVE | Indicateur utilisé pour identifier un CVE. Est toujours associé à un indicateur `CVE-<CVE Number>`. Contactez Adobe pour en savoir plus sur les CVE contre lesquels Adobe vous protégera. |

#### Trafic suspect

| **ID d’indicateur** | **Nom de l’indicateur** | **Description** |
|---|---|---|
| ABNORMALPATH | Chemin d’accès anormal | Le chemin d’accès anormal indique que le chemin d’accès d’origine est différent du chemin d’accès normalisé (par exemple, `/foo/./bar` est normalisé en `/foo/bar`). |
| BAD-IP | Adresse IP incorrecte | Identifie les requêtes provenant d’adresses IP connues pour être malveillantes, soit en raison de leur inclusion dans des jeux de données tels que `SANS` et `TORNODE`, soit en fonction d’une détection préalable de comportements malveillants par le WAF |
| BHH | En-têtes de saut incorrects | Les en-têtes de saut incorrects indiquent une tentative de passage HTTP via un en-tête de transcodage (TE) ou de longueur de contenu (CL) mal formé, ou un en-tête de TE et de CL bien formé. |
| CODEINJECTION | Injection de code | L’injection de code est une tentative de contrôle ou d’endommagement d’un système cible par le biais de commandes arbitraires de code d’application à l’aide d’entrées de l’utilisateur ou de l’utilisatrice. |
| COMPRESSED | Compression détectée | Le corps de la requête POST est compressé et ne peut pas être inspecté. Par exemple, si un en-tête de requête `Content-Encoding: gzip` est spécifié et que le corps POST n’est pas en texte brut. |
| RESPONSESPLIT | Fractionnement des réponses HTTP | Identifie le moment où les caractères CRLF sont envoyés en entrée de l’application pour injecter des en-têtes dans la réponse HTTP. |
| NOTUTF8 | Encodage non valide | Un encodage non valide peut entraîner la traduction par le serveur de caractères malveillants d’une requête dans une réponse, provoquant un déni de service ou un XSS. |
| MALFORMED-DATA | Données incorrectes dans le corps de la requête | Corps de requête POST, PUT ou PATCH incorrect selon l’en-tête de requête « Content-Type ». Par exemple, si un en-tête de requête « Content-Type: application/x-www-form-urlencoded » est spécifié et contient un corps de POST qui est json. Il s’agit souvent d’une erreur de programmation, d’une requête automatisée ou malveillante. Nécessite l’agent 3.2 ou version ultérieure. |
| SANS | Trafic IP malveillant | [Internet Storm Center SANS](https://isc.sans.edu/) : liste des adresses IP qui ont été signalées comme ayant participé à une activité malveillante. |
| NO-CONTENT-TYPE | En-tête de requête « Content-Type » manquant | Requête POST, PUT ou PATCH ne comportant pas d’en-tête de requête « Content-Type ». Par défaut, les serveurs d’applications doivent assumer « Content-Type: text/plain; charset=us-ascii » dans ce cas. De nombreuses requêtes automatisées et malveillantes peuvent ne pas disposer de « Content-Type ». |
| NOUA | Aucun agent utilisateur | Indique qu’une requête ne contenait pas d’en-tête « User-Agent » ou que la valeur de l’en-tête n’a pas été définie. |
| NULLBYTE | Octet nul | Les octets nuls n’apparaissent généralement pas dans une requête et indiquent que la requête est incorrecte et potentiellement malveillante. |
| OOB-DOMAIN | Domaine hors-bande | Les domaines hors-bande sont généralement utilisés pendant les tests de pénétration pour identifier les vulnérabilités dans lesquelles l’accès réseau est autorisé. |
| PRIVATEFILE | Fichiers privés | Les fichiers privés sont de nature confidentielle, par exemple un fichier Apache `.htaccess` ou un fichier de configuration susceptible de faire fuiter des informations sensibles. |
| SCANNER | Scanner | Identifie les services et outils d’analyse les plus utilisés. |

#### Trafic divers

| **ID d’indicateur** | **Nom de l’indicateur** | **Description** |
|---|---|---|
| CENTRE DE DONNÉES | Centre de données | Identifie la requête comme provenant d’un fournisseur d’hébergement connu. Ce type de trafic n’est généralement pas associé à un utilisateur final réel ou une utilisatrice finale réelle. |
| DOUBLEENCODING | Encodage double | L’encodage double vérifie la technique d’évasion du double encodage des caractères HTML. |
| JSON-ERROR | Erreur d’encodage JSON | Corps de requête POST, PUT ou PATCH spécifié comme contenant JSON dans l’en-tête de requête « Content-Type », mais contenant des erreurs d’analyse JSON. Cela est souvent lié à une erreur de programmation ou à une requête automatisée ou malveillante. |
| TORNODE | Trafic Tor | Tor est un logiciel qui cache l’identité d’un utilisateur ou d’une utilisatrice. Un pic de trafic Tor peut indiquer qu’une personne malveillante essaie de masquer sa localisation. |
| XML-ERROR | Erreur de codage XML | Corps de requête POST, PUT ou PATCH spécifié comme contenant du code XML dans l’en-tête de requête « Content-Type », mais contenant des erreurs d’analyse XML. Cela est souvent lié à une erreur de programmation ou à une requête automatisée ou malveillante. |

## Considérations {#considerations}

* Lorsque deux règles en conflit sont créées, les règles d’autorisation ont toujours la priorité sur les règles de blocage. Par exemple, si vous créez une règle pour bloquer un chemin spécifique et une règle pour autoriser une adresse IP spécifique, les requêtes provenant de cette adresse IP sur le chemin bloqué sont autorisées.

* Si une règle est mise en correspondance et bloquée, le réseau CDN répond avec un code de retour `406`.

* Les fichiers de configuration ne contiennent aucun secret, car ils sont lisibles par toute personne ayant accès au référentiel Git.

* Les liste d’adresses IP autorisées définies dans Cloud Manager sont prioritaires sur les règles de filtres de trafic.

* Les correspondances de règles WAF apparaissent uniquement dans les journaux de réseau CDN pour les échecs et les réussites du réseau CDN, et non les accès.

## Exemples de règles {#examples}

Voici quelques exemples de règles. Voir la [section de limite de débit](#rate-limit-rules) plus bas pour des exemples de règles de limite de débit.

**Exemple 1**

Cette règle bloque les requêtes provenant de l’**IP192.168.1.1** :

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
     rules:
       - name: "block-request-from-ip"
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
         action:
           type: block
```

**Exemple 2**

Cette règle bloque les requêtes de chemin d’accès `/helloworld` lors de la publication avec un User-Agent contenant Chrome :

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
      - name: "block-request-from-chrome-on-path-helloworld-for-publish-tier"
        when:
          allOf:
          - { reqProperty: path, equals: /helloworld }
          - { reqProperty: tier, equals: publish }
          - { reqHeader: user-agent, matches: '.*Chrome.*'  }
        action:
          type: block
```

**Exemple 3**

Cette règle bloque les requêtes à la publication qui contiennent le paramètre de requête `foo`, mais autorise chaque requête provenant de l’adresse IP 192.168.1.1 :

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
      - name: "block-request-that-contains-query-parameter-foo"
        when:
          allOf:
            - { queryParam: url-param, equals: foo }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
      - name: "allow-all-requests-from-ip"
        when: { reqProperty: clientIp, equals: 192.168.1.1 }
        action:
          type: allow
```

**Exemple 4**

Cette règle bloque les requêtes vers le chemin d’accès `/block-me` à la publication et bloque chaque requête qui correspond à un modèle `SQLI` ou `XSS`. Cet exemple comprend une règle de filtrage du trafic WAF, qui fait référence aux indicateurs `SQLI` et `XSS` [WAF](#waf-flags-list) et nécessite donc une licence distincte.

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when:
          allOf:
            - { reqProperty: path, equals: /block-me }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

**Exemple 5**

Cette règle bloque l’accès aux pays de l’OFAC :

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
      - name: block-ofac-countries
        when:
          allOf:
            - reqProperty: tier
              matches: "author|publish"
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

## Règles de limite de débit

Il est parfois souhaitable de bloquer le trafic s’il dépasse un certain débit de requêtes entrantes, selon une condition spécifique. Définir une valeur pour la propriété `rateLimit` limite le débit des requêtes correspondant à la condition de la règle.

Les règles de limite de débit ne peuvent pas faire référence aux indicateurs WAF. Elles sont disponibles pour tous les clientes et clients Sites et Forms.

Les limites de débit sont calculées par POP de réseau CDN. Supposons, par exemple, que les POP de Montréal, Miami et Dublin connaissent des débits de trafic de 80, 90 et 120 requêtes par seconde, respectivement, et que la règle de limite de débit soit définie sur une limite de 100. Dans ce cas, seul le trafic vers Dublin est limité par le tarif.

Les limites de débit sont évaluées en fonction du trafic Edge, du trafic d’origine ou du nombre d’erreurs.

### Structure rateLimit {#ratelimit-structure}

| **Propriété** | **Type** | **Par défaut** | **SIGNIFICATION** |
|---|---|---|---|
| limite | entier compris entre 10 et 10 000 | obligatoire | Débit de requête (par POP de réseau CDN) dans les requêtes par seconde pour lesquelles la règle est déclenchée. |
| fenêtre | nombre entier : 1, 10 ou 60 | 10 | Fenêtre d’échantillonnage en secondes pour laquelle le débit de requête est calculé. La précision des compteurs dépend de la taille de la fenêtre (plus la fenêtre est grande, plus la précision est élevée). Par exemple, on peut s’attendre à une précision de 50 % pour la fenêtre d’1 seconde et de 90 % pour la fenêtre de 60 secondes. |
| pénalité | entier compris entre 60 et 3 600 | 300 (5 minutes) | Période en secondes pendant laquelle les requêtes correspondantes sont bloquées (arrondie à la minute la plus proche). |
| nombre | tout, récupérations, erreurs | tout | Évaluer en fonction du trafic Edge (tout), du trafic d’origine (récupérations) ou du nombre d’erreurs (erreurs). |
| groupBy | tableau [Getter] | aucun | Le compteur de limiteur de taux sera agrégé par un ensemble de propriétés de requête (par exemple, clientIp). |

### Exemples {#ratelimiting-examples}

**Exemple 1**

Cette règle bloque un client pendant 5 minutes lorsqu’elle dépasse une moyenne de 60 req/s (par réseau CDN POP) au cours des 10 dernières secondes :

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
    - name: limit-requests-client-ip
      when:
        reqProperty: tier
        matches: "author|publish"
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        count: all
        groupBy:
          - reqProperty: clientIp
      action: block
```

**Exemple 2**

Bloque les requêtes sur le chemin d’accès /critical/resource pendant 60 secondes lorsqu’il dépasse une moyenne de 100 requêtes/s à l’origine (par POP de réseau CDN) sur une fenêtre de temps de 10 secondes :

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
      - name: rate-limit-example
        when:
          allOf:
            - { reqProperty: path, equals: /critical/resource }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
        rateLimit: { limit: 100, window: 10, penalty: 60, count: fetches }
```

Pour obtenir des fragments de code supplémentaires pour les scénarios avancés, consultez l’article [ Fragments de code de configuration du réseau CDN pour les scénarios courants ](/help/implementing/dispatcher/cdn-configuration-snippets-common-scenarios.md).

## Règles CVE {#cve-rules}

Si WAF est sous licence, Adobe applique automatiquement des règles de blocage pour se protéger contre de nombreux CVE connus (Vulnérabilités et expositions courantes) et de nouveaux CVE sont ajoutés peu de temps après leur découverte. Les clients ne configurent pas eux-mêmes les règles CVE.

Si une requête de trafic correspond à un fichier CVE, elle apparaît dans l’entrée de journal CDN correspondante.

Contactez l’assistance Adobe si vous avez des questions sur un CVE spécifique ou si votre entreprise souhaite désactiver une règle CVE spécifique.

## Alertes sur les règles de filtrage du trafic {#traffic-filter-rules-alerts}

Une règle peut être configurée pour envoyer une notification du Centre d’actions si elle est déclenchée dix fois pendant une fenêtre de 5 minutes. Une telle règle vous avertit lorsque certains schémas de trafic se produisent afin que vous puissiez prendre les mesures nécessaires. Une fois qu’une alerte est déclenchée pour une règle spécifique, elle ne se déclenche pas de nouveau avant le lendemain (UTC).

En savoir plus sur le [Centre d’actions](/help/operations/actions-center.md), notamment comment configurer les profils de notification requis pour recevoir des e-mails.

![Notification du Centre d’actions](/help/security/assets/traffic-filter-rules-actions-center-alert.png)


La propriété d’alerte peut être appliquée au nœud d’action pour tous les types d’actions (autoriser, bloquer, consigner).

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when:
          allOf:
            - { reqProperty: path, equals: /block-me }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
          alert: true
```

## Alerte de pic de trafic par défaut à l’origine {#traffic-spike-at-origin-alert}

Une notification par e-mail du [Centre d’actions](/help/operations/actions-center.md) vous avertit lorsqu’un trafic élevé provenant de la même adresse IP atteint son origine, ce qui suggère une attaque DDoS.

Si ce seuil est atteint, Adobe bloque le trafic provenant de cette adresse IP. Prenez des mesures supplémentaires pour protéger votre origine, telles que la configuration des règles de filtrage du trafic avec limite de débit. Consultez le tutoriel [ Blocage des attaques par déni de service et par déni de service à l’aide des règles de trafic ](#tutorial-blocking-DDoS-with-rules) pour une présentation guidée.

Le système active cette alerte par défaut, mais vous pouvez la désactiver à l’aide de la propriété *defaultTrafficAlerts*, définie sur false. Une fois l’alerte déclenchée, elle ne se déclenche plus avant le lendemain (UTC).

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
   defaultTrafficAlerts: false
```

## Journaux de réseau CDN {#cdn-logs}

AEM as a Cloud Service permet d’accéder aux journaux de réseau CDN qui sont utiles pour les cas d’utilisation, notamment l’optimisation du rapport d’accès au cache et la configuration des règles de filtre de trafic. Les journaux de réseau CDN s’affichent dans la boîte de dialogue **Journaux de téléchargement** de Cloud Manager, lors de la sélection du service de création ou de publication.

Les journaux CDN sont retardés de cinq minutes maximum.

La propriété `rules` décrit les règles de filtre de trafic correspondantes et présente le modèle suivant :

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

Par exemple :

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

Les règles se comportent comme suit :

* Le nom de règle déclaré par le client ou la cliente de toutes les règles correspondantes est répertorié dans l’attribut `match`.
* L’attribut `action` détermine si les règles bloquent, autorisent ou consignent.
* Si le WAF est sous licence et activé, l’attribut `waf` répertorie tous les indicateurs WAF (par exemple, SQLI) détectés, Ce comportement s’applique que les indicateurs WAF aient été répertoriés ou non dans une règle. Cette journalisation a pour but de fournir à insight de nouvelles règles potentielles à déclarer.
* Si aucune règle déclarée par le client ou la cliente ni aucune règle WAF ne correspond, la propriété `rules` est vide.

Comme nous l’avons vu plus haut, les correspondances de règles WAF apparaissent uniquement dans les journaux de réseau CDN pour les échecs et les réussites du réseau CDN, et non les accès.

L’exemple ci-dessous illustre un exemple de `cdn.yaml` et deux entrées de journal de réseau CDN :


```
kind: "CDN"
version: "1"
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
| *timestamp* | Heure à laquelle la requête a commencé, après la fin de TLS. |
| *ttfb* | Abréviation de *Time To First Byte*. Intervalle entre le démarrage de la requête et le début de la diffusion du corps de la réponse. |
| *cli_ip* | Adresse IP du client ou de la cliente. |
| *cli_country* | Code de pays alpha-2 à deux lettres [ISO 3166-1](https://fr.wikipedia.org/wiki/ISO_3166-1) pour le pays du client ou de la cliente. |
| *rid* | Valeur de l’en-tête de requête utilisé pour identifier la requête de manière unique. |
| *req_ua* | Agent utilisateur responsable de l’exécution d’une requête HTTP donnée. |
| *host* | Autorité à laquelle la requête est destinée. |
| *url* | Chemin d’accès complet, y compris les paramètres de requête. |
| *method* | Méthode HTTP envoyée par le client ou la cliente, telle que GET ou POST. |
| *res_ctype* | Type de contenu utilisé pour indiquer le type de média d’origine de la ressource. |
| *cache* | État du cache. Les valeurs possibles sont HIT, MISS ou PASS |
| *status* | Code d’état HTTP sous la forme d’une valeur d’entier. |
| *res_age* | Durée (en secondes) pendant laquelle une réponse a été mise en cache (dans tous les nœuds). |
| *pop* | Centre de données du serveur de cache de réseau CDN. |
| *rules* | Nom de toute règle correspondante.<br><br>Indique également si la correspondance a entraîné un bloc. <br><br>Par exemple, « `match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked` » <br><br>Vide si aucune règle ne correspondait. |

## Outils de tableau de bord {#dashboard-tooling}

Adobe fournit un mécanisme de téléchargement des outils de tableau de bord sur votre ordinateur pour ingérer les journaux de réseau CDN téléchargés via Cloud Manager. Utilisez cet outil pour analyser le trafic et déterminer les règles de filtrage de trafic appropriées à déclarer, y compris les règles WAF.

Les outils de tableau de bord peuvent être clonés directement à partir du référentiel GitHub [AEMCS-CDN-Log-Analysis-Tooling](https://github.com/adobe/AEMCS-CDN-Log-Analysis-Tooling).

[Un tutoriel](#tutorial) contient des instructions concrètes sur l’utilisation des outils de tableau de bord.

## Règles de démarrage recommandées {#recommended-starter-rules}

Adobe suggère de commencer par les règles de filtrage de trafic ci-dessous, puis de les affiner au fil du temps. Les *règles standard* sont disponibles avec une licence Sites ou Forms, tandis que les *règles WAF* nécessitent une licence de sécurité étendue (anciennement appelée Protection WAF-DDoS) ou de sécurité étendue pour les soins de santé (anciennement appelée Sécurité renforcée).

### Règles standard recommandées {#recommended-nonwaf-starter-rules}

Commencez par les règles suivantes :

1. Limite de débit (mode journal) :
   * consigner lorsque le trafic provenant d’une adresse IP donnée dépasse une limite de débit. Passez en mode bloc après avoir vérifié qu’aucune alerte n’a été reçue. Si des alertes ont été reçues, cela indique que la valeur limite était trop basse.
2. pays spécifiques (mode bloc) :
   * bloquer le trafic provenant de certains pays (modifiez les codes de pays en fonction des besoins de votre entreprise)

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
    rules:
    #  Block client for 5m when it exceeds an average of 100 req/sec to origin on a time window of 10sec
    - name: limit-origin-requests-client-ip
      when:
        reqProperty: tier
        equals: 'publish'
      rateLimit:
        limit: 100
        window: 10
        count: fetches
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: log
    #  Block client for 5m when it exceeds an average of 500 req/sec on a time window of 10sec
    - name: limit-requests-client-ip
      when:
        reqProperty: tier
        equals: 'publish'
      rateLimit:
        limit: 500
        window: 10
        count: all
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: log
      alert: true
    # Block requests coming from OFAC countries
    - name: ofac-countries
      when:
        allOf:
          - { reqProperty: tier, in: ["author", "publish"] }
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

### Règles WAF recommandées {#recommended-waf-starter-rules}

Ajoutez les règles suivantes à votre configuration existante :

1. Indicateur ATTAQUE DEPUIS UNE MAUVAISE ADRESSE IP (mode bloc) :
   * Bloquez immédiatement le trafic qui correspond à des modèles suspects (y compris plusieurs éléments de la liste [Indicateurs WAF](#waf-flags-list)) et provient d&#39;adresses IP connues pour être malveillantes.
   * L&#39;indicateur ATTACK-FROM-BAD-IP remplit les deux conditions (correspondance de motifs et adresse IP malveillante connue), ce qui réduit le risque de faux positifs. Ainsi, vous pouvez appliquer cette règle en mode blocage de manière sûre et immédiate.
2. Indicateur d’ATTAQUE (mode journal) :
   * Consignez (plutôt que de bloquer) le trafic correspondant à des modèles suspects, mais ne provenant pas d’adresses IP malveillantes connues. Cette approche prudente, consistant à journaliser plutôt qu’à bloquer, permet d’éviter de bloquer par inadvertance le trafic légitime (faux positifs).
   * Pour vérifier que les requêtes légitimes ne sont pas incorrectement marquées, analysez les journaux du réseau CDN après le déploiement de cette règle. Lorsque vous avez la certitude qu’aucun trafic légitime n’est affecté, passez en mode bloc.

>[!NOTE]
>
> L’expérience indique que les faux positifs associés à l’indicateur ATTAQUE sont rares. Par conséquent, une stratégie pratique consiste à bloquer immédiatement tout trafic suspect et à utiliser l’analyse des journaux du réseau CDN pour identifier et introduire des règles d’autorisation pour le trafic légitime. Chaque organisation évalue sa propre tolérance au risque, en pesant les avantages d’une meilleure protection contre le risque de bloquer par inadvertance des requêtes légitimes.

```
    # blocks likely attack traffic, which also comes from suspected IPs
    - name: attacks-from-bad-ips-globally
      when:
        reqProperty: tier
        in: ["author", "publish"]
      action:
        type: block
        wafFlags:
          - ATTACK-FROM-BAD-IP
    # log likely attack traffic, and later switch to block mode if false positives aren't observed
    - name: attacks-from-any-ips-globally
      when:
        reqProperty: tier
        in: ["author", "publish"]
      action:
        type: log
        wafFlags:
          - ATTACK
```

### Anciennes règles WAF recommandées {#previous-waf-starter-rules}

Avant juillet 2025, Adobe recommandait les règles WAF répertoriées ci-dessous, qui sont toujours valides et efficaces pour se défendre contre le trafic malveillant. Pour plus d’informations sur la migration vers les nouvelles règles recommandées, consultez le tutoriel.

+++ Développez pour afficher les anciennes règles WAF recommandées.

```
    # Enable recommended WAF protections (only works if WAF is licensed enabled for your environment)
    - name: block-waf-flags-globally
      when:
        reqProperty: tier
        in: ["author", "publish"]
      action:
        type: log
        wafFlags:
          - TRAVERSAL
          - CMDEXE-NO-BIN
          - XSS
          - LOG4J-JNDI
          - BACKDOOR
          - USERAGENT
          - SQLI
          - SANS
          - TORNODE
          - NOUA
          - SCANNER
          - PRIVATEFILE
          - NULLBYTE
```

+++

## Tutoriel {#tutorial}

Pour acquérir des connaissances et une expérience pratiques sur les règles de filtrage du trafic, y compris les règles de WAF, suivez une série [ tutoriels ](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview).

En voici un aperçu :

* Vue d’ensemble des règles de filtrage de trafic standard et WAF
* Pour bloquer les attaques, y compris les attaques par déni de service (DoS), configurez les règles de filtrage du trafic standard et WAF recommandées.
* Déploiement de règles à l’aide du pipeline de configuration Cloud Manager
* Test de vos règles à l’aide d’outils de simulation de trafic malveillant
* Analyse des résultats à l’aide de l’outil d’analyse du journal
* Bonnes pratiques
