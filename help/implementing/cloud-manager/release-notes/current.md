---
title: Notes de mise à jour de Cloud Manager 2025.2.0 dans Adobe Experience Manager as a Cloud Service
description: En savoir plus sur la version 2025.2.0 de Cloud Manager dans AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: c2a0961cae6d36d8ea3116c6e7982889257f90c8
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 35%

---

# Notes de mise à jour de Cloud Manager 2025.2.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

En savoir plus sur la version 2025.2.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.


Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.2.0 de Cloud Manager dans AEM as a Cloud Service a été le vendredi 13 février 2025.

La prochaine version est prévue le vendredi 13 mars 2025.

## Nouveautés {#what-is-new}

* **Mise à jour vers les règles de qualité du code.**
À compter du jeudi 13 février 2025, l’étape de qualité du code Cloud Manager utilise désormais une version mise à niveau de SonarQube 9.9.5.90363.

  Les règles mises à jour, disponibles pour Cloud Manager dans AEM as a Cloud Service à [cette adresse](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules), déterminent les scores de sécurité et la qualité du code pour les pipelines Cloud Manager. Cette mise à jour peut avoir un impact sur vos points de contrôle qualité et bloquer potentiellement les déploiements.

* **Prise en charge de la version Java 17 et Java 21.**

  Les clients peuvent désormais créer des versions avec Java 17 ou Java 21, et ont ainsi accès aux améliorations de performances et aux nouvelles fonctionnalités de langage. Pour connaître les étapes de configuration, notamment la mise à jour des versions de votre projet Maven et de votre bibliothèque, voir la section [Environnement de création](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Lorsque la version est définie sur Java 17 ou Java 21, l’environnement d’exécution déployé est Java 21.

   * **Activation des fonctionnalités**
      * Cette fonctionnalité sera activée pour tous les utilisateurs et utilisatrices le jeudi 13 février 2025, date coïncidant avec le déploiement par défaut de la nouvelle version de SonarQube.
      * Les clientes et clients peuvent l’activer *immédiatement* en définissant les deux configurations de variables décrites ci-dessus pour la mise à niveau de la version 9.9 de SonarQube.

   * **Déploiement de l’environnement d’exécution Java 21**
      * L’environnement d’exécution Java 21 est déployé lors d’une création avec Java 17 ou Java 21.
      * Le déploiement progressif vers tous les environnements Cloud Manager commence en février pour les sandbox et les environnements de développement et s’étend aux environnements de production en avril.
      * Les clientes et clients qui créent avec Java 11 et qui souhaitent adopter l’environnement d’exécution Java 21 *plus tôt* peuvent contacter Adobe à l’adresse [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com).

* **99,99 % de reporting sur la disponibilité pour Edge Delivery Services.**
Des rapports de disponibilité à 99,99 % de haute disponibilité sont désormais disponibles pour les programmes Edge Delivery Services admissibles. Pour activer cette fonctionnalité, les clients doivent intégrer leurs sites Edge Delivery Services et appliquer leur Service level agreement (SLA) à 99,99 % dans Cloud Manager.

  Voir aussi [SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla).

* **Amélioration de l’expérience d’invitation des utilisateurs pour Edge Delivery Services.**
Des améliorations ont été apportées à l’expérience d’invitation d’utilisateurs au référentiel de contenu associé à Edge Delivery Services. <!-- CMGR-65331 -->

* **Création automatique de profils d’administration sur les instances de publication.**
Auparavant, Cloud Manager permettait la création manuelle de profils d’administration sur les instances de publication, mais ne prenait pas en charge la création automatique par défaut. Grâce à cette mise à jour, les profils d’administration sont désormais automatiquement créés sur les instances de publication, ce qui améliore la convivialité et réduit le temps de configuration pour les clients.

  Pour plus d’informations, voir [Autorisations personnalisées](/help/implementing/cloud-manager/custom-permissions.md).

  ![Filtrage des activités du pipeline](/help/implementing/cloud-manager/release-notes/assets/product-profiles.png)

* **Transition vers OAuth pour les environnements Cloud Service.**
Les nouveaux environnements Cloud Service utilisent désormais l’authentification service à service basée sur OAuth pour les projets d’intégration Adobe Developer Console au lieu de la méthode d’authentification JWT utilisée précédemment. L’authentification JWT est obsolète et devrait prendre fin en juin 2025.

* **Prise en charge des clés privées EC (courbe elliptique) (secp384r1).**
Cloud Manager prend désormais en charge les clés privées `secp384r1` courbe elliptique (EC), ce qui améliore la sécurité et la conformité pour les certificats SSL OV/EV gérés par le client.
Pour plus d’informations, voir [Conditions requises pour les certificats SSL OV/EV gérés par le client](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md). <!-- CMGR-63636 -->

<!--
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


## Correctifs

* **(IU) Correction d’un problème qui empêchait la configuration du réseau CDN pour les domaines dans Cloud Manager.**
Les clients et clientes qui tentent d’ajouter une configuration de réseau CDN dans Cloud Manager rencontrent une erreur d’écran lorsqu’ils sélectionnent un domaine dans le menu déroulant. Ce bug de l’interface utilisateur empêchait le mappage de domaine dans les environnements de production, bloquant ainsi le processus de configuration.

  En outre, certains domaines sont restés inaccessibles sur le serveur principal, bien qu’ils aient été supprimés de l’interface utilisateur. Ce problème entraînait des conflits avec les configurations CDN existantes.

  Ce correctif vous permet désormais de sélectionner un domaine dans la liste déroulante sans rencontrer d’erreur. Les incohérences du serveur principal qui empêchaient la reconfiguration du domaine ont été corrigées. Enfin, une validation améliorée garantit désormais que les domaines en conflit sont correctement supprimés avant de les ajouter à nouveau.<!-- CMGR-64888 -->
* **(serveur principal) Correction d’un problème en raison duquel les notifications d’expiration SSL étaient envoyées plusieurs fois.**
Un bug a été identifié où le planificateur de notifications d’expiration SSL, conçu pour s’exécuter une fois par jour à minuit, se déclenchait incorrectement deux fois par jour, une fois à minuit et une fois de plus à minuit:30. Ce problème entraînait l’envoi de plusieurs notifications redondantes concernant les certificats SSL arrivant à expiration.

  Le planificateur de notifications s’exécute désormais correctement une seule fois par jour, comme prévu. De plus, vous ne recevez plus de notifications d’expiration SSL en double. <!-- CMGR-64748 -->




<!-- ## Known issues {#known-issues} -->
