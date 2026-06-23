---
title: Objet de champ de date dans l’éditeur de communication interactive
description: L’objet de champ de date dans l’éditeur de communication interactive d’AEM Forms permet aux auteurs d’insérer un champ de sélection de date basé sur un calendrier dans un document.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: f8cc1dd1-3b55-4cd9-b051-959c88195eb4
source-git-commit: 53ff71c82d35b9ec9b20b521ef469d3f0abd79df
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 5%

---

# Objet de champ de date dans l’éditeur de communication interactive


## &#x200B;1. Présentation

Le composant **Champ de date** de l’éditeur de communication interactive permet aux auteurs d’insérer un champ de sélection de date basé sur un calendrier dans un document. Cela permet aux utilisateurs de sélectionner facilement une date dans un sélecteur de date ou de la saisir manuellement dans un format prédéfini.

Idéal pour capturer les dates de naissance, les horaires de rendez-vous, les dates de candidature ou les dates de début/fin des politiques, le champ de date améliore la précision et réduit les erreurs de saisie. Il prend en charge la mise en forme, le style et la liaison de données pour une intégration transparente aux modèles de données et aux systèmes principaux.

![Rechercher un document IC](/help/forms/interactive-communication/assets/date.png)

## &#x200B;2. Afficher le modèle

Vous pouvez affecter un **modèle d’affichage** à un champ de date à partir du panneau **Propriétés**, par exemple : **1er avril 2007** ou **01/04/2007**.

Le modèle configuré est immédiatement répercuté dans l’aperçu de la zone de travail et est conservé pendant les cycles d’enregistrement et de rechargement. Pour les cas d’utilisation avancés, vous pouvez définir une **clause d’image XFA personnalisée** afin d’obtenir le format de sortie souhaité.

### Configuration d’un modèle d’affichage

1. Sélectionnez le composant Champ de date dans la zone de travail de conception.
2. Ouvrez le panneau **Propriétés**.
3. Dans la section **Motif d’affichage**, choisissez un motif prédéfini ou saisissez une clause d’image personnalisée.
4. Prévisualisez la valeur formatée sur la zone de travail.

### Exemple de modèle personnalisé (Date)

| Modèle | Exemple de sortie | Description |
|---------|----------------|-------------|
| `date{DD/MM/YYYY}` | 01/04/2007 | Jour/mois/année |

**Jetons de date courants :**

| Jeton | Signification |
|-------|---------|
| D, DD | Jour |
| M, MM, MM, MMMM | Mois |
| YYY, YYYY | Année |
| EEEE | Jour de la semaine |

>[!NOTE]
>
> Pour que les modèles d’affichage s’affichent correctement, les valeurs des champs de date sous-jacents doivent être conformes à la norme **ISO 8601**. Indiquez les valeurs au format **AAAA-MM-JJ** (par exemple, `2007-04-01`). Les valeurs qui ne respectent pas ce format sont affichées en l’état, sans formatage de modèle appliqué.

## &#x200B;3. Propriétés

L’objet Champ de date comprend plusieurs propriétés configurables :

2.1. Champ de base

- **Name :** identifiant unique utilisé pour référencer le champ dans des règles, des scripts et des modèles de données.

- **Légende :** libellé affiché pour l’utilisateur ou l’utilisatrice (par exemple, « Date de naissance »).

- **Date :** valeur de date réelle, qui peut être vide par défaut ou préremplie à l’aide de données dynamiques.

- **Réserver :** une date de secours facultative (affichée si aucune date n’est sélectionnée ou si des données ne sont pas disponibles).

- **Apparence :** un paramètre prédéfini de style rapide (par exemple, souligné, plat, bordé) pour une meilleure cohérence visuelle.

2.2. Typographie

Contrôle l’affichage de la date dans le champ :

- **Variation de police :** sélectionnez la famille de polices, l’épaisseur (par exemple, Standard, Gras) et le style (par exemple, Italique).

