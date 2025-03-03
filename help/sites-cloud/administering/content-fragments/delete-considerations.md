---
title: Fragments de contenu – considérations sur la suppression
description: Examinez ces points importants avant de définir vos politiques de suppression de fragments de contenu dans AEM. Les fragments de contenu forment un puissant outil de diffusion de contenu découplé. Les implications de leur suppression doivent être soigneusement examinées.
feature: Content Fragments
role: User, Developer, Architect
exl-id: d1726bff-3aa8-4758-bee7-0cacea1f660a
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 46%

---

# Considérations sur la suppression des fragments de contenu {#delete-considerations-content-fragments}

Consultez ces points importants avant de définir vos stratégies de suppression pour les fragments de contenu dans AEM. Les fragments de contenu forment un puissant outil de diffusion de contenu découplé. Les implications de leur suppression doivent être soigneusement examinées.

## Autorisations – Supprimer ou ne pas supprimer {#permissions-delete-or-not-delete}

Pouvoir supprimer du contenu est une capacité puissante, mais potentiellement sensible. Pour cette raison, de nombreux secteurs d’activité doivent limiter et contrôler la manière dont ces privilèges sont distribués.

En ce qui concerne les autorisations de suppression, les fragments de contenu doivent être pris en compte à deux niveaux :

1. **Le fragment de contenu en tant qu’entité unique.**

   * **Cas d’utilisation** : utilisateur qui doit modifier/mettre à jour un fragment de contenu - **et supprimer un fragment entier**.
   * **Autorisations** : l’autorisation Supprimer peut être affectée via la gestion des utilisateurs et/ou des groupes.

2. **Les multiples sous-entités qui constituent un fragment de contenu ; par exemple, les variations, les sous-noeuds.**

   Le fonctionnement de base de l’éditeur de fragment de contenu nécessite que ces sous-éléments transitoires puissent être supprimés. Par exemple, lors de la manipulation des variantes, mais également lors de la modification de métadonnées ou de la gestion du contenu associé.

   * **Cas d’utilisation** : utilisateur qui doit modifier/mettre à jour un fragment de contenu - **sans être autorisé à supprimer un fragment entier**.
   * **Autorisations** : voir [Autorisations requises pour la fonctionnalité d’éditeur uniquement](#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Voir aussi Contrôle des opérations de gestion des utilisateurs dans AEM.

## Autorisations requises pour la fonctionnalité d’éditeur uniquement {#permissions-required-for-editor-functionality-only}

Pour les utilisateurs qui doivent modifier/mettre à jour un fragment de contenu, **sans leur permettre de supprimer l’intégralité d’un fragment**, des autorisations spécifiques doivent être attribuées, car l’opération de base de l’éditeur de fragment de contenu nécessite que les sous-éléments transitoires puissent être supprimés.

Par exemple, lors de la manipulation des variantes, mais également lors de la modification de métadonnées ou de la gestion du contenu associé.

>[!NOTE]
>
>Les autorisations de suppression, requises pour modifier/mettre à jour un fragment de contenu, sont incluses dans l’autorisation Supprimer affectée via la gestion des utilisateurs et/ou des groupes.

Les autorisations nécessaires pour modifier/mettre à jour un fragment doivent être appliquées au noeud contenant le fragment de contenu ou à un noeud parent approprié (à n’importe quel niveau sous `/content/dam`). Lorsqu’elles sont affectées à ce nœud parent, les autorisations sont appliquées à tous les noeuds de cette branche.

Par exemple, un dossier contenant tous les fragments de contenu, comme :

* `/content/dam/contentfragments`

>[!CAUTION]
>
>La définition des autorisations sur `/content/dam` est également possible, car tous les fragments de contenu sont stockés ici.
>
>Toutefois, cette action applique les mêmes autorisations de suppression à *tous* les autres types de ressources.

Les conditions préalables aux autorisations pour permettre à un utilisateur et/ou à un groupe spécifique de modifier/mettre à jour un fragment de contenu sont les suivantes :

>[!NOTE]
>
>Cette liste répertorie tous les privilèges requis, pas uniquement les privilèges de suppression.

* Pour les nœuds ou dossiers de fragments de contenu :

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Pour le nœud `jcr:content` de tous les fragments de contenu :

   * `jcr:addChildNodes`, `jcr:modifyProperties` et `jcr:removeChildNodes`

* Pour tous les nœuds situés sous `jcr:content` de tous les fragments de contenu :

   * `jcr:addChildNodes`, `jcr:modifyProperties` et `jcr:removeChildNodes`, `jcr:removeNode`
