---
title: Présentation des programmes Sandbox
description: Découvrez ce que sont les programmes Sandbox et en quoi ils diffèrent des programmes de production.
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 33%

---


# Présentation des programmes Sandbox {#sandbox-programs}

Découvrez ce que sont les programmes Sandbox et en quoi ils diffèrent des programmes de production.

## Présentation {#introduction}

Un programme Sandbox est généralement créé pour servir à la formation, à l’exécution de démonstrations, à l’activation ou aux preuves de concept (POC), ils ne sont donc pas destinés à transporter du trafic en direct.

Un programme Sandbox est l’un des deux types de programmes disponibles dans AEM Cloud Service, l’autre étant un [ programme de production ](introduction-production-programs.md). Voir [Présentation des programmes et des types de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) pour en savoir plus sur les types de programmes.

## Création automatique {#auto-creation}

Les programmes Sandbox proposent la création automatique. Chaque fois que vous [créez un programme Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md), Cloud Manager effectue automatiquement les opérations suivantes :

* Ajoute AEM Sites, Assets et Edge Delivery Services en tant que solutions par défaut à votre programme.

  ![Sélection de solutions et de modules complémentaires pour une sandbox](assets/sandbox-solutions-add-ons.png)

* Configurez un référentiel Git de projet avec un exemple de projet basé sur l’[archétype de projet AEM](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/developing/archetype/overview).
* Création d’un environnement de développement.
* Création d’un pipeline hors production qui se déploie vers l’environnement de développement.

Un programme Sandbox ne comporte qu’un seul environnement de développement.

## Notes et conditions d’utilisation {#usage-notes-conditions}

Étant donné qu’ils ne sont pas destinés au trafic en direct, les programmes Sandbox présentent certaines limites et conditions d’utilisation qui les différencient des programmes de production.

| Limitation/condition | Description |
| --- | --- |
| Aucun trafic en direct | Les programmes Sandbox ne sont pas destinés à transporter du trafic en direct et ne sont donc pas soumis aux [Engagements AEM as a Cloud Service](https://www.adobe.com/fr/legal/service-commitments.html). |
| Aucune mise à l’échelle automatique | Les environnements créés dans un programme Sandbox ne sont pas configurés pour la mise à l’échelle automatique. Par conséquent, ils ne conviennent pas aux tests de performances ou de charge. |
| Aucun domaine personnalisé ni Liste autorisée IP | Les [domaines personnalisés](/help/implementing/cloud-manager/custom-domain-names/introduction.md) et les [Listes autorisées IP](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) ne sont pas disponibles dans les programmes Sandbox. |
| Aucune région de publication supplémentaire | [Les régions de publication supplémentaires](/help/operations/additional-publish-regions.md) ne sont pas disponibles dans les programmes Sandbox. |
| Pas de SLA à 99,99 % | [99,99 % SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla) ne s’applique pas aux programmes sandbox. |
| Aucune mise en réseau avancée | Les [fonctionnalités de mise en réseau avancées](/help/security/configuring-advanced-networking.md) (par exemple, la configuration en libre-service de réseaux VPN, de ports non standards, d’adresses IP de sortie dédiées, etc.) ne sont pas disponibles dans les programmes Sandbox. |
| Aucune mise à jour automatique d’AEM | Les mises à jour AEM ne sont pas automatiquement transmises aux programmes Sandbox, mais peuvent être appliquées manuellement aux environnements dans votre programme Sandbox.<br>· Une mise à jour manuelle ne peut être exécutée que si l’environnement ciblé dispose d’un pipeline correctement configuré.<br>· Une mise à jour manuelle d’un environnement de production ou d’évaluation met automatiquement à jour l’autre. Le jeu d’environnements Production+Évaluation doit se trouver dans la même version AEM.<br>Voir [Mises à jour des versions d’AEM](/help/implementing/deploying/aem-version-updates.md) pour plus d’informations.<br>Voir [Mise à jour de l’environnement](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) pour savoir comment mettre à jour un environnement. |
| Aucun support technique | Comme un programme Sandbox est généralement créé pour les besoins de formation, à des fins de démonstration, d’activation ou de preuve de concept, l’assistance technique n’est pas disponible pour les problèmes rencontrés dans un programme Sandbox.<br>Si vous rencontrez des problèmes lors de la création et de la gestion de vos programmes Sandbox, ces problèmes relèvent de la compétence de l’assistance technique. |
| Mise en veille et suppression | Les environnements d’un programme Sandbox sont automatiquement mis en veille après huit heures d’inactivité. Les environnements Sandbox sont supprimés après six mois de mise en veille continus.<br>Voir [Mise en veille et réactivation d’environnements Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-environments.md) pour plus d’informations sur la réactivation d’environnements et la suppression automatique de sandbox. |
