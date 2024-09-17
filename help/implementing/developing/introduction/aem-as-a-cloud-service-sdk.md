---
title: SDK AEM as a Cloud Service
description: Aperçu du SDK AEM as a Cloud Service
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8ccf03ebcb4a96b66a15dc9a1161a857888278a7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# SDK d’AEM as a Cloud Service {#aem-as-a-cloud-service-sdk}

Le SDK d’AEM as a Cloud Service est constitué des artefacts suivants :

* **Quickstart Jar** : composant d’exécution AEM utilisé pour le développement local
* **Java™ API Jar** : dépendance Java™ Jar/Maven qui expose toutes les API Java™ autorisées pouvant être utilisées en vue de développer pour AEM as a Cloud Service. Anciennement appelé Uberjar
* **Javadoc Jar** : javadocs du fichier Java™ API Jar
* **Outils Dispatcher** : ensemble d’outils utilisés en vue du développement local pour Dispatcher. Artefacts distincts pour Unix® et Windows

En outre, certains clientes et clients qui ont déjà été déployés avec AEM 6.5 ou des versions antérieures utilisent les artefacts ci-dessous. Si la compilation locale ne fonctionne pas avec le fichier jar Quickstart et que vous pensez que c’est dû à la suppression des interfaces d’AEM déployé as a Cloud Service, contactez le service clientèle. Ils peuvent déterminer si vous avez besoin d’un accès. Cela nécessite des modifications dans le serveur principal.

* **6.5 Java™ API Jar obsolète** : jeu supplémentaire d’interfaces qui ont été supprimées depuis AEM 6.5.
* **6.5 Deprecated Javadoc Jar** : Javadocs pour l’ensemble supplémentaire d’interfaces.

>[!NOTE]
> 
> Il existe des différences entre AEM as a Cloud Service et le SDK, dans plusieurs domaines différents. Dans les cas où des modifications rapides et itératives sont nécessaires, Adobe a introduit des environnements de développement rapide. Pour plus d’informations, consultez la section [Environnements de développement rapide](/help/implementing/developing/introduction/rapid-development-environments.md) .

## Création pour le SDK {#building-for-the-sdk}

Le SDK AEM as a Cloud Service permet de créer et de déployer du code personnalisé. Consultez la [documentation AEM sur l’archétype de projet](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=fr). Voici ce qui est réalisé de manière générale :

* **Compilation du code**. Comme prévu, le code source est compilé afin de générer les packages de contenu résultants.
* **Création d’artefacts**. Les artefacts sont créés pendant ce processus.
* **Analyse des lots**. Les lots sont analysés à l’aide du plug-in d’analyse Maven, qui recherche des problèmes dans le projet Maven, tels que les dépendances manquantes.
* **Déploiement d’artefacts**. Les artefacts sont déployés sur le serveur local.

Les mêmes opérations sont exécutées par Cloud Manager lors du déploiement vers des environnements cloud. L’exécution locale des versions permet le développement et les tests locaux. Les développeurs et les développeuses peuvent découvrir du code ou des problèmes structurels efficacement avant de s’engager dans le contrôle de code source et de déclencher des déploiements de Cloud Manager, ce qui peut prendre plus de temps.

>[!NOTE]
>
>Le SDK AEM as a Cloud Service doit être créé avec une distribution et une version de Java prises en charge par [l’environnement de génération Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Les clients AEM as a Cloud Service peuvent télécharger le JDK d’Oracle à partir du [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?lang=fr) et bénéficier d’une prise en charge étendue de Java 11 jusqu’en septembre 2026 en raison des conditions d’octroi de licence et de prise en charge de la technologie Java d’Oracle lorsqu’elle est utilisée dans des projets Adobe Experience Manager.

## Accès au SDK d’AEM as a Cloud Service {#accessing-the-aem-as-a-cloud-service-sdk}

* Vous pouvez consulter l’icône **À propos d’Adobe Experience Manager** d’AEM Admin Console pour connaître la version d’AEM que vous exécutez en production.
* Le fichier Quickstart Jar et les outils Dispatcher peuvent être téléchargés dans un fichier ZIP depuis le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?lang=fr). L’accès aux listes de SDK est limité aux personnes qui ont des environnements sur AEM Managed Services ou AEM as a Cloud Service.
* Les fichiers Java™ API Jar et Javadoc Jar peuvent être téléchargés via l’outil Maven, soit en ligne de commande, soit avec votre IDE préféré.
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
>L’entrée de version du SDK doit correspondre à la version d’AEM as a Cloud Service. Vous pouvez voir la version que vous utilisez en vous connectant à AEM. Dans le coin supérieur droit de l’écran, accédez au point d’interrogation et sélectionnez **[!UICONTROL À propos d’Adobe Experience Manager]**.


## Actualisation d’un projet local avec une nouvelle version du SDK {#refreshing-a-local-project-with-a-new-skd-version}

