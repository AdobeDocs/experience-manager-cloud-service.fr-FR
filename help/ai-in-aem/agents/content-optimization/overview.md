---
title: Agent d’optimisation de contenu
description: Découvrez comment utiliser l’agent d’optimisation de contenu pour transformer la manière dont les utilisateurs affinent et adaptent des ressources en appliquant des instructions en langage naturel pour créer des variations prêtes pour le canal.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: ad027974400bdce3428ce96e8804abfe087b48da
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# Agent d’optimisation de contenu {#content-optimization-agent}

L’agent d’optimisation de contenu transforme la manière dont les utilisateurs affinent et adaptent les ressources en appliquant des instructions en langage naturel pour créer des variations prêtes pour le canal. Qu’il s’agisse de générer de nouveaux rendus, d’ajuster les propriétés visuelles, de modifier les arrière-plans ou de préparer des ressources pour des canaux numériques spécifiques, l’agent interprète les intentions de l’utilisateur et effectue automatiquement des tâches de modification complexes. Il fonctionne de manière transparente avec Discovery Agent, récupérant les ressources qu’il trouve et produisant des variations optimisées à l’aide des principales [Dynamic Media avec des fonctionnalités OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) qui répondent aux exigences de la marque, du canal et de la campagne sans effort de conception manuel.

Voici quelques-uns des principaux avantages de l’optimisation du contenu :

* **Transformation simple des ressources** : permet de convertir des invites simples et conversationnelles en opérations d’image précises, telles que le redimensionnement, l’accentuation, la mise en miroir ou le recoloriage, en éliminant le besoin d’outils d’édition spécialisés.

* **Sorties optimisées pour les canaux** : produit rapidement des rendus adaptés à des plateformes spécifiques telles que des histoires sur Instagram, des bannières web ou d’autres points de contact marketing, en s’assurant que les ressources sont prêtes à être utilisées immédiatement.

* **Amélioration de Creative à grande échelle** : applique des ajustements et des améliorations visuels, tels que des modifications en arrière-plan ou des superpositions de graphiques, pour prendre en charge les workflows créatifs volumineux sans ralentir les équipes.

* **[Collaboration transparente avec l’agent Discovery](/help/ai-in-aem/agents/discovery/overview.md)** : s’appuie sur les ressources identifiées par l’agent Discovery, permettant la récupération et l’optimisation des ressources de bout en bout par le biais d’une conversation naturelle.

