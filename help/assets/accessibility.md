---
title: Accessibilité dans [!DNL Experience Manager Assets].
description: Know how accessibility features in [!DNL Adobe Experience Manager] as a Cloud Service help disabled users.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5d129538618630faff4bb2542668b8e47ef0e5f6
workflow-type: tm+mt
source-wordcount: '1823'
ht-degree: 3%

---


<!--
Original scope of this article for Core Assets for all a11y topics is around the following topics. This has changed since then but keeping this list of topics for posterity's sake.

* Convert the absolute doc links to relative links.
* Add an overview
* Compile a list of enhancements done in the last ~1 year.
* Top-level actions supported, such as clickable UI elements, keyboard shortcuts, popup dialogs, etc.)
* Specific user tasks supported, such as, download assets, datepicker, editing metadata, etc.
* Support matrix of user tasks with browsers and screen readers + OSes combinations
* Exceptions that users should be aware of.
* CTA – what is next and more info from AEM team:
  * Link to ACRs on a.com.
  * Generic a11y info by Adobe to begin with.
  * Examples of other a11y DX Docs from Elle.
  * Link to a11y-specific channels to report issues, seek support, or request enhancements, if any. Available info from Elle.
-->

# Accessibility in [!DNL Adobe Experience Manager Assets] as a Cloud Service {#accessibility-in-aem-assets}

adobe s&#39;engage à fabriquer des produits pour tous les utilisateurs, y compris les personnes handicapées. [!DNL Adobe Experience Manager] est continuellement améliorée pour répondre aux besoins de tous les types d&#39;utilisateurs. [!DNL Experience Manager] publie des informations sur la conformité qui détaillent les normes qu’il respecte, décrit les fonctions d’accessibilité du produit et décrit le niveau de conformité. Il aide les utilisateurs à comprendre l’étendue de l’adhésion.

[!DNL Adobe Experience Manager] offre divers niveaux de prise en charge des normes suivantes :

