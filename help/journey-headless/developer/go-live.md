---
title: Comment mettre en ligne votre application découplée
description: Dans cette partie du Parcours de développement découplé AEM, apprenez à déployer une application découplée en direct en prenant votre code local dans Git et en le déplaçant vers le Git Cloud Manager pour le pipeline CI/CD.
exl-id: 81616e31-764b-44b0-94a6-3ae24ce56bf6
source-git-commit: 270eb35023e34eed2cd17674372794c6c2cc7757
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 81%

---

# Comment mettre en ligne votre application découplée {#go-live}

Dans cette partie du [Parcours de développement découplé AEM](overview.md), apprenez à déployer une application découplée en direct en prenant votre code local dans Git et en le déplaçant vers le Git Cloud Manager pour le pipeline CI/CD.

## Un peu d’histoire...  {#story-so-far}

Dans le document précédent du parcours sans tête AEM, [Comment tout assembler - Votre application et votre contenu AEM sans affichage](put-it-all-together.md) vous avez appris à utiliser les outils de développement d’AEM pour rassembler toutes les facettes de votre projet.

Cet article s’appuie sur ces principes de base pour que vous compreniez comment préparer votre propre projet AEM découplé à être mis en ligne.

## Objectif {#objective}

Ce document vous aide à comprendre le pipeline de publication sans interface utilisateur AEM et les considérations de performances que vous devez connaître avant de passer en ligne avec votre application.

* Sécurisez et mettez à l’échelle votre application avant son lancement
* Surveillance des performances et du débogage

<!-- Alexandru: this is a bit redundant, to review again later

## Prepare your AEM Headless Application for Go-Live {#prepare-your-aem-headless-application-for-golive}

-->
Pour préparer votre application AEM sans interface pour le lancement, suivez les bonnes pratiques décrites ci-dessous.

## Sécurisez et mettez à l’échelle votre application découplée avant son lancement {#secure-and-scale-before-launch}

1. Configuration de l’[authentification basée sur les jetons](/help/headless/security/authentication.md) avec vos requêtes GraphQL
1. Configurez la [mise en cache](/help/implementing/dispatcher/caching.md).

## Structure du modèle par rapport à l’output GraphQL {#structure-vs-output}

* Évitez de créer des requêtes qui génèrent plus de 15 ko de JSON (fichier compressé gzip). Les fichiers JSON trop longs consomment beaucoup de ressources que l’application cliente doit ensuite analyser.
* Évitez plus de cinq niveaux imbriqués dans les hiérarchies de fragments. Les niveaux supplémentaires rendent difficile la prise en compte de l’impact de leurs modifications par les auteurs de contenu.
* Utilisez des requêtes à plusieurs objets au lieu de modéliser des requêtes avec des hiérarchies de dépendances au sein des modèles. Vous obtiendrez grâce à cela une plus grande flexibilité à long terme pour restructurer la sortie JSON sans avoir à effectuer de nombreuses modifications de contenu.

## Maximiser le ratio cache-accès CDN {#maximize-cdn}

* N’utilisez pas de requêtes GraphQL directes, sauf si vous demandez du contenu en direct à la surface.
   * Dans la mesure du possible, utilisez des requêtes persistantes.
   * Fournissez un TTL CDN supérieur à 600 secondes pour que le CDN les mette en cache.
   * AEM peut calculer l’impact d’une modification de modèle sur des requêtes existantes.
* Partagez les requêtes de fichiers JSON et GraphQL entre un taux de changement de contenu faible et élevé afin de réduire le trafic client sur le réseau de diffusion de contenu et d’attribuer un TTL plus élevé. Vous minimiserez grâce à cela la revalidation par le CDN du fichier JSON avec le serveur d’origine.
* Pour invalider activement le contenu du réseau de diffusion de contenu, utilisez la fonction Purge progressive. Cela permet au CDN de retélécharger le contenu sans provoquer l’échec du cache.

## Amélioration du temps de téléchargement du contenu découplé {#improve-download-time}

* Assurez-vous que les clients HTTP utilisent HTTP/2.
* Assurez-vous que les clients HTTP acceptent la requête d’en-têtes pour gzip.
* Réduisez le nombre de domaines utilisés pour héberger les artefacts JSON et les artefacts référencés.
* Utilisez `Last-modified-since` pour actualiser les ressources.
* Utilisez la sortie `_reference` du fichier JSON pour commencer à télécharger des ressources sans avoir à analyser les fichiers JSON complets.

## Déploiement en environnement de production {#deploy-to-production}

Une fois que vous avez vérifié que tout a été testé et fonctionne correctement, vous êtes prêt à envoyer vos mises à jour de code vers une [référentiel Git centralisé dans Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=fr).

