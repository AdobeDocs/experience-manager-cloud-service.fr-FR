---
title: Comment vivre avec votre application sans en-tête
description: Dans cette partie du Parcours AEM de développement sans tête, apprenez comment déployer une application sans tête en direct en emportant votre code local dans Git et en le déplaçant vers Cloud Manager Git pour le pipeline CI/CD.
hide: true
hidefromtoc: true
index: false
exl-id: f79b5ada-8f59-4706-9f90-bc63301b2b7d
source-git-commit: 7c30a7415cc424e7f417d92bad9eeb01877994d2
workflow-type: tm+mt
source-wordcount: '1829'
ht-degree: 2%

---

# Comment vivre avec votre application sans en-tête {#go-live}

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette partie du [Parcours de développement AEM sans en-tête](overview.md), apprenez à déployer une application sans en-tête en direct en emportant votre code local dans Git et en le déplaçant vers Cloud Manager Git pour le pipeline CI/CD.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent du parcours sans tête AEM, [Comment mettre à jour votre contenu via les API AEM Assets](update-your-content.md) vous avez appris à mettre à jour votre contenu sans tête existant dans AEM via l&#39;API et vous devez maintenant :

* Comprenez l’API HTTP AEM Assets.

Cet article s&#39;appuie sur ces principes fondamentaux pour vous aider à préparer votre propre projet AEM sans tête pour qu&#39;il soit opérationnel.

## Intention {#objective}

Ce document vous aide à comprendre l&#39;AEM canal de publication sans en-tête et les considérations de performances dont vous devez tenir compte avant de commencer à utiliser votre application.

* Découvrez l’AEM SDK et l’outil de développement requis
* Configuration d’un environnement d’exécution de développement local pour simuler votre contenu avant de le publier
* Comprendre les bases de la réplication et de la mise en cache du contenu AEM
* Sécurisation et mise à l’échelle de votre application avant le lancement
* Surveillance des performances et débogage

## SDK AEM {#the-aem-sdk}

Le SDK AEM est utilisé pour créer et déployer du code personnalisé. C&#39;est l&#39;outil principal dont vous avez besoin pour développer et tester votre application sans tête avant de passer en ligne. Il contient les artefacts suivants :

* Le fichier JAR de démarrage rapide : fichier JAR exécutable qui peut être utilisé pour configurer à la fois un auteur et une instance de publication.
* Outils du répartiteur : module du répartiteur et ses dépendances pour les systèmes Windows et UNIX
* Jar API Java - Dépendance Java Jar/Maven qui expose toutes les API Java autorisées qui peuvent être utilisées pour le développement par rapport aux AEM
* Javadoc jar - les javadocs du jar API Java

## Outils de développement supplémentaires {#additional-development-tools}

Outre le SDK AEM, vous aurez besoin d’outils supplémentaires qui facilitent le développement et le test de votre code et contenu localement :

* Java
* Git
* Apache Maven
* Bibliothèque Node.js
* L&#39;IDE de votre choix

AEM étant une application Java, vous devez installer Java et le SDK Java pour prendre en charge le développement d’AEM en tant que Cloud Service.

Git est ce que vous utiliserez pour gérer le contrôle de code source et pour intégrer les modifications apportées à Cloud Manager, puis les déployer sur une instance de production.

AEM utilise Apache Maven pour construire des projets générés à partir de l&#39;archétype AEM Maven Project. Tous les principaux IDE offrent une prise en charge de l&#39;intégration pour Maven.

Node.js est un environnement d’exécution JavaScript utilisé pour travailler avec les actifs frontaux d’un sous-projet `ui.frontend` d’un projet AEM. Node.js est distribué avec npm, est de facto le gestionnaire de package Node.js, utilisé pour gérer les dépendances JavaScript.

## Composants d&#39;un système AEM en un coup d&#39;oeil {#components-of-an-aem-system-at-a-glance}

Ensuite, jetons un coup d&#39;oeil aux parties constitutives d&#39;un environnement AEM.

Un environnement AEM complet est constitué d’un auteur, d’une publication et d’un répartiteur. Ces mêmes composants seront rendus disponibles dans l’exécution de développement local afin de vous permettre de prévisualisation plus facilement de votre code et de votre contenu avant de commencer à travailler.

* **Ce** service permet aux utilisateurs internes de créer, gérer et prévisualisation du contenu.

* **Le** service de publication est considéré comme l’environnement &quot;en direct&quot; et est généralement utilisé par les utilisateurs finaux pour interagir. Le contenu, après avoir été modifié et approuvé sur le service Auteur, est distribué au service Publication. Le modèle de déploiement le plus courant avec AEM applications sans en-tête consiste à faire en sorte que la version de production de l’application se connecte à un service de publication AEM.

