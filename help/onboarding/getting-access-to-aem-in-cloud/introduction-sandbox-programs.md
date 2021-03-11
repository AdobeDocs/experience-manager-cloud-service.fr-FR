---
title: 'Présentation des Programmes Sandbox '
description: 'Présentation des Programmes Sandbox '
translation-type: tm+mt
source-git-commit: d98e3ba930690627bfbe9b90ce5cb93328c30503
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 79%

---


# Introduction aux Programmes Sandbox {#sandbox-programs}

## Présentation {#introduction}

Un programme Sandbox est l&#39;un des deux types de programmes disponibles dans AEM Cloud Service, l&#39;autre étant un programme de production.

Un sandbox est généralement créé pour servir à la formation, à l’exécution de démonstrations, à l’activation ou aux preuves de concept (POC). Ces tâches ne sont pas destinées à transporter du trafic en direct. Elles ne sont pas soumises aux [engagements d’AEM as a Cloud Service](https://www.adobe.com/fr/legal/service-commitments.html).

Les environnements créés dans un sandbox ne sont pas configurés pour la mise à l’échelle automatique. Par conséquent, ces environnements ne conviennent pas aux essais de performances ou de charge.

Les programmes Sandbox comprennent les sites et les ressources et sont automatiquement renseignés avec un référentiel Git, un environnement de développement et un pipeline hors production. Le référentiel Git est renseigné avec un exemple de projet basé sur l’archétype de projet AEM.

Consultez [Présentation des programmes et des types de programmes](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md) pour en savoir plus sur les types de programmes.

### Attributs des programmes Sandbox {#attributes-sandbox}

Les programmes Sandbox possèdent les attributs suivants :

1. **Création de programme :** la création du programme Sandbox inclut des éléments automatiques :
   * Configuration d’un projet avec un exemple de code et de contenu
   * Création d’un environnement de développement
   * Création d’un canal hors production se déployant vers l’environnement de développement (déploiement de branche principale vers l’environnement de développement)

1. **Solutions :** les programmes Sandbox incluent AEM Sites et Assets.

1. **Mises à jour AEM :** les mises à jour AEM peuvent être appliquées manuellement aux environnements d’un programme Sandbox et ne sont pas automatiquement exécutées.
Pour plus d&#39;informations, consultez [AEM mises à jour des Environnements Sandbox](/help/onboarding/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md#aem-updates-sandbox).

1. **Veille :** les environnements d’un programme Sandbox sont automatiquement mis en veille si aucune activité n’est détectée pendant une certaine période. Les environnements mis en veille peuvent être réactivés manuellement.
Pour plus d’informations, voir [Mise en veille et réactivation d’environnements Sandbox](/help/onboarding/getting-access-to-aem-in-cloud/hibernating-de-hibernating-sandbox-environments.md).