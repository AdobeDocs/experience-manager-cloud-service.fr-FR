---
title: Déploiement sur AEM en tant que service Cloud
description: 'Déploiement sur AEM en tant que service Cloud '
translation-type: tm+mt
source-git-commit: de23de0b79e6b897a69bd18035d2e7fcd07104c5

---


# Déploiement sur AEM en tant que service Cloud {#deploying-to-aem-as-a-cloud-service}

## Présentation {#introduction}

Les fondamentaux du développement du code sont similaires dans AEM en tant que service Cloud par rapport aux solutions AEM On Premise et Managed Services. Les développeurs écrivent du code et le testent localement, qui est ensuite envoyé vers AEM distant en tant qu’environnements de service Cloud. Cloud Manager, qui était un outil de diffusion de contenu facultatif pour les services gérés, est requis. Il s’agit désormais du seul mécanisme permettant de déployer du code vers AEM en tant qu’environnements de service Cloud.

La mise à jour de la version AEM est toujours un événement de déploiement distinct de la publication de code personnalisé. D’une autre manière, les versions de code personnalisé doivent être testées par rapport à la version d’AEM en cours de production, car c’est ce dont elles seront déployées par-dessus. Les mises à jour de version d’AEM qui se produisent après cette date, qui seront fréquentes par rapport aux services gérés aujourd’hui, sont automatiquement appliquées. Ils sont censés être rétrocompatibles avec le code client déjà déployé.

Le reste de ce document décrit la manière dont les développeurs doivent adapter leurs pratiques afin qu’ils travaillent avec AEM en tant que mises à jour de version du service Cloud et mises à jour client.

>[!NOTE]
>Il est recommandé aux clients disposant de bases de code existantes de passer par l’exercice de restructuration du référentiel décrit dans la documentation [](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html)AEM.


## Mises à jour de la version AEM {#version-updates}

Il est essentiel de comprendre qu’AEM sera fréquemment mis à jour, potentiellement aussi souvent qu’une fois par jour, et qu’il se concentrera sur les correctifs et les améliorations des performances. La mise à jour se fera de manière transparente et sans provoquer d’interruption de service. La mise à jour est conçue pour être rétrocompatible, ce qui signifie que vous ne devez pas modifier le code personnalisé. En fait, les mises à jour AEM sont des événements indépendants des déploiements de code client. La mise à jour d’AEM est déployée en plus de votre dernière publication de code réussie, ce qui implique que les modifications engagées depuis la dernière publication vers la production ne seront pas déployées.

>[!NOTE]
>
> Si vous avez poussé le code personnalisé vers l’évaluation, puis l’avez rejeté, la prochaine mise à jour d’AEM supprimera ces modifications afin de refléter la balise git de la dernière version de production du client réussie.

En fréquence régulière, une version des fonctionnalités sera publiée, en mettant l’accent sur les ajouts et les améliorations qui auront un impact plus important sur l’expérience des utilisateurs que sur les versions quotidiennes. Une version de fonctionnalité est déclenchée non pas par le déploiement d’un jeu de modifications important, mais par le retournement d’une bascule de version, activant le code qui s’est accumulé au cours des jours ou des semaines par le biais des mises à jour quotidiennes.

Les contrôles d’intégrité servent à surveiller l’état de l’application. Si ces vérifications échouent lors d’une mise à jour d’AEM en tant que service cloud, la version ne sera pas publiée pour cet environnement et Adobe examinera pourquoi la mise à jour a provoqué ce comportement inattendu.

### Magasin de noeuds composites {#composite-node-store}

Comme nous l’avons mentionné plus haut, les mises à jour n’entraînent dans la plupart des cas aucune interruption, y compris pour l’auteur, qui est un groupe de noeuds. Les mises à jour roulantes sont possibles en raison de la fonctionnalité &quot;magasin de noeuds composites&quot; dans Oak. Cette fonctionnalité permet à AEM de référencer plusieurs référentiels simultanément. Dans un déploiement variable, la nouvelle version d’AEM verte contient son propre `/libs` (référentiel immuable basé sur TarMK), distinct de l’ancienne version d’AEM Bleue, bien que les deux référencent un référentiel mutable basé sur DocumentMK partagé qui contient des zones comme `/content`, `/conf`, `/etc` et d’autres. Comme le bleu et le vert ont leurs propres versions de `/libs`, ils peuvent tous deux être actifs pendant la mise à jour roulante, prenant tous deux le trafic jusqu&#39;à ce que le bleu soit complètement remplacé par le vert.

