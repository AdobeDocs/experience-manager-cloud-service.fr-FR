---
title: Tests fonctionnels – Cloud Services
description: Tests fonctionnels – Cloud Services
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 006fd74a9c4f4d5321bb3d0b35b5c9d49def7bc4
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 55%

---

# Tests fonctionnels {#functional-testing}


>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Tests fonctionnels"
>abstract="Les tests fonctionnels sont classés en trois types : Tests fonctionnels de produit, tests fonctionnels personnalisés et tests IU personnalisés"

Les tests fonctionnels sont classés en trois types :


* Tests fonctionnels du produit
* Tests fonctionnels personnalisés
* Test d’interface utilisateur personnalisé

## Tests fonctionnels du produit {#product-functional-testing}

Les tests fonctionnels du produit forment un ensemble de tests d’intégration HTTP stables qui s’articulent autour de fonctionnalités de base d’AEM (par exemple, la création et la réplication) et qui empêchent le déploiement de modifications du code de l’application par les clients s’il ne respecte pas ces fonctionnalités de base.

Les tests fonctionnels de produit s’exécutent automatiquement lorsqu’un client déploie un nouveau code dans Cloud Manager et ils ne peuvent pas être ignorés.

Référez-vous à [Tests fonctionnels du produit](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) pour accéder à des exemples de tests.

## Tests fonctionnels personnalisés {#custom-functional-testing}

L’étape des tests fonctionnels personnalisés du pipeline est toujours présente et ne peut pas être ignorée.

Cependant, si aucun fichier JAR de test n’est généré par la compilation, le test réussit par défaut.

>[!NOTE]
>Le bouton **Télécharger le journal** permet d’accéder à un fichier ZIP contenant les journaux du formulaire détaillé d’exécution du test. Ces journaux ne contiennent pas les journaux du processus d’exécution AEM proprement dit. Vous pouvez y accéder à l’aide de la fonctionnalité de téléchargement standard ou d’affichage des dernières lignes des journaux. Pour plus d’informations, reportez-vous à [Accès et gestion des journaux](/help/implementing/cloud-manager/manage-logs.md).

## Test d’interface utilisateur personnalisé {#custom-ui-testing}

AEM fournit à ses clients une suite intégrée de portes de qualité Cloud Manager pour assurer des mises à jour régulières de leurs applications. En particulier, les passerelles de test informatique permettent déjà aux clients de créer et d&#39;automatiser leurs propres tests qui utilisent des API AEM.

La fonction de test de l&#39;interface utilisateur personnalisée est une fonction en option [Opt-in client](#customer-opt-in) qui permet à nos clients de créer et d&#39;exécuter automatiquement des tests d&#39;interface utilisateur pour leurs applications. Les tests de l’interface utilisateur sont des tests basés sur Selenium placés dans une image Docker afin de permettre un large choix de langues et de cadres (tels que Java et Maven, Node et WebDriver.io, ou tout autre cadre et technologie basé sur Selenium). Vous pouvez en savoir plus sur la création de l’interface utilisateur et la création de tests d’interface utilisateur à partir de cet emplacement. De plus, un projet de tests d&#39;interface utilisateur peut être facilement généré à l&#39;aide de l&#39;archétype de projet AEM.

Les clients peuvent créer (via GIT) des tests personnalisés et des suites de tests pour l’interface utilisateur. Le test de l’interface utilisateur sera exécuté dans le cadre d’une porte d’entrée de qualité spécifique pour chaque pipeline de Cloud Manager, avec leurs informations d’étape et de commentaire spécifiques. Les tests d’interface utilisateur, y compris la régression et les nouvelles fonctionnalités, permettront de détecter les erreurs et de les signaler dans le contexte du client.

Les tests de l’interface utilisateur client s’exécutent automatiquement sur le canal Production, sous l’étape &quot;Tests personnalisés de l’interface utilisateur&quot;.

Contrairement aux tests fonctionnels personnalisés qui sont des tests HTTP écrits en java, les tests de l&#39;interface utilisateur peuvent être une image docker avec des tests écrits dans n&#39;importe quelle langue, à condition qu&#39;ils respectent les conventions définies dans [Création de tests d&#39;interface utilisateur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/ui-testing.html?lang=en#building-ui-tests).

>[!NOTE]
>Il est recommandé de suivre la structure et la langue *(js et wdio)* qui sont fournies à titre pratique dans l&#39;[AEM Archétype du projet ](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/ui.tests) comme point de départ.

### Inscription du client {#customer-opt-in}

Pour que leurs tests d&#39;interface utilisateur soient créés et exécutés, les clients doivent &quot;s&#39;inscrire&quot; en ajoutant un fichier à leur référentiel de code, sous le sous-module maven pour les tests d&#39;interface utilisateur (en regard du fichier pom.xml du sous-module tests d&#39;interface utilisateur) et s&#39;assurer que ce fichier est à la racine du fichier `tar.gz` créé.

*Nom du fichier*: `testing.properties`

*Sommaire*: `one line: ui-tests.version=1`

Si ce n&#39;est pas le cas dans le fichier `tar.gz` créé, la création et les exécutions des tests de l&#39;interface utilisateur sont ignorées.

>[!NOTE]
>Les oléoducs de production créés avant le 10 février 2021 devront être mis à jour afin d’utiliser les tests d’interface utilisateur décrits dans cette section. Cela signifie essentiellement que l’utilisateur doit modifier le pipeline de production et cliquer sur **Enregistrer** dans l’interface utilisateur même si aucune modification n’a été apportée.
>Consultez [Configuration de votre pipeline CI-CD](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=fr#using-cloud-manager) pour en savoir plus sur la configuration du pipeline.

### Écriture de tests fonctionnels {#writing-functional-tests}

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

Dans ce fichier JAR, les noms de classe des tests à exécuter doivent se terminer par IT.

Par exemple, une classe nommée `com.myco.tests.aem.ExampleIT` sera exécutée, mais pas une classe nommée `com.myco.tests.aem.ExampleTest`.

Les classes de test doivent être des tests JUnit normaux. L’infrastructure de test est conçue et configurée pour être compatible avec les conventions utilisées par la bibliothèque de tests aem-testing-clients. Les développeurs sont vivement encouragés à utiliser cette bibliothèque et à suivre les bonnes pratiques en vigueur. Pour plus d’informations, voir [Lien Git](https://github.com/adobe/aem-testing-clients).

### Exécution locale du test {#local-test-execution}

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
