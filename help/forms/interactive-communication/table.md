---
title: Composant Tableau dans l’éditeur de communication interactive
description: Le composant Tableau dans l’éditeur de communication interactive d’AEM Forms permet aux auteurs d’insérer facilement des tableaux personnalisables dans les modèles de communication.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: e651869132a232db577e94946c082c46eea26bb3
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 8%

---


# Composant Tableau dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

Le composant Tableau de l’éditeur de communication interactive (IC) permet aux auteurs d’insérer facilement des tableaux personnalisables dans les modèles de communication. Ce composant prend en charge la représentation tabulaire des données pour des cas d’utilisation tels que des résumés, des listes d’éléments, des entrées structurées ou des mises en page de comparaison.

Les auteurs peuvent faire glisser et déposer le composant de tableau dans la zone de travail, configurer le nombre de lignes et de colonnes et choisir des options telles que l’inclusion de lignes d’en-tête et de pied de page ou la définition de l’orientation de mise en page. Les tableaux peuvent être définis comme des modèles par défaut par souci de cohérence entre plusieurs communications.

![Rechercher un document IC](/help/forms/interactive-communication/assets/table.png)

## &#x200B;2. Propriétés

Le composant Tableau comprend plusieurs propriétés configurables pour aider les auteurs à personnaliser le comportement et l’aspect du tableau :


2.1 Champ de base

- **Name :** identifiant unique de la table. Ce nom est utilisé en interne pour référencer la table dans les modèles de données et la logique.

- **Lignes :** indique le nombre de lignes de contenu (à l’exclusion de l’en-tête et du pied de page).

- **Colonnes :** permet de définir le nombre de colonnes du tableau.

- **Ligne d’en-tête :** option permettant d’inclure une ligne d’en-tête en haut du tableau pour les libellés des colonnes.

- **Ligne de pied de page :** option permettant d’inclure une ligne de pied de page pour les totaux ou les valeurs de synthèse.

- **Définir comme valeur par défaut :** permet aux utilisateurs d’enregistrer la configuration actuelle en tant que modèle de tableau par défaut en vue d’une utilisation ultérieure.

- **Direction de mise en page :** définit la façon dont les lignes sont renseignées, généralement définie de gauche à droite.

2.2 Position

- **Description :** contrôle le placement du tableau dans la mise en page.

- **Paramètres:**

   - Coordonnées **X et Y :** permet de définir les positions horizontale (X) et verticale (Y) du tableau sur la zone de travail.

   - **Hauteur et largeur :** définit la taille globale du tableau (en mm), ce qui permet une allocation d’espace flexible.

2.3 Apparence

**Apparence :** permet de définir le style visuel du tableau. Les auteurs peuvent choisir parmi des paramètres prédéfinis, tels que bordé, plat ou élevé.

- **Remplissage :** couleur d’arrière-plan du tableau ou des cellules.

- **Contour :** couleur de bordure autour du tableau ou de cellules spécifiques.

- **Largeur :** Épaisseur des lignes de bordure.

- **Style :** sélectionnez les types d’arêtes : coins arrondis ou angles vifs.

- **Arêtes :** permet de configurer la visibilité des bordures des cellules et du rayon des angles.

2.4 Présence

- **Description :** détermine la visibilité de la table au moment de l’exécution.

- **Options:**

   - **Visible :** permet d’afficher le tableau normalement dans la sortie.

   - **Masqué :** masque le tableau tout en conservant un espace dans la mise en page.

2.5 Liaison de données

**Liaison de données :** connectez la table à une source de données (par exemple, JSON, schéma XML) pour remplir dynamiquement les lignes et les colonnes avec des valeurs pendant la génération. Cela s’avère utile pour la facturation détaillée, les enregistrements de transaction ou les listes de produits.

## &#x200B;3. Utilisation

Le composant Tableau est idéal pour afficher des informations structurées ou répétitives. Les cas d’utilisation standard incluent :

- Factures et factures avec lignes d&#39;article

- Comparaison de politiques ou de plans

- Résumés des données de profil ou de compte

- Catalogues de produits ou matrices de fonctionnalités

Les auteurs peuvent configurer le nombre de lignes et de colonnes, appliquer une visibilité conditionnelle ou lier les données pour afficher des informations dynamiques.

## &#x200B;4. Bonnes Pratiques

- Utilisez les lignes d’en-tête pour étiqueter clairement chaque colonne afin d’en améliorer la lisibilité.

- Appliquez des lignes de pied de page pour les totaux ou les notes importantes, le cas échéant.

- Tirez parti de la liaison de données pour renseigner les lignes de manière dynamique en fonction d’une entrée structurée.

- Conservez la cohérence du style et de l’espacement à l’aide des paramètres d’apparence et de marge .

- Lorsque vous masquez un tableau, assurez la continuité de la mise en page en choisissant de conserver ou non de l’espace.

- Utilisez des modèles par défaut pour normaliser le contenu tabulaire dans les documents.

Le composant Tableau de l’éditeur IC est un composant flexible et convivial conçu pour prendre en charge le contenu structuré dans vos communications . Grâce aux options de disposition personnalisables, aux fonctionnalités de style et à la puissante liaison de données, il permet aux auteurs de présenter les informations de manière claire et efficace.


