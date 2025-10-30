---
title: Numérotation dynamique de page dans l’éditeur de communication interactive
description: La numérotation dynamique de page dans l’éditeur de communication interactive permet aux auteurs d’afficher automatiquement les numéros de page dans leur sortie PDF.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: dae482e1f57a3504bf08926b57b89ca9266bd36a
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 18%

---


# Numérotation dynamique de page dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

## Présentation

La fonction de numérotation dynamique de page d’une communication interactive (IC) permet aux auteurs d’afficher automatiquement les numéros de page dans leur sortie PDF. La numérotation des pages peut être activée au niveau du gabarit de page, ce qui permet d’assurer une numérotation cohérente sur toutes les pages de conception associées. Cela permet de maintenir un suivi des pages clair et une mise en page professionnelle tout au long des communications multipages.

## Fonctionnalités essentielles

- Configuration De La Page De Principal ****
La numérotation de page peut être activée au niveau du gabarit de page. Le composant peut être placé n’importe où sur la zone de travail après avoir été déposé et personnalisé librement, car il prend en charge toutes les propriétés disponibles dans le composant de texte.

- **Emplacement automatique :**
Un composant de numérotation de page s’affiche au centre inférieur de chaque page avec le format suivant :
« **Page # of ##** »

   - La première **#** représente le numéro de page actuel.

   - Le deuxième **##** représente le nombre total de pages dans la communication.

- **Affichage dynamique dans l’aperçu PDF :**
Les numéros de page s’affichent de manière dynamique lors de l’aperçu PDF, affichant une numérotation de page précise dans la sortie finale.

### Exemple

Lors de la prévisualisation d’une communication interactive de 5 pages, chaque page affiche :

Page 1 sur 5

Page 2 sur 5

... et ainsi de suite, mise à jour dynamique pendant la génération de PDF.

## Principaux avantages

- Améliore la lisibilité et le professionnalisme des documents.

- Automatise la numérotation des pages sans intervention manuelle.

- Permet de maintenir la cohérence sur toutes les pages liées à un gabarit de page.
