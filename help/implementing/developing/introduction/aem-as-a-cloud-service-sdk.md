---
title: SDK AEM as a Cloud Service
description: 'À terminer '
translation-type: tm+mt
source-git-commit: 2142bce6296e671fd1039dec8b0686c609611d98

---


# SDK d’AEM as a Cloud Service {#aem-as-a-cloud-service-sdk}

Le SDK d’AEM as a Cloud Service est constitué des artefacts suivants :

* **Quickstart Jar** : composant d’exécution AEM utilisé pour le développement local.
* **Java API Jar** : dépendance Java Jar/Maven qui expose toutes les API Java autorisées pouvant être utilisées en vue de développer pour AEM as a Cloud Service. Anciennement appelé Uberjar.
* **Javadoc Jar** : javadocs du fichier Java API Jar.
* **Outils Dispatcher** : ensemble d’outils utilisés en vue du développement local pour Dispatcher. Artefacts distincts pour Unix et Windows

En outre, certains clients qui ont déjà été déployés avec AEM 6.5 ou des versions antérieures utiliseront les artefacts ci-dessous. Si la compilation locale ne fonctionne pas avec le fichier Quickstart Jar et que vous pensez que cela est dû à la suppression des interfaces d’AEM déployé en tant que Cloud Service, contactez le service clientèle pour déterminer si vous avez besoin d’un accès. Cela nécessitera des modifications sur le serveur principal.

* **6.5 Deprecated Java API Jar** : jeu supplémentaire d’interfaces qui ont été supprimées depuis AEM 6.5.
* **6.5 Deprecated Javadoc Jar** : Javadocs pour l’ensemble supplémentaire d’interfaces.

## Accès au SDK d’AEM as a Cloud Service {#accessing-the-aem-as-a-cloud-service-sdk}

