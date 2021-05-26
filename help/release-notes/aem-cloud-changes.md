---
title: Modifications notables apportées à Adobe Experience Manager (AEM) as a Cloud Service
description: Modifications notables apportées à Adobe Experience Manager (AEM) as a Cloud Service
exl-id: fe11d779-66cd-45aa-aa6b-c819b88d2405
source-git-commit: 71f05dda4ccd52c66bbf1d9025900976f07227f3
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 94%

---

# Modifications notables apportées à Adobe Experience Manager (AEM) as a Cloud Service {#notable-changes-aem-cloud}

AEM Cloud Service offre une foule de nouvelles fonctionnalités et possibilités pour gérer vos projets AEM. Cependant, il existe plusieurs différences entre les ressources AEM Sites sur site ou dans Adobe Managed Service par rapport à AEM Cloud Service. Ce document met en lumière les différences importantes.

>[!CONTEXTUALHELP]
>id="aem_cloud_notable_changes"
>title="Modifications notables apportées à AEM en tant que Cloud Service"
>abstract="Dans cet onglet, vous pouvez afficher le contenu qui vous aidera à comprendre les différences entre AEM on premise ou dans Adobe Managed Services, par rapport à AEM en tant que Cloud Service."
>additional-url="https://video.tv.adobe.com/v/330543" text="Evolution de l&#39;AEM en tant que Cloud Service"


