---
title: Règles de qualité du code personnalisé
description: Découvrez Cloud Manager des règles de qualité du code personnalisé, basées sur les bonnes pratiques en matière d’ingénierie de Adobe Experience Manager, pour garantir un code de haute qualité grâce à des tests approfondis.
exl-id: f40e5774-c76b-4c84-9d14-8e40ee6b775b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2573eb5f8a8ff21a8e30b94287b554885cd1cd89
workflow-type: tm+mt
source-wordcount: '4421'
ht-degree: 66%

---

# Règles de qualité du code personnalisé {#custom-code-quality-rules}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_customcodequalityrules"
>title="Règles de qualité du code personnalisé"
>abstract="Découvrez Cloud Manager des règles de qualité du code personnalisé, basées sur les bonnes pratiques en matière d’ingénierie de Adobe Experience Manager, pour garantir un code de haute qualité grâce à des tests approfondis."

Découvrez Cloud Manager des règles de qualité du code personnalisé, basées sur les bonnes pratiques en matière d’ingénierie de Adobe Experience Manager, pour garantir un code de haute qualité grâce à des tests approfondis. Voir aussi [test de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md).

>[!NOTE]
>
>Les règles SonarQube complètes ne peuvent pas être téléchargées en raison des informations propriétaires d’Adobe. Vous pouvez télécharger la liste complète des règles [via ce lien](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx). Poursuivez la lecture de ce document pour obtenir des descriptions et des exemples de règles.

