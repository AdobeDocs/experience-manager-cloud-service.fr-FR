---
title: Envoi d’un connecteur AEM
description: Envoi d’un connecteur AEM
translation-type: tm+mt
source-git-commit: 629de3a9f55d2e4c52ef91c9e0bb5d439aebe84f

---


Envoi d’un connecteur AEM
===========================

Les informations fournies ci-dessous sont utiles pour l’envoi des connecteurs AEM. Elles doivent être lues conjointement avec les articles sur l’ [implémentation](implement.md) et la [maintenance](maintain.md) des connecteurs.

Les connecteurs AEM sont répertoriés dans [Adobe Exchange](https://marketing.adobe.com/resources/content/resources/en/exchange/marketplace.html).

Dans les solutions AEM précédentes, Package Manager était utilisé pour installer des connecteurs sur diverses instances AEM. Toutefois, avec AEM en tant que service Cloud, les connecteurs sont déployés pendant le processus de CI/CD dans Cloud Manager. Pour que les connecteurs soient déployés, les connecteurs doivent être référencés dans le fichier pom.xml du projet maven.

Il existe différentes options pour inclure les packages dans un projet :

1. Référentiel public du partenaire : un partenaire hébergerait le package de contenu dans un référentiel expert accessible au public
1. Artefact assemblé : dans ce cas, le module connecteur est inclus localement dans le projet expert du client.

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

Si le partenaire ISV héberge le connecteur sur un référentiel maven accessible sur Internet (tel que Cloud Manager accessible), le fichier ISV doit fournir la configuration du référentiel où le fichier pom.xml peut être placé, de sorte que les dépendances du connecteur (ci-dessus) puissent être résolues au moment de la création (localement et par Cloud Manager).

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

Si le partenaire ISV choisit de distribuer le connecteur en tant que fichiers téléchargeables, le fichier ISV doit alors fournir des instructions sur la manière dont les fichiers peuvent être déployés dans un référentiel maven du système de fichiers local qui doit être archivé dans Git dans le cadre du projet AEM, afin que Cloud Manager puisse résoudre ces dépendances.
