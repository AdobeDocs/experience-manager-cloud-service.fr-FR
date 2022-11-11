---
title: Incorporation d’un formulaire adaptatif dans une page AEM Sites
seo-title: Hwo to add an Adaptive Form to an AEM Sites page?
description: Vous pouvez utiliser le composant Conteneur AEM Forms pour ajouter ou incorporer un Forms adaptatif à une page AEM Sites afin de remplir et d’envoyer un formulaire sans quitter les pages AEM Sites.
feature: Adaptive Forms
source-git-commit: 434071de17d6ff56ede561735f7214d96f98cfa0
workflow-type: tm+mt
source-wordcount: '1178'
ht-degree: 67%

---

# Incorporation d’un formulaire adaptatif à une page de sites AEM {#embed-an-adaptive-form-to-aem-sites-page}

## Présentation {#overview}

AEM Forms permet aux développeurs de formulaires d’incorporer facilement des formulaires adaptatifs dans une page de sites AEM ou une page Web hébergée en dehors d’AEM. Le formulaire adaptatif incorporé est entièrement fonctionnel, et les utilisateurs peuvent le remplir et l’envoyer sans quitter la page. Il permet à l’utilisateur de rester dans le contexte des autres éléments de la page Web et d’interagir simultanément avec le formulaire.

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). -->

Sur une page AEM Sites, vous pouvez ajouter un formulaire ou un document adaptatif avec :

* **Composant Conteneur AEM Forms**
AEM Forms fournit un composant que vous pouvez ajouter à vos pages de site. Le conteneur AEM Forms permet d’incorporer un formulaire ou un document adaptatif.

* **Explorateur de ressources**
Tous les formulaires sont disponibles sous Ressources. Vous pouvez faire glisser et déposer le formulaire sous forme de ressource dans votre page.

## Conditions préalables {#prerequisites}

Pour incorporer un formulaire adaptatif dans une page AEM Sites qui utilise un modèle modifiable, assurez-vous que le composant AEM formulaire est configuré comme un composant autorisé dans le modèle associé.

Dans le cas **Composant Conteneur AEM Forms** n’est pas visible dans la variable **Panneau Explorateur de composants** sur la page AEM sites, effectuez les étapes suivantes, comme illustré dans la vidéo.

