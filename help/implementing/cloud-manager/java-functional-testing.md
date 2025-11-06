---
title: Tests fonctionnels Java &trade;
description: Découvrez comment écrire des tests fonctionnels Java &trade; pour AEM as a Cloud Service
exl-id: e014b8ad-ac9f-446c-bee8-adf05a6b4d70
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 77%

---


# Tests fonctionnels Java™

Découvrez comment écrire des tests fonctionnels Java™ pour AEM as a Cloud Service

## Prise en main des tests fonctionnels {#getting-started-functional-tests}

Lors de la création d’un référentiel de code dans Cloud Manager, un dossier `it.tests` est automatiquement créé avec des exemples de cas de test.

>[!NOTE]
>
>Si votre référentiel a été créé avant la création automatique des dossiers `it.tests` par Cloud Manager, vous pouvez également générer la dernière version en date à l’aide de l’[archétype de projet AEM](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/it.tests).

Une fois que vous disposez du contenu du dossier `it.tests`, vous pouvez l’utiliser comme base pour vos propres tests. Ensuite :

1. [Développez vos cas de test](#writing-functional-tests).
1. [Exécutez les tests localement](#local-test-execution).
1. Validez votre code dans le référentiel Cloud Manager et exécutez un pipeline Cloud Manager.

## Écriture de tests fonctionnels personnalisés {#writing-functional-tests}

Les mêmes outils que ceux utilisés par Adobe pour rédiger des tests fonctionnels de produit peuvent être utilisés pour rédiger vos tests fonctionnels personnalisés. Utilisez les [tests fonctionnels du produit](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) dans GitHub comme exemple de la manière d’écrire vos tests.

Le code du test fonctionnel personnalisé est du code Java™ dans le dossier `it.tests` de votre projet. Il doit produire un seul fichier JAR avec tous les tests fonctionnels. Si le build génère plusieurs fichiers JAR de test, le fichier JAR sélectionné est non déterministe. S’il ne génère aucun fichier JAR de test, l’étape de test est effectuée par défaut. Voir [Archétype de projet AEM](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) pour obtenir des exemples de tests.

Les tests sont exécutés sur l’infrastructure de test gérée par Adobe, comprenant au moins deux instances de création, deux instances de publication et une configuration de Dispatcher. Cette configuration signifie que vos tests fonctionnels personnalisés s’exécutent sur l’ensemble de la pile AEM.

### Structure des tests fonctionnels {#functional-tests-structure}

Les tests fonctionnels personnalisés par le client doivent être placés dans un fichier JAR distinct produit par la même version de Maven que les artefacts à déployer dans AEM. En règle générale, cette version est un module Maven distinct. Le fichier JAR obtenu doit contenir toutes les dépendances requises. Il est généralement créé avec le `maven-assembly-plugin` à l’aide du descripteur `jar-with-dependencies`.

En outre, l’en-tête de manifeste `Cloud-Manager-TestType` du fichier JAR doit être défini sur `integration-test`.

Ce qui suit est un exemple de configuration pour le `maven-assembly-plugin`.

```XML
<build>
    <plugins>
        <!-- Create self-contained jar with dependencies -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <version>3.1.0</version>
            <configuration>
                <descriptorRefs>
                    <descriptorRef>jar-with-dependencies</descriptorRef>
                </descriptorRefs>
                <archive>
                    <manifestEntries>
                        <Cloud-Manager-TestType>integration-test</Cloud-Manager-TestType>
                    </manifestEntries>
                </archive>
            </configuration>
            <executions>
                <execution>
                    <id>make-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```

Dans ce fichier JAR, les noms de classe des tests à exécuter doivent se terminer par `IT`.

Par exemple, une classe nommée `com.myco.tests.aem.it.ExampleIT` sera exécutée, mais pas une classe nommée `com.myco.tests.aem.it.ExampleTest`.

De plus, pour exclure le code test de la vérification de la couverture de l’analyse du code, le code test doit se trouver sous un package nommé `it` (le filtre d’exclusion de la couverture est `**/it/**/*.java`).

Les classes de test doivent être des tests JUnit normaux. L’infrastructure de test est conçue et configurée pour être compatible avec les conventions utilisées par la bibliothèque de tests `aem-testing-clients`. Les développeurs et développeuses sont encouragés à utiliser cette bibliothèque et à suivre les bonnes pratiques en vigueur.

Pour plus d’informations, voir le [`aem-testing-clients`référentiel GitHub ](https://github.com/adobe/aem-testing-clients).

>[!TIP]
>
>[Regardez cette vidéo](https://www.youtube.com/watch?v=yJX6r3xRLHU) sur la manière dont vous pouvez utiliser des tests fonctionnels personnalisés pour améliorer votre confiance dans vos pipelines CI/CD.

### Prérequis {#prerequisites}

1. Les tests dans Cloud Manager sont exécutés par une personne administratrice technique.

>[!NOTE]
>
>Pour exécuter les tests fonctionnels à partir de votre ordinateur local, créez un utilisateur ou une utilisatrice avec des autorisations de type administration afin d’obtenir le même comportement.

1. L’infrastructure en conteneur qui est prévue pour les tests fonctionnels est restreinte par les limites suivantes :

| Type | Valeur | Description |
|----------------------|-------|--------------------------------------------------------------------|
| Processeur | 0,5 | Quantité de temps réservé au processeur par exécution de test |
| Mémoire | 0,5 Go | Quantité de mémoire allouée au test, valeur en gibioctets |
| Délai d’expiration | 30 min | Délai au bout duquel le test s’arrête. |
| Durée recommandée | 15 min | Adobe recommande de n’écrire les tests que si leur durée n’est pas supérieure à cette durée. |

#### Dépendances

* aem-cloud-testing-clients :

Les modifications à venir de l’infrastructure en conteneur pour l’exécution des tests fonctionnels nécessitent la mise à jour de la bibliothèque [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) de vos tests fonctionnels personnalisés vers la version **1.2.1** ou ultérieure. Assurez-vous que la dépendance de votre fichier `it.tests/pom.xml` est mise à jour en conséquence.

```
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

>[!NOTE]
>
>Cette modification doit être effectuée avant le 6 avril 2024.
>Si la bibliothèque de dépendances n’est pas mise à jour, des échecs de pipeline peuvent se produire à l’étape « Tests fonctionnels personnalisés ».

### Exécution locale du test {#local-test-execution}

Avant d’activer les tests fonctionnels dans un pipeline Cloud Manager, il est recommandé d’exécuter les tests fonctionnels localement à l’aide du [SDK AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) ou d’une instance d’AEM as a Cloud Service réelle.

#### Exécution dans un IDE {#running-in-an-ide}

Les classes de test étant des tests JUnit, elles peuvent être exécutées à partir d’IDE Java ™ standard tels qu’Eclipse, IntelliJ et NetBeans. Les tests fonctionnels de produit et les tests fonctionnels personnalisés étant basés sur la même technologie, les deux peuvent être exécutés localement en copiant les tests de produit dans vos tests personnalisés.

Cependant, lors de l’exécution de ces tests, il est nécessaire de définir un ensemble de propriétés système attendues par la bibliothèque `aem-testing-clients` (et la clientèle de test Sling sous-jacente).

Les propriétés système sont les suivantes.

| Propriété | Description | Exemple |
|-------------------------------------|------------------------------------------------------------------|-------------------------|
| `sling.it.instances` | Le nombre d’instances pour correspondre au service cloud doit être défini sur `2`. | `2` |
| `sling.it.instance.url.1` | Définissez sur l’URL de création. | `http://localhost:4502` |
| `sling.it.instance.runmode.1` | Mode d’exécution de la première instance. Définissez sur `author`. | `author` |
| `sling.it.instance.adminUser.1` | Définissez sur l’utilisateur ou l’utilisatrice admin de création. | `admin` |
| `sling.it.instance.adminPassword.1` | Définissez sur le mot de passe de l’administrateur ou l’administratrice de création. |                         |
| `sling.it.instance.url.2` | défini sur l’URL de publication. | `http://localhost:4503` |
| `sling.it.instance.runmode.2` | Mode d’exécution de la deuxième instance. Définissez sur `publish`. | `publish` |
| `sling.it.instance.adminUser.2` | Définissez sur l’utilisateur ou l’utilisatrice admin de publication. | `admin` |
| `sling.it.instance.adminPassword.2` | Définissez sur le mot de passe de l’administrateur de publication. |                         |

#### Exécution de tous les tests à l’aide de Maven {#using-maven}

1. Ouvrez un conteneur et accédez au dossier `it.tests` dans votre référentiel

1. Exécutez la commande suivante fournissant les paramètres nécessaires pour démarrer les tests à l’aide de Maven.

```shell
mvn verify -Plocal \
    -Dit.author.url=https://author-<program-id>-<environment-id>.adobeaemcloud.com \
    -Dit.author.user=<user> \
    -Dit.author.password=<password> \
    -Dit.publish.url=https://publish-<program-id>-<environment-id>.adobeaemcloud.com \
    -Dit.publish.user=<user> \
    -Dit.publish.password=<password>
```
