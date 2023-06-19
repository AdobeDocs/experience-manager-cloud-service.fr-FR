---
title: Notes de mise à jour de [!DNL Workfront for Experience Manager enhanced connector]
description: Notes de mise à jour de [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: 0cc57a144b69799cfabc8baae2051e9ac8701d49
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 92%

---

# Notes de mise à jour de [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

La section suivante présente les notes de mise à jour générales de [!DNL Workfront for Experience Manager enhanced connector].

## Date de publication {#release-date}

Date de publication de la dernière version 1.9.11 de [!DNL Workfront for Experience Manager enhanced connector] est le 19 juin 2023.

## Principaux éléments de la mise à jour {#release-highlights}

La dernière version de [!DNL Workfront for Experience Manager enhanced connector] inclut les mises à jour suivantes :

* Lorsque vous avez configuré la mise en réseau avancée, des problèmes se produisent lors de l’envoi de contenu d’Adobe Workfront vers AEM as a Cloud Service.

>[!NOTE]
>
>AEM version 6.4 a atteint la fin de la prise en charge étendue. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=en).


>[!IMPORTANT]
>
>Adobe vous recommande d’effectuer une [mise à niveau vers la dernière version soit la version 1.9.11](../assets/update-workfront-enhanced-connector.md) de [!DNL Workfront for Experience Manager enhanced connector].

## Problèmes connus {#known-issues}

* Lors de la configuration de dossiers liés à un projet avec AEM 6.4, Experience Manager n’enregistre pas les valeurs pour les champs **[!UICONTROL Sous-dossiers]** et **[!UICONTROL Création d’un dossier lié dans des projets avec portfolio]**. La valeur du champ de **[!UICONTROL sous-dossiers]** est remplacé par **[!UICONTROL indéfini]** et la valeur du champ **[!UICONTROL Création d’un dossier lié dans des projets avec portfolio]** est remplacé par **[!UICONTROL Portfolio par défaut]** automatiquement après l’enregistrement de la configuration.

* Lorsque vous utilisez l’expérience Workfront classique, l’option **[!UICONTROL Envoyer à]** disponible dans la liste déroulante **[!UICONTROL Plus]** ne vous permet pas de sélectionner la destination cible dans Experience Manager. L’option **[!UICONTROL Envoyer à]** fonctionne correctement avec la liste déroulante **[!UICONTROL Actions de document]**. L’option **[!UICONTROL Envoyer à]** fonctionne correctement pour la liste déroulante **[!UICONTROL Plus]** et la liste déroulante **[!UICONTROL Actions de document]** est disponible dans la nouvelle expérience Workfront.

## Versions précédentes {#previous-releases}

### Version de mai 2023 {#may-2023-release}

* Workfront renvoie une réponse HTTP 409 pour les abonnements d’événements en double basée sur un appel REST de Experience Manager vers Workfront, ce qui entraîne une exception de pointeur nulle.

### Version d’avril 2023 {#april-2023-release}

[!DNL Workfront for Experience Manager enhanced connector] La version 1.9.9, publiée le 10 avril 2023, comprend les mises à jour suivantes :

* Experience Manager affiche une exception `DateTimeParseException` lorsqu’il reçoit la date de dernière modification de Workfront lors de la création du dossier lié.

* Problèmes lors de la création de plusieurs dossiers de projet liés dans un court laps de temps.

* Impossible de configurer une limite de seuil pour le nombre de nouveaux dossiers liés au projet.

### Version de mars 2023 {#march-2023-release}

La version 1.9.8 de [!DNL Workfront for Experience Manager enhanced connector], publiée le 03 mars 2023, comprend les mises à jour suivantes :

* Amélioration des performances dans Experience Manager lors de la création de dossiers liés à un projet dans Workfront.

* Les suppressions de commentaires dans Workfront sont désormais répercutées dans Experience Manager.

* Possibilité de gérer le blocage des nouveaux clients et des nouvelles clientes sur Experience Manager as a Cloud Service à partir de la configuration du connecteur.


### Version de janvier 2023 {#january-2022-release}

