---
title: Personnalisation des thèmes de formulaire adaptatif à l’aide de l’éditeur de thèmes
description: Découvrez comment utiliser l’éditeur de thèmes pour créer et personnaliser des thèmes visuels pour le Forms adaptatif basé sur les composants principaux dans Adobe Experience Manager.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: f1b318803b9b854ec2ce800670f6484799113599
workflow-type: tm+mt
source-wordcount: '1951'
ht-degree: 1%

---


# Personnalisation des thèmes de formulaire {#customizing-form-themes}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/themes.html) |
| AEM as a Cloud Service | Cet article |

L’éditeur de thèmes dans Adobe Experience Manager (AEM) Forms est une interface visuelle qui vous permet de créer et de personnaliser des thèmes pour votre Forms adaptatif sans écrire de code manuellement. Un thème définit l’aspect des composants et des panneaux de formulaire, y compris les couleurs d’arrière-plan, les styles de police, les bordures, les dimensions et l’espacement. Lorsque vous appliquez un thème, les styles spécifiés se reflètent sur les composants correspondants et vous pouvez réutiliser le même thème sur plusieurs Forms adaptatives.

L’éditeur de thèmes élimine la nécessité d’une personne développeur dédiée pour le style de formulaire de base. Grâce à vos simples connaissances opérationnelles du CSS, vous pouvez mettre en forme des formulaires à l’aide de la barre latérale visuelle ou écrire des remplacements CSS avancés directement dans l’éditeur.

## Conditions préalables {#prerequisites}

* Autorisations au niveau de l’auteur dans Adobe Experience Manager Forms.
* Compréhension de base des principes de style CSS. Pour obtenir une référence CSS complète, consultez la référence CSS [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference).

## Accédez au répertoire des thèmes {#navigate-to-themes}

1. Connectez-vous à votre instance de création AEM.
1. Accédez à **** > **[!UICONTROL Forms]** > **[!UICONTROL Thèmes]**.

   Le répertoire Thèmes affiche tous les thèmes disponibles, y compris les thèmes standard fournis par la zone de travail d’AEM, ainsi que les thèmes personnalisés que vous ou votre organisation avez créés.

### Créer un thème {#create-a-new-theme}

1. Dans le répertoire Thèmes, sélectionnez le dossier dans lequel vous souhaitez stocker votre nouveau thème.
1. Cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Thème]**.

   ![Créer un thème](/help/forms/assets/custom-theme-create.png)

1. Dans la boîte de dialogue **[!UICONTROL Créer un thème]**, spécifiez les détails suivants :
   * **[!UICONTROL Titre]** : titre descriptif du thème.
   * **[!UICONTROL Name]** : nom du nœud pour le thème.
   * **[!UICONTROL Formulaire adaptatif pour prévisualiser le thème]** : pour un thème de composant principal, sélectionnez un formulaire adaptatif basé sur les composants principaux. **[!UICONTROL Utiliser le formulaire adaptatif par défaut]** utilise un formulaire adaptatif de base, et non les composants principaux. Le formulaire sélectionné s’affiche dans la zone de travail de l’éditeur de thèmes pour un aperçu en temps réel pendant que vous le modifiez.
   * **[!UICONTROL Description]** *(facultatif)* : brève description du thème.
   * **[!UICONTROL Conteneur de configurations]** *(facultatif)* : conteneur de configurations contenant les détails de la configuration des polices Adobe.
   * **[!UICONTROL Balises]** *(facultatif)* : balises associées au thème pour identification et recherche.
1. Cliquez sur **[!UICONTROL Créer]**.

   ![configuration du thème personnalisé](/help/forms/assets/custom-theme-name.png)

   Le thème est créé. Vous pouvez maintenant cliquer sur **[!UICONTROL Modifier]** pour l’ouvrir dans l’éditeur de thèmes.

### Modifier un thème existant {#edit-an-existing-theme}

1. Dans le répertoire **Thèmes**, sélectionnez le thème à modifier.
1. Cliquez sur **[!UICONTROL Modifier]** dans la barre d’actions pour ouvrir le thème dans l’éditeur de thèmes.

   ![ Modification d’un thème ](/help/forms/assets/custom-theme-edit.png)

### Charger un thème {#upload-a-theme}

Vous pouvez importer un package de thème (par exemple, un package exporté à partir d’un autre environnement) dans le répertoire Thèmes :

