---
title: Composant Code à barres dans l’éditeur de communication interactive
description: Le composant Barcode dans l’éditeur de communication interactive d’AEM Forms permet aux auteurs de représenter visuellement les données codées dans des modèles de communication.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: b44cc569-00a1-4a66-ae25-3d672cf5fc12
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 2%

---

# Composant Code à barres dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

## &#x200B;1. Présentation

Le composant Barcode de l’éditeur de communication interactive permet aux auteurs de représenter visuellement les données codées dans des modèles de communication. Cela s’avère particulièrement utile pour les applications qui impliquent le suivi, l’identification, la facturation ou l’automatisation. Grâce à la prise en charge de diverses normes de code à barres telles que le code 128, QR, etc., ce composant offre des options de style, de positionnement et de liaison de données flexibles pour répondre à un large éventail de besoins professionnels.

Que vous créiez des factures client, des étiquettes d’expédition ou des cartes de membre, le composant Code-barres simplifie le processus en incorporant des données lisibles par machine directement dans votre document.

![Rechercher un document IC](/help/forms/interactive-communication/assets/barcode.png)

## &#x200B;2. Propriétés

Le composant Code à barres est fourni avec un ensemble complet d’options configurables pour contrôler son comportement et son aspect :

2.1 Champ de base

**Name :** identifiant unique du code-barres. Il est utilisé pour référencer le composant dans les modèles de données et les ensembles de règles.

**Location :** indique l’emplacement d’affichage du texte du code-barres par rapport au symbole du code-barres.

**Options:**

- **Aucune :** masque le texte.

- **Au-dessus :** affiche le texte au-dessus du code-barres.

- **Ci-dessous :** affiche le texte sous le code-barres.

- **Ci-dessus incorporé :** incorpore le texte dans la zone supérieure du code-barres.

- **Incorporé en dessous :** incorpore le texte dans la zone inférieure du code à barres.

- **Type :** indique la norme du code-barres (par exemple, Code 128, Code 39, Code QR, etc.).

- **Valeur par défaut :** valeur prédéfinie qui s’affiche si aucune donnée n’est fournie.

- **Longueur des données :** indique le nombre attendu ou maximal de caractères que le code à barres peut contenir.

- **Somme de contrôle :** valide les données de code à barres pour en garantir la précision.

   - **Options:**

      - **Aucune :** aucune validation de somme de contrôle.

      - **Auto :** calcule automatiquement la somme de contrôle en fonction du type.

- **Rapport largeur/largeur étroite :** définit la largeur relative des barres larges par rapport aux barres étroites (utilisé dans certains codes-barres 1D).

2.2 Emplacement

Détermine l’emplacement du code à barres par rapport au contenu :

- **Aucun :** aucun positionnement supplémentaire.

- **Ci-dessus :** place le code-barres au-dessus du contenu associé.

- **Ci-dessous :** place le code-barres sous le contenu.

- **Ci-dessus incorporé :** code-barres est incorporé et flotte au-dessus du contenu.

- **Contenu incorporé en dessous :** Contenu incorporé en dessous.

2.3 Position

Définit l’emplacement exact du code-barres dans la mise en page :

- Coordonnées **X et Y :** positionnez le code-barres au sein du formulaire en utilisant des unités millimétriques.

- **Hauteur et largeur :** permet de définir les dimensions physiques du code-barres.

2.4 Marge

Ajoute un espacement autour du code-barres pour une meilleure séparation visuelle :

- Haut

- Bas

- Gauche

- Droite

Ces marges facilitent la cohérence et la lisibilité de la mise en page.

2.5 Apparence

Personnalisez le style visuel du code à barres :

- **Remplissage :** couleur d’arrière-plan de la zone de code-barres.

- **Tracé :** couleur de bordure.

- **Largeur :** définit l’épaisseur des lignes du code-barres.

- **Style :** sélectionnez l’un des paramètres prédéfinis, tels que plat, bordé ou élevé.

- **Arêtes :** permet de choisir entre les coins arrondis ou pointus de la zone de code-barres.

2.6 Présence

Contrôle si le code à barres est affiché ou masqué au moment de l’exécution :

- **Visible :** code-barres est affiché dans la sortie finale.

- **Caché :** espace réservé mais le code-barres n&#39;est pas affiché.

2.7 Liaison de données

Liaison de données : connecte le code à barres à un modèle de données principal (XML ou JSON). Cela permet de s’assurer que le code à barres reflète dynamiquement des données uniques par instance de document, telles qu’un identifiant de commande ou un numéro de suivi.

## &#x200B;3. Utilisation

Le composant Code à barres est particulièrement utile pour automatiser les processus qui reposent sur des données numérisées. Il peut être ajouté aux modèles de communication, par exemple :

- Factures (pour les paiements de référence client et d&#39;analyse rapide)

- Étiquettes d’expédition (pour le suivi des packages)

- Cartes de membre ou de fidélité (pour l&#39;identification par balayage)

- Coupons et bons (pour validation sur le point de vente)

Les auteurs peuvent incorporer le code à barres dans des conteneurs de mises en page et le mettre en forme en fonction de la marque ou du thème du document.

## &#x200B;4. Bonnes Pratiques

- Utilisez un type de code-barres approprié au cas d’utilisation, par exemple, Code QR pour les URL, Code 128 pour les identifiants alphanumériques.

- Validez la lisibilité du code-barres en imprimant des versions de test et en les numérisant.

- Assurez l’intégrité des données à l’aide de l’option somme de contrôle si la norme de code à barres la prend en charge.

- Choisissez des tailles lisibles et des largeurs de ligne pour éviter les problèmes d&#39;analyse.

- Conservez des marges adéquates pour empêcher l&#39;écrêtage lors de l&#39;impression.

Le composant Code à barres de l’éditeur de communication interactive permet aux créateurs et aux créatrices de documents de combler le fossé entre les systèmes numériques et physiques. Lorsqu’elle est mise en œuvre efficacement, elle améliore l’automatisation, la commodité pour les utilisateurs et prend en charge une intégration transparente avec les appareils et les workflows d’analyse.