## Versions du client {#customer-releases}

### Codage par rapport à la version AEM appropriée {#coding-against-the-right-aem-version}

Pour les solutions AEM précédentes, la version la plus récente d’AEM a rarement été modifiée (environ une fois par an avec des Service Packs trimestriels) et les clients mettaient à jour les instances de production pour qu’elles démarrent rapidement le plus tard à leur propre heure, en référençant le Jar API. Toutefois, les applications AEM en tant que service Cloud sont automatiquement mises à jour vers la dernière version d’AEM plus souvent, de sorte que le code personnalisé pour les versions internes doit être créé par rapport à ces nouvelles interfaces AEM.

Comme pour les versions existantes d’AEM hors cloud, un développement local hors ligne basé sur un démarrage rapide spécifique sera pris en charge et devrait être l’outil de choix pour le débogage dans la plupart des cas.

> [!REMARQUE}
>Il existe des différences opérationnelles subtiles entre le comportement de l’application sur un ordinateur local et celui d’Adobe Cloud. Ces différences architecturales doivent être respectées lors du développement local et peuvent entraîner un comportement différent lors du déploiement sur l’infrastructure de cloud. En raison de ces différences, il est important d’effectuer des tests exhaustifs sur les environnements de développement et d’évaluation avant de déployer un nouveau code personnalisé en production.

Vous trouverez ci-dessous le processus permettant aux développeurs d’accéder à la version appropriée des artefacts AEM, que nous appellerons AEM en tant que SDK de service cloud, nécessaire au développement du code personnalisé pour une version interne. Vous trouverez des informations sur le répartiteur [dans cette page](/help/implementing/dispatcher/overview.md).

## AEM en tant que SDK de service cloud {#aem-as-a-cloud-service-sdk}

Le SDK d’AEM as a Cloud Service est constitué des artefacts suivants :

* **Jar** de démarrage rapide - Le runtime AEM utilisé pour le développement local
* **Jar** d’API Java - Dépendance Java Jar/Maven qui expose toutes les API Java autorisées qui peuvent être utilisées pour le développement contre AEM en tant que service Cloud. Anciennement appelé Uberjar
* **Javadoc Jar** - Les javadocs du Jar de l’API Java
* **Outils** du répartiteur - Ensemble d&#39;outils utilisés pour le développement local contre le répartiteur. Artefacts distincts pour les fenêtres et les uniformes

En outre, certains clients qui ont déjà été déployés avec AEM 6.5 ou des versions antérieures utiliseront les artefacts ci-dessous. Si la compilation locale ne fonctionne pas avec le fichier JAR Quickstart et que vous pensez qu’il est dû aux interfaces qui ont été supprimées d’AEM déployées en tant que service Cloud, contactez le service d’assistance clientèle pour déterminer si vous avez besoin d’accès. Cela nécessitera des modifications dans le serveur principal.

* **6.5 Jar** d’API Java obsolète : jeu d’interfaces supplémentaire qui ont été supprimées depuis AEM 6.5
* **6.5 Javadoc Jar** obsolète - les Javadocs pour l’ensemble supplémentaire de Javadoc

## Accès à AEM en tant que SDK de service Cloud {#accessing-the-aem-as-a-cloud-service-sdk}

* Vous pouvez consulter l’icône **À propos d’Adobe Experience Manager** de la console d’administration AEM pour connaître la version d’AEM que vous exécutez en production.
* Le fichier JAR de démarrage rapide et les outils du répartiteur peuvent être téléchargés dans un fichier zip depuis le portail [de distribution de](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/aemcloud.html)logiciels. Notez que l’accès aux listes de SDK est limité aux environnements avec les services gérés AEM ou AEM en tant qu’environnements de services Cloud.
* Les Jar de l&#39;API Java et Javadoc Jar peuvent être téléchargés via l&#39;outil Maven, soit en ligne de commande, soit avec votre IDE préféré.
* Les applications de projet maven doivent faire référence au package Jar API suivant. Cette dépendance doit également être référencée dans tous les modules complémentaires.

```
<dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>aem-sdk-api</artifactId>
  <version>2019.11.3006.20191108T223635Z-191201</version> 
  <scope>provided</scope>
</dependency>
```

> [!NOTE] L’entrée de version du SDK doit correspondre à la version d’AEM en tant que service Cloud. Vous pouvez voir quelle version vous utilisez en vous connectant à AEM, puis en accédant au point d’interrogation dans le coin supérieur droit de l’écran et en sélectionnant **[!UICONTROL A propos d’Adobe Experience Manager.]**

