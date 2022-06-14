---
title: Règles de qualité du code personnalisé
description: Cette page décrit les règles de qualité du code personnalisé exécutées par Cloud Manager dans le cadre du test de qualité du code. Elles sont basées sur les bonnes pratiques de l’ingénierie AEM.
exl-id: f40e5774-c76b-4c84-9d14-8e40ee6b775b
source-git-commit: ee45ba3a03f9ab5461a09188888694ca22a11b20
workflow-type: tm+mt
source-wordcount: '3495'
ht-degree: 100%

---

# Règles de qualité du code personnalisé {#custom-code-quality-rules}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_customcodequalityrules"
>title="Règles de qualité du code personnalisé"
>abstract="Cette page décrit les règles de qualité du code personnalisé exécutées par Cloud Manager dans le cadre du test de qualité du code. Elles sont basées sur les bonnes pratiques de l’ingénierie AEM."

Cette page décrit les règles de qualité du code personnalisé exécutées par Cloud Manager dans le cadre du [test de qualité du code.](/help/implementing/cloud-manager/code-quality-testing.md) Elles sont basées sur les bonnes pratiques de l’ingénierie AEM.

>[!NOTE]
>
>Les exemples de code utilisés ici ne sont fournis qu’à titre d’illustration. Consultez la [Documentation sur les concepts](https://docs.sonarqube.org/7.4/user-guide/concepts/) SonarQube pour en savoir plus sur les concepts et les règles de qualité de SonarQube.

## Règles SonarQube {#sonarqube-rules}

La section suivante détaille les règles SonarQube exécutées par Cloud Manager.

### Ne pas utiliser de fonctions potentiellement dangereuses {#do-not-use-potentially-dangerous-functions}

* **Clé** : CQRules:CWE-676
* **Type** : vulnérabilité
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

Les méthodes `Thread.stop()` et `Thread.interrupt()` peuvent générer des problèmes difficiles à reproduire et, dans certains cas, des failles de sécurité. Leur utilisation doit être minutieusement surveillée et validée. En règle générale, la transmission de messages est une méthode plus sûre pour atteindre des objectifs similaires.

#### Code non conforme {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### Code conforme {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### Ne pas utiliser de chaînes de format pouvant être contrôlées en externe {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Clé** : CQRules:CWE-134
* **Type** : vulnérabilité
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

L’utilisation d’une chaîne de format provenant d’une source externe (telle qu’un paramètre de requête ou un contenu généré par l’utilisateur) peut exposer une application aux attaques par déni de service. Dans certains cas, une chaîne de format peut être contrôlée en externe, mais elle n’est autorisée que si elle provient de sources approuvées.

#### Code non conforme {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### Les requêtes HTTP doivent toujours avoir des délais de socket et de connexion {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Clé** : CQRules:ConnectionTimeoutMechanism
* **Type** : bogue
* **Gravité** : critique
* **Depuis** : version 2018.6.0

Lors de l’exécution de requêtes HTTP à partir d’une application AEM, il est essentiel de vérifier que les délais appropriés sont configurés afin d’éviter toute consommation inutile de threads. Malheureusement, le comportement par défaut du client HTTP Java par défaut `java.net.HttpUrlConnection` et du client de composants Apache HTTP couramment utilisé consiste à ne jamais expirer. Par conséquent, les délais d’expiration doivent être explicitement définis. De plus, en règle générale, ces délais d’expiration ne doivent pas dépasser 60 secondes.

#### Code non conforme {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### Code conforme {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### Les objets ResourceResolver doivent toujours être fermés {#resourceresolver-objects-should-always-be-closed}

* **Clé** : CQRules:CQBP-72
* **Type** : code smell
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

Les objets `ResourceResolver` obtenus à partir de `ResourceResolverFactory` consomment des ressources système. Bien qu’il existe des mesures pour récupérer ces ressources lorsqu’un objet `ResourceResolver` n’est plus en cours d’utilisation, il est plus efficace de fermer explicitement tous les objets `ResourceResolver` ouverts en appelant la méthode `close()`.

Une idée relativement répandue est que les objets `ResourceResolver` créés à l’aide d’une session JCR existante ne doivent pas être fermés explicitement ou ne doivent pas fermer la session JCR sous-jacente. Ce n’est pas le cas. Quelle que soit la manière dont un objet `ResourceResolver` est ouvert, il doit être fermé lorsqu’il n’est plus utilisé. Puisque `ResourceResolver` implémente l’interface `Closeable`, il est également possible d’utiliser la syntaxe `try-with-resources` plutôt que d’appeler explicitement `close()`.

#### Code non conforme {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Code conforme {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### Ne pas utiliser les chemins de servlet Sling pour enregistrer les servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Clé** : CQRules:CQBP-75
* **Type** : code smell
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

Comme décrit dans la [documentation Sling](http://sling.apache.org/documentation/the-sling-engine/servlets.html), il est déconseillé de lier les servlets aux chemins. Les servlets liés au chemin ne peuvent pas utiliser les contrôles d’accès JCR standard et, par conséquent, nécessitent une rigueur de sécurité supplémentaire. Plutôt que d’utiliser des servlets liés au chemin d’accès, il est recommandé de créer des nœuds dans le référentiel et d’enregistrer les servlets par type de ressource.

#### Code non conforme {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Les exceptions capturées doivent être consignées ou renvoyées, mais pas les deux {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Clé** : CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

En règle générale, une exception doit être consignée une seule fois. Journaliser les exceptions à plusieurs reprises peut prêter à confusion car il est difficile de connaître le nombre d’occurrences d’une exception. Le modèle le plus courant qui conduit à cette action consiste à journaliser et à émettre une exception capturée.

#### Code non conforme {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### Code conforme {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Éviter les instructions de journal immédiatement suivies d’une instruction de renvoi {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Clé** : CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Un autre schéma courant à éviter consiste à consigner un message, puis à émettre immédiatement une exception. Cela indique généralement que le message d’exception sera dupliqué dans les fichiers journaux.

#### Code non conforme {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Code conforme {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Éviter de journaliser les informations lors de la gestion des requêtes GET ou HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Clé** : CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Type** : code smell
* **Gravité** : mineure

En règle générale, le niveau de journal Informations doit être utilisé pour délimiter les actions importantes et, par défaut, AEM est configuré pour le journal au niveau Information ou au-dessus. Les méthodes GET et HEAD ne doivent jamais être en lecture seule et ne constituent donc pas des actions importantes. La journalisation au niveau d’Informations en réponse aux demandes GET ou HEAD est susceptible de créer un bruit journal significatif, rendant ainsi plus difficile l’identification des informations utiles dans les fichiers journaux. La journalisation lors de la gestion des demandes GET ou HEAD doit être soit au niveau d’avertissement ou d’erreur lorsque quelque chose est erroné, soit aux niveaux DEBUG ou TRACE si des informations de dépannage plus approfondies étaient utiles.

>[!NOTE]
>
>Cela ne s’applique pas à la journalisation de type `access.log` pour chaque requête.

#### Code non conforme {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Code conforme {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Ne pas utiliser Exception.getMessage() comme premier paramètre d’une instruction de journalisation {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Clé** : CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Il est recommandé que les messages de journal fournissent des informations contextuelles sur l’emplacement d’une exception dans l’application. Bien que le contexte puisse également être déterminé par l’utilisation des arborescences des appels de procédure, il est généralement plus facile de lire et de comprendre le message du journal. Par conséquent, lors de la journalisation d’une exception, il est déconseillé d’utiliser le message de l’exception comme message du journal : le message d’exception contiendra ce qu’il s’est passé, alors que le message du journal doit servir à indiquer à un lecteur ce que faisait l’application lorsque l’exception s’est produite. Le message d’exception sera toujours consigné. En spécifiant votre propre message, les journaux seront simplement plus faciles à comprendre.

#### Code non conforme {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Code conforme {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### La journalisation des blocs catch doit se trouver au niveau d’avertissement ou d’erreur {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Clé** : CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Comme le suggère leur nom, les exceptions Java doivent toujours être utilisées dans des circonstances exceptionnelles. Par conséquent, lorsqu’une exception est capturée, il est important de s’assurer que les messages du journal sont consignés au niveau approprié, AVERTISSEMENT ou ERREUR. Ces messages s’affichent ainsi correctement dans les journaux.

#### Code non conforme {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Code conforme {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Ne pas imprimer les arborescences des appels de procédure sur la console {#do-not-print-stack-traces-to-the-console}

* **Clé** : CQRules:CQBP-44---ExceptionPrintStackTrace
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Comme nous l’avons mentionné, le contexte est essentiel lors de la compréhension des messages du journal. Utiliser `Exception.printStackTrace()` entraîne seulement la sortie de l’arborescence des appels de procédure dans le flux d’erreurs standard, perdant ainsi tout le contexte. De plus, dans une application multi-thread telle qu’AEM, si plusieurs exceptions sont imprimées à l’aide de cette méthode en parallèle, leurs arborescences des appels de procédure peuvent se chevaucher, ce qui prête à confusion. Les exceptions ne doivent être consignées que dans la structure de journalisation.

#### Code non conforme {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Code conforme {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Ne pas générer de sortie standard ou d’erreur standard {#do-not-output-to-standard-output-or-standard-error}

* **Clé** : CQRules:CQBP-44—LogLevelConsolePrinters
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

La journalisation sur AEM doit toujours être effectuée via la structure de journalisation (SLF4J). La génération directe d’une sortie standard ou d’un flux d’erreur standard perd les informations structurelles et contextuelles fournies par la structure de journalisation et peut parfois entraîner des problèmes de performances.

#### Code non conforme {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Code conforme {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Évitez les chemins /apps et /libs codés en dur {#avoid-hardcoded-apps-and-libs-paths}

* **Clé** : CQRules:CQBP-71
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

En règle générale, les chemins qui commencent par `/libs` et `/apps` ne doivent pas être codés en dur, car les chemins auxquels ils se réfèrent sont le plus souvent stockés comme chemins relatifs au chemin de recherche Sling, qui est défini par défaut sur `/libs,/apps`. L’utilisation du chemin absolu peut introduire des défauts discrets qui n’apparaîtront que plus tard dans le cycle de vie du projet.

#### Code non conforme {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Code conforme {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Le planificateur Sling ne doit pas être utilisé {#sonarqube-sling-scheduler}

* **Clé** : CQRules:AMSCORE-554
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

Le planificateur Sling ne doit pas être utilisé pour des tâches qui nécessitent une exécution garantie. Les tâches planifiées Sling garantissent l’exécution et conviennent mieux aux environnements organisés avec ou sans grappes.

Reportez-vous à la section [Traitement des tâches et gestion des événements Apache Sling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) pour en savoir plus sur la façon dont les tâches Sling sont gérées dans des environnements organisés en grappes.

### Les API AEM obsolètes ne doivent pas être utilisées {#sonarqube-aem-deprecated}

* **Clé** : AMSCORE-553
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

La surface de l’API AEM est constamment revue pour identifier les API dont l’utilisation est déconseillée et qui sont donc considérées comme obsolètes.

Dans de nombreux cas, ces API sont abandonnées en y associant l’annotation standard Java `@Deprecated`. Elles sont à ce titre identifiées par la mention `squid:CallToDeprecatedMethod`.

Cependant, il arrive qu’une API soit déconseillée dans le contexte d’AEM, mais pas dans d’autres contextes. Cette règle identifie cette deuxième classe.


## Règles de contenu OakPAL {#oakpal-rules}

La section suivante présente les vérifications OakPAL exécutées par Cloud Manager.

>[!NOTE]
>
>OakPAL est une structure qui valide les packages de contenu à l’aide d’un référentiel Oak autonome. Cette structure a été développée par un partenaire d’AEM, lauréat du prix 2019 AEM Rockstar en Amérique du Nord.

### Les API de produit annotées avec @ProviderType ne doivent pas être implémentées ni étendues par les clients {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Clé** : CQBP-84
* **Type** : bogue
* **Gravité** : critique
* **Depuis** : version 2018.7.0

L’API AEM contient des classes et interfaces Java qui sont censées être utilisées, mais pas implémentées, par du code personnalisé. Par exemple, l’interface `com.day.cq.wcm.api.Page` est conçue pour être implémentée par AEM uniquement.

Lorsque de nouvelles méthodes sont ajoutées à ces interfaces, celles-ci n’ont aucun impact sur le code existant qui utilise ces interfaces et, par conséquent, l’ajout de nouvelles méthodes à ces interfaces est considéré comme rétrocompatible. Cependant, si le code personnalisé implémente l’une de ces interfaces, il introduit un risque de rétrocompatibilité pour le client.

Les interfaces et classes destinées uniquement à être implémentées par AEM sont annotées `org.osgi.annotation.versioning.ProviderType` ou, dans certains cas, avec une annotation héritée `aQute.bnd.annotation.ProviderType` similaire. Cette règle identifie les cas où une telle interface est implémentée (ou une classe est étendue) par code personnalisé.

#### Code non conforme {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Les index Lucene Oak personnalisés doivent avoir une configuration Tika {#oakpal-indextikanode}

* **Clé** : IndexTikaNode
* **Type** : bogue
* **Gravité** : bloqueur
* **Depuis** : 2021.8.0

Plusieurs index prêts à l’emploi AEM Oak incluent une configuration Tika et les personnalisations de ces index doivent inclure une configuration Tika. Cette règle recherche les personnalisations des index `damAssetLucene`, `lucene` et `graphqlConfig`, et soulève un problème si le nœud `tika` est manquant ou si un nœud enfant nommé `config.xml` est manquant dans le nœud `tika`.

Pour plus d’informations sur la personnalisation des définitions d’index, consultez la [documentation sur l’indexation](/help/operations/indexing.md#preparing-the-new-index-definition).

#### Code non conforme {#non-compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
```

#### Code conforme {#compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Les index Lucene Oak personnalisés ne doivent pas être synchrones {#oakpal-indexasync}

* **Clé** : IndexAsyncProperty
* **Type** : bogue
* **Gravité** : bloqueur
* **Depuis** : 2021.8.0

Les index Oak de type `lucene` doivent toujours être indexés de manière asynchrone. Si ce n’est pas le cas, le système risque d’être instable. Vous trouverez plus d’informations sur la structure des index Lucene dans la [documentation Oak.](https://jackrabbit.apache.org/oak/docs/query/lucene.html#index-definition)

#### Code non conforme {#non-compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - type: lucene
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

#### Code conforme {#compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Les index Lucene Oak de ressource DAM personnalisés sont correctement structurés.  {#oakpal-damAssetLucene-sanity-check}

* **Clé** : IndexDamAssetLucene
* **Type** : bogue
* **Gravité** : bloqueur
* **Depuis** : 2021.6.0

Pour que la recherche de ressources fonctionne correctement dans AEM Assets, les personnalisations de l’index Oak `damAssetLucene` doivent suivre un ensemble de directives spécifiques à cet index. Cette règle vérifie que la définition d’index doit avoir une propriété à plusieurs valeurs nommée `tags` qui contient la valeur `visualSimilaritySearch`.

#### Code non conforme {#non-compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - type: lucene
      + tika
        + config.xml
```

#### Code conforme {#compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - reindex: false
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Les packages des clients ne doivent ni créer ni modifier les nœuds sous /libs {#oakpal-customer-package}

* **Clé** : BannedPath
* **Type** : bogue
* **Gravité** : critique
* **Depuis** : version 2019.6.0

En guise de bonne pratique, il a été établi depuis longtemps que l’arborescence de contenu `/libs` dans le référentiel de contenu AEM doit être considérée comme étant en lecture seule par les clients. La modification des nœuds et des propriétés sous `/libs` crée un risque significatif pour les mises à jour majeures et mineures. Les modifications apportées à `/libs` ne doivent être effectuées que par Adobe par le biais de canaux officiels.

### Les packages ne doivent pas contenir de configurations OSGi en double {#oakpal-package-osgi}

* **Clé** : DuplicateOsgiConfigurations
* **Type** : bogue
* **Gravité** : majeure
* **Depuis** : version 2019.6.0

Le fait qu’un même composant OSGi soit configuré plusieurs fois est un problème courant qui se produit sur les projets complexes. Cela crée une ambiguïté sur la configuration qui sera exploitable. Cette règle est « compatible avec le mode d’exécution » en ce qu’elle identifie uniquement les problèmes où le même composant est configuré plusieurs fois dans le même mode d’exécution ou la même combinaison de modes d’exécution.

>[!NOTE]
>
>Cette règle crée des problèmes lorsque la même configuration, pour le même chemin, est définie dans plusieurs packages, y compris dans les cas où le même package est dupliqué dans la liste globale des packages créés.
>
>Par exemple, si la génération produit des packages nommés `com.myco:com.myco.ui.apps` et `com.myco:com.myco.all`, où `com.myco:com.myco.all` contient `com.myco:com.myco.ui.apps`, toutes les configurations de `com.myco:com.myco.ui.apps` seront signalées comme doublons.
>
>Il s’agit généralement d’un cas où les [Consignes relatives à la structure du module de contenu n’ont pas été suivies.](/help/implementing/developing/introduction/aem-project-content-package-structure.md). Dans cet exemple spécifique, la propriété `<cloudManagerTarget>none</cloudManagerTarget>` est absente du module `com.myco:com.myco.ui.apps`.

#### Code non conforme {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Code conforme {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Les dossiers de configuration et d’installation ne doivent contenir que des nœuds OSGi {#oakpal-config-install}

* **Clé** : ConfigAndInstallShouldOnlyContainOsgiNodes
* **Type** : bogue
* **Gravité** : majeure
* **Depuis** : version 2019.6.0

Pour des raisons de sécurité, les chemins contenant `/config/` et `/install/` ne sont lisibles que par les utilisateurs administratifs dans AEM et doivent être utilisés uniquement pour la configuration OSGi et les lots OSGi. Placer d’autres types de contenu sous les chemins contenant ces segments donne un comportement d’application qui varie involontairement entre les utilisateurs administratifs et non administrateurs.

Un problème courant est l’utilisation de nœuds nommés `config` dans les boîtes de dialogue des composants ou lors de la spécification de la configuration de l’éditeur de texte enrichi pour la modification statique. Pour résoudre ce problème, le nœud incriminé doit être renommé avec un nom compatible. Pour la configuration de l’éditeur de texte enrichi, utilisez la propriété `configPath` sur le nœud `cq:inplaceEditing` pour spécifier le nouvel emplacement.

#### Code non conforme {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Code conforme {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Les packages ne doivent pas se chevaucher {#oakpal-no-overlap}

* **Clé** : PackageOverlaps
* **Type** : bogue
* **Gravité** : majeure
* **Depuis** : version 2019.6.0

Tout comme la règle [Les packages ne doivent pas contenir de configurations OSGi en double](#oakpal-package-osgi), il s’agit d’un problème courant sur les projets complexes où le même chemin de nœud est écrit par plusieurs packages de contenu distincts. Bien que l’utilisation des dépendances des packages de contenu puisse servir à garantir un résultat cohérent, il est préférable d’éviter tout chevauchement.

### Le mode de création par défaut ne doit pas être défini sur Interface utilisateur classique {#oakpal-default-authoring}

* **Clé** : ClassicUIAuthoringMode
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

La configuration OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` définit le mode de création par défaut dans AEM. Comme [l’interface utilisateur classique est abandonnée depuis AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=fr), un problème survient lorsque le mode de création par défaut est configuré sur l’interface utilisateur classique.

### Les boîtes de dialogue de composants doivent être de type interface utilisateur tactile {#oakpal-components-dialogs}

* **Clé** : ComponentWithOnlyClassicUIDialog
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

Les composants AEM disposant d’une boîte de dialogue d’interface utilisateur classique doivent toujours avoir une boîte de dialogue d’interface utilisateur tactile correspondante. Ainsi, l’expérience de création est optimale et la compatibilité avec le modèle de déploiement Cloud Service, où l’interface utilisateur classique n’est pas prise en charge, est assurée. Cette règle vérifie les scénarios suivants :

* Un composant doté d’une boîte de dialogue d’interface utilisateur classique (c’est-à-dire un nœud enfant `dialog`) doit avoir une boîte de dialogue d’interface utilisateur tactile correspondante (c’est-à-dire un nœud enfant `cq:dialog`).
* Un composant doté d’une boîte de dialogue d’interface utilisateur classique (c’est-à-dire un nœud `design_dialog`) doit avoir une boîte de dialogue de conception d’interface utilisateur tactile correspondante (c’est-à-dire un nœud enfant `cq:design_dialog`).
* Un composant doté d’une boîte de dialogue d’interface utilisateur classique et d’une boîte de dialogue de conception d’interface utilisateur classique doit comporter à la fois une boîte de dialogue d’interface utilisateur tactile correspondante et une boîte de dialogue de conception d’interface utilisateur tactile correspondante.

La documentation des outils de modernisation d’AEM contient des documents et des outils pour convertir les composants de l’interface utilisateur classique en interface utilisateur tactile. Consultez la [documentation relative aux outils de modernisation d’AEM](https://opensource.adobe.com/aem-modernize-tools/pages/tools.html) pour en savoir plus.

### Les packages ne doivent pas combiner du contenu modifiable et non modifiable {#oakpal-packages-immutable}

* **Clé** : ImmutableMutableMixedPackage
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

Pour être compatible avec le modèle de déploiement Cloud Service, les packages de contenu individuels doivent contenir du contenu pour les zones non modifiables du référentiel (c’est-à-dire, `/apps` et `/libs`) ou la zone modifiable (c’est-à-dire, tout ce qui ne se trouve pas dans `/apps` ou `/libs`), mais pas les deux. Par exemple, un package contenant à la fois `/apps/myco/components/text and /etc/clientlibs/myco` est incompatible avec Cloud Service et provoquera la notification d’un problème.

>[!NOTE]
>
>La règle [Les packages de clients ne doivent ni créer ni modifier de nœuds sous /libs](#oakpal-customer-package) s’applique toujours.

Pour plus d’informations, voir [Structure de projet AEM](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

### Les agents de réplication inverse ne doivent pas être utilisés {#oakpal-reverse-replication}

* **Clé** : ReverseReplication
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

La prise en charge de la réplication inverse n’est pas disponible dans les déploiements de Cloud Service, comme décrit dans les [notes de mise à jour](/help/release-notes/aem-cloud-changes.md#replication-agents) d’AEM as a Cloud Service.

Les clients qui utilisent la réplication inverse doivent contacter Adobe pour obtenir d’autres solutions.

### Les ressources contenues dans les bibliothèques clientes activées par proxy doivent se trouver dans un dossier nommé ressources {#oakpal-resources-proxy}

* **Clé** : ClientlibProxyResource
* **Type** : bogue
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Les bibliothèques clientes AEM peuvent contenir des ressources statiques telles que des images et des polices. Comme décrit dans le document [Utilisation de préprocesseurs](/help/implementing/developing/introduction/clientlibs.md#using-preprocessors), lorsque vous utilisez des bibliothèques clientes activées par proxy, ces ressources statiques doivent être contenues dans un dossier enfant nommé `resources` afin d’être référencées efficacement sur les instances de publication.

#### Code non conforme {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Code conforme {#compliant-proxy-enabled}

```tet
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Utilisation de processus de workflow non compatibles avec Cloud Service {#oakpal-usage-cloud-service}

* **Clé** : CloudServiceIncompatibleWorkflowProcess
* **Type** : bogue
* **Gravité** : majeure
* **Depuis** : version 2021.2.0

Avec l’adoption de micro-services Assets pour le traitement des ressources dans AEM as a Cloud Service, plusieurs processus de workflow utilisés dans les versions on-premise et AMS d’AEM ne sont plus pris en charge ou sont devenus inutiles.

L’outil de migration dans le [référentiel GitHub d’AEM Assets as a Cloud Service](https://github.com/adobe/aem-cloud-migration) peut être utilisé pour mettre à jour les modèles de workflow lors de la migration vers AEM as a Cloud Service.

### L’utilisation de modèles statiques est découragée en faveur de modèles modifiables {#oakpal-static-template}

* **Clé** : StaticTemplateUsage
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Bien que l’utilisation de modèles statiques ait toujours été très fréquente dans les projets AEM, les modèles modifiables sont fortement recommandés, car ils offrent la plus grande flexibilité et prennent en charge les fonctionnalités supplémentaires qui ne sont pas présentes dans les modèles statiques. Vous trouverez plus d’informations à ce sujet dans le document [Modèles de page.](/help/implementing/developing/components/templates.md)

La migration de modèles statiques vers des modèles modifiables peut être largement automatisée à l’aide des [outils de modernisation d’AEM](https://opensource.adobe.com/aem-modernize-tools/).

### L’utilisation des composants de base hérités n’est pas encouragée {#oakpal-usage-legacy}

* **Clé** : LegacyFoundationComponentUsage
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Les composants de base hérités (c’est-à-dire les composants situés dans `/libs/foundation`) ont été [abandonnés pour plusieurs versions d’AEM](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html) au profit des composants principaux. L’utilisation des composants de base comme base pour les composants personnalisés, que ce soit par recouvrement ou par héritage, n’est pas encouragée et ces composants doivent être convertis en composants principaux correspondants.

Cette conversion peut être facilitée par les [outils de modernisation d’AEM](https://opensource.adobe.com/aem-modernize-tools/).

### Seuls les noms et les ordres de modes d’exécution pris en charge doivent être utilisés {#oakpal-supported-runmodes}

* **Clé** : SupportedRunmode
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM as a Cloud Service applique une politique de dénomination stricte pour les noms des modes d’exécution et un ordre strict pour ces modes d’exécution. La liste des modes d’exécution pris en charge se trouve dans le document [Déploiement vers AEM as a Cloud Service](/help/implementing/deploying/overview.md#runmodes) et toute déviation est identifiée comme un problème.

### Les nœuds de définition d’index de recherche personnalisée doivent être des enfants directs de /oak:index {#oakpal-custom-search}

* **Clé** : OakIndexLocation
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM as a Cloud Service exige que les définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) soient des nœuds enfants directs de `/oak:index`. Les index qui se trouvent à des emplacements différents doivent être déplacés pour être compatibles avec AEM as a Cloud Service. Vous trouverez plus d’informations sur les index de recherche dans le document [Recherche et indexation de contenu](/help/operations/indexing.md).

### Les nœuds de définition d’index de recherche personnalisée doivent avoir une compatVersion de 2 {#oakpal-custom-search-compatVersion}

* **Clé** : IndexCompatVersion
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM as a Cloud Service exige que la propriété `compatVersion` soit définie sur `2` pour les définitions d’index de recherche personnalisée (c’est-à-dire pour les nœuds de type `oak:QueryIndexDefinition`). AEM as a Cloud Service ne prend en charge aucune autre valeur. Vous trouverez plus d’informations sur les index de recherche dans [Recherche et indexation de contenu.](/help/operations/indexing.md)

### Les nœuds descendants des nœuds de définition d’index de recherche personnalisée doivent être de type nt:unstructured {#oakpal-descendent-nodes}

* **Clé** : IndexDescendantNodeType
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Des problèmes difficiles à résoudre peuvent survenir lorsqu’un nœud de définition d’index de recherche personnalisée comporte des nœuds enfants non ordonnés. Pour éviter cette situation, il est recommandé que tous les nœuds descendants d’un nœud `oak:QueryIndexDefinition` soient de type `nt:unstructured`.

### Les nœuds de définition d’index de recherche personnalisée doivent contenir un nœud enfant nommé indexRules qui a des enfants {#oakpal-custom-search-index}

* **Clé** : IndexRulesNode
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Un nœud de définition d’index de recherche personnalisée correctement défini doit contenir un nœud enfant appelé `indexRules` qui, à son tour, doit avoir au moins un enfant. Vous trouverez plus d’informations à ce sujet dans la [documentation d’Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Les nœuds de définition d’index de recherche personnalisée doivent respecter les conventions d’attribution de noms {#oakpal-custom-search-definitions}

* **Clé** : IndexName
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM as a Cloud Service exige que les définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) soient nommés selon un modèle spécifique décrit dans le document [Recherche et indexation de contenu.](/help/operations/indexing.md)

### Les nœuds de définition d’index de recherche personnalisée doivent utiliser le type d’index lucene  {#oakpal-index-type-lucene}

* **Clé** : IndexType
* **Type** : bogue
* **Gravité** : bloqueur
* **Depuis** : version 2021.2.0 (changement de type et de gravité en 2021.8.0)

AEM as a Cloud Service exige que les définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) aient une propriété `type` dont la valeur est définie sur `lucene`. L’indexation avec ces types d’index hérités doit être mise à jour avant la migration vers AEM as a Cloud Service. Consultez le document [Recherche et indexation de contenu](/help/operations/indexing.md#how-to-use) pour en savoir plus.

### Les nœuds de définition d’index de recherche personnalisée ne doivent pas contenir de propriété nommée seed {#oakpal-property-name-seed}

* **Clé** : IndexSeedProperty
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM as a Cloud Service interdit aux définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) de contenir une propriété nommée `seed`. L’indexation avec cette propriété doit être mise à jour avant la migration vers AEM as a Cloud Service. Consultez le document [Recherche et indexation de contenu](/help/operations/indexing.md#how-to-use) pour en savoir plus.

### Les nœuds de définition d’index de recherche personnalisée ne doivent pas contenir de propriété nommée reindex {#oakpal-reindex-property}

* **Clé** : IndexReindexProperty
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

AEM as a Cloud Service interdit aux définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) de contenir une propriété nommée `reindex`. L’indexation avec cette propriété doit être mise à jour avant la migration vers AEM as a Cloud Service. Consultez le document [Recherche et indexation de contenu](/help/operations/indexing.md#how-to-use) pour en savoir plus.
