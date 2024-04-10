---
title: Présentation des listes d’adresses IP autorisées
description: Découvrez comment les listes d’adresses IP autorisées peuvent limiter les adresses à partir desquelles les utilisateurs et utilisatrices peuvent accéder à vos domaines AEM as a Cloud Service.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: f0edd0e3deeba89dcbd2dc1a07859138b24e2220
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 100%

---


# Présentation des listes d’adresses IP autorisées {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Gérer les listes d’IP autorisées"
>abstract="AEM as a Cloud Service est accessible par le biais d’Internet et sa sécurité est assurée par l’authentification et l’autorisation des utilisateurs et utilisatrices. Les listes d’adresses IP autorisées de Cloud Manager peuvent être utilisées pour contrôler l’accès et le limiter uniquement aux adresses IP de confiance. Les utilisateurs et utilisatrices de Cloud Manager disposant des autorisations appropriées peuvent créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines d’AEM."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html" text="Ajouter une liste d’adresses IP autorisées"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists.html?lang=fr" text="Afficher et mettre à jour une liste d’adresses IP autorisées"

AEM as a cloud service est par défaut accessible via Internet. Bien que la sécurité soit gérée au moyen de l’authentification et de l’autorisation des utilisateurs et utilisatrices, la liste autorisée d’adresses IP permet de limiter l’accès aux seules adresses IP de confiance.

Les listes d’adresses IP autorisées de Cloud Manager peuvent être utilisées pour contrôler l’accès et le limiter uniquement aux adresses IP de confiance. Les utilisateurs et utilisatrices de Cloud Manager disposant des autorisations appropriées peuvent [créer des listes autorisées](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) d’adresses IP de confiance à partir desquelles les utilisateurs et utilisatrices de leur site peuvent accéder à leurs domaines AEM.

Une fois ajoutées, les [listes d’adresses IP autorisées peuvent être appliquées/annulées](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) plusieurs fois en tant qu’unité ou entité à un service de création et/ou de publication dans un environnement.

>[!NOTE]
>
>Si aucune liste d’adresses IP autorisées n’est appliquée, toutes les adresses IP sont autorisées par défaut. Lorsqu’une liste d’adresses IP autorisées est appliquée, aucune adresse IP n’est autorisée, à l’exception des adresses répertoriées dans la liste d’adresses IP autorisées.

## Limites {#limitations}

Les listes d’adresses IP autorisées ont plusieurs limites qu’il convient de garder à l’esprit.

* Vous pouvez ajouter jusqu’à 50 listes d’adresses IP autorisées à votre programme
* Il est possible d’ajouter jusqu’à 50 adresses IP/CIDR à chaque liste d’adresses IP autorisées.
* Les noms des listes d’adresses IP autorisées sont pris en charge dans Cloud Manager pour les services de création et/ou de publication dans un environnement.