* [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG/).
* [Section révisée 508](https://www.access-board.gov/guidelines-and-standards/communications-and-it/about-the-ict-refresh/final-rule/text-of-the-standards-and-guidelines).
* [WAI-ARIA](https://www.w3.org/WAI/standards-guidelines/aria/).
* [EN 301 549](https://en.wikipedia.org/wiki/EN_301_549).

Pour accéder au rapport détaillant les niveaux de conformité, consultez la page Rapports de conformité [sur l’accessibilité ](https://www.adobe.com/accessibility/compliance.html) (ACR) pour toutes les solutions d’Adobe.

## Technologies d&#39;assistance {#at-support}

Les utilisateurs souffrant de déficiences se fient fréquemment au matériel et aux logiciels pour accéder au contenu Web. Ces outils sont connus sous le nom de technologies d’assistance. [!DNL Adobe Experience Manager Assets] utilisez les technologies d’assistance suivantes pour permettre aux utilisateurs d’utiliser les fonctionnalités de base :

* Lecteurs d’écran.
* Logiciel de reconnaissance vocale.
* Utilisation du clavier - navigation et raccourcis.
* Outils d’agrandissement de l’interface utilisateur.

## [!DNL Experience Manager Assets] cas d’utilisation accessibles {#accessible-assets-use-cases}

En [!DNL Experience Manager]outre, les fonctions d’accessibilité répondent à deux exigences clés pour [!DNL Experience Manager] les utilisateurs et leurs clients.

Pour les concepteurs et les créateurs de contenu, il existe des fonctionnalités permettant de créer et de publier du contenu accessible, qui est ensuite utilisé par leurs clients et les visiteurs de site Web. Le contenu peut être utilisé par des personnes handicapées à l&#39;aide de technologies d&#39;assistance. Pour plus d’informations, reportez-vous aux directives [d’accessibilité](/help/onboarding/accessibility/web-accessibility.md)Web.

De plus, [!DNL Experience Manager] permet à ses utilisateurs et administrateurs handicapés d’accéder à l’interface utilisateur et aux contrôles pour créer et gérer du contenu. La personne handicapée peut utiliser les technologies d&#39;assistance pour naviguer, utiliser et gérer la [!DNL Assets] capacité.

Les principales fonctionnalités de [!DNL Assets] la section sont plus accessibles qu&#39;auparavant et sont régulièrement mises à jour afin d&#39;améliorer la conformité aux normes mondiales. Les opérations CRUD dans Assets comportent un certain degré d’accessibilité. Les workflows DAM tels que l’ajout, la gestion, la recherche et la distribution de ressources sont accessibles à l’aide de raccourcis clavier, de texte de lecteur d’écran, de contraste de couleur, etc.

## Prise en charge de l’utilisation du clavier {#keyboard-use}

De nombreux éléments de l’interface utilisateur qui peuvent être cliqués ou actionnés avec un pointeur peuvent également être manipulés à l’aide du clavier. A l’aide du clavier, les utilisateurs peuvent se concentrer sur les éléments de l’interface et prendre les mesures appropriées. Les utilisateurs peuvent directement utiliser des raccourcis clavier pour déclencher une commande ou une action sans avoir à se concentrer sur les éléments de l’interface utilisateur et la déclencher à l’aide du clavier. Par exemple, les utilisateurs peuvent ouvrir la chronologie d’un fichier dans la partie gauche en accédant à la commande de l’interface utilisateur à l’aide du clavier et en appuyant sur Retour et en appuyant sur le raccourci `alt + 2` clavier.

<!-- TBD items:

* The button/menu to toggle between list view and card view exposes relevant info to the screen readers. What about column view option? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* How to open and browse through the profile popup dialog in [!DNL Experience Manager] UI using a keyboard? The navigation does not match the order of visual display of options on the UI. This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’. What about setting preferences and impersonating a user?
* Using the [!DNL Experience Manager] tag browser and operating the buttons like delete tag? This info can go into ‘basic handling’ info aka article to ‘understand and use the workspace’.
* Read-only form fields can be focused with the keyboard. Can users tab to these fields to understand the contents and are they able to copy text from the fields?
-->

### Raccourcis clavier dans les ressources {#keyboard-shortcuts}

<!-- TBD: Add here only those keyboard shortcuts that work for/with Assets. Do with Oct release.
-->

| Interface utilisateur ou scénario | Raccourci clavier | Action |
|---|---|---|
| Vue des colonnes dans l’interface utilisateur Ressources | Touches fléchées Haut et Bas | Accédez aux fichiers et aux dossiers dans la même hiérarchie. |
| Vue des colonnes dans l’interface utilisateur Ressources | Touches fléchées gauche et droite | Accédez aux fichiers et aux dossiers situés au-dessus ou au-dessous du dossier actif. |
| Navigation dans les dossiers des ressources | `/` | Appelez la recherche en ouvrant la zone Omnisearch. |
| Console Ressources | ` | Activer/désactiver les rails |
| Console Ressources | Alt + 1 | Ouvrez l’arborescence de contenu. |
| Console Ressources | Alt + 2 | Navigation [!UICONTROL ouverte] : |
| Console Ressources | Alt + 3 | Afficher le [!UICONTROL scénario] d’une ressource sélectionnée. |
| Console Ressources | Alt + 4 | Ouvrez les références Live Copy de la ressource sélectionnée. |
| Console Ressources | Alt + 5 | Appelez la recherche et la recherche dans le dossier sélectionné. |
| Ressource ou dossier sélectionné | Retour arrière | Supprimez la ressource ou le dossier sélectionné. |
| Ressource ou dossier sélectionné | `p` | Ouvrez la page Propriétés de la ressource sélectionnée. |
| Ressource ou dossier sélectionné | `e` | Modifiez la ressource sélectionnée. |
| Ressource ou dossier sélectionné | `m` | Déplace la ressource sélectionnée. |
| Ressource ou dossier sélectionné | Ctrl + C | Copiez la ressource sélectionnée. |
| Ressource ou dossier sélectionné | Échap | Désélectionnez la sélection. |
| La boîte de dialogue s&#39;ouvre et est active | Échap | Fermer la boîte de dialogue. |
| Dans un dossier dans DAM | Ctrl + V | Collez le fichier copié. |
| Console Ressources | Ctrl+A | Sélectionnez tous les fichiers. |
| Pages de propriétés des ressources | Ctrl + S | Enregistrez les modifications. |
| Console Ressources | `?` | Voir une liste de raccourcis clavier. |

La plupart des raccourcis clavier qui s’appliquent aux [!DNL Experience Manager] consoles s’appliquent également aux ressources. See [Keyboard Shortcuts for Consoles](https://docs.adobe.com/content/help/en/experience-manager-65/authoring/essentials/keyboard-shortcuts.html). Découvrez comment [activer ou désactiver les raccourcis clavier](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md).

## Connexion et navigation dans l’interface [!DNL Assets] utilisateur {#login}

Les utilisateurs peuvent utiliser le clavier pour naviguer jusqu’au champ de connexion et le remplir pour se connecter. Les messages d’erreur dus à des combinaisons de nom d’utilisateur et de mot de passe incorrectes sur la page de connexion sont annoncés par les lecteurs d’écran chaque fois que l’erreur se produit.

Après la connexion, les utilisateurs de la gestion des actifs numériques peuvent accéder à l’interface [!DNL Assets] utilisateur à l’aide du clavier. L’ordre de navigation du clavier est de gauche à droite et de haut en bas. Lorsque vous naviguez à l’aide du clavier, toute option exploitable ciblée est mise en évidence avec un meilleur contraste de couleur et est commentée par un lecteur d’écran. Un lecteur d’écran annonce l’état (étendu ou réduit) des options ciblées du menu.

Si un utilisateur développe l’option d’aide ou de profil d’utilisateur à partir du menu, l’option ou l’état approprié est annoncé par le lecteur d’écran. Si un utilisateur développe l’option de profil utilisateur, les options disponibles peuvent être sélectionnées à l’aide du clavier. Par exemple, un utilisateur peut se faire passer pour un autre utilisateur. Option de l’interface utilisateur et message d’erreur

![Navigation au clavier des principales options dans l’interface utilisateur du Experience Manager](assets/keyboard-navigation-in-aem.gif)

*Figure : Navigation dans les options en haut de l’interface utilisateur du Experience Manager à l’aide de la`Tab`touche.*

Si un utilisateur recherche une chaîne à partir de l’option [!UICONTROL Aide] , un narrateur annonce &quot;Recherche d’aide&quot; pour indiquer qu’une recherche est en cours.

## Parcourir les ressources existantes et les informations relatives aux vues {#browse}

Dans l’interface [!DNL Assets] utilisateur, les utilisateurs peuvent utiliser le clavier pour parcourir la liste des ressources numériques existantes dans le référentiel de gestion des actifs numériques, pour prévisualisation ou pour télécharger un actif, voir les rendus générés, changer de vue, voir les rendus générés, voir la chronologie et l’historique des versions, voir les commentaires et les références, ainsi que la vue et la gestion des métadonnées.

<!-- TBD: Not sure about the following list items mean:

In Experience Manager header section, when navigating in browse mode, screen reader now announces,
  
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
* La sélection de l’utilisateur lors de la navigation à l’aide de `Tab` la clé peut passer à l’option de fermeture dans la prévisualisation de version.
* Lorsque vous utilisez le clavier pour naviguer, les options d’interface utilisateur exploitables mises en surbrillance ont une mise au point visuelle plus visible et un contraste amélioré. Elle permet à l’utilisateur d’identifier plus facilement la zone ciblée.
* L&#39;utilisation de la `Esc` touche pour supprimer les icônes d&#39;action rapide de la vue de miniature ne supprime pas la sélection du clavier du dernier élément sélectionné.
* Une fois un fichier sélectionné, appuyez sur le raccourci clavier Alt + 4 pour ouvrir la liste Références. A l’aide de `Tab` la touche, les utilisateurs peuvent parcourir les entrées de référence aucune-zéro.
* Les commentaires sur une ressource sont disponibles dans la chronologie de la ressource. Il est accessible par le clavier.
* Les paramètres de vue dans le Experience Manager sont accessibles par le clavier. L’utilisateur peut parcourir les tailles de carte disponibles à l’aide des touches fléchées, puis sélectionner et faire défiler par onglets pour parcourir et définir d’autres éléments dans la vue des paramètres de Vue existante.

<!-- TBD: Gradually,  as more enhancements are done in these categories, add more content.

## Add and upload digital assets {#upload}

## Configure and administer [!DNL Assets] {#config-admin}

* List the a11y fixes in workflows to configure and administer [!DNL Experience Manager Assets]?
* Some enhancements in Processing profiles creation or application to a folder?
* Some enhancements to metadata properties UI?

-->

## Gestion des éléments numériques {#manage-assets}

De nombreuses tâches de gestion des ressources, telles que les opérations CRUD, le téléchargement d’une ressource et l’ajout de métadonnées, sont accessibles dans divers degrés. Les ressources vous permettent d’accomplir les tâches à l’aide de diverses technologies d’assistance, notamment un lecteur d’écran et un clavier.

Vous pouvez visionner une démonstration vidéo de l’utilisation d’un clavier pour [parcourir le référentiel et télécharger un fichier](https://youtu.be/K3dgqMRQJys).

Pour les opérations de métadonnées généralement effectuées par des rôles tels que les marketeurs et les administrateurs, les fonctionnalités suivantes améliorent l’accessibilité :

* [!UICONTROL L’option Enregistrer et fermer] de la page Propriétés du fichier est désormais accessible à l’aide du clavier.
* Les lecteurs d’écran annoncent les options de suppression des balises sélectionnées dans l’onglet Simple des boutons Propriétés du fichier pour supprimer les balises sélectionnées.
* La boîte de dialogue contextuelle du sélecteur de date peut être utilisée à l’aide du clavier. Le sélecteur de date est utilisé pour définir les heures d’ouverture et les heures d’ouverture.
* La fonctionnalité de glisser-déplacer à l’aide du clavier fonctionne correctement dans l’éditeur de Schéma de métadonnées en mode de navigation du lecteur d’écran.
* Un utilisateur peut déplacer la cible d’action à l’aide du clavier vers le champ Ajouter l’utilisateur ou le groupe sous Groupe d’utilisateurs fermé dans l’onglet Autorisations du dossier Propriétés.

## Recherche de ressources numériques {#search-assets}

Une recherche rapide et transparente des ressources augmente la vitesse du contenu. Les cas d&#39;utilisation de la vitesse du contenu font partie des principales [!DNL Assets] fonctionnalités. Pour début d&#39;une recherche à partir de la barre de recherche Omniture, les utilisateurs peuvent utiliser un raccourci clavier `/` ou `Tab` des lecteurs d&#39;écran pour localiser rapidement l&#39;option de recherche. Le lecteur d’écran indique le nom de l’option en tant que bouton [!UICONTROL de] recherche lorsque l’accent est mis sur l’option ![de](assets/do-not-localize/search_icon.png)recherche des options de recherche. Les utilisateurs peuvent appuyer `Return` sur pour ouvrir la boîte Omnisearch. Le lecteur d’écran n’explique pas seulement le mot-clé saisi dans la zone de recherche, mais il décrit également les suggestions de saisie semi-automatique proposées par [!DNL Experience Manager Assets]. Les utilisateurs peuvent utiliser une combinaison de touches fléchées `Return`et `Tab` accéder aux différentes options pour déclencher une recherche.

La fonctionnalité de recherche est rendue plus accessible par les fonctionnalités suivantes :

* Le titre de la page, tel qu’il est disponible pour un lecteur d’écran, permet d’identifier la page comme page de recherche de ressources.
* Les utilisateurs recherchent des ressources dans la barre d&#39;Omnisearch. Utilisez les touches du clavier ou le raccourci clavier `/` pour accéder à la barre de recherche Omniture.
* Début de saisie du mot-clé de recherche et utilisation du clavier pour sélectionner les suggestions automatiques. Appuyez sur la touche Retour pour accepter une chaîne suggérée automatiquement et rechercher des ressources.
* Les lecteurs d’écran peuvent identifier et annoncer les cases à cocher d’état mixte (dans lesquelles, sauf si vous sélectionnez tous les prédicats imbriqués, les cases de premier niveau ne sont pas sélectionnées et sont enfoncées) dans le panneau Filtres lors du filtrage des résultats de recherche.
* L&#39;utilisateur sélectionne les options de recherche une fois la zone Omnisearch fermée.

Lors du filtrage des résultats de la recherche :

* La page des résultats de la recherche comporte des titres informatifs pour mieux comprendre les utilisateurs de lecteurs d’écran.
* Un lecteur d’écran affiche les options du filtre de recherche sous forme d’accordéons extensibles.
* Les prédicats comportant des boutons à états mixtes sont annoncés par les lecteurs d’écran.

## Partage de ressources {#share-assets}

<!-- TBD: Accessibility in DA, BP, AAL? Asked CCE team for AAL content?
-->

Lors du partage de fichiers, les fonctionnalités suivantes améliorent l’accessibilité :

* Un utilisateur peut déplacer la cible d’action à l’aide du clavier dans le champ Rechercher et Ajouter l’adresse électronique de la boîte de dialogue de partage de liens.

* Dans la boîte de dialogue de partage de liens, lorsque vous naviguez en mode de navigation, les lecteurs d’écran,

   * Ne narrez pas les informations du tableau dès que la boîte de dialogue est chargée.
   * Peut accéder à toutes les suggestions automatiques répertoriées.
   * Narrez les suggestions automatiques affichées pour les champs Ajouter l’adresse électronique et Rechercher.

## Accessibilité dans [!DNL Dynamic Media] {#dynamic-media-accessibility}

Lors de l’utilisation de Contenu multimédia dynamique, les fonctionnalités suivantes permettent de le rendre accessible :

* Un utilisateur peut se concentrer sur `Flyout`, `InlineZoom`, `Shoppable_Banner`, `Zoom_dark`, `Zoom_light``ZoomVertical_dark`et `ZoomVertical_light` les options à l’aide de la clé  dans les détails de la ressource Visionneuses dans .`Tab`[!DNL Dynamic Media]

## Documentation accessible {#accessible-docs}

[!DNL Experience Manager] fournit une documentation accessible qui peut être consommée par les personnes handicapées. Les éléments suivants permettent de rendre l’offre de contenu accessible pour l’instant, tandis que l’Adobe continue d’améliorer le modèle et le contenu :

* Les lecteurs d’écran peuvent lire le texte.
* Les images et les illustrations ont du texte alternatif disponible.
* La navigation par clavier est possible.
* Les ratios de contraste permettent de mettre en évidence certaines parties du site Web de documentation.

<!-- 
## More resources for accessibility {#a11y-resources}

TBD: If anyone is aware of AEM-specific resources that help users leverage any accessibility features or use any assistive technology with AEM, please share or leave a link here.
-->

## Améliorations des [!DNL Experience Manager Assets] versions {#rn-fixes}

Pour une liste des améliorations spécifiques apportées à chaque version, consultez les notes [de mise à jour des](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/release-notes/home.html) versions respectives.

>[!MORELIKETHIS]
>
>* [Conseils AEM en matière d&#39;accessibilité](/help/onboarding/accessibility/web-accessibility.md)
>* [Rapports de conformité pour les solutions d&#39;Adobe](https://www.adobe.com/accessibility/compliance.html)

