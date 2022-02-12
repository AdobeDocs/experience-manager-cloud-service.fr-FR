---
title: Utilisation de l’IDE GraphiQL dans AEM
description: Découvrez comment utiliser l’IDE GraphiQL dans Adobe Experience Manager.
feature: Content Fragments,GraphQL API
source-git-commit: c4490690edb1ec0e2a6b8cca724fe9c290650bc8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 24%

---


# Utilisation de l’IDE GraphiQL {#graphiql-ide}

Une mise en oeuvre de la norme [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE est disponible pour une utilisation avec AEM GraphQL. Cette interface peut être [installée avec AEM](#installing-graphiql-ide).

>[!NOTE]
>
>GraphiQL est liée au point d’entrée global (et ne fonctionne pas avec d’autres points d’entrée pour des configurations Sites spécifiques).

L’outil GraphiQL vous permet de saisir, de tester et de déboguer directement des requêtes. GraphiQL permet également d’accéder facilement à la documentation, ce qui facilite l’apprentissage et la compréhension des méthodes disponibles.

Par exemple :

* `http://localhost:4502/content/graphiql.html`

Vous disposez de fonctionnalités telles que la mise en surbrillance de la syntaxe, la saisie semi-automatique et la suggestion automatique, ainsi qu’un historique et une documentation en ligne :

![Interface GraphiQL](assets/cfm-graphiql-interface.png "Interface GraphiQL")

## Installation de l’IDE GraphiQL AEM {#installing-graphiql-ide}

L’IDE GraphiQL est un outil de développement qui n’est nécessaire que dans les environnements de niveau inférieur tels qu’une instance de développement ou locale. Par conséquent, il n’est pas inclus dans le projet AEM, mais il est fourni sous la forme d’un package distinct qui peut être installé sur une base ad hoc.

1. Accédez au **[Portail de distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)** > **AEM as a Cloud Service**.
1. Recherchez &quot;GraphiQL&quot; (veillez à inclure la variable **i** in **GraphiQL**.
1. Télécharger la dernière version **Package de contenu GraphiQL v.x.x.x**
1. Dans la **AEM** Accédez à **Outils** > **Déploiement** > **Packages**.
1. Cliquez sur **Télécharger le module** et sélectionnez le package téléchargé à l’étape précédente. Cliquez sur **Installer** pour installer le package.

