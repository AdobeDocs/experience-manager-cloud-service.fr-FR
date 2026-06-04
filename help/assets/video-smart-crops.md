---
title: Application de recadrages intelligents vidéo aux vidéos approuvées
description: Dynamic Media avec des fonctionnalités OpenAPI permet de générer des sorties vidéo recadrées intelligemment pour des ressources vidéo dans Adobe Experience Manager (AEM).
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="Application pour AEM Assets."
source-git-commit: 200d311ff279b6db8826a8c0cecd5b60d62f0585
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 5%

---


Appliquez des recadrages intelligents vidéo aux vidéos approuvées {#apply-video-smart-crops-dmwoapi}
================================================

[!DNL Dynamic Media with OpenAPI capabilities] vous permet de générer des sorties vidéo recadrées intelligemment pour les ressources vidéo dans [!DNL Adobe Experience Manager (AEM)].

Les recadrages intelligents vidéo analysent le contenu vidéo et ajustent dynamiquement le cadrage afin de garder le sujet clé en évidence sur différents proportions et appareils.

Pour utiliser cette fonctionnalité, configurez le schéma de métadonnées des ressources vidéo. Une fois activé, les utilisateurs peuvent appliquer des recadrages intelligents de vidéo en mettant à jour les métadonnées de la ressource et en approuvant la ressource.

Avant de commencer {#prerequisites-for-video-smart-crops}
--------------------------------------------------------

Vérifiez que vous disposez des éléments suivants :

* Accès à [!DNL AEM Assets as a Cloud Service].
* Autorisation de modifier les schémas de métadonnées.
* Dynamic Media avec les fonctionnalités OpenAPI activées pour votre environnement.
* Ressources vidéo disponibles dans AEM Assets.

Activer le recadrage intelligent de vidéo pour les vidéos (administration) {#enable-video-smart-crops}
------------------------------------------------------------------------

Pour activer le recadrage intelligent de vidéo, configurez le schéma de métadonnées utilisé pour les ressources vidéo.

Procédez comme suit :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.

2. Ouvrez le schéma de métadonnées appliqué à vos ressources vidéo, puis cliquez sur **[!UICONTROL Modifier]**.

3. Dans l’éditeur de schéma de métadonnées, sélectionnez l’onglet **[!UICONTROL Vidéo]**.

4. Dans la section **[!UICONTROL Créer un formulaire]**, faites glisser le composant **[!UICONTROL Liste déroulante]** vers le formulaire.

   ![Créer un champ de recadrage intelligent de vidéo ajouté au schéma de métadonnées](/help/assets/assets/metadata-schema-form.png)

5. Sélectionnez le champ nouvellement ajouté et configurez les éléments suivants dans le panneau **[!UICONTROL Paramètres]** :

   * **Libellé du champ** : indiquez un libellé de champ de votre choix.
   * **Associer à la propriété** : `./jcr:content/dam:applyVideoSmartCrop`

6. Dans la section **[!UICONTROL Choix]**, ajoutez les valeurs suivantes :

   * Oui → vrai
   * Aucun → faux

   ![Configurer le champ Créer un recadrage intelligent de vidéo](/help/assets/assets/edit-setting1.png)

7. Cliquez sur **[!UICONTROL Enregistrer]**.

> **REMARQUE :** si le schéma de métadonnées `dm_video` est utilisé dans votre environnement, assurez-vous que la même configuration est également appliquée au schéma de `dm_video`. Cela garantit un comportement cohérent des recadrages intelligents vidéo pour tous les types de schéma vidéo.

Appliquez des recadrages intelligents vidéo aux vidéos approuvées {#apply-video-smart-crops}
----------------------------------------------------------------------

Vous pouvez appliquer des recadrages intelligents de vidéo aux ressources vidéo en activant le champ de métadonnées et en approuvant la ressource.

Procédez comme suit :

1. Dans [!DNL Assets View], sélectionnez **[!UICONTROL Assets]** et accédez à votre dossier.

2. Sélectionnez la ressource vidéo.

3. Cliquez sur **[!UICONTROL Propriétés]**.

4. Dans le panneau des métadonnées, définissez **[!UICONTROL Créer un recadrage intelligent de vidéo]** sur **Oui**, mettez à jour le statut de la ressource sur **[!UICONTROL Approuvé]**, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![Ressource vidéo approuvée avec recadrage intelligent de vidéo activé](/help/assets/assets/assets-create-video-smartcrops1.png)

Un message de confirmation s’affiche une fois les propriétés mises à jour.

Affichez les sorties vidéo recadrées intelligemment {#view-video-smart-crops}
----------------------------------------------------------

Une fois que les recadrages intelligents de vidéo sont générés, incluez le paramètre `mode=smartcrop` dans la requête de diffusion vidéo du point d’entrée `/play` pour en effectuer le rendu.

* Les recadrages intelligents de vidéo sont appliqués dynamiquement lors de la lecture lorsque le paramètre `mode=smartcrop` est utilisé.
* La visionneuse Dynamic Media sélectionne automatiquement le recadrage le plus approprié en fonction de l’appareil et des proportions.
* La lecture vidéo s’ajuste dynamiquement pour garder le sujet principal au centre de l’attention.