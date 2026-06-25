---
title: Présentation de l’agent de développement
description: Découvrez comment l’agent de développement dans AEM analyse les pipelines en échec dans Cloud Manager et crée des journaux pour suggérer des correctifs de code et accélérer le débogage. Apprenez également comment récupérer les informations de Cloud Manager et l’aide en cas d’échec de réplication, et comment définir des heures de silence et mettre à jour les périodes d’accès gratuit pour les mises à jour d’AEM.
feature: Agentic AI, AI Assistant, AI Tools, User Roles
role: User, Admin, Developer
exl-id: 2194556f-aac2-4cdd-8f7f-00c92c8c4424
source-git-commit: fb0eaf8173b0cb5c81062424dbdfa723319df539
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 8%

---


# Présentation de l’agent de développement {#development-agent-overview}

[Dans le cadre du Brand Experience Agent,](/help/ai-in-aem/agents/brand-experience/overview.md) l’agent de développement aide les développeurs et les administrateurs de la pile Java AEM traditionnelle à créer, déboguer, déployer et optimiser le code plus efficacement.

Il prend en charge les tâches suivantes, accessibles par le biais de l’interface conversationnelle de l’assistant d’IA.

* Tâche Cloud Manager : opérations en lecture seule, y compris la liste des programmes et des environnements, ainsi que l’état du pipeline
* Tâche de dépannage du pipeline : débogage des pipelines ayant échoué
* Tâche de gestion des heures creuses et des périodes creuses (disponibilité limitée) : affichage, création et modification des heures creuses et mise à jour des périodes creuses
* Tâche de dépannage de la réplication (Beta) : débogage des problèmes liés à la réplication, tels que les files d’attente bloquées.

