---
title: Vérification du statut d’un certificat SSL – Gestion des certificats SSL
description: Vérification du statut d’un certificat SSL – Gestion des certificats SSL
exl-id: 59d81356-2fa9-43db-bfa5-c2896c530eaa
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 58%

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

## Configurations de réseau de diffusion de contenu préexistantes pour les Listes autorisées IP {#pre-existing-cdn}

Les clients avec des environnements qui incluent des configurations CDN préexistantes pour les Listes autorisées IP, les certificats SSL ou les noms de domaine personnalisés verront le message suivant dans la **Liste autorisée IP** et la page de détails **Environnement**. Le message affiché dans l’interface utilisateur disparaît une fois que le client a entièrement migré toutes les configurations d’environnement préexistantes via l’interface utilisateur et il peut prendre 1 à 2 jours ouvrables pour que le message disparaisse.

>[!NOTE]
>Pour afficher et gérer les configurations préexistantes, elles doivent être ajoutées via l’interface utilisateur. Pour plus d’informations, voir [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) .

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
