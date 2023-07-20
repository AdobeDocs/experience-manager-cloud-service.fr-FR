---
title: Répétabilité dans un formulaire adaptatif (composants principaux)
description: Utilisez la fonction de répétabilité des composants du panneau pour répéter des sections similaires dans un formulaire adaptatif.
role: Architect, Developer, Admin, User
source-git-commit: fcdb96a6bbe8ff8761293eedc0d38efaecb56037
workflow-type: tm+mt
source-wordcount: '1391'
ht-degree: 31%

---


# Création de formulaires avec des sections répétables (composants principaux) {#repeat-panel}


| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-forms-repeatable-sections.html?lang=en) |
| AEM as a Cloud Service | Cet article |

Une section répétable fait référence à une partie d’un formulaire qui peut être dupliquée ou répétée plusieurs fois afin de collecter des informations pour plusieurs instances d’une même donnée.

Prenons l’exemple d’un formulaire utilisé pour collecter des informations sur l’expérience professionnelle d’une personne. Vous pouvez avoir une section répétable pour capturer les détails de chaque tâche précédente. La section répétable contient généralement des champs tels que le nom de l’entreprise, le titre de la tâche, les dates de travail et les responsabilités professionnelles. L’utilisateur peut ajouter plusieurs instances de la section répétable pour saisir des informations sur chaque tâche qu’il a effectuée.

![Répétabilité](/help/forms/assets/repeatable-adaptive-form-example.gif)

À la fin de cet article, vous apprenez à :

* Création d’une section répétable dans un formulaire adaptatif
* Définir le nombre minimal ou maximal de répétitions pour un composant de formulaire adaptatif
* Utilisez l’éditeur de règles pour configurer les actions d’ajout ou de suppression pour les sections répétables.

Vous pouvez utiliser la variable [Panneau](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html), [Accordéon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Onglets horizontaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html)ou [Assistant](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html) pour rendre les sections d’un formulaire adaptatif répétables. Vous pouvez ajouter des composants enfants au panneau, à l’accordéon, aux onglets horizontaux ou aux composants de l’assistant pour créer une section répétable dans un formulaire.


Les exemples de ce document reposent sur la fonction [Panneau](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html) composant. Vous pouvez effectuer les étapes identiques pour créer la variable [Accordéon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Onglets horizontaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html), et [Assistant](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html) composants répétables.

## Ajout ou suppression de sections répétables dans un formulaire {#add-or-delete-repeatable-section-in-panel-container}

Pour répéter un panneau dans le formulaire ou supprimer les panneaux répétables, un auteur de formulaire utilise un composant de bouton pour ajouter ou supprimer une instance du panneau. Pour ajouter ou supprimer des sections répétables (panneaux) dans un formulaire :

