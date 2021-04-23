---
title: Comment vivre avec votre application sans en-tête
description: Dans cette partie du Parcours AEM de développement sans tête, apprenez comment déployer une application sans tête en direct en emportant votre code local dans Git et en le déplaçant vers Cloud Manager Git pour le pipeline CI/CD.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 6097cb8961f604ec2d3f5f6d602c927efc7344d5
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 2%

---


# Comment vivre avec votre application sans en-tête {#go-live}

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette partie du [AEM Parcours de développement sans tête,](#overview.md) apprenez comment déployer une application sans tête en direct en prenant votre code local dans Git et en le déplaçant vers Cloud Manager Git pour le pipeline CI/CD.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent de l&#39;parcours sans tête AEM, [Comment assembler tout - Votre application et votre contenu dans AEM sans tête](put-it-all-together.md) vous avez appris à préparer votre propre projet sans tête pour qu&#39;il soit mis en ligne et vous devriez maintenant :

* Comprendre les exigences pour être opérationnel.

Cet article s&#39;appuie sur ces principes de base pour vous permettre de comprendre comment mettre en oeuvre votre projet AEM sans tête.

## Intention {#objective}

Ce document vous aide à comprendre l&#39;AEM canal de publication sans en-tête et les considérations de performances dont vous devez tenir compte avant de commencer à utiliser votre application.

* Comprendre les bases de la réplication et de la mise en cache du contenu AEM
* Configurez l&#39;outil nécessaire pour simuler le passage en service de votre application sans tête
* Sécurisation et mise à l’échelle de votre application avant le lancement
* Surveillance des performances et débogage

## Concepts de base de la réplication et de la mise en cache du contenu {#content-replication-and-caching}

Un environnement AEM complet est constitué d’un auteur, d’une publication et d’un répartiteur.

* **Ce** service permet aux utilisateurs internes de créer, gérer et prévisualisation du contenu.

* **Le** service de publication est considéré comme l’environnement &quot;en direct&quot; et est généralement utilisé par les utilisateurs finaux pour interagir. Le contenu, après avoir été modifié et approuvé sur le service Auteur, est distribué au service Publication.

* **Le** Dispatcher est un serveur Web statique auquel s&#39;ajoute le module de répartiteur d&#39;AEM. Ce module met en cache les pages web produites par l’instance de publication pour améliorer les performances.

Le modèle de déploiement le plus courant avec AEM applications sans en-tête consiste à faire en sorte que la version de production de l’application se connecte à un service de publication AEM.

## Exigences et configuration {#requirements-and-configuration}

1. Configurez un [environnement d’exécution local](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#install-java) en utilisant [AEM comme SDK de service Cloud](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
2. Installez le [contenu d’exemple WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) et les points de terminaison GraphQL suivants.
3. Déployez et configurez un [serveur de noeud statique ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/production-deployment.html?lang=en#static-server).

## Sécuriser et mettre à l’échelle votre application sans en-tête avant le lancement {#secure-and-scale-before-launch}

1. Configurer [Authentification basée sur un jeton](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)
2. Connexions Web sécurisées
3. Configuration de la mise en cache et de l’évolutivité

## Déploiement en environnement de production {#deploy-to-production}

### Structure du modèle par rapport à la sortie GraphQL {#structure-vs-output}

* Evitez de créer des requêtes qui génèrent plus de 15 kb de JSON (gzip compressé). Les fichiers JSON longs nécessitent beaucoup de ressources pour être analysés par l’application cliente.
* Evitez plus de cinq niveaux imbriqués de hiérarchies de fragments. Les niveaux supplémentaires rendent difficile pour les auteurs de contenu de tenir compte de l’impact de leurs modifications.
* Utilisez des requêtes à plusieurs objets au lieu de modéliser des requêtes avec des hiérarchies de dépendance dans les modèles. Cela permet une plus grande flexibilité à long terme pour restructurer la sortie JSON sans avoir à effectuer de nombreuses modifications de contenu.

### Maximiser le taux d’accès au cache CDN {#maximize-cdn}

* N&#39;utilisez pas de requêtes GraphQL directes, sauf si vous demandez du contenu en direct à la surface.
   * Utilisez plutôt des requêtes persistantes.
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

## Surveillance {#monitoring}

### Comment vérifier les performances globales {#check-overall-performance}

* Validation des versions de prévisualisation et de production de l’application
* Vérifier les pages d&#39;état AEM pour l&#39;état actuel de disponibilité du service
* Accès aux rapports de performances
   * Performances des diffusions
      * Rapide (CDN) - vérifier le nombre d’appels, le taux de cache, les taux d’erreur, le trafic de charge utile
      * Serveurs d&#39;Origine : nombre d&#39;appels, taux d&#39;erreur, charges d&#39;UC, trafic de charge
   * Performances de l’auteur
      * Vérifier le nombre d’utilisateurs, de requêtes et de chargements
* Accès aux rapports de performances spécifiques à l’application et à l’espace
   * Une fois le serveur opérationnel, vérifiez si les mesures générales sont vertes/orange/rouges, puis identifiez les problèmes spécifiques à l’application.
   * Ouvrez les mêmes rapports que ceux ci-dessus filtrés dans l’application/l’espace (par exemple, bureau Photoshop, paywall, etc.).
   * Utiliser les API du journal Splunk pour accéder aux performances du service et de l&#39;application
   * Contactez l’assistance clientèle si d’autres problèmes se produisent.

## Résolution des incidents {#troubleshooting}

### Débogage {#debugging}

Pour vous assurer que votre application fonctionne correctement avant le lancement, il est recommandé de suivre les étapes suivantes en tant qu’approche générale du débogage :

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

## Eléments suivants {#what-is-next}

Maintenant que vous avez terminé cette partie du Parcours de développement AEM sans tête, vous devez :

* Comprendre les principes de base de la réplication du contenu AEM et de la mise en cache.
* Sachez comment configurer l&#39;outillage nécessaire pour simuler la mise en service de votre application sans tête.
* Découvrez comment sécuriser et mettre à l’échelle votre application avant le lancement.
* Découvrez comment surveiller les problèmes de performances et de débogage.

Vous devez continuer votre parcours sans tête AEM en examinant ensuite le document [Lancement de la publication](post-launch.md) où vous apprendrez à conserver votre expérience sans tête.

## Ressources supplémentaires {#additional-resources}
