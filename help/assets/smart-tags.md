---
title: Balisez des images avec des services d’intelligence artificielle.
description: Balisez des images avec des services d’intelligence artificielle en appliquant des balises commerciales contextuelles et descriptives à l’aide des services Adobe Sensei.
contentOwner: AG
translation-type: ht
source-git-commit: cc24b16cf17f146e773e7974c649adae1bd10ddf
workflow-type: ht
source-wordcount: '2401'
ht-degree: 100%

---


# Entraînez le service de balises intelligentes et balisez vos images {#train-service-tag-assets}

Les entreprises qui traitent des ressources numériques utilisent de plus en plus le vocabulaire contrôlé par taxonomie dans les métadonnées des ressources. Il s’agit essentiellement d’une liste des mots-clés que les employés, les partenaires et les clients utilisent fréquemment pour mentionner et rechercher des ressources numériques. Le balisage des ressources avec vocabulaire contrôlé par taxonomie permet de s’assurer qu’elles peuvent être facilement identifiées et récupérées au moyen de recherches sur les balises.

Comparé aux vocabulaires des langages naturels, le balisage basé sur la taxonomie métier aide à aligner les ressources avec les activités d’une entreprise et à veiller à ce que les mieux adaptées apparaissent dans les recherches. Par exemple, un constructeur de voitures peut baliser les images de voitures avec les noms de modèles afin de n’afficher que les images appropriées lors de recherches servant à concevoir une campagne de promotion.

