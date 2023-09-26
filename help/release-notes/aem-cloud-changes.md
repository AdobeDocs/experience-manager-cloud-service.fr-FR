---
title: Modifications notables apportées à Adobe Experience Manager (AEM) as a Cloud Service
description: Modifications notables apportées à Adobe Experience Manager (AEM) as a Cloud Service.
exl-id: fe11d779-66cd-45aa-aa6b-c819b88d2405
source-git-commit: 78ead5f15c2613d9c3bed3025b43423a66805c59
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 43%

---

# Modifications notables apportées à Adobe Experience Manager as a Cloud Service {#notable-changes-aem-cloud}

Adobe Experience Manager (AEM) Cloud Service offre de nombreuses nouvelles fonctionnalités et possibilités de gestion de vos projets AEM. Cependant, il existe des différences entre AEM Sites on premise ou Adobe Managed Service par rapport à AEM Cloud Service. Ce document met en lumière les différences importantes.

>[!CONTEXTUALHELP]
>id="aem_cloud_notable_changes"
>title="Changements notables dans AEM as a Cloud Service"
>abstract="Dans cet onglet, vous pouvez afficher le contenu qui vous aide à comprendre les différences entre AEM on premise ou dans Adobe Managed Services, par rapport à AEM as a Cloud Service."
>additional-url="https://video.tv.adobe.com/v/330543" text="Architecture d’AEM as a Cloud Service"


>[!NOTE]
>Ce document met en évidence les modifications notables apportées à AEM dans son ensemble. Pour plus d’informations et des modifications spécifiques aux solutions, voir :
>
>* [Introduction à Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
>* [Nouveautés et différences](/help/overview/what-is-new-and-different.md) entre Adobe Experience Manager as a Cloud Service avec les versions précédentes
>* [Architecture](/help/overview/architecture.md) d’Adobe Experience Manager as a Cloud Service
>* [Modifications notables apportées à AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
>* [Modifications notables apportées à AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)

Les principales différences sont les suivantes :

* [/apps et /libs ne sont pas modifiables au moment de l’exécution](#apps-libs-immutable)

* [Les lots et configurations OSGi doivent être traités comme du code.](#osgi)

* [Les modifications apportées au référentiel de publication ne sont pas autorisées](#changes-to-publish-repo)

* [Les modes d’exécution personnalisés ne sont pas autorisés](#custom-runmodes)

* [Suppression des agents de réplication  et des modifications connexes](#replication-agents)

* [Suppression de l’interface utilisateur classique](#classic-ui)

* [Diffusion côté publication](#publish-side-delivery)

* [Gestion et diffusion des ressources](#asset-handling)

## /apps et /libs ne sont pas modifiables au moment de l’exécution {#apps-libs-immutable}

Tout contenu et sous-dossiers dans `/apps` et `/libs` est en lecture seule. Les fonctionnalités ou le code personnalisé qui s’attendent à y apporter des modifications échouent. Une erreur est renvoyée indiquant que ce contenu est en lecture seule et que l’opération d’écriture n’a pas pu être terminée. Cela a un impact dans plusieurs domaines AEM :

* Aucune modification n’est autorisée dans `/libs`.
   * Il ne s’agit pas d’une nouvelle règle, mais elle n’a pas été appliquée dans les versions on-premise précédentes d’AEM.
* Recouvrements pour les zones de `/libs` qui peuvent être superposées sont toujours autorisées dans `/apps`.
   * Ces recouvrements doivent provenir de Git par le biais du pipeline CI/CD.
* Informations de conception de modèle statique stockées dans `/apps` ne peut pas être modifié à l’aide de l’interface utilisateur.
   * Il est recommandé d’utiliser plutôt des modèles modifiables .
   * Si des modèles statiques sont toujours requis, les informations de configuration doivent provenir de Git par le biais du pipeline CI/CD.
* Les configurations de déploiement MSM personnalisées et le plan directeur MSM doivent être installés à partir de Git par le biais du pipeline CI/CD.
* Les modifications de traduction I18n doivent provenir de Git par le biais du pipeline CI/CD.

## Les lots et configurations OSGi doivent être traités comme du code. {#osgi}

Les modifications apportées aux lots et aux configurations OSGi doivent être introduites par le biais du pipeline CI/CD.

* Les lots OSGi nouveaux ou mis à jour doivent être introduits par le biais de Git au moyen du pipeline CI/CD.
* Les modifications apportées aux configurations OSGi peuvent uniquement provenir de Git par le biais du pipeline CI/CD.

La console web, qui était utilisée dans les versions précédentes d’AEM pour modifier les lots et les configurations OSGi, n’est pas disponible dans AEM Cloud Service.

## Les modifications apportées au référentiel de publication ne sont pas autorisées {#changes-to-publish-repo}

Outre les modifications apportées au dossier `/home` dans la couche Publication, les modifications directes apportées au référentiel de publication ne sont pas autorisées sur AEM Cloud Service. Dans les versions précédentes d’AEM ou d’AEM on AMS, des modifications de code pouvaient être apportées directement au référentiel de publication. Certaines limitations peuvent être atténuées de différentes manières :

* Pour la configuration du contenu et du contenu : effectuez vos modifications sur l’instance d’auteur et publiez-les.
* Pour le code et la configuration : effectuez vos modifications dans le référentiel GIT et exécutez le pipeline CI/CD pour les déployer.

## Les modes d’exécution personnalisés ne sont pas autorisés {#custom-runmodes}

Les modes d’exécution suivants sont fournis prêts à l’emploi pour AEM Cloud Service :

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

## Suppression des agents de réplication  et des modifications connexes {#replication-agents}

Dans AEM Cloud Service, le contenu est publié à l’aide du module [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html). Les agents de réplication utilisés dans les versions précédentes d’AEM ne sont plus utilisés ni fournis, ce qui peut avoir une incidence sur les zones suivantes des projets AEM existants :

* Workflows personnalisés qui envoient, par exemple, du contenu vers les agents de réplication des serveurs d’aperçu.
* Personnalisation des agents de réplication pour transformer le contenu.
* Utilisation de la réplication inverse pour ramener le contenu de la publication vers l’auteur.

En outre, les boutons pause et désactivation sont supprimés de la console d’administration de l’agent de réplication.

## Suppression de l’interface utilisateur classique {#classic-ui}

L’interface utilisateur classique n’est plus disponible dans AEM Cloud Service.

## Diffusion côté publication {#publish-side-delivery}

L’accélération HTTP, y compris la gestion du trafic et du réseau de diffusion de contenu pour les services d’auteur et de publication, est fournie par défaut dans AEM Cloud Service.

Pour les projets qui passent d’AMS ou une installation sur site, Adobe recommande vivement d’utiliser le réseau de diffusion de contenu intégré, car les fonctionnalités d’AEM Cloud Service sont optimisées pour le réseau de diffusion de contenu fourni.

## Gestion et diffusion des ressources {#asset-handling}

Le chargement, le traitement et le téléchargement des ressources sont optimisés dans [!DNL Experience Manager Assets] en tant que [!DNL Cloud Service]. AEM [!DNL Assets] est désormais plus efficace, permet une mise à l’échelle plus importante et vous permet de télécharger et télécharger plus rapidement. Cela a également un impact sur le code personnalisé existant et sur certaines opérations. Pour obtenir la liste des modifications et la parité avec les fonctionnalités [!DNL Experience Manager] 6.5, voir les [modifications apportées à [!DNL Assets]](/help/assets/assets-cloud-changes.md).
