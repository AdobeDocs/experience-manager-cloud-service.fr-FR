---
title: Modifications notables apportées à Adobe Experience Manager (AEM) as a Cloud Service
description: Modifications notables apportées à Adobe Experience Manager (AEM) as a Cloud Service
translation-type: ht
source-git-commit: e76de9b84931dced6383570e384ffdb6fb334daf

---


# Modifications notables apportées à Adobe Experience Manager (AEM) as a Cloud Service {#notable-changes-aem-cloud}

AEM Cloud Service offre une foule de nouvelles fonctionnalités et possibilités pour gérer vos projets AEM. Cependant, il existe plusieurs différences entre les ressources AEM Sites sur site ou dans Adobe Managed Service par rapport à AEM Cloud Service. Ce document met en lumière les différences importantes.

>[!NOTE]
>Ce document met en évidence les modifications notables apportées à AEM dans son ensemble. Pour les modifications spécifiques à une solution, voir :
>
>* [Modifications notables d’AEM Sites dans AEM Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Modifications notables d’AEM Assets dans AEM Cloud Service](/help/assets/assets-cloud-changes.md)


Les principales différences sont les suivantes :

* [/apps et /libs ne sont pas modifiables au moment de l’exécution](#apps-libs-immutable)
* [Les paramètres et bundles OSGi doivent être basés sur le référentiel](#osgi)
* [Les modifications apportées au référentiel de publication ne sont pas autorisées](#changes-to-publish-repo)
* [Les modes d’exécution personnalisés ne sont pas autorisés](#custom-runmodes)
* [Suppression des agents de réplication](#replication-agents)
* [Suppression de l’interface utilisateur de la version classique](#classic-ui)
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
* Les configurations de déploiement MSM personnalisées et MSM Blueprint doivent être installées à partir de Git via le pipeline CI/CD.
* Les changements de traduction I18n doivent provenir de Git via le pipeline CI/CD.

## Les paramètres et bundles OSGi doivent être basés sur le référentiel {#osgi}

La console web, qui était utilisée dans les versions précédentes d’AEM pour modifier les paramètres OSGi, n’est pas disponible dans AEM Cloud Service. Par conséquent, les modifications apportées à OSGi doivent être introduites par le biais du pipeline CI/CD.

* Les modifications apportées aux paramètres OSGi ne peuvent être effectuées que par le biais de la persistance Git en tant que paramètres OSGi basés sur JCR.
* Les bundles OSGi (qu’ils soient nouveaux ou qu’ils aient été mis à jour) doivent être introduits via Git dans le cadre du processus de création du pipeline CI/CD.

## Les modifications apportées au référentiel de publication ne sont pas autorisées {#changes-to-publish-repo}

Les modifications directes apportées au référentiel de publication ne sont pas autorisées sur AEM Cloud Service. Dans les versions antérieures d’AEM sur site ou d’AEM sur AMS, les modifications de code peuvent être apportées directement au référentiel de publication ; pour créer des utilisateurs, mettre à jour le profil utilisateur et créer des nœuds, par exemple. Cela n’est plus possible et vous pouvez y remédier de différentes façons :

* Pour le contenu et la configuration basée sur le contenu : effectuez les modifications sur l’instance d’auteur et publiez-les.
* Pour le code et la configuration : effectuez les modifications dans le référentiel GIT et exécutez le pipeline CI/CD pour les déployer.
* Pour les données liées à l’utilisateur, telles que les envois de formulaire ou les données de profil : utilisez le service de profil unifié à partir d’Experience Cloud Platform ou d’un autre magasin de sessions tiers.

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

## Suppression de l’interface utilisateur de la version classique {#classic-ui}

L’interface utilisateur de la version classique n’est plus disponible dans AEM Cloud Service.

## Diffusion côté publication {#publish-side-delivery}

L’accélération HTTP, y compris la gestion du trafic et du réseau CDN pour les services d’auteur et de publication, est fournie par défaut dans AEM Cloud Service.

Pour la transition d’un projet à partir d’AMS ou d’une installation sur site, Adobe recommande vivement d’exploiter le réseau CDN intégré, car les fonctionnalités d’AEM Cloud Service sont optimisées pour le réseau CDN fourni.

## Gestion et diffusion des ressources {#asset-handling}

Le chargement, le traitement et le téléchargement des ressources ont été optimisés dans AEM Cloud Service. Cela se traduit par un dimensionnement plus efficace, ainsi que des chargements et des téléchargements plus rapides. Cela peut toutefois avoir une incidence sur certains codes personnalisés existants.

* Le workflow par défaut de **Mise à jour des ressources DAM** dans les versions précédentes d’AEM n’est plus disponible.
* Les composants de site web qui diffusent un fichier binaire **sans transformation** doivent utiliser le téléchargement direct.
   * Le servlet Sling GET a été modifié afin d’effectuer cette opération par défaut.
* Les composants de site web qui diffusent un fichier binaire **avec transformation** (redimensionnement via servlet, par exemple) peuvent continuer à fonctionner normalement.
* Les ressources qui arrivent par le biais de Package Manager nécessitent un retraitement manuel à l’aide de l’action **Retraiter les ressources** dans l’interface d’Assets.
