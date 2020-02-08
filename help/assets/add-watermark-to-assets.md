---
title: Ajout d’un filigrane à vos ressources numériques
description: Découvrez comment utiliser la fonctionnalité d’application d’un filigrane pour ajouter un filigrane numérique aux ressources.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Application d’un filigrane {#watermarking}

La fonction Filigrane des ressources d’Adobe Experience Manager (AEM) vous permet d’ajouter un filigrane numérique aux ressources, ce qui permet aux utilisateurs de vérifier l’authenticité et la propriété des ressources par copyright. AEM Assets prend en charge le texte à utiliser comme un filigrane sur les fichiers PNG et JPEG.

Pour pouvoir appliquer un filigrane aux fichiers, ajoutez l’étape Filigrane dans le flux de travaux de mise à jour des actifs de gestion des actifs numériques.

1. Appuyez/cliquez sur le logo AEM et accédez à **[!UICONTROL Outils]** > **[!UICONTROL Processus]** > **[!UICONTROL Modèles]**.
1. From the Workflow Models page, select the **[!UICONTROL DAM Update Asset]** workflow and click **[!UICONTROL Edit]**.

1. From the Side Panel, drag the **[!UICONTROL Add Watermark]** step to the DAM Update Asset workflow.

<!--  ![Darg add watermark step in the DAM update asset workflow](assets/add_watermark_step_aem_assets.png) -->

>[!NOTE]
>
>Placez l’étape Ajouter un filigrane n’importe où avant l’étape Miniature de processus.

1. Ouvrez l’étape **[!UICONTROL Ajouter un filigrane]** pour afficher ses propriétés.
1. Sous l’onglet **[!UICONTROL Arguments]**, spécifiez des valeurs valides dans les différents champs, notamment le texte, le type de police, la taille, la couleur, l’emplacement, l’orientation, etc. Pour confirmer les modifications, appuyez/cliquez sur l’icône Terminé.

<!--   ![Provide the arguments in the add watermark step in Assets](assets/arguments_add_watermark_aem_assets.png) -->

1. Save the **[!UICONTROL DAM Update Asset]** workflow with the Watermark step.
1. Dans l’interface utilisateur Ressources, téléchargez un exemple de fichier. Le filigrane apparaît avec la taille de police, la couleur, etc., à l’emplacement configuré aux étapes ci-dessus.
