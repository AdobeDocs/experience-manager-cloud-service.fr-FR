---
title: Configuration de l’équipe de développement d’entreprise
description: Découvrez comment configurer et mettre à l’échelle votre équipe de développement d’entreprise et comment AEM as a Cloud Service peut prendre en charge votre processus de développement.
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: cbeb3d8f5fa5cbf1839e1e8c5e651329b06e60a4
workflow-type: tm+mt
source-wordcount: '1401'
ht-degree: 40%

---

# Configuration de l’équipe de développement d’entreprise pour AEM as a Cloud Service {#enterprise-setup}

Découvrez comment configurer et mettre à l’échelle votre équipe de développement d’entreprise et comment Adobe Experience Manager () as a Cloud Service peut prendre en charge votre processus de développement.

## Présentation {#introduction}

Pour prendre en charge les clientes et les clients avec les configurations de développement d’entreprise, AEM as a Cloud Service s’intègre entièrement à Cloud Manager et à ses [pipelines CI/CD parfaitement définis](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) conçus spécifiquement pour les besoins. Ces pipelines et services sont créés sur la base des bonnes pratiques, ce qui garantit des [tests complets et la plus haute qualité de code](/help/implementing/cloud-manager/code-quality-testing.md).

## Prise en charge de Cloud Manager dans la configuration du développement de l’équipe d’entreprise {#cloud-manager}

Pour garantir une intégration rapide, Cloud Manager fournit tout ce dont vous avez besoin pour commencer à développer des expériences numériques immédiatement, y compris un référentiel Git pour stocker les personnalisations, qui sont ensuite créées, vérifiées et déployées par Cloud Manager.

Grâce à Cloud Manager, les équipes de développement peuvent envisager de valider fréquemment les modifications sans dépendre des équipes d’Adobe.

Trois types d’environnements sont disponibles dans Cloud Manager.

* Développement
* Évaluation
* Production

Il est possible de déployer le code dans des environnements de développement en utilisant un pipeline hors production. Pour les environnements d’évaluation et de production, qui vont toujours de pair et garantissent ainsi la bonne pratique de validation avant le déploiement en production, un pipeline de production utilise des [points de contrôle qualité](/help/implementing/cloud-manager/custom-code-quality-rules.md) pour valider le code de l’application et les modifications de configuration.

Le pipeline de production déploie d’abord le code et la configuration dans l’environnement d’évaluation, teste l’application et effectue enfin le déploiement en production.

Un SDK Cloud Service toujours mis à jour avec les dernières améliorations d’AEM as a Cloud Service permet un développement local directement à l’aide du matériel local du développeur. Cette approche permet un développement rapide avec des temps de réponse très faibles. Les développeurs peuvent ainsi rester dans l’environnement local avec lequel ils sont familiarisés, choisir parmi un large éventail d’outils de développement, et accéder à des environnements de développement ou de production lorsqu’ils le jugent approprié.

Cloud Manager prend en charge des configurations multi-équipes flexibles qui peuvent être ajustées en fonction des besoins d’une entreprise. Pour garantir des déploiements stables au sein de plusieurs équipes, le pipeline Cloud Manager opiniâtre valide et teste le code de toutes les équipes ensemble. Cette approche permet d’éviter les situations où les modifications d’une équipe affectent la production pour toutes les équipes.

## Exemple de monde réel {#real-world-example}

Chaque entreprise a des exigences différentes, notamment la configuration de l’équipe, les processus et les processus de développement. La configuration décrite ci-dessous est utilisée par Adobe pour plusieurs projets qui assurent la mise en œuvre d’expériences en s’appuyant sur AEM as a Cloud Service.

