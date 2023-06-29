---
title: Configuration de l’équipe de développement des grands comptes
description: Découvrez comment configurer et mettre à l’échelle votre équipe de développement d’entreprise et comment AEM as a Cloud Service peut prendre en charge votre processus de développement.
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1437'
ht-degree: 46%

---

# Configuration de l’équipe de développement d’entreprise pour AEM as a Cloud Service {#enterprise-setup}

Découvrez comment configurer et mettre à l’échelle votre équipe de développement d’entreprise et comment AEM as a Cloud Service peut prendre en charge votre processus de développement.

## Présentation {#introduction}

Pour aider les clients à configurer le développement d’entreprise, AEM as a Cloud Service s’intègre entièrement à Cloud Manager et à ses [Pipelines CI/CD avec opinion](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md). Ces pipelines et services sont construits sur la base des bonnes pratiques, ce qui garantit un suivi complet. [test et qualité de code la plus élevée](/help/implementing/cloud-manager/code-quality-testing.md).

## Prise en charge de Cloud Manager dans la configuration Enterprise Team Development {#cloud-manager}

Pour garantir une intégration rapide, Cloud Manager fournit tout ce dont vous avez besoin pour commencer à développer des expériences numériques immédiatement, y compris un référentiel git pour stocker les personnalisations qui sont ensuite créées, vérifiées et déployées par Cloud Manager.

Grâce à Cloud Manager, les équipes de développement peuvent envisager de valider fréquemment les modifications sans dépendre des équipes d’Adobe.

Trois types d’environnements sont disponibles dans Cloud Manager.

* Développement
* Évaluation
* Production

Il est possible de déployer le code dans des environnements de développement en utilisant un pipeline hors production. Pour les environnements d’évaluation et de production qui vont toujours ensemble et assurent ainsi la validation avant le déploiement en production comme bonnes pratiques, un pipeline de production utilise [points de contrôle de qualité](/help/implementing/cloud-manager/custom-code-quality-rules.md) pour valider le code de l’application et les modifications apportées à la configuration.

Le pipeline de production déploie d’abord le code et la configuration dans l’environnement d’évaluation, teste l’application et se déploie finalement en production.

Un SDK Cloud Service toujours mis à jour avec les dernières améliorations as a Cloud Service AEM permet un développement local directement à l’aide du matériel local du développeur. Le développement est ainsi rapide et les temps de réponse très courts. Les développeurs peuvent ainsi rester dans l’environnement local avec lequel ils sont familiarisés, choisir parmi un large éventail d’outils de développement, et accéder à des environnements de développement ou de production lorsqu’ils le jugent approprié.

Cloud Manager prend en charge des configurations multi-équipes flexibles, ajustables en fonction des besoins de l’entreprise. Pour garantir des déploiements stables avec plusieurs équipes tout en évitant les situations où une équipe impacte la production pour toutes les équipes, le pipeline opiniâtre de Cloud Manager valide et teste toujours le code de toutes les équipes ensemble.

## Exemple concret {#real-world-example}

Chaque entreprise a des exigences différentes, notamment la configuration de l’équipe, les processus et les processus de développement. La configuration décrite ci-dessous est utilisée par Adobe pour plusieurs projets qui assurent la mise en œuvre d’expériences en s’appuyant sur AEM as a Cloud Service.

