---
title: Notes de mise à jour de la version  [!DNL Workfront for Experience Manager enhanced connector]
description: Notes de mise à jour de la version  [!DNL Workfront for Experience Manager enhanced connector]
exl-id: 12de589d-fe5d-4bd6-b96b-48ec8f1ebcb6
source-git-commit: 081f7ed8c39382408285887928163e2569c5cbfe
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 4%

---

# Notes de mise à jour de la version [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

La section suivante présente les notes générales de mise à jour pour [!DNL Workfront for Experience Manager enhanced connector].

## Date de publication {#release-date}

Date de publication de la dernière version 1.9.0 de [!DNL Workfront for Experience Manager enhanced connector] est le 16 juin 2022.

## Faits saillants des versions {#release-highlights}

La dernière version de la variable [!DNL Workfront for Experience Manager enhanced connector] inclut le correctif de bogue suivant :

* Lorsque vous effectuez un téléchargement via un dossier lié ou que vous utilisez l’événement `Send To` action disponible dans Workfront pour charger des ressources vers Experience Manager as a Cloud Service, les ressources sont corrompues et ne peuvent pas être ouvertes dans Adobe Photoshop.

>[!IMPORTANT]
>
>Adobe vous recommande de [mise à niveau vers la dernière version 1.9.0](../assets/update-workfront-enhanced-connector.md) de [!DNL Workfront for Experience Manager enhanced connector].

## Problèmes connus {#known-issues}

* Lors de la configuration de dossiers liés à un projet avec AEM 6.4, Experience Manager n’enregistre pas les valeurs de pour **[!UICONTROL sous-dossiers]** et **[!UICONTROL Création d’un dossier lié dans des projets avec portfolio]** champs. La valeur de la variable **[!UICONTROL sous-dossiers]** mises à jour des champs **[!UICONTROL undefined]** et la valeur de la variable **[!UICONTROL Création d’un dossier lié dans des projets avec portfolio]** mises à jour des champs **[!UICONTROL Portfolio par défaut]** automatiquement après l’enregistrement de la configuration.

* Lorsque vous utilisez l’expérience Workfront classique, la variable **[!UICONTROL Envoyer à]** , disponible dans la variable **[!UICONTROL Plus]** la liste déroulante ne vous permet pas de sélectionner la destination cible dans Experience Manager. Le **[!UICONTROL Envoyer à]** fonctionne correctement avec l’option **[!UICONTROL Actions de document]** liste déroulante Le **[!UICONTROL Envoyer à]** fonctionne correctement pour **[!UICONTROL Plus]** liste déroulante et **[!UICONTROL Actions de document]** liste déroulante disponible dans la nouvelle expérience Workfront.

## Versions précédentes {#previous-releases}

### Version de mars 2022 {#march-2022-release}

[!DNL Workfront for Experience Manager enhanced connector] comprend désormais les mises à jour suivantes :

* Vous pouvez désormais créer des dossiers liés entre Adobe Workfront et AEM Assets as a Cloud Service même s’il existe plusieurs configurations de dossiers liés à un projet.

* Ajout de la prise en charge de la pagination des abonnements aux événements.

* Ajout de la prise en charge d’AEM 6.4.x.

* Ajout de la prise en charge des environnements proxy.

* Plusieurs correctifs de bogues basés sur les commentaires des partenaires et des clients.

>[!MORELIKETHIS]
>
>* [Intégrer [!DNL Workfront for Experience Manager enhanced connector] avec Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=en)
>* [Intégrer [!DNL Workfront for Experience Manager enhanced connector] avec Experience Manager 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-integrations.html?lang=en)

