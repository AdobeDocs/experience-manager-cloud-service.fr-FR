---
title: Notes de mise à jour de la version 2025.9.0 de Cloud Manager
description: En savoir plus sur la version 2025.9.0 de Cloud Manager dans Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 67fbd48d8cf4ac58d3bcff1eb314045b4ebd24b3
workflow-type: tm+mt
source-wordcount: '1138'
ht-degree: 98%

---

# Notes de mise à jour de Cloud Manager 2025.9.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

En savoir plus sur la version 2025.9.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.9.0 de Cloud Manager dans AEM as a Cloud Service est le jeudi 4 septembre 2025.

La prochaine version est prévue le jeudi 2 octobre 2025.

## Nouveautés {#what-is-new}

* **Renouveler manuellement les certificats de validation de domaine gérés par Adobe**

  Vous pouvez désormais renouveler manuellement les certificats de validation de domaine (DV) gérés par Adobe ayant échoué à partir de Cloud Manager ou de l’API publique pour actualiser les certificats de manière proactive. <!-- CMGR-68738 -->

  ![Renouvellement du certificat SSL](/help/implementing/cloud-manager/release-notes/assets/ssl-certificate-adobedv-renew.png)

* **Ajout de la prise en charge d’Azure DevOps (référentiels privés)**

  Les mises à jour de la documentation incluent les étapes de configuration pour Apporter votre propre Git (BYOG) avec Azure DevOps et la validation de la demande d’extraction. Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

* **Prise en charge de Bring Your Own Git (BYOG) étendue aux pipelines de configuration (référentiels privés)**

  Cloud Manager prend désormais en charge les pipelines de configuration avec des référentiels privés sur GitHub, Bitbucket, Azure DevOps et GitLab. Cette prise en charge accélère encore le cycle de développement. Voir [Vérifications des demandes de tirage pour les référentiels privés](/help/implementing/cloud-manager/managing-code/github-check-config.md).

<!--
### Staging-Only and Production-Only Pipelines {#staging-production-only-pipelines}

Support for [staging-only and production-only pipelines](/help/implementing/cloud-manager/configuring-pipelines/stage-prod-only.md) has been introduced, enabling you to split full-stack production deployment pipelines into smaller, specialized deployments.

If you are interested in testing this new feature and sharing your feedback, send an email to  `Grp-cloudmanager_splitpipelines@adobe.com` from your email address associated with your Adobe ID. -->


## Programmes bêta {#private-beta-program}

Participez au programme bêta de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur disponibilité générale.

Les opportunités suivantes sont actuellement disponibles :
<!--
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.-->

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
>Adobe a fermé les demandes d’accès à la version bêta pour les environnements de test spécialisés, ayant atteint un nombre suffisant de participantes et participants. Cette fonctionnalité est en cours de préparation en vue d’une disponibilité générale.

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

### Ajouter un pipeline de configuration Edge Delivery {#add-eds-pipeline}

Les pipelines de configuration sont désormais pris en charge pour les sites créés avec Edge Delivery Services, ce qui étend cette fonctionnalité au-delà des seuls environnements Cloud Service. Vous pouvez utiliser les **pipelines de configuration** pour gérer des paramètres tels que les règles de filtrage du trafic et les configurations du pare-feu d’application web (WAF), le cas échéant. Consultez [Configurations prises en charge](/help/operations/config-pipeline.md#configurations).

**Amélioration récente**

* Les pipelines de configuration d’Edge Delivery prennent désormais en charge les secrets via les variables de pipeline Cloud Manager.
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

## Correctifs {#bug-fixes}

La version de septembre de Cloud Manager ne contient aucun correctif important.


<!-- ## Known issues {#known-issues} -->

