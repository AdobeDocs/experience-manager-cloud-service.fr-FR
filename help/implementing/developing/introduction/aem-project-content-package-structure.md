---
title: Structure de projet AEM
description: Découvrez comment définir des structures de package en vue d’un déploiement sur Adobe Experience Manager Cloud Service.
exl-id: 38f05723-5dad-417f-81ed-78a09880512a
source-git-commit: 92c123817a654d0103d0f7b8e457489d9e82c2ce
workflow-type: tm+mt
source-wordcount: '2918'
ht-degree: 56%

---

# Structure de projet AEM

>[!TIP]
>
>L’[archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) et le [plug-in Maven FileVault Content](/help/implementing/developing/tools/maven-plugin.md) font partie des thèmes abordés dans cet article. Vous êtes donc invité à vous familiariser avec ces concepts.

Cet article décrit les modifications requises pour que les projets Maven Adobe Experience Manager soient as a Cloud Service et compatibles, en veillant à ce qu’ils respectent la division entre contenu modifiable et non modifiable. En outre, les dépendances sont établies pour créer des déploiements déterministes non conflictuels, et elles sont regroupées dans une structure déployable.

AEM les déploiements d’applications doivent être composés d’un seul module AEM. Ce module doit à son tour contenir des sous-modules qui comprennent tout ce dont l’application a besoin pour fonctionner, y compris le code, la configuration et tout contenu de base pris en charge.

AEM requiert une séparation du **contenu** et du **code**, ce qui signifie qu’un même package de contenu **ne peut pas** être déployé **à la fois** dans les zones `/apps` et dans les zones accessibles en écriture au moment de l’exécution (`/content`, `/conf`, `/home` ou toute zone autre que `/apps`) du référentiel. L’application doit séparer le code et le contenu dans des packages distincts en vue du déploiement dans AEM.

La structure de package décrite dans ce document est compatible avec les déploiements de développement en local **et** les déploiements d’AEM Cloud Service.

