---
title: Comment gérer les métadonnées pour AEM Forms ?
description: Les métadonnées permettent de catégoriser et d’organiser plus facilement les ressources. Les utilisateurs peuvent ainsi retrouver aisément une ressource spécifique.
feature: Adaptive Forms, Foundation Components
exl-id: 8527246a-37f0-4d43-a49e-1c76c265514e
role: User, Developer
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '1735'
ht-degree: 95%

---

# Ajout, suppression ou modification des métadonnées d’un formulaire adaptatif {#manage-form-metadata}

>[!NOTE]
>
> Adobe recommande d’utiliser la capture de données moderne et extensible [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr) pour [créer un nouveau Forms adaptatif](/help/forms/creating-adaptive-form-core-components.md) ou [ajouter un Forms adaptatif aux pages AEM Sites](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Ces composants représentent une avancée significative dans la création de formulaires adaptatifs, ce qui garantit des expériences utilisateur impressionnantes. Cet article décrit une ancienne approche de création de Forms adaptatif à l’aide de composants de base.


| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/manage-form-metadata.html) |
| AEM as a Cloud Service | Cet article |

Les métadonnées permettent de catégoriser et d’organiser plus facilement les ressources. Les utilisateurs peuvent ainsi retrouver aisément une ressource spécifique.

Par défaut, [!DNL AEM Forms] fournit un ensemble défini de métadonnées pour chaque type de ressource. En plus des métadonnées par défaut, vous pouvez ajouter des métadonnées personnalisées à chaque type de ressources. [!DNL AEM Forms] permet également de créer, de gérer et d’échanger efficacement toutes ces métadonnées pour vos formulaires.

<!-- If you are a developer or a site owner, you can customize Forms Portal, the end-user interface for [!DNL AEM Forms] to reflect the metadata you are using in your organization. For more information abouts Forms Portal, see [Introduction to publishing forms on a portal](introduction-publishing-forms.md). -->

## Métadonnées dans [!DNL AEM Forms] {#metadata-in-aem-forms}

Dans [!DNL AEM Forms], la liste des propriétés de métadonnées associées à une ressource dépend du type de cette dernière. En outre, si vous ajoutez une propriété de métadonnées personnalisée, celle-ci est ajoutée pour toutes les ressources du même type.

### Types de ressources {#asset-types}

Les types de ressources suivants sont pris en charge dans [!DNL AEM Forms] :

* Modèles de formulaire (formulaires XFA)
* Formulaires PDF
* Document (PDF plats)
* Formulaires adaptatifs
* Modèle de données de formulaire
* XFS

#### Liste exhaustive de métadonnées {#extensive-list-of-metadata}

Vous trouverez ci-dessous une liste exhaustive des propriétés de métadonnées prises en charge dans [!DNL AEM Forms] :

