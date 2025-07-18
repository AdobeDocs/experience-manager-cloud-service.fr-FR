---
title: Notes de mise à jour de la version 2025.7.0 de Cloud Manager
description: En savoir plus sur la version 2025.7.0 de Cloud Manager dans Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 3e7ce0c7f330ba92b57e36ea8fe5bb17b5998cb1
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 99%

---

# Notes de mise à jour de Cloud Manager 2025.7.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

En savoir plus sur la version 2025.7.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.7.0 de Cloud Manager dans AEM as a Cloud Service est le jeudi 10 juillet 2025.

La prochaine version est prévue le jeudi 7 août 2025.

## Nouveautés {#what-is-new}

* **Cloud Manager ajoute la prise en charge du certificat SSL ECDSA (Elliptic Curve Digital Signature Algorithm).**

  Cloud Manager prend désormais en charge les certificats ECDSA. La fonctionnalité offre une sécurité renforcée avec des tailles de clé plus petites, ce qui permet à la clientèle d’appliquer une cryptographie moderne légère dans ses configurations de réseau CDN. <!-- https://jira.corp.adobe.com/browse/CMGR-62399 -->

* **Télécharger le rapport d’utilisation de la licence du site**

  Sur la page **Détails d’utilisation des sites** (dans Cloud Manager, cliquez sur **Licence**. Dans le tableau Solutions, dans la ligne **Sites**, cliquez sur **Afficher les détails d’utilisation**). La clientèle peut désormais cliquer sur **Télécharger le rapport** pour exporter ses données au format CSV. Ce téléchargement simplifie l’analyse et le partage des tendances d’utilisation. <!-- https://jira.corp.adobe.com/browse/CMGR-42274 -->

  ![Page Détails d’utilisation des sites](/help/implementing/cloud-manager/release-notes/assets/sites-license-usage-page.png)

  Consultez le [tableau de bord des licences](/help/implementing/cloud-manager/license-dashboard.md).

## Programmes d’adoption précoce {#private-beta-program}

Participez aux programmes Beta et Alpha de Cloud Manager pour obtenir un accès exclusif aux fonctionnalités à venir avant leur publication générale.

Les opportunités suivantes sont actuellement disponibles :

### Restauration en un clic pour les déploiements de pipeline {#one-click-rollback}

Revenez rapidement à un déploiement précédent si le dernier code source client ne fonctionne pas comme prévu ; il n’est pas nécessaire de réexécuter le pipeline complet ou de rétablir manuellement les validations.<!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

![Restaurez le code source client à partir de la carte Environnements](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed.png) *Carte Environnements ci-dessus présentant l’option **Restaurer** >**Code précédent déployé**pour un environnement sélectionné.*


![Boîte de dialogue Restaurer le code déployé précédent](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed-dialogbox.png)
*Dans la boîte de dialogue **Restaurer le code déployé précédent**, passez en revue la version actuellement déployée et la version à restaurer, puis cliquez sur **Confirmer***.


![Activation de la restauration](/help/implementing/cloud-manager/release-notes/assets/restoring-previous-code-deployed-restoring.png)
*Cloud Manager restaure l’environnement à sa version précédente, conserve le contenu et la configuration intacts et marque l’environnement comme **restauré**jusqu’à la fin du déploiement.*


