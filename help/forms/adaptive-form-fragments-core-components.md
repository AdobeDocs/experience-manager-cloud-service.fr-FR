---
title: Que sont les fragments de formulaire adaptatif ?
description: Les formulaires adaptatifs fournissent un mécanisme permettant de créer un segment de formulaire, tel qu’un panneau ou un groupe de champs, utilisable dans tout formulaire adaptatif. Vous pouvez également enregistrer un panneau existant en tant que fragment.
topic-tags: author
keywords: Ajouter des fragments de formulaire adaptatif, fragments de formulaire adaptatif, Créer un fragment de formulaire, Ajouter un fragment à un formulaire adaptatif, Gérer des fragments
feature: Adaptive Forms, Core Components
exl-id: 3a9ad1b7-2f6f-4ca9-a1c9-549c4238c59e
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1355'
ht-degree: 80%

---

# Créer et utiliser des fragments de formulaires adaptatifs dans un formulaire adaptatif en fonction des composants principaux {#adaptive-form-fragments}


| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM as a Cloud Service (composants principaux) | Cet article |
| AEM as a Cloud Service (composants de base) | [Cliquez ici](/help/forms/adaptive-form-fragments.md) |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/adaptive-form-fragments.html?lang=fr) |

Bien que chaque formulaire soit conçu pour un rôle spécifique, certains segments sont communs à la plupart des formulaires, comme les informations personnelles telles que le nom et l’adresse, les informations relatives à la famille et aux revenus. Les développeurs et développeuses de formulaires doivent créer ces segments communs chaque fois qu’un nouveau formulaire est créé.

Les formulaires adaptatifs fournissent un mécanisme pratique pour créer un segment de formulaire, comme un panneau ou un groupe de champs, une seule fois et pour les réutiliser dans des formulaires adaptatifs. Ces segments réutilisables et autonomes s’appellent des fragments de formulaire adaptatif.

Les fragments de formulaire s’intègrent facilement à plusieurs formulaires, ce qui rationalise la création de formulaires cohérents et d’apparence professionnelle. Les fragments de formulaire assurent la réutilisation, la normalisation et la cohérence de la marque grâce à la fonctionnalité &quot;changer une fois et refléter partout&quot;. Expérimentez une plus grande maintenabilité et une plus grande efficacité, car les mises à jour effectuées à un emplacement donné sont automatiquement propagées à tous les formulaires qui utilisent ces fragments.

Vous pouvez ajouter un fragment plusieurs fois à un document et utiliser les propriétés de liaison de données de ses composants pour les lier à différentes sources de données ou différents schémas. Par exemple, vous pouvez utiliser le même fragment d’adresse pour les adresses permanentes, de communication et de facturation et le connecter à différents champs d’une source de données ou d’un schéma.

>[!NOTE]
>
> Vous pouvez facilement personnaliser votre expérience de fragment pour les personnes qui utilisent la [boîte de dialogue de configuration et la boîte de dialogue de conception d’un composant Fragment de formulaire](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/adaptive-form-fragment).

## Créer un fragment de formulaire adaptatif {#create-a-fragment}

Vous pouvez créer entièrement un fragment de formulaire adaptatif ou enregistrer un panneau dans un formulaire adaptatif existant en tant que fragment. Pour créer un fragment de formulaire :

1. Connectez-vous à votre instance de création d’AEM Forms à l’adresse https://[*nom_hôte*]:[*port*]/aem/forms.html.
1. Cliquez sur **Créer > Fragment de formulaire adaptatif**.

   ![Créer un fragment de formulaire adaptatif](/help/forms/assets/adaptive-form-fragment.png)

1. Indiquez le titre, le nom, la description et les balises du fragment. Assurez-vous de spécifier un nom unique pour le fragment. S’il existe déjà un autre fragment portant le même nom, la création du fragment échoue.
1. Sélectionnez un modèle de formulaire. Vous pouvez créer un fragment de formulaire pour le Forms adaptatif basé sur les composants principaux ou le Forms adaptatif basé sur les composants de base. Pour créer un fragment de formulaire pour les formulaires basés sur des composants principaux, sélectionnez un modèle basé sur des composants principaux.

   Lorsque vous créez un fragment de formulaire pour les formulaires basés sur des composants principaux, utilisez l’option Sélectionner un thème de formulaire pour sélectionner un thème basé sur des composants principaux.