- **Taille :** généralement définie sur 10 pt par défaut, mais personnalisable par souci de cohérence avec le contenu environnant.

2.3. Position

Définit l&#39;emplacement dans la mise en page du document :

- Coordonnées **X et Y :** détermine le positionnement horizontal et vertical.

- **Largeur et Hauteur :** définissez en millimètres ou en pourcentages pour vous aligner sur les autres éléments de formulaire.

2.4. Marge

Spécifie l&#39;espacement autour des limites du champ :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

Ces valeurs permettent un alignement précis dans les sous-formulaires ou les grilles de disposition.

2.5. Aspect

Définit le style visuel du conteneur de champs :

- **Remplissage :** couleur d’arrière-plan du champ (blanc, gris clair, par exemple).

- **Contour :** couleur ou contour de la bordure.

- **Largeur:** Épaisseur de la bordure du champ.

- **Style :** options de trait plein, en tirets ou en pointillés.

- **Arêtes :** personnalisez les coins comme étant arrondis ou nets pour différentes préférences de conception.

2.6. Présence

Détermine comment et quand le champ s’affiche :

- **Visible :** paramètre par défaut où le champ s’affiche au moment de l’exécution.

- **Caché (conserve l’espace) :** le champ reste invisible, mais l’espace de disposition est conservé.

Cela s’avère utile pour activer dynamiquement la visibilité en fonction des entrées ou des règles de l’utilisateur.

2.7. Liaison de données

Connecte le champ de date aux structures de données pour stocker ou préremplir des valeurs.

**Type de liaison de données :**

- **Utiliser le nom :** lie le champ au schéma à l’aide de son attribut name.

- **Utiliser des données globales :** lie à l’aide d’un modèle de données ou d’un élément de schéma prédéfini.

- **Aucune liaison de données :** le champ reste statique, n’est connecté à aucune source de données.

Cela permet de récupérer, d’afficher ou de stocker des valeurs de date dynamiques en fonction de la logique de l’application.

## &#x200B;4. Utilisation

Le champ de date est particulièrement utile dans les scénarios suivants :

- Capture de la date de naissance ou de jointure dans les formulaires d’intégration.

- la sélection des dates de début et de fin des services, des abonnements ou des événements ;

- Saisir les dates limites de candidature, les créneaux horaires ou les dates de vérification.

Les auteurs peuvent placer le champ de date dans des conteneurs de disposition ou des sous-formulaires, puis configurer la validation (format de date, limites de plage, etc.) pour améliorer la qualité des données.

## &#x200B;5. Bonnes pratiques

- Utilisez des légendes claires telles que « Date de début » ou « Sélectionner la date du rendez-vous » pour une meilleure expérience utilisateur.

- Définissez des périodes minimales et maximales pour empêcher toute entrée non valide (par exemple, une future BD).

- Appliquez des styles de police cohérents (10 points recommandés) pour faciliter la lecture.

- Liez les champs au schéma là où l’intégration des données principales est nécessaire.

- Masquez dynamiquement les champs de date non pertinents à l’aide des règles de visibilité.

L’objet **Champ de date** dans l’éditeur de communication interactive est un outil puissant permettant de capturer facilement et avec précision des données sensibles à l’heure. Lorsqu’il est stylisé de manière réfléchie et connecté à des chemins de données significatifs, il prend en charge une expérience utilisateur transparente et un traitement efficace des entrées temporelles.

## Voir également

- [Composant de zone de texte](/help/forms/interactive-communication/text-box.md)
- [Composant de champ numérique](/help/forms/interactive-communication/numeric-field.md)
- [Composant De Champ Date/Heure](/help/forms/interactive-communication/date-time-field.md)
- [Composant de variable non lié](/help/forms/interactive-communication/unbound-variable.md)
- [Configurer la liaison de données dans l’éditeur de communication interactive](/help/forms/interactive-communication/configure-data-binding.md)
- [Utiliser l’éditeur de règles dans l’éditeur de communication interactive](/help/forms/interactive-communication/use-the-rule-editor.md)

