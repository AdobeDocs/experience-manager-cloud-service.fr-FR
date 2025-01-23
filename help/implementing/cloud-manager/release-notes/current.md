---
title: Notes de mise à jour de Cloud Manager 2025.1.0 dans Adobe Experience Manager as a Cloud Service
description: En savoir plus sur la version 2025.1.0 de Cloud Manager dans AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: ee01e5a2b805330f47af7ff563ca1ac90036f0bf
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 11%

---

# Notes de mise à jour de Cloud Manager 2025.1.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

En savoir plus sur la version 2025.1.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Consultez les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.1.0 de Cloud Manager dans AEM as a Cloud Service est le mercredi 22 janvier 2025.

La prochaine version est prévue le vendredi 13 février 2025.


## Nouveautés {#what-is-new}

* **Règles de qualité du code - Mise à niveau du serveur SonarQube :** l’étape Qualité du code Cloud Manager commencera à utiliser SonarQube Server 9.9 avec la version Cloud Manager 2025.2.0, prévue pour le jeudi 13 février 2025.

  Pour vous préparer, les règles SonarQube mises à jour sont désormais disponibles à l’adresse [Règles de qualité du code](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules).

  Vous pouvez « vérifier rapidement » les nouvelles règles en définissant la variable de texte de pipeline suivante :

  `CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

  En outre, définissez la variable suivante pour vous assurer que l’étape de qualité du code s’exécute pour la même validation (normalement ignorée pour la même `commitId`) :

  `CM_DISABLE_BUILD_REUSE` = `true`

![Page de configuration des variables](/help/implementing/cloud-manager/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe recommande de créer un pipeline de qualité du code CI/CD, configuré sur la même branche que votre pipeline de production principal. Définissez les variables appropriées *avant* dans la version du 13 février 2025 pour vérifier que les nouvelles règles appliquées n’introduisent pas de bloqueurs.

* Prise en charge des builds **Java 17 et Java 21 :** les clients peuvent désormais créer des builds avec Java 17 ou Java 21, ce qui leur permet d’accéder à des améliorations de performances et à de nouvelles fonctionnalités de langage. Pour connaître les étapes de configuration, notamment la mise à jour des versions de votre projet Maven et de votre bibliothèque, voir [Environnement de création](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Lorsque la version de build est définie sur Java 17 ou Java 21, l’exécution déployée est Java 21.

   * **Activation des fonctionnalités**
      * Cette fonctionnalité sera activée pour tous les clients et clientes le jeudi 13 février 2025, date coïncidant avec le déploiement par défaut de la nouvelle version de SonarQube.
      * Les clients peuvent l’activer *immédiatement* en définissant les deux configurations de variables décrites ci-dessus pour la mise à niveau de la version 9.9 de SonarQube.

   * **Déploiement d’exécution Java 21**
      * L’exécution Java 21 est déployée lors de la création avec Java 17 ou Java 21.
      * Le déploiement progressif vers tous les environnements Cloud Manager commence en février pour les sandbox et les environnements de développement et s’étend aux environnements de production en avril.
      * Les clients qui créent avec Java 11 et qui souhaitent adopter l’exécution Java 21 *auparavant* peuvent contacter l’Adobe à l’adresse [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com).

* **« Configurations du réseau CDN » renommées « Mappages de domaine » :** dans le cadre des améliorations de l’interface utilisateur dans AEM Cloud Manager, le libellé « Configurations du réseau CDN » est désormais renommé « Mappages de domaine ». Cette modification améliore l’alignement terminologique avec les fonctionnalités. <!-- CMGR-64738 -->

  ![ « Configurations du réseau CDN » renommées « Mappages de domaine » dans l’interface utilisateur](/help/implementing/cloud-manager/release-notes/assets/domain-mappings.png)

* **Approvisionnement d’un site Edge Delivery en un clic :** Cloud Manager permet désormais aux utilisateurs disposant des autorisations et licences appropriées de créer un exemple de site de Edge Delivery Services en un seul clic. Ce processus simplifié offre les fonctionnalités automatisées suivantes :

   * **Intégration GitHub** : crée automatiquement un référentiel GitHub au sein d’une organisation existante, préconfiguré avec un modèle standard pour les Edge Delivery Services.
   * **Installation de l’application de synchronisation du code AEM** - Installe l’application de synchronisation du code AEM sur le référentiel, assurant ainsi une synchronisation et un déploiement transparents.
   * **Configuration de Content Collaboration** : associe un dossier Google Drive désigné pour le stockage de contenu, fournissant ainsi un environnement collaboratif pour la gestion de contenu.
   * **Publication de contenu** - Les utilisateurs peuvent désormais publier du contenu pour les sites configurés directement à partir de l’interface utilisateur de Cloud Manager, ce qui simplifie les workflows et améliore l’efficacité.
   * **Enhanced Collaboration** - La plateforme permet aux utilisateurs d’ajouter plusieurs collaborateurs au dossier de stockage de contenu de Google Drive, ce qui facilite le travail d’équipe et les contributions de contenu.

  Ces améliorations visent à améliorer l’automatisation, à simplifier les processus de configuration et à améliorer la collaboration pour les utilisateurs Edge Delivery Services. <!-- CMGR-59362 -->

  ![Mise en service d’un site Edge Delivery](/help/implementing/cloud-manager/release-notes/assets/eds-one-click-60.png)

  ![Boîte de dialogue Configuration du site Edge Delivery](/help/implementing/cloud-manager/release-notes/assets/eds-provision-60.png)

* **Prise en charge améliorée des sites Edge Delivery Services :** Cloud Manager prend désormais en charge l’intégration des derniers sites Edge Delivery Services. Cette mise à jour comprend une refactorisation complète du réseau CDN et de la pile de diffusion, ce qui se traduit par une robustesse et une maintenabilité améliorées.

* **Mise à jour du programme pour les utilisateurs et utilisatrices précoces - Prise en charge de la validation PR pour Bitbucket et GitLab :** Cloud Manager prend désormais en charge la validation de la requête de tirage (PR) pour les versions cloud et auto-hébergées de Bitbucket et GitLab. Cette fonctionnalité permet aux clients de tester leurs modifications de code par rapport aux seuils de qualité de code d’Adobe avant de fusionner une requête de tirage. En garantissant une qualité de code supérieure avant la fusion, cette amélioration améliore considérablement le taux de réussite des modifications de code dans les pipelines de production, ce qui réduit le délai de mise sur le marché et rationalise les workflows de développement.


<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->

<!-- ## Bug fixes -->




<!-- ## Known issues {#known-issues} -->
