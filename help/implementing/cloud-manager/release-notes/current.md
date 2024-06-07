---
title: Notes de mise à jour de Cloud Manager 2024.6.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2024.6.0 dans AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: 5644e6f433b18408780e13057ba469e7c4926f78
workflow-type: ht
source-wordcount: '702'
ht-degree: 100%

---


# Notes de mise à jour de Cloud Manager 2024.6.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2024.6.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour obtenir les notes de mise à jour actuelle d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de mise à jour de Cloud Manager version 2024.6.0 dans AEM as a Cloud Service est prévue pour le 6 juin 2024. La prochaine version est prévue pour le 11 juillet 2024.

## Nouveautés {#what-is-new}

* Vous pouvez désormais [utiliser vos propres référentiels GitHub](/help/implementing/cloud-manager/managing-code/private-repositories.md) comme sources pour les pipelines full-stack et frontend.
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

### Collecte côté client via Real User Monitoring (RUM) {#rum}

Vous pouvez utiliser le [Service de données Real User Monitoring (RUM)](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) pour activer la collecte côté client pour AEM as a Cloud Service.

Le Service de données Real User Monitoring (RUM) offre un reflet plus précis des interactions des utilisateurs et utilisatrices, assurant une mesure fiable de l’engagement du site web. Il constitue une excellente opportunité d’obtenir des informations avancées sur les performances de votre page. Il est ainsi utile pour la clientèle qui utilise un réseau CDN géré ou non par Adobe. Pour les personnes utilisant un réseau CDN non géré par Adobe, la création de rapports automatisés sur le trafic peut désormais être activée, leur évitant ainsi d’avoir à partager n’importe quel rapport sur le trafic avec Adobe.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à `aemcs-rum-adopter@adobe.com` à partir de l’adresse e-mail associée à votre Adobe ID. Indiquez le nom de domaine des environnements de production, d’évaluation et de développement dans votre e-mail.  La disponibilité du programme d’adoption précoce de cette fonctionnalité est limitée.

### Tableau de bord d’audit de l’expérience {#experience-audit-dashboard}

[Le tableau de bord d’audit de l’expérience de Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) inclut une vue de tendance des scores de performances de votre page, ainsi que des informations et des recommandations pour vous aider à les améliorer. L’audit de l’expérience est inclus en tant qu’étape dans le pipeline de production de Cloud Manager.

Le tableau de bord tire parti de Google Lighthouse, un outil automatisé et open source permettant d’améliorer la qualité de vos applications web. Vous pouvez l’exécuter sur n’importe quelle page web, publique ou nécessitant une authentification. Il comporte des audits des performances, de l’accessibilité, des applications web progressives, de l’optimisation du moteur de recherche et plus encore.

Vous souhaitez tester le nouveau tableau de bord ? Pour commencer, envoyez un e-mail à l’adresse `aem-lighthouse-pilot@adobe.com` à partir de votre adresse e-mail associée à votre Adobe ID.
