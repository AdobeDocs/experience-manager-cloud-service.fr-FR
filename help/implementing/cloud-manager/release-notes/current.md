---
title: Notes de mise à jour de Cloud Manager 2024.12.0 dans Adobe Experience Manager as a Cloud Service
description: En savoir plus sur la version 2024.12.0 de Cloud Manager dans AEM as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: ea1aa471a4fcb2ace6e4079715ac88af2d296e18
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 37%

---

# Notes de mise à jour de Cloud Manager 2024.12.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

En savoir plus sur la version 2024.12.0 de Cloud Manager dans AEM (Adobe Experience Manager) as a Cloud Service.

>[!NOTE]
>
>Consultez les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Dates de publication {#release-date}

La date de publication de Cloud Manager 2024.12.0 dans AEM as a Cloud Service est le jeudi 5 décembre 2024.

La prochaine version est prévue pour janvier 2024.

## Nouveautés {#what-is-new}

* **Prise en charge de Java 21 :** Les clients peuvent désormais créer avec Java 17 ou Java 21, en profitant des améliorations de performances et des nouvelles fonctionnalités de langue. Voir [Environnement de création](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) pour connaître les étapes de configuration, y compris la mise à jour de la description de votre projet Maven et de certaines versions de bibliothèque. Lorsque la version de build est définie sur Java 17 ou Java 21, l’exécution prend par défaut Java 21.

  À compter de février 2025, les environnements de test et de développement effectuent la mise à niveau vers l’exécution Java 21, quelle que soit la version de build (Java 8, 11, 17 ou 21). Les environnements de production ont été mis à niveau en avril 2025.

* **Un type d’enregistrement :** La prise en charge d’un type d’enregistrement a été ajoutée afin d’améliorer la préparation Go Live Readiness des domaines à l’aide des configurations CDN dans AEM Cloud Manager. Vous avez désormais la possibilité d’activer en ajoutant un type d’enregistrement CNAME ou un type d’enregistrement A représentant les adresses IP de Fastly, ce qui simplifie le routage de domaine. Cette amélioration élimine la restriction de ne compter que sur des enregistrements CNAME pour la configuration de domaine avec Fastly.

  Voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). <!-- CMGR-63076 -->

* **Ajouter plusieurs domaines à un site Edge Delivery :** vous pouvez désormais ajouter plusieurs domaines, y compris des domaines apex et non-apex, à un site Edge Delivery (EDS) dans AEM Cloud Manager. Cette amélioration résout les limitations précédentes qui limitaient la possibilité d’associer plusieurs domaines à une origine EDS. La mise à jour offre une meilleure flexibilité pour la gestion des configurations de domaine et simplifie les processus d’activation pour les sites avec des configurations de domaine complexes. <!-- CMGR-63007 -->

* **Options de filtrage avancé :** Des options de filtrage avancées ont été introduites sur les pages d’exécution de pipeline et les pages de certificat SSL dans AEM Cloud Manager. Vous pouvez désormais filtrer selon plusieurs critères, ce qui vous permet d’accéder plus rapidement aux données pertinentes et d’améliorer l’efficacité du déploiement. <!-- CMGR-26263 -->

   * **Filtrage des activités de pipeline :** comprend le filtrage des activités de pipeline, ce qui vous permet d’affiner les résultats de recherche pour des activités de pipeline spécifiques. Les filtres disponibles incluent pipeline, action et état.
     ![Filtrage des activités de pipeline](/help/implementing/cloud-manager/assets/filters-pipeline.png)


   * **Filtrage des certificats SSL :** comprend le filtrage des certificats SSL, ce qui vous permet d’affiner les résultats de recherche de certificats spécifiques. Les filtres disponibles incluent le nom, la propriété et l’état du certificat SSL.
     ![Filtrage du certificat SSL](/help/implementing/cloud-manager/assets/filters-ssl-certificates.png)

## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce de Cloud Manager afin de pouvoir tester certaines fonctionnalités à venir.

### Apportez votre propre Git - avec prise en charge de GitLab et Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La fonctionnalité **Bring Your Own Git** a été étendue pour inclure la prise en charge de référentiels externes, tels que GitLab et Bitbucket. Cette nouvelle prise en charge s’ajoute à la prise en charge existante des référentiels GitHub privés et d’entreprise. Lorsque vous ajoutez ces nouveaux référentiels, vous pouvez également les lier directement à vos pipelines. Vous pouvez héberger ces référentiels sur des plateformes cloud publiques ou dans votre infrastructure ou cloud privés. Cette intégration élimine également la nécessité d’une synchronisation constante du code avec le référentiel d’Adobe et permet de valider les requêtes d’extraction avant de les fusionner dans une branche principale.

Les pipelines qui utilisent des référentiels externes (à l’exclusion de ceux hébergés par GitHub) et le **Déclencheur de déploiement** défini sur **Lors des modifications Git** démarrent désormais automatiquement.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actuellement, les contrôles de qualité du code des requêtes d’extraction prêts à l’emploi sont exclusifs aux référentiels hébergés par GitHub, mais une mise à jour permettant d’étendre cette fonctionnalité à d’autres fournisseurs Git est en cours.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.

## Correctifs

* Une protection a été ajoutée pour empêcher la suppression des domaines avec mappages de domaine actifs dans AEM Cloud Manager. Les utilisateurs qui tentent de supprimer de tels domaines reçoivent désormais un message d’erreur leur indiquant d’abord de supprimer le mappage de domaine avant de poursuivre la suppression du domaine. Ce workflow assure l’intégrité du domaine et évite les erreurs de configuration accidentelles. <!-- CMGR-63033 -->
* Les utilisateurs ne pouvaient pas souvent ajouter de nom de domaine ou mettre à jour un certificat SSL en raison d’un état incorrect associé dans les cas respectifs. <!-- CMGR-62816 -->


<!-- ## Known issues {#known-issues} -->