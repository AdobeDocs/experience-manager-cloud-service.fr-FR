---
title: Introduction - Gestion des certificats SSL
description: Introduction - Gestion des certificats SSL
translation-type: tm+mt
source-git-commit: 5ebe94c8562b952521effa3b67267c3eab925d16
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Présentation {#introduction}

Cloud Manager permet aux clients d’installer des certificats SSL en libre-service via l’interface utilisateur de Cloud Manager. Cloud Manager utilise un service Platform TLS pour gérer les certificats SSL et les clés privées détenues par les clients et généralement obtenues auprès d’autorités de certification tierces, par exemple Let’s Encrypt.

>[!IMPORTANT]
>Cloud Manager ne fournit pas de certificats SSL ni de clés privées. Ils doivent être obtenus auprès d&#39;autorités de certification tierces. Consultez [Obtention d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) pour en savoir plus.

>[!NOTE]
>aem en tant que Cloud Service ne prend en charge que les sites https sécurisés. Les clients disposant de plusieurs domaines personnalisés ne souhaitent pas télécharger de certificat chaque fois qu’ils ajoutent un domaine. Par conséquent, ces clients bénéficieront d’un certificat comportant plusieurs domaines.

Cloud Manager prend en charge les exigences de certificat SSL client suivantes :

* Un certificat SSL peut être utilisé par plusieurs Environnements, c’est-à-dire, ajouter une fois et utiliser plusieurs fois.
* Chaque Environnement de Cloud Manager peut utiliser plusieurs certificats.
* Une clé privée peut émettre plusieurs certificats SSL.
* Chaque certificat contient généralement plusieurs domaines.
* Le service TLS de plate-forme achemine les demandes vers le service CDN du client en fonction du certificat SSL utilisé pour s’arrêter et du service CDN qui héberge ce domaine.

A l’aide de la page Certificats SSL de l’interface utilisateur de Cloud Manager, un utilisateur disposant d’autorisations peut exécuter plusieurs tâches pour gérer des certificats SSL pour un programme :

* Ajouter un certificat SSL
* Affichage, mise à jour ou remplacement d’un certificat SSL
   >[!NOTE]
   >Ces actions vous permettent de vue des détails ou de remplacer un certificat qui arrive à expiration.
* Suppression d’un certificat SSL