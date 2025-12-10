---
title: Créer un fragment de communication interactive
description: Créez des fragments de communication interactive dans AEM Forms pour créer des blocs de contenu modulaires réutilisables qui garantissent la cohérence, gagnent du temps et prennent en charge les communications personnalisées basées sur les données.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 19270498fa60f860b31400ad40705ecd2f821cf8
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 10%

---


# Liaison de données dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## &#x200B;1. Présentation

La liaison de données dans l’éditeur de communication interactive connecte les champs de la zone de travail à une couche de données régie afin que les communications s’affichent avec des informations contextuelles réelles. En liant les composants à un modèle de données de formulaire (FDM), les auteurs peuvent garantir la précision, réduire le travail manuel et offrir des expériences dynamiques et personnalisées.

Au-delà de la simple connexion de valeurs, la liaison de données dans IC prend en charge le mappage visuel, le préremplissage et la synchronisation, ce qui permet aux auteurs de concevoir plus rapidement tout en restant alignés sur les systèmes principaux et les modèles de données.

![Rechercher document IC](/help/forms/interactive-communication/assets/data-binding1.png)

## &#x200B;2. Propriétés

2.1 Gestion des connexions aux données (FDM)

- **Sélectionner le FDM :** sélectionnez le modèle de données de formulaire approprié (par exemple, clients, comptes ou politiques). Cela établit le schéma faisant autorité pour les champs, les tableaux et les objets utilisés dans la communication.

- **Créer une liaison de données :** une fois les liaisons activées, chaque champ peut être associé à des chemins FDM, ce qui réduit les erreurs et garantit une intégration cohérente.

- **Liaison de champs au modèle de données :** pointez les champs vers des nœuds spécifiques (par exemple, customer.name, policy.holder.id) pour orienter le rendu avec des données actives et pour prendre en charge les validations ou la logique conditionnelle.

2.2 Création de liaisons de données

- **Mappage visuel :** le mappage par glisser-déposer entre les champs et les nœuds FDM permet aux utilisateurs n’ayant pas de connaissances techniques d’éviter les erreurs.

- **Association de champs :** permet de définir le chemin d’accès de la cible, le type de données (texte, nombre, date, valeur booléenne, image) et les formateurs facultatifs (par exemple, masque de date, devise).

- **Aperçu des liaisons :** testez les liaisons avec des exemples de jeux de données pour valider la mise en forme et l’exactitude avant la publication.

## &#x200B;3. Utilisation

La liaison de données est généralement utilisée lorsque les communications doivent afficher des enregistrements faisant autorité ou capturer des entrées utilisateur. Voici quelques exemples :

- **Personalization :** renseignez les détails du client tels que le nom, l’adresse ou le solde du compte.

- **Contenu conditionnel :** permet d’afficher ou de masquer des sections en fonction des valeurs du modèle (par exemple, clients actifs ou inactifs).

- **Collections et tableaux :** permet de générer des historiques, des transactions ou des listes d’énumération à partir de tableaux.

- **Images et médias :** lier des photos de profil, des logos d’entreprise ou des images de produit.

- **Vérifier et eSign :** préremplir les formulaires avec des données et autoriser les mises à jour par une synchronisation bidirectionnelle.

Les auteurs sélectionnent généralement le FDM au début du projet, mappent visuellement les champs pendant la conception et testent avec des exemples de données avant de le publier.

## &#x200B;4. Bonnes Pratiques

- **Définir le schéma au plus tôt :** finalisez le FDM avant la liaison pour éviter tout remappage ultérieur.

- **Utiliser le mappage visuel :** permet d’éviter les fautes de frappe et les correspondances de chemins d’accès en effectuant un glisser-déposer.

- **Valider les types de données :** appliquez des formateurs pour la devise, les dates ou les numéros de téléphone afin d’assurer la cohérence.

- **Garder les liaisons explicites :** chaque champ doit correspondre clairement à un seul nœud de données.

- **Test avec des exemples de données :** prévisualisez les cas communs et les cas de périphérie (par exemple, valeurs vides, tableaux longs).

- **Limiter la synchronisation bidirectionnelle :** à utiliser uniquement lorsque des modifications ou des approbations sont requises.

- **Modulariser les collections :** permet d’utiliser des lignes de modèle pour les structures répétables.

- **Sécuriser les données sensibles :** appliquer le masquage, le chiffrement et l’accès avec les privilèges les plus faibles aux informations d’identification personnelles ou aux détails de paiement.

En configurant soigneusement la liaison de données, les auteurs créent un lien fiable entre la conception et les données, ce qui accélère la création de communications, garantit la précision et fournit des expériences hautement personnalisées à grande échelle.

