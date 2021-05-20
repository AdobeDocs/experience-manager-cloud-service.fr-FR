---
title: Configuration du développement des équipes d’entreprise - Cloud Services
description: Consultez cette page pour en savoir plus sur la configuration du développement de l’équipe d’entreprise
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
source-git-commit: 33e1c7eb5ea224b46ba441ca7447f90f04476c76
workflow-type: tm+mt
source-wordcount: '1525'
ht-degree: 1%

---

# Configuration du développement de l’équipe d’entreprise pour AEM en tant que Cloud Service {#enterprise-setup}

## Présentation {#introduction}

AEM en tant que Cloud Service, une offre native au cloud qui fournit AEM as a service est conçue pour bénéficier de plus de 10 ans de diffusion de logiciels d’entreprise aux équipes d’entreprise avec leurs besoins spécifiques. Bien qu’elle catapulte l’AEM dans le monde natif du cloud, avec de nouvelles valeurs comme toujours actives, toujours à jour, toujours sécurisées et toujours à grande échelle, elle conserve la proposition de valeur principale que AEM fournit en tant que plateforme personnalisable à nos clients et permet aux équipes d’entreprise d’intégrer dans leurs procédures de développement et de diffusion.

Pour prendre en charge nos clients avec les configurations de développement d’entreprise, AEM as a Cloud Service s’intègre entièrement à Cloud Manager et à ses pipelines CI/CD dédiés, qui sont équipés de bonnes pratiques et d’enseignements tirés de plusieurs années d’expérience en matière de développement et de déploiements au niveau de l’entreprise, assurant ainsi des tests approfondis et une qualité de code optimale pour offrir des expériences exceptionnelles.

## Prise en charge de Cloud Manager dans la configuration du développement de l’équipe d’entreprise {#cloud-manager}

Pour garantir une intégration rapide des clients, Cloud Manager fournit tout ce qui est nécessaire pour commencer à développer des expériences immédiatement, y compris un référentiel git pour stocker les personnalisations qui sont ensuite créées, vérifiées et déployées par Cloud Manager.
Grâce à Cloud Manager, les équipes de développement peuvent travailler à la validation fréquente de modifications sans dépendre du personnel de l’Adobe.

Dans Cloud Manager, trois types d’environnement sont disponibles :

* Développement
* Évaluation
* Production

Le code peut être déployé dans des environnements de développement à l’aide d’un pipeline hors production. Pour les environnements d’évaluation et de production, qui vont toujours de pair et garantissent ainsi la validation avant le déploiement en production comme une bonne pratique, un pipeline de production utilise des points de contrôle qualité pour valider le code de l’application et les modifications de configuration.

Le pipeline de production déploie d’abord le code et la configuration dans l’environnement d’évaluation, teste l’application et se déploie finalement en production.
Un SDK Cloud Service toujours mis à jour avec les dernières améliorations du Cloud Service permet un développement local directement à l’aide du matériel local du développeur. Cela permet un développement rapide avec des temps de réponse très faibles. Ainsi, les développeurs peuvent rester dans leur environnement local familier et choisir parmi une grande variété d’outils de développement, et pousser vers les environnements de développement ou de production lorsqu’ils le jugent approprié.

Cloud Manager prend en charge des configurations multi-équipes flexibles qui peuvent être ajustées en fonction des besoins d’une entreprise. Cela s’applique aussi bien à Cloud Service qu’à AMS. Pour garantir des déploiements stables avec plusieurs équipes et éviter qu’une seule équipe n’impacte la production pour toutes les équipes, les responsables du cloud ont toujours approuvé le pipeline qui valide et teste le code de toutes les équipes ensemble.


## Exemple de monde réel {#real-world-example}

Chaque entreprise a des exigences différentes, notamment la configuration, les processus et les workflows de développement de l’équipe. La configuration décrite ci-dessous est utilisée par Adobe pour plusieurs projets qui offrent des expériences en plus d’AEM en tant que Cloud Service.

