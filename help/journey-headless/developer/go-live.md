---
title: Comment passer à l’application sans affichage
description: Dans cette partie du Parcours de développement AEM sans interface utilisateur, apprenez à déployer une application sans interface utilisateur en direct en prenant votre code local dans Git et en le déplaçant vers Cloud Manager Git pour le pipeline CI/CD.
source-git-commit: 8e96827f9353d6ffdf1e01645f2bc8bdaac2610f
workflow-type: tm+mt
source-wordcount: '1907'
ht-degree: 2%

---


# Comment passer à l’application sans affichage {#go-live}

Dans cette partie du [Parcours de développement AEM sans affichage](overview.md), apprenez à déployer une application sans interface en direct en prenant votre code local dans Git et en le déplaçant vers Cloud Manager Git pour le pipeline CI/CD.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent du parcours sans interface utilisateur AEM, [Comment mettre à jour votre contenu via les API AEM Assets](update-your-content.md) vous avez appris à mettre à jour votre contenu sans interface utilisateur à AEM via l’API et vous devez maintenant :

* Comprendre l’API HTTP AEM Assets.

Cet article s’appuie sur ces principes de base pour que vous compreniez comment préparer votre propre projet AEM sans tête pour qu’il passe en ligne.

## Intention {#objective}

Ce document vous aide à comprendre le pipeline de publication sans interface utilisateur AEM et les considérations de performances que vous devez connaître avant de passer en ligne avec votre application.

* En savoir plus sur le SDK AEM et sur l’outil de développement requis
* Configuration d’un environnement d’exécution de développement local pour simuler votre contenu avant la mise en ligne
* Présentation des notions de base sur la réplication et la mise en cache du contenu AEM
* Sécurisez et mettez à l’échelle votre application avant Launch
* Surveillance des performances et du débogage

## SDK AEM {#the-aem-sdk}

Le SDK AEM est utilisé pour créer et déployer du code personnalisé. Il s’agit de l’outil principal dont vous avez besoin pour développer et tester votre application sans interface avant sa mise en ligne. Il contient les artefacts suivants :

* Quickstart jar : fichier jar exécutable qui peut être utilisé pour configurer une instance d’auteur et une instance de publication.
* Outils de Dispatcher : module de Dispatcher et ses dépendances pour les systèmes Windows et UNIX
* Java API Jar : dépendance Java Jar/Maven qui expose toutes les API Java autorisées pouvant être utilisées pour le développement par rapport à AEM.
* Javadoc jar : javadocs du jar de l’API Java

## Outils de développement supplémentaires {#additional-development-tools}

Outre le SDK AEM, vous avez besoin d’outils supplémentaires qui facilitent le développement et le test local de votre code et contenu :

* Java
* Git
* Apache Maven
* Bibliothèque Node.js
* L’IDE de votre choix

Comme AEM est une application Java, vous devez installer Java et le SDK Java pour prendre en charge le développement d’AEM en tant que Cloud Service.

Git est ce que vous utiliserez pour gérer le contrôle de code source et pour archiver les modifications apportées à Cloud Manager, puis les déployer sur une instance de production.

AEM utilise Apache Maven pour créer des projets générés à partir de l’archétype de projet AEM Maven. Tous les principaux IDE prennent en charge l’intégration de Maven.

Node.js est un environnement d’exécution JavaScript utilisé pour fonctionner avec les ressources front-end du sous-projet `ui.frontend` d’un projet AEM. Node.js est distribué avec npm, qui est de facto le gestionnaire de modules Node.js utilisé pour gérer les dépendances JavaScript.

## Composants d’un système AEM en un coup d’oeil {#components-of-an-aem-system-at-a-glance}

Regardons ensuite les parties constituantes d&#39;un environnement AEM.

Un environnement d’AEM complet est constitué d’un auteur, d’une publication et d’un Dispatcher. Ces mêmes composants seront disponibles dans l’exécution de développement local afin de vous permettre de prévisualiser plus facilement votre code et votre contenu avant la mise en ligne.

* **Le** service Auteur permet aux utilisateurs internes de créer, gérer et prévisualiser du contenu.

* **Le** service de publication est considéré comme l’environnement &quot;En ligne&quot; et est généralement ce avec lequel les utilisateurs finaux interagissent. Le contenu, après avoir été modifié et approuvé sur le service Auteur, est distribué au service Publication. Le modèle de déploiement le plus courant avec AEM applications sans interface utilisateur est de se connecter à la version de production de l’application à un service de publication AEM.

* **Dispatcher** est un serveur web statique qui est alimenté par le module Dispatcher d’AEM. Ce module met en cache les pages web produites par l’instance de publication pour améliorer les performances.

## Workflow de développement local {#the-local-development-workflow}

Le projet de développement local est basé sur Apache Maven et utilise Git pour le contrôle de code source. Pour mettre à jour le projet, les développeurs peuvent utiliser leur environnement de développement intégré préféré, tel qu’Eclipse, Visual Studio Code ou IntelliJ, entre autres.