<table>
 <tbody> 
  <tr> 
   <td><strong>Nom de la propriété</strong></td> 
   <td><strong>Type de ressource</strong></td> 
   <td><strong>Description</strong><br /> </td> 
  </tr> 
  <tr> 
   <td>Titre</td> 
   <td>Tous sauf la ressource</td> 
   <td>Nom d’affichage de la ressource.<br /> </td> 
  </tr> 
  <tr> 
   <td>Description</td> 
   <td>Tous sauf la ressource</td> 
   <td>Description. L’utilisateur ou utilisatrice peut spécifier cette valeur.<br /> </td> 
  </tr> 
  <tr> 
   <td>Type</td> 
   <td>Tous</td> 
   <td><p>Valeur en lecture seule spécifiant le type de ressource. Elle peut avoir l’une des valeurs suivantes :</p> 
    <ul> 
     <li>Modèle de formulaire</li> 
     <li>Formulaire PDF, formulaire PDF (Acroform) ou formulaire PDF (signé)</li> 
     <li>Document, document (signé)</li> 
     <li>Formulaire adaptatif</li> 
     <li>Modèle de données de formulaire (FDM)</li>
     <li>Ressource</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Créé</td> 
   <td>Tous</td> 
   <td>Valeur en lecture seule indiquant la date de création de la ressource.</td> 
  </tr> 
  <tr> 
   <td>Date de la dernière modification</td> 
   <td>Tous</td> 
   <td>Valeur en lecture seule indiquant l’heure de la dernière modification de la ressource.</td> 
  </tr> 
  <tr> 
   <td>Création</td> 
   <td>Tous sauf la ressource</td> 
   <td><p>Valeur en lecture seule qui est automatiquement calculée en fonction du type de formulaire.</p> 
    <ul> 
     <li>PDF/Modèle de formulaire/Document – extrait du fichier binaire téléchargé.</li> 
     <li>Formulaire adaptatif – utilisateur connecté au moment de la création du formulaire.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>État</td> 
   <td>Tous sauf la ressource</td> 
   <td><p> Valeur en lecture seule qui définit l’un des états suivants d’un formulaire :</p> 
    <ul> 
     <li>Aucune valeur : si un formulaire n’a jamais été publié.</li> 
     <li>Publié : lorsqu’un formulaire est publié.</li> 
     <li>Modifié : lorsqu’un formulaire a été modifié après avoir été publié une fois.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Date de dernière publication</td> 
   <td>Tous sauf la ressource</td> 
   <td>Valeur en lecture seule indiquant la date de dernière publication du formulaire.</td> 
  </tr> 
  <tr> 
   <td>Heure d’activation/de désactivation de la publication</td> 
   <td>Tous sauf la ressource</td> 
   <td><p>Heure à laquelle la publication/l’annulation de publication automatique du formulaire est planifiée. L’utilisateur ou utilisatrice définit cette valeur lors de la modification des métadonnées.</p> 
    <ul> 
     <li>L’heure d’activation et de désactivation de la publication doit être postérieure à la date actuelle. </li> 
     <li>La date d’annulation de la publication doit être antérieure à celle de la publication. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Envoyer l’URL</td> 
   <td><p>Modèle de formulaire</p> <p>Formulaire PDF</p> </td> 
   <td><p>Pour configurer une URL spécifiée par l’utilisateur ou utilisatrice afin d’envoyer des données de formulaire à un servlet.</p> <p>L’URL d’envoi peut être configurée à l’aide de l’une des méthodes suivantes, citées par ordre de priorité :</p> 
    <ul> 
     <li>Spécifiez une URL d’envoi directement dans un modèle de formulaire à l’aide du bouton Envoyer via HTTP lors de la création d’un formulaire XFA dans AEM Forms Designer.</li> 
     <li>Dans l’interface utilisateur AEM Forms, sélectionnez un formulaire et spécifiez une URL d’envoi lors de la modification des propriétés de métadonnées.</li> 
     <!-- <li>In Forms Portal, edit the Search &amp; Lister component and specify a submit URL under the Form Link tab.</li> -->
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Profil de rendu de HTML</td> 
   <td>Modèle de formulaire</td> 
   <td>Profil de rendu de HTML utilisé lors du rendu d’un modèle de formulaire au format HTML.</td> 
  </tr> 
  <tr> 
   <td>Format de rendu</td> 
   <td><p>Modèle de formulaire</p> <p>Formulaire adaptatif</p> </td> 
   <td><p>Cette option permet à l’utilisateur ou utilisatrice de spécifier le format de rendu du formulaire lors de la publication des formulaires :</p> 
    <ul> 
     <li>HTML</li> 
     <li>PDF</li> 
     <li>Les deux</li> 
    </ul> <p>Cette option est utilisée pour restreindre le format de rendu des formulaires uniquement sur le portail de formulaires où ils sont visibles par l’utilisateur.</p> </td> 
  </tr> 
  <tr> 
   <td>Balises</td> 
   <td>Tous sauf la ressource</td> 
   <td>Étiquettes associées au formulaire pour faciliter la recherche.</td> 
  </tr> 
  <tr> 
   <td>Références</td> 
   <td><p>Formulaire adaptatif</p> <p>Modèle de formulaire</p> <p>Ressource</p> </td> 
   <td><p>Liste des ressources (autres formulaires ou ressources) auxquelles ce formulaire est associé. Ces ressources peuvent appartenir à deux catégories :</p> 
    <ul> 
     <li>Fait référence : ressources auxquelles le formulaire actuel fait référence.</li> 
     <li>Référencée par : ressources qui font référence à la ressource actuelle.</li> 
    </ul> <p>Ces ressources sont affichées sous forme de liens et leurs métadonnées sont accessibles en cliquant dessus.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Sélection du modèle de formulaire (XDP/XSD)</td> 
   <td>Formulaire adaptatif</td> 
   <td><p>Indique quel modèle de formulaire est utilisé lors de la création du formulaire adaptatif. Cette propriété peut avoir les valeurs suivantes :</p> 
    <ul> 
      <li>Modèle de données de formulaire (FDM)</li>
      <li>Schéma : un code XML du schéma JSON</li>
     <!-- <li>Form template: A form template is selected from the ones existing in the repository. This value can be updated.</li> 
     <li>XML schema: An XSD file is uploaded. This value can be updated.</li> -->
     <li>Aucune</li> 
    </ul> 
    <div>
      Un modèle de formulaire sélectionné peut être mis à jour, mais pas supprimé. 
    </div> </td> 
  </tr> 
 </tbody> 
