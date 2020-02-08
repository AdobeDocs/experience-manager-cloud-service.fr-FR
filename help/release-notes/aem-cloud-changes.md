---
title: Modifications notables d’Adobe Experience Manager (AEM) en tant que service Cloud
description: Modifications notables d’Adobe Experience Manager (AEM) en tant que service Cloud
translation-type: tm+mt
source-git-commit: e76de9b84931dced6383570e384ffdb6fb334daf

---


# Modifications notables d’Adobe Experience Manager (AEM) en tant que service Cloud {#notable-changes-aem-cloud}

Le service AEM Cloud offre de nombreuses nouvelles fonctionnalités et possibilités pour la gestion de vos projets AEM. Cependant, il existe plusieurs différences entre les sites AEM sur site ou dans le service géré Adobe par rapport au service cloud AEM. Ce document met en lumière les différences importantes.

>[!NOTE]
>Ce document met en évidence les modifications notables apportées à AEM dans son ensemble. Pour les modifications spécifiques à une solution, voir :
>
>* [Modifications notables apportées aux sites AEM dans le service AEM Cloud](/help/sites-cloud/sites-cloud-changes.md)
>* [Modifications notables des ressources AEM dans le service AEM Cloud](/help/assets/assets-cloud-changes.md)


Les principales différences sont les suivantes :

* [/apps et /libs sont immuables au moment de l’exécution](#apps-libs-immutable)
* [Les lots et paramètres OSGi doivent être basés sur le référentiel](#osgi)
* [Les modifications apportées au référentiel de publication ne sont pas autorisées](#changes-to-publish-repo)
* [Les modes d’exécution personnalisés ne sont pas autorisés](#custom-runmodes)
* [Suppression des agents de réplication](#replication-agents)
* [Suppression de l’interface utilisateur classique](#classic-ui)
* [Livraison côté publication](#publish-side-delivery)
* [Gestion et livraison des ressources](#asset-handling)

## /apps et /libs sont immuables au moment de l’exécution {#apps-libs-immutable}

Tout contenu et sous-dossier dans `/apps` et `/libs` est en lecture seule. Toute fonctionnalité ou tout code personnalisé qui s’attend à y apporter des modifications échouera. Une erreur sera renvoyée indiquant que ce contenu est en lecture seule et que l’opération d’écriture n’a pas pu être terminée. Cela a un impact dans plusieurs domaines d’AEM :

* Aucune modification n&#39; `/libs` est autorisée.
   * Il ne s’agit pas d’une nouvelle règle, mais elle n’a pas été appliquée dans les versions sur site précédentes d’AEM.
* Les superpositions pour les zones `/libs` qui peuvent être superposées sont toujours autorisées dans `/apps`.
   * Ces recouvrements doivent provenir de Git par l&#39;intermédiaire du pipeline CI/CD.
* Les informations de conception de modèle statique stockées dans `/apps` ne peuvent pas être modifiées via l’interface utilisateur.
   * Il est recommandé d’utiliser plutôt des modèles modifiables.
   * Si des modèles statiques sont toujours requis, les informations de configuration doivent provenir de Git via le pipeline CI/CD.
* Les configurations de déploiement MSM Blueprint et de déploiement MSM personnalisé doivent être installées à partir de Git via le pipeline CI/CD.
* Les changements de traduction I18n doivent venir de Git via le pipeline CI/CD.

## Les lots et paramètres OSGi doivent être basés sur le référentiel {#osgi}

La console Web, utilisée dans les versions précédentes d’AEM pour modifier les paramètres OSGi, n’est pas disponible dans le service AEM Cloud. Par conséquent, les changements à OSGi doivent être introduits par le biais du pipeline CI/CD.

* Les modifications apportées aux paramètres OSGi ne peuvent être apportées que par la persistance Git en tant que paramètres OSGi basés sur JCR.
* Les lots OSGi nouveaux ou mis à jour doivent être introduits par Git dans le cadre du processus de construction du pipeline CI/CD.

## Les modifications apportées au référentiel de publication ne sont pas autorisées {#changes-to-publish-repo}

Les modifications directes apportées au référentiel de publication ne sont pas autorisées sur le service AEM Cloud. Dans les versions antérieures d’AEM sur site ou d’AEM sur AMS, les modifications de code peuvent être apportées directement au référentiel de publication, par exemple pour créer des utilisateurs, mettre à jour le profil utilisateur et créer des noeuds. Cela n’est plus possible et peut être atténué de la manière suivante :

* Pour la configuration basée sur le contenu et le contenu : effectuez les modifications sur l’instance d’auteur et publiez-les.
* Pour le code et la configuration : effectuez les modifications dans le référentiel GIT et exécutez le pipeline CI/CD pour les déployer.
* Pour les données liées à l’utilisateur, telles que les envois de formulaire ou les données de profil : utilisez le service de profil unifié de la plate-forme Experience Cloud ou d’un autre magasin d’informations de session tiers.

## Les modes d’exécution personnalisés ne sont pas autorisés {#custom-runmodes}

Les modes d’exécution suivants sont fournis prêts à l’emploi pour le service AEM Cloud :

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

Les modes d’exécution supplémentaires ou personnalisés ne sont pas possibles dans le service cloud AEM.

## Suppression des agents de réplication {#replication-agents}

Dans le service AEM Cloud, le contenu est publié à l’aide de [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html). Les agents de réplication utilisés dans les versions précédentes d’AEM ne sont plus utilisés ni fournis, ce qui peut avoir un impact sur les zones suivantes des projets AEM existants :

* Processus personnalisés qui poussent le contenu vers les agents de réplication des serveurs d’aperçu, par exemple.
* Personnalisation des agents de réplication pour transformer le contenu
* Utilisation de la réplication inverse pour ramener le contenu de la publication à l’auteur

## Suppression de l’interface utilisateur classique {#classic-ui}

L’interface utilisateur classique n’est plus disponible dans le service cloud AEM.

## Livraison côté publication {#publish-side-delivery}

L’accélération HTTP, y compris le CDN et la gestion du trafic pour les services d’auteur et de publication, sont fournies par défaut dans le service AEM Cloud.

Pour la transition d’un projet à partir d’AMS ou d’une installation sur site, Adobe recommande vivement d’exploiter le CDN intégré, car les fonctionnalités du service AEM Cloud sont optimisées pour le CDN fourni.

## Gestion et livraison des ressources {#asset-handling}

Le transfert, le traitement et le téléchargement des ressources ont été optimisés dans le service AEM Cloud afin d’être plus efficaces et de permettre une mise à l’échelle et des téléchargements plus rapides. Cela peut toutefois avoir un impact sur certains codes personnalisés existants.

* La mise à jour **par défaut des ressources** DAM du processus dans les versions précédentes d’AEM n’est plus disponible.
* Les composants du site Web qui fournissent un fichier binaire **sans transformation** doivent utiliser le téléchargement direct.
   * La servlet Sling GET a été modifiée pour effectuer cette opération par défaut.
* Les composants du site Web qui fournissent un fichier binaire **avec transformation** (par exemple, redimensionner par servlet) peuvent continuer à fonctionner comme ils l&#39;ont fait.
* Les ressources qui arrivent par le biais de Package Manager nécessitent un retraitement manuel à l’aide de l’action **Retraiter les ressources** dans l’interface Ressources.
