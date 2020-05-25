---
title: Règles de qualité du code personnalisé - Cloud Services
description: Règles de qualité du code personnalisé - Cloud Services
translation-type: tm+mt
source-git-commit: f2fa2adeec74bfa687ed59d3e0847e6246028040
workflow-type: tm+mt
source-wordcount: '2254'
ht-degree: 100%

---


# Présentation des règles de qualité du code personnalisé {#custom-code-quality-rules}


Cette page décrit les règles de qualité du code personnalisé exécutées par Cloud Manager qui sont créées selon les bonnes pratiques en matière d’ingénierie AEM.

>[!NOTE]
>
>Les exemples de code utilisés ici ne sont fournis qu’à titre d’exemple.

## Règles SonarQube {#sonarqube-rules}

La section suivante met en évidence les règles SonarQube :

### N’utilisez pas de fonctions potentiellement dangereuses {#do-not-use-potentially-dangerous-functions}

**Clé** : CQRules:CWE-676

**Type** : vulnérabilité

**Gravité** : majeure

**Depuis** : version 2018.4.0

Les méthodes ***Thread.stop()*** et ***Thread.interrupt()*** peuvent générer des problèmes difficiles à reproduire et, dans certains cas, des vulnérabilités en matière de sécurité. Leur utilisation doit être minutieusement surveillée et validée. En règle générale, la transmission de messages est une méthode plus sûre pour atteindre des objectifs similaires.

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

### N’utilisez pas de chaînes de format pouvant être contrôlées en externe {#do-not-use-format-strings-which-may-be-externally-controlled}

**Clé** : CQRules:CWE-134

**Type** : vulnérabilité

**Gravité** : majeure

**Depuis** : version 2018.4.0

L’utilisation d’une chaîne de format provenant d’une source externe (telle qu’un paramètre de requête ou un contenu généré par l’utilisateur) peut exposer une application aux attaques par déni de service. Dans certains cas, une chaîne de format peut être contrôlée en externe, mais elle n’est autorisée que par les sources approuvées.

#### Code non conforme {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### Les requêtes HTTP doivent toujours avoir des délais de socket et de connexion {#http-requests-should-always-have-socket-and-connect-timeouts}

**Clé** : CQRules:ConnectionTimeoutMechanism

**Type** : bogue

**Gravité** : critique

**Depuis** : version 2018.6.0

Lors de l’exécution de requêtes HTTP à partir d’une application AEM, il est essentiel de vérifier que les délais appropriés sont configurés afin d’éviter toute consommation inutile de threads. Malheureusement, le comportement par défaut du client HTTP Java par défaut (java.net.HttpUrlconnection) et du client de composants Apache HTTP couramment utilisé ne doivent jamais expirer, donc les délais d’expiration doivent être explicitement définis. De plus, en règle générale, ces délais d’expiration ne doivent pas dépasser 60 secondes.

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

### Les API de produit annotées avec @ProviderType ne doivent pas être implémentées ni étendues par les clients {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**Clé** : CQBP-84, CQBP-84-dependencies

**Type** : bogue

**Gravité** : critique

**Depuis** : version 2018.7.0

L’API AEM contient des classes et interfaces Java qui sont censées être utilisées, mais pas implémentées, par du code personnalisé. Par exemple, l’interface *com.day.cq.wcm.api.Page* est conçue pour être implémentée par ***AEM uniquement***.

Lorsque de nouvelles méthodes sont ajoutées à ces interfaces, celles-ci n’ont aucun impact sur le code existant qui utilise ces interfaces et, par conséquent, l’ajout de nouvelles méthodes à ces interfaces est considéré comme rétrocompatible. Cependant, si le code personnalisé ***implémente*** l’une de ces interfaces, il introduit un risque de rétrocompatibilité pour le client.

Les interfaces (et les classes) destinées uniquement à être implémentées par AEM sont annotées de *org.osgi.annotation.version.ProviderType* (ou, dans certains cas, une annotation héritée similaire *aQute.bnd.annotation.ProviderType*). Cette règle identifie les cas où une telle interface est implémentée (ou une classe est étendue) par code personnalisé.

#### Code non conforme {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Les objets ResourceResolver doivent toujours être fermés {#resourceresolver-objects-should-always-be-closed}

**Clé** : CQRules:CQBP-72

**Type** : code Smell

**Gravité** : majeure

**Depuis** : version 2018.4.0

