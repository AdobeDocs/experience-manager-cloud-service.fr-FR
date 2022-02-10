---
title: Test de qualité du code
description: Découvrez le fonctionnement du test de qualité du code des pipelines et comment il peut améliorer la qualité de vos déploiements.
exl-id: e2981be9-fb14-451c-ad1e-97c487e6dc46
source-git-commit: ca3c1f255b8441a8d376a55a5353d58848384b8b
workflow-type: tm+mt
source-wordcount: '1106'
ht-degree: 20%

---

# Test de qualité du code {#code-quality-testing}

Découvrez le fonctionnement du test de qualité du code des pipelines et comment il peut améliorer la qualité de vos déploiements.

>[!CONTEXTUALHELP]
>
>id="aemcloud_nonbpa_codequalitytests"
>title="Code Quality Testing"
>abstract="Code quality testing evaluates your application code based on a set of quality rules. It is the primary purpose of a code-quality only pipeline and is executed immediately following the build step in all production and non-production pipelines."

## Présentation {#introduction}

Le test de qualité du code évalue votre code d’application en fonction d’un ensemble de règles de qualité. Il s’agit de l’objectif Principal d’un pipeline de qualité de code uniquement et qui est exécuté immédiatement après l’étape de création dans tous les pipelines de production et hors production.