* La coordonnée distante du référentiel maven dans lequel le package est hébergé doit être incluse dans le fichier pom.

```
<repository>
    <id>adobe-aem-releases</id>
    <name>Adobe AEM Repository</name>
    <url>https://downloads.experiencecloud.adobe.com/content/maven/public</url>
    <releases>
        <enabled>true</enabled>
        <updatePolicy>never</updatePolicy>
    </releases>
    <snapshots>
        <enabled>false</enabled>
    </snapshots>
</repository>
```

## Actualisation d’un projet local avec une nouvelle version du SDK {#refreshing-a-local-prokect-with-a-new-skd-version}

Quand est-il recommandé d’actualiser le projet local avec un nouveau SDK ?

Il est *recommandé* de l’actualiser au moins après une version de maintenance mensuelle.

Il est *facultatif* de l’actualiser après une version de maintenance quotidienne. Les clients seront informés lorsque leur instance de production a été correctement mise à niveau vers une nouvelle version d’AEM. Pour les versions de maintenance quotidiennes, il n’est pas prévu que le nouveau SDK ait changé de manière significative, voire significative. Il est toutefois recommandé d’actualiser occasionnellement l’environnement de développement AEM local avec le dernier SDK, puis de recréer et de tester l’application personnalisée. La version de maintenance mensuelle comprend généralement des modifications ayant plus d’impact et les développeurs doivent donc immédiatement actualiser, recréer et tester.

Voici la procédure recommandée pour actualiser un environnement local :

1. Assurez-vous que tout contenu utile est soit engagé dans le projet dans le contrôle de code source, soit disponible dans un package de contenu modifiable pour une importation ultérieure.
1. Le contenu du test de développement local doit être stocké séparément afin qu’il ne soit pas déployé dans le cadre de la génération du pipeline de Cloud Manager. C&#39;est parce qu&#39;il ne doit être utilisé que pour le développement local.
1. Arrêter le démarrage rapide en cours d’exécution
1. Déplacer le `crx-quickstart` dossier vers un autre dossier pour assurer la sécurité
1. Notez la nouvelle version d’AEM, qui est indiquée dans Cloud Manager (elle sera utilisée pour identifier la nouvelle version de QuickStart Jar à télécharger plus loin).
1. Téléchargez le fichier JAR QuickStart dont la version correspond à la version d’AEM de production depuis le portail de distribution de logiciels.
1. Créez un nouveau dossier et insérez le nouveau fichier Jar QuickStart dans
1. Démarrez le nouveau QuickStart avec les modes d&#39;exécution de votre choix (renommer le fichier ou transmettre les modes d&#39;exécution via `-r`).
   * Assurez-vous qu&#39;il n&#39;y a aucun vestige de l&#39;ancien démarrage rapide dans le dossier.
1. Création de votre application AEM
1. Déployez votre application AEM vers AEM local via PackageManager.
1. Installez tous les packages de contenu modifiable nécessaires au test de l’environnement local via PackageManager.
1. Poursuivre le développement et déployer les modifications si nécessaire

Si du contenu doit être installé avec chaque nouvelle version de démarrage rapide d’AEM, incluez-le dans un package de contenu et dans le contrôle de code source du projet. Installez-le ensuite à chaque fois.

Il est recommandé de mettre à jour fréquemment le SDK (par exemple, toutes les deux semaines) et de supprimer quotidiennement l’état local complet pour ne pas dépendre accidentellement des données d’état dans l’application.

Si vous dépendez de CryptoSupport ([soit en configurant les informations d’identification de Cloudservices, soit du service de messagerie SMTP dans AEM, soit en utilisant l’API CryptoSupport dans votre application](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/crypto/CryptoSupport.html)), les propriétés chiffrées sont chiffrées par une clé qui est générée automatiquement au premier démarrage d’un environnement AEM. Bien que Cloudsetup s&#39;occupe de réutiliser automatiquement CryptoKey spécifique à l&#39;environnement, il est nécessaire d&#39;injecter la clé de chiffrement dans l&#39;environnement de développement local.

Par défaut, AEM est configuré pour stocker les données clés dans le dossier de données d’un dossier, mais pour faciliter leur réutilisation dans le développement, le processus AEM peut être initialisé au premier démarrage avec &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Les données de chiffrement seront alors générées à l’adresse &quot;`/etc/key`&quot;.

Pour pouvoir réutiliser des packages de contenu contenant les valeurs chiffrées, procédez comme suit :

