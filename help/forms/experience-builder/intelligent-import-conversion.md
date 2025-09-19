---
title: Import et conversion intelligents
description: Découvrez comment transformer des documents, PDF et images existants en formulaires numériques interactifs à l’aide des fonctionnalités intelligentes d’importation et de conversion de Forms Experience Builder.
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---


# Import et conversion intelligents

>[!NOTE]
>
> Forms Experience Builder est disponible dans le cadre d’un programme d’accès anticipé. Avant de commencer, vérifiez que vous avez demandé et obtenu l’accès.

La fonctionnalité d’importation et de conversion intelligentes de Forms Experience Builder vous permet de transformer des documents, des PDF et des images existants en formulaires numériques interactifs modernes à l’aide d’une analyse et d’une conversion optimisées par l’IA.

## Formats sources pris en charge

### Documents PDF

**PDF AcroForm :**

- PDF forms interactive avec champs de formulaire
- PDF statiques avec des dispositions de type formulaire
- Documents de plusieurs pages avec contenu structuré

**PDF basés sur XFA:**

- Formulaires XFA (XML Forms Architecture) hérités
- Formulaires professionnels complexes avec mises en page avancées
- Formulaires de gouvernement et d&#39;entreprise

**PDF statiques:**

- Documents et formulaires numérisés
- Formulaires prêts à l’impression sans éléments interactifs
- Documents avec des structures de type formulaire

### Fichiers image

**Formats pris en charge :**

- PNG, JPG, JPEG, GIF
- Numérisation à haute résolution des formulaires papier
- Captures d’écran de formulaires numériques
- Esquisses et maquettes dessinées à la main

**Exigences de qualité d’image :**

- 300 ppp minimum pour la reconnaissance de texte
- Texte clair et lisible et éléments de formulaire
- Bon contraste entre le texte et l’arrière-plan
- Orientation correcte (sans rotation)

### Fichiers de conception

**Figma designs :**

- Maquettes et prototypes de formulaires
- Fichiers de conception UI/UX
- Dispositions de formulaires basés sur des composants

**Autres formats de conception :**

- Fichiers Adobe XD
- Conceptions d’esquisse
- Documents filaires

## Importation et conversion

### Étape 1 : accéder à la fonction d’importation

1. Ouvrez Forms Experience Builder
2. Cliquez sur l’icône de pièce jointe dans l’interface
3. Sélectionnez l’option « Importer et convertir ».
4. Choisir votre fichier source

### Étape 2 : télécharger votre document

**Pour les fichiers PDF :**

1. Sélection de votre document PDF
2. Attendez que l’IA analyse la structure.
3. Vérifier les éléments de formulaire détectés
4. Confirmer les paramètres de conversion

**Pour les fichiers image :**

1. Chargez votre image (PNG, JPG, etc.)
2. L’IA analysera la mise en page et le texte
3. Vérifier les champs de formulaire détectés
4. Apportez des ajustements si nécessaire.

**Pour les fichiers de conception :**

1. Chargez votre fichier de conception
2. L’IA extrait les composants de formulaire
3. Vérifier les éléments convertis
4. Personnaliser la structure du formulaire

### Étape 3 : vérifier et personnaliser

Après la conversion initiale :

1. **Vérification des champs détectés** : vérifiez que tous les éléments de formulaire sont correctement identifiés
2. **Ajuster les types de champs** : modifiez les types de champs (texte, liste déroulante, case à cocher, etc.)
3. **Ajouter la validation** : configurer des règles de validation de champ
4. **Personnaliser le style** : appliquer des thèmes et une image de marque
5. **Fonctionnalité de test** : vérifier le comportement et la logique du formulaire

## Exemples de conversion

### Conversion de formulaire PDF

**Formulaire PDF d’origine :**

- Formulaire de contact statique avec nom, adresse e-mail et champs de téléphone
- Section Informations sur la société
- Zone des commentaires

**Formulaire adaptatif converti :**

- Champs de texte interactif avec validation
- Liste déroulante pour la taille de l’entreprise
- Zone de texte multi-lignes pour les commentaires
- Bouton Envoyer avec intégration de la messagerie

### Conversion d’image en formulaire

**Image d’origine :**

- Photo d&#39;un formulaire d&#39;inscription papier
- Formulaire manuscrit avec cases à cocher
- Plusieurs sections pour des informations différentes

**Formulaire adaptatif converti :**

