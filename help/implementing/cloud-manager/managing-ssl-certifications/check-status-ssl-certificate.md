---
title: Vérification du statut d’un certificat SSL – Gestion des certificats SSL
description: Vérification du statut d’un certificat SSL – Gestion des certificats SSL
translation-type: tm+mt
source-git-commit: ddee11fdfa8cadfcd63472fd3c94cd8af555c856
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 69%

---


# Vérification du statut d’un certificat SSL {#checking-status-an-ssl-certificate}

L’état de vos certificats SSL se comprend d’un seul coup d’oeil grâce à la page de certificat SSL.

Vous pouvez identifier le statut d’un certificat SSL d’après les modèles de couleurs suivants :

* Le **vert**
indique que votre certificat est valide pendant au moins 60 jours dans le futur.

* L’**orange**
indique que votre certificat doit expirer dans moins de 60 jours. Il est temps de vous assurer que vous disposez d’un plan de renouvellement de votre certificat afin de le remplacer via l’interface utilisateur de Cloud Manager et d’éviter d’éventuelles interruptions d’accès au site. Cloud Manager envoie régulièrement des notifications dans l’interface utilisateur pour vous avertir d’une expiration imminente du certificat.

* Le **rouge**
indique que malgré plusieurs notifications, votre certificat SSL a expiré.

## Configurations CDN préexistantes pour les Listes autorisées IP {#pre-existing-cdn}

Les clients disposant d’environnements qui incluent des configurations CDN préexistantes pour les Listes autorisées IP, les certificats SSL ou les noms de domaine personnalisés voient le message suivant dans les pages de détails **Liste autorisée IP** et **Environnement**.

![](/help/implementing/cloud-manager/assets/ip-allow-list-1.png)

>[!NOTE]
>Pour afficher et gérer les configurations préexistantes, elles doivent être ajoutées via l’interface utilisateur, comme le montre la figure ci-dessous.

![](/help/implementing/cloud-manager/assets/ip-allow-list-2.png)