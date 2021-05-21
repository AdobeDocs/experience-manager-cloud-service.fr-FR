---
title: 'Présentation des programmes Sandbox '
description: Présentation des programmes Sandbox
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
source-git-commit: 3b57acc47dd60d050ceebebb12bd9080b7fc5cf5
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 88%

---

# Présentation des programmes Sandbox {#sandbox-programs}

## Présentation {#introduction}

Un programme Sandbox est l’un des deux types de programmes disponibles dans AEM Cloud Service, l’autre étant un programme de production.

Un sandbox est généralement créé pour servir à la formation, à l’exécution de démonstrations, à l’activation ou aux preuves de concept (POC). Ces tâches ne sont pas destinées à transporter du trafic en direct. Elles ne sont pas soumises aux [engagements d’AEM as a Cloud Service](https://www.adobe.com/fr/legal/service-commitments.html).

Les environnements créés dans un sandbox ne sont pas configurés pour la mise à l’échelle automatique. Par conséquent, ils ne conviennent pas aux tests de performances ou de charge.

Les programmes Sandbox comprennent les sites et les ressources et sont automatiquement renseignés avec un référentiel Git, un environnement de développement et un pipeline hors production.  Le référentiel Git est renseigné avec un exemple de projet basé sur l’archétype de projet AEM.

Consultez [Présentation des programmes et des types de programmes](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md) pour en savoir plus sur les types de programmes.

### Attributs des programmes Sandbox {#attributes-sandbox}

Les programmes Sandbox possèdent les attributs suivants :

1. **Création de programme :** la création du programme Sandbox inclut des éléments automatiques :
   * Configuration d’un projet avec un exemple de code et de contenu
   * Création d’un environnement de développement
   * Création d’un canal hors production se déployant vers l’environnement de développement (déploiement de branche principale vers l’environnement de développement)

1. **Solutions :** les programmes Sandbox incluent AEM Sites et Assets.

1. **Mises à jour AEM :** les mises à jour AEM peuvent être appliquées manuellement aux environnements d’un programme Sandbox et ne sont pas automatiquement exécutées.
Pour plus d’informations, consultez [Mises à jour AEM des environnements Sandbox](/help/onboarding/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md#aem-updates-sandbox).

1. **Veille :** les environnements d’un programme Sandbox sont automatiquement mis en veille si aucune activité n’est détectée pendant une certaine période. Les environnements de test sont placés dans le noeud de veille après 8 heures d’inactivité, après quoi ils peuvent être réactivés. Les environnements mis en veille peuvent être réactivés manuellement.
Pour plus d’informations, voir [Mise en veille et réactivation d’environnements Sandbox](/help/onboarding/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md).

1. **Suppression** : Les environnements de test sont supprimés après 6 mois de mise en veille continue, après quoi ils peuvent être recréés.
