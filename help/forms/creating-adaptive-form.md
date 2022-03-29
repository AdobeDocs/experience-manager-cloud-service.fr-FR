---
title: Comment créer un formulaire adaptatif ?
description: 'Découvrez comment créer un formulaire adaptatif à l’aide de [!DNL Experience Manager Forms]. Les formulaires adaptatifs sont des formulaires HTML5 réactifs qui rationalisent la collecte et le traitement des informations. Découvrez comment créer un formulaire adaptatif basé sur un modèle de données de formulaire et un schéma XML ou JSON. '
feature: Adaptive Forms
role: User, Developer
level: Beginner
exl-id: 38ca5eea-793b-420b-ae60-3a0bd83caf00
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1500'
ht-degree: 100%

---

# Création d’un formulaire adaptatif {#creating-an-adaptive-form}

Les formulaires adaptatifs vous permettent de créer des formulaires attrayants, réactifs, dynamiques et adaptatifs. [!DNL AEM Forms] fournit une interface utilisateur intuitive et des composants prêts à l’emploi pour la création et l’utilisation de formulaires adaptatifs. Vous pouvez choisir de créer un formulaire adaptatif basé sur un modèle de formulaire ou un schéma ou sans modèle de formulaire. Il est important de choisir avec soin le modèle de formulaire qui convient non seulement à vos besoins, mais qui étend également vos investissements et vos ressources d’infrastructure existantes. Vous pouvez choisir parmi les options suivantes pour créer un formulaire adaptatif :

* **Utilisation d’un modèle de données de formulaire**
   L’[intégration de données](data-integration.md) vous permet d’intégrer des entités et des services provenant de sources de données disparates dans un modèle de données de formulaire que vous pouvez utiliser pour créer des formulaires adaptatifs. Choisissez le modèle de données de formulaire si le formulaire adaptatif que vous créez implique l’extraction et l’écriture de données depuis et vers plusieurs sources de données.

   <!--  * **Using an XDP Form Template**
   It is an ideal form model if you have investments in XFA-based or XDP forms. It provides a direct way to convert your XFA-based forms into Adaptive Forms. Any existing XFA rules are retained in the associated Adaptive Forms. The resulting Adaptive Forms support XFA constructs, such as validations, events, properties, and patterns. -->

* **Utilisation d’une définition de schéma XML (XSD) ou d’un schéma JSON**
Les schémas XML et JSON représentent la structure dans laquelle les données sont produites ou consommées par le système principal de votre entreprise. Vous pouvez associer le schéma à un formulaire adaptatif et utiliser ses éléments pour ajouter du contenu dynamique à un formulaire adaptatif. Les éléments du schéma peuvent être utilisés dans l’onglet Objets du modèle de données de l’explorateur de contenu lors de la création de formulaires adaptatifs.

* **Utilisation sans aucun modèle de formulaire**
Les formulaires adaptatifs créés avec cette option n’utilisent aucun modèle de formulaire. Les données XML générées à partir de ce type de formulaire présentent une structure plate avec des champs et des valeurs correspondantes.

## Conditions préalables

Pour créer un formulaire adaptatif, vous devez disposer des éléments suivants :

* Modèle de formulaire adaptatif. Un modèle fournit une structure de base et définit l’aspect, c’est-à-dire la mise en page et les styles, d’un formulaire adaptatif. Il comporte des composants préformatés contenant certaines propriétés et une structure de contenu. Vous pouvez [créer un nouveau modèle](template-editor.md), importer un modèle existant ou télécharger et importer des [modèles d’exemple](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:3f89abe1-0ece-492a-b5af-57c73badad52).
* Un thème de formulaire adaptatif. Un thème contient des détails de style pour les composants et les panneaux. Ces styles incluent les propriétés telles que les couleurs d’arrière-plan, les couleurs d’état, la transparence, l’alignement et la taille. Lorsque vous appliquez un thème, le style spécifié se reflète sur les composants correspondants. Vous pouvez [créer un nouveau thème](themes.md), [importer un thème existant](import-export-forms-templates.md#uploading-a-theme) ou télécharger et importer des [exemples de thèmes](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:2779f80e-16ba-4cd1-a96f-8e2b53f3be25).
* Ajoutez vos utilisateurs aux utilisateurs à [!DNL forms-users] pour leur fournir les autorisations de création d’un formulaire adaptatif. Pour obtenir la liste détaillée des groupes d’utilisateurs spécifiques aux formulaires, voir [Groupes et autorisations](forms-groups-privileges-tasks.md).

## Création d’un formulaire adaptatif {#strong-create-an-adaptive-form-strong}

Pour créer un formulaire adaptatif, suivez la procédure décrite ci-après.

1. Accédez à l’instance d’auteur [!DNL Experience Manager Forms]. Il peut s’agir d’une instance cloud ou d’une instance de développement local.

1. Entrez vos informations d’identification dans la page de connexion d’Experience Manager.

   Une fois connecté, dans le coin supérieur gauche, appuyez sur **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulaires]** > **[!UICONTROL Formulaires et documents.]**.

