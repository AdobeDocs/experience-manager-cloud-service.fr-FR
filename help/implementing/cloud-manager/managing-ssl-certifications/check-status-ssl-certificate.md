---
title: Vérification du statut d’un certificat SSL – Gestion des certificats SSL
description: Vérification du statut d’un certificat SSL – Gestion des certificats SSL
translation-type: tm+mt
source-git-commit: f426a9a653a3a3ae06abdbd2262e5d8f4beff277
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 87%

---


# Vérification du statut d’un certificat SSL {#checking-status-an-ssl-certificate}

L’état de vos certificats SSL peut être compris d’un seul coup d’oeil à partir de la page de certificat SSL.

Vous pouvez identifier le statut d’un certificat SSL d’après les modèles de couleurs suivants :

* Le **vert**
indique que votre certificat est valide pendant au moins 60 jours dans le futur.

* L’**orange**
indique que votre certificat doit expirer dans moins de 60 jours. Il est temps de vous assurer que vous disposez d’un plan de renouvellement de votre certificat afin de le remplacer via l’interface utilisateur de Cloud Manager et d’éviter d’éventuelles interruptions d’accès au site. Cloud Manager envoie régulièrement des notifications dans l’interface utilisateur pour vous avertir d’une expiration imminente du certificat.

* Le **rouge**
indique que malgré plusieurs notifications, votre certificat SSL a expiré.