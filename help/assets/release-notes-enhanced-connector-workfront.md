---
title: Notes de mise à jour de [!DNL Workfront for Experience Manager enhanced connector]
description: Notes de mise à jour de [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: f49ac67b7a90d638e266b9f7f5bf5ac9d7f78e3a
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 52%

---

# Notes de mise à jour de[!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

La section suivante présente les notes de mise à jour générales de [!DNL Workfront for Experience Manager enhanced connector].

## Date de publication {#release-date}

Date de publication de la dernière version 1.9.2 de [!DNL Workfront for Experience Manager enhanced connector] est le 3 août 2022.

## Principaux éléments de la mise à jour {#release-highlights}

La dernière version de la variable [!DNL Workfront for Experience Manager enhanced connector] comprend les améliorations et correctifs suivants :

* Le **[!UICONTROL Télécharger le document]** l’étape de workflow ne parvient pas à joindre un document à Workfront.

* Le **[!UICONTROL Télécharger le document]** l’étape de workflow ne parvient pas à joindre un document aux tâches et problèmes dans Workfront. L’étape de processus associe correctement un document aux projets.

>[!IMPORTANT]
>
>Adobe vous recommande de [mise à niveau vers la dernière version 1.9.2](../assets/update-workfront-enhanced-connector.md) de [!DNL Workfront for Experience Manager enhanced connector].

## Problèmes connus {#known-issues}

* Lors de la configuration de dossiers liés à un projet avec AEM 6.4, Experience Manager n’enregistre pas les valeurs pour les champs **[!UICONTROL Sous-dossiers]** et **[!UICONTROL Création d’un dossier lié dans des projets avec portfolio]**. La valeur du champ de **[!UICONTROL sous-dossiers]** est remplacé par **[!UICONTROL indéfini]** et la valeur du champ **[!UICONTROL Création d’un dossier lié dans des projets avec portfolio]** est remplacé par **[!UICONTROL Portfolio par défaut]** automatiquement après l’enregistrement de la configuration.

* Lorsque vous utilisez l’expérience Workfront classique, l’option **[!UICONTROL Envoyer à]** disponible dans la liste déroulante **[!UICONTROL Plus]** ne vous permet pas de sélectionner la destination cible dans Experience Manager. L’option **[!UICONTROL Envoyer à]** fonctionne correctement avec la liste déroulante **[!UICONTROL Actions de document]**. L’option **[!UICONTROL Envoyer à]** fonctionne correctement pour la liste déroulante **[!UICONTROL Plus]** et la liste déroulante **[!UICONTROL Actions de document]** est disponible dans la nouvelle expérience Workfront.

## Versions précédentes {#previous-releases}

### Version de juillet 2022 {#july-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] La version 1.9.1 comprend les mises à jour suivantes :

* Ajout de la prise en charge de l’authentification entre les applications Experience Manager et Workfront à l’aide de la clé API Workfront pour les instances migrées vers Adobe IMS.

* Lorsque vous liez des fichiers ou des dossiers externes, l’application Workfront affiche la variable `SERVER_ERROR` message d’erreur. Le message d’erreur fait référence à une exception non autorisée en raison d’une incohérence des clés API.

* Lorsque vous exécutez un workflow Créer une tâche pour une ressource, l’exception Null Pointer s’affiche dans les messages du journal.

* Lorsque vous activez la variable `Replace Spaces with DASH` l’option de configuration sous Paramètres avancés dans Experience Manager entraîne la création de dossiers en double dans Workfront.

### Version de juin 2022 {#june-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] comprend désormais les mises à jour suivantes :

* Lorsque vous effectuez un téléchargement via un dossier lié ou que vous utilisez l’événement `Send To` action disponible dans Workfront pour charger des ressources vers Experience Manager as a Cloud Service, les ressources sont corrompues et ne peuvent pas être ouvertes dans Adobe Photoshop.

### Version de mars 2022 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] comprend désormais les mises à jour suivantes :

* Vous pouvez désormais créer des dossiers liés entre Adobe Workfront et AEM Assets as a Cloud Service même s’il existe plusieurs configurations de dossiers liés à un projet.

* Ajout de la prise en charge de la pagination des abonnements aux événements.

* Ajout de la prise en charge d’AEM 6.4.x.

* Ajout de la prise en charge des environnements proxy.

* Plusieurs correctifs de bogues basés sur les commentaires des partenaires et des clients.

>[!MORELIKETHIS]
>
>* [Intégrer  [!DNL Workfront for Experience Manager enhanced connector]  avec Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=fr)
>* [Intégrer  [!DNL Workfront for Experience Manager enhanced connector]  avec Experience Manager 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-integrations.html?lang=fr)