* **Le** Dispatcher est un serveur Web statique auquel s&#39;ajoute le module de répartiteur d&#39;AEM. Ce module met en cache les pages web produites par l’instance de publication pour améliorer les performances.

## Processus de développement local {#the-local-development-workflow}

Le projet de développement local est construit sur Apache Maven et utilise Git pour le contrôle de code source. Pour mettre à jour le projet, les développeurs peuvent utiliser leur environnement de développement intégré préféré, tel que Eclipse, Visual Studio Code ou IntelliJ, entre autres.

Pour tester le code ou les mises à jour de contenu qui seront ingérées par votre application sans en-tête, vous devez déployer les mises à jour sur l’exécution AEM locale, qui inclut les instances locales des services AEM d’auteur et de publication.

Veillez à prendre note des distinctions entre chaque composant dans l’AEM d’exécution locale, car il est important de tester vos mises à jour là où elles comptent le plus. Par exemple, testez les mises à jour de contenu sur l’auteur ou testez le nouveau code sur l’instance de publication.

Dans un système de production, un répartiteur et un serveur HTTP Apache s’assoient toujours devant une instance de publication AEM. Ils fournissent des services de mise en cache et de sécurité pour le système AEM. Il est donc essentiel de tester le code et les mises à jour de contenu par rapport au répartiteur.

## Aperçu de votre code et de votre contenu localement avec l’Environnement de développement local {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Afin de préparer votre projet AEM sans tête pour le lancement, vous devez vous assurer que tous les éléments constitutifs de votre projet fonctionnent bien.

Pour ce faire, il faut tout assembler : le code, le contenu et la configuration et testez-le dans un environnement de développement local afin d’être prêt à l’emploi.

L&#39;environnement de développement local comprend trois domaines principaux :

1. Le projet AEM - contient tout le code, la configuration et le contenu personnalisés sur lesquels les AEM développeurs vont travailler
1. L&#39;exécution locale de l&#39;AEM : versions locales des services d&#39;auteur et de publication AEM qui seront utilisés pour déployer le code du projet AEM
1. Exécution du répartiteur local : version locale du serveur Web htttpd Apache qui inclut le module Répartiteur

Une fois l’environnement de développement local configuré, vous pouvez simuler le contenu diffusé dans l’application React en déployant localement un serveur de noeud statique.

