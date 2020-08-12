---
title: Présentation des résultats de test - Cloud Services
description: Présentation des résultats de test - Cloud Services
translation-type: tm+mt
source-git-commit: f878421950bac58702f9d4b418fbcc2dc3e397b2
workflow-type: tm+mt
source-wordcount: '1596'
ht-degree: 60%

---


# Présentation des résultats de test {#understand-test-results}

Les exécutions du pipeline Cloud Manager for Cloud Services prennent en charge l’exécution de tests sur l’environnement d’évaluation. Cela contraste avec les tests exécutés dans le cadre de l’étape Test de création et d’unité, qui sont réalisés hors ligne, sans aucun accès à un environnement AEM actif.

Il existe trois grandes catégories de tests pris en charge par Cloud Manager pour le gazoduc Cloud Services :

1. [Test de qualité du code](#code-quality-testing)
1. [Tests fonctionnels](#functional-testing)
1. [Test de l’audit du contenu](#content-audit-testing)

Ces tests peuvent être :

* Écrit par le client
* adobe écrit
* Proposé par Lighthouse depuis Google en tant qu&#39;outil open source

   >[!NOTE]
   > Les tests écrits par le client et les tests écrits par Adobe sont exécutés dans une infrastructure conteneurisée conçue pour exécuter ces types de tests.


## Test de qualité du code {#code-quality-testing}

Dans le cadre du pipeline, le code source est analysé afin de garantir que les déploiements respectent certains critères de qualité. Actuellement, cette analyse est implémentée par une combinaison de SonarQube et d’examens au niveau du package de contenu à l’aide de OakPAL. Il existe plus de 100 règles combinant des règles Java génériques et des règles spécifiques à AEM. Le tableau suivant résume l’évaluation des critères de test :

| Nom | Définition | Catégorie | Seuil d’échec |
|--- |--- |--- |--- |
| Cote de sécurité | A = 0 vulnérabilité <br/>B = au moins 1 vulnérabilité mineure<br/> C = au moins 1 vulnérabilité majeure <br/>D = au moins 1 vulnérabilité critique <br/>E = au moins 1 vulnérabilité de blocage | Critique | &lt; B |
| Cote de fiabilité | A = 0 bogue <br/>B = au moins 1 bogue mineur <br/>C = au moins 1 bogue majeur <br/>D = au moins 1 bogue critique E = au moins 1 bogue bloqueur | Important | &lt; C |
| Évaluation de maintenabilité | Le coût de correction en suspens pour les smells du code est : <br/><ul><li>&lt;=5% du temps qui s’est déjà écoulé dans l’application, la note est A </li><li>entre 6 et 10 % la note est B </li><li>entre 11 et 20 % la note est C </li><li>entre 21 et 50 % la note est D</li><li>tout ce qui dépasse 50 % est E</li></ul> | Important | &lt; A |
| Couverture | Combinaison de couverture de ligne de tests unitaires et de couverture de condition utilisant cette formule : <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`<br/> où : CT = conditions qui ont été évaluées comme « vrai » au moins une fois lors de l’exécution de tests unitaires <br/>CF = conditions qui ont été évaluées comme « faux » au moins une fois <br/>LC = lignes couvertes = lines_ to_ cover - uncover_ lines <br/><br/> B = nombre total de conditions <br/>EL = nombre total de lignes exécutables (lines_to_cover) | Important | &lt; 50% |
| Tests unitaires ignorés | Nombre de tests unitaires ignorés. | Infos | > 1 |
| Problèmes en cours | Types de problèmes généraux - Vulnérabilités, bogues et smells de code | Infos | > 0 |
| Lignes dupliquées | Nombre de lignes impliquées dans des blocs dupliqués. <br/>Pour qu’un bloc de code soit considéré comme dupliqué : <br/><ul><li>**Projets non Java :**</li><li>Il doit y avoir au moins 100 jetons successifs et dupliqués.</li><li>Ces jetons doivent être répartis au moins sur : </li><li>30 lignes de code pour COBOL </li><li>20 lignes de code pour ABAP </li><li>10 lignes de code pour d’autres langages</li><li>**Projets Java :**</li><li> Il devrait y avoir au moins 10 instructions successives et dupliquées, quel que soit le nombre de jetons et de lignes.</li></ul> <br/>Les différences dans la mise en retrait ainsi que dans les littéraux de chaîne sont ignorées lors de la détection des doublons. | Infos | > 1% |
| Compatibilité Cloud Service | Nombre de problèmes de compatibilité Cloud Service identifiés. | Infos | > 0 |


>[!NOTE]
>
>Pour des définitions plus détaillées, consultez [Définitions des mesures](https://docs.sonarqube.org/display/SONAR/Metric+Definitions).

Vous pouvez télécharger la liste des règles ici : [code-quality-rules.xlsx](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest.xlsx).

>[!NOTE]
>
>Pour en savoir plus sur les règles de qualité du code personnalisé exécutées par [!UICONTROL Cloud Manager], reportez-vous à la section [Règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md).

### Traitement des faux positifs {#dealing-with-false-positives}

Le processus d’analyse de qualité n’est pas parfait et identifiera parfois de manière incorrecte des problèmes qui ne sont pas réellement problématiques. On parle alors de « faux positif ».

Dans ce cas, une annotation Java `@SuppressWarnings` standard spécifiant l’ID de règle comme attribut d’annotation peut être inscrite dans le code source. Par exemple, la règle SonarQube permettant de détecter les mots de passe codés en dur peut être agressive sur la façon dont un mot de passe codé en dur est identifié.

Pour prendre un exemple spécifique, ce code serait assez courant dans un projet AEM qui comporte un code pour se connecter à un service externe :

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube lèvera alors une vulnérabilité de bloqueur. Après avoir examiné le code, vous identifiez qu’il ne s’agit pas d’une vulnérabilité et pouvez l’annoter avec l’identifiant de règle approprié.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

En revanche, si le code était le suivant :

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

La bonne solution consiste alors à supprimer le mot de passe codé en dur.

>[!NOTE]
>
>Bien qu’il soit préférable de rendre l’annotation `@SuppressWarnings` aussi précise que possible, c’est-à-dire de n’annoter que l’énoncé ou le bloc qui cause le problème, il est tout de même possible de le faire à un niveau qui se rapporte à la classe.

>[!NOTE]
>Bien qu&#39;il n&#39;y ait pas d&#39;étape de test de sécurité explicite, des règles de qualité du code liées à la sécurité sont toujours évaluées au cours de l&#39;étape de qualité du code. Refer to [Security Overview for AEM as a Cloud Service](/help/security/cloud-service-security-overview.md) for more details.

## Tests fonctionnels {#functional-testing}

Les tests fonctionnels sont classés en deux types :

* Test fonctionnel du produit
* Tests fonctionnels personnalisés

### Test fonctionnel du produit {#product-functional-testing}

Les tests fonctionnels du produit sont un ensemble de tests d’intégration HTTP (IT) stables qui s’articulent autour des fonctionnalités de base des AEM (par exemple, la création et la réplication) et qui empêchent le déploiement des modifications du code de l’application par les clients s’il rompt cette fonctionnalité de base.

Elles s’exécutent automatiquement chaque fois qu’un client déploie un nouveau code dans Cloud Manager.

### Tests fonctionnels personnalisés {#custom-functional-testing}

L’étape des tests fonctionnels personnalisés du pipeline est toujours présente et ne peut pas être ignorée.

Cependant, si aucun fichier JAR de test n’est généré par la compilation, le test réussit par défaut.

>[!NOTE]
>le bouton **Télécharger le journal** permet d’accéder à un fichier ZIP contenant les journaux du formulaire détaillé d’exécution du test. Ces journaux ne contiennent pas les journaux du processus d’exécution AEM proprement dit. Vous pouvez y accéder à l’aide de la fonctionnalité de téléchargement standard ou d’affichage des dernières lignes des journaux. Refer to [Accessing and Managing Logs](/help/implementing/cloud-manager/manage-logs.md) for more details.


#### Écriture de tests fonctionnels {#writing-functional-tests}

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

## Test de l’audit du contenu {#content-audit-testing}

L’audit de contenu est une fonctionnalité disponible dans les oléoducs de production de sites Cloud Manager optimisés par Lighthouse, un outil open source de Google. Cette fonctionnalité est activée dans tous les pipelines de production de Cloud Manager.

Il valide le processus de déploiement et permet de s’assurer que les modifications sont déployées :

1. Respectez les normes de base en matière de performances, d&#39;accessibilité, de bonnes pratiques, d&#39;optimisation du référencement (optimisation pour les moteurs de recherche) et de PWA (application Web progressive).

1. N’incluez pas de régressions dans ces dimensions.

L’audit de contenu dans Cloud Manager garantit que l’expérience numérique des utilisateurs finaux sur le site peut être maintenue aux normes les plus élevées. Les résultats sont informatifs et permettent à l’utilisateur de voir les scores et le changement entre les scores actuel et précédent. Cette connaissance est utile pour déterminer si une régression est introduite avec le déploiement actuel.

### Présentation des résultats de l&#39;audit du contenu {#understanding-content-audit-results}

L’audit de contenu fournit des résultats de test détaillés et agrégats au niveau de la page via la page d’exécution du pipeline de production.

* Les mesures au niveau de l’Agrégat mesurent le score moyen sur les pages qui ont été vérifiées.
* Des scores individuels au niveau de la page sont également disponibles par le biais d’une analyse approfondie.
* Des détails sur les notes sont disponibles pour voir quels sont les résultats des tests individuels, ainsi que des conseils sur la façon de résoudre les problèmes qui ont été identifiés lors de la vérification du contenu.
* Un historique des résultats du test est conservé dans Cloud Manager afin que les clients puissent voir si les modifications introduites dans l’exécution du pipeline incluent des régressions par rapport à l’exécution précédente.

#### Scores d’Agrégat {#aggregate-scores}

Il existe un score de niveau agrégat pour chaque type de test (performances, accessibilité, optimisation du référencement, bonnes pratiques et PWA).

Le score de niveau agrégat correspond au score moyen des pages incluses dans l’exécution. Le changement au niveau de l’agrégat représente le score moyen des pages de l’exécution en cours par rapport à la moyenne des scores de l’exécution précédente, même si la collection de pages configurées pour être incluses a été modifiée entre les exécutions.

La mesure Valeur de changement peut être l’une des mesures suivantes :

* **Valeur** positive : les pages ont été améliorées sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Valeur** négative : les pages ont régressé sur le test sélectionné depuis la dernière exécution du pipeline de production.

* **Aucune modification** : les pages ont obtenu le même score depuis la dernière exécution du pipeline de production.

* **S/O** - aucun score précédent n’était disponible pour la comparaison

   ![](assets/content-audit-test1.png)

#### Scores au niveau de la page {#page-level-scores}

En analysant n’importe lequel des tests, vous obtenez des scores de niveau de page plus détaillés. L’utilisateur pourra voir comment les pages individuelles ont obtenu un score pour le test spécifique, ainsi que la variation par rapport à la précédente exécution du test.

Un clic sur les détails d&#39;une page donnée fournit des informations sur les éléments de la page qui ont été évalués et des conseils pour résoudre les problèmes si des opportunités d&#39;amélioration sont détectées. Les détails des tests et les conseils associés sont fournis par Google Lighthouse.

![](assets/page-level-scores.png)

## Exécution locale du test {#local-test-execution}

Les classes de test étant des tests JUnit, elles peuvent être exécutées à partir d’IDE Java standard comme Eclipse, IntelliJ, NetBeans, etc.

Cependant, lors de l’exécution de ces tests, il est nécessaire de définir diverses propriétés système attendues par aem-testing-clients (et les clients de test Sling sous-jacents).

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

