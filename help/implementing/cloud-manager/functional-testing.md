---
title: Tests fonctionnels
description: Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement as a Cloud Service AEM pour garantir la qualité et la fiabilité de votre code.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 15de47e28e804fd84434d5e8e5d2fe8fe6797241
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 34%

---


# Tests fonctionnels {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Tests fonctionnels"
>abstract="Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement as a Cloud Service AEM pour garantir la qualité et la fiabilité de votre code."

Découvrez les trois différents types de tests fonctionnels intégrés au [AEM processus de déploiement as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md) pour garantir la qualité et la fiabilité de votre code.

## Présentation {#overview}

Il existe trois types différents de tests fonctionnels dans AEM as a Cloud Service.

* [Tests fonctionnels du produit](#product-functional-testing)
* [Tests fonctionnels personnalisés](#custom-functional-testing)
* [Test d’interface utilisateur personnalisé](#custom-ui-testing)

Pour tous les tests fonctionnels, les résultats détaillés des tests peuvent être téléchargés en tant que `.zip` en utilisant la variable **Journal de version de téléchargement** dans l’écran d’aperçu de la version, dans le cadre de la [processus de déploiement.](/help/implementing/cloud-manager/deploy-code.md) Ces journaux n’incluent pas les journaux du processus d’exécution AEM réel. Pour accéder à ces journaux, reportez-vous au document . [Accès aux journaux et leur gestion](/help/implementing/cloud-manager/manage-logs.md) pour plus d’informations.

## Tests fonctionnels du produit {#product-functional-testing}

Les tests fonctionnels du produit sont un ensemble de tests d’intégration HTTP (IT) stables des fonctionnalités de base d’AEM telles que les tâches de création et de réplication. Ces tests empêchent le déploiement des modifications du code d’application personnalisé par les clients s’il rompt les fonctionnalités de base.

Les tests fonctionnels du produit s’exécutent automatiquement chaque fois que vous déployez du nouveau code dans Cloud Manager et ne peuvent pas être ignorés.

Reportez-vous à la section [tests fonctionnels du produit](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) dans GitHub pour des exemples de tests.

## Tests fonctionnels personnalisés {#custom-functional-testing}

L’étape de test fonctionnel personnalisé du pipeline est toujours présente et ne peut pas être ignorée.

Le build doit produire zéro ou un fichier JAR de test. S’il ne génère aucun fichier JAR de test, l’étape de test est effectuée par défaut. Si le build génère plusieurs fichiers JAR de test, le fichier JAR sélectionné est non déterministe.

### Écriture de tests fonctionnels {#writing-functional-tests}

Les tests fonctionnels personnalisés doivent être mis en package sous la forme d’un fichier JAR distinct généré par la même version de Maven que les artefacts à déployer sur AEM. En règle générale, il s’agit d’un module Maven distinct. Le fichier JAR obtenu doit contenir toutes les dépendances requises. Il est généralement créé à l’aide de la variable `maven-assembly-plugin` en utilisant la variable `jar-with-dependencies` descripteur.

En outre, le fichier JAR doit avoir la variable `Cloud-Manager-TestType` L’en-tête du manifeste est défini sur `integration-test`. Il est prévu que d’autres valeurs d’en-tête soient prises en charge à l’avenir.

Voici un exemple de configuration pour la variable `maven-assembly-plugin`.

```java
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
```

Dans ce fichier JAR, les noms de classe des tests à exécuter doivent se terminer par `IT`.

Par exemple, une classe nommée `com.myco.tests.aem.it.ExampleIT` sera exécutée, mais pas une classe nommée `com.myco.tests.aem.it.ExampleTest`.

De plus, pour exclure le code test de la vérification de la couverture de l’analyse du code, le code test doit se trouver sous un package nommé `it` (le filtre d’exclusion de la couverture est `**/it/**/*.java`).

Les classes de test doivent être des tests JUnit normaux. L’infrastructure de test est conçue et configurée pour être compatible avec les conventions utilisées par la variable `aem-testing-clients` bibliothèque de test. Les développeurs sont vivement encouragés à utiliser cette bibliothèque et à suivre les bonnes pratiques en vigueur.

Reportez-vous à la section [`aem-testing-clients` Référentiel GitHub](https://github.com/adobe/aem-testing-clients) pour plus d’informations.

## Test d’interface utilisateur personnalisé {#custom-ui-testing}

Les tests d’interface utilisateur personnalisés sont une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications. Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basé sur Selenium).

Reportez-vous au document [Tests de l’interface utilisateur personnalisée](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) pour plus d’informations.

## Exécution locale du test {#local-test-execution}

Les classes de test étant des tests JUnit, elles peuvent être exécutées à partir d’IDE Java standard tels qu’Eclipse, IntelliJ, NetBeans, etc.

Toutefois, lors de l’exécution de ces tests, il sera nécessaire de définir diverses propriétés système attendues par la variable `aem-testing-clients` (et la bibliothèque Sling Testing Clients sous-jacente).

Les propriétés du système sont les suivantes.

* `sling.it.instances - should be set to 2`
* `sling.it.instance.url.1 - should be set to the author URL, for example, http://localhost:4502`
* `sling.it.instance.runmode.1 - should be set to author`
* `sling.it.instance.adminUser.1 - should be set to the author admin user, e.g. admin`
* `sling.it.instance.adminPassword.1 - should be set to the author admin password`
* `sling.it.instance.url.2 - should be set to the author URL, for example, http://localhost:4503`
* `sling.it.instance.runmode.2 - should be set to publish`
* `sling.it.instance.adminUser.2 - should be set to the publish admin user, for example, admin`
* `sling.it.instance.adminPassword.2 - should be set to the publish admin password`
