---
title: Gérer des entités après la migration
description: Découvrez comment configurer des utilisateurs et utilisatrices et des groupes dans IMS et AEM.
exl-id: 46c4abfb-7e28-4f18-a6d4-f729dd42ea7b
source-git-commit: 1c638f3d1cca4f97eb1f760054febd405b5714f5
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 79%

---

# Gérer des entités après la migration {#managing-principals-after-migration}

>[!CONTEXTUALHELP]
>id="managing-principals"
>title="Gérer des entités après la migration"
>abstract="Découvrez comment configurer des utilisateurs et utilisatrices et des groupes dans IMS et AEM."

Ce document décrit les étapes générales que doivent suivre les clients et les clientes pour configurer leurs utilisateurs, utilisatrices et groupes dans IMS et AEM afin de travailler avec leur environnement AEM as a Cloud Service.

Pour plus d’informations sur la migration de groupe et le rapport de migration principale disponible avec chaque ingestion, voir [ Migration de groupe ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

Pour obtenir un guide sur l’utilisation des fichiers de groupe en bloc et d’utilisateur dans Admin Console, voir [Chargement en bloc des entités de sécurité dans IMS après avoir utilisé CTT](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/bulk-principal-uploading.md).

## Gestion des principaux {#managing-principals}

Pour AEM as a Cloud Service, les utilisateurs, les utilisatrices et les groupes doivent être gérés principalement à l’aide d’Admin Console.  Si vous envisagez d’effectuer une migration, certaines tâches peuvent être réalisées avant la migration du contenu.  De ces groupes de tâches principaux,

* Créer des utilisateurs, des utilisatrices et des groupes dans IMS
* Affecter des utilisateurs et des utilisatrices à des groupes dans IMS
* Affecter des groupes IMS à des groupes AEM (le cas échéant)

Les deux premières peuvent être effectuées avant ou après la migration du contenu.  Il s’agit d’étapes qui affectent uniquement les utilisateurs, les utilisatrices et les groupes dans IMS, éventuellement l’intégration à un fournisseur d’identité externe tel qu’Active Directory ou LDAP.  Vous trouverez ces étapes dans la section [Gestion des principaux dans IMS avec Admin Console](/help/journey-migration/managing-principals.md).

Une fois le contenu migré vers l’environnement AEM as a Cloud Service, vous pouvez effectuer la troisième étape.

### Migration des groupes

Lors de la phase d’ingestion de la migration, les groupes sont migrés s’ils sont nécessaires pour satisfaire les listes de contrôle d’accès ou les stratégies de CUG du contenu migré.  Pour plus d’informations, voir la section [Migration des groupes](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

Les groupes migrés (ceux qui ne sont pas créés par la création de collections de ressources — voir Collections ci-dessous) sont configurés en tant que groupes IMS.  Cela signifie que tout groupe du même nom créé dans IMS (via Admin Console, par exemple) sera lié au groupe dans AEM, et les utilisateurs et utilisatrices membres du groupe IMS deviendront également membres du groupe dans AEM.  Pour établir cette liaison, le groupe doit être créé en premier dans IMS.  Utilisez Admin Console pour créer des groupes, un par un ou en masse, dans votre instance AEM, comme décrit dans la section [Gestion des principaux dans IMS avec Admin Console](/help/journey-migration/managing-principals.md).

Utilisez l’interface utilisateur de sécurité d’AEM pour affecter des groupes IMS aux groupes AEM locaux. Pour ce faire, accédez à la page Outils dans AEM, cliquez sur Sécurité, puis sélectionnez Groupes.

### Utilisateurs et utilisatrices IMS

Les utilisateurs et utilisatrices ne sont pas migrés. Vous devez les créer dans IMS afin de pouvoir les utiliser dans AEM.  Il existe plusieurs façons de procéder, mais le plus important est d’affecter les utilisateurs et utilisatrices créés aux groupes IMS appropriés afin qu’ils aient le même accès au contenu que dans le système AEM précédent.  Pour cela, vous pouvez utiliser la fonctionnalité de chargement en masse d’Admin Console. Utilisez le chargement en masse pour charger les utilisateurs et utilisatrices avec les groupes dont ils doivent être membres.  Avant cela, vous devez créer les groupes dans IMS, comme décrit ci-dessus.

Pour savoir à quels groupes doit appartenir chaque utilisateur et utilisatrice, vous pouvez utiliser le rapport utilisateur (voir [Migration de groupes](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md)).  Ce rapport répertorie les groupes dont chaque utilisateur doit être membre et cette liste est normalement incluse dans le fichier de saisie d’utilisateur en bloc à utiliser avec la fonctionnalité de chargement en bloc d’Admin Console.

### Collections

La création d’une collection de ressources entraîne la création automatique de certains groupes pour gérer l’accès à cette collection.  Ces groupes sont migrés s’ils sont mentionnés sur les collections migrées, mais ils ne sont pas configurés pour être directement liés aux groupes IMS. Dans AEM, ils restent des « groupes locaux » qui ne peuvent pas être gérés via IMS.

Ces groupes ne se trouvant pas dans IMS, vous ne pouvez pas utiliser l’outil de chargement en masse pour créer des utilisateurs et utilisatrices en tant que membres directs.  Vous pouvez ajouter un par un les utilisateurs et utilisatrices IMS qui se trouvent également dans AEM à ces groupes, mais cela suppose une étape supplémentaire.  Vous pouvez procéder de la manière suivante :
* Créez un ou plusieurs groupes dans Admin Console/IMS pour accéder aux collections et les configurer pour AEM.
* Connectez-vous en tant que membre du ou des groupes afin que ceux-ci soient créés dans AEM.
* Pour les collections migrées, utilisez l’interface des collections de ressources pour ajouter le nouveau groupe en tant qu’éditeur/propriétaire/observateur.
* Ajoutez (ou chargez en masse) des utilisateurs et utilisatrices au nouveau groupe dans Admin Console.
* Lorsque la personne se connecte pour la première fois, son utilisatrice ou utilisateur IMS est créé dans AEM. Elle devrait avoir accès aux nouveaux groupes et donc aux groupes de collection d’origine.

Remarque : pour l’affectation en bloc d’utilisateurs, les étapes ci-dessus doivent être utilisées pour créer les utilisateurs dans IMS. Les utilisateurs qui existent déjà dans IMS ne peuvent pas être créés à nouveau par le biais du téléchargement en bloc, bien que l’éditeur en bloc puisse être utilisé pour effectuer ce type de modifications (voir [Chargement d’utilisateurs en bloc Admin Console](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html) sous **Modifier les détails de l’utilisateur**).
