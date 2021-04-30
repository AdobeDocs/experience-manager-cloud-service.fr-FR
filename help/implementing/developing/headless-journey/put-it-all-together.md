---
title: Comment tout assembler - Votre application et votre contenu sans AEM tête
description: Dans cette partie du Parcours AEM développeur sans tête, apprenez à prendre votre projet AEM, y compris les fragments de contenu, vos appels GraphQL, vos appels d'API REST et votre application, et à le préparer pour qu'il soit en direct.
hide: true
hidefromtoc: true
index: false
exl-id: 254fb9dd-36c8-43ce-aaea-ceb4d079503d
translation-type: tm+mt
source-git-commit: dc4f1e916620127ebf068fdcc6359041b49891cf
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 0%

---

# Comment tout assembler - Votre application et votre contenu sans en-tête {#put-it-all-together} AEM

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette partie du [AEM Parcours de développement sans tête,](overview.md) apprenez comment prendre votre projet AEM, y compris les fragments de contenu, vos appels GraphQL, vos appels d&#39;API REST et votre application, et comment le préparer pour la mise en service.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent du parcours sans tête AEM, [Comment mettre à jour votre contenu via les API AEM Assets](update-your-content.md) vous avez appris à mettre à jour votre contenu sans tête existant dans AEM via l&#39;API et vous devez maintenant :

* Comprenez l’API HTTP AEM Assets.

Cet article s&#39;appuie sur ces principes fondamentaux pour vous aider à préparer votre propre projet AEM sans tête pour qu&#39;il soit opérationnel.

## Intention {#objective}

* Installez AEM SDK pour obtenir un environnement d’exécution de développement local que vous pouvez utiliser pour tester votre contenu sur
* Découvrez les outils de développement dont vous avez besoin
* Testez votre code et votre contenu localement avant de passer en direct

## Processus de développement local {#the-local-development-workflow}

Le projet de développement local est construit sur Apache Maven et utilise Git pour le contrôle de code source. Pour mettre à jour le projet, les développeurs peuvent utiliser leur environnement de développement intégré préféré, tel que Eclipse, Visual Studio Code ou IntelliJ, entre autres.

Pour tester le code ou les mises à jour de contenu qui seront ingérées par votre application sans en-tête, vous devez déployer les mises à jour sur un environnement d’exécution AEM local, qui inclut les instances locales des instances d’AEM auteur et de publication.

Veillez à prendre note des distinctions entre chaque composant dans l’AEM d’exécution locale, car il est important de tester vos mises à jour là où elles comptent le plus - par exemple, testez les mises à jour de contenu sur l’auteur ou testez le nouveau code sur l’instance de publication.

Dans un système de production, un répartiteur et un serveur HTTP Apache s’assoient toujours devant une instance de publication AEM. Ils fournissent des services de mise en cache et de sécurité pour le système AEM. Il est donc essentiel de tester le code et les mises à jour de contenu par rapport au répartiteur.

Une fois que vous avez vérifié que tout a été testé et fonctionne correctement, vous êtes prêt à transmettre vos mises à jour de code à un référentiel Git centralisé dans Cloud Manager.

Une fois les mises à jour téléchargées dans Cloud Manager, elles peuvent être déployées en AEM Cloud Service à l’aide du pipeline de CI/CD de Cloud Manager.


## SDK AEM {#the-aem-sdk}

Le SDK AEM est utilisé pour créer et déployer du code personnalisé. Il contient les artefacts suivants :

* Le fichier JAR de démarrage rapide : fichier JAR exécutable qui peut être utilisé pour configurer à la fois un auteur et une instance de publication.
* Outils du répartiteur : module du répartiteur et ses dépendances pour les systèmes Windows et UNIX
* Jar API Java - Dépendance Java Jar/Maven qui expose toutes les API Java autorisées qui peuvent être utilisées pour le développement par rapport aux AEM
* Javadoc jar - les javadocs du jar API Java

## Configuration de l&#39;Environnement de développement local {#local-development-environment}

Afin de préparer votre projet AEM sans tête pour le lancement, vous devez vous assurer que tous les éléments constitutifs de votre projet fonctionnent bien.

Pour ce faire, vous devez tout assembler - code, contenu et configuration et le tester dans un environnement de développement local pour être prêt en direct.

L&#39;environnement de développement local comprend trois domaines principaux :

1. Le projet AEM - contient tout le code, la configuration et le contenu personnalisés sur lesquels les AEM développeurs vont travailler
1. L&#39;exécution locale de l&#39;AEM : versions locales des services d&#39;auteur et de publication AEM qui seront utilisés pour déployer le code du projet AEM
1. Exécution du répartiteur local : version locale du serveur Web htttpd Apache qui inclut le module Répartiteur

## Outils de développement {#development-tools}

Outre le SDK AEM, vous aurez besoin d’outils supplémentaires qui facilitent le développement et le test de votre code et contenu localement :

* Java
* Git
* Apache Maven
* Bibliothèque Node.js
* L&#39;IDE de votre choix

AEM étant une application Java, vous devez installer Java et le SDK Java pour prendre en charge le développement d’AEM en tant que Cloud Service.

Git est l’outil que vous utiliserez pour gérer le contrôle de code source et pour intégrer les modifications apportées à Cloud Manager, puis les déployer sur une instance de production.

AEM utilise Apache Maven pour construire des projets générés à partir de l&#39;archétype AEM Maven Project. Tous les principaux IDE offrent une prise en charge de l&#39;intégration pour Maven.

Node.js est un environnement d’exécution JavaScript utilisé pour traiter les ressources frontales du sous-projet ui.frontend d’un projet AEM. Node.js est distribué avec npm, est de facto le gestionnaire de package Node.js, utilisé pour gérer les dépendances JavaScript.

## Eléments suivants {#what-is-next}

Vous devriez continuer votre parcours AEM sans tête en passant en revue le document [Comment vivre avec votre application sans tête](go-live.md) où vous mettez en ligne votre projet AEM sans tête !

## Ressources supplémentaires {#additional-resources}

* [Configuration](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-dispatcher-runtime)  de l&#39;Environnement de développement local - Apprenez à installer les outils nécessaires au développement de débuts pour AEM
* [AEM en tant que SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)  Cloud Service - examinez en détail le SDK AEM