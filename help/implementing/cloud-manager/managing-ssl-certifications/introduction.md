---
title: Introduction – Gestion des certificats SSL
description: Introduction – Gestion des certificats SSL
exl-id: 0d41723c-c096-4882-a3fd-050b7c9996d8
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 100%

---

# Présentation {#introduction}

Cloud Manager permet aux clients d’installer des certificats SSL en libre-service via l’interface utilisateur de Cloud Manager. Cloud Manager utilise un service Platform TLS pour gérer les certificats SSL et les clés privées détenues par les clients et généralement obtenues auprès d’autorités de certification tierces, telles que *Let’s Encrypt*.

## Points importants {#important-considerations}


* Cloud Manager ne fournit pas de certificats SSL ni de clés privées. Ils doivent être obtenus auprès d’autorités de certification tierces. Consultez [Obtention d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/get-ssl-certificate.md) pour en savoir plus.

* AEM as a Cloud Service ne prend en charge que les sites sécurisés `https`. Les clients disposant de plusieurs domaines personnalisés ne souhaitent pas télécharger un certificat à chaque fois qu’ils ajoutent un domaine. Ces clients obtiendront ainsi un certificat comportant plusieurs domaines.

Cloud Manager respecte les exigences suivantes en matière de certificat SSL client :

* Un certificat SSL peut être utilisé par plusieurs environnements, c’est-à-dire ajouter une fois et utiliser plusieurs fois.
* Chaque environnement Cloud Manager peut utiliser plusieurs certificats.
* Une clé privée peut émettre plusieurs certificats SSL.
* Chaque certificat contient généralement plusieurs domaines.
* Le service Platform TLS achemine les requêtes vers le service CDN du client en fonction du certificat SSL utilisé pour s’arrêter et du service CDN qui héberge ce domaine.

La page Certificats SSL de l’interface utilisateur de Cloud Manager permet à un utilisateur disposant d’autorisations d’exécuter plusieurs tâches pour gérer des certificats SSL pour un programme :

* [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)
* [Affichage, mise à jour ou remplacement d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/view-update-replace-ssl-certificate.md)
   >[!NOTE]
   >Ces actions vous permettent de consulter des détails ou de remplacer un certificat qui arrive à expiration.
* [Suppression d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/delete-ssl-certificate.md)