>[!VIDEO](https://video.tv.adobe.com/v/3410544)

Si la page Sites utilise un modèle statique, vous devez le configurer dans le système de paragraphes de la page du site.

## Incorporation d’un formulaire adaptatif  {#af-component}

Pour incorporer un formulaire ou un document adaptatif à l’aide du composant Conteneur d’AEM Forms :

1. Ouvrez la page AEM Sites en mode d’édition dans laquelle vous souhaitez incorporer un formulaire adaptatif.
1. À partir du volet Explorateur des composants, faites glisser et déposez le composant Conteneur AEM Forms sur la page. Vous pouvez également chercher un formulaire adaptatif dans le navigateur de ressources et le glisser-déposer sur la page de Sites. Cela inclut le formulaire dans un conteneur AEM Forms. Vous pouvez créer et ajouter un nouveau formulaire adaptatif ou incorporer un formulaire adaptatif existant.

   >[!NOTE]
   >
   >Les composants de plusieurs conteneurs d’AEM Forms sur une page ne sont pas pris en charge.

1. Pour créer et incorporer un nouveau formulaire, dans la barre d’outils du composant, appuyez sur la **Créer un formulaire** icône . Une fenêtre pour créer le formulaire s’ouvre.

1. Appuyez sur le composant Conteneur d’AEM Forms sur la page de site, puis appuyez sur ![settings_icon](assets/settings_icon.png) dans la barre d’action. La boîte de dialogue **[!UICONTROL Modifier le conteneur d’AEM Forms]** s’affiche.
1. Dans la boîte de dialogue Modifier le conteneur d’AEM Forms, précisez ce qui suit.

   **Type de ressource :** sélectionnez le type de ressource à incorporer.
   * **Chemin d’accès à la ressource** : cherchez et sélectionnez le formulaire adaptatif à incorporer. Il est prérempli si vous le faites glisser à partir du navigateur de ressources.
   * **Envoi de publication** : Sélectionnez l’action à déclencher lors de l’envoi du formulaire. Vous pouvez choisir d’afficher un message de remerciement ou une page de remerciement.
      * Afficher

      * **Message de remerciement** : rédigez un message à l’aide de l’éditeur de texte enrichi à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher un message de remerciement.
      * **Page de remerciement** : recherchez et sélectionnez la page à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
         * **Redirection vers la page de remerciement**: Activez l’option pour remplacer la page contenant le formulaire adaptatif incorporé par la page de remerciement. Dans le cas contraire, la page de remerciement remplace le formulaire adaptatif dans le conteneur AEM Forms, sans actualiser les sites sous-jacents de la page. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
   * **Utiliser la langue de la page**: Utilisez le paramètre local de la page AEM Sites au lieu du paramètre régional du formulaire adaptatif.
   * **Définir la cible d’action sur le formulaire**: Sélectionnez cette option pour mettre l’accent sur le premier champ du formulaire adaptatif.
   * **Thème** : sélectionnez un thème qui définit le style des composants de votre formulaire adaptatif. Style comprend des propriétés d’aspect, comme le style de police, la couleur d’arrière-plan, les dimensions et l’alignement.
   * **Le formulaire couvre toute la largeur du cadre.**: Si cette case est cochée, iframe n’est pas utilisé pour générer le formulaire.
   * **Hauteur :** spécifiez la hauteur du conteneur. Laissez ce champ vide pour redimensionner automatiquement le conteneur.
   * **Bibliothèque client CSS** : spécifiez le chemin d’accès à une bibliothèque client CSS.

1. Enregistrez les paramètres. Le formulaire adaptatif est maintenant incorporé dans la page.

AEM site vous permet également de créer à la volée un formulaire adaptatif à l’aide du composant de conteneur d’AEM forms. Suivez les étapes pour créer un formulaire adaptatif à l’aide de **Composant de conteneur AEM Forms** sur la page AEM sites :
1. Ouvrez la page AEM Sites en mode d’édition dans laquelle vous souhaitez incorporer un formulaire adaptatif.
1. À partir du volet Explorateur des composants, faites glisser et déposez le composant Conteneur AEM Forms sur la page.
1. Cliquez sur le bouton **Plus** et vous serez redirigé vers l’assistant de création de formulaire.

   ![Composant de conteneur de formulaires AEM](/help/forms/assets/aemformcontainer.png)

1. Lorsqu’un formulaire adaptatif est créé, vous êtes redirigé vers la page de sites d’AEM et le formulaire créé s’affiche sur la page de sites AEM.

## Publication d’un formulaire adaptatif incorporé {#publishing-embedded-adaptive-form}

Examinons les scénarios suivants pour publier un formulaire adaptatif incorporé sur AEM page de sites :

* Si vous publiez la page AEM Sites pour la première fois et qu’elle comporte un formulaire adaptatif incorporé, publiez la page de site et la ressource incorporée.
* Si vous n’avez modifié que le formulaire incorporé à une page de site publiée, publiez le formulaire d’origine et les modifications seront répercutées sur la page de site publiée. La page de site publiée comprend une référence à la ressource et ne doit pas être republiée.
* Si vous avez modifié la page de site et le formulaire adaptatif ou la communication interactive incorporé, republiez la page de site et la ressource incorporée.

## Modification d’un formulaire adaptatif incorporé  {#modifying-embedded-adaptive-form}

La page AEM Sites conserve une référence au formulaire adaptatif dans le Conteneur d’AEM Forms. Par conséquent, toutes les configurations et les propriétés, comme le thème, les styles et l’action Envoyer, configurées dans le formulaire adaptatif d’origine sont conservées dans le formulaire adaptatif incorporé .

Pour modifier une configuration ou une propriété du formulaire adaptatif incorporé, procédez de l’une des manières suivantes.

* Ouvrez le formulaire d’origine dans les formulaires adaptatifs dans les éditeurs respectifs et modifiez-le.
* Appuyez sur le formulaire adaptatif à partir de la page du site en mode d’édition, puis appuyez sur **[!UICONTROL Modifier dans une nouvelle fenêtre]**. Le formulaire d’origine s’affiche en mode d’édition, et vous pouvez alors le modifier.

>[!NOTE]
>
>Les modifications apportées au formulaire d’origine sont répercutées automatiquement dans le formulaire incorporé. Cependant, republiez le formulaire adaptatif ou la page du site pour répercuter les modifications dans la page publiée.

## Éléments à prendre en compte et bonnes pratiques {#considerations-and-best-practices}

Gardez les points suivants à l’esprit lorsque vous incorporez des formulaires adaptatifs à des pages de sites AEM :

* L’en-tête et le pied de page du formulaire d’origine ne sont pas intégrés dans le formulaire incorporé.
* Les brouillons et les envois de formulaires incorporés sont pris en charge et visibles dans les onglets Brouillons et Formulaires envoyés du portail de formulaires.
* L’action Envoyer configurée sur le formulaire d’origine est conservée dans le formulaire incorporé.
* Le ciblage d’expérience et les tests A/B configurés sur le formulaire d’origine ne fonctionnent pas dans le formulaire incorporé. Cependant, vous pouvez utiliser un ciblage d’expérience au niveau de la page de sites pour présenter différents formulaires basés sur les profils d’utilisateurs.
* Si vous avez configuré Adobe Analytics pour le formulaire d’origine, les données d’analyse du formulaire incorporé seront capturées dans Adobe Analytics. En revanche, elles ne seront pas disponibles dans le rapport d’analyse des formulaires.
