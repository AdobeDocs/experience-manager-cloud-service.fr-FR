---
title: Notes de mise à jour de la version 2025.10.0 de Cloud Manager
description: En savoir plus sur la version 2025.10.0 de Cloud Manager dans Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 302248ade67683712bf1895fd8dfdd8853aae1ac
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 56%

---

# Notes de mise à jour de Cloud Manager 2025.10.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

En savoir plus sur la version 2025.10.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.10.0 de Cloud Manager dans AEM as a Cloud Service est le vendredi 2 octobre 2025.

La prochaine version est prévue le vendredi 6 novembre 2025.

## Nouveautés {#what-is-new}

* **Pipelines de déploiement d’évaluation uniquement et de production uniquement** dédiés

  Cloud Manager propose désormais des pipelines de déploiement d’évaluation uniquement et de production uniquement dédiés, offrant ainsi une plus grande flexibilité pour gérer indépendamment les déploiements vers les environnements d’évaluation et de production. Voir [Fractionner des pipelines d’évaluation uniquement et de production uniquement](/help/implementing/cloud-manager/configuring-pipelines/stage-prod-only.md).

* **Service AEM Cloud Health Assessment**

  Adobe présente le service d’évaluation de l’intégrité du cloud AEM, un outil de contrôle automatisé et non invasif qui garantit l’optimisation, la sécurité et l’alignement de votre environnement AEM as a Cloud Service avec les bonnes pratiques.

  Ce service effectue les opérations suivantes :

   * Analyse les environnements afin d’identifier les goulots d’étranglement, les inefficacités et les risques potentiels.
   * Analyse les structures de contenu (plans directeurs, Live Copies) et les configurations personnalisées.
   * Identifie les dépendances obsolètes (AEM SDK, bibliothèques tierces).
   * Signale les problèmes de qualité du code (annotations incorrectes, modèles inefficaces).
   * Fournit des conseils pratiques par le biais de tableaux de bord tels que **Action Center**.
   * Prend en charge l’optimisation proactive par la détection et la résolution précoces des problèmes.

  Les équipes peuvent surveiller et améliorer en permanence leurs environnements AEM pour des performances plus fluides, une sécurité renforcée et une maintenabilité à long terme.

  Voir [&#x200B; Évaluation de l’intégrité pour les environnements de production et d’évaluation](/help/implementing/cloud-manager/reports/report-health-assessment.md).

* **Configuration de la prise en charge du pipeline**

  Les pipelines de configuration sont désormais pris en charge pour les sites créés avec Edge Delivery Services, ce qui étend cette fonctionnalité au-delà des seuls environnements Cloud Service. Vous pouvez utiliser les **Pipelines de configuration** pour gérer des paramètres tels que la configuration du réseau CDN, y compris les règles de filtrage du trafic et les sélecteurs d’origine. Consultez [Configurations prises en charge](/help/operations/config-pipeline.md#configurations).

  Les pipelines de configuration d’Edge Delivery prennent également en charge les secrets via les variables de pipeline Cloud Manager.

  Voir [Ajouter un pipeline Edge Delivery](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).

* **Boîte de dialogue de configuration du mappage de domaine-réseau CDN simplifiée**

  Cloud Manager a simplifié le flux **Mapper le domaine au réseau CDN** afin de réduire la confusion et d’accélérer la configuration. La boîte de dialogue met désormais l’accent sur le **réseau CDN géré par Adobe** (avec un badge « Recommandé »).

  ![Boîte de dialogue Mapper le domaine au réseau CDN avec le bouton radio Adobe Managed CDN sélectionné](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-dialog-box-adobe-managed-cdn.png).

  Voir [Ajouter un mappage de domaine](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md).

  La boîte de dialogue présente également une liste de contrôle unique et concise pour la vignette **Autre fournisseur de réseau CDN**, axée sur le contenu pédagogique avec les éléments suivants :

   * Pointez l’origine de votre réseau CDN sur `publish-p<PROGRAM_ID>-e<ENV_ID>.adobeaemcloud.com`.
   * Définissez **Host/SNI** pour transférer l’hôte d’origine.
   * Ajoutez `X-AEM-Edge-Key` (après le déploiement de la clé dans Cloud Manager).
   * Définissez `X-Forwarded-Host` sur votre domaine orienté client.
   * Effacez les autres en-têtes de `X-Forwarded-*` avant d’atteindre AEM.

  ![Boîte de dialogue Mapper le domaine au réseau CDN avec le bouton radio Autre fournisseur CDN sélectionné](/help/implementing/cloud-manager/assets/cdn/map-domain-to-cdn-dialog-box-other-cdn-provider.png)

  <!-- (no redundant `Origin` field or "Learn more" clutter) -->Le pied de page qui l’accompagne fournit deux liens utiles : des exemples de configurations pour les principaux réseaux de diffusion de contenu et un lien vers la documentation complète. Un seul bouton de confirmation - J’ai configuré mon réseau CDN - complète le flux.

  Voir [Réseau CDN dans AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN).

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

### Extensibilité et personnalisation d’Experience Hub {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) sert de point d’entrée à AEM, personnalisé en fonction des besoins de votre entreprise. Informez Adobe de vos extensions d’interface utilisateur AEM existantes afin qu’elles puissent vous aider à les activer dans Experience Hub avec un effort minimal.

![Diagramme du workflow d’extensibilité et de personnalisation d’Experience Hub](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Intégrez des expériences personnalisées dans Experience Hub pour étendre et personnaliser le tableau de bord de votre organisation. Outre les widgets intégrés d’Adobe, ajoutez les vôtres à l’aide du framework [Extensibilité de l’interface utilisateur](https://developer.adobe.com/uix/docs/). Créez des applications d’interface utilisateur basées sur JavaScript et faites-les apparaître à vos utilisateurs pour répondre aux besoins et aux workflows spécifiques à l’entreprise.

Intéressé par la version bêta ? Envoyez un courrier électronique à l’adresse [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) avec votre ID d’organisation Adobe et une brève description de la personnalisation que vous avez l’intention de créer.

### Versions plus rapides avec mise en cache du module {#quick-build-cm-pipelines}

Un nouveau modèle de version compile uniquement les modules modifiés (plutôt que le référentiel entier) à l’aide de la mise en cache au niveau du module pour réduire les temps de création. Elle s’applique aux pipelines de qualité de code, full stack et intermédiaires uniquement.

![Boîte de dialogue Modifier le pipeline hors production présentant les deux options de stratégie de création qui sont Création complète et Génération intelligente](/help/implementing/cloud-manager/release-notes/assets/non-production-pipeline-edit.png) *Boîte de dialogue Modifier le pipeline hors production présentant les deux options de stratégie de création qui sont Création complète et Génération intelligente.*

Dans la boîte de dialogue **Ajouter/Modifier un pipeline**, sous l’onglet **Code Source**, une nouvelle section **Stratégie de build** vous permet de choisir l’une des options de build suivantes :

* **Version complète** — crée tous les modules du référentiel à chaque exécution.
* **Version intelligente** : crée uniquement les modules qui ont été modifiés depuis la dernière validation, ce qui réduit la durée globale de la création.

Vous contrôlez les pipelines qui utilisent **génération intelligente**. Dans la version bêta, cette option s’affiche uniquement pour les pipelines **Qualité du code** et **Déploiement de développement**.

Intéressé ? Envoyez [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) par e-mail avec votre ID d’organisation et votre ID de programme Adobe.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline Variables in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).-->



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


## Correctifs {#bug-fixes}

La version d’octobre de Cloud Manager ne contient aucun correctif significatif.


<!-- ## Known issues {#known-issues} -->

