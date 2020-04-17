---
title: Fragments de contenu - Considérations sur la suppression
description: Fragments de contenu - Considérations sur la suppression
translation-type: ht
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Fragments de contenu - Considérations sur la suppression{#content-fragments-delete-considerations}

## Autorisations - Supprimer ou ne pas supprimer {#permissions-delete-or-not-delete}

Pouvoir supprimer du contenu est une capacité puissante, mais potentiellement sensible. Pour cette raison, de nombreux secteurs d’activité doivent limiter et contrôler la manière dont ces privilèges sont distribués.

En ce qui concerne les autorisations de suppression, les fragments de contenu doivent être pris en compte à deux niveaux :

1. **Le fragment de contenu en tant qu’entité unique.**

   * **Cas d’utilisation** : un utilisateur qui a besoin de modifier/mettre à jour un fragment de contenu **et de supprimer un fragment entier**.
   * **Autorisations** : l’autorisation Supprimer peut être affectée via la gestion des utilisateurs et/ou des groupes.<!-- The [Delete](/help/sites-administering/security.md#actions) permission can be [assigned through User and/or Group Management](/help/sites-administering/security.md#managing-permissions). -->

2. **Les multiples sous-entités qui constituent un fragment de contenu ; par exemple, les variantes, les sous-nœuds.**

   Le fonctionnement de base de l’éditeur de fragment de contenu nécessite que ces sous-éléments transitoires puissent être supprimés. Par exemple, lors de la manipulation des variantes ; également lors de la modification de métadonnées ou de la gestion du contenu associé.

   * **Cas d’utilisation** : un utilisateur qui a besoin de modifier/mettre à jour un fragment de contenu, **sans être autorisé à supprimer un fragment entier**.
   * **Autorisations** : voir Autorisations requises pour la fonctionnalité d’éditeur uniquement. <!-- See [Permissions Required for Editor Functionality Only](/help/assets/content-fragments-delete.md#permissions-required-for-editor-functionality-only). -->

>[!NOTE]
>
>Lorsqu’un utilisateur ne dispose d’aucune autorisation Supprimer, l’éditeur de fragment de contenu fonctionne en mode *lecture seule*. <!-- When a user does not have any [Delete](/help/sites-administering/security.md#actions) permissions, the Content Fragment editor operates in *read-only* mode. -->

>[!NOTE]
>
>Voir également Contrôle des opérations de gestion des utilisateurs dans AEM. <!-- See also [How to Audit User Management Operations in AEM](/help/sites-administering/audit-user-management-operations.md). -->

## Autorisations requises pour la fonctionnalité d’éditeur uniquement {#permissions-required-for-editor-functionality-only}

Pour les utilisateurs qui doivent modifier/mettre à jour un fragment de contenu, **sans leur permettre de supprimer un fragment entier**, des autorisations spécifiques doivent être attribuées, car le fonctionnement de base de l’éditeur de fragment de contenu nécessite que les sous-éléments transitoires puissent être supprimés.

Par exemple, lors de la manipulation des variantes ; également lors de la modification de métadonnées ou de la gestion du contenu associé.

>[!NOTE]
>
>Les autorisations de suppression, requises pour modifier/mettre à jour un fragment de contenu, sont incluses dans l’autorisation Supprimer<!-- The delete permissions, required to edit/update a Content Fragment, are included in the Delete permission [assigned through User and/or Group Management](/help/sites-administering/security.md#managing-permissions). --> affectée via la gestion des utilisateurs et/ou des groupes. 

Les autorisations nécessaires à la modification/mise à jour d’un fragment doivent être appliquées au nœud contenant le fragment de contenu ou à un nœud parent approprié (à n’importe quel niveau sous `/content/dam`/). Lorsqu’elles sont affectées à un tel nœud parent, les autorisations sont appliquées à tous les nœuds figurant dans cette branche.

Par exemple, un dossier allant contenir tous les fragments de contenu, tels que :

* `/content/dam/contentfragments`

>[!CAUTION]
>
>La définition des autorisations sur `/content/dam` est également possible, car tous les fragments de contenu y sont stockés.
>
>Toutefois, cette action applique les mêmes autorisations de suppression à *tous* les autres types de ressources également.

Les conditions requises pour autoriser un utilisateur et/ou un groupe spécifique à modifier/mettre à jour un fragment de contenu sont les suivantes :

>[!NOTE]
>
>Cette liste répertorie tous les privilèges requis et non simplement les privilèges de suppression.

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

![cf-delete-03](assets/cf-delete-03.png)
-->