>[!NOTE]
>Ce document met en évidence les modifications notables apportées à AEM dans son ensemble. Pour plus d’informations et connaître les changements spécifiques à une solution, voir :
>
>* [Introduction à Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
* [Nouveautés et différences](/help/overview/what-is-new-and-different.md) entre Adobe Experience Manager as a Cloud Service avec les versions précédentes
* [Architecture](/help/core-concepts/architecture.md) d’Adobe Experience Manager as a Cloud Service
* [Modifications notables apportées à AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
* [Modifications notables apportées à AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)


Les principales différences sont les suivantes :

* [/apps et /libs ne sont pas modifiables au moment de l’exécution](#apps-libs-immutable)

* [Les paramètres et bundles OSGi doivent être basés sur le référentiel](#osgi)

* [Les modifications apportées au référentiel de publication ne sont pas autorisées](#changes-to-publish-repo)

* [Les modes d’exécution personnalisés ne sont pas autorisés](#custom-runmodes)

* [Suppression des agents de réplication](#replication-agents)

* [Suppression de l’interface utilisateur classique](#classic-ui)

* [Diffusion côté publication](#publish-side-delivery)

* [Gestion et diffusion des ressources](#asset-handling)

## /apps et /libs ne sont pas modifiables au moment de l’exécution {#apps-libs-immutable}

Le contenu et les sous-dossiers de `/apps` et `/libs` sont en lecture seule. Les fonctionnalités ou le code personnalisé qui s’attendent à apporter des modifications à ces emplacements échoueront. Une erreur sera alors renvoyée, indiquant que ce contenu est en lecture seule et que l’opération d’écriture n’a pas pu être effectuée. Cela a une incidence dans plusieurs domaines d’AEM :

* Aucune modification n’est autorisée dans `/libs`.
   * Il ne s’agit pas d’une nouvelle règle, mais elle n’était pas appliquée dans les précédentes versions sur site d’AEM.
* Les superpositions pour les zones de `/libs` qui peuvent être superposées sont toujours autorisées dans `/apps`.
   * Ces superpositions doivent provenir de Git par l’intermédiaire du pipeline CI/CD.
* Les informations de conception de modèles statiques stockées dans `/apps` ne peuvent pas être modifiées au moyen de l’interface utilisateur.
   * Il est recommandé d’utiliser plutôt des modèles modifiables.
   * Si des modèles statiques sont toujours requis, les informations de configuration doivent provenir de Git via le pipeline CI/CD.
* Les configurations de déploiement MSM personnalisées et le plan directeur MSM doivent être installés à partir de Git via le pipeline CI/CD.
* Les changements de traduction I18n doivent provenir de Git via le pipeline CI/CD.

## Les paramètres et bundles OSGi doivent être basés sur le référentiel {#osgi}

La console web, qui était utilisée dans les versions précédentes d’AEM pour modifier les paramètres OSGi, n’est pas disponible dans AEM Cloud Service. Par conséquent, les modifications apportées à OSGi doivent être introduites par le biais du pipeline CI/CD.

* Les modifications apportées aux paramètres OSGi ne peuvent être effectuées que par le biais de la persistance Git en tant que paramètres OSGi basés sur JCR.
* Les bundles OSGi (qu’ils soient nouveaux ou qu’ils aient été mis à jour) doivent être introduits via Git dans le cadre du processus de création du pipeline CI/CD.

## Les modifications apportées au référentiel de publication ne sont pas autorisées {#changes-to-publish-repo}

Outre les modifications apportées au dossier `/home` dans la couche Publication, les modifications directes apportées au référentiel de publication ne sont pas autorisées sur AEM Cloud Service. Dans les versions précédentes d’AEM ou d’AEM on AMS, des modifications de code pouvaient être apportées directement au référentiel de publication. Certaines limitations peuvent être atténuées de différentes manières :

* Pour le contenu et la configuration basée sur le contenu : effectuez les modifications sur l’instance d’auteur et publiez-les.
* Pour le code et la configuration : effectuez les modifications dans le référentiel GIT et exécutez le pipeline CI/CD pour les déployer.

## Les modes d’exécution personnalisés ne sont pas autorisés {#custom-runmodes}

Les modes d’exécution suivants sont fournis en standard pour AEM Cloud Service :

* `author`
* `publish`
* `prod`
* `author.prod`
* `publish.prod`
* `stage`
* `author.stage`
* `publish.stage`
* `dev`
* `author.dev`
* `publish.dev`

Aucun mode d’exécution supplémentaire ou personnalisé n’est accepté dans AEM Cloud Service.

## Suppression des agents de réplication {#replication-agents}

Dans AEM Cloud Service, le contenu est publié à l’aide du module [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html). Les agents de réplication utilisés dans les versions précédentes d’AEM ne sont plus utilisés ni fournis, ce qui peut avoir une incidence sur les zones suivantes des projets AEM existants :

* Workflows personnalisés qui envoient, par exemple, du contenu vers les agents de réplication des serveurs d’aperçu.
* Personnalisation des agents de réplication pour transformer le contenu
* Utilisation de la réplication inverse pour ramener le contenu de la publication à l’auteur.

## Suppression de l’interface utilisateur classique {#classic-ui}

L’interface utilisateur classique n’est plus disponible dans AEM Cloud Service.

## Diffusion côté publication {#publish-side-delivery}

L’accélération HTTP, y compris la gestion du trafic et du réseau CDN pour les services d’auteur et de publication, est fournie par défaut dans AEM Cloud Service.

Pour la transition d’un projet à partir d’AMS ou d’une installation sur site, Adobe recommande vivement d’exploiter le réseau CDN intégré, car les fonctionnalités d’AEM Cloud Service sont optimisées pour le réseau CDN fourni.

## Gestion et diffusion des ressources {#asset-handling}

Le chargement, le traitement et le téléchargement des ressources ont été optimisés dans Assets as a Cloud Service. Cela se traduit par un dimensionnement plus efficace, ainsi que des chargements et des téléchargements plus rapides. Cela peut toutefois avoir une incidence sur certains codes personnalisés existants.

* Le workflow par défaut de **Mise à jour des ressources DAM** dans les versions précédentes d’AEM n’est plus disponible.
* Les composants de site web qui diffusent un fichier binaire **sans transformation** doivent utiliser le téléchargement direct.
   * Le servlet Sling GET a été modifié afin d’effectuer cette opération par défaut.
* Les composants de site web qui diffusent un fichier binaire **avec transformation** (redimensionnement via servlet, par exemple) peuvent continuer à fonctionner normalement.
* Les ressources qui arrivent par le biais de Package Manager nécessitent un retraitement manuel à l’aide de l’action **Retraiter les ressources** dans l’interface d’Assets.
