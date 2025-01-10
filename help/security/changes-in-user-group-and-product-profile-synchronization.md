---
title: Modifications dans la synchronisation des groupes d’utilisateurs et des profils de produits
description: Découvrez les modifications apportées à la synchronisation des groupes d’utilisateurs et des profils de produits dans AEM as a Cloud Service
feature: Security
role: Admin
hide: true
hidefromtoc: true
source-git-commit: 32ce30ce136a714e277e00197d38ea380c777377
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Modifications dans la synchronisation des groupes d’utilisateurs et des profils de produits {#changes-in-user-group-and-product-profile-synchronization}

Chaque fois qu’un utilisateur se connecte à AEM as a Cloud Service ou qu’un jeton d’accès est utilisé, les groupes d’utilisateurs Adobe Admin Console, les profils de produit et les services de profil de produit sont synchronisés dans le référentiel AEM en tant que groupes.

Le 28 janvier, afin de réduire l’encombrement de l’interface utilisateur et d’optimiser les performances, quelques modifications seront apportées au comportement de synchronisation, ce qui réduira le nombre de groupes apparaissant dans AEM. Deux catégories de groupes AEM seront supprimées :

1. Groupes AEM avec suffixe `GROUP_NAME_SUFFIX`. Ces groupes n’apparaissent pas dans Adobe Developer Console, mais dans l’écran Gestion des groupes AEM, comme illustré ci-dessous. Dans le cas peu probable où votre application AEM fait référence à ces groupes, veillez à référencer les groupes d’utilisateurs Adobe Admin Console sans ce suffixe à la place.

   ![Groupes supprimés 1](/help/security/assets/removed-groups-1.png)

1. Groupes AEM associés aux profils de produits Adobe Admin Console sans rapport avec l’environnement spécifique. Cela peut inclure des profils de produit qui sont :

   * liés à d&#39;autres produits Adobes
   * associées à d&#39;autres programmes AEM
   * liées à d’autres environnements AEM du même programme AEM
   * associé à Cloud Manager (par exemple, `Business Owner - Cloud Service`)

   Par exemple, dans l’image ci-dessous, il existe de nombreuses lignes avec le modèle `AEM Administrators-<suffix>` ou `AEM Users-<suffix>` où le suffixe n’est pas associé à l’environnement actuel.

   ![Groupes supprimés 2](/help/security/assets/removed-groups-2.png)

Vous pouvez vérifier quel suffixe est associé à l’environnement actuel en sélectionnant Gérer **Accès - Profils de création** (ou **Profils Publish**) dans le menu d’actions de l’environnement dans Cloud Manager.

![Vérifier les suffixes](/help/security/assets/suffix-check.png)

Vous accédez alors au Adobe Admin Console, comme illustré dans la capture d’écran ci-dessous. Notez que le `<suffix>` peut être soit un ensemble aléatoire de caractères, soit le niveau, ainsi que les identifiants de programme et d’environnement (par exemple, `author - Program 12345 - Environment 45678`).

![Suffixes dans l’Admin Console ](/help/security/assets/admin-console-profile-suffixes.png)

Dans le cas peu probable où votre application AEM fait référence à un groupe qui n’apparaîtra plus dans AEM, veillez à utiliser i) un profil de produit de l’instance AEM appropriée ou ii) un groupe d’utilisateurs Adobe Admin Console.
