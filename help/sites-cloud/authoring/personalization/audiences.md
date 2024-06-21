---
title: Gestion des audiences
description: La console Audiences vous permet de créer, d’organiser et de gérer les audiences associées à votre compte Adobe Target ou de gérer des segments pour ContextHub.
exl-id: dff72c15-afcd-4b16-a711-e9ca3010e3ec
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 86%

---

# Gestion des audiences{#managing-audiences}

La console Audiences vous permet de créer, d’organiser et de gérer les audiences associées à votre compte Adobe Target ou de gérer des segments pour ContextHub :

* Ajouter des audiences : audiences Adobe Target ou segments ContextHub.
* Gérer des audiences.

Une audience, appelée *segment* dans ContextHub, désigne une classe de visiteurs définie selon des critères spécifiques et qui détermine qui peut voir une activité ciblée. Lorsque vous ciblez une activité, vous pouvez sélectionner des audiences directement dans le processus de ciblage ou en créer d’autres dans la console Audiences.

Dans la console Audiences, les audiences sont organisées par marque.

Les audiences sont disponibles en mode Ciblage pour [créer du contenu ciblé](/help/sites-cloud/authoring/personalization/targeted-content.md) ou pour créer des audiences (mais vous devez créer des audiences Adobe Target dans la console Audiences). Les audiences que vous créez en mode ciblage apparaissent dans la console Audiences.

Les audiences s’affichent avec un libellé décrivant le type d’audience défini :

* CH - segment ContextHub
* AT - audience Adobe Target

## Création d’un segment ContextHub dans la console Audiences {#creating-a-contexthub-segment-in-the-audiences-console}

Vous pouvez créer un segment ContextHub dans la console Audiences ou durant le processus de ciblage.

Pour créer un segment ContextHub dans la console Audiences :

1. Dans la console Navigation, sélectionnez **Personnalisation**. Sélectionner **Audiences**.
1. Sélectionner **Créer un segment ContextHub**.

   ![Création d’un segment](/help/sites-cloud/authoring/assets/audiences-create-segment.png)

1. Dans la boîte de dialogue **Nouveau segment ContextHub**, saisissez un titre, ajustez l’amplification et cliquez sur **Créer**. Votre nouveau segment ContextHub apparaît dans la liste des audiences.

   >[!NOTE]
   >
   >Vous pouvez trier la liste modifiée en appuyant ou en cliquant sur **Modifié** pour trier par ordre décroissant afin d’afficher toutes les audiences créées.

Pour plus d’informations sur la création de segments à l’aide de ContextHub, voir la documentation Configuration de la segmentation avec ContextHub. <!--For further detail about creating segments using ContextHub, see [Configuring Segmentation with ContextHub](/help/sites-administering/segmentation.md).-->

## Création d’une audience Adobe Target dans la console Audiences {#creating-an-adobe-target-audience-using-the-audience-console}

Vous pouvez créer des audiences Adobe Target directement dans AEM à l’aide de la console Audiences.

Les audiences sont définies par des règles qui déterminent les personnes incluses dans une activité cible. Une définition d’audience peut inclure plusieurs règles et chaque règle peut inclure plusieurs paramètres.

Lorsque vous utilisez plusieurs règles, celles-ci sont combinées par l’opérateur booléen ET, ce qui signifie que les personnes pouvant potentiellement faire partie de l’audience doivent remplir toutes les conditions définies pour être incluses dans l’activité. Par exemple, si vous définissez une règle de système d’exploitation ET une règle de navigateur, seules les personnes utilisant le système d’exploitation défini ET le navigateur défini sont incluses dans l’activité.

>[!NOTE]
>
>Si vous ne voyez pas l’option **Créer le public cible** dans le menu **Créer**, cela signifie que vous ne disposez pas des autorisations nécessaires pour créer une audience. Vous avez besoin de droits d’accès en écriture sous `/etc/segmentation` pour pouvoir créer des audiences. Le groupe content-authors dispose par défaut d’autorisations d’écriture.

Pour créer une audience Adobe Target :

1. Dans la console Navigation, sélectionnez **Personnalisation**. Sélectionner **Audiences**.

   ![Accès aux audiences](/help/sites-cloud/authoring/assets/audiences-navigation.png)

