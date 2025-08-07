---
title: Comment créer des panneaux répétables dans les composants principaux de formulaire adaptatif ?
description: Découvrez comment créer une ou plusieurs sections répétables dans un formulaire adaptatif.
role: Architect, Developer, Admin, User
feature: Adaptive Forms, Core Components
exl-id: 02521bf3-83c1-40a0-8fe6-23af240727e9
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 92%

---

# Créer des formulaires avec des sections répétables (composants principaux) {#repeat-panel}


| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-forms-repeatable-sections.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

Une section répétable fait référence à une partie d’un formulaire qui peut être dupliquée ou répétée plusieurs fois afin de collecter des informations pour plusieurs instances des mêmes données.

Prenons l’exemple d’un formulaire utilisé pour collecter des informations sur l’expérience professionnelle d’une personne. Vous pouvez avoir une section répétable pour capturer les détails de chaque emploi précédent. La section répétable contient généralement des champs tels que le nom de l’entreprise, l’intitulé du poste, les dates de début et de fin d’emploi, et les responsabilités. La personne utilisatrice peut ajouter plusieurs instances de la section répétable pour saisir des informations sur chaque emploi qu’elle a effectué.

![Répétabilité](/help/forms/assets/repeatable-adaptive-form-example.gif)

À la fin de cet article, vous saurez :

* Création d’une section répétable dans un formulaire adaptatif
* définir le nombre minimal ou maximal de répétitions pour un composant de formulaire adaptatif ;
* utiliser l’éditeur de règles pour configurer les actions d’ajout ou de suppression pour les sections répétables