En arrière-plan, le service de balises intelligentes utilise le framework d’intelligence artificielle d’[Adobe Sensei](https://www.adobe.com/fr/sensei/experience-cloud-artificial-intelligence.html) pour entraîner son algorithme de reconnaissance d’images à propos de votre structure de balises et de votre taxonomie métier. Cette intelligence de contenu est ensuite utilisée pour appliquer les balises pertinentes sur un ensemble de ressources différentes.

<!-- TBD: Create a similar flowchart for how training works in CS.
![flowchart](assets/flowchart.gif) 
-->

Pour utiliser le balisage intelligent, effectuez les tâches suivantes :

* [Intégrer Experience Manager avec Adobe Developer Console](#integrate-aem-with-aio).
* [Comprendre les directives et les modèles relatifs aux balises](#understand-tag-models-guidelines).
* [Entraîner le modèle](#train-model).
* [Baliser vos ressources numériques](#tag-assets).
* [Gérer les balises et les recherches](#manage-smart-tags-and-searches).

Les balises intelligentes ne s’appliquent qu’aux clients [!DNL Adobe Experience Manager Assets]. Elles sont disponibles à l’achat sous la forme d’un module complémentaire de [!DNL Experience Manager].

<!-- TBD: Is there a link to buy SCS or initiate a sales call. How are AIO services sold? -->

## Intégrer [!DNL Experience Manager] avec Adobe Developer Console {#integrate-aem-with-aio}

Vous pouvez intégrer [!DNL Adobe Experience Manager] avec les balises intelligentes à l’aide d’Adobe Developer Console. Utilisez cette configuration pour accéder au service de balises intelligentes depuis [!DNL Experience Manager].

Voir [Configuration d’Experience Manager pour le balisage intelligent des ressources](smart-tags-configuration.md) pour les tâches de configuration des balises intelligentes. En arrière-plan, le serveur [!DNL Experience Manager] authentifie vos informations d’identification du service auprès de la passerelle Adobe Developer Console avant de transférer votre demande au service de balises intelligentes.

## Comprendre les directives et les modèles relatifs aux balises {#understand-tag-models-guidelines}.

Un modèle de balise est formé d’un groupe de balises connexes associées à un aspect visuel de l’image. Par exemple, une collection de chaussures peut avoir des balises différentes. Cependant, toutes les balises sont liées à des chaussures et peuvent appartenir au même modèle. Les balises ne peuvent concerner que des aspects visuels des images incontestablement différents. Pour comprendre la représentation du contenu d’un modèle d’entraînement dans [!DNL Experience Manager], imaginez un modèle d’entraînement comme une entité de niveau supérieur, composée d’un groupe de balises ajoutées manuellement et d’exemples d’images pour chaque balise. Chaque balise s’applique exclusivement à une image.

Les balises impossibles à gérer de manière pratique se caractérisent par les critères suivants :

* Aspects non visuels et abstraits, tels que l’année ou la saison de la sortie d’un produit, une ambiance ou une émotion évoquée par une image.
* Différences visuelles fines pour des produits tels que des chemises avec ou sans cols, ou de petits logos incorporés sur des produits.

Avant de créer un modèle de balise et d’entraîner le service, identifiez un ensemble de balises uniques décrivant le mieux les objets contenus dans les images replacés dans le contexte de votre activité. Vérifiez que les ressources figurant dans la série sélectionnée sont conformes aux [instructions d’entraînement](#training-guidelines).

### Instructions d’entraînement {#training-guidelines}

Les images de votre corpus d’entraînement doivent respecter les instructions suivantes :

**Quantité et taille :** 10 images au minimum et 50 images au maximum par balise.

**Cohérence** : les images associées à une même balise doivent être visuellement similaires. Il est préférable de regrouper les balises portant sur les mêmes aspects visuels (par exemple, un même type d’objet dans une image) dans un modèle de balise unique. Par exemple, il est déconseillé d’incorporer une balise `my-party` pour toutes ces images (en situation d’entraînement), car elles ne sont pas similaires visuellement.

![Images d’illustration donnant un exemple d’instructions d’entraînement](assets/do-not-localize/coherence.png)

**Couverture** : les images d’entraînement doivent être suffisamment variées. L’idée est de fournir quelques exemples raisonnablement différents pour apprendre à AEM à se concentrer sur les bons éléments. Si vous appliquez la même balise sur des images visuellement différentes, incluez au moins cinq exemples de chaque type. Par exemple, pour la balise *mannequin-pose-tête-baissée*, incluez davantage d’images d’entraînement similaires à l’image mise en évidence ci-dessous pour que le service reconnaisse les images similaires avec plus de précision lors du balisage.

![Images d’illustration donnant un exemple d’instructions d’entraînement](assets/do-not-localize/coverage_1.png)

**Distraction/obstruction** : l’entraînement du service donne de meilleurs résultats sur les images qui ont moins de distractions (telles que des arrière-plans importants ou des objets/personnes sans lien avec le sujet principal). Par exemple, pour la balise *chaussure-décontractée*, la seconde image n’est pas un bon candidat pour l’entraînement.

![Images d’illustration donnant un exemple d’instructions d’entraînement](assets/do-not-localize/distraction.png)

**Complétude :** si une image est admissible pour plusieurs balises, ajoutez toutes les balises applicables avant d’inclure l’image à des fins de formation. Par exemple, pour les balises telles que *raincoat* et *model-side-view*, ajoutez les deux balises sur la ressource éligible avant de l’inclure pour la formation.

![Images d’illustration donnant un exemple d’instructions d’entraînement](assets/do-not-localize/completeness.png)

**Nombre de balises** : Adobe recommande d’entraîner un modèle à l’aide, au moins, de deux balises distinctes et 10 images différentes pour chaque balise. Dans un modèle de balise unique, n’ajoutez pas plus de 50 balises.

**Nombre d’exemples** : pour chaque balise, ajoutez au moins 10 exemples. Cependant, Adobe recommande environ 30 exemples. Pour chaque balise, 50 exemples au maximum sont pris en charge.

**Empêcher les faux positifs et les conflits** : Adobe recommande de créer un modèle de balise unique pour un aspect visuel donné. Organisez les modèles de balises de manière à éviter le chevauchement des balises entre les modèles. Par exemple, n’utilisez pas de balises communes comme `sneakers` dans deux noms de modèles de balises différents `shoes` et `footwear`. Le processus d’entraînement remplace un modèle de balise entraîné par l’autre en cas de mot-clé commun.

**Exemples** : Voici d’autres exemples à titre de conseil :

* Créez un modèle de balise contenant
   * uniquement des balises relatives à des modèles de voitures.
   * uniquement des balises relatives à des couleurs des chemises.
   * uniquement des balises relatives à des vestes pour femmes et hommes.
* Ne créez pas
   * un modèle de balise contenant des modèles de voitures commercialisés en 2019 et 2020.
   * plusieurs modèles de balises contenant ces mêmes modèles de voitures en nombre limité.

**Images utilisées pour l’entraînement** : vous pouvez utiliser les mêmes images pour entraîner différents modèles de balises. Cependant, ces modèles n’associent pas une image à plusieurs balises dans un modèle donné. Il est donc possible de baliser la même image avec des balises différentes appartenant à différents modèles.

Vous ne pouvez pas annuler l’entraînement. Les instructions ci-dessus doivent vous aider à choisir les bonnes images pour l’entraînement.

## Entraînement du modèle pour vos balises personnalisées {#train-model}

Pour créer et entraîner un modèle pour vos balises spécifiques à votre entreprise, procédez comme suit :

1. Créez les balises nécessaires et la structure de balise appropriée. Chargez les images appropriées dans le référentiel de gestion des ressources numériques (DAM).
1. Dans l’interface utilisateur d’[!DNL Experience Manager], accédez à **[!UICONTROL Ressources]** > **[!UICONTROL Entraînement des balises intelligentes]**.
1. Cliquez sur **[!UICONTROL Créer]**. Indiquez un **[!UICONTROL titre]** et une **[!UICONTROL description]**.
1. Recherchez et sélectionnez les balises existantes dans `cq:tags` pour entraîner le modèle. Cliquez sur **[!UICONTROL Suivant]**.
1. Dans la boîte de dialogue **[!UICONTROL Sélectionner les ressources]**, cliquez sur **[!UICONTROL Ajouter les ressources]** pour chaque balise. Effectuez des recherches dans le référentiel de gestion des actifs numériques ou parcourez le référentiel pour sélectionner au moins 10, et au plus 50 images. Sélectionnez les ressources et non le dossier. Une fois les images sélectionnées, cliquez sur **[!UICONTROL Sélectionner]**.
1. Pour avoir un aperçu des miniatures des images sélectionnées, cliquez sur l’accordéon situé face à une balise. Vous pouvez modifier votre sélection en cliquant sur **[!UICONTROL Ajouter les ressources]**. Une fois la sélection effectuée, cliquez sur **[!UICONTROL Envoyer]**. L’interface utilisateur affiche une notification au bas de la page indiquant que l’entraînement est lancé.
1. Vérifiez l’état de l’entraînement dans la colonne **[!UICONTROL État]** pour chaque modèle de balise. Les états possibles sont [!UICONTROL En Attente], [!UICONTROL Entraîné(s)] et [!UICONTROL Échec].

![Workflow d’entraînement du modèle de balisage pour le balisage intelligent](assets/smart-tag-model-training-flow.png)

*Figure : Étapes du processus d’entraînement du modèle de balisage.*

### Afficher l’état et le rapport d’entraînement {#training-status}

Pour vérifier que le service de balises intelligentes est entraîné sur vos balises dans la série de ressources d’entraînement, examinez le rapport de workflow d’entraînement dans la console Rapports.

1. Dans l’interface d’[!DNL Experience Manager], accédez à **[!UICONTROL Outils > Ressources > Rapports]**.
1. Dans la page **[!UICONTROL Rapports de ressources]**, cliquez sur **[!UICONTROL Créer]**.
1. Sélectionnez le rapport **[!UICONTROL Entraînement des balises intelligentes]**, puis cliquez sur **[!UICONTROL Suivant]** dans la barre d’outils.
1. Indiquez un titre et une description pour le rapport. Sous **[!UICONTROL Planifier le rapport]**, laissez l’option **[!UICONTROL Maintenant]** sélectionnée. Si vous souhaitez planifier le rapport pour une date ultérieure, sélectionnez **[!UICONTROL Plus tard]** et spécifiez une date et une heure. Ensuite, cliquez sur **[!UICONTROL Créer]** dans la barre d’outils.
1. Dans la page **[!UICONTROL Rapports de ressources]**, sélectionnez le rapport que vous avez généré. Pour afficher le rapport, cliquez sur **[!UICONTROL Afficher]** dans la barre d’outils.
1. Passez en revue les détails du rapport. Le rapport affiche l’état d’identification des balises que vous avez entraînées. La couleur verte de la colonne **[!UICONTROL État de l’entraînement]** indique que le service de balises intelligentes est entraîné pour la balise. La couleur jaune indique que le service n’est pas complètement entraîné pour une balise particulière. Dans ce cas, ajoutez d’autres images avec la balise particulière et exécutez le processus d’entraînement pour l’entraînement complet du service sur la balise. Si vous ne voyez pas vos balises dans ce rapport, lancez à nouveau le workflow d’entraînement pour ces balises.
1. Pour télécharger le rapport, sélectionnez-le dans la liste, puis cliquez sur **[!UICONTROL Télécharger]** dans la barre d’outils. Le rapport est téléchargé sous la forme d’une feuille de calcul Microsoft Excel.

## Balisage des ressources {#tag-assets}

Après avoir entraîné le service de balises intelligentes, vous pouvez déclencher le workflow de balisage pour appliquer automatiquement les balises appropriées sur une autre série de ressources similaire. Vous pouvez appliquer le workflow de balisage périodiquement ou en fonction des besoins, aussi bien aux ressources qu’aux dossiers.

### Balisage des ressources à l’aide de la console de workflow {#tagging-assets-from-the-workflow-console}

1. Dans l’interface d’Experience Manager, accédez à **[!UICONTROL Outils > Workflow > Modèles]**.
1. Dans la page **[!UICONTROL Modèles de processus]**, sélectionnez le workflow **[!UICONTROL Balisage intelligent des ressources (gestion des actifs numériques)]**, puis appuyez/cliquez sur **[!UICONTROL Démarrer le processus]** dans la barre d’outils.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Dans la boîte de dialogue **[!UICONTROL Exécuter le processus]**, accédez au dossier de charge utile contenant les ressources sur lesquelles vous souhaitez appliquer vos balises automatiquement.
1. Indiquez un titre pour le workflow et un commentaire facultatif. Cliquez sur **[!UICONTROL Exécuter]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Accédez au dossier de ressources et passez en revue les balises pour vérifier que ces ressources sont correctement balisées. Pour plus d’informations, voir [Gestion des balises intelligentes](#manage-smart-tags-and-searches).

### Balisage des ressources à partir de la chronologie {#tagging-assets-from-the-timeline}

1. Depuis l’interface utilisateur Assets, sélectionnez le dossier contenant les ressources ou des ressources spécifiques auxquelles vous souhaitez appliquer des balises intelligentes.
1. Dans le coin supérieur gauche, ouvrez la **[!UICONTROL Chronologie]**.
1. Ouvrez les actions dans la partie inférieure de la barre latérale gauche et cliquez sur **[!UICONTROL Démarrer le processus]**.

   ![start_workflow](assets/start_workflow.png)

1. Sélectionnez le workflow **[!UICONTROL Balisage intelligent des ressources (gestion des actifs numériques)]** et spécifiez un titre pour le workflow.
1. Cliquez sur **[!UICONTROL Démarrer]**. Le workflow applique vos balises aux ressources. Accédez au dossier de ressources et passez en revue les balises pour vérifier que ces ressources sont correctement balisées. Pour plus d’informations, voir [Gestion des balises intelligentes](#manage-smart-tags-and-searches).

>[!NOTE]
>
>Lors des cycles de balisage suivants, seules les ressources modifiées seront à nouveau balisées avec des balises nouvellement entraînées. Cependant, même les ressources inchangées seront balisées si l’écart entre le dernier cycle de balisage et le cycle de balisage actuel du workflow de balisage dépasse 24 heures. Pour les workflows de balisage périodiques, les ressources inchangées sont balisées lorsque l’intervalle dépasse 6 mois.

### Balisage des ressources chargées {#tag-uploaded-assets}

Experience Manager peut automatiquement baliser les ressources que les utilisateurs chargent dans le système de gestion des actifs numériques. Pour ce faire, les administrateurs configurent un workflow pour ajouter une étape disponible pour le balisage intelligent des ressources. Voir [Comment activer le balisage intelligent pour les ressources chargées](/help/assets/smart-tags-configuration.md#enable-smart-tagging-for-uploaded-assets).

## Gestion des balises intelligentes et des recherches d’images {#manage-smart-tags-and-searches}

Vous pouvez organiser les balises intelligentes pour supprimer toute balise non pertinente qui pourrait avoir été attribuée à vos images de marque, afin que seules les balises les plus pertinentes s’affichent.

La modération de balises intelligentes contribue également à affiner les résultats des recherches d’images basées sur des balises, en garantissant que votre image apparaisse dans les résultats de la recherche pour les balises les plus pertinentes. Essentiellement, cela réduit les risques que des images non pertinentes apparaissent dans les résultats de la recherche.

Vous pouvez également attribuer un rang supérieur à une balise afin d’accroître son degré de pertinence par rapport à une image. La promotion d’une balise pour une image augmente les risques qu’une image apparaisse dans les résultats de la recherche lorsqu’une recherche est basée sur cette balise.

1. Dans l’encadré Omnisearch, recherchez des ressources sur la base d’une balise.
1. Examinez les résultats de la recherche pour identifier une image que vous ne trouvez pas pertinente.
1. Sélectionnez l’image, puis cliquez sur l’icône **[!UICONTROL Gérer les balises]** dans la barre d’outils.
1. Examinez les balises sur la page **[!UICONTROL Gérer les balises]**. Si vous ne souhaitez pas que l’image puisse être recherchée sur la base d’une balise spécifique, sélectionnez la balise, puis cliquez sur l’icône Supprimer dans la barre d’outils. Sinon, cliquez sur le symbole `X` qui apparaît en face du libellé.
1. Pour attribuer un rang supérieur à une balise, sélectionnez-la, puis cliquez sur l’icône Convertir dans la barre d’outils. La balise objet d’une conversion est déplacée dans la section **[!UICONTROL Balises]**.
1. Cliquez sur **[!UICONTROL Enregistrer]**, puis sur **[!UICONTROL OK]** pour fermer la boîte de dialogue de réussite.
1. Accédez à la page Propriétés de l’image. Remarquez que la balise que vous avez convertie se voit attribuer une pertinence élevée et apparaît donc plus haut dans les résultats de la recherche.

### Comprendre les résultats de recherche AEM avec des balises dynamiques  {#understandsearch}

Par défaut, la recherche AEM associe les termes de recherche avec une clause `AND`. L’utilisation de balises intelligentes ne modifie pas ce comportement par défaut. Elle ajoute une clause `OR` supplémentaire pour trouver l’un des termes de recherche dans les balises intelligentes. Par exemple, pour la recherche de `woman running`. Les ressources avec les mots-clés `woman` ou `running` uniquement dans les métadonnées n’apparaissent pas dans les résultats de recherche par défaut. Toutefois, une ressource balisée avec `woman` ou `running` à l’aide de balises intelligentes apparaît dans une telle requête de recherche. Les résultats de la recherche sont donc une combinaison de

* ressources avec les mots-clés `woman` et `running` dans les métadonnées.

* ressources avec balise dynamique avec l’un des mots-clés.

Les résultats de recherche qui correspondent à tous les termes de recherche dans les champs de métadonnées s’affichent en premier, suivis des résultats de recherche correspondant à l’un des termes de recherche des balises dynamiques. Dans l’exemple ci-dessus, l’ordre approximatif de l’affichage des résultats de recherche est le suivant :

1. correspondances de `woman running` dans les différents champs de métadonnées.
1. correspondances de `woman running` dans les balises intelligentes.
1. correspondances de `woman` ou de `running` dans les balises intelligentes.

### Limites du balisage {#limitations}

Les balises intelligentes améliorées sont basées sur des modèles d’apprentissage d’images de marque et de leurs balises. Ces modèles ne sont pas toujours parfaits pour identifier les balises. La version actuelle des balises intelligentes présente les limites suivantes :

* Impossibilité d’identifier des différences subtiles dans les images. Par exemple, des chemises coupe droite ou ajustée.
* Impossibilité d’identifier des balises basées sur des motifs/éléments minuscules d’une image. Par exemple, des logos sur des T-shirts.
* Le balisage est pris en charge dans les paramètres régionaux gérés par AEM. Pour obtenir la liste des langues, voir [Notes de mise à jour relatives aux balises intelligentes](https://docs.adobe.com/content/help/fr-FR/experience-manager-64/release-notes/smart-content-service-release-notes.html).

Pour rechercher des ressources avec des balises intelligentes (standard ou améliorées), utilisez la recherche de texte intégral d’Assets. Il n’y a aucun prédicat de recherche distinct pour les balises intelligentes.

>[!NOTE]
>
>La capacité des balises intelligentes à s’entraîner à partir de vos balises et à les appliquer à d’autres images dépend de la qualité des images que vous utilisez pour l’entraînement.
>Pour obtenir des résultats optimaux, Adobe recommande d’utiliser des images visuellement similaires afin d’entraîner le service pour chaque balise.

>[!MORELIKETHIS]
>
>* [Configuration d’Experience Manager pour le balisage intelligent](smart-tags-configuration.md)
>* [Comprendre comment les balises intelligentes facilitent la gestion des ressources](https://medium.com/adobetech/efficient-asset-management-with-enhanced-smart-tags-887bd47dbb3f)

