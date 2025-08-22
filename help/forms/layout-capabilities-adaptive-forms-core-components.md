---
title: Quelles sont les fonctionnalités de disposition du Forms adaptatif en fonction des composants principaux ?
description: La disposition et l’apparence des formulaires adaptatifs sur différents appareils sont déterminées par les paramètres de disposition. Comprenez les différentes dispositions et leur mode d’application.
feature: Adaptive Forms, Core Components
keywords: Disposition d’un formulaire adaptatif en fonction des composants principaux, dispositions différentes pour les formulaires, dispositions de formulaires dynamiques AEM, dispositions de formulaires AEM Cloud Service, types de dispositions de formulaires dans les composants principaux AEM, dispositions de formulaires adaptatifs
role: User, Developer, Admin
exl-id: dcc01d84-0d39-4fa8-ac47-71a9aba91b1e
source-git-commit: 16b1e7ffa4e3812e9207bb283c63029939f7d14e
workflow-type: tm+mt
source-wordcount: '2106'
ht-degree: 17%

---

# Fonctionnalités de disposition du Forms adaptatif en fonction des composants principaux


| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/layout-capabilities-adaptive-forms.html) |
| AEM as a Cloud Service (composants de base) | [Cliquer ici](/help/forms/layout-capabilities-adaptive-forms.md) |
| AEM as a Cloud Service (composants principaux) | Cet article |

Le Forms adaptatif fournit des composants de première classe pour mettre en page et concevoir les formulaires efficacement. La disposition contrôle l’affichage des composants dans un formulaire. Forms adaptatif prend en charge différentes dispositions : panneau, assistant, accordéon, onglets supérieurs/horizontaux et onglets gauche/vertical.

<!-- ![Types of Layout](/help/forms/assets/generic-layout-hero-image.png){align="center"}-->

## Condition préalable

Avant d’explorer les différentes fonctionnalités d’une disposition, assurez-vous que les composants principaux sont activés pour votre environnement. Installez la dernière version de pour activer les composants principaux de Forms adaptatif pour votre environnement AEM Cloud Service.

## Types de disposition de Forms adaptatif

Les formulaires adaptatifs basés sur les composants principaux prennent en charge les types de dispositions suivants :
* **Mise en page du panneau**
* **Disposition Assistant**
* **Disposition verticale**
* **Disposition horizontale**
* **Disposition en accordéon**

>[!BEGINTABS]

>[!TAB Disposition de panneau]

La disposition de panneau est utile pour organiser les champs associés de manière à faciliter la navigation et la recherche du contenu correspondant. La disposition des panneaux organise les composants de formulaire en sections ou panneaux distincts dans un formulaire adaptatif.

![Disposition de panneau](/help/forms/assets/panel-layout.png)

Disposition de panneau

Vous pouvez utiliser le [composant Panneau](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) pour ajouter la disposition de panneau dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Panneau, reportez-vous à l’article [composant Panneau](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel).

>[!TAB Disposition de l’Assistant]

La disposition de l’Assistant permet de simplifier un formulaire complexe en le divisant en étapes distinctes. Chaque étape représente une partie différente du processus et les utilisateurs naviguent de manière séquentielle parmi les étapes, souvent avec les boutons **Suivant** et **Précédent**. Vous pouvez utiliser la disposition de l’Assistant pour créer un formulaire qui implique plusieurs sections ou étapes.

![Disposition de l’Assistant](/help/forms/assets/wizard-layout-compare.gif)

Disposition de l’Assistant

Vous pouvez utiliser le [composant Assistant](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) pour ajouter la disposition de l’Assistant dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Assistant, reportez-vous à l’article [composant Assistant](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard).

>[!TAB Disposition d’onglets verticaux]

La disposition à onglets verticaux est également appelée onglets sur la disposition de gauche. La disposition onglets verticaux organise les panneaux ou les sections le long du côté gauche d’un formulaire. Il s’agit d’une disposition courante pour les formulaires où les panneaux/sections sont empilés verticalement pour faciliter la lecture et la navigation.

![Disposition verticale](/help/forms/assets/vertical-tab.gif)

Disposition Onglets verticaux

