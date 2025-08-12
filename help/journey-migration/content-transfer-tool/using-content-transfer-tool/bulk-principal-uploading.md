---
title: Chargement groupé des entités de sécurité dans IMS après l’utilisation du CTT
description: Cette section présente les fichiers de chargement en masse pour les groupes et les personnes, ainsi que leur utilisation dans Admin Console pour créer des groupes et des personnes dans IMS.
exl-id: 43ebd6f1-1492-461a-8d9b-2b55dcde9052
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '2384'
ht-degree: 3%

---

# Chargement en masse des entités principales dans IMS après l’utilisation de l’outil de transfert de contenu (CTT) {#bulk-principal-uploading}

>[!CONTEXTUALHELP]
>id="bulk-principal-uploading"
>title="Chargement en masse de entités princpales"
>abstract="Cette section présente les fichiers de chargement en masse pour les groupes et les personnes, ainsi que leur utilisation dans Admin Console pour créer des groupes et des personnes dans IMS."
>additional-url="https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/onboarding/journey/admin-console" text="Documentation dʼAEM Admin Console"
>additional-url="https://adminconsole.adobe.com/" text="AEM Admin Console"

## Présentation {#introduction}

La migration de contenu vers le cloud à l’aide du CTT et de CAM crée des groupes sur l’instance cloud d’AEM, mais elle ne peut rien faire pour placer des groupes ou des utilisateurs dans IMS. Ils doivent exister dans IMS pour être correctement gérés par les clients. Heureusement, Admin Console offre des fonctionnalités pour créer des groupes IMS et des utilisateurs en bloc. L’ingestion CAM facilite ce processus en enregistrant les fichiers d’entrée pour cette création en bloc, ce qui permet aux clients d’effectuer cette action Admin Console dans le cadre de leur processus de migration global. Deux types de fichiers de chargement en masse sont créés : un pour les groupes et un pour les utilisateurs.

