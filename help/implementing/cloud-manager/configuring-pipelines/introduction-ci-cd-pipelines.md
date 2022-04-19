---
title: Pipelines CI/CD
description: Découvrez les pipelines CI/CD de Cloud Manager et comment les utiliser pour déployer votre code efficacement.
index: true
exl-id: 40d6778f-65e0-4612-bbe3-ece02905709b
source-git-commit: 6c246444f48440c64af0951e75f2071c00e477fa
workflow-type: tm+mt
source-wordcount: '1377'
ht-degree: 7%

---

# Pipelines CI/CD de Cloud Manager {#intro-cicd}

Découvrez les pipelines CI/CD de Cloud Manager et comment les utiliser pour déployer votre code efficacement.

## Présentation {#introduction}

Un pipeline CI/CD dans Cloud Manager est un mécanisme permettant de créer du code à partir d’un référentiel source et de le déployer dans un environnement. Un pipeline peut être déclenché par un événement, tel qu’une requête d’extraction d’un référentiel de code source (c’est-à-dire un changement de code), ou selon une planification régulière pour correspondre à une cadence de publication.

Pour configurer un pipeline, vous devez :

* Définissez le déclencheur qui démarrera le pipeline.
* Définissez les paramètres contrôlant le déploiement en production.
* Configurez les paramètres de test de performance.

Cloud Manager propose deux types de pipelines :

