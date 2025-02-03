---
Title: Authoring a Form
Description: This article provides information on various form authoring platforms, including the Universal Editor, document-based authoring, and Adaptive Forms editors (Core Components and Foundation Components).
Keywords: Universal Editor for WYSIWYG authoring, document-based authoring, Adaptive Forms editors, Adaptive Forms editors for Core Components authoring, Adaptive Forms editors for Foundation Components authoring
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: bdc0e51a8b16df432f1f1aeabed11135fb8c8e0c
workflow-type: ht
source-wordcount: '877'
ht-degree: 100%

---


# Création d’un formulaire

Adobe Experience Manager propose et prend en charge plusieurs éditeurs pour créer un formulaire. Vous pouvez utiliser :
* Éditeur universel (pour la création WYSIWYG)
* Microsoft Excel ou Google Sheets (création basée sur des documents)
* Éditeurs de formulaires adaptatifs (pour la création basée sur les composants principaux ou les composants de base)

**[image à ajouter]**

## Éditeur universel (pour la création WYSIWYG)

L’éditeur universel est un éditeur visuel polyvalent qui offre une fonctionnalité « ce que vous voyez est ce que vous obtenez » (WYSIWYG), assurant ainsi une expérience de création de formulaire intuitive. Il est recommandé d’utiliser l’éditeur universel lors de la création de formulaires, car ce dernier offre une conception moderne et conviviale dotée d’une interface pratique par glisser-déposer.

Pour créer des formulaires à l’aide de l’éditeur universel, les modèles Edge Delivery Services disponibles dans l’environnement AEM sont utilisés. Ces formulaires héritent de l’aspect des configurations dans le référentiel GitHub Edge Delivery Services. [Une connexion entre votre environnement AEM et le référentiel GitHub Edge Delivery Services](/help/edge/docs/forms/publishing-forms.md) est établie pour permettre la publication de ces formulaires sur les Edge Delivery Services.

Pour des informations détaillées sur la création à l’aide de l’éditeur universel, consultez l’article [Créer du contenu avec l’éditeur universel](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/sites/authoring/universal-editor/authoring).

## Microsoft Excel ou Google Sheets (création basée sur des documents)

Vous pouvez créer des formulaires à l’aide de la création basée sur des documents avec des fichiers Microsoft Excel ou Google Sheets, ce qui vous permet d’exploiter les solides écosystèmes et API de Google Sheets, Microsoft Excel et Microsoft SharePoint. Cette approche est particulièrement utile pour créer des formulaires simples sans services d’envoi avancés.

Pour commencer à créer un formulaire à l’aide de Microsoft Excel ou de Google Sheets, [configurez un projet AEM à l’aide du modèle standard d’AEM Forms](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block), puis clonez le référentiel GitHub correspondant sur votre ordinateur local. AEM Forms Edge Delivery propose une fonctionnalité appelée Bloc de formulaires adaptatifs, qui simplifie le processus de création de formulaires pour la capture et le stockage des données. Pour savoir comment créer et publier des formulaires à l’aide du bloc de formulaires adaptatifs sur Edge Delivery Services, reportez-vous à la section [Créer un formulaire](/help/edge/docs/forms/create-forms.md).

## Éditeurs de formulaires adaptatifs (pour la création basée sur les composants principaux ou les composants de base)

Vous pouvez créer des formulaires attrayants, réactifs et dynamiques. L’éditeur de formulaire adaptatif fournit un assistant convivial qui vous permet de créer rapidement des formulaires adaptatifs. L’assistant de formulaire offre une navigation facile par onglets, ce qui vous permet de sélectionner des modèles préconfigurés pour les composants de base ou principaux, les thèmes, les modèles de données et les options d’envoi, afin de créer un formulaire de manière efficace.

La [création de formulaires avec des composants principaux](/help/forms/creating-adaptive-form-core-components.md) vous permet d’exploiter des composants de capture de données normalisés qui peuvent être personnalisés, ce qui réduit le temps de développement et les coûts de maintenance pour les expériences d’inscription numérique. Ces formulaires peuvent être publiés à l’aide du bloc de formulaires adaptatifs sur Edge Delivery Services ou via l’instance de publication AEM.

