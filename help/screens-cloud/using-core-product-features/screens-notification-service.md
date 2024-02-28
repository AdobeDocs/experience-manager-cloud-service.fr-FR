---
title: Service de notification Screens dans Screens as a Cloud Service
description: Cette page décrit comment configurer le service de notification dans Screens as a Cloud Service.
index: true
exl-id: 74215a70-45c8-4b7f-ba30-60c332de07e9
source-git-commit: 69798b1ac3758d37c4e2f480ccc23bae24d6a814
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 5%

---

# Service de notification Screens {#notification-service}

## Introduction {#introduction}

### Vue d’ensemble

Le service de notifications AEM Screens permet aux administrateurs de recevoir un rapport avec une liste de tous les lecteurs AEM Screens qui n’ont pas effectué de test ping pendant une période configurable sur un email.

### Comment configurer

Sur AEM Screens Cloud, les clients peuvent demander un rapport sur l’état d’inactivité des périphériques en créant un ticket d’assistance avec les informations suivantes :

* Nom du client
* Identifiant de l&#39;organisation IMS
* Fréquence des planifications : indiquez une heure ou une fréquence (par exemple, 1) à laquelle ce moniteur doit envoyer des emails.
* Délai d’expiration du ping : spécifie l’intervalle en minutes après lequel un appareil doit être considéré comme inaccessible.
* ID de message électronique : ID de message électronique où le rapport sera envoyé

>[!NOTE]
>Le lecteur ne sera signalé que si l’appareil n’a pas envoyé de ping pendant le délai d’expiration du ping donné au moment de la génération de l’email.

### Exemple de cas d’utilisation

Si vous définissez l’heure du rapport sur 5 h et le délai d’expiration du ping sur 1 heure, si votre périphérique Screens ne effectue pas de test ping entre 4 h et 5 h, vous recevrez une notification par e-mail confirmant l’inactivité du périphérique.
