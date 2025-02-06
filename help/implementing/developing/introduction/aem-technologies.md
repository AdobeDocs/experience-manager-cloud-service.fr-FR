---
title: Fondements techniques d’AEM
description: Présentation des fondements techniques d’AEM, y compris la manière dont AEM est structuré et les technologies fondamentales comme JCR, Sling et OSGi.
exl-id: ab6e7fe9-a25d-4351-a005-f4466cc0f40e
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '2130'
ht-degree: 97%

---

# Fondements techniques d’AEM {#aem-technical-foundations}

AEM est une plateforme robuste fondée sur des technologies éprouvées, évolutives et flexibles. Ce document contient une vue d’ensemble détaillée des différentes parties constituant AEM. Il est conçu comme une annexe technique pour un développeur ou une développeuse AEM full-stack. Il ne s’agit pas d’un guide de prise en main. Si vous êtes novice en matière de développement AEM, consultez d’abord la [Prise en main du développement d’AEM Sites – Tutoriel WKND](develop-wknd-tutorial.md).

>[!TIP]
>
>Avant de passer aux technologies de base d’AEM, Adobe vous recommande de suivre le [Tutoriel Prise en main du développement d’AEM Sites - WKND](develop-wknd-tutorial.md).

## Principes fondamentaux {#fundamentals}

En tant que système moderne de gestion de contenu, AEM s’appuie sur des technologies web standard :

* Cycle request-response (XMLHttpRequest / XMLHttpResponse)
* HTML
* CSS
* JavaScript

Les couches de référentiel de contenu et de logique métier sous-jacentes sont créées à partir des technologies Java™ :

* JCR
* Sling
* OSGi

## Java™ Content Repository {#java-content-repository}

La norme Java™ Content Repository (JCR), [JSR 283](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html), spécifie un moyen, indépendant du fournisseur et de l’implémentation, d’accéder au contenu d’un référentiel de contenu à un niveau granulaire et de manière bidirectionnelle. La spécification est gérée par Adobe Research (Suisse) AG.

Le package [JCR API 2.0](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html), `javax.jcr.*`, est utilisé pour l’accès direct et la manipulation du contenu du référentiel.

AEM est basé sur un JCR.

## Apache Jackrabbit Oak {#jackrabbit-oak}

[Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/) est une implémentation d’un référentiel de contenu hiérarchisé, évolutif et hautement performant, utilisé comme base pour des sites Web modernes de classe mondiale et d’autres applications de contenu exigeantes, conforme à la norme JCR.

Jackrabbit Oak (également appelé simplement Oak) est l’implémentation de la norme JCR sur laquelle AEM est construit.

## Traitement de requête Sling {#sling-request-processing}