</table>

## Affichage des métadonnées de formulaire {#view-form-metadata}

Les ressources ont des valeurs de propriété existantes, qui peuvent être affichées en mode lecture seule. Ces métadonnées sont générées au moment du chargement ou de la création du formulaire.

1. Accédez à l’emplacement de la ressource pour laquelle vous souhaitez afficher les métadonnées.

1. Ouvrez la page de propriétés à l’aide de l’une des méthodes suivantes :

   * Cliquez sur l’icône **[!UICONTROL Propriétés]** ![Propriétés](assets/Smock_Info_18_N.svg) dans les actions rapides.

     >[!NOTE]
     >
     >Les actions rapides sont les éléments d’action qui s’affichent sur une vignette lorsque vous pointez dessus.

   * Sélectionnez le formulaire, puis cliquez sur l’icône **[!UICONTROL Propriétés]** ![Propriétés](assets/Smock_Info_18_N.svg) qui s’affiche dans la barre d’outils.
   * Accédez à la page des détails du formulaire en cliquant sur la vignette de celui-ci lorsque vous n’êtes pas en mode de sélection. Cliquez ensuite sur l’icône représentant un œil ![Propriétés](assets/Smock_Info_18_N.svg) en haut à droite, puis sur Propriétés dans la liste en dessous.

1. La page de propriétés qui s’ouvre affiche un schéma contenant uniquement les propriétés de métadonnées comportant des valeurs.

   <!-- The properties page has a toolbar containing two action icons:

    * Edit: ![Edit](assets/Smock_Edit_18_N.svg) Edit the metadata property values
    * View: ![aem6forms_eye_viewon](assets/aem6forms_eye_viewon.png) Navigate to the form details page, which opens the form in the preview mode. -->

   La section du contenu est divisée en deux parties :

   * Le panneau de gauche contient une vignette du formulaire.
   * Le panneau de droite contient les propriétés de métadonnées en mode lecture seule, réparties dans différents onglets.

## Ajout/mise à jour de valeurs de métadonnées de formulaire {#add-update-form-metadata-values}

Vous pouvez modifier les valeurs des propriétés de métadonnées existantes ou ajouter de nouvelles valeurs à un champ de propriété de métadonnées existant (par exemple, lorsqu’un champ de métadonnées est vide).

