---
title: Compétence en création de communication
description: Découvrez les compétences de création de communication de l’agent de production d’expérience et comment utiliser le langage naturel pour créer des communications interactives.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: dab727f81a8863ca82c7c531e65c365b29fd5c23
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---


# Compétence de création de communication {#ic-creation-skill}

>[!NOTE]
>
> La compétence Création de communications est actuellement en version Alpha. Si vous souhaitez participer, veuillez envoyer une demande à partir de votre adresse e-mail officielle à [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com).

Les communications interactives sont des documents personnalisés, pilotés par les données, conçus pour la correspondance commerciale telle que les relevés de compte, les documents de politique, les factures, les kits de bienvenue et les avis de prestations. Contrairement aux formulaires qui collectent les entrées des utilisateurs, les communications interactives génèrent des documents de sortie avec un contenu dynamique spécifique au destinataire.

La compétence Création de communication est une fonctionnalité de l’agent de production d’expérience conçue pour développer des communications interactives à l’aide d’invites en langage naturel. Cette compétence génère automatiquement une correspondance personnalisée, pilotée par les données, pour l’impression (au format PDF). La compétence est surfacée via l’assistant d’IA.

Voici quelques-uns des principaux avantages des compétences en création de communication :

* **Développement accéléré des communications** : créez rapidement des communications à l’aide de commandes en langage naturel simples, éliminant la nécessité d’apprendre les interfaces de produit traditionnelles.
* **Correspondance cohérente et interne à la marque** : créez des communications qui respectent les directives de votre organisation en matière d’image de marque, de modèles et de style en utilisant des modèles et des styles approuvés.
* **Barrière technique plus faible** : permet aux utilisateurs professionnels de créer facilement des communications, sans avoir besoin d’une expertise technique avancée ou approfondie en matière de produits.

## Fonctionnalités {#capabilities}

<!-- * **Create personalized communications with plain text prompt**: You can create communication documents for print (in PDF format) by submitting your requirements in plain language. The agent automatically generates appropriate document structures, layouts, and data bindings based on your natural language description. -->

* **Créer à partir de modèles** : vous pouvez utiliser des modèles organisationnels approuvés pour garantir la cohérence de la marque et les normes de conformité. L’agent tire parti de vos modèles et directives de style existants pour créer une correspondance de marque conforme aux exigences réglementaires.

* **Importer et convertir des images et des documents existants en communications interactives** : vous pouvez importer et transformer des documents existants en communications interactives. L’agent analyse le contenu chargé pour détecter les champs, conserver les mises en page et créer une correspondance pilotée par les données grâce aux fonctionnalités de contenu dynamique. Les formats pris en charge sont les PDF, les images (JPG, PNG) et les modèles dessinés à la main.


## Exemples d’invites {#sample-prompts}

* *Créez une communication pour un relevé de prêt à l’aide du modèle à l’adresse https://[aem-author-url]/path/to/pdf/file*
* *Créez une communication à partir de PDF à l’adresse https://[aem-author-url]/path/to/pdf/file*
* *Créez une communication à partir du fichier image à l’adresse https://[aem-author-url]/path/to/image/file*
* Créez une lettre en utilisant le fichier PDF à l’adresse https://[aem-author-url]/path/to/pdf/file


## Affiner votre communication {#refine-with-ic-editor}


Après avoir créé votre structure de communication initiale à l’aide de l’assistant AI, vous pouvez utiliser l’éditeur de communications interactives pour affiner et améliorer votre document. Dans l’éditeur de communications interactives, vous pouvez fournir des invites en langage naturel pour :

* **Ajouter des champs et du contenu** : ajoutez de nouveaux champs, blocs de texte, images, graphiques, tableaux et autres composants à vos documents de communication à l’aide d’invites en langage naturel. L’agent interprète vos instructions et insère les éléments appropriés avec une structure et une mise en forme appropriées.

* **Modifier les champs et le contenu** : modifiez les champs et le contenu existants dans vos documents de communication au moyen de commandes de conversation. Mettez à jour les propriétés du champ, modifiez le contenu du texte, ajustez les liaisons de données et affinez les configurations de composant.

* **Supprimer des champs et du contenu** : supprimez les champs, composants ou sections indésirables de vos documents de communication à l’aide des instructions en langage naturel. L’agent supprime les éléments spécifiés tout en conservant l’intégrité de la structure du document et de la disposition.

* **Mettre en forme des champs et du contenu** : appliquez une mise en forme et un style aux champs et au contenu à l’aide d’invites en langage naturel. Ajustez les polices, les couleurs, l’alignement, l’espacement et d’autres propriétés visuelles pour répondre aux directives de votre marque et aux exigences de conception.

### Exemples d’invites pour affiner les communications {#sample-prompts-refining}

* *Générer une lettre de règlement de demande d’assurance automobile*
* *Mettre le texte de clause de non-responsabilité en italique*
* *Remplacez la taille de police du texte de clause de non-responsabilité par 12*
* *Mettre à jour la couleur de police du texte de clause de non-responsabilité en rouge*
* *Mettre à jour la couleur d’arrière-plan des zones de texte d’en-tête et de pied de page en gris clair*
* *Ajouter un nouveau panneau de clause de non-responsabilité avec des champs de signature et de confirmation*
* *Supprimer le champ de texte de confirmation*
* *Ajoutez un tableau des détails de paiement avec trois colonnes*
* *Mettre à jour l’alignement du champ du numéro de politique sur le centre*
* *Remplacez l’espacement des lignes de la section Conditions générales par 1.5*

Pour plus d’informations sur les fonctionnalités de l’éditeur de communication interactive, voir [Documentation sur les communications interactives](/help/forms/introduction-to-interactive-communication.md).
