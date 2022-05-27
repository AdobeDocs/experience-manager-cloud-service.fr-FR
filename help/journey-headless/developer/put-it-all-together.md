---
title: Tout assembler – Votre application et votre contenu dans AEM découplé
description: Dans cette partie du parcours de développement AEM découplé, découvrez comment aborder votre projet AEM, notamment les fragments de contenu, les appels GraphQL, les appels API REST et votre application, mais aussi comment préparer ce projet pour la mise en ligne.
exl-id: bece84ad-4c8c-410c-847e-9ef3f79970cb
source-git-commit: 270eb35023e34eed2cd17674372794c6c2cc7757
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 53%

---

# Tout assembler – Votre application et votre contenu dans AEM découplé {#put-it-all-together}

Dans cette partie du [AEM Parcours développeur sans tête](overview.md), vous familiarisez-vous avec l’utilisation des outils de développement AEM et du SDK Headless pour assembler votre application.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent du parcours découplé AEM, [Comment mettre à jour votre contenu grâce aux API d’AEM Assets](update-your-content.md) vous avez appris à mettre à jour votre contenu découplé dans AEM à l’aide de l’API et vous devriez maintenant :

* comprendre comment fonctionne l’API HTTP d’AEM Assets.

## Objectif {#objective}

Cet article vise à vous aider à comprendre comment assembler votre application AEM sans interface utilisateur :

* En savoir plus sur le SDK AEM sans affichage et les outils de développement requis
* Configuration d’un environnement d’exécution de développement local pour simuler votre contenu avant la mise en ligne
* Présentation des bases de la réplication de contenu AEM

## SDK AEM {#the-aem-sdk}

Le SDK AEM permet de créer et de déployer du code personnalisé. Il s’agit de l’outil principal dont vous avez besoin pour développer et tester votre application sans interface avant de la mettre en ligne. Il contient les artefacts suivants :

* Le jar Quickstart : fichier jar exécutable qui peut être utilisé pour configurer une instance d’auteur et une instance de publication.
* Outils de Dispatcher : module de Dispatcher et ses dépendances pour les systèmes Windows et UNIX®
* Java™ API Jar : dépendance Java™ Jar/Maven qui expose toutes les API Java™ autorisées pouvant être utilisées pour le développement par rapport à AEM
* Javadoc jar : javadocs du jar de l’API Java™.

## SDK AEM sans affichage {#the-aem-headless-sdk}

Différent du SDK AEM, l’AEM **SDK sans tête** est un ensemble de bibliothèques qui peuvent être utilisées par les clients pour interagir rapidement et facilement avec les API AEM sans affichage sur HTTP.

Pour plus d’informations sur le SDK AEM sans affichage, voir [documentation ici](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/how-to/aem-headless-sdk.html?lang=en).

## Outils de développement supplémentaires {#additional-development-tools}

Outre le SDK AEM, vous avez besoin d’outils supplémentaires qui facilitent le développement et le test local de votre code et contenu :

* Java™
* Git
* Apache Maven
* La bibliothèque Node.js
* L’environnement de développement intégré (IDE) de votre choix

Comme AEM est une application Java™, vous devez installer Java™ et le SDK Java™ pour prendre en charge le développement d’AEM as a Cloud Service.

Git est ce que vous utiliserez pour gérer le contrôle de code source et archiver les modifications apportées à Cloud Manager, puis les déployer sur une instance de production.

AEM utilise Apache Maven pour créer des projets générés à partir de l’archétype de projet AEM Maven. Tous les environnements de développement intégré majeurs prennent en charge l’intégration de Maven.

Node.js est un environnement d’exécution JavaScript utilisé pour fonctionner avec les ressources front-end du sous-projet `ui.frontend` d’un projet AEM. Node.js est distribué avec npm, qui est de facto le gestionnaire de modules Node.js utilisé pour gérer les dépendances JavaScript.

## Composants d’un système AEM en un coup d’œil {#components-of-an-aem-system-at-a-glance}

Regardons ensuite les éléments qui constituent un environnement AEM.

