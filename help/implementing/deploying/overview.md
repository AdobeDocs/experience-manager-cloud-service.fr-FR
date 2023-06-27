---
title: Déploiement sur AEM as a Cloud Service
description: Déploiement sur AEM as a Cloud Service
feature: Deploying
exl-id: 7fafd417-a53f-4909-8fa4-07bdb421484e
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '3462'
ht-degree: 40%

---

# Déploiement sur AEM as a Cloud Service {#deploying-to-aem-as-a-cloud-service}

## Présentation {#introduction}

Les principes fondamentaux du développement de code sont similaires dans AEM as a Cloud Service par rapport aux solutions AEM On Premise et Managed Services. Les développeurs écrivent du code et le testent localement, qui est ensuite envoyé vers des environnements distants sur AEM as a Cloud Service. Cloud Manager, qui était un outil de diffusion de contenu facultatif pour Managed Services, est requis. Cet outil de diffusion est désormais le seul mécanisme de déploiement du code pour AEM les environnements de développement, d’évaluation et de production as a Cloud Service. Pour une validation et un débogage rapides des fonctionnalités avant de déployer ces environnements mentionnés précédemment, le code peut être synchronisé d’un environnement local à un [Environnement de développement rapide](/help/implementing/developing/introduction/rapid-development-environments.md).

La mise à jour de la [version d’AEM](/help/implementing/deploying/aem-version-updates.md) est toujours un événement de déploiement distinct de la publication de [code personnalisé](#customer-releases). Visionné d’une autre manière, les versions de code personnalisé doivent être testées par rapport à la version AEM en production, car c’est ce qu’il est déployé en haut de l’écran. AEM les mises à jour de version qui surviennent par la suite, qui sont fréquentes et sont automatiquement appliquées. Elles sont conçues pour être rétrocompatibles avec le code client déjà déployé.

Le reste de ce document décrit la manière dont les développeurs doivent adapter leurs pratiques pour qu’elles fonctionnent avec les mises à jour de version d’AEM as a Cloud Service et les mises à jour client.

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).
-->

## Versions client {#customer-releases}

### Codage par rapport à la version appropriée d’AEM {#coding-against-the-right-aem-version}

Pour les solutions AEM précédentes, la version la plus récente d’AEM était rarement modifiée (environ une fois par an avec des Service Packs trimestriels) et les clients mettaient à jour les instances de production au moment voulu vers le quickstart le plus récent, en référençant le fichier Jar de l’API. Toutefois, les applications sur AEM as a Cloud Service sont automatiquement mises à jour vers la dernière version d’AEM plus souvent, de sorte que le code personnalisé pour les versions internes doit être créé par rapport à la dernière version d’AEM.

Comme pour les versions d’AEM non cloud existantes, un développement local hors ligne basé sur un démarrage rapide spécifique est pris en charge et devrait être l’outil de choix pour le débogage généralement.

>[!NOTE]
>Il existe des différences opérationnelles subtiles entre le comportement de l’application sur un ordinateur local et sur Adobe Cloud. Ces différences architecturales doivent être respectées lors du développement local et peuvent entraîner un comportement différent lors du déploiement sur l’infrastructure cloud. En raison de ces différences, il est important d’effectuer des tests exhaustifs sur les environnements de développement et d’évaluation avant de déployer un nouveau code personnalisé en production.

Pour développer du code personnalisé pour une version interne, la version appropriée de la variable [AEM SDK as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) doit être téléchargé et installé. Pour plus d’informations sur l’utilisation des outils Dispatcher d’AEM as a Cloud Service, voir [cette page](/help/implementing/dispatcher/disp-overview.md).

La vidéo suivante présente un aperçu général du déploiement du code sur AEM as a Cloud Service :

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html). 
-->

## Déploiement de modules de contenu au moyen de Cloud Manager et de Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Déploiements par le biais de Cloud Manager {#deployments-via-cloud-manager}

<!-- Alexandru: temporarily commenting this out, until I get some clarification from Brian 

