---
title: Comment créer des formulaires avec des sections répétables ?
description: Découvrez comment créer des sections répétables dans un formulaire pouvant être ajouté ou supprimé dynamiquement dans un formulaire.
uuid: c3fa2aa4-a6b4-458e-8534-138e075290b1
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 01724ca0-6901-45e7-b045-f44814ed574e
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 60%

---


# Création de formulaires avec des sections répétables {#creating-forms-with-repeatable-sections}

Les sections répétables sont des panneaux qui peuvent être ajoutés ou supprimés dynamiquement dans un formulaire.

Par exemple, lors de la demande d’une tâche, le chercheur d’emploi fournit des détails sur la précédente tâche, tels que le nom de l’entreprise, le rôle, le projet et d’autres informations. L’information de tous les employeurs nécessite des sections différentes mais similaires. Dans un tel scénario, le formulaire d’embauche fournit une section employeur et fournit également une option pour ajouter dynamiquement d’autres sections de ce type. Ces sections dynamiquement ajoutées sont appelées sections répétables.

Pour créer des panneaux répétables, vous pouvez utiliser l’une des méthodes suivantes :

## Utilisation du gestionnaire d’instances via des scripts  {#using-instance-manager-via-scripts-nbsp}

1. En mode d’édition, sélectionnez un panneau, puis sélectionnez ![cmppr](assets/cmppr.png). Dans la barre latérale, sous Propriétés, activez **[!UICONTROL Activer la répétition du panneau]**. Spécifiez des valeurs pour les champs **[!UICONTROL Maximum]** et **[!UICONTROL Minimum.]**

   Le champ Maximum spécifie le nombre maximal de fois qu’un panneau peut apparaître sur la page. Vous pouvez spécifier -1 dans le champ Nombre maximum pour que le panneau s’affiche un nombre infini de fois.

   Le champ Minimum spécifie le nombre minimum de fois qu’un panneau s’affiche sur le formulaire. Si vous définissez le champ Nombre minimum sur zéro, vous pouvez ultérieurement supprimer toutes les instances via des scripts une fois le rendu terminé.

   >[!NOTE]
   >
   >Pour créer un panneau non répétable, définissez la valeur des champs Maximum et Minimum sur 1. La mise en page en accordéon ne prend pas en charge -1 dans le champ Nombre maximum . Vous pouvez spécifier un nombre élevé pour donner la notion de valeur infinie.

1. Le parent du panneau, qui doit être répété, doit contenir des boutons d’ajout et de suppression pour gérer les instances des panneaux répétables. Pour insérer des boutons dans le parent et activer des scripts sur les boutons, procédez comme suit :

   1. A partir de la barre latérale, faites glisser un composant Bouton jusqu’au parent du panneau. Sélectionnez le composant, puis sélectionnez ![edit-rules](assets/edit-rules.png). Les règles du bouton s’ouvrent dans l’éditeur de règles.
   1. Dans la fenêtre Éditeur de règles, cliquez sur **Créer**.

      Sélectionnez **Éditeur visuel** dans la ligne Objets et fonctions de formulaire.

      1. Dans la zone de règle, sous QUAND, sélectionnez l’état **lorsque l’on clique dessus**.
      1. Sous ALORS :

         * Pour créer un bouton d’ajout de panneau, sélectionnez **Ajouter une instance** et glissez-déposez le panneau à l’aide du ![panneau latéral](assets/toggle-side-panel.png) ou sélectionnez-le à l’aide de l’option **Déposer l’objet ou sélectionner ici.**
         * Pour créer un bouton de suppression de panneau, sélectionnez **Supprimer une instance**, et glissez-déposez le panneau à l’aide du ![panneau latéral](assets/toggle-side-panel.png) ou sélectionnez-le à l’aide de l’option **Déposer l’objet ou sélectionner ici**

      Sélectionnez **Éditeur de code** dans la ligne Objets et fonctions de formulaire. Cliquez sur **Modifier les règles** et dans la zone de code :

      * Pour créer un bouton d’ajout de panneau, spécifiez `this.panel.instanceManager.addInstance()`.
      * Pour créer un bouton de suppression de panneau, spécifiez `this.panel.instanceManager.removeInstance(this.panel.instanceIndex)`.

      Cliquez sur **Terminé**.

      >[!NOTE]
      >
      >Si un champ appartient à un panneau répétable, vous ne pouvez pas y accéder directement via son nom dans vos scripts. Pour accéder au champ, spécifiez l’instance répétable à laquelle le champ appartient à l’aide de l’API `instances` dans `InstanceManager`. La syntaxe pour utiliser l’API `instances` dans`InstanceManager` est la suivante :
      >
      >
      >`<panelName>.instanceManager.instances[<instanceNumber>].<fieldname>`
      >
      >
      >Vous pouvez par exemple créer un formulaire adaptatif avec un panneau répétable contenant une zone de texte. Lorsque vous pré-remplissez le formulaire avec trois zones de texte répétables, le code xml ci-dessous est requis :
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
      >Pour plus d’informations, voir : Class: InstanceManager#instances dans [Référence API Java pour AEM Forms](https://adobe.com/go/learn_aemforms_documentation_63_fr).

      >[!NOTE]
      >
      >Lorsque toutes les instances d’un panneau sont supprimées d’un formulaire adaptatif, pour ajouter une instance du panneau supprimé, utilisez la syntaxe _panelName pour capturer le gestionnaire d’instances du panneau et utilisez l’API addInstance du gestionnaire d’instances pour ajouter l’instance supprimée. Par exemple, _panelName.addInstance(). Elle ajoute une instance du panneau supprimé.