1. Cliquez pour ouvrir l’onglet **Modèle de formulaire**, puis dans le menu déroulant **Choisir parmi**, sélectionnez l’un des modèles de fragment suivants :

   ![Affichage du type de modèle dans l’onglet Modèle de formulaire](assets/create-af-1-1.png)

   * **Aucun** : indique que le fragment doit être créé de zéro sans utiliser de modèle de formulaire.

     >[!NOTE]
     >
     > Dans les formulaires adaptatifs, vous pouvez utiliser plusieurs fois un fragment de formulaire unique (basé sur des composants principaux). Il prend en charge les fragments de formulaire basés sur des schémas et sans modèle.

   * **Schéma** : indique de créer un fragment à partir d’un schéma XML ou JSON chargé dans AEM Forms. Vous pouvez charger ou sélectionner l’un des schémas XML ou JSON comme modèle de formulaire pour le fragment. Lorsque vous sélectionnez un schéma XML, vous pouvez également créer un fragment de formulaire adaptatif en sélectionnant un type complexe présent dans le schéma sélectionné à partir de la liste déroulante **[!UICONTROL Type complexe de schéma XML]**. Lorsque vous sélectionnez un schéma JSON, vous pouvez également créer un fragment de formulaire adaptatif en sélectionnant une définition de schéma présente dans le schéma sélectionné à partir de la liste déroulante **[!UICONTROL Définitions de schéma JSON]**.
   * **Modèle de données de formulaire** : indique de créer le fragment à l’aide d’un modèle de données de formulaire (FDM). Vous pouvez créer un fragment de formulaire adaptatif basé sur un seul objet de modèle de données dans un modèle de données de formulaire (FDM). Développez la liste déroulante Définitions de modèle de données de formulaire (FDM) . Il répertorie tous les objets de modèle de données dans le modèle de données de formulaire spécifié (FDM). Sélectionnez un objet de modèle de données dans la liste.

   ![Modèle de données de formulaire (FDM)](assets/create-af-3.png)

1. Cliquez sur **Créer** puis sur **Ouvrir** pour ouvrir le fragment, avec un modèle par défaut, en mode d’édition. En mode d’édition, vous pouvez ajouter n’importe quel composant de formulaire adaptatif au fragment.

<!-- For information about Adaptive Form components, see [Introduction to authoring Adaptive Forms](../../forms/using/introduction-forms-authoring.md). --> En outre, si vous avez sélectionné un schéma XML comme modèle de formulaire pour votre fragment, un nouvel onglet affichant la hiérarchie des modèles de formulaire s’affiche dans l’outil de recherche de contenu. Il vous permet de faire glisser des éléments de modèle de formulaire sur le fragment. <!--The added form-model elements get converted into form components while retaining the original properties from the associated XDP or XSD. -->

Une fois le fragment de formulaire adaptatif basé sur un schéma ou un modèle de données de formulaire (FDM) créé, les éléments de modèle de données de formulaire (FDM) ou de schéma apparaissent dans l’onglet Sources de données du navigateur de contenu de l’éditeur de formulaire adaptatif. Vous pouvez glisser-déposer des éléments du modèle de formulaire sur le fragment. Les éléments de modèle de formulaire ajoutés sont convertis en composants de formulaire tout en conservant les propriétés d’origine du schéma associé.


## Ajouter un fragment à un formulaire adaptatif {#insert-a-fragment-in-an-adaptive-form}

Pour ajouter un fragment de formulaire adaptatif à un formulaire adaptatif, procédez comme suit :

1. Ouvrez le formulaire adaptatif en mode d’édition.
1. Ajoutez le composant **Fragment de formulaire adaptatif** au formulaire.
1. Ouvrez la boîte de dialogue Configuration du composant **Fragment de formulaire adaptatif** .
1. Sélectionnez la **référence au fragment** dans l’onglet **De base**. Tous les fragments de formulaires adaptatifs disponibles pour votre formulaire, selon le modèle du formulaire, s’affichent.

1. Sélectionnez un fragment de formulaire adaptatif sur le composant **Fragment de formulaire adaptatif** de votre formulaire adaptatif.

   ![Sélection de l’option Fragments de formulaire adaptatif](/help/forms/assets/adaptive-form-fragment-basic.png)

<!-- >[!NOTE]
   >
   >The Adaptive Form fragment is not enabled for authoring from within the Adaptive Form. Moreover, you cannot use an XSD-based fragment in a JSON-based Adaptive Form and the opposite way. -->

Le fragment de formulaire adaptatif est ajouté par référence au formulaire adaptatif et est synchronisé avec le fragment autonome du formulaire adaptatif. Cela signifie que toutes les modifications apportées au fragment de formulaire adaptatif sont répercutées dans toutes les instances où le fragment est incorporé dans les formulaires adaptatifs.

<!--### Embed a fragment in Adaptive Form {#embed-a-fragment-in-adaptive-form}

You can choose to embed an Adaptive Form fragment in an Adaptive Form by clicking the ![Embed](assets/Smock_Import_18_N.svg) icon the panel toolbar of the added fragment

The embedded fragment is no longer linked with the standalone fragment. You can edit the components in the embedded fragment from within the Adaptive Form.-->

<!-- 
## Configure fragment appearance {#configure-fragment-appearance}

Any fragment you insert in Adaptive Forms appears as a placeholder image. The placeholder displays titles of up to a maximum of ten child panels in the fragment. You can configure AEM Forms to show the complete fragment instead of the placeholder image.

Perform the following steps to show complete fragments in forms:

1. Go to AEM web console configuration page at https:[*host*]:[*port*]/system/console/configMgr.

1. Search and click **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** to open it in edit mode.
1. Disable **[!UICONTROL Enable Placeholder in place of Fragment]** checkbox to show complete fragments rather than the placeholder image.

