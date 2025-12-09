---
title: Composant Line dans l’éditeur de communication interactive
description: Le composant Ligne dans l’éditeur de communication interactive d’AEM Forms permet aux auteurs d’insérer des lignes horizontales ou verticales dans une disposition de communication.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 11%

---


# Composant Line dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

Le composant Ligne de l’éditeur de communication interactive (IC) permet aux auteurs d’insérer des lignes horizontales ou verticales dans une disposition de communication. Ces lignes permettent de segmenter visuellement le contenu, d’améliorer la lisibilité ou de mettre en évidence la structure des formulaires. Avec des styles personnalisables tels que des lignes pleines ou des soulignements et un positionnement flexible, le composant Ligne peut être utilisé à des fins fonctionnelles et esthétiques dans la conception de formulaire.

![Rechercher un document IC](/help/forms/interactive-communication/assets/line.png)

## &#x200B;2. Propriétés

Le composant de ligne est fourni avec une plage de propriétés configurables pour définir son identité, son apparence, son emplacement et sa visibilité dans le document.

2.1. Champ De Base

- **Name :** identifiant unique utilisé en interne pour référencer le composant de ligne dans les modèles de données, les règles ou les scripts.

- **Type d’apparence :** permet de sélectionner l’aspect de la ligne dans le formulaire.

   - **Aucune :** aucune ligne n’est affichée.

   - **Zone pleine :** effectue le rendu de la ligne sous forme de zone pleine, généralement utilisée comme séparateur.

   - **Soulignement :** dessine un soulignement généralement utilisé sous les en-têtes ou les champs.

2.2. Position

- **Description :** définit l’emplacement physique de la ligne sur la disposition du formulaire.

- **Paramètres:**

   - Coordonnées **X et Y :** permet de définir le positionnement horizontal et vertical.

   - **Hauteur et largeur :** définissez la longueur et l’épaisseur de la ligne (en mm).

2.3. Marge

- **Description :** ajoute une marge intérieure ou un espacement autour du composant de ligne pour contrôler la densité de disposition.

- **Options:**

   - Haut

   - Bas

   - Gauche

   - Droite

2.4. Apparence

- **Description :** permet que le style de la ligne corresponde à la conception du document.

- **Options:**

   - **Trait :** définit la couleur et l’épaisseur du trait.

   - **Largeur :** détermine la largeur de la ligne sur le formulaire.

   - **Style :** choisissez entre les styles de tirets, de pointillés ou de traits continus.

2.5. Présence

- **Description :** contrôle la visibilité du composant de ligne pendant l’exécution.

- **Options:**

   - **Visible :** la ligne est rendue sur la sortie finale.

   - **Masqué :** la ligne n’est pas affichée, mais son espace de mise en page est conservé.

## &#x200B;3. Utilisation

Le composant Ligne est souvent utilisé pour :

- Division visuelle de sections dans un formulaire long

- Souligner les en-têtes ou les libellés pour mettre en évidence

- Création de bordures ou de zones autour de groupes de champs

- Améliorer la hiérarchie visuelle de la mise en page des communications

## &#x200B;4. Bonnes Pratiques

- Utilisez des styles de ligne cohérents dans l’ensemble du formulaire pour conserver un aspect professionnel.

- Ajustez les marges pour éviter l&#39;encombrement visuel et assurer l&#39;alignement.

- Choisissez les paramètres de contour et de style appropriés pour correspondre à la conception de la marque ou du document.

- Masquez les lignes inutiles pour éviter les distractions tout en préservant l’espacement des mises en page.

Le composant Line de l’éditeur de communication interactive est un élément de conception simple mais puissant. Utilisé stratégiquement, il améliore la structure visuelle des documents de communication, aidant ainsi les utilisateurs à mieux naviguer dans le contenu et assurant une mise en page plus épurée et plus soignée.


