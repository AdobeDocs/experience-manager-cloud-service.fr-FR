---
title: Présentation de l’agent de développement
description: Découvrez comment l’agent de développement dans AEM analyse les pipelines ayant échoué dans Cloud Manager et crée des journaux pour suggérer des correctifs de code et accélérer le débogage.
feature: Agentic AI, AI Assistant, AI Tools, User Roles
role: User, Admin, Architect, Developer
exl-id: 2194556f-aac2-4cdd-8f7f-00c92c8c4424
source-git-commit: eeaa119711b480197b5807b85eb9c566a735f270
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 1%

---

# Présentation de l’agent de développement {#development-agent-overview}

L’agent de développement permet aux développeurs et aux administrateurs d’AEM de créer, déboguer, déployer et optimiser le code plus efficacement.

Actuellement, l’agent peut récupérer les statuts de pipeline et vous aider à résoudre les problèmes d’échec des étapes de création en suggérant des correctifs, ce qui vous permet de gagner du temps lors du débogage des déploiements d’AEM as a Cloud Service dans les environnements de développement, d’évaluation et de production. Il examine les journaux de génération et le code associé pour vous recommander un correctif que vous pouvez appliquer manuellement.

>[!VIDEO](https://video.tv.adobe.com/v/3478009?captions=fre_fr&quality=12&learn=on)

>[!IMPORTANT]
>
>Les réponses générées par l&#39;IA peuvent être inexactes ou trompeuses. Assurez-vous de vérifier les correctifs et les réponses suggérés.
>
>Consultez également les [Directives d’utilisation de l’IA générative de Adobe Experience Cloud](https://www.adobe.com/fr/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

<!-- 
## Cloud Manager Pipeline Troubleshooting  {#cloud-manager-pipeline-troubleshooting}
-->

Pour accéder à cet agent, reportez-vous aux [notes de mise à jour](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs) pour obtenir des instructions sur la façon de s’inscrire au programme bêta et veillez à indiquer votre intérêt pour l’agent de développement. Vous pouvez également envoyer par e-mail les commentaires spécifiques à l’agent de développement à [aem-devagent@adobe.com](mailto:aem-devagent@adobe.com).

[Suivez un tutoriel](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/cloud-service/ai/development-agent-troubleshoot-ci-cd-pipeline) pour savoir comment utiliser l’agent de développement afin de résoudre les problèmes liés aux pipelines.

## Accès à l’agent de développement via Cloud Manager {#how-to-access-the-agent}

Vous accédez à l’agent de développement par le biais de l’assistant d’IA présent dans les interfaces utilisateur, notamment Cloud Manager ou Experience Hub.

**Pour accéder à l’agent de développement via Cloud Manager :**

1. Pour commencer, cliquez sur [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home) pour ouvrir sa page d&#39;accueil.

   ![Page d&#39;accueil de Adobe Experience Cloud](/help/implementing/cloud-manager/assets/experience-cloud-experiencemanager.png)

1. Dans le rail de gauche, sous l’en-tête **Services**, cliquez sur **Cloud Manager**.

   ![La liste déroulante affichant le paramètre prédéfini de création de contenu est sélectionnée](/help/implementing/cloud-manager/assets/experience-hub-role-selection.png)

   >[!IMPORTANT]
   >
   >Les widgets, outils et artefacts affichés dépendent du personnage de l’utilisateur, des droits et du type de déploiement d’AEM (AEM as a Cloud Service ou Managed Services 6.5/6.5 LTS).

1. Dans le rail de gauche, sous **Programme**, cliquez sur **![Icône Aperçu](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) Aperçu**.

1. Sur la page **Aperçu du programme**, dans la vignette **Pipelines**, cliquez sur un pipeline.

   ![&#x200B; Pipeline sélectionné &#x200B;](/help/ai-in-aem/agents/development/assets/dev-agent-pipeline-select.png)

1. Sur la page **Génération et analyse du code**, notez l’échec du pipeline.

   ![Échec du pipeline affiché sur la page Génération et analyse du code](/help/ai-in-aem/agents/development/assets/dev-agent-pipeline-failure.png)

1. Dans le coin supérieur droit de l’interface utilisateur d’AEM (à partir des pages Cloud Manager ou de l’instance d’auteur des environnements AEM), cliquez sur l’icône **Assistant IA**.

   ![Icône Assistant IA de la barre d’outils](/help/implementing/cloud-manager/assets/ai-assistant-icon.png)

   Consultez également la section [Assistant AI dans AEM](/help/implementing/cloud-manager/ai-assistant-in-aem.md).

1. Dans la zone de texte du panneau **Assistant AI** située en bas, saisissez votre question ou votre invite, puis appuyez sur `Enter` ou cliquez sur ![Icône Envoyer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Send_18_N.svg).

   Par exemple :
   *Dans le programme « eda-org-01-no-access », analysez l’échec du pipeline « no-access » et résolvez les problèmes.*

   L’invite génère la réponse suivante.

   ![invite de l’assistant AI et réponse qui en résulte](/help/ai-in-aem/agents/development/assets/dev-agent-prompt-response.png)


## Autorisations {#permissions}

La tâche de dépannage du pipeline de l’agent de développement nécessite le rôle Cloud Manager - Développeur ou Cloud Manager - Gestionnaire de programme .

## Exemples d’invites {#sample-prompts}

| Prompt | Résultat |
| --- | --- |
| *Résolution des problèmes liés à mon pipeline en échec* | Effectue une analyse des raisons de l’échec d’un pipeline ; si le pipeline auquel il est fait référence n’est pas clair, des questions supplémentaires sont posées à l’utilisateur ou l’utilisatrice. |
| *Répertorier mes pipelines ayant échoué pour le programme Programme principal.* | Bien que les résultats puissent varier, cette invite génère un tableau des pipelines ayant échoué, avec une suggestion de suivi pour référencer un pipeline spécifique à analyser. |
| *Analysez mon pipeline en échec appelé « Pipeline de développement ».* | Cette invite génère une analyse du pipeline ayant échoué avec des suggestions pour corriger le problème. S’il y a plusieurs échecs, des questions supplémentaires seront posées à l’utilisateur. |
| *Résolution des problèmes liés aux 1234567* d’exécution du pipeline | En fournissant un identifiant d’exécution de pipeline exact, une analyse du pipeline est effectuée. |

## Fonctionnalités hors de portée {#out-of-scope-features}

Le dépannage du pipeline fonctionne à l’étape de création du pipeline full-stack. Pour les autres types de pipeline et étapes, déboguez les échecs en téléchargeant et en examinant les journaux.

Voir [Journaux d’accès et de téléchargement](/help/implementing/cloud-manager/manage-logs.md).