>[!TIP]
>
>Les configurations décrites dans ce document sont fournies par [AEM Project Maven Archetype 24 ou version ultérieure](https://github.com/adobe/aem-project-archetype/releases).

## Zones modifiables ou non modifiables du référentiel {#mutable-vs-immutable}

Le `/apps` et `/libs` les zones d’AEM sont prises en compte **non modifiable** car ils ne peuvent pas être modifiés (créer, mettre à jour, supprimer) une fois AEM démarrée (c’est-à-dire au moment de l’exécution). Toute tentative de modification d’une zone immuable au moment de l’exécution échoue.

Tout le reste dans le référentiel, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`, etc. sont tous **mutable** , ce qui signifie qu’elles peuvent être modifiées au moment de l’exécution.

>[!WARNING]
>
>Comme dans les versions précédentes d’AEM, `/libs` ne doit pas être modifié. Seul le code de produit AEM peut être déployé sur `/libs`.

### Index Oak {#oak-indexes}

Index Oak (`/oak:index`) sont gérés par le processus de déploiement as a Cloud Service AEM. Cela est dû au fait que Cloud Manager doit attendre le déploiement d’un nouvel index et la réindexation complète avant de passer à la nouvelle image de code.

Ainsi, bien que les index Oak soient modifiables au moment de l’exécution, ils doivent être déployés sous forme de code pour pouvoir être installés avant les packages modifiables. Les configurations `/oak:index` font donc partie du package de code, mais pas du package de contenu, [comme décrit ci-dessous](#recommended-package-structure).

>[!TIP]
>
>Pour plus d’informations sur l’indexation dans AEM as a Cloud Service, voir [Recherche et indexation de contenu](/help/operations/indexing.md).

## Structure de package recommandée {#recommended-package-structure}

![Structure de package de projet Experience Manager](assets/content-package-organization.png)

Ce diagramme présente un aperçu de la structure de projet recommandée et des artefacts de déploiement du package.

La structure de déploiement d’application recommandée est la suivante :

### Packages de code/Bundles OSGi

+ Le fichier Jar du bundle OSGi est généré et directement incorporé dans l’ensemble du projet.

+ Le package `ui.apps` contient tout le code à déployer. Il est déployé uniquement sur `/apps`. Voici un aperçu des éléments courants du package `ui.apps` :
   + [Définitions des composants et scripts HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=fr)
      + `/apps/my-app/components`
   + Code JavaScript et CSS (via les [bibliothèques clientes](/help/implementing/developing/introduction/clientlibs.md))
      + `/apps/my-app/clientlibs`
   + [Recouvrements](/help/implementing/developing/introduction/overlays.md) de `/libs`
      + `/apps/cq`, `/apps/dam/`, et ainsi de suite.
   + Configurations basées sur le contexte de secours
      + `/apps/settings`
   + Listes de contrôle d’accès (autorisations)
      + Tout `rep:policy` pour tout chemin d’accès sous `/apps`
   + [Scripts groupés précompilés](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/precompiled-bundled-scripts.html?lang=fr)

>[!NOTE]
>
>Le même code doit être déployé dans tous les environnements. Ce code garantit un niveau de confiance dans lequel les validations dans l’environnement intermédiaire sont également en production. Pour plus d’informations, voir la section [Modes d’exécution](/help/implementing/deploying/overview.md#runmodes).


### Packages de contenu

+ Le package `ui.content` contient l’ensemble du contenu et de la configuration. Le package de contenu contient toutes les définitions de nœud qui ne se trouvent pas dans les packages `ui.apps` ou `ui.config` ou, en d’autres termes, tout ce qui ne se trouve pas dans `/apps` ou `/oak:index`. Voici un aperçu des éléments courants du package `ui.content` :
   + Configurations basées sur le contexte
      + `/conf`
   + Structures de contenu requises et complexes (c’est-à-dire la création de contenu qui s’appuie sur et étend d’anciennes structures de contenu de ligne de base définies dans Repo Init).
      + `/content`, `/content/dam`, et ainsi de suite.
   + Taxonomies du balisage régies
      + `/content/cq:tags`
   + Noeuds etc. hérités (idéalement, migrez ces noeuds vers des emplacements autres que /etc)
      + `/etc`

### Packages conteneurs

+ Le `all` Le module est un module conteneur qui comprend UNIQUEMENT des artefacts déployables, le fichier Jar du bundle OSGI, `ui.apps`, `ui.config`, et `ui.content` modules en tant qu’incorporations. Le `all` Le package ne doit pas comporter **tout contenu ou code** mais à la place, vous devez déléguer tout le déploiement au référentiel à ses sous-modules ou fichiers Jar du bundle OSGi.

  Les modules sont désormais inclus à l’aide de Maven. [Configuration intégrée du module externe FileVault Package Maven](#embeddeds), plutôt que la variable `<subPackages>` configuration.

  Pour les déploiements de Experience Manager complexes, il peut être souhaitable de créer plusieurs `ui.apps`, `ui.config`, et `ui.content` projets/packages représentant des sites ou des clients spécifiques dans AEM. Si cette approche est effectuée, assurez-vous que la division entre contenu modifiable et non modifiable est respectée, et que les modules de contenu et les fichiers Jar du bundle OSGi requis sont incorporés en tant que sous-modules dans la variable `all` module de contenu du conteneur.

  Une structure complexe d’un package de contenu de déploiement peut, par exemple, se présenter comme suit :

   + Le package de contenu `all` intègre les packages suivants afin de créer un artefact de déploiement unique
      + `common.ui.apps` déploie le code requis par les sites A **et** B
      + Fichier Jar de bundle OSGi `site-a.core` requis par le site A
      + `site-a.ui.apps` déploie le code requis par le site A
      + `site-a.ui.config` déploie les configurations OSGi requises par le site A
      + `site-a.ui.content` déploie le contenu et la configuration requis par le site A
      + Fichier Jar de bundle OSGi `site-b.core` requis par le site B
      + `site-b.ui.apps` déploie le code requis par le site B
      + `site-b.ui.config` déploie les configurations OSGi requises par le site B
      + `site-b.ui.content` déploie le contenu et la configuration requis par le site B

+ Le package `ui.config` contient toutes les [configurations OSGi](/help/implementing/deploying/configuring-osgi.md) :
   + Considéré comme du code et appartient aux lots OSGi, mais ne contient pas de nœuds de contenu standard. Ainsi, il est marqué comme un package de conteneurs.
   + Dossier d’organisation contenant des définitions de configuration OSGi spécifiques au mode d’exécution
      + `/apps/my-app/osgiconfig`
   + Dossier de configuration OSGi commun contenant les configurations OSGi par défaut qui s’appliquent à toutes les cibles de déploiement AEM as a Cloud Service
      + `/apps/my-app/osgiconfig/config`
   + Dossiers de configuration OSGi spécifiques au mode d’exécution contenant les configurations OSGi par défaut qui s’appliquent à toutes les cibles AEM déploiement as a Cloud Service
      + `/apps/my-app/osgiconfig/config.<author|publish>.<dev|stage|prod>`
   + Scripts de configuration OSGi Repo Init
      + [Repo Init](#repo-init) est la méthode recommandée pour déployer du contenu (mutable) faisant logiquement partie de l’application AEM. Les configurations OSGi Repo Init doivent être placées dans le dossier `config.<runmode>` approprié, comme indiqué ci-dessus, et être utilisées pour définir :
         + Structures de contenu de base
         + Utilisateurs
         + Utilisateurs du service
         + Groupes
         + Listes de contrôle d’accès (autorisations)

### Packages d’applications supplémentaires {#extra-application-packages}

Si d’autres projets AEM, eux-mêmes composés de leur propre code et de leurs propres modules de contenu, sont utilisés par le déploiement AEM, leurs modules conteneur doivent être incorporés dans le module du projet. `all` module.

Par exemple, un projet AEM qui comprend deux applications AEM de fournisseur peut se présenter comme suit :

+ Le package de contenu `all` intègre les packages suivants afin de créer un artefact de déploiement unique
   + Fichier Jar de bundle OSGi `core` requis par l’application AEM
   + `ui.apps` déploie le code requis par l’application AEM
   + `ui.config` déploie les configurations OSGi requises par l’application AEM
   + `ui.content` déploie le contenu et la configuration requis par l’application AEM
   + `vendor-x.all` déploie tous les éléments (code et contenu) requis par l’application du fournisseur X
   + `vendor-y.all` déploie tout les éléments (code et contenu) requis par l’application du fournisseur Y

## Types de packages {#package-types}

Les packages doivent être marqués avec le type déclaré. Les types de packages permettent de clarifier l’objectif et le déploiement d’un package.

+ Les packages de conteneurs doivent définir leur `packageType` sur `container`. Les packages de conteneurs ne doivent pas contenir de nœuds standard. Seuls les lots OSGi, les configurations et les sous-modules sont autorisés. Les conteneurs dans AEM as a Cloud Service ne sont pas autorisés à utiliser les [hooks d’installation](https://jackrabbit.apache.org/filevault/installhooks.html).
+ Les packages de code (non modifiables) doivent définir leur `packageType` sur `application`.
+ Les packages de contenu (modifiables) doivent définir leur `packageType` sur `content`.


Pour plus d’informations, consultez la [documentation d’Apache Jackrabbit FileVault - Plug-in Maven pour les packages](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType), les [Types de packages Apache Jackrabbit](https://jackrabbit.apache.org/filevault/packagetypes.html) et le [Fragment de code de configuration FileVault Maven](#marking-packages-for-deployment-by-adoube-cloud-manager) ci-dessous.

>[!TIP]
>
>Pour obtenir un fragment de code complet, reportez-vous à la section [Fragments de code XML POM](#xml-package-types) ci-dessous.

## Marquage de packages en vue du déploiement par Adobe Cloud Manager {#marking-packages-for-deployment-by-adoube-cloud-manager}

Par défaut, Adobe Cloud Manager récupère tous les packages générés par la version Maven. Cependant, car le conteneur (`all`) est l’artefact de déploiement unique qui contient tous les modules de code et de contenu. Vous devez vous assurer que **only** le conteneur (`all`) est déployé. Pour ce faire, les autres modules générés par la version Maven doivent être marqués avec la configuration suivante du plug-in Maven FileVault Content Package : `<properties><cloudManagerTarget>none</cloudManageTarget></properties>`.

>[!TIP]
>
>Pour obtenir un fragment de code complet, reportez-vous à la section [Fragments de code XML POM](#pom-xml-snippets) ci-dessous.

## Repo Init {#repo-init}

Repo Init fournit des instructions, ou scripts, qui définissent les structures JCR, allant des structures de noeud courantes telles que les arborescences de dossiers, aux utilisateurs, aux utilisateurs de service, aux groupes et à la définition de liste de contrôle d’accès.

Les principaux avantages de Repo Init sont qu’ils disposent d’autorisations implicites pour effectuer toutes les actions définies par leurs scripts. De plus, ces scripts sont appelés plus tôt au cours du cycle de vie du déploiement, ce qui garantit que toutes les structures JCR requises existent au moment de l’exécution du code temporel.

Bien que les scripts Repo Init résident eux-mêmes dans le projet `ui.config` en tant que scripts, ils peuvent et doivent être utilisés pour définir les structures mutables suivantes :

+ Structures de contenu de base
+ Utilisateurs du service
+ Utilisateurs
+ Groupes
+ Listes ACL

Les scripts Repo Init sont stockés sous la forme `scripts` entrées de `RepositoryInitializer` Configurations d’usine OSGi. Ils peuvent donc être implicitement ciblés par le mode d’exécution, ce qui permet d’établir des différences entre les scripts Repo Init des services d’auteur et de publication AEM, voire entre les environnements (développement, évaluation et production).

Les configurations OSGi Repo Init sont mieux écrites dans le [`.config` format de configuration OSGi](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-config-1), car elles prennent en charge plusieurs lignes, ce qui est une exception aux bonnes pratiques d’utilisation de [`.cfg.json` pour définir des configurations OSGi](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).

Lors de la définition des utilisateurs et des groupes, seuls les groupes sont considérés comme faisant partie de l’application et faisant partie intégrante de sa fonction. Vous définissez toujours des utilisateurs et des groupes d’organisation au moment de l’exécution dans AEM. Par exemple, si un workflow personnalisé attribue du travail à un groupe nommé, définissez ce groupe au moyen de Repo Init dans l’application AEM. Cependant, si le groupement est simplement organisationnel, comme &quot;l&#39;équipe de Wendy&quot; et &quot;l&#39;équipe de Sean&quot;, ces groupes sont mieux définis et gérés au moment de l&#39;exécution dans AEM.

>[!TIP]
>
>Scripts Repo Init *must* être défini dans la `scripts` ou la variable `references` ne fonctionne pas.

Le vocabulaire complet des scripts Repo Init est disponible dans la [documentation d’Apache Sling Repo Init](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language).

>[!TIP]
>
>Pour obtenir un fragment de code complet, reportez-vous à la section [Fragments de code Repo Init](#snippet-repo-init) ci-dessous.

## Package de structure du référentiel {#repository-structure-package}

Les modules de code nécessitent la configuration du plug-in Maven FileVault pour référencer une `<repositoryStructurePackage>` qui applique l’exactitude des dépendances structurelles (pour s’assurer qu’un package de code ne s’installe pas sur un autre). Vous pouvez [créer votre propre package de structure de référentiel pour votre projet](repository-structure-package.md).

**Uniquement requis** pour les modules de code, c’est-à-dire tout module marqué par `<packageType>application</packageType>`.

Pour savoir comment créer un package de structure de référentiel pour votre application, voir [Développement d’un package de structure de référentiel](repository-structure-package.md).

Modules de contenu (`<packageType>content</packageType>`) **ne pas** nécessite ce module de structure de référentiel.

>[!TIP]
>
>Pour obtenir un fragment de code complet, reportez-vous à la section [Fragments de code XML POM](#xml-repository-structure-package) ci-dessous.

## Intégration de sous-modules dans le module conteneur{#embeddeds}

Les packages de contenu ou de code sont placés dans un dossier « sidecar » spécial et peuvent être ciblés en vue d’une installation sur AEM Author, AEM Publish, ou les deux, à l’aide de la configuration `<embeddeds>` du plug-in Maven FileVault. N’utilisez pas la variable `<subPackages>` configuration.

Scénarios d’utilisation courants :

+ Listes de contrôles d’accès/autorisations différentes selon qu’il s’agit d’utilisateurs AEM Author ou AEM Publish
+ Configurations utilisées pour prendre en charge les activités uniquement sur AEM Author
+ Code tel que des intégrations aux systèmes administratifs, nécessaire uniquement pour une exécution sur AEM Author

![Incorporation de packages](assets/embeddeds.png)

Pour cibler AEM auteur, AEM publie, ou les deux, le module est incorporé dans la variable `all` module conteneur dans un emplacement-dossier spécial, au format suivant :

`/apps/<app-name>-packages/(content|application|container)/install(.author|.publish)?`

Ventilation de cette structure de dossiers :

+ Le dossier de premier niveau **doit être** `/apps`.
+ Le dossier de deuxième niveau représente l’application, avec le `-packages` ajouté après le nom du dossier. Souvent, il n’existe qu’un seul dossier de deuxième niveau sous lequel tous les sous-modules sont incorporés, mais tout nombre de dossiers de deuxième niveau peut être créé pour représenter au mieux la structure logique de l’application :
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`

  >[!WARNING]
  >
  >Par convention, les dossiers incorporés des sous-modules sont nommés avec le suffixe de `-packages`. Ce nommage garantit que le code de déploiement et les modules de contenu sont **not** déploiement des dossiers cibles de tout sous-package ; `/apps/<app-name>/...`  qui entraîne un comportement d’installation destructif et cyclique.

+ Le dossier de troisième niveau doit être
  `application`, `content` ou `container`
   + Le dossier `application` contient des packages de code.
   + Le dossier `content` contient des packages de contenu.
   + Le dossier `container` contient les [packages d’applications supplémentaires](#extra-application-packages) pouvant être inclus par l’application AEM.
Ce nom de dossier correspond au [types de package](#package-types) des modules qu’il contient.
+ Le dossier de quatrième niveau contient les sous-modules et doit être l’un des suivants :
   + `install` vous devez donc installer sur **both** Création AEM et publication AEM
   + `install.author` vous devez installer **only** sur l’auteur AEM
   + `install.publish` vous devez installer **only** sur AEM publication uniquement `install.author` et `install.publish` sont des cibles prises en charge. Les autres modes d’exécution **ne sont pas** pris en charge.

Par exemple, un déploiement qui contient des packages spécifiques à AEM Author et AEM Publish peut se présenter comme suit :

+ Le package conteneur `all` intègre les packages suivants afin de créer un artefact de déploiement unique
   + `ui.apps` incorporé dans `/apps/my-app-packages/application/install` déploie le code sur AEM Author et AEM Publish
   + `ui.apps.author` incorporé dans `/apps/my-app-packages/application/install.author` déploie le code uniquement sur AEM Author
   + `ui.content` incorporé dans `/apps/my-app-packages/content/install` déploie le contenu et la configuration sur AEM Author et AEM Publish
   + `ui.content.publish` incorporé dans `/apps/my-app-packages/content/install.publish` déploie le contenu et la configuration uniquement sur AEM Publish

>[!TIP]
>
>Pour obtenir un fragment de code complet, reportez-vous à la section [Fragments de code XML POM](#xml-embeddeds) ci-dessous.

### Définition du filtre du package conteneur {#container-package-filter-definition}

En raison de l’incorporation des sous-modules de code et de contenu dans le module conteneur, les chemins d’accès cibles incorporés doivent être ajoutés au fichier du projet de conteneur. `filter.xml`. Cela permet de s’assurer que les modules incorporés sont inclus dans le module conteneur lors de sa création.

Il vous suffit d’ajouter la variable `<filter root="/apps/<my-app>-packages"/>` des entrées pour tous les dossiers de deuxième niveau contenant des sous-modules à déployer.

>[!TIP]
>
>Pour obtenir un fragment de code complet, reportez-vous à la section [Fragments de code XML POM](#xml-container-package-filters) ci-dessous.

## Incorporation de packages tiers {#embedding-3rd-party-packages}

Tous les packages doivent être disponibles via le [Référentiel d’artefacts Maven public d’Adobe](https://repo1.maven.org/maven2/com/adobe/) ou un référentiel d’artefacts Maven tiers accessible au public pouvant être référencé.

Si les modules tiers se trouvent dans **Référentiel d’artefacts Maven public d’Adobe**, aucune configuration supplémentaire n’est nécessaire pour qu’Adobe Cloud Manager puisse résoudre les artefacts.

Si les modules tiers se trouvent dans une **référentiel d’artefacts Maven tiers public**, ce référentiel doit être enregistré dans le `pom.xml` et incorporé suivant la méthode [présenté ci-dessus](#embeddeds).

Les applications/connecteurs tiers doivent être incorporés à l’aide de ses `all` module en tant que conteneur dans le conteneur de votre projet (`all`).

L’ajout de dépendances Maven suit les pratiques Maven standard et l’incorporation d’artefacts tiers (modules de code et de contenu) sont [présenté ci-dessus](#embedding-3rd-party-packages).

>[!TIP]
>
>Pour obtenir un fragment de code complet, reportez-vous à la section [Fragments de code XML POM](#xml-3rd-party-maven-repositories) ci-dessous.

## Dépendances entre les packages `ui.apps` et `ui.content` {#package-dependencies}

Pour assurer une installation correcte des packages, il est recommandé d’établir des dépendances inter-packages.

La règle est que les packages contenant du contenu modifiable (`ui.content`) doivent dépendre du code non modifiable (`ui.apps`) qui prend en charge le rendu et l’utilisation du contenu modifiable.

Une exception notable à cette règle générale est que le package de code non modifiable (`ui.apps` ou autre) contient __uniquement__ des bundles OSGi. Si tel est le cas, aucun package AEM ne doit déclarer une dépendance à son égard. La raison est que les modules de code non modifiables incluent __only__ contenir des lots OSGi, ne sont pas enregistrés avec AEM [Gestionnaire de modules](/help/implementing/developing/tools/package-manager.md). Par conséquent, tout module AEM qui en dépend a une dépendance insatisfaite et ne parvient pas à s’installer.

>[!TIP]
>
>Pour obtenir un fragment de code complet, reportez-vous à la section [Fragments de code XML POM](#xml-package-dependencies) ci-dessous.

Les schémas courants applicables aux dépendances des packages de contenu sont les suivants :

### Dépendances de packages dans un déploiement simple {#simple-deployment-package-dependencies}

Dans ce scénario, le package de contenu modifiable `ui.content` est défini de telle sorte qu’il dépende du package de code non modifiable `ui.apps`.

+ `all` ne comporte aucune dépendance
   + `ui.apps` ne comporte aucune dépendance
   + `ui.content` dépend de `ui.apps`

### Dépendances de packages dans un déploiement complexe {#complex-deploxment-package-dependencies}

Les déploiements complexes étendent le scénario de déploiement simple et définissent les dépendances entre les packages de contenu modifiable et non modifiable correspondants. Suivant les besoins, des dépendances peuvent également être établies entre des packages de code non modifiable.

+ `all` ne comporte aucune dépendance
   + `common.ui.apps.common` ne comporte aucune dépendance
   + `site-a.ui.apps` dépend de `common.ui.apps`
   + `site-a.ui.content` dépend de `site-a.ui.apps`
   + `site-b.ui.apps` dépend de `common.ui.apps`
   + `site-b.ui.content` dépend de `site-b.ui.apps`

## Développement et déploiement en local {#local-development-and-deployment}

L’organisation et les structures de projet décrites dans cet article sont **entièrement compatibles** avec les instances AEM de développement en local.

## Fragments de code XML POM {#pom-xml-snippets}

Vous trouverez, ci-après, des fragments de code de configuration `pom.xml` Maven pouvant être ajoutés aux projets Maven pour respecter les recommandations ci-dessus.

### Types de packages {#xml-package-types}

Les modules de code et de contenu qui sont déployés sous la forme de sous-modules doivent déclarer un type de module **application** ou **content**, selon ce qu’ils contiennent.

#### Types de packages conteneur {#container-package-types}

Le projet `all/pom.xml` du conteneur ne déclare **pas** de `<packageType>`.

#### Types de packages de code (non modifiable)  {#immutable-package-types}

Les packages de code doivent définir leur `packageType` sur `application`.

Dans le fichier `ui.apps/pom.xml`, la directive de configuration de version `<packageType>application</packageType>` de la déclaration du plug-in `filevault-package-maven-plugin` déclare son type de package.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        <group>${project.groupId}</group>
        <name>my-app.ui.apps</name>
        <packageType>application</packageType>
        <accessControlHandling>merge</accessControlHandling>
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

#### Types de packages de contenu (modifiable)  {#mutable-package-types}

Les packages de contenu doivent définir leur `packageType` sur `content`.

Dans le fichier `ui.content/pom.xml`, la directive de configuration de version `<packageType>content</packageType>` de la déclaration du plug-in `filevault-package-maven-plugin` déclare son type de package.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        <group>${project.groupId}</group>
        <name>my-app.ui.content</name>
        <packageType>content</packageType>
        <accessControlHandling>merge</accessControlHandling>
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

### Marquage de packages en vue d’un déploiement par Adobe Cloud Manager {#cloud-manager-target}

Dans chaque projet générant un package, **à l’exception** du projet conteneur (`all`), ajoutez `<cloudManagerTarget>none</cloudManagerTarget>` à la configuration `<properties>` de la déclaration du plug-in `filevault-package-maven-plugin` pour vous assurer que le déploiement n’est **pas** effectué par Adobe Cloud Manager. Le package conteneur (`all`) doit être le package unique déployé via Cloud Manager qui, à son tour, incorpore tous les packages de code et de contenu requis.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        ...
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

### Repo Init {#snippet-repo-init}

Les scripts Repo Init sont définis dans la configuration d’usine OSGi `RepositoryInitializer` via la propriété `scripts`. Comme ces scripts sont définis dans les configurations OSGi, ils peuvent être facilement définis par le mode d’exécution à l’aide de la méthode habituelle `../config.<runmode>` sémantique du dossier.

Comme les scripts sont généralement des déclarations multilignes, il est plus facile de les définir dans la variable `.config` plutôt que le fichier basé sur JSON. `.cfg.json` format.

`/apps/my-app/config.author/org.apache.sling.jcr.repoinit.RepositoryInitializer-author.config`

```plain
scripts=["
    create service user my-data-reader-service

    set ACL on /var/my-data
        allow jcr:read for my-data-reader-service
    end

    create path (sling:Folder) /conf/my-app/settings
"]
```

La propriété OSGi `scripts` contient des directives définies par le [langage Repo Init d’Apache Sling](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language).

### Package de structure du référentiel {#xml-repository-structure-package}

Dans le fichier `ui.apps/pom.xml`, ainsi que dans tout autre fichier `pom.xml` qui déclare un package de code (`<packageType>application</packageType>`), ajoutez la configuration de package de structure de référentiel suivante au plug-in Maven FileVault. Vous pouvez [créer votre propre package de structure de référentiel pour votre projet](repository-structure-package.md).

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        ...
        <repositoryStructurePackages>
          <repositoryStructurePackage>
              <groupId>${project.groupId}</groupId>
              <artifactId>ui.apps.structure</artifactId>
              <version>${project.version}</version>
          </repositoryStructurePackage>
        </repositoryStructurePackages>
      </configuration>
    </plugin>
    ...
```

### Intégration de sous-modules dans le module conteneur {#xml-embeddeds}

Dans le fichier `all/pom.xml`, ajoutez les directives `<embeddeds>` suivantes à la déclaration du plug-in `filevault-package-maven-plugin`. Souvenez-vous, **ne pas** utilisez la méthode `<subPackages>` configuration. La raison en est qu’elle inclut les sous-modules dans `/etc/packages` plutôt que `/apps/my-app-packages/<application|content|container>/install(.author|.publish)?`.

```xml
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <embeddeds>

          <!-- Include the application's ui.apps and ui.content packages -->
          <!-- Ensure the artifactIds are correct -->

          <!-- OSGi Bundle Jar file that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.core</artifactId>
              <type>jar</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

          <!-- Code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

           <!-- OSGi configuration code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.config</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

          <!-- Code package that deploys ONLY to AEM Author -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps.author</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install.author</target>
          </embedded>

          <!-- Content package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.content</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/content/install</target>
          </embedded>

          <!-- Content package that deploys ONLY to AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.content.publish-only</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/content/install.publish</target>
          </embedded>

          <!-- Include any other extra packages  -->
          <embedded>
              <groupId>com.vendor.x</groupId>
              <artifactId>vendor.plug-in.all</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/container/install</target>
          </embedded>
      <embeddeds>
  </configuration>
</plugin>
...
```

### Définition du filtre du package conteneur {#xml-container-package-filters}

Dans le `all` du projet `filter.xml` (`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`), **include** any `-packages` dossiers contenant des sous-modules à déployer :

```xml
<filter root="/apps/my-app-packages"/>
```

Si plusieurs `/apps/*-packages` sont utilisés dans les cibles incorporées, ils doivent tous être énumérés ici.

### Référentiels Maven tiers {#xml-3rd-party-maven-repositories}

>[!WARNING]
>
>L’ajout d’autres référentiels Maven peut prolonger les délais de création, car d’autres référentiels Maven sont vérifiés pour en déterminer les dépendances.

Dans le projet Reactor `pom.xml`, ajoutez toute directive de référentiel Maven public tiers nécessaire. L&#39;intégralité `<repository>` La configuration doit être disponible auprès du fournisseur de référentiel tiers.

```xml
<repositories>
  ...
  <repository>
      <id>3rd-party-repository</id>
      <name>Public 3rd Party Repository</name>
      <url>https://repo.3rdparty.example.com/...</url>
      <releases>
          <enabled>true</enabled>
          <updatePolicy>never</updatePolicy>
      </releases>
      <snapshots>
          <enabled>false</enabled>
      </snapshots>
  </repository>
  ...
</repositories>
```

### Dépendances entre les packages `ui.apps` et `ui.content` {#xml-package-dependencies}

Dans le fichier `ui.content/pom.xml`, ajoutez les directives `<dependencies>` suivantes à la déclaration du plug-in `filevault-package-maven-plugin`.

```xml
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <dependencies>
        <!-- Declare the content package dependency in the ui.content/pom.xml on the ui.apps project -->
        <dependency>
            <groupId${project.groupId}</groupId>
            <artifactId>my-app.ui.apps</artifactId>
            <version>${project.version}</version>
        </dependency>
      </dependencies>
    ...
  </configuration>
</plugin>
...
```

### Nettoyage du dossier cible du projet de conteneur {#xml-clean-container-package}

Dans le `all/pom.xml`, ajoutez le `maven-clean-plugin` qui nettoie le répertoire cible avant une version de Maven.

```xml
<plugins>
  ...
  <plugin>
    <artifactId>maven-clean-plugin</artifactId>
    <executions>
      <execution>
        <id>auto-clean</id>
        <!-- Run at the beginning of the build rather than the default, which is after the build is done -->
        <phase>initialize</phase>
        <goals>
          <goal>clean</goal>
        </goals>
      </execution>
    </executions>
  </plugin>
  ...
</plugins>
```

## Ressources supplémentaires {#additional-resources}

+ [Gestion des packages à l’aide de Maven](/help/implementing/developing/tools/maven-plugin.md)
+ [Plug-in FileVault Content Package Maven](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