<!-- ### Update metadata property values {#update-metadata-property-values}

1. Follow the steps mentioned in the previous section to open the properties page where existing metadata of the selected form can be viewed.  

1. From the toolbar, click the Edit icon ![Edit](assets/Smock_Edit_18_N.svg) to change the mode of the page from read-only to read/write.  

1. The properties page that opens holds a schema that contains a mix of editable input fields and static text.  

1. The properties displayed in static text are the ones that you cannot edit.  

1. You can navigate to other tabs to find input fields for metadata properties placed under them.

   This page has a toolbar containing two action icons different from those in view mode:

    * Cancel: ![aem6forms_close](assets/aem6forms_close.svg_w24.png) Cancel any changes made to metadata property values so far
    * Done: ![aem6forms_check](assets/aem6forms_check.png) Save all the changes made to metadata property values so far

   Both these actions direct the user back to read-only mode of the properties page containing the updated values.-->

### Mise à jour de la vignette du formulaire {#update-the-form-thumbnail}

Dans la page de propriétés, le panneau de gauche affiche la vignette du formulaire. Par défaut, la vignette affichée est celle qui a été générée au moment de la création du formulaire (formulaire adaptatif) ou du téléchargement du formulaire.

Pour tous les types de formulaires, vous avez la possibilité de télécharger une image en cliquant sur **[!UICONTROL Télécharger l’image]** et en accédant à un fichier image dans le répertoire local. L’image sélectionnée remplace la vignette par défaut.

Pour les formulaires adaptatifs, les utilisateurs ont également la possibilité de générer une vignette en tant qu’instantané de l’aperçu du formulaire adaptatif actuel. Comme [!DNL AEM Forms] prend également en charge la création de formulaires adaptatifs, l’aperçu d’un formulaire adaptatif peut être modifié chaque fois que vous changez ce dernier. Cette possibilité de générer une vignette permet d’obtenir une vignette mise à jour du formulaire adaptatif selon l’état de l’aperçu actuel. Cliquez sur **[!UICONTROL Générer l’aperçu]** pour effectuer cette action.

>[!NOTE]
>
>* Utilisez une image carrée pour la vignette. Lorsque vous utilisez une image qui n’est pas carrée et affichez la miniature dans une vue Liste, la miniature apparaît tronquée.
>* Une fois qu’une nouvelle image est téléchargée ou générée, la vignette est remplacée par celle-ci et l’image précédente ne peut pas être rétablie.
>

## Ajout de métadonnées personnalisées {#add-custom-metadata}

Outre les métadonnées prêtes à l’emploi, [!DNL AEM Forms] prend en charge de nouvelles métadonnées personnalisées.

Un outil (l’éditeur de schéma de métadonnées) est proposé pour définir le schéma de la mise en page des métadonnées, c’est-à-dire la mise en page des élément de la page de **[!UICONTROL propriétés]** d’un formulaire. L’éditeur de schéma de métadonnées permet d’ajouter ou de modifier un schéma personnalisé pour vos ressources.

[!DNL AEM Forms] expose les schémas de métadonnées des types de formulaires pris en charge dans cet outil. Vous pouvez ainsi accéder à ces schémas et utiliser les fonctionnalités de l’éditeur de schéma de métadonnées pour ajouter des propriétés personnalisées.

### Navigation dans l’éditeur de schéma de métadonnées {#navigate-the-metadata-schema-editor}

1. Accédez à **[!UICONTROL Outils > Ressources > Schémas de métadonnées]**.

1. Cliquez sur **[!UICONTROL formulaires]** dans les formulaires de schéma répertoriés.

1. Dans la liste qui s’affiche, cliquez sur le type de ressource auquel vous souhaitez ajouter des métadonnées personnalisées.

   >[!NOTE]
   >
   >Ces schémas contiennent des propriétés de métadonnées prêtes à l’emploi qui ne doivent pas être modifiées (en cochant des cases ou en cliquant sur Modifier dans la barre d’outils) pour éviter tout problème fonctionnel.

