---
title: Notes de mise à jour de la version 2026.3.0 de Cloud Manager
description: En savoir plus sur la version 2026.3.0 de Cloud Manager dans Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: eb3e826e27e14b8b1da534440f11d43e973130ec
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 23%

---

# Notes de mise à jour de Cloud Manager 2026.3.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

En savoir plus sur la version 2026.3.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2026.3.0 de Cloud Manager dans AEM as a Cloud Service est le vendredi 5 mars 2026.

La prochaine version est prévue le vendredi 2 avril 2026.


## Nouveautés - Cloud Manager {#cloud-manager-whats-new}

* **Cloud Manager prend désormais en charge une option** Effacer **pour les importations** Copie de contenu **&#x200B;**

  Lorsque vous activez **Effacer**, Cloud Manager supprime le contenu existant à la destination avant de démarrer l’importation, ce qui vous permet de repartir de zéro et d’éviter les conflits avec le contenu préexistant. Si vous laissez l’option **Effacer** désactivée, Cloud Manager importe le nouveau contenu en plus du contenu de destination existant. Une invite de confirmation s’affiche avant le début de l’effacement. Cloud Manager consigne l’action d’effacement et importe les détails pour en assurer la traçabilité.

  Voir aussi [Copier le contenu](/help/implementing/developing/tools/content-copy.md#copy-content).

* **Prise en charge de l’extensibilité de l’interface utilisateur dans AEM Experience Hub**
La prise en charge des extensions d’interface utilisateur dans [AEM Experience Hub](https://experience.adobe.com/experiencemanager) est désormais activée, ce qui permet aux développeurs d’étendre l’interface avec des fonctionnalités et des widgets personnalisés créés à l’aide d’Adobe App Builder.

  Pour en savoir plus, voir [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

* **Stabilité, performances et fiabilité améliorées**

  Cette version comprend des mises à jour d’optimisation et de maintenance qui ont amélioré la stabilité, les performances et la fiabilité de Cloud Manager.


## Programmes bêta {#private-beta-program}

Participez au programme bêta de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur disponibilité générale.

>[!IMPORTANT]
>
>Les versions de Beta peuvent contenir des défauts et sont fournies « EN L’ÉTAT » sans garantie d’aucune sorte. Adobe n’a aucune obligation de tenir à jour, corriger, mettre à jour, modifier, remplacer ou prendre en charge (par le biais des services d’assistance Adobe ou d’une autre manière) les versions bêta. Adobe conseille aux clients d’être prudent et de ne pas se fier au bon fonctionnement ou aux performances des versions bêta, ni à la documentation ou aux documents d’accompagnement. Les fonctionnalités et API de la version bêta peuvent être modifiées sans préavis. Par conséquent, toute utilisation des versions bêta s’effectue entièrement aux risques et périls du client.

Voir aussi [Programmes AEM Beta](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)

Les opportunités suivantes sont actuellement disponibles :
<!--
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.-->

### Serveur Cloud Manager MCP pour les IDE optimisés par l’IA{#mcp-server-for-cm}

Vous pouvez désormais essayer un serveur MCP (Model Context Protocol) qui expose les API publiques de Cloud Manager en tant qu’outils pour les IDE compatibles avec l’IA (comme Cursor). Une fois connecté, vous pouvez utiliser des invites de conversation pour répertorier et gérer les programmes, les pipelines, les environnements et les référentiels, ce qui vous permet de vous déplacer plus rapidement sans quitter votre éditeur.

Consultez la documentation [Utilisation de MCP avec AEM as a Cloud Service](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md).

Voir le tutoriel [Cloud Manager MCP Server](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/mcp-server/cloud-manager#).

La version bêta vous intéresse ? Envoyez [GRP-AEM-CM-MCP-FEEDBACK@adobe.com](mailto:GRP-AEM-CM-MCP-FEEDBACK@adobe.com) par e-mail avec votre ID d’organisation et votre ID de programme Adobe.


<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI Extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### Versions plus rapides avec mise en cache du module {#quick-build-cm-pipelines}

Un nouveau modèle de version compile uniquement les modules modifiés (plutôt que le référentiel entier) à l’aide de la mise en cache au niveau du module pour réduire les temps de création. Elle s’applique aux pipelines de qualité de code, full stack et intermédiaires uniquement.

![Boîte de dialogue Modifier le pipeline hors production présentant les deux options de stratégie de création qui sont Création complète et Création intelligente](/help/implementing/cloud-manager/release-notes/assets/non-production-pipeline-edit.png)
*Boîte de dialogue Modifier le pipeline hors production présentant les deux options de stratégie de création qui sont Création complète et Création intelligente.*

Dans la boîte de dialogue **Ajouter/Modifier un pipeline**, sous l’onglet **Code Source**, une nouvelle section **Stratégie de build** vous permet de choisir l’une des options de build suivantes :

* **Version complète** — crée tous les modules du référentiel à chaque exécution.
* **Version intelligente** : crée uniquement les modules qui ont été modifiés depuis la dernière validation, ce qui réduit la durée globale de la création.

Vous contrôlez les pipelines qui utilisent **génération intelligente**. Dans la version bêta, cette option s’affiche uniquement pour les pipelines **Qualité du code** et **Déploiement de développement**.

Cela vous intéresse ? Envoyez un e-mail à l’adresse [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) avec votre ID d’organisation et votre ID de programme Adobe.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline Variables in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).-->

## Correctifs {#bug-fixes}

* Correction d’un problème en raison duquel l’API Restore Points pouvait renvoyer une erreur 500 lors de la récupération de points de restauration. Le point d’entrée gère désormais correctement les valeurs nulles, ce qui garantit des réponses cohérentes et fiables. (CMGR-72963)
* Cloud Manager accepte désormais les URL de référentiel GitHub avec ou sans suffixe `.git`, ce qui permet d’aligner le comportement de l’API avec l’interface utilisateur et de rendre l’intégration du référentiel plus flexible. (CMGR-73296)
* La validation des noms de profil de produit ne respecte plus la casse, ce qui empêche les erreurs lors de la création de profils dont les noms ne diffèrent que par les majuscules. (CMGR-74075)
* Vous pouvez désormais effectuer plusieurs opérations de restauration à partir de la même exécution de pipeline, ce qui permet des restaurations séquentielles pour des environnements tels que l’évaluation et la production sans avoir à exécuter un nouveau pipeline. (CMGR-73538)


<!-- ## Known issues {#known-issues} -->

