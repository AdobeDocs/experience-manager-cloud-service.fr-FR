---
title: Conventions de dénomination
description: Les nœuds dans le référentiel sont soumis aux conventions de dénomination du référentiel Java Content
translation-type: tm+mt
source-git-commit: fee73b5f5ba69422494efe554ac5aa62c046ad86
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 87%

---


# Conventions de dénomination{#naming-conventions}

Les nœuds dans le référentiel sont soumis aux conventions de dénomination du référentiel Java Content. Toutefois, AEM impose d’autres conventions pour le nom des nœuds de page.

## Conventions de dénomination pour les pages {#naming-conventions-for-pages}

Ces conventions sont mises en place à différents niveaux :

* JcrUtil : implémentation AEM des [utilitaires JCR](#jcr-utilities).
* PageManager : le [Gestionnaire de pages](#page-manager) fournit des méthodes pour les opérations au niveau de la page.
* Dans l’interface utilisateur AEM {#ui-behavior}

### Utilitaires JCR {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) est l’implémentation AEM des utilitaires JCR. Les mappages de caractères contrôlés et les validations suivantes se révèlent particulièrement intéressants dans le cadre de la validation des noms :

* `isValidName`
   * Vérifie si le nom n’est pas vide et contient uniquement des caractères valides.
   * Peut être utilisé pour vérifier la validité d’un nom proposé.
* `createValidName`
   * Crée un libellé valide à partir d’une chaîne arbitraire.
   * Peut être utilisé pour créer un nom à partir d’un titre.

### Gestionnaire de pages {#page-manager}

[PageManager](https://helpx.adobe.com/fr/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) fournit des méthodes pour les opérations au niveau de la page, sur la base de [JCRUtil](#jcr-utilities).

### Comportement de l’interface utilisateur AEM {#ui-behavior}

Lors de la gestion du contenu, l’interface utilisateur AEM :

* Valide le nom en fonction des restrictions imposées par PageManager dans l’une des situations suivantes :
   * Un titre de page est fourni pour la conversion dans le nom de nœud.
   * Un nom de nœud explicite est fourni.
