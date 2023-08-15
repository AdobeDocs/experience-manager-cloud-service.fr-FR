---
title: Comment utiliser un modèle de données de formulaire ?
description: Découvrez comment ajouter des services et des objets de modèle de données, créer des objets de modèle de données et des propriétés enfants. Apprenez également comment configurer des services, ajouter des associations et utiliser les propriétés de navigation des services OData. Découvrez comment générer et modifier des exemples de données, tester des services et des objets de modèle de données et automatiser la validation des données d’entrée.
feature: Form Data Model
role: User
level: Beginner, Intermediate
exl-id: c17c0443-d4dc-41f8-9315-6cc49e6c471f
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '4137'
ht-degree: 74%

---

# Utilisation d’un modèle de données de formulaire {#work-with-form-data-model}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/work-with-form-data-model.html?lang=fr) |
| AEM as a Cloud Service | Cet article |


![data-integration](do-not-localize/data-integeration.png)

L’éditeur de modèle de données de formulaire fournit une interface utilisateur intuitive et des outils d’édition et de configuration d’un modèle de données de formulaire. L’éditeur vous permet d’ajouter et de configurer des objets, des propriétés et des services de modèle de données à partir des sources de données disponibles dans le modèle de données de formulaire. En outre, il vous permet de créer des objets et des propriétés de modèle de données sans sources de données et de les lier ultérieurement aux objets et propriétés de modèle de données respectifs. Vous pouvez également générer et modifier des exemples de données pour les propriétés d’objet de modèle de données que vous pouvez utiliser pour préremplir des formulaires adaptatifs <!--and interactive communications--> lors de la prévisualisation. Vous pouvez tester les services et objets de modèle de données configurés dans un modèle de données de formulaire afin de vous assurer de leur intégration correcte aux sources de données.

Si vous êtes novice en intégration de données Forms et n’avez pas configuré de source de données ou créé de modèle de données de formulaire, consultez les rubriques suivantes :

* [Intégration de données [!DNL Experience Manager Forms]](data-integration.md)
* [Configuration des sources de données](configure-data-sources.md)
* [Création d’un modèle de données de formulaire](create-form-data-models.md)

Lisez la suite pour plus de détails sur les diverses tâches et configurations que vous pouvez effectuer à l’aide de l’éditeur de modèle de données de formulaire.

>[!NOTE]
>
>Vous devez être membre des deux groupes **fdm-author** et **forms-user** pour pouvoir créer et utiliser le modèle de données de formulaire. Contactez votre administrateur [!DNL Experience Manager] pour devenir membre des groupes.

## Ajout d’objets et de services de modèle de données {#add-data-model-objects-and-services}

Après avoir créé un modèle de données de formulaire et ajouté des sources de données, vous pouvez utiliser l’éditeur de modèle de données de formulaire pour ajouter des objets et des services de modèle de données, configurer leurs propriétés, créer des associations entre objets de modèle de données et tester le modèle et les services de données de formulaire.

Vous pouvez ajouter des objets et des services de modèle de données à partir des sources de données disponibles dans le modèle de données de formulaire. Tandis que les objets de modèle de données ajoutés apparaissent dans l’onglet Modèle, les services ajoutés apparaissent dans l’onglet Services.

Pour ajouter des objets et services de modèle de données :

