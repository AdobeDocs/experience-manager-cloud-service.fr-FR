---
title: 'Balisage automatique des ressources avec le service dynamique [!DNL Adobe AI] '
description: Balisez les ressources à l’aide d’un service d’intelligence artificielle qui applique des balises commerciales contextuelles et descriptives.
feature: Smart Tags,Tagging
role: Admin,User
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 66%

---


# Entraînement des balises intelligentes

L’entraînement des balises intelligentes vous permet d’entraîner vos balises afin que vous puissiez spécifier les informations si les balises appropriées ne sont pas présentes. Il utilise un cadre d’intelligence artificielle de l’[IA d’Adobe](https://business.adobe.com/ai/adobe-genai.html) pour entraîner son algorithme de reconnaissance d’images par rapport à votre structure de balises et de votre taxonomie métier. Cette intelligence de contenu est ensuite utilisée pour appliquer les balises pertinentes sur un ensemble de ressources différentes. [!DNL Experience Manager Assets] applique automatiquement les balises intelligentes aux ressources chargées, par défaut.

## Détermination des exigences de l’entraînement sur les balises intelligentes {#smart-tag-training-requirement}

L’entraînement aux balises intelligentes est requis dans les scénarios suivants :

* Pour ajouter un libellé automatisé afin d’enregistrer les itérations de l’ajout de libellés chaque fois que vous chargez la même ressource.
* Améliorer la capacité des ressources à appliquer des balises pertinentes.
* Pour augmenter la précision des balises affichées pour une ressource.
* Pour ajouter des libellés indisponibles ou manquants.


>[!NOTE]
>
>L’entraînement des balises intelligentes s’applique uniquement dans un ***type image*** de ressource.

## Étapes d’entraînement des balises intelligentes

[!DNL Experience Manager] as a [!DNL Cloud Service] génère automatiquement les balises intelligentes pour les ressources textuelles et les vidéos par défaut. Pour entraîner les balises intelligentes aux images, effectuez les tâches suivantes :

* [Comprendre les directives et les modèles relatifs aux balises](#understand-tag-models-guidelines)
* [Entraînement du modèle](#train-model)
* [Balisage de vos ressources numériques](#tag-assets)
* [Gestion des balises et des recherches](#manage-smart-tags-and-searches)

## Comprendre les directives et les modèles relatifs aux balises {#understand-tag-models-guidelines}

Un modèle de balise est un groupe de balises connexes qui sont associées à divers aspects visuels des images balisées. Les balises sont liées aux différents aspects visuels des images, de sorte qu’une fois appliquées, les balises permettent de rechercher des types d’images spécifiques. Par exemple, une collection de chaussures peut avoir des balises différentes. Cependant, toutes les balises sont liées à des chaussures et peuvent appartenir au même modèle. Lorsqu’elles sont appliquées, les balises permettent de trouver différents types de chaussures, par exemple selon leur conception ou leur utilisation.

Avant de créer un modèle de balise et d’entraîner le service, identifiez un ensemble de balises uniques décrivant le mieux les objets contenus dans les images replacés dans le contexte de votre activité. Assurez-vous que les ressources figurant dans la série sélectionnée confirment [les instructions d’entraînement](#training-guidelines).

### Instructions d’entraînement {#training-guidelines}

Vérifiez que les images figurant dans la série de formation sont conformes aux instructions suivantes :

<table>
   <tr>
      <th> Mesures </th>
      <th> Description </th>
   </tr>
   <tr>
      <td> <b>Quantité et taille </b></td>
      <td> 10 images minimum et 50 images maximum par balise. </td>
   </tr>
   <tr>
      <td> <b> Cohérence </b> </td>
      <td> Assurez-vous que les images d’une balise sont visuellement similaires. Il est préférable d’ajouter les balises portant sur les mêmes aspects visuels (par exemple, un même type d’objet dans une image) dans un modèle de balise unique. Par exemple, il n’est pas recommandé de marquer toutes ces images comme <i>mon parti</i> (pour l’entraînement), car elles ne sont pas visuellement similaires. </td>
   </tr>
   <tr>
      <td colspan="2"> <img src="assets/do-not-localize/coherence.png"><br><i>Image : images illustratives de la cohérence pour illustrer les directives d’entraînement</i>
      </td>
   </tr>
   <tr>
      <td> <b>Couverture</b></td>
      <td> Les images de l’entraînement doivent être suffisamment variées. L’idée est de fournir quelques exemples raisonnablement différents pour apprendre à se concentrer sur les bons éléments. Si vous appliquez la même balise sur des images visuellement différentes, incluez au moins cinq exemples de chaque type. Par exemple, pour la balise <i>mannequin-pose-tête-baissée</i>, incluez davantage d’images d’entraînement similaires à l’image mise en évidence ci-dessous pour que le service reconnaisse les images similaires avec plus de précision lors du balisage.</td>
   </tr>
   <tr>
   <td colspan="2"> <img src="assets/do-not-localize/coverage_1.png"><br><i>Image : images illustratives de la couverture pour illustrer les directives d’entraînement</i>
   </td>
   </tr>
   <tr>
      <td><b>Distraction/obstruction</b> </td>
      <td> Le service s’entraîne mieux sur les images qui ont moins de distractions (telles que des arrière-plans importants ou des objets/personnes sans lien avec le sujet principal). Par exemple, pour la balise <i>chaussure-décontractée</i>, la seconde image n’est pas un bon candidat pour l’entraînement. </td>
   </tr>
   <tr>
      <td colspan="2"> <img src="assets/do-not-localize/distraction.png"><br><i>Image : Images illustratives de distractions/obstacles pour illustrer les directives d’entraînement</i>
      </td>
   </tr>
   <tr>
      <td> <b>Exhaustivité</b> </td>
      <td> Si une image est admissible pour plusieurs balises, ajoutez toutes les balises applicables avant d’inclure l’image à des fins d’entraînement. Par exemple, pour les balises telles que <i>raincoat</i> et <i>model-side-view</i>, ajoutez les deux balises sur la ressource éligible avant de l’inclure pour la formation. </td>
   </tr>
   <tr>
      <td colspan="2"> <img src="assets/do-not-localize/completeness.png"><br><i>Image : images illustratives de l’exhaustivité pour illustrer les instructions d’entraînement</i>
      </td>
   </tr>
   <tr>
      <td> <b> Nombre de balises </b> </td>
      <td> Adobe recommande d’entraîner un modèle à l’aide d’au moins deux balises distinctes et d’au moins dix images différentes pour chaque balise. Dans un modèle de balise unique, n’ajoutez pas plus de 50 balises. </td>
   </tr>
   <tr>
      <td> <b>Nombre d'exemples</b> </td>
      <td> Pour chaque balise, ajoutez au moins dix exemples. Cependant, Adobe recommande environ 30 exemples. Pour chaque balise, 50 exemples au maximum sont pris en charge. </td>
   </tr>
   <tr>
      <td> <b>Prévenir les faux positifs et les conflits</b> </td>
      <td> Adobe recommande de créer un modèle de balise unique pour un seul aspect visuel. Organisez les modèles de balises de manière à éviter le chevauchement des balises entre les modèles. Par exemple, n’utilisez pas de balises courantes telles que <i>baskets</i> dans deux modèles de balises différents appelés <i>chaussures</i> et <i>chaussures</i>. Le processus d’entraînement remplace un modèle de balise entraîné par l’autre en cas de mot-clé commun. </td>
   </tr>
</table>

**Exemples** : voici d’autres exemples à titre de conseil :

* Créez un modèle de balise contenant uniquement :

   * des balises relatives à des modèles de voitures ;
   * des balises relatives aux vestes pour adultes et enfants.

* Ne créez pas :

   * un modèle de balise contenant des modèles de voitures commercialisés en 2019 et 2020 ;
   * plusieurs modèles de balises contenant ces mêmes modèles de voitures en nombre limité.

>[!NOTE]
>
>Vous pouvez utiliser les mêmes images pour entraîner différents modèles de balises. Cependant, ces modèles n’associent pas une image à plus d’une balise dans un modèle donné. Il est donc possible de baliser la même image avec des balises différentes appartenant à différents modèles.
>Vous ne pouvez pas annuler l’entraînement. Les instructions ci-dessus doivent vous aider à choisir les bonnes images pour l’entraînement.

## Entraînement du modèle pour vos balises personnalisées {#train-model}

Pour créer et entraîner un modèle pour vos balises spécifiques à votre entreprise, procédez comme suit :

1. Créez les balises nécessaires et la structure de balise appropriée. Chargez les images appropriées dans le référentiel de gestion des ressources numériques (DAM).
1. Dans l’interface utilisation d’[!DNL Experience Manager Cloud Service], accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Entraînement des balises intelligentes]**.
1. Cliquez sur **[!UICONTROL Créer]**. Indiquez un **[!UICONTROL titre]** et une **[!UICONTROL description]**.
1. Cliquez sur l’icône de dossier dans le champ **[!UICONTROL Balises]**. Une fenêtre contextuelle s’ouvre.
1. Recherchez ou sélectionnez les balises appropriées parmi les balises existantes dans `cq-tags` que vous souhaitez ajouter au modèle. Cliquez sur **[!UICONTROL Suivant]**.

   >[!NOTE]
   >
   >Vous pouvez trier la structure des balises par ordre croissant ou décroissant en fonction du **[!UICONTROL Nom]** (par ordre alphabétique), de la date de **[!UICONTROL Création]** ou de la date de **[!UICONTROL Modification]**.


1. Dans la boîte de dialogue **[!UICONTROL Sélectionner les ressources]**, cliquez sur **[!UICONTROL Ajouter les ressources]** pour chaque balise. Effectuez des recherches dans le référentiel de gestion des ressources numériques (DAM) ou parcourez le référentiel pour sélectionner au moins 10, et au plus 50 images. Sélectionnez les ressources et non le dossier. Une fois les images sélectionnées, cliquez sur **[!UICONTROL Sélectionner]**.

   ![Afficher le statut de la formation](assets/smart-tags-training-status.png)

1. Pour avoir un aperçu des miniatures des images sélectionnées, cliquez sur l’accordéon situé face à une balise. Vous pouvez modifier votre sélection en cliquant sur **[!UICONTROL Ajouter les ressources]**. Une fois la sélection effectuée, cliquez sur **[!UICONTROL Envoyer]**. L’interface utilisateur affiche une notification au bas de la page indiquant que l’entraînement est lancé.
1. Vérifiez le statut de l’entraînement dans la colonne **[!UICONTROL Statut]** pour chaque modèle de balise. Les statuts possibles sont [!UICONTROL En Attente], [!UICONTROL Entraîné(s)] et [!UICONTROL Échec].

![Workflow d’entraînement du modèle de balisage pour les balises intelligentes](assets/smart-tag-model-training-flow.png)

*Figure : Étapes du workflow d’entraînement du modèle de balisage.*

### Affichage du statut et du rapport d’entraînement {#training-status}

Pour vérifier que le service de balises intelligentes est entraîné sur vos balises dans la série de ressources d’entraînement, examinez le rapport de workflow d’entraînement dans la console Rapports.

1. Dans l’interface [!DNL Experience Manager Cloud Service], accédez à **[!UICONTROL Outils]** > **[!UICONTROL Ressources]** > **[!UICONTROL Rapports]**.
1. Dans la page **[!UICONTROL Rapports de ressources]**, cliquez sur **[!UICONTROL Créer]**.
1. Sélectionnez le rapport **[!UICONTROL Entraînement des balises intelligentes]**, puis cliquez sur **[!UICONTROL Suivant]** dans la barre d’outils.
1. Indiquez un titre et une description pour le rapport. Sous **[!UICONTROL Planifier le rapport]**, laissez l’option **[!UICONTROL Maintenant]** sélectionnée. Si vous souhaitez planifier le rapport pour une date ultérieure, sélectionnez **[!UICONTROL Plus tard]** et spécifiez une date et une heure. Ensuite, cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.
1. Dans la page **[!UICONTROL Rapports de ressources]**, sélectionnez le rapport que vous avez généré. Pour afficher le rapport, cliquez sur **[!UICONTROL Afficher]** dans la barre d’outils.
1. Passez en revue les détails du rapport. Le rapport affiche le statut d’identification des balises que vous avez entraînées. La couleur verte de la colonne **[!UICONTROL Statut de l’entraînement]** indique que le service Balises intelligentes est entraîné pour la balise. La couleur jaune indique que le service n’est que partiellement entraîné pour une balise particulière. Pour entraîner complètement le service pour une balise, ajoutez d’autres images avec cette balise particulière et exécutez le workflow d’entraînement. Si vous ne voyez pas vos balises dans ce rapport, exécutez à nouveau le workflow d’entraînement pour ces balises.
1. Pour télécharger le rapport, sélectionnez-le dans la liste, puis cliquez sur **[!UICONTROL Télécharger]** dans la barre d’outils. Le rapport est téléchargé sous la forme d’une feuille de calcul.

>[!NOTE]
>
>Que se passe-t-il si je souhaite transférer l’entraînement aux balises intelligentes d’une instance à une autre via une exportation ?
>Vous n’avez pas besoin d’exporter l’entraînement aux balises intelligentes si l’environnement appartient à la même organisation IMS. Il est automatiquement partagé. Si l’environnement se trouve dans plusieurs organisations IMS, il n’est alors pas possible de partager ou d’exporter l’entraînement sur les balises intelligentes.

## Restrictions et bonnes pratiques relatives aux balises intelligentes {#limitations-smart-tags-training}

* Pour entraîner le modèle, utilisez les images les plus appropriées. L’entraînement ne peut pas être annulé ou le modèle d’entraînement ne peut pas être supprimé. La précision de votre balisage dépend de l’entraînement en cours. Il doit donc être effectué soigneusement.
* Vous ne pouvez pas entraîner le service qui applique les balises intelligentes aux vidéos en utilisant des vidéos spécifiques. Le processus fonctionne avec les paramètres [!DNL Adobe AI] par défaut.


>[!NOTE]
>
>La capacité des balises intelligentes à s’entraîner à partir de vos balises et à les appliquer à d’autres images dépend de la qualité des images que vous utilisez pour l’entraînement.
>Pour obtenir des résultats optimaux, Adobe recommande d’utiliser des images visuellement similaires afin d’entraîner le service pour chaque balise.