1. Dans la console Audiences, sélectionnez **Créer** puis **Création d’une audience Target**.

   ![Création d’un public cible](/help/sites-cloud/authoring/assets/audiences-create-target.png)

1. Dans le **Configuration Adobe Target** , sélectionnez la configuration de la cible, puis **OK**.
1. Dans la zone Règle#1, sélectionnez le type d’attribut et saisissez toutes les informations d’attribut dans les champs disponibles. Lorsque vous avez terminé, cochez la case située à droite de l’attribut pour l’enregistrer. Voir [Attributs et leurs options](#attributes-and-their-options) pour plus d’informations sur tous les attributs.
1. Cliquez sur **Ajouter une règle** pour ajouter une autre règle. Entrez autant de règles que nécessaire. Les règles sont combinées avec l’opérateur booléen ET, ce qui signifie que l’audience doit répondre à toutes les exigences de chaque règle pour être éligible à une activité.
1. Sélectionnez **Suivant**.
1. Saisissez un nom pour l’audience et sélectionnez **Enregistrer**.
1. Sélectionnez **Enregistrer**. Votre audience est répertoriée dans la liste des audiences.

### Attributs et leurs options {#attributes-and-their-options}

Vous pouvez créer des règles de ciblage pour chacun des attributs suivants :

| **Attribut** | **Description** | **Pour plus d’informations** |
|---|---|---|
| **Mobile** | Appareils mobiles Target basés sur des paramètres tels que l’appareil mobile, le type d’appareil, le fabricant de l’appareil, les dimensions de l’écran (en pixels), etc. | Voir la [documentation mobile](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/mobile.html?lang=fr) dans Adobe Target. |
| **Personnalisé** | Les paramètres personnalisés sont des paramètres mbox. Si vous transférez des paramètres mbox à des mbox ou utilisez la fonction targetPageParams, ces paramètres apparaissent ici pour utilisation dans les audiences. | Voir la [documentation sur les paramètres personnalisés](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/custom-parameters.html?lang=fr) dans Adobe Target. |
| **Système d’exploitation** | Vous pouvez cibler les visiteurs et visiteuses qui utilisent un système d’exploitation spécifique. | Ciblez les utilisateurs et utilisatrices qui utilisent Linux, Macintosh ou Windows. |
| **Pages du site** | Ciblez les visiteurs et visiteuses qui se trouvent sur une page spécifique ou qui possèdent un paramètre mBox spécifique. | Reportez-vous à la [documentation relative aux pages de site](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/site-pages.html?lang=fr) dans Adobe Target. |
| **Navigateur** | Vous pouvez cibler les utilisateurs et utilisatrices qui utilisent un navigateur spécifique ou des options de navigateur spécifiques lors de leur visite sur votre page. | Reportez-vous à la [documentation relative aux options de navigateur](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/browser.html?lang=fr) dans Adobe Target. |
| **Profil du visiteur ou de la visiteuse** | Ciblez les visiteurs et visiteuses qui respectent des paramètres de profil spécifiques. | Reportez-vous à la [documentation relative aux profils de visiteur](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/visitor-profile.html?lang=fr) dans Adobe Target. |
| **Sources de trafic** | Ciblez les visiteurs et visiteuses en fonction du moteur de recherche ou de la page de destination qui les renvoie à votre site. | Reportez-vous à la [documentation relative aux sources de trafic](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/traffic-sources.html?lang=fr) dans Adobe Target. |

## Modification d’une audience dans la console Audiences {#modifying-an-audience-in-the-audiences-console}

>[!NOTE]
>
>Vous ne pouvez modifier que les audiences Adobe Target créées dans la même instance d’AEM que celle où vous effectuez des modifications. Les audiences Target créées dans différents environnements d’AEM ne peuvent pas être modifiées.

Vous pouvez modifier n’importe quelle audience ContextHub à partir de la console Audiences. Vous pouvez également modifier des audiences Adobe Target à condition qu’elles aient été créées dans AEM :

1. Dans la console Navigation, sélectionnez **Personnalisation**. Sélectionner **Audiences**.
1. Sélectionnez l’icône en regard du segment ContextHub à modifier, puis sélectionnez **Modifier**.
1. Apportez toutes les modifications dans l’éditeur de segment. Pour plus d’informations, voir la documentation de ContextHub. <!--See the [ContextHub](/help/sites-administering/contexthub-config.md) documentation for more information.-->