* [Rendre le conteneur de panneau répétable](#make-panel-container-repeatable)
* [Ajout d’une section répétable](#add-repeatable-section-using-instance-manager-via-scripts)
* [Suppression de sections répétables](#delete-repeatable-section-using-instance-manager-via-scripts)

### Rendre le conteneur de panneau répétable {#make-panel-container-repeatable}

![Onglet Accessibilité](/help/forms/assets/repeat-panel.png)

Pour rendre un panneau répétable, procédez comme suit :
1. Sélectionnez un conteneur de panneaux et appuyez sur ![cmppr](/help/forms/assets/cmppr.png).
1. Cliquez sur le bouton **panneau de répétition** et activez le bouton d’activation/désactivation sur **rendre le panneau répétable**.
1. Définir **répétitions minimales** comme requis pour les sections répétables minimales, vous pouvez définir **répétitions minimales** à zéro pour la non-réparation des panneaux ou pour supprimer les panneaux répétés. Par défaut, la valeur de répétition minimale est zéro.
1. Définir **répétitions maximales** pour répéter le nombre de fois requis dans le panneau, la valeur est par défaut infinie.

   >[!NOTE]
   >
   > 
   > * La répétition minimale ne peut pas être de valeur -ve.
   > * Pour créer un panneau non répétable, définissez la valeur des champs maximum et minimum sur 1.

### Ajout d’une section répétable à l’aide du gestionnaire d’instances (via des scripts) {#add-repeatable-section-using-instance-manager-via-scripts}

Le parent du panneau à répéter doit contenir un bouton d’ajout pour gérer l’instance de répétition du panneau. Pour insérer des boutons dans le parent et activer des scripts sur les boutons, procédez comme suit :

1. Ajouter un **composant de bouton** au parent du panneau. Dans l’exemple de vidéo ci-dessous, un composant de bouton avec le nom du libellé **Ajouter** et nom du champ **AddPanel**, est utilisé. Sélectionnez le composant et appuyez sur ![edit-rules](/help/forms/assets/edit-rules.png). Les règles du composant de bouton s’ouvrent dans l’éditeur de règles.
1. Dans la fenêtre Éditeur de règles, cliquez sur **Créer**.

   Sélectionnez **Éditeur visuel** dans la ligne Objets et fonctions de formulaire.

   1. Dans la zone de règle, sous QUAND, sélectionnez l’état. **est cliqué**.
   1. Sous ALORS, sélectionnez **Ajouter une instance**, puis effectuez un glisser-déposer du panneau à l’aide de ![bouton bascule-côté-panneau](/help/forms/assets/toggle-side-panel.png) ou sélectionnez-le à l’aide de **Déposez l’objet ou sélectionnez ici.**

   Sélectionner **Éditeur de code** sur la ligne Objets et fonctions de formulaire . Cliquez sur **Modifier les règles** et dans la zone de code :

   * Pour créer un bouton d’ajout de panneau, spécifiez `this.panel.instanceManager.addInstance()`.

   Cliquez sur **Terminé**.

>[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)


### Suppression des sections répétables à l’aide du gestionnaire d’instances (via des scripts) {#delete-repeatable-section-using-instance-manager-via-scripts}

Le parent du panneau doit contenir un bouton de suppression pour supprimer l’instance des panneaux répétables. Effectuez les étapes suivantes pour insérer des boutons dans le parent et activer des scripts sur les boutons pour supprimer les panneaux répétables :

1. Ajouter un **composant de bouton** au parent du panneau, dans la vidéo ci-dessous, un composant de bouton avec le nom du libellé **delete** et nom du champ **DeletePanel** est utilisée. Sélectionnez le composant et appuyez sur ![edit-rules](/help/forms/assets/edit-rules.png). Les règles du composant de bouton s’ouvrent dans l’éditeur de règles.
1. Dans la fenêtre Éditeur de règles, cliquez sur **Créer**.

   Sélectionnez **Éditeur visuel** dans la ligne Objets et fonctions de formulaire.

   1. Dans la zone de règle, sous QUAND **DeletePanel**, sélectionnez état **est cliqué**.
   1. Sous ALORS, sélectionnez **Supprimer une instance**, puis effectuez un glisser-déposer du panneau à l’aide de ![bouton bascule-côté-panneau](/help/forms/assets/toggle-side-panel.png) ou sélectionnez-le à l’aide de **Déposez l’objet ou sélectionnez ici.**

   Sélectionner **Éditeur de code** sur la ligne Objets et fonctions de formulaire . Cliquez sur **Modifier les règles** et dans la zone de code :

   * Pour créer un bouton de suppression de panneau, spécifiez `this.panel.instanceManager.removeInstance(this.panel.instanceIndex)`.

   Cliquez sur **Terminé**.
>[!VIDEO](https://video.tv.adobe.com/v/3421620/adaptive-forms-repeatable-sections)

>[!NOTE]
>
>Si un champ appartient à un panneau répétable, vous ne pouvez pas y accéder directement via son nom dans vos scripts. Pour accéder au champ, spécifiez l’instance répétable à laquelle le champ appartient à l’aide de l’API `instances` dans `InstanceManager`. La syntaxe pour utiliser l’API `instances` dans`InstanceManager` est la suivante :
>
>
>`<panelName>.instanceManager.instances[<instanceNumber>].<fieldname>`
>
>
>Par exemple, vous créez un formulaire adaptatif avec un panneau répétable doté d’une zone de texte. Lorsque vous pré-remplissez le formulaire avec trois zones de texte répétables, le code xml ci-dessous est requis :
>
>
>`<panel1><textbox1>AA1</panel1></textbox1>`
>
>
>`<panel1><textbox1>AA2</panel1></textbox1>`
>
>
>`<panel1><textbox1>AA3</panel1></textbox1>`
>
>
>Pour lire les données AA1, spécifiez les paramètres suivants :
>
>
>`Panel1.instanceManager.instances[0].textbox.value`
>
>
>Pour lire les données AA2, spécifiez les paramètres suivants :
>
>
>`Panel1.instanceManager.instances[1].textbox.value`
>
>
>

<!-- 
>For more information, see: Class: InstanceManager#instances in [AEM Forms Java API reference](https://adobe.com/go/learn_aemforms_documentation_63).      
-->

>[!NOTE]
>
> Lorsque toutes les instances d’un panneau sont supprimées d’un formulaire adaptatif, pour ajouter une instance du panneau supprimé, utilisez la syntaxe _panelName pour capturer le gestionnaire d’instances du panneau et l’API addInstance du gestionnaire d’instances afin d’ajouter l’instance supprimée. Par exemple, _panelName.addInstance(). Elle ajoute une instance du panneau supprimé.

<!--
![panel-repeatability-video](/help/adaptive-forms/assets/panel-repeatability-video.mp4)
-->

<!--

## Using the accordion layout for the parent panel &nbsp; {#using-the-accordion-layout-for-the-parent-panel-nbsp}

A panel has various layouts options. The Layout for accordian design option has out of the box support for repeatable panels. Perform the following steps to repeatable panel with Layout for accordian design option:

1. On the parent of panel to be repeated, tap ![cmppr](assets/cmppr.png). You can see the properties in the sidebar. In the **Layout** drop-down, select **Accordion**.
1. On a panel, which is to be repeated, tap ![cmppr](assets/cmppr.png). You can see the panel properties in the sidebar. Enable the **Make Panel Repeatable** tab, and specify value for the **Maximum** and **Minimum** fields.

   Now, you can use the plus (+) and delete ( ![delete-panel](assets/delete-panel.png)) buttons to add and remove the panels.

-->

## Utilisation des sous-formulaires qui se répètent du modèle de formulaire (XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

Un sous-formulaire répétable est similaire aux panneaux répétables dans les formulaires adaptatifs. Dans AEM Forms Designer, suivez la procédure suivante pour créer un sous-formulaire qui se répète :

1. Dans la palette Hiérarchie, sélectionnez le sous-formulaire parent du sous-formulaire à répéter.
1. Dans la palette Objet, cliquez sur l’onglet Sous-formulaire et sélectionnez Distribué dans la liste Contenu.
1. Sélectionnez le sous-formulaire à répéter.
1. Dans la palette Objet, cliquez sur l’onglet Sous-formulaire et sélectionnez Positionné ou Distribué dans la liste Contenu.
1. Cliquez sur l’onglet Liaison et sélectionnez Sous-formulaire pour chaque élément.
1. Pour spécifier le nombre minimum de répétitions, sélectionnez Min. de répétitions et saisissez un nombre dans la zone associée. Si cette option est définie sur 0 et qu’aucune donnée n’est fournie pour les objets du sous-formulaire au moment de la fusion, le sous-formulaire n’est pas placé lors de la génération du formulaire.
1. Pour spécifier le nombre maximal de répétitions du sous-formulaire, sélectionnez Max. et saisissez un nombre dans la zone associée. Si vous n’indiquez pas de valeur dans la zone Max., le nombre de répétitions du sous-formulaire est illimité.
1. Pour spécifier un nombre précis de répétitions du sous-formulaire, quelle que soit la quantité de données, sélectionnez l’option Quantité initiale et tapez un nombre dans la zone associée. Si vous sélectionnez cette option et qu’aucune donnée n’est disponible ou qu’il existe moins d’entrées de données par rapport à la valeur Quantité initiale spécifiée, des instances vides du sous-formulaire sont toujours placées sur le formulaire.
1. Ajoutez deux boutons dans le sous-formulaire parent : un pour ajouter une instance et un autre pour supprimer une instance du sous-formulaire répétable. Pour obtenir des instructions détaillées, voir [Création d’une action](https://help.adobe.com/fr_FR/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2).
1. Maintenant, liez le modèle de formulaire au formulaire adaptatif. Pour obtenir des instructions détaillées, voir [Créer un formulaire adaptatif basé sur un modèle](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html?lang=en#create-an-adaptive-form-based-on-an-xfa-form-template).
1. Utilisez les boutons créés à l’étape 9 pour ajouter et supprimer des sous-formulaires.

Le fichier .zip joint contient un exemple de sous-formulaire répétable.

[Obtenir le fichier](/help/forms/assets/samplerepeatablesubform.zip)

## Utilisation des paramètres de répétition d’un schéma XML (XSD) {#using-repeat-settings-of-an-xml-schema-xsd-br}

Vous pouvez créer des panneaux répétables à partir d’un schéma XML et de la propriété minOccurs et maxOccurs de n’importe quel élément de type complexe. Pour plus d’informations sur le schéma XML, voir [Créer des formulaires adaptatifs à l’aide d’un schéma XML en tant que modèle de formulaire](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adaptive-form-xml-schema-form-model.html).

Dans le code suivant, le panneau`SampleType` utilise la propriété minOccurs &amp; maxOccurs.

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="https://adobe.com/sample.xsd"
                    xmlns="https://adobe.com/sample.xsd"
                    xmlns:xs="https://www.w3.org/2001/XMLSchema"
                >

        <xs:element name="sample" type="SampleType"/>

        <xs:complexType name="SampleType">
            <xs:sequence>
                <xs:element name="leaderName" type="xs:string" default="Enter Name"/>
                <xs:element name="assignmentStartDate" type="xs:date"/>
                <xs:element name="gender" type="GenderEnum"/>
                <xs:element name="noOfProjectsAssigned" type="IntType"/>
                <xs:element name="assignmentDetails" type="AssignmentDetails"
                                            minOccurs="0" maxOccurs="10"/>
            </xs:sequence>
        </xs:complexType>

        <xs:complexType name="AssignmentDetails">
            <xs:attribute name="name" type="xs:string" use="required"/>
            <xs:attribute name="durationOfAssignment" type="xs:unsignedInt" use="required"/>
            <xs:attribute name="numberOfMentees" type="xs:unsignedInt" use="required"/>
             <xs:attribute name="descriptionOfAssignment" type="xs:string" use="required"/>
             <xs:attribute name="financeRelatedProject" type="xs:boolean"/>
       </xs:complexType>
  <xs:simpleType name="IntType">
            <xs:restriction base="xs:int">
            </xs:restriction>
        </xs:simpleType>
  <xs:simpleType name="GenderEnum">
            <xs:restriction base="xs:string">
                <xs:enumeration value="Female"/>
                <xs:enumeration value="Male"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:schema>
```


## Articles connexes

* [Créer un formulaire adaptatif](creating-adaptive-form-core-components.md)
* [Créer un style ou des thèmes pour vos formulaires](using-themes-in-core-components.md)
* [Ajout d’un comportement dynamique aux formulaires à l’aide de l’éditeur de règles](rule-editor.md)
* [Définir la disposition des formulaires pour différentes tailles d’écran et différents types d’appareils](/help/sites-cloud/authoring/features/responsive-layout.md)