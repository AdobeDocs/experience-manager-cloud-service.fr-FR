---
title: Compétence en création de formulaire
description: Découvrez les compétences de création de formulaires de l’agent de production d’expérience et comment utiliser le langage naturel pour créer des formulaires en partant de zéro.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: aa8369979c99535f0fd77e6a51af10cc17afd971
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---


# Compétence de création de formulaire {#form-creation-skill}

La compétence de création de formulaire est une fonctionnalité de l’agent de production d’expérience conçu pour développer des formulaires à l’aide d’invites en langage naturel. Cette compétence génère automatiquement la structure de formulaire et les types de champ appropriés. La compétence est surfacée via l’assistant d’IA.

Voici quelques-uns des principaux avantages des compétences de création de formulaire :

* **Développement accéléré de formulaires** : créez rapidement des formulaires à l’aide de
commandes en langage naturel simple, éliminant la nécessité d’apprendre les interfaces de produit traditionnelles.
* **Expériences cohérentes et sur la marque** : créez des formulaires qui suivent les directives de votre organisation en matière d’image de marque, de modèles et de style à l’aide de modèles et de styles approuvés.
* **Barrière technique plus faible** : permet aux utilisateurs professionnels de créer facilement des formulaires, sans avoir besoin d’une expertise technique avancée ou d’un savoir-faire approfondi en matière de produits.

## Fonctionnalités {#capabilitiess}

* **Créer un formulaire avec une invite en texte brut** : vous pouvez créer un formulaire en soumettant vos besoins en langage clair. L’agent génère automatiquement la structure de formulaire appropriée, les types de champs et les expériences sur la marque en fonction de votre description en langage naturel et du modèle spécifié. Cette fonctionnalité accélère la création de formulaires tout en garantissant le respect des normes de marque et de conformité.

* **Importer un document PDF et le convertir en formulaire** : vous pouvez importer et transformer des documents PDF existants en formulaires. L’agent analyse le contenu chargé pour détecter les types de champs, conserver les mises en page et améliorer les formulaires grâce à une conception réactive et à une logique de validation, tout en garantissant le respect des normes de marque et de conformité.

  Lorsque vous utilisez l’une des fonctionnalités ci-dessus, vous êtes invité à choisir le type de formulaire à créer, à spécifier un modèle de formulaires adaptatifs basé sur les composants principaux ou un modèle de formulaires adaptatifs basé sur Edge Delivery Services, puis à indiquer votre chemin préféré pour enregistrer le formulaire. Si vous créez un formulaire basé sur Edge Delivery Services, vous pouvez également spécifier l’URL GitHub de votre référentiel.


### Exemples d’invites {#sample-prompts}

* *Créez un formulaire pour la collecte de commentaires avec des champs de nom, d’e-mail et de message*
* *Créez un formulaire de commentaires client avec l’évaluation du produit (1 à 5 étoiles), un champ de commentaire et un e-mail facultatif*
* *Créez un formulaire de contact avec les champs nom, e-mail, liste déroulante d’objet et message*
* *Créez un formulaire d’enregistrement contenant des informations personnelles, les préférences du compte et l’acceptation des conditions*
* *Créez un formulaire de demande de carte de crédit en important le fichier PDF disponible à l’adresse « https:// [aem-author-url ]/path/to/pdf/file »*
* *Créez un formulaire de commentaires à l’aide du modèle standard sur « <https://github.com/wkndforms/wesecure> »*

## Affiner le formulaire {#refine-with-forms-experience-builder}

Après avoir créé votre structure de formulaire initiale à l’aide de l’assistant AI, vous pouvez utiliser le Forms Experience Builder pour :

* **Mettre à jour les formulaires** : ajoutez ou modifiez des champs, ajustez les types de champs et mettez à jour le style selon les besoins à l’aide de l’éditeur visuel.

* **Mettre à jour la disposition** : réorganisez les sections, les groupes ou les champs, ajustez l’espacement et modifiez la hiérarchie visuelle pour améliorer la convivialité et vous assurer que votre formulaire est clair et intuitif pour votre audience.

