---
title: Vérification du statut d’un certificat SSL – Gestion des certificats SSL
description: Vérification du statut d’un certificat SSL – Gestion des certificats SSL
exl-id: 59d81356-2fa9-43db-bfa5-c2896c530eaa
source-git-commit: 828490e12d99bc8f4aefa0b41a886f86fee920b4
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 98%

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

## Configurations de réseau de diffusion de contenu préexistantes {#pre-existing-cdn}

Les clients disposant d’environnements qui incluent des configurations CDN préexistantes pour les listes autorisées d’adresses IP, des certificats SSL ou des noms de domaines personnalisés voient le message suivant dans les pages de détails **Liste autorisée d’adresses IP** et **Environnement**. Le message affiché dans l’interface utilisateur disparaît une fois que le client a effectué la migration complète de toutes les configurations d’environnement préexistantes via l’interface utilisateur et il peut s’écouler entre 1 et 2 jours ouvrés avant que le message ne disparaisse.

>[!NOTE]
>Pour afficher et gérer les configurations préexistantes, elles doivent être ajoutées via l’interface utilisateur. Consultez la section [Obtention d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) pour plus d’informations.

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
