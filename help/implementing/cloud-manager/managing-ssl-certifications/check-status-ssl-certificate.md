---
title: Vérification de l’état d’un certificat SSL - Gestion des certificats SSL
description: Vérification de l’état d’un certificat SSL - Gestion des certificats SSL
translation-type: tm+mt
source-git-commit: e27e5302802e68dce2a5713626950896bb35420a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# Vérification du statut d’un certificat SSL {#checking-status-an-ssl-certificate}

L’état de vos certificats SSL peut être compris d’un seul coup d’oeil à partir de la page de certificat SSL ou de la page de détails de l’Environnement.

Vous pouvez identifier l’état d’un certificat SSL à partir des modèles de couleurs suivants :

* **Vert** Indique que votre certificat est valide pendant au moins 60 jours dans le futur.

* **Orange** Indique que votre certificat doit expirer dans moins de 60 jours. Il est temps de vous assurer que vous disposez d’un plan pour renouveler votre certificat et le remplacer via l’interface utilisateur de Cloud Manager afin d’éviter d’éventuels accès au site ou interruptions de service. Cloud Manager envoie régulièrement des notifications dans l’interface utilisateur pour vous avertir d’une expiration imminente du certificat.

* **Rouge** Indique que, malgré plusieurs notifications, votre certificat SSL a expiré.