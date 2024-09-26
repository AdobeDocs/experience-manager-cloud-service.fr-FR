---
title: Gestion des entités
description: Gestion des entités pour la migration à l’aide d’Admin Console
exl-id: a75598d0-8f59-466b-984e-dfe527388c2a
source-git-commit: a5bec2c05b46f8db55762b7ee1f346f3bb099d24
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 7%

---

# Gestion des entités {#managing-principals}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_managingprincipals"
>title="Gestion des entités"
>abstract="Découvrez ce qui doit être fait pour gérer les utilisateurs et utilisatrices pendant ou après une migration de contenu."

Avant que le contenu ne soit transféré vers l’environnement cloud AEM as a Cloud Service, certaines tâches peuvent être effectuées sur l’Admin Console.  Il s’agit de : créer des utilisateurs, créer des groupes et affecter des utilisateurs à des groupes ; ces utilisateurs et groupes existent dans IMS, le service Identity Management d’Adobe, qui est utilisé pour gérer les utilisateurs et les groupes pour tous les services cloud d’Adobe.

### Création de groupes et de leurs utilisateurs dans Admin Console

[L’utilisation d’Admin Console pour AEM Principals](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/ims-support#how-to-set-up) fournit des instructions détaillées sur la création d’utilisateurs et de groupes dans IMS, ainsi que sur la manière d’ajouter des utilisateurs aux groupes en même temps ou ultérieurement.  Le document comprend trois options pour les créer : manuellement par l’intermédiaire de l’Admin Console, au moyen d’un fichier CSV transféré via l’Admin Console et via un outil de synchronisation des utilisateurs.

L’option manuelle vous permet de créer un groupe ou un utilisateur à la fois ; le transfert CSV vous permet de créer et de lier plusieurs utilisateurs et groupes à la fois ; et l’outil de synchronisation des utilisateurs vous permet d’utiliser un fournisseur d’identité existant pour créer et gérer les utilisateurs et groupes IMS.

Une fois qu’un utilisateur utilise IMS pour se connecter à AEM, une représentation AEM de l’utilisateur est créée.  En outre, tous les groupes IMS dans lesquels se trouve l’utilisateur auront des groupes AEM équivalents créés dans AEM.  Ces utilisateurs et groupes d’AEM créés par IMS sont toujours principalement gérés à l’aide de l’Admin Console.

Une fois la migration du contenu terminée, les groupes IMS devront généralement disposer d’une configuration supplémentaire pour pouvoir accéder au contenu migré.  Voir [Migration des entités après la migration](/help/journey-migration/managing-principals-after-migration.md)

Voir aussi [Tutoriel, AEM utilisateurs, groupes et autorisations](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions) pour en savoir plus sur l’intégration et l’administration des utilisateurs et groupes AEM et IMS.