Vous pouvez utiliser le composant [onglets verticaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) pour ajouter la disposition des onglets verticaux dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant onglets verticaux, reportez-vous à l’article [composant onglets verticaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs).


>[!TAB Disposition des onglets horizontaux]

La disposition des onglets horizontaux est également appelée disposition Onglets visibles. La disposition des onglets horizontaux organise les panneaux ou les sections côte à côte dans une ligne. Cette disposition présente les sections du formulaire de manière linéaire sur la largeur du formulaire ou du panneau.


![Disposition horizontale](/help/forms/assets/horizontal-layout.gif)

Disposition des onglets horizontaux

Vous pouvez utiliser le composant [onglets horizontaux](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs) pour ajouter la disposition des onglets horizontaux dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Onglets horizontaux, reportez-vous à l’article [composant Onglets horizontaux](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs).


>[!TAB Disposition en accordéon]

La disposition en accordéon affiche le contenu dans des sections ou des panneaux réductibles d’un formulaire adaptatif. Lorsqu’une section est développée, elle y affiche le contenu tandis que les autres sections restent réduites. Cette disposition est idéale pour afficher de grandes quantités d’informations sous une forme compacte.

![Disposition en accordéon](/help/forms/assets/accordion-layout-compare.gif)

Disposition en accordéon

Vous pouvez utiliser le [composant Accordéon](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) pour ajouter la disposition en accordéon dans un formulaire. Pour obtenir des instructions détaillées sur la configuration des différentes propriétés du composant Accordéon, reportez-vous à l’article [Composant Accordéon](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion).

>[!ENDTABS]

