---
title: Service de notification Screens dans Screens as a Cloud Service
description: Cette page décrit comment configurer le service de notification dans Screens as a Cloud Service.
index: true
exl-id: 74215a70-45c8-4b7f-ba30-60c332de07e9
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: 81f85045212ca6fd92f2b665aeceaa0d4b92318c
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 5%

---

# Service de notification Screens {#notification-service}

## Présentation {#introduction}

### Vue d’ensemble

Le service de notifications AEM Screens permet aux administrateurs de recevoir un rapport avec une liste de tous les lecteurs AEM Screens qui n’ont pas envoyé de ping pendant une période configurable sur un e-mail.

### Comment configurer

Sur AEM Screens Cloud, les clients peuvent demander un rapport sur le statut d’inactivité de l’appareil en créant un ticket d’assistance avec les informations suivantes :

* Nom du client
* ID d’organisation IMS
* Fréquence de planification : indiquez l’heure ou la fréquence, en heures (par exemple, 1) à laquelle ce moniteur doit envoyer des e-mails.
* Délai d’expiration du ping : indique l’intervalle en minutes après lequel un appareil doit être considéré comme inaccessible.
* Email ID(s) : Email id(s) où le rapport sera envoyé

>[!NOTE]
>Le lecteur ne sera signalé dans les e-mails que si l’appareil n’a pas envoyé de ping pour la temporisation de ping donnée au moment de la génération de l’e-mail.

### Exemple de cas d’utilisation

Si vous définissez l’heure du rapport sur 5 heures et le délai d’expiration du ping sur 1 heure, si votre appareil Screens n’effectue pas de ping entre 4 :00 et 5 :00, vous recevrez une notification par e-mail confirmant l’inactivité de l’appareil.
