---
title: Composant de zone de texte dans l’éditeur de communication interactive
description: Le composant Zone de texte dans l’éditeur de communication interactive d’AEM Forms permet aux auteurs de saisir et d’afficher du contenu texte dans une communication.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: 6bed824c-b959-4882-a5aa-dbb7fbf2f8a0
source-git-commit: ea372529b504ed70b74171e75d1d54f98fef432c
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 4%

---

# Composant de zone de texte dans l’éditeur de communication interactive


## &#x200B;1. Présentation

Le composant **Zone de texte** de l’éditeur de communication interactive permet aux auteurs de saisir et d’afficher du contenu textuel dans une communication. Il s’agit de l’un des composants les plus fondamentaux et les plus utilisés, généralement utilisé pour collecter des noms, des commentaires, des commentaires ou des données personnalisées lors de la conception de communications interactives ou de fragments de communication.

La zone de texte prend en charge la **liaison de données**, ce qui permet aux auteurs de combiner facilement du contenu statique et dynamique, par exemple : ***« Nom de l’utilisateur : @name« &#x200B;***, où @name est un champ de données lié qui est renseigné dynamiquement lorsque le document est enregistré en tant que PDF. En outre, il prend en charge la mise en forme de texte enrichi et un positionnement flexible pour un contrôle de disposition précis.

![Rechercher document IC](/help/forms/interactive-communication/assets/textbox.png)

## &#x200B;2. Afficher le modèle

Vous pouvez affecter un **modèle d’affichage** à un champ de zone de texte à partir du panneau **Propriétés**. Les modèles d’affichage contrôlent la manière dont les valeurs de champ sont présentées aux utilisateurs finaux dans l’aperçu de la zone de travail et dans la sortie générée, par exemple en masquant une entrée de texte comme numéro de téléphone : **(555) 123-4567**.

Le modèle configuré est immédiatement répercuté dans l’aperçu de la zone de travail et est conservé pendant les cycles d’enregistrement et de rechargement. Pour les cas d’utilisation avancés, vous pouvez définir une **clause d’image XFA personnalisée** afin d’obtenir le format de sortie souhaité.

### Configuration d’un modèle d’affichage

1. Sélectionnez le composant Zone de texte dans la zone de travail de conception.
2. Ouvrez le panneau **Propriétés**.
3. Dans la section **Motif d’affichage**, choisissez un motif prédéfini ou saisissez une clause d’image personnalisée.
4. Prévisualisez la valeur formatée sur la zone de travail.

### Exemple de modèle personnalisé (texte)

| Modèle | Exemple de sortie | Description |
|---------|----------------|-------------|
| `text{(999) 999-9999}` | (555) 123-4567 | Masque des numéros de téléphone |

**Symboles de clause d’image (texte) :**

| Symbole | Signification |
|--------|---------|
| 9 | Correspond à un chiffre |
| A | Correspond à une lettre |
| O | Correspond à l’alphanumérique |
| X | Correspond à n’importe quel caractère |

### Bonnes pratiques

- Choisissez un modèle qui correspond à la façon dont les utilisateurs finaux s’attendent à lire la valeur (téléphone, ID, code postal).
- Validez les exemples de données dans l’aperçu de la zone de travail avant la publication.
- Utilisez des clauses d’image personnalisées uniquement lorsque les modèles prédéfinis ne répondent pas à vos besoins de mise en forme.

## &#x200B;3. Propriétés

Le composant de zone de texte fournit un large ensemble de propriétés pour vous aider à configurer son aspect, son toucher et son comportement.

2.1 Typographie

**Famille de polices :** permet de sélectionner des styles de polices tels qu’Arial, Helvetica, Times New Roman, etc.

**Validation des polices :** des contraintes d’entrée facultatives peuvent être appliquées pour vous assurer que seuls les formats texte, numérique ou spéciaux sont acceptés.

**Alignement du texte :** les options comprennent l’alignement à gauche, à droite, centré ou justifié.

**Style de texte :** activez la mise en forme du texte avec les fonctions gras, italique, barré et souligné.

**Listes :** prend en charge l’insertion de listes triées (numérotées) et non triées (à puces).

2.2 Position

**Largeur et Hauteur :** permet de définir les dimensions de la zone de texte en pixels ou en pourcentage par rapport au conteneur.

2.3 Marge

Définissez l’espacement autour de la zone de texte :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

2.4 Apparence

- **Remplissage du texte :** personnalisez la couleur et la transparence du texte.

- **Remplissage :** définit la couleur d’arrière-plan de la zone de texte.

- **Contour :** Ajouter des bordures avec personnalisable :

   - Largeur (épaisseur)

   - Style (trait plein, tirets, pointillés)

   - Edge (coins arrondis ou nets)

2.5 Présence

**Visible :** paramètre par défaut ; la zone de texte est affichée pour l’utilisateur.

**Masqué :** la zone de texte est incluse dans le formulaire, mais n’est pas affichée.



## &#x200B;4. Utilisation

La zone de texte est utilisée pour :

- Collecter des informations client telles que des noms, des commentaires ou des commentaires.

- Saisir des valeurs alphanumériques.

- Intégration de messages personnalisés à l’aide de modèles de données liés.

- Incorporation dans des fragments pour une utilisation répétée dans des documents.

Les auteurs peuvent faire glisser la zone de texte de la bibliothèque de composants vers le mode Création ou le mode Maître et configurer son comportement à l’aide du panneau Propriétés.

## &#x200B;5. Bonnes pratiques

- Associez toujours les zones de texte à des libellés de champ significatifs pour améliorer l’accessibilité.

- Utilisez des validations d’entrée appropriées pour éviter les erreurs de saisie de données.

- Garantissez une disposition réactive en définissant des marges et des largeurs relatives aux conteneurs parents.

- Évitez les styles de police excessifs qui pourraient nuire à la lisibilité.

En configurant les propriétés de la zone de texte de manière approfondie, les auteurs peuvent créer des expériences de communication interactives, réactives et conviviales dans l’éditeur de communication interactive d’AEM.

## Voir également

- [Composant de champ numérique](/help/forms/interactive-communication/numeric-field.md)
- [Composant de champ de date](/help/forms/interactive-communication/date-field.md)
- [Composant De Champ Date/Heure](/help/forms/interactive-communication/date-time-field.md)
- [Composant de variable non lié](/help/forms/interactive-communication/unbound-variable.md)
- [Configurer la liaison de données dans l’éditeur de communication interactive](/help/forms/interactive-communication/configure-data-binding.md)
- [Utiliser l’éditeur de règles dans l’éditeur de communication interactive](/help/forms/interactive-communication/use-the-rule-editor.md)