Pour savoir comment insérer une disposition et y ajouter des composants de formulaire, reportez-vous à la section intitulée [Comment insérer une disposition et y ajouter des composants de formulaire ?](#how-to-insert-a-layout-and-add-form-components-to-it)

### Comment choisir la bonne disposition de formulaire adaptatif ?

Il est important de sélectionner la bonne disposition de formulaire adaptatif pour optimiser l’expérience utilisateur et les fonctionnalités de formulaire. Le tableau vous aide à comprendre les différentes options de disposition disponibles et vous guide dans le choix de la disposition la plus appropriée en fonction de vos besoins spécifiques et cas d’utilisation :

| Fonctionnalité | Disposition de panneau | Disposition de l’Assistant | Onglets supérieurs/disposition des onglets verticaux | Onglets à gauche/disposition des onglets horizontaux | Disposition en accordéon |
|--------------------------|-----------------------------------------------------|----------------------------------------------------|-----------------------------------------------------|--------------------------------------------------------|--------|
| **Objectif** | Regroupe les contenus associés dans des sections distinctes. | Guide les utilisateurs et utilisatrices à travers un processus ou un formulaire à plusieurs étapes. | Permet de basculer entre les sections/vues sur la même page | Similaire aux onglets supérieurs, mais disposés verticalement sur la gauche | Organise le contenu en sections réductibles. |
| **Structure** | Sections distinctes | Étapes/pages séquentielles | Onglets horizontaux en haut | Onglets verticaux sur la gauche | Panneaux/sections réductibles |
| **Navigation** | Cliquez sur les en-têtes du panneau pour naviguer. | - Avancer : bouton « Suivant »<br>- Revenir en arrière : bouton « Précédent »<br>- Étapes facultatives à ignorer | Clic sur les onglets pour changer de section | Clic sur les onglets pour changer de section | Cliquez sur les en-têtes pour développer/réduire les sections. |
| **Expérience clientèle** | Organise de grandes quantités de contenu faciles à gérer. | Conseils détaillés pour réduire la surcharge | Basculement entre les vues clair et accessible | Utilisation efficace de l’espace vertical, onglets toujours visibles | Vue compacte avec sections développées/réduites |
| **Cas d’utilisation** | Formulaires complexes avec sections classées | Processus de configuration, formulaires complexes | Paramètres d’organisation des catégories de contenu | Tableaux de bord, vues de données complexes | Questions fréquentes, menus de paramètres, sections de contenu détaillées |


## Comment insérer une disposition et y ajouter des composants de formulaire ?

Le diagramme ci-dessous montre les étapes à suivre pour insérer une disposition dans un formulaire et y ajouter des composants de formulaire :

![Processus d’ajout d’une disposition et de composants de formulaire](/help/forms/assets/workflow-to-add-component-to-a-layout.png)

Tenez compte du **Formulaire de demande informatique** illustré dans la section [Types de disposition de Forms adaptatif](#adaptive-forms-layout-types). Le formulaire rassemble les informations des employés rencontrant des problèmes techniques liés à leur réseau ou ordinateur portable. Il comprend trois panneaux :

* **Détails de l’employé** : le panneau collecte des informations sur l’employé et contient trois zones de texte intitulées Nom, ID d’e-mail et Service.

* **Détails du problème** : le panneau capture les détails du problème. Il comprend une case à cocher pour la catégorie de problème avec trois options : Réseau, Ordinateur ou Autre. Il comprend également deux zones de texte intitulées Veuillez spécifier et Commentaires.

* **Pièces jointes** : le panneau permet aux utilisateurs de charger des documents annexes liés au problème.

Examinons le processus détaillé d’insertion d’une disposition et d’ajout de composants à celle-ci. Dans cet exemple, une disposition à onglets horizontaux est insérée dans un formulaire.

### &#x200B;1. Insérer un composant de disposition dans un formulaire

1. Connectez-vous à l’instance [!DNL Experience Manager Forms].
1. Dans le coin supérieur gauche, sélectionnez **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms et documents]**.
1. Ouvrez un formulaire adaptatif existant en mode d’édition s’il a déjà été créé.

   ![Ouvrir un formulaire adaptatif](/help/forms/assets/insert-layout.png)

   Vous pouvez également [créer un formulaire adaptatif](/help/forms/creating-adaptive-form-core-components.md).

1. Recherchez la section dans l’éditeur de formulaires qui vous permet d’ajouter une mise en page.

   ![Éditeur de formulaire](/help/forms/assets/form-editor.png)
1. Cliquez sur l’icône **Ajouter**. L’icône est un signe plus (+) qui signifie que vous pouvez ajouter de nouveaux composants.

   ![Insérer une disposition](/help/forms/assets/insert-layout-add-icon.png)

   Cliquez sur l’icône **Ajouter** pour afficher une boîte de dialogue **Insérer un nouveau composant** qui affiche différents composants à insérer.

   >[!NOTE]
   >
   > Vous pouvez également [glisser-déposer le composant de disposition](#extra-bytes).

1. Parcourez les composants disponibles dans la boîte de dialogue et sélectionnez la disposition souhaitée dans la liste. Dans notre cas, nous sélectionnons le composant Onglets horizontaux pour insérer la disposition Onglets horizontaux.

   ![Sélectionner les onglets horizontaux](/help/forms/assets/select-horizontal-tab.png)

   Lorsque vous ajoutez le composant Onglets horizontaux à votre formulaire, il se compose initialement de deux panneaux vides, nommés Item1 et Item2, par défaut. Vous devez ajouter manuellement des composants de formulaire à ces panneaux.

   ![Onglets horizontaux.](/help/forms/assets/insert-tabs-on-top.png)

1. Ouvrez les propriétés du composant Onglets horizontaux et spécifiez le nom du composant.
Par exemple, dans ce cas, nous ajoutons le nom du composant Onglets horizontaux en tant que Formulaire de demande informatique.

   ![Ajouter un nom pour les onglets horizontaux](/help/forms/assets/change-name-of-horizontal-tabs.png)

1. Cliquez sur **Terminé**.

   ![Onglets horizontaux.](/help/forms/assets/tabs-on-top-rename-component.png)

Une fois le composant de mise en page ajouté au formulaire, modifiez le nombre de panneaux en fonction des besoins.

### &#x200B;2. Ajouter des panneaux à la disposition

Ajoutez un nouveau panneau au composant Onglets horizontaux :

1. Ouvrez les propriétés du composant Onglets horizontaux et cliquez sur l’onglet **Éléments**.

   ![Onglet Élément pour les onglets horizontaux](/help/forms/assets/tabs-on-top-items-tab.png)

1. Cliquez sur l’icône **Ajouter** pour ajouter un nouveau panneau.

   ![Ajouter un nouveau panneau](/help/forms/assets/tabs-on-top-add-panel.png)

   Lorsque vous cliquez sur l’icône **Ajouter**, la boîte de dialogue **Insérer un nouveau composant** s’affiche.

1. Sélectionnez le composant Panneau.

   ![Ajouter un nouveau panneau](/help/forms/assets/tabs-on-top-new-panel.png)

   Lorsque vous sélectionnez le composant Panneau, le nouveau panneau est ajouté à la disposition horizontale.

   ![Ajouter un nouveau panneau](/help/forms/assets/tabs-on-top-add-new-panel.png)

   Attribuez un nom au nouveau panneau. Sinon, vous ne pouvez pas enregistrer les propriétés du composant Onglets horizontaux.

1. Spécifiez les noms des panneaux comme illustré dans la figure ci-dessous :

   ![Noms de panneau](/help/forms/assets/tabs-on-tops-panel-name.png)

1. Cliquez sur **Terminé**.

   Une fois que vous avez cliqué sur **Terminé**, les trois panneaux s’affichent côte à côte dans une ligne. Les noms des panneaux sont affichés sous forme d’en-têtes pour chaque panneau et vous pouvez ajouter des composants de formulaire à chaque panneau.

   ![Noms de panneau](/help/forms/assets/tabs-on-top-initial-view.png)

   Vous pouvez configurer les propriétés du composant Panneau. Par exemple, le formulaire de demande informatique n’inclut pas les titres du panneau. Voici les étapes de configuration des propriétés du composant Panneau.

1. Ouvrez les propriétés du premier panneau.

   ![Propriétés du panneau 1](/help/forms/assets/tabs-on-tops-panel1-properties.png)

1. Cochez la case **Masquer le titre** dans l’onglet **De base**.

   ![Masquer le titre](/help/forms/assets/tabs-on-top-hide-panel.png)

1. Cliquez sur **Terminé**.

De même, vous pouvez masquer les titres des deux autres panneaux. Une fois cette opération terminée, vous pouvez procéder à l’ajout des composants de formulaire à chaque panneau.

### &#x200B;3. Ajouter des composants de formulaire au panneau

<!-- You can employ one of the following method to add form components to the panel:
* [Add components to a layout's panel using the Add icon](#add-components-to-a-layouts-panel-using-the-add-icon)
* [Drag and drop components into a layout's panel](#drag-and-drop-components-into-a-layouts-panel) -->

1. Recherchez la section du panneau qui vous permet d’ajouter des composants.
1. Cliquez sur l’icône **Ajouter**. L’icône est un signe plus (+) qui signifie que vous pouvez ajouter de nouveaux composants.
   ![Insérer une disposition](/help/forms/assets/tabs-on-top-add-component.png)

   Cliquez sur l’icône **Ajouter** pour afficher une boîte de dialogue **Insérer un nouveau composant** qui affiche différents composants à insérer.

   ![Boîte De Dialogue Insérer Un Nouveau Composant](/help/forms/assets/insert-new-component.png)

1. Parcourez les composants disponibles dans la boîte de dialogue qui s’affiche et sélectionnez le composant de votre choix. Dans notre cas, sélectionnez le composant Zone de texte .
1. Ouvrez les propriétés du composant ajouté et spécifiez son nom. Permet de modifier les propriétés du composant Zone de texte ajouté et de spécifier son nom.
   ![Insérer une disposition](/help/forms/assets/tabs-on-top-textbox-component.png)
1. De même, ajoutez deux autres composants Zone de texte et Nom en tant qu’ID d’e-mail et Service.\
   ![Premier panneau](/help/forms/assets/tabs-on-tops-first-panel.png)

   Maintenant que les composants du premier panneau ont été ajoutés, vous pouvez procéder à l’ajout des composants au second panneau.

1. Pour changer de panneau, cliquez sur **Sélectionner un panneau** dans la barre d’outils.

   ![Basculer le panneau](/help/forms/assets/tabs-on-top-select-panel.png)

   Lorsque vous cliquez sur le **Sélectionner un panneau**, la liste des panneaux ajoutés dans le composant Onglets horizontaux s’affiche.

   ![Basculer le panneau](/help/forms/assets/tabs-on-tops-panel2.png)

1. Sélectionnez **2 Panneau** dans la liste des panneaux et l’affichage change du premier au second panneau.

   ![Deuxième Panneau](/help/forms/assets/tabs-on-top-panel2-component.png)

1. Répétez les étapes décrites entre les étapes 2 et 4 pour ajouter les composants souhaités dans le panneau 2, comme illustré dans la figure ci-dessous :

   ![Deuxième composant du panneau](/help/forms/assets/panel-2-components.png)

1. Passez au panneau **3** en suivant les étapes décrites aux étapes 6 et 7.

1. Répétez les étapes décrites de l’étape 2 à l’étape 4 pour ajouter le composant souhaité dans le panneau 3 :

   ![Composants du troisième panneau](/help/forms/assets/panel-3-component.png)

1. Cliquez sur **[!UICONTROL Aperçu]** dans le coin supérieur droit de votre environnement de création.
   ![Disposition horizontale](/help/forms/assets/horizontal-layout.gif)

Vous pouvez également [faire glisser et déposer les composants](#extra-bytes) pour ajouter les composants de formulaire à chaque panneau.


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



Vous pouvez également supprimer le composant de formulaire du panneau à l’aide de l’icône ![Supprimer](/help/forms/assets/Smock_Delete_18_N.svg).

![Supprimer un composant](/help/forms/assets/delete-component.png)

Vous pouvez également ajouter les validations requises pour les composants selon vos besoins.

## Comment remplacer une disposition existante par une nouvelle disposition ?

Vous pouvez remplacer la disposition d’un formulaire par une nouvelle disposition, ce qui implique de modifier la manière dont les composants sont organisés et affichés dans un formulaire.

Pour remplacer la mise en page existante d’un formulaire, procédez comme suit :

1. Cliquez sur l’icône Remplacer dans la barre d’outils du composant de mise en page pour afficher la boîte de dialogue **[!UICONTROL Remplacer le composant]**.

   ![Remplacer la disposition](/help/forms/assets/replace-layout.png)

1. Sélectionnez la disposition souhaitée dans la boîte de dialogue **[!UICONTROL Remplacer le composant]**.

   ![Boîte de dialogue Remplacer le composant](/help/forms/assets/replace-component.png)

   Après avoir sélectionné la disposition, la disposition des composants dans la disposition change en conséquence. Par exemple, sélectionnez le composant Onglets verticaux dans la boîte de dialogue **[!UICONTROL Remplacer le composant]** ; la disposition du panneau se transforme en onglets sur la gauche :

   ![Disposition verticale](/help/forms/assets/vertical-tab.gif)

## Octets supplémentaires

Pour faire glisser et déposer des composants dans l’éditeur de formulaires, procédez comme suit :

1. Recherchez la section qui vous permet d’ajouter des composants.
1. Accédez au panneau de gauche de votre environnement de création et cliquez sur **Composants**.

   ![Panneau de composant](/help/forms/assets/add-new-component.png)

   Lorsque vous cliquez sur l’option **Composants**, la liste des composants disponibles s’affiche.

   ![Panneau de composant](/help/forms/assets/add-new-component2.png)

1. Parcourez les composants disponibles et sélectionnez le composant de votre choix.

1. Faites glisser le composant en cliquant sur le composant sélectionné et en le maintenant enfoncé, puis faites-le glisser sur la zone du panneau pour le placer.

1. Déposez le composant dans le panneau en relâchant la souris.

## Étapes suivantes

Une fois que vous êtes familiarisé avec les différentes fonctionnalités de disposition d’un formulaire adaptatif basé sur les composants principaux, vous pouvez passer aux étapes suivantes :

* [Création de votre premier formulaire adaptatif en fonction des composants principaux](/help/forms/creating-adaptive-form-core-components.md)
* [Création et utilisation des thèmes de formulaire adaptatif](/help/forms/using-themes-in-core-components.md)



## Voir également

{{see-also}}