-->

### Utilisation de fragments dans les fragments {#using-fragments-within-fragments}

Vous pouvez créer des fragments de formulaire adaptatif imbriqués, ce qui signifie que vous pouvez ajouter un fragment dans un autre fragment et avoir une structure de fragment imbriqué.

### Utiliser un fragment de formulaire plusieurs fois dans un formulaire adaptatif {#using-form-fragment-mutiple-times-in-af}

Vous pouvez utiliser plusieurs fois un fragment de formulaire basé sur un schéma et sans modèle dans un formulaire adaptatif pour enregistrer les données de manière unique pour chaque champ de fragment de formulaire. Par exemple, vous pouvez utiliser un fragment de formulaire d’adresse pour collecter les détails des adresses pour les adresses permanentes, les communications et les adresses actives présentes dans un formulaire de demande de prêt.

![Utiliser plusieurs fragments dans un formulaire adaptatif](/help/forms/assets/using-multiple-fragment-af.gif)

<!--

## Auto mapping of fragments for data binding {#auto-mapping-of-fragments-for-data-binding}

When you create an Adaptive Form fragment using an XFA form template or XSD complex type and drag-drop the fragment to an Adaptive Form, the XFA fragment or the XSD complex type is automatically replaced by the corresponding Adaptive Form fragment whose fragment model root is mapped to the XFA fragment or XSD complex Type.

You can change the fragment asset and its bindings from the Edit component dialog.

You can also drag-drop a bound Adaptive Form fragment from Adaptive Form Fragment library in AEM content finder and provide the correct bind reference from the Edit component dialog of the Adaptive Form fragment panel. -->

## Gérer les fragments {#manage-fragments}

Vous pouvez effectuer plusieurs opérations sur des fragments de formulaire adaptatif depuis l’interface utilisateur d’AEM Forms.

1. Accédez à `https://[hostname]/aem/forms.html`.

1. Cliquez sur **Sélectionner** dans la barre d’outils de l’interface utilisateur d’un AEM Forms et sélectionnez un fragment de formulaire adaptatif. La barre d’outils affiche les opérations suivantes que vous pouvez effectuer sur le fragment de formulaire adaptatif sélectionné.

<table>
 <tbody>
  <tr>
   <td><p><strong>Opération</strong></p> </td>
   <td><p><strong>Description</strong></p> </td>
  </tr>
  <tr>
   <td><p>Modifier</p> </td>
   <td><p>Ouvre le fragment de formulaire adaptatif sélectionné en mode d’édition.<br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>Prévisualisation</p> </td>
   <td><p>Fournit des options de prévisualisation du fragment en HTML ou un aperçu personnalisé en fusionnant les données d’un fichier XML avec le fragment. Pour plus d’informations, voir <a>Aperçu d’un formulaire</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Télécharger</p> </td>
   <td><p>Télécharge le fragment sélectionné.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Démarrage de la révision/Gestion de la révision</p> </td>
   <td><p>Permet de lancer et de gérer la révision du fragment sélectionné. Pour plus d’informations, voir <a>Créer et gérer des révisions</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Ajouter un dictionnaire</p> </td>
   <td><p>Génère un dictionnaire pour localiser le fragment sélectionné. Pour plus d’informations, voir <a>Localisation des formulaires adaptatifs</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Publier/Dépublier</p> </td>
   <td><p>Publie/annule la publication du fragment sélectionné.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Supprimer</p> </td>
   <td><p>Supprime le fragment sélectionné.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## Points essentiels à respecter lorsque vous utilisez des fragments {#key-points-to-remember-when-working-with-fragments}

* Assurez-vous que le nom du fragment est unique. La création du fragment échoue si un fragment portant le même nom existe déjà.
* Toute expression, tout script ou tout style d’un fragment de formulaire adaptatif autonome est conservé lorsqu’il est inséré par référence ou incorporé dans un formulaire adaptatif.
* Vous ne pouvez pas modifier un fragment de formulaire adaptatif, inséré par référence, au sein même d’un formulaire adaptatif. Pour modifier, modifiez le fragment de formulaire adaptatif autonome.
* Lorsque vous publiez un formulaire adaptatif, vous devez publier le fragment de formulaire adaptatif autonome inséré par référence dans le formulaire adaptatif.
* Lorsque vous publiez de nouveau un fragment de formulaire adaptatif mis à jour, les modifications sont répercutées dans les instances publiées du formulaire adaptatif dans lequel le fragment est utilisé.
* Le formulaire adaptatif contenant le composant Vérifier ne prend pas en charge les utilisateurs et utilisatrices anonymes. En outre, il n’est pas recommandé d’utiliser le composant Vérifier dans un fragment de formulaire adaptatif.

## Fragments de référence {#reference-fragments}

Les fragments de formulaire adaptatif de référence que vous pouvez utiliser pour créer votre formulaire sont disponibles.
<!-- For more information, see [Reference Fragments](../../forms/using/reference-adaptive-form-fragments.md). -->



## Voir également {#see-also}

{{see-also}}