Pour tester le code ou les mises à jour de contenu qui seront ingérées par votre application sans interface utilisateur, vous devez déployer les mises à jour sur le runtime AEM local, qui inclut les instances locales des services de création et de publication AEM.

Veillez à tenir compte des différences entre chaque composant dans l’exécution AEM locale, car il est important de tester vos mises à jour là où elles comptent le plus. Par exemple, testez les mises à jour du contenu sur l’instance de création ou testez le nouveau code sur l’instance de publication.

Dans un système de production, un dispatcher et un serveur Apache http se trouvent toujours devant une instance de publication AEM. Ils fournissent des services de mise en cache et de sécurité pour le système AEM. Il est donc essentiel de tester le code et les mises à jour de contenu par rapport au dispatcher.

## Aperçu local de votre code et du contenu avec l’environnement de développement local {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Pour préparer votre projet sans interface AEM pour le lancement, vous devez vous assurer que toutes les parties constituantes de votre projet fonctionnent correctement.

Pour cela, vous devez tout assembler : code, contenu et configuration, puis testez-le dans un environnement de développement local pour vous préparer en temps réel.

L&#39;environnement de développement local se compose de trois axes :

1. Le projet AEM : contient tout le code personnalisé, la configuration et le contenu sur lesquels les développeurs AEM vont travailler.
1. Exécution locale de l’AEM : versions locales des services d’auteur et de publication AEM qui seront utilisés pour déployer le code du projet AEM
1. Exécution locale de Dispatcher : version locale du serveur web Apache httpd qui comprend le module de Dispatcher.

Une fois l’environnement de développement local configuré, vous pouvez simuler la diffusion de contenu vers l’application React en déployant localement un serveur de noeuds statique.

