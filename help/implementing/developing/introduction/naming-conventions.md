---
title: Conventions de dénomination
description: Les nœuds dans le référentiel sont soumis aux conventions de dénomination de Java Content Repository
exl-id: 3c5c39dd-b209-488b-a93e-e840786fe224
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 53%

---

# Conventions de dénomination{#naming-conventions}

Les nœuds dans le référentiel sont soumis aux conventions de dénomination de Java Content Repository. Toutefois, AEM impose d’autres conventions pour le nom des nœuds de page.

## Conventions de dénomination pour les pages {#naming-conventions-for-pages}

Ces conventions de dénomination sont mises en oeuvre à différents niveaux :

* JcrUtil : la mise en oeuvre AEM de la [Utilitaires JCR](#jcr-utilities).
* PageManager : la valeur [Gestionnaire de pages](#page-manager) fournit des méthodes pour les opérations au niveau de la page.
* Dans l’interface utilisateur d’AEM {#ui-behavior}

### Utilitaires JCR {#jcr-utilities}

[JcrUtil](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/jcr/JcrUtil.html) est l’implémentation AEM des utilitaires JCR. Les mappages de caractères qu’il contrôle et les validations suivantes présentent un intérêt particulier pour la validation des noms :

* `isValidName`
   * Vérifie si le nom n’est pas vide et contient uniquement des caractères valides.
   * Peut être utilisé pour vérifier si un nom proposé est valide.
* `createValidName`
   * Crée un libellé valide à partir d’une chaîne arbitraire.
   * Peut être utilisé pour créer un nom à partir d’un titre.

### Gestionnaire de pages {#page-manager}

[PageManager](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html) fournit des méthodes pour les opérations au niveau de la page, sur la base de [JCRUtil](#jcr-utilities).

### Comportement de l’interface utilisateur d’AEM {#ui-behavior}

Au cours de la gestion du contenu, l’interface utilisateur AEM :

* Valide le nom en fonction des restrictions imposées par PageManager lorsque :
   * un titre de page est fourni pour la conversion dans le nom de noeud.
   * un nom de noeud explicite est fourni.