1. Appuyez sur **[!UICONTROL Créer]** et sélectionner **[!UICONTROL Formulaire adaptatif]**. Sélectionnez le modèle, puis appuyez sur **[!UICONTROL Suivant]**.
1. L’option **[!UICONTROL Ajouter des propriétés]** s’affiche. Spécifiez les valeurs des champs de propriété suivants. Les champs Titre et Nom sont obligatoires :

   * **[!UICONTROL Titre :]** spécifie le nom d’affichage du formulaire. Le titre vous permet d’identifier le formulaire dans l’interface utilisateur [!DNL Experience Manager Forms] d’AEM Forms.
   * **[!UICONTROL Nom :]** indique le nom du formulaire. Un nœud portant le nom indiqué est alors créé dans le référentiel. Lorsque vous commencez à saisir un titre, une valeur pour le champ de nom est automatiquement générée. Vous pouvez modifier la valeur suggérée. Le champ de nom peut contenir uniquement des caractères alphanumériques, des traits d’union et des tirets bas. Toutes les entrées non valides sont remplacées par un tiret.
   * **[!UICONTROL Description :]** indique des informations détaillées relatives au formulaire.
   * **[!UICONTROL Balises :]** indique les balises pour individualiser le formulaire adaptatif. Les balises aident à rechercher le formulaire. Pour créer des balises, saisissez les nouveaux noms de balise dans la boîte de dialogue **[!UICONTROL Balises.]**

