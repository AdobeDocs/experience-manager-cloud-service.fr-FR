---
Title: How Edge Delivery Services Forms work?
Description: This article provides information on how Edge Delivery Services Forms work. It also provides information on various form authoring platforms, including the Universal Editor and document-based authoring.
Keywords: Universal Editor for WYSIWYG authoring, document-based authoring, Working of Edge Delivery Services Forms, How Edge Delivery Services Forms work?
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 1244bafe1263c52a584b587845c1a12b9ddfd333
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 57%

---


# Edge Delivery Services Forms

Adobe Edge Delivery Services Forms transforme la création, l’exécution et le traitement des formulaires. Grâce à Edge Delivery Services, les entreprises peuvent créer des formulaires numériques rapides, sécurisés et hautement disponibles, ce qui améliore l’expérience utilisateur et l’efficacité opérationnelle dans un environnement de développement rapide. Avec Edge Delivery Services Forms, vous pouvez augmenter les conversions, réduire les coûts et accélérer la diffusion de contenu.

## Avantages de Edge Delivery Services Forms

* **Création de formulaire plus rapide** : créez des formulaires hautes performances avec un score Lighthouse parfait et surveillez en permanence leurs performances en situation réelle à l’aide de la surveillance réelle de l’utilisateur (RUM).

* **Processus de création rationalisé** : gérez facilement du contenu provenant de plusieurs sources pour une plus grande flexibilité. Par défaut, vous pouvez créer des formulaires à l’aide de WYSIWYG et de la création de documents, ce qui permet une intégration transparente de divers formats de contenu.

* **Facilité d’utilisation pour les utilisateurs n’ayant pas de connaissances techniques** : Edge Delivery Services permet aux non-programmeurs de gérer et de publier facilement des formulaires sans avoir à disposer de connaissances approfondies en matière de programmation.

* **Amélioration de l’expérience utilisateur** : permet des temps de chargement rapides et des interactions fluides, ce qui réduit au minimum les temps d’attente et offre aux utilisateurs une expérience de remplissage de formulaires intuitive.

* **Exécution sans serveur** : Edge Delivery Services permet l’exécution sans serveur de la logique de formulaire. Cela inclut les éléments suivants :

   * **Validation côté client** : la validation des champs de formulaire se produit côté client, ce qui réduit les délais d’aller-retour.

   * **Préremplissage et Personalization** : le préremplissage des données de formulaire est géré côté client pour une expérience utilisateur fluide.

   * **Traitement des envois** : les envois de formulaire sont validés et transférés en toute sécurité sans serveur central

## Comment fonctionne Edge Delivery Services Forms ?

Les utilisateurs peuvent créer des Forms Edge Delivery Services à l’aide d’outils de création documentaires tels que Google Drive, SharePoint ou l’éditeur universel (création WYSIWYG), tout en exploitant les styles, comportements et composants de base disponibles dans le référentiel GitHub. Une fois la création effectuée, Edge Delivery Services Forms peut envoyer des données à n’importe quelle plateforme à l’aide du service d’envoi Forms.

![Fonctionnement de Edge Delivery Services Forms](/help/edge/docs/forms/assets/eds-forms-working.png)

### Composants clés de Edge Delivery Services Forms

Les principaux composants de Forms des services Edge Delivery sont les suivants :

* **Référentiel GitHub** : le référentiel GitHub sert de référence pour la création de Forms Edge Delivery Services. Les formulaires tirent parti du style et des fonctionnalités de base du référentiel et permettent aux utilisateurs et utilisatrices d’ajouter des personnalisations et des composants personnalisés au Forms Edge Delivery Services.

* **Création de formulaires** : Edge Delivery Services Forms prend en charge deux types de création : WYSIWYG et la création basée sur des documents. La création basée sur des documents permet aux utilisateurs de créer des formulaires à l’aide d’outils familiers tels que Google Docs et Microsoft Office. La création WYSIWYG permet aux utilisateurs et utilisatrices de concevoir des formulaires visuellement à l’aide de l’éditeur universel, ce qui facilite la création et la gestion des formulaires pour les personnes n’ayant pas de connaissances techniques. L’éditeur universel offre une expérience de création de formulaire intuitive et permet d’accéder à de nombreuses fonctionnalités de formulaire.