## Utilisation de la mise en page en accordéon pour le panneau parent  {#using-the-accordion-layout-for-the-parent-panel-nbsp}

Un panneau présente différentes options de disposition. La mise en page de l’option de conception en accordéon prend en charge les panneaux répétables. Effectuez les étapes suivantes pour créer un panneau répétable avec la mise en page de l’option de conception en accordéon :

1. Sur le parent du panneau à répéter, sélectionnez ![cmppr](assets/cmppr.png). Vous pouvez afficher les propriétés dans la barre latérale. Dans le menu déroulant **Disposition**, sélectionnez **Accordéon**.
1. Dans un panneau à répéter, sélectionnez ![cmppr](assets/cmppr.png). Vous pouvez afficher les propriétés dans la barre latérale. Activez la variable **Rendre le panneau répétable** et spécifiez les valeurs de la variable **Maximum** et **Minimum** des champs.

   Vous pouvez désormais utiliser les boutons plus (+) et Supprimer (![delete-panel](assets/delete-panel.png)) pour ajouter ou supprimer des panneaux.

## Utilisation des sous-formulaires qui se répètent du modèle de formulaire (XDP/XSD) {#using-repeating-subforms-from-form-template-xdp-xsd}

Un sous-formulaire répétable est similaire aux panneaux répétables dans les formulaires adaptatifs. Dans [!DNL AEM Forms] Designer, suivez la procédure suivante pour créer un sous-formulaire qui se répète :

1. Dans la palette Hiérarchie, sélectionnez le sous-formulaire parent du sous-formulaire à répéter.
1. Dans la palette Objet, cliquez sur l’onglet Sous-formulaire et sélectionnez Distribué dans la liste Contenu.
1. Sélectionnez le sous-formulaire à répéter.
1. Dans la palette Objet, cliquez sur l’onglet Sous-formulaire et sélectionnez Positionné ou Distribué dans la liste Contenu.
1. Cliquez sur l’onglet Liaison et sélectionnez Sous-formulaire pour chaque élément.
1. Pour spécifier le nombre minimum de répétitions, sélectionnez Nombre minimum de répétitions et saisissez un nombre dans la zone associée. Si cette option est définie sur 0 et qu’aucune donnée n’est fournie pour les objets du sous-formulaire au moment de la fusion des données, le sous-formulaire n’est pas placé lors de la génération du formulaire.
1. Pour spécifier le nombre maximum de répétitions du sous-formulaire, sélectionnez Nombre maximum de répétitions et saisissez un nombre dans la zone associée. Si vous n’indiquez pas de valeur dans la zone Nombre maximum de répétitions, le nombre de répétitions du sous-formulaire est illimité.
1. Pour spécifier un nombre précis de répétitions du sous-formulaire, quelle que soit la quantité de données, sélectionnez l’option Quantité initiale et tapez un nombre dans la zone associée. Si vous sélectionnez cette option et qu’aucune donnée n’est disponible ou qu’il existe moins d’entrées de données par rapport à la valeur Nombre initial spécifiée, des instances vides du sous-formulaire sont quand même placées sur le formulaire.
1. Ajoutez deux boutons dans le sous-formulaire parent : un pour ajouter une instance et un autre pour supprimer une instance d’un sous-formulaire répétable. Pour obtenir des instructions détaillées, voir [Création d’une action](https://help.adobe.com/fr_FR/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c74572b5612a87ca2b56-8000.2.html#WS107c29ade9134a2c-1f74d86012a87d4fe55-8000.2).
1. Liez maintenant le modèle de formulaire au formulaire adaptatif. Pour les étapes détaillées, voir [Création d’un formulaire adaptatif basé sur un modèle](creating-adaptive-form.md#create-an-adaptive-form-based-on-a-template).
1. Utilisez les boutons créés à l’étape 9 pour ajouter et supprimer des sous-formulaires.

Le fichier .zip joint contient un exemple de sous-formulaire répétable.

[Obtenir le fichier](assets/samplerepeatablesubform.zip)

## Utilisation des paramètres de répétition d’un schéma XML (XSD) {#using-repeat-settings-of-an-xml-schema-xsd-br}

Vous pouvez créer des panneaux répétables à partir d’un schéma XML et de la propriété minOccurs et maxOccurs de n’importe quel élément de type complexe. Pour des informations détaillées sur le schéma XML, voir [Création de formulaires adaptatifs à l’aide du schéma XML en tant que modèle de formulaire](adaptive-form-xml-schema-form-model.md).

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

>[!NOTE]
>
>Pour une mise en page sans accordéon, utilisez les composants de bouton Formulaire adaptatif pour ajouter et supprimer des instances.


>[!MORELIKETHIS]
>
>* [Création de formulaires avec des sections répétables dans les composants principaux de formulaire adaptatif](/help/forms/create-forms-repeatable-sections.md)