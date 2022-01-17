---
title: Tests fonctionnels – Cloud Services
description: Tests fonctionnels – Cloud Services
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 02db915e114c2af8329eaddbb868045944a3574d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Tests fonctionnels {#functional-testing}


>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Tests fonctionnels"
>abstract="Les tests fonctionnels sont classés en trois types : tests fonctionnels du produit, tests fonctionnels personnalisés et tests de l’interface utilisateur personnalisés"

Les tests fonctionnels sont classés en trois types :


* [Tests fonctionnels du produit](#product-functional-testing)
* [Tests fonctionnels personnalisés](#custom-functional-testing)
* [Test d’interface utilisateur personnalisé](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing)

## Tests fonctionnels du produit {#product-functional-testing}

Les tests fonctionnels du produit forment un ensemble de tests d’intégration HTTP stables qui s’articulent autour de fonctionnalités de base d’AEM (par exemple, la création et la réplication) et qui empêchent le déploiement de modifications du code de l’application par les clients s’il ne respecte pas ces fonctionnalités de base.

Les tests fonctionnels de produit s’exécutent automatiquement lorsqu’un client déploie un nouveau code dans Cloud Manager et ils ne peuvent pas être ignorés.

Référez-vous à [Tests fonctionnels du produit](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) pour accéder à des exemples de tests.

## Tests fonctionnels personnalisés {#custom-functional-testing}

L’étape des tests fonctionnels personnalisés du pipeline est toujours présente et ne peut pas être ignorée.

La version doit produire zéro ou un fichier JAR de test. S’il ne génère aucun fichier JAR de test, l’étape de test est effectuée par défaut. Si la version génère plusieurs fichiers JAR de test, le fichier JAR sélectionné est non déterministe.

>[!NOTE]
>Le bouton **Télécharger le journal** permet d’accéder à un fichier ZIP contenant les journaux du formulaire détaillé d’exécution du test. Ces journaux ne contiennent pas les journaux du processus d’exécution AEM proprement dit. Vous pouvez y accéder à l’aide de la fonctionnalité de téléchargement standard ou d’affichage des dernières lignes des journaux. Pour plus d’informations, reportez-vous à [Accès et gestion des journaux](/help/implementing/cloud-manager/manage-logs.md).


## Écriture de tests fonctionnels {#writing-functional-tests}

Les tests fonctionnels écrits par le client doivent être placés dans un fichier JAR distinct produit par la même version de Maven que les artefacts à déployer dans AEM. En règle générale, il s’agit d’un module Maven distinct. Le fichier JAR obtenu doit contenir toutes les dépendances requises. Il est généralement créé avec le plug-in Assembly de Maven à l’aide du descripteur jar-with-dependencies.

En outre, l’en-tête de manifeste Cloud-Manager-TestType du fichier JAR doit être défini sur integration-test. Il est prévu que d’autres valeurs d’en-tête soient prises en charge à l’avenir. Voici un exemple de configuration pour le plug-in Assembly de Maven :

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

Par exemple, une classe nommée `com.myco.tests.aem.it.ExampleIT` est exécuté, mais une classe nommée `com.myco.tests.aem.it.ExampleTest` non.

De plus, pour exclure le code test de la vérification de la couverture de l’analyse du code, le code test doit se trouver sous un package nommé `it` (le filtre d’exclusion de la couverture est `**/it/**/*.java`).

Les classes de test doivent être des tests JUnit normaux. L’infrastructure de test est conçue et configurée pour être compatible avec les conventions utilisées par la bibliothèque de tests aem-testing-clients. Les développeurs sont vivement encouragés à utiliser cette bibliothèque et à suivre les bonnes pratiques en vigueur. Pour plus d’informations, voir [Lien Git](https://github.com/adobe/aem-testing-clients).

## Exécution locale du test {#local-test-execution}

Les classes de test étant des tests JUnit, elles peuvent être exécutées à partir d’IDE Java standard comme Eclipse, IntelliJ, NetBeans, etc.

Cependant, lors de l’exécution de ces tests, il est nécessaire de définir diverses propriétés système attendues par les clients de test AEM (et les clients de test Sling sous-jacents).

Les propriétés système sont les suivantes :

* `sling.it.instances - should be set to 2`
* `sling.it.instance.url.1 - should be set to the author URL, for example, http://localhost:4502`
* `sling.it.instance.runmode.1 - should be set to author`
* `sling.it.instance.adminUser.1 - should be set to the author admin user, e.g. admin`
* `sling.it.instance.adminPassword.1 - should be set to the author admin password`
* `sling.it.instance.url.2 - should be set to the author URL, for example, http://localhost:4503`
* `sling.it.instance.runmode.2 - should be set to publish`
* `sling.it.instance.adminUser.2 - should be set to the publish admin user, for example, admin`
* `sling.it.instance.adminPassword.2 - should be set to the publish admin password`
