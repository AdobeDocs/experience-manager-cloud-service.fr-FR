---
title: Gestion des audiences
description: La console Audiences vous permet de créer, d’organiser et de gérer les audiences associées à votre compte Adobe Target ou de gérer des segments pour ContextHub.
translation-type: ht
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Gestion des audiences{#managing-audiences}

La console Audiences vous permet de créer, d’organiser et de gérer les audiences associées à votre compte Adobe Target ou de gérer des segments pour ContextHub :

* Ajouter des audiences (audiences d’Adobe Target ou segments ContextHub).
* Gérer des audiences.

Une audience, appelée *segment* dans ContextHub, désigne une classe de visiteurs définie selon des critères spécifiques et qui détermine qui peut voir une activité ciblée. Lorsque vous ciblez une activité, vous pouvez sélectionner des audiences directement dans le processus de ciblage ou en créer de nouvelles dans la console Audiences.

Dans la console Audiences, les audiences sont organisées par marque.

Les audiences sont disponibles en mode Ciblage pour [créer du contenu ciblé](/help/sites-cloud/authoring/personalization/targeted-content.md) ou pour créer des audiences (mais vous devez créer des audiences Adobe Target dans la console Audiences). Les audiences que vous créez en mode Ciblage apparaissent dans la console Audiences.

Les audiences sont accompagnées d’un libellé qui décrit le type d’audience défini :

* CH - segment ContextHub
* AT - audience Adobe Target

## Création d’un segment ContextHub dans la console Audiences   {#creating-a-contexthub-segment-in-the-audiences-console}

Vous pouvez créer un segment ContextHub dans la console Audiences ou durant le processus de ciblage.

Pour créer un segment ContextHub dans la console Audiences :

1. Dans la console Navigation, cliquez ou appuyez sur **Personnalisation**. Cliquez ou appuyez sur **Audiences**.
1. Cliquez ou appuyez sur **Créer un segment ContextHub**.

   ![Création d’un segment](/help/sites-cloud/authoring/assets/audiences-create-segment.png)

1. Dans la boîte de dialogue **Nouveau segment ContextHub**, saisissez un titre, ajustez l’amplification et cliquez sur **Créer**. Votre nouveau segment ContextHub apparaît dans la liste des audiences.

   >[!NOTE]
   >
   >Vous pouvez trier la liste modifiée en appuyant ou en cliquant sur **Modifié** pour la trier par ordre décroissant afin de voir toutes les audiences nouvellement créées.

Pour plus d’informations sur la création de segments à l’aide de ContextHub, voir la documentation Configuration de la segmentation avec ContextHub. <!--For further detail about creating segments using ContextHub, please see the [Configuring Segmentation with ContextHub](/help/sites-administering/segmentation.md) documentation.-->

## Création d’une audience Adobe Target dans la console Audiences {#creating-an-adobe-target-audience-using-the-audience-console}

Vous pouvez créer des audiences Adobe Target directement dans AEM à l’aide de la console Audiences.

Les audiences sont définies par des règles qui déterminent qui est inclus dans une activité Target. Une définition d’audience peut contenir plusieurs règles. De plus, chaque règle peut inclure plusieurs paramètres.

Lorsque vous utilisez plusieurs règles, elles sont combinées par l’opérateur booléen ET, ce qui signifie qu’un candidat potentiellement membre d’une audience doit répondre à toutes les conditions définies pour être inclus dans l’activité. Par exemple, si vous définissez une règle de système d’exploitation ET une règle de navigateur, seuls les visiteurs qui utilisent le système d’exploitation défini ET le navigateur défini sont inclus dans l’activité.

>[!NOTE]
>
>Si vous ne voyez pas l’option **Créer le public cible** dans le menu **Créer**, cela signifie que vous ne disposez pas des autorisations nécessaires pour créer une audience. Vous avez besoin de droits d’accès en écriture sous `/etc/segmentation` pour pouvoir créer des audiences. Le groupe content-authors dispose par défaut d’autorisations d’écriture.

Pour créer une audience Adobe Target :

1. Dans la console Navigation, cliquez ou appuyez sur **Personnalisation**. Cliquez ou appuyez sur **Audiences**.

   ![Accès aux audiences](/help/sites-cloud/authoring/assets/audiences-navigation.png)

1. Dans la console Audiences, appuyez ou cliquez sur **Créer**, puis sur **Créer le public cible**.

   ![Création d’un public cible](/help/sites-cloud/authoring/assets/audiences-create-target.png)

1. Dans la boîte de dialogue **Configuration d’Adobe Target**, choisissez la configuration cible et cliquez ou appuyez sur **OK**.
1. Dans la zone Règle nº 1, cliquez ou appuyez sur le type d’attribut et entrez les informations d’attribut dans les champs disponibles. Lorsque vous avez terminé, cochez la case située à droite de l’attribut pour l’enregistrer. Voir [Attributs et leurs options](#attributes-and-their-options) pour plus d’informations sur tous les attributs.
1. Cliquez sur **Ajouter une règle** pour ajouter une autre règle. Entrez autant de règles que vous le souhaitez. Les règles sont combinées avec l’opérateur booléen ET, ce qui signifie que l’audience doit répondre à tous les critères de chaque règle pour être candidate à une activité.
1. Cliquez ou appuyez sur **Suivant**.
1. Saisissez le nom de l’audience et cliquez ou appuyez sur le bouton **Enregistrer**.
1. Cliquez ou appuyez sur **Enregistrer**. Votre audience est répertoriée dans la liste des audiences.

### Attributs et leurs options   {#attributes-and-their-options}

Vous pouvez créer des règles de ciblage pour chacun des attributs suivants :

| **Attribut** | **Description** | **Pour plus d’informations** |
|---|---|---|
| **Mobile** | Périphériques mobiles Target basés sur des paramètres tels que l’appareil mobile, le type d’appareil, el fabricant de l’appareil, les dimensions de l’écran (en pixels), etc. | Reportez-vous à la [documentation relative au ciblage mobile](https://marketing.adobe.com/resources/help/en_US/target/target/c_mobile.html) dans Adobe Target. |
| **Personnalisé** | Les paramètres personnalisés sont des paramètres mbox. Si vous transférez des paramètres mbox à des mbox ou utilisez la fonction targetPageParams, ces paramètres apparaissent ici pour utilisation dans les audiences. | Reportez-vous à la [documentation relative aux paramètres personnalisés](https://marketing.adobe.com/resources/help/en_US/target/target/c_custom_parameters.html) dans Adobe Target. |
| **Système d’exploitation** | Vous pouvez cibler les visiteurs qui utilisent un système d’exploitation en particulier. | Utilisateurs de Target sous Linux, Mac ou Windows. |
| **Pages du site** | Visiteurs ciblés qui se trouvent sur une page spécifique ou qui possèdent un paramètre de mbox spécifique. | Reportez-vous à la [documentation relative aux pages de site](https://marketing.adobe.com/resources/help/en_US/target/target/c_site_pages.html) dans Adobe Target. |
| **Navigateur** | Vous pouvez cibler les visiteurs qui utilisent un navigateur spécifique ou des options de navigateur spécifiques lors de l’accès à votre page. | Reportez-vous à la [documentation relative aux options de navigateur](https://marketing.adobe.com/resources/help/en_US/target/target/c_browser_options.html) dans Adobe Target. |
| **Profil du visiteur** | Visiteurs Target qui respectent des paramètres de profil spécifiques. | Reportez-vous à la [documentation relative aux profils de visiteur](https://marketing.adobe.com/resources/help/en_US/target/target/c_visitor_profile.html) dans Adobe Target. |
| **Sources de trafic** | Visiteurs ciblés selon le moteur de recherche ou la page d’entrée qui les renvoie au site. | Reportez-vous à la [documentation relative aux sources de trafic](https://marketing.adobe.com/resources/help/en_US/target/target/c_traffic_sources.html) dans Adobe Target. |

## Modification d’une audience dans la console Audiences {#modifying-an-audience-in-the-audiences-console}

>[!NOTE]
>
>Vous pouvez seulement modifier les audiences Adobe Target qui ont été créées dans l’instance d’AEM dans laquelle vous procédez aux modifications. Les audiences Target créées dans différents environnements AEM ne peuvent pas être modifiées.

Vous pouvez modifier n’importe quelle audience ContextHub à partir de la console Audiences. Vous pouvez également modifier des audiences Adobe Target à condition qu’elles aient été créées dans AEM :

1. Dans la console Navigation, cliquez ou appuyez sur **Personnalisation**. Cliquez ou appuyez sur **Audiences**.
1. Appuyez ou cliquez sur l’icône en regard du segment ContextHub à modifier, puis appuyez ou cliquez sur **Modifier**.
1. Apportez toutes les modifications dans l’éditeur de segment. Pour plus d’informations, voir la documentation de ContextHub. <!--See the [ContextHub](/help/sites-administering/contexthub-config.md) documentation for more information.-->
