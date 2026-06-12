---
title: Configuration d’un domaine personnalisé pour le niveau de diffusion
description: Découvrez comment configurer un domaine personnalisé pour le niveau de diffusion dans Adobe Cloud Manager.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: b24faf23435948a8f122223bf38227a0936bbeb5
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 3%

---


# Configuration d’un domaine personnalisé pour le niveau de diffusion{#configure-custom-domain}

Dans Adobe Cloud Manager, vous pouvez faire en sorte que votre site web se démarque en ajoutant un domaine personnalisé. Bien qu’AEM as a Cloud Service soit fourni avec un domaine par défaut, vous pouvez le personnaliser en fonction de vos besoins.

>[!NOTE]
>
>Les clients disposant de licences Dynamic Media Prime ou Dynamic Media Ultimate doivent utiliser la configuration de domaine personnalisé en libre-service disponible dans Cloud Manager.
>Pour plus d’informations, consultez la [documentation de Dynamic Media Prime et d’Ultimate](/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md#configure-custom-domain-in-delivery-tier).
>
>Les clients qui utilisent d’anciennes configurations de Dynamic Media dans lesquelles Dynamic Media avec OpenAPI est activé manuellement doivent suivre cette documentation. Pour ces configurations, le mappage de domaine personnalisé est effectué par le biais d’une demande d’assistance Adobe.

## Préparez-vous à démarrer

Assurez-vous de répondre aux exigences suivantes avant de démarrer le processus de configuration :

* Accès à Cloud Manager
* Déjà activé Dynamic Media avec OpenAPI dans votre environnement via un ticket d’assistance
* Certificat SSL de type EV ou OV pour le domaine utilisé dans le niveau de diffusion. Voir [&#x200B; Présentation des certificats SSL &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates) pour plus d’informations

## Configuration d’un domaine personnalisé dans le niveau de diffusion à l’aide de Cloud Manager

Exécutez les étapes suivantes dans Cloud Manager :

1. [Ajouter un certificat SSL géré par le client](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate#add-customer-managed-ssl-cert)

2. [Ajouter un nom de domaine personnalisé](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name#adding-cdn-settings)

Après avoir suivi les étapes ci-dessus, ouvrez un ticket d’assistance Adobe pour le mappage de domaine personnalisé. Adobe effectue le mappage de domaine dans le cadre du processus de prise en charge.