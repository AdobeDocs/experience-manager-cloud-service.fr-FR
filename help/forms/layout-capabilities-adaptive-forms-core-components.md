---
title: Quelles sont les fonctionnalités de mise en page d’Adaptive Forms en fonction des composants principaux ?
description: La disposition et l’apparence des formulaires adaptatifs sur différents appareils sont déterminées par les paramètres de disposition. Comprenez les différentes dispositions et leur mode d’application.
feature: Adaptive Forms, Core Components
keywords: Disposition d’un formulaire adaptatif en fonction des composants principaux, Différentes mises en page pour les formulaires, AEM de mises en page de formulaires dynamiques, AEM Cloud Service de formulaires, types de mises en page de formulaires dans AEM composants principaux, dispositions de formulaires adaptatifs
role: User, Developer, Admin
exl-id: dcc01d84-0d39-4fa8-ac47-71a9aba91b1e
source-git-commit: 7cb963794ca0d7a12d8007564c9fd6e49b53d5c4
workflow-type: tm+mt
source-wordcount: '2104'
ht-degree: 3%

---

# Fonctionnalités de mise en page de Forms adaptatif basées sur les composants principaux


| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/layout-capabilities-adaptive-forms.html?lang=fr) |
| AEM as a Cloud Service (composants de base) | [Cliquez ici](/help/forms/layout-capabilities-adaptive-forms.md) |
| AEM as a Cloud Service (composants principaux) | Cet article |

Adaptive Forms fournit des composants de première classe pour la mise en page et la conception de formulaires de manière efficace. La mise en page contrôle l’affichage des composants dans un formulaire. Les Forms adaptatives prennent en charge différentes mises en page : panneau, assistant, accordéon, onglets dans les onglets supérieur/horizontal et onglets dans les onglets gauche/vertical.

<!-- ![Types of Layout](/help/forms/assets/generic-layout-hero-image.png){align="center"}-->

## Condition préalable

Avant d’explorer les différentes fonctionnalités d’une mise en page, vérifiez que les composants principaux sont activés pour votre environnement. Pour obtenir des instructions détaillées sur l’activation des composants principaux pour votre environnement, [cliquez ici](/help/forms/enable-adaptive-forms-core-components.md).

## Types de disposition Adaptive Forms

Le formulaire adaptatif basé sur les composants principaux prend en charge les types de disposition suivants :
* **Mise en page du panneau**
* **Mise en page de l’assistant**
* **Disposition verticale**
* **Disposition horizontale**
* **Mise en page en accordéon**

>[!BEGINTABS]

>[!TAB Disposition de panneau]

La disposition de panneau est utile pour organiser les champs associés de manière à faciliter la navigation et la recherche de contenu correspondant. La disposition du panneau dispose les composants de formulaire dans des sections ou des panneaux distincts d’un formulaire adaptatif.

![Disposition de panneau](/help/forms/assets/panel-layout.png)

Disposition de panneau

Vous pouvez utiliser le [composant de panneau](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) pour ajouter la disposition de panneau dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Panneau, reportez-vous à l’article [panel component](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) .

>[!TAB Disposition de l’assistant]

La mise en page de l’assistant permet de simplifier un formulaire complexe en le divisant en plusieurs étapes distinctes. Chaque étape représente une partie différente du processus, et les utilisateurs parcourent les étapes de manière séquentielle, souvent avec les boutons **Suivant** et **Précédent** . Vous pouvez utiliser la mise en page de l’assistant pour créer un formulaire comprenant plusieurs sections ou étapes.

![Disposition de l’assistant](/help/forms/assets/wizard-layout-compare.gif)

Disposition de l’assistant

Vous pouvez utiliser le [composant assistant](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) pour ajouter la disposition de l’assistant dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Assistant, reportez-vous à l’article [assistant component](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) .

>[!TAB Disposition Verticale Des Onglets]

La disposition à onglets verticaux est également appelée onglets dans la disposition de gauche. La mise en page à onglets verticaux organise les panneaux ou les sections le long du côté gauche d’un formulaire. Il s’agit d’une disposition courante pour les formulaires où les panneaux/sections sont empilés verticalement pour faciliter la lecture et la navigation.

![Disposition verticale](/help/forms/assets/vertical-tab.gif)

Disposition des onglets verticaux

Vous pouvez utiliser le [composant Onglets verticaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) pour ajouter la mise en page Onglets verticaux dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Onglets verticaux, reportez-vous à l’article [Composant Onglets verticaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) .


>[!TAB Disposition à onglets horizontaux]