1. Dans le répertoire **Thèmes**, cliquez sur **[!UICONTROL Créer]** > **[!UICONTROL Chargement de fichier]**.
1. Recherchez le package de thème (fichier ZIP) sur votre ordinateur, puis cliquez sur **[!UICONTROL Télécharger]**.

   ![Thème de chargement - Menu Créer avec l’option Chargement de fichier](/help/forms/assets/custom-theme-upload.png)

Le thème chargé apparaît dans le répertoire des thèmes et peut être modifié comme tout autre thème.

### Télécharger un thème {#download-a-theme}

Vous pouvez exporter un thème sous la forme d’un package (fichier ZIP) pour le réutiliser dans un autre environnement AEM Forms ou le sauvegarder :

1. Dans le répertoire **Thèmes**, sélectionnez un ou plusieurs thèmes (cochez les cases des cartes de thème).
1. Cliquez sur **[!UICONTROL Télécharger]** dans la barre d’actions. Une boîte de dialogue peut s’afficher avec des détails du ou des thèmes sélectionnés.
1. Confirmez ou cliquez sur **[!UICONTROL Télécharger]** dans la boîte de dialogue. Le package de thème est téléchargé sous la forme d’un fichier ZIP sur votre ordinateur.

   ![Télécharger le thème - sélectionnez le thème et cliquez sur Télécharger](/help/forms/assets/custom-theme-download.png)