Par exemple, les applications Adobe Creative Cloud comme Adobe Photoshop ou Adobe Illustrator, contiennent des ressources de contenu, notamment des tutoriels, des exemples et des guides mis à la disposition des utilisateurs finaux. Ce contenu est consommé par les applications clientes à l’aide d’AEM as a Cloud Service en mode découplé. Pour cela, elles effectuent des appels d’API vers le niveau de publication d’AEM Cloud afin de récupérer le contenu structuré en flux JSON. Par ailleurs, elles exploitent le [réseau de diffusion de contenu (CDN) d’AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#content-delivery) pour diffuser des contenus structurés et non structurés avec des performances optimales.

Les équipes qui contribuent à ce projet suivent le processus suivant.

Chaque équipe utilise son propre workflow de développement et dispose d’un référentiel git distinct. Un référentiel git partagé supplémentaire est utilisé pour les projets d’intégration. Ce référentiel git contient la structure racine du référentiel git de Cloud Manager, y compris la configuration du Dispatcher partagé.

L’intégration d’un nouveau projet nécessite une liste dans le fichier de projet Maven Reactor à la racine du référentiel Git partagé. Pour la configuration du Dispatcher, un nouveau fichier de configuration est créé dans le projet de Dispatcher. Ce fichier est ensuite inclus par la configuration Dispatcher principale. Chaque équipe est responsable de son propre fichier de configuration de Dispatcher. Les modifications apportées au référentiel Git partagé sont rares et ne sont généralement requises que lorsqu’un nouveau projet est intégré. Le travail principal est effectué par chaque équipe de projet dans son propre référentiel Git.

![Diagramme de workflow](/help/implementing/cloud-manager/assets/team-setup1.png)

Le référentiel git pour chacun d’eux est configuré à l’aide de la fonction [AEM Archétype de projet](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) et suivent donc les bonnes pratiques pour la configuration des projets AEM. La seule exception est la configuration du Dispatcher qui est effectuée dans le référentiel git partagé comme indiqué ci-dessus.

Chaque équipe utilise un workflow Git simplifié avec deux branches + N, suivant le modèle de flux Git :

* Une branche de version stable contient le code de production.

* Une branche de développement contient le dernier développement.

* Pour chaque fonctionnalité, une nouvelle branche est créée.

Le développement est effectué dans une branche de fonctionnalités. Lorsque la fonctionnalité est à maturité, elle est fusionnée dans la branche de développement. Les fonctionnalités terminées et validées sont sélectionnées à partir de la branche de développement et fusionnées dans la branche stable.

Toutes les modifications sont effectuées par le biais de demandes d’extraction (PR). Chaque requête d’extraction est automatiquement validée par les points de contrôle qualité. Sonar est utilisé pour la vérification de la qualité du code et un ensemble de suites de tests est exécuté pour s’assurer que le nouveau code n’introduit aucune régression.

La configuration du référentiel git de Cloud Manager comporte deux branches.

* Une branche de version stable contient le code de production de toutes les équipes.
* Une branche de développement contient le code de développement de toutes les équipes.

Chaque notification push vers le référentiel git d’une équipe dans le développement ou la branche stable déclenche une [Action GitHub](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md#managing-code).

Tous les projets appliquent la même configuration pour la branche stable. Une notification push vers la branche stable d’un projet est automatiquement envoyée à la branche stable du référentiel Git de Cloud Manager. Le pipeline de production dans Cloud Manager est configuré pour être déclenché par une transmission push vers la branche stable. Le pipeline de production est donc exécuté par chaque notification push d’une équipe dans une branche stable et le déploiement en production est mis à jour si tous les points de contrôle qualité sont franchis avec succès.

![Diagramme push](/help/implementing/cloud-manager/assets/team-setup2.png)

Les envois vers la branche de développement sont gérés différemment. Bien qu’une notification push envoyée à une branche de développement dans le référentiel git d’une équipe déclenche également une action GitHub et que le code soit automatiquement envoyé à la branche de développement dans le référentiel git de Cloud Manager, le pipeline hors production n’est pas automatiquement déclenché par la notification push du code. Elle est déclenchée par un appel à l’API de Cloud Manager.

L’exécution du pipeline de production comprend la vérification du code de toutes les équipes via les points de contrôle qualité fournis. Une fois le code déployé dans l’environnement intermédiaire, les tests et les audits sont exécutés pour s’assurer que tout fonctionne comme prévu. Une fois tous les points de contrôle passés, les modifications sont déployées en production sans interruption ou arrêt.

Le [SDK d’AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md#developing) est utilisé pour le développement local. Le SDK permet de configurer un auteur, une publication et un dispatcher locaux. Vous pouvez ainsi effectuer votre développement hors ligne et obtenir des délais d’exécution rapides. Parfois, seul l’environnement de création est utilisé pour le développement, mais la configuration rapide des environnements de Dispatcher et de publication permet de tout tester localement avant de le transférer dans le référentiel git.

Les membres de chaque équipe extraient généralement le code de la Git partagée pour leur propre code de projet. Il n’est pas nécessaire de passer en revue d’autres projets car ceux-ci sont indépendants.

![Extraction locale et SDK](/help/implementing/cloud-manager/assets/team-setup3.png)

Il est possible d’utiliser cette configuration concrète comme plan directeur, puis de la personnaliser selon les besoins de l’entreprise. Le concept flexible d’embranchement et de fusion de Git permet de créer des variantes des workflows ci-dessus, personnalisées selon les besoins de chaque équipe. AEM as a Cloud Service prend en charge toutes ces variations sans sacrifier la valeur de base du pipeline parfaitement défini de Cloud Manager.

>[!TIP]
>
>Voir [Utilisation de plusieurs référentiels Git source](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html?lang=fr#managing-code) pour en savoir plus sur cette configuration.

### Considérations relatives à une configuration multi-équipes {#considerations}

Avec le référentiel git de Cloud Manager et le pipeline de production, le code de production complet est toujours exécuté par tous les points de contrôle qualité, le considérant comme une unité de déploiement. Ainsi, le système de production est toujours opérationnel sans interruption ni interruption.

En revanche, en l’absence d’un tel système, chaque équipe pouvant effectuer un déploiement distinct, il est possible qu’une mise à jour d’une seule équipe entraîne des problèmes de stabilité en production. En outre, il est nécessaire de prévoir une coordination et des temps d’arrêt planifiés pour déployer les mises à jour. Avec un nombre croissant d&#39;équipes, l&#39;effort de coordination devient beaucoup plus complexe et rapidement ingérable.

Si un problème est détecté au niveau des points de contrôle qualité, la production ne sera pas affectée, et le problème pourra être détecté et corrigé sans que le personnel Adobe n’ait à intervenir. Sans Cloud Service et sans toujours tester l’ensemble du déploiement, les déploiements partiels peuvent entraîner des pannes nécessitant une demande de restauration ou même une restauration complète à partir d’une sauvegarde. Les tests partiels peuvent aussi entraîner d’autres problèmes qui devront être résolus ultérieurement, ce qui nécessitera à nouveau la coordination et l’assistance du personnel d’Adobe.

>[!TIP]
>
>Pour toute configuration multi-équipes, il est essentiel de définir un modèle de gouvernance et un ensemble de normes que toutes les équipes doivent respecter. Le plan directeur précédent pour une configuration multi-équipes permet de mettre à l’échelle un plus grand nombre d’équipes, que vous pouvez utiliser comme point de départ.
