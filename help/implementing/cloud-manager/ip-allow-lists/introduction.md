---
title: Présentation des listes d’adresses IP autorisées
description: Découvrez comment les listes d’adresses IP autorisées peuvent limiter les adresses à partir desquelles les utilisateurs peuvent accéder à vos domaines AEM as a Cloud Service.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 18ecf3394ff575213756fced84a3b08795188240
workflow-type: ht
source-wordcount: '319'
ht-degree: 100%

---


# Présentation des listes d’adresses IP autorisées {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="Gérer les listes d’adresses IP autorisées"
>abstract="AEM as a Cloud Service est accessible par le biais d’Internet et sa sécurité est assurée par l’authentification et l’autorisation des utilisateurs. Les listes d’adresses IP autorisées de Cloud Manager peuvent être utilisées pour contrôler l’accès et le limiter uniquement aux adresses IP de confiance. Les utilisateurs de Cloud Manager disposant des autorisations appropriées peuvent créer des listes autorisées d’adresses IP de confiance à partir desquelles les utilisateurs de leur site peuvent accéder à leurs domaines d’AEM."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html?lang=fr" text="Ajout d’une liste d’adresses IP autorisées"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html?lang=fr" text="Affichage et mise à jour de la liste des adresses IP autorisées"

AEM as a cloud service est par défaut accessible via Internet. Bien que la sécurité soit gérée au moyen de l’authentification et de l’autorisation des utilisateurs et utilisatrices, la liste autorisée d’adresses IP permet de limiter l’accès aux seules adresses IP de confiance.

Les listes autorisées d’adresses IP de Cloud Manager peuvent être utilisées pour contrôler l’accès et le limiter uniquement aux adresses IP de confiance. Les utilisateurs et utilisatrices de Cloud Manager disposant des autorisations appropriées peuvent [créer des listes autorisées](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) d’adresses IP de confiance à partir desquelles les utilisateurs et utilisatrices de leur site peuvent accéder à leurs domaines d’AEM.

Une fois ajoutées, les [listes autorisées d’adresses IP peuvent être appliquées/annulées](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) plusieurs fois en tant qu’unité ou entité à un service création et/ou publication dans un environnement.

>[!NOTE]
>
>Si aucune liste autorisée d’adresses IP n’est appliquée, toutes les adresses IP sont autorisées par défaut. Dès qu’une liste autorisée d’adresses IP est appliquée, aucune adresse IP n’est autorisée, à l’exception de celles présentes sur la liste.

## Limites {#limitations}

Les listes d’adresses IP autorisées présentent un certain nombre de restrictions que vous devez garder à l’esprit.

* Vous pouvez ajouter jusqu’à 50 listes d’adresses IP autorisées à votre programme.
* Il est possible d’ajouter jusqu’à 50 adresses IP/CIDR à chaque liste d’adresses IP autorisées.
* Les noms des listes d’adresses IP autorisées sont pris en charge dans Cloud Manager pour les services de création ou de publication dans un environnement.
