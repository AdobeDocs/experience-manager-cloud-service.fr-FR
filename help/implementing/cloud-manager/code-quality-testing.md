---
title: Test de qualité du code
description: Découvrez comment fonctionne le test de qualité du code des pipelines et comment il peut améliorer la qualité de vos déploiements.
exl-id: e2981be9-fb14-451c-ad1e-97c487e6dc46
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 96%

---

# Test de qualité du code {#code-quality-testing}

Découvrez comment fonctionne le test de qualité du code des pipelines et comment il peut améliorer la qualité de vos déploiements.

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_codequalitytests"
>title="Test de qualité du code"
>abstract="Le test de qualité du code évalue le code de votre application en fonction d’un ensemble de règles de qualité. Il s’agit de l’objectif principal d’un pipeline dédié uniquement à la qualité du code. Cette étape est exécutée immédiatement après l’étape de création dans tous les pipelines, aussi bien en production que hors production."

## Présentation {#introduction}

Le test de qualité du code évalue le code de votre application en fonction d’un ensemble de règles de qualité. Il s’agit de l’objectif principal d’un pipeline dédié uniquement à la qualité du code. Cette étape est exécutée immédiatement après l’étape de création dans tous les pipelines, aussi bien en production que hors production.

Voir [Configuration de votre pipeline CI-CD](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) pour en savoir plus sur les différents types de pipelines.

## Règles de qualité du code {#understanding-code-quality-rules}

Les tests de qualité du code analysent le code source afin de s’assurer qu’il répond à certains critères de qualité. Cette analyse est implémentée par une combinaison de SonarQube et d’examens au niveau du package de contenu à l’aide d’OakPAL. Il existe plus de 100 règles combinant des règles Java génériques et des règles spécifiques à AEM. Certaines des règles spécifiques à AEM sont créées en fonction des bonnes pratiques de l’équipe d’ingénierie AEM et sont appelées [Règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md).

>[!NOTE]
>
>Vous pouvez télécharger la liste complète des règles [via ce lien](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx).

### Évaluation à trois niveaux {#three-tiered-gate}

Les problèmes identifiés par le test de qualité du code sont affectés à l’une des trois catégories.

* **Critique** - il s’agit des problèmes qui entraînent une défaillance immédiate du pipeline.

* **Important** - il s’agit des problèmes qui entraînent la mise en pause du pipeline. Un responsable de déploiement, un responsable de projet ou un propriétaire d’entreprise peuvent soit contourner les problèmes, auquel cas le pipeline continue, soit accepter les problèmes, auquel cas le pipeline s’arrête avec un échec.

* **Informations** - Il s’agit des problèmes fournis uniquement à titre d’information et qui n’ont aucune incidence sur l’exécution du pipeline

>[!NOTE]
>
>Dans un pipeline uniquement axé sur la qualité du code, les échecs importants du point de contrôle Qualité du code ne peuvent pas être ignorés car l’étape de test de qualité du code est la dernière étape du pipeline.

### Évaluations {#ratings}

Les résultats de cette étape sont fournis sous forme de **notes**.

Le tableau suivant résume les notes et les seuils d’échec pour chacune des catégories Critique, Important et Informations.

| Nom | Définition | Catégorie | Seuil d’échec |
|--- |--- |--- |--- |
| Note de sécurité | A = Aucune vulnérabilité <br/>B = au moins 1 vulnérabilité mineure <br/>C = au moins 1 vulnérabilité majeure <br/>D = au moins 1 vulnérabilité critique <br/>E = au moins 1 vulnérabilité bloquante | Critique | &lt; B |
| Note de fiabilité | A = Aucun bug <br/>B = au moins 1 bug mineur <br/>C = au moins 1 bug majeur <br/>D = au moins 1 bug critique <br>E = au moins 1 bug bloquant | Critique | &lt; D |
| Note de maintenabilité | Défini par le coût de remédiation en suspens pour les code smells, comme un pourcentage du temps qui a déjà été consacré à l’application.<br/><ul><li>A = &lt;= 5 %</li><li>B = 6-10 %</li><li>C = 11-20 %</li><li>D = 21-50 %</li><li>E = > 50 %</li></ul> | Important | &lt; A |
| Couverture | Défini par un mélange de couverture de ligne de test unitaire et de couverture de condition à l’aide de la formule : <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <ul><li>`CT` = Conditions qui ont été évaluées comme `true` au moins une fois lors de l’exécution de tests unitaires</li><li>`CF` = Conditions qui ont été évaluées comme `false` au moins une fois lors de l’exécution de tests unitaires</li><li>`LC` = Lignes couvertes = lines_to_cover - uncover_lines</li><li>`B` = nombre total de conditions</li><li>`EL` = nombre total de lignes exécutables (lines_to_cover)</li></ul> | Important | &lt; 50 % |
| Tests unitaires ignorés | Nombre de tests unitaires ignorés | Infos | > 1 |
| Problèmes en cours | Types de problèmes généraux – Vulnérabilités, bogues et smells de code | Infos | > 0 |
| Lignes dupliquées | Défini comme le nombre de lignes impliquées dans les blocs dupliqués. Un bloc de code est considéré comme dupliqué dans les conditions suivantes.<br>Projets non Java :<ul><li>Il doit y avoir au moins 100 jetons successifs et dupliqués.</li><li>Ces jetons doivent être répartis au moins sur : </li><li>30 lignes de code pour COBOL </li><li>20 lignes de code pour ABAP </li><li>10 lignes de code pour d’autres langages</li></ul>Projets Java :<ul></li><li> Il devrait y avoir au moins 10 déclarations successives et dupliquées, quel que soit le nombre de jetons et de lignes.</li></ul>Les différences dans la mise en retrait ainsi que dans les littéraux de chaîne sont ignorées lors de la détection des doublons. | Infos | > 1 % |
| Compatibilité Cloud Service | Nombre de problèmes de compatibilité Cloud Service identifiés | Infos | > 0 |