* [Pipelines de production](#prod-pipeline)
* [Pipelines hors production](#non-prod-pipeline)

![Types de pipelines](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## Présentation vidéo {#video}

Pour un aperçu rapide des types de pipeline, regardez cette courte vidéo.

>[!VIDEO](https://video.tv.adobe.com/v/342363)

## Pipelines de production {#prod-pipeline}

Un pipeline de production est un pipeline personnalisé qui comprend une série d’étapes orchestrées pour déployer le code source en vue d’une utilisation en production. Les étapes incluent d’abord la création, le conditionnement, le test, la validation et le déploiement dans tous les environnements d’évaluation. Par conséquent, un pipeline de production ne peut être ajouté qu’une fois qu’un ensemble d’environnements de production et d’évaluation est créé.

>[!TIP]
>
>Reportez-vous au document [Configuration d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) pour plus d’informations.

## Pipeline hors production {#non-prod-pipeline}

Un pipeline hors production sert principalement à exécuter des analyses de qualité du code ou à déployer le code source vers un environnement de développement.

>[!TIP]
>
>Reportez-vous au document [Configuration d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) pour plus d’informations.

## Sources de code {#code-sources}

Outre la production et les pipelines hors production, les pipelines peuvent être différenciés par le type de code qu’ils déploient.

* **[Pipelines complets empilés](#full-stack-pipeline)** - Déploiement simultané de versions de code front-end et back-end contenant une ou plusieurs applications de serveur AEM avec des configurations HTTPD/Dispatcher
* **[Pipelines front-end](#front-end)** - Déploiement de versions de code frontal contenant une ou plusieurs applications d’interface utilisateur côté client
* **[Pipelines de configuration de niveau web](#web-tier-config-pipelines)** - Déploiement des configurations HTTPD/Dispatcher

Elles sont décrites en détail plus loin dans ce document.

### Présentation des pipelines CI-CD dans Cloud Manager {#understand-pipelines}

Le tableau suivant récapitule tous les pipelines disponibles dans Cloud Manager et leur utilisation.

| Type de pipeline | Déploiement ou qualité du code | Code source | Objectif | Remarques |
|--- |--- |--- |---|---|
| Production ou hors production | Déploiement | Pile complète | Déploie simultanément des versions de code front-end et back-end avec des configurations HTTPD/Dispatcher. | Lorsque le code frontal doit être déployé simultanément avec le code AEM serveur.<br>Lorsque les pipelines front-end ou les pipelines de configuration de niveau web n’ont pas encore été adoptés. |
| Production ou hors production | Déploiement | Front-end | Déploie une version de code frontal contenant une ou plusieurs applications d’interface utilisateur côté client. | Prise en charge de plusieurs pipelines front-end simultanés<br>Beaucoup plus rapide que les déploiements de pile complète |
| Production ou hors production | Déploiement | Configuration de la couche web | Déploiement des configurations HTTPD/Dispatcher | Déploiement en minutes |
| Hors production | Qualité du code | Pile complète | Exécute des analyses de qualité du code sur le code de pile complète sans déploiement. | Prise en charge de plusieurs pipelines |
| Hors production | Qualité du code | Front-end | Exécute des analyses de qualité du code sur le code frontal sans déploiement. | Prise en charge de plusieurs pipelines |
| Hors production | Qualité du code | Configuration de la couche web | Exécute des analyses de qualité du code sur les configurations du Dispatcher sans déploiement. | Prise en charge de plusieurs pipelines |

Le diagramme suivant illustre les configurations de pipeline de Cloud Manager avec des configurations de référentiel front-end standard, uniques ou de référentiel front-end indépendant.

![Configurations de pipeline de Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Pipelines pleine empilement {#full-stack-pipeline}

Les pipelines entièrement empilés déploient simultanément le code principal, le code frontal et les configurations de niveau web pour AEM exécution.

* Code principal : contenu non modifiable tel que du code Java, des configurations OSGi, repoinit, ainsi que du contenu modifiable.
* Code front-end : ressources de l’interface utilisateur de l’application telles que JavaScript, CSS, polices
* Configuration de niveau web - Configurations HTTPD/Dispatcher

Le pipeline pleine pile représente un pipeline &quot;uber&quot;, qui fait tout en même temps, tout en donnant aux utilisateurs les options de déployer exclusivement leur code frontal ou leurs configurations Dispatcher via le pipeline frontal et les pipelines de configuration de niveau web respectivement.

Les pipelines entièrement empilés empaquettent le code frontal (JavaScript/CSS) sous la forme [AEM des bibliothèques clientes.](/help/implementing/developing/introduction/clientlibs.md)

Les pipelines à pile complète peuvent déployer des configurations de niveau web si un [pipeline de configuration de niveau web](#web-tier-config-pipelines) n’est pas configuré.

Les restrictions suivantes s’appliquent.

* Un utilisateur doit être connecté à la variable **Responsable de déploiement** pour configurer ou exécuter des pipelines.
* À tout moment, il ne peut y avoir qu’un seul pipeline à pile complète par environnement.

En outre, sachez comment se comporte le pipeline de la pile complète si vous choisissez d’introduire un [pipeline de configuration de niveau web.](#web-tier-config-pipelines)

* Le pipeline de pile complète pour un environnement ignore la configuration de Dispatcher si le pipeline de configuration de niveau web correspondant existe.
* Si le pipeline de configuration de niveau web correspondant à l’environnement n’existe pas, l’utilisateur peut configurer le pipeline de pile complète pour inclure ou ignorer la configuration de Dispatcher.

Les pipelines à pile complète peuvent être des pipelines ou un déploiement de qualité de code.

## Pipelines front-end {#front-end}

Le code frontal est un code qui est présenté sous la forme de fichiers statiques. Il est distinct du code de l’interface utilisateur fourni par AEM et peut inclure des thèmes de site, des SPA définis par le client, des Firefly, ainsi que d’autres solutions.

Les pipelines front-end aident vos équipes à rationaliser votre processus de conception et de développement en activant le déploiement accéléré de code frontal asynchrone du développement principal. Ce pipeline dédié déploie JavaScript et CSS sur la couche de distribution AEM en tant que thème, ce qui entraîne une nouvelle version de thème qui peut être référencée à partir des pages fournies par AEM.

>[!IMPORTANT]
>
>Vous devez être sur AEM version `2021.10.5933.20211012T154732Z ` ou version ultérieure avec AEM Sites activé pour exploiter les pipelines front-end.

>[!NOTE]
>
>Un utilisateur avec la variable **Responsable de déploiement** peut créer et exécuter plusieurs pipelines front-end simultanément.
>
>Toutefois, il existe une limite maximale de 300 pipelines par programme (pour tous les types de pipelines). Il peut s’agir de pipelines de qualité de code frontal ou de déploiement front-end.

Les pipelines front-end peuvent être des pipelines ou un déploiement de qualité de code.

### Avant de configurer des pipelines front-end {#before-start}

Avant de configurer les pipelines front-end, consultez la section [parcours de création rapide de site](/help/journey-sites/quick-site/overview.md) pour obtenir un guide de bout en bout à l’aide de l’outil de création rapide de site d’AEM simple d’utilisation. Ce parcours vous aidera à rationaliser votre développement frontal et vous permettra de personnaliser rapidement votre site sans aucune connaissance AEM principale.

### Configuration d’un pipeline front-end {#configure-front-end}

Pour savoir comment configurer les pipelines front-end, reportez-vous aux documents suivants.

* [Ajout d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Ajout d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)

### Développer des sites avec le pipeline front-end {#developing-with-front-end-pipeline}

Avec les pipelines front-end, les développeurs front-end bénéficient d’une plus grande indépendance et le processus de développement peut être accéléré.

Reportez-vous au document [Développement de sites avec le pipeline front-end](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) pour le fonctionnement de ce processus, ainsi que certaines considérations à prendre en compte afin de tirer pleinement parti de ce processus.

### Configuration de pipelines empilés complets {#configure-full-stack}

Pour savoir comment configurer des pipelines pleine pile, reportez-vous aux documents suivants.

* [Ajout d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Ajout d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)


## Pipelines de configuration de niveau web {#web-tier-config-pipelines}

Les pipelines de configuration de niveau web permettent le déploiement exclusif de la configuration HTTPD/Dispatcher sur le runtime AEM en le découplant des autres modifications de code. Il s’agit d’un pipeline rationalisé qui fournit aux utilisateurs qui souhaitent déployer uniquement les modifications de configuration du Dispatcher, une méthode accélérée pour le faire en quelques minutes seulement.

>[!TIP]
>
>Avec les pipelines de configuration de niveau web, vous pouvez choisir entre stocker votre configuration web au même emplacement source que le pipeline de pile complet ou à un autre emplacement, selon la structure qui convient le mieux à votre projet.

Les restrictions suivantes s’appliquent.

* Vous devez être sur AEM version `2021.12.6151.20211217T120950Z` ou plus récent pour tirer parti des pipelines de configuration de niveau web.
* Vous devez [vous inscrire au mode flexible des outils de Dispatcher ;](/help/implementing/dispatcher/disp-overview.md#validation-debug) pour tirer parti des pipelines de configuration de niveau web.
* Un utilisateur doit être connecté à la variable **Responsable de déploiement** pour configurer ou exécuter des pipelines.
* À tout moment, il ne peut y avoir qu’un seul pipeline de configuration de niveau web par environnement.
* L’utilisateur ne peut pas configurer de pipeline de configuration de niveau web lorsque le pipeline de pile complète correspondant est en cours d’exécution.
* La structure de niveau web doit se conformer à la structure de mode flexible, telle que définie dans le document. [Dispatcher en mode cloud.](/help/implementing/dispatcher/disp-overview.md#validation-debug)

Sachez également comment la variable [pipeline de pile complète](#full-stack-pipeline) se comporte lors de l’introduction d’un pipeline de niveau web.

* Si un pipeline de configuration de niveau web n’a pas été configuré pour un environnement, l’utilisateur peut effectuer une sélection lors de la configuration de son pipeline de pile complète correspondant afin d’inclure ou d’ignorer la configuration de Dispatcher pendant l’exécution et le déploiement.
* Une fois qu’un pipeline de configuration de niveau web a été configuré pour un environnement, son pipeline de pile complète correspondant (s’il en existe un) ignorera la configuration du dispatcher lors de l’exécution et du déploiement.
* Une fois qu’un pipeline de configuration de niveau web est supprimé, son pipeline de pile complète correspondant est réinitialisé pour déployer les configurations du Dispatcher pendant son exécution.

Les pipelines de configuration de niveau web peuvent être de type qualité de code ou déploiement .

### Configuration des pipelines de configuration de niveau web {#configure-web-tier-config-pipelines}

Pour savoir comment configurer des pipelines de configuration de niveau web, reportez-vous aux documents suivants.

* [Ajout d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Ajout d’un pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)