>[!IMPORTANT]
>
>Les réponses générées par l&#39;IA peuvent être inexactes ou trompeuses. Assurez-vous de vérifier les correctifs et les réponses suggérés.
>
>Consultez également les [Directives d’utilisation de l’IA générative de Adobe Experience Cloud](https://www.adobe.com/fr/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

## Conditions préalables {#prerequisites-content-optimization-agent}

Pour générer des variations ou des optimisations pour les ressources d’image. Vous devez avoir :

* Une licence Dynamic Media valide

* Dynamic Media avec OpenAPI activé dans l’environnement AEM as a Cloud Service.

* Les ressources à l’[état approuvé](/help/assets/manage-organize-assets-view.md#manage-asset-status) dans votre environnement AEM as a Cloud Service.


## Compétences {#skills-content-optimization-agent}

L’agent d’optimisation de contenu fournit les compétences suivantes :

* **Comprendre l’intention grâce au langage naturel**

  L’agent d’optimisation de contenu interprète l’intention de l’utilisateur à partir d’invites en langage naturel, en tenant compte du canal, de la campagne et du contexte d’audience pour déterminer les actions d’optimisation les plus pertinentes.

* **Génère des variantes de contenu dynamique**

  L’agent d’optimisation de contenu crée des variantes optimisées sous la forme d’URL dynamiques personnalisées pour différents canaux et types de format.

* **Optimise le contenu des images**

  L’agent d’optimisation du contenu apporte des améliorations telles que la conversion de format, les ajustements de résolution, le recadrage et l’accentuation pour améliorer la qualité de l’image.

* **Optimisation de ressources à plusieurs variantes**

  L’agent d’optimisation de contenu peut générer plusieurs variations d’image optimisées à partir des ressources renvoyées par l’agent de découverte à l’aide d’une seule invite en langage naturel, ce qui permet aux utilisateurs de produire rapidement et efficacement des rendus prêts pour le canal.

## Personnes {#personas-content-optimization-agent}

Les spécialistes du marketing des canaux, personnage clé de l’agent d’optimisation du contenu, peuvent sélectionner le contenu source haute résolution approprié et demander des formats optimisés adaptés à leurs canaux et segments d’audience.

Les professionnels du marketing et les employés d’agence régionaux peuvent également utiliser l’agent d’optimisation de contenu pour générer rapidement des variations d’image prêtes pour le canal qui prennent en charge une production de contenu plus rapide et plus cohérente.

## Comment accéder à l’agent d’optimisation de contenu ? {#access-content-optimization-agent}

Vous pouvez accéder aux agents dans AEM via l’assistant d’IA. Connectez-vous à experience.adobe.com et vous pourrez commencer à interagir avec l’assistant AI en spécifiant votre invite en langage naturel à l’aide du champ `Ask AI Assistant anything` :

![Accéder à l&#39;agent Discovery](/help/ai-in-aem/agents/discovery/assets/access-discovery-agent.png)

## Cas d’utilisation courants et exemples d’invites {#use-cases-prompts}

Utilisez les invites d’optimisation de contenu en recherchant les ressources appropriées via l’[agent de découverte](/help/ai-in-aem/agents/discovery/overview.md). Une fois les images appropriées affichées, les utilisateurs peuvent générer des variantes optimisées ou spécifiques à un canal pour une ou plusieurs ressources directement à partir des résultats de la recherche. Ce workflow garantit des entrées de haute qualité et de meilleurs résultats d’optimisation de manière cohérente. [Consultez la liste complète des optimisations disponibles](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/).

* **Création de rendu haute résolution**

  L’agent peut générer de nouveaux rendus d’une ressource à une résolution et un niveau de qualité spécifiés, ce qui facilite la préparation de variations prêtes pour le canal sans modification manuelle.


  Exemple d’invite :

  Créez un rendu `2000px` en tant que `JPEG` avec la qualité de `80%`.

  Recherchez la ressource appropriée à l’aide de l’agent [Discovery](/help/ai-in-aem/agents/discovery/overview.md), puis utilisez les invites suivantes en cas de résultats de recherche multiples :

  Pour le 3e résultat de recherche, créez un rendu `2000px` en tant que `JPEG` avec une qualité `80%`.

  OU

  Par `Asset ID`, générez un rendu de 2 000 px `JPEG` avec une qualité `80%`

* **Amélioration des images**

  L’agent peut appliquer des améliorations visuelles, telles que l’accentuation, pour s’assurer que les ressources ont l’air nettes et bien définies avant d’être utilisées dans les campagnes.

  Exemple d’invite :

  Accentuez l’image.


* **Réglages des couleurs de fond**

  L’agent peut mettre à jour ou remplacer les couleurs de fond dans les ressources transparentes, en prenant en charge des modèles de couleurs spécifiques à la marque ou des thèmes visuels pilotés par les campagnes.

  Exemple d’invite :

  Remplacez la couleur d’arrière-plan du `PNG` par `#ff8932`.

* **Transformations d’orientation**

  L’agent peut inverser ou refléter les visuels pour s’aligner sur les besoins de mise en page ou le sens créatif, sans avoir besoin d’outils de modification externes.

  Exemple d’invite :

  Mettre l’image en miroir horizontalement.

* **Rendus optimisés pour les canaux**

  L’agent peut produire des rendus adaptés aux exigences spécifiques de la plateforme, telles que les histoires sur Instagram, ce qui garantit que les ressources respectent automatiquement les directives en matière de format, de ratio et de qualité.

  Exemple d&#39;invite :

  Créez un rendu pour une histoire `Instagram`.

* **Recouvrements de marque et génération composite**

  L’agent peut appliquer des graphiques promotionnels, des recouvrements ou des badges aux ressources existantes avec un emplacement précis, ce qui permet de créer rapidement des composites prêts pour la campagne.

  Exemple d&#39;invite :

  Recouvrez l’image avec `30%` graphiques de réduction sur la bannière promotionnelle, en la plaçant `100px` au centre.

  >[!NOTE]
  >
  >Les positions de recouvrement peuvent ne pas être exactes.


## Résultats de l’optimisation {#content-optimization-agent-results}

Lorsque vous spécifiez une invite d’optimisation, l’agent d’optimisation de contenu renvoie la ressource améliorée avec des options d’accès pratiques en fonction du type de ressource :

* **Images** : la réponse comprend un aperçu miniature et des options pour ouvrir l’URL Dynamic Media ou télécharger l’image optimisée.

* **Documents PDF** : la réponse comprend un aperçu miniature et des options pour ouvrir l’URL Dynamic Media ou télécharger le fichier optimisé.

* **Vidéos** : la réponse fournit des options pour ouvrir l’URL Dynamic Media ou télécharger la vidéo optimisée.

![Résultats de l’optimisation du contenu](/help/ai-in-aem/agents/content-optimization/assets/download-content-optimization.png)

Ces résultats facilitent la révision de la sortie optimisée et son utilisation immédiate sur les canaux ou workflows en aval.

<!--


## Prompting best Practices {#prompting-best-practices-content-optimization-agent}

The following are some of the prompting best practices:

* Be explicit about the enhancement you want the Content Optimization Agent to apply. Clearly state the transformation or adjustment you expect. Precise instructions help the agent produce accurate and predictable results. For example, Instead of `Make it good quality`, specify `Create a JPEG image with 90% quality`.

* Provide detailed parameters whenever possible. The more context you give, such as dimensions, format, quality, placement, or color values, the more tailored the output is.

-->