![image](https://git.corp.adobe.com/storage/user/9001/files/e91b880e-226c-4d5a-93e0-ae5c3d6685c8) -->

Les clients déploient le code personnalisé dans les environnements cloud via Cloud Manager. Cloud Manager transforme des modules de contenu assemblés localement en artefact conforme au modèle de fonctionnalité Sling, qui est la manière dont une application sur AEM as a Cloud Service est décrite lors de l’exécution dans un environnement cloud. Par conséquent, lors de l’examen des modules dans [Gestionnaire de modules](/help/implementing/developing/tools/package-manager.md) dans les environnements cloud, le nom inclut &quot;cp2fm&quot; et toutes les métadonnées sont supprimées pour les modules transformés. Ils ne peuvent pas être interactifs, ce qui signifie qu’ils ne peuvent pas être téléchargés, répliqués, ni ouverts. Vous trouverez [ici](https://github.com/apache/sling-org-apache-sling-feature-cpconverter) une documentation détaillée sur le convertisseur.

Les modules de contenu écrits pour les applications sur AEM as a Cloud Service doivent avoir une séparation nette entre le contenu non modifiable et le contenu modifiable. De plus, Cloud Manager installe uniquement le contenu modifiable, et génère également un message du type suivant :

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

Le reste de cette section décrit la composition et les implications des modules modifiables et non modifiables.

### Packages de contenu non modifiables {#immutabe-content-packages}

L’ensemble du contenu et du code conservés dans le référentiel non modifiable doit être archivé dans git et déployé via Cloud Manager. En d’autres termes, contrairement aux solutions AEM actuelles, le code n’est jamais déployé directement sur une instance AEM en cours d’exécution. Ce workflow garantit que le code exécuté pour une version donnée dans n’importe quel environnement cloud est identique, ce qui élimine le risque de variation non intentionnelle du code en production. Par exemple, la configuration OSGI doit être validée dans le contrôle de code source plutôt que gérée au moment de l’exécution au moyen du gestionnaire de configuration de la console web AEM.

Les modifications d’application dues au modèle de déploiement étant activées par un commutateur, elles ne peuvent pas dépendre des modifications du référentiel modifiable, à l’exception des utilisateurs du service, de leurs listes de contrôle d’accès, de leurs types de noeuds et des modifications de la définition d’index.

Pour les clients qui disposent de bases de code, il est essentiel de passer par l’exercice de restructuration du référentiel décrit dans la documentation d’AEM en vue de s’assurer que le contenu qui se trouvait auparavant sous /etc est déplacé vers le bon emplacement.

Certaines restrictions supplémentaires s’appliquent à ces packages de code, les [hooks d’installation](https://jackrabbit.apache.org/filevault/installhooks.html) ne sont par exemple pas pris en charge.

## Configuration OSGI {#osgi-configuration}

Comme mentionné ci-dessus, la configuration OSGI doit être validée dans le contrôle de code source plutôt que par le biais de la console web. Pour ce faire, les techniques suivantes sont disponibles :

* Apporter les modifications nécessaires à l’environnement AEM local du développeur avec le gestionnaire de configuration de la console web AEM, puis exporter les résultats vers le projet AEM sur le système de fichiers local
* Créer manuellement la configuration OSGI dans le projet AEM sur le système de fichiers local et faire référence au gestionnaire de configuration de la console AEM pour les noms de propriétés

Pour plus d’informations sur la configuration d’OSGI, voir la section [Configuration d’OSGi pour AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).

## Contenu modifiable {#mutable-content}

Parfois, il peut s’avérer utile de préparer les modifications de contenu dans le contrôle de code source afin qu’il puisse être déployé par Cloud Manager chaque fois qu’un environnement a été mis à jour. Par exemple, il peut être raisonnable d’amorcer certaines structures de dossiers racine. Vous pouvez également aligner les modifications apportées aux modèles modifiables pour activer les composants de stratégies qui ont été mis à jour par le déploiement de l’application.

Il existe deux stratégies pour décrire le contenu déployé par Cloud Manager sur le référentiel modifiable, les modules de contenu modifiable et `repoinit` des instructions.

### Packages de contenu modifiables {#mutable-content-packages}

Les contenus tels que les hiérarchies de chemins de dossier, les utilisateurs du service et les contrôles d’accès (ACL) sont généralement validés dans un projet AEM Maven basé sur l’archétype. Les techniques incluent l’exportation depuis AEM ou l’écriture directe au format XML. Au cours du processus de création et de déploiement, Cloud Manager crée le package de contenu modifiable résultant. Le contenu modifiable est installé trois fois différentes lors de la phase de déploiement dans le pipeline :

Avant le démarrage de la nouvelle version de l’application :

* Définitions d’index (ajout, modification, suppression)

Au démarrage d’une nouvelle version de l’application, mais avant le basculement :

* Utilisateurs du service (ajout)
* Liste de contrôle d’accès des utilisateurs du service (ajout)
* Types de nœuds (ajout)

Après le basculement vers la nouvelle version de l’application :

* Tout autre contenu pouvant être défini par le biais de coffre Jackrabbit. Par exemple :
   * Dossiers (ajout, modification, suppression)
   * Modèles modifiables (ajout, modification, suppression)
   * Configuration tenant compte du contexte (tout sous `/conf`) (ajout, modification, suppression)
   * Scripts (les packages peuvent déclencher des hooks d’installation à diverses étapes du processus d’installation de package : Voir [Documentation Jackrabbit filevault](https://jackrabbit.apache.org/filevault/installhooks.html) à propos des hooks d’installation. AEM CS utilise actuellement la version 3.4.0 de Filevault, qui limite les hooks d’installation aux utilisateurs administrateurs, aux utilisateurs système et aux membres du groupe administrateurs).

Il est possible de limiter l’installation de contenu modifiable à la création ou à la publication en incorporant des packages dans un dossier install.author ou install.publish sous `/apps`. Une restructuration pour refléter cette séparation a été réalisée dans AEM 6.5 et les détails relatifs à la restructuration de projet recommandée sont disponibles dans la [documentation d’AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html?lang=fr).

>[!NOTE]
>Les packages de contenu sont déployés sur tous les types d’environnements (développement, évaluation et production). Il n’est pas possible de limiter le déploiement à un environnement spécifique. Cette limitation est en place pour garantir l’option d’une série de tests d’exécution automatisée. Le contenu spécifique à un environnement nécessite une installation manuelle [Gestionnaire de modules.](/help/implementing/developing/tools/package-manager.md)

En outre, il n’existe aucun mécanisme permettant de restaurer les modifications du module de contenu modifiable après leur application. Si les clients détectent un problème, ils peuvent choisir de le résoudre dans la prochaine version de leur code ou, en dernier recours, restaurer l’ensemble du système à un moment donné avant le déploiement.

Les modules tiers inclus doivent être validés comme étant compatibles AEM as a Cloud Service, sinon leur inclusion entraîne un échec de déploiement.

Comme mentionné ci-dessus, les clients disposant de bases de code doivent se conformer à l’exercice de restructuration du référentiel requis par les modifications du référentiel 6.5 décrites dans la section [Documentation d’AEM 6.5.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html?lang=fr)

## Repoinit {#repoinit}

Dans les cas suivants, il est préférable d’utiliser l’approche du codage manuel des instructions `repoinit` de création de contenu explicite dans les configurations OSGI d’usine :

* Création/suppression/désactivation d’utilisateurs du service
* Création/suppression de groupes
* Création/suppression d’utilisateurs
* Ajout de listes de contrôle d’accès

  >[!NOTE]
  >
  >La définition des listes de contrôle d’accès requiert que les structures de nœud soient déjà présentes. Par conséquent, il peut être nécessaire de créer au préalable des instructions de chemin.

* Ajout d’un chemin (par exemple, pour les structures de dossiers racine)
* Ajout de CND (définitions de types de nœuds)

Il est préférable d’opter pour repoinit pour ces scénarios de modification de contenu pris en charge en raison des avantages suivants :

* `Repoinit` crée des ressources au démarrage si bien que la logique peut prendre l’existence de ces ressources pour acquise. Dans l’approche du package de contenu modifiable, les ressources sont créées après le démarrage. Le code de l’application reposant sur ces ressources peut donc échouer.
* `Repoinit` est un jeu d’instructions relativement sûr, car vous contrôlez explicitement l’action à entreprendre. En outre, les seules opérations prises en charge sont les ajouts, à l’exception de quelques cas liés à la sécurité qui permettent de supprimer des utilisateurs, des utilisateurs de service et des groupes. En revanche, la suppression d’un élément dans l’approche du module de contenu modifiable est explicite. lorsque vous définissez un filtre, tout élément couvert par un filtre est supprimé. Néanmoins, il faut être prudent car, pour tout contenu, il existe des scénarios où la présence d’un nouveau contenu peut modifier le comportement de l’application.
* `Repoinit` effectue des opérations atomiques et rapides. Cependant, les packages de contenu modifiable peuvent fortement dépendre des performances selon les structures couvertes par un filtre. Même si vous mettez à jour un nœud unique, un instantané d’une grande arborescence peut être créé.
* Il est possible de valider `repoinit` sur un environnement de développement local au moment de l’exécution, car elles sont exécutées lorsque la configuration OSGi est enregistrée.
* `Repoinit` sont atomiques et explicites et sont ignorées si l’état correspond déjà.

Lorsque Cloud Manager déploie l’application, il exécute ces instructions, indépendamment de l’installation des packages de contenu.

Pour créer `repoinit` , procédez comme suit :

1. Ajoutez une configuration OSGi pour le PID d’usine `org.apache.sling.jcr.repoinit.RepositoryInitializer` dans un dossier de configuration du projet. Utilisez un nom explicite pour la configuration, tel que **org.apache.sling.jcr.repoinit.RepositoryInitializer~initstructure**.
1. Ajouter `repoinit` à la propriété de script de la configuration. La syntaxe et les options sont décrites dans la [documentation Sling](https://sling.apache.org/documentation/bundles/repository-initialization.html). Il doit y avoir une création explicite d’un dossier parent avant leurs dossiers enfants. Par exemple, une création explicite de `/content` avant `/content/myfolder`, et avant `/content/myfolder/mysubfolder`. Pour que les listes de contrôle d’accès soient définies sur des structures de bas niveau, il est recommandé de les définir à un niveau supérieur et de travailler avec une `rep:glob` restriction. Par exemple, `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. Validez l’environnement de développement local au moment de l’exécution.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>Pour les listes de contrôle d’accès définies pour les noeuds situés sous `/apps` ou `/libs` la valeur `repoinit`, l’exécution démarre sur un référentiel vide. Les modules sont installés après `repoinit` ainsi, les instructions ne peuvent pas s’appuyer sur un élément défini dans les packages, mais doivent définir les conditions préalables comme les structures parentes sous-jacentes.

>[!TIP]
>
>Pour les listes de contrôle d’accès, la création de structures profondes peut être laborieuse. Par conséquent, il est plus raisonnable de définir une liste de contrôle d’accès à un niveau supérieur et de limiter les endroits où elle est censée agir au moyen d’une `rep:glob` restriction.

Plus d’informations sur `repoinit` se trouve dans la variable [Documentation Sling](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### Utilisation ponctuelle du gestionnaire de packages pour les packages de contenu modifiables {#package-manager-oneoffs-for-mutable-content-packages}

>[!CONTEXTUALHELP]
>id="aemcloud_packagemanager"
>title="Gestionnaire de modules – Migration de packages de contenu modifiable"
>abstract="Explorez l’utilisation de Package Manager pour les cas d’utilisation où un module de contenu doit être installé &quot;un seul fois&quot;. L’installation comprend l’importation de contenu spécifique de la production vers l’évaluation pour déboguer un problème de production, le transfert de petits modules de contenu de l’environnement on-premise vers les environnements AEM Cloud, etc."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en" text="Outil de transfert de contenu"

Il existe des cas d’utilisation où un package de contenu doit être installé de façon ponctuelle. Par exemple, l’importation de contenu spécifique de la production vers l’évaluation pour déboguer un problème de production. Pour ces scénarios, [Gestionnaire de modules](/help/implementing/developing/tools/package-manager.md) peut être utilisé dans des environnements sur AEM as a Cloud Service.

Le gestionnaire de packages étant un concept d’exécution, il n’est pas possible d’installer du contenu ni du code dans le référentiel non modifiable. Par conséquent, ces packages doivent être constitués uniquement de contenu modifiable (principalement `/content` ou `/conf`). Si le module de contenu comprend du contenu mixte (modifiable et non modifiable), seul le contenu modifiable est installé.

>[!IMPORTANT]
>
>L’interface utilisateur du gestionnaire de modules peut renvoyer une **undefined** message d’erreur si l’installation d’un package dure plus de dix minutes.
>
>Cette période n’est pas due à une erreur lors de l’installation, mais à un délai d’attente du Cloud Service pour toutes les requêtes.
>
>N’essayez pas d’effectuer une nouvelle installation si une telle erreur s’affiche. L’installation se déroule correctement en arrière-plan. Si vous redémarrez l’installation, certains conflits peuvent être introduits par plusieurs processus d’importation simultanés.

Tous les modules de contenu installés par le biais de Cloud Manager (modifiable et non modifiable) apparaissent à l’état figé dans l’interface utilisateur d’AEM Gestionnaire de modules. Ces modules ne peuvent pas être réinstallés, recréés ou même téléchargés. Ils sont répertoriés avec une **&quot;cp2fm&quot;** , indiquant que leur installation a été gérée par Cloud Manager.

### Inclusion de modules tiers {#including-third-party}

Il est courant pour les clients d’inclure des modules prédéfinis provenant de sources tierces, telles que des fournisseurs de logiciels comme les partenaires de traduction d’Adobe. Il est recommandé d’héberger ces packages au sein d’un référentiel distant et de les référencer dans le `pom.xml`. Cette méthode est possible pour les référentiels publics et également pour les référentiels privés avec protection par mot de passe, comme décrit dans la section [Référentiels Maven protégés par mot de passe](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories).

Si le stockage du package dans un référentiel distant n’est pas possible, les clients peuvent le placer dans un référentiel Maven local basé sur un système de fichiers, qui est validé dans SCM dans le cadre du projet. Il est référencé par tout ce qui en dépend. Le référentiel est déclaré dans le modèle pom du projet, comme illustré ci-dessous :


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Les modules tiers inclus doivent respecter les directives de codage et de conditionnement as a Cloud Service décrites dans cet article, sans quoi leur inclusion entraîne un échec de déploiement.

Maven suivant `POM.xml` Le fragment de code indique comment les modules tiers peuvent être incorporés dans le module &quot;Conteneur&quot; du projet, généralement appelé **&#39;all&#39;**, par l’intermédiaire de la fonction **filevault-package-maven-plugin** Configuration du module externe Maven.

```
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <embeddeds>

          ...

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

## Fonctionnement des déploiements en continu {#how-rolling-deployments-work}

À l’instar des mises à jour AEM, les versions des clients sont déployées à l’aide d’une stratégie de déploiement en continu afin d’éliminer les temps d’arrêt de la grappe d’auteurs dans les bonnes circonstances. La séquence générale des événements est décrite ci-dessous, où les noeuds comportant à la fois l’ancienne et la nouvelle versions du code client exécutent la même version du code AEM.

* Les noeuds avec l’ancienne version sont principaux et un candidat de version pour la nouvelle version est créé et devient disponible.
* S’il existe des définitions d’index nouvelles ou mises à jour, les index correspondants sont traités. Les noeuds avec l’ancienne version utilisent toujours les anciens index, tandis que les noeuds avec la nouvelle version utilisent toujours les nouveaux index.
* Les noeuds avec la nouvelle version démarrent, tandis que les anciennes versions diffusent toujours du trafic.
* Les noeuds avec l’ancienne version sont en cours d’exécution et continuent de servir pendant que les noeuds avec la nouvelle version sont vérifiés pour vérifier leur état de préparation au moyen de contrôles de l’intégrité.
* Les noeuds avec la nouvelle version qui sont prêts, acceptent le trafic et remplacent les noeuds par l’ancienne version, qui sont supprimés.
* Au fil du temps, les noeuds avec l’ancienne version sont remplacés par des noeuds avec la nouvelle version jusqu’à ce que seuls les noeuds avec de nouvelles versions restent, ce qui permet d’effectuer le déploiement.
* Tout contenu modifiable nouveau ou modifié est ensuite déployé.

## Index {#indexes}

Les index nouveaux ou modifiés provoquent une étape d’indexation ou de réindexation supplémentaire avant que la nouvelle version ne puisse prendre en charge le trafic. Vous trouverez dans [cet article](/help/operations/indexing.md) des informations détaillées sur la gestion des index dans AEM as a Cloud Service. Vous pouvez vérifier l’état d’indexation des pages de création sur Cloud Manager et recevoir une notification lorsque la nouvelle version est prête à recevoir le trafic.

>[!NOTE]
>
>Le temps nécessaire à un déploiement en continu varie en fonction de la taille de l’index. Cela est dû au fait que la nouvelle version ne peut pas accepter le trafic tant que le nouvel index n’a pas été généré.

Actuellement, AEM as a Cloud Service ne fonctionne pas avec les outils de gestion des index tels que ACS Commons Verify Oak Index.

## Réplication {#replication}

Le mécanisme de publication est rétrocompatible avec [API Java™ de réplication d’AEM](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=fr).

Pour développer et tester avec la réplication avec le démarrage rapide AEM cloud, les fonctionnalités classiques de réplication doivent être utilisées avec une configuration Auteur/Publication. Si le point d’entrée de l’interface utilisateur sur l’auteur AEM est supprimé pour le cloud, les utilisateurs accèdent à `http://localhost:4502/etc/replication` pour la configuration.

## Code rétrocompatible pour les déploiements en continu {#backwards-compatible-code-for-rolling-deployments}

Comme indiqué ci-dessus, la stratégie de déploiement en continu d’AEM as a Cloud Service implique que les anciennes et nouvelles versions peuvent être opérationnelles en même temps. Par conséquent, soyez prudent par rapport aux modifications de code qui ne sont pas rétrocompatibles avec l’ancienne version d’AEM qui est encore utilisée.

En outre, l’ancienne version doit être testée pour vérifier sa compatibilité avec toute nouvelle structure de contenu modifiable appliquée par la nouvelle version en cas de restauration, car le contenu modifiable n’est pas supprimé.

### Utilisateurs du service et modifications des listes de contrôle d’accès {#service-users-and-acl-changes}

La modification des utilisateurs du service, ou des listes de contrôle d’accès qui accèdent au contenu ou au code, peut entraîner des erreurs dans les anciennes versions AEM, ce qui entraîne l’accès à ce contenu ou à ce code avec des utilisateurs du service obsolètes. Pour remédier à ce problème, il est recommandé d’effectuer des modifications réparties sur au moins deux versions, la première version jouant le rôle de lien avant de procéder au nettoyage dans la version suivante.

### Modifications des index {#index-changes}

Si des modifications sont apportées aux index, il est important que la nouvelle version continue à utiliser ses index jusqu’à ce qu’il soit arrêté, tandis que l’ancienne version utilise son propre jeu d’index modifié. Le développeur doit suivre les techniques de gestion des index décrites [dans cet article](/help/operations/indexing.md).

### Codage conservateur pour les restaurations {#conservative-coding-for-rollbacks}

Si un échec est signalé ou détecté après le déploiement, il est possible qu’une restauration de l’ancienne version soit requise. Assurez-vous que le nouveau code est compatible avec toutes les nouvelles structures créées par cette nouvelle version puisque les nouvelles structures (tout contenu modifiable) ne sont pas restaurées. Si l’ancien code n’est pas compatible, des correctifs doivent être appliqués dans les versions ultérieures du client.

## Environnements de développement rapide (RDE) {#rde}

[Environnements de développement rapide](/help/implementing/developing/introduction/rapid-development-environments.md) (ou les RDE pour abréger) permettent aux développeurs de déployer et de passer rapidement en revue les modifications, ce qui réduit le temps nécessaire au test des fonctionnalités qui ont déjà fait leurs preuves dans un environnement de développement local.

Contrairement aux environnements de développement standard qui déploient le code par le biais du pipeline Cloud Manager, les développeurs utilisent des outils de ligne de commande pour synchroniser le code d’un environnement de développement local avec l’éditeur de texte enrichi. Une fois les modifications testées dans un RDE, déployez-les dans un environnement de développement cloud classique via le pipeline Cloud Manager, qui place le code par le biais des points de contrôle qualité appropriés.

## Modes d’exécution {#runmodes}

Dans les solutions AEM existantes, les clients et les clientes peuvent exécuter des instances avec des modes d’exécution arbitraires et appliquer la configuration OSGI ou installer des lots OSGI sur ces instances. Les modes d’exécution définis incluent généralement le *service* (création et publication) et l’environnement (RDE, développement, évaluation et production).

AEM as a Cloud Service, en revanche, est plus précis sur les modes d’exécution disponibles et sur la manière dont les bundles OSGI et la configuration OSGI peuvent être mappés sur ces modes :

* Les modes d’exécution de configuration OSGI doivent faire référence à RDE, développement, évaluation, production pour l’environnement ou création, publication pour le service. Une combinaison de `<service>.<environment_type>` est pris en charge, alors que ces environnements doivent être utilisés dans cet ordre particulier (par exemple `author.dev` ou `publish.prod`). Les jetons OSGI doivent être référencés directement à partir du code plutôt que d’utiliser la variable `getRunModes` qui n’inclut plus la méthode `environment_type` au moment de l’exécution. Pour plus d’informations, voir [Configuration d’OSGi pour AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).
* Les modes d’exécution des lots OSGI sont limités au service (auteur et publication). Les lots OSGI par mode d’exécution doivent être installés dans le package de contenu sous `install.author` ou `install.publish`.

AEM as a Cloud Service ne permet pas d’utiliser des modes d’exécution pour installer du contenu destiné à des environnements ou des services spécifiques. Si un environnement de développement doit être ensemencé avec des données ou un HTML qui ne se trouve pas dans les environnements d’évaluation ou de production, le gestionnaire de modules peut être utilisé.

Les configurations de mode d’exécution prises en charge sont les suivantes :

* **config** (*Par défaut, s’applique à tous les services AEM*)
* **config.author** (*s’applique à tous les services Auteur AEM*)
* **config.author.dev** (*s’applique au service Auteur de développement AEM*)
* **config.author.rde** (*S’applique au service de création RDE d’AEM*)
* **config.author.stage** (*s’applique au service Auteur d’évaluation AEM*)
* **config.author.prod** (*s’applique au service Auteur de production AEM*)
* **config.publish** (*s’applique au service Publication AEM*)
* **config.publish.dev** (*s’applique au service de publication de développement AEM*)
* **config.publish.rde** (*S’applique au service de publication RDE d’AEM*)
* **config.publish.stage** (*s’applique au service Publication d’évaluation AEM*)
* **config.publish.prod** (*s’applique au service Publication de production AEM*)
* **config.dev** (*s’applique aux services de développement AEM*)
* **config.rde** (*S’applique aux services RDE*)
* **config.stage** (*s’applique aux services d’évaluation AEM*)
* **config.prod** (*s’applique aux services de production AEM*)

La configuration OSGI qui possède le plus de modes d’exécution correspondants est utilisée.

Lors d’un développement local, un paramètre de démarrage en mode d’exécution, `-r`, est utilisé pour spécifier la configuration OSGI du mode d’exécution.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Configuration des tâches de maintenance dans le contrôle de code source {#maintenance-tasks-configuration-in-source-control}

Les configurations des tâches de maintenance doivent être conservées dans le contrôle de code source, car la variable **Outils > Opérations** n’est pas disponible dans les environnements cloud. Cet avantage permet de s’assurer que les modifications sont intentionnellement conservées plutôt que appliquées de manière réactive et oubliées. Voir [Article sur les tâches de maintenance](/help/operations/maintenance.md) pour plus d’informations.
