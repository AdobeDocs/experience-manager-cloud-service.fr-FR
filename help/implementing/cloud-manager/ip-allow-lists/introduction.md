---
title: Présentation des listes d’adresses IP autorisées
description: Découvrez comment les Listes autorisées IP peuvent limiter les adresses à partir desquelles les utilisateurs peuvent accéder aux domaines dans AEM as a Cloud Service.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1415d07235641262814e81362c806572bcf582ba
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 15%

---


# Présentation des listes d’adresses IP autorisées {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Gérer les listes d’adresses IP autorisées"
>abstract="AEM as a Cloud Service est accessible par Internet et sécurisé par l’authentification et l’autorisation des utilisateurs. Les Listes autorisées IP de Cloud Manager peuvent être utilisées pour limiter et contrôler l’accès uniquement aux adresses IP de confiance. Les utilisateurs et utilisatrices de Cloud Manager disposant des autorisations appropriées peuvent créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines d’AEM."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists" text="Ajouter une liste d’adresses IP autorisées"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists" text="Affichage et mise à jour d’une Liste autorisée IP"

AEM as a Cloud Service est par défaut accessible via Internet. Bien que la sécurité soit gérée au moyen de l’authentification et de l’autorisation des utilisateurs et utilisatrices, la liste autorisée d’adresses IP permet de limiter l’accès aux seules adresses IP de confiance.

Les Listes autorisées IP de Cloud Manager peuvent être utilisées pour limiter et contrôler l’accès uniquement à ces adresses IP approuvées. Les utilisateurs de Cloud Manager disposant des autorisations appropriées peuvent [créer et ajouter des Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines d’AEM.

Après l’ajout de , [les Listes autorisées IP peuvent être appliquées ou non ](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) plusieurs fois en tant qu’unité ou entité à un service de création, ou à un service d’éditeur, ou les deux, dans un environnement.

>[!NOTE]
>
>Si aucune Liste autorisée IP n’est appliquée, toutes les adresses IP sont autorisées par défaut. Lorsqu’une Liste autorisée IP est appliquée, aucune adresse IP n’est autorisée, à l’exception des adresses de la Liste autorisée IP.

## Utilisation de la Liste autorisée IP Cloud Manager avec le pipeline frontal {#allowlists-frontend-pipeline}

Si vous utilisez (ou envisagez d’utiliser) le pipeline [front-end pour développer des sites](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md), la Liste autorisée IP Cloud Manager suivante doit être ajoutée au préalable.

Lorsque vous [ajoutez la Liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md#add-cm-allowlist), nommez-la *`Cloud Manager`*, puis copiez la liste des adresses ci-dessous et collez-les dans la boîte de dialogue Liste autorisée IP.

**Liste autorisée IP Cloud Manager**

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

Pour éviter toute interruption de l’exécution du pipeline frontal, assurez-vous que cette Liste autorisée IP Cloud Manager est ajoutée. Ensuite, appliquez la liste à l’environnement de création *avant* d’activer le pipeline.

Voir [Appliquer la Liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md).
Voir [Activation du pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md).


## Limites {#limitations}

Les Listes autorisées IP ont plusieurs limites à garder à l’esprit.

* Vous pouvez ajouter un maximum de 50 Listes autorisées IP à votre programme.
* Il est possible d’ajouter un maximum de 50 adresses IP/CIDR à chaque Liste autorisée IP.
* Les noms de Liste autorisée IP sont pris en charge dans Cloud Manager pour le service de création ou de publication, ou les deux, dans un environnement.
