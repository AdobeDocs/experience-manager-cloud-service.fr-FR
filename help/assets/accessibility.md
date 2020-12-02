---
title: Accessibilité dans [!DNL Experience Manager Assets]
description: Découvrez comment les fonctions d'accessibilité de  [!DNL Adobe Experience Manager] en tant que Cloud Service aident les utilisateurs handicapés.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 1dc278c85a1dabdd3e6ac4c0de95271d9da3260c
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 2%

---


<!--
Possible topics to cover in this article are below.

* Compile a list of enhancements done in the last ~1 year.
* Showcase a few prominent use cases (search?) in a screencast.
* Top-level actions supported, such as clickable UI elements, keyboard shortcuts, popup dialogs, etc.
* List all UIs that are keyboard navigable.
* Unified list of the product tasks supported, such as, search assets, download assets, add or editing metadata, use DM Viewers, etc.
* Do we need to add support matrix of user tasks with browser and screen reader combinations. Everything may not work in all browsers and/or using all screen readers.
* Any exceptions that users should be aware of. It may help to call out (it may be done in ACR) what tasks are NOT supported.
* CTAs – what's next and more info from AEM team:
  * Link to ACRs on a.com.
  * Generic a11y info by Adobe to begin with.
  * Link to a11y-specific online methods to report issues, seek support, or request enhancements, if any. Asked the a11y team on Slack.
-->

# Fonctionnalités d&#39;accessibilité de [!DNL Adobe Experience Manager Assets] en tant que Cloud Service {#accessibility-in-aem-assets}

[!DNL Adobe Experience Manager] permet aux créateurs et aux éditeurs de contenu de proposer des expériences étonnantes sur le Web. Adobe s&#39;efforce d&#39;inclure les créateurs handicapés en améliorant l&#39;accessibilité de [!DNL Experience Manager]. Le logiciel est continuellement amélioré pour répondre aux besoins de tous les types d&#39;utilisateurs et se conformer aux normes internationales qui incluent les personnes ayant une déficience visuelle, auditive, mobilité ou autre.

[!DNL Experience Manager] publie des informations sur la conformité décrivant les normes qu’il respecte, décrit les fonctions d’accessibilité du produit et décrit le niveau de conformité. Les rapports de conformité à l&#39;accessibilité aident [!DNL Experience Manager] les utilisateurs à comprendre le niveau d&#39;adhésion à diverses normes. Les améliorations apportées à [!DNL Assets] permettent à tous les utilisateurs d&#39;utiliser facilement les interfaces au moyen du clavier, d&#39;un lecteur d&#39;écran, de loupes et d&#39;autres technologies d&#39;assistance.

[!DNL Experience Manager] offre divers niveaux de prise en charge des normes suivantes :