Pour plus d’informations sur la configuration d’un environnement de développement local et sur toutes les dépendances nécessaires à l’aperçu du contenu, voir [Documentation sur le déploiement en production](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/production-deployment.html?lang=en#prerequisites).

## Préparation de votre application AEM sans affichage pour la mise en service {#prepare-your-aem-headless-application-for-golive}

Il est maintenant temps de préparer votre application AEM sans interface pour le lancement, en suivant les bonnes pratiques décrites ci-dessous.

### Sécurisez et mettez à l’échelle votre application sans affichage avant le lancement {#secure-and-scale-before-launch}

1. Configuration de l’[authentification basée sur les jetons](/help/assets/content-fragments/graphql-authentication-content-fragments.md) avec vos requêtes GraphQL
1. Configurez la [mise en cache](/help/implementing/dispatcher/caching.md).

### Structure du modèle par rapport à la sortie GraphQL {#structure-vs-output}

* Évitez de créer des requêtes qui génèrent plus de 15 ko de JSON (fichier compressé gzip). Les fichiers JSON longs consomment beaucoup de ressources pour que l’application cliente puisse les analyser.
* Évitez plus de cinq niveaux imbriqués de hiérarchies de fragments. Les niveaux supplémentaires rendent difficile la prise en compte de l’impact de leurs modifications par les auteurs de contenu.
* Utilisez des requêtes à plusieurs objets au lieu de modéliser des requêtes avec des hiérarchies de dépendances au sein des modèles. Cela offre une plus grande flexibilité à long terme pour restructurer la sortie JSON sans avoir à effectuer de nombreuses modifications de contenu.

### Maximiser le ratio cache-accès CDN {#maximize-cdn}

* N’utilisez pas de requêtes GraphQL directes, sauf si vous demandez du contenu en direct à la surface.
   * Dans la mesure du possible, utilisez des requêtes persistantes.
   * Fournissez un TTL CDN supérieur à 600 secondes pour que le CDN les mette en cache.
   * AEM peut calculer l’impact d’une modification de modèle sur des requêtes existantes.
* Partage des fichiers JSON/requêtes GraphQL entre un taux de changement de contenu faible et élevé afin de réduire le trafic client sur le réseau de diffusion de contenu et d’attribuer un TTL plus élevé. Cela minimise la revalidation du réseau de diffusion de contenu du fichier JSON avec le serveur d’origine.
* Pour invalider activement le contenu du réseau de diffusion de contenu, utilisez la fonction Purge progressive. Cela permet au réseau de diffusion de contenu de télécharger à nouveau le contenu sans provoquer l’échec du cache.

### Amélioration du temps de téléchargement du contenu sans affichage {#improve-download-time}

* Assurez-vous que les clients HTTP utilisent HTTP/2.
* Assurez-vous que les clients HTTP acceptent la requête d’en-têtes pour gzip.
* Réduisez le nombre de domaines utilisés pour héberger les artefacts JSON et référencés.
* Utilisez `Last-modified-since` pour actualiser les ressources.
* Utilisez la sortie `_reference` du fichier JSON pour commencer à télécharger des ressources sans avoir à analyser les fichiers JSON complets.

## Déploiement en environnement de production {#deploy-to-production}

Une fois que vous avez vérifié que tout a été testé et fonctionne correctement, vous êtes prêt à envoyer vos mises à jour de code vers un [référentiel Git centralisé dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html).

Une fois les mises à jour transférées vers Cloud Manager, elles peuvent être déployées vers AEM en tant que Cloud Service à l’aide du [pipeline CI/CD de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=fr).

Vous pouvez commencer à déployer votre code en exploitant le pipeline CI/CD de Cloud Manager, qui est décrit en détail [ici](/help/implementing/deploying/overview.md).

## Surveillance des performances {#performance-monitoring}

Pour que les utilisateurs disposent de la meilleure expérience possible lorsqu’ils utilisent AEM application sans interface utilisateur, il est important de surveiller les mesures de performances clés, comme indiqué ci-dessous :

* Validation des versions d’aperçu et de production de l’application
* Vérifier les pages d’état AEM de l’état actuel de disponibilité du service
* Accès aux rapports de performance
   * Performances des diffusions
      * Performances du réseau de diffusion de contenu (Fastly) : vérifiez le nombre d’appels, le taux de mise en cache, les taux d’erreur et le trafic de charge utile.
      * Serveurs d’origine : nombre d’appels, taux d’erreur, charge du processeur, trafic de charge utile.
   * Performances de création
      * Vérifier le nombre d’utilisateurs, de demandes et de chargements
* Accès aux rapports de performances spécifiques à l’application et à l’espace
   * Une fois le serveur ouvert, vérifiez si les mesures générales sont vert/orange/rouge, puis identifiez les problèmes spécifiques à l’application.
   * Ouvrir les mêmes rapports ci-dessus filtrés dans l’application ou l’espace (par exemple, bureau Photoshop, paywall)
   * Utilisation des API de journal Splunk pour accéder aux performances du service et de l’application
   * Contactez le service clientèle si d’autres problèmes se produisent.

## Résolution des problèmes {#troubleshooting}

### Débogage {#debugging}

Suivez ces bonnes pratiques en tant qu’approche générale du débogage :

* Validation des fonctionnalités et des performances avec la version d’aperçu de l’application
* Validation des fonctionnalités et des performances avec la version de production de l’application
* Validation à l’aide de l’aperçu JSON de l’éditeur de fragment de contenu
* Inspect du JSON dans l’application cliente pour vérifier la présence de problèmes d’application cliente ou de diffusion
* Inspect du JSON à l’aide de GraphQL pour vérifier la présence de problèmes liés au contenu mis en cache ou à l’AEM

### Journalisation d’un bogue avec prise en charge {#logging-a-bug-with-support}

Pour consigner efficacement un bogue avec l’assistance si vous avez besoin d’aide supplémentaire, procédez comme suit :

* Si nécessaire, réalisez des captures d’écran du problème.
* Documenter un moyen de reproduire le problème
* Documenter le contenu reproduit par le problème
* Consignez un problème via le portail d’assistance AEM avec la priorité appropriée.

## Le Parcours Se Termine - Ou Le Fait-Il ? {#journey-ends}

Félicitations ! Vous avez terminé le Parcours de développement AEM sans tête ! Vous devez maintenant comprendre les éléments suivants :

* Différence entre diffusion de contenu sans interface utilisateur graphique et en mode plein écran.
* AEM fonctionnalités sans interface.
* Comment organiser et AEM un projet sans affichage.
* Comment créer du contenu sans interface dans AEM.
* Comment récupérer et mettre à jour du contenu sans affichage dans AEM.
* Mise en ligne d’un projet AEM sans affichage.
* Que faire après la mise en service.

Vous avez déjà lancé votre premier projet AEM sans affichage ou vous disposez maintenant de toutes les connaissances nécessaires pour le faire. Super boulot !

### Exploration des applications d’une seule page {#explore-spa}

Les magasins sans tête d&#39;AEM n&#39;ont pourtant pas besoin de s&#39;arrêter ici. Vous vous souvenez peut-être dans la section [Prise en main du parcours](getting-started.md#integration-levels) que nous avons brièvement expliqué comment AEM non seulement prend en charge la livraison sans interface utilisateur et les modèles complets traditionnels, mais peut également prendre en charge les modèles hybrides qui combinent les avantages des deux.

Si ce type de flexibilité est nécessaire pour votre projet, passez à la partie facultative supplémentaire du parcours [Comment créer des applications d’une seule page (SPA) avec AEM.](create-spa.md)

## Ressources supplémentaires {#additional-resources}

* [Présentation du déploiement sur AEM en tant que Cloud Service](/help/implementing/deploying/overview.md)
* [SDK d’AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [Configuration D’Un Environnement AEM Local](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)
* [Utilisation de Cloud Manager pour déployer votre code](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)
* [Intégration du référentiel Git de Cloud Manager à un référentiel Git externe et déploiement d’un projet AEM en tant que Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html)
