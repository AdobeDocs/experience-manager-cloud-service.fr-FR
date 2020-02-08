---
title: Création de contenu ciblé en mode Ciblage
description: Le mode Ciblage et le composant cible fournissent des outils permettant de créer du contenu pour les expériences.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Création de contenu ciblé en mode Ciblage {#authoring-targeted-content-using-targeting-mode}

Créez du contenu ciblé à l’aide du mode Ciblage d’AEM. Le mode Ciblage et le composant cible fournissent des outils pour créer du contenu pour les expériences :

* Identifiez facilement le contenu ciblé figurant dans la page. Une ligne pointillée forme une bordure autour de tout le contenu ciblé.
* Sélectionnez une marque et une activité pour afficher les expériences.
* Ajoutez des expériences à une activité ou supprimez des expériences.
* Effectuez des tests A/B et convertissez les gagnants (Adobe Target uniquement).
* Ajoutez des offres à une expérience en créant des offres ou en utilisant les offres d’une bibliothèque.
* Configurez les objectifs et les performances du moniteur.
* Simulez l’expérience utilisateur.
* Pour une personnalisation plus importante, configurez le composant cible.

Vous pouvez utiliser AEM ou Adobe Target comme moteur de ciblage (pour utiliser Adobe Target, vous devez disposer d’un compte Adobe Target valide). Si vous utilisez Adobe Target, vous devez commencer par configurer l’intégration. See the instructions for integrating with Adobe Target. <!--See the[instructions for integrating with Adobe Target](/help/sites-administering/target.md).-->

![Ciblage de contenu](/help/sites-cloud/authoring/assets/targeted-content.png)

The activities and experiences that you see in Target mode reflect the [Activities console](/help/sites-cloud/authoring/personalization/activities.md):

* Les modifications apportées aux activités et aux expériences en mode Ciblage se répercutent dans la console Activités.
* Les modifications apportées dans la console Activités se répercutent dans le mode Ciblage.

>[!NOTE]
>
>Lorsque vous créez une campagne dans Adobe Target, elle affecte la propriété `thirdPartyId` à chaque campagne. Lorsque vous supprimez la campagne dans Adobe Target, thirdPartyId n’est pas supprimé. Vous ne pouvez pas réutiliser la propriété `thirdPartyId` pour des campagnes de différents types (AB, XT) et elle ne peut pas être supprimée manuellement. Pour éviter ce problème, attribuez un nom unique à chaque campagne ; les noms de campagne ne peuvent donc pas être réutilisés dans différents types de campagne.
>
>Si vous utilisez le même nom dans le même type de campagne, vous remplacerez la campagne existante.
>
>Lors de la synchronisation, si le message d’erreur « Échec de la demande. `thirdPartyId` existe déjà » s’affiche, modifiez le nom de la campagne et resynchronisez-la.

>[!NOTE]
>
>Lors du ciblage, la combinaison de la marque et de l’activité est conservée au niveau de l’utilisateur, pas au niveau du canal.

## Passage en mode Ciblage {#switching-to-targeting-mode}

Passez en mode Cible pour accéder aux outils de création de contenu ciblé.

Pour passer en mode Cible :

1. Ouvrez la page pour laquelle vous souhaitez créer du contenu ciblé.
1. Dans la barre d’outils en haut de la page, cliquez ou appuyez sur le menu déroulant Mode pour afficher les types de mode disponibles.

   ![Mode Ciblage](/help/sites-cloud/authoring/assets/targeted-mode.png)

1. Cliquez ou appuyez sur **Ciblage**. Les options de ciblage s’affichent dans la partie supérieure de la page.

   ![Barre d’outils de ciblage](/help/sites-cloud/authoring/assets/targeted-toolbar.png)

## Ajout d’une activité à l’aide du mode Ciblage {#adding-an-activity-using-targeting-mode}

Utilisez le mode Ciblage pour ajouter une activité à une marque. Lorsque vous ajoutez une activité, elle contient l’expérience par défaut. Une fois que vous avez ajouté l’activité, vous commencez la procédure de ciblage de contenu de l’activité.

Vous pouvez également créer et gérer des activités Adobe Target à partir d’AEM avec l’option de sélection du moteur cible (AEM ou Adobe Target) et de sélection du type d’activité (ciblage de l’expérience ou test A/B).

De plus, vous pouvez gérer les objectifs et les mesures pour toutes les activités Adobe Target et gérer vos audiences Adobe Target. La création de rapports d’activité Adobe Target, y compris la conversion des gagnants, pour les tests A/B est également fournie.

Lorsque vous ajoutez une activité, elle s’affiche également dans la [console Activités](/help/sites-cloud/authoring/personalization/activities.md).

Pour ajouter une activité :

1. Utilisez le menu déroulant **Marque** pour sélectionner la marque pour laquelle vous souhaitez créer l’activité.

   >[!NOTE]
   >
   >Il est recommandé de [créer des marques via la console d’activités](/help/sites-cloud/authoring/personalization/activities.md#creating-a-brand-using-the-activities-console).
   >
   >
   >If you create a brand in any other way, make certain that the node `/campaigns/<brand>/master` exists or an error will result when you attempt to create an activity.

1. Cliquez ou appuyez sur « + » en regard du menu déroulant **Activité**.
1. Tapez le nom de l’activité.

   >[!NOTE]
   >
   >Lorsque vous créez une activité et qu’une configuration de cloud Adobe Target est associée à la page ou à une page parente, AEM considère automatiquement Adobe Target comme le moteur.

1. Dans le menu déroulant du moteur **Ciblage**, sélectionnez votre moteur de ciblage.

   * If you select **ContextHub AEM**, the remaining fields are dimmed and not available. Cliquez ou appuyez sur **Créer**.

   * Si vous sélectionnez **Adobe Target**, vous pouvez choisir une configuration (par défaut, il s’agit de celle définie lorsque vous avez configuré le compte) et un type d’activité. <!--If you select **Adobe Target**, you can select a configuration (by default, it is the configuration you provided when you [configured the account](/help/sites-administering/opt-in.md)) and Activity Type.-->

1. Dans le menu Activité, sélectionnez **Ciblage de l’expérience** ou **Test A/B**.

   * Ciblage de l’expérience : gérez les activités Adobe Target à partir d’AEM.
   * Test A/B : créez/gérez les activités de test A/B dans Adobe Target à partir d’AEM.

## Procédure de ciblage : création, ciblage et objectifs et paramètres {#the-targeting-process-create-target-and-goals-settings}

Le mode Ciblage permet de configurer plusieurs aspects d’une activité. Pour créer du contenu ciblé pour une activité de marque, utilisez la procédure en trois étapes ci-dessous :

1. [Créer](#create-authoring-the-experiences) : ajoutez ou supprimez des expériences et ajoutez des offres pour chaque expérience.
1. [Cible](#target-configuring-the-audiences) : spécifiez l’audience ciblée par les différentes expériences. Vous pouvez cibler une audience spécifique et, si vous utilisez un test A/B, déterminer le pourcentage de trafic dirigé vers une expérience.
1. [Objectifs et paramètres](#goals-settings-configuring-the-activity-and-setting-goals) : planifiez l’activité et définissez la priorité. Vous pouvez également définir des objectifs de mesures de réussite.

Utilisez la procédure ci-dessous pour commencer la procédure de ciblage du contenu pour une activité.

>[!NOTE]
>
>Pour utiliser le processus de ciblage, vous devez être membre du groupe d’utilisateurs Auteurs d’activités Target.

Pour ajouter une activité :

1. Dans le menu déroulant **Marque**, sélectionnez la marque qui contient l’activité sur laquelle vous travaillez.
1. Dans le menu déroulant **Activité**, sélectionnez l’activité pour laquelle vous créez du contenu ciblé.
1. Pour afficher les options qui vous guident lors de la procédure de ciblage, cliquez ou appuyez sur **Commencer le ciblage**.

   ![Commencer le ciblage](/help/sites-cloud/authoring/assets/targeted-start-targeting.png)

   >[!NOTE]
   >
   >Pour modifier l’activité que vous utilisez, cliquez ou appuyez sur **Précédent**.

## Créer : création d’expériences {#create-authoring-the-experiences}

L’étape Créer du ciblage de contenu consiste à créer des expériences. Au cours de cette étape, vous pouvez créer ou supprimer les expériences de l’activité et ajouter des offres à chaque expérience.

### Affichage des offres d’expérience en mode Ciblage {#seeing-experience-offers-in-targeting-mode}

Après avoir [commencé la procédure de ciblage](#the-targeting-process-create-target-and-goals-settings), sélectionnez une expérience pour afficher les offres disponibles pour cette expérience. Lorsque vous sélectionnez une expérience, les composants ciblés dans la page changent de manière à afficher l’offre concernant cette expérience.

>[!CAUTION]
>
>Soyez prudent lorsque vous désactivez le ciblage d’un composant déjà ciblé dans l’instance d’auteur. L’activité correspondante sera automatiquement supprimée de l’instance de publication.

>[!NOTE]
>
>Une offre est le contenu d’un composant ciblé.

Les expériences sont affichées dans le volet Audiences. In the following example, experiences include **Default**, **Female**, **Female over 30**, and **Female under 30**. Cet exemple affiche l’offre Par défaut d’un composant **Image** ciblé.

![Composant d’image ciblé](/help/sites-cloud/authoring/assets/targeted-image-component.png)

Lorsqu’une autre expérience est sélectionnée, le composant Image affiche l’offre concernant cette expérience.

![Composant d’image ciblé modifié](/help/sites-cloud/authoring/assets/targeted-image-different.png)

Lorsqu’une expérience est sélectionnée et que le composant ciblé ne comporte pas d’offre pour cette expérience, le composant affiche la mention **Ajouter une offre** superposée sur l’offre Par défaut en semi-transparence. Lorsqu’aucune offre n’a été créée pour une expérience, l’offre **Par défaut** s’affiche pour le segment mappé sur l’expérience.

![Ajouter une offre](/help/sites-cloud/authoring/assets/targeted-add-offer.png)

L’expérience par défaut s’affiche également si les propriétés du visiteur ne correspondent à aucun segment mappé sur les expériences. See [Adding Experiences using Targeting Mode](#adding-and-removing-experiences-using-targeting-mode).

### Offres personnalisées et offres de bibliothèque {#custom-offers-and-library-offers}

Les offres qui sont [créées dans la page](#adding-a-custom-offer) et utilisées pour une seule expérience sont des « offres personnalisées ». L’image ci-dessous est superposée sur le contenu d’une offre personnalisée :

![Icône d’offre personnalisée](/help/sites-cloud/authoring/assets/targeted-custom-offer-icon.png)

Les offres [ajoutées à partir d’une bibliothèque d’offres](#adding-an-offer-from-an-offer-library) sont superposées sur l’image suivante :

![Icône d’offre de bibliothèque](/help/sites-cloud/authoring/assets/targeted-library-offer-icon.png)

Vous pouvez enregistrer des offres personnalisées à une bibliothèque d’offres si vous estimez que vous êtes susceptible de les réutiliser. Vous pouvez également convertir une offre de bibliothèque en offre personnalisée si vous souhaitez modifier le contenu d’une expérience. Après la modification, vous pouvez réenregistrer l’offre dans la bibliothèque.

### Ajout et suppression d’expériences à l’aide du mode Ciblage {#adding-and-removing-experiences-using-targeting-mode}

À l’aide de l’étape Créer de la [procédure de ciblage](#the-targeting-process-create-target-and-goals-settings), vous pouvez ajouter et supprimer des expériences. Vous pouvez également dupliquer une expérience et la renommer.

#### Ajout d’expériences à l’aide du mode Ciblage {#adding-experiences-using-targeting-mode}

Pour ajouter une expérience :

1. To add an experience, click or tap **+** **Add Experience Targeting **that appears below existing experiences in the **Audiences** pane.
1. Sélectionnez une audience. Par défaut, ce nom est le nom de l’expérience. Vous pouvez entrer un autre nom, si vous le souhaitez. Cliquez ou appuyez sur **OK**.

#### Suppression d’expériences à l’aide du mode Ciblage {#removing-experiences-using-targeting-mode}

Pour supprimer une expérience :

1. Cliquez ou appuyez sur la flèche en regard du nom de l’expérience.

   ![Suppression et expérience](/help/sites-cloud/authoring/assets/targeted-delete-experiene.png)

1. Cliquez sur **Supprimer**.

#### Attribution d’un nouveau nom à des expériences à l’aide du mode Ciblage {#renaming-experiences-using-targeting-mode}

Pour renommer des expériences à l’aide du mode Ciblage :

1. Cliquez ou appuyez sur la flèche en regard du nom de l’expérience.
1. Click **Rename Experience** and type in the new name.
1. Cliquez ou appuyez sur un autre emplacement de l’écran pour enregistrer les modifications.

#### Modification des audiences à l’aide du mode Ciblage {#editing-audiences-using-targeting-mode}

Pour modifier les audiences à l’aide du mode Ciblage :

1. Cliquez ou appuyez sur la flèche en regard du nom de l’expérience.
1. Click **Edit Audience** and select a new audience.
1. Cliquez sur **OK**.

#### Duplication d’expériences à l’aide du mode Ciblage {#duplicating-experiences-using-targeting-mode}

Pour copier des expériences à l’aide du mode Ciblage :

1. Cliquez ou appuyez sur la flèche en regard du nom de l’expérience.
1. Cliquez sur **Dupliquer** et sélectionnez l’audience.
1. Renommez l’expérience, si vous le souhaitez, puis cliquez sur **OK**.

### Création d’offres à l’aide du mode Ciblage {#creating-offers-using-targeting-mode}

Ciblez un composant pour créer des offres pour les expériences. Les composants ciblés fournissent le contenu utilisé comme offres pour les expériences.

* [Ciblez un composant existant](#creating-a-default-offer-by-targeting-an-existing-component). Le contenu devient l’offre de l’expérience par défaut.
* [Ajoutez un composant cible](#creating-an-offer-by-adding-a-target-component), puis ajoutez du contenu au composant.

Une fois qu’un composant est ciblé, vous pouvez ajouter des offres pour chaque expérience :

* [Ajoutez des offres personnalisées](#adding-a-custom-offer).
* [Ajoutez des offres d’une bibliothèque](#adding-an-offer-from-an-offer-library).

Les outils ci-dessous sont disponibles pour l’utilisation d’offres :

* [Ajoutez une offre personnalisée à une bibliothèque d’offres](#adding-a-custom-offer-to-a-library).
* [Convertissez une offre de bibliothèque en offre personnalisée](#converting-a-library-offer-to-a-custom-library).
* [Ouvrez une offre de bibliothèque et modifiez son contenu](#editing-a-library-offer).

#### Création d’une offre par défaut à l’aide d’un composant Ciblage existant {#creating-a-default-offer-by-targeting-an-existing-component}

Ciblez un composant dans la page pour l’utiliser comme offre pour l’expérience par défaut de l’activité. Lorsque vous ciblez un composant, il est enveloppé dans un composant cible et son contenu devient l’offre de l’expérience par défaut.

Si vous ciblez un composant, seul ce composant peut être utilisé dans l’offre. Vous ne pouvez pas supprimer le composant de l’offre ou ajouter d’autres composants à l’offre.

Suivez la procédure ci-dessous après [avoir commencé la procédure de ciblage](#the-targeting-process-create-target-and-goals-settings).

1. Cliquez ou appuyez sur le composant à cibler. La barre d’outils du composant s’affiche, comme indiqué sur l’exemple suivant.

   ![Composant ciblé](/help/sites-cloud/authoring/assets/targeted-component.png)

1. Cliquez ou appuyez sur l’icône Cible.

   ![Bouton Cible](/help/sites-cloud/authoring/assets/targeted-target-button.png)

   Le contenu du composant est l’offre de l’expérience par défaut. Lorsqu’un composant est ciblé, son nœud par défaut sera répliqué pour chaque expérience. Cela est nécessaire afin de modifier le nœud de contenu adéquat lors d’une création spécifique à une expérience. For these non-default experiences, either [add a custom offer](#adding-a-custom-offer) or [add a library offer](#adding-an-offer-from-an-offer-library).

#### Création d’une offre en ajoutant un composant cible {#creating-an-offer-by-adding-a-target-component}

Ajoutez un composant cible pour créer l’offre pour l’expérience par défaut. Le composant cible est un conteneur pour d’autres composants, et les composants insérés dans ce conteneur sont ciblés. Lorsque vous utilisez le composant cible, vous pouvez ajouter plusieurs composants pour créer une offre. De plus, vous pouvez utiliser différents composants dans chaque expérience pour créer des offres différentes.

See [Configuring Target component options](#configuring-target-component-options) for information on customizing this component.

>[!NOTE]
>
>Offers that you create using the [Offers console](/help/sites-cloud/authoring/personalization/offers.md) can also contain several components. Ces offres appartiennent à une bibliothèque d’offres et peuvent être utilisées pour différentes expériences.

Comme le composant cible est un conteneur, il s’affiche sous forme de zone cible pour d’autres composants.

En mode Cible, le composant cible possède une bordure bleue, et le message de indique la nature ciblée.

![Zone de dépôt cible](/help/sites-cloud/authoring/assets/targeted-drop-target.png)

En mode d’édition, le composant cible comporte une icône Cible.

![Icône de la zone de dépôt cible](/help/sites-cloud/authoring/assets/targeted-drop-target-icon.png)

Lorsque vous faites glisser des composants dans le composant cible, ils sont des composants ciblés.

![Zone de dépôt avec cibles](/help/sites-cloud/authoring/assets/targeted-drop-zone-populated.png)

Lorsque vous ajoutez un composant au composant cible, il fournit du contenu pour une expérience spécifique. Pour spécifier l’expérience, vous sélectionnez l’expérience avant d’ajouter des composants.

Vous pouvez ajouter un composant cible à la page en mode d’édition ou en mode Cible. Vous ne pouvez ajouter des composants au composant cible qu’en mode Cible. Le composant cible appartient au groupe Composants de personnalisation.

Si vous modifiez le contenu ciblé, vous devez cliquer ou appuyer sur **Commencer le ciblage **avant de pouvoir le faire.

1. Faites glisser le composant cible vers la page dans laquelle vous souhaitez afficher l’offre.
1. Par défaut, aucun ID d’emplacement n’est défini. Cliquez ou appuyez sur Configurer (icône d’engrenage) pour définir l’emplacement.

   >[!NOTE]
   >
   >Si cette option est définie par votre administrateur, vous devrez peut-être définir l’emplacement de manière explicite.
   >
   >Administrators can decide whether setting this configuration is required at `https://<host>:<port>/system/console/configMgr/com.day.cq.personalization.impl.servlets.TargetingConfigurationServlet`
   >
   >Pour obliger les utilisateurs à saisir un emplacement, cochez la case **Forcer à indiquer l’emplacement**.

1. Sélectionnez l’expérience pour laquelle vous souhaitez créer l’offre.
1. Création de l’offre :

   * Pour l’expérience par défaut, faites glisser les composants vers la zone de dépôt ciblée et modifiez les propriétés du composant comme vous le faites habituellement pour créer le contenu de l’offre.
   * Pour les expériences autres que l’expérience par défaut, [ajoutez une offre personnalisée](#adding-a-custom-offer) ou [ajoutez une offre de bibliothèque](#adding-an-offer-from-an-offer-library).

#### Ajout d’une offre personnalisée {#adding-a-custom-offer}

Créez une offre en créant le contenu d’un composant ciblé en mode Ciblage. Lorsque vous créez une offre personnalisée, elle est utilisée comme offre pour une seule expérience.

If you decide that the offer can be used for other experiences, you can create a custom offer and [add it to the library](#adding-a-custom-offer-to-a-library). Pour plus d’informations sur l’utilisation de la console Offres pour créer une offre réutilisable, reportez-vous à la section [Ajout d’une offre à une bibliothèque d’offres](/help/sites-cloud/authoring/personalization/offers.md#add-an-offer-to-an-offer-library).

1. Sélectionnez l’expérience à laquelle vous ajoutez l’offre.
1. Pour afficher le menu Composant, cliquez ou appuyez sur le composant ciblé auquel vous ajoutez l’offre.

   ![Ajout d’une offre](/help/sites-cloud/authoring/assets/targeted-component-menu.png)

1. Cliquez ou appuyez sur l’icône « + ».

   Le contenu de l’offre Par défaut est utilisé comme offre pour l’expérience actuelle.

1. Cliquez ou appuyez sur l’offre pour afficher le menu Offre, puis cliquez ou appuyez sur l’icône Modifier.

   ![Barre d’outils du composant Target](/help/sites-cloud/authoring/assets/targeted-offer-menu.png)

1. Modifiez le contenu du composant.

#### Ajout d’une offre à partir d’une bibliothèque d’offres {#adding-an-offer-from-an-offer-library}

Add an offer from the [offer library](/help/sites-cloud/authoring/personalization/offers.md) to an experience. Vous pouvez ajouter une offre de la bibliothèque de la marque que vous ciblez actuellement.

Vous ne pouvez pas ajouter d’offres de bibliothèque à l’expérience par défaut.

1. Sélectionnez l’expérience à laquelle vous ajoutez l’offre.
1. Pour afficher le menu Composant, cliquez ou appuyez sur le composant ciblé auquel vous ajoutez l’offre.

   ![Offre ciblée](/help/sites-cloud/authoring/assets/targeted-add-offer-large.png)

1. Cliquez ou appuyez sur l’icône Dossier.

   ![Icône Dossier](/help/sites-cloud/authoring/assets/targeted-folder-button.png)

1. Sélectionnez l’offre dans la bibliothèque, puis cliquez ou appuyez sur l’icône Coche.

   ![Bibliothèque d’offres](/help/sites-cloud/authoring/assets/targeted-select-content.png)

   Le sélecteur d’offres permet de chercher ou de filtrer les offres. Lors de la recherche ou du filtrage, vous pouvez également trier les offres et modifier le mode d’affichage. Le nombre dans la partie supérieure droite indique le nombre d’offres disponibles dans la bibliothèque actuelle.

   * Click or tap **Browse** to navigate to another folder. Le volet de navigation s’affiche. Cliquez sur la flèche pour accéder aux dossiers. Click or tap **Browse** again to close the navigation pane.
   ![Parcourir le contenu](/help/sites-cloud/authoring/assets/targeted-select-content-browse.png)

   * Cliquez ou appuyez sur **Filtrer** pour filtrer les offres selon les mots-clés et les balises. Vous saisissez des mots-clés et sélectionnez des balises dans le menu déroulant. Cliquez ou appuyez de nouveau sur **Filtrer** pour fermer le volet de filtrage.
   ![Filtrage du contenu](/help/sites-cloud/authoring/assets/targeted-filter.png)

   * Modifiez la façon dont vous triez les offres en cliquant ou en appuyant sur la flèche en regard de **Du plus récent au plus ancien**. Les offres peuvent être triées de la plus récente à la plus ancienne et inversement.
   ![Ordre de tri des filtres](/help/sites-cloud/authoring/assets/targeted-filter-sort.png)

   Cliquez ou appuyez sur l’icône en regard de **Afficher sous** pour afficher les offres sous forme de mosaïque ou de liste.

   ![Afficher sous forme de bouton](/help/sites-cloud/authoring/assets/targeted-view-as-button.png)

#### Adding a Custom Offer to a Library {#adding-a-custom-offer-to-a-library}

Ajoutez une offre personnalisée à la [bibliothèque d’offres](/help/sites-cloud/authoring/personalization/offers.md) lorsque vous souhaitez la réutiliser comme offre pour différentes expériences. Vous pouvez ajouter des offres à la bibliothèque de la marque actuelle que vous ciblez. 

Pour plus d’informations sur l’utilisation de la console Offres pour créer une offre réutilisable, reportez-vous à la section [Ajout d’une offre à une bibliothèque d’offres](/help/sites-cloud/authoring/personalization/offers.md#add-an-offer-to-an-offer-library).

1. Sélectionnez l’expérience pour afficher l’offre personnalisée.
1. Cliquez ou appuyez sur l’offre personnalisée pour afficher le menu Offre, puis cliquez ou appuyez sur l’icône **Enregistrer l’offre dans la bibliothèque d’offre**.

   ![Enregistrer l&#39;offre dans la bibliothèque d&#39;offres](/help/sites-cloud/authoring/assets/targeted-save-offer-library-button.png)

1. Saisissez le nom de l’offre et sélectionnez la bibliothèque à laquelle vous ajoutez l’offre, puis cliquez ou appuyez sur l’icône Coche.

#### Conversion d’une offre de bibliothèque en bibliothèque personnalisée {#converting-a-library-offer-to-a-custom-library}

Convertissez une offre de bibliothèque en offre personnalisée pour modifier l’offre pour l’expérience actuelle, sans modifier l’offre dans d’autres expériences.

1. Sélectionnez l’expérience pour afficher l’offre de bibliothèque.
1. Cliquez ou appuyez sur l’offre de bibliothèque pour afficher le menu Offre, puis cliquez ou appuyez sur l’icône Convertir en offre intégrée.

   ![Convertir en offre insérée](/help/sites-cloud/authoring/assets/targeted-convert-inline.png)

#### Modification d’une offre de bibliothèque {#editing-a-library-offer}

Ouvrez une offre de bibliothèque à partir d’une expérience en mode ciblé pour modifier l’offre. Les modifications que vous apportez s’affichent dans toutes les expériences qui utilisent l’offre.

1. Sélectionnez l’expérience pour afficher l’offre de bibliothèque.
1. Convertissez l’offre de bibliothèque en offre locale/personnalisée. See [Converting a Library Offer to a Custom Library](#converting-a-library-offer-to-a-custom-library).
1. Modifiez le contenu de l’offre.

1. Réenregistrez-la dans la bibliothèque. See [Adding a Custom Offer to a Library](#adding-a-custom-offer-to-a-library).

## Cible : configuration des audiences {#target-configuring-the-audiences}

L’étape Cibler de la [procédure de ciblage](#the-targeting-process-create-target-and-goals-settings) implique de mapper les audiences sur les expériences utilisées lors de l’étape Créer. La page Cible affiche les audiences ciblées par chaque expérience. Vous pouvez spécifier ou modifier l’audience de chaque expérience. Si vous utilisez Adobe Target, vous pouvez également créer des tests A/B qui permettent de cibler le pourcentage de trafic d’une audience pour une expérience spécifique.

### Si vous utilisez le ciblage d’AEM ou d’Adobe Target (ciblage d’expériences)… {#if-you-are-using-aem-targeting-or-adobe-target-experience-targeting}

Les audiences s’affichent dans la partie gauche du diagramme de mappage, tandis que les expériences s’affichent dans la partie droite.

![Mappage d’audiences](/help/sites-cloud/authoring/assets/targeted-diagram.png)

Définissez une audience à l’aide d’un segment. La configuration du cloud de la page détermine les segments qui vous sont accessibles. Lorsque la page n’est pas associée à une configuration de cloud d’Adobe Target, les segments AEM sont disponibles pour définir les audiences. Lorsque la page est associée à une configuration de cloud d’Adobe Target, vous utilisez les segments cibles.

Pour plus d’informations sur les moteurs de ciblage, reportez-vous à la section [Moteur de ciblage](/help/sites-cloud/authoring/personalization/overview.md#targeting-engine).

Une audience ne doit pas être utilisée par plusieurs expériences. Un symbole d’avertissement s’affiche en regard d’une expérience lorsqu’elle est associée à une audience mappée à une autre expérience.

![Icône Avertissement](/help/sites-cloud/authoring/assets/targeted-warn.png)

### Association d’expériences à des audiences (AEM ou Adobe Target) {#associating-experiences-with-audiences-aem-or-adobe-target}

Suivez la procédure ci-dessous pour associer une expérience à une audience lorsque vous utilisez le ciblage d’AEM (ou le ciblage d’expériences d’Adobe Target) :

1. Cliquez ou appuyez sur la flèche de liste déroulante en regard de la zone de l’audience sur l’expérience.
1. (Optional) Click or tap **Edit** and then type a keyword to search for the desired segment.
1. Dans la liste d’audiences, sélectionnez l’audience et cliquez ou appuyez sur **OK**.

### Si vous utilisez des tests A/B (Adobe Target)… {#if-you-are-using-a-b-testing-adobe-target}

Si vous avez une activité de test A/B, les audiences se trouvent dans la partie gauche, le pourcentage de chaque expérience s’affiche au centre et les expériences se trouvent à droite.

Vous pouvez modifier les pourcentages, à condition que leur somme reste égale à 100 %. Une audience peut être utilisée par plusieurs expériences dans un test A/B.

![Ciblage A/B](/help/sites-cloud/authoring/assets/targeted-ab.png)

### Association d’audiences et de pourcentages de trafic avec un test A/B {#associating-audiences-and-traffic-percentages-with-a-b-testing}

1. Cliquez ou appuyez sur la zone de liste déroulante en regard de l’audience mappée sur l’expérience.
1. (Facultatif) Cliquez sur **Modifier**, puis saisissez un mot-clé pour chercher le segment de votre choix.
1. Cliquez ou appuyez sur **OK.**
1. Saisissez les pourcentages pour configurer le mode d’acheminement du trafic vers les différentes expériences. Le total doit être égal à 100.
1. (Facultatif) Modifiez le nom de l’expérience en cliquant sur le menu déroulant en regard du nom de l’expérience.

## Objectifs et paramètres : configuration de l’activité et définition des objectifs {#goals-settings-configuring-the-activity-and-setting-goals}

The Goals &amp; Settings step of [the targeting process](#the-targeting-process-create-target-and-goals-settings) involves configuring the behavior of the brand activity. Spécifiez le moment auquel l’activité commence et se termine, ainsi que le niveau de priorité de l’activité. Vous pouvez également suivre les objectifs. En particulier, vous pouvez déterminer ce que vous souhaitez mesurer avec vos activités.

Les mesures d’objectif ne sont disponibles que si vous utilisez Adobe Target pour votre moteur de ciblage. Vous devez définir au moins une mesure d’objectif. Si Adobe Analytics est configuré et que vous disposez d’une configuration de cloud A4T Analytics, vous pouvez choisir si la source de création de rapports est Adobe Target ou Adobe Analytics.

Les mesures d’objectif ne sont mesurées que pour la campagne publiée.

Si vous utilisez AEM comme moteur de ciblage :

![AEM en tant que moteur cible](/help/sites-cloud/authoring/assets/targeted-goals.png)

Si vous utilisez Adobe Target comme moteur de ciblage :

![Adobe Target en tant que moteur de ciblage](/help/sites-cloud/authoring/assets/targeted-engine.png)

Si vous utilisez Adobe Target comme moteur de ciblage et que A4T Analytics est configuré pour le compte, un menu déroulant supplémentaire, **Source de création de rapports**, s’affiche :

![A4T](/help/sites-cloud/authoring/assets/targeted-source.png)

Les mesures de réussite ci-dessous sont disponibles (pour la publication uniquement) :

| Mesure | Description | Options |
|---|---|---|
| Conversion | Pourcentage de visiteurs ayant cliqué sur n’importe quelle partie de l’expérience testée. Une conversion peut être comptabilisée une fois par visiteur ou chaque fois qu’un visiteur effectue une conversion. La mesure de conversion est définie sur l’une des valeurs suivantes : | Affichage d’une page : vous pouvez définir la page que le public a consultée en sélectionnant l’URL, puis en définissant l’URL ou plusieurs URL, ou en sélectionnant l’URL, puis en ajoutant un chemin ou un mot-clé. A affiché une mbox : vous pouvez définir la mbox que l’audience a consultée en saisissant le nom de la mbox. Vous pouvez saisir plusieurs mbox en cliquant sur Ajouter une mbox. |
| Recettes | Recettes générées par la visite. Vous pouvez choisir parmi les mesures de recettes répertoriées. Pour ces options, la consultation d’une mbox indique que l’objectif a été atteint. Vous pouvez définir la mbox ou plusieurs mbox. | Recettes par visiteur (RPV), Valeur de commande moyenne (AOV), Total ventes, Commandes |
| Engagement | Vous pouvez mesurer trois types d’engagement | Pages vues, Score personnalisé, Temps passé sur le site |

De plus, il existe des paramètres avancés qui permettent de déterminer comment compter les mesures de réussite. Les options incluent la comptabilisation de la mesure par impression ou une fois par visiteur et la possibilité de conserver l’utilisateur dans l’activité ou de l’en retirer.

Utilisez les options avancées pour déterminer ce qui se passe **après** qu’un utilisateur a rencontré la mesuré d’objectif. Le tableau suivant présente les options disponibles.

| Une fois qu’un utilisateur a rencontré cette mesure d’objectif... | Vous sélectionnez l’événement suivant…  |
|---|---|
| Incrémenter le décompte et laisser l’utilisateur dans l’activité | Indiquez comment le nombre est incrémenté : Une fois par participant, à chaque impression, à l’exclusion des actualisations de page, à chaque impression |
| Incrémenter le décompte, libérer l’utilisateur et autoriser le retour | Sélectionnez l’expérience que voit le visiteur s’il entre de nouveau dans l’activité : Même expérience, expérience aléatoire, expérience invisible |
| Incrémenter le décompte, libérer l’utilisateur et saisir de nouveau la barre | Déterminez ce que l’utilisateur voit au lieu du contenu de l’activité : Même expérience, sans suivi, contenu par défaut ou autre contenu d’activité |

Pour plus d’informations sur les mesures de réussite, reportez-vous à la section [Documentation d’Adobe Target](https://marketing.adobe.com/resources/help/en_US/target/target/r_success_metrics.html).

### Paramètres de configuration (ciblage d’AEM) {#configuring-settings-aem-targeting}

Pour configurer les paramètres si vous utilisez le ciblage d’AEM :

1. Pour indiquer le moment où l’activité commence, utilisez le menu déroulant **Démarrer** pour sélectionner l’une des valeurs suivantes :

   * **Après activation** : l’activité commence lorsque la page contenant le contenu ciblé est activée.
   * **Date et heure spécifiées :** heure spécifique. Lorsque vous sélectionnez cette option, appuyez ou cliquez sur l’icône de calendrier, sélectionnez une date, puis spécifiez l’heure de début de l’activité.

1. Pour spécifier le moment où l’activité se termine, utilisez le menu déroulant **Fin** pour sélectionner l’une des valeurs suivantes :

   * **Si désactivés** : l’activité s’arrête lorsque la page contenant le contenu ciblé est désactivée.
   * **Date et heure spécifiées :** heure spécifique. Lorsque vous sélectionnez cette option, appuyez ou cliquez sur l’icône de calendrier, sélectionnez une date, puis spécifiez l’heure de fin de l’activité.

1. Pour spécifier la priorité de l’activité, utilisez le curseur pour choisir **Faible**, **Normale** ou **Élevée**.

### Configuration des objectifs et des paramètres (Adobe Target) {#configuring-goals-settings-adobe-target}

Pour configurer les objectifs et les paramètres si vous utilisez Adobe Target :

1. Pour indiquer le moment où l’activité commence, utilisez le menu déroulant **Démarrer** pour sélectionner l’une des valeurs suivantes :

   * **Après activation** : l’activité commence lorsque la page contenant le contenu ciblé est activée.
   * **Date et heure spécifiées :** heure spécifique. Lorsque vous sélectionnez cette option, appuyez ou cliquez sur l’icône de calendrier, sélectionnez une date, puis spécifiez l’heure de début de l’activité.

1. Pour spécifier le moment où l’activité se termine, utilisez le menu déroulant **Fin** pour sélectionner l’une des valeurs suivantes :

   * **Si désactivés** : l’activité s’arrête lorsque la page contenant le contenu ciblé est désactivée.
   * **Date et heure spécifiées :** heure spécifique. Lorsque vous sélectionnez cette option, appuyez ou cliquez sur l’icône de calendrier, sélectionnez une date, puis spécifiez l’heure de fin de l’activité.

1. Pour spécifier la priorité de l’activité, utilisez le curseur pour choisir **Faible**, **Normale** ou **Élevée**.
1. If you have configured Adobe Analytics with your Adobe Target Account, then you see the **Reporting Source** drop-down menu. Sélectionnez **Adobe Target** ou **Adobe Analytics** comme source.

   Si vous avez sélectionné **Adobe Analytics**, sélectionnez la société et une suite de rapports. Si vous sélectionnez **Adobe Target**, aucune action n’est nécessaire.

   ![Source de création de rapports](/help/sites-cloud/authoring/assets/targeted-reporting-source.png)

1. Dans la zone **Mesure de l’objectif**, sous **Mon principal objectif**, sélectionnez la mesure de réussite que vous souhaitez suivre (Conversion, Revenu, Engagement) et indiquez comment cette mesure est mesurée (ou l’action effectuée par l’audience pour indiquer qu’un objectif a été atteint). Reportez-vous à la définition des mesures d’objectif dans le tableau précédent et reportez-vous à la section relative aux mesures de réussite de la [Documentation d’Adobe Target](https://marketing.adobe.com/resources/help/en_US/target/target/r_success_metrics.html).

   Vous pouvez renommer l’objectif en cliquant sur le bouton de sélection dans le coin supérieur droit et en sélectionnant **Renommer**.

   Si vous devez supprimer tous les champs, cliquez sur le bouton de sélection dans le coin supérieur droit et sélectionnez **Effacer tous les champs**.

   Toutes les mesures comportent également des paramètres avancés que vous pouvez définir. Sélectionnez **Paramètres avancés** pour y accéder. See definition of how success metrics are counted in previous table and see [Adobe Target documentation](https://marketing.adobe.com/resources/help/en_US/target/target/r_success_metrics.html).

   >[!NOTE]
   >
   >Un objectif au moins doit être défini.

   ![Mesure des objectifs](/help/sites-cloud/authoring/assets/targeted-goal-metric.png)

   >[!NOTE]
   >
   >S’il manque des informations dans votre mesure, la mesure est entourée d’une ligne rouge.

1. Cliquez sur **Ajouter une nouvelle mesure** pour configurer d’autres mesures de réussite.

   ![Mesures supplémentaires](/help/sites-cloud/authoring/assets/targeted-additional-metrics.png)

   >[!NOTE]
   >
   >Vous pouvez supprimer d’autres objectifs en cliquant ou en appuyant sur le bouton de sélection et cliquant ou en appuyant sur **Supprimer**. AEM exige qu’au moins un objectif soit défini.

1. If you want more control over how success metrics are counted, click or tap **Advanced Settings** to access those.
1. Cliquez sur **Enregistrer**.

Après la configuration, vous pouvez [afficher les performances de vos activités](/help/sites-cloud/authoring/personalization/activities.md#viewing-performance-and-converting-winning-experiences-a-b-test), qui utilisent Adobe Target (ciblage d’expériences ou des tests A/B). De plus, avec le ciblage des tests A/B, vous pouvez [convertir les gagnants](/help/sites-cloud/authoring/personalization/activities.md#viewing-performance-and-converting-winning-experiences-a-b-test).

## Simulation d’une expérience {#simulating-an-experience}

Simulez l’expérience d’un visiteur pour vérifier que le contenu de la page s’affiche de la façon escomptée en fonction de la conception du contenu ciblé. Lors de la simulation, chargez différents profils utilisateur et découvrez le contenu ciblé pour l’utilisateur en question.

Les critères ci-dessous déterminent le contenu qui s’affiche lors de la simulation des interactions d’un visiteur :

* Les données contenues dans le magasin de la session de l’utilisateur (par le biais de ContextHub).
* [Activités qui sont activées](/help/sites-cloud/authoring/personalization/activities.md).
* [Règles qui définissent les segments](/help/sites-cloud/authoring/personalization/segmentation.md).
* Contenu des expériences dans les composants Cible.
* [Configuration du moteur de ciblage](/help/sites-cloud/authoring/personalization/activities.md).

Si un contenu inattendu s’affiche dans la page lorsque vous chargez un profil, vérifiez la configuration de chaque élément de cette liste.

>[!NOTE]
>
>Si vous utilisez des tests A/B, lors de la simulation, les expériences s’affichent en fonction du pourcentage de trafic. Cette action est gérée par Adobe Target, ce qui peut entraîner des résultats inattendus pour les créateurs. (L’activité _créateur est synchronisée avec les paramètres spécifiques qui permettent une réévaluation lors de la simulation.) Les créateurs peuvent avoir besoin d’actualiser pour afficher les autres expériences en fonction des paramètres de trafic.

Pour simuler l’expérience du visiteur, utilisez les outils suivants :

* Activité de simulation en mode Ciblage : la page affiche les offres pour l’utilisateur sélectionné dans ContextHub. Vous pouvez modifier les offres qui ciblent l’utilisateur.
* Mode Aperçu : utilisez ContextHub pour sélectionner les utilisateurs et les emplacements répondant aux critères des segments sur lesquels vos expériences sont fondées. En cas de modification de vos sélections ContextHub, le contenu ciblé change en conséquence.

1. To switch to Preview mode, on the toolbar click or tap **Preview**.
1. Dans la barre d’outils, cliquez ou appuyez sur l’icône ContextHub.

   ![Bouton ContextHub](/help/sites-cloud/authoring/assets/targeted-contexthub-button.png)

1. Utilisez ContextHub pour modifier les propriétés de contexte. Par exemple, cliquez ou appuyez sur la propriété Persona pour sélectionner un autre utilisateur.

   ![Barre d’outils ContextHub](/help/sites-cloud/authoring/assets/targeted-contexthub-toolbar.png)

   La page change pour afficher le contenu ciblé pour le contexte actuel.

1. Pour apporter des modifications aux offres affichées, passez en mode Ciblage. L’activité de simulation étant sélectionnée, modifiez les offres pour le contexte configuré en mode Aperçu.

## Configuration des options du composant cible {#configuring-target-component-options}

Vous pouvez personnaliser le composant cible en accédant aux options du composant de l’une des deux façons suivantes :

1. Après avoir ciblé le composant, dans le composant Target, cliquez ou appuyez sur le composant, puis sur l’icône de paramètres (engrenage).

   ![Paramètres du composant](/help/sites-cloud/authoring/assets/targeted-component-settings.png)

   AEM affiche la fenêtre Options du composant cible.

   ![Boîte de dialogue Cible](/help/sites-cloud/authoring/assets/targeted-dialog.png)

1. Autrement, pour accéder à ces paramètres en mode Plein écran, dans la fenêtre Options du composant cible, cliquez ou appuyez sur l’icône Plein écran.

   ![Bouton Plein écran](/help/sites-cloud/authoring/assets/targeted-fullscreen.png)

   AEM affiche la fenêtre Options du composant cible en plein écran.

   ![Composant en mode Plein écran](/help/sites-cloud/authoring/assets/targeted-target-as-enging.png)

1. Configurez les paramètres du composant cible, comme indiqué dans les tableaux suivants.

| Option | Description |
|---|---|
| Emplacement | L’emplacement est une chaîne qui attribue un nom à l’emplacement du contenu ciblé et connecte les offres aux lieux (ou aux emplacements ou aux composants) dans la page où ces offres doivent être positionnées. Ce champ est une valeur générique. Si vous insérez une offre dans un composant, l’offre mémorise l’ID d’emplacement. Lorsque la page est exécutée, le moteur évalue les segments de l’utilisateur et, à partir de là, résout les expériences des campagnes actives qui doivent s’afficher. Ensuite, il cherche les ID d’emplacement dans la page et tente de faire correspondre les offres aux ID d’emplacement. |
| Moteur | Sélectionnez entre les règles côté client (sans suivi), Adobe Target, ContextHub et Adobe Campaign selon le moteur à utiliser. |

Si vous sélectionnez Adobe Target comme moteur :

![Ciblage en tant que moteur](/help/sites-cloud/authoring/assets/targeted-target-as-enging.png)

| Option | Description |
|---|---|
| Ciblage précis | L’activation du ciblage précis indique au composant d’attendre les données de contexte du client ou les données ContextHub pour être disponible avant l’envoi de la demande à Adobe Target. Cela peut accroître le temps de chargement. Pour la création, le ciblage précis est toujours activé. Si vous cochez la case Ciblage précis, la mbox commence par effectuer une opération mboxDefine, puis une opération mboxUpdate dans une demande Ajax une fois que les données sont disponibles. Si vous ne cochez pas la case Ciblage précis, la mbox effectue immédiatement une mboxCreate, ce qui entraîne une requête synchrone (dans ce cas, toutes les données contextuelles ne sont pas encore disponibles). Remarque : L’activation ou la désactivation du ciblage précis sur un composant spécifique n’a aucune incidence sur les paramètres définis globalement. Vous pouvez toujours remplacer les paramètres globaux en sélectionnant Ciblage précis dans le composant. |
| Inclure les segments résolus | Si vous cochez cette case, tous les segments résolus dans l’appel de mbox et les paramètres configurés dans la page et dans l’infrastructure sont inclus. Cela ne fonctionne avec l’API XML que lorsque vous synchronisez des segments AEM. Si des segments dans AEM ne sont pas gérés par Adobe Target (comme les segments de script), cette option permet de résoudre le segment dans AEM et d’envoyer à Adobe Target des informations indiquant que le segment est actif. |
| Paramètres contextuels hérités | Répertorie les paramètres de contexte hérités de l’infrastructure Adobe Target, le cas échéant, associés à la page sélectionnée. |
| Paramètres de contexte | Cliquez ou appuyez sur Ajouter un champ pour configurer d’autres paramètres contextuels (comme dans la structure Target). Les paramètres de contexte ajoutés au composant ne concernent que le composant et non un autre composant, comme ce serait le cas si vous ajoutiez des paramètres de contexte directement dans l’infrastructure. |
| Paramètres statiques | Cliquez ou appuyez sur Ajouter un champ pour configurer d’autres paramètres statiques (comme dans la structure Target). Les paramètres statiques ajoutés au composant s’appliquent uniquement au composant et non à un autre composant, comme cela serait le cas si vous ajoutiez des paramètres statiques directement à la structure. Les paramètres statiques ne proviennent pas du contexte (contexte du client de ContextHub). |

>[!NOTE]
>
>Lorsque vous sélectionnez un composant et que vous définissez son ciblage, AEM remplace également le composant et y insère un composant Adobe Target. (Le composant Adobe Target est utilisé non seulement lorsque vous l’ajoutez manuellement à la page, mais également lorsque vous ciblez un composant existant.)
>
>Vous sélectionnez **Adobe Campaign** comme moteur si vous intégrez AEM à Adobe Campaign. Pour plus d’informations, voir Intégration d’AEM à Adobe Campaign .
>
>Sélectionnez **ContextHub** comme moteur si vous utilisez le ciblage ContextHub. Voir Configuration de ContextHub pour plus d’informations.
<!--You select **Adobe Campaign** as the engine if you are integrating AEM with Adobe Campaign. See [Integrating AEM with Adobe Campaign](/help/sites-administering/campaign.md) for more information.-->
<!--Select **ContextHub** as the engine if you are using ContextHub for targeting. See [Configuring ContextHub.](/help/sites-administering/contexthub-config.md)-->
