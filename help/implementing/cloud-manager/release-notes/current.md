---
title: Notes de mise à jour de Cloud Manager 2025.1.0 dans Adobe Experience Manager as a Cloud Service
description: En savoir plus sur la version 2025.1.0 de Cloud Manager dans AEM as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: bf12306969581723e4e9ce1517a8f0d445f26521
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 22%

---

# Notes de mise à jour de Cloud Manager 2025.1.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

En savoir plus sur la version 2025.1.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Consultez les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de la version 2025.1.0 de Cloud Manager dans AEM as a Cloud Service est le mercredi 22 janvier 2025.

La prochaine version est prévue le vendredi 13 février 2025.


## Nouveautés {#what-is-new}

* **Règles de qualité du code :** l’étape de qualité du code Cloud Manager commencera à utiliser SonarQube Server 9.9 avec la version Cloud Manager 2025.2.0, prévue pour le jeudi 13 février 2025.

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
      * Les clients peuvent l’activer *immédiatement* en définissant les deux configurations de variable décrites ci-dessus pour la mise à niveau de la version 9.9 de SonarQube.

   * **Déploiement d’exécution Java 21**
      * L’exécution Java 21 est déployée lors de la création avec Java 17 ou Java 21.
      * Le déploiement progressif vers tous les environnements Cloud Manager commence en février pour les sandbox et les environnements de développement et s’étend aux environnements de production en avril.
      * Les clients qui souhaitent adopter l’exécution Java 21 *auparavant* peuvent contacter l’Adobe à l’adresse [aemcs-java-adopter@adobe.com](mailto:aemcs-java-adopter@adobe.com).


<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->

<!-- ## Bug fixes -->




<!-- ## Known issues {#known-issues} -->