La version 1.9.7 de [!DNL Workfront for Experience Manager enhanced connector] publiée le 02 février 2023 comprend les mises à jour suivantes :

* L’éditeur de métadonnées ne répertorie pas les propriétés de formulaires personnalisés Workfront après l’installation de la version 1.9.6.

* La console de développement affiche le message d’erreur `/content/dam/jcr:content/metadata/wfProjectURL not found` après l’installation du connecteur amélioré Workfront et l’ouverture de la page d’accueil d’Assets.

### Version de décembre 2022 {#december-2022-release}

La version 1.9.6 de [!DNL Workfront for Experience Manager enhanced connector] publiée le 09 décembre comprend les mises à jour suivantes :

**Amélioration**

<!--

* Workfront enhanced connector now allows you to use new search parameters to be more specific while defining folder names on large repositories.

-->

* Le connecteur amélioré de Workfront permet désormais d’effectuer une recherche de texte intégral sur les ressources et les dossiers.

**Correctifs**

* Les métadonnées de version de document ne se synchronisent pas correctement entre Workfront et Experience Manager.
* Problèmes lors de la création d’un dossier lié à Experience Manager dans Workfront lorsque le dossier utilise un schéma dont la définition est manquante dans la configuration globale.
* Le formulaire de l’éditeur de schéma de métadonnées ne répond plus lorsque vous cliquez sur n’importe quel champ en raison d’un temps de chargement plus long que prévu. Ajout d’une configuration OSGi spécifique pour que les formulaires personnalisés résolvent le problème. Les noms des formulaires personnalisés que vous ajoutez à l’éditeur de schéma de métadonnées sont disponibles dans les journaux.

### Version de novembre 2022 {#november-2022-release}

La version 1.9.5 de [!DNL Workfront for Experience Manager enhanced connector] publiée le 11 novembre comprend les mises à jour suivantes :

* Lorsque vous définissez une seule valeur pour un champ à plusieurs valeurs dans Workfront, la valeur du champ n’est pas mappée correctement à Experience Manager.

* Experience Manager affiche `SERVER_ERROR` sur l’écran **[!UICONTROL Lier des fichiers et des dossiers externes]** lors de l’accès aux dossiers de ressources en raison d’autorisations non valides sur `/content/dam/collections`.

* L’activation de l’option **[!UICONTROL Publier des ressources dans Brand Portal]** sur la page de configuration du connecteur amélioré de Workfront crée un événement incorrect. L’événement n’est pas supprimé, même une fois l’option désactivée.

  Pour résoudre le problème :

   1. Effectuez la mise à niveau vers la version 1.9.5 du connecteur amélioré.

   1. Désactivez l’option **[!UICONTROL Publier des ressources dans Brand Portal]** sous les paramètres avancés.

   1. Activez l’option **[!UICONTROL Publier des ressources dans Brand Portal]**.

   1. Supprimez les abonnements aux événements incorrects.

      1. Effectuez des appels GET vers `/attask/eventsubscription/api/v1/subscriptions?page=<page-number>`.

         Exécutez un appel API pour chaque numéro de page.

      1. Recherchez le texte suivant pour trouver les abonnements aux événements qui correspondent à l’URL suivante et ne comportent pas de `objId` :

         ```
              "objId": "",
             "url": "<your-aem-domain>/bin/workfront-tools/events/linkedfolderprojectupdate<your-aem-domain>/
         ```

         Assurez-vous que le contenu entre `"objId": "",` et `"url"` correspond à la réponse JSON. Pour ce faire, il est recommandé d’effectuer une copie depuis n’importe quel abonnement à un événement comportant un `objId` puis de supprimer le nombre.

      1. Notez l’ID d’abonnement à l’événement.

      1. Supprimez l’abonnement à un événement incorrect. Effectuez un appel API de suppression à `<your-aem-domain>/attask/eventsubscription/api/v1/subscriptions/<event-subscription-ID-from-previous-step>`.

         Le code de réponse `200` indique la suppression réussie des abonnements à des événements incorrects.
  >[!NOTE]
  >
  >Si vous avez déjà supprimé les abonnements aux événements incorrects avant d’exécuter les étapes mentionnées dans cette procédure, vous pouvez ignorer la dernière étape.