- Champs de texte numérique correspondant à la mise en page
- Cases à cocher et boutons radio interactifs
- Sections organisées avec espacement approprié
- Conception réactive pour les appareils mobiles

### Conversion du fichier de conception

**Design Figma d&#39;origine :**

- Maquette d’interface utilisateur moderne avec composants de formulaire
- Styles et couleurs de marque
- Disposition complexe avec plusieurs panneaux

**Formulaire adaptatif converti :**

- Recréation parfaite du design
- Éléments de formulaire interactif
- Comportement réactif sur tous les appareils
- Style cohérent de la marque

## Fonctionnalités de conversion avancées

### Détection intelligente des champs

L’IA détecte et convertit automatiquement :

- **Champs de texte** : zones de texte monoligne et multiligne
- **Champs de sélection** : listes déroulantes, boutons radio, cases à cocher
- **Champs de date** : sélecteurs de date au formatage approprié
- **Champs numériques** : entrées numériques avec validation
- **Chargements de fichiers** : zones de chargement de documents et d’images

### Conservation de la disposition

La conversion conserve :

- **Structure d’origine** : permet de conserver la disposition et l’organisation
- **Hiérarchie visuelle** : conserve les en-têtes et les sauts de section
- **Espacement et alignement** : maintient un espacement de formulaire approprié
- **Éléments de marque** : permet de conserver les logos et les éléments de style.

### Validation intelligente

Ajoute automatiquement la validation appropriée :

- **Champs e-mail** : validation du format des e-mails
- **Numéros de téléphone** : validation du format des numéros de téléphone
- **Champs obligatoires** : marque les champs obligatoires évidents
- **Périodes** : définit les contraintes de date appropriées

## Bonnes pratiques d’importation et de conversion

### Préparation des documents sources

**Pour les fichiers PDF :**

- Assurez-vous que le texte est sélectionnable (et pas seulement les images).
- Utiliser des analyses de haute qualité pour les PDF statiques
- Organisation du contenu en sections logiques
- Inclure des libellés de champ vierges

**Pour les images :**

- Utiliser des images haute résolution (plus de 300 PPP)
- Garantir un contraste et une lisibilité satisfaisants
- Éviter les images pivotées ou inclinées
- Inclure tous les éléments de formulaire dans l’image

**Pour les fichiers de conception :**

- Utiliser des noms cohérents pour les composants de formulaire
- Organisation logique des calques
- Inclure tous les éléments de formulaire nécessaires
- Exporter en haute qualité

### Optimisation post-conversion

**Vérifier et tester :**

- Tester tous les champs de formulaire et validation
- Vérifier la réactivité mobile
- Vérifier la conformité de l’accessibilité
- Tester la fonctionnalité d’envoi

**Personnaliser et améliorer :**

- Ajouter une logique commerciale et des règles conditionnelles
- Implémenter une gestion des erreurs appropriée
- Configuration des points d’entrée d’envoi
- Appliquer le style et les thèmes de la marque

## Résolution des problèmes de conversion

### Problèmes courants

**Mauvaise détection de champ :**

- Amélioration de la qualité d’image ou de la clarté du texte PDF
- Ajuster manuellement les types de champs après la conversion
- Utiliser des libellés de champ plus descriptifs dans la source

**Problèmes de mise en page :**

- Ajuster manuellement l&#39;espacement et l&#39;alignement
- Utilisation des principes de Responsive Design
- Test sur différentes tailles d’écran

**Éléments manquants :**

- Ajouter manuellement les champs manquants
- Réimporter avec une meilleure qualité de source
- Utiliser l’approche de conversion incrémentielle

### Obtention d’aide

Pour les problèmes de conversion :

- Consultez la [FAQ sur Forms Experience Builder](forms-experience-builder-frequently-asked-questions.md)
- Consultez le [ Guide de prise en main ](forms-experience-builder-getting-started.md)
- Contactez votre administrateur système pour obtenir une assistance technique

## Articles connexes

- [Présentation de Forms Experience Builder](product-overview.md)
- [Prise en main de Forms Experience Builder](forms-experience-builder-getting-started.md)
- [Déploiement et configuration de Forms Experience Builder](deploy-forms-experience-builder.md)
- [Envoi et intégration du formulaire](form-submission-integration.md)
- [Questions fréquentes](forms-experience-builder-frequently-asked-questions.md)
