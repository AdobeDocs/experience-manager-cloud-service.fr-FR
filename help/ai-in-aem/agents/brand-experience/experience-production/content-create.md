---
title: Création de tâche de contenu
description: Découvrez ce qu’est la tâche de création de contenu Brand Experience Agent et ce qu’elle peut vous apporter.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
source-git-commit: b92c13f690903074272e471c89bc0acc81627af1
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 1%

---


# Création de tâche de contenu {#content-create}

La tâche de création de contenu fait partie de l’[agent de production Experience](/help/ai-in-aem/agents/brand-experience/experience-production/overview.md) qui crée de nouvelles pages sur la marque à l’aide du langage naturel, d’un résumé marketing et d’un modèle AEM. La tâche accélère la production de pages pour Adobe Experience Manager (AEM) as a Cloud Service et Edge Delivery Services.

<!-- see Limitations too and update when appropriate -->

>[!NOTE]
>
>La tâche de création de contenu est actuellement en disponibilité limitée. Si vous souhaitez participer, veuillez envoyer une demande à partir de votre adresse e-mail officielle à [&#128279;](mailto:experience-production-agent@adobe.com).

## Vue d’ensemble {#overview}

La tâche de création de contenu génère de nouvelles pages sur la marque à l’aide du langage naturel, ainsi qu’un résumé marketing et un modèle AEM.

Vous pouvez accéder à la tâche de création de contenu à partir de :

* [L’assistant AI](#access-ai-assistant)

>[!VIDEO](https://video.tv.adobe.com/v/3488436?learn=on)

Pour utiliser la tâche Créer du contenu :

* Vous [fournissez](#provide-the-prompt-and-brief) :

   * Une invite en langage naturel qui décrit ce que vous devez créer et où la page doit se trouver.

   * Un brief :

      * La tâche de création de contenu utilise un résumé ou un document marketing qui décrit ce que l’agent doit générer. Le travail accepte un large éventail de formats pour le brief. Des notes efficaces spécifient souvent les objectifs, l’audience, les sujets, le nombre de mots cibles et les mots-clés.

* Vous pouvez ensuite [Envoyer](#submit) l’invite et le résumé
* Spécifiez ensuite un modèle [&#128279;](#select-a-template) : qui définit la disposition requise
* Le travail fournira un [plan que vous pourrez examiner](#review-the-plan)
* Vous pouvez ensuite [poursuivre la génération](#proceed-with-generation) et [affiner davantage la création si nécessaire](#further-refinement-in-authoring)

L’agent aligne la génération sur le modèle et peut ajouter ou supprimer des sections pour correspondre au brief ; par exemple, lorsque vous avez besoin d’un nombre de mots plus élevé ou plus faible.

>[!NOTE]
>
>Cette page utilise un exemple pour créer une page basée sur un brief joint à `https://frescopa.coffee/sustainability/coffee-bean-types`

## Accès - Assistant IA {#access-ai-assistant}

Vous pouvez accéder au traitement dans AEM à partir de l’assistant AI.

Ouvrez l’[assistant AI](/help/implementing/cloud-manager/ai-assistant-in-aem.md) dans la barre d’outils supérieure droite de [`experience.adobe.com`](https://experience.adobe.com).

## Fournissez l’invite et le résumé {#provide-the-prompt-and-brief}

Dans l’assistant d’IA, vous devez :

1. Utilisez le langage naturel pour décrire ce que vous souhaitez faire et identifier l’emplacement de la page, à l’aide d’un chemin d’accès ou d’une URL dans votre site web. Par exemple, en créant une page basée sur votre brief :

   * `create a new page based on the attached at https://frescopa.coffee/sustainability/coffee-bean-types`

     ![Tâche de création de contenu - Ajoutez une invite](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-create-page.png)

1. Chargez le brief correspondant à votre demande. Pour charger le brief :

   1. Sélectionnez **+** dans le coin inférieur gauche de l’assistant AI et choisissez **Joindre des fichiers** :

      ![Content Create Job - charge un brief](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-load-brief.png)

   1. Ajoutez votre fichier de résumé. Le brief chargé s’affiche en haut à droite de la boîte de dialogue de l’invite :

      ![Content Create Job - loaded brief](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-loaded-brief.png)

1. Lorsque vous êtes prêt, envoyez l’invite et le résumé à l’aide de l’icône d’envoi bleue (flèche bleue).

## Sélectionner un modèle {#select-a-template}

L’agent vous demandera alors de spécifier un modèle. Le modèle fournit à l’agent la structure et la disposition de la page. La génération est conforme à cette disposition. L’agent peut ajouter et supprimer des sections selon les besoins, en fonction du résumé ; par exemple, pour répondre à un nombre de mots différent.

![Tâche de création de contenu - Spécifiez le modèle](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-select-template.png)

## Examiner le plan {#review-the-plan}

Ensuite, l&#39;agent présente un plan pour les changements qu&#39;il apportera, en fonction de vos commentaires et de son analyse du mémoire. Vous pouvez ajuster le plan ou poursuivre le plan et commencer la génération.

>[!NOTE]
>
> Si vous utilisez l’[agent de gouvernance](/help/ai-in-aem/agents/governance/overview.md), la génération peut suivre les directives de votre marque.

![Content Create Job - Consultez le plan](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-review-plan.png)

## Continuer la génération {#proceed-with-generation}

Une fois la génération terminée, l’agent fournit deux liens :

* un lien **aperçu** ;
* un lien **modifier** ;
   * Utilisez le lien d’édition pour [ouvrir la page dans une surface de création AEM](#further-refinement-in-authoring) afin de l’affiner davantage.

![Tâche de création de contenu - poursuivre la génération](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-proceed-generation.png)

## Amélioration de la création {#further-refinement-in-authoring}

Une fois que vous avez choisi de modifier la page dans AEM, elle s’ouvre dans votre environnement de création ; par exemple, l’[éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md) ou l’[éditeur de page](/help/sites-cloud/authoring/page-editor/introduction.md).

Dans l’[éditeur universel](#universal-editor-edit-text-with-the-assistant), l’assistant d’IA est *contextuel* : vous pouvez sélectionner des éléments sur la zone de travail et les utiliser avec l’assistant.

### Éditeur universel : permet de modifier du texte avec l’assistant. {#universal-editor-edit-text-with-the-assistant}

Pour affiner la copie à partir de l’assistant lors de la création :

1. Sélectionnez l’élément dans l’[éditeur universel](/help/sites-cloud/authoring/universal-editor/authoring.md).
1. Ouvrez l’assistant d’IA dans le coin supérieur droit, saisissez votre invite, puis effectuez l’envoi.

Exemples d’invites :

* `Update to Explore the World of Coffee`
* `Update to be more engaging for the 30-40 year old age demographic and avid coffee drinker`

Sélectionnez **Appliquer les modifications** (ou l’équivalent) pour que les mises à jour apparaissent sur la page.

## Activation {#activation}

Vous pouvez explorer les agents AEM via l’[aire de jeu](https://www.aem.live/developer/aem-playground) ou vous connecter à votre CSM ou à votre TAM pour discuter de l’accès via le SKU de l’agent.

## Restrictions {#limitations}

Gardez à l’esprit les limites suivantes :

* Cette fonctionnalité est en disponibilité limitée et nécessite une intégration manuelle pour la participation. Si vous souhaitez participer, veuillez envoyer une demande à partir de votre adresse e-mail officielle à [&#128279;](mailto:experience-production-agent@adobe.com).

## Ressources supplémentaires {#additional-resources}

Les ressources suivantes peuvent s’avérer utiles lorsque vous continuez à explorer l’agent de production d’expérience :

* Vous pouvez également utiliser le [classeur de l’agent de production Experience](https://www.adobe.com/go/aem-epa-workbook_fr) pour obtenir des instructions pratiques et guidées.
