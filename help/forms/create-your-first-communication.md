---
title: Créer votre première communication interactive
description: Concevez facilement des communications dynamiques basées sur les données avec les communications interactives AEM Forms
feature: Release Information
role: Admin
hide: true
hidefromtoc: true
source-git-commit: a771aa7e683cfbcacc8a9d5765c63d50169a2756
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 52%

---


# Créer votre première communication interactive


>[!VIDEO](https://video.tv.adobe.com/v/3444094/)

## Étape 1 : Planifier la communication interactive

La première étape de la planification d’une communication interactive consiste à finaliser le contenu de cette dernière. Une fois le contenu finalisé, vous devez l’analyser pour identifier les différents types de ressources requis pour créer la communication interactive.

### Observations relatives à la planification

Une communication interactive comprend les éléments suivants :

* Le **texte statique** inclut principalement les parties de la communication interactive qui sont génériques par nature et incluses dans la communication pour toutes les clientes et tous les clients. Par exemple, en-tête, pied-de-page, salutation ou clauses de non-responsabilité.

* Les **données provenant d’un système principal (modèle de données de formulaire)** sont spécifiques au client ou à la cliente et fusionnées dynamiquement avec la communication interactive. Par exemple, le numéro de police ou l’adresse peuvent être obtenue à l’aide du modèle de données de formulaire.

* La **disposition ou les modèles** pour les versions d’impression et web de la communication interactive.

* L’**ordre** dans lequel les différents paragraphes de texte apparaissent dans la communication interactive.

* Les **données conditionnelles** qui sont renseignées en fonction de conditions prédéfinies. Par exemple, la date à laquelle la communication interactive est générée.

* Les **images stockées dans un référentiel**, comme les logos et les images de signature. Les images comme les logos de l’entreprise sont présentes dans la majorité ou dans toutes les communications interactives.

* Les **graphiques et tableaux** requis pour simplifier la représentation de données complexes dans une communication interactive.

### Structure de la communication interactive

Une fois que vous avez finalisé le contenu et les éléments utilisés pour créer votre communication interactive, vous pouvez créer une structure pour la communication interactive. L&#39;anatomie doit avoir les détails répertoriés dans la section Considérations relatives à la planification . Par exemple, une anatomie de la facture mensuelle qu’un opérateur de télécommunications envoie à ses clients.

La structure comprend des données avec les modes de saisie suivants :

* Du texte statique
* Modèle de données de formulaire
* Données conditionnelles
* Images


## Étape 2 : Créer un modèle de données de formulaire

Un modèle de données de formulaire vous permet de connecter une communication interactive à des sources de données disparates. Par exemple, un profil utilisateur AEM, des services web RESTful, des services web SOAP, des services OData et des bases de données relationnelles. Un modèle de données de formulaire est un schéma de représentation de données unifié des entités et services d’entreprise disponibles dans des sources de données connectées. Vous pouvez utiliser le modèle de données de formulaire avec une communication interactive pour extraire des données de sources de données connectées. Pour plus d’informations sur le modèle de données de formulaire, consultez la section [Intégration de données AEM Forms](/help/forms/data-integration.md).

## Étape 3 : créer des fragments

Les fragments de document sont des composants réutilisables d’une correspondance qui sont utilisés pour composer une communication interactive. Les fragments de document sont de types : Texte, Liste et Condition.


## Étape 4 : Créer des modèles

L’éditeur de communications interactives fournit plusieurs modèles prêts à l’emploi. Vous pouvez modifier ces modèles en fonction des besoins de votre entreprise ou créer un modèle à partir de zéro.


## Étape 5 : Créer une communication interactive

Une fois que vous avez créé tous les blocs de création, tels que le modèle de données de formulaire, les fragments de document et les modèles pour la version web, vous pouvez commencer à créer une communication interactive. Pour commencer à créer une communication interactive :

1. Connectez-vous à votre environnement AEM Forms as a Cloud Service.
1. Accédez à Forms > Forms et documents .
1. Cliquez sur **Créer** et sélectionnez **Document de communication**. Un écran de configuration s’affiche pour vous permettre de configurer les options suivantes :

   | Champ | Description | Obligatoire |
   |-------|-------------|----------|
   | Nom | Identifiant unique de la communication | Oui |
   | Titre | Nom d’affichage de la communication | Oui |
   | Description | Brève description de l&#39;objet de la communication | Non |
   | Modèle | Sélectionnez un modèle préconfiguré ou commencez à partir de zéro | Oui |
   | Balises | Ajout de balises de métadonnées pour une meilleure organisation | Non |

1. Dans l&#39;onglet &#39;Préréglages&#39; , paramétrez les options suivantes :

   | Champ | Description |
   |-------|-------------|
   | Liste des paramètres prédéfinis | Sélectionnez un paramètre prédéfini préconfiguré pour la taille du document. Les options courantes comprennent A4, Lettre, etc. |
   | Largeur prédéfinie | Affiche la largeur du paramètre prédéfini pour la liste de paramètres prédéfinis sélectionnée. |
   | Hauteur prédéfinie | Affiche la hauteur du paramètre prédéfini pour la liste de paramètres prédéfinis sélectionnée. |
   | Unité prédéfinie | Sélectionnez l&#39;unité de mesure des cotes du document (par exemple, millimètres, pouces). |
   | Orientation prédéfinie | Choisissez l’orientation du document : Portrait ou Paysage. |

1. Cliquez sur **Créer**. La communication s’ouvre dans l’éditeur.
1. Faites glisser et déposez des composants et des fragments pour concevoir la communication interactive.

   * Utilisez **Page Principal** pour le contenu commun à toutes les pages. Les pages de Principal sont conçues pour mettre en forme les pages. Elles facilitent l’homogénéité de la conception car elles peuvent fournir un format d’arrière-plan et de mise en page pour plusieurs pages d’une conception de document.

   * Utilisez **Pages** pour mettre en page le contenu et la mise en page de votre document. Chaque page est dimensionnée et orientée à partir d’un gabarit de page et, par défaut, chaque page est associée au gabarit de page par défaut créé par Designer.


1. Utilisez la notation `@` pour remplir automatiquement les champs de données en fonction du modèle de données connecté.
1. Utilisez l’option `PDF Preview` pour prévisualiser le document avec les données. Vous avez besoin du fichier de données au format JSON.
