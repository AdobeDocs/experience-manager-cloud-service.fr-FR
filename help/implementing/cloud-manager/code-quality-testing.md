---
title: Test de qualité du code - Cloud Services
description: Test de qualité du code - Cloud Services
translation-type: tm+mt
source-git-commit: 25ba5798de175b71be442d909ee5c9c37dcf10d4
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 78%

---


# Test de qualité du code {#code-quality-testing}

Le test de qualité du code évalue la qualité du code de votre application. Il s&#39;agit de l&#39;objectif principal d&#39;un pipeline de qualité code uniquement et il est exécuté immédiatement après l&#39;étape de construction dans tous les pipelines de non-production et de production.

Reportez-vous à [Configuration de votre pipeline](/help/implementing/cloud-manager/configure-pipeline.md) CI-CD pour en savoir plus sur les différents types de conduites.

## Présentation des règles de qualité du code personnalisé {#understanding-code-quality-rules}

Dans le test de qualité du code, le code source est analysé afin de s’assurer qu’il répond à certains critères de qualité. Actuellement, cette analyse est implémentée par une combinaison de SonarQube et d’examens au niveau du package de contenu à l’aide de OakPAL. Il existe plus de 100 règles combinant des règles Java génériques et des règles spécifiques à AEM. Certaines des règles spécifiques à l&#39;AEM sont créées en fonction des meilleures pratiques d&#39;AEM Engineering et sont appelées Règles [de qualité du code](/help/implementing/cloud-manager/custom-code-quality-rules.md)personnalisé.

>[!NOTE]
>You can download the complete list of rules [here](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest.xlsx).

Les résultats de cette étape sont distribués sous forme de *cotation*. Le tableau suivant résume l’évaluation des critères de test :

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


>[!NOTE]
>
>Pour en savoir plus sur les règles de qualité du code personnalisé exécutées par [!UICONTROL Cloud Manager], reportez-vous à la section [Règles de qualité du code personnalisé](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## Traitement des faux positifs {#dealing-with-false-positives}

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
>Bien qu&#39;il n&#39;y ait pas d&#39;étape de test de sécurité explicite, des règles de qualité du code liées à la sécurité sont toujours évaluées au cours de l&#39;étape de qualité du code. Pour en savoir plus sur la sécurité dans le Cloud Service, reportez-vous à la section Aperçu de [la sécurité pour AEM Cloud Service](/help/security/cloud-service-security-overview.md) .