1. Connectez-vous à l’instance d’auteur [!DNL Experience Manager], accédez à **[!UICONTROL Formulaires > Intégrations de données]** et ouvrez le modèle de données de formulaire dans lequel vous souhaitez ajouter des objets de modèle de données.
1. Dans le volet Sources de données, développez les sources de données pour afficher les objets et services de modèle de données disponibles.
1. Sélectionnez les objets et services de modèle de données que vous souhaitez ajouter au modèle de données de formulaire, puis appuyez sur **[!UICONTROL Ajouter la sélection]**.

   ![selected-objects](assets/selected-objects.png)

   Objets et services de modèle de données sélectionnés

   L’onglet **[!UICONTROL Modèle]** affiche une représentation graphique de tous les objets de modèle de données et de leurs propriétés ajoutées au modèle de données de formulaire. Chaque objet de modèle de données est représenté par une boîte dans le modèle de données de formulaire.

   ![model-tab](assets/model-tab.png)

   L’onglet **[!UICONTROL Modèle]** affiche les objets de modèle de données ajoutés

   >[!NOTE]
   >
   >Vous pouvez appuyer sur des zones d’objet de modèle de données et les faire glisser pour les organiser dans la zone de contenu. Tous les objets de modèle de données ajoutés dans le modèle de données de formulaire sont grisés dans le volet Sources de données.

   L’onglet **[!UICONTROL Services]** répertorie les services ajoutés.

   ![services-tab](assets/services-tab.png)

   L’onglet **[!UICONTROL Services]** affiche les services de modèle de données

   >[!NOTE]
   >
   >En plus des objets et services de modèle de données, le document de métadonnées de service OData inclut des propriétés de navigation qui définissent l’association entre deux objets de modèle de données. Pour plus d’informations, voir [Utilisation des propriétés de navigation des services OData](#work-with-navigation-properties-of-odata-services).

1. Appuyer **[!UICONTROL Enregistrer]** pour enregistrer l’objet de modèle de formulaire.

   >[!NOTE]
   >
   >Vous pouvez appeler les services que vous avez configurés dans l’onglet Services d’un modèle de données de formulaire à l’aide des règles de formulaire adaptatif. Les services configurés sont disponibles dans l’action Appeler les services de l’éditeur de règles. Pour plus d’informations sur l’utilisation de ces services dans des règles de formulaire adaptatif, voir les règles Appeler des services et Définir la valeur des règles dans l’[éditeur de règles](rule-editor.md).

## Création des objets de modèle de données et des propriétés enfant {#create-data-model-objects-and-child-properties}

### Création des objets de modèle de données {#create-data-model-objects}

Bien que vous puissiez ajouter des objets de modèle de données provenant de sources de données configurées, vous pouvez également créer des objets ou des entités de modèle de données sans sources de données. Cela s’avère particulièrement utile si vous n’avez pas configuré de sources de données dans le modèle de données de formulaire.

Pour créer un objet de modèle de données sans sources de données :

1. Connectez-vous à l’instance d’auteur [!DNL Experience Manager], accédez à **[!UICONTROL Formulaires > Intégrations de données]** et ouvrez le modèle de données de formulaire dans lequel vous souhaitez créer un objet ou une entité de modèle de données.
1. Appuyez sur **[!UICONTROL Créer une entité]**.
1. Dans la boîte de dialogue [!UICONTROL Créer un modèle de données de formulaire], spécifiez un nom pour l’objet de modèle de données de formulaire et appuyez sur **[!UICONTROL Ajouter]**. Un objet de modèle de données est ajouté au modèle de données de formulaire. L’objet de modèle de données ajouté n’est pas lié à une source de données et n’a aucune propriété comme indiqué dans l’image suivante.

   ![new-entity](assets/new-entity.png)

Vous pouvez ensuite ajouter des propriétés enfants dans les objets de modèle de données non liés.

### Ajout des propriétés enfant {#child-properties}

L’éditeur de modèle de données de formulaire vous permet de créer des propriétés enfants dans un objet de modèle de données. Une fois créée, la propriété n’est liée à aucune propriété d’une source de données. Vous pouvez ensuite lier la propriété enfant à une autre propriété dans l’objet de modèle de données conteneur.

Pour créer une propriété enfant :

1. Dans un modèle de données de formulaire, sélectionnez un objet de modèle de données et appuyez sur **[!UICONTROL Créer une propriété enfant]**.
1. Dans le **[!UICONTROL Créer une propriété enfant]** spécifiez un nom et un type de données pour la propriété dans la boîte de dialogue **[!UICONTROL Nom]** et **[!UICONTROL Type]** , respectivement. Vous pouvez éventuellement spécifier un titre et une description pour la propriété.
1. Activez Calculé si la propriété est une propriété calculée. La valeur d’une propriété calculée est évaluée en fonction d’une règle ou d’une expression. Pour plus d’informations, voir [Modifier les propriétés](#properties).
1. Si l’objet de modèle de données est lié à une source de données, la propriété enfant ajoutée est automatiquement liée à la propriété de l’objet de modèle de données parent portant le même nom et le même type de données.

   Pour lier manuellement une propriété enfant à une propriété d’objet de modèle de données, appuyez sur l’icône Parcourir en regard de la propriété **[!UICONTROL Référence de liaison]** champ . La boîte de dialogue **[!UICONTROL Sélection d’objet]** répertorie toutes les propriétés de l’objet modèle de données parent. Sélectionnez une propriété à lier et appuyez sur l’icône de coche. Notez que vous pouvez uniquement sélectionner une propriété du même type de données que la propriété enfant.

1. Appuyez sur **[!UICONTROL Terminé]** pour enregistrer la propriété enfant puis sur **[!UICONTROL Enregistrer]** pour enregistrer le modèle de données de formulaire. La propriété enfant est maintenant ajoutée à l’objet de modèle de données.

Après avoir créé des objets et des propriétés de modèle de données, vous pouvez continuer à créer des formulaires adaptatifs basés sur le modèle de données de formulaire <!--and interactive communications-->. Ultérieurement, lorsque des sources de données sont disponibles et configurées, vous pouvez lier le modèle de données de formulaire à des sources de données. La liaison est automatiquement mise à jour dans les formulaires adaptatifs <!--and interactive communications--> associés. Pour plus d’informations sur la création de formulaires adaptatifs <!--and interactive communications--> à l’aide du modèle de données de formulaire, consultez la section [Utilisation d’un modèle de données de formulaire](using-form-data-model.md).

### Liaison des objets et des propriétés de modèle de données {#bind-data-model-objects-and-properties}

Lorsque les sources de données que vous souhaitez intégrer au modèle de données de formulaire sont disponibles, vous pouvez les ajouter au modèle de données de formulaire, comme indiqué dans la section [Mise à jour des sources de données](create-form-data-models.md#update). Ensuite, procédez comme suit pour lier les objets et propriétés de modèle de données non liés :

1. Dans le modèle de données de formulaire, sélectionnez la source de données non liée à lier à une source de données.
1. Appuyez sur **[!UICONTROL Modifier les propriétés]**.
1. Dans le **[!UICONTROL Modifier les propriétés]** Appuyez sur l’icône de navigation en regard du volet **[!UICONTROL Liaison]** champ . Elle ouvre la fenêtre **[!UICONTROL Sélectionner un objet]** qui répertorie les sources de données ajoutées dans le modèle de données de formulaire.

   ![select-object](assets/select-object.png)

1. Développez l’arborescence des sources de données, sélectionnez un objet de modèle de données à lier et appuyez sur l’icône en forme de coche.
1. Appuyer **[!UICONTROL Terminé]** pour enregistrer les propriétés, puis appuyez sur **[!UICONTROL Enregistrer]** pour enregistrer le modèle de données de formulaire. L’objet de modèle de données est désormais lié à une source de données. Notez que l’objet de modèle de données n’est plus marqué comme Non lié.

   ![bound-model-object](assets/bound-model-object.png)

## Configuration des services {#configure-services}

Pour lire et écrire des données pour un objet de modèle de données, procédez comme suit pour configurer les services de lecture et d’écriture :

1. Cochez la case en haut d’un objet de modèle de données pour le sélectionner, puis appuyez sur **[!UICONTROL Modifier les propriétés]**.

   ![edit-properties](assets/edit-properties.png)

   Modification des propriétés pour configurer les services de lecture et d’écriture pour un objet de modèle de données

   La boîte de dialogue [!UICONTROL Modifier les propriétés] s’ouvre.

   ![edit-properties-2](assets/edit-properties-2.png)

   Boîte de dialogue Modifier les propriétés

   >[!NOTE]
   >
   >En plus des objets et services de modèle de données, le document de métadonnées de service OData inclut des propriétés de navigation qui définissent l’association entre deux objets de modèle de données. Lorsque vous ajoutez une source de données de service OData à un modèle de données de formulaire, un service est disponible dans le modèle de données de formulaire pour toutes les propriétés de navigation dans un objet de modèle de données. Vous pouvez utiliser ce service pour lire les propriétés de navigation de l’objet de modèle de données correspondant.
   >
   >
   >Pour plus d’informations sur l’utilisation du service, voir [Utilisation des propriétés de navigation des services OData](#work-with-navigation-properties-of-odata-services).

1. Basculer **[!UICONTROL Objet de niveau supérieur]** pour spécifier si l’objet de modèle de données est un objet de modèle de niveau supérieur.

   Les objets de modèle de données configurés dans un modèle de données de formulaire peuvent être utilisés dans l’onglet Objets de modèle de données de l’explorateur de contenu d’un formulaire adaptatif basé sur le modèle de données de formulaire. Lorsque vous ajoutez une association entre deux objets de modèle de données, l’objet de modèle de données à associer est imbriqué sous l’objet de modèle de données auquel vous l’associez dans l’onglet **[!UICONTROL Objets de modèle de données]**. Si le modèle de données imbriqué est un objet de niveau supérieur, il apparaît également séparément dans l’onglet **[!UICONTROL Objets de modèle de données]**. Par conséquent, vous en voyez deux entrées, l’une à l’intérieur et l’autre à l’extérieur de la hiérarchie imbriquée, ce qui pourrait perturber les auteurs de formulaires. Pour que l’objet de modèle de données associé apparaisse uniquement dans la hiérarchie imbriquée, désactivez la propriété Objet de niveau supérieur.

1. Sélectionnez Services de lecture et d’écriture pour les objets de modèle de données sélectionnés. Les arguments pour les services s’affichent.

   ![read-write-services](assets/read-write-services.png)

   Services de lecture et d’écriture configurés pour la source de données des employés

1. Appuyez sur ![aem_6_3_edit](assets/edit.svg) pour l’argument de service de lecture afin de [lier l’argument à une valeur Attribut du profil utilisateur, Attribut de requête ou Littéral](#bindargument) et spécifiez la valeur de liaison.
1. Appuyez sur **[!UICONTROL Terminé]** pour enregistrer l’argument, **[!UICONTROL Terminé]** pour enregistrer les propriétés, puis sur **[!UICONTROL Enregistrer]** pour enregistrer le modèle de données de formulaire.

### Liaison des arguments du service de lecture {#bindargument}

Liez l’argument du service de lecture à une valeur Attribut du profil utilisateur, Attribut de requête ou Littéral en fonction d’une valeur de liaison. La valeur est transmise au service en tant qu’argument pour récupérer les détails associés à la valeur spécifiée à partir de la source de données.

#### Valeur Littéral {#literal-value}

Sélectionnez **[!UICONTROL Littéral]** dans le menu déroulant **[!UICONTROL Liaison à]** et entrez une valeur dans le champ **[!UICONTROL Valeur de liaison]**. Les détails associés à la valeur sont récupérés à partir de la source de données. Utilisez cette option pour récupérer les détails associés à une valeur statique.

Dans cet exemple, les détails associés à **4367655678**, en tant que valeur de l’argument `mobilenum`, sont récupérés à partir de la source de données. Les détails associés, si vous transmettez la valeur d’un argument de numéro de mobile, peuvent inclure des propriétés telles que le nom du client, l’adresse du client et la ville.

![Valeur Littéral](assets/fdm_binding_literal_new.png)

#### Attribut du profil utilisateur {#user-profile-attribute}

Sélectionnez **[!UICONTROL Attribut du profil utilisateur]** dans le menu déroulant **[!UICONTROL Liaison à]** et saisissez le nom de l’attribut dans le champ **[!UICONTROL Valeur de liaison]**. Les détails de l’utilisateur connecté à l’instance [!DNL Experience Manager] sont récupérés à partir de la source de données en fonction du nom de l’attribut.

Le nom d’attribut spécifié dans le champ **[!UICONTROL Valeur de liaison]** doit inclure le chemin de liaison complet jusqu’au nom d’attribut de l’utilisateur. Ouvrez l’URL suivante pour accéder aux détails de l’utilisateur sur CRXDE :

`https://[server-name]:[port]/crx/de/index.jsp#/home/users/`

![Profil utilisateur](assets/binding_crxde_user_profile_new.png)

Dans cet exemple, spécifiez `profile.empid` dans le champ **[!UICONTROL Valeur de liaison]** de l’utilisateur `grios`.

![Modifier l’argument](assets/edit_argument_user_profile_new.png)

L’argument `id` prend la valeur de l’attribut `empid` du profil utilisateur et le transmet en tant qu’argument au service de lecture. Il lit et renvoie les valeurs des propriétés associées à partir de l’objet de modèle de données de l’employé pour le `empid` associé à l’utilisateur connecté.

#### Attribut de requête {#request-attribute}

Utilisez l’attribut de requête pour récupérer les propriétés associées à partir de la source de données.

1. Sélectionnez **[!UICONTROL Attribut de requête]** dans le menu déroulant **[!UICONTROL Liaison à]** et saisissez le nom de l’attribut dans le champ **[!UICONTROL Valeur de liaison]**.

1. Créez une [superposition](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/overlays.html?lang=fr#developing) pour head.jsp. Pour créer la superposition, ouvrez CRX DE et copiez le fichier `https://<server-name>:<port number>/crx/de/index.jsp#/libs/fd/af/components/page2/afStaticTemplatePage/head.jsp` dans `https://<server-name>:<port number>/crx/de/index.jsp#/apps/fd/af/components/page2/afStaticTemplatePage/head.jsp`

   >[!NOTE]
   >
   > * Si vous utilisez un modèle statique, superposez le fichier head.jsp à l’adresse suivante :
   >   `/libs/fd/af/components/page2/afStaticTemplatePage/head.jsp`
   > * Si vous utilisez un modèle modifiable, superposez le fichier aftemplatedpage.jsp à l’adresse suivante :
   >   `/libs/fd/af/components/page2/aftemplatedpage/aftemplatedpage.jsp`

1. Définissez [!DNL paramMap] pour l’attribut de requête. Par exemple, incluez le code suivant dans le fichier .jsp du dossier des applications :

   ```javascript
   <%Map paraMap = new HashMap();
    paraMap.put("<request_attribute>",request.getParameter("<request_attribute>"));
    request.setAttribute("paramMap",paraMap);
   ```

   Par exemple, utilisez le code ci-suivant pour récupérer la valeur de petid à partir de la source de données :


   ```javascript
   <%Map paraMap = new HashMap();
   paraMap.put("petId",request.getParameter("petId"));
   request.setAttribute("paramMap",paraMap);%>
   ```

Les détails sont récupérés à partir de la source de données en fonction du nom d’attribut spécifié dans la requête.

Par exemple, la spécification de l’attribut en tant que `petid=100` dans la requête extrait les propriétés associées à la valeur d’attribut de la source de données.

## Ajout des associations {#add-associations}

En règle générale, il existe des associations entre des objets de modèle de données dans une source de données. L’association peut lier un objet à un ou plusieurs objets. Par exemple, plusieurs personnes à charge peuvent être associées à un employé ou une employée. Il s’agit d’une association d’un objet à plusieurs objets, désignée par `1:n` sur la ligne reliant les objets de modèle de données associés. Toutefois, si une association renvoie un nom d’employé unique pour un ID d’employé donné, elle est appelée association un-à-un.

Lorsque vous ajoutez des objets de modèle de données associés d’une source de données à un modèle de données de formulaire, leurs associations sont conservées et affichées comme étant liées par des lignes fléchées. Vous pouvez ajouter des associations entre des objets de modèle de données sur des sources de données disparates dans un modèle de données de formulaire.

>[!NOTE]
>
>Les associations prédéfinies dans une source de données JDBC ne sont pas conservées dans le modèle de données de formulaire. Vous devez les créer manuellement.

Pour ajouter une association :

1. Cochez la case en haut d’un objet de modèle de données pour le sélectionner, puis appuyez sur **[!UICONTROL Ajouter une association]**. La boîte de dialogue Ajouter une association s’ouvre.

   ![ajouter-association](assets/add-association.png)

   >[!NOTE]
   >
   >En plus des objets et services de modèle de données, le document de métadonnées de service OData inclut des propriétés de navigation qui définissent l’association entre deux objets de modèle de données. Vous pouvez utiliser ces propriétés de navigation lors de l’ajout d’associations dans le modèle de données de formulaire. Pour plus d’informations, voir [Utilisation des propriétés de navigation des services OData](#work-with-navigation-properties-of-odata-services).

   La boîte de dialogue [!UICONTROL Ajouter une association] s’ouvre.

   ![add-association-2](assets/add-association-2.png)

   Boîte de dialogue Ajouter une association

1. Dans le volet Ajouter une association :

   * Spécifiez un titre pour l’association.
   * Sélectionnez le type d’association : **[!UICONTROL un à un]** ou **[!UICONTROL un à plusieurs]**.
   * Sélectionnez l’objet de modèle de données à associer.
   * Sélectionnez le service de lecture pour lire les données de l’objet de modèle sélectionné. L’argument de service de lecture s’affiche. Modifiez l’argument si nécessaire et liez-le à la propriété de l’objet de modèle de données à associer.

   Dans l’exemple suivant, l’argument par défaut pour le service de lecture de l’objet de modèle de données Personnes à charge est `dependentid`.

   ![add-association-example](assets/add-association-example.png)

   L’argument par défaut pour le service de lecture Personnes à charge est dependentid

   Toutefois, l’argument doit être une propriété commune entre l’objet de modèle de données associé, qui est `Employeeid` dans cet exemple. Par conséquent, l’argument `Employeeid` doit être lié à la propriété `id` de l’objet de modèle de données Employé pour extraire les détails des personnes à charge associés de l’objet de modèle de données Personnes à charge.

   ![add-association-example-2](assets/add-association-example-2.png)

   Argument et liaison mis à jour

   Appuyer **[!UICONTROL Terminé]** pour enregistrer l’argument .

1. Appuyer **[!UICONTROL Terminé]** pour enregistrer l’association, puis **[!UICONTROL Enregistrer]** pour enregistrer le modèle de données de formulaire.
1. Répétez les étapes pour créer d’autres associations selon les besoins.

>[!NOTE]
>
>L’association ajoutée apparaît dans la zone d’objet de modèle de données avec le titre spécifié et une ligne reliant les objets de modèle de données associés.
>
>Vous pouvez modifier une association en cochant la case correspondante et en appuyant sur **[!UICONTROL Modifier l’association]**.

![added-association](assets/added-association.png)

## Modification des propriétés {#properties}

Vous pouvez modifier les propriétés des objets de modèle de données, leurs propriétés et les services ajoutés dans le modèle de données de formulaire.

Pour modifier les propriétés :

1. Cochez la case en regard d’un objet de modèle de données, d’une propriété ou d’un service dans le modèle de données de formulaire.
1. Appuyez sur **[!UICONTROL Modifier les propriétés]**. La variable **[!UICONTROL Modifier les propriétés]** Le volet correspondant à l’objet de modèle, la propriété ou le service sélectionné s’ouvre.

   * **[!UICONTROL Objet de modèle de données]**: spécifiez les services de lecture et d’écriture et modifiez les arguments.
   * **[!UICONTROL Propriété]**: spécifiez le type, le sous-type et le format de la propriété. Vous pouvez également spécifier si la propriété sélectionnée est la clé primaire de l’objet de modèle de données.
   * **[!UICONTROL Service]**: spécifiez l’objet de modèle d’entrée, le type de sortie et les arguments du service. Pour un service Get, vous pouvez spécifier s’il doit renvoyer un tableau .

     ![edit-properties-service](assets/edit-properties-service.png)

   Boîte de dialogue Modifier les propriétés pour un service get

1. Appuyer **[!UICONTROL Terminé]** pour enregistrer les propriétés, puis **[!UICONTROL Enregistrer]** pour enregistrer le modèle de données de formulaire.

### Création des propriétés calculées {#computed}

Une propriété calculée est celle dont la valeur est calculée sur la base d’une règle ou d’une expression. À l’aide d’une règle, vous pouvez définir la valeur d’une propriété calculée sur une chaîne littérale, un nombre, le résultat d’une expression mathématique ou la valeur d’une autre propriété dans le modèle de données de formulaire.

Par exemple, vous pouvez créer une propriété calculée. **FullName** dont la valeur est le résultat d’une concaténation de la variable **FirstName** et **LastName** propriétés. Pour ce faire :

1. Créez une nouvelle propriété nommée `FullName` dont le type de données est Chaîne.
1. Activez **[!UICONTROL Calculé]** et appuyez sur **[!UICONTROL Terminé]** pour créer la propriété.

   ![calculé](assets/computed.png)

   La propriété calculée FullName est créée. Notez l’icône en regard de la propriété pour représenter une propriété calculée.

   ![prop-calculée](assets/computed-prop.png)

1. Sélectionnez la propriété FullName et appuyez sur **[!UICONTROL Modifier la règle]**. Une fenêtre Éditeur de règles s’ouvre.
1. Dans la fenêtre Éditeur de règles, cliquez sur **[!UICONTROL Créer]**. A **[!UICONTROL Définir la valeur]** s’ouvre.

   Dans la liste déroulante Sélectionner une option, sélectionnez **[!UICONTROL Expression mathématique]**. Les autres options disponibles sont **[!UICONTROL Objet de modèle de données de formulaire]** et **[!UICONTROL Chaîne]**.

1. Dans l’expression mathématique, sélectionnez **[!UICONTROL FirstName]** et **[!UICONTROL LastName]** dans les premier et deuxième objets, respectivement. Sélectionnez **[!UICONTROL plus]** en tant qu’opérateur.

   Appuyez sur **[!UICONTROL Terminé]** puis sur **[!UICONTROL Fermer]** pour fermer la fenêtre de l’éditeur de règles. La règle se présente comme suit :

   ![règle](assets/rule.png)

1. Sur le modèle de données de formulaire, appuyez sur **[!UICONTROL Enregistrer]**. La propriété calculée est configurée.

## Utilisation des propriétés de navigation des services OData {#work-with-navigation-properties-of-odata-services}

Dans les services OData, les propriétés de navigation sont utilisées pour définir des associations entre deux objets de modèle de données. Ces propriétés sont définies sur un type d’entité ou un type complexe. Par exemple, dans l’extrait suivant du fichier de métadonnées des exemples de services OData [TripPin](https://www.odata.org/blog/trippin-new-odata-v4-sample-service/), l’entité de personne contient trois propriétés de navigation : Friends, BestFriend et Trips.

Pour plus d’informations sur les propriétés de navigation, voir [Documentation OData](https://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part3-csdl/odata-v4.0-errata03-os-part3-csdl-complete.html#_Toc453752536).

```xml
<edmx:Edmx xmlns:edmx="https://docs.oasis-open.org/odata/ns/edmx" Version="4.0">
<script/>
<edmx:DataServices>
<Schema xmlns="https://docs.oasis-open.org/odata/ns/edm" Namespace="Microsoft.OData.Service.Sample.TrippinInMemory.Models">
<EntityType Name="Person">
<Key>
<PropertyRef Name="UserName"/>
</Key>
<Property Name="UserName" Type="Edm.String" Nullable="false"/>
<Property Name="FirstName" Type="Edm.String" Nullable="false"/>
<Property Name="LastName" Type="Edm.String"/>
<Property Name="MiddleName" Type="Edm.String"/>
<Property Name="Gender" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.PersonGender" Nullable="false"/>
<Property Name="Age" Type="Edm.Int64"/>
<Property Name="Emails" Type="Collection(Edm.String)"/>
<Property Name="AddressInfo" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Location)"/>
<Property Name="HomeAddress" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Location"/>
<Property Name="FavoriteFeature" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Feature" Nullable="false"/>
<Property Name="Features" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Feature)" Nullable="false"/>
<NavigationProperty Name="Friends" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Person)"/>
<NavigationProperty Name="BestFriend" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Person"/>
<NavigationProperty Name="Trips" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Trip)"/>
</EntityType>
```

Lorsque vous configurez un service OData dans un modèle de données de formulaire, toutes les propriétés de navigation d’un conteneur d’entités sont mises à disposition via un service dans le modèle de données de formulaire. Dans cet exemple de service ODP TripPin, les trois propriétés de navigation du conteneur d’entité `Person` peuvent être lues à l’aide d’un service `GET LINK` dans le modèle de données de formulaire.

Les éléments suivants mettent en évidence le service `GET LINK of Person /People` dans le modèle de données de formulaire, qui est un service combiné pour les trois propriétés de navigation dans l’entité `Person` du service TripPin OData.

![nav-prop-service](assets/nav-prop-service.png)

Une fois que vous avez ajouté le service `GET LINK` à l’onglet Modèle de données de formulaire, vous pouvez modifier les propriétés pour choisir l’objet de modèle de sortie et la propriété de navigation à utiliser dans le service. Par exemple, le service `GET LINK of Person /People` dans l’exemple suivant utilise Trip comme objet de modèle de sortie et la propriété de navigation Trips.

![edit-prop-nav-prop](assets/edit-prop-nav-prop.png)

>[!NOTE]
>
>Les valeurs disponibles dans le champ **[!UICONTROL Valeur par défaut]** de l’argument **NavigationPropertyName** dépendent de l’état du bouton bascule **[!UICONTROL Revenir au tableau ?Bouton bascule]**. Lorsqu’elle est activée, elle affiche les propriétés de navigation du type Collection.

Dans cet exemple, vous pouvez également choisir l’objet de modèle de sortie Person et l’argument de propriété de navigation Friends ou BestFriend (selon que **[!UICONTROL Revenir au tableau ?]** est activé ou désactivé).

![edit-prop-nav-prop2](assets/edit-prop-nav-prop2.png)

De même, vous pouvez choisir un service `GET LINK` et configurer ses propriétés de navigation lors de l’ajout d’associations dans le modèle de données de formulaire. Toutefois, pour pouvoir sélectionner une propriété de navigation, assurez-vous que le champ **[!UICONTROL Liaison à]** est défini sur **[!UICONTROL Littéral]**.

![add-association-nav-prop](assets/add-association-nav-prop.png)

## Génération et modification des exemples de données {#sample}

L’éditeur de modèle de données de formulaire vous permet de générer des données d’exemple pour toutes les propriétés d’objet de modèle de données, y compris les propriétés calculées, dans un modèle de données de formulaire. Il s’agit d’un ensemble de valeurs aléatoires conformes au type de données configuré pour chaque propriété. Vous pouvez également modifier et enregistrer des données qui sont conservées même si vous régénérez les données d’exemple.

Pour générer et modifier des exemples de données, procédez comme suit :

1. Ouvrez un modèle de données de formulaire et appuyez sur **[!UICONTROL Modifier les exemples de données]**. Cela génère et affiche les exemples de données dans la fenêtre Modifier les exemples de données.

   ![Génération des exemples de données](assets/form_data_model_generate_sample_data_new.png)

1. Dans la fenêtre **[!UICONTROL Modifier les exemples de données]**, modifiez les données selon les besoins puis appuyez sur **[!UICONTROL Enregistrer]**.

<!--Next, you can use the sample data to prefill and test interactive communications based on the form data model. For more information, see [Use form data model](using-form-data-model.md).-->

## Test des objets et des services de modèle de données {#test-data-model-objects-and-services}

Votre modèle de données de formulaire est configuré, mais avant de le mettre en service, vous pouvez vérifier si les objets et services de modèle de données configurés fonctionnent comme prévu. Pour tester les objets et les services de modèle de données :

1. Sélectionnez un objet ou service de modèle de données dans le modèle de données de formulaire et appuyez sur **[!UICONTROL Tester l’objet de modèle]** ou **[!UICONTROL Tester le service]**, respectivement.

   La fenêtre Tester le modèle de données de formulaire s’ouvre.

   ![test-data-model](assets/test-data-model.png)

1. Dans la fenêtre [!UICONTROL Tester le modèle de données de formulaire], sélectionnez l’objet ou le service de modèle de données à tester dans le volet de saisie.

1. Spécifiez une valeur d’argument dans le code de test et appuyez sur **[!UICONTROL Test]**. Un test réussi renvoie la sortie dans le volet Output (Sortie).

   ![Résultats du test](assets/test_results_form_data_model_new.png)

De même, vous pouvez tester d’autres objets et services de modèle de données dans le modèle de données de formulaire.

## Validation automatisée des données d’entrée {#automated-validation-of-input-data}

Le modèle de données de formulaire valide les données reçues en tant qu’entrées lors de l’appel de l’API DermisBridge (en fonction des critères de validation disponibles dans le modèle de données de formulaire). La validation est basée sur l’indicateur `ValidationOptions` défini dans l’objet de requête utilisé pour appeler l’API.

L’indicateur peut être défini sur l’une des valeurs suivantes :

* **FULL** : FDM effectue la validation en fonction de toutes les contraintes.
* **OFF** : aucune validation.
* **BASIC**: FDM effectue la validation en fonction des contraintes &quot;requises&quot; et &quot;nullable&quot;.

Si aucune valeur n’est définie pour l’indicateur `ValidationOptions`, la validation **BASIC** est effectuée sur les données d’entrée.

Voici un exemple de définition de l’indicateur de validation sur **FULL** :

```java
operationOptions.setValidationOptions(ValidationOptions.FULL);
```

>[!NOTE]
>
>La valeur que vous fournissez pour un attribut dans les données d’entrée doit correspondre au type de données défini pour l’attribut dans le document de métadonnées.\
>Si la valeur ne correspond pas au type de données défini pour l’attribut, l’API DermisBridge affiche une exception quelle que soit la valeur de l’indicateur `ValidationOptions`. Si le niveau de journal est défini sur Débogage, une erreur est consignée dans le fichier **error.log**.

Le modèle de données de formulaire valide les données d’entrée en fonction d’une liste de contraintes de type de données. La liste des contraintes pour les données d’entrée peut varier en fonction de la source de données.

Le tableau suivant répertorie les contraintes des données d’entrée en fonction de la source de données :

<table>
 <tbody> 
  <tr> 
   <td>Contraintes</td> 
   <td>Description</td> 
   <td>Source de données d’entrée</td> 
  </tr> 
  <tr> 
   <td>required</td> 
   <td>Si la valeur est true, le paramètre doit être inclus dans les données d’entrée.</td> 
   <td>Swagger, WSDL et base de données</td> 
  </tr> 
  <tr> 
   <td>nullable</td> 
   <td>Si la valeur est true, la valeur du paramètre peut être définie sur Null dans les données d’entrée.</td> 
   <td>WSDL, Odata et base de données</td> 
  </tr> 
  <tr> 
   <td>maximum</td> 
   <td>Spécifie la limite supérieure pour les valeurs numériques. La valeur maximale spécifiée comme limite supérieure peut également être affectée au paramètre dans les données d’entrée.</td> 
   <td>Swagger et WSDL</td> 
  </tr> 
  <tr> 
   <td>minimum</td> 
   <td>Définit la limite inférieure pour les valeurs numériques. La valeur minimale spécifiée comme limite inférieure peut également être affectée au paramètre dans les données d’entrée.</td> 
   <td>Swagger et WSDL</td> 
  </tr> 
  <tr> 
   <td>exclusiveMaximum</td> 
   <td>Spécifie la limite supérieure pour les valeurs numériques. La valeur maximale spécifiée comme limite supérieure ne doit pas être affectée au paramètre dans les données d’entrée.</td> 
   <td>Swagger et WSDL</td> 
  </tr> 
  <tr> 
   <td>exclusiveMinimum</td> 
   <td>Définit la limite inférieure pour les valeurs numériques. La valeur minimale spécifiée comme limite inférieure ne doit pas être affectée au paramètre dans les données d’entrée.</td> 
   <td>Swagger et WSDL</td> 
  </tr> 
  <tr> 
   <td>minLength</td> 
   <td>Indique la limite inférieure pour le nombre de caractères inclus dans une chaîne. La valeur minimale spécifiée comme limite inférieure peut également être affectée au paramètre dans les données d’entrée.</td> 
   <td>Swagger et WSDL</td> 
  </tr> 
  <tr> 
   <td>maxLength</td> 
   <td>Indique la limite supérieure pour le nombre de caractères inclus dans une chaîne. La valeur maximale spécifiée comme limite supérieure peut également être affectée au paramètre dans les données d’entrée.</td> 
   <td>Swagger, WSDL, Odata et base de données</td> 
  </tr> 
  <tr> 
   <td>pattern</td> 
   <td>Indique une séquence fixe de caractères. La chaîne d’entrée n’est validée avec succès que si les caractères sont conformes au modèle spécifié.</td> 
   <td>Swagger</td> 
  </tr> 
  <tr> 
   <td>minItems</td> 
   <td>Indique le nombre minimum d’éléments dans un tableau. La valeur minimale spécifiée comme limite inférieure peut également être affectée au paramètre dans les données d’entrée.</td> 
   <td>Swagger et WSDL</td> 
  </tr> 
  <tr> 
   <td>maxItems</td> 
   <td>Indique le nombre maximum d’éléments dans un tableau. La valeur maximale spécifiée comme limite supérieure peut également être affectée au paramètre dans les données d’entrée.</td> 
   <td>Swagger et WSDL</td> 
  </tr> 
  <tr> 
   <td>uniqueItems</td> 
   <td>Si la valeur est true, tous les éléments du tableau doivent être uniques dans les données d’entrée.</td> 
   <td>Swagger</td> 
  </tr> 
  <tr> 
   <td>enum (chaîne)<br /> <br /> </td> 
   <td>Limite la valeur d’un paramètre dans les données d’entrée à un ensemble fixe de valeurs de chaîne. Il doit s’agir d’un tableau contenant au moins un élément, où chaque élément est unique.</td> 
   <td>Swagger, WSDL et Odata</td> 
  </tr> 
  <tr> 
   <td>enum (nombre)<br /> <br /> </td> 
   <td>Limite la valeur d’un paramètre dans les données d’entrée à un ensemble fixe de valeurs numériques. Il doit s’agir d’un tableau contenant au moins un élément, où chaque élément est unique.</td> 
   <td>WSDL</td> 
  </tr> 
 </tbody> 
</table>

Dans cet exemple, les données d’entrée sont validées en fonction des contraintes maximales, minimales et requises définies dans le fichier Swagger. Les données d’entrée ne répondent aux critères de validation que si l’ID de commande est présent et que sa valeur est comprise entre 1 et 10.

```json
   parameters: [
   {
   name: "orderId",
   in: "path",
   description: "ID of pet that needs to be fetched",
   required: true,
   type: "integer",
   maximum: 10,
   minimum: 1,
   format: "int64"
   }
   ]
```

Une exception s’affiche si les données d’entrée ne répondent pas aux critères de validation. Si le niveau de journal est défini sur **Débogage**, une erreur est consignée dans le fichier **error.log**. Par exemple,

```verilog
21.01.2019 17:26:37.411 *ERROR* com.adobe.aem.dermis.core.validation.JsonSchemaValidator {"errorCode":"AEM-FDM-001-044","errorMessage":"Input validations failed during operation execution.","violations":{"/orderId":["numeric instance is greater than the required maximum (maximum: 10, found: 16)"]}}
```

## Étapes suivantes {#next-steps}

Vous disposez d’un modèle de données de formulaire fonctionnel pouvant à présent être utilisé dans les processus de formulaires adaptatifs <!--and interactive communications-->. Pour plus d’informations, reportez-vous à la section [Utilisation d’un modèle de données de formulaire](using-form-data-model.md).