Quand est-il recommandé d’actualiser le projet local avec un nouveau SDK ?

Adobe *recommande* de l’actualiser après une mise à jour mensuelle.

Il est *facultatif* de l’actualiser après une version de maintenance quotidienne. Les clientes et clients sont informés lorsque leur instance de production a été correctement mise à niveau vers une nouvelle version d’AEM. Pour les versions de maintenance quotidiennes, il n’est pas prévu que le nouveau SDK change de manière significative, voire qu’il change du tout. Il est toutefois recommandé d’actualiser occasionnellement l’environnement de développement AEM local avec le dernier SDK, puis de recréer et de tester l’application personnalisée. La version de maintenance mensuelle comprend généralement des modifications ayant davantage d’impact. Les développeurs et développeuses doivent par conséquent immédiatement actualiser, recréer et tester.

Voici la procédure recommandée pour actualiser un environnement local :

1. Assurez-vous que tout contenu utile est validé dans le projet dans le contrôle de code source ou disponible dans un module de contenu modifiable pour importation ultérieure.
1. Le contenu du test de développement local doit être stocké séparément afin qu’il ne soit pas déployé dans le cadre de la création du pipeline de Cloud Manager. La raison en est qu’il n’est utilisé que pour le développement local.
1. Arrêtez le fichier QuickStart en cours d’exécution.
1. Déplacez le dossier `crx-quickstart` vers un autre dossier pour le conserver en lieu sûr.
1. Notez la nouvelle version d’AEM, qui est indiquée dans Cloud Manager (elle sera utilisée pour identifier la nouvelle version du fichier QuickStart Jar à télécharger plus tard).
1. Téléchargez le fichier QuickStart Jar dont la version correspond à la version d’AEM en production depuis le portail de distribution de logiciels.
1. Créez un dossier et placez-y le nouveau fichier QuickStart Jar.
1. Démarrez le nouveau fichier QuickStart avec les modes d’exécution de votre choix (renommez le fichier ou transmettez les modes d’exécution à l’aide de `-r`).
   * Assurez-vous qu’il n’y a aucun vestige de l’ancien fichier quickstart dans le dossier.
1. Créez votre application AEM.
1. Déployez votre application AEM sur une instance AEM locale à l’aide du gestionnaire de packages.
1. Installez tous les packages de contenu modifiable nécessaires au test de l’environnement local via le gestionnaire de packages.
1. Poursuivez le développement et déployez les modifications si nécessaire.

Si du contenu doit être installé avec chaque nouvelle version de quickstart d’AEM, incluez-le dans un package de contenu et dans le contrôle de code source du projet. Installez-le ensuite à chaque fois.

Il est recommandé de mettre à jour fréquemment le SDK (par exemple, toutes les deux semaines) et de supprimer quotidiennement l’état local complet afin de ne pas dépendre accidentellement de données avec état dans l’application.

Si vous dépendez de CryptoSupport ([en configurant les informations d’identification des services Cloud ou du service de messagerie SMTP dans AEM ou en utilisant l’API CryptoSupport dans votre application](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html)), les propriétés chiffrées sont chiffrées par une clé. Cette clé est générée automatiquement lors du premier démarrage d’un environnement AEM. Bien que la configuration du cloud s’occupe de réutiliser automatiquement la clé de chiffrement (CryptoKey) spécifique à l’environnement, il est nécessaire d’injecter la clé de chiffrement dans l’environnement de développement local.

Par défaut, AEM est configuré pour stocker les données clés dans le dossier de données d’un dossier, mais pour faciliter leur réutilisation dans le développement, le processus AEM peut être initialisé lors du premier démarrage avec « `-Dcom.adobe.granite.crypto.file.disable=true` ». Ce processus génère les données de chiffrement sur « `/etc/key` ».

Pour pouvoir réutiliser des packages de contenu contenant les valeurs chiffrées, procédez comme suit :

* Lorsque vous démarrez le fichier quickstart.jar local, veillez à ajouter le paramètre ci-dessous : « `-Dcom.adobe.granite.crypto.file.disable=true` ». Il est recommandé de toujours l’ajouter, bien qu’il soit facultatif.
* La toute première fois que vous démarrez une instance, créez un package contenant un filtre pour la racine « `/etc/key` ». Ce package contient le secret à réutiliser dans tous les environnements pour lesquels vous souhaitez qu’il soit réutilisé.
* Exportez tout contenu modifiable contenant des secrets ou recherchez les valeurs chiffrées à l’aide de `/crx/de` afin de les ajouter au package réutilisé dans toutes les installations.
* Lorsque vous créez une nouvelle instance (pour la remplacer par une nouvelle version ou parce que plusieurs environnements de développement doivent partager les informations d’identification pour les tests), installez le package généré aux étapes 2 et 3. Cela vous permet de réutiliser le contenu sans avoir à le reconfigurer manuellement. C’est parce que la clé de chiffrement est désormais synchronisée.
