---
title: Prise en main de Edge Delivery Services pour AEM Forms à l’aide de l’éditeur universel
description: Découvrez comment créer et publier des formulaires hautes performances à l’aide de Edge Delivery Services avec la création WYSIWYG de l’éditeur universel.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '2609'
ht-degree: 2%

---


# Prise en main de Edge Delivery Services pour AEM Forms à l’aide de l’éditeur universel

| Méthode de création | Guide |
|---------------------------------|-----------------------------------------------------------------------|
| **Éditeur universel (WYSIWYG)** | Cet article |
| **Création basée sur des documents** | [Tutoriel basé sur des documents](/help/edge/docs/forms/tutorial.md) |

Edge Delivery Services pour AEM Forms associe une diffusion web haute performance à la création WYSIWYG dans l’éditeur universel. Ce guide couvre la création, la personnalisation et la publication de formulaires à chargement rapide.

## Ce que vous allez accomplir

À la fin de ce tutoriel, vous pourrez :

- Configurer un référentiel GitHub avec le bloc de Forms adaptatif
- Création d’un site AEM intégré à Edge Delivery Services
- Créer et publier des formulaires à l’aide de l’éditeur universel
- Configuration de l’environnement de développement local

## Choisissez Votre Chemin

Sélectionnez l’approche qui correspond à votre scénario :

![Choisissez Votre Guide De Décision De Chemin](/help/edge/docs/forms/universal-editor/assets/choose-your-path.svg)
*Image : guide visuel pour vous aider à choisir le bon chemin d’implémentation*

