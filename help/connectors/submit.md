---
title: Envoi d’un connecteur AEM
description: Envoi d’un connecteur AEM
exl-id: 9be1f00e-3666-411c-9001-c047e90b6ee5
source-git-commit: eb6aa8741a07e14727b4e74df66b9643936e9231
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 97%

---

Envoi d’un connecteur AEM
===========================

Les informations fournies ci-dessous sont utiles pour l’envoi des connecteurs AEM. Elles doivent être lues conjointement avec les articles sur l’[implémentation](implement.md) et la [maintenance](maintain.md) des connecteurs.

Les connecteurs AEM sont répertoriés dans [Adobe Exchange](https://partners.adobe.com/exchangeprogram/experiencecloud).

Dans les solutions AEM précédentes, Package Manager était utilisé pour installer des connecteurs sur diverses instances AEM. Toutefois, avec AEM as a Cloud Service, les connecteurs sont déployés pendant le processus de CI/CD dans Cloud Manager. Pour que les connecteurs soient déployés, ils doivent être référencés dans le fichier pom.xml du projet Maven.

Il existe différentes options pour inclure les packages dans un projet :

1. Référentiel public du partenaire : un partenaire héberge le package de contenu dans un référentiel expert accessible au public.
1. Référentiel protégé par mot de passe du partenaire : un partenaire héberge le package de contenu dans un référentiel Maven protégé par mot de passe. Voir Référentiels Maven protégés par mot de passe pour obtenir des instructions.
1. Artefact assemblé : dans ce cas, le package de connecteur est inclus localement dans le projet expert du client.

Où qu’ils soient hébergés, les packages doivent être référencés en tant que dépendances dans le fichier pom.xml, comme indiqué par le fournisseur.

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

Si le partenaire logiciel héberge le connecteur sur un référentiel Maven accessible sur Internet (tel que Cloud Manager accessible), ce partenaire doit fournir la configuration du référentiel où le fichier pom.xml peut être placé, de sorte que les dépendances du connecteur (ci-dessus) puissent être résolues au moment de la création (localement et par Cloud Manager).

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

Si le partenaire logiciel choisit de distribuer le connecteur en tant que fichiers téléchargeables, le partenaire doit alors fournir des instructions sur la manière dont les fichiers peuvent être déployés dans un référentiel Maven du système de fichiers local qui doit être archivé dans Git dans le cadre du projet AEM, afin que Cloud Manager puisse résoudre ces dépendances.