La [création de formulaires avec des composants de base](/help/forms/create-an-adaptive-form.md) utilise des composants de capture de données classiques. Ces formulaires ne peuvent être publiés qu’à l’aide de l’instance de publication AEM.

Vous pouvez également publier des formulaires créés à l’aide des éditeurs de formulaires adaptatifs sur Edge Delivery Services en établissant une [connexion entre votre environnement AEM et le référentiel GitHub Edge Delivery Services ](/help/edge/docs/forms/publishing-forms.md).

## Comment choisir entre différents types de création de formulaires ?

Le tableau suivant décrit les fonctionnalités et les cas d’utilisation de chaque éditeur de création, ce qui vous permet de choisir le bon en fonction de vos besoins et de vos envois de formulaire.

| **Éditeur de création de formulaire** | **Approche clé** | **Fonctionnalités** | **Méthode de publication** | **Cas d’utilisation** |
|--------|-----------|-------|-------|------------------------------------------------|
| **Création basée sur des documents** | Tire parti d’outils familiers tels que Google Docs et Microsoft Office pour la création de formulaires. | Les formulaires sont conçus à l’aide de feuilles de calcul, avec des données directement envoyées aux feuilles Google Sheets ou Microsoft Excel. </br> </br> Ces formulaires sont plus rapides à créer et à déployer. Vous n’avez pas besoin d’une connaissance préalable d’AEM pour développer des composants et des styles personnalisés pour ces formulaires. | Ces formulaires sont publiés sur Edge Delivery Services et ont un score Google Lighthouse très élevé. </br> </br> Le score élevé entraîne un rendu plus rapide et un meilleur référencement. | Ces formulaires sont parfaits pour le prototypage rapide ou les formulaires de base pour lesquels des services d’envoi avancés ne sont pas nécessaires. </br> </br> Ils sont adaptés aux formulaires d’enquête, d’enregistrement ou de commentaires nécessitant un stockage des données dans des feuilles de calcul. Ces formulaires sont publiés dans Edge Delivery Services |
| **Éditeur universel** </br> </br> Utilisez l’éditeur universel pour créer vos formulaires. | Offre une interface WYSIWYG pour la création intuitive de formulaires. | Les formulaires sont conçus à l’aide d’une interface intuitive par glisser-déposer. </br> </br> Ces formulaires empruntent l’apparence du référentiel GitHub Edge Delivery Services configuré pour le formulaire correspondant. | Ces formulaires sont publiés sur Edge Delivery Services et ont un score Google Lighthouse très élevé. </br> </br> Le score élevé entraîne un rendu plus rapide et un meilleur référencement. | Ces formulaires sont parfaits pour les sites et les pages Edge Delivery Service. Ces scénarios de formulaires impliquent des formulaires et des workflows complexes, des actions personnalisées ou des intégrations à des systèmes externes |
| **Éditeur de formulaires adaptatifs** | Fournit une approche pilotée par un assistant pour lancer rapidement la création de formulaires à l’aide de modèles, de styles et de champs prédéfinis. | Utilisez ces éditeurs pour créer des formulaires basés sur les composants principaux ou des formulaires basés sur les composants de base. | Ces formulaires peuvent être publiés sur Edge Delivery Services ou via des instances de publication AEM. | Utilisez ces éditeurs pour créer des formulaires basés sur les composants principaux ou des formulaires basés sur les composants de base. Ils sont parfaits pour les scénarios impliquant des formulaires et des workflows complexes, des actions personnalisées ou des intégrations à des systèmes externes. |


>[!NOTE]
>
>
> Si vous constatez des fonctionnalités manquantes dans l’éditeur universel qui étaient auparavant disponibles dans l’éditeur de formulaires adaptatifs, vous pouvez les demander en envoyant un e-mail à mailto:aem-forms-ea@adobe.com à l’aide de votre adresse e-mail officielle.

## Article connexe

* [Création basée sur des documents à l’aide de Microsoft Excel ou de Google Sheets](/help/edge/docs/forms/create-forms.md)
* [Éditeur universel pour la création WYSIWYG](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
* [Créer un formulaire adaptatif (composants de base)](/help/forms/creating-adaptive-form.md)
* [Créer un formulaire adaptatif (composants principaux)](/help/forms/create-an-adaptive-form.md)

## Voir également

{{see-more-forms-eds}}