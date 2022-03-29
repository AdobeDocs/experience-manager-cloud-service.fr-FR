---
title: 'Comment incorporer un formulaire adaptatif dans une page AEM Sites ? '
description: Vous pouvez incorporer des formulaires adaptatifs dans des pages AEM Sites. Les utilisateurs peuvent remplir et envoyer des formulaires sans quitter les pages du site.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 100%

---


# Incorporation d’un formulaire adaptatif dans une page AEM Sites {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

[!DNL AEM Forms] permet aux développeurs de formulaires d’incorporer facilement des formulaires adaptatifs dans une page AEM Sites ou une page web hébergée en dehors d’AEM. Le formulaire adaptatif incorporé est entièrement fonctionnel, et les utilisateurs peuvent le remplir et l’envoyer sans quitter la page. Il permet à l’utilisateur de rester dans le contexte des autres éléments de la page Web et d’interagir simultanément avec le formulaire.

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). -->

Sur une page AEM Sites, vous pouvez ajouter un formulaire ou un document adaptatif avec :

* **[[!DNL AEM Forms] Composant de conteneur](#af-component)**
   [!DNL AEM Forms] fournit un composant que vous pouvez ajouter aux pages de votre site. Le composant de conteneur [!DNL AEM Forms] permet d’incorporer un formulaire adaptatif.

* **[Explorateur des ressources](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)**
Tous les formulaires que vous créez sont disponibles sous Ressources. Vous pouvez faire glisser et déposer le formulaire sous forme de ressource dans votre page.

## Conditions préalables {#prerequisites}

Pour incorporer un formulaire ou un document adaptatif dans une page AEM Sites qui utilise un modèle modifiable, assurez-vous que le composant AEM Forms est configuré comme composant autorisé dans le modèle associé. Pour plus d’informations, voir **Stratégie et propriétés (conteneur de disposition)** dans [Création de modèles de page](/help/sites-authoring/templates.md).

Si une page de site utilise un modèle statique, vous devez le configurer dans le système de paragraphe de la page de site. Pour plus d’informations, voir [Configuration des composants en mode Création](/help/sites-authoring/default-components-designmode.md).

## Incorporation d’un formulaire adaptatif   {#af-component}

Pour incorporer un formulaire adaptatif à l’aide du composant de conteneur d’[!DNL AEM Forms] :

1. Ouvrez la page AEM Sites en mode d’édition dans laquelle vous souhaitez incorporer un formulaire adaptatif.
1. À partir du volet Explorateur des composants, faites glisser et déposez le composant de conteneur [!DNL AEM Forms] sur la page.

   Vous pouvez également chercher un formulaire adaptatif dans le navigateur de ressources et le glisser-déposer sur la page de Sites. Cela incorpore le formulaire dans un conteneur [!DNL AEM Forms].

   >[!NOTE]
   >
   >Plusieurs composants de conteneur d’[!DNL AEM Forms] ne sont pas pris en charge sur une page.

1. Appuyez sur le composant de conteneur d’[!DNL AEM Forms] sur la page de site, puis appuyez sur ![settings_icon](assets/settings_icon.png) dans la barre d’action. La boîte de dialogue **[!UICONTROL Modifier le conteneur d’AEM Forms]** s’affiche.
1. Dans la boîte de dialogue Modifier le conteneur d’[!DNL AEM Forms], précisez ce qui suit.

   * **Type de ressource :** sélectionnez le type de ressource à incorporer. Les options sont Formulaire adaptatif
   * **Chemin d’accès à la ressource** : cherchez et sélectionnez le formulaire adaptatif à incorporer. Il est prérempli si vous le faites glisser à partir du navigateur de ressources.
   * (Formulaire adaptatif uniquement) **Publier l’envoi** : sélectionnez l’action à déclencher lors de l’envoi du formulaire. Vous pouvez choisir d’afficher un message de remerciement ou une page de remerciement.

      * **Message de remerciement** : rédigez un message à l’aide de l’éditeur de texte enrichi à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher un message de remerciement.
      * **Page de remerciement** : recherchez et sélectionnez la page à afficher après l’envoi du formulaire. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
      * **Actualiser la page lors de l’envoi** : activez cette option pour actualiser la page contenant le formulaire adaptatif incorporé afin d’afficher la page de remerciement. Autrement, la page de remerciement remplace le formulaire adaptatif dans le conteneur d’[!DNL AEM Forms] sans actualiser la page. Cette option n’est disponible que lorsque vous choisissez d’afficher une page de remerciement.
   * **Thème** : sélectionnez un thème qui définit le style des composants de votre formulaire adaptatif. Style comprend des propriétés d’aspect, comme le style de police, la couleur d’arrière-plan, les dimensions et l’alignement.
   * **Hauteur :** spécifiez la hauteur du conteneur. Laissez ce champ vide pour redimensionner automatiquement le conteneur.
   * **Bibliothèque client CSS** : spécifiez le chemin d’accès à une bibliothèque client CSS.


1. Enregistrez les paramètres. Le formulaire adaptatif est maintenant incorporé dans la page.

## Publication d’un formulaire adaptatif incorporé {#publishing-embedded-adaptive-form}

Examinons les scénarios suivants pour publier une ressource incorporée (formulaire adaptatif ou communication interactive) à une page AEM Sites :

* Si vous publiez la page AEM Sites pour la première fois et qu’elle comporte un formulaire adaptatif incorporé, publiez la page de site et la ressource incorporée.
* Si vous n’avez modifié que le formulaire incorporé à une page de site publiée, publiez le formulaire d’origine et les modifications seront répercutées sur la page de site publiée. La page de site publiée comprend une référence à la ressource et ne doit pas être republiée.
* Si vous avez modifié la page de site et le formulaire adaptatif ou la communication interactive incorporé, republiez la page de site et la ressource incorporée.

## Modification d’un formulaire adaptatif incorporé {#modifying-embedded-adaptive-form-and-interactive-communication}

La page AEM Sites conserve une référence au formulaire adaptatif dans le conteneur d’[!DNL AEM Forms]. Par conséquent, toutes les configurations et les propriétés, comme le thème, les styles et l’action Envoyer, configurées dans le formulaire adaptatif d’origine sont conservées dans le formulaire adaptatif incorporé.

Pour modifier une configuration ou une propriété du formulaire adaptatif incorporé, procédez de l’une des manières suivantes.

* Ouvrez le formulaire d’origine dans des formulaires adaptatifs ou une communication interactive dans les éditeurs correspondants et modifiez-les.
* Appuyez sur le formulaire adaptatif à partir de la page du site en mode d’édition, puis appuyez sur **[!UICONTROL Modifier dans une nouvelle fenêtre]**. Le formulaire d’origine s’affiche en mode d’édition, et vous pouvez alors le modifier.

>[!NOTE]
>
>Les modifications apportées au formulaire d’origine sont répercutées automatiquement dans le formulaire incorporé. Cependant, republiez le formulaire adaptatif ou la page du site pour répercuter les modifications dans la page publiée.

## Considérations et bonnes pratiques {#considerations-and-best-practices}

Lorsque vous incorporez des formulaires adaptatifs à des pages AEM Sites, gardez en tête les points suivants :

* L’en-tête et le pied de page du formulaire d’origine ne sont pas intégrés dans le formulaire incorporé.
* Les brouillons et les envois de formulaires incorporés sont pris en charge et visibles dans les onglets Brouillons et Formulaires envoyés du portail de formulaires.
* L’action Envoyer configurée sur le formulaire d’origine est conservée dans le formulaire incorporé.
* Le ciblage d’expérience et les tests A/B configurés sur le formulaire d’origine ne fonctionnent pas dans le formulaire incorporé. Cependant, vous pouvez utiliser un ciblage d’expérience au niveau de la page de sites pour présenter différents formulaires basés sur les profils d’utilisateurs.
* Si vous avez configuré Adobe Analytics pour le formulaire d’origine, les données d’analyse du formulaire incorporé seront capturées dans Adobe Analytics. En revanche, elles ne seront pas disponibles dans le rapport d’analyse des formulaires.