Les objets ResourceResolver obtenus à partir de ResourceResolverFactory consomment des ressources système. Bien qu’il existe des mesures pour récupérer ces ressources lorsqu’un ResourceResolver n’est plus en cours d’utilisation, il est plus efficace de fermer explicitement tous les objets ResourceResolver ouverts en appelant la méthode close().

Une idée relativement courante est que les objets ResourceResolver créés à l’aide d’une session JCR existante ne doivent pas être fermés explicitement ou que cela ferme la session JCR sous-jacente. Ce n’est pas le cas : quelle que soit la manière dont un ResourceResolver est ouvert, il doit être fermé lorsqu’il n’est plus utilisé. Puisque ResourceResolver implémente l’interface qui accepte close(), il est également possible d’utiliser la syntaxe try-with-resources plutôt que d’appeler explicitement close().

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

**Clé** : CQRules:CQBP-75

**Type** : code Smell

**Gravité** : majeure

**Depuis** : version 2018.4.0

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

### Les exceptions capturées doivent être consignées ou émises, mais pas les deux. {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**Clé** : CQRules:CQBP-44---CatchAndEitherLogOrThrow

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2018.4.0

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

### Évitez de faire suivre une instruction de journal immédiatement par une instruction d’émission {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**Clé** : CQRules:CQBP-44---ConsecutivelyLogAndThrow

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2018.4.0

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

### Évitez de journaliser les informations lors de la gestion des requêtes GET ou HEAD. {#avoid-logging-at-info-when-handling-get-or-head-requests}

**Clé** : CQRules:CQBP-44---LogInfoInGetOrHeadRequests

**Type** : code Smell

**Gravité** : mineure

En règle générale, le niveau de journal Informations doit être utilisé pour délimiter les actions importantes et, par défaut, AEM est configuré pour le journal au niveau Information ou au-dessus. Les méthodes GET et HEAD ne doivent jamais être en lecture seule et ne constituent donc pas des actions importantes. La journalisation au niveau d’Informations en réponse aux demandes GET ou HEAD est susceptible de créer un bruit journal significatif, rendant ainsi plus difficile l’identification des informations utiles dans les fichiers journaux. La journalisation lors de la gestion des demandes GET ou HEAD doit être soit au niveau d’avertissement ou d’erreur lorsque quelque chose est erroné, soit aux niveaux DEBUG ou TRACE si des informations de dépannage plus approfondies étaient utiles.

>[!CAUTION]
>
>Cela ne s’applique pas à la journalisation access.log-type pour chaque requête.

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

**Clé** : CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2018.4.0

Il est recommandé que les messages de journal fournissent des informations contextuelles sur l’emplacement d’une exception dans l’application. Bien que le contexte puisse également être déterminé par l’utilisation des arborescences des appels de procédure, il est généralement plus facile de lire et de comprendre le message du journal. Par conséquent, lors de la journalisation d’une exception, il est déconseillé d’utiliser le message de l’exception comme message du journal : le message d’exception contiendra ce qu’il s’est passé, alors que le message du journal doit servir à indiquer à un lecteur ce que faisait l’application lorsque l’exception s’est produite. Le message d’exception sera toujours consigné ; en spécifiant votre propre message, les journaux seront simplement plus faciles à comprendre.

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

### La journalisation des blocs catch doit se trouver au niveau d’avertissement ou d’erreur. {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

**Clé** : CQRules:CQBP-44---WrongLogLevelInCatchBlock

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2018.4.0

Comme le suggère leur nom, les exceptions Java doivent toujours être utilisées dans des circonstances *exceptionnelles*. Par conséquent, lorsqu’une exception est capturée, il est important de s’assurer que les messages du journal sont consignés au niveau approprié : AVERTISSEMENT ou ERREUR. Ces messages s’affichent ainsi correctement dans les journaux.

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

**Clé** : CQRules:CQBP-44---ExceptionPrintStackTrace

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2018.4.0

Comme nous l’avons mentionné, le contexte est essentiel lors de la compréhension des messages du journal. Utiliser Exception.printStackTrace() entraîne **seulement** la sortie de l’arborescence des appels de procédure dans le flux d’erreurs standard, perdant ainsi tout le contexte. De plus, dans une application multi-thread telle qu’AEM, si plusieurs exceptions sont imprimées à l’aide de cette méthode en parallèle, leurs arborescences des appels de procédure peuvent se chevaucher, ce qui prête à confusion. Les exceptions ne doivent être consignées que dans la structure de journalisation.

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

