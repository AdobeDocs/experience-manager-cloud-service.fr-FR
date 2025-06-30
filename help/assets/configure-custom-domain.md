---
title: Configuration d’un domaine personnalisé pour le niveau de publication
description: Découvrez comment configurer un domaine personnalisé pour le niveau de publication dans Adobe Cloud Manager.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 6%

---

# Configuration d’un domaine personnalisé pour le niveau de publication{#configure-custom-domain}

Dans Adobe Cloud Manager, vous pouvez faire en sorte que votre site web se démarque en ajoutant un domaine personnalisé. Bien qu’AEM as a Cloud Service soit fourni avec un domaine par défaut, vous pouvez le personnaliser en fonction de vos besoins.

## Avant de commencer

* Vous devez disposer d&#39;un certificat TLS ou SSL multi-SAN (Subject Alternative Name).
* Le certificat SSL doit comporter des SAN distincts par rapport au certificat mappé pour le niveau de publication dans le même domaine.
* La politique de certificat doit respecter la politique Validation étendue (EV) ou Validation de l’organisation (OV), et non la politique Validation de domaine (DV).


## Configuration d’un domaine personnalisé pour le niveau de publication

1. Accédez à **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL Présentation du programme]** > **[!UICONTROL Certificats SSL]** et ajoutez votre certificat SSL.
   ![image](/help/assets/assets/ssl-certificate.png)
Découvrez comment ajouter un [certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) dans Adobe Cloud Manager.

1. Après avoir ajouté le certificat SSL, ajoutez un domaine personnalisé. Cliquez sur **[!UICONTROL Paramètres du domaine]** et spécifiez le domaine personnalisé par rapport à l’option **[!UICONTROL Service de publication]**.
En savoir plus sur le [domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Ajoutez deux [enregistrements CNAME](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) dans votre enregistrement DNS correspondant aux domaines de publication.
La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.

1. Enregistrez un dossier d’assistance pour faciliter la configuration du domaine personnalisé, en veillant à ce qu’il soit dirigé vers le niveau de diffusion.

>[!NOTE]
>
>Ajoutez le domaine personnalisé à la liste des URL de redirection autorisées . La liste se trouve dans le client IMS pour le sélecteur de ressources.<br>Contactez l’équipe Adobe correspondante pour exécuter cette tâche en fournissant la chaîne de domaine personnalisée.