>[!NOTE]
>
> Les développeurs trouveront également utiles ces fonctionnalités optimisées par l’IA :
> * [Compétences de l’agent IDE](/help/ai-in-aem/local-development-with-ai-tools.md#agent-skills) pour les scénarios de développement local, tels que la génération de composants AEM.
> * [Serveurs MCP locaux](/help/ai-in-aem/local-development-with-ai-tools.md#aem-quickstart-mcp-server) pour le développement local, en particulier pour le débogage des problèmes d’AEM et de Dispatcher.
> * [Serveurs MCP distants](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md) pour accéder aux API et aux agents AEM.

>[!IMPORTANT]
>
>Les réponses générées par l&#39;IA peuvent être inexactes ou trompeuses. Assurez-vous de vérifier les correctifs et les réponses suggérés.
>
>Consultez également la section [Directives d’utilisation d’Adobe Experience Cloud Generative AI](https://www.adobe.com/fr/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

Vous pouvez envoyer par e-mail les commentaires spécifiques à l’agent de développement à [&#128279;](mailto:aem-devagent@adobe.com).

## Tâche Cloud Manager {#cloud-manager-job}

Obtenez des informations sur vos programmes et environnements AEM, notamment :
* liste des programmes et environnements
* liste des variables d’environnement
* recherche des noms des pipelines et du statut d’exécution actuel et des détails des étapes
* récupération des liens vers les journaux téléchargeables

### Exemples d’invites {#sample-cm-job-prompts}


| Prompt | Résultat |
| --- | --- |
| *Liste de tous mes programmes AEM Cloud Service* | Liste les programmes auxquels vous avez accès. |
| *Obtenir des détails sur les 12345* du programme | Récupérez les détails du programme. |
| *Liste des environnements dans les 12345* de programme | Répertorie les environnements du programme. |
| *Obtention des journaux pour l’environnement de production* | Récupère des liens vers divers fichiers journaux d’AEM, du Dispatcher et du réseau CDN afin qu’ils puissent être téléchargés à des fins de débogage ou autres. |
| *liste des pipelines pour les 12345* de programme | Répertorier les pipelines dans le programme. |
| *Quel est le statut de l’exécution actuelle du pipeline ?* | Répond avec le statut du pipeline. |
| *Obtenez-moi les liens du journal de génération pour les 12345* d’exécution du pipeline | Récupère les liens vers les journaux de génération de pipeline pour une exécution de pipeline spécifique. |


## Tâche de gestion des heures creuses et des périodes libres de mise à jour {#control-updates-job}

>[!AVAILABILITY]
>
>Cette fonctionnalité est en phase de disponibilité limitée et sera déployée au cours des prochaines semaines. E-Mail [aem-devagent@adobe.com.](mailto:aem-devagent@adobe.com) pour un accès immédiat.

Affichez, créez et modifiez les heures creuses et mettez à jour les périodes libres directement via l’assistant AEM AI.

L’avantage clé est la réduction des erreurs de planification. Lorsque vous effectuez une demande, l’assistant vous guide tout au long des étapes possibles et signale les limites qui s’appliquent, telles que la limite de trois périodes, l’intervalle obligatoire d’une semaine entre les périodes et les fenêtres d’exclusion de la maintenance planifiée que vous ne pouvez pas planifier.

Ainsi, au lieu de découvrir une contrainte après une configuration ayant échoué, les propriétaires d’entreprise et les responsables de déploiement sont dirigés vers un planning valide dans la même conversation. Cela permet de protéger les fenêtres d’activité critiques contre les mises à jour de maintenance automatique tout en réduisant les allers-retours et les erreurs de configuration.

### Exemples d’invites {#sample-updates-prompts}

| Prompt | Résultat |
| --- | --- |
| *Quel est le planning actuel de mise à jour des 12345 du programme ?* | Permet d’obtenir la liste des règles de mise à jour AEM actuelles. |
| *Bloquez les mises à jour d’AEM de 9 h à 17 h EST pour les 12345* du programme. | Configurez une règle pour que les mises à jour d’AEM ne soient pas appliquées pendant les heures de travail standard. |
| *Supprimer le bloc de mise à jour quotidienne pour les 12345* du programme | Supprime les règles qui empêchent les mises à jour AEM. |
| *Mise à jour d’AEM en pause dans deux semaines pour les 12345* du programme | Crée une règle pour empêcher les mises à jour d&#39;AEM. |
| *Mon programme est constamment mis à jour à des moments inopportuns. Quelles sont mes options ?* | Répond avec des informations sur la façon de définir des règles pour contrôler le planning de mise à jour d’AEM. |



## Tâche de dépannage du pipeline {#cloud-manager-pipeline-troubleshooting}

Cette tâche peut récupérer les statuts du pipeline et vous aider à résoudre les problèmes liés aux étapes de création échouées en suggérant des correctifs, ce qui vous permet de gagner du temps lors du débogage des déploiements d’AEM as a Cloud Service dans les environnements de développement, d’évaluation et de production. Il examine les journaux de génération et le code associé pour vous recommander un correctif que vous pouvez appliquer manuellement.

>[!VIDEO](https://video.tv.adobe.com/v/3478006?quality=12&learn=on)

>[!NOTE]
>
>Le dépannage des pipelines se limite aux pipelines de pile complète (déploiement et qualité du code) et Pipeline de configuration de niveau web.

<!--
To access this agent, please refer to the [release notes](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs) for instructions on how to enroll in the beta program, being sure to indicate your interest in the  Development Agent. You can also email development agent–specific feedback to [aem-devagent@adobe.com.](mailto:aem-devagent@adobe.com)

-->

[Suivez un tutoriel](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/agents/development-agent-troubleshoot-ci-cd-pipeline) pour savoir comment utiliser l’agent de développement afin de résoudre les problèmes liés aux pipelines.

### Accès à l’agent de développement via Cloud Manager {#how-to-access-the-agent}

Vous accédez à l’agent de développement par le biais de l’assistant d’IA présent dans les interfaces utilisateur, notamment Cloud Manager ou Experience Hub.

1. Pour commencer, cliquez sur [Adobe Experience Cloud](https://experience.adobe.com) pour ouvrir sa page d’accueil.

   ![Page d’accueil d’Adobe Experience Cloud](/help/implementing/cloud-manager/assets/experience-cloud-experiencemanager.png)

1. Dans le rail de gauche, sous l’en-tête **Services**, cliquez sur **Cloud Manager**.

   ![Rail de gauche d’Experience Hub affichant Cloud Manager répertorié sous l’en-tête Services](/help/implementing/cloud-manager/assets/experience-hub-role-selection.png)

   >[!IMPORTANT]
   >
   >Les widgets, outils et artefacts affichés dépendent du persona de l’utilisateur ou de l’utilisatrice, des droits et du type de déploiement d’AEM (AEM as a Cloud Service ou Managed Services 6.5/6.5 LTS).

1. Dans le rail de gauche, sous **Programme**, cliquez sur **![Icône Aperçu](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) Aperçu**.

1. Sur la page **Aperçu du programme**, dans la vignette **Pipelines**, cliquez sur un pipeline.

   ![&#x200B; Pipeline sélectionné &#x200B;](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-pipeline-select.png)

1. Sur la page **Génération et analyse du code**, notez l’échec du pipeline.

   ![Échec du pipeline affiché sur la page Génération et analyse du code](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-pipeline-failure.png)

1. Dans le coin supérieur droit de l’interface d’utilisation d’AEM (à partir des pages Cloud Manager ou de l’instance de création des environnements AEM), cliquez sur l’icône **Assistant IA**.

   ![Icône Assistant IA de la barre d’outils](/help/implementing/cloud-manager/assets/ai-assistant-icon.png)

   Consultez également la section [Assistant AI dans AEM](/help/implementing/cloud-manager/ai-assistant-in-aem.md).

1. Dans la zone de texte du panneau **Assistant IA** située en bas, saisissez votre question ou votre prompt, puis appuyez sur `Enter` ou cliquez sur ![icône Envoyer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Send_18_N.svg).

   Par exemple :
   *Dans le programme « eda-org-01-no-access », analysez l’échec du pipeline « no-access » et résolvez les problèmes.*

   L’invite génère la réponse suivante.

   ![invite de l’assistant AI et réponse qui en résulte](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-prompt-response.png)

#### Dépannage direct à partir de l’échec de l’exécution du pipeline {#troubleshoot-with-ai-button}

Lorsque l’exécution d’un pipeline échoue, Cloud Manager affiche également un bouton **Dépanner par l’IA** directement sur la page d’exécution du pipeline. Il s’agit du moyen le plus rapide de démarrer une session de dépannage, car l’exécution ayant échoué est automatiquement transmise en tant que contexte à l’assistant d’IA, aucune entrée d’invite manuelle n’étant nécessaire.

1. Dans Cloud Manager, ouvrez l’échec de l’exécution du pipeline. La bannière d’état s’affiche **Échec** et le bouton **Résolution des problèmes avec l’IA** s’affiche dans le coin supérieur droit de la page.

   ![Page d’exécution du pipeline ayant échoué affichant le bouton Dépannage avec l’IA et le panneau de l’assistant d’IA avec une analyse préchargée](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-troubleshoot-button.png)

1. Cliquez sur **Résolution des problèmes liés à l’IA**.

   Le panneau Assistant d’IA s’ouvre dans la partie droite de l’écran. L’assistant référence automatiquement l’échec de l’exécution du pipeline et commence son analyse, en identifiant l’étape qui a échoué et en suggérant un correctif que vous pouvez appliquer manuellement.

1. Passez en revue la réponse et, si nécessaire, poursuivez la conversation dans la zone de texte **Assistant IA** pour poser des questions de suivi ou demander plus de détails.

#### Dépannage à partir du widget Pipelines ayant échoué dans l’Experience Home {#troubleshoot-from-experience-home-widget}

Experience Home comprend un widget **Pipelines en échec** qui vous donne une vue d’ensemble des échecs de pipeline entre vos programmes sans que vous ayez à accéder à Cloud Manager au préalable. Chaque ligne du widget représente un pipeline en échec et affiche le nom du pipeline, la date et l’heure de la dernière exécution, la durée et l’étape qui a échoué. Un bouton **Résolution des problèmes avec l’IA** est disponible en ligne pour chaque entrée.

>[!NOTE]
>
>Le widget **Pipelines en échec** est visible uniquement lorsque le rôle **Admin &amp; IT** est sélectionné dans Experience Home. Si le widget n’apparaît pas, vérifiez que votre rôle est défini sur **Admin &amp; IT** à l’aide du sélecteur de rôle dans le coin supérieur droit de la page.

![&#x200B; Le widget Pipelines en échec sur la page d’accueil d’Experience Platform, affichant une entrée de pipeline en échec avec un bouton Dépannage avec l’IA &#x200B;](/help/ai-in-aem/agents/brand-experience/development/assets/dev-agent-failed-pipelines-widget.png)

1. Ouvrez [Accueil Experience](https://experience.adobe.com), cliquez sur **Experience Manager** et faites défiler l’écran jusqu’au widget **Pipelines en échec**.

1. Recherchez le pipeline que vous souhaitez étudier, puis cliquez sur **Dépannage avec l’IA** dans cette ligne.

   Le panneau de l’assistant d’IA s’ouvre avec l’échec d’exécution du pipeline préchargé en tant que contexte. L’assistant commence son analyse automatiquement, en identifiant la cause première et en suggérant un correctif.

1. Passez en revue la réponse et, si nécessaire, poursuivez la conversation dans la zone de texte **Assistant IA** pour poser des questions de suivi ou demander plus de détails.

### Autorisations {#permissions}

La tâche de dépannage du pipeline nécessite le rôle Cloud Manager - Développeur ou Cloud Manager - Gestionnaire de programme.

### Exemples d’invites {#sample-pipeline-prompts}

| Prompt | Résultat |
| --- | --- |
| *Résolution des problèmes liés à mon pipeline en échec* | Effectue une analyse des raisons de l’échec d’un pipeline ; si le pipeline auquel il est fait référence n’est pas clair, des questions supplémentaires sont posées à l’utilisateur ou l’utilisatrice. |
| *Répertorier mes pipelines ayant échoué pour le programme Programme principal.* | Bien que les résultats puissent varier, cette invite génère un tableau des pipelines ayant échoué, avec une suggestion de suivi pour référencer un pipeline spécifique à analyser. |
| *Analysez mon pipeline en échec appelé « Pipeline de développement ».* | Cette invite génère une analyse du pipeline ayant échoué avec des suggestions pour corriger le problème. S’il y a plusieurs échecs, des questions supplémentaires seront posées à l’utilisateur. |
| *Résolution des problèmes liés aux 1234567* d’exécution du pipeline | En fournissant un identifiant d’exécution de pipeline exact, une analyse du pipeline est effectuée. |

### Fonctionnalités hors de portée {#out-of-scope-features}

Le dépannage du pipeline fonctionne sur les étapes de test unitaire et de création et d’analyse de code dans les pipelines Déploiement de pile complète et Qualité du code . Il prend également en charge les [pipelines de configuration de niveau web](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines).

Pour les autres types de pipeline et étapes, déboguez les échecs en téléchargeant et en examinant les journaux. Voir [Journaux d’accès et de téléchargement](/help/implementing/cloud-manager/manage-logs.md) pour plus d’informations.

## Tâche de dépannage de la réplication (Beta) {#replication-troubleshooting-job}

Déboguer les problèmes liés à la réplication, tels que les files d’attente bloquées.

Veuillez envoyer un e-mail à [&#128279;](mailto:aem-devagent@adobe.com) pour accéder au programme bêta.