Reportez-vous au document [Configuration de votre pipeline CI-CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour en savoir plus sur les différents types de pipelines.

## Règles de qualité du code {#understanding-code-quality-rules}

Le test de qualité du code analyse le code source pour s’assurer qu’il répond à certains critères de qualité. Cela est mis en oeuvre par une combinaison de SonarQube et d’examen au niveau du package de contenu à l’aide d’OakPAL. Il existe plus de 100 règles, combinant des règles Java génériques et des règles spécifiques à AEM. Certaines des règles spécifiques à l’AEM sont créées en fonction des bonnes pratiques d’AEM Engineering et sont appelées [règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md).

>[!NOTE]
Vous pouvez télécharger la liste complète des règles [avec ce lien.](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx)

### Classement à trois niveaux {#three-tiered-gate}

Les problèmes identifiés par le test de qualité du code sont affectés à l’une des trois catégories.

* **Critique** - Il s’agit de problèmes qui entraînent l’échec immédiat du pipeline.

* **Important** - Il s’agit de problèmes qui entraînent la suspension du pipeline. Un responsable de déploiement, un responsable de projet ou un propriétaire d’entreprise peuvent soit contourner les problèmes, auquel cas le pipeline continue, soit accepter les problèmes, auquel cas le pipeline s’arrête avec un échec.

* **Infos** - Il s’agit de problèmes qui sont fournis uniquement à titre d’information et qui n’ont aucun impact sur l’exécution du pipeline.

Les résultats de cette étape sont fournis sous forme de **notes**.

Le tableau suivant résume les notes et les seuils d’échec pour chacune des catégories critiques, importantes et d’informations.

| Nom | Définition | Catégorie | Seuil d’échec |
|--- |--- |--- |--- |
| Note de sécurité | A = Aucune vulnérabilité <br/>B = Au moins 1 vulnérabilité mineure<br/> C = Au moins 1 vulnérabilité majeure <br/>D = Au moins 1 vulnérabilité critique <br/>E = Au moins 1 vulnérabilité de bloqueur | Critique | &lt; B |
| Note de fiabilité | A = Aucun bogue <br/>B = Au moins 1 bogue mineur <br/>C = Au moins 1 bogue majeur <br/>D = Au moins 1 bogue critique<br>E = Au moins 1 bogue de blocage | Critique | &lt; D |
| Note de maintenabilité | Défini par le coût de correction en suspens pour le code sent comme un pourcentage du temps qui a déjà été consacré à l’application.<br/><ul><li>A = &lt;=5 %</li><li>B = 6-10 %</li><li>C = 11-20 %</li><li>D = 21-50 %</li><li>E = > 50 %</li></ul> | Important | &lt; A |
| Couverture | Défini par un mélange de couverture de ligne de test unitaire et de couverture de condition à l’aide de la formule : <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <ul><li>`CT` = Conditions qui ont été évaluées comme `true` au moins une fois lors de l’exécution de tests unitaires</li><li>`CF` = Conditions qui ont été évaluées comme `false` au moins une fois lors de l’exécution de tests unitaires</li><li>`LC` = Lignes couvertes = lines_to_cover - uncover_lines</li><li>`B` = nombre total de conditions</li><li>`EL` = nombre total de lignes exécutables (lines_to_cover)</li></ul> | Important | &lt; 50 % |
| Tests unitaires ignorés | Nombre de tests unitaires ignorés | Infos | > 1 |
| Problèmes en cours | Types de problèmes généraux – Vulnérabilités, bogues et smells de code | Infos | > 0 |
| Lignes dupliquées | Défini comme le nombre de lignes impliquées dans les blocs dupliqués. Un bloc de code est considéré comme dupliqué dans les conditions suivantes.<br>Projets non Java :<ul><li>Il doit y avoir au moins 100 jetons successifs et dupliqués.</li><li>Ces jetons doivent être répartis au moins sur : </li><li>30 lignes de code pour COBOL </li><li>20 lignes de code pour ABAP </li><li>10 lignes de code pour d’autres langages</li></ul>Projets Java :<ul></li><li> Il doit y avoir au moins 10 instructions successives et dupliquées, quel que soit le nombre de jetons et de lignes.</li></ul>Les différences dans la mise en retrait ainsi que dans les littéraux de chaîne sont ignorées lors de la détection des doublons. | Infos | > 1 % |
| Compatibilité Cloud Service | Nombre de problèmes de compatibilité du service cloud identifiés | Infos | > 0 |

>[!NOTE]
Voir [Définitions des mesures de SonarQube](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) pour des définitions plus détaillées.

>[!NOTE]
Pour en savoir plus sur les règles de qualité du code personnalisé exécutées par [!UICONTROL Cloud Manager], reportez-vous au document . [Règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## Traitement des faux positifs {#dealing-with-false-positives}

Le processus d’analyse de qualité n’est pas parfait et identifiera parfois de manière incorrecte des problèmes qui ne sont pas réellement problématiques. On parle alors de **faux positif**.

Dans ce cas, une annotation Java `@SuppressWarnings` standard spécifiant l’ID de règle comme attribut d’annotation peut être inscrite dans le code source. Par exemple, un faux positif courant est que la règle SonarQube permettant de détecter les mots de passe codés en dur peut être agressive sur la manière dont un mot de passe codé en dur est identifié.

Le code suivant est assez courant dans un projet AEM, qui comporte du code pour se connecter à un service externe.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube génère alors une vulnérabilité de bloqueur. Mais après avoir examiné le code, vous reconnaissez qu’il ne s’agit pas d’une vulnérabilité et vous pouvez annoter le code avec l’ID de règle approprié.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Cependant, si le code était en fait le suivant :

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

La bonne solution consiste alors à supprimer le mot de passe codé en dur.

>[!NOTE]
Bien qu’il soit préférable de rendre l’annotation `@SuppressWarnings` aussi précise que possible, c’est-à-dire de n’annoter que l’énoncé ou le bloc qui cause le problème, il est tout de même possible de le faire à un niveau qui se rapporte à la classe.

>[!NOTE]
Bien qu’il n’existe pas d’étape de test de sécurité explicite, des règles de qualité du code liées à la sécurité sont évaluées à l’étape de qualité du code. Reportez-vous au document [Présentation de la sécurité pour AEM as a Cloud Service](/help/security/cloud-service-security-overview.md) pour en savoir plus sur la sécurité en Cloud Service.

## Optimisation de l’analyse des modules de contenu {#content-package-scanning-optimization}

Dans le cadre du processus d’analyse de la qualité, Cloud Manager analyse les packages de contenu générés par la version Maven. Cloud Manager offre des optimisations pour accélérer ce processus, qui sont efficaces lorsque certaines contraintes de conditionnement sont observées. Le plus significatif est l’optimisation effectuée pour les projets qui génèrent un module de contenu unique, généralement appelé &quot;tout&quot;, qui contient un certain nombre d’autres modules de contenu générés, qui sont marqués comme ignorés. Lorsque Cloud Manager détecte ce scénario, plutôt que de décompresser le module &quot;all&quot;, les modules de contenu individuels sont analysés directement et triés en fonction des dépendances. Prenons l’exemple de la sortie de génération suivante.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

Si les seuls éléments à l’intérieur `myco-all-1.0.0-SNAPSHOT.zip` sont les deux packages de contenu ignorés, puis les deux packages incorporés seront analysés au lieu du package de contenu &quot;all&quot;.

Pour les projets qui produisent des dizaines de packages incorporés, cette optimisation a été affichée pour économiser jusqu’à 10 minutes par exécution de pipeline.

Un cas particulier peut se produire lorsque le module de contenu &quot;all&quot; contient une combinaison de modules de contenu ignorés et de lots OSGi. Par exemple, si `myco-all-1.0.0-SNAPSHOT.zip` contenait les deux packages incorporés mentionnés précédemment ainsi qu’un ou plusieurs lots OSGi, puis un nouveau package de contenu minimal est créé avec uniquement les lots OSGi. Ce module est toujours nommé `cloudmanager-synthetic-jar-package` et les lots contenus sont placés dans `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
* Cette optimisation n’a aucune incidence sur les modules déployés sur AEM.
* La correspondance entre les modules de contenu incorporés et les modules de contenu ignorés étant basée sur les noms de fichier, cette optimisation ne peut pas être effectuée si plusieurs modules de contenu ignorés portent exactement le même nom de fichier ou si le nom de fichier est modifié lors de l’incorporation.

