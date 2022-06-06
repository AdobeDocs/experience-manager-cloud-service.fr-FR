---
title: 'Présentation des programmes Sandbox '
description: Découvrez en quoi les programmes Sandbox diffèrent des programmes de production.
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
source-git-commit: b74a0dbb1c9fdb74941f7b71bed9215853b63666
workflow-type: ht
source-wordcount: '413'
ht-degree: 100%

---


# Présentation des programmes Sandbox {#sandbox-programs}

Découvrez en quoi les programmes Sandbox diffèrent des programmes de production.

## Présentation {#introduction}

Un programme Sandbox est généralement créé pour servir à la formation, à l’exécution de démonstrations, à l’activation ou aux preuves de concept (POC), ils ne sont donc pas destinés à transporter du trafic en direct.

Le programme Sandbox est l’un des deux types de programmes disponibles dans AEM Cloud Service, l’autre étant le [programme de production.](introduction-production-programs.md) Consultez le document [Présentation des programmes et des types de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) pour en savoir plus sur les types de programmes.

## Création automatique {#auto-creation}

Les programmes Sandbox proposent la création automatique. Chaque fois que vous créez automatiquement un programme Sandbox Cloud Manager :

* Ajout d’AEM Sites et d’AEM Assets en tant que solutions dans votre programme.
* Configuration d’un référentiel git de projet avec un exemple de projet basé sur l’[archétype de projet AEM.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr)
* Création d’un environnement de développement.
* Création d’un pipeline hors production qui se déploie vers l’environnement de développement.

Un programme Sandbox ne comporte qu’un seul environnement de développement.

## Restrictions et conditions {#limitations}

Étant donné qu’ils ne sont pas destinés au trafic en direct, les programmes Sandbox présentent certaines limites et conditions d’utilisation qui les différencient des programmes de production.

### Aucun trafic en direct {#live-traffic}

Les programmes Sandbox ne sont pas destinés à transporter du trafic en direct et ne sont donc pas soumis aux [Engagements AEM as a Cloud Service.](https://www.adobe.com/fr/legal/service-commitments.html)

### Aucune mise à l’échelle automatique {#auto-scaling}

Les environnements créés dans un programme Sandbox ne sont pas configurés pour la mise à l’échelle automatique. Par conséquent, ils ne conviennent pas aux tests de performances ou de charge.

### Aucun domaine personnalisé ni liste d’adresses IP autorisées {#ip-allow}

Les domaines personnalisés et les listes d’adresses IP autorisées ne sont pas disponibles dans les programmes Sandbox.

### Mises à jour AEM manuelles {#updates}

Les mises à jour AEM ne sont pas automatiquement transmises aux programmes Sandbox, mais peuvent être appliquées manuellement aux environnements dans votre programme Sandbox.

* Une mise à jour manuelle ne peut être exécutée que si l’environnement ciblé dispose d’un pipeline correctement configuré.
* Une mise à jour manuelle d’un environnement de production met automatiquement à jour l’environnement d’évaluation, et vice-versa. Le jeu d’environnements Production+Évaluation doit se trouver dans la même version AEM.

Consultez le document [Mises à jour des versions d’AEM](/help/implementing/deploying/aem-version-updates.md) pour plus d’informations.

Consultez le document [Mise à jour de l’environnement](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) pour savoir comment mettre à jour un environnement.

### Mise en veille et suppression {#hibernation}

Les environnements d’un programme Sandbox sont automatiquement mis en veille après 8 heures d’inactivité. Une fois
mis en veille, ils peuvent être réactivés manuellement.

Les programmes Sandbox sont supprimés après 6 mois de mise en veille continue, après quoi ils peuvent être recréés.

Pour plus d’informations, consultez [Mise en veille et réactivation d’environnements Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-environments.md).
