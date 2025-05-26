---
title: Prévisualisation du contenu
description: Découvrez comment utiliser le service d’aperçu AEM pour prévisualiser le contenu avant sa mise en ligne.
exl-id: 6b4b57f6-2e66-4c83-94d9-bc1e0daab0f3
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: b93bcb5d26a63babf0b81c92a4fd85d358bfbea7
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 65%

---


# Prévisualisation du contenu {#previewing-content}

AEM propose un service d’aperçu Sites qui permet aux développeurs et aux auteurs de contenu de prévisualiser l’expérience finale d’un site web avant qu’il n’atteigne l’environnement de publication et soit disponible publiquement.

Il facilite la prévisualisation des expériences de page qui ne seraient pas visibles autrement à partir de l’environnement de création, comme les transitions de page et tout autre contenu côté publication uniquement.

>[!IMPORTANT]
>
>L’accès à l’environnement de prévisualisation nécessite la configuration d’une liste autorisée IP. Pour plus d’informations, consultez [Accès au service d’aperçu](/help/implementing/cloud-manager/manage-environments.md#access-preview-service#access-preview-service).
>
>Pour plus d’informations sur tous les environnements, voir [Gérer les environnements](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

>[!NOTE]
>
>Le contenu étant *publié* dans l’environnement de prévisualisation, il est accessible par URL.

## Publication de contenu en vue de la prévisualisation {#publishing-content-to-preview}

Vous pouvez publier du contenu dans le service d’aperçu à l’aide de l’interface utilisateur de **Publication gérée**.

1. Dans la console Sites , sélectionnez la ou les pages à envoyer en prévisualisation, puis cliquez sur le bouton **Gérer la publication**.
1. Dans l’assistant suivant, sélectionnez **Aperçu** comme destination.

   ![publication gérée](/help/sites-cloud/authoring/assets/previewmanagedpublication.png)

1. Cliquez sur **Suivant**, puis sur **Publier** pour confirmer.

1. Une boîte de dialogue affiche les URL d’accès au contenu dans l’environnement de prévisualisation.

   >[!NOTE]
   >
   >Le contenu étant *publié* dans l’environnement de prévisualisation, il est accessible par URL (il n’a donc pas besoin d’accéder à AEM).

Vous pouvez également utiliser les URL affichées dans l’assistant pour afficher le contenu de l’aperçu, ou ajouter `preview-` à l’URL de publication de votre instance de production.

```
https://preview-p<programID>-e>environmentID>.adobeaemcloud.com/<pathtopage>.html
```

Voir [ Gestion des environnements](/help/implementing/cloud-manager/manage-environments.md) pour plus d’informations sur la manière de récupérer les URL de vos environnements.

Le contenu peut également être publié pour la prévisualisation à l’aide d’un [workflow de publication de l’arborescence de contenu](/help/operations/replication.md#publish-content-tree-workflow) avec le paramètre `agentId` défini sur `preview` ou à l’aide de l’[API de réplication](/help/operations/replication.md#replication-api) avec un `AgentFilter` configuré pour la prévisualisation.

## Dépublier du contenu à partir de l’aperçu {#unpublishing-content-from-preview}

Dépublier du contenu à partir de l’environnement **Aperçu** est fondamentalement le même processus que la [dépublication de pages](/help/sites-cloud/authoring/sites-console/publishing-pages.md#unpublishing-pages) de l’environnement **Publier**.

La seule différence réside dans le fait que vous pouvez sélectionner la **Destination** à afficher en **aperçu**.
