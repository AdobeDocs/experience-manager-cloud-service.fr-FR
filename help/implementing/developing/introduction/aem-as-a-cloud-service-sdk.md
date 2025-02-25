---
title: SDK AEM as a Cloud Service
description: Présentation du kit de développement logiciel AEM as a Cloud Service.
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 82f5078740b2cf6ac481d83df40bbbc4fb3c1a77
workflow-type: tm+mt
source-wordcount: '1246'
ht-degree: 43%

---

# SDK d’AEM as a Cloud Service {#aem-as-a-cloud-service-sdk}

Le SDK d’AEM as a Cloud Service est constitué des artefacts suivants :

* **Quickstart Jar** - Runtime AEM utilisé pour le développement local.
* **Java™ API Jar** : dépendance Java™ Jar/Maven qui expose toutes les API Java™ autorisées pouvant être utilisées en vue de développer pour AEM as a Cloud Service. Anciennement appelé Uberjar.
* **Jar Javadoc** - Documentation Java pour le fichier Jar de l’API Java™.
* **Outils Dispatcher** : ensemble d’outils utilisés en vue du développement local pour Dispatcher. Artefacts séparés pour UNIX® et Windows.

En outre, certains clientes et clients qui ont déjà été déployés avec AEM 6.5 ou des versions antérieures utilisent les artefacts ci-dessous. Si la compilation locale ne fonctionne pas avec le fichier Jar QuickStart et que vous pensez qu’elle provient de la suppression d’interfaces d’as a Cloud Service déployé dans AEM, contactez le service clientèle. Ils peuvent déterminer si vous avez besoin d’un accès. Cela nécessite des modifications dans le serveur principal.

* **6.5 - Jar d’API Java™ obsolète** - Ensemble supplémentaire d’interfaces qui ont été supprimées depuis AEM 6.5.
* Jar Javadoc **6.5 obsolète** - Documentation Java pour l’ensemble supplémentaire d’interfaces.

>[!NOTE]
> 
> Il existe des différences entre AEM as a Cloud Service et SDK dans de nombreux domaines. Dans les cas où des modifications rapides et itératives sont nécessaires, Adobe a introduit des environnements de développement rapide. Consultez [Environnements de développement rapide](/help/implementing/developing/introduction/rapid-development-environments.md) pour plus d’informations.

## Création pour le SDK {#building-for-the-sdk}

Le SDK AEM as a Cloud Service permet de créer et de déployer du code personnalisé. Voir la documentation sur l’[archétype de projet AEM](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/using). Voici ce qui est réalisé de manière générale :

* **Compiler le code** - Le code Source est compilé, générant les packages de contenu résultants.
* **Créer des artefacts** - Les artefacts sont créés pendant ce processus.
* **Analyser les lots** - Les lots sont analysés à l’aide du plug-in Maven Analyzer, qui recherche les problèmes du projet Maven tels que les dépendances manquantes.
* **Déployer les artefacts** - Les artefacts sont déployés sur le serveur local.

Cloud Manager exécute les mêmes étapes lors d’un déploiement dans des environnements cloud. L’exécution locale des versions permet le développement et les tests locaux. Les développeurs peuvent identifier efficacement les problèmes de code ou de structure avant de s’engager dans le contrôle de code source. Ce processus permet d’éviter les retards liés au déclenchement des déploiements de Cloud Manager, qui peuvent prendre plus de temps.