>[!NOTE]
>
>Reportez-vous aux [Définitions des mesures de SonarQube](https://docs.sonarqube.org/latest/user-guide/metric-definitions/) pour des définitions plus détaillées.

>[!NOTE]
>
>Pour en savoir plus sur les règles de qualité du code personnalisé exécutées par [!UICONTROL Cloud Manager], reportez-vous à la section [Règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## Traitement des faux positifs {#dealing-with-false-positives}

Le processus d’analyse de qualité n’est pas parfait et identifiera parfois de manière incorrecte des problèmes qui ne sont pas réellement problématiques. On parle alors de **faux positif**.

Dans ces cas, le code source peut être annoté avec l’annotation standard Java `@SuppressWarnings` en spécifiant l’ID de la règle comme attribut d’annotation. Par exemple, un faux positif courant est que la règle de SonarQube permettant de détecter les mots de passe codés en dur peut être agressive sur la façon dont un mot de passe codé en dur est identifié.

Le code suivant est assez courant dans un projet AEM, qui comporte du code pour se connecter à un service externe.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube lèvera alors une vulnérabilité de blocage. Mais après avoir examiné le code, vous identifiez qu’il ne s’agit pas d’une vulnérabilité et vous pouvez l’annoter avec l’identifiant de règle approprié.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Cependant, si le code était en fait ceci :

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

La bonne solution consiste alors à supprimer le mot de passe codé en dur.

>[!NOTE]
>
>Bien que la bonne pratique consiste à rendre l’annotation `@SuppressWarnings` aussi précise que possible (c’est-à-dire à annoter uniquement l’instruction ou le bloc à l’origine du problème), il est tout de même possible d’annoter au niveau de la classe.

>[!NOTE]
>Bien qu’il n’existe pas d’étape de test de sécurité explicite, des règles de qualité du code liées à la sécurité sont évaluées à l’étape de qualité du code. Pour en savoir plus sur la sécurité dans Cloud Service, reportez-vous à [Vue d’ensemble de la sécurité pour AEM as a Cloud Service](/help/security/cloud-service-security-overview.md).

## Optimisation de l’analyse des packages de contenu {#content-package-scanning-optimization}

Dans le cadre du processus d’analyse de la qualité, Cloud Manager effectue une analyse des packages de contenu générés par la version Maven. Cloud Manager propose des optimisations pour accélérer ce processus, qui sont efficaces lorsque certaines contraintes de conditionnement sont observées. Le plus significatif est l’optimisation effectuée pour les projets qui génèrent un module de contenu unique, généralement appelé &quot;tout&quot;, qui contient plusieurs autres modules de contenu générés, qui sont marqués comme ignorés. Lorsque Cloud Manager détecte ce scénario, plutôt que de décompresser le package « all », les packages de contenu individuels sont analysés directement et triés en fonction des dépendances. Par exemple, considérez la sortie de génération suivante.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (package de contenu)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (package de contenu ignoré)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (package de contenu ignoré)

Si les seuls éléments contenus dans `myco-all-1.0.0-SNAPSHOT.zip` sont les deux packages de contenu ignorés, les deux packages incorporés sont analysés au lieu du package de contenu « all ».

Pour les projets qui produisent des dizaines de packages incorporés, il a été démontré que cette optimisation permet de gagner jusqu’à 10 minutes par exécution de pipeline.

Un cas particulier peut se produire lorsque le package de contenu « all » contient une combinaison de packages de contenu ignorés et de lots OSGi. Par exemple, si `myco-all-1.0.0-SNAPSHOT.zip` contient les deux packages incorporés mentionnés précédemment ainsi qu’un ou plusieurs lots OSGi, un nouveau package de contenu minimal est créé avec uniquement les lots OSGi. Ce package est toujours nommé `cloudmanager-synthetic-jar-package` et les lots contenus sont placés dans `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* Cette optimisation n’a aucune incidence sur les packages déployés dans AEM.
>* Étant donné que la correspondance entre les packages de contenu incorporés et les packages de contenu ignorés est basée sur les noms de fichier, cette optimisation ne peut pas être effectuée si plusieurs packages de contenu ignorés portent exactement le même nom de fichier ou si le nom du fichier est modifié lors de l’incorporation.