La disposition des onglets horizontaux est également appelée Onglets dans la disposition supérieure. La disposition des onglets horizontaux organise les panneaux ou les sections côte à côte dans une rangée. Cette disposition présente les sections de formulaire de manière linéaire sur la largeur du formulaire ou du panneau.


![Disposition horizontale](/help/forms/assets/horizontal-layout.gif)

Disposition des onglets horizontaux

Vous pouvez utiliser le [composant Onglets horizontaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs) pour ajouter la disposition Onglets horizontaux dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Onglets horizontaux, reportez-vous à l’article [Composant Onglets horizontaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs) .


>[!TAB Mise en page en accordéon]

La disposition en accordéon affiche le contenu dans des sections ou des panneaux réductibles d’un formulaire adaptatif. Lorsqu’une section est développée, elle affiche le contenu dans , tandis que d’autres sections restent réduites. Cette disposition est idéale pour afficher de grandes quantités d’informations sous une forme compacte.

![Mise en page en accordéon](/help/forms/assets/accordion-layout-compare.gif)

Disposition en accordéon

Vous pouvez utiliser le [composant d’accordéon](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) pour ajouter la disposition d’accordéon dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant d’accordéon, reportez-vous à l’article [composant d’accordéon](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) .

>[!ENDTABS]

