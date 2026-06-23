---
title: Composant de variable non lié dans l’éditeur de communication interactive
description: Le composant Variable indépendante dans l’éditeur de communication interactive vous permet d’afficher des valeurs calculées, scriptées ou définies indépendamment avec un contrôle complet de la mise en forme.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="S’applique à AEM Forms)."
exl-id: unbound-variable-ic-editor
source-git-commit: ea372529b504ed70b74171e75d1d54f98fef432c
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 3%

---


# Composant de variable non lié dans l’éditeur de communication interactive


## &#x200B;1. Présentation

Le composant **Variable non liée** de l’éditeur de communication interactive (IC) vous permet de placer un champ dont la valeur n’est liée à aucun modèle de données externe ou nœud de schéma. Au lieu de cela, la valeur est fournie par le biais d’un script, d’un calcul basé sur des règles ou d’une valeur statique par défaut, ce qui fait de ce composant le bon choix chaque fois que vous avez besoin d’une valeur d’affichage calculée ou intermédiaire qui ne provient pas directement d’une source de données liée.

Étant donné qu’une variable non liée n’est pas connectée à un modèle de données de formulaire, elle vous permet de contrôler entièrement la création de la valeur au moment de la conception et de l’exécution. Vous pouvez l’utiliser pour afficher des totaux calculés, des numéros de référence générés dynamiquement, des résultats de formule intermédiaires ou toute autre valeur générée par votre moteur de règles.

Le composant prend en charge les quatre types de données **Texte**, **Numérique**, **Date** et **Date/Heure**. Le type de données actif détermine la syntaxe du modèle d’affichage et les symboles des clauses d’image à appliquer.

## &#x200B;2. Afficher le modèle

Vous pouvez affecter un **modèle d’affichage** à un champ Variable non lié à partir du panneau **Propriétés**, à l’aide des mêmes contrôles de modèle d’affichage que ceux disponibles pour les composants Zone de texte, Champ numérique, Champ de date et Champ date/heure. Cela permet une présentation formatée des valeurs calculées ou référencées dans l’aperçu de la zone de travail et dans la sortie générée.

Le modèle configuré est immédiatement répercuté dans l’aperçu de la zone de travail et est conservé pendant les cycles d’enregistrement et de rechargement.

### Configuration d’un modèle d’affichage

1. Sélectionnez le composant Variable non liée sur la zone de travail de conception.
2. Ouvrez le panneau **Propriétés**.
3. Dans la section **Motif d’affichage**, choisissez un motif prédéfini ou saisissez une clause d’image personnalisée.
4. Prévisualisez la valeur formatée sur la zone de travail.

### Choisir le bon modèle

Étant donné qu’une variable non liée peut contenir n’importe quel type de données, la syntaxe de clause d’image que vous utilisez doit correspondre au type de données configuré du champ :

