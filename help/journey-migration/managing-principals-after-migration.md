---
title: Gérer des entités après la migration
description: Découvrez comment configurer des utilisateurs et utilisatrices et des groupes dans IMS et AEM.
exl-id: 46c4abfb-7e28-4f18-a6d4-f729dd42ea7b
source-git-commit: a5bec2c05b46f8db55762b7ee1f346f3bb099d24
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 5%

---

# Gérer des entités après la migration {#managing-principals-after-migration}

>[!CONTEXTUALHELP]
>id="managing-principals"
>title="Gérer des entités après la migration"
>abstract="Découvrez comment configurer des utilisateurs et utilisatrices et des groupes dans IMS et AEM."

Ce document décrit les étapes générales que doivent suivre les clients pour configurer leurs utilisateurs et groupes dans IMS et les AEM pour travailler avec leur environnement AEM as a Cloud Service.

## Gestion des entités {#managing-principals}

Pour AEM as a Cloud Service, les utilisateurs et les groupes doivent être gérés principalement à l’aide de l’Admin Console.  Lorsque vous envisagez une migration, certaines de ces tâches peuvent être réalisées avant la migration du contenu.  Essentiellement, de ces groupes de tâches principaux

* Création d’utilisateurs et de groupes dans IMS
* Affectation d’utilisateurs à des groupes dans IMS
* Affecter des groupes IMS à des groupes AEM (si nécessaire)

les deux premières peuvent être réalisées avant ou après la migration du contenu.  Il s’agit d’étapes qui affectent uniquement les utilisateurs et les groupes dans IMS, notamment éventuellement l’intégration à un fournisseur d’identité externe tel qu’Active Directory ou LDAP.  Ces étapes sont décrites dans la section [Gestion des entités dans IMS avec l’Admin Console](/help/journey-migration/managing-principals.md).

Une fois le contenu migré vers l&#39;environnement AEM as a Cloud Service, la troisième étape peut être effectuée.

### Migration de groupes

Lors de la phase d’ingestion de la migration, les groupes sont migrés s’ils sont nécessaires pour satisfaire les listes de contrôle d’accès ou les stratégies de CUG sur le contenu migré.  Pour plus d’informations, voir [Migration de groupe](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) .

Les groupes migrés (ceux qui ne sont pas créés par la création de collections Assets — voir Collections ci-dessous) sont configurés en tant que groupes IMS.  Cela signifie que tout groupe du même nom créé dans IMS (via l’Admin Console, par exemple) sera lié au groupe dans AEM, et les utilisateurs qui sont membres du groupe IMS deviendront également membres du groupe dans AEM.  Pour que cette liaison se produise, le groupe doit également être créé en premier dans IMS.  Utilisez l’Admin Console pour créer des groupes, individuellement ou en bloc, dans votre instance AEM, comme décrit dans la section [Gestion des entités dans IMS avec l’Admin Console](/help/journey-migration/managing-principals.md).

Utilisez l’interface utilisateur de sécurité d’AEM pour affecter des groupes IMS à des groupes AEM locaux.  Voir [Création et configuration de groupes](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-groups#edit-a-group).  Bien que ce document concerne AEM version 6.5, il s’applique également à l’ajout de groupes à d’autres groupes dans AEM as a Cloud Service.

### Utilisateurs IMS

Les utilisateurs n’étant pas migrés, ils doivent être créés dans IMS afin de pouvoir être utilisés dans AEM.  Il existe plusieurs façons d’y parvenir, mais il est important que les utilisateurs créés soient affectés aux groupes IMS appropriés afin que les utilisateurs aient le même accès au contenu qu’ils avaient dans le système AEM précédent.  L’un des outils pouvant être utilisé à cette fin est la fonctionnalité de chargement en masse de l’Admin Console ; utilisez le téléchargement en masse pour charger les utilisateurs avec les groupes dont ils doivent être membres.  Avant cela, les groupes doivent d’abord être créés dans IMS, comme décrit ci-dessus.

Pour savoir à quels groupes chaque utilisateur doit appartenir, vous pouvez utiliser le rapport utilisateur (voir [Migration de groupe](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md)).  Ce rapport répertorie les groupes dont chaque utilisateur doit être membre. Cette liste peut être incluse dans le fichier d’entrée de la fonctionnalité de transfert en masse de l’Admin Console.

### Collections

La création d’une collection Assets crée également automatiquement certains groupes pour gérer l’accès à cette collection.  Ces groupes sont migrés s’ils sont mentionnés sur les collections migrées, mais ils ne sont pas configurés pour être directement liés aux groupes IMS ; en AEM ils restent des &quot;groupes locaux&quot; et ils ne peuvent pas être gérés via IMS.

Ces groupes ne se trouvant pas dans IMS, l’outil de chargement en masse ne peut pas être utilisé pour créer des utilisateurs en tant que membres directs.  Les utilisateurs IMS qui se trouvent également dans AEM peuvent être ajoutés à ces groupes individuellement, mais cela nécessite une étape supplémentaire.  Vous pouvez procéder de la manière suivante :
* Créez un ou plusieurs groupes dans Admin Console/IMS pour accéder aux collections et les configurer pour AEM.
* Connectez-vous en tant que membre du ou des groupes afin que ceux-ci soient créés dans AEM.
* Pour les collections migrées, utilisez l’interface utilisateur Collections Assets pour ajouter le nouveau groupe en tant qu’éditeur/propriétaire/visionneuse.
* Ajoutez des utilisateurs (ou transférez en masse) au nouveau groupe dans Admin Console.
* Lorsque l’utilisateur se connecte pour la première fois, son utilisateur IMS est créé dans AEM et il doit avoir accès au(x) nouveau(s) groupe(s) et donc aux groupes de collection d’origine.

Remarque : Pour l’affectation en masse d’utilisateurs, les étapes ci-dessus doivent être utilisées pour créer les utilisateurs dans IMS ; les utilisateurs qui existent déjà dans IMS ne peuvent pas être recréés par téléchargement en masse.