1. Vous pouvez créer un formulaire adaptatif sur la base de l’un des modèles de formulaire suivants :

   * [Modèle de données de formulaire](#fdm)

   <!--* [XFA form template](#create-an-adaptive-form-based-on-an-xfa-form-template)-->
   * [Schéma XML ou JSON](#create-an-adaptive-form-based-on-xml-or-json-schema)
   * Aucun ou sans modèle de formulaire

   Vous pouvez configurer ces informations via l’onglet **[!UICONTROL Modèle de formulaire]** figurant sur la page **[!UICONTROL Ajouter des propriétés]**. Par défaut, le modèle de formulaire sélectionné est **[!UICONTROL Aucun]**.

1. Appuyez sur **[!UICONTROL Créer]**. Un formulaire adaptatif est créé et une boîte de dialogue pour ouvrir le formulaire à modifier s’affiche.

1. Appuyez sur **[!UICONTROL Ouvrir]** pour ouvrir le formulaire nouvellement créé dans un nouvel onglet. Le formulaire s’ouvre pour être modifié et affiche le contenu disponible dans le modèle. Il affiche également la barre latérale permettant de personnaliser le formulaire nouvellement créé selon vos besoins.

   En fonction du type de formulaire adaptatif, les éléments de formulaire présents dans le modèle de formulaire XFA, <!--XFA form template, -->le schéma XML ou JSON associé sont affichés dans l’onglet **[!UICONTROL Objets de modèle de données]** de l’**[!UICONTROL explorateur de contenu]** dans la barre latérale. Vous pouvez également faire glisser ces éléments pour créer votre formulaire adaptatif.

## Créer un formulaire adaptatif en fonction d’un modèle de données de formulaire {#fdm}

L’[intégration de données](data-integration.md) vous permet d’intégrer plusieurs sources de données et de rassembler leurs entités et services pour créer un modèle de données de formulaire. Il s’agit d’une extension du schéma JSON. Vous pouvez utiliser un modèle de données du formulaire pour créer un formulaire adaptatif. Les entités ou les objets de modèle de données configurés dans un modèle de données de formulaire sont disponibles en tant qu’objets de modèle de données pour la création de formulaire. Ils sont associés à des sources de données respectives et utilisés pour pré-remplir un formulaire et écrire les données envoyées dans les sources de données respectives. Vous pouvez également appeler des services configurés dans un modèle de données de formulaire à l’aide des règles de formulaire adaptatif.

Pour utiliser un modèle de données de formulaire pour créer un formulaire adaptatif :

1. Dans l’onglet Modèle de formulaire de l’écran Ajouter des propriétés, sélectionnez **[!UICONTROL Modèle de données de formulaire]** dans la liste déroulante **[!UICONTROL Choisir parmi]**.

   ![Création d’un formulaire adaptatif](assets/create-af-1-1.png)

1. Appuyez pour développer le **[!UICONTROL modèle de données de formulaire sélectionné]**. Tous les modèles de données de formulaire disponibles sont répertoriés. Sélectionnez un modèle de données.

>[!NOTE]
>
>Vous pouvez également remplacer le modèle de données de formulaire par un formulaire adaptatif. Pour obtenir des instructions détaillées, consultez la page [Modifier les propriétés du modèle de formulaire d’un formulaire adaptatif](#edit-form-model).

## Créer un formulaire adaptatif en fonction du schéma XML ou JSON {#create-an-adaptive-form-based-on-xml-or-json-schema}

Les schémas XML et JSON représentent la structure dans laquelle les données sont générées ou utilisées par le système principal de votre organisation. Vous pouvez associer un schéma à un formulaire adaptatif et utiliser ses éléments pour ajouter du contenu dynamique à un formulaire adaptatif. Les éléments du schéma sont disponibles dans l’onglet Objet du modèle de données du navigateur de contenu pour la création de formulaires adaptatifs. Vous pouvez faire glisser et déposer les éléments du schéma pour créer le formulaire.

Consultez les documents suivants pour découvrir comment concevoir un schéma XML ou JSON pour la création de formulaires adaptatifs.

* [Création de formulaires adaptatifs à l’aide d’un schéma XML](adaptive-form-xml-schema-form-model.md)
* [Création de formulaires adaptatifs à l’aide d’un schéma JSON](adaptive-form-json-schema-form-model.md)

Procédez comme suit pour utiliser un schéma XML ou JSON comme modèle de formulaire pour un formulaire adaptatif :

1. À l’étape **[!UICONTROL Ajouter des propriétés]** de la page de création de formulaire adaptatif, appuyez sur l’onglet **[!UICONTROL Modèle de formulaire]**.
1. Dans l’onglet Modèle de formulaire, sélectionnez **[!UICONTROL Schéma]** dans le champ déroulant **[!UICONTROL Choisir parmi]**.

1. Appuyez sur **[!UICONTROL Sélectionner le schéma]** et effectuez l’une des opérations suivantes :

   * **[!UICONTROL Télécharger à partir du disque]** : sélectionnez cette option et appuyez sur Charger une définition de schéma pour parcourir et charger un schéma XML ou un schéma JSON à partir de votre système de fichiers. Le fichier de schéma chargé se trouve avec le formulaire et n’est pas accessible aux autres formulaires adaptatifs.
   * **[!UICONTROL Recherche dans le référentiel]** : sélectionnez cette option pour effectuer une sélection dans la liste fichiers de définition de schéma disponibles dans le référentiel. Sélectionnez le fichier de schéma XML ou JSON comme modèle de formulaire. Le schéma sélectionné est associé au formulaire par référence et est accessible pour une utilisation dans d’autres formulaires adaptatifs.

      Assurez-vous que le nom du schéma JSON se termine par **.schema.json**. Par exemple : mySchema.schema.json
   ![Sélection du schéma XML ou JSON](assets/upload-schema.png)
   **Figure :** *Sélection d’un schéma XML ou JSON*

1. (Pour le schéma XML uniquement) Après avoir sélectionné ou chargé un schéma XML, spécifiez un élément racine du fichier XSD sélectionné à mapper avec le formulaire adaptatif.

   ![Sélection de l’élément racine de schéma XSD](assets/xsd-root-element.png)
   **Figure :** *Sélection de l’élément racine XSD*

>[!NOTE]
>
>Vous pouvez également remplacer le schéma par un formulaire adaptatif. Pour obtenir des instructions détaillées, consultez la page [Modifier les propriétés du modèle de formulaire d’un formulaire adaptatif](#edit-form-model).

## Modifier les propriétés du modèle de formulaire d’un formulaire adaptatif {#edit-form-model}

Les formulaires adaptatifs sont créés sans modèle de formulaire (en utilisant l’option Aucun pour le modèle de formulaire) ou en utilisant un modèle de formulaire tel qu’un schéma XML <!-- form template, --> ou JSON ou un modèle de données de formulaire. Vous pouvez remplacer le modèle de formulaire par un formulaire adaptatif en remplaçant Aucun par un autre modèle de formulaire. Pour un formulaire adaptatif basé sur un modèle de formulaire, vous pouvez choisir un autre schéma XML ou JSON, ou un autre modèle de données de formulaire <!-- form template,--> pour le même modèle de formulaire. Cependant, vous ne pouvez pas passer d’un modèle de formulaire à un autre.

1. Sélectionnez le document adaptatif et appuyez sur l’icône **Propriétés**.
1. Ouvrez l’onglet **[!UICONTROL Modèle de formulaire]** et effectuez l’une des actions suivantes.

   * Si le formulaire adaptatif ne dispose pas de modèle de formulaire, vous pouvez choisir un autre modèle de formulaire et, ensuite, sélectionner un <!-- a form template, -->schéma XML ou JSON, ou un modèle de formulaire.
   * Pour un formulaire adaptatif est basé sur un modèle de formulaire, vous pouvez choisir un autre<!-- form template, --> schéma XML ou JSON, ou un autre modèle de données de formulaire pour le même modèle de formulaire.

1. Appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer les propriétés.