* **Service d’envoi Forms** : le service d’envoi Forms vous permet de stocker les données des envois de formulaires sur n’importe quelle plateforme, telle que OneDrive, SharePoint ou Google Sheets, ce qui facilite l’accès et la gestion des données de formulaire dans votre système préféré.

## Création d’un formulaire

Adobe Experience Manager propose et prend en charge plusieurs éditeurs pour créer un formulaire. Vous pouvez utiliser :
* [Éditeur universel (pour la création WYSIWYG)](#universal-editor-for-wysiwyg-authoring)
* [Microsoft Excel ou Google Sheets (création basée sur des documents)](#microsoft-excel-or-google-sheets-known-as-document-based-authoring)

### Éditeur universel (pour la création WYSIWYG)

L’éditeur universel est un éditeur visuel polyvalent qui offre une fonctionnalité « ce que vous voyez est ce que vous obtenez » (WYSIWYG), assurant ainsi une expérience de création de formulaire intuitive. Il est recommandé d’utiliser l’éditeur universel lors de la création de formulaires, car ce dernier offre une conception moderne et conviviale dotée d’une interface pratique par glisser-déposer.

Pour créer des formulaires à l’aide de l’éditeur universel, les modèles Edge Delivery Services disponibles dans l’environnement AEM sont utilisés. Ces formulaires héritent de l’aspect des configurations dans le référentiel GitHub Edge Delivery Services. [Une connexion entre votre environnement AEM et le référentiel GitHub Edge Delivery Services](/help/edge/docs/forms/publishing-forms.md) est établie pour permettre la publication de ces formulaires sur les Edge Delivery Services.

Pour des informations détaillées sur la création à l’aide de l’éditeur universel, consultez l’article [Créer du contenu avec l’éditeur universel](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/sites/authoring/universal-editor/authoring).

### Microsoft Excel ou Google Sheets (création basée sur des documents)

Vous pouvez créer des formulaires à l’aide de la création basée sur des documents avec des fichiers Microsoft Excel ou Google Sheets, ce qui vous permet d’exploiter les solides écosystèmes et API de Google Sheets, Microsoft Excel et Microsoft SharePoint. Cette approche est particulièrement utile pour créer des formulaires simples sans services d’envoi avancés.

Pour commencer à créer un formulaire à l’aide de Microsoft Excel ou de Google Sheets, [configurez un projet AEM à l’aide du modèle standard d’AEM Forms](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block), puis clonez le référentiel GitHub correspondant sur votre ordinateur local. AEM Forms Edge Delivery propose une fonctionnalité appelée Bloc de formulaires adaptatifs, qui simplifie le processus de création de formulaires pour la capture et le stockage des données. Pour savoir comment créer et publier des formulaires à l’aide du bloc de formulaires adaptatifs sur Edge Delivery Services, reportez-vous à la section [Créer un formulaire](/help/edge/docs/forms/create-forms.md).

<!--
## Adaptive Forms editors (for Core Components or foundation components based authoring)

You can author forms that are engaging, responsive and dynamic. The Adaptive Form editor provides a user-friendly wizard that allows you to quickly create Adaptive Forms. The form wizard features easy tab navigation, enabling you to select pre-configured templates for foundation or core components, themes, data models, and submission options to create a form efficiently. 

[Authoring forms with Core Components](/help/forms/creating-adaptive-form-core-components.md) allows you to leverage standardized data capture components that can be customized, reducing development time and lowering maintenance costs for digital enrollment experiences. These forms can be published using the Adaptive Forms Block on Edge Delivery Services or through the AEM Publish instance. 

[Authoring forms with Foundation Components](/help/forms/create-an-adaptive-form.md) uses classic data capture components. These forms can only be published using the AEM Publish instance. 

You can also publish forms created using Adaptive Forms Editors on Edge Delivery Services by establishing [connection between your AEM environment and the Edge Delivery Services GitHub repository](/help/edge/docs/forms/publishing-forms.md).


| **Adaptive Forms editors** | Provides a wizard-driven approach to quickly start forms authoring using templates, styling, and predefined fields. | Use these editors to create Core Components based forms or Foundation Components based forms. | These forms can be published on Edge Delivery Services or via AEM Publish instances.  | Use these editors to create Core Components based forms or Foundation Components based forms. Ideal for scenarios involving complex forms, complex workflows, custom actions, or integrations with external systems. |  



## Types of Publishing for Edge Delivery Services Forms

You can publish Edge Delivery Services Forms on one of the following:

* **Edge Delivery Services Form Submission**: Edge Delivery Services Form Submissions ensure that form interactions, including submission and data processing, are handled efficiently and securely. This enables a faster and more reliable user experience, particularly during high traffic periods. By processing form submissions at the edge, Edge Delivery Services minimizes the reliance on a centralized server.

* **AEM Publish instance**: The AEM Forms server offers a publish instance that manages the forms and related assets available to end users.
-->

### Comment choisir entre différents types de création de formulaires ?

Le tableau suivant décrit les fonctionnalités et les cas d’utilisation de chaque éditeur de création, ce qui vous permet de choisir le bon en fonction de vos besoins et de vos envois de formulaire.

| **Éditeur de création de formulaire** | **Approche clé** | **Fonctionnalités** | **Méthode de publication** | **Cas d’utilisation** |
|--------|-----------|-------|-------|------------------------------------------------|
| **Création basée sur des documents** | Tire parti d’outils familiers tels que Google Docs et Microsoft Office pour la création de formulaires. | Les formulaires sont conçus à l’aide de feuilles de calcul, avec des données directement envoyées aux feuilles Google Sheets ou Microsoft Excel. </br> </br> Ces formulaires sont plus rapides à créer et à déployer. Vous n’avez pas besoin d’une connaissance préalable d’AEM pour développer des composants et des styles personnalisés pour ces formulaires. | Ces formulaires sont publiés sur Edge Delivery Services et ont un score Google Lighthouse très élevé. </br> </br> Le score élevé entraîne un rendu plus rapide et un meilleur référencement. | Ces formulaires sont parfaits pour le prototypage rapide ou les formulaires de base pour lesquels des services d’envoi avancés ne sont pas nécessaires. </br> </br> Ils sont adaptés aux formulaires d’enquête, d’enregistrement ou de commentaires nécessitant un stockage des données dans des feuilles de calcul. Ces formulaires sont publiés dans Edge Delivery Services |
| **Éditeur universel** </br> </br> Utilisez l’éditeur universel pour créer vos formulaires. | Offre une interface WYSIWYG pour la création intuitive de formulaires. | Les formulaires sont conçus à l’aide d’une interface intuitive par glisser-déposer. </br> </br> Ces formulaires empruntent l’apparence du référentiel GitHub Edge Delivery Services configuré pour le formulaire correspondant. | Ces formulaires sont publiés sur Edge Delivery Services et ont un score Google Lighthouse très élevé. </br> </br> Le score élevé entraîne un rendu plus rapide et un meilleur référencement. | Ces formulaires sont parfaits pour les sites et les pages Edge Delivery Service. Ces scénarios de formulaires impliquent des formulaires et des workflows complexes, des actions personnalisées ou des intégrations à des systèmes externes |

>[!NOTE]
>
>
> Si vous constatez des fonctionnalités manquantes dans l’éditeur universel qui étaient auparavant disponibles dans l’éditeur de formulaires adaptatifs, vous pouvez les demander en envoyant un e-mail à mailto:aem-forms-ea@adobe.com à l’aide de votre adresse e-mail officielle.

## Voir également

{{see-more-forms-eds}}




