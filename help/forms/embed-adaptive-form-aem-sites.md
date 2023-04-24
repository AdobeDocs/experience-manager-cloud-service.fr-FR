---
title: Incorporer un formulaire adaptatif dans une page AEM Sites
seo-title: Hwo to add an Adaptive Form to an AEM Sites page?
description: Vous pouvez utiliser le composant Intégration de Forms adaptatif pour ajouter ou incorporer une Forms adaptative à une page AEM Sites afin de remplir et d’envoyer un formulaire sans quitter les pages AEM Sites.
feature: Adaptive Forms
exl-id: 359b05e8-d8c1-4a77-9e70-6f6b6e668560
source-git-commit: 2a487654c3af2d2ec3aa43481caed5e1d4fc77a2
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 61%

---

# Incorporer un formulaire adaptatif dans une page AEM Sites {#embed-an-adaptive-form-to-aem-sites-page}

## Présentation {#overview}

AEM Forms permet aux développeurs de formulaires d’incorporer aisément Adaptive Forms dans une page AEM Sites ou une page web hébergée en dehors d’AEM. Le formulaire adaptatif incorporé est entièrement fonctionnel, et les utilisateurs et utilisatrices peuvent le remplir et l’envoyer sans quitter la page. Il permet à l’utilisateur ou à l’utilisatrice de rester dans le contexte des autres éléments de la page Web et d’interagir simultanément avec le formulaire.



<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). -->

Sur une page AEM Sites, vous pouvez ajouter un formulaire ou un document adaptatif avec :

* **Forms adaptatif - composant Incorporer**
Forms adaptatif : le composant Incorporer permet aux auteurs AEM Sites d’inclure un formulaire adaptatif existant dans une page AEM Sites, améliorant ainsi la réutilisation des formulaires adaptatifs. Les Forms adaptatives existantes peuvent être utilisées seules ou incorporées dans la page du site. Cette intégration permet aux clients de réutiliser le Forms adaptatif qu’ils ont déjà créé.

* **Explorateur des ressources**
Tous les formulaires sont disponibles sous Ressources. Vous pouvez faire glisser et déposer le formulaire sous forme de ressource dans votre page.

## Conditions préalables {#prerequisites}

Pour incorporer un formulaire adaptatif dans une page AEM Sites qui utilise un modèle modifiable, assurez-vous que le composant AEM Forms est configuré comme composant autorisé dans le modèle associé.

Dans le cas **Forms adaptatif - composant Incorporer** n’est pas visible dans la variable **Panneau Explorateur de composants** sur la page AEM sites, effectuez les étapes suivantes, comme illustré dans la vidéo.