### Version d’octobre 2022 {#october-2022-release}

La version 1.9.4 de [!DNL Workfront for Experience Manager enhanced connector], publiée le 7 octobre, comprend les mises à jour suivantes :

* Impossible d’afficher l’onglet Abonnements aux événements sur la page de configuration du connecteur améliorée en raison d’un grand nombre d’événements.

* Workfront ne parvient pas à récupérer la liste des dossiers existants dans un projet, ce qui entraîne la création de dossiers en double.

### Version de septembre 2022 {#september-2022-release}

La version 1.9.3 de [!DNL Workfront for Experience Manager enhanced connector], publiée le 16 septembre, comprend les mises à jour suivantes :

* Impossible de charger un fichier de plus de 8 Go.
* Problèmes lors de la publication automatique de ressources envoyées depuis Workfront vers AEM.
* Le champ Chemin d’accès racine n’est pas disponible pour le champ Balises lors de la modification d’un formulaire de schéma de métadonnées par défaut.
* Problèmes lors de l’ajout de nouvelles versions dans Workfront à l’aide de workflows AEM.
* Lorsque vous exécutez une recherche AEM de ressources disponibles dans Workfront, AEM affiche un message d’erreur.
* Lorsque vous créez un workflow AEM pour la création d’une tâche à partir d’une ressource et que vous ne définissez pas de nom de tâche parent, la tâche n’est pas créée dans Workfront.

### Version d’août 2022 {#august-2022-release}

La version 1.9.2 de [!DNL Workfront for Experience Manager enhanced connector], publiée le 3 août, comprend les mises à jour suivantes :

* L’étape de workflow **[!UICONTROL Charger le document]** ne parvient pas à joindre un document à Workfront.

* L’étape de workflow **[!UICONTROL Charger le document]** ne parvient pas à joindre un document aux tâches et problèmes dans Workfront. L’étape de workflow joint correctement un document aux projets.

### Version de juillet 2022 {#july-2022-release}

La version 1.9.1 de [!DNL Workfront for Experience Manager enhanced connector] comprend les mises à jour suivantes :

* Un ajout de la prise en charge de l’authentification entre les applications Experience Manager et Workfront à l’aide de la clé API Workfront pour les instances migrées vers Adobe IMS.

* Lorsque vous liez des fichiers ou des dossiers externes, l’application Workfront affiche le message d’erreur `SERVER_ERROR`. Le message d’erreur fait référence à une exception non autorisée en raison d’une incohérence des clés API.

* Lorsque vous exécutez un workflow Créer une tâche pour une ressource, l’exception de pointeur Null s’affiche dans les messages du journal.

* Lorsque vous activez l’option de configuration `Replace Spaces with DASH` sous Paramètres avancés dans Experience Manager, cela entraîne la création de dossiers en double dans Workfront.

### Version de juin 2022 {#june-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] comprend désormais les mises à jour suivantes :

* Lorsque vous effectuez un chargement via un dossier lié ou que vous utilisez l’action `Send To` disponible dans Workfront pour charger des ressources vers Experience Manager as a Cloud Service, la ou les ressources sont endommagées et ne peuvent pas être ouvertes dans Adobe Photoshop.

### Version de mars 2022 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] comprend désormais les mises à jour suivantes :

* Vous pouvez désormais créer des dossiers liés entre Adobe Workfront et AEM Assets as a Cloud Service même s’il existe plusieurs configurations de dossiers liés à un projet.

* Ajout de la prise en charge de la pagination des abonnements aux événements.

* Ajout de la prise en charge d’AEM 6.4.x.

* Ajout de la prise en charge des environnements proxy.

* Plusieurs correctifs de bogues basés sur les commentaires des partenaires et des clients.

>[!MORELIKETHIS]
>
>* [Intégrer  [!DNL Workfront for Experience Manager enhanced connector]  avec Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=fr)