>[!NOTE]
>
>AEM as a Cloud Service SDK doit être créé avec une distribution et une version de Java prises en charge par l’environnement de création [Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Les clients AEM as a Cloud Service peuvent télécharger le JDK Oracle à partir du [portail de distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?lang=fr). Ils bénéficient de la prise en charge étendue de Java 11 jusqu’en septembre 2026 en raison des conditions de licence et de prise en charge d’Adobe pour la technologie Java Oracle dans les projets Adobe Experience Manager.

## Accès au SDK d’AEM as a Cloud Service {#accessing-the-aem-as-a-cloud-service-sdk}

* Vous pouvez vérifier l’icône AEM Admin Console **À propos de Adobe Experience Manager** pour connaître la version d’AEM que vous exécutez en production.
* Les outils QuickStart Jar et Dispatcher peuvent être téléchargés sous la forme d’un fichier zip à partir du [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?lang=fr). L’accès aux listes de SDK est limité aux personnes qui ont des environnements sur AEM Managed Services ou AEM as a Cloud Service.
* Le jar de l’API Java™ et le jar Javadoc peuvent être téléchargés via l’outil Maven, en ligne de commande ou avec l’IDE de votre choix.
* Les fichiers pom de projet Maven doivent faire référence au package API Jar suivant. Vous devez également référencer la dépendance à l’égard de tout sous-package pom.

```
<dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>aem-sdk-api</artifactId>
  <version>2019.11.3006.20191108T223635Z-191201</version>
  <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>L’entrée de version du SDK doit correspondre à la version d’AEM as a Cloud Service. Vous pouvez voir la version que vous utilisez en vous connectant à AEM. Dans le coin supérieur droit de l’écran, accédez au point d’interrogation et cliquez sur **[!UICONTROL À propos de Adobe Experience Manager]**.


## Actualiser un projet local avec une nouvelle version de SDK {#refreshing-a-local-project-with-a-new-skd-version}

Quand est-il recommandé d’actualiser le projet local avec un nouveau SDK ?

Adobe *recommande* de l’actualiser après une mise à jour mensuelle.

Il est *facultatif* de l’actualiser après une version de maintenance quotidienne. Les clientes et clients sont informés lorsque leur instance de production a été correctement mise à niveau vers une nouvelle version d’AEM. Pour les versions de maintenance quotidiennes, il n’est pas prévu que le nouveau SDK change de manière significative, voire qu’il change du tout. Néanmoins, Adobe vous recommande d’actualiser occasionnellement l’environnement de développement AEM local avec le dernier SDK, puis de recréer et de tester l’application personnalisée. La version de maintenance mensuelle comprend généralement des modifications ayant davantage d’impact. Les développeurs et développeuses doivent par conséquent immédiatement actualiser, recréer et tester.

**Pour actualiser un projet local avec une nouvelle version de SDK :**

1. Assurez-vous que tout le contenu utile est validé dans le contrôle de code source. Ou stocké dans un package de contenu modifiable en vue d’une importation ultérieure.
1. Le contenu du test de développement local doit être stocké séparément afin qu’il ne soit pas déployé dans le cadre de la création du pipeline de Cloud Manager. La raison en est qu’il n’est utilisé que pour le développement local.
1. Arrêtez le fichier QuickStart en cours d’exécution.
1. Déplacez le dossier `crx-quickstart` vers un autre dossier pour le conserver en lieu sûr.
1. Notez la nouvelle version d’AEM, qui est indiquée dans Cloud Manager (elle sera utilisée pour identifier la nouvelle version du fichier QuickStart Jar à télécharger plus tard).
1. Téléchargez le fichier Jar de démarrage rapide dont la version correspond à la version de production d’AEM à partir du portail de distribution de logiciels .
1. Créez un dossier et placez-y le nouveau fichier QuickStart Jar.
1. Démarrez le nouveau QuickStart avec les modes d’exécution souhaités (en renommant le fichier ou en transmettant les modes d’exécution par le biais du `-r`).
Assurez-vous qu’il n’y a aucun reste de l’ancien démarrage rapide dans le dossier.
1. Créez votre application AEM.
1. Déployez votre application AEM sur une instance AEM locale à l’aide du gestionnaire de packages.
1. Installez tous les packages de contenu modifiables nécessaires aux tests de l’environnement local via le gestionnaire de packages.
1. Poursuivez le développement et déployez les modifications si nécessaire.

Si du contenu doit être installé avec chaque nouvelle version de quickstart d’AEM, incluez-le dans un package de contenu et dans le contrôle de code source du projet. Installez-le ensuite à chaque fois.

Adobe vous recommande de mettre à jour SDK fréquemment, par exemple toutes les deux semaines. De plus, éliminez quotidiennement l’intégralité de l’état local afin de ne pas dépendre accidentellement des données d’état dans l’application.

Si vous utilisez CryptoSupport pour les services cloud, la configuration de messagerie SMTP ou l&#39;API CryptoSupport, les propriétés chiffrées sont sécurisées avec une clé . Pour plus d’informations, consultez la [documentation de l’API CryptoSupport](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html). Cette clé est générée automatiquement lors du premier démarrage d’un environnement AEM. Bien que la configuration du cloud s’occupe de réutiliser automatiquement la clé de chiffrement (CryptoKey) spécifique à l’environnement, il est nécessaire d’injecter la clé de chiffrement dans l’environnement de développement local.

Par défaut, AEM est configuré pour stocker les données essentielles dans le dossier de données d’un dossier, mais pour faciliter leur réutilisation dans le développement, le processus AEM peut être initialisé au premier démarrage avec « `-Dcom.adobe.granite.crypto.file.disable=true` ». Ce processus génère les données de chiffrement à « `/etc/key` ».

**Pour réutiliser des packages de contenu contenant les valeurs chiffrées :**

* Lorsque vous démarrez initialement le fichier quickstart.jar local, veillez à ajouter le paramètre suivant : « `-Dcom.adobe.granite.crypto.file.disable=true` ». Adobe vous recommande éventuellement de toujours l’ajouter.
* La première fois que vous avez démarré une instance, créez un package contenant un filtre pour la racine « `/etc/key` ». Ce package contient le secret à réutiliser dans tous les environnements pour lesquels vous souhaitez qu’il soit réutilisé.
* Exportez tout contenu modifiable contenant des secrets. Vous pouvez également rechercher les valeurs chiffrées par le biais de `/crx/de` afin de les ajouter au package qui est réutilisé sur plusieurs installations.
* Lorsque vous créez une nouvelle instance (pour la remplacer par une nouvelle version ou parce que plusieurs environnements de développement doivent partager les informations d’identification pour les tests), installez le package généré aux étapes 2 et 3. Cela vous permet de réutiliser le contenu sans avoir à le reconfigurer manuellement. C’est parce que la clé de chiffrement est désormais synchronisée.

