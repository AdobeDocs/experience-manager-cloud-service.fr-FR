---
title: Réutilisation des propriétés de métadonnées d’un formulaire adaptatif
seo-title: Reuse metadata properties of an Adaptive Form
description: Vous pouvez réutiliser un formulaire adaptatif existant afin d’en créer de nouveaux.
seo-description: You can reuse an existing Adaptive Form to create new Adaptive Forms.
exl-id: fb8cf3a9-fd19-46bf-b40e-2af76ca68b9f
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 100%

---

# Réutilisation des propriétés de métadonnées d’un formulaire adaptatif {#reusing-adaptive-forms}

Si vous souhaitez utiliser certaines des propriétés d’un formulaire adaptatif existant pour en générer un nouveau, il vous suffit d’utiliser la fonctionnalité de copier-coller. Vous pouvez, en outre, coller le nouveau formulaire adaptatif dans le dossier de votre choix. Toutes les propriétés de métadonnées sont répliquées ; les XFA et XSD relatifs aux formulaires adaptatifs basés sur XFA et XSD sont également copiés.

>[!NOTE]
>
>L’état et les détails de révision ne sont pas copiés. Par exemple, si votre formulaire adaptatif est copié après avoir été publié, le formulaire collé se trouve dans l’état « non publié ». De même, si un élément copié est en cours de révision, l’élément collé ne se trouve pas sous la même révision.

## Copie d’un formulaire adaptatif {#copy-an-adaptive-form}

Copiez un formulaire adaptatif en utilisant l’une des méthodes suivantes :

1. Cliquez sur l’icône de copie ![aem6forms_copy](assets/aem6forms_copy.png) dans les actions rapides.

   >[!NOTE]
   >
   >Les actions rapides sont les éléments d’action qui s’affichent sur une vignette lorsque vous pointez dessus.

1. Sélectionnez le formulaire adaptatif. Le processus de sélection est différent pour chaque vue.

   Si le mode d’affichage Carte est actif, accédez au mode de sélection en cliquant sur l’icône de sélection ![aem6forms_check-circle](assets/aem6forms_check-circle.png), puis cliquez sur tous les formulaires adaptatifs à copier.

   Si le mode Liste est actif, cochez les cases à cocher de tous les formulaires adaptatifs pour les sélectionner.

   >[!NOTE]
   >
   >Tous les éléments sélectionnés doivent être des formulaires adaptatifs, car la fonctionnalité de copier-coller n’est prise en charge que pour ces formulaires, et tous doivent figurer dans le même dossier.

   Après avoir sélectionné les éléments, cliquez sur l’icône de copie ![aem6forms_copy](assets/aem6forms_copy.png) de la barre d’outils pour copier le formulaire adaptatif sélectionné.

## Coller un formulaire adaptatif {#paste-an-adaptive-form}

Un clic sur l’action de copie annule automatiquement le mode de sélection et rend visible l’icône ![Coller](assets/Smock_Paste_18_N.svg). Accédez maintenant au dossier de votre choix et cliquez sur l’icône ![Coller](assets/Smock_Paste_18_N.svg) pour coller le formulaire adaptatif copié.

Si vous collez le formulaire dans le même dossier ou s’il existe déjà un autre fichier portant le même nom de nœud (avec lequel il est stocké dans le référentiel CRX) dans ce dossier cible, une unité est ajoutée au suffixe (par exemple, myaf devient myaf1 et si myaf1 existe déjà au même emplacement, myaf devient myaf2). Toutes les autres propriétés restent identiques au formulaire adaptatif d’origine.

Si vous cliquez une nouvelle fois sur l’icône ![Coller](assets/Smock_Paste_18_N.svg), elle sera à nouveau masquée. Vous ne pouvez effectuer qu’une seule opération de copie à la fois. Pour créer une autre copie d’un même élément, copiez le à nouveau.

## Modification du contenu du nouveau formulaire adaptatif {#change-contents-of-new-adaptive-form}

Le contenu d’un formulaire adaptatif collé peut être modifié en utilisant les méthodes suivantes en vue de le rendre différent du formulaire copié :

1. **Modification des propriétés de métadonnées :**

   Vous pouvez modifier les propriétés de métadonnées du formulaire adaptatif ; le titre et la description, par exemple. Pour plus d’informations sur les propriétés de métadonnées et la méthode à appliquer pour les modifier, reportez-vous à la section [Gestion de métadonnées de formulaire](manage-form-metadata.md).

1. **Modification de XFA/XSD pour les formulaires adaptatifs basés sur XFA/XSD :**

   Vous pouvez modifier le XFA/XSD utilisé dans les formulaires adaptatifs. Pour savoir comment ces formulaires adaptatifs peuvent être modifiés, reportez-vous à la section [Gestion des métadonnées de formulaire](manage-form-metadata.md)

1. **Republication :**

   L’élément collé est différent de celui qui a été copié. Vous pouvez le publier en tant que nouvel élément afin de le mettre à la disposition des utilisateurs finaux. Pour savoir comment publier un fichier, <!-- see [Publishing and unpublishing forms](publishing-unpublishing-forms.md) -->
