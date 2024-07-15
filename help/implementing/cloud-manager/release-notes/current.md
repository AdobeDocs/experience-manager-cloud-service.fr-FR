---
title: Notes de mise à jour de Cloud Manager 2024.6.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2024.6.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: 6ca376bda8055d62e35e13053ff21f861c12b292
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 100%

---


# Notes de mise à jour de Cloud Manager 2024.6.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2024.6.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de mise à jour de Cloud Manager version 2024.6.0 dans AEM as a Cloud Service est prévue pour le 6 juin 2024. La prochaine version est prévue pour le 18 juillet 2024.

## Nouveautés {#what-is-new}

* Vous pouvez désormais [utiliser vos propres référentiels GitHub](/help/implementing/cloud-manager/managing-code/private-repositories.md) comme sources pour les pipelines full-stack et front-end.
   * De plus, vous pouvez tirer parti des référentiels GitHub avec les [sous-modules git](/help/implementing/cloud-manager/managing-code/git-submodules.md), qui vous procurent un meilleur contrôle sur les pipelines générés automatiquement et utilisés pour la validation des demandes d’extraction. Vous pouvez également définir des comportements pour les mesures essentielles pendant la phase d’analyse du code.
   * [Vous avez également le choix](/help/implementing/cloud-manager/managing-code/github-check-config.md) de conserver l’historique des rapports sur GitHub, de nommer le pipeline et de définir les variables de pipeline en fonction de vos besoins.
* La fonction [Restaurer le contenu en libre-service](/help/operations/restore.md) fournit une restauration de sauvegarde pendant sept jours au maximum, ainsi que diverses fonctionnalités :
   * Restauration de sauvegarde ponctuelle des dernières 24 heures.
   * Restaurations de périodes fixes pendant sept jours au maximum.
* De [nouvelles règles OakPal](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-ui-content-package) ont été ajoutées à l’analyse de la qualité du code de Cloud Manager.
   * Chaque nouvelle règle ajoutée à partir de juin 2024 est irréversible.
   * Nous vous conseillons vivement de prendre en compte ces nouvelles règles dès que possible, car elles entraîneront l’échec des pipelines à compter de la version d’août 2024 de Cloud Manager.

## Programme d’adoption précoce {#early-adoption}

Pour avoir la possibilité de tester certaines fonctionnalités à venir, participez au programme d’adoption précoce d’Adobe.

### Assistance Edge Delivery Services dans Cloud Manager {#edge-delivery-services}

Si vous disposez d’Edge Delivery Services sous licence avec Adobe Experience Manager Sites, [vous pouvez désormais créer votre site avec Edge Delivery Services directement dans Cloud Manager](/help/implementing/cloud-manager/edge-delivery-services.md) et publier à l’aide d’une expérience guidée en libre-service.

Vous bénéficiez ainsi d’une expérience unifiée pour toutes vos propriétés AEM, ce qui garantit la cohérence avec tous les workflows critiques, notamment la gestion des noms de domaine, la gestion des certificats SSL et les mappages CDN.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `aemcs-cmedgedelsvs-program-adopter@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.

### Certificats de domaine validés (DV)

Cloud Manager vous permet désormais de [générer et gérer en libre-service des certificats SSL (DV) validés par domaine.](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) Vous bénéficiez ainsi de la solution la plus rapide, la plus simple et la plus économique pour créer un site web sécurisé destiné à votre entreprise en ligne.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `Grp-aemcs-dv-dert-adopter@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID.

<!-- RICK: REMOVED THIS SECTION AS PER EMAIL REQUEST TO DL-AEM-DOCS FROM SHWETA DUA, WEDNESDAY, JUNE 12, 2024 ### Client-Side Collection via Real Use Monitoring (RUM) {#rum}

You can leverage the [Real Use Monitoring (RUM) Data Service](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) to enable client-side collection for AEM as a Cloud Service.

Real Use Monitoring (RUM) Data Service offers a more precise reflection of user interactions, ensuring a reliable measure of website engagement. It is a great opportunity to gain advanced insights into your page performance. This is beneficial for customers who use either Adobe-managed CDN or non-Adobe managed CDN. For customers using a non-Adobe managed CDN, automated traffic reporting can now be enabled for them, thus removing the need to share any traffic report with Adobe.

If you are interested in testing this new feature and sharing your feedback, please send an email to `aemcs-rum-adopter@adobe.com` from the email address associated with your Adobe ID. Please include the domain name for production, stage, and dev environments in your email.  Availability of the early adopter program of this feature is limited.-->

### Tableau de bord d’audit de l’expérience {#experience-audit-dashboard}

[Le tableau de bord d’audit de l’expérience de Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) inclut une vue de tendance des scores de performances de votre page, ainsi que des informations et des recommandations pour vous aider à les améliorer. L’audit de l’expérience est inclus en tant qu’étape dans le pipeline de production de Cloud Manager.

Le tableau de bord tire parti de Google Lighthouse, un outil automatisé et open source permettant d’améliorer la qualité de vos applications web. Vous pouvez l’exécuter sur n’importe quelle page web, publique ou nécessitant une authentification. Il comporte des audits des performances, de l’accessibilité, des applications web progressives, de l’optimisation du moteur de recherche et plus encore.

Vous souhaitez tester le nouveau tableau de bord ? Pour commencer, envoyez un e-mail à l’adresse `aem-lighthouse-pilot@adobe.com` à partir de votre adresse e-mail associée à votre Adobe ID.
