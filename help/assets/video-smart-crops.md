---
title: Application de recadrages intelligents vidéo aux vidéos approuvées
description: Dynamic Media avec les fonctionnalités OpenAPI permet de générer automatiquement des sorties vidéo recadrées intelligentes pour les ressources vidéo approuvées dans Adobe Experience Manager (AEM).
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
exl-id: video-smartcrop-dmwoapi
source-git-commit: 8ddd2ade491069e4592becf3b77c04e6bbb2c06a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 4%

---


# Application de recadrages intelligents vidéo aux vidéos approuvées {#apply-video-smart-crops-dmwoapi}

[!DNL Dynamic Media with OpenAPI capabilities] vous permet de générer automatiquement des sorties vidéo recadrées intelligemment pour les ressources vidéo dans [!DNL Adobe Experience Manager (AEM)]. Les recadrages intelligents vidéo analysent le contenu vidéo et ajustent dynamiquement le cadrage afin de garder le sujet clé en évidence sur différents proportions et appareils.

Les recadrages intelligents vidéo sont générés automatiquement lorsque la fonction est activée et que la ressource vidéo est approuvée

## Avant de commencer {#prerequisites-for-video-smart-crops}

Vérifiez que vous disposez des éléments suivants :

* Accès à [!DNL AEM Assets as a Cloud Service].
* Autorisation de modifier les schémas de métadonnées.
* Dynamic Media avec les fonctionnalités OpenAPI activées pour votre environnement.
* Ressources vidéo pouvant être marquées comme **[!UICONTROL approuvées]**.

## Activation du recadrage intelligent de vidéo pour les vidéos {#enable-video-smart-crops}

Pour activer le recadrage intelligent de vidéo, configurez le schéma de métadonnées utilisé pour les ressources vidéo :

1. Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Schémas de métadonnées]**.
2. Ouvrez le schéma de métadonnées applicable (par exemple, **par défaut**).
3. Sélectionnez le formulaire **Vidéo** et cliquez sur **[!UICONTROL Modifier]**.
4. Ajoutez un nouveau **[!UICONTROL champ déroulant]** et configurez les éléments suivants :

   * **Libellé Du Champ** : Créer Des Smartcrops Vidéo
   * **Associer à la propriété** : `./jcr:content/dam:applyVideoSmartCrop`

5. Ajoutez manuellement les valeurs suivantes :

   * Oui → vrai
   * Aucun → faux

6. Enregistrez le schéma.

L’option **Créer des recadrages intelligents de vidéo** est désormais disponible dans le formulaire de métadonnées de ressource vidéo.

![Créer un champ de recadrage intelligent de vidéo](/help/assets/assets/video-smartcrop-metadata-field.png)

## Application de recadrages intelligents vidéo aux vidéos approuvées {#apply-video-smart-crops}

Vous pouvez appliquer des recadrages intelligents de vidéo aux ressources vidéo en activant le champ de métadonnées et en approuvant la ressource.

Procédez comme suit :

1. Dans [!DNL Assets View], sélectionnez **[!UICONTROL Assets]** et accédez à votre dossier.
2. Sélectionnez la ressource vidéo.
3. Cliquez sur **[!UICONTROL Détails]**.
4. Dans le panneau des métadonnées, recherchez **[!UICONTROL Créer un recadrage intelligent de vidéo]**.
5. Définissez la valeur sur **Oui**, puis cliquez sur **[!UICONTROL Enregistrer]**.
6. Définissez le statut de la ressource sur **[!UICONTROL Approuvé]**.

Une fois la ressource approuvée, les sorties recadrées intelligentes de la vidéo sont générées automatiquement.

## Affichage des sorties vidéo recadrées intelligemment {#view-video-smart-crops}

Une fois les recadrages intelligents vidéo générés :

* Les sorties sont disponibles pendant la lecture vidéo.
* La visionneuse Dynamic Media sélectionne automatiquement le recadrage le plus approprié en fonction de l’appareil et des proportions.
* La lecture vidéo s’ajuste dynamiquement pour garder le sujet principal actif.

## Utilisation de vidéos avec recadrage intelligent {#use-video-smart-crops}

Vous pouvez utiliser des sorties recadrées intelligentes vidéo où la ressource vidéo est diffusée, par exemple :

* Pages web
* Applications
* Lecteurs vidéo intégrés

La visionneuse applique automatiquement le recadrage intelligent approprié pendant la lecture.

>[!NOTE]
>
>* Les recadrages intelligents vidéo sont générés uniquement pour les ressources vidéo **approuvées**.
>* Assurez-vous que le champ **Créer un recadrage intelligent de vidéo** est défini sur **Oui** avant d’approuver la ressource.
>* Le recadrage intelligent de vidéo ne modifie pas la ressource d’origine. Le recadrage est appliqué dynamiquement pendant la lecture.