* Lorsque vous démarrez le fichier locale quickstart.jar, veillez à ajouter le paramètre ci-dessous : &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Il est recommandé, mais facultatif, de toujours l’ajouter.
* La toute première fois que vous avez démarré une instance, créez un package contenant un filtre pour la racine &quot;`/etc/key`&quot;. Le secret sera alors réutilisé dans tous les environnements pour lesquels vous souhaitez qu’ils soient réutilisés.
* Exportez tout contenu modifiable contenant des secrets, ou recherchez les valeurs chiffrées `/crx/de` pour l’ajouter au package qui sera réutilisé lors des installations.
* Chaque fois que vous faites tourner une nouvelle instance (soit pour remplacer par une nouvelle version, soit comme plusieurs environnements de développement doivent partager les informations d’identification pour les tests), installez le package produit aux étapes 2 et 3 afin de pouvoir réutiliser le contenu sans avoir à reconfigurer manuellement. C&#39;est parce que maintenant la cryptoclé est en synchronisation.

## Déploiement de packs de contenu via Cloud Manager et Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Déploiements via Cloud Manager {#deployments-via-cloud-manager}

Les clients déploient du code personnalisé dans les environnements Cloud Manager. Il est à noter que Cloud Manager transforme des packages de contenu assemblés localement en artefact conforme au modèle de fonctionnalité Sling, qui décrit une application AEM en tant qu’application de service Cloud lors de l’exécution dans un environnement cloud. Par conséquent, lorsque vous examinez les packages de Package Manager dans les environnements Cloud, le nom inclut &quot;cp2fm&quot; et toutes les métadonnées des packages transformés sont supprimées. Ils ne peuvent pas être interactifs, ce qui signifie qu’ils ne peuvent pas être téléchargés, répliqués ou ouverts. Vous trouverez ici [](https://github.com/apache/sling-org-apache-sling-feature-cpconverter)une documentation détaillée sur le convertisseur.

Les packs de contenu écrits pour AEM en tant qu’applications de service Cloud doivent avoir une séparation nette entre le contenu immuable et mutant et Cloud Manager l’appliquera en échouant à la création, en générant un message du type :

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

Le reste de cette section décrit la composition et les implications des paquets immuables et mutables.

### Packages de contenu immuables {#immutabe-content-packages}

Tout le contenu et le code conservés dans le référentiel immuable doivent être archivés dans git et déployés via Cloud Manager. En d’autres termes, contrairement aux solutions AEM actuelles, le code n’est jamais déployé directement sur une instance AEM en cours d’exécution. Cela garantit que le code en cours d’exécution pour une version donnée dans n’importe quel environnement Cloud est identique, ce qui élimine le risque de variation non intentionnelle du code en production. Par exemple, la configuration OSGI doit être engagée dans le contrôle de code source plutôt que gérée au moment de l’exécution via le gestionnaire de configuration de la console Web AEM.

Les modifications d’application dues au modèle de déploiement Blue-Green étant activées par un commutateur, elles ne peuvent pas dépendre des modifications du référentiel mutable, à l’exception des utilisateurs du service, de leurs listes de contrôle d’accès, de leurs nodetypes et des modifications de la définition d’index.

Pour les clients qui disposent de bases de code existantes, il est essentiel de passer par l’exercice de restructuration du référentiel décrit dans la documentation AEM pour s’assurer que le contenu qui se trouvait auparavant sous /etc est déplacé vers le bon emplacement.

## Configuration OSGI {#osgi-configuration}

Comme mentionné ci-dessus, la configuration OSGI doit être engagée dans le contrôle de code source plutôt que par le biais de la console Web. Pour ce faire, les techniques suivantes sont disponibles :

* Apporter les modifications nécessaires à l’environnement AEM local du développeur avec le gestionnaire de configuration de la console Web AEM, puis exporter les résultats vers le projet AEM sur le système de fichiers local
* Création manuelle de la configuration OSGI dans le projet AEM sur le système de fichiers local, référence au gestionnaire de configuration de la console AEM pour les noms de propriété.

## Contenu muable {#mutable-content}

Dans certains cas, il peut s’avérer utile de préparer les changements de contenu dans le contrôle de source afin qu’il puisse être déployé par Cloud Manager chaque fois qu’un environnement a été mis à jour. Par exemple, il peut être raisonnable d’amorcer certaines structures de dossiers racine ou d’aligner les modifications dans les modèles modifiables afin d’activer les stratégies pour les composants qui ont été mis à jour par le déploiement de l’application.

Il existe deux stratégies pour décrire le contenu qui sera déployé par Cloud Manager vers le référentiel modifiable, les packages de contenu modifiable et les instructions repointit.

### Packages de contenu mutables {#mutable-content-packages}

Les contenus tels que les hiérarchies de chemins de dossier, les utilisateurs de service et les contrôles d’accès (ACL) sont généralement validés dans un projet AEM maven basé sur l’archétype. Les techniques incluent l’exportation depuis AEM ou l’écriture directe au format XML. Au cours du processus de création et de déploiement, Cloud Manager met en package le package de contenu modifiable résultant. Le contenu modifiable est installé à 3 reprises lors de la phase de déploiement du pipeline :

Avant le démarrage de la nouvelle version de l’application :

* définitions d’index (ajout, modification, suppression)

Au démarrage d’une nouvelle version de l’application, mais avant la mise en service :

* Utilisateurs du service (ajouter)
* Liste de contrôle d’accès utilisateur du service (ajouter)
* types de noeud (ajouter)

Après le passage à la nouvelle version de l’application :

* Tous les autres contenus peuvent être définis via jackrabbit Vault. Par exemple :
   * Dossiers (ajout, modification, suppression)
   * Modèles modifiables (ajout, modification, suppression)
   * Configuration de la prise en compte du contexte (tout sous `/conf`) (ajouter, modifier, supprimer)
   * Scripts (les packages peuvent déclencher des Hooks d’installation à diverses étapes du processus d’installation du package

Il est possible de limiter l’installation de contenu modifiable à la création ou à la publication en incorporant des packages dans un dossier install.author ou install.publish sous `/apps`. Informations détaillées sur la restructuration de projet recommandée dans la documentation [d’](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/restructuring/repository-restructuring.html) AEM.

>[!NOTE] Les packages de contenu sont déployés sur tous les types d’environnement (développement, étape, prod). Il n’est pas possible de limiter le déploiement à un environnement spécifique. Cette limitation est en place pour garantir l&#39;option d&#39;une série de tests d&#39;exécution automatisée. Le contenu spécifique à un environnement nécessite une installation manuelle via Package Manager.

En outre, il n’existe aucun mécanisme permettant d’annuler les modifications du package de contenu modifiable après leur application. Si les clients détectent un problème, ils peuvent choisir de le résoudre dans leur prochaine version de code ou, en dernier recours, restaurer l’ensemble du système à un moment donné avant le déploiement.

Les packs tiers inclus doivent être validés en tant qu’AEM compatible avec le service Cloud, sinon leur inclusion entraînera un échec du déploiement.

Comme mentionné ci-dessus, les clients disposant de bases de code existantes doivent se conformer à l’exercice de restructuration du référentiel décrit dans la documentation [](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/repository-restructuring.html)AEM.

## Repointer {#repoinit}

Dans les cas suivants, il est préférable d’utiliser l’approche du codage manuel pour coder manuellement les `repoinit` instructions de création de contenu explicite dans les configurations d’usine OSGI :

* Créer/supprimer/désactiver des utilisateurs de service
* Créer/supprimer des groupes
* Créer/supprimer des utilisateurs
* Ajout d’ACL
   > [!NOTE] La définition des listes de contrôle d’accès requiert que les structures de noeud soient déjà présentes. Par conséquent, il peut être nécessaire de créer des instructions de chemin avant.
* Ajouter un chemin (par exemple pour les structures de dossiers racine)
* Ajout de CND (définitions de type de noeud)

Il est préférable d’opter pour la redirection pour ces cas d’utilisation de modification de contenu pris en charge en raison des avantages suivants :

* Repoinit crée des ressources au démarrage pour que la logique prenne l&#39;existence de ces ressources pour acquise. Dans l’approche du package de contenu modifiable, les ressources sont créées après le démarrage. Le code de l’application reposant sur ces ressources peut donc échouer.
* Le repointage est un jeu d’instructions relativement sûr, car vous contrôlez explicitement l’action à entreprendre. En outre, les seules opérations prises en charge sont les ajouts, à l’exception de quelques cas liés à la sécurité qui permettent de supprimer des utilisateurs, des utilisateurs de service et des groupes. En revanche, la suppression d&#39;un élément dans l&#39;approche du package de contenu modifiable est explicite;  lorsque vous définissez un filtre, tout élément couvert par un filtre sera supprimé. Néanmoins, il faut être prudent car, pour tout contenu, il existe des scénarios où la présence d’un nouveau contenu peut modifier le comportement de l’application.
* Repoinit effectue des opérations atomiques et rapides. Les packages de contenu mutables en revanche peuvent fortement dépendre des performances selon les structures couvertes par un filtre. Même si vous mettez à jour un noeud unique, un instantané d’une grande arborescence peut être créé.
* Il est possible de valider les instructions repoinit sur un environnement de développement local au moment de l’exécution, car elles seront exécutées lorsque la configuration OSGi sera enregistrée.
* Les instructions Repoinit sont atomiques et explicites et ignorent si l’état correspond déjà.

Lorsque Cloud Manager déploie l’application, il exécute ces instructions, indépendamment de l’installation des packages de contenu.

Pour créer des instructions de redirection, procédez comme suit :

1. Ajout d’une configuration OSGi pour PID `org.apache.sling.jcr.repoinit.RepositoryInitializer` dans un dossier de configuration du projet
1. Ajoutez des instructions repoinit à la propriété de script de la configuration. La syntaxe et les options sont décrites dans la documentation [](https://sling.apache.org/documentation/bundles/repository-initialization.html)Sling. Notez que vous devez créer explicitement un dossier parent avant les dossiers enfants. Par exemple, une création explicite de `/content` before `/content/myfolder`, before `/content/myfolder/mysubfolder`. Pour que les listes ACL soient définies sur des structures de bas niveau, il est recommandé de les définir sur un niveau supérieur et de travailler avec une `rep:glob` restriction.  Par exemple `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. Validez l’environnement de développement local au moment de l’exécution.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>Pour les listes de contrôle d’accès définies pour les noeuds situés en dessous `/apps` ou `/libs` l’exécution du repointage démarre sur un référentiel vide. Les packages sont installés après repointit, de sorte que les instructions ne peuvent pas compter sur les éléments définis dans les packages, mais doivent définir les conditions préalables comme les structures parents sous-jacentes.

>[!TIP]
>
>Pour les ACL, la création de structures profondes peut être encombrante, il est donc plus raisonnable de définir une ACL à un niveau supérieur et de contraindre là où elle est censée agir par une restriction rep:glob.

Pour plus d’informations sur le repointage, reportez-vous à la documentation [Sling.](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### Package Manager &quot;one-off&quot; pour les packages de contenu mutables {#package-manager-oneoffs-for-mutable-content-packages}

Il existe des cas d’utilisation où un package de contenu doit être installé comme &quot;un package unique&quot;. Par exemple, pour déboguer un problème de production, vous devez importer du contenu spécifique de la production à la phase intermédiaire. Pour ces scénarios, Package Manager peut être utilisé dans AEM en tant qu’environnements de service Cloud.

Comme Package Manager est un concept d’exécution, il n’est pas possible d’installer du contenu ou du code dans le référentiel immuable. Par conséquent, ces packages de contenu ne doivent se composer que de contenu mutable (principalement `/content` ou `/conf`). Si le package de contenu comprend du contenu mixte (contenu mutant et non modifiable), seul le contenu mutable sera installé.

Les packages de contenu installés via Cloud Manager (modifiables et non modifiables) s’affichent dans un état figé dans l’interface utilisateur d’AEM Package Manager. Ces packs ne peuvent pas être réinstallés, recréés ou même téléchargés. Ils sont répertoriés avec un suffixe **&quot;cp2fm&quot;** , indiquant que leur installation a été gérée par Cloud Manager.

### Inclusion de packs tiers {#including-third-party}

Il est courant pour les clients d’inclure des packs prédéveloppés provenant de sources tierces, telles que des fournisseurs de logiciels tels que les partenaires de traduction d’Adobe. Il est recommandé d’héberger ces packages dans un référentiel distant et de les référencer dans le `pom.xml`. Cela n&#39;est possible que pour les référentiels publics.

S’il n’est pas possible de stocker le package dans un référentiel distant, les clients peuvent le placer dans un référentiel Maven local basé sur un système de fichiers, qui est engagé dans SCM dans le cadre du projet et référencé par tout ce qui en dépend. Le référentiel serait déclaré dans les grandes lignes du projet, comme illustré ci-dessous:


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Les packs tiers inclus doivent être conformes aux directives de codage et de création de package d’AEM en tant que service Cloud et de service AEM décrites dans cet article. Sinon, son inclusion entraînera un échec du déploiement.

Le fragment de code XML Maven POM suivant montre comment les packages tiers peuvent être incorporés dans le package &quot;Container&quot; du projet, généralement appelé **&#39;all&#39;**, via la configuration du module externe Maven **filevault-package-maven** .

```
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <subPackages>
           
          <!-- Include the application's ui.apps and ui.content packages -->
          ...
 
          <!-- Include any other extra packages such as AEM WCM Core Components -->
          <!-- Set the version for all dependencies, including 3rd party packages, in the project's Reactor POM -->
          <subPackage>
              <groupId>com.adobe.cq</groupId>
              <artifactId>core.wcm.components.all</artifactId>
              <filter>true</filter>
          </subPackage>
 
 
          <subPackage>
              <groupId>com.3rdparty.groupId</groupId>
              <artifactId>core.3rdparty.artifactId</artifactId>
              <filter>true</filter>
          </subPackage>
      <subPackages>
  </configuration>
</plugin>
...
```

## Fonctionnement des déploiements roulants {#how-rolling-deployments-work}

Comme les mises à jour d’AEM, les versions des clients sont déployées à l’aide d’une stratégie de déploiement variable afin d’éliminer les temps d’arrêt de la grappe d’auteurs dans les bonnes circonstances. La séquence générale des événements est décrite ci-dessous, où **Blue** est l’ancienne version du code client et **Green** est la nouvelle version. Blue et Green exécutent tous deux la même version du code AEM.

* La version bleue est active et un candidat à la version verte est créé et disponible
* S’il existe des définitions d’index nouvelles ou mises à jour, les index correspondants sont traités. Notez que le déploiement bleu utilisera toujours les anciens index, tandis que le vert utilisera toujours les nouveaux index.
* Le vert commence alors que le bleu sert toujours
* Blue fonctionne et sert pendant que Green est contrôlé pour vérifier l&#39;état de préparation au moyen de contrôles d&#39;intégrité
* Les noeuds verts qui acceptent le trafic et remplacent les noeuds bleus, qui sont abaissés
* Au fil du temps, les noeuds bleus sont remplacés par des noeuds verts jusqu’à ce que seuls les noeuds verts restent, ce qui permet d’achever le déploiement.
* Tout contenu modifiable nouveau ou modifié est déployé

## Indexes {#indexes}

Les nouveaux index ou les index modifiés entraîneront une étape supplémentaire d’indexation ou de réindexation avant que la nouvelle version (verte) puisse prendre en charge le trafic. Vous trouverez des détails sur la gestion des index dans Skyline dans [cet article](/help/operations/indexing.md). Vous pouvez vérifier l’état de la tâche d’indexation sur la page de création de Cloud Manager et recevrez une notification lorsque la nouvelle version sera prête à recevoir du trafic.

>[!NOTE]
>
>Le temps nécessaire pour un déploiement variable varie en fonction de la taille de l’index, car la version verte ne peut pas accepter le trafic tant que le nouvel index n’a pas été généré.

Pour le moment, Skyline ne fonctionne pas avec des outils de gestion d&#39;index tels que ACS Commons Verify Oak Index.

## Réplication {#replication}

Le mécanisme de publication est rétrocompatible avec les API [Java de réplication](https://helpx.adobe.com/experience-manager/6-3/sites/developing/using/reference-materials/diff-previous/changes/com.day.cq.replication.Replicator.html)AEM.

Pour développer et tester la réplication avec AEM Quickstart prêt pour le cloud, les fonctionnalités classiques de réplication doivent être utilisées avec une configuration Auteur/Publication. Dans le cas où le point d’entrée de l’interface utilisateur sur AEM Author a été supprimé pour le cloud, les utilisateurs accèdent à `http://localhost:4502/etc/replication` la configuration.

## Code rétrocompatible pour les déploiements variables {#backwards-compatible-code-for-rolling-deployments}

Comme indiqué ci-dessus, la stratégie de déploiement variable d’AEM en tant que service Cloud implique que les anciennes et nouvelles versions peuvent être opérationnelles en même temps. Par conséquent, soyez prudent lorsque vous modifiez le code qui n’est pas rétrocompatible avec l’ancienne version d’AEM qui est toujours opérationnelle.

En outre, l’ancienne version doit être testée pour vérifier sa compatibilité avec toute nouvelle structure de contenu modifiable appliquée par la nouvelle version en cas de restauration, puisque le contenu mutable n’est pas supprimé.

### Utilisateurs du service et modifications d’ACL {#service-users-and-acl-changes}

La modification des utilisateurs de service ou des listes de contrôle d’accès nécessaires pour accéder au contenu ou au code peut entraîner des erreurs dans les anciennes versions d’AEM, ce qui entraîne l’accès à ce contenu ou à ce code avec des utilisateurs de service obsolètes. Pour remédier à ce problème, il est recommandé d’effectuer des modifications sur au moins 2 versions, la première version jouant le rôle de passerelle avant de procéder au nettoyage dans la version suivante.

### Modifications de l’index {#index-changes}

Si des modifications sont apportées aux index, il est important que la version Bleue continue à utiliser ses index jusqu&#39;à ce qu&#39;il soit terminé, tandis que la version verte utilise son propre jeu d&#39;index modifié. Le développeur doit suivre les techniques de gestion des index décrites [dans cet article](/help/operations/indexing.md).

### Codage conservateur pour les restaurations {#conservative-coding-for-rollbacks}

Si un échec est signalé ou détecté après le déploiement, il est possible qu’une restauration de la version bleue soit nécessaire. Il serait judicieux de s&#39;assurer que le code Bleu est compatible avec toutes les nouvelles structures créées par la version Verte puisque les nouvelles structures (tout contenu mutant) ne seront pas annulées. Si l’ancien code n’est pas compatible, des correctifs devront être appliqués dans les versions ultérieures du client.

## Runmodes {#runmodes}

Dans les solutions AEM existantes, les clients peuvent exécuter des instances avec des modes d’exécution arbitraires et appliquer la configuration OSGI ou installer des lots OSGI à ces instances spécifiques. Les modes d’exécution définis incluent généralement le *service* (auteur et publication) et l’environnement (développement, étape, prod).

AEM as a Cloud Service, en revanche, est plus précis sur les modes d’exécution disponibles et sur la manière dont les lots OSGI et la configuration OSGI peuvent être mappés à ces modes :

* Les modes d’exécution de configuration OSGI doivent faire référence au développement, à l’étape, à la prod pour l’environnement ou à l’auteur, à la publication pour le service. Une combinaison de `<service>.<environment_type>` est prise en charge alors qu’elle doit être utilisée dans cet ordre particulier (par exemple author.dev ou publish.prod). Les jetons OSGI doivent être référencés directement à partir du code plutôt que d’utiliser la `getRunModes` méthode, qui n’inclut plus les jetons `environment_type` au moment de l’exécution.
* Les modes d’exécution des lots OSGI sont limités au service (auteur, publication). Les lots OSGI par mode d’exécution doivent être installés dans le package de contenu sous `install/author` ou `install/publish`.

Comme les solutions AEM existantes, il n’existe aucun moyen d’utiliser les modes d’exécution pour installer uniquement le contenu pour des environnements ou services spécifiques. S’il était nécessaire d’amorcer un environnement de développement avec des données ou du code HTML qui n’est pas sur l’étape ou la production, le gestionnaire de packages pourrait être utilisé.

Les configurations runmode prises en charge sont les suivantes :

* **config** (*La valeur par défaut s’applique à tous les services* AEM)
* **config.author** (*s’applique à tous les services* Auteur AEM)
* **config.author.dev** (*s’applique au service* Auteur de développement AEM)
* **config.author.stage** (*s’applique au service* d’auteur d’évaluation AEM)
* **config.author.prod** (*s’applique au service* Auteur de production AEM)
* **config.publish** (*s’applique au service* de publication AEM)
* **config.publish.dev** (*s’applique au service* de publication de développement AEM)
* **config.publish.stage** (*s’applique au service* de publication intermédiaire AEM)
* **config.publish.prod** (*s’applique au service* de publication de production AEM)
* **config.dev** (*S’applique aux services AEM Dev)
* **config.stage** (*S’applique aux services de test AEM)
* **config.prod** (*S’applique aux services de production AEM)

La configuration OSGI qui possède les modes d’exécution les plus correspondants est utilisée.

Lors du développement local, un paramètre de démarrage en mode d’exécution peut être transmis pour indiquer quelle configuration OSGI en mode d’exécution sera utilisée.

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Configuration des tâches de maintenance dans le contrôle source {#maintenance-tasks-configuration-in-source-control}

Les configurations de tâches de maintenance doivent être conservées dans le contrôle de code source, car l’écran **Outils > Opérations** ne sera plus disponible dans les environnements Cloud. Cela a l&#39;avantage de s&#39;assurer que les changements sont intentionnellement maintenus plutôt que appliqués de manière réactive et peut-être oubliés. Pour plus d&#39;informations, reportez-vous à l&#39;article [Tâche de](/help/operations/maintenance.md) maintenance.
