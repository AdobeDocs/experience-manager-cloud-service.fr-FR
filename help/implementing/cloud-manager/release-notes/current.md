---
title: Notes de mise à jour de Cloud Manager 2025.2.0 dans Adobe Experience Manager as a Cloud Service
description: En savoir plus sur la version 2025.2.0 de Cloud Manager dans AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: aaef376b733c10643e44205e55a0921c22008990
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 66%

---

# Notes de mise à jour de Cloud Manager 2025.2.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3389843928 -->

En savoir plus sur la version 2025.2.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.


Consultez également les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.2.0 de Cloud Manager dans AEM as a Cloud Service est le jeudi 13 février 2025.

La prochaine version est prévue le jeudi 13 mars 2025.

## Nouveautés {#what-is-new}

* **Mettre à jour vers les règles de qualité du code**

  À compter du jeudi 13 février 2025, l’étape de qualité du code Cloud Manager utilise désormais SonarQube 9.9.5.90363.

  Les règles mises à jour, disponibles pour Cloud Manager sur AEM as a Cloud Service à l’adresse [ce lien](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules), déterminent les scores de sécurité et la qualité du code pour les pipelines Cloud Manager.

* SonarQube 9.9 est désormais le moteur d’analyse de la qualité du code par défaut pour tous les clients.

* **Prise en charge de la version Java 17 et Java 21**

  La clientèle peut désormais créer des versions avec Java 17 ou Java 21 afin d’accéder à des améliorations de performances et à de nouvelles fonctionnalités de langage. Pour connaître les étapes de configuration, notamment la mise à jour des versions de votre projet Maven et de votre bibliothèque, voir la section [Environnement de création](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Lorsque la version est définie sur Java 17 ou Java 21, l’environnement d’exécution déployé est Java 21.

* **99,99 % rapports de disponibilité de SLA pour Edge Delivery Services**

  Des rapports de disponibilité à 99,99 % de haute disponibilité sont désormais disponibles pour les programmes Edge Delivery Services admissibles. Pour activer cette fonctionnalité, la clientèle doit intégrer ses sites Edge Delivery Services et appliquer son contrat de niveau de service (SLA) à 99,99 % dans Cloud Manager.

  Voir aussi [Contrat de niveau de service (SLA)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla).

* **Amélioration de l’expérience d’invitation des utilisateurs pour Edge Delivery Services**

  Des améliorations ont été apportées à l’expérience d’invitation d’utilisateurs au référentiel de contenu associé à Edge Delivery Services. <!-- CMGR-65331 -->

* **Création automatique de profils administrateur sur les instances de publication**

  Auparavant, Cloud Manager permettait la création manuelle de profils d’administration sur les instances de publication, mais ne prenait pas en charge la création automatique par défaut. Grâce à cette mise à jour, les profils d’administration sont désormais automatiquement créés sur les instances de publication, ce qui améliore la convivialité et réduit le temps de configuration.

  Pour plus d’informations, voir [Autorisations personnalisées](/help/implementing/cloud-manager/custom-permissions.md).

  ![Filtrage des activités du pipeline](/help/implementing/cloud-manager/release-notes/assets/product-profiles.png)

* **Transition vers OAuth pour les environnements Cloud Service**

  Les nouveaux environnements Cloud Service utilisent désormais l’authentification service à service basée sur OAuth pour les projets d’intégration Adobe Developer Console au lieu de la méthode d’authentification JWT utilisée précédemment. L’authentification JWT est obsolète et devrait prendre fin en juin 2025.

* **Prise en charge des clés privées EC (courbe elliptique) (secp384r1)**

  Cloud Manager prend désormais en charge les clés privées `secp384r1` courbe elliptique (EC), ce qui améliore la sécurité et la conformité pour les certificats SSL OV/EV gérés par le client.
Pour plus d’informations, voir [Conditions requises pour les certificats SSL OV/EV gérés par la clientèle](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements). <!-- CMGR-63636 -->

* **Environnements de test spécialisés**

  Un nouvel environnement de développement doté de ressources améliorées sera disponible pour les utilisateurs et utilisatrices précoces à compter du 27 février 2025.


<!--
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


## Correctifs

* **(IU) Correction d’un problème qui empêchait la configuration du réseau CDN pour les domaines dans Cloud Manager.**
Les clientes et clients qui tentaient d’ajouter une configuration de réseau CDN dans Cloud Manager rencontraient une erreur d’écran lorsqu’ils ou elles sélectionnaient un domaine dans le menu déroulant. Ce bug de l’interface d’utilisation empêchait le mappage de domaine dans les environnements de production, bloquant ainsi le processus de configuration.

  En outre, certains domaines restaient inaccessibles sur le serveur principal, malgré leur suppression de l’interface d’utilisation. Ce problème entraînait des conflits avec les configurations CDN existantes.

  Ce correctif vous permet désormais de sélectionner un domaine dans la liste déroulante sans rencontrer d’erreur. Les incohérences du serveur principal qui empêchaient la reconfiguration du domaine ont été corrigées. Enfin, une validation améliorée garantit désormais que les domaines en conflit sont correctement supprimés avant de les ajouter à nouveau.<!-- CMGR-64888 -->
* **(serveur principal) Correction d’un problème en raison duquel les notifications d’expiration SSL étaient envoyées plusieurs fois.**
Un bug a été identifié, où le planificateur de notifications d’expiration SSL, conçu pour s’exécuter une fois par jour à minuit, se déclenchait incorrectement deux fois par jour, une fois à minuit et une fois de plus à minuit et demi. Ce problème entraînait l’envoi de plusieurs notifications redondantes concernant les certificats SSL arrivant à expiration.

  Le planificateur de notifications s’exécute désormais correctement une seule fois par jour, comme prévu. De plus, vous ne recevez plus de notifications d’expiration SSL en double. <!-- CMGR-64748 -->




<!-- ## Known issues {#known-issues} -->
