---
title: Tout assembler – Votre application et votre contenu dans AEM découplé
description: Dans cette partie du parcours de développement AEM découplé, découvrez comment aborder votre projet AEM, notamment les fragments de contenu, les appels GraphQL, les appels API REST et votre application, mais aussi comment préparer ce projet pour la mise en ligne.
exl-id: bece84ad-4c8c-410c-847e-9ef3f79970cb
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 100%

---

# Tout assembler – Votre application et votre contenu dans AEM découplé {#put-it-all-together}

Dans cette partie du [Parcours développeur découplé AEM](overview.md), vous vous familiariserez avec l’utilisation des outils de développement AEM et du SDK découplé pour assembler votre application.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent du parcours découplé AEM, [Comment mettre à jour votre contenu grâce aux API d’AEM Assets](update-your-content.md) vous avez appris à mettre à jour votre contenu découplé dans AEM à l’aide de l’API et vous devriez maintenant :

* comprendre comment fonctionne l’API HTTP d’AEM Assets.

## Objectif {#objective}

Cet article vise à vous aider à comprendre comment assembler votre application AEM découplé :

* En savoir plus sur le SDK AEM découplé et sur l’outil de développement requis
* Configuration d’un environnement d’exécution de développement local pour simuler votre contenu avant la mise en ligne
* Présentation des bases de la réplication de contenu AEM

## SDK AEM {#the-aem-sdk}

Le SDK AEM permet de créer et de déployer du code personnalisé. Il s’agit du principal outil dont vous avez besoin pour développer et tester votre application découplée avant sa mise en ligne. Il contient les artefacts suivants :

* Le jar Quickstart : fichier jar exécutable qui peut être utilisé pour configurer une instance d’auteur et une instance de publication.
* Les outils de dispatcher : le module Dispatcher et ses dépendances pour les systèmes Windows et UNIX®
* Le jar de l’API Java™ : dépendance Jar/Maven Java™ qui expose toutes les API Java™ autorisées pouvant être utilisées en vue de développer pour AEM
* Le jar Javadoc : javadocs du fichier jar de l’API Java™

## SDK découplé AEM {#the-aem-headless-sdk}

Différent du SDK AEM, le **SDK découplé** AEM est un ensemble de bibliothèques qui peuvent être utilisées par les clients pour interagir rapidement et facilement avec les API AEM découplé sur HTTP.

Pour plus d’informations, voir la section [SDK découplé AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/aem-headless-sdk.html?lang=fr).

## Outils de développement supplémentaires {#additional-development-tools}

Outre le SDK AEM, vous avez besoin d’outils supplémentaires qui facilitent le développement et le test local de votre code et de votre contenu :

* Java™
* Git
* Apache Maven
* La bibliothèque Node.js
* L’environnement de développement intégré (IDE) de votre choix

Comme AEM est une application Java™, vous devez installer Java™ et le SDK Java™ pour prendre en charge le développement d’AEM as a Cloud Service.

Utilisez le référentiel Git pour gérer le contrôle de code source et pour archiver les modifications apportées à Cloud Manager, puis pour les déployer sur une instance de production.

AEM utilise Apache Maven pour créer des projets générés à partir de l’archétype de projet AEM Maven. Tous les environnements de développement intégré majeurs prennent en charge l’intégration de Maven.

Node.js est un environnement d’exécution JavaScript utilisé pour fonctionner avec les ressources front-end du sous-projet `ui.frontend` d’un projet AEM. Node.js est distribué avec npm, qui est le gestionnaire de modules Node.js de facto utilisé pour gérer les dépendances JavaScript.

## Composants d’un système AEM en un coup d’œil {#components-of-an-aem-system-at-a-glance}

Regardons maintenant les éléments qui constituent un environnement AEM.

Un environnement d’AEM complet est constitué d’un auteur, d’une publication et d’un Dispatcher. Ces mêmes composants sont disponibles dans l’exécution de développement local afin de vous permettre de prévisualiser plus facilement votre code et votre contenu avant la mise en ligne.

* **Le service Auteur** permet aux utilisateurs internes de créer, gérer et prévisualiser du contenu.

