---
title: Présentation des Listes autorisées IP
description: Découvrez comment les listes autorisées IP peuvent limiter les adresses à partir desquelles les utilisateurs peuvent accéder à vos domaines as a Cloud Service AEM.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 8d1680fa8dbaaefa297cf8c6698097b3c7acc48d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 11%

---


# Présentation des Listes autorisées IP {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Gestion des listes autorisées d’adresses IP"
>abstract="AEM as a cloud service est accessible via Internet et sécurisé via l’authentification et l’autorisation des utilisateurs. Les listes autorisées IP de Cloud Manager peuvent être utilisées pour limiter et contrôler l’accès uniquement aux adresses IP de confiance. Les utilisateurs de Cloud Manager disposant des autorisations appropriées peuvent créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines d’AEM."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html?lang=fr" text="Ajout d’une liste d’adresses IP autorisées"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html?lang=fr" text="Affichage et mise à jour de la liste des adresses IP autorisées"

AEM as a cloud service est accessible via Internet et sécurisé via l’authentification et l’autorisation des utilisateurs. Les listes autorisées IP de Cloud Manager peuvent être utilisées pour limiter et contrôler l’accès uniquement aux adresses IP de confiance. Les utilisateurs de Cloud Manager disposant des autorisations appropriées peuvent créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines d’AEM.

Les listes autorisées IP peuvent être ajoutées une seule fois et appliquées/non appliquées plusieurs fois en tant qu’entité ou entité à un service de création et/ou d’éditeur dans un environnement.

## Limites {#limitations}

Les listes d’adresses IP autorisées ont un certain nombre de limitations à garder à l’esprit.

* 50 listes autorisées IP au maximum peuvent être ajoutées à votre programme
* Il est possible d’ajouter un maximum de 50 adresses IP/CIDR à chaque liste autorisée IP.
* Les noms de listes autorisées IP sont pris en charge dans Cloud Manager pour le service de création et/ou de publication dans un environnement.