Vous pouvez utiliser les composants [Panneau](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel), [Accordéon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html#features?lang=fr), [Onglets horizontaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html#features?lang=fr), [Onglets verticaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) ou [Assistant](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html#features?lang=fr) pour rendre les sections d’un formulaire adaptatif répétables. Vous pouvez ajouter des composants enfants à ces composants pour créer une section répétable dans un formulaire.


Les exemples de ce document reposent sur le composant [Panneau](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel). Vous pouvez effectuer les mêmes étapes pour rendre les composants [Panneau](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel), [Accordéon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html#features?lang=fr), [Onglets horizontaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html#features?lang=fr), [Onglets verticaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) ou [Assistant](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html#features?lang=fr) répétables.

## Ajouter ou supprimer des sections répétables dans un formulaire {#add-or-delete-repeatable-section-in-panel-container}

Pour répéter un panneau dans le formulaire ou supprimer les panneaux répétables, un auteur ou une autrice de formulaire utilise un composant de bouton pour ajouter ou supprimer une instance du panneau. Pour ajouter ou supprimer des sections répétables (panneaux) dans un formulaire :

* [Activer la répétition du conteneur du panneau](#make-panel-container-repeatable)
* [Ajouter une section répétable](#add-repeatable-section-using-instance-manager-via-scripts)
* [Supprimer des sections répétables](#delete-repeatable-section-using-instance-manager-via-scripts)

### Activer la répétition du conteneur du panneau {#make-panel-container-repeatable}

![Onglet Accessibilité](/help/forms/assets/repeat-panel.png)

Pour activer la répétition d’un panneau, procédez comme suit :

1. Sélectionnez un conteneur de panneau et sélectionnez ![cmppr](/help/forms/assets/cmppr.png).
1. Cliquez sur **Répéter le panneau** et mettez le bouton (bascule) sur **Activer la répétition du panneau**.
1. Définissez les **répétitions minimales** comme requis pour les sections répétables minimales. Vous pouvez définir les **répétitions minimales** sur zéro pour ne pas répéter de panneaux ou pour supprimer les panneaux répétés. Par défaut, la valeur de répétition minimale est zéro.
1. Définissez les **répétitions maximales** pour répéter le panneau autant de fois que nécessaire. La valeur est par défaut infinie.

   >[!NOTE]
   >
   > 
   > * La répétition minimale ne peut pas être de valeur -ve.
   > * Pour créer un panneau non répétable, définissez la valeur des champs maximum et minimum sur 1.

### Ajouter une section répétable à l’aide du gestionnaire d’instances (via des scripts) {#add-repeatable-section-using-instance-manager-via-scripts}

Le parent du panneau à répéter doit contenir un bouton d’ajout pour gérer l’instance de répétition du panneau. Pour insérer des boutons dans le parent et activer des scripts sur les boutons, procédez comme suit :

1. Ajoutez un **composant de bouton** au parent du panneau. Dans la vidéo d’exemple ci-dessous, un composant de bouton avec le nom de libellé **Ajouter** et le nom de champ **AddPanel** est utilisé. Sélectionnez le composant, puis ![edit-rules](/help/forms/assets/edit-rules.png). Les règles du composant de bouton s’ouvrent dans l’éditeur de règles.
1. Dans la fenêtre Éditeur de règles, cliquez sur **Créer**.

   Sélectionnez **Éditeur visuel** dans la ligne Objets et fonctions de formulaire.

   1. Dans la zone de règle, sous QUAND, sélectionnez l’état **lorsque l’on clique dessus**.
   1. Sous ALORS, sélectionnez **Ajouter une instance** et glissez-déposez le panneau à l’aide de ![toggle-side-panel](/help/forms/assets/toggle-side-panel.png) ou sélectionnez-le à l’aide de l’option **Déposer l’objet ou sélectionner ici.**

   Sélectionnez **Éditeur de code** dans la ligne Objets et fonctions de formulaire. Cliquez sur **Modifier les règles** et dans la zone de code :

   * Pour créer un bouton d’ajout de panneau, spécifiez `this.panel.instanceManager.addInstance()`.

   Cliquez sur **Terminé**.

>[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)


### Supprimer des sections répétables à l’aide du gestionnaire d’instances (via des scripts) {#delete-repeatable-section-using-instance-manager-via-scripts}

Le parent du panneau doit contenir un bouton de suppression pour supprimer l’instance des panneaux répétables. Pour insérer des boutons dans le parent et activer des scripts sur les boutons pour supprimer les panneaux répétables, procédez comme suit :

1. Ajoutez un **composant de bouton** au parent du panneau. Dans la vidéo ci-dessous, un composant de bouton avec le nom de libellé **Supprimer** et le nom de champ **DeletePanel** est utilisé. Sélectionnez le composant, puis ![edit-rules](/help/forms/assets/edit-rules.png). Les règles du composant de bouton s’ouvrent dans l’éditeur de règles.
1. Dans la fenêtre Éditeur de règles, cliquez sur **Créer**.

   Sélectionnez **Éditeur visuel** dans la ligne Objets et fonctions de formulaire.

   1. Dans la zone de règle, sous QUAND **DeletePanel**, sélectionnez l’état **lorsque l’on clique dessus**.
   1. Sous ALORS, sélectionnez **Supprimer une instance**, et glissez-déposez le panneau à l’aide de ![toggle-side-panel](/help/forms/assets/toggle-side-panel.png) ou sélectionnez-le à l’aide de l’option **Déposer l’objet ou sélectionner ici.**

   Sélectionnez **Éditeur de code** dans la ligne Objets et fonctions de formulaire. Cliquez sur **Modifier les règles** et dans la zone de code :

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
>Par exemple, vous créez un formulaire adaptatif avec un panneau répétable contenant une zone de texte. Lorsque vous pré-remplissez le formulaire avec trois zones de texte répétables, le code xml ci-dessous est requis :
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

>[!NOTE]
>
> Lorsque toutes les instances d’un panneau sont supprimées d’un formulaire adaptatif, pour ajouter une instance du panneau supprimé, utilisez la syntaxe _panelName pour capturer le gestionnaire d’instances du panneau et l’API addInstance du gestionnaire d’instances pour ajouter l’instance supprimée. Par exemple, « _panelName.addInstance() ». Elle ajoute une instance du panneau supprimé.

## Utilisation des sous-formulaires qui se répètent du modèle de formulaire (XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

Un sous-formulaire répétable est similaire aux panneaux répétables dans les formulaires adaptatifs. Dans AEM Forms Designer, suivez la procédure suivante pour créer un sous-formulaire qui se répète :

1. Dans la palette Hiérarchie, sélectionner le sous-formulaire parent du sous-formulaire à répéter.
1. Dans la palette Objet, cliquez sur l’onglet Sous-formulaire et sélectionnez Distribué dans la liste Contenu.
1. Sélectionnez le sous-formulaire à répéter.
1. Dans la palette Objet, cliquez sur l’onglet Sous-formulaire et sélectionnez Positionné ou Distribué dans la liste Contenu.
1. Cliquez sur l’onglet Liaison et sélectionnez Sous-formulaire pour chaque élément.
1. Pour spécifier le nombre minimum de répétitions, sélectionnez Nombre minimum de répétitions et saisissez un nombre dans la zone associée. Si cette option est définie sur 0 et qu’aucune donnée n’est fournie pour les objets du sous-formulaire au moment de la fusion, le sous-formulaire n’est pas placé lors de la génération du formulaire.
1. Pour spécifier le nombre maximum de répétitions du sous-formulaire, sélectionnez Nombre maximum de répétitions et saisissez un nombre dans la zone associée. Si vous ne spécifiez aucune valeur dans la zone Nombre maximum, le nombre de répétitions du sous-formulaire est illimité.
1. Pour spécifier un nombre précis de répétitions du sous-formulaire, quelle que soit la quantité de données, sélectionnez l’option Quantité initiale et tapez un nombre dans la zone associée. Si vous sélectionnez cette option et qu’aucune donnée n’est disponible ou qu’il existe moins d’entrées de données par rapport à la valeur Quantité initiale spécifiée, des instances vides du sous-formulaire sont toujours placées sur le formulaire.
1. Ajoutez deux boutons dans le sous-formulaire parent : un pour ajouter une instance et un autre pour supprimer une instance du sous-formulaire répétable. Pour obtenir des instructions détaillées, voir [Création d’une action](https://help.adobe.com/fr_FR/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2).
1. Liez maintenant le modèle de formulaire au formulaire adaptatif. Pour les étapes détaillées, voir [Création d’un formulaire adaptatif basé sur un modèle](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html?lang=fr#create-an-adaptive-form-based-on-an-xfa-form-template).
1. Utilisez les boutons créés à l’étape 9 pour ajouter et supprimer des sous-formulaires.

Le fichier .zip joint contient un exemple de sous-formulaire répétable.

[Obtenir le fichier](/help/forms/assets/samplerepeatablesubform.zip)

## Utilisation des paramètres de répétition d’un schéma XML (XSD) {#using-repeat-settings-of-an-xml-schema-xsd-br}

Vous pouvez créer des panneaux répétables à partir d’un schéma XML et de la propriété minOccurs et maxOccurs de n’importe quel élément de type complexe. Pour des informations détaillées sur le schéma XML, voir [Création de formulaires adaptatifs à l’aide du schéma XML en tant que modèle de formulaire](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adaptive-form-xml-schema-form-model.html?lang=fr).

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


## Voir également {#see-also}

{{see-also}}

<!--

>[!MORELIKETHIS]
>
>* [Create an Adaptive Form](creating-adaptive-form-core-components.md)
>* [Create style or themes for your forms](using-themes-in-core-components.md)
>* [Add dynamic behavior to forms using the rule editor](rule-editor.md)
>* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/features/console-layout.md)

-->