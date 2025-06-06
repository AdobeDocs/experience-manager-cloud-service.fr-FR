---
title: Notes de mise à jour de la version 2025.6.0 de Cloud Manager
description: En savoir plus sur la version 2025.6.0 de Cloud Manager dans Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 52c8745d3a3cc4bc41003a258a85a817e7ccb48b
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 32%

---

# Notes de mise à jour de Cloud Manager 2025.6.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

En savoir plus sur la version 2025.6.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.6.0 de Cloud Manager dans AEM as a Cloud Service est le vendredi 5 juin 2025.

La prochaine version est prévue le vendredi 10 juillet 2025.

## Nouveautés {#what-is-new}

* **Le tableau de bord des licences comprend désormais la licence Edge Delivery Services**

  L’utilisation de la licence Edge Delivery Services s’affiche désormais dans le tableau de bord des licences, ce qui vous permet de mieux connaître vos droits et votre statut. <!-- CMGR-67686 -->

  ![Tableau de bord des licences](/help/implementing/cloud-manager/assets/license-dashboard.png)

  Voir [Tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md).

* **Configuration du site Edge Delivery mise à jour**

  Simplification du flux d’ajout d’un site Edge Delivery en demandant l’**origine Edge Delivery** au lieu de l’**URL du référentiel**, ce qui rend l’intégration et la configuration plus rapides et plus intuitives <!-- CMGR-67686 -->

  ![ Boîte de dialogue Ajouter un site Edge Delivery ](/help/implementing/cloud-manager/release-notes/assets/add-edge-delivery-site.png)

  Voir [Ajouter un site Edge Delivery](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md).

* **Favoris de pipeline**

  Dans cette version, Cloud Manager offre la possibilité d’épingler les pipelines favoris, ce qui vous permet de marquer des pipelines spécifiques comme favoris afin qu’ils apparaissent en haut de la liste sur la page **Pipelines**. Cette amélioration facilite la recherche et l’exécution des pipelines fréquemment consultés. <!-- CMGR-68293 -->

  ![Pipelines marqués comme favoris](/help/implementing/cloud-manager/release-notes/assets/pipeline-favorites.png) *deux pipelines marqués comme favoris.*

  Voir [Marquer les favoris du pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipeline-favorites).


## Programme d’adoption précoce {#early-adoption}

Participez au programme d’adoption précoce de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale.

Les possibilités d’adoption précoce suivantes sont actuellement disponibles :


### Environnement de test spécialisé {#specialized-test-environment}

Cloud Manager prend désormais en charge l’ajout d’un nouveau type d’environnement appelé **Environnement de test spécialisé**. L’environnement est conçu pour aider les équipes à valider les fonctionnalités dans des conditions proches de la production avant la mise en ligne. Ce type d’environnement est distinct des environnements *Production + Évaluation*, *Développement* ou *Développement rapide* et offre un espace ciblé pour exécuter des scénarios de validation avancés.

Voir [Ajout d’un environnement de test spécialisé](/help/implementing/cloud-manager/specialized-test-environment.md).

![Boîte de dialogue Ajouter un environnement avec le bouton radio Environnement de test spécialisé sélectionné](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.


### Apportez votre propre Git (BYOG) - maintenant avec la prise en charge d’Azure DevOps {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Les clientes et clients peuvent désormais intégrer leurs référentiels Git Azure DevOps dans Cloud Manager, avec la prise en charge des référentiels Azure DevOps modernes et VSTS (Visual Studio Team Services) hérités.

* Pour les utilisateurs et utilisatrices d’Edge Delivery Services, le référentiel intégré peut être utilisé pour synchroniser et déployer le code du site.
* Pour les utilisateurs et utilisatrices d’AEM as a Cloud Service et d’Adobe Managed Services (AMS), le référentiel peut être lié aux pipelines full stack et front-end.

La prise en charge de types de pipeline supplémentaires et de la validation des demandes d’extraction par le biais de pipelines de qualité du code sera bientôt disponible.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.


**Questions fréquentes sur BYOG**

| Question | Répondre |
|---|---|
| *Comment un projet peut-il revenir au référentiel Git géré par Adobe si nécessaire ?* | Revenir en arrière est simple. [Mettez à jour les pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) pour pointer vers le référentiel Adobe et supprimer le référentiel externe s’il n’est plus nécessaire. |
| *Est-il possible de configurer différents référentiels pour différents environnements (par exemple, hors production ou production) afin d’autoriser d’abord les tests en dehors de la production ?* | Oui, différents référentiels peuvent être configurés pour des environnements distincts. Par exemple, le pipeline de développement ou de qualité du code peut pointer vers un référentiel externe tandis que le pipeline de production reste connecté au référentiel Adobe. Assurez-vous que la tâche de synchronisation entre les deux référentiels reste active pendant cette configuration. |
| *Les paramètres existants tels que les listes autorisées IP continuent-ils à fonctionner ?* | Oui, les listes autorisées IP existantes continuent de fonctionner comme d’habitude. Cependant, si le référentiel Git externe est protégé par un pare-feu, les [adresses IP Adobe nécessaires doivent être ajoutées à la liste autorisée ](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *Toutes les URL du référentiel GitLab fonctionnent-elles ? L’URL du référentiel utilisée suit le format `https://gitlab_dedicated_url.com/path/repo-name.git`, qui diffère de l’exemple de la documentation.* | Oui, tout référentiel GitLab prenant en charge l’API V3 ou V4 est pris en charge, y compris les URL GitLab auto-hébergées telles que celle décrite dans [Ajout de référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md) (`https://git-vendor-name.com/org-name/repo-name.git`). |


#### Gérer les jetons d’accès{#manage-access-tokens}

Utilisez **Gérer les jetons d’accès** dans Cloud Manager pour afficher, renommer et supprimer les jetons d’accès associés aux référentiels BYOG externes, tels que GitHub Enterprise, GitLab, Bitbucket et Azure DevOps.

Voir [ Gestion des jetons d’accès ](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

Si vous souhaitez tester cette nouvelle fonctionnalité et partager vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.


### Ajouter le pipeline de configuration Edge Delivery {#add-eds-pipeline}

Les pipelines de configuration sont désormais pris en charge pour les sites créés avec Edge Delivery Services, étendant cette fonctionnalité au-delà des seuls environnements Cloud Service. Vous pouvez utiliser **Pipelines de configuration** pour gérer des paramètres tels que les règles de filtrage du trafic et les configurations du pare-feu d’application web (WAF), le cas échéant. Consultez [Configurations prises en charge](/help/operations/config-pipeline.md#configurations).

![Ajout d’un pipeline Edge Delivery dans la liste déroulante Ajouter un pipeline](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png) *Ajout d’un pipeline Edge Delivery à partir de la page **Aperçu du programme**,**Carte Pipelines**.*

![Boîte de dialogue Ajouter un pipeline Edge Delivery](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Boîte de dialogue Ajouter un pipeline Edge Delivery.*

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.


## Correctifs

* Les environnements Sandbox précédemment marqués comme `HIBERNATED` ne restent plus bloqués dans cet état, ce qui permet à l’exécution ou au déploiement du pipeline de se poursuivre comme prévu. <!-- CMGR-67705 -->
* AEM Cloud Manager mappe désormais correctement les échecs de build Maven provoqués par des erreurs 409 (conflits) lors de la récupération des artefacts client vers un échec provoqué par le client. Cette modification améliore le message d’erreur en faisant la distinction entre les erreurs internes et les problèmes liés à la configuration de l’environnement client. <!-- CMGR-66673 -->


<!-- ## Known issues {#known-issues} -->

