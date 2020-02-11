---
title: AEM en tant que SDK de service cloud
description: 'À terminer '
translation-type: tm+mt
source-git-commit: a7dc007230632bf8343004794b2bc4c5baaf4e05

---


# AEM en tant que SDK de service cloud {#aem-as-a-cloud-service-sdk}

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