>[!VIDEO](https://video.tv.adobe.com/v/3410544)

Si une page de sites utilise un modèle statique, vous devez le configurer dans le système de paragraphe de la page de sites.

## Incorporation d’un formulaire adaptatif  {#af-component}

Pour incorporer un formulaire adaptatif à l’aide de la fonction **[!UICONTROL Forms adaptatif - Incorporer]** component :

1. Ouvrez la page AEM Sites en mode d’édition dans laquelle vous souhaitez incorporer un formulaire adaptatif.
1. Dans le panneau Explorateur de composants, faites glisser et déposez le [!UICONTROL Forms adaptatif - Incorporer] sur la page. Vous pouvez également chercher un formulaire adaptatif dans le navigateur de ressources et le glisser-déposer sur la page de Sites. Vous pouvez ajouter un nouveau formulaire adaptatif ou incorporer un formulaire adaptatif existant.

   >[!NOTE]
   >
   >Plusieurs Forms adaptatives : les composants incorporés sur une page ne sont pas pris en charge.

1. Dans la barre d’outils du composant, appuyez sur l’icône **Créer un formulaire** pour créer et incorporer un formulaire. Une fenêtre permettant de créer le formulaire s’ouvre.

1. Appuyez sur le composant Forms adaptatif intégré - Incorporer dans la page Sites, puis appuyez sur . ![settings_icon](assets/settings_icon.png) dans la barre d’actions. Le **[!UICONTROL Modifier le Forms adaptatif - Incorporer]** s’ouvre.
1. Dans la boîte de dialogue Modifier le Forms adaptatif - Incorporer , spécifiez ce qui suit.

   **Type de ressource :** sélectionnez le type de ressource à incorporer.
   * **Chemin d’accès à la ressource** : cherchez et sélectionnez le formulaire adaptatif à incorporer. Il est prérempli si vous le faites glisser à partir du navigateur de ressources.
   * **Publier l’envoi** : sélectionnez l’action à déclencher lors de l’envoi du formulaire. Vous pouvez choisir d’afficher un message de remerciement ou une page de remerciement.
      * Afficher

      * **Message de remerciement** : rédigez un message à l’aide de l’éditeur de texte enrichi à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher un message de remerciement.
      * **Page de remerciement** : recherchez et sélectionnez la page à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
         * **Rediriger vers la page de remerciement** : activez cette option pour remplacer la page contenant le formulaire adaptatif incorporé par la page de remerciement. Sinon, la page de remerciement remplace le formulaire adaptatif dans la [!UICONTROL Forms adaptatif - Incorporer] sans actualiser les sites sous-jacents de la page. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
   * **Utiliser la langue de la page** : utilisez les paramètres régionaux de la page AEM Sites au lieu de ceux du formulaire adaptatif.
   * **Définir le focus sur le formulaire** : sélectionnez cette option pour définir le focus sur le premier champ du formulaire adaptatif.
   * **Thème** : sélectionnez un thème qui définit le style des composants de votre formulaire adaptatif. Style comprend des propriétés d’aspect, comme le style de police, la couleur d’arrière-plan, les dimensions et l’alignement.
   * **Le formulaire couvre toute la largeur du cadre.**: Si cette case est cochée, iframe n’est pas utilisé pour générer le formulaire.
   * **Hauteur**: Indiquez la hauteur du conteneur. Laissez ce champ vide pour redimensionner automatiquement le conteneur.
   * **Bibliothèque cliente CSS**: Spécifiez le chemin d’accès à une bibliothèque cliente CSS.

1. Enregistrez les paramètres. Le formulaire adaptatif est maintenant incorporé dans la page.

AEM site vous permet également de créer à la volée un formulaire adaptatif à l’aide du composant Forms adaptatif - Incorporer . Suivez les étapes de création d’un formulaire adaptatif à l’aide du **Forms adaptatif - composant Incorporer** sur la page AEM sites :
1. Ouvrez la page AEM Sites en mode d’édition dans laquelle vous souhaitez incorporer un formulaire adaptatif.
1. Dans le panneau Explorateur de composants, faites glisser et déposez le composant Forms adaptatif - Incorporer sur la page.
1. Cliquez sur le bouton **Plus** et vous êtes redirigé vers l’assistant de création de formulaire.

   ![Forms adaptatif - Composant Incorporer](/help/forms/assets/aemformcontainer.png)

1. Vous pouvez désormais incorporer un formulaire adaptatif dans AEM pages du site à l’aide de la fonction [!UICONTROL Composant de conteneur AEM Forms].

## Publication d’un formulaire adaptatif incorporé {#publishing-embedded-adaptive-form}

Examinons les scénarios suivants concernant la publication d’un formulaire adaptatif incorporé dans une page AEM Sites :

* Si vous publiez la page AEM Sites pour la première fois et qu’elle comporte un formulaire adaptatif incorporé, publiez la page de Sites et la ressource incorporée.
* Si vous n’avez modifié que le formulaire incorporé à une page de site publiée, publiez le formulaire d’origine et les modifications seront répercutées sur la page de site publiée. La page de site publiée comprend une référence à la ressource et ne doit pas être republiée.
* Si vous avez modifié la page de site et le formulaire adaptatif ou la communication interactive incorporé, republiez la page de site et la ressource incorporée.

## Modification d’un formulaire adaptatif incorporé  {#modifying-embedded-adaptive-form}

AEM page de sites conserve une référence au formulaire adaptatif dans le Forms adaptatif - Incorporer. Par conséquent, toutes les configurations et les propriétés, comme le thème, les styles et l’action Envoyer, configurées dans le formulaire adaptatif d’origine sont conservées dans le formulaire adaptatif incorporé .

Pour modifier une configuration ou une propriété du formulaire adaptatif incorporé, procédez de l’une des manières suivantes.

* Ouvrez le formulaire d’origine dans des formulaires adaptatifs dans les éditeurs correspondants et modifiez-les.
* Appuyez sur le formulaire adaptatif à partir de la page du site en mode d’édition, puis appuyez sur **[!UICONTROL Modifier dans une nouvelle fenêtre]**. Le formulaire d’origine s’affiche en mode d’édition, et vous pouvez alors le modifier.

>[!NOTE]
>
>Les modifications apportées au formulaire d’origine sont répercutées automatiquement dans le formulaire incorporé. Cependant, republiez le formulaire adaptatif ou la page du site pour répercuter les modifications dans la page publiée.

## Éléments à prendre en compte et bonnes pratiques {#considerations-and-best-practices}

Gardez les points suivants à l’esprit lorsque vous incorporez des formulaires adaptatifs à des pages de sites AEM :

* L’en-tête et le pied de page du formulaire d’origine ne sont pas inclus dans le formulaire incorporé.
* Les brouillons et les envois des formulaires incorporés sont pris en charge et visibles dans les onglets Brouillons et Forms envoyés du portail Forms.
* L’action d’envoi configurée sur le formulaire d’origine est conservée dans le formulaire incorporé.
* Si vous avez configuré Adobe Analytics pour le formulaire d’origine, les données d’analyse du formulaire incorporé seront capturées dans Adobe Analytics. En revanche, elles ne seront pas disponibles dans le rapport d’analyse des formulaires.
