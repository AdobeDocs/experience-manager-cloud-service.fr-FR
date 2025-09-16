---
title: Créer et publier des formulaires adaptatifs avec Edge Delivery Services
description: Instructions détaillées pour créer, rédiger et publier des formulaires adaptatifs à l’aide des modèles Edge Delivery Services dans AEM, en mettant l’accent sur la précision technique et la clarté.
keywords: Formulaires adaptatifs, Edge Delivery Services, éditeur universel, création de formulaires, AEM Forms, publication de formulaires
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: 07160248d5b5817d155a118475878ce04a687a32
workflow-type: ht
source-wordcount: '1005'
ht-degree: 100%

---


# Créer et publier des formulaires adaptatifs avec Edge Delivery Services

Ce document fournit des instructions détaillées pour créer, configurer et publier des formulaires adaptatifs à l’aide des modèles Edge Delivery Services dans AEM. Il couvre l’ensemble du workflow, de la création du formulaire au déploiement en production.

Après avoir consulté ce guide, vous saurez accomplir ce qui suit :

- Créer des formulaires à l’aide de modèles Edge Delivery Services
- Créer des formulaires à l’aide de l’éditeur universel
- Configurer et publier des formulaires dans Edge Delivery Services
- Accéder aux formulaires publiés et vérifier le déploiement



## Conditions préalables

Assurez-vous que les conditions préalables suivantes sont remplies avant de continuer :


- **AEM Forms as a Cloud Service** : instance de création active disposant d’une licence Forms.
- **Compte GitHub** : compte personnel ou professionnel pour la gestion du référentiel.
- **Configuration du référentiel** : sélectionnez l’une des options suivantes :
   - **Nouveau projet** : [créez un projet AEM avec le bloc de formulaires adaptatifs](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block). Le référentiel est préconfiguré pour Edge Delivery Services.
   - **Projet existant** : [ajoutez un bloc de formulaires adaptatifs à un référentiel existant](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) et mettez à jour la configuration.

- **Connexion AEM-GitHub** : [établissez une connexion](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template) entre votre instance AEM et le référentiel GitHub.
- **Edge Delivery Services** : assurez-vous que le référentiel est configuré pour un déploiement automatique.
- **Autorisations** : vérifiez que vous disposez des droits d’accès nécessaires pour la création et la publication de formulaires.

- Vérifiez que le référentiel GitHub contient le bloc de formulaires adaptatifs.



## Workflow de création et de publication de formulaire

Le processus est composé de trois phases principales :