* **Le service de publication** est considéré comme l’environnement « En ligne » et est généralement celui avec lequel les utilisateurs finaux interagissent. Le contenu, après avoir été modifié et approuvé sur le service Auteur, est distribué au service Publication. Le modèle de déploiement le plus courant avec les applications découplées d’AEM est de connecter la version de production de l’application à un service de publication d’AEM.

* **Le Dispatcher** est un serveur web statique qui est alimenté par le module Dispatcher d’AEM. Ce module met en cache les pages web produites par l’instance de publication pour améliorer les performances.

## Workflow de développement local {#the-local-development-workflow}

Le projet de développement local est basé sur Apache Maven et utilise Git pour le contrôle de code source. Pour mettre à jour le projet, les développeurs et développeuses peuvent utiliser leur environnement de développement intégré préféré, tel qu’Eclipse, Visual Studio Code ou IntelliJ, entre autres.

Pour tester le code ou les mises à jour de contenu ingérées par votre application découplée, vous devez déployer les mises à jour sur l’exécution locale AEM, qui inclut les instances locales des services de création et de publication AEM.

Veillez à tenir compte des différences entre chaque composant dans l’exécution locale AEM, car il est important de tester vos mises à jour là où elles comptent le plus. Par exemple, testez les mises à jour du contenu sur l’instance de création ou testez le nouveau code sur l’instance de publication.

Dans un système de production, un Dispatcher et un serveur Apache http se trouvent toujours en face d’une instance de publication AEM. Ils fournissent des services de mise en cache et de sécurité pour le système AEM. Il est donc essentiel de tester le code et les mises à jour de contenu par rapport au Dispatcher.

## Prévisualisation locale de votre code et de votre contenu avec l’environnement de développement local {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Pour préparer votre projet découplé AEM à son lancement, vous devez vous assurer que tous les éléments constituant votre projet fonctionnent correctement.

Pour cela, vous devez tout assembler (code, contenu et configuration), puis le tester dans un environnement de développement local pour vous préparer en temps réel.

L’environnement de développement local se compose de trois principaux éléments :

1. Le projet AEM : il contient tout le code personnalisé, la configuration et le contenu sur lesquels les développeurs AEM vont travailler.
1. L’exécution locale AEM : les versions locales des services de création et de publication AEM utilisés pour déployer le code du projet AEM.
1. L’exécution locale du Dispatcher : la version locale du serveur web Apache httpd qui comprend le module du Dispatcher.

Une fois l’environnement de développement local configuré, vous pouvez simuler la diffusion de contenu vers l’application React en déployant localement un serveur de nœuds statique.

<!-- THIS TOPIC IS 404. IT DOES NOT APPEAR IN THE TOC OR ANYWHERE ELSE To get a more in-depth look at setting up a local development environment and all dependencies needed for content preview, see [Production Deployment documentation](https://experienceleague.adobe.com/docs/experience-manager-learn/headless-tutorial/graphql/multi-step/production-deployment.html). -->

## Prochaines étapes {#whats-next}

Maintenant que vous avez terminé cette partie du parcours de développement découplé AEM, vous devriez pouvoir :

* Familiarisez-vous avec les outils de développement AEM
* Découvrez le workflow de développement local

Poursuivez votre parcours dans AEM découplé en consultant le document [Comment mettre en ligne votre application en mode découplé](/help/journey-headless/developer/go-live.md) dans lequel vous mettez en ligne votre projet AEM découplé !

## Ressources supplémentaires {#additional-resources}

* [SDK d’AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [Configurer un environnement AEM local](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html?lang=fr)
* [SDK AEM découplé pour les navigateurs côté client (JavaScript)](https://github.com/adobe/aem-headless-client-js)
* [SDK AEM découplé pour les Node.js côté serveur (JavaScript)](https://github.com/adobe/aem-headless-client-nodejs)
* [SDK AEM découplé pour Java™](https://github.com/adobe/aem-headless-client-java)
* [Présentation d’AEM en tant que CMS découplé](/help/headless/introduction.md)
* [Portail de développement d’AEM ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=fr)
* [Tutoriels pour le découplage dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr)