1. Lorsque vous cliquez sur n’importe quel type de ressource, une liste contenant l’option `extendedmetadata` s’affiche. Modifiez ce schéma.

1. Cochez la case en regard de l’option `extendedmetadata`, puis cliquez sur l’icône ![Modifier](assets/Smock_Edit_18_N.svg) qui s’affiche dans la barre d’outils.

1. [!DNL AEM Forms] ouvre l’éditeur de schéma de métadonnées/le créateur de formulaires du type de ressource sélectionné (dans ce cas présent, du formulaire adaptatif).

   Éditeur de métadonnées

   1. Le panneau de gauche contient des sections à onglets où se trouvent les champs. Le panneau de droite affiche tous les composants d’IU disponibles et les propriétés du champ sélectionné dans le panneau de gauche.

   1. La section verrouillée n’est pas modifiable et contient les champs de toutes les propriétés de métadonnées prêtes à l’emploi.

   1. Vous pouvez ajouter d’autres onglets en cliquant sur le symbole +.

   1. Vous pouvez ajouter un champ personnalisé de type souhaité en faisant glisser le composant de champ de la section **[!UICONTROL Créateur de formulaires]** jusqu’à la page de schéma.
   1. Les caractéristiques de ce champ peuvent être affichées sous la section **[!UICONTROL Paramètres]** en cliquant dessus.

### Ajout d’une propriété de métadonnées personnalisée dans l’éditeur de schéma {#add-custom-metadata-property-in-schema-editor}

1. Accédez à l’onglet (nouveau ou existant) auquel vous souhaitez ajouter la propriété personnalisée.

1. Faites glisser un composant du type souhaité de la section **[!UICONTROL Créer le formulaire]** du panneau de gauche jusqu’à l’emplacement souhaité.

   >[!NOTE]
   >
   >Vous ne pouvez pas déplacer les sections verrouillées. Vous pouvez toutefois placer votre composant dans un des espaces vides.

1. Cliquez sur un composant que vous venez de déplacer. Dans l’onglet Paramètres qui s’affiche dans le panneau de droite, renseignez les champs suivants :

   1. Indiquez un libellé de champ à utiliser comme nom d’affichage au-dessus du champ placé dans le schéma (par exemple : Service)
   1. Sous le champ Associer à la propriété, vous pouvez voir une valeur préremplie **./jcr:content/metadata/default&#39;**. Remplacez « **default** » par le nom de propriété de votre choix, qui sera utilisé pour stocker la propriété dans le référentiel crx (par exemple, &#39;./jcr:content/metadata/department&#39;)

      >[!NOTE]
      >
      >Ne modifiez pas le préfixe &#39;./jcr:content/metadata/&#39; car il définit le chemin d’accès où la propriété est stockée.
      >
      >En outre, le nom de la propriété doit être unique pour éviter d’écrire des valeurs pour plusieurs propriétés au même emplacement dans le référentiel. Il est donc recommandé de modifier la valeur « default ».

   1. Remplissez les autres paramètres en fonction des besoins. Sélectionnez par exemple l’option Obligatoire si vous souhaitez que le champ soit obligatoire.
   1. Pour supprimer un champ que vous avez ajouté, sélectionnez-le, puis cliquez sur l’icône ![Supprimer](assets/Smock_Delete_18_N.svg).

1. Si nécessaire, suivez les étapes 1 à 3 pour ajouter une autre propriété.
1. Cliquez sur **[!UICONTROL Enregistrer]** après avoir effectué toutes les modifications.

   Vous venez d’ajouter une propriété de métadonnées personnalisée.

Tous les formulaires adaptatifs d’[!DNL AEM Forms] contiennent maintenant cette autre propriété de métadonnées. Vous pouvez la modifier dans la page de propriétés.


## Voir également {#see-also}

{{see-also}}