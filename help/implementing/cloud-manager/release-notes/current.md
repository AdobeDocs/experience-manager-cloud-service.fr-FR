---
title: Notes de mise à jour de la version 2026.1.0 de Cloud Manager
description: En savoir plus sur la version 2026.1.0 de Cloud Manager dans Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 2ea076c42a6406548bf48cd246227fc8ddb3a080
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 46%

---

# Notes de mise à jour de Cloud Manager 2026.1.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

En savoir plus sur la version 2026.1.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2026.1.0 de Cloud Manager dans AEM as a Cloud Service est le vendredi 22 janvier 2026.

La prochaine version est prévue le vendredi 5 février 2026.

## Nouveautés - Cloud Manager {#cloud-manager-whats-new}

* **Les pipelines de configuration prennent désormais en charge les secrets gérés**

  Les utilisateurs peuvent désormais ajouter et gérer des secrets directement dans les pipelines de configuration de Cloud Manager. Ces secrets remplacent en toute sécurité les valeurs dans la spécification de configuration du pipeline et prennent en charge les déploiements flexibles spécifiques à un environnement.

  ![Option Afficher/Modifier les variables dans le menu déroulant d’un pipeline sélectionné](/help/implementing/cloud-manager/release-notes/assets/view-edit-variables-option.png)
  *Option Afficher/Modifier les variables dans le menu déroulant d’un pipeline sélectionné.*

  ![Boîte de dialogue Configuration des variables &#x200B;](/help/implementing/cloud-manager/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Boîte de dialogue Configuration des variables.*

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

### Extensibilité et personnalisation d’Experience Hub {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) sert de point d’entrée à AEM, personnalisé en fonction des besoins de votre entreprise. Informez Adobe de vos extensions de l’interface d’utilisation AEM existantes afin que l’on puisse vous aider à les activer dans Experience Hub sans difficulté.

![Diagramme du workflow d’extensibilité et de personnalisation d’Experience Hub](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Intégrez des expériences personnalisées dans Experience Hub pour étendre et personnaliser le tableau de bord de votre organisation. Outre les widgets intégrés d’Adobe, ajoutez les vôtres à l’aide du framework d’[extensibilité de l’interface d’utilisation](https://developer.adobe.com/uix/docs/). Créez des applications d’interface d’utilisation basées sur JavaScript et mettez-les à disposition de vos utilisateurs et utilisatrices pour répondre aux besoins et aux workflows spécifiques à l’entreprise.

La version bêta vous intéresse ? Envoyez un e-mail à l’adresse [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) avec votre ID d’organisation Adobe et une brève description de la personnalisation que vous avez l’intention de créer.

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

Il n’existe aucun correctif de bugs significatif dans la version de décembre 2025 de Cloud Manager.


<!-- ## Known issues {#known-issues} -->

