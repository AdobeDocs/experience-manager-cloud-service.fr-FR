---
title: Fragments de contenu - Considérations sur la suppression (Ressources - Fragments de contenu)
description: Examinez ces points importants avant de définir vos politiques de suppression de fragments de contenu dans AEM. Les fragments de contenu forment un puissant outil de diffusion de contenu découplé. Les implications de leur suppression doivent être soigneusement examinées.
exl-id: 69c08f2f-4d51-4aea-957e-ee81c4604377
feature: Content Fragments
role: User
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 92%

---

# Fragments de contenu – considérations sur la suppression {#content-fragments-delete-considerations}

Examinez ces points importants avant de définir vos politiques de suppression de fragments de contenu dans AEM. Les fragments de contenu forment un puissant outil de diffusion de contenu découplé. Les implications de leur suppression doivent être soigneusement examinées.

## Autorisations – Supprimer ou ne pas supprimer {#permissions-delete-or-not-delete}

Pouvoir supprimer du contenu est une capacité puissante, mais potentiellement sensible. Pour cette raison, de nombreux secteurs d’activité doivent limiter et contrôler la manière dont ces privilèges sont distribués.

En ce qui concerne les autorisations de suppression, les fragments de contenu doivent être pris en compte à deux niveaux :

1. **Le fragment de contenu en tant qu’entité unique.**

   * **Cas d’utilisation** : utilisateur qui doit modifier/mettre à jour un fragment de contenu - **et supprimer un fragment entier**.
   * **Autorisations** : l’autorisation Supprimer peut être affectée via la gestion des utilisateurs et/ou des groupes. <!-- The [Delete](/help/sites-administering/security.md#actions) permission can be [assigned through User and/or Group Management](/help/sites-administering/security.md#managing-permissions). -->

2. **Les multiples sous-entités qui constituent un fragment de contenu ; par exemple, les variations, les sous-nœuds.**

   Le fonctionnement de base de l’éditeur de fragment de contenu nécessite que ces sous-éléments transitoires puissent être supprimés. Par exemple, lors de la manipulation des variantes, mais également lors de la modification de métadonnées ou de la gestion du contenu associé.

   * **Cas d’utilisation** : utilisateur qui doit modifier/mettre à jour un fragment de contenu - **sans être autorisé à supprimer un fragment entier**.
   * **Autorisations** : voir [Autorisations requises pour la fonctionnalité d’éditeur uniquement](#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Lorsqu’un utilisateur ne dispose d’aucune autorisation Supprimer, l’éditeur de fragment de contenu fonctionne en mode *lecture seule*. <!-- When a user does not have any [Delete](/help/sites-administering/security.md#actions) permissions, the Content Fragment editor operates in *read-only* mode. -->

>[!NOTE]
>
>Voir également Contrôle des opérations de gestion des utilisateurs dans AEM. <!-- See also [How to Audit User Management Operations in AEM](/help/sites-administering/audit-user-management-operations.md). -->

## Autorisations requises pour la fonctionnalité d’éditeur uniquement {#permissions-required-for-editor-functionality-only}

Dans le cas des utilisateurs qui doivent modifier/mettre à jour un fragment de contenu, **sans leur permettre de supprimer l’intégralité d’un fragment**, des autorisations spécifiques doivent être attribuées, car l’opération de base de l’éditeur de fragment de contenu nécessite la possibilité de supprimer des sous-éléments transitoires.

Par exemple, lors de la manipulation des variantes, mais également lors de la modification de métadonnées ou de la gestion du contenu associé.

>[!NOTE]
>
>Les autorisations de suppression, requises pour modifier/mettre à jour un fragment de contenu, sont incluses dans l’autorisation Supprimer<!-- The delete permissions, required to edit/update a Content Fragment, are included in the Delete permission [assigned through User and/or Group Management](/help/sites-administering/security.md#managing-permissions). --> affectée via la gestion des utilisateurs et/ou des groupes. 

Les autorisations nécessaires à la modification/mise à jour d’un fragment doivent être appliquées au nœud contenant le fragment de contenu ou à un nœud parent approprié (à n’importe quel niveau sous `/content/dam`/). Lorsqu’elles sont affectées à ce nœud parent, les autorisations sont appliquées à tous les noeuds de cette branche.

Par exemple, un dossier qui contiendra tous les fragments de contenu, comme :

* `/content/dam/contentfragments`

>[!CAUTION]
>
>La définition des autorisations sur `/content/dam` est également possible, car tous les fragments de contenu y sont stockés.
>
>Toutefois, cette action applique les mêmes autorisations de suppression à *tous* les autres types de ressources.

Les autorisations nécessaires pour permettre à une personne utilisatrice et/ou à un groupe spécifique de modifier/mettre à jour un fragment de contenu sont les suivantes :

>[!NOTE]
>
>Cette liste répertorie tous les privilèges requis, pas uniquement les privilèges de suppression.

* Pour les nœuds ou dossiers de fragments de contenu :

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Pour le nœud `jcr:content` de tous les fragments de contenu :

   * `jcr:addChildNodes`, `jcr:modifyProperties` et `jcr:removeChildNodes`

* Pour tous les nœuds situés sous `jcr:content` de tous les fragments de contenu :

   * `jcr:addChildNodes`, `jcr:modifyProperties` et `jcr:removeChildNodes`, `jcr:removeNode`

<!-- There is no CRXDE Lite -->

<!--
These `remove` privileges must be [administered using Access Control Lists, within CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management). 

The `add` and `modify` privileges can also be administered in CRXDE Lite, or using the User Management console.

For example, the definition of the `remove` privileges for a group `content-authors-no-delete`:

![Remove privileges](assets/cf-delete-03.png)
-->