**Clé** : CQRules:CQBP-44—LogLevelConsolePrinters

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2018.4.0

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

**Clé** : CQRules:CQBP-71

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2018.4.0

En règle générale, les chemins qui commencent par /libs et /apps ne doivent pas être codés en dur car les chemins auxquels ils se réfèrent sont le plus souvent stockés comme chemins relatifs au chemin de recherche Sling (qui est défini par défaut sur /libs et /apps). L’utilisation du chemin absolu peut introduire des défauts subtils qui n’apparaîtront que plus tard dans le cycle de vie du projet.

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

**Clé** : CQRules:AMSCORE-554

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2020.5.0

Le planificateur Sling ne doit pas être utilisé pour des tâches qui nécessitent une exécution garantie. Les tâches planifiées Sling garantissent l’exécution et conviennent mieux aux environnements organisés avec ou sans grappes.

Reportez-vous à la section [Traitement des tâches et gestion des événements Apache Sling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) pour en savoir plus sur la façon dont les tâches Sling sont gérées dans des environnements organisés en grappes.

### Les API AEM obsolètes ne doivent pas être utilisées {#sonarqube-aem-deprecated}

**Clé** : AMSCORE-553

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2020.5.0

La surface de l’API AEM est constamment revue pour identifier les API dont l’utilisation est déconseillée et qui sont donc considérées comme obsolètes.

Dans de nombreux cas, ces API sont abandonnées en y associant l’annotation standard Java *@Deprecated*. Elles sont à ce titre identifiées par la mention `squid:CallToDeprecatedMethod`.

Cependant, il arrive qu’une API soit déconseillée dans le contexte d’AEM, mais pas dans d’autres contextes. Cette règle identifie cette deuxième classe.

## Règles de contenu OakPAL {#oakpal-rules}

Vous trouverez ci-dessous les vérifications OakPAL exécutées par Cloud Manager.

>[!NOTE]
>OakPAL est une infrastructure développée par un partenaire AEM (ayant remporté le prix AEM Rockstar North America 2019) qui valide des packages de contenu à l’aide d’un référentiel Oak autonome.

### Les packages des clients ne doivent pas créer ni modifier les nœuds sous /libs {#oakpal-customer-package}

**Clé** : BannedPaths

**Type** : bogue

**Gravité** : bloqueur

**Depuis** : version 2019.6.0

Il a été établi depuis longtemps que l’arborescence de contenu /libs dans le référentiel de contenu AEM doit être considérée comme étant en lecture seule par les clients. La modification des nœuds et des propriétés sous */libs* crée un risque significatif pour les mises à jour majeures et mineures. Les modifications apportées à */libs* ne doivent être effectuées que par Adobe par le biais de canaux officiels.

### Les packages ne doivent pas contenir de configurations OSGi en double {#oakpal-package-osgi}

**Clé** : DuplicateOsgiConfigurations

**Type** : bogue

**Gravité** : majeure

**Depuis** : version 2019.6.0

Le fait qu’un même composant OSGi soit configuré plusieurs fois est un problème courant qui se produit sur les projets complexes. Cela crée une ambiguïté quant à la configuration qui sera exploitable. Cette règle est « compatible avec le mode d’exécution » en ce qu’elle identifie uniquement les problèmes où le même composant est configuré plusieurs fois dans le même mode d’exécution (ou combinaison de modes d’exécution).

#### Code non conforme {#non-compliant-code-osgi}

