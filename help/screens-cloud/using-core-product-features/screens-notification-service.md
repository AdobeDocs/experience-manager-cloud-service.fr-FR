---
title: Service de notification Screens dans Screens as a Cloud Service
description: Cette page décrit comment configurer le service de notification dans Screens as a Cloud Service.
index: true
source-git-commit: 81ce7954479366e40b47325577e1450f3d7a4c29
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 4%

---


# Service de notification Screens {#notification-service}

## Présentation {#introduction}

### Vue d’ensemble

Le service de notifications AEM Screens permet aux administrateurs de recevoir un courrier électronique si un lecteur AEM Screens ne effectue pas de test ping pendant une période configurable.

### Comment configurer

Sur AEM Screens Cloud, les clients peuvent demander des alertes sur l’état d’inactivité d’un appareil en créant un ticket d’assistance avec les informations suivantes :

* Nom du client
* Identifiant de l&#39;organisation IMS
* Fréquence des planifications : indiquez une heure ou une fréquence en heures (1, par exemple) à laquelle ce moniteur doit envoyer des emails.
* Délai d’expiration du ping : spécifie l’intervalle en minutes après lequel un appareil doit être considéré comme inaccessible.
* ID de message électronique : ID de message électronique où le rapport sera envoyé