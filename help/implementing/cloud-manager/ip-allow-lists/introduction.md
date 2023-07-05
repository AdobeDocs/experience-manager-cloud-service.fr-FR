---
title: Présentation des listes d’adresses IP autorisées
description: Découvrez comment les listes autorisées IP peuvent limiter les adresses à partir desquelles les utilisateurs peuvent accéder aux domaines sur AEM as a Cloud Service.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: f0edd0e3deeba89dcbd2dc1a07859138b24e2220
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 44%

---


# Présentation des listes d’adresses IP autorisées {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Gérer les listes d’IP autorisées"
>abstract="AEM as a Cloud Service est accessible par le biais d’Internet et sa sécurité est assurée par l’authentification et l’autorisation des utilisateurs. Les listes d’adresses IP autorisées de Cloud Manager peuvent être utilisées pour contrôler l’accès et le limiter uniquement aux adresses IP de confiance. Les utilisateurs de Cloud Manager disposant des autorisations appropriées peuvent créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines d’AEM."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html" text="Ajout d’une liste d’adresses IP autorisées"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists.html?lang=fr" text="Affichage et mise à jour de la liste des adresses IP autorisées"

AEM as a cloud service est par défaut accessible via Internet. Bien que la sécurité soit gérée au moyen de l’authentification et de l’autorisation des utilisateurs et utilisatrices, la liste autorisée d’adresses IP permet de limiter l’accès aux seules adresses IP de confiance.

Les listes autorisées IP de Cloud Manager peuvent être utilisées pour limiter et contrôler l’accès uniquement à ces adresses IP approuvées. Les utilisateurs de Cloud Manager disposant des autorisations appropriées peuvent [création de listes autorisées](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines AEM.

Après l’ajout, [Les listes autorisées IP peuvent être appliquées/non appliquées](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) plusieurs fois en tant qu’entité ou entité à un service de création et/ou d’éditeur dans un environnement.

>[!NOTE]
>
>Si aucune liste autorisée IP n’est appliquée, toutes les adresses IP sont autorisées par défaut. Lorsqu’une liste autorisée IP est appliquée, aucune adresse IP n’est autorisée, à l’exception des adresses de la liste autorisée IP.

## Limites {#limitations}

Les listes autorisées IP ont plusieurs limites à garder à l’esprit.

* 50 listes autorisées IP au maximum peuvent être ajoutées à votre programme
* Il est possible d’ajouter un maximum de 50 adresses IP/CIDR à chaque liste autorisée IP.
* Les noms des listes autorisées IP sont pris en charge dans Cloud Manager pour le service de création, de publication ou les deux dans un environnement.