```+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Code conforme {#compliant-code-osgi}

```+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Les dossiers de configuration et d’installation ne doivent contenir que des nœuds OSGi {#oakpal-config-install}

**Clé** : ConfigAndInstallShouldOnlyContainOsgiNodes

**Type** : bogue

**Gravité** : majeure

**Depuis** : version 2019.6.0

Pour des raisons de sécurité, les chemins contenant */config/ et /install/* ne sont lisibles que par les utilisateurs administratifs dans AEM et doivent être utilisés uniquement pour la configuration OSGi et les lots OSGi. Placer d’autres types de contenu sous les chemins contenant ces segments donne un comportement d’application qui varie involontairement entre les utilisateurs administratifs et non administrateurs.

Un problème courant est l’utilisation de nœuds nommés `config` dans les boîtes de dialogue des composants ou lors de la spécification de la configuration de l’éditeur de texte enrichi pour la modification statique. Pour résoudre ce problème, le nœud incriminé doit être renommé avec un nom compatible. Pour la configuration de l’éditeur de texte enrichi, utilisez la propriété `configPath` sur le nœud `cq:inplaceEditing` pour spécifier le nouvel emplacement.

#### Code non conforme {#non-compliant-code-config-install}

```
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Code conforme {#compliant-code-config-install}

```
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Les packages ne doivent pas se chevaucher {#oakpal-no-overlap}

**Clé** : PackageOverlaps

**Type** : bogue

**Gravité** : majeure

**Depuis** : version 2019.6.0

Tout comme *Les packages ne doivent pas contenir de configurations OSGi en double*, il s’agit d’un problème courant sur les projets complexes où le même chemin de nœud est écrit par plusieurs packages de contenu distincts. Bien que l’utilisation des dépendances des packages de contenu puisse servir à garantir un résultat cohérent, il est préférable d’éviter tout chevauchement.

### Le mode de création par défaut ne doit pas être défini sur Interface utilisateur classique {#oakpal-default-authoring}

**Clé** : ClassicUIAuthoringMode

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2020.5.0

La configuration OSGi `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` définit le mode de création par défaut dans AEM. Comme l’interface utilisateur classique a été abandonnée depuis AEM 6.4, un problème survient lorsque le mode de création par défaut est configuré sur Interface utilisateur classique.

### Les boîtes de dialogue de composants doivent être de type interface utilisateur tactile {#oakpal-components-dialogs}

**Clé** : ComponentWithOnlyClassicUIDialog

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2020.5.0

Les composants AEM disposant d’une boîte de dialogue d’interface utilisateur classique doivent toujours avoir une boîte de dialogue d’interface utilisateur tactile correspondante. Ainsi, l’expérience de création est optimale et la compatibilité avec le modèle de déploiement du service cloud, où l’interface utilisateur classique n’est pas prise en charge, est assurée. Cette règle vérifie les scénarios suivants :

* Un composant doté d’une boîte de dialogue d’interface utilisateur classique (c’est-à-dire un nœud enfant dialog) doit avoir une boîte de dialogue d’interface utilisateur tactile correspondante (c’est-à-dire un nœud enfant `cq:dialog`).
* Un composant doté d’une boîte de dialogue d’interface utilisateur classique (c’est-à-dire un nœud enfant design_dialog) doit avoir une boîte de dialogue d’interface utilisateur tactile correspondante (c’est-à-dire un nœud enfant `cq:design_dialog`).
* Un composant doté d’une boîte de dialogue d’interface utilisateur classique et d’une boîte de dialogue de conception d’interface utilisateur classique doit comporter à la fois une boîte de dialogue d’interface utilisateur tactile correspondante et une boîte de dialogue de conception d’interface utilisateur tactile correspondante.

La documentation des outils de modernisation d’AEM contient des documents et des outils pour convertir les composants de l’interface utilisateur classique en interface utilisateur tactile. Consultez la section [Les outils de modernisation AEM](https://opensource.adobe.com/aem-modernize-tools/pages/tools.html) pour en savoir plus.

### Les packages ne doivent pas combiner du contenu modifiable et non modifiable {#oakpal-packages-immutable}

**Clé** : ImmutableMutableMixedPackage

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2020.5.0

Pour être compatibles avec le modèle de déploiement du service cloud, les packages de contenu individuels doivent contenir soit du contenu pour les zones non modifiables du référentiel (`/apps and /libs, although /libs` ne doivent pas être modifiées par le code client et provoqueront une violation distincte), soit la zone modifiable (c’est-à-dire tout le reste), mais pas les deux. Par exemple, un package contenant à la fois `/apps/myco/components/text and /etc/clientlibs/myco` est incompatible avec le service cloud et provoquera la notification d’un problème.

Pour plus d’informations, voir [Structure de projet AEM](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html).

### Les agents de réplication inverse ne doivent pas être utilisés {#oakpal-reverse-replication}

**Clé** : ReverseReplication

**Type** : code Smell

**Gravité** : mineure

**Depuis** : version 2020.5.0

La prise en charge de la réplication inverse n’est pas disponible dans les déploiements du service cloud, comme décrit dans la section [Notes de mise à jour : suppression des agents de réplication](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/release-notes/aem-cloud-changes.html#replication-agents).

Les clients qui utilisent la réplication inverse doivent contacter Adobe pour obtenir d’autres solutions.