Par exemple, les applications Adobe Creative Cloud, telles qu’Adobe Photoshop ou Adobe Illustrator, incluent des ressources de contenu telles que des tutoriels, des exemples et des guides à la disposition des utilisateurs finaux. Ce contenu est consommé par les applications clientes à l’aide d’AEM en tant que Cloud Service de manière *headless*, en effectuant des appels d’API vers le niveau de publication d’AEM Cloud pour récupérer le contenu structuré en flux JSON, et en exploitant le [réseau de diffusion de contenu (CDN) d’en tant que Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=fr#content-delivery) pour offrir des performances optimales au contenu structuré et non structuré.

Les équipes qui contribuent à ce projet suivent le processus décrit ci-après.

>[!NOTE]
>Pour en savoir plus sur la configuration, voir [Utilisation de plusieurs référentiels Git source](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html#managing-code) .

Chaque équipe utilise son propre workflow de développement et dispose d’un référentiel git distinct. Un référentiel git partagé supplémentaire est utilisé pour l’intégration de projets. Ce référentiel git contient la structure racine du référentiel git de Cloud Manager, y compris la configuration du Dispatcher partagé. L’intégration d’un nouveau projet nécessite une liste dans le fichier de projet Maven Reactor à la racine du référentiel Git partagé. Pour la configuration du Dispatcher, un nouveau fichier de configuration est créé dans le projet du Dispatcher. Ce fichier est ensuite inclus par la configuration Dispatcher principale. Chaque équipe est responsable de son propre fichier de configuration de Dispatcher. Les modifications apportées au référentiel git partagé sont rares et ne sont généralement requises que lorsqu’un nouveau projet est intégré. Le travail principal est effectué par chaque équipe de projet dans son propre référentiel git.

![](assets/team-setup1.png)

Le référentiel git pour chaque équipe a été configuré à l’aide de l’archétype Maven AEM et suit donc les bonnes pratiques pour configurer AEM projets. La seule exception concerne la gestion de la configuration du Dispatcher qui est effectuée dans le référentiel git partagé, comme indiqué ci-dessus.
Chaque équipe utilise un workflow Git simplifié avec deux branches + N, suivant le modèle de flux Git :

* Une branche de version stable contient le code de production.

* Une branche de développement contient le dernier développement

* Pour chaque fonctionnalité, une nouvelle branche est créée.


Le développement est effectué dans une branche de fonctionnalités, lorsque celle-ci se développe, elle est fusionnée dans la branche de développement. Les fonctionnalités terminées et validées sont sélectionnées à partir de la branche de développement et fusionnées dans la branche stable. Toutes les modifications sont effectuées par le biais des demandes d’extraction (PR). Chaque requête de tirage est automatiquement validée par les points de contrôle qualité. Sonar est utilisé pour la vérification de la qualité du code et un ensemble de suites de tests est exécuté pour s’assurer que le nouveau code n’introduit aucune régression.

La configuration du référentiel git de Cloud Manager comporte deux branches :

* Une *branche de version stable*, contenant le code de production de toutes les équipes
* Une *branche de développement*, contenant le code de développement de toutes les équipes

Chaque notification push vers le référentiel git d’une équipe dans le développement ou la branche stable déclenche une [action github](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html?lang=en#managing-code). Tous les projets suivent la même configuration pour la branche stable. Une notification push vers la branche stable d’un projet est automatiquement envoyée à la branche stable du référentiel git de Cloud Manager. Le pipeline de production dans Cloud Manager est configuré pour être déclenché par une notification push vers la branche stable. Le pipeline de production est donc exécuté par chaque notification push d’une équipe dans une branche stable et le déploiement en production est mis à jour si tous les points de contrôle qualité réussissent.

![](assets/team-setup2.png)

Les envois vers la branche de développement sont gérés différemment. Bien qu’une notification push envoyée à une branche de développement dans le référentiel git d’une équipe déclenche également une action github et que le code soit automatiquement envoyé à la branche de développement dans le référentiel git de Cloud Manager, le pipeline hors production n’est pas automatiquement déclenché par la notification push du code. Elle est déclenchée par un appel à l’api de Cloud Manager.
L’exécution du pipeline de production inclut la vérification du code de toutes les équipes via les points de contrôle qualité fournis. Une fois le code déployé dans l’environnement intermédiaire, les tests et les audits sont exécutés pour s’assurer que tout fonctionne comme prévu. Une fois tous les points de contrôle passés, les modifications sont déployées en production sans interruption ni interruption.
Pour le développement local, le [SDK pour AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=fr#developing) est utilisé. Le SDK permet de configurer un auteur, une publication et un dispatcher locaux. Cela permet le développement hors ligne et des délais d’exécution rapides. Parfois, seul l’auteur est utilisé pour le développement, mais la configuration rapide du dispatcher et de la publication permet de tout tester localement avant de le transférer dans le référentiel git. Les membres de chaque équipe extraient généralement le code de la Git partagée ainsi que leur propre code de projet. Il n’est pas nécessaire de passer en revue d’autres projets car ceux-ci sont indépendants.

![](assets/team-setup3.png)

Cette configuration du monde réel peut être utilisée comme plan directeur, puis personnalisée selon les besoins d’une entreprise. Le concept flexible d’embranchement et de fusion de Git permet de créer des variantes des workflows ci-dessus, personnalisées selon les besoins de chaque équipe. AEM en tant que Cloud Service prend en charge toutes ces variations sans sacrifier la valeur de base du pipeline Cloud Manager opiniâtre.

### Considérations relatives à la configuration de plusieurs équipes {#considerations}

>[!NOTE]
>Pour toute configuration multi-équipe, il est essentiel de définir un modèle de gouvernance et un ensemble de normes que toutes les équipes doivent respecter. Le plan directeur décrit ci-dessus pour une configuration multi-équipes permet de mettre à l’échelle un plus grand nombre d’équipes et vous pouvez utiliser ce plan directeur comme point de départ.

Avec le référentiel git de Cloud Manager et le pipeline de production, le code de production complet est toujours exécuté par tous les points de contrôle qualité, le considérant comme une unité de déploiement. Ainsi, le système de production est toujours *activé* sans interruption ni temps d’arrêt.
En revanche, en l’absence d’un tel système, chaque équipe pouvant se déployer séparément, il est possible qu’une mise à jour d’une seule équipe entraîne des problèmes de stabilité de production. En outre, il nécessite une coordination et des temps d’arrêt planifiés pour déployer les mises à jour. Avec un nombre croissant d&#39;équipes, l&#39;effort de coordination deviendra beaucoup plus complexe et rapidement ingérable.

Si un problème est détecté dans les points de contrôle qualité, la production n&#39;est pas affectée, et le problème peut être détecté et corrigé sans que le personnel Adobe ne soit tenu de s&#39;y mêler. Sans Cloud Service et sans toujours tester l’ensemble du déploiement, les déploiements partiels peuvent entraîner des pannes nécessitant une demande de restauration ou même une restauration complète à partir d’une sauvegarde. Les essais partiels pourraient aussi entraîner d&#39;autres problèmes qui devront être résolus après avoir besoin à nouveau de la coordination et du soutien du personnel de l&#39;Adobe.