* **Ajouter une logique métier** : créez une logique conditionnelle, affichez/masquez des règles, des dépendances de champs et définissez des règles de validation.

* **Configurer l’envoi** : permet de configurer l’endroit où les données de formulaire sont envoyées, y compris la configuration des notifications par e-mail, des intégrations aux workflows ou des connexions aux systèmes externes.

Pour plus d’informations, voir la documentation de Forms Experience Builder[.](/help/forms/experience-builder/product-overview.md)


## Activation {#activation}

Pour activer l’agent de production Experience pour votre organisation, l’activation doit être lancée par l’intermédiaire d’Adobe. Commencez le processus en contactant par le biais de :

* E-mail : `experience-production-agent@adobe.com`
* Vous pouvez également contacter l’équipe de compte Adobe désignée.

Pour une expérience d’intégration efficace, préparez et fournissez les détails suivants :

Pour **AEM as a Cloud Service**, partagez les identifiants suivants :

* Identifiant d&#39;organisation
* `product_id`
* `profile_id`

Votre administrateur AEM peut les localiser en procédant comme suit :

1. Accès à <https://adminconsole.adobe.com/>
1. Sélection de **Adobe Experience Manager as a Cloud Service**
1. Choisir l’instance AEM appropriée dans votre environnement
1. Sélection d’un profil avec des autorisations de lecture/écriture pour le contenu approprié
1. Copie de l’URL complète du navigateur à partir de cette page
1. Extraire les valeurs `product_id` et `profile_id` de l’URL\
   (par exemple, une URL telle que `https://adminconsole.adobe.com/products/profiles/users` contient ces paramètres).

Pour la **création de documents Edge Delivery**, fournissez les éléments suivants à votre équipe Adobe :

* Domaines pour votre environnement Edge Delivery Services
* Détails GitHub correspondants :
   * Organisation (Org)
   * Référentiel (Repo)
   * Branche

Fournir des informations complètes et précises accélère le processus d’activation et garantit la mise en service rapide de l’agent de production d’expérience.

<!-- 
#### Import and convert {#import-and-convert}

Transform existing documents into interactive digital forms. The agent analyzes uploaded content to detect field types, preserve layouts, and enhance forms with responsive design and validation logic. Supported formats include Acroforms, XFA PDFs, flat PDFs, images (JPG, PNG), and hand-drawn form photographs.

>[!VIDEO](https://video.tv.adobe.com/v/3474042)

**Prompt examples:**

* *Convert the attached PDF file to an adaptive form*
* *Transform this scanned form image into an interactive digital form*
* *Import the employee onboarding PDF and create an editable form*
* *Convert this paper form photograph into a digital form with validation*
-->

<!-- 
### Embed an existing form to a sites page {#embed-existing-form}

The form creation skill enables seamless integration of existing forms into any sites page through natural language commands. Rather than manually locating, copying, and embedding form components, users can simply specify which form to add and where to place it. The agent handles the technical implementation, ensuring proper rendering and functionality.

>[!VIDEO](https://video.tv.adobe.com/v/PLACEHOLDER)

**Prompt examples:**

* *Embed the contact form to the homepage*
* *Add the existing customer feedback form to the support page*
* *Insert the newsletter signup form into the footer section*
* *Place the registration form on /content/site/signup*
* *Add form "contact-us-2024" to the current page*
-->

<!-- 
### Build and add a form to an existing sites page {#build-and-add-form}

The form creation skill combines form creation and site integration in a single conversational workflow. Users can describe the form they need and specify where to add it, and the agent creates the form and embeds it into the specified page automatically. This eliminates the traditional multi-step process of creating a form separately and then manually adding it to a page.

>[!VIDEO](https://video.tv.adobe.com/v/PLACEHOLDER)

**Prompt examples:**

* *Create a newsletter signup form with email field and add it to the footer*
* *Build a quick contact form with name, email, and message, then add it to /content/about-us*
* *Add a feedback form with rating stars and comment field to this page*
* *Create a simple survey form with 5 questions and embed it on the customer portal homepage*
* *Build an event registration form with name, email, and date selection, then add it to /content/events/conference-2025*
-->
