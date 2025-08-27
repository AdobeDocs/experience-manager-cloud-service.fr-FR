---
title: Présentation des listes d’adresses IP autorisées
description: Découvrez comment les Listes autorisées IP peuvent limiter les adresses à partir desquelles les utilisateurs peuvent accéder aux domaines dans AEM as a Cloud Service.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f1e9b76742c8d97f44ff974fb8686fdcb3d804e6
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 21%

---


# Présentation des listes d’adresses IP autorisées {#introduction}

Découvrez comment les Listes autorisées IP peuvent limiter les adresses à partir desquelles les utilisateurs peuvent accéder aux domaines dans AEM as a Cloud Service.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Gérer les listes d’adresses IP autorisées"
>abstract="AEM as a Cloud Service est accessible par le biais d’Internet et sa sécurité est assurée par l’authentification et l’autorisation des utilisateurs et utilisatrices. Les listes d’adresses IP autorisées de Cloud Manager peuvent être utilisées pour contrôler l’accès et le limiter uniquement aux adresses IP de confiance. Les utilisateurs et utilisatrices de Cloud Manager disposant des autorisations appropriées peuvent créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines d’AEM."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/cicd-pipelines/ip-allow-lists/add-ip-allow-lists" text="Ajouter une liste d’adresses IP autorisées"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/cicd-pipelines/ip-allow-lists/managing-ip-allow-lists" text="Afficher et mettre à jour une liste d’adresses IP autorisées"

## Vue d’ensemble {#overview}

AEM as a cloud service est par défaut accessible par le biais d’Internet. Bien que la sécurité soit gérée au moyen de l’authentification et de l’autorisation des utilisateurs et utilisatrices, la liste autorisée d’adresses IP permet de limiter l’accès aux seules adresses IP de confiance.

Les Listes autorisées IP Cloud Manager peuvent être utilisées pour contrôler l’accès et le limiter uniquement à ces adresses IP de confiance. Les utilisateurs de Cloud Manager disposant des autorisations appropriées peuvent [créer et ajouter des Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines AEM.

Après l’ajout, les Listes autorisées IP [ peuvent être appliquées ou non appliquées](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) plusieurs fois en tant qu’unité ou entité à un service de création ou un service d’éditeur, ou les deux, dans un environnement.

>[!NOTE]
>
>Si aucune Liste autorisée IP n’est appliquée, toutes les adresses IP sont autorisées par défaut. Lorsqu’une Liste autorisée IP est appliquée, aucune adresse IP n’est autorisée, à l’exception de celles figurant sur la Liste autorisée IP.

## Remarques sur l’utilisation {#usage-notes}

* Vous pouvez ajouter jusqu’à 50 Listes autorisées IP à votre programme.
* Vous pouvez ajouter jusqu’à 50 adresses IP/CIDR à chaque Liste autorisée IP.
* Les noms de Liste autorisée IP sont pris en charge dans Cloud Manager pour le service de création ou le service de publication, ou les deux, dans un environnement.

### Pipelines front-end et Listes autorisées IP {#front-end-pipeline}

Si vous utilisez ou avez l’intention d’utiliser le pipeline front-end [ pour développer des sites](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md), la Liste autorisée IP Cloud Manager suivante doit être ajoutée au préalable.

Lorsque vous [ajoutez la Liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md#add-cm-allowlist), donnez-lui *`Cloud Manager`* nom, puis copiez la liste d’adresses ci-dessous et collez-la dans la boîte de dialogue Liste autorisée IP .

```text
52.254.106.192/28
20.186.185.181
52.254.106.240/28
52.254.107.128/28
52.254.105.192/28
52.254.106.176/28
20.186.185.227
52.254.106.144/28
52.254.107.64/28
20.186.185.239
20.22.83.112
52.254.107.80/28
52.254.107.144/28
52.254.106.224/28
20.14.241.153
52.254.107.0/28
52.254.107.32/28
52.254.106.208/28
40.70.154.136/29
52.254.106.160/28
52.254.107.16/28
52.254.106.0/28
4.152.211.251
```

Pour éviter toute interruption de l’exécution du pipeline front-end, assurez-vous que cette Liste autorisée IP Cloud Manager est ajoutée. Appliquez ensuite la liste à l’environnement de création *avant* d’activer le pipeline.

Voir [Appliquer la Liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) et [Activer le pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md) pour plus d’informations.

### L’éditeur universel et les Listes autorisées IP {#universal-editor}

Si vous avez l’intention d’utiliser l’éditeur universel pour créer votre contenu, vous devez ajouter les adresses IP que le service d’éditeur universel utilise à une Liste autorisée et l’appliquer.

1. Récupérez les adresses IP utilisées par le service d’éditeur universel à partir du point d’entrée API suivant : `http://universal-editor-service.adobe.io/ip-ranges`.
1. Créez une liste autorisée avec ces adresses IP, en lui attribuant un nom `Universal Editor Service` ou similaire.
1. Appliquez la liste autorisée `Universal Editor Service`.

La liste des adresses IP utilisées par le service d’éditeur universel peut être modifiée et vous devez mettre à jour votre liste autorisée en conséquence.