Une fois les mises à jour transférées vers Cloud Manager, elles peuvent être déployées vers AEM as a Cloud Service à l’aide du [pipeline CI/CD de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=fr).

Vous pouvez commencer à déployer votre code en exploitant le pipeline CI/CD de Cloud Manager, qui est traité en détail [ici](/help/implementing/deploying/overview.md).

## Surveillance des performances {#performance-monitoring}

Pour que les utilisateurs disposent de la meilleure expérience possible lors de l’utilisation de l’application AEM sans interface utilisateur, il est important de surveiller les mesures de performances clés, comme indiqué ci-dessous :

* la validation des versions d’aperçu et de production de l’application ;
* la vérification des pages d’état AEM pour l’état de disponibilité actuelle du service ;
* l’accès aux rapports de performance ;
   * Les performances de diffusion
      * Les performances du CDN (en termes de rapidité) : pour vérifier le nombre d’appels, le taux de mise en cache, les taux d’erreur et le trafic de charge utile
      * Les serveurs d’origine : le nombre d’appels, les taux d’erreur, la charge du processeur, le trafic de charge utile
   * Les performances auteur
      * Pour vérifier le nombre d’utilisateurs, de demandes et de chargements
* Accès aux rapports de performances spécifiques à l’application et à l’espace
   * Une fois le serveur ouvert, vérifiez si les mesures générales apparaissent en vert/orange/rouge, puis identifiez les problèmes spécifiques à l’application.
   * Ouvrez les rapports ci-dessus filtrés par application ou par surface (par exemple, la version bureau de Photoshop, un paywall).
   * Utilisez des API de journal Splunk pour accéder aux performances du service et de l’application.
   * Contactez le service clientèle si d’autres problèmes se produisent.

## Résolution des problèmes {#troubleshooting}

### Débogage {#debugging}

Observez ces bonnes pratiques pour votre approche générale de débogage :

* Validez les fonctionnalités et les performances avec la version d’aperçu de l’application.
* Validez les fonctionnalités et les performances avec la version de production de l’application.
* Validez à l’aide de l’aperçu JSON de l’éditeur de fragment de contenu.
* Inspectez le JSON dans l’application cliente pour vérifier la présence de problèmes d’application cliente ou de diffusion.
* Inspectez le JSON à l’aide de GraphQL pour vérifier la présence de problèmes liés au contenu mis en cache ou à AEM.

### Journalisation d’un bogue avec prise en charge {#logging-a-bug-with-support}

Pour consigner efficacement un bogue avec l’assistance si vous avez besoin d’aide supplémentaire, procédez comme suit :

* Si nécessaire, réalisez des captures d’écran du problème.
* Documentez une façon de reproduire le problème.
* Documentez le contenu à l’origine du problème.
* Consignez un problème à l’aide du portail d’assistance AEM avec la priorité appropriée.

## Serait-ce la fin de notre voyage ?  {#journey-ends}

Félicitations ! Vous avez terminé le parcours de développement découplé AEM. Vous devriez maintenant comprendre les éléments suivants :

* La différence entre la diffusion de contenu couplé et découplé
* Les fonctionnalités découplées AEM
* Comment organiser un projet découplé AEM
* Comment créer du contenu découplé dans AEM
* Comment récupérer et mettre à jour du contenu découplé dans AEM
* La mise en ligne d’un projet découplé AEM
* Que faire après la mise en service.

Vous avez peut-être déjà lancé votre premier projet découplé AEM, vous disposez en tout cas déjà de toutes les connaissances nécessaires pour le faire. Super boulot !

### Découvrez les applications sur une seule page {#explore-spa}

Les magasins découplés AEM n’ont pourtant pas besoin de s’arrêter à ça. Vous vous souviendrez peut-être dans le [Prise en main dans le parcours](getting-started.md#integration-levels) nous avons discuté brièvement de la manière dont AEM prend en charge non seulement la livraison sans interface utilisateur et les modèles traditionnels de pile complète, mais aussi les modèles hybrides qui combinent les avantages des deux.

Si ce type de flexibilité est nécessaire pour votre projet, passez à la section optionnelle du parcours intitulée [Comment créer des applications sur une seule page (SPA) avec AEM.](create-spa.md)

## Ressources supplémentaires {#additional-resources}

* [Présentation du déploiement sur AEM as a Cloud Service](/help/implementing/deploying/overview.md)
* [Utilisation de Cloud Manager pour déployer votre code](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)
* [Intégration du référentiel Git de Cloud Manager à un référentiel Git externe et déploiement d’un projet AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html?lang=fr)