Voir également [Gérer les utilisateurs](https://helpx.adobe.com/fr/enterprise/using/users.html) pour plus d’informations sur la gestion des utilisateurs d’AEM as a Cloud Service.

## Règles générales pour le téléchargement de fichiers {#rules}

Il existe quelques instructions générales pour modifier et utiliser les deux types de fichiers de chargement :

* L’accès administrateur à Admin Console doit d’abord être accordé avant que ces instructions puissent être suivies.
* Notez qu’il existe plusieurs façons de créer des utilisateurs et des groupes dans IMS.  Voir [Prise en charge IMS d’Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/ims-support) pour en savoir plus sur toutes les options disponibles.  Seules les méthodes de chargement en masse d’Admin Console sont décrites ici.
* Il existe trois types d’identité possibles dans IMS : Adobe ID, Enterprise ID et Federated ID.  Les instructions de cette page sont fournies pour **Adobe ID uniquement**.  Si vous devez utiliser Enterprise ID ou Federated ID, reportez-vous à la documentation complète d’[Admin Console](https://helpx.adobe.com/ca/enterprise/using/admin-console.html) ainsi qu’à la documentation spécifique pour le [chargement de groupes par lot d’Admin Console](https://helpx.adobe.com/ca/enterprise/using/user-groups.html) et le [chargement d’utilisateurs par lot d’Admin Console](https://helpx.adobe.com/ca/enterprise/using/bulk-upload-users.html).  Les spécifications des fichiers de chargement sont quelque peu différentes pour ces deux types d’identité.
* Si un seul champ CSV autorise plusieurs entrées (telles que plusieurs profils de produit, plusieurs groupes ou plusieurs administrateurs), les entrées doivent être contenues entre guillemets doubles et séparées par une virgule, c’est-à-dire `"profile 1,profile 2"`.

   * Dans ce cas, il est possible d&#39;utiliser des guillemets simples au lieu de guillemets doubles, mais la modification du fichier dans Microsoft Excel peut entraîner des problèmes d&#39;analyse. Si vous utilisez Excel pour modifier ces fichiers, veillez à utiliser des guillemets doubles au lieu de guillemets simples.

## Chargement groupé de groupes {#group-upload}

### Cas pratique : les groupes ont été migrés vers AEM as a Cloud Service, mais ces groupes ne sont pas présents dans IMS/Admin Console, ils doivent donc être chargés vers IMS via Admin Console.

Pour utiliser la fonctionnalité de chargement de groupe en bloc d’Admin Console après l’exécution d’une migration CTT/CAM, procédez comme suit :

1. Télécharger le fichier de groupe en bloc à partir de CAM

   1. Dans CAM, accédez à **Transfert de contenu** et sélectionnez **Tâches d’ingestion**.
   1. Cliquez sur les points de suspension (...) sur la ligne de l’ingestion en question, puis choisissez **Afficher le résumé principal**.
   1. Dans la boîte de dialogue qui s’affiche, sélectionnez **Fichier de groupe en bloc** dans la liste déroulante sous **Télécharger un fichier...** et cliquez sur le bouton **Télécharger**.
   1. Enregistrez le fichier CSV obtenu.

1. Modifier le fichier de groupe en bloc

   * Chaque ligne représente un groupe à charger, et comporte quatre champs (les noms des champs constituent la première ligne du fichier) :

      * _Nom du groupe d’utilisateurs_ - Le nom du groupe est obligatoire et peut contenir au maximum 255 caractères.  Le nom de ce groupe doit être identique dans IMS et AEM
      * _Description_ - Ce champ est facultatif et peut contenir un maximum de 255 caractères
      * _Administrateurs du groupe d’utilisateurs_ - Au moins un administrateur de groupe doit être inclus dans ce champ. Plusieurs administrateurs peuvent être affectés en séparant chaque administrateur par une virgule et en plaçant la liste entre guillemets. L’entrée de chaque administrateur doit inclure le type d’identité de l’utilisateur, suivi d’un trait d’union, puis l’adresse électronique.  par exemple,
        `"Adobe ID-myAdmin@example.com,Adobe ID-myOtherAdmin@example.com"`. N’insérez pas d’espace après la virgule séparant les administrateurs. Vous ne pouvez pas inclure dans Admin Console des utilisateurs (en tant qu’administrateurs) qui ne font pas actuellement partie de l’organisation
      * _Profils de produit attribués_ - Ce champ est facultatif. Vous pouvez attribuer plusieurs profils de produit en séparant chaque profil par une virgule et en plaçant la liste entre guillemets. Toutefois, les profils de produit que vous incluez doivent déjà être configurés pour l’organisation. Veillez à spécifier le nom du profil de produit et non le nom du produit.  L’appartenance à des profils de produit affectés à un groupe sera héritée par tous les utilisateurs placés dans ce groupe.  Pour trouver un profil de produit :

         1. Accéder à Admin Console
         1. Recherchez votre produit (c’est-à-dire Adobe Experience Manager as a Cloud Service), puis cliquez dessus.
         1. Recherchez votre environnement (instance) et cliquez dessus.
         1. Répertoriez les profils de produit, puis cliquez sur celui de votre environnement AEM. Le profil de produit se trouve en haut, à savoir « _Utilisateurs AEM - auteur - 12345 de programme - 012345_ d’environnement ».

   * Lors de la modification du fichier CSV, certaines applications peuvent ajouter des guillemets supplémentaires lors de l’enregistrement, ce qui entraîne l’échec du traitement. Il est recommandé d’examiner le fichier CSV brut dans un simple éditeur de texte pour s’assurer que chaque champ comporte uniquement un guillemet ouvrant et un guillemet fermant (et il ne doit pas s’agir de « guillemets intelligents »).

1. Chargez le fichier de groupe en bloc dans Admin Console.

   1. Dans Admin Console, accédez à **Utilisateurs**, puis **Groupes d’utilisateurs**
   1. Sur le côté droit, cliquez sur le bouton « ... ». Sélectionnez **Ajouter des groupes d’utilisateurs par fichier CSV** dans le menu, puis choisissez le fichier CSV à charger. Cliquez sur **Télécharger**
   1. Vous obtiendrez une réponse indiquant que le fichier CSV est chargé (dans Admin Console), mais il n’a pas encore été importé dans IMS
   1. Accédez au même menu « ... » et choisissez **Résultats des opérations en bloc**. Elle vous affiche une liste des tentatives de chargement en bloc et vous indique (sous **Statut**) si le chargement en bloc est en cours de traitement, a réussi ou a échoué

      * Au début, il affichera Traitement , ce qui indique qu’il n’est pas encore terminé
      * Une fois l’opération terminée, cliquez sur le lien **Ajouter des groupes d’utilisateurs** pour afficher un message de statut simple pour chaque ligne.
      * Si, au contraire, il a échoué, cliquez sur la petite icône sous **Fichier** et vous obtiendrez un peu plus d’informations sur les raisons de son échec.  Les numéros de ligne du groupe sont référencés à partir de la ligne 1.
1. Utilisez Admin Console pour vérifier vos modifications.

## Chargement et modification d’utilisateurs en bloc {#bulk-user}

Admin Console comprend deux actions distinctes pour le chargement et la modification des détails de l’utilisateur. Les instructions ci-dessous concernent l’ajout de nouveaux utilisateurs à IMS. Les instructions de modification des utilisateurs IMS existants se trouvent dans la section suivante appelée [ Modification d’utilisateurs en bloc ](#user-edit).

### Chargement utilisateur en bloc {#user-upload}

#### Cas pratique : les groupes ont été migrés vers AEM as a Cloud Service et chargés via le chargement en bloc ou une autre méthode.  Les utilisateurs peuvent ne pas être présents dans IMS/Admin Console, ils doivent donc être chargés et liés à leurs groupes dans IMS via Admin Console.

>[!NOTE]
>
>Un utilisateur apparaît dans le fichier **Chargement d’utilisateurs en bloc** s’il se trouve dans un groupe ingéré lors de la même ingestion que celle à partir de laquelle le fichier est créé. Il peut également s’afficher si l’utilisateur se trouve directement sur une liste de contrôle d’accès ou un groupe d’utilisateurs fermé du contenu migré, ou s’il est membre d’un groupe intégré ou local se trouvant sur une liste de contrôle d’accès ou un groupe d’utilisateur fermé du contenu migré. Voir [Migration de groupe](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md) pour plus d’informations sur ces cas.

Pour utiliser la fonctionnalité de téléchargement massif d’utilisateurs d’Admin Console, procédez comme suit :

1. Télécharger le fichier d’utilisateur en bloc à partir de CAM
   1. Dans CAM, accédez à **Transfert de contenu** et sélectionnez **Tâches d’ingestion**.
   1. Cliquez sur les points de suspension (...) sur la ligne de l’ingestion en question, puis choisissez **Afficher le résumé principal**.
   1. Dans la boîte de dialogue qui s’affiche, sélectionnez **Fichier utilisateur en bloc** dans la liste déroulante sous **Télécharger un fichier...** et cliquez sur le bouton **Télécharger**.
   1. Enregistrer le fichier CSV obtenu
1. Modifier le fichier d’utilisateur en bloc
   * Chaque ligne représente un utilisateur à charger, et comporte quinze champs (les noms des champs constituent la première ligne du fichier). Certains champs sont facultatifs et ne sont pas décrits ici. Pour plus d&#39;informations, consultez la section [Format CSV utilisateur en bloc](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format).  Les champs sont les suivants :

      * _Type d’identité_ - Facultatif.  Si elle n’est pas spécifiée, elle est créée en tant qu’Adobe ID
      * _Nom d’utilisateur_ - Facultatif et non utilisé pour les chargements Adobe ID
      * _Domain_ - Facultatif et non utilisé pour les chargements Adobe ID
      * _Email_ - Obligatoire.  L’adresse e-mail sera utilisée à des fins de vérification la première fois que l’utilisateur se connectera
      * _Prénom_ - Facultatif.  Doit être utilisé car il apparaît, avec le nom, à plusieurs endroits
      * _Nom_ - Facultatif.  Doit être utilisé car il apparaît à plusieurs endroits
      * _Code pays_ - Facultatif et non utilisé pour les chargements Adobe ID
      * _ID_ - Facultatif et non utilisé pour les chargements Adobe ID
      * _Configurations du produit_ - Facultatif. Ce champ sera également hérité de tous les groupes dont l’utilisateur est membre
      * _Rôles d’administration_ - Facultatif. Utilisez ce champ si l’utilisateur est administrateur. Voir [Format CSV d’utilisateur en bloc](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) pour plus d’informations
      * _Configurations de produit administrées_ - Facultatif.  Voir [Format CSV d’utilisateur en bloc](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) pour plus d’informations. Ce champ sera également hérité de tous les groupes dont l’utilisateur est membre
      * _User Groups_ - Facultatif. Liste des groupes auxquels l’utilisateur doit être affecté en tant que membre. Chaque groupe doit être un groupe IMS existant. Lorsque le fichier d’utilisateur en bloc est téléchargé à partir de CAM, ce champ est prérempli avec des noms de groupe activé pour IMS dont l’utilisateur était membre (directement ou indirectement) avant la migration
      * _Groupes d’utilisateurs administrés_ - Facultatif.  Voir [Format CSV d’utilisateur en bloc](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) pour plus d’informations. Ce champ sera également hérité de tous les groupes dont l’utilisateur est membre
      * _Produits administrés_ - facultatif.  Voir [Format CSV d’utilisateur en bloc](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) pour plus d’informations. Ce champ sera également hérité de tous les groupes dont l’utilisateur est membre
      * _Contrats administrés_ - Facultatif.  Voir [Format CSV d’utilisateur en bloc](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) pour plus d’informations
      * _Accès développeur_ - Facultatif.  Voir [Format CSV d’utilisateur en bloc](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) pour plus d’informations
      * _Produits affectés automatiquement_ - Facultatif.  Voir [Format CSV d’utilisateur en bloc](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html#csv-format) pour plus d’informations

   * Lors de la modification du fichier CSV, certaines applications peuvent ajouter des guillemets supplémentaires lors de l’enregistrement, ce qui entraîne l’échec du traitement. Il est recommandé d’inspecter le fichier CSV brut dans un simple éditeur de texte pour s’assurer que chaque champ ne comporte qu’un guillemet ouvrant et un guillemet fermant (et il ne doit pas s’agir de « guillemets intelligents »)

1. Utiliser Admin Console pour importer le fichier utilisateur en bloc

   1. Dans Admin Console, accédez à Utilisateurs .
   1. Cliquez sur le bouton **Ajouter des utilisateurs par fichier CSV**
   1. Glisser-déposer ou sélectionner un fichier CSV d’utilisateur en bloc téléchargé à partir de CAM
   1. Cliquez sur le bouton **Télécharger**
   1. Vous obtiendrez une réponse indiquant que le fichier CSV est chargé (dans Admin Console), mais il n’a pas encore été importé dans IMS.
   1. Accédez au menu « ... » à droite et choisissez **Résultats des opérations en bloc**.  Elle affiche une liste des tentatives de chargement en masse et indique (sous **Statut**) si le chargement en masse est en cours de traitement, a réussi ou a échoué.

      * Au début, il affichera Traitement , ce qui indique qu’il n’est pas encore terminé
      * Une fois l’opération terminée, cliquez sur le lien **Ajouter des utilisateurs** pour afficher un message de statut simple pour chaque ligne
      * Si au contraire il a échoué, cliquez sur la petite icône sous **Fichier** et il vous donnera un peu plus d&#39;informations sur la raison de son échec. Les numéros de ligne utilisateur sont référencés à partir de la ligne 1.

1. Utilisez Admin Console pour vérifier vos modifications.

>[!NOTE]
>
>Après une ingestion autre que l’effacement, il est possible que les utilisateurs qui ont été précédemment migrés, puis créés dans IMS, apparaissent dans le fichier de chargement d’utilisateurs en bloc. Cela pourrait être le cas pour de nombreuses raisons. Dans ce cas, le chargement de l’utilisateur échoue à nouveau. Essayez plutôt de supprimer l’utilisateur du fichier de chargement d’utilisateurs en bloc et, si l’utilisateur doit être ajouté à différents groupes, utilisez le fichier de modification d’utilisateurs en bloc comme indiqué ci-dessous.

### Modification d’utilisateurs en bloc {#user-edit}

#### Cas d’utilisation : les groupes et les utilisateurs ont été migrés vers AEM as a Cloud Service et téléchargés par le biais du téléchargement en bloc ou d’une autre méthode. Désormais, certaines modifications doivent être apportées à plusieurs utilisateurs à la fois, par exemple en les ajoutant à un groupe IMS existant.

Pour utiliser la fonctionnalité de modification d’utilisateurs en bloc d’Admin Console, procédez comme suit :

1. Télécharger le fichier d’utilisateur en bloc à partir d’Admin Console

   1. Dans Admin Console, accédez à Utilisateurs .
   1. Sur le côté droit, cliquez sur le bouton « ... ».  Choisissez **Modifier les détails de l’utilisateur par CSV** dans le menu
   1. Cliquez sur **Télécharger le modèle CSV** et choisissez **Utilisateurs actuels**.  Un fichier CSV doit apparaître dans votre dossier Téléchargements local.

1. Modifier le fichier d’utilisateur en bloc

   1. Dans Admin Console, accédez à Utilisateurs .
   1. Modifiez le fichier CSV à l’aide d’un éditeur de texte (recommandé) ou d’une application de feuille de calcul telle qu’Excel. L’utilisation d’une application peut apporter des modifications imprévisibles aux données. Il est donc recommandé, une fois toutes les modifications effectuées, d’utiliser un éditeur de texte pour vérifier la mise en forme du fichier
   1. Les descriptions des champs de ce fichier sont les mêmes que ci-dessus, sous Chargement utilisateur en bloc
   1. Supprimer tous les utilisateurs qui ne sont pas en cours de modification
   1. Si vous modifiez le champ Groupes d’utilisateurs , laissez les groupes actuels et ajoutez-en de nouveaux selon les besoins. Si vous supprimez un groupe existant, l’utilisateur sera retiré de ce groupe dans IMS
   1. Lors de la modification du fichier CSV, certaines applications peuvent ajouter des guillemets supplémentaires lors de l’enregistrement, ce qui entraîne l’échec du traitement. Il est recommandé d’inspecter le fichier CSV brut dans un simple éditeur de texte pour s’assurer que chaque champ ne comporte qu’un guillemet ouvrant et un guillemet fermant (et il ne doit pas s’agir de « guillemets intelligents »)

1. Chargez le fichier d’utilisateur en bloc dans Admin Console

   1. Dans Admin Console, accédez à Utilisateurs .
   1. Sur le côté droit, cliquez sur le bouton « ... ». Choisissez **Modifier les détails de l’utilisateur par CSV** dans le menu
   1. Effectuez un glisser-déposer ou sélectionnez le fichier CSV d’utilisateur en bloc modifié
   1. Cliquez sur le bouton Charger .
   1. Vous obtiendrez une réponse indiquant que le fichier CSV est chargé (dans Admin Console), mais il n’a pas encore été importé dans IMS
   1. Accédez au menu « ... » à droite et choisissez **Résultats des opérations en bloc**. Elle vous montre une liste de tentatives de chargement en masse et vous indique (sous Statut) si le chargement en masse est en cours de traitement, réussi ou a échoué.

      * Au début, il affichera Traitement , ce qui indique qu’il n’est pas encore terminé
      * Une fois l’opération terminée, cliquez sur le lien **Modifier les détails de l’utilisateur** pour afficher un message de statut simple pour chaque ligne
      * Si au contraire il a échoué, cliquez sur la petite icône sous **Fichier** et il affichera un peu plus d&#39;informations sur la raison de son échec. Les numéros de ligne utilisateur sont référencés à partir de la ligne 1.

1. Utilisez Admin Console pour vérifier vos modifications.