Pour obtenir une analyse plus approfondie de la configuration d’un environnement de développement local et de toutes les dépendances nécessaires à la prévisualisation du contenu, voir [Documentation sur le déploiement de la production](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/production-deployment.html?lang=en#prerequisites).

## Préparation de votre demande AEM sans en-tête pour Go-Live {#prepare-your-aem-headless-application-for-golive}

Il est maintenant temps de préparer votre AEM application sans tête pour le lancement, en suivant les meilleures pratiques décrites ci-dessous.

### Sécuriser et mettre à l’échelle votre application sans en-tête avant le lancement {#secure-and-scale-before-launch}

1. Configurer [l&#39;authentification basée sur un jeton](/help/assets/content-fragments/graphql-authentication-content-fragments.md) avec vos requêtes GraphQL
1. Configurez [Mise en cache](/help/implementing/dispatcher/caching.md).

### Structure du modèle par rapport à la sortie GraphQL {#structure-vs-output}

* Evitez de créer des requêtes qui génèrent plus de 15 kb de JSON (gzip compressé). Les fichiers JSON longs nécessitent beaucoup de ressources pour être analysés par l’application cliente.
* Evitez plus de cinq niveaux imbriqués de hiérarchies de fragments. Les niveaux supplémentaires rendent difficile pour les auteurs de contenu de tenir compte de l’impact de leurs modifications.
* Utilisez des requêtes à plusieurs objets au lieu de modéliser des requêtes avec des hiérarchies de dépendance dans les modèles. Cela permet une plus grande flexibilité à long terme pour restructurer la sortie JSON sans avoir à effectuer de nombreuses modifications de contenu.

### Maximiser le taux d’accès au cache CDN {#maximize-cdn}

* N&#39;utilisez pas de requêtes GraphQL directes, sauf si vous demandez du contenu en direct à la surface.
   * Utilisez des requêtes persistantes chaque fois que possible.
   * Fournissez un TTL CDN supérieur à 600 secondes pour que le CDN puisse les mettre en cache.
   * AEM peut calculer l&#39;impact d&#39;un changement de modèle sur les requêtes existantes.
* Fractionner les fichiers JSON/requêtes GraphQL entre un taux de changement de contenu faible et élevé afin de réduire le trafic client sur le réseau de diffusion de contenu et d’affecter un TTL plus élevé. Cela permet de réduire le nombre de CDN lors de la revalidation du fichier JSON avec le serveur d’origines.
* Pour invalider activement le contenu du réseau de diffusion de contenu, utilisez la fonction Purger à l’aide de l’option Purger à l’aide de l’écran. Cela permet au CDN de retélécharger le contenu sans provoquer l’échec du cache.

### Amélioration du temps de téléchargement du contenu sans en-tête {#improve-download-time}

* Assurez-vous que les clients HTTP utilisent HTTP/2.
* Assurez-vous que les clients HTTP acceptent les en-têtes de demande de gzip.
* Réduisez le nombre de domaines utilisés pour héberger JSON et les artefacts référencés.
* Tirez parti de `Last-modified-since` pour actualiser les ressources.
* Utilisez la sortie `_reference` du fichier JSON pour début de télécharger des fichiers sans avoir à analyser les fichiers JSON complets.

## Déploiement en environnement de production {#deploy-to-production}

Une fois que vous avez vérifié que tout a été testé et fonctionne correctement, vous êtes prêt à transmettre vos mises à jour de code à un [référentiel Git centralisé dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html).

Une fois les mises à jour téléchargées dans Cloud Manager, elles peuvent être déployées en tant que Cloud Service à l’AEM à l’aide du [pipeline CI/CD de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=fr).

Vous pouvez début le déploiement de votre code en exploitant le pipeline de CD/CI de Cloud Manager, qui est traité en détail [ici](/help/implementing/deploying/overview.md).

## Surveillance des performances {#performance-monitoring}

Pour que les utilisateurs puissent bénéficier d’une expérience optimale lors de l’utilisation de l’application AEM sans en-tête, il est important de surveiller les mesures de performances clés, comme indiqué ci-dessous :

* Validation des versions de prévisualisation et de production de l’application
* Vérifier les pages d&#39;état AEM pour l&#39;état actuel de disponibilité du service
* Accès aux rapports de performances
   * Performances des diffusions
      * Performances du CDN (Fastly) : contrôle du nombre d&#39;appels, du taux de cache, des taux d&#39;erreur et du trafic de charge utile
      * Serveurs d&#39;Origine : nombre d&#39;appels, taux d&#39;erreur, charges d&#39;UC, trafic de charge
   * Performances de l’auteur
      * Vérifier le nombre d’utilisateurs, de requêtes et de chargements
* Accès aux rapports de performances spécifiques à l’application et à l’espace
   * Une fois le serveur opérationnel, vérifiez si les mesures générales sont vertes/orange/rouges, puis identifiez les problèmes spécifiques à l’application.
   * Ouvrir les mêmes rapports que ceux ci-dessus filtrés dans l’application ou l’espace (par exemple, bureau Photoshop, paywall)
   * Utiliser les API du journal Splunk pour accéder aux performances du service et de l&#39;application
   * Contactez l’assistance clientèle si d’autres problèmes se produisent.

## Résolution des problèmes {#troubleshooting}

### Débogage {#debugging}

Suivez ces bonnes pratiques en tant qu’approche générale du débogage :

* Valider les fonctionnalités et les performances avec la version prévisualisation de l’application
* Valider les fonctionnalités et les performances avec la version de production de l’application
* Validation avec la prévisualisation JSON de l’éditeur de fragments de contenu
* Inspect le fichier JSON dans l’application cliente pour vérifier la présence de problèmes d’application ou de diffusion client
* Inspect le fichier JSON à l’aide de GraphQL pour vérifier la présence de problèmes liés au contenu ou à l’AEM mis en cache

### Journalisation d&#39;un bogue avec prise en charge {#logging-a-bug-with-support}

Pour consigner efficacement un bogue avec l&#39;assistance au cas où vous auriez besoin d&#39;aide supplémentaire, procédez comme suit :

* Si nécessaire, prenez des captures d&#39;écran du problème.
* Document d’un moyen de reproduire le problème
* Document du contenu avec lequel la publication se reproduit
* Consignez un problème sur le portail d&#39;assistance AEM avec la priorité appropriée.

## Le Parcours Se Termine - Ou Est-Ce Le Cas ? {#journey-ends}

Félicitations ! Vous avez terminé le Parcours AEM développement sans tête ! Vous devez maintenant comprendre :

* Différence entre la diffusion de contenu sans en-tête et avec en-tête.
* AEM fonctionnalités sans tête.
* Comment organiser et AEM projet sans tête.
* Comment créer du contenu sans en-tête en AEM.
* Comment récupérer et mettre à jour du contenu sans en-tête dans AEM.
* Comment vivre avec un projet AEM sans tête.
* Que faire après le lancement.

## Ressources supplémentaires {#additional-resources}

* [Présentation du déploiement sur AEM en tant que Cloud Service](/help/implementing/deploying/overview.md)
* [SDK d’AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [Configuration D’Un Environnement D’AEM Local](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)
* [Utilisation de Cloud Manager pour déployer votre code](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)
* [Intégration du référentiel Git de Cloud Manager à un référentiel Git externe et déploiement d’un projet AEM en tant que Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html)