| **Chemin A : Nouveau Projet** | **Chemin B : Projet Existant** |
|----------------------------------------|-------------------------------------------|
| Commencer avec un modèle préconfiguré | Ajouter des formulaires à votre projet AEM actuel |
| **Idéal pour :** nouvelles implémentations | **Idéal pour :** AEM Sites existant |
| **Avantages :** bloc Forms préconfiguré | **Avantages :** Forms ajouté à un site existant |
| **Étapes :** configuration de l’→ de modèle → Forms | **Étapes :** Intégration → Configuration → Forms |
| [Commencer par le chemin A](#path-a-create-new-project-with-forms) | [Commencer par le chemin B](#path-b-add-forms-to-existing-project) |

## Prérequis

Pour garantir une expérience fluide et réussie avec Edge Delivery Services pour AEM Forms à l’aide de l’éditeur universel, passez en revue et confirmez les conditions préalables suivantes avant de continuer :

### Conditions d’accès

- **Compte GitHub** : vous devez disposer d’un compte GitHub disposant des autorisations pour créer des référentiels. Cela est essentiel pour gérer le code source de votre projet et collaborer avec votre équipe.
- **Accès à la création AEM as a Cloud Service** : vérifiez que vous disposez d’un accès au niveau de la création à votre environnement AEM as a Cloud Service. Cet accès est requis pour créer, modifier et publier des formulaires.

### Exigences techniques

- **Familiarité avec Git** : vous devriez être à l’aise pour effectuer des opérations Git de base telles que le clonage de référentiels, la validation de modifications et l’envoi de mises à jour. Ces compétences sont fondamentales pour le contrôle de code source et la collaboration avec les projets.
- **Compréhension des technologies web** : une connaissance pratique d’HTML, de CSS et de JavaScript est recommandée. Ces technologies constituent la base de la personnalisation et du dépannage des formulaires.
- **Node.js (version 16 ou ultérieure)** : Node.js est requis pour le développement local et l’exécution des outils de création. Assurez-vous que la version 16 ou une version ultérieure est installée sur votre système.
- **Gestionnaire de packages (npm ou yarn)** : vous aurez besoin de npm (Gestionnaire de packages de nœuds) ou yarn pour gérer les dépendances et les scripts du projet.

### Arrière-plan recommandé

- **Concepts d’AEM Sites** : une connaissance de base d’AEM Sites, notamment de la structure du site et de la création de contenu, vous aidera à parcourir et à intégrer efficacement les formulaires.
- **Principes de conception de formulaire** : la connaissance des bonnes pratiques en matière de conception de formulaire, telles que la convivialité, l’accessibilité et la validation des données, vous permettra de créer des formulaires efficaces et conviviaux.
- **Expérience avec les éditeurs WYSIWYG** : une expérience préalable avec les éditeurs What You See Is What You Get (WYSIWYG) vous aidera à exploiter plus efficacement les fonctionnalités de création visuelle de l’éditeur universel.

>[!TIP]
>
> Vous découvrez AEM ? Commencez par le [Guide de prise en main d’AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=fr).

## Chemin A : création d’un projet avec Forms

**Recommandé pour** nouveaux projets, pilotes ou initiatives de preuve de concept.

Tirez parti d’AEM Forms Boilerplate pour accélérer la configuration de votre projet. Ce modèle standard offre un modèle prêt à l’emploi qui intègre de manière transparente le bloc de Forms adaptatif, ce qui vous permet de créer et de déployer rapidement des formulaires dans votre site AEM.

### Vue d’ensemble

Pour lancer correctement votre nouveau projet avec les formulaires intégrés, vous devez :

1. Créez un référentiel GitHub à l’aide du modèle standard AEM Forms.
2. Configurez la synchronisation du code AEM pour automatiser la synchronisation du contenu entre AEM et votre référentiel.
3. Configurez la connexion entre votre projet GitHub et votre environnement AEM.
4. Établissez et publiez un nouveau site AEM.
5. Ajouter et gérer des formulaires à l’aide de l’éditeur universel

Les sections suivantes vous guideront à travers chaque étape en détail, afin d’assurer une expérience de configuration de projet fluide et efficace.

+++Étape 1 : créer un référentiel GitHub à partir d’un modèle

1. **Accès au modèle AEM Forms Boilerplate**
   - Accédez à [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms)

   ![Modèle standard AEM Forms](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   *Image : référentiel standard AEM Forms avec bloc de Forms adaptatif préconfiguré*

2. **Créer votre référentiel**
   - Cliquez sur **Utiliser ce modèle** > **Créer un référentiel**

   ![Créer un référentiel à partir d’un modèle](/help/edge/docs/forms/assets/use-eds-form-template.png)
   *Image : utilisation du modèle pour créer un référentiel*

3. **Configurer les paramètres du référentiel**
   - **Propriétaire** : sélectionnez votre compte ou organisation GitHub
   - **Nom du référentiel** : choisissez un nom explicite (par exemple, `my-forms-project`).
   - **Visibilité** : sélectionnez **Public** (recommandé pour Edge Delivery Services).
   - Cliquez sur **Créer un référentiel**

   ![Configuration du référentiel](/help/edge/docs/forms/assets/name-eds-repo.png)
   *Image : configuration de votre nouveau référentiel avec une visibilité publique*

**Validation :** vérifiez que vous disposez d’un nouveau référentiel GitHub basé sur le modèle standard d’AEM Forms.

+++

+++Étape 2 : Installer la synchronisation du code AEM

La synchronisation du code AEM synchronise automatiquement les modifications de contenu entre votre environnement de création AEM et votre référentiel GitHub.

1. **Installation de l’application GitHub**
   - Accédez à [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new)

2. **Configurer les autorisations d’accès**
   - Sélectionnez **Sélectionner uniquement les référentiels**.
   - Choisissez le référentiel que vous venez de créer.
   - Cliquez sur **Enregistrer**.

   ![Installation de la synchronisation du code AEM](/help/edge/docs/forms/assets/aem-code-sync-up.png)
   *Image : installation de la synchronisation du code AEM avec des autorisations spécifiques au référentiel*

**Point de contrôle :** la synchronisation du code AEM est maintenant installée et a accès à votre référentiel.

+++

+++Étape 3 : Configurer l’intégration d’AEM

Le fichier `fstab.yaml` connecte votre référentiel GitHub à l’environnement de création AEM pour la synchronisation du contenu.

1. **Accédez à votre référentiel**
   - Accédez au référentiel GitHub que vous venez de créer.
   - Vous devriez voir les fichiers standard AEM Forms

2. **Créer le fichier fstab.yaml**
   - Cliquez sur **Ajouter un fichier** > **Créer un nouveau fichier** dans le répertoire racine
   - Nommez le fichier `fstab.yaml`

   ![Création du fichier fstab.yaml](/help/edge/docs/forms/assets/open-fstab.png)
   *Image : création du fichier de configuration fstab.yaml*

3. **Ajouter les détails de votre connexion AEM**

   Copiez et collez la configuration suivante, en remplaçant les espaces réservés :

   ```yaml
   mountpoints:
     /: https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main
   ```

   **Remplacer:**
   - `<aem-author>` : votre URL d’auteur AEM as a Cloud Service (par exemple, `author-p12345-e67890.adobeaemcloud.com`).
   - `<owner>` : nom d’utilisateur ou organisation GitHub
   - `<repository>` : nom de votre référentiel

   **Exemple :**

   ```yaml
   mountpoints:
     /: https://author-p12345-e67890.adobeaemcloud.com/bin/franklin.delivery/mycompany/my-forms-project/main
   ```

   ![Modification du fichier fstab.yaml](/help/edge/docs/forms/assets/edit-fstab-file.png)
   *Image : configuration du point de montage pour l’intégration AEM*

4. **Validez la configuration**
   - Ajoutez un message de validation : « Ajout de la configuration de l’intégration AEM »
   - Cliquez sur **Valider le nouveau fichier**

   ![Validation des modifications fstab](/help/edge/docs/forms/assets/commit-fstab-changes.png)
   *Image : validation de la configuration fstab.yaml*

**Validation :** confirmez la connexion de votre référentiel GitHub à AEM.

    >[ !REMARQUE]
    >
    >Vous rencontrez des problèmes de build ? Voir [Résolution des problèmes de build GitHub](#troubleshooting-github-build-issues).

+++

+++Étape 4 : création d’un site AEM connecté à votre référentiel GitHub.

1. **Accéder à la console AEM Sites**
   - Connectez-vous à votre instance de création AEM as a Cloud Service
   - Accéder à **Sites**

   ![Console AEM Sites](/help/edge/assets/select-sites.png)
   *Image : accès à la console AEM Sites*

2. **Démarrer la création du site**
   - Cliquez sur **Créer** > **Site à partir du modèle**

   ![Option Créer Un Site](/help/edge/docs/forms/assets/create-sites.png)
   *Image : création d’un site à partir d’un modèle*

3. **Sélectionnez le modèle Edge Delivery Services**
   - Choisissez le modèle **Site Edge Delivery Services**
   - Cliquez sur **Suivant**.

   ![Sélection de modèles de site](/help/edge/docs/forms/assets/select-site-template.png)
   *Figure : Sélection du modèle de site Edge Delivery Services*

   >[!NOTE]
   >
   >**Modèle non disponible ?** Si vous ne voyez pas le modèle Edge Delivery Services :
   >
   >1. Cliquez sur **Importer** pour charger le modèle
   >2. Télécharger des modèles à partir des versions de [GitHub](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)

4. **Configuration de votre site**

   Saisissez les informations suivantes :

   | Champ | Valeur | Exemple |
   |-----------------|-----------------------------|-----------------------------------------|
   | **Titre du site** | Nom descriptif du site | « Mon projet Forms » |
   | **Nom du site** | Nom convivial de l’URL | « mon-projet-formulaires » |
   | **URL GitHub** | Votre URL de référentiel | `https://github.com/mycompany/my-forms-project` |

   ![Configuration du site](/help/edge/docs/forms/assets/create-aem-site.png)
   *Image : configuration de votre nouveau site AEM avec l’intégration GitHub*

5. **Création complète du site**
   - Vérifier vos paramètres
   - Cliquez sur **Créer**.

   ![Confirmer la création du site](/help/edge/docs/forms/assets/click-ok-aem-site.png)
   *Image : confirmation de la création du site*

   **Opération réussie !** Votre site AEM est maintenant créé et connecté à GitHub.

6. **Ouvrez dans l’éditeur universel**
   - Dans la console Sites , recherchez votre nouveau site
   - Sélectionnez la page `index`
   - Cliquez sur **Modifier**

   ![Modifier le site dans l’éditeur universel](/help/edge/docs/forms/assets/edit-site.png)
   *Image : ouverture de votre site pour le modifier*

   L’éditeur universel s’ouvre dans un nouvel onglet, fournissant des fonctionnalités de création WYSIWYG.

   ![Interface de l’éditeur universel](/help/edge/docs/forms/assets/site-in-universal-editor.png)
   *Image : votre site s’est ouvert dans l’éditeur universel pour la modification dans WYSIWYG*

**Validation :** vérifiez que votre site AEM est prêt pour la création de formulaires.

+++

+++Étape 5 : publier votre site

La publication rend votre site disponible sur Edge Delivery Services pour un accès global.

1. **Publication rapide à partir de la console Sites**
   - Revenir à la console AEM Sites
   - Sélectionnez les pages de votre site (ou sélectionnez-les toutes en appuyant sur Ctrl + A)
   - Cliquez sur **Publication rapide**

   ![Publication d’un site AEM](/help/edge/docs/forms/assets/publish-sites.png)
   *Figure : Sélection de pages pour la publication rapide*

2. **Confirmer la publication**
   - Dans la boîte de dialogue de confirmation, cliquez sur **Publier**

   ![ Boîte de dialogue Publication rapide ](/help/edge/docs/forms/assets/quick-publish.png)
   *Image : confirmation de l’action de publication*

   **Alternative :** vous pouvez également publier directement à partir de l’éditeur universel à l’aide du bouton de publication.

   ![Publication à partir de l’éditeur universel](/help/edge/docs/forms/assets/qui.png)
   *Image : publication directe à partir de l’éditeur universel*

3. **Accéder à votre site en ligne**

   Votre site est maintenant en ligne à l’adresse :

   ```
   https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/
   ```

   **Présentation de la structure de l’URL :**
   - `<branch>` : branche GitHub (généralement `main`)
   - `<repo>` : nom de votre référentiel
   - `<owner>` : nom d’utilisateur ou organisation GitHub
   - `<site-name>` : nom de votre site AEM

   **Exemple :**

   ```
   https://main--my-forms-project--mycompany.aem.page/content/my-forms-project/
   ```

**Validation :** vérifiez que votre site est en ligne sur Edge Delivery Services.

>[!TIP]
>
> **Modèles d’URL :**
>
> - **Page d’accueil :** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
> - **Autres pages :** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<page-name>`

**Suivant :** [créer votre premier formulaire](#create-your-first-form)

+++

## Chemin d’accès B : ajouter Forms au projet existant

**Idéal pour** : AEM Sites existant avec Edge Delivery Services

Si vous disposez déjà d’un projet AEM utilisant Edge Delivery Services, vous pouvez ajouter des fonctionnalités de formulaire en intégrant le bloc de Forms adaptatif.

### Conditions préalables pour le chemin d’accès B

Pour poursuivre l’intégration de forms dans votre projet AEM existant, vérifiez que les conditions préalables suivantes sont remplies :

- Vous disposez d’un projet AEM existant qui a été créé à l’aide de la norme XWalk[ de ](https://github.com/adobe-rnd/aem-boilerplate-xwalk)AEM Boilerplate.
- Vous disposez d’un [ environnement de développement local configuré](#set-up-local-development-environment)
- Vous disposez d’un accès Git à votre référentiel de projet, ce qui vous permet de cloner, modifier et pousser les modifications selon vos besoins.

>[!NOTE]
>
> Si votre projet a été initialement configuré à l’aide du [modèle standard d’AEM Forms](https://github.com/adobe-rnd/aem-boilerplate-forms), la fonctionnalité de formulaire est déjà incluse. Dans ce cas, vous pouvez passer à la section [Créer votre premier formulaire](#create-your-first-form).

Le guide suivant fournit une approche structurée pour ajouter des fonctionnalités de formulaire à votre projet existant. Chaque étape est conçue pour assurer une intégration transparente et une fonctionnalité optimale dans l’environnement de l’éditeur universel.

### Vue d’ensemble

Vous allez effectuer les étapes de haut niveau suivantes :

1. Copiez les fichiers de bloc de Forms adaptatif dans votre projet.
2. Mettez à jour la configuration de votre projet pour reconnaître et prendre en charge les composants de formulaire.
3. Ajustez les règles ESLint pour prendre en charge les nouveaux fichiers et modèles de codage.
4. Créez votre projet et validez les modifications dans votre référentiel.

+++Étape 1 : Copier les fichiers de bloc Forms

1. **Accédez à votre projet local**

   ```bash
   cd /path/to/your/aem-project
   ```

2. **Télécharger les fichiers requis à partir d’AEM Forms Boilerplate**

   Copiez ces fichiers à partir du référentiel standard d’[AEM Forms ](https://github.com/adobe-rnd/aem-boilerplate-forms) :

   | Source | Destination | Objectif |
   |------------------------------------------------------------------------|----------------------------|----------------------------|
   | [`blocks/form/`](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form) | `blocks/form/` | Fonctionnalité de formulaire principale |
   | [`scripts/form-editor-support.js`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js) | `scripts/form-editor-support.js` | Intégration de l’éditeur universel |
   | [`scripts/form-editor-support.css`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css) | `scripts/form-editor-support.css` | Style de l’éditeur |

3. **Prise en charge de l’éditeur de mise à jour**
   - Remplacez votre fichier `/scripts/editor-support.js` par [editor-support.js d’AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js)

**Validation :** vérifiez que les fichiers de bloc de formulaire se trouvent dans votre projet.

+++

+++Étape 2 : mettre à jour la configuration du composant

1. **Mettre à jour le modèle de section**

   Ouvrez `/models/_section.json` et ajoutez des composants de formulaire aux filtres :

   ```json
   {
        "filters": [
        {
      "id": "section",
      "components": [
           "text",
           "image",
           "button",
        "form",
        "embed-adaptive-form"
      ]
       }
     ]
   }
   ```

   **Fonction :** active les composants de formulaire dans le sélecteur de composants de l’éditeur universel.

**Validation :** confirmer que les composants de formulaire apparaissent dans l’éditeur universel.

+++

+++Étape 3 : Configuration d’ESLint (facultatif)

**Pourquoi cette étape :** empêche les erreurs de liaison de fichiers spécifiques aux formulaires et configure les règles de validation appropriées.

1. **Mettre à jour .eslintignore**

   Ajoutez les lignes suivantes aux `/.eslintignore` :

   ```bash
   # Form block rule engine files
   blocks/form/rules/formula/*
   blocks/form/rules/model/*
   blocks/form/rules/functions.js
   scripts/editor-support.js
   scripts/editor-support-rte.js
   ```

2. **Mettre à jour .eslintrc.js**

   Ajoutez ces règles à l’objet `rules` dans `/.eslintrc.js` :

   ```javascript
   {
     "rules": {
       // Existing rules...
   
       // Form component cell limits
    'xwalk/max-cells': ['error', {
         '*': 4, // default limit
      form: 15,
      wizard: 12,
      'form-button': 7,
      'checkbox-group': 20,
      checkbox: 19,
      'date-input': 21,
      'drop-down': 19,
      email: 22,
      'file-input': 20,
      'form-fragment': 15,
      'form-image': 7,
      'multiline-input': 23,
      'number-input': 22,
      panel: 17,
      'radio-group': 20,
      'form-reset-button': 7,
      'form-submit-button': 7,
      'telephone-input': 20,
      'text-input': 23,
      accordion: 14,
      modal: 11,
      rating: 18,
      password: 20,
         tnc: 12
       }],
   
       // Disable this rule for forms
       'xwalk/no-orphan-collapsible-fields': 'off'
     }
   }
   ```

**Validation :** confirmer que ESLint fonctionne avec les composants de formulaire.

+++

+++Étape 4 : créer et déployer

1. **Installation des dépendances et génération**

   ```bash
   # Install any new dependencies
   npm install
   
   # Build component definitions
   npm run build:json
   ```

   **À quoi cela sert-il**
   - Met à jour les `component-definition.json` avec les composants de formulaire.
   - Génère des `component-models.json` avec des modèles de formulaire
   - Crée des `component-filters.json` avec des règles de filtrage

2. **Vérifier les fichiers générés**

   Vérifiez que ces fichiers dans la racine de votre projet contiennent des objets liés au formulaire :
   - `component-definition.json`
   - `component-models.json`
   - `component-filters.json`

3. **Valider et envoyer les modifications**

   ```bash
   git add .
   git commit -m "Add Adaptive Forms Block integration"
   git push origin main
   ```

**Validation :** vérifiez que votre projet comprend des fonctionnalités de formulaire.

+++

**Suivant :** [Créez Votre Premier Formulaire](#create-your-first-form)

## Création De Votre Premier Formulaire

**Qui doit suivre cette section**\
Cette section s’adresse aux utilisateurs qui suivent le chemin A (nouveau projet) ou le chemin B (projet existant).

Votre projet étant désormais équipé pour la création de formulaires, vous êtes prêt à créer votre premier formulaire à l’aide de l’environnement de création WYSIWYG intuitif de l’éditeur universel. Les étapes suivantes fournissent une approche structurée de la conception, de la configuration et de la publication d’un formulaire dans votre site AEM.

### Vue d’ensemble

Le processus de création d’un formulaire dans l’éditeur universel comprend plusieurs étapes clés :

1. **Insérer le bloc de formulaire adaptatif**\
   Commencez par ajouter le bloc de formulaire adaptatif à la page de votre choix.

2. **Ajouter des composants de formulaire**\
   Renseignez votre formulaire en insérant des composants tels que des champs de texte, des boutons et d’autres éléments de saisie.

3. **Configurer les propriétés du composant**\
   Ajustez les paramètres et les propriétés de chaque composant pour répondre aux exigences de votre formulaire.

4. **Prévisualiser et tester le formulaire**\
   Utilisez la fonctionnalité d’aperçu pour valider l’apparence et le comportement de votre formulaire avant sa publication.

5. **Publier la page mise à jour**\
   Une fois satisfait, publiez votre page pour mettre le formulaire à la disposition des utilisateurs finaux.

Les sections suivantes vous guideront à travers chacune de ces étapes en détail, afin de garantir une expérience de création de formulaire fluide et efficace.

+++Étape 1 : Ajouter Un Bloc De Formulaire Adaptatif

1. **Ouvrez votre page dans l’éditeur universel**
   - Accédez à la console **Sites** dans AEM
   - Sélectionnez la page sur laquelle vous souhaitez ajouter un formulaire (par exemple, `index`)
   - Cliquez sur **Modifier**

   Votre page s’ouvre dans l’éditeur universel pour la modification dans WYSIWYG.

2. **Ajouter le composant Formulaire adaptatif**
   - Ouvrez le panneau **Arborescence de contenu** (barre latérale gauche)
   - Accédez à une section dans laquelle vous souhaitez ajouter votre formulaire
   - Cliquez sur l’icône **Ajouter** (+)
   - Sélectionnez **Formulaire adaptatif** dans la liste des composants

   ![Ajout d’un bloc de formulaire adaptatif](/help/edge/docs/forms/assets/add-adaptive-form-block.png)
   *Image : ajout d’un bloc de formulaire adaptatif à une page*

**Validation :** vérifiez que vous disposez d’un conteneur de formulaire vide.

+++

+++Étape 2 : Ajouter des composants de formulaire

1. **Accédez à votre bloc de formulaire**
   - Dans l’arborescence de contenu, recherchez la section de formulaire adaptatif que vous venez d’ajouter

   ![Bloc de formulaire adaptatif ajouté](/help/edge/docs/forms/assets/adative-form-block.png)
   *Image : bloc Formulaire adaptatif dans l’arborescence de contenu*

2. **Ajouter des composants de formulaire**

   Vous pouvez ajouter des composants de deux manières :

   **Méthode A : cliquer pour ajouter**
   - Cliquez sur l’icône **Ajouter** (+) dans la section de votre formulaire
   - Sélectionnez des composants dans la liste **Composants de formulaire adaptatif**

   **Méthode B : glisser-déposer**
   - Faites glisser des composants directement du panneau des composants vers votre formulaire

   ![Ajout de composants de formulaire](/help/edge/docs/forms/assets/add-component.png)
   *Image : ajout de composants à un formulaire*

   **Composants de démarrage recommandés :**
   - Entrée de texte (pour le nom, l’e-mail)
   - Zone de texte (pour les messages)
   - Bouton Envoyer

3. **Configurer les propriétés du composant**
   - Sélectionner un composant de formulaire
   - Utilisez le panneau **Propriétés** (barre latérale droite) pour configurer :
      - Libellés et espaces réservés
      - Règles de validation
      - Paramètres de champ obligatoires

   ![Panneau Propriétés du composant](/help/edge/docs/forms/assets/component-properties.png)
   *Figure : Configuration des propriétés du composant*

4. **Prévisualiser le formulaire**

   Votre formulaire ressemblera à ceci :

   ![Aperçu de formulaire terminé](/help/edge/docs/forms/assets/added-form-aem-sites.png)
   *Image : exemple de formulaire créé avec l’éditeur universel*

**Validation :** vérifiez que votre formulaire est prêt pour la publication.

>[!IMPORTANT]
>
> N’oubliez pas de publier votre page après avoir apporté des modifications pour afficher les mises à jour dans le navigateur.

+++

+++Étape 3 : Publier Votre Formulaire

1. **Publication à partir de l’éditeur universel**
   - Cliquez sur le bouton **Publier** dans l’éditeur universel

   ![Publication du formulaire](/help/edge/docs/forms/assets/publish-form.png)
   *Image : publication de votre formulaire à partir de l’éditeur universel*

2. **Confirmer la publication**
   - Dans la boîte de dialogue de confirmation, cliquez sur **Publier**

   ![Confirmation de publication](/help/edge/docs/forms/assets/publish-form1.png)
   *Image : confirmation de l’action de publication*

   Un message de réussite confirmant la publication s’affiche.

   ![Publication réussie](/help/edge/docs/forms/assets/publish-form2.png)
   *Image : confirmation de publication réussie*

3. **Afficher votre formulaire dynamique**

   Votre formulaire est maintenant en ligne à l’adresse :

   ```
   https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/
   ```

   **Exemple d’URL :**

   ```
   https://main--my-forms-project--mycompany.aem.page/content/my-forms-project/
   ```

   ![Page Formulaire dynamique](/help/edge/docs/forms/assets/publish-index-page.png)
   *Image : page de formulaire publiée sur Edge Delivery Services*

**Félicitations !** Votre formulaire est maintenant en ligne et prêt à collecter les envois.

+++

### Étapes suivantes

Maintenant que vous disposez d’un formulaire de travail, vous pouvez :

- **Personnaliser le style** en modifiant les fichiers CSS et JavaScript
- **Ajout de fonctionnalités de formulaire avancées** telles que les règles de validation et la logique conditionnelle
- **Configuration du développement local** pour une itération plus rapide
- **Créer des formulaires autonomes** pour des cas d’utilisation spécifiques

>[!TIP]
>
> **En savoir plus :** [Créer des formulaires autonomes dans l’éditeur universel](/help/edge/docs/forms/universal-editor/create-forms.md)

## Configuration D’Un Environnement De Développement Local

**Idéal pour :** les développeurs et développeuses qui souhaitent personnaliser le style et le comportement des formulaires

Un environnement de développement local vous permet d’apporter des modifications et de les voir instantanément sans passer par le cycle de publication.

+++Configuration de l’interface de ligne de commande AEM et du développement local

1. **Installer l’interface de ligne de commande AEM**

   L’interface de ligne de commande d’AEM simplifie les tâches de développement local :

   ```bash
       npm install -g @adobe/aem-cli
   ```

2. **Clonez votre référentiel**

   ```bash
   git clone https://github.com/<owner>/<repo>
   cd <repo>
   ```

   Remplacez `<owner>` et `<repo>` par vos détails GitHub réels.

3. **Démarrez le serveur de développement local**

   ```bash
   aem up
   ```

   Vous démarrez ainsi un serveur local avec des fonctionnalités de rechargement à chaud.

4. **Effectuer des personnalisations**

   - Modifier les fichiers du répertoire `blocks/form/` pour connaître le style et le comportement du formulaire
   - Modifier les `form.css` pour la mise en forme
   - Mettre à jour les `form.js` pour le comportement

   **Voir les modifications instantanément** dans votre navigateur à l’adresse `http://localhost:3000`

5. **Déployer vos modifications**

   ```bash
   git add .
   git commit -m "Custom form styling"
   git push origin main
   ```

   Vos modifications seront disponibles à l’adresse :
   - **Aperçu :** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`
   - **Production :** `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`

+++


## Résolution des problèmes

### Problèmes courants et solutions

+++Problèmes de build GitHub

**Problème :** erreurs de création ou erreurs de linting

**Solution 1 : gérer les erreurs de liaison**

Si vous rencontrez des erreurs de liaison :

1. Ouvrez `package.json` dans la racine de votre projet.
2. Recherchez le script `lint` :

   ```json
   "scripts": {
     "lint": "npm run lint:js && npm run lint:css"
   }
   ```

3. Désactivez temporairement la liaison :

   ```json
   "scripts": {
     "lint": "echo 'skipping linting for now'"
   }
   ```

4. Valider et transmettre les modifications

**Solution 2 : erreurs de chemin du module**

Si vous voyez « Impossible de résoudre le chemin d’accès sur le module « /scripts/lib-franklin.js » :

1. Accédez à `blocks/form/form.js`.
2. Mettez à jour l’instruction d’importation :

   ```javascript
   // Change this:
   import { ... } from '/scripts/lib-franklin.js';
   
   // To this:
   import { ... } from '/scripts/aem.js';
   ```

+++

+++Problèmes de fonctionnalité de formulaire

**Problème :** envois de formulaire ne fonctionnent pas

**Solutions:**

- Vérifiez que vous disposez d’un composant de bouton d’envoi
- Vérifier la configuration de l’URL de l’action de formulaire
- Vérifier les règles de validation du formulaire
- Tester d’abord en mode Aperçu

**Problème :** de mise en forme

**Solutions:**

- Vérifier les chemins d’accès aux fichiers CSS dans `blocks/form/`
- Effacer le cache du navigateur
- Vérifier la syntaxe CSS
- Test dans l’environnement de développement local

+++

+++Problèmes liés à l’éditeur universel

**Problème :** composants de formulaire n’apparaissent pas dans l’éditeur universel

**Solutions:**

- Vérifiez que la synchronisation du code AEM est installée et en cours d’exécution.
- Vérifiez que `fstab.yaml` possède l’URL d’auteur AEM appropriée.
- Assurez-vous que l’accès anticipé à votre instance AEM est activé.
- Confirmer `component-definition.json` inclut les composants de formulaire

**Problème :** modifications non visibles après publication

**Solutions:**

- Attendez l’actualisation du cache CDN.
- Vérification du cache du navigateur (essayer en mode incognito/privé)
- Vérifiez que le format d’URL utilisé est correct

+++



