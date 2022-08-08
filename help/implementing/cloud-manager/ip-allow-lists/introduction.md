---
title: Présentation des listes d’adresses IP autorisées
description: Découvrez comment les listes d’adresses IP autorisées peuvent limiter les adresses à partir desquelles les utilisateurs peuvent accéder à vos domaines AEM as a Cloud Service.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 8d1680fa8dbaaefa297cf8c6698097b3c7acc48d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 100%

---


# Présentation des listes d’adresses IP autorisées {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Gérer les listes d’adresses IP autorisées"
>abstract="AEM as a Cloud Service est accessible par le biais d’Internet et sa sécurité est assurée par l’authentification et l’autorisation des utilisateurs. Les listes d’adresses IP autorisées de Cloud Manager peuvent être utilisées pour contrôler l’accès et le limiter uniquement aux adresses IP de confiance. Les utilisateurs de Cloud Manager disposant des autorisations appropriées peuvent créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines d’AEM."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html?lang=fr" text="Ajout d’une liste d’adresses IP autorisées"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html?lang=fr" text="Affichage et mise à jour de la liste des adresses IP autorisées"

AEM as a Cloud Service est accessible par le biais d’Internet et sa sécurité est assurée par l’authentification et l’autorisation des utilisateurs. Les listes d’adresses IP autorisées de Cloud Manager peuvent être utilisées pour contrôler l’accès et le limiter uniquement aux adresses IP de confiance. Les utilisateurs de Cloud Manager disposant des autorisations appropriées peuvent créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines d’AEM.

Les listes d’adresses IP autorisées peuvent être ajoutées une fois et appliquées ou non appliquées plusieurs fois en tant qu’unité ou entité à un service auteur et publication dans un environnement.

## Limites {#limitations}

Les listes d’adresses IP autorisées présentent un certain nombre de restrictions que vous devez garder à l’esprit.

* Vous pouvez ajouter jusqu’à 50 listes d’adresses IP autorisées à votre programme.
* Il est possible d’ajouter jusqu’à 50 adresses IP/CIDR à chaque liste d’adresses IP autorisées.
* Les noms des listes d’adresses IP autorisées sont pris en charge dans Cloud Manager pour les services de création ou de publication dans un environnement.
