---
title: Étendre Multi Site Manager
description: Découvrez comment étendre les fonctionnalités de Multi Site Manager.
exl-id: 4b7a23c3-65d1-4784-9dea-32fcceca37d1
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2336'
ht-degree: 59%

---

# Étendre Multi Site Manager {#extending-the-multi-site-manager}

Ce document vous aide à comprendre comment étendre les fonctionnalités de Multi Site Manager et couvre les sujets suivants.

* Découvrez les principaux membres de l’API Java MSM
* Créez une nouvelle action de synchronisation pouvant être utilisée dans une configuration de déploiement
* Modifier la langue et les codes pays par défaut

>[!TIP]
>
>Cette page est plus facile à comprendre dans le contexte du document [Réutilisation de contenu : Multi Site Manager](/help/sites-cloud/administering/msm/overview.md).

>[!CAUTION]
>
>Multi Site Manager et son API sont utilisés lors de la création d’un site web et ne sont donc destinés qu’à un environnement de création.

## Vue d’ensemble de l’API Java {#overview-of-the-java-api}

La gestion multisite se compose des packages suivants :

* [com.day.cq.wcm.msm.api](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/package-frame.html)
* [com.day.cq.wcm.msm.commons](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/commons/package-frame.html)

Les principaux objets API MSM interagissent comme suit (voir également la section [Termes utilisés](/help/sites-cloud/administering/msm/overview.md#terms-used)) :

![Principaux objets de l’API MSM](assets/msm-api-interaction.png)

* **`Blueprint`** - Un `Blueprint` (comme dans [configuration de plan directeur](/help/sites-cloud/administering/msm/overview.md#source-blueprints-and-blueprint-configurations)) spécifie les pages à partir desquelles une Live Copy peut hériter du contenu.

  ![Plan directeur](assets/msm-blueprint-interaction.png)

   * L’utilisation d’une configuration de plan directeur (`Blueprint`) est facultative, mais :

      * Il permet à l’auteur d’utiliser l’option **Déployer** sur la source pour pousser explicitement les modifications vers les Live Copies qui héritent de cette source.
      * Il permet à l’auteur d’utiliser **Créer un site**, ce qui permet à l’utilisateur de sélectionner facilement les langues et de configurer la structure de la Live Copy.
      * Il définit la configuration de déploiement par défaut pour toutes les Live Copies créées.

* **`LiveRelationship`** - Le `LiveRelationship` spécifie le lien (relation) entre une ressource dans la branche Live Copy et sa ressource source/plan directeur équivalente.

   * Les relations sont utilisées lors de la réalisation de l’héritage et du déploiement.
   * Les objets `LiveRelationship` fournissent un accès (références) aux objets de configuration de déploiement (`RolloutConfig`), `LiveCopy` et `LiveStatus` liés à la relation.

   * Par exemple, une Live Copy est créée dans `/content/copy/us` à partir de la source ou du plan directeur au niveau `/content/wknd/language-masters`. Les ressources `/content/wknd/language-masters/en/jcr:content` et `/content/copy/us/en/jcr:content` forment une relation.

* **`LiveCopy`** - Un `LiveCopy` contient les détails de configuration pour les relations (`LiveRelationship`) entre les ressources de Live Copy et leurs ressources de source ou de plan directeur.

   * Utilisez la classe `LiveCopy` pour accéder au chemin d’accès de la page, au chemin d’accès de la page de source ou de plan directeur, aux configurations de déploiement et si les pages enfants sont également incluses dans la `LiveCopy`.

   * Un nœud `LiveCopy` est créé chaque fois que **Créer un site** ou **Créer une Live Copy** est utilisé.

* **`LiveStatus`** - Les objets `LiveStatus` donnent accès au statut d’exécution d’un `LiveRelationship`. Permet d’interroger le statut de synchronisation d’une Live Copy.

* **`LiveAction`** - Une `LiveAction` est une action exécutée sur chaque ressource impliquée dans le déploiement.

   * Les `LiveAction` ne sont générés que par les `RolloutConfig`.

* **`LiveActionFactory`** - Un `LiveActionFactory` crée `LiveAction` objets selon une configuration `LiveAction`. Les configurations sont stockées en tant que ressources dans le référentiel.

* **`RolloutConfig`** - Le `RolloutConfig` contient une liste de `LiveActions` à utiliser lors du déclenchement. La `LiveCopy` hérite de `RolloutConfig` et le résultat est présent dans `LiveRelationship`.

   * La toute première configuration d’une Live Copy utilise également un `RolloutConfig` (qui déclenche les `LiveAction` ).

## Créer une action de synchronisation {#creating-a-new-synchronization-action}

Vous pouvez créer des actions de synchronisation personnalisées à utiliser avec vos configurations de déploiement. Cela peut s’avérer utile lorsque les [actions installées](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-synchronization-actions) ne répondent pas aux exigences spécifiques de votre application.

Pour ce faire, créez deux classes :

* Une implémentation de l’interface [`com.day.cq.wcm.msm.api.LiveAction`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveAction.html) qui effectue l’action.
* Un composant OSGi qui implémente l’interface [`com.day.cq.wcm.msm.api.LiveActionFactory`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) et crée des instances de votre classe `LiveAction`

La `LiveActionFactory` crée des instances de la classe `LiveAction` pour une configuration donnée :

* Les classes `LiveAction` incluent les méthodes suivantes :

   * `getName` - Renvoie le nom de l’action

      * Le nom est utilisé pour faire référence à l’action, par exemple, dans les configurations de déploiement.

   * `execute` - Effectue les tâches de l’action

* Les classes `LiveActionFactory` incluent les méthodes suivantes :

   * `LIVE_ACTION_NAME` - Champ contenant le nom du `LiveAction` associé

      * Ce nom doit coïncider avec la valeur renvoyée par la méthode `getName` de la classe `LiveAction`.

   * `createAction` - Crée une instance du `LiveAction`

      * Le paramètre facultatif `Resource` peut être utilisé pour fournir des informations de configuration.

   * `createsAction` - Renvoie le nom du `LiveAction` associé

### Accès au nœud de configuration LiveAction {#accessing-the-liveaction-configuration-node}

Utilisez le nœud de configuration `LiveAction` dans le référentiel pour stocker les informations qui affectent le comportement d’exécution de l’instance `LiveAction`. Le nœud du référentiel qui stocke la configuration `LiveAction` est disponible pour l’objet `LiveActionFactory` lors de l’exécution. Par conséquent, vous pouvez ajouter des propriétés au nœud de configuration et les utiliser dans votre implémentation `LiveActionFactory` si nécessaire.

Par exemple, un `LiveAction` doit stocker le nom de l’auteur du plan directeur. Une propriété du nœud de configuration inclut le nom de la propriété de la page plan directeur qui stocke les informations. Lorsqu’elle est exécutée, la `LiveAction` récupère le nom de la propriété à partir de la configuration, puis obtient la valeur de la propriété.

Le paramètre de la méthode [`LiveActionFactory.createAction`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) est un objet `Resource`. Cet objet `Resource` représente le nœud `cq:LiveSyncAction` pour cette LiveAction dans la configuration du déploiement.

Voir [Création d’une configuration de déploiement](/help/sites-cloud/administering/msm/live-copy-sync-config.md#creating-a-rollout-configuration) pour plus d’informations.

Comme d’habitude, lorsque vous utilisez un nœud de configuration, vous devez l’adapter à un objet `ValueMap` :

```java
public LiveAction createAction(Resource resource) throws WCMException {
        ValueMap config;
        if (resource == null || resource.adaptTo(ValueMap.class) == null) {
            config = new ValueMapDecorator(Collections.<String, Object>emptyMap());
        } else {
            config = resource.adaptTo(ValueMap.class);
        }
        return new MyLiveAction(config, this);
}
```

### Accès aux nœuds cibles, aux nœuds sources et à la relation LiveRelationship {#accessing-target-nodes-source-nodes-and-the-liverelationship}

Les objets suivants sont fournis en tant que paramètres de la méthode `execute` de l’objet `LiveAction` :

* Objet [`Resource`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) représentant la source de la Live Copy
* Objet `Resource` représentant la cible de la Live Copy.
* Objet [`LiveRelationship`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/msm/api/LiveRelationship.html) pour la Live Copy
   * La valeur `autoSave` indique si votre `LiveAction` doit enregistrer les modifications apportées au référentiel
   * La valeur `reset` indique le mode de réinitialisation du déploiement.

À partir de ces objets, vous pouvez obtenir des informations sur le `LiveCopy` . Vous pouvez également utiliser les objets `Resource` pour obtenir les objets `ResourceResolver`, `Session` et `Node`. Ces objets sont utiles pour manipuler le contenu du référentiel :

Dans la première ligne du code suivant, source est l’objet `Resource` de la page source :

```java
ResourceResolver resolver = source.getResourceResolver();
Session session = resolver.adaptTo(javax.jcr.Session.class);
Node sourcenode = source.adaptTo(javax.jcr.Node.class);
```

>[!NOTE]
>
>Les arguments `Resource` peuvent être des objets `null` ou `Resources` qui ne s’adaptent pas aux objets `Node`, tels que les objets [`NonExistingResource`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/NonExistingResource.html).

## Créer une configuration de déploiement {#creating-a-new-rollout-configuration}

Vous pouvez créer une configuration de déploiement lorsque celles installées ne répondent pas aux exigences de votre application en deux étapes :

* [Création de la configuration de déploiement](#create-the-rollout-configuration)
* [Ajouter des actions de synchronisation à la configuration de déploiement](#add-synchronization-actions-to-the-rollout-configuration)

La nouvelle configuration de déploiement est alors disponible pour vous lors de la définition des configurations de déploiement sur une page de plan directeur ou de Live Copy.

>[!TIP]
>
>Consultez également les [bonnes pratiques pour la personnalisation des déploiements](/help/sites-cloud/administering/msm/best-practices.md#customizing-rollouts).

### Créer la configuration de déploiement {#create-the-rollout-configuration}

Pour créer une configuration de déploiement :

1. Ouvrez CRXDE Lite sur `https://<host>:<port>/crx/de`.

1. Accédez à `/apps/msm/<your-project>/rolloutconfigs`, la version personnalisée de `/libs/msm/wcm/rolloutconfigs` de votre projet.

   * S’il s’agit de votre première configuration, cette branche `/libs` doit être utilisée comme modèle pour créer la branche sous `/apps`.

1. Sous cet emplacement, créez un nœud avec les propriétés suivantes :

   * **Nom** : nom de nœud de la configuration de déploiement, par exemple `contentCopy` ou `workflow`
   * **Type** : `cq:RolloutConfig`

1. Ajoutez les propriétés suivantes à ce nœud :

   * **Nom** : `jcr:title`
     **Type** : `String`
     **Valeur** : titre d’identification qui apparaîtra dans l’interface utilisateur

   * **Nom** : `jcr:description`
     **Type** : `String`
     **Valeur** : une description facultative.

   * **Nom** : `cq:trigger`
     **Type** : `String`
     **Value** : [ Déclencheur de déploiement](/help/sites-cloud/administering/msm/live-copy-sync-config.md#rollout-triggers) à utiliser
      * `rollout`
      * `modification`
      * `publish`
      * `deactivate`

1. Cliquez sur **Enregistrer tout**.

### Ajouter des actions de synchronisation à la configuration de déploiement {#add-synchronization-actions-to-the-rollout-configuration}

Les configurations de déploiement sont stockées sous le nœud [configuration de déploiement](#create-the-rollout-configuration) que vous avez créé sous le nœud `/apps/msm/<your-project>/rolloutconfigs`.

Ajoutez des nœuds enfants de type `cq:LiveSyncAction` pour ajouter des actions de synchronisation à la configuration de déploiement. L’ordre des nœuds d’action de synchronisation détermine l’ordre dans lequel les actions se produisent.

1. Dans CRXDE Lite, sélectionnez votre nœud [Configuration du déploiement](#create-the-rollout-configuration), par exemple, `/apps/msm/myproject/rolloutconfigs/myrolloutconfig`.

1. Créez un nœud avec les propriétés de nœud suivantes :

   * **Name** : nom de nœud de l’action de synchronisation
      * Le nom doit être identique au **Nom de l’action** dans la table sous [Actions de synchronisation](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-synchronization-actions) tel que `contentCopy` ou `workflow`.
   * **Type** : `cq:LiveSyncAction`

1. Ajoutez et configurez autant de nœuds d’action de synchronisation que nécessaire.

1. Réorganisez les nœuds d’action afin que leur ordre corresponde à celui dans lequel vous souhaitez qu’ils se produisent.
   * Le nœud d’action le plus haut se produit en premier.

## Création et utilisation d’une classe LiveActionFactory simple {#creating-and-using-a-simple-liveactionfactory-class}

Suivez les procédures de cette section pour développer une `LiveActionFactory` et l’utiliser dans une configuration de déploiement. Les procédures utilisent Maven et Eclipse pour développer et déployer la `LiveActionFactory` :

1. [Créez le projet Maven](#create-the-maven-project) et importez-le dans Eclipse.
1. [Ajoutez des dépendances](#add-dependencies-to-the-pom-file) au fichier POM.
1. [Implémentez l’interface `LiveActionFactory` et déployez ](#implement-liveactionfactory) lot OSGi.
1. [Créez la configuration de déploiement](#create-the-example-rollout-configuration).
1. [Créez la Live Copy](#create-the-live-copy).

[Le projet Maven et le code source de la classe Java](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-msmrollout) sont disponibles dans le référentiel Git public.

### Créer le projet Maven {#create-the-maven-project}

La procédure suivante nécessite que vous ayez ajouté le profil `adobe-public` à votre fichier de paramètres Maven.

* Pour plus d’informations sur le profil adobe-public, voir [Obtention du plug-in de module de contenu Maven](/help/implementing/developing/tools/maven-plugin.md#obtaining-the-content-package-maven-plugin).
* Pour plus d’informations sur le fichier de paramètres Maven, voir [Référence des paramètres](https://maven.apache.org/settings.html) Maven.

1. Ouvrez une session de terminal ou de ligne de commande, puis modifiez le répertoire pour qu’il pointe vers l’emplacement où le projet sera créé.
1. Saisissez la commande suivante :

   ```text
   mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault -DarchetypeArtifactId=multimodule-content-package-archetype -DarchetypeVersion=1.0.0 -DarchetypeRepository=adobe-public-releases
   ```

1. Spécifiez les valeurs suivantes au prompt interactif :

   * **`groupId`**: `com.adobe.example.msm`
   * **`artifactId`**: `MyLiveActionFactory`
   * **`version`**: `1.0-SNAPSHOT`
   * **`package`**: `MyPackage`
   * **`appsFolderName`**: `myapp`
   * **`artifactName`**: `MyLiveActionFactory package`
   * **`packageGroup`**: `myPackages`

1. Démarrez Eclipse et [importez le projet Maven](/help/implementing/developing/tools/eclipse.md#import-the-maven-project-into-eclipse).

### Ajouter des dépendances au fichier POM {#add-dependencies-to-the-pom-file}

Ajoutez des dépendances pour que le compilateur Eclipse puisse référencer les classes utilisées dans le code `LiveActionFactory`.

1. Dans l’explorateur de projet Eclipse, ouvrez le fichier `MyLiveActionFactory/pom.xml`.

1. Dans l’éditeur, cliquez sur l’onglet `pom.xml` et localisez la section `project/dependencyManagement/dependencies`.

1. Ajoutez le code XML suivant dans l’élément `dependencyManagement`, puis enregistrez le fichier.

   ```xml
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-msm-api</artifactId>
     <version>5.6.2</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.api</artifactId>
     <version>2.4.3-R1488084</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-wcm-api</artifactId>
     <version>5.6.6</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.commons.json</artifactId>
     <version>2.0.6</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
     <version>5.6.4</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
     <version>2.0.0</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
     <version>5.6.4</version>
     <scope>provided</scope>
    </dependency>
   ```

1. Ouvrez le fichier POM pour le bundle depuis l’**explorateur de projets** à l’adresse `MyLiveActionFactory-bundle/pom.xml`.

1. Dans l’éditeur, cliquez sur l’onglet `pom.xml` et localisez la section project/dependencies. Ajoutez le code XML suivant dans l’élément des dépendances, puis enregistrez le fichier :

   ```xml
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-msm-api</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.api</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-wcm-api</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.commons.json</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
    </dependency>
   ```

### Implémenter LiveActionFactory {#implement-liveactionfactory}

La classe `LiveActionFactory` suivante implémente une `LiveAction` qui enregistre les messages sur les pages source et cible et copie la propriété `cq:lastModifiedBy` du nœud source vers le nœud cible. Le nom de la live action est `exampleLiveAction`.

1. Dans l’explorateur de projet Eclipse, cliquez avec le bouton droit de la souris sur le package `MyLiveActionFactory-bundle/src/main/java/com.adobe.example.msm`, puis cliquez sur **Nouveau** > **Classe**.

1. Comme **nom**, entrez `ExampleLiveActionFactory`, puis cliquez sur **Terminer**.

1. Ouvrez le fichier `ExampleLiveActionFactory.java`, remplacez le contenu par le code suivant et enregistrez le fichier.

   ```java
   package com.adobe.example.msm;
   
   import java.util.Collections;
   
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Property;
   import org.apache.felix.scr.annotations.Service;
   import org.apache.sling.api.resource.Resource;
   import org.apache.sling.api.resource.ResourceResolver;
   import org.apache.sling.api.resource.ValueMap;
   import org.apache.sling.api.wrappers.ValueMapDecorator;
   import org.apache.sling.commons.json.io.JSONWriter;
   import org.apache.sling.commons.json.JSONException;
   
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   
   import com.day.cq.wcm.msm.api.ActionConfig;
   import com.day.cq.wcm.msm.api.LiveAction;
   import com.day.cq.wcm.msm.api.LiveActionFactory;
   import com.day.cq.wcm.msm.api.LiveRelationship;
   import com.day.cq.wcm.api.WCMException;
   
   @Component(metatype = false)
   @Service
   public class ExampleLiveActionFactory implements LiveActionFactory<LiveAction> {
    @Property(value="exampleLiveAction")
    static final String actionname = LiveActionFactory.LIVE_ACTION_NAME;
   
    public LiveAction createAction(Resource config) {
     ValueMap configs;
     /* Adapt the config resource to a ValueMap */
           if (config == null || config.adaptTo(ValueMap.class) == null) {
               configs = new ValueMapDecorator(Collections.<String, Object>emptyMap());
           } else {
               configs = config.adaptTo(ValueMap.class);
           }
   
     return new ExampleLiveAction(actionname, configs);
    }
    public String createsAction() {
     return actionname;
    }
    /************* LiveAction ****************/
    private static class ExampleLiveAction implements LiveAction {
     private String name;
     private ValueMap configs;
     private static final Logger log = LoggerFactory.getLogger(ExampleLiveAction.class);
   
     public ExampleLiveAction(String nm, ValueMap config){
      name = nm;
      configs = config;
     }
   
     public void execute(Resource source, Resource target,
       LiveRelationship liverel, boolean autoSave, boolean isResetRollout)
         throws WCMException {
   
      String lastMod = null;
   
      log.info(" *** Executing ExampleLiveAction *** ");
   
      /* Determine if the LiveAction is configured to copy the cq:lastModifiedBy property */
      if ((Boolean) configs.get("repLastModBy")){
   
       /* get the source's cq:lastModifiedBy property */
       if (source != null && source.adaptTo(Node.class) !=  null){
        ValueMap sourcevm = source.adaptTo(ValueMap.class);
        lastMod = sourcevm.get(com.day.cq.wcm.msm.api.MSMNameConstants.PN_PAGE_LAST_MOD_BY, String.class);
       }
   
       /* set the target node's la-lastModifiedBy property */
       Session session = null;
       if (target != null && target.adaptTo(Node.class) !=  null){
        ResourceResolver resolver = target.getResourceResolver();
        session = resolver.adaptTo(javax.jcr.Session.class);
        Node targetNode;
        try{
         targetNode=target.adaptTo(javax.jcr.Node.class);
         targetNode.setProperty("la-lastModifiedBy", lastMod);
         log.info(" *** Target node lastModifiedBy property updated: {} ***",lastMod);
        }catch(Exception e){
         log.error(e.getMessage());
        }
       }
       if(autoSave){
        try {
         session.save();
        } catch (Exception e) {
         try {
          session.refresh(true);
         } catch (RepositoryException e1) {
          e1.printStackTrace();
         }
         e.printStackTrace();
        }
       }
      }
     }
     public String getName() {
      return name;
     }
   
     /************* Deprecated *************/
     @Deprecated
     public void execute(ResourceResolver arg0, LiveRelationship arg1,
       ActionConfig arg2, boolean arg3) throws WCMException {
     }
     @Deprecated
     public void execute(ResourceResolver arg0, LiveRelationship arg1,
       ActionConfig arg2, boolean arg3, boolean arg4)
         throws WCMException {
     }
     @Deprecated
     public String getParameterName() {
      return null;
     }
     @Deprecated
     public String[] getPropertiesNames() {
      return null;
     }
     @Deprecated
     public int getRank() {
      return 0;
     }
     @Deprecated
     public String getTitle() {
      return null;
     }
     @Deprecated
     public void write(JSONWriter arg0) throws JSONException {
     }
    }
   }
   ```

1. A l’aide du terminal ou de la session de commande, remplacez le répertoire par le répertoire `MyLiveActionFactory` (répertoire du projet Maven). Ensuite, entrez la commande suivante :

   ```shell
   mvn -PautoInstallPackage clean install
   ```

1. Le fichier `error.log` d’AEM doit indiquer que le bundle est démarré, visible dans les journaux à l’`https://<host>:<port>/system/console/status-slinglogs`.

   ```text
   13.08.2013 14:34:55.450 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent RESOLVED
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTING
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTED
   13.08.2013 14:34:55.453 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle Service [com.adobe.example.msm.ExampleLiveActionFactory,2188] ServiceEvent REGISTERED
   13.08.2013 14:34:55.454 *INFO* [OsgiInstallerImpl] org.apache.sling.audit.osgi.installer Started bundle com.adobe.example.msm.MyLiveActionFactory-bundle [316]
   ```

### Création de l’exemple de configuration de déploiement {#create-the-example-rollout-configuration}

Créez la configuration de déploiement du MSM qui utilise la `LiveActionFactory` que vous avez créée :

1. Créez et configurez une [configuration de déploiement avec la procédure standard](/help/sites-cloud/administering/msm/live-copy-sync-config.md#creating-a-rollout-configuration) à l’aide des propriétés :

   * **Titre** : exemple de configuration de déploiement
   * **Nom** : examplerolloutconfig
   * **cq:trigger** : `publish`

### Ajout de la LiveAction à l’exemple de configuration de déploiement {#add-the-live-action-to-the-example-rollout-configuration}

Paramétrez la configuration de déploiement que vous avez créée dans la procédure précédente afin qu’elle utilise la classe `ExampleLiveActionFactory`.

1. Ouvrez CRXDE Lite.

1. Créez le nœud correspondant sous `/apps/msm/rolloutconfigs/examplerolloutconfig/jcr:content` :

   * **Nom** : `exampleLiveAction`
   * **Type** : `cq:LiveSyncAction`

1. Cliquez sur **Enregistrer tout**.

1. Sélectionnez le nœud `exampleLiveAction` et ajoutez une propriété pour indiquer à la classe `ExampleLiveAction` que la propriété `cq:LastModifiedBy` doit être répliquée du nœud source vers le nœud cible.

   * **Nom** : `repLastModBy`
   * **Type** : `Boolean`
   * **Valeur** : `true`

1. Cliquez sur **Enregistrer tout**.

### Créer la Live Copy {#create-the-live-copy}

[Créez une Live Copy](/help/sites-cloud/administering/msm/creating-live-copies.md#creating-a-live-copy-of-a-page) de la branche Anglais/Produits du site de référence WKND à l’aide de votre configuration de déploiement :

* **Source** : `/content/wknd/language-masters/en/products`

* **Configuration de déploiement** : exemple de configuration de déploiement

Activez la page **Products** (en anglais) de la branche source et observez les messages de journalisation générés par la classe `LiveAction` :

```xml
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***ExampleLiveAction has been executed.***
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***Target node lastModifiedBy property updated: admin ***
```

## Modifer les noms de langue et les pays par défaut {#changing-language-names-and-default-countries}

AEM utilise un ensemble par défaut de codes de langue et de pays.

* Le code de langue par défaut est le code à deux lettres en minuscules, tel que défini par la norme ISO-639-1.
* Le code de pays par défaut est le code à deux lettres, en minuscules ou en majuscules, comme défini par la norme ISO 3166.

MSM utilise une liste stockée de codes de langue et de pays pour déterminer le nom du pays associé au nom de la version linguistique de votre page. Si nécessaire, vous pouvez modifier les aspects suivants de la liste :

* Titres de langue
* Noms de pays
* Pays par défaut pour les langues (pour les codes tels que `en`, `de`, entre autres)

La liste des langues est stockée sous le nœud `/libs/wcm/core/resources/languages`. Chaque nœud enfant représente une langue ou un code langue-pays :

* Le nom du nœud est le code langue (par exemple `en` ou `de`) ou le code language_country (par exemple `en_us` ou `de_ch`).

* La propriété `language` du nœud stocke le nom complet de la langue pour le code.
* La propriété `country` du nœud stocke le nom complet du pays pour le code.
* Lorsque le nom de nœud consiste uniquement en un code de langue (`en`, par exemple), la propriété de pays est `*` et une propriété supplémentaire `defaultCountry` stocke le code langue-pays pour indiquer le pays à utiliser.

![Définition de la langue](assets/msm-language-manager.png)

Pour modifier les langues :

1. Ouvrez CRXDE Lite.
1. Sélectionnez le dossier `/apps` et cliquez sur **Créer**, puis sur **Créer un dossier.**

1. Nommez le nouveau dossier `wcm`.

1. Répétez l’étape précédente pour créer l’arborescence de dossiers `/apps/wcm/core`. Créez un nœud de type `sling:Folder` dans `core` appelé `resources`.

1. Cliquez avec le bouton droit sur le nœud `/libs/wcm/core/resources/languages` et cliquez sur **Copier**.
1. Cliquez avec le bouton droit sur le dossier `/apps/wcm/core/resources` et cliquez sur **Coller**. Modifiez les nœuds enfants selon les besoins.
1. Cliquez sur **Enregistrer tout**.
1. Cliquez sur **Outils**, **Opérations** puis **Console Web**. Dans cette console, cliquez sur **OSGi**, puis **Configuration**.
1. Recherchez et cliquez sur le **Gestionnaire de langues de gestion de contenu Web Day CQ** et redéfinissez la valeur de **Liste de langues** sur `/apps/wcm/core/resources/languages`, puis cliquez sur **Enregistrer**.

   ![Gestionnaire de langues de la gestion du contenu web Day CQ](assets/msm-language-manager.png)

## Configuration des verrous MSM sur les propriétés de page {#configuring-msm-locks-on-page-properties}

Lors de la création d’une propriété de page personnalisée, vous devrez peut-être déterminer si la nouvelle propriété doit être éligible au déploiement sur des Live Copies.

Par exemple, si deux nouvelles propriétés de page sont ajoutées :

* Contact e-mail :

   * Cette propriété ne doit pas être déployée, car elle sera différente dans chaque pays (ou marque, etc.).

* Style visuel clé :

   * Cette propriété doit être déployée, car elle est (généralement) commune à tous les pays (ou marques, etc.).

Assurez-vous ensuite que les propriétés suivantes sont correctement configurées :

* Contact e-mail :

   * Est exclu des propriétés déployées.
   * Voir [Configuration de la synchronisation des Live Copies](/help/sites-cloud/administering/msm/live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) pour plus d’informations.

* Style visuel clé :

   * Assurez-vous que vous n’êtes pas autorisé à modifier cette propriété sauf si l’héritage est annulé.
   * Assurez-vous également que vous pouvez ensuite rétablir l’héritage. Pour ce faire, cliquez sur les maillons chain/broken-chain qui basculent pour indiquer le statut de la connexion.

La propriété de boîte de dialogue détermine si une propriété de page est soumise au déploiement, et donc à l’annulation ou au rétablissement de l’héritage lors de la modification :

* `cq-msm-lockable`

   * Le symbole de chaînage est alors créé dans la boîte de dialogue.
   * Cela ne permet d’effectuer des modifications que si l’héritage est annulé (le chaînage est rompu).
   * Cela s’applique uniquement au premier niveau enfant de la ressource
      * **Type** : `String`
      * **Valeur** : contient le nom de la propriété considérée et est comparable à la valeur de la propriété `name`
         * Par exemple, consultez
           `/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title`

Lorsque `cq-msm-lockable` a été défini, la rupture/le verrouillage de la chaîne interagit avec le MSM de la façon suivante :

* Si la valeur de `cq-msm-lockable` est :

   * **Relative** (par exemple, `myProperty` ou `./myProperty`)

      * La rupture de la chaîne ajoute et supprime la propriété de `cq:propertyInheritanceCancelled`.

   * **Absolue** (par exemple, `/image`)

      * La rupture de la chaîne annule l’héritage en ajoutant le mixin `cq:LiveSyncCancelled` à `./image` et en définissant `cq:isCancelledForChildren` sur `true`.

      * La fermeture de la chaîne rétablit l’héritage.

>[!NOTE]
>
>`cq-msm-lockable` s’applique au premier niveau enfant de la ressource à éditer et il n’est pas fonctionnel à un niveau plus profond, que la valeur soit définie comme absolue ou relative.

>[!NOTE]
>
>Lorsque vous réactivez l’héritage, la propriété de page de la Live Copy n’est pas automatiquement synchronisée avec la propriété source. Vous pouvez demander manuellement une synchronisation si nécessaire.
