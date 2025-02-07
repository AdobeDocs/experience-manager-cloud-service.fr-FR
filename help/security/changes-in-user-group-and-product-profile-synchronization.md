---
title: Modifications concernant la synchronisation des groupes d’utilisateurs et d’utilisatrices et des profils de produits
description: Découvrez les modifications apportées à la synchronisation des groupes d’utilisateurs et d’utilisatrices et des profils de produits dans AEM as a Cloud Service.
feature: Security
role: Admin
hide: true
hidefromtoc: true
exl-id: 0b097ab3-bf1d-4d43-9e19-d544594844ef
source-git-commit: 5c103fcce1ae47bc89f4f572d89967c62c1f7603
workflow-type: ht
source-wordcount: '385'
ht-degree: 100%

---

# Modifications concernant la synchronisation des groupes d’utilisateurs et d’utilisatrices et des profils de produits {#changes-in-user-group-and-product-profile-synchronization}

Chaque fois qu’une personne se connecte à AEM as a Cloud Service ou qu’un jeton d’accès est utilisé, les groupes d’utilisateurs et d’utilisatrices, les profils de produit et les services de profil de produit d’Adobe Admin Console sont synchronisés dans le référentiel AEM en tant que groupes.

À partir de la version de maintenance 19149 d’AEM, le comportement de synchronisation des groupes est modifié pour réduire l’encombrement de l’interface d’utilisation et optimiser les performances. Plus précisément, l’appartenance à un groupe d’utilisateurs et d’utilisatrices des deux catégories de groupes AEM suivantes ne sera plus synchronisée :

1. Groupes AEM avec le suffixe `GROUP_NAME_SUFFIX`. Ces groupes n’apparaissent pas dans Adobe Developer Console, mais apparaissent sur l’écran de gestion des groupes dans AEM, comme illustré ci-dessous. Dans le cas peu probable où votre application AEM fait référence à ces groupes, veillez plutôt à référencer les groupes d’utilisateurs et d’utilisatrices Adobe Admin Console sans ce suffixe.

   ![Groupes supprimés 1](/help/security/assets/removed-groups-1.png)

1. Groupes AEM associés aux profils de produits Adobe Admin Console sans rapport avec l’environnement spécifique. Cela peut inclure des profils de produit qui sont :

   * associés à d’autres produits Adobe ;
   * associés à d’autres programmes AEM ;
   * associés à d’autres environnements AEM dans un même programme AEM ;
   * associés à Cloud Manager (par exemple, `Business Owner - Cloud Service`).

   Par exemple, sur l’image ci-dessous, il y a de nombreuses lignes avec le motif `AEM Administrators-<suffix>` ou `AEM Users-<suffix>` où le suffixe n’est pas associé à l’environnement actuel.

   ![Groupes supprimés 2](/help/security/assets/removed-groups-2.png)

Vous pouvez vérifier quel suffixe est associé à l’environnement actuel en sélectionnant Gérer **Accès - Profils de création** (ou **Profils de publication**) dans le menu d’actions de l’environnement dans Cloud Manager.

![Vérification des suffixes](/help/security/assets/suffix-check.png)

Vous accédez alors à Adobe Admin Console, comme illustré sur la capture d’écran ci-dessous. Notez que le `<suffix>` peut être soit un ensemble aléatoire de caractères, soit les identifiants de niveau, de programme et d’environnement (par exemple, `author - Program 12345 - Environment 45678`).

![Suffixes dans Admin Console](/help/security/assets/admin-console-profile-suffixes.png)

Dans le cas peu probable où votre application AEM fait référence à un groupe qui n’apparaîtra plus dans AEM, veillez plutôt à utiliser i) un profil de produit de l’instance AEM appropriée ou ii) un groupe d’utilisateurs et d’utilisatrices Adobe Admin Console.

L’appartenance de la personne à des groupes est synchronisée lorsqu’elle se connecte à l’environnement et elle est supprimée des groupes non liés à l’environnement actuel. Les groupes eux-mêmes restent et incluent les personnes qui ne se sont pas connectées depuis que la fonctionnalité a été activée.
