---
title: Envoi d’un connecteur AEM
description: Découvrez comment référencer et déployer correctement les connecteurs as a Cloud Service Adobe Experience Manager (AEM).
exl-id: 9be1f00e-3666-411c-9001-c047e90b6ee5
feature: Operations
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 32%

---

# Envoi d’un connecteur AEM

Les informations fournies ci-dessous sont utiles pour l’envoi de connecteurs Adobe Experience Manager (AEM) et doivent être lues avec des articles sur l’ [implémentation](implement.md) et la [&#x200B; maintenance](maintain.md) des connecteurs.

Les connecteurs AEM sont répertoriés dans [Adobe Exchange](https://partners.adobe.com/technologyprogram/experiencecloud.html).

Dans les solutions AEM précédentes, le [Gestionnaire de packages](/help/implementing/developing/tools/package-manager.md) était utilisé pour installer des connecteurs sur diverses instances AEM. Toutefois, avec AEM as a Cloud Service, les connecteurs sont déployés pendant le processus de CI/CD dans Cloud Manager. Pour que les connecteurs soient déployés, ils doivent être référencés dans le fichier pom.xml du projet Maven.

Il existe différentes options pour inclure les packages dans un projet :

1. Référentiel public du partenaire : un partenaire héberge le package de contenu dans un référentiel expert accessible au public.
1. Référentiel protégé par mot de passe du partenaire : un partenaire héberge le module de contenu dans un référentiel Maven protégé par mot de passe. Voir [Référentiels Maven protégés par mot de passe](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/setting-up-project.html?lang=fr#password-protected-maven-repositories) pour obtenir des instructions.
1. Artefact assemblé : dans ce cas, le package de connecteur est inclus localement dans le projet expert du client.

Où qu’ils soient hébergés, les modules doivent être référencés en tant que dépendances dans le fichier pom.xml, tel qu’il est fourni par le fournisseur.

```xml
<!-- UberJAR Dependency to be added to the project's Reactor pom.xml -->
<dependency>
  <groupId>com.partnername</groupId>
  <artifactId>my-artifact</artifactId>
  <version>V123</version> <!-- use the latest! -->
  <scope>provided</scope>
  <classifier>my_classifier</classifier>
</dependency>
```

Si le partenaire logiciel héberge le connecteur sur un référentiel Maven accessible sur Internet (tel que Cloud Manager accessible), le partenaire doit fournir la configuration du référentiel où le `pom.xml` peut être placé. Cela est dû au fait que les dépendances des connecteurs (ci-dessus) peuvent être résolues au moment de la création, à la fois localement et par Cloud Manager.

```xml
<repository>
    <id>the-repository</id>
    <name>The Repository Where the Connector is Hosted</name>
    <url>https://repo.partnername.com/repositories/aem_connector_repo</url>
    <releases>
        <enabled>true</enabled>
        <updatePolicy>never</updatePolicy>
    </releases>
    <snapshots>
        <enabled>false</enabled>
    </snapshots>
</repository>
```

Si le partenaire logiciel choisit de distribuer le connecteur en tant que fichiers téléchargeables, le partenaire doit alors fournir des instructions. L’instruction doit décrire comment les fichiers peuvent être déployés dans un référentiel Maven de système de fichiers local qui doit être archivé dans Git dans le cadre du projet AEM. Cela permet à Cloud Manager de résoudre ces dépendances.