![Version du code Source utilisée](/help/implementing/cloud-manager/release-notes/assets/environments-view-details-sourcecodeversion.png) *La vue Détails de l’environnement, comme illustré ci-dessus, affiche désormais également la version active utilisée du code source.*

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [restorecode@adobe.com](mailto:restorecode@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.

Voir [Restaurer le code précédemment déployé dans AEM as a Cloud Service](/help/operations/restore-previous-code-deployed.md).

Consultez également [Restauration de contenu dans AEM as a Cloud Service](/help/operations/restore.md).


### Environnement de test spécialisé {#specialized-test-environment}

Cloud Manager prend désormais en charge l’ajout d’un nouveau type d’environnement appelé **Environnement de test spécialisé**. L’environnement est conçu pour aider les équipes à valider les fonctionnalités dans des conditions proches de la production avant la mise en ligne. Ce type d’environnement est distinct des environnements *Production+Évaluation*, *Développement* ou *Développement rapide* et offre un espace ciblé pour exécuter des scénarios de validation avancés.

Amélioration récente : vous pouvez désormais configurer des environnements de test spécialisés sur un pipeline hors production grâce à un workflow plus simple et plus intuitif. La configuration rationalisée accélère l’achèvement et réduit les erreurs de configuration.

Voir la section [Ajouter un environnement de test spécialisé](/help/implementing/cloud-manager/specialized-test-environment.md).

![Boîte de dialogue Ajouter un environnement avec le bouton radio Environnement de test spécialisé sélectionné](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png)

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [grp-earlyadopter_cs_advtestenvironment@adobe.com](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.


### Apportez votre propre Git (BYOG), maintenant avec prise en charge d’Azure DevOps {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Les clientes et clients peuvent désormais intégrer leurs référentiels Git Azure DevOps dans Cloud Manager, avec la prise en charge des référentiels Azure DevOps modernes et VSTS (Visual Studio Team Services) hérités.

* Pour les utilisateurs et utilisatrices d’Edge Delivery Services, le référentiel intégré peut être utilisé pour synchroniser et déployer le code du site.
* Pour les utilisateurs et utilisatrices d’AEM as a Cloud Service et d’Adobe Managed Services (AMS), le référentiel peut être lié aux pipelines full stack et front-end.

La prise en charge de types de pipeline supplémentaires et de la validation des demandes d’extraction par le biais de pipelines de qualité du code sera bientôt disponible.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.


**Questions fréquentes sur BYOG**

| Question | Réponse |
|---|---|
| *Comment un projet peut-il revenir au référentiel Git géré par Adobe si nécessaire ?* | Il est simple de revenir en arrière. [Mettez à jour les pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) pour pointer vers le référentiel Adobe et supprimez le référentiel externe s’il n’est plus nécessaire. |
| *Est-il possible de configurer différents référentiels pour différents environnements (par exemple, hors production ou en production) afin d’autoriser d’abord les tests hors production ?* | Oui, différents référentiels peuvent être configurés pour des environnements distincts. Par exemple, le pipeline de développement ou de qualité du code peut pointer vers un référentiel externe tandis que le pipeline de production reste connecté au référentiel Adobe. Assurez-vous que le traitement de synchronisation entre les deux référentiels reste actif pendant cette configuration. |
| *Les paramètres existants comme les listes d’adresses IP autorisées continuent-ils à fonctionner ?* | Oui, les listes d’adresses IP autorisées existantes continuent de fonctionner comme d’habitude. Cependant, si le référentiel Git externe est protégé par un pare-feu, les [adresses IP Adobe nécessaires doivent être ajoutées à la liste autorisée](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *Toutes les URL du référentiel GitLab fonctionnent-elles ? L’URL du référentiel utilisée suit le format `https://gitlab_dedicated_url.com/path/repo-name.git`, qui diffère de l’exemple de la documentation.* | Oui, tout référentiel GitLab prenant en charge l’API V3 ou V4 est pris en charge, y compris les URL GitLab auto-hébergées telles que celle décrite dans [Ajout de référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md) (`https://git-vendor-name.com/org-name/repo-name.git`). |


#### Gérer les jetons d’accès{#manage-access-tokens}

Utilisez **Gérer les jetons d’accès** dans Cloud Manager pour afficher, renommer et supprimer les jetons d’accès associés aux référentiels BYOG externes, tels que GitHub Enterprise, GitLab, Bitbucket et Azure DevOps.

Voir la section [Gérer les jetons d’accès](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.


### Ajouter un pipeline de configuration Edge Delivery {#add-eds-pipeline}

Les pipelines de configuration sont désormais pris en charge pour les sites créés avec Edge Delivery Services, ce qui étend cette fonctionnalité au-delà des seuls environnements Cloud Service. Vous pouvez utiliser les **pipelines de configuration** pour gérer des paramètres tels que les règles de filtrage du trafic et les configurations du pare-feu d’application web (WAF), le cas échéant. Consultez [Configurations prises en charge](/help/operations/config-pipeline.md#configurations).

![Ajouter un pipeline Edge Delivery dans la liste déroulante Ajouter un pipeline](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png) *Ajout d’un pipeline Edge Delivery à partir de la page **Vue d’ensemble du programme**, carte **Pipelines**.*

![Boîte de dialogue Ajouter un pipeline Edge Delivery](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *Boîte de dialogue Ajouter un pipeline Edge Delivery.*

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID.


## Correctifs

* Cloud Manager met désormais à jour la version de tous les pipelines lors des mises à niveau de l’environnement, assurant ainsi un suivi de version cohérent sur tous les types de pipeline. <!-- CMGR-69043 -->
* L’interface d’utilisation affiche désormais des messages de statut et d’erreur détaillés lorsqu’un certificat SSL de validation de domaine (DV) échoue, ce qui permet de comprendre et de résoudre les problèmes de certificat. <!-- CMGR-68872 -->
* Lors de la modification d’un mappage de domaine, l’interface d’utilisation empêche désormais de sélectionner des certificats SSL qui ne correspondent pas au domaine sélectionné, ce qui réduit les erreurs de configuration et améliore la fiabilité lors de la configuration. <!-- CMGR-64307 -->
* Dans certains cas, les certificats n’ont pas été correctement supprimés, la maintenance du domaine est toujours active. <!-- CMGR-69867 -->
* Correction d’un problème qui pouvait bloquer les mises à niveau de *Adobe Assets* vers *Adobe Assets Ultimate* dans certains cas. Les transitions sont désormais plus fluides et plus fiables. <!-- CMGR-69506 -->
* Correction d’un problème où les champs de région clés étaient automatiquement définis lors de la création d’environnements multi-régions pour prendre en charge les services et déploiements en aval en douceur. <!-- CMGR-69471 -->
* Correction d’un problème en raison duquel certains pipelines de configuration ne s’arrêtaient pas correctement après l’exécution. Désormais, les pipelines se terminent correctement et se ferment comme prévu, ce qui améliore la fiabilité. <!-- CMGR-69344 -->


<!-- ## Known issues {#known-issues} -->

