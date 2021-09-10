---
title: Introduction – Listes autorisées IP dans Cloud Manager
description: Introduction – Listes autorisées IP dans Cloud Manager
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 1875920ae5180074dcad98fb5c10242b6baa76c7
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 86%

---

# Présentation {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Gestion des Listes autorisées IP"
>abstract="AEM as a Cloud Service a accès à Internet, et la sécurité est gérée par l’authentification et l’autorisation des utilisateurs. La liste des adresses IP autorisées est une fonctionnalité de Cloud Manager permettant de contrôler l’accès et de le limiter aux utilisateurs de confiance uniquement. Cette fonctionnalité permet aux utilisateurs autorisés de créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leurs sites peuvent accéder à leurs domaines AEM."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html?lang=fr" text="Ajout d’une Liste autorisée IP"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html?lang=fr" text="Affichage et mise à jour d’une Liste autorisée IP"

AEM as a Cloud Service a accès à Internet, et la sécurité est gérée par l’authentification et l’autorisation des utilisateurs. La liste des adresses IP autorisées est une fonctionnalité de Cloud Manager permettant de contrôler l’accès et de le limiter aux utilisateurs de confiance uniquement. Cette fonctionnalité permet aux utilisateurs autorisés de créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leurs sites peuvent accéder à leurs domaines AEM.

>[!NOTE]
>Vous pouvez ajouter un maximum de 50 Listes autorisées IP dans votre programme et 50 adresses IP/CIDR peuvent être ajoutées à chaque Liste autorisée IP.

Les listes autorisées d’adresses IP peuvent être ajoutées une fois et appliquées/non appliquées plusieurs fois en tant qu’unité ou entité à un service auteur et/ou publicateur dans un environnement.

>[!NOTE]
>Les noms des listes d’adresses IP autorisées sont pris en charge dans Cloud Manager pour les services d’auteur ou de publication dans un environnement.

La page Liste autorisée IP de l’interface utilisateur Cloud Manager ou la page Détails de l’environnement permet à un utilisateur disposant d’autorisations d’effectuer plusieurs tâches afin de gérer les listes autorisées IP de vos environnements, y compris :

* [Ajout d’une liste d’adresses IP autorisées](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md)
   >[!NOTE]
   > Vous pouvez ajouter une fois et réutiliser ou appliquer la règle autant de fois que vous le voulez dans les services d’environnement du programme.
* [Affichage ou mise à jour d’une liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/view-update-ip-allow-list.md)
* [Application ou annulation de l’application d’une liste autorisée IP](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)
* [Suppression d’une liste autorisée d’adresses IP](/help/implementing/cloud-manager/ip-allow-lists/delete-ip-allow-list.md)
