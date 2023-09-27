---
title: Prévisualisation du contenu
description: Découvrez comment utiliser le service d’aperçu AEM pour prévisualiser le contenu avant sa mise en ligne.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
source-git-commit: 1804eacb5399dc38c97ff953031666711b9a0e4f
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 83%

---


# Prévisualisation du contenu {#previewing-content}

AEM propose un service d’aperçu Sites qui permet aux développeurs et aux auteurs de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et soit disponible publiquement.

Il facilite la prévisualisation des expériences de page qui ne seraient pas visibles autrement à partir de l’environnement de création, comme les transitions de page et tout autre contenu côté publication uniquement.

>[!NOTE]
>
>Comme le contenu est *publié* dans l’environnement de prévisualisation, il est accessible par URL (il n’a donc pas besoin d’accéder à AEM).

Pour plus d’informations sur les environnements d’aperçu, voir [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

## Publication de contenu en vue de la prévisualisation {#publishing-content-to-preview}

Vous pouvez publier du contenu dans le service d’aperçu à l’aide de l’interface utilisateur de **Publication gérée**.

1. Dans la console Sites, sélectionnez la ou les pages à envoyer en prévisualisation, puis cliquez sur le bouton **Gérer la publication**
1. Dans l’assistant suivant, sélectionnez **Aperçu** comme destination.

   ![publication gérée](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Cliquez sur **Suivant**, puis sur **Publier** pour confirmer.

1. Une boîte de dialogue affiche les URL d’accès au contenu dans l’environnement de prévisualisation.

   >[!NOTE]
   >
   >Comme le contenu est *publié* dans l’environnement de prévisualisation, il est accessible par URL (il n’a donc pas besoin d’accéder à AEM).

Vous pouvez également utiliser les URL affichées dans l’assistant pour afficher le contenu de l’aperçu, ou ajouter `preview-` à l’URL de publication de votre instance de production.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

Consultez le document [Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour plus d’informations sur la manière de récupérer les URL de vos environnements.

Le contenu peut également être publié pour la prévisualisation à l’aide d’un [workflow de publication de l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) avec le paramètre `agentId` défini sur `preview` ou à l’aide de l’[API de réplication](/help/operations/replication.md#replication-api) avec un `AgentFilter` configuré pour la prévisualisation.

## Dépublier du contenu à partir de l’aperçu {#unpublishing-content-from-preview}

Dépublier du contenu à partir de l’environnement **Aperçu** est fondamentalement le même processus que la [dépublication de pages](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#unpublishing-pages) de l’environnement **Publier**.

La seule différence réside dans le fait que vous pouvez sélectionner la **Destination** à afficher en **aperçu**.

## Informations supplémentaires {#further-information}

Voir également :

* [Configuration des paramètres OSGi pour le niveau de prévisualisation](/help/implementing/preview-tier/preview-tier-configuring-osgi.md#configuring-osgi-settings-for-the-preview-tier)

* [Débogage de l’aperçu à l’aide de Developer Console](/help/implementing/preview-tier/preview-tier-configuring-osgi.md#debugging-preview-using-the-developer-console)