- **Phase 1 :** [création de formulaire](#step-1-form-creation)
- **Phase 2 :** [création et conception du formulaire](#step-2-form-authoring-and-design)
- **Phase 3 :** [configuration et publication](#step-3-configuration-and-publishing)

Chaque phase comprend des étapes de validation pour confirmer une configuration correcte.


### Étape 1 : création de formulaire

1. **Accéder à la création de formulaires**
   - Connectez-vous à votre instance de création AEM Forms as a Cloud Service.
   - Accédez à **Adobe Experience Manager** > **Formulaires** > **Formulaires et documents**.
   - Cliquez sur **Créer** > **Formulaires adaptatifs**.

1. **Sélectionner un modèle**
   - Dans l’onglet **Source**, sélectionnez un **modèle basé sur Edge Delivery Services**.
   - Le bouton **Créer** devient activé.

     ![Créer des formulaires EDS](/help/edge/assets/create-eds-forms.png)

1. **Configurer les options (facultatif)**
   - **Onglet Source de données** : sélectionnez l’intégration de données si nécessaire.
   - **Onglet Envoi** : sélectionnez une action d’envoi (configurable ultérieurement).
   - **Onglet Diffusion** : définissez le planning de publication/dépublication.

1. **Terminer la configuration du formulaire**
   - Cliquez sur **Créer** pour ouvrir l’assistant de création de formulaires.
   - Entrez la commande suivante :
      - **Nom** : identifiant interne (pas d&#39;espace, utilisez des tirets).
      - **Titre** : nom d’affichage du formulaire.
      - **URL GitHub** : URL du référentiel (par exemple, `https://github.com/your-org/your-repo`).

   ![Assistant Créer un formulaire](/help/edge/assets/create-form-wizard.png)

1. **Validation**
   - Après avoir cliqué sur **Créer**, vérifiez les éléments suivants :
      - Le formulaire s’ouvre dans l’éditeur universel.
      - L’URL GitHub est correctement liée.
      - La palette de composants est disponible.
      - La zone de travail du formulaire est visible.

   ![Interface de l’éditeur universel](/help/edge/assets/author-form.png)

**Résultat :** le formulaire est prêt pour la création dans l’éditeur universel.

### Étape 2 : création et conception de formulaire


1. **Accédez à la bibliothèque de composants**
   - Ouvrez l’explorateur de contenu dans l’éditeur universel.
   - Accédez à la section **Formulaire adaptatif** dans l’arborescence de contenu.

   ![ Navigation dans l’arborescence de contenu ](/help/edge/assets/content-tree.png)

1. **Ajout de champs de formulaire**
   - Cliquez sur l’icône **Ajouter** pour ouvrir la bibliothèque de composants.
   - Sélectionnez les composants de votre choix dans la liste **Composants de formulaire adaptatif**.
   - Faites glisser et déposez des composants sur la zone de travail du formulaire.

   ![Ajout de composants](/help/edge/assets/add-component.png)

1. **Concevoir le formulaire**
   - Configurez les propriétés du champ dans le panneau des propriétés.
   - Définissez des règles et des comportements de validation.
   - Ajustez le style et la mise en page selon vos besoins.

   ![Formulaire d’enregistrement complété](/help/edge/assets/contact-us.png)

#### Validation

- Tous les champs obligatoires sont présents.
- Les propriétés des champs sont correctement configurées.
- La mise en page est réactive et accessible.
- Les règles de validation fonctionnent comme prévu.

#### Étapes suivantes

- [Configurer les actions d’envoi](/help/edge/docs/forms/universal-editor/submit-action.md) pour la gestion des données.
- [Guide de l’éditeur universel](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg) pour les fonctionnalités avancées.

### Étape 3 : configuration et publication

Configurez Edge Delivery Services et publiez votre formulaire.

**Configuration :** automatique (aucune configuration manuelle requise).

- La connexion au référentiel GitHub et la configuration Edge Delivery Services sont créées lors de la création du formulaire.
- Les points d’entrée de publication sont configurés automatiquement.

**Vérification :**

- Confirmez que la configuration s’affiche dans les paramètres du formulaire.
- Assurez-vous que l’URL GitHub est correctement liée.

![Configuration EDS automatique](/help/edge/assets/aem-instance-eds-configuration.png)

#### Publication du formulaire

1. Dans l’éditeur universel, cliquez sur le bouton **Publier** (coin supérieur droit).
2. Confirmez que la publication a réussi dans la boîte de dialogue.
3. Notez les URL générées pour les versions intermédiaires et en ligne.

   ![Publication de l’éditeur universel](/help/edge/assets/publish-form.png)

- [Guide de publication](/help/edge/docs/forms/universal-editor/publish-forms.md)

## URL de formulaires

Les formulaires publiés sont accessibles via des URL Edge Delivery Services.

### Structure de l’URL

- **Intermédiaire (prévisualisation/test) :**

  ```
  https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
  ```

- **En ligne (production) :**

  ```
  https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>
  ```

#### Paramètres d’URL

- `<branch>` : nom de la branche GitHub (par exemple, `main`, `develop`)
- `<repo>` : nom du référentiel GitHub (par exemple, `my-forms-project`)
- `<owner>` : nom d’utilisation ou organisation GitHub (par exemple, `company-name`).
- `<form_name>` : identifiant du formulaire tel que défini dans AEM (par exemple, `contact-us`)

#### Exemple

Exemple pour le formulaire `contact-us` dans le référentiel `forms-project` de l’organisation `acme-corp` :

- **Intermédiaire :** `https://main--forms-project--acme-corp.aem.page/content/forms/af/contact-us`
- **En direct :** `https://main--forms-project--acme-corp.aem.live/content/forms/af/contact-us`

#### Différences d’environnement

- **Intermédiaire (.page) :** dernières modifications pour le test.
- **En direct (.live) :** contenu publié pour la production.

![Structure de l’URL](/help/edge/docs/forms/universal-editor/assets/url-structure.svg)
*Répartition de la structure de l’URL du formulaire Edge Delivery Services*

#### Exemples visuels

**Modèle Edge Delivery Services :**

- Intermédiaire : ![version intermédiaire du formulaire d’enregistrement](/help/forms/assets/registration-form-staged-version.png)
- En direct : ![version en direct du formulaire d’enregistrement](/help/forms/assets/registration-form-live-version.png)

## Résolution des problèmes

Vous trouverez ci-dessous les problèmes courants et les solutions pour AEM Forms avec Edge Delivery Services.

+++Le formulaire ne charge pas

**Problème :** l’URL du formulaire renvoie une page 404 ou vide.

**Résolution :**

- Supprimez l’extension `.html` des URL.
- Vérifiez que le formulaire est publié.
- Vérifiez le référentiel GitHub pour le bloc de formulaires adaptatifs.
- Assurez-vous que le nom du formulaire correspond à l’URL (sensible à la casse).

+++

+++Problèmes de configuration

**Problème :** la configuration de Edge Delivery Services ne fonctionne pas.

**Résolution :**

- Assurez-vous que l’URL GitHub est au format `https://github.com/owner/repository`.
- Utilisez le nom de branche correct dans la configuration.
- Vérifiez l’accès au référentiel (public ou authentifié).
- Vérifiez `fstab.yaml` afin d’obtenir les informations GitHub correctes.

+++

+++Problèmes de publication

**Problème :** les modifications n’apparaissent pas sur le site actif.

**Résolution :**

- Patientez 2 à 3 minutes pour l’actualisation du cache du réseau CDN.
- Confirmez que le workflow de publication est terminé.
- Testez d’abord l’environnement intermédiaire (.page).
- Assurez-vous que le référentiel GitHub est mis à jour.

+++

+++Problèmes liés à l’éditeur universel

**Problème :** impossible de modifier le formulaire ou les composants ne se chargent pas.

**Résolution :**

- Utilisez un navigateur pris en charge (Chrome, Firefox, Safari).
- Effacez la mémoire cache et les cookies du navigateur.
- Vérifiez la connectivité réseau.
- Confirmez les autorisations de création.

+++

+++Erreurs d’envoi de formulaire

**Problème :** les envois de formulaire ne fonctionnent pas.

**Résolution :**

- Configurez l’action Envoyer dans les propriétés du formulaire.
- Testez manuellement les points d’entrée d’envoi.
- Vérifiez les paramètres CORS en cas d’incorporation de formulaires.
- Vérifiez que les champs obligatoires sont configurés.

+++

+++Problèmes de performances

**Problème :** chargement du formulaire lent ou faibles performances.

**Résolution :**

- Optimisez les images.
- Supprimez les composants inutiles.
- Utilisez le CDN Edge Delivery Services.
- Réduisez le JavaScript/CSS personnalisé.

+++

+++Obtention d’aide

Si les problèmes persistent :

1. Vérifiez l’état du service Adobe Experience Cloud.
2. Consultez la [documentation d’Edge Delivery Services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=fr).
3. Visitez [Communauté Adobe Experience League](https://experienceleaguecommunities.adobe.com/?profile.language=fr).
4. Contactez l’assistance clientèle Adobe.

+++

## Étapes suivantes

Après avoir créé et publié le formulaire, tenez compte des points suivants :

- [Configurer les actions Envoyer](/help/edge/docs/forms/universal-editor/submit-action.md) : configurez la gestion des données et les intégrations.
- [Modèles de données de formulaire](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) : connectez les formulaires aux sources de données back-end.
- [Bonnes pratiques relatives à Edge Delivery Services](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=fr) : optimisez les performances.
- [Analyse du formulaire](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/analytics.html?lang=fr) : suivez les performances des formulaires et le comportement des utilisateurs et utilisatrices.