Vous pouvez charger ce fichier ZIP ultérieurement à l’aide de l’option [Charger un thème](#upload-a-theme) dans le même environnement ou dans un autre.

## Comprendre l’interface de l’éditeur de thèmes {#understand-the-theme-editor}

Lorsque vous ouvrez un thème dans l’éditeur de thèmes, vous voyez deux zones principales :

![Éditeur de thèmes](/help/forms/assets/custom-theme-editor.png)

* **Zone de travail** (côté droit) : affiche un aperçu du formulaire adaptatif lié au thème. Toutes les modifications de style sont immédiatement répercutées ici, afin que vous puissiez voir l’impact de vos modifications en temps réel.
* **Barre latérale** (côté gauche) : contient le panneau **Sélecteurs** qui répertorie tous les composants de formulaire pouvant faire l’objet d’un style dans une arborescence, tels que Page, Formulaire, Champ, Bouton, Panneau, Image, hCaptcha et reCaptcha.

### Barre d’outils Zone de travail {#canvas-toolbar}

![Barre d’outils de la zone de travail de l’éditeur de thèmes avec Activer/désactiver le panneau latéral, Annuler, Rétablir, Émulateur, Modifier/Prévisualiser et les options de thème](/help/forms/assets/custom-theme-toolbar-utilities.png)

De gauche à droite, la barre d’outils propose les éléments suivants :
* **A : Activer/désactiver le panneau latéral** : affiche ou masque la barre latérale des sélecteurs. Utilisez cette option pour agrandir la zone d’aperçu du formulaire lorsque vous souhaitez placer le focus sur la zone de travail ou afficher à nouveau la barre latérale lorsque vous devez sélectionner ou mettre en forme des composants.
* **B : Options du thème** (liste déroulante) : ouvre un menu avec quatre options. Cliquez dessus lorsque vous devez modifier le formulaire de prévisualisation, afficher le CSS, gérer les styles enregistrés ou obtenir de l’aide dans l’éditeur. Lorsque vous ouvrez la liste déroulante Options du thème , vous voyez :

  ![le menu déroulant Options du thème qui affiche les options Configurer, Afficher le thème CSS, Gérer les styles et Aide](/help/forms/assets/custom-theme-configure.png)

   * **[!UICONTROL Configurer]** : basculez le formulaire affiché dans la zone de travail vers un autre formulaire adaptatif. Utilisez cette option pour vérifier l’aspect de votre thème sur un autre formulaire sans quitter l’éditeur.
     ![Configurer le formulaire adaptatif pour la prévisualisation du thème](/help/forms/assets/custom-theme-switch-af.png)
   * **[!UICONTROL Afficher le thème CSS]** : ouvrez une boîte de dialogue avec le fichier CSS compilé complet pour le thème. Pour afficher le CSS uniquement pour le composant actuellement sélectionné, utilisez plutôt **[!UICONTROL Affichage CSS]** dans la barre latérale (pratique pour le débogage ou la copie de règles).
     ![Afficher le CSS final](/help/forms/assets/custom-theme-view-css.png)
   * **[!UICONTROL Gérer les styles]** : ouvrez la boîte de dialogue pour enregistrer, nommer et réutiliser les styles de texte et d’image. Les styles enregistrés peuvent être appliqués à d’autres composants ; les styles récemment utilisés peuvent également apparaître pour une réutilisation rapide.
   * **[!UICONTROL Aide]** : démarrez la visite guidée par image de l’éditeur de thèmes.
* **C : annuler/rétablir** : permet d’annuler ou de réappliquer vos dernières modifications de style. Utile si vous essayez un style et que vous souhaitez revenir en arrière sans perdre d’autres modifications.
* **D : émulateur** : sélectionnez un appareil ou un point d’arrêt (par exemple, bureau, tablette ou mobile) pour prévisualiser le formulaire à cette taille d’écran. L’aperçu du formulaire se redimensionne pour correspondre au point d’arrêt sélectionné. Tous les styles que vous définissez lorsqu’un point d’arrêt est sélectionné s’appliquent uniquement à ce point d’arrêt, ce qui vous permet de définir des styles réactifs. Pour plus d’informations, consultez [Mise en forme pour différentes tailles d’écran](#styling-for-different-screen-sizes).
* **E : Modifier / Prévisualiser** : basculer entre deux modes. La valeur par défaut est **Modifier** : vous pouvez cliquer sur des composants sur la zone de travail pour les sélectionner et modifier leur mise en forme dans la barre latérale. L’option **Aperçu** affiche le formulaire comme un utilisateur final le verrait sans bordures de sélection, libellés de composant ou barre latérale de mise en forme, de sorte que vous puissiez vérifier l’aspect et le comportement du formulaire avec thème avant sa publication.

<!--**3. Bottom of the sidebar: Simulate Error and Simulate Success**

When you style components by state (for example, Error or Success), you can preview that look without submitting the form. In AEM Forms as a Cloud Service, **Simulate Error** and **Simulate Success** are available at the **bottom of the left sidebar**. Scroll down in the sidebar if you don’t see them; they appear when you have a component selected and let you toggle the preview to match the Error or Success state.

* **Simulate Error**: Show the form as if a field failed validation, so you can see your **[!UICONTROL Error]** state styling.
* **Simulate Success**: Show the form as if validation passed, so you can see your **[!UICONTROL Success]** state styling.

Toggle these on or off as you adjust styles for each state. For more on styling by state, see [Style by component state](#style-by-state).-->

### Donner un style à un composant

Vous pouvez sélectionner un composant à mettre en forme de deux manières :
* **Dans la zone de travail** : cliquez directement sur un composant du formulaire (par exemple, un champ de texte, un bouton ou une liste déroulante). L’élément sélectionné est mis en surbrillance avec une bordure et un libellé de composant (par exemple, « Widget de saisie de texte ») s’affiche au-dessus. Les options de mise en forme de ce composant s’affichent dans la barre latérale.

  ![Modifier le thème à partir de la zone de travail](/help/forms/assets/custom-theme-field-level.png)

* **À partir du panneau Sélecteurs** : utilisez l’arborescence de la barre latérale gauche pour effectuer une analyse en profondeur de composants spécifiques. Par exemple, développez **[!UICONTROL Champ]** > **[!UICONTROL Widget]** > **[!UICONTROL Entrée de texte]** pour cibler spécifiquement le widget de zone de texte.

  ![Modifier le thème à partir du panneau Sélecteur](/help/forms/assets/custom-theme-selector.png)

#### Application de styles à un composant {#apply-styles-to-a-component}

Une fois qu’un composant est sélectionné, la barre latérale affiche les propriétés de mise en forme disponibles organisées dans les catégories suivantes :

* **[!UICONTROL Dimensions et position]** : contrôle de l’alignement, de la taille, de la marge intérieure, de la marge, de la largeur, de la hauteur et de l’index Z.
* **[!UICONTROL Texte]** : configurez la famille de polices, l’épaisseur, la couleur, la taille, la hauteur de ligne, l’alignement, l’espacement des lettres, la décoration du texte et la transformation. Pour obtenir la liste complète des propriétés de texte CSS prises en charge, consultez la documentation [Texte CSS MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_text).
* **[!UICONTROL Arrière-plan]** : définissez une couleur, une image ou un gradient d’arrière-plan. Voir la documentation sur les arrière-plans CSS [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_backgrounds_and_borders).
* **[!UICONTROL Bordure]** : permet de définir la largeur, le style, le rayon et la couleur de la bordure.
* **[!UICONTROL Effets]** : ajoutez une opacité, des modes de fusion et des ombres.

Pour appliquer un style :

1. Sélectionnez le composant dans la zone de travail ou le panneau Sélecteurs .
1. Définissez les propriétés visuelles souhaitées dans la barre latérale. Par exemple, choisissez une **[!UICONTROL Couleur d’arrière-plan]** et définissez la **[!UICONTROL Couleur de police]**.
1. Cliquez sur l’icône de coche **[!UICONTROL OK]** pour confirmer la modification de la propriété.

   ![Application du style](/help/forms/assets/custom-theme-applying-style.png)

<!--#### Style by component state {#style-by-state}

Components can have different visual states (for example, default, focus, hover, disabled, error, success). You can style each state separately so the form looks correct during user interaction and validation.

1. Select the component from the canvas or the Selectors panel.
1. In the sidebar, use the **[!UICONTROL State]** dropdown to choose the state you want to style (for example, **[!UICONTROL Default]**, **[!UICONTROL Focus]**, **[!UICONTROL Hover]**, **[!UICONTROL Disabled]**, **[!UICONTROL Error]**, or **[!UICONTROL Success]**).
1. Set the styling properties (Background, Border, Text, and so on) for that state.
1. Click **[!UICONTROL OK]** to confirm.

   ![State dropdown in sidebar for styling Default, Focus, Error, Success, and other states](/help/forms/assets/custom-theme-state-dropdown.png)

The styles you define apply only when the component is in the selected state. For example, if you set a red border and red background for the **[!UICONTROL Error]** state, the field shows that styling when validation fails. If your environment supports it, use **Simulate Error** or **Simulate Success** at the bottom of the sidebar to preview how the component looks in those states without submitting the form.-->

### Style au niveau du formulaire {#form-level-styling}

Le style au niveau du formulaire applique globalement un style à tous les composants du même type. Par exemple, si vous sélectionnez **[!UICONTROL Champ]** dans le panneau **Sélecteurs** et définissez une couleur d’arrière-plan bleue, chaque champ du formulaire (zones de texte, zones numériques, sélecteurs de date et listes déroulantes) hérite de cet arrière-plan bleu.

**Exemple :** pour définir une couleur d’arrière-plan uniforme sur tous les champs du formulaire :

1. Dans le panneau **Sélecteurs**, sélectionnez **[!UICONTROL Champ]**.
1. Dans la barre latérale, définissez la **[!UICONTROL Couleur d’arrière-plan]** sur bleu.
1. Cliquez sur **[!UICONTROL OK]**.

   ![Style au niveau du formulaire](/help/forms/assets/custom-theme-form-level-styling.png)

Tous les composants de champ du formulaire affichent désormais un arrière-plan bleu.

### Style au niveau du composant {#component-level-styling}

Les styles au niveau du composant ciblent un type de composant spécifique, en remplaçant tout style au niveau du formulaire plus large. Par exemple, si vous souhaitez que seul le widget Zone de texte ait une couleur d’arrière-plan différente tandis que tous les autres champs restent bleus, vous ciblez spécifiquement le widget Zone de texte.

**Exemple :** pour définir un arrière-plan vert et une police violette uniquement sur le widget de zone de texte :

1. Dans le panneau Sélecteurs, développez **[!UICONTROL Champ]** > **[!UICONTROL Widget]** > **[!UICONTROL Entrée de texte]**.
1. Définissez la **[!UICONTROL Couleur de police]** sur violette.
   ![Style au niveau du champ](/help/forms/assets/custom-theme-field-level-styling1.png)
1. Définissez la **[!UICONTROL Couleur d’arrière-plan]** sur vert.
   ![Style au niveau du champ](/help/forms/assets/custom-theme-field-level-styling2.png)
1. Cliquez sur **[!UICONTROL OK]**.

Le widget Zone de texte affiche désormais un arrière-plan vert avec du texte violet, tandis que tous les autres champs restent bleus à partir du style au niveau du formulaire.

>[!NOTE]
>
> **Le style au niveau du composant a toujours la priorité sur le style au niveau du formulaire.** Lorsqu’un style est défini aux deux niveaux, le sélecteur au niveau du composant le plus spécifique remplace le sélecteur au niveau du formulaire le plus large. Cela suit les [règles de spécificité CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) standard. Par exemple, si vous définissez un arrière-plan bleu sur tous les champs (au niveau du formulaire) et un arrière-plan vert sur le widget textbox (au niveau du composant), la textbox affiche un arrière-plan vert.

## Mise en forme pour différentes tailles d’écran {#styling-for-different-screen-sizes}

Vous pouvez définir différents styles pour différentes tailles d’appareil afin que votre thème soit réactif. La barre d’outils de l’éditeur de thèmes affiche **options d’appareil** (par exemple, iPhone 5, iPad, Bureau, Tablette, Petit écran) pour prévisualiser et mettre en forme le formulaire à cette taille d’écran.

1. Dans la barre d’outils de la zone de travail, utilisez l’**émulateur d’appareil** : cliquez sur l’un des libellés d’appareil (par exemple, **[!UICONTROL Bureau]**, **[!UICONTROL Tablette]**, **[!UICONTROL iPad]**, **[!UICONTROL Écran plus petit]**). Une règle au-dessus du formulaire affiche la largeur en pixels de l’appareil sélectionné.
1. Une fois cet appareil sélectionné, utilisez la barre latérale pour définir ou ajuster les styles. Les styles s’appliquent uniquement à la vue d’appareil sélectionnée.
1. Passez à un autre appareil et définissez des styles selon vos besoins.
1. Cliquez sur **[!UICONTROL OK]** et enregistrez le thème une fois l’opération terminée.

   ![Émulateur d’appareil dans l’éditeur de thèmes - options de règle et d’appareil (bureau, tablette, iPad, écran plus petit)](/help/forms/assets/custom-theme-emulator.png)

Un même thème peut donc avoir différents espacements, tailles de police ou styles liés à la disposition par appareil, correspondant au comportement de l’éditeur de thèmes [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/themes.html) pour un style réactif.

## Utiliser les remplacements CSS avancés {#use-advanced-css-overrides}

Pour les styles qui ne sont pas disponibles via la barre latérale visuelle, vous pouvez écrire un CSS personnalisé directement dans l’éditeur.

1. Sélectionnez le composant.
1. Dans la barre latérale, développez la section **[!UICONTROL Avancé]**.
1. Écrivez vos règles CSS personnalisées dans la zone **[!UICONTROL Remplacement CSS]**. Ces règles remplacent toutes les propriétés définies par le biais des contrôles visuels en cas de conflit.

Pour obtenir une référence complète des propriétés CSS, reportez-vous à la référence CSS [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference).

### Ajout de pseudo-éléments CSS {#add-css-pseudo-elements}

La section **[!UICONTROL Avancé]** prend également en charge les pseudo-éléments CSS tels que les `::before` et les `::after`. Vous pouvez ainsi injecter du contenu ou un style décoratif autour d’un composant sans modifier la structure du formulaire. Par exemple, pour ajouter un indicateur visuel avant un composant textbox :

1. Sélectionnez le composant (par exemple, `CMP Textbox`).
1. Développez la section **[!UICONTROL Avancé]**.
1. Dans les champs de pseudo-élément `::before`, ajoutez des propriétés CSS telles que :

   ```css
   color: #B10DC9;
   ```

   ![Avant CSS](/help/forms/assets/custom-theme-before-css.png)

1. Dans les champs de pseudo-élément `::after`, ajoutez des propriétés CSS telles que :

   ```css
   color: #006400;
   ```

   ![Après CSS](/help/forms/assets/custom-theme-after-css.png)


Ces pseudo-éléments suivent le comportement CSS standard. Pour une référence complète, voir [Pseudo-éléments CSS MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements).

## Bonnes pratiques {#best-practices}

* **Utilisez le panneau Sélecteurs pour un ciblage précis** : lorsque vous mettez en forme des éléments imbriqués tels qu’un libellé de champ ou une description longue, utilisez le panneau Sélecteurs à gauche plutôt que de cliquer sur la zone de travail. Cela permet de s’assurer que le sélecteur CSS correct est généré avec la spécificité appropriée.
* **Évitez les ressources d’autres thèmes** : lors de la modification d’un thème, ne parcourez pas et n’ajoutez pas de ressources (telles que des images) d’autres thèmes. Si le thème source est déplacé ou supprimé, votre thème actuel se rompt.
* **Ne pas modifier la largeur de disposition du panneau conteneur** : la spécification d’une largeur fixe sur les panneaux de conteneur les rend statiques et les empêche de s’adapter à différentes tailles d’écran.

## Voir également {#see-also}

{{see-also}}