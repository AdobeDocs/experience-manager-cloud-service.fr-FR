---
title: Prise en charge des miniatures pour les vidéos dans Screens as a Cloud Service
description: Cette page décrit comment ajouter la prise en charge des miniatures pour les vidéos dans Screens as a Cloud Service.
index: true
exl-id: 7b15d7cc-f089-4008-9039-5f48343a0f20
source-git-commit: f5af37bf39ecd5a964a8c94a731111c561c2934e
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 30%

---

# Prise en charge des miniatures pour les vidéos {#thumbnail-support-videos}

## Présentation {#introduction}

Un auteur de contenu peut définir une miniature pour les vidéos afin que l’image soit utilisée comme espace réservé et tester correctement la lecture et le ciblage du contenu, pendant que la vidéo réelle est en cours de finalisation par l’équipe appropriée. L’image peut également être utilisée au cas où la lecture de la vidéo échouerait.

L’ajout de la prise en charge d’une miniature sur le composant vidéo permet au client d’ajouter correctement un composant valide dans le canal, avec du contenu réel, et d’effectuer toutes les configurations de ciblage avant la diffusion de la vidéo.

>[!NOTE]
>L’image miniature, si elle est définie sur le composant vidéo, est lue en cas d’échec de la lecture vidéo sur le lecteur. Ce workflow vous permet de diffuser le message souhaité à l’audience (en lisant le contenu) au lieu de l’ignorer complètement.

La prise en charge des miniatures vous permet d’effectuer les opérations suivantes :

* Préparer une expérience sur un canal lorsque les vidéos ne sont pas encore prêtes ou lorsque vous ne souhaitez pas nécessairement tester un téléchargement de ressource volumineux sur les lecteurs.

* Définir un mécanisme de secours en cas de problèmes de lecture sur l’appareil.

## Utilisation de miniatures dans les vidéos {#using-thumbnails}

>[!IMPORTANT]
>**Conditions préalables**
>Avant d’apprendre à utiliser des miniatures pour les vidéos, veillez à apprendre à créer des rendus vidéo pour les canaux dans un projet Screens as a Cloud Service. Voir [Création de rendus vidéo dans Screens as a Cloud Service](/help/screens-cloud/configuring/creating-screens-video-renditions-cloud-service.md).

Suivez les étapes ci-dessous pour utiliser des miniatures dans les vidéos :

1. Accédez à un canal Screens existant ou créez-en un.

   >[!NOTE]
   >Pour savoir comment créer un canal et ajouter du contenu à un canal, consultez [Création et gestion d’un canal dans Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html?lang=en).

1. Sélectionnez le canal. Dans la barre d’actions, cliquez sur **Modifier** pour ouvrir l’éditeur.


   ![Bouton Modifier de la barre d’actions.](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png)

1. Ajoutez ou modifiez un composant vidéo existant, comme illustré dans le schéma ci-dessous.

   ![Image mise en surbrillance d’une ressource vidéo.](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png)

1. Ajoutez ou modifiez un composant vidéo existant, comme illustré dans le schéma ci-dessous.

1. Sélectionnez la vidéo et cliquez sur Configurer (*clé à molette*) pour ouvrir les propriétés de la vidéo.

   ![Image de ressource vidéo sélectionnée avec une flèche pointant vers l’icône Configurer, représentée sous la forme d’une clé à molette. dans la barre d’outils.](/help/screens-cloud/using-core-product-features/assets/thumbnail-3.png)

1. Le **Vidéo** la boîte de dialogue s’ouvre, dans laquelle vous pouvez afficher les **Miniature** zone de dépôt.

   ![Boîte de dialogue Vidéo présentant l’image de la ressource vidéo et la zone de dépôt Miniature.](/help/screens-cloud/using-core-product-features/assets/thumbnail-4.png)

1. Faites glisser et déposez une image du sélecteur de ressources vers le **Miniature** zone de dépôt et cliquez sur **Terminé**.

   ![Sélecteur d’image de ressource affiché derrière la boîte de dialogue Vidéo avec la ressource d’image affichée dans la zone de dépôt Miniature.](/help/screens-cloud/using-core-product-features/assets/thumbnail-5.png)

1. Cliquez sur **Aperçu**. 

1. Si une vidéo est définie sur le composant, elle est lue. Si ce n’est pas le cas, et que la miniature est définie, la miniature est lue. Dans le cas contraire, le composant est considéré comme non configuré et est ignoré.

## Cas d’utilisation pris en charge lors de l’utilisation de miniatures dans des vidéos {#understand-use-case}

La miniature dans les vidéos prend en charge les cas d’utilisation suivants :

* Un composant vidéo sans configuration est ignoré.

* Un composant vidéo avec uniquement la miniature lit la miniature.

* Un composant vidéo avec la vidéo (si la vidéo présente un rendu correct) et la visionneuse de miniatures lit la vidéo.

* Un composant vidéo avec la visionneuse de vidéos lit la miniature, en cas d’erreur de lecture, ou passe à l’élément suivant si la miniature n’est pas configurée.