Un environnement d’AEM complet est constitué d’un auteur, d’une publication et d’un Dispatcher. Ces mêmes composants sont disponibles dans l’exécution de développement local afin de vous permettre de prévisualiser plus facilement votre code et votre contenu avant la mise en ligne.

* **Le service Auteur** permet aux utilisateurs internes de créer, gérer et prévisualiser du contenu.

* **Le service de publication** est considéré comme l’environnement « En ligne » et est généralement celui avec lequel les utilisateurs finaux interagissent. Le contenu, après avoir été modifié et approuvé sur le service Auteur, est distribué au service Publication. Le modèle de déploiement le plus courant avec les applications découplées AEM est de connecter la version de production de l’application à un service de publication AEM.

* **Dispatcher** est un serveur web statique augmenté avec le module AEM Dispatcher. Ce module met en cache les pages web produites par l’instance de publication pour améliorer les performances.

## Workflow de développement local {#the-local-development-workflow}

Le projet de développement local est basé sur Apache Maven et utilise Git pour le contrôle de code source. Pour mettre à jour le projet, les développeurs peuvent utiliser leur environnement de développement intégré préféré, tel qu’Eclipse, Visual Studio Code ou IntelliJ, entre autres.

Pour tester le code ou les mises à jour de contenu qui seront ingérées par votre application sans interface utilisateur, vous devez déployer les mises à jour sur l’exécution AEM locale, qui inclut les instances locales des services de création et de publication AEM.

Veillez à tenir compte des différences entre chaque composant dans l’exécution locale AEM, car il est important de tester vos mises à jour là où elles comptent le plus. Par exemple, testez les mises à jour du contenu sur l’instance de création ou testez le nouveau code sur l’instance de publication.

Dans un système de production, un Dispatcher et un serveur Apache http se trouvent toujours devant une instance de publication AEM. Ils fournissent des services de mise en cache et de sécurité pour le système AEM. Il est donc essentiel de tester le code et les mises à jour de contenu par rapport à Dispatcher.

## Prévisualisation locale de votre code et de votre contenu avec l’environnement de développement local {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Pour préparer votre projet découplé AEM à son lancement, vous devez vous assurer que tous les éléments constituant votre projet fonctionnent correctement.

Pour cela, vous devez tout assembler : code, contenu et configuration, puis testez-le dans un environnement de développement local pour vous préparer en temps réel.

L’environnement de développement local se compose de trois principaux éléments :

1. Le projet AEM : contient tout le code personnalisé, la configuration et le contenu sur lesquels les développeurs AEM vont travailler.
1. L’exécution locale AEM : les versions locales des services d’auteur et de publication AEM qui seront utilisés pour déployer le code du projet AEM.
1. L’exécution locale du Dispatcher : la version locale du serveur web Apache httpd qui comprend le module de Dispatcher.

Une fois l’environnement de développement local configuré, vous pouvez simuler la diffusion de contenu vers l’application React en déployant localement un serveur de nœuds statique.

Pour obtenir un aperçu plus détaillé de la configuration d’un environnement de développement local et de toutes les dépendances nécessaires à l’aperçu du contenu, voir [Documentation sur le déploiement en production](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/production-deployment.html?lang=fr#prerequisites).

## Et après ? {#whats-next}

Maintenant que vous avez terminé cette partie du parcours de développement découplé AEM, vous devriez pouvoir :

* Familiarisez-vous avec les outils de développement AEM
* Présentation du workflow de développement local

Poursuivez votre parcours dans AEM découplé en consultant le document [Comment mettre en ligne votre application en mode découplé](/help/journey-headless/developer/go-live.md) dans lequel vous mettez en ligne votre projet AEM découplé.

## Ressources supplémentaires {#additional-resources}

* [SDK d’AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [Configurer un environnement AEM local](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html?lang=fr)
* [AEM SDK sans affichage pour les navigateurs côté client (JavaScript)](https://github.com/adobe/aem-headless-client-js)
* [AEM SDK sans affichage pour server-side/Node.js (JavaScript)](https://github.com/adobe/aem-headless-client-nodejs)
* [AEM SDK sans affichage pour Java™](https://github.com/adobe/aem-headless-client-java)