| Type de données du champ | Syntaxe du motif | Exemple de sortie | Référence |
|-----------------|----------------|----------------|-----------|
| Texte | `text{…}` | (555) 123-4567 | [Zone de texte — Modèle d&#39;affichage](/help/forms/interactive-communication/text-box.md#2-display-pattern) |
| Numérique | `num{…}` | $1,234.21 | [Champ numérique — Modèle d&#39;affichage](/help/forms/interactive-communication/numeric-field.md#2-display-pattern) |
| Date | `date{…}` | 01/04/2007 | [Champ de date — Modèle d’affichage](/help/forms/interactive-communication/date-field.md#2-display-pattern) |
| Date/Heure | `date{…} time{…}` | 04/01/2007 14:30 | [Champ Date/Heure — Modèle D’Affichage](/help/forms/interactive-communication/date-time-field.md#2-display-pattern) |

>[!NOTE]
>
> Si le type de données du champ est Date ou Date/Heure, la valeur sous-jacente doit être conforme au format **ISO 8601** (`YYYY-MM-DD` ou `YYYY-MM-DDTHH:MM`). Les valeurs qui ne suivent pas ce format sont affichées en l’état, sans modèle d’affichage appliqué.

## &#x200B;3. Propriétés

Le composant Variable non liée partage un jeu de propriétés commun avec d’autres composants de champ, avec une distinction clé : il ne dispose d’aucune option de liaison de données externe, car, par définition, sa valeur est non liée à toute source de données.

3.1 Champ de base

- **Name :** identifiant unique de la variable. Utilisé pour le référencer dans les règles, scripts et expressions au sein de l’IC.

- **Type de données :** indique le type de valeur que cette variable contient **Texte**, **Numérique**, **Date** ou **Date/Heure**. Le type de données sélectionné détermine la syntaxe du modèle d’affichage à appliquer et la manière dont la valeur est validée.

- **Légende :** libellé affiché à côté du champ sur la zone de travail (par exemple, « Total calculé » ou « Numéro de référence »).

- **Valeur :** valeur par défaut ou calculée affichée dans le champ. Dans la plupart des cas, cette opération est définie par programmation à l’aide de l’éditeur de règles ou d’un script, plutôt que saisie manuellement.

- **Réserve :** valeur de secours affichée lorsqu’aucune valeur calculée n’est disponible. Utile pour une sortie en impression seule ou en lecture seule lorsqu’un champ vide est inacceptable.

- **Apparence :** paramètre prédéfini de style visuel (Aucun, Zone pleine ou Soulignement) pour le conteneur de champs.

3.2 Typographie

Contrôle le style de la valeur affichée :

- **Variation de police :** sélectionnez la famille de polices, l’épaisseur (standard, gras) et le style (italique) pour correspondre au contenu environnant.

- **Taille de police :** généralement définie sur 10 pt par défaut ; à ajuster pour maintenir la cohérence visuelle avec le reste de la communication.

3.3 Position

Définit l’emplacement du composant sur la zone de travail :

- Coordonnées **X et Y :** définissez la position horizontale et verticale exacte.

- **Largeur et Hauteur :** spécifiez les dimensions en millimètres pour l’alignement avec les éléments adjacents.

3.4 Marge

Définit l’espacement autour de la limite du composant :

- Haut (Haut)

- Bas (Bas)

- Gauche

- Droite

3.5 Apparence

Définit le style du conteneur de champs :

- **Remplir :** couleur d’arrière-plan du champ.

- **Tracé :** bordure autour du champ, avec les options suivantes :

   - **Largeur:** Épaisseur de la bordure.

   - **Style :** uni, en tirets ou en pointillés.

   - **Edge :** coins arrondis ou nets.

3.6 Présence

Contrôle la visibilité au moment de l’exécution :

- **Visible :** le champ s’affiche et occupe l’espace de disposition.

- **Masqué (conserve l’espace) :** le champ est invisible, mais son espace de disposition est conservé, ce qui est utile pour activer/désactiver la visibilité de manière dynamique à l’aide de l’éditeur de règles.

## &#x200B;4. Utilisation

Utilisez une variable non liée lorsque la valeur que vous souhaitez afficher est :

- **Calculé par une règle ou un script** par exemple, un total cumulé, un calcul de taxe ou un montant de remise dérivé d&#39;autres valeurs de champ.

- **Généré par programmation** par exemple, un numéro de référence ou un code de suivi affecté au moment de l’exécution par la logique du serveur principal.

- **Non disponible dans le modèle de données** par exemple, un résultat intermédiaire significatif à l’écran mais qui n’existe pas en tant que champ de schéma.

- **Visible sous condition** : affichez un message ou une valeur calculée uniquement lorsque des conditions spécifiques sont remplies, à l’aide de l’éditeur de règles pour définir la visibilité et la valeur ensemble.

Vous pouvez placer une variable non liée dans des sous-formulaires, des conteneurs de mises en page ou directement sur la zone de travail de conception. Combinez-le avec l’éditeur de règles pour écrire des expressions qui calculent sa valeur en fonction d’autres champs liés dans l’IC.

## &#x200B;5. Bonnes pratiques

- **Définissez une valeur de réserve significative** de sorte que la sortie d’impression et les aperçus en lecture seule n’affichent jamais de champ vide lorsque la valeur calculée n’est pas disponible.

- **Faire correspondre le type de données à la sortie** — si vous calculez un montant en devise, définissez le type de données sur Numérique et appliquez un modèle d&#39;affichage numérique ; si vous calculez une date, définissez-la sur Date et assurez-vous que l&#39;entrée est ISO 8601.

- **Utiliser une légende claire** — comme la valeur est calculée et n’est pas directement reconnaissable à partir d’un libellé, une légende descriptive (par exemple, « Sous-total (calculé) ») évite toute confusion pour les réviseurs et les utilisateurs finaux.

- **Évitez de surutiliser des variables non liées pour les données qui appartiennent au modèle** — si une valeur peut raisonnablement être ajoutée au modèle de données de formulaire, préférez lier un champ standard. Réservez les variables non liées pour les valeurs véritablement transitoires ou dérivatives.

- **Documentez vos expressions** — ajoutez un commentaire dans l’éditeur de règles décrivant ce que calcule chaque variable non liée, de sorte que la logique reste gérable lorsque l’IC est modifié ultérieurement.

## Voir également

- [Composant de zone de texte](/help/forms/interactive-communication/text-box.md) — syntaxe de modèle d&#39;affichage des valeurs de texte
- [Composant de champ numérique](/help/forms/interactive-communication/numeric-field.md) : syntaxe de modèle d’affichage des valeurs numériques et monétaires
- [Composant de champ de date](/help/forms/interactive-communication/date-field.md) — syntaxe de modèle d’affichage des dates
- [Composant de champ date/heure](/help/forms/interactive-communication/date-time-field.md) : syntaxe de modèle d’affichage pour les valeurs de date et d’heure combinées
- [Utiliser l’éditeur de règles dans l’éditeur de communication interactive](/help/forms/interactive-communication/use-the-rule-editor.md) — écrivez des expressions pour calculer et affecter des valeurs aux variables non liées
- [Configurer la liaison de données dans l’éditeur de communication interactive](/help/forms/interactive-communication/configure-data-binding.md)
