---
title: Gestion des principaux
description: Gestion des entités pour la migration à l’aide d’Admin Console
exl-id: a75598d0-8f59-466b-984e-dfe527388c2a
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 100%

---

# Gestion des principaux {#managing-principals}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_managingprincipals"
>title="Gestion des principaux"
>abstract="Découvrez ce qui doit être fait pour gérer les utilisateurs et utilisatrices pendant ou après une migration de contenu."

Avant que le contenu ne soit transféré vers l’environnement cloud AEM as a Cloud Service, certaines tâches peuvent être effectuées sur Admin Console.  Il s’agit de : créer des utilisateurs et utilisatrices, créer des groupes et affecter des utilisateurs et utilisatrices à des groupes ; ces utilisateurs et utilisatrices et groupes existent dans IMS, le service Identity Management d’Adobe, qui est utilisé pour gérer les utilisateurs et utilisatrices et les groupes pour tous les services cloud d’Adobe.

## Création de groupes et de leurs utilisateurs et utilisatrices dans Admin Console

[L’utilisation d’Admin Console pour les entités AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/ims-support#how-to-set-up) fournit des instructions détaillées sur la création d’utilisateurs et utilisatrices et de groupes dans IMS, ainsi que sur la manière d’ajouter des utilisateurs et utilisatrices aux groupes en même temps ou ultérieurement.  Le document comprend trois options pour les créer : manuellement par l’intermédiaire d’Admin Console, au moyen d’un fichier CSV chargé via Admin Console et via un outil de synchronisation des utilisateurs et utilisatrices.

L’option manuelle vous permet de créer un groupe ou un utilisateur ou une utilisatrice à la fois ; le chargement CSV vous permet de créer et de lier plusieurs utilisateurs et utilisatrices et groupes à la fois ; et l’outil de synchronisation des utilisateurs et utilisatrices vous permet d’utiliser un fournisseur d’identité existant pour créer et gérer les utilisateurs et utilisatrices et groupes IMS.

Une fois qu’un utilisateur ou une utilisatrice utilise IMS pour se connecter à AEM, une représentation AEM de l’utilisateur ou de l’utilisatrice est créée.  En outre, tous les groupes IMS dans lesquels se trouve l’utilisateur ou l’utilisatrice auront des groupes AEM équivalents créés dans AEM.  Ces utilisateurs et utilisatrices et groupes AEM créés par IMS sont toujours principalement gérés à l’aide d’Admin Console.

Une fois la migration du contenu terminée, les groupes IMS devront généralement disposer d’une configuration supplémentaire pour pouvoir accéder au contenu migré.  Voir [Migration des entités après la migration](/help/journey-migration/managing-principals-after-migration.md)

Voir aussi [Tutoriel, utilisateurs et utilisatrices AEM, groupes et autorisations](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions) pour en savoir plus sur l’intégration et l’administration des utilisateurs et utilisatrices et groupes AEM et IMS.