>[!NOTE]
>
>Les exemples de code utilisés ici ne sont fournis qu’à titre d’illustration. Consultez la [Documentation sur les concepts](https://docs.sonarsource.com/sonarqube/latest/) SonarQube pour en savoir plus sur les concepts et les règles de qualité de SonarQube.

## Règles SonarQube {#sonarqube-rules}

La section suivante détaille les règles SonarQube exécutées par Cloud Manager.

### N’utilisez pas de fonctions potentiellement dangereuses {#do-not-use-potentially-dangerous-functions}

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

### N’utilisez pas de chaînes de format pouvant être contrôlées en externe. {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Clé** : CQRules:CWE-134
* **Type** : vulnérabilité
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

L’utilisation d’une chaîne de format provenant d’une source externe (telle qu’un paramètre de requête ou un contenu créé par l’utilisateur ou l’utilisatrice) peut exposer une application aux attaques par déni de service. Dans certains cas, une chaîne de format peut être contrôlée en externe, mais elle n’est autorisée que si elle provient de sources approuvées.

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

Lors de l’exécution de requêtes HTTP dans une application Experience Manager, il est essentiel de configurer les délais d’expiration appropriés afin d’éviter toute consommation inutile de threads.
Par défaut, le client HTTP Java™ (java.net.HttpUrlConnection) et le client de composants HTTP Apache largement utilisé n’imposent pas de délai d’expiration. Ils doivent donc être configurés manuellement. En règle générale, les délais d’expiration doivent être définis sur 60 secondes ou moins.

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

public void orDoThis () {
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

### Toujours fermer les objets ResourceResolver {#resourceresolver-objects-should-always-be-closed}

* **Clé** : CQRules:CQBP-72
* **Type** : code smell
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

Les objets ResourceResolver obtenus à partir de `ResourceResolverFactory` consomment des ressources système. Bien qu’il existe des mesures pour récupérer ces ressources lorsqu’un objet `ResourceResolver` n’est plus en cours d’utilisation, il est plus efficace de fermer explicitement tous les objets `ResourceResolver` ouverts en appelant la méthode `close()`.

Une idée fausse courante est que les objets `ResourceResolver` créés avec une session JCR existante ne doivent pas être fermés explicitement ou que leur fermeture affecte la session JCR. Cette information est incorrecte. Un `ResourceResolver` doit toujours être fermé lorsqu’il n’est plus nécessaire. Puisque `ResourceResolver` implémente l&#39;interface `Closeable`, vous pouvez également utiliser la syntaxe `try-with-resources` au lieu d&#39;appeler `close()` directement.

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

### N’utilisez pas les chemins de servlet Sling pour enregistrer les servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Clé** : CQRules:CQBP-75
* **Type** : code smell
* **Gravité** : majeure
* **Depuis** : version 2018.4.0

Comme décrit dans la [documentation Sling](https://sling.apache.org/documentation/the-sling-engine/servlets.html), il est déconseillé de lier les servlets aux chemins. Les servlets liés au chemin ne peuvent pas utiliser les contrôles d’accès JCR standard et, par conséquent, nécessitent une rigueur de sécurité supplémentaire. Plutôt que d’utiliser des servlets liés au chemin d’accès, il est recommandé de créer des nœuds dans le référentiel et d’enregistrer les servlets par type de ressource.

#### Code non conforme {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Les exceptions capturées doivent être consignées ou renvoyées, mais pas les deux. {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Clé** : CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

En règle générale, une exception doit être consignée une seule fois. La journalisation d’exceptions à plusieurs reprises peut prêter à confusion. La raison en est qu’il n’est pas clair combien de fois une exception s’est produite. Le modèle le plus courant qui mène à cet effet est la journalisation et le lancement d’une exception capturée.

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

Un autre schéma courant à éviter consiste à consigner un message, puis à émettre immédiatement une exception. Cette pratique indique généralement que le message d’exception sera dupliqué dans les fichiers journaux.

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

### Évitez de journaliser les informations lors de la gestion des requêtes GET ou HEAD {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Clé** : CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Type** : code smell
* **Gravité** : mineure

En règle générale, le niveau de journalisation INFO doit être utilisé pour délimiter les actions importantes et, par défaut, Experience Manager est configuré pour le journal au niveau INFO ou au-dessus. Les méthodes GET et HEAD ne doivent jamais être en lecture seule et ne constituent donc pas des actions importantes. La journalisation au niveau INFO en réponse aux demandes GET ou HEAD est susceptible de créer un bruit journal significatif, rendant ainsi plus difficile l’identification des informations utiles dans les fichiers journaux. Lorsque vous gérez des requêtes GET ou HEAD, connectez-vous aux niveaux AVERTISSEMENT ou ERREUR si quelque chose ne s’est pas passé. Utilisez les niveaux DEBUG ou TRACE si des informations de dépannage détaillées sont nécessaires.

>[!NOTE]
>
>Ne s’applique pas à la journalisation de type `access.log` pour chaque requête.

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

### N’utilisez pas Exception.getMessage() comme premier paramètre d’une instruction de journalisation {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Clé** : CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Il est recommandé que les messages de journal fournissent des informations contextuelles sur l’emplacement d’une exception dans l’application. Bien que le contexte puisse également être déterminé par l’utilisation des arborescences des appels de procédure, il est généralement plus facile de lire et de comprendre le message du journal. Par conséquent, lors de la journalisation d’une exception, il est déconseillé d’utiliser le message de l’exception comme message du journal. Le message d’exception explique ce qui s’est passé, tandis que le message du journal doit informer le lecteur de ce que faisait l’application lorsque l’exception s’est produite. Le message d’exception est toujours journalisé. En spécifiant votre propre message, les journaux sont plus faciles à comprendre.

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

Comme le suggère leur nom, les exceptions Java™ doivent toujours être utilisées dans des circonstances exceptionnelles. Par conséquent, lorsqu’une exception est capturée, il est important de s’assurer que les messages du journal sont consignés au niveau approprié, AVERTISSEMENT ou ERREUR. Ce processus permet de s’assurer que ces messages s’affichent correctement dans les logs.

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

Comme nous l’avons mentionné, le contexte est essentiel lors de la compréhension des messages du journal. L’utilisation d’`Exception.printStackTrace()` entraîne seulement la sortie de l’arborescence des appels de procédure dans le flux d’erreurs standard, ce qui provoque la perte de tout le contexte. De plus, dans une application multi-thread telle qu’Experience Manager, si plusieurs exceptions sont imprimées à l’aide de cette méthode en parallèle, leurs arborescences des appels de procédure peuvent se chevaucher, ce qui prête à confusion. Les exceptions ne doivent être consignées que dans la structure de journalisation.

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

### Ne générez pas de sortie standard ou d’erreur standard. {#do-not-output-to-standard-output-or-standard-error}

* **Clé** : CQRules:CQBP-44—LogLevelConsolePrinters
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

La journalisation sur Experience Manager doit toujours être effectuée via le cadre de journalisation (SLF4J). La génération directe de la sortie standard ou des flux d’erreur standard perd les informations structurelles et contextuelles fournies par le cadre de journalisation. Parfois, cela peut entraîner des problèmes de performances.

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

### Éviter les chemins d’accès aux applications et libs codés en dur {#avoid-hardcoded-apps-and-libs-paths}

* **Clé** : CQRules:CQBP-71
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2018.4.0

Les chemins commençant par `/libs` et `/apps` ne doivent généralement pas être codés en dur. Ces chemins sont généralement stockés par rapport au chemin de recherche Sling, qui est par défaut de `/libs,/apps`. L’utilisation du chemin absolu peut introduire des défauts discrets qui n’apparaîtront que plus tard dans le cycle de vie du projet.

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

### N’utilisez pas le planificateur Sling. {#sonarqube-sling-scheduler}

* **Clé** : CQRules:AMSCORE-554
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

N’utilisez pas le planificateur Sling pour les tâches qui nécessitent une exécution garantie. Les tâches planifiées Sling garantissent l’exécution et conviennent mieux aux environnements organisés avec ou sans grappes.

Consultez [Gestion des tâches et des événements Apache Sling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) pour en savoir plus sur la façon dont les tâches Sling sont gérées dans des environnements en cluster.

### N’utilisez pas d’API obsolètes d’Experience Manager. {#sonarqube-aem-deprecated}

* **Clé** : AMSCORE-553
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

La surface de l’API Experience Manager fait l’objet d’une révision continue afin d’identifier les API dont l’utilisation est déconseillée et qui sont donc considérées comme obsolètes.

Dans de nombreux cas, ces API sont abandonnées en y associant l’annotation standard Java™ `@Deprecated`. Elles sont à ce titre identifiées par la mention `squid:CallToDeprecatedMethod`.

Cependant, il arrive qu’une API devienne obsolète dans le contexte d’Experience Manager, mais pas dans d’autres contextes. Cette règle identifie cette deuxième classe.

### N’utilisez pas @Inject annotation avec @Optional dans les modèles Sling {#sonarqube-slingmodels-inject-optional}

* **Clé** : InjectAnnotationWithOptionalInjectionCheck
* **Type** : Qualité logicielle
* **Gravité** : mineure
* **Depuis** : version 2023.11

Le projet Apache Sling décourage l’utilisation de l’annotation `@Inject` dans le contexte des modèles Sling, car cela peut entraîner de mauvaises performances lorsqu’elle est combinée avec l’élément `DefaultInjectionStrategy.OPTIONAL` (au niveau du champ ou de la classe). À la place, des injections plus spécifiques (telles que les annotations `@ValueMapValue` ou `@OsgiInjector`) doivent être utilisées.

Pour plus d’informations sur les annotations recommandées et sur les raisons pour lesquelles cette recommandation a été faite, consultez la [documentation Apache Sling](https://sling.apache.org/documentation/bundles/models.html#discouraged-annotations-1).


### Réutilisation des instances d’un client HTTPC {#sonarqube-reuse-httpclient}

* **Clé** : AEMSRE-870
* **Type** : Qualité logicielle
* **Gravité** : mineure
* **Depuis** : version 2023.11

AEM applications atteignent souvent d’autres applications à l’aide du protocole HTTP, et Apache HttpClient est une bibliothèque souvent utilisée à cette fin. Mais la création d’un tel objet HttpClient s’accompagne d’une surcharge. Ces objets doivent donc être réutilisés autant que possible.

Cette règle vérifie qu’un tel objet HttpClient n’est pas privé dans une méthode, mais global au niveau de la classe, afin qu’il puisse être réutilisé. Dans ce cas, le champ HttpClient doit être défini dans le constructeur de la classe ou de la méthode `activate()` (si cette classe est un composant/service OSGi).

Consultez le [Guide d’optimisation](https://hc.apache.org/httpclient-legacy/performance.html) de HttpClient pour connaître quelques bonnes pratiques concernant l’utilisation de HttpClient.

#### Code non conforme {#non-compliant-code-14}

```java
public void doHttpCall() {
  HttpClient httpclient = HttpClients.createDefault();
  // do something with the httpclient
}
```

#### Code conforme {#compliant-code-11}

```java
public class myClass {

  HttpClient httpclient;

  public void doHttpCall() {
    // do something with the httpclient
  }

}
```

## Règles de contenu OakPAL {#oakpal-rules}

La section suivante présente les vérifications OakPAL exécutées par Cloud Manager.

>[!NOTE]
>
>OakPAL est une structure qui valide les packages de contenu à l’aide d’un référentiel Oak autonome. Un partenaire Experience Manager, qui a remporté le prix Rockstar North America 2019, l&#39;Experience Manager, l&#39;a développé.

### Les clients ne doivent pas implémenter ni étendre les API de produit annotées avec @ProviderType{#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Clé** : CQBP-84
* **Type** : bogue
* **Gravité** : critique
* **Depuis** : version 2018.7.0

L’API Experience Manager contient des interfaces et des classes Java™, qui sont destinées uniquement à être utilisées (mais pas implémentées) par du code personnalisé. Par exemple, seul l’Experience Manager doit implémenter l’interface `com.day.cq.wcm.api.Page`.

Lorsque de nouvelles méthodes sont ajoutées à ces interfaces, ces méthodes supplémentaires n’affectent pas le code existant qui utilise ces interfaces. Par conséquent, l’ajout de nouvelles méthodes à ces interfaces est considéré comme rétrocompatible. Cependant, si le code personnalisé implémente l’une de ces interfaces, il introduit un risque de rétrocompatibilité pour le client ou la cliente.

Les interfaces et les classes, telles qu’implémentées par Experience Manager, comportent l’annotation `org.osgi.annotation.versioning.ProviderType` ou parfois une annotation héritée similaire `aQute.bnd.annotation.ProviderType`. Cette règle identifie les cas où le code personnalisé met en oeuvre une telle interface ou étend une classe .

#### Code non conforme {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Les index Lucene Oak personnalisés doivent avoir une configuration Tika. {#oakpal-indextikanode}

* **Clé** : IndexTikaNode
* **Type** : bogue
* **Gravité** : bloqueur
* **Depuis** : 2021.8.0

Plusieurs index prêts à l’emploi Experience Manager Oak incluent une configuration Tika et les personnalisations de ces index doivent contenir une configuration Tika. Cette règle recherche les personnalisations des index `damAssetLucene`, `lucene` et `graphqlConfig`, et soulève un problème si le nœud `tika` est manquant ou si un nœud enfant nommé `config.xml` est manquant dans le nœud `tika`.

Pour plus d’informations sur la personnalisation des définitions d’index, consultez la [documentation sur l’indexation](/help/operations/indexing.md#preparing-the-new-index-definition).

#### Code non conforme {#non-compliant-code-indextikanode}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
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

Les index Oak de type `lucene` doivent toujours être indexés de manière asynchrone. Sinon, le système risque d’être instable. Vous trouverez plus d’informations sur la structure des index Lucene dans la [documentation Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html#index-definition).

#### Code non conforme {#non-compliant-code-indexasync}

```text
+ oak:index
    + damAssetLucene-1-custom
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
      - type: lucene
      - tags: [visualSimilaritySearch]
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
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Les index Lucene Oak de ressource DAM personnalisés sont correctement structurés. {#oakpal-damAssetLucene-sanity-check}

* **Clé** : IndexDamAssetLucene
* **Type** : bogue
* **Gravité** : bloqueur
* **Depuis** : 2021.6.0

Pour que la recherche de ressources fonctionne correctement dans Experience Manager Assets, les personnalisations de l’index Oak `damAssetLucene` doivent suivre un ensemble de directives spécifiques à cet index. Cette règle vérifie que la définition d’index doit avoir une propriété à plusieurs valeurs nommée `tags`, qui contient la valeur `visualSimilaritySearch`.

#### Code non conforme {#non-compliant-code-damAssetLucene}

```text
+ oak:index
    + damAssetLucene-1-custom
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: /content/dam
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
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Les packages client ne doivent pas créer ni modifier de noeuds sous libs {#oakpal-customer-package}

* **Clé** : BannedPath
* **Type** : bogue
* **Gravité** : critique
* **Depuis** : version 2019.6.0

En guise de bonne pratique, il a été établi depuis longtemps que l’arborescence de contenu `/libs` dans le référentiel de contenu Experience Manager doit être considérée comme étant en lecture seule par les clients. La modification des nœuds et des propriétés sous `/libs` crée un risque significatif pour les mises à jour majeures et mineures. Utilisez Adobe, via les canaux officiels, pour apporter des modifications à `/libs`.

### Les packages ne doivent pas contenir de configurations OSGi en double. {#oakpal-package-osgi}

* **Clé** : DuplicateOsgiConfigurations
* **Type** : bogue
* **Gravité** : majeure
* **Depuis** : version 2019.6.0

Le fait qu’un même composant OSGi soit configuré plusieurs fois est un problème courant qui se produit sur les projets complexes. Cela crée une ambiguïté sur la configuration qui sera applicable. Cette règle est « compatible avec le mode d’exécution » en ce qu’elle identifie uniquement les problèmes où le même composant est configuré plusieurs fois dans le même mode d’exécution ou la même combinaison de modes d’exécution.

>[!NOTE]
>
>Cette règle crée des problèmes lorsque la même configuration, pour le même chemin, est définie dans plusieurs packages, y compris dans les cas où le même package est dupliqué dans la liste globale des packages créés.
>
>Par exemple, si la création génère des packages nommés `com.myco:com.myco.ui.apps` et `com.myco:com.myco.all`, où `com.myco:com.myco.all` contient `com.myco:com.myco.ui.apps`, toutes les configurations dans `com.myco:com.myco.ui.apps` seront signalées comme doublons.
>
>En règle générale, cette situation est le cas où vous ne respectez pas les [directives de structure de module de contenu](/help/implementing/developing/introduction/aem-project-content-package-structure.md). Dans cet exemple, la propriété `<cloudManagerTarget>none</cloudManagerTarget>` est manquante dans le package `com.myco:com.myco.ui.apps`.

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

Pour des raisons de sécurité, les chemins contenant `/config/` et `/install/` ne sont lisibles que par les utilisateurs administratifs dans Experience Manager et doivent être utilisés uniquement pour la configuration OSGi et les paquets OSGi. Le placement d’autres types de contenu sous des chemins contenant ces segments entraîne involontairement la différence de comportement de l’application entre les utilisateurs administratifs et non administrateurs.

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

### Les packages ne doivent pas se chevaucher. {#oakpal-no-overlap}

* **Clé** : PackageOverlaps
* **Type** : bogue
* **Gravité** : majeure
* **Depuis** : version 2019.6.0

Tout comme la règle [Les packages ne doivent pas contenir de configurations OSGi en double](#oakpal-package-osgi), cette situation est un problème courant sur les projets complexes où le même chemin de noeud est écrit par plusieurs packages de contenu distincts. Bien que l’utilisation des dépendances des packages de contenu puisse servir à garantir un résultat cohérent, il est préférable d’éviter tout recouvrement.

### Le mode de création par défaut ne doit pas être une IU classique {#oakpal-default-authoring}

* **Clé** : ClassicUIAuthoringMode
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

La configuration OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` définit le mode de création par défaut dans Experience Manager. Comme l’interface utilisateur classique a été abandonnée depuis Experience Manager 6.4, un problème se produit lorsque le mode de création par défaut est configuré sur l’interface utilisateur classique.

### Les composants avec boîtes de dialogue doivent avoir des boîtes de dialogue d’interface utilisateur tactile. {#oakpal-components-dialogs}

* **Clé** : ComponentWithOnlyClassicUIDialog
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

Les composants Experience Manager disposant d’une boîte de dialogue d’interface utilisateur classique doivent toujours comporter une boîte de dialogue d’interface utilisateur tactile correspondante. Toutes deux offrent une expérience de création optimale compatible avec le modèle de déploiement Cloud Service, où l’interface utilisateur classique n’est plus prise en charge. Cette règle vérifie les scénarios suivants :

* Un composant doté d’une boîte de dialogue d’interface utilisateur classique (c’est-à-dire un nœud enfant `dialog`) doit avoir une boîte de dialogue d’interface utilisateur tactile correspondante (c’est-à-dire un nœud enfant `cq:dialog`).
* Un composant doté d’une boîte de dialogue d’interface utilisateur classique (c’est-à-dire un nœud `design_dialog`) doit avoir une boîte de dialogue de conception d’interface utilisateur tactile correspondante (c’est-à-dire un nœud enfant `cq:design_dialog`).
* Un composant doté d’une boîte de dialogue d’interface utilisateur classique et d’une boîte de dialogue de conception d’interface utilisateur classique doit comporter à la fois une boîte de dialogue d’interface utilisateur tactile correspondante et une boîte de dialogue de conception d’interface utilisateur tactile correspondante.

La documentation sur les outils de modernisation d’Experience Manager contient des documents et des outils pour convertir les composants de l’interface utilisateur classique en interface utilisateur tactile. Consultez la [documentation relative aux outils de modernisation d’Experience Manager](https://opensource.adobe.com/aem-modernize-tools/) pour en savoir plus.

### Les packages ne doivent pas combiner du contenu modifiable et non modifiable. {#oakpal-packages-immutable}

* **Clé** : ImmutableMutableMixedPackage
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

Pour être compatible avec le modèle de déploiement sdu service cloud, les packages de contenu individuels doivent contenir du contenu pour les zones non modifiables du référentiel (c’est-à-dire, `/apps` et `/libs`) ou la zone modifiable (c’est-à-dire, tout ce qui ne se trouve pas dans `/apps` ou `/libs`), mais pas les deux. Par exemple, un package qui comprend à la fois `/apps/myco/components/text` et `/etc/clientlibs/myco` n’est pas compatible avec Cloud Service et provoque le signalement d’un problème.

>[!NOTE]
>
>La règle [Les packages client ne doivent pas créer ni modifier des noeuds sous libs](#oakpal-customer-package) s’applique toujours.

Pour plus d’informations, consultez la section [Structure de projet Experience Manager](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

### N’utilisez pas d’agents de réplication inverse. {#oakpal-reverse-replication}

* **Clé** : ReverseReplication
* **Type** : code smell/comptabilité avec Cloud Service
* **Gravité** : mineure
* **Depuis** : version 2020.5.0

La prise en charge de la réplication inverse n’est pas disponible dans les déploiements de Cloud Service, comme décrit dans les [notes de mise à jour](/help/release-notes/aem-cloud-changes.md#replication-agents) d’Experience Manager as a Cloud Service.

Les client(e)s qui utilisent la réplication inverse doivent contacter Adobe pour obtenir d’autres solutions.

### Les ressources contenues dans les bibliothèques clientes activées par proxy doivent se trouver dans un dossier nommé ressources. {#oakpal-resources-proxy}

* **Clé** : ClientlibProxyResource
* **Type** : bogue
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Les bibliothèques clientes d’Experience Manager peuvent contenir des ressources statiques telles que des images et des polices. Comme décrit dans le document [Utilisation de préprocesseurs](/help/implementing/developing/introduction/clientlibs.md#using-preprocessors), lors de l’utilisation de bibliothèques clientes proxy, ces ressources statiques doivent être contenues dans un dossier enfant nommé `resources` pour être référencées efficacement sur les instances de publication.

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

### Utilisation de Cloud Service incompatible avec les processus de workflow {#oakpal-usage-cloud-service}

* **Clé** : CloudServiceIncompatibleWorkflowProcess
* **Type** : bogue
* **Gravité** : majeure
* **Depuis** : version 2021.2.0

Avec le passage aux micro-services de ressources pour le traitement des ressources dans Adobe Experience Manager as a Cloud Service, plusieurs processus de workflow utilisés dans les versions On-Premise et AMS ne sont désormais plus pris en charge. La plupart de ces workflows sont également devenus inutiles.

L’outil de migration dans le [référentiel GitHub de ressources d’Experience Manager as a Cloud Service](https://github.com/adobe/aem-cloud-migration) peut être utilisé pour mettre à jour les modèles de workflow lors de la migration vers Experience Manager as a Cloud Service.

### L’utilisation de modèles statiques est découragée en faveur de modèles modifiables. {#oakpal-static-template}

* **Clé** : StaticTemplateUsage
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Bien que l’utilisation des modèles statiques soit historiquement courante dans les projets Experience Manager, Adobe recommande les modèles modifiables, car ils offrent la plus grande flexibilité et prennent en charge des fonctionnalités supplémentaires qui ne sont pas présentes dans les modèles statiques. Vous trouverez plus d’informations à ce sujet dans le document [Modèles de page](/help/implementing/developing/components/templates.md).

La migration de modèles statiques vers des modèles modifiables peut être largement automatisée à l’aide des [outils de modernisation Experience Manager](https://opensource.adobe.com/aem-modernize-tools/).

### L’utilisation des composants de base hérités n’est pas encouragée. {#oakpal-usage-legacy}

* **Clé** : LegacyFoundationComponentUsage
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Les composants de base hérités (c’est-à-dire les composants situés dans `/libs/foundation`) ont été abandonnés depuis plusieurs versions d’Experience Manager au profit des composants principaux. L’utilisation des composants de base comme base pour les composants personnalisés, que ce soit par recouvrement ou par héritage, n’est pas encouragée et ces composants doivent être convertis en composants principaux correspondants.

[Les outils de modernisation Experience Manager](https://opensource.adobe.com/aem-modernize-tools/) peuvent faciliter cette conversion.

### Utilisez uniquement les noms et l’ordre des modes d’exécution pris en charge {#oakpal-supported-runmodes}

* **Clé** : SupportedRunmode
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Experience Manager as a Cloud Service applique une stratégie de nommage stricte pour les noms des modes d’exécution et un ordre strict pour ces modes d’exécution. La liste des modes d’exécution pris en charge est créée dans le document [Déploiement sur as a Cloud Service Experience Manager](/help/implementing/deploying/overview.md#runmodes) et toute déviation de cette liste est identifiée comme un problème.

### Les nœuds de définition d’index de recherche personnalisée doivent être des enfants directs de `/oak:index`. {#oakpal-custom-search}

* **Clé** : OakIndexLocation
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Experience Manager as a Cloud Service exige que les définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) soient des nœuds enfants directs de `/oak:index`. Les index qui se trouvent à des emplacements différents doivent être déplacés pour être compatibles avec Experience Manager as a Cloud Service. Vous trouverez plus d’informations sur les index de recherche dans le document [Recherche et indexation de contenu](/help/operations/indexing.md).

### Les nœuds de définition d’index de recherche personnalisée doivent avoir une compatVersion de 2. {#oakpal-custom-search-compatVersion}

* **Clé** : IndexCompatVersion
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Experience Manager as a Cloud Service exige que la propriété `compatVersion` soit définie sur `2` pour les définitions d’index de recherche personnalisée (telles que pour les nœuds de type `oak:QueryIndexDefinition`). Adobe Experience Manager as a Cloud Service ne prend en charge aucune autre valeur. Voir [Recherche et indexation de contenu](/help/operations/indexing.md) pour plus d’informations sur les index de recherche.

### Les nœuds descendants des nœuds de définition d’index de recherche personnalisée doivent être de type `nt:unstructured `.{#oakpal-descendent-nodes}

* **Clé** : IndexDescendantNodeType
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Des problèmes difficiles à résoudre peuvent survenir lorsqu’un nœud de définition d’index de recherche personnalisée comporte des nœuds enfants non ordonnés. Pour éviter cette situation, il est recommandé que tous les nœuds descendants d’un nœud `oak:QueryIndexDefinition` soient de type `nt:unstructured`.

### Les nœuds de définition d’index de recherche personnalisée doivent contenir un nœud enfant nommé indexRules qui a des enfants. {#oakpal-custom-search-index}

* **Clé** : IndexRulesNode
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Un noeud de définition d’index de recherche personnalisé correctement défini doit contenir un noeud enfant nommé `indexRules`, qui doit à son tour comporter au moins un enfant. Vous trouverez plus d’informations à ce sujet dans la [documentation d’Oak](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Les nœuds de définition d’index de recherche personnalisée doivent respecter les conventions de nommage. {#oakpal-custom-search-definitions}

* **Clé** : IndexName
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Experience Manager as a Cloud Service exige que les définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) soient nommées selon un modèle spécifique décrit dans le document [Recherche et indexation de contenu](/help/operations/indexing.md).

### Les nœuds de définition d’index de recherche personnalisée doivent utiliser le type d’index Lucene. {#oakpal-index-type-lucene}

* **Clé** : IndexType
* **Type** : bogue
* **Gravité** : bloqueur
* **Depuis** : version 2021.2.0 (changement de type et de gravité en 2021.8.0)

Experience Manager as a Cloud Service exige que les définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) aient une propriété `type` dont la valeur est définie sur `lucene`. L’indexation avec les types d’index hérités doit être mise à jour avant la migration vers Experience Manager as a Cloud Service. Consultez [Recherche et indexation de contenu](/help/operations/indexing.md#how-to-use) pour plus d’informations.

### Les nœuds de définition d’index de recherche personnalisée ne doivent pas contenir de propriété nommée seed. {#oakpal-property-name-seed}

* **Clé** : IndexSeedProperty
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Experience Manager as a Cloud Service interdit aux définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) de contenir une propriété nommée `seed`. L’indexation avec cette propriété doit être mise à jour avant la migration vers Experience Manager as a Cloud Service. Consultez le document [Recherche et indexation de contenu](/help/operations/indexing.md#how-to-use) pour en savoir plus.

### Les nœuds de définition d’index de recherche personnalisée ne doivent pas contenir de propriété nommée reindex. {#oakpal-reindex-property}

* **Clé** : IndexReindexProperty
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2021.2.0

Experience Manager as a Cloud Service interdit aux définitions d’index de recherche personnalisée (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) de contenir une propriété nommée `reindex`. L’indexation à l’aide de cette propriété doit être mise à jour avant la migration vers Experience Manager en tant que
Cloud Service. Consultez le document [Recherche et indexation de contenu](/help/operations/indexing.md#how-to-use) pour en savoir plus.

### Les noeuds lucene de ressource DAM personnalisés ne doivent pas spécifier `queryPaths` {#oakpal-damAssetLucene-queryPaths}

* **Clé** : IndexDamAssetLucene
* **Type** : bogue
* **Gravité** : bloqueur
* **Depuis** : version 2022.1.0

#### Code non conforme {#non-compliant-code-damAssetLucene-queryPaths}

```text
+ oak:index
    + damAssetLucene-1-custom-1
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: [/content/dam]
      - queryPaths: [/content/dam]
      - type: lucene
      + tika
        + config.xml
```

#### Code conforme {#compliant-code-damAssetLucene-queryPaths}

```text
+ oak:index
    + damAssetLucene-1-custom-2
      - async: [async, nrt]
      - evaluatePathRestrictions: true
      - includedPaths: [/content/dam]
      - tags: [visualSimilaritySearch]
      - type: lucene
      + tika
        + config.xml
```

### Si la définition d’index de recherche personnalisée contient `compatVersion`, elle doit être définie sur 2 {#oakpal-compatVersion}

* **Clé** : IndexCompatVersion
* **Type** : code smell
* **Gravité** : majeure
* **Depuis** : version 2022.1.0


### Le noeud d&#39;index spécifiant `includedPaths` doit également spécifier `queryPaths` avec les mêmes valeurs. {#oakpal-included-paths-without-query-paths}

* **Key** : IndexIncludedPathsWithoutQueryPaths
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2023.1.0

Pour les index personnalisés, configurez `includedPaths` et `queryPaths` avec des valeurs identiques. Si l’un est spécifié, l’autre doit correspondre à l’autre. Cependant, il existe un cas spécial pour les index de `damAssetLucene`, y compris ses versions personnalisées. Pour ces cas, fournissez uniquement `includedPaths`.

### Le noeud d&#39;index spécifiant `nodeScopeIndex` sur le type de noeud générique doit également spécifier `includedPaths` et `queryPaths` {#oakpal-full-text-on-generic-node-type}

* **Clé** : IndexFulltextOnGenericType
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2023.1.0

Lors de la définition de la propriété `nodeScopeIndex` sur un type de noeud &quot;générique&quot; comme `nt:unstructured` ou `nt:base`, vous devez également spécifier les propriétés `includedPaths` et `queryPaths`.
Le type de noeud `nt:base` peut être considéré comme &quot;générique&quot;, car tous les types de noeuds en héritent. Par conséquent, la définition d’un `nodeScopeIndex` sur `nt:base` l’indexe tous les noeuds du référentiel. De même, `nt:unstructured` est également considéré comme &quot;générique&quot;, car il existe de nombreux noeuds dans les référentiels de ce type.

#### Code non conforme {#non-compliant-code-full-text-on-generic-node-type}

```text
+ oak:index/acme.someIndex-custom-1
  - async: [async, nrt]
  - evaluatePathRestrictions: true
  - tags: [visualSimilaritySearch]
  - type: lucene
    + indexRules
      - jcr:primaryType: nt:unstructured
      + nt:base
        - jcr:primaryType: nt:unstructured
        + properties
          + acme.someIndex-custom-1
            - nodeScopeIndex: true
```

#### Code conforme {#compliant-code-full-text-on-generic-node-type}

```text
+ oak:index/acme.someIndex-custom-1
  - async: [async, nrt]
  - evaluatePathRestrictions: true
  - tags: [visualSimilaritySearch]
  - type: lucene
  - includedPaths: ["/content/dam/"] 
  - queryPaths: ["/content/dam/"]
    + indexRules
      - jcr:primaryType: nt:unstructured
      + nt:base
        - jcr:primaryType: nt:unstructured
        + properties
          + acme.someIndex-custom-1
            - nodeScopeIndex: true
```

### La propriété queryLimitReads du moteur de requête ne doit pas être remplacée. {#oakpal-query-limit-reads}

* **Key** : OverrideOfQueryLimitReads
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2023.1.0

Le remplacement de la valeur par défaut peut entraîner des lenteurs de lecture des pages, en particulier lorsque davantage de contenu est ajouté.

### Plusieurs versions actives du même index {#oakpal-multiple-active-versions}

* **Clé** : IndexDetectMultipleActiveVersionsOfSameIndex
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2023.1.0

#### Code non conforme {#non-compliant-code-multiple-active-versions}

```text
+ oak:index
  + damAssetLucene-1-custom-1
    ...
  + damAssetLucene-1-custom-2
    ...
  + damAssetLucene-1-custom-3
    ...
```

#### Code conforme {#compliant-code-multiple-active-versions}

```text
+ damAssetLucene-1-custom-3
    ...
```


### Le nom des définitions d’index entièrement personnalisées doit être conforme aux instructions officielles. {#oakpal-fully-custom-index-name}

* **Clé** : IndexValidFullyCustomName
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2023.1.0

Le modèle attendu pour les noms d’index entièrement personnalisés est : `[prefix].[indexName]-custom-[version]`. Vous trouverez plus d’informations dans le document [Recherche et indexation de contenu](/help/operations/indexing.md).

### Même propriété avec des valeurs analysées différentes dans la même définition d’index {#oakpal-same-property-different-analyzed-values}

#### Code non conforme {#non-compliant-code-same-property-different-analyzed-values}

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
        - analyzed: true
  + dam:cfVariationNode
    + properties
      + status
        - name: status
```

#### Code conforme {#compliant-code-same-property-different-analyzed-values}

Exemple :

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
        - analyzed: true
  + dam:cfVariationNode
    + properties
      + status
        - name: status
        - analyzed: true
```

Exemple :

```text
+ indexRules
  + dam:Asset
    + properties
      + status
        - name: status
  + dam:cfVariationNode
    + properties
      + status
        - name: status
        - analyzed: true
```

Si la propriété analysée n’est pas explicitement définie, sa valeur par défaut est false.

### Propriété Balises {#tags-property}

* **Clé** : IndexHasValidTagsProperty
* **Type** : code smell
* **Gravité** : mineure
* **Depuis** : version 2023.1.0

Pour des index spécifiques, veillez à conserver la propriété tags et ses valeurs actuelles. Bien que l’ajout de nouvelles valeurs à la propriété de balises soit autorisé, la suppression de toutes les valeurs existantes (ou de la propriété dans son ensemble) peut entraîner des résultats inattendus.

### Les nœuds de définition d’index ne doivent pas être déployés dans le module de contenu de l’interface d’utilisation. {#oakpal-ui-content-package}

* **Clé** : IndexNotUnderUIContent
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.6.0

AEM Cloud Service interdit le déploiement de définitions d’index de recherche personnalisées (nœuds de type `oak:QueryIndexDefinition`) dans le package de contenu de l’interface d’utilisation.

>[!WARNING]
>
>Vous devez résoudre ce problème le plus tôt possible, car il peut entraîner des échecs de pipeline à partir de la version d’ [Cloud Manager août 2024](/help/implementing/cloud-manager/release-notes/current.md).

### La définition d’index de texte intégral personnalisé de type damAssetLucene doit comporter le préfixe &quot;damAssetLucene&quot;. {#oakpal-dam-asset-lucene}

* **Clé** : CustomFulltextIndexesOfTheDamAssetCheck
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.6.0

AEM Cloud Service interdit que les définitions d’index en texte intégral personnalisées de type `damAssetLucene` comprennent un préfixe autre que `damAssetLucene`.

>[!WARNING]
>
>Résolvez ce problème dès que possible, car il peut entraîner des échecs de pipeline à partir de la version [Cloud Manager August 2024](/help/implementing/cloud-manager/release-notes/current.md).

### Les nœuds de définition d’index ne doivent pas contenir de propriétés portant le même nom. {#oakpal-index-property-name}

* **Clé** : DuplicateNameProperty
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.6.0

AEM Cloud Service interdit que les définitions d’index de recherche personnalisées (c’est-à-dire les nœuds de type `oak:QueryIndexDefinition`) contiennent des propriétés portant le même nom.

>[!WARNING]
>
>Résolvez ce problème dès que possible, car il peut entraîner des échecs de pipeline à partir de la version [Cloud Manager August 2024](/help/implementing/cloud-manager/release-notes/current.md).

### La personnalisation de certaines définitions d’index intégrées est interdite. {#oakpal-customizing-ootb-index}

* **Clé** : RestrictIndexCustomization
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.6.0

AEM Cloud Service interdit toute modification non autorisée des index intégrés suivants :

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>Résolvez ce problème dès que possible, car il peut entraîner des échecs de pipeline à partir de la version [Cloud Manager August 2024](/help/implementing/cloud-manager/release-notes/current.md).

### La configuration des jetons dans les analyseurs doit être créée avec le nom &#39;tokenizer&#39;. {#oakpal-tokenizer}

* **Clé** : AnalyzerTokenizerConfigCheck
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.6.0

AEM Cloud Service interdit la création de jetons dont les noms sont incorrects dans les analyseurs. Les générateurs de jetons doivent toujours être définis en tant que `tokenizer`.

>[!WARNING]
>
>Résolvez ce problème dès que possible, car il peut entraîner des échecs de pipeline à partir de la version [Cloud Manager August 2024](/help/implementing/cloud-manager/release-notes/current.md).

### La configuration des définitions d’indexation ne doit pas contenir d’espaces. {#oakpal-indexing-definitions-spaces}

* **Clé** : PathSpacesCheck
* **Type** : amélioration
* **Gravité** : mineure
* **Depuis** : version 2024.7.0

AEM Cloud Service interdit la création de définitions d’indexation qui contiennent des propriétés avec des espaces.
