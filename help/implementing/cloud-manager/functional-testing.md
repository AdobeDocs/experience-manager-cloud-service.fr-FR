---
title: Tests fonctionnels
description: Découvrez les trois différents types de tests fonctionnels intégrés au processus de déploiement as a Cloud Service AEM pour garantir la qualité et la fiabilité de votre code.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: a936f056685f2233a272b4b3105d845f832d143c
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 20%

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

Pour tous les tests fonctionnels, les résultats détaillés des tests peuvent être téléchargés en tant que `.zip` en utilisant la variable **Journal de version de téléchargement** dans l’écran d’aperçu de la version, dans le cadre de la [processus de déploiement.](/help/implementing/cloud-manager/deploy-code.md)

Ces journaux n’incluent pas les journaux du processus d’exécution AEM réel. Pour accéder à ces journaux, reportez-vous au document . [Accès aux journaux et leur gestion](/help/implementing/cloud-manager/manage-logs.md) pour plus d’informations.

Les tests fonctionnels du produit et les exemples de tests fonctionnels personnalisés sont basés sur la variable [AEM des clients de test.](https://github.com/adobe/aem-testing-clients)

## Tests fonctionnels du produit {#product-functional-testing}

Les tests fonctionnels du produit sont un ensemble de tests d’intégration HTTP (IT) stables des fonctionnalités de base d’AEM telles que les tâches de création et de réplication. Ces tests sont gérés par Adobe et sont destinés à empêcher le déploiement de modifications du code d’application personnalisé s’il rompt les fonctionnalités de base.

Les tests fonctionnels du produit s’exécutent automatiquement chaque fois que vous déployez du nouveau code dans Cloud Manager et ne peuvent pas être ignorés.

Les tests fonctionnels du produit sont conservés en tant que projet open source. Reportez-vous à la section [tests fonctionnels du produit](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) dans GitHub pour plus d’informations.

## Tests fonctionnels personnalisés {#custom-functional-testing}

Bien que les tests fonctionnels du produit soient définis par Adobe, vous pouvez rédiger vos propres tests de qualité pour votre propre application. Cela sera exécuté en tant que test fonctionnel personnalisé dans le cadre du pipeline de production pour garantir la qualité de votre application.

Les tests fonctionnels personnalisés sont exécutés à la fois pour les déploiements de code personnalisé et les mises à niveau push, ce qui rend particulièrement important la rédaction de bons tests fonctionnels qui empêchent AEM changements de code d’enfreindre le code de votre application. L’étape de test fonctionnel personnalisé est toujours présente et ne peut pas être ignorée.

### Écriture de tests fonctionnels personnalisés {#writing-functional-tests}

Les mêmes outils que ceux utilisés par Adobe pour rédiger des tests fonctionnels de produit peuvent être utilisés pour rédiger vos tests fonctionnels personnalisés. Utilisez la variable [tests fonctionnels du produit](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) dans GitHub comme exemple de la manière d’écrire vos tests.

Le code du test fonctionnel personnalisé est du code Java situé dans la variable `it.tests` du projet. Il doit produire un seul fichier JAR avec tous les tests fonctionnels. Si la version génère plusieurs fichiers JAR de test, le fichier JAR sélectionné est non déterministe. S’il ne génère aucun fichier JAR de test, l’étape de test est effectuée par défaut. [Voir AEM archétype de projet](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) pour des exemples de tests.

Les tests sont exécutés sur l’infrastructure de test gérée par l’Adobe, y compris au moins deux instances d’auteur, deux instances de publication et une configuration de Dispatcher. Cela signifie que vos tests fonctionnels personnalisés s’exécutent sur l’ensemble de la pile AEM.

Les tests fonctionnels personnalisés doivent être mis en package sous la forme d’un fichier JAR distinct généré par la même version de Maven que les artefacts à déployer sur AEM. En règle générale, il s’agit d’un module Maven distinct. Le fichier JAR obtenu doit contenir toutes les dépendances requises. Il est généralement créé à l’aide de la variable `maven-assembly-plugin` en utilisant la variable `jar-with-dependencies` descripteur.

En outre, le fichier JAR doit avoir la variable `Cloud-Manager-TestType` L’en-tête du manifeste est défini sur `integration-test`.

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

>[!TIP]
>
>[Regarder cette vidéo](https://www.youtube.com/watch?v=yJX6r3xRLHU) sur la manière dont vous pouvez utiliser des tests fonctionnels personnalisés pour améliorer votre confiance dans vos pipelines CI/CD.

## Test d’interface utilisateur personnalisé {#custom-ui-testing}

Les tests d’interface utilisateur personnalisés sont une fonctionnalité facultative qui vous permet de créer et d’exécuter automatiquement des tests d’interface utilisateur pour vos applications. Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basé sur Selenium).

Reportez-vous au document [Tests de l’interface utilisateur personnalisée](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) pour plus d’informations.

## Exécution locale du test {#local-test-execution}

Les classes de test étant des tests JUnit, elles peuvent être exécutées à partir d’IDE Java standard tels qu’Eclipse, IntelliJ, NetBeans, etc. Les tests fonctionnels de produit et les tests fonctionnels personnalisés étant basés sur la même technologie, les deux peuvent être exécutés localement en copiant les tests de produit dans vos tests personnalisés.

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