AEM repose sur [Sling](https://sling.apache.org/index.html), un framework d’application web basé sur des principes REST. Il facilite le développement d’applications orientées contenu. Sling utilise un référentiel JCR, comme Apache Jackrabbit Oak, servant de magasin de données. The Apache Software Foundation a contribué au développement de Sling. Plus d’informations sont disponibles sur Apache.

### Introduction à Sling {#introduction-to-sling}

Avec Sling, le type de contenu à diffuser n’est pas la première considération en matière de traitement. Il s’agit plutôt de savoir si l’URL se résout en un objet de contenu pour lequel un script peut ensuite être identifié afin d’effectuer le rendu. Ce processus offre une excellente prise en charge aux auteurs et autrices de contenu web pour créer des pages facilement personnalisées selon leurs besoins.

Les avantages liés à cette flexibilité sont évidents dans les applications comportant un vaste éventail d’éléments de contenu différents ou dans les cas où des pages facilement personnalisables sont nécessaires. C’est en particulier le cas pour la mise en œuvre d’un système de gestion de contenu web comme AEM.

Voir [Découvrir Sling en 15 minutes](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html) pour connaître les premières étapes de développement avec Sling.

Le schéma suivant explique la résolution du script Sling : il montre comment passer de la requête HTTP au nœud de contenu, du nœud de contenu au type de ressource, du type de ressource au script, ainsi que les variables de script disponibles.

![Présentation de la résolution du script Apache Sling](assets/sling-cheatsheet-01.png)

Le diagramme suivant explique les paramètres de requête masqués, mais puissants, que vous pouvez utiliser avec `SlingPostServlet`, gestionnaire par défaut pour toutes les requêtes POST. Le gestionnaire vous offre des options infinies pour créer, modifier, supprimer, copier et déplacer des nœuds dans le référentiel.

![Utilisation de SlingPostServlet](assets/sling-cheatsheet-02.png)

### Sling est centré sur le contenu {#sling-is-content-centric}

Sling est *axé sur le contenu*. Cela signifie que le traitement est axé sur le contenu, car chaque requête (HTTP) est mappée sur le contenu sous la forme d’une ressource JCR (un nœud de référentiel) :

* La première cible est la ressource (nœud JCR) qui contient le contenu
* Ensuite, la représentation, ou script, est localisé à partir des propriétés de ressource avec certaines parties de la requête (par exemple des sélecteurs et/ou l’extension)

### Sling RESTful {#restful-sling}

En raison de son approche centrée sur le contenu, Sling implémente un serveur orienté REST et propose ainsi un nouveau concept dans les frameworks d’applications web. Les avantages sont les suivants :

* Niveau RESTful, et pas seulement en surface ; les ressources et les représentations sont correctement modélisées dans le serveur
* Supprime un ou plusieurs modèles de données
   * D’autres frameworks de gestion de contenu peuvent nécessiter la structure d’URL, des objets métier et un schéma de base de données pour accéder à une ressource.
   * L’utilisation revient à : URL = ressource = structure JCR

### Décomposition d’URL {#url-decomposition}

Dans Sling, le traitement est piloté par l’URL de la requête utilisateur. Il définit le contenu à afficher par les scripts appropriés. Les informations sont extraites de l’URL.

Analyser l’URL suivante :

```text
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

Nous pouvons la diviser en plusieurs parties composites :

| protocol | host |  | content path | selectors | Extension |  | Suffixe |  | params |
|---|---|---|---|---|---|---|---|---|---|
| `https://` | `myhost` | `/` | `tools/spy` | `.printable.a4.` | `html` | `/` | `a/b` | `?` | `x=12` |

* **protocol** – HTTPS
* **host** – Domaine du site
* **content path** – Chemin spécifiant le contenu à restituer et utilisé avec l’extension. Dans cet exemple, il se traduit par `tools/spy.html`
* **selectors** – Utilisé pour les méthodes secondaires de rendu du contenu ; dans cet exemple, il s’agit de la version imprimable au format A4
* **extension** – Format de contenu ; spécifie également le script à utiliser pour le rendu
* **suffix** – Peut servir à spécifier des informations supplémentaires
* **params** – Tout paramètre requis pour le contenu dynamique

#### De l’URL au contenu et aux scripts {#from-url-to-content-and-scripts}

Selon les principes de la décomposition des URL :

* Le mappage utilise le chemin d’accès au contenu extrait de la requête pour localiser la ressource.
* Lorsque la ressource appropriée est localisée, le type de ressource sling est extrait et utilisé pour localiser le script à appliquer pour le rendu du contenu.

La figure ci-dessous illustre le mécanisme, décrit plus en détail dans les sections suivantes.

![Mécanisme de mappage des URL](assets/url-mapping.png)

Avec Sling, vous spécifiez le script à appliquer pour le rendu d’une entité donnée (en définissant la propriété `sling:resourceType` dans le nœud JCR). Ce mécanisme offre plus de liberté que celui selon lequel le script accède aux entités de données (comme le ferait une instruction SQL dans un script PHP) puisqu’une ressource peut avoir plusieurs rendus.

#### Mappage des requêtes avec les ressources {#mapping-requests-to-resources}

La requête est décomposée et les informations nécessaires sont extraites. Recherche du référentiel pour la ressource demandée (nœud de contenu) :

* D’abord, Sling vérifie si un nœud existe à l’emplacement spécifié dans la requête. Par exemple, `../content/corporate/jobs/developer.html`
* Si aucun nœud n’est identifié, l’extension est supprimée et la recherche recommence. Par exemple, `../content/corporate/jobs/developer`
* Si aucun nœud n’est identifié, Sling renvoie le code 404 (Not Found).

Sling permet également à des éléments autres que des nœuds JCR d’être des ressources, mais il s’agit là d’une fonctionnalité avancée.

### Localisation du script {#locating-the-script}

Lorsque la ressource appropriée (nœud de contenu) est localisée, le **type de ressource sling** est extrait. Ce chemin d’accès localise le script à utiliser pour le rendu du contenu.

Le chemin spécifié par le `sling:resourceType` peut être :

* Absolu
* Relatif à un paramètre de configuration

>[!TIP]
>
>Les chemins relatifs sont recommandés par Adobe car ils contribuent à la portabilité.

Tous les scripts Sling sont stockés dans des sous-dossiers `/apps` (modifiables, scripts utilisateur) ou `/libs` (non modifiables, scripts système), qui seront recherchés dans cet ordre.

Un certain nombre d’autres points sont à noter :

* Si la méthode (GET, POST) est requise, elle est indiquée en majuscules selon la spécification HTTP, par exemple `jobs.POST.esp`
* Différents moteurs de script sont pris en charge, mais les scripts courants recommandés sont HTL et JavaScript.

La liste des moteurs de script pris en charge par l’instance donnée d’AEM figure dans la Felix Management Console (`http://<host>:<port>/system/console/slingscripting`).

En reprenant l’exemple ci-dessus, si le `sling:resourceType` est `hr/jobs` alors pour :

* les requêtes GET/HEAD et les URL se terminant par `.html` (types de requête par défaut, format par défaut)
   * Le script est `/apps/hr/jobs/jobs.esp` ; la dernière section de `sling:resourceType` forme le nom du fichier.
* Requêtes POST (tous les types de requête, à l’exclusion des GET/HEAD, le nom de la méthode doit être en majuscules)
   * POST sera utilisé dans le nom du script.
   * Le script est `/apps/hr/jobs/jobs.POST.esp`.
* URL dans d’autres formats, qui ne se terminent pas par `.html`
   * Par exemple, `../content/corporate/jobs/developer.pdf`
   * Le script est `/apps/hr/jobs/jobs.pdf.esp` ; le suffixe est ajouté au nom du script.
* URL avec sélecteurs
   * Les sélecteurs peuvent être utilisés pour afficher le même contenu dans un autre format. Par exemple une version imprimable, un flux rss ou un résumé.
   * Si nous étudions une version adaptée à l’imprimante dans laquelle le sélecteur peut être `print` ; comme dans `../content/corporate/jobs/developer.print.html`
   * Le script est `/apps/hr/jobs/jobs.print.esp` ; le sélecteur est ajouté au nom du script.
* Si non, `sling:resourceType` est défini, puis :
   * le chemin d’accès au contenu est utilisé pour rechercher un script correspondant (si `ResourceTypeProvider` basé sur un chemin est actif) ;
   * par exemple, le script pour `../content/corporate/jobs/developer.html` génère une recherche dans `/apps/content/corporate/jobs/` ;
   * Le type de nœud principal est utilisé.
* Si aucun script n’est trouvé, le script par défaut est utilisé.
   * Le rendu par défaut est pris en charge sous la forme de texte brut (`.txt`), HTML (`.html`) et JSON (`.json`) en répertoriant toutes les propriétés du nœud (correctement mises en forme). Le rendu par défaut pour l’extension `.res`, ou les requêtes sans extension de requête, consiste à spouler la ressource (si possible).
* Pour la gestion des erreurs http (codes 403 ou 404), Sling recherche un script dans :
   * l’emplacement `/apps/sling/servlet/errorhandler` pour les scripts personnalisés ;
   * ou l’emplacement du script standard `/libs/sling/servlet/errorhandler/404.jsp`.

Si plusieurs scripts s’appliquent pour une requête donnée, celui avec la meilleure correspondance est sélectionné. Plus une correspondance est précise, mieux c’est. En d’autres termes, plus il y a de correspondances avec les sélecteurs, mieux c’est, indépendamment de toute correspondance entre l’extension de la requête ou le nom de la méthode.

Par exemple, envisagez une demande d’accès à la ressource


* `/content/corporate/jobs/developer.print.a4.html`

De type

* `sling:resourceType="hr/jobs"`

En supposant que les scripts suivants sont présents au bon emplacement :

1. `GET.esp`
1. `jobs.esp`
1. `html.esp`
1. `print.esp`
1. `print.html.esp`
1. `print/a4.esp`
1. `print/a4/html.esp`
1. `print/a4.html.esp`

L’ordre de préférence serait (8) – (7) – (6) – (5) – (4) – (3) – (2) – (1).

En plus des types de ressources (principalement définis par la propriété `sling:resourceType`), il existe également le super type de ressource. Il est généralement indiqué par la propriété `sling:resourceSuperType`. Ces super types sont aussi pris en compte lors de la recherche d’un script. Les super types de ressources présentent l’avantage de former une hiérarchie de ressources où le type de ressource par défaut `sling/servlet/default` (utilisé par les servlets par défaut) est effectivement la racine.

Le super type de ressource d’une ressource peut être défini de deux manières :

* par la propriété `sling:resourceSuperType` de la ressource ;
* par la propriété `sling:resourceSuperType` du nœud vers lequel pointe `sling:resourceType`.

Par exemple :

* `/`
   * `a`
   * `b`
      * `sling:resourceSuperType = a`
   * `c`
      * `sling:resourceSuperType = b`
   * `x`
      * `sling:resourceType = c`
   * `y`
      * `sling:resourceType = c`
      * `sling:resourceSuperType = a`

La hiérarchie de type de :

* `/x`
   * est `[ c, b, a, <default>]`
* alors que pour `/y`
   * La hiérarchie est `[ c, a, <default>]`

Ceci est dû au fait que `/y` possède la propriété `sling:resourceSuperType` contrairement à `/x`, et donc son super type est issu de son type de ressource.

#### Les scripts Sling ne peuvent pas être appelés directement {#sling-scripts-cannot-be-called-directly}

Dans Sling, les scripts ne peuvent pas être appelés directement, car cela violerait le concept strict d’un serveur REST ; vous mélangeriez les ressources et les représentations.

Si vous appelez la représentation (le script) directement, vous masquez la ressource dans le script, donc le framework (Sling) ne peut plus la détecter. Vous perdez ainsi certaines fonctionnalités :

* Le traitement automatique des méthodes http autres que GET, y compris :
   * les méthodes POST, PUT, DELETE qui sont gérées avec une implémentation par défaut de Sling ;
   * le script `POST.jsp` dans votre emplacement `sling:resourceType`
* L’architecture du code perd de son intégrité et de sa structure qui sont primordiales dans les développements à grande échelle

### API Sling {#sling-api}

Utilise le package d’API Sling, `org.apache.sling.*` et des bibliothèques de balises.

### Référencement d’éléments existants avec sling:include {#referencing-existing-elements-using-sling-include}

En dernier lieu, il faut considérer la nécessité de référencer les éléments existants dans les scripts.

Les scripts plus complexes (scripts d’agrégation) accèdent à plusieurs ressources (par exemple, la navigation, la barre latérale, le pied de page, les éléments d’une liste), et ce, en incluant la *ressource*.

Dans ce cas, vous pouvez utiliser la commande `sling:include("/<path>/<resource>")`. Elle inclut effectivement la définition de la ressource référencée.

## OSGi {#osgi}

OSGi désigne une architecture permettant de développer et de déployer des applications et des bibliothèques modulaires (également connu sous le nom de Dynamic Module System for Java™). Les conteneurs OSGi vous permettent de décomposer votre application en modules distincts (des fichiers jar contenant des méta-informations supplémentaires appelés « bundles » dans le jargon OSGi) et de gérer les interdépendances qui existent entre eux avec :

* Services mis en œuvre dans le conteneur
* Un contrat entre le conteneur et votre application

Ces services et contrats fournissent une architecture qui permet à des éléments particuliers de se découvrir dynamiquement les uns les autres à des fins de collaboration.

Un framework OSGi vous offre ensuite le chargement/déchargement dynamique, la configuration et le contrôle de ces lots, sans nécessiter de redémarrage.

>[!NOTE]
>
>Vous trouverez des informations complètes sur la technologie OSGi sur le [site web d’OSGi](https://www.osgi.org).
>
>En particulier, la page Basic Education (formation de base) contient un ensemble de présentations et de tutoriels.

Cette architecture vous permet d’étendre Sling avec des modules spécifiques à l’application. Sling, et donc AEM, utilise l’implémentation [Apache Felix](https://felix.apache.org/documentation/index.html) d’OSGi. Les deux sont des groupes de lots OSGi qui s’exécutent dans un framework OSGi.

Cette fonctionnalité vous permet d’effectuer les actions suivantes sur l’un des packages de votre installation :

* Installer
* Démarrer
* Arrêter
* Mettre à jour
* Désinstaller
* Afficher le dernier statut
* Accéder à des informations plus détaillées sur des lots spécifiques, par exemple, le nom symbolique, la version et l’emplacement

Voir [Configuration d’OSGi pour AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md) pour plus d’informations.

## Structure dans le référentiel {#structure-within-the-repository}

La liste suivante propose une vue d’ensemble de la structure que vous verrez dans le référentiel.

* `/apps` – Application connexe qui inclut des définitions de composants spécifiques à votre site web. Les composants que vous développez peuvent être basés sur les composants prêts à l’emploi disponibles dans `/libs/core/wcm/components`.
* `/content` – Contenu créé pour votre site web.
* `/etc`
* `/home` – Informations sur les utilisateurs et les groupes.
* `/libs` – Bibliothèques et définitions appartenant au noyau d’AEM. Les sous-dossiers de `/libs` représentent les fonctionnalités AEM prêtes à l’emploi. Le contenu de `/libs` ne peut pas être modifié. Les fonctionnalités spécifiques à votre site web doivent être définies sous `/apps`.
* `/tmp` – Espace de travail temporaire.
* `/var` – Fichiers qui évoluent et sont mis à jour par le système, tels que les journaux d’audit, les statistiques, la gestion des événements.

>[!CAUTION]
>
>Les modifications apportées à cette structure, ou aux fichiers qu’elle contient, doivent l’être prudemment. Assurez-vous de bien comprendre les implications de tout changement apporté.
>
>Vous ne devez rien modifier dans le chemin `/libs`. Pour la configuration et d’autres modifications, copiez l’élément de `/libs` dans `/apps` et apportez des modifications dans `/apps`.