Par exemple, les applications Adobe Creative Cloud comme Adobe Photoshop ou Adobe Illustrator, contiennent des ressources de contenu, notamment des tutoriels, des exemples et des guides mis à la disposition des utilisateurs finaux. Les applications clientes consomment du contenu d’AEM as a Cloud Service sans interface utilisateur graphique. Ils effectuent des appels d’API au niveau de publication d’AEM Cloud pour récupérer du contenu structuré en tant que flux JSON. De plus, le [réseau de diffusion de contenu (CDN) dans AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#content-delivery) est utilisé pour diffuser du contenu structuré et non structuré avec des performances optimales.

Les équipes qui contribuent à ce projet suivent le processus suivant.

Chaque équipe utilise son propre workflow de développement et dispose d’un référentiel Git distinct. Un référentiel Git partagé supplémentaire est utilisé pour les projets d’intégration. Ce référentiel Git contient la structure racine du référentiel Git de Cloud Manager, y compris la configuration Dispatcher partagée.

L’intégration d’un nouveau projet nécessite une liste dans le fichier de projet Maven Reactor à la racine du référentiel Git partagé. Pour la configuration Dispatcher, un nouveau fichier de configuration est créé dans le projet Dispatcher. La configuration Dispatcher principale inclut alors ce fichier. Chaque équipe est responsable de son propre fichier de configuration Dispatcher. Les modifications apportées au référentiel Git partagé sont rares et ne sont généralement requises que lorsqu’un nouveau projet est intégré. Le travail principal est effectué par chaque équipe de projet au sein de leur propre référentiel Git.

![Diagramme de workflow](/help/implementing/cloud-manager/assets/team-setup1.png)

Le référentiel Git pour chacun d’eux est configuré à l’aide de l’[archétype de projet AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/overview) et suit donc les bonnes pratiques pour configurer AEM Projets. La seule exception concerne la configuration de Dispatcher, qui est effectuée dans le référentiel Git partagé comme indiqué ci-dessus.

Chaque équipe utilise un workflow Git simplifié avec deux branches + N, suivant le modèle de flux Git :

* Une branche de version stable contient le code de production.

* Une branche de développement contient le développement le plus récent.

* Pour chaque fonctionnalité, une nouvelle branche est créée.

Le développement est effectué dans une branche de fonctionnalités. Lorsque la fonctionnalité est mûrie, elle est fusionnée dans la branche de développement. Les fonctionnalités terminées et validées sont sélectionnées à partir de la branche de développement et fusionnées dans la branche stable.

Toutes les modifications sont effectuées par le biais de requêtes de tirage (PR). Les points de contrôle de qualité valident automatiquement chaque requête de tirage. Sonar est utilisé pour la vérification de la qualité du code et un ensemble de suites de tests est exécuté pour s’assurer que le nouveau code n’introduit aucune régression.

La configuration dans le référentiel Git de Cloud Manager comporte deux branches.

* Une branche de version stable contient le code de production de toutes les équipes.
* Une branche de développement contient le code de développement de toutes les équipes.

Chaque notification push vers le référentiel Git d’une équipe dans le développement ou la branche stable déclenche une [action GitHub](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md#managing-code).

Tous les projets appliquent la même configuration pour la branche stable. Un push vers la branche stable d’un projet est automatiquement envoyé vers la branche stable du référentiel Git Cloud Manager. Une notification push vers la branche stable déclenche le pipeline de production dans Cloud Manager. Chaque notification push d’une équipe dans une branche stable déclenche le pipeline de production. Le déploiement en production est mis à jour si tous les points de contrôle qualité réussissent.

![Diagramme de notification push](/help/implementing/cloud-manager/assets/team-setup2.png)

Les envois vers la branche de développement sont gérés différemment. Une notification push vers une branche de développement dans le référentiel Git d’une équipe déclenche également une action GitHub. Cette action envoie automatiquement le code dans la branche de développement du référentiel Git Cloud Manager. Toutefois, cette notification push de code ne déclenche pas automatiquement le pipeline hors production. Un appel à l’API Cloud Manager le déclenche.

L’exécution du pipeline de production comprend la vérification du code de toutes les équipes via les points de contrôle qualité fournis. Une fois le code déployé dans l’environnement intermédiaire, les tests et les audits sont exécutés afin que tout fonctionne comme prévu. Lorsque tous les points de contrôle sont transmis, les modifications sont déployées en production sans interruption ni interruption.

Le [SDK d’AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md#developing) est utilisé pour le développement local. Le SDK permet de configurer un auteur, une publication et un Dispatcher locaux. Ce workflow permet le développement hors ligne et des délais d’exécution rapides. Parfois, seul l’environnement de création est utilisé pour le développement, mais la configuration rapide des environnements Dispatcher et de publication permet de tout tester localement avant de le transférer dans le référentiel Git.

Les membres de chaque équipe extraient généralement le code du Git partagé pour leur propre code de projet. Il n’est pas nécessaire de vérifier d’autres projets car ils sont indépendants.

![Extraction locale et SDK](/help/implementing/cloud-manager/assets/team-setup3.png)

Il est possible d’utiliser cette configuration concrète comme plan directeur, puis de la personnaliser selon les besoins de l’entreprise. Le concept flexible d’embranchement et de fusion de Git permet des variantes des workflows ci-dessus, personnalisées selon les besoins de chaque équipe. AEM as a Cloud Service prend en charge toutes ces variations sans sacrifier la valeur de base du pipeline parfaitement défini de Cloud Manager.

>[!TIP]
>
>Voir [Utilisation de plusieurs référentiels Git Source](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/managing-code/multiple-git-repos#managing-code) pour en savoir plus sur cette configuration.

### Considérations relatives à une configuration multi-équipe {#considerations}

Avec le référentiel Git de Cloud Manager et le pipeline de production, le code de production complet passe toujours par tous les points de contrôle de qualité, le considérant comme une unité de déploiement. Ainsi, le système de production est toujours activé sans interruption ni temps d’arrêt.

En revanche, en l’absence d’un tel système, chaque équipe pouvant se déployer séparément, il est possible qu’une mise à jour d’une seule équipe entraîne des problèmes de stabilité de production. En outre, il est nécessaire de prévoir une coordination et des temps d’arrêt planifiés pour déployer les mises à jour. Avec un nombre croissant d’équipes, l’effort de coordination devient beaucoup plus complexe et rapidement ingérable.

Si un problème est détecté au niveau des points de contrôle qualité, la production ne sera pas affectée, et le problème pourra être détecté et corrigé sans que le personnel Adobe ait à intervenir. Sans Cloud Service et sans test systématique de l’ensemble du déploiement, les déploiements partiels peuvent entraîner des pannes qui nécessitent une requête de restauration ou même une restauration complète à partir d’une sauvegarde. Les tests partiels peuvent également entraîner des problèmes supplémentaires qui doivent être résolus ultérieurement, nécessitant une coordination et un soutien de la part du personnel Adobe.

>[!TIP]
>
>Pour toute configuration multi-équipes, il est essentiel de définir un modèle de gouvernance et un ensemble de normes que toutes les équipes doivent respecter. Le plan directeur précédent, qui correspond à une configuration multi-équipes, permet de mettre à l’échelle un plus grand nombre d’équipes.Vous pouvez ainsi utiliser ce plan directeur comme point de départ.