* Vous pouvez consulter l’icône **À propos d’Adobe Experience Manager** d’AEM Admin Console pour connaître la version d’AEM que vous exécutez en production.
* Le fichier Quickstart Jar et les outils Dispatcher peuvent être téléchargés dans un fichier ZIP depuis le [portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Notez que l’accès aux listes de SDK est limité aux environnements AEM Managed Services ou AEM as a Cloud Service.
* Les fichiers Java API Jar et Javadoc Jar peuvent être téléchargés via l’outil Maven, soit en ligne de commande, soit avec votre IDE préféré.
* Les fichiers pom de projet Maven doivent faire référence au module API Jar suivant. Cette dépendance doit également être référencée dans tous les sous-modules pom.

```
<dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>aem-sdk-api</artifactId>
  <version>2019.11.3006.20191108T223635Z-191201</version> 
  <scope>provided</scope>
</dependency>
```

> [!NOTE] L’entrée de version du SDK doit correspondre à la version d’AEM as a Cloud Service. Vous pouvez voir quelle version vous utilisez en vous connectant à AEM, puis en accédant au point d’interrogation dans le coin supérieur droit de l’écran et en sélectionnant **[!UICONTROL À propos d’Adobe Experience Manager]**.

* La coordonnée distante du référentiel Maven dans lequel le module est hébergé doit être incluse dans le fichier pom.

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

Quand est-il recommandé d’actualiser le projet local avec un nouveau SDK ?

Il est *recommandé* de l’actualiser au moins après une version de maintenance mensuelle.

Il est *facultatif* de l’actualiser après une version de maintenance quotidienne. Les clients seront informés lorsque leur instance de production a été correctement mise à niveau vers une nouvelle version d’AEM. Pour les versions de maintenance quotidiennes, il n’est pas prévu que le nouveau SDK change de manière significative, voire qu’il change du tout. Il est toutefois recommandé d’actualiser occasionnellement l’environnement de développement AEM local avec le dernier SDK, puis de recréer et de tester l’application personnalisée. La version de maintenance mensuelle comprend généralement des modifications ayant davantage d’impact. Les développeurs doivent par conséquent immédiatement actualiser, recréer et tester.

Voici la procédure recommandée pour actualiser un environnement local :

1. Assurez-vous que tout contenu utile est soit validé dans le projet dans le contrôle de code source, soit disponible dans un module de contenu modifiable pour importation ultérieure.
1. Le contenu du test de développement local doit être stocké séparément afin qu’il ne soit pas déployé dans le cadre de la génération du pipeline de Cloud Manager. C’est parce qu’il ne doit être utilisé que pour le développement local.
1. Arrêtez le fichier quickstart en cours d’exécution.
1. Déplacez le dossier `crx-quickstart` vers un autre dossier pour le conserver en lieu sûr.
1. Notez la nouvelle version d’AEM, qui est indiquée dans Cloud Manager (elle sera utilisée pour identifier la nouvelle version du fichier QuickStart Jar à télécharger plus loin).
1. Téléchargez le fichier QuickStart Jar dont la version correspond à la version d’AEM en production depuis le portail de distribution de logiciels.
1. Créez un dossier et placez-y le nouveau fichier QuickStart Jar.
1. Démarrez le nouveau fichier QuickStart avec les modes d’exécution de votre choix (renommez le fichier ou transmettez les modes d’exécution via `-r`).
   * Assurez-vous qu’il n’y a aucun vestige de l’ancien fichier quickstart dans le dossier.
1. Créez votre application AEM.
1. Déployez votre application AEM vers AEM local via le gestionnaire de modules.
1. Installez tous les modules de contenu modifiable nécessaires au test de l’environnement local via le gestionnaire de modules.
1. Poursuivez le développement et déployez les modifications si nécessaire.

Si du contenu doit être installé avec chaque nouvelle version de quickstart d’AEM, incluez-le dans un module de contenu et dans le contrôle de code source du projet. Installez-le ensuite à chaque fois.

Il est recommandé de mettre à jour fréquemment le SDK (par exemple, toutes les deux semaines) et de supprimer quotidiennement l’état local complet pour ne pas dépendre accidentellement de données avec état dans l’application.

Si vous dépendez de CryptoSupport ([soit en configurant les informations d’identification des Cloud Services ou du service de messagerie SMTP dans AEM, soit en utilisant l’API CryptoSupport dans votre application](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/crypto/CryptoSupport.html)), les propriétés sont chiffrées par une clé qui est générée automatiquement au premier démarrage d’un environnement AEM. Bien que la configuration du cloud s’occupe de réutiliser automatiquement la clé de chiffrement (CryptoKey) spécifique à l’environnement, il est nécessaire d’injecter la clé de chiffrement dans l’environnement de développement local.

Par défaut, AEM est configuré pour stocker les données clés dans le dossier de données d’un dossier, mais pour faciliter leur réutilisation dans le développement, le processus AEM peut être initialisé au premier démarrage avec « `-Dcom.adobe.granite.crypto.file.disable=true` ». Les données de chiffrement seront alors générées à l’emplacement « `/etc/key` ».

Pour pouvoir réutiliser des modules de contenu contenant les valeurs chiffrées, procédez comme suit :

* Lorsque vous démarrez le fichier quickstart.jar local, veillez à ajouter le paramètre ci-dessous : « `-Dcom.adobe.granite.crypto.file.disable=true` ». Il est recommandé de toujours l’ajouter, bien qu’il soit facultatif.
* La toute première fois que vous démarrez une instance, créez un module contenant un filtre pour la racine « `/etc/key` ». Le secret sera alors réutilisé dans tous les environnements pour lesquels vous souhaitez qu’il le soit.
* Exportez tout contenu modifiable contenant des secrets, ou recherchez les valeurs chiffrées via `/crx/de` pour les ajouter au module qui sera réutilisé dans toutes les installations.
* Chaque fois que vous créez une instance (pour remplacer une instance par une nouvelle version ou parce que plusieurs environnements de développement doivent partager les informations d’identification pour les tests), installez le module généré aux étapes 2 et 3 afin de pouvoir réutiliser le contenu sans avoir à reconfigurer manuellement. C’est parce que la clé de chiffrement est maintenant synchronisée.