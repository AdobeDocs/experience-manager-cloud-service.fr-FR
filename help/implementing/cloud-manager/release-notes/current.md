---
title: Notes de mise à jour de la version 2025.8.0 de Cloud Manager
description: En savoir plus sur la version 2025.8.0 de Cloud Manager dans Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 94a20e8e95edf603227bfadd07e4b4c62e6421e6
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 93%

---

# Notes de mise à jour de Cloud Manager 2025.8.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

En savoir plus sur la version 2025.8.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.8.0 de Cloud Manager dans AEM as a Cloud Service est le 7 août 2025.

La prochaine version est prévue le 4 septembre 2025.

## Nouveautés {#what-is-new}

* **Adobe Experience Hub bientôt disponible**

  À partir du 19 août 2025, Adobe commence le déploiement échelonné de la nouvelle Experience Hub auprès de tous les utilisateurs de Adobe Experience Manager.

  Experience Hub est un point de départ unifié qui offre des expériences contextuelles personnalisées pour aider les utilisateurs à atteindre plus rapidement leurs objectifs. Le déploiement se termine le 26 août 2025, date à laquelle il sera disponible pour tous les utilisateurs. Le nouvel Experience Hub est accessible directement sur [experience.adobe.com](https://experience.adobe.com/). Pour en savoir plus, voir [Experience Hub](/help/experience-hub.md).

* **La licence Edge Delivery Services peut être incluse dans un programme HIPAA en libre-service.**

  Les entreprises qui doivent utiliser des données sensibles ou relatives aux soins de santé peuvent désormais utiliser Edge Delivery Services en libre-service, ce qui leur permet d’être conformes à la loi HIPAA afin de respecter les normes réglementaires strictes. <!-- CMGR-70016 -->

* **BYOG est désormais disponible pour Edge Delivery Services**

  Cloud Manager vous permet désormais de configurer des référentiels Git externes et ainsi d’utiliser des workflows de gestion de code flexibles. <!--(CMGR‑69010, CMGR‑70988) --> Il vous permet également d’extraire du code d’une branche sélectionnée directement dans l’interface d’utilisation de Cloud Manager, ce qui réduit les tâches manuelles dans les référentiels. Voir [Configurer un site Edge Delivery pour utiliser un référentiel Git externe](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md) <!-- (CMGR‑68085)(CMGR-69015) --> <!-- KT: https://wiki.corp.adobe.com/display/DMSArchitecture/%5B2025%5D+Cloud+Manager+-+Bring+Your+Own+Git+with+EDS -->

* **Approvisionnement automatisé pour le nouveau module complémentaire Forms**

  Les clientes et les clients qui utilisent uniquement Sites ont souvent besoin d’un moyen léger et économique de créer des formulaires marketing. Le nouveau module complémentaire AEM Forms pour Sites répond à ce besoin en ajoutant des fonctionnalités Forms limitées à un programme Sites. Il crée également un parcours de mise à niveau clair vers l’offre AEM Forms complète. <!-- (CMGR-64301) --> <!-- KT: CMGR Provisioning Support for AEM Forms Sites Add-On SKU https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3578379797 -->

  Le module complémentaire :
   * Se connecte à un programme Sites et se déploie en parallèle, sans programme ni droits Forms séparés.
   * Cible les cas d’utilisation simples de formulaires marketing.
   * S’affiche dans la liste **Solutions et modules complémentaires** lors de la création d’un programme de production ou de la modification d’un programme de production, uniquement lorsque l’organisation IMS possède des licences disponibles de modules complémentaires Forms.

     ![Modules complémentaires Forms ](/help/implementing/cloud-manager/release-notes/assets/forms-add-on.png) *Le module complémentaire Forms peut être ajouté dans le programme uniquement si des licences de modules complémentaires Forms sont disponibles dans votre organisation IMS.*

     ![Module complémentaire Forms dans Solutions et modules complémentaires lors de la création d’un programme de production](/help/implementing/cloud-manager/release-notes/assets/forms-add-on-creating-production-program.png) *Lors de la création d’un programme, vous pouvez sélectionner le module complémentaire Forms dans la solution Sites.*

     ![Module complémentaire Forms lors de la modification d’un programme de production](/help/implementing/cloud-manager/release-notes/assets/forms-add-on-editing-production-program.png) *Dans **Modifier le programme**, sélectionnez le module complémentaire Forms du programme Sites, puis exécutez le pipeline pour l’activer dans les environnements.*

     Pour plus d’informations, consultez [Créer un programme de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).

## Programmes bêta {#private-beta-program}

Participez au programme bêta de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur disponibilité générale.

Les opportunités suivantes sont actuellement disponibles :

### Restauration en un clic pour les déploiements de pipeline {#one-click-rollback}

Revenez rapidement à un déploiement précédent si le dernier code source client ne fonctionne pas comme prévu ; il n’est pas nécessaire de réexécuter le pipeline complet ou de rétablir manuellement les validations.<!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

![Restaurez le code source client à partir de la carte Environnements](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed.png) *Carte Environnements ci-dessus présentant l’option **Restaurer** >**Code précédent déployé**&#x200B;pour un environnement sélectionné.*

![Boîte de dialogue Restaurer le code déployé précédent](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed-dialogbox.png)
*Dans la boîte de dialogue **Restaurer le code déployé précédent**, passez en revue la version actuellement déployée et la version à restaurer, puis cliquez sur **Confirmer***.

![Activation de la restauration](/help/implementing/cloud-manager/release-notes/assets/restoring-previous-code-deployed-restoring.png)
*Cloud Manager restaure l’environnement à sa version précédente, conserve le contenu et la configuration intacts et marque l’environnement comme **restauré**&#x200B;jusqu’à la fin du déploiement.*

![Version du code Source utilisée](/help/implementing/cloud-manager/release-notes/assets/environments-view-details-sourcecodeversion.png) *La vue Détails de l’environnement, comme illustré ci-dessus, affiche désormais également la version active utilisée du code source.*

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [restorecode@adobe.com](mailto:restorecode@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.

Voir la section [Restaurer le code précédemment déployé dans AEM as a Cloud Service](/help/operations/restore-previous-code-deployed.md).

Consultez également [Restauration de contenu dans AEM as a Cloud Service](/help/operations/restore.md).

### Environnement de test spécialisé {#specialized-test-environment}

Cloud Manager prend désormais en charge l’ajout d’un nouveau type d’environnement appelé **Environnement de test spécialisé**. L’environnement est conçu pour aider les équipes à valider les fonctionnalités dans des conditions proches de la production avant la mise en ligne. Ce type d’environnement est distinct des environnements *Production+Évaluation*, *Développement* ou *Développement rapide* et offre un espace ciblé pour exécuter des scénarios de validation avancés.

**Améliorations récentes**

* Vous pouvez désormais configurer des environnements de test spécialisés pour un pipeline hors environnement de production via un workflow plus simple et plus intuitif. La configuration rationalisée accélère l’achèvement et réduit les erreurs de configuration.
* **Copier le contenu** est désormais pris en charge dans les environnements de test spécialisés. Vous pouvez désormais exécuter **Copier le contenu** en toute sécurité dans des environnements de test isolés qui reflètent l’environnement de production. <!-- (CMGR‑68900) -->

Voir la section [Ajouter un environnement de test spécialisé](/help/implementing/cloud-manager/specialized-test-environment.md).

![Boîte de dialogue Ajouter un environnement avec le bouton radio Environnement de test spécialisé sélectionné](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

>[!NOTE]
>
>Adobe a fermé les demandes d’accès à la version bêta pour les environnements de test spécialisés, ayant atteint un nombre suffisant de participants. Cette fonctionnalité est en cours de préparation pour une disponibilité générale.

<!--
If you are interested in testing this new feature and sharing your feedback, send an email to [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) from your email address associated with your Adobe ID. -->


### Apporter votre propre Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Les clientes et clients peuvent désormais intégrer leurs référentiels Git Azure DevOps dans Cloud Manager, avec la prise en charge des référentiels Azure DevOps modernes et VSTS (Visual Studio Team Services) hérités.

* Pour les utilisateurs et utilisatrices d’Edge Delivery Services, le référentiel intégré peut être utilisé pour synchroniser et déployer le code du site.
* Pour les utilisateurs et utilisatrices d’AEM as a Cloud Service et d’Adobe Managed Services (AMS), le référentiel peut être lié aux pipelines full stack et front-end.

La prise en charge de types de pipeline supplémentaires et de la validation des demandes d’extraction par le biais de pipelines de qualité du code sera bientôt disponible.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->

**Questions fréquentes sur BYOG**

| Question | Réponse |
|---|---|
| *Comment un projet peut-il revenir au référentiel Git géré par Adobe si nécessaire ?* | Il est simple de revenir en arrière. [Mettez à jour les pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) pour pointer vers le référentiel Adobe et supprimez le référentiel externe s’il n’est plus nécessaire. |
| *Est-il possible de configurer différents référentiels pour différents environnements (par exemple, hors production ou en production) afin d’autoriser d’abord les tests hors production ?* | Oui, différents référentiels peuvent être configurés pour des environnements distincts. Par exemple, le pipeline de développement ou de qualité du code peut pointer vers un référentiel externe tandis que le pipeline de production reste connecté au référentiel Adobe. Assurez-vous que le traitement de synchronisation entre les deux référentiels reste actif pendant cette configuration. |
| *Les paramètres existants, comme les listes `IP Allow`, continuent-ils de fonctionner ?* | Oui, les listes `IP Allow` existantes continuent de fonctionner normalement. Cependant, si le référentiel Git externe est protégé par un pare-feu, les [adresses IP Adobe nécessaires doivent être ajoutées à la liste autorisée](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *Toutes les URL du référentiel GitLab fonctionnent-elles ? L’URL du référentiel utilisée suit le format `https://gitlab_dedicated_url.com/path/repo-name.git`, qui diffère de l’exemple de la documentation.* | Oui, tout référentiel GitLab prenant en charge l’API V3 ou V4 est pris en charge, y compris les URL GitLab auto-hébergées telles que celle décrite dans [Ajout de référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md) (`https://git-vendor-name.com/org-name/repo-name.git`). |


#### Gérer les jetons d’accès{#manage-access-tokens}

Utilisez **Gérer les jetons d’accès** dans Cloud Manager pour afficher, renommer et supprimer les jetons d’accès associés aux référentiels BYOG externes, tels que GitHub Enterprise, GitLab, Bitbucket et Azure DevOps.

Voir la section [Gérer les jetons d’accès](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

### Ajouter un pipeline de configuration Edge Delivery {#add-eds-pipeline}

Les pipelines de configuration sont désormais pris en charge pour les sites créés avec Edge Delivery Services, ce qui étend cette fonctionnalité au-delà des seuls environnements Cloud Service. Vous pouvez utiliser les **pipelines de configuration** pour gérer des paramètres tels que les règles de filtrage du trafic et les configurations du pare-feu d’application web (WAF), le cas échéant. Consultez [Configurations prises en charge](/help/operations/config-pipeline.md#configurations).

**Amélioration récente**

* Les pipelines Edge Delivery Services affichent désormais **Configuration** dans la colonne **Code déployé**, ce qui permet d’identifier instantanément les déploiements de configuration uniquement. <!-- CMGR‑69681 -->
* Cloud Manager affiche **Ajouter un pipeline Edge Delivery** dès qu’un programme contient au moins un site Edge Delivery Services et un domaine mappé. Dans le cas contraire, l’option est désactivée et une info-bulle explique les exigences manquantes. <!-- CMGR‑69680 -->
* L’onglet **Edge Delivery** affiche un nouveau widget **Pipelines Edge Delivery** qui répertorie le nom, le statut, le référentiel et la branche de chaque pipeline. <!-- (CMGR-69052) -->

  ![Widget de pipeline Edge Delivery affichant le nom, le statut, le référentiel et la branche du pipeline](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)

* Le panneau **Filtres** ajoute une section **Type de diffusion** qui comprend les cases à cocher **Diffusion Edge** et **Diffusion Publier**. <!-- (CMGR-69682) -->

  ![Panneau de filtrage présentant le nouveau type de diffusion de la diffusion Edge et de la diffusion Publier](/help/implementing/cloud-manager/release-notes/assets/filter-delivery-type.png)

![Ajouter un pipeline Edge Delivery dans la liste déroulante Ajouter un pipeline](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png) *Ajout d’un pipeline Edge Delivery à partir de la page **Vue d’ensemble du programme**, carte **Pipelines**.*

![Boîte de dialogue Ajouter un pipeline Edge Delivery](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Boîte de dialogue Ajouter un pipeline Edge Delivery.*

Voir la section [Ajouter un pipeline Edge Delivery](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md)

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.


## Correctifs

* Les pipelines ne fournissent désormais des variables qu’à la configuration de domaine Edge Delivery Services active, en ignorant toute configuration supprimée lors de la recréation du pipeline. <!-- (CMGR‑70039) -->
* L’exécution du pipeline démarre désormais de manière fiable. Correction d’un problème en raison duquel certains pipelines ne démarraient pas du fait d’erreurs de gestion des ressources internes. <!-- (CMGR‑58167) -->
* La copie de contenu valide les autorisations Cloud Manager et bloque les démarrages des utilisateurs et utilisatrices ne disposant pas des droits de gestion de déploiement ou d’administration. <!-- (CMGR‑62097) -->


<!-- ## Known issues {#known-issues} -->