* [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/).
* [Révision de l&#39;article 508 de la loi sur](https://www.access-board.gov/guidelines-and-standards/communications-and-it/about-the-ict-refresh/final-rule/text-of-the-standards-and-guidelines) la réhabilitation.
* [Accessibility Initiative - Accessible Rich Internet Applications (WAI-ARIA) par W3C](https://www.w3.org/WAI/standards-guidelines/aria/).
* [EN 301 549](https://en.wikipedia.org/wiki/EN_301_549).

Pour lire un rapport contenant des détails sur le niveau de conformité, voir la [page Rapport de conformité à l’accessibilité](https://www.adobe.com/accessibility/compliance.html) (ACR).

<!-- TBD: Add link after release.
To know how [!DNL Dynamic Media] is accessible, see [accessibility in [!DNL Dynamic Media]](/). -->

## Technologies d&#39;assistance {#at-support}

Les utilisateurs souffrant d’un handicap se fient fréquemment au matériel et aux logiciels pour accéder au contenu Web et utiliser les logiciels. Ces outils sont connus sous le nom de technologies d’assistance. [!DNL Experience Manager Assets] peut fonctionner avec les types suivants de technologies d&#39;assistance (AT) lors de l&#39;utilisation des fonctionnalités de base du logiciel :

* Lecteurs d’écran et loupe d’écran.
* Logiciel de reconnaissance vocale.
* Utilisation du clavier - navigation et raccourcis.
* Matériel d&#39;assistance, y compris les commandes de commutation, les affichages en braille actualisables et d&#39;autres périphériques d&#39;entrée d&#39;ordinateur.
* Outils d’agrandissement de l’interface utilisateur.

## [!DNL Experience Manager Assets] cas d’utilisation accessibles  {#accessible-assets-use-cases}

Dans [!DNL Experience Manager], les fonctions d&#39;accessibilité répondent à deux exigences clés des utilisateurs [!DNL Experience Manager] et de leurs clients.

* Pour les concepteurs et les créateurs de contenu, il existe des fonctionnalités permettant de créer et de publier du contenu accessible, qui est ensuite utilisé par leurs clients et les visiteurs de site Web. Le contenu peut être utilisé par des personnes handicapées à l&#39;aide de technologies d&#39;assistance. Pour plus d&#39;informations, consultez les [directives d&#39;accessibilité Web](/help/onboarding/accessibility/web-accessibility.md).
* [!DNL Experience Manager] permet également à ses utilisateurs et administrateurs handicapés d’accéder à l’interface utilisateur et aux contrôles pour créer et gérer du contenu. La personne handicapée peut utiliser des technologies d&#39;assistance pour naviguer, utiliser et gérer la fonctionnalité [!DNL Assets].

Les fonctionnalités de base de [!DNL Assets] sont plus accessibles qu&#39;auparavant et sont régulièrement mises à jour pour améliorer la conformité aux normes mondiales. Les opérations CRUD dans [!DNL Assets] comportent un certain degré d&#39;accessibilité. Les workflows DAM tels que l’ajout, la gestion, la recherche et la distribution de ressources sont accessibles à l’aide de raccourcis clavier, de texte de lecteur d’écran, de contraste de couleur, etc.

## Prise en charge de l’utilisation du clavier {#keyboard-use}

De nombreux éléments de l’interface utilisateur qui peuvent être cliqués ou actionnés avec un pointeur peuvent également être manipulés à l’aide du clavier. A l’aide du clavier, les utilisateurs peuvent se concentrer sur les éléments de l’interface et prendre les mesures appropriées. Les utilisateurs peuvent directement utiliser des raccourcis clavier pour déclencher une commande ou une action sans avoir à se concentrer sur les éléments de l’interface utilisateur et la déclencher à l’aide du clavier. Par exemple, les utilisateurs peuvent ouvrir la chronologie d’un fichier dans la partie gauche en accédant au contrôle de l’interface utilisateur à l’aide d’un clavier, en sélectionnant `Return` et en sélectionnant le raccourci clavier `Alt + 2`.

<!-- TBD items:

* The button/menu to toggle between list view and card view exposes relevant info to the screen readers. What about column view option? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* How to open and browse through the profile popup dialog in [!DNL Experience Manager] UI using a keyboard? The navigation does not match the order of visual display of options on the UI. This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’. What about setting preferences and impersonating a user?
* Using the [!DNL Experience Manager] tag browser and operating the buttons like delete tag? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* Read-only form fields can be focused with the keyboard. Can users tab to these fields to understand the contents and are they able to copy text from the fields?
-->

### Raccourcis clavier dans [!DNL Assets] {#keyboard-shortcuts}

Les actions suivantes de [!DNL Assets] fonctionnent avec les raccourcis clavier répertoriés. La plupart des raccourcis clavier qui s’appliquent aux consoles [!DNL Experience Manager] s’appliquent également à [!DNL Assets]. Voir [raccourcis clavier pour Consoles](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md). Voir comment [activer ou désactiver les raccourcis clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md).

| Interface utilisateur ou scénario | Raccourci clavier | Action |
|---|---|---|
| Vue des colonnes dans l&#39;interface utilisateur [!DNL Assets] | Touches fléchées Haut et Bas | Accédez aux fichiers et aux dossiers dans la même hiérarchie. |
| Vue des colonnes dans l&#39;interface utilisateur [!DNL Assets] | Touches fléchées gauche et droite | Accédez aux fichiers et aux dossiers situés au-dessus ou au-dessous du dossier actif. |
| Navigation dans les dossiers dans [!DNL Assets] | `/` | Appelez la recherche en ouvrant la zone Omnisearch. |
| [!DNL Assets] Console | ` | Activer/désactiver les rails |
| [!DNL Assets] Console | `Alt + 1` | Ouvrez l’arborescence de contenu. |
| [!DNL Assets] Console | `Alt + 2` | Ouvrez le rail de gauche [!UICONTROL Navigation]. |
| [!DNL Assets] Console | `Alt + 3` | Afficher [!UICONTROL Chronologie] d’une ressource sélectionnée. |
| [!DNL Assets] Console | `Alt + 4` | Ouvrez les références Live Copy de la ressource sélectionnée. |
| [!DNL Assets] Console | `Alt + 5` | Appelez la recherche et la recherche dans le dossier sélectionné. |
| Ressource ou dossier sélectionné | Retour arrière | Supprimez la ressource ou le dossier sélectionné. |
| Ressource ou dossier sélectionné | `p` | Ouvrez la page Propriétés de la ressource sélectionnée. |
| Ressource ou dossier sélectionné | `e` | Modifiez la ressource sélectionnée. |
| Ressource ou dossier sélectionné | `m` | Déplace la ressource sélectionnée. |
| Ressource ou dossier sélectionné | `Ctrl + c` | Copiez la ressource sélectionnée. |
| Ressource ou dossier sélectionné | `Esc` | Désélectionnez la sélection. |
| La boîte de dialogue s&#39;ouvre et est active | `Esc` | Fermer la boîte de dialogue. |
| Dans un dossier dans DAM | `Ctrl + v` | Collez le fichier copié. |
| [!DNL Assets] Console | `Ctrl + A` | Sélectionnez tous les fichiers. |
| Pages de propriétés des ressources | `Ctrl + S` | Enregistrez les modifications. |
| [!DNL Assets] Console | `?` | Voir une liste de raccourcis clavier. |

## Connectez-vous et naviguez [!DNL Assets] interface utilisateur {#login}

Les utilisateurs peuvent utiliser le clavier pour naviguer jusqu’au champ de connexion et le remplir pour se connecter. Les messages d’erreur dus à des combinaisons de nom d’utilisateur et de mot de passe incorrectes sur la page de connexion sont annoncés par les lecteurs d’écran chaque fois que l’erreur se produit.

Après la connexion, les utilisateurs DAM peuvent naviguer dans l&#39;interface utilisateur [!DNL Assets] à l&#39;aide du clavier. Les éléments de l’interface utilisateur, tels que le rail de gauche, les menus, le profil utilisateur, la barre de recherche, les fichiers et les dossiers, ainsi que les paramètres d’administration et de configuration, peuvent être navigués à l’aide du clavier. L’ordre de navigation du clavier est de gauche à droite et de haut en bas. Lorsque vous naviguez à l’aide du clavier, une option utilisable lorsque l’option est activée est mise en évidence avec un meilleur contraste de couleur et est commentée par un lecteur d’écran. Le cas échéant, un lecteur d’écran annonce l’état (étendu, réduit et mixte, par exemple) des options ciblées du menu. En outre, l’objectif de l’option utilisable est annoncé par un lecteur d’écran, au lieu de, par exemple, l’aspect ou l’emplacement de l’interface utilisateur.

Si un utilisateur développe l’option d’aide ou de profil d’utilisateur à partir du menu, l’option ou l’état approprié est annoncé par le lecteur d’écran. Si un utilisateur développe l’option de profil utilisateur, les options disponibles peuvent être sélectionnées à l’aide du clavier. Par exemple, un administrateur peut se faire passer pour un autre utilisateur. Si un utilisateur recherche une chaîne à partir de l&#39;option [!UICONTROL Aide], un narrateur annonce &quot;Recherche d&#39;aide&quot; pour indiquer qu&#39;une recherche est en cours.

<!-- TBD: Removing for now. Add a more informative video later. Host it on tv.adobe

![Keyboard navigation of top options in [!DNL Experience Manager] user interface](assets/keyboard-navigation-in-aem.gif)

*Figure: Navigating through the options at the top of [!DNL Experience Manager] user interface using `Tab` key.*
-->

## Parcourir les ressources et vue les informations associées {#browse}

Dans l&#39;interface utilisateur [!DNL Assets], les utilisateurs peuvent utiliser le clavier pour parcourir la liste des ressources numériques existantes dans le référentiel de gestion des actifs numériques, prévisualisation ou télécharger un actif, voir les rendus générés, changer de vue, voir les rendus générés, voir la chronologie et l&#39;historique des versions, voir les commentaires et les références, ainsi que la vue et la gestion des métadonnées.

<!-- TBD: Not sure about the following list items mean:

In [!DNL Experience Manager] header section, when navigating in browse mode, screen reader now announces,
  
  * Suggestions to search in Omnisearch.
  * The state as expanded or collapsed for Solutions, Help, Inbox and User options.
  * The Searching Help status message that is displayed when user enters a search string in Search for Help field under Help option
  * The error message if incorrect value is entered in Impersonate as field under User option and focus correctly moves to the text field (NPR-33804).

Review CQ-4282133 before adding - Close button in a coral-dialog wasn't accessible through keyboard, due to which user cannot trigger close button through keyboard press in version preview dialog. After fix, user can close dialog through close button using keyboard.

* CQ-4273122 - Assets of video/audio type will have aria-label in format "Multimedia player: <Title>" so users relying on screen-reader will get to know that they are video/audio assets.
-->

Lors de la navigation dans le référentiel d’actifs, les fonctionnalités suivantes améliorent l’accessibilité :

* Le lecteur d’écran annonce des alternatives textuelles qui décrivent l’objectif ou la fonctionnalité des icônes au lieu de leurs noms.
* Les utilisateurs peuvent accéder aux options de l’interface utilisateur interactive et les cibler dans la liste Références des ressources à l’aide des touches du clavier.
* Les éléments de chaque ligne de la vue de liste sont annoncés comme éléments de la même ligne par les lecteurs d’écran.
* Lorsque vous naviguez à l’aide de la clé `Tab`, la cible d’action peut passer à l’option de fermeture dans la prévisualisation de version.
* Lorsque vous utilisez le clavier pour naviguer, les options d’interface utilisateur exploitables mises en surbrillance ont une mise au point visuelle plus visible et un contraste amélioré. Elle permet à l’utilisateur d’identifier plus facilement la zone ciblée.
* L&#39;utilisation de la touche `Esc` pour supprimer les icônes d&#39;action rapide de la vue de miniature ne supprime pas la cible d&#39;action du clavier du dernier élément sélectionné.
* Une fois une ressource sélectionnée, le raccourci clavier `Alt + 4` ouvre la liste [!UICONTROL Références] dans le rail de gauche. En utilisant la clé `Tab`, les utilisateurs peuvent parcourir les entrées de référence non nulles. En parcourant uniquement les entrées de référence non nulles, vous économisez également les efforts et les touches.
* Les commentaires sur une ressource sont disponibles dans la chronologie de la ressource. Il est accessible si vous accédez au rail gauche à l’aide d’un clavier ou d’un raccourci clavier.
* [!UICONTROL Les ] paramètres de vue  [!DNL Experience Manager] sont accessibles à l’aide du clavier. Les utilisateurs peuvent parcourir les tailles de carte disponibles à l’aide des touches fléchées, puis sélectionner et passer d’un onglet à l’autre pour parcourir et définir d’autres éléments dans la vue Paramètres de Vue existante.

<!-- TBD: Gradually, as more enhancements are done in these categories, add more content.

## Add and upload digital assets {#upload}

## Configure and administer [!DNL Assets] {#config-admin}

* List the a11y fixes in workflows to configure and administer [!DNL Experience Manager Assets]?
* Some enhancements in Processing profiles creation or application to a folder?
* Some enhancements to metadata properties UI?
-->

## Gestion des ressources numériques {#manage-assets}

De nombreuses tâches de gestion des ressources, telles que les opérations CRUD, le téléchargement d’une ressource et l’ajout de métadonnées, sont accessibles à divers degrés. [!DNL Assets] vous permet d’accomplir les tâches à l’aide de diverses technologies d’assistance, notamment un lecteur d’écran et un clavier.

Consultez une démonstration vidéo de l’utilisation d’un clavier pour [parcourir le référentiel et télécharger un fichier](https://youtu.be/K3dgqMRQJys).

Pour les opérations de métadonnées généralement effectuées par des rôles tels que les marketeurs et les administrateurs, les fonctionnalités suivantes améliorent l’accessibilité :

* [!UICONTROL L’option Enregistrer et ] fermer de la   page Propriétés des ressources est désormais accessible à l’aide du clavier.
* Les lecteurs d’écran annoncent les options permettant de supprimer les balises sélectionnées dans l’onglet [!UICONTROL Basic] du fichier [!UICONTROL Propriétés].
* Les utilisateurs peuvent utiliser la boîte de dialogue contextuelle du sélecteur de données à l’aide du clavier. L’élément d’interface utilisateur du sélecteur de date est utilisé pour définir les heures d’ouverture et les heures d’ouverture, ainsi que pour sélectionner la date.
* La fonctionnalité de glisser-déplacer à l’aide du clavier fonctionne correctement dans [!UICONTROL l’éditeur de Schéma de métadonnées] en mode de navigation du lecteur d’écran.
* Un utilisateur peut déplacer la cible d’action à l’aide du clavier vers le champ Utilisateur ou Groupe Ajouté sous [!UICONTROL Groupe d’utilisateurs fermé] dans l’onglet [!UICONTROL Autorisations] du dossier [!UICONTROL Propriétés].

## Recherche de ressources numériques {#search-assets}

Une recherche rapide et transparente des ressources augmente la vitesse du contenu. Les cas d&#39;utilisation de la vitesse du contenu font partie de la fonctionnalité de base [!DNL Assets]. Pour début d&#39;une recherche à partir de la barre de recherche Omnisearch, les utilisateurs peuvent utiliser le raccourci clavier `/` ou `Tab` avec les lecteurs d&#39;écran pour localiser rapidement l&#39;option de recherche. Le lecteur d’écran indique le nom de l’option comme &quot;Bouton de recherche&quot; lorsque l’accent est mis sur l’option de recherche ![option de recherche](assets/do-not-localize/search_icon.png). Les utilisateurs peuvent sélectionner `Return` pour ouvrir la zone Omnisearch. Le lecteur d’écran n’affiche pas seulement le mot-clé saisi dans la zone de recherche, mais également les suggestions de [!DNL Experience Manager Assets]. Les utilisateurs peuvent utiliser une combinaison de touches fléchées `Return` et `Tab` pour accéder aux différentes options permettant de déclencher une recherche.

La fonctionnalité de recherche est rendue accessible par les fonctionnalités suivantes :

* Le titre de la page, tel qu’il est disponible pour un lecteur d’écran, permet d’identifier la page comme page de recherche de ressources.
* Les utilisateurs recherchent des ressources dans le champ Omnisearch. Les utilisateurs peuvent l’ouvrir à l’aide du clavier ou du raccourci clavier `/`.
* Les utilisateurs peuvent début saisir le mot-clé de recherche, puis sélectionner les suggestions automatiques à l’aide des touches fléchées. La suggestion mise en évidence peut être sélectionnée à l&#39;aide de la clé `Return` et la suggestion sélectionnée est recherchée dans les ressources.
* Les lecteurs d’écran peuvent identifier et annoncer les cases à cocher à états mixtes (dans lesquelles, sauf si vous sélectionnez tous les prédicats imbriqués, les cases de premier niveau ne sont pas sélectionnées et sont enfoncées) dans le panneau Filtres lors du filtrage des résultats de recherche.
* L&#39;utilisateur sélectionne les options de recherche une fois la zone Omnisearch fermée.

Lors du filtrage des résultats de la recherche :

* La page des résultats de la recherche comporte un titre informatif pour mieux comprendre les utilisateurs de lecteurs d’écran.
* Un lecteur d’écran affiche les options du filtre de recherche sous forme d’accordéons extensibles.
* Les prédicats comportant des options à états mixtes sont annoncés par les lecteurs d’écran.

## Partage de ressources {#share-assets}

<!-- TBD: Anything about accessibility in DA, BP? AAL team confirmed that there's no content for AAL a11y on helpx.
-->

Lors du partage de fichiers, les fonctionnalités suivantes améliorent l’accessibilité :

* Un utilisateur peut déplacer la cible d’action à l’aide du clavier dans le champ Rechercher et Ajouter l’adresse électronique de la boîte de dialogue de partage de liens.

* Dans la boîte de dialogue de partage de liens, lorsque vous naviguez en mode de navigation, les lecteurs d’écran,

   * Ne narrez pas les informations du tableau dès que la boîte de dialogue est chargée.
   * Peut accéder à toutes les suggestions répertoriées.
   * Narrez les suggestions affichées pour les champs Ajouter l’adresse électronique et Rechercher.

## Documentation accessible {#accessible-docs}

[!DNL Experience Manager] fournit une documentation accessible pour les personnes handicapées. Les éléments suivants permettent de rendre l’offre de contenu accessible pour l’instant, tandis que l’Adobe continue d’améliorer le modèle et le contenu :

* Les lecteurs d’écran peuvent lire le texte.
* Les images et les illustrations ont du texte alternatif disponible.
* La navigation par clavier est possible.
* Les ratios de contraste permettent de mettre en évidence certaines parties du site Web de documentation.

## Fournir des commentaires {#a11y-feedback}

Pour fournir des commentaires, poser des questions et demander des améliorations au produit, liées à l’accessibilité, utilisez les méthodes suivantes :

* Remplissez le formulaire à l’adresse [www.adobe.com/accessibility/feedback.html](https://www.adobe.com/accessibility/feedback.html).
* Envoyez-nous un courriel à access@adobe.com.

>[!MORELIKETHIS]
>
>* [Notes de mise à jour des améliorations apportées à chaque version](/help/release-notes/release-notes-cloud/release-notes-current.md).
>* [[!DNL Adobe Experience Manager] guide](/help/onboarding/accessibility/web-accessibility.md) d&#39;accessibilité.
>* [Rapports de conformité (ACR) et liste VPAT pour les solutions](https://www.adobe.com/accessibility/compliance.html) d&#39;Adobe.