Pour savoir comment insérer une mise en page et y ajouter des composants de formulaire, reportez-vous à la section intitulée [Comment insérer une mise en page et y ajouter des composants de formulaire ?](#how-to-insert-a-layout-and-add-form-components-to-it)

### Comment choisir la bonne disposition de formulaire adaptatif ?

Il est important de sélectionner la disposition de formulaire adaptatif appropriée pour optimiser l’expérience utilisateur et les fonctionnalités de formulaire. Le tableau vous aide à comprendre les différentes options de mise en page disponibles et vous guide dans la sélection de la mise en page la plus appropriée en fonction de vos besoins et cas d’utilisation spécifiques :

| Fonctionnalité | Disposition de panneau | Disposition de l’assistant | Onglets sur la disposition des onglets supérieure/verticale | Onglets sur la disposition d’onglets gauche/horizontal | Disposition en accordéon |
|--------------------------|-----------------------------------------------------|----------------------------------------------------|-----------------------------------------------------|--------------------------------------------------------|--------|
| **Objectif** | Regroupe le contenu associé dans des sections distinctes. | Guides les utilisateurs à travers un processus ou un formulaire à plusieurs étapes | Permet de basculer entre les sections/vues d’une même page. | Semblable aux onglets supérieurs mais organisés verticalement à gauche | Organise le contenu en sections réductibles |
| **Structure** | Sections distinctes | Étapes/pages séquentielles | Onglets horizontaux en haut | Onglets verticaux à gauche | Panneaux/sections réductibles |
| **Navigation** | Cliquez sur les en-têtes du panneau pour naviguer. | - En avant : bouton &quot;Suivant&quot;<br> - En arrière : bouton &quot;Précédent&quot;<br> - Étapes facultatives de saut | Cliquez sur les onglets pour changer de section. | Cliquez sur les onglets pour changer de section. | Cliquer sur les en-têtes pour développer/réduire les sections |
| **Expérience utilisateur** | Organise de grandes quantités de contenu de manière gérable | Conseils détaillés, réduction de l’écrasement | Changement clair et accessible entre les vues | Utilisation efficace de l’espace vertical, des onglets toujours visibles | Affichage réduit avec des sections développées/réduites |
| **Cas d’utilisation** | Formulaires complexes avec sections classées | Configuration de processus, formulaires complexes | Organisation des paramètres ou des catégories de contenu | Tableaux de bord, vues de données complexes | Questions fréquentes, menus des paramètres, sections de contenu détaillées |


## Comment insérer une mise en page et y ajouter des composants de formulaire ?

Le diagramme ci-dessous montre les étapes à suivre pour insérer une mise en page dans un formulaire et y ajouter des composants de formulaire :

![Workflow d’ajout d’une mise en page et de composants de formulaire](/help/forms/assets/workflow-to-add-component-to-a-layout.png)

Examinez le **formulaire de demande informatique** affiché dans la section [Types de disposition de Forms adaptatif](#adaptive-forms-layout-types) . Le formulaire rassemble des informations provenant des employés qui rencontrent des problèmes techniques liés à leur réseau ou leur ordinateur portable. Il comprend trois panneaux :

* **Détails de l’employé** : le panneau collecte des informations sur l’employé et contient trois zones de texte intitulées Nom, ID de message électronique et Service.

* **Détails du problème** : le panneau capture les détails du problème. Elle comprend une case à cocher pour la catégorie de problèmes avec trois options : Réseau, Ordinateur ou Autre. Il comprend également deux zones de texte intitulées Veuillez préciser et Commentaires .

* **Pièces jointes** : le panneau permet aux utilisateurs de télécharger des documents annexes liés au problème.

Explorons le processus étape par étape pour insérer une mise en page et y ajouter des composants. Dans cet exemple, une disposition à onglets horizontaux est insérée dans un formulaire.

### 1. Insertion d’un composant de mise en page dans un formulaire

1. Connectez-vous à l’instance [!DNL Experience Manager Forms].
1. Dans le coin supérieur gauche, sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms &amp; Documents]**.
1. Ouvrez un formulaire adaptatif existant en mode d’édition s’il a déjà été créé.

   ![Ouvrir un formulaire adaptatif](/help/forms/assets/insert-layout.png)

   Vous pouvez également [créer un formulaire adaptatif](/help/forms/creating-adaptive-form-core-components.md).

1. Recherchez la section dans l’éditeur de formulaire qui vous permet d’ajouter une mise en page.

   ![Éditeur de formulaire](/help/forms/assets/form-editor.png)
1. Cliquez sur l&#39;icône **Ajouter** . L’icône est un signe plus (+) qui indique l’option d’ajout de nouveaux composants.

   ![Insérer la mise en page](/help/forms/assets/insert-layout-add-icon.png)

   Cliquez sur l’icône **Ajouter** pour afficher une boîte de dialogue **Insérer un nouveau composant** qui affiche divers composants à insérer.

   >[!NOTE]
   >
   > Vous pouvez également [faire glisser et déposer le composant de mise en page](#extra-bytes).

1. Parcourez les composants disponibles dans la boîte de dialogue et sélectionnez la disposition souhaitée dans la liste. Dans notre cas, nous sélectionnons le composant Onglets horizontaux pour insérer la disposition des onglets horizontaux.

   ![Sélectionner des onglets horizontaux](/help/forms/assets/select-horizontal-tab.png)

   Lorsque vous ajoutez le composant Onglets horizontaux à votre formulaire, il se compose initialement de deux panneaux vides, nommés Item1 et Item2, par défaut. Vous devez ajouter manuellement des composants de formulaire à ces panneaux.

   ![Onglets horizontaux.](/help/forms/assets/insert-tabs-on-top.png)

1. Ouvrez les propriétés du composant Onglets horizontaux et spécifiez le nom du composant.
Par exemple, dans ce cas, nous ajoutons le nom du composant Onglets horizontaux en tant que formulaire de demande informatique.

   ![Ajouter un nom pour les onglets horizontaux](/help/forms/assets/change-name-of-horizontal-tabs.png)

1. Cliquez sur **Terminé**.

   ![Onglets horizontaux.](/help/forms/assets/tabs-on-top-rename-component.png)

Une fois le composant de mise en page ajouté dans le formulaire, modifiez le nombre de panneaux en fonction des besoins.

### 2. Ajout de panneaux à la mise en page

Ajoutez un nouveau panneau au composant Onglets horizontaux :

1. Ouvrez les propriétés du composant Onglets horizontaux et cliquez sur l’onglet **Éléments** .

   ![Onglet Élément pour les onglets Horizontaux](/help/forms/assets/tabs-on-top-items-tab.png)

1. Cliquez sur l&#39;icône **Ajouter** pour ajouter un nouveau panneau.

   ![Ajouter un nouveau panneau](/help/forms/assets/tabs-on-top-add-panel.png)

   Lorsque vous cliquez sur l&#39;icône **Ajouter**, la boîte de dialogue **Insérer un nouveau composant** s&#39;affiche.

1. Sélectionnez le composant de panneau.

   ![Ajouter un nouveau panneau](/help/forms/assets/tabs-on-top-new-panel.png)

   Lorsque vous sélectionnez le composant Panneau, le nouveau panneau est ajouté à la disposition horizontale.

   ![Ajouter un nouveau panneau](/help/forms/assets/tabs-on-top-add-new-panel.png)

   Attribuez un nom au nouveau panneau. Dans le cas contraire, vous ne pourrez pas enregistrer les propriétés du composant Onglets horizontaux.

1. Spécifiez les noms des panneaux comme illustré dans la figure ci-dessous :

   ![Noms de panneau](/help/forms/assets/tabs-on-tops-panel-name.png)

1. Cliquez sur **Terminé**.

   Une fois que vous avez cliqué sur **Terminé**, les trois panneaux s’affichent côte à côte dans une ligne. Les noms des panneaux s’affichent sous forme d’en-têtes pour chaque panneau. Vous pouvez y ajouter des composants.

   ![Noms de panneau](/help/forms/assets/tabs-on-top-initial-view.png)

   Vous pouvez configurer les propriétés du composant Panneau. Par exemple, le formulaire de demande informatique n’inclut pas de titres de panneau. Voici les étapes de configuration des propriétés du composant de panneau.

1. Ouvrez les propriétés du premier panneau.

   ![Propriétés du panneau 1](/help/forms/assets/tabs-on-tops-panel1-properties.png)

1. Cochez la case **Masquer le titre** dans l’onglet **De base** .

   ![Masquer le titre](/help/forms/assets/tabs-on-top-hide-panel.png)

1. Cliquez sur **Terminé**.

De même, vous pouvez masquer les titres des deux autres panneaux. Une fois que vous avez terminé, vous pouvez ajouter des composants de formulaire à chaque panneau.

### 3. Ajout de composants de formulaire au panneau

<!-- You can employ one of the following method to add form components to the panel:
* [Add components to a layout's panel using the Add icon](#add-components-to-a-layouts-panel-using-the-add-icon)
* [Drag and drop components into a layout's panel](#drag-and-drop-components-into-a-layouts-panel) -->

1. Localisez la section du panneau qui vous permet d’ajouter des composants.
1. Cliquez sur l&#39;icône **Ajouter** . L’icône est un signe plus (+) qui indique l’option d’ajout de nouveaux composants.
   ![Insérer la mise en page](/help/forms/assets/tabs-on-top-add-component.png)

   Cliquez sur l’icône **Ajouter** pour afficher une boîte de dialogue **Insérer un nouveau composant** qui affiche divers composants à insérer.

   ![Boîte de dialogue Insérer un nouveau composant](/help/forms/assets/insert-new-component.png)

1. Parcourez les composants disponibles dans la boîte de dialogue qui s’affiche et sélectionnez le composant souhaité. Dans notre cas, sélectionnez le composant Zone de texte .
1. Ouvrez les propriétés du composant ajouté et indiquez son nom. Permet de modifier les propriétés du composant Zone de texte ajouté et de spécifier son nom.
   ![Insérer la mise en page](/help/forms/assets/tabs-on-top-textbox-component.png)
1. De même, ajoutez deux autres composants de zone de texte et nommez les composants ajoutés en tant qu’ID de courrier électronique et Service.\
   ![Premier panneau](/help/forms/assets/tabs-on-tops-first-panel.png)

   Maintenant que les composants du premier panneau ont été ajoutés, vous pouvez continuer à ajouter les composants au deuxième panneau.

1. Pour changer de panneau, cliquez sur **Sélectionner un panneau** dans la barre d’outils.

   ![Changer de panneau](/help/forms/assets/tabs-on-top-select-panel.png)

   Lorsque vous cliquez sur l’icône **Sélectionner un panneau**, la liste des panneaux ajoutés dans le composant Onglets horizontaux s’affiche.

   ![Changer de panneau](/help/forms/assets/tabs-on-tops-panel2.png)

1. Sélectionnez **2 Panel** dans la liste des panneaux et l’affichage passe du premier panneau au second.

   ![Deuxième panneau](/help/forms/assets/tabs-on-top-panel2-component.png)

1. Répétez les étapes décrites des étapes 2 à 4 pour ajouter les composants souhaités dans le panneau 2, comme illustré dans la figure ci-dessous :

   ![Composants du deuxième panneau](/help/forms/assets/panel-2-components.png)

1. Passez au **3 Panel** en suivant les étapes décrites aux étapes 6 et 7.

1. Répétez les étapes décrites des étapes 2 à 4 pour ajouter le composant souhaité dans le panneau 3 :

   ![Composants du troisième panneau](/help/forms/assets/panel-3-component.png)

1. Cliquez sur **[!UICONTROL Aperçu]** dans le coin supérieur droit de votre environnement de création.
   ![Disposition horizontale](/help/forms/assets/horizontal-layout.gif)

Vous pouvez également [ faire glisser les composants](#extra-bytes) pour ajouter les composants de formulaire à chaque panneau.


<!-- #### Drag and drop components into a layout's panel 

1. Locate the section within the panel that allows you to add components. 
2. Navigate to the left panel within your authoring environment and click **Components**.

    ![Component Panel](/help/forms/assets/add-new-component.png){width="200" align="center"}

    When you click the **Components** option, the list of the available components appears.   

    ![Component Panel](/help/forms/assets/add-new-component2.png){width="200" align="center"}

3. Browse the available components and select the Text Box component.

4. Drag the component by clicking and holding the selected component, then drag it over to the panel area to place it.

5. Drop the component into the panel by releasing the mouse. 

6. Open the properties of the added Text Box component and specify its name as Name.
    ![Insert layout](/help/forms/assets/tabs-on-top-textbox-component.png){width="200" align="center"}
7. Similarly, add two more Text Box components and name added the components as Email ID and Department.   
    ![First Panel](/help/forms/assets/tabs-on-tops-first-panel.png){width="200" align="center"}

    Now that the components in the first panel have been added, you can proceed with adding the components to the second panel. 

8. To switch the panel, click **Select Panel** from the toolbar. 

    ![Switch Panel](/help/forms/assets/tabs-on-top-select-panel.png){width="200" align="center"}

    When you click the **Select Panel**, the list of the added panels in the Horizontal Tabs component appears.

    ![Switch Panel](/help/forms/assets/tabs-on-tops-panel2.png){width="200" align="center"}

9. Select **2 Panel** from the panel list and the view changes from the first panel to the second panel.

    ![Second Panel](/help/forms/assets/tabs-on-top-panel2-component.png){width="200" align="center"}

10. Repeat the steps outlined from Step 2 to Step 6 for adding the desired components in panel 2 as shown in the below figure:   

     ![Second Panel components](/help/forms/assets/panel-2-components.png){width="200" align="center"}

11. Switch to the **3 Panel** by following the steps outlined in Step 8 and Step 9.

12. Repeat the steps outlined from Step 2 to Step 6 for adding the desired component in panel 3:

    ![Third Panel components](/help/forms/assets/panel-3-component.png){width="200" align="center"} 

    -->



Vous pouvez également supprimer un composant de formulaire du panneau à l’aide de l’icône ![Supprimer l’icône](/help/forms/assets/Smock_Delete_18_N.svg).

![Suppression d’un composant](/help/forms/assets/delete-component.png)

Vous pouvez également ajouter les validations requises pour les composants, selon les besoins.

## Comment remplacer une disposition existante par une nouvelle disposition ?

Vous pouvez remplacer une mise en page d’un formulaire par une nouvelle mise en page, ce qui implique de modifier la façon dont les composants sont organisés et affichés dans un formulaire.

Effectuez les étapes suivantes pour remplacer la disposition existante d’un formulaire :

1. Cliquez sur l’icône Remplacer dans la barre d’outils du composant de mise en page et la boîte de dialogue **[!UICONTROL Remplacer le composant]** s’affiche.

   ![Remplacer la mise en page](/help/forms/assets/replace-layout.png)

1. Sélectionnez la disposition souhaitée dans la boîte de dialogue **[!UICONTROL Remplacer le composant]**.

   ![Boîte de dialogue Remplacer le composant](/help/forms/assets/replace-component.png)

   Après avoir sélectionné la mise en page, la disposition des composants change en conséquence. Par exemple, sélectionnez le composant Onglets verticaux dans la boîte de dialogue **[!UICONTROL Remplacer le composant]** ; la disposition du panneau se transforme en onglets à gauche :

   ![Disposition verticale](/help/forms/assets/vertical-tab.gif)

## Octets supplémentaires

Pour faire glisser des composants dans l’éditeur de formulaire, procédez comme suit :

1. Recherchez la section qui vous permet d’ajouter des composants.
1. Accédez au panneau de gauche dans votre environnement de création et cliquez sur **Composants**.

   ![Panneau de composants](/help/forms/assets/add-new-component.png)

   Lorsque vous cliquez sur l’option **Components** , la liste des composants disponibles s’affiche.

   ![Panneau de composants](/help/forms/assets/add-new-component2.png)

1. Parcourez les composants disponibles et sélectionnez le composant souhaité.

1. Faites glisser le composant en cliquant et en le maintenant enfoncé, puis faites-le glisser sur la zone de panneau pour le placer.

1. Déposez le composant dans le panneau en relâchant la souris.

## Étapes suivantes

Une fois que vous connaissez les différentes fonctionnalités de mise en page d’un formulaire adaptatif en fonction des composants principaux, vous pouvez passer aux étapes suivantes :

* [Créer votre premier formulaire adaptatif basé sur les composants principaux](/help/forms/creating-adaptive-form-core-components.md)
* [Créer et utiliser des thèmes de formulaire adaptatif](/help/forms/using-themes-in-core-components.md)



## Voir également

{{see-also}}
