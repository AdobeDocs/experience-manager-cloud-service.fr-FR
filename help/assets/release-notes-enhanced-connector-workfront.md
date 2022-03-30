---
title: Notes de mise à jour de la version  [!DNL Workfront for Experience Manager enhanced connector]
description: Notes de mise à jour de la version  [!DNL Workfront for Experience Manager enhanced connector]
source-git-commit: 02df53e47d2b8617c9a81f5c438814996af92340
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 5%

---


# Notes de mise à jour de la version [!DNL Workfront for Experience Manager enhanced connector] {#release-notes-enhanced-connector-workfront}

La section suivante présente les notes générales de mise à jour pour [!DNL Workfront for Experience Manager enhanced connector].

## Date de publication {#release-date}

Date de publication de la dernière version de [!DNL Workfront for Experience Manager enhanced connector] est le 28 mars 2022.

## Faits saillants des versions {#release-highlights}

[!DNL Workfront for Experience Manager enhanced connector] comprend désormais les mises à jour suivantes :

* Vous pouvez désormais créer des dossiers liés entre Adobe Workfront et AEM Assets as a Cloud Service même s’il existe plusieurs configurations de dossiers liés à un projet.

* Ajout de la prise en charge de la pagination des abonnements aux événements.

* Ajout de la prise en charge d’AEM 6.4.x.

* Ajout de la prise en charge des environnements proxy.

* Plusieurs correctifs de bogues basés sur les commentaires des partenaires et des clients.

## Problèmes connus {#known-issues}

* Lors de la configuration de dossiers liés à un projet avec AEM 6.4, Experience Manager n’enregistre pas les valeurs de pour **[!UICONTROL sous-dossiers]** et **[!UICONTROL Création d’un dossier lié dans des projets avec portfolio]** champs. La valeur de la variable **[!UICONTROL sous-dossiers]** mises à jour des champs **[!UICONTROL undefined]** et la valeur de la variable **[!UICONTROL Création d’un dossier lié dans des projets avec portfolio]** mises à jour des champs **[!UICONTROL Portfolio par défaut]** automatiquement après l’enregistrement de la configuration.

* Lorsque vous utilisez l’expérience Workfront classique, la variable **[!UICONTROL Envoyer à]** , disponible dans la variable **[!UICONTROL Plus]** la liste déroulante ne vous permet pas de sélectionner la destination cible dans Experience Manager. Le **[!UICONTROL Envoyer à]** fonctionne correctement avec l’option **[!UICONTROL Actions de document]** liste déroulante Le **[!UICONTROL Envoyer à]** fonctionne correctement pour **[!UICONTROL Plus]** liste déroulante et **[!UICONTROL Actions de document]** liste déroulante disponible dans la nouvelle expérience Workfront.

>[!MORELIKETHIS]
>
>* [Intégrer [!DNL Workfront for Experience Manager enhanced connector] avec Experience Manager 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html?lang=en)
>* [Intégrer [!DNL Workfront for Experience Manager enhanced connector] avec Experience Manager 6.4](https://experienceleague.adobe.com/docs/experience-manager-64/assets/integrations/workfront-integrations.html?lang=en)


