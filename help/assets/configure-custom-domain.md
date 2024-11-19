---
title: Configuration d’un domaine personnalisé pour le niveau Publish
description: Découvrez comment configurer un domaine personnalisé pour le niveau de publication dans Adobe Cloud Manager.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 11%

---

# Configuration d’un domaine personnalisé pour le niveau de publication{#configure-custom-domain}

| [Bonnes pratiques de recherche](/help/assets/search-best-practices.md) | [Bonnes pratiques relatives aux métadonnées](/help/assets/metadata-best-practices.md) | [Hub de contenus](/help/assets/product-overview.md) | [Fonctionnalités Dynamic Media avec OpenAPI](/help/assets/dynamic-media-open-apis-overview.md) | [Documentation de développement pour AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Le guide des fonctionnalités de Dynamic Media avec OpenAPI est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant Adobe Acrobat AI pour répondre à vos requêtes.
>
>[!BADGE Dynamic Media avec OpenAPI Feature PDF ]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Dans Adobe Cloud Manager, vous pouvez faire ressortir votre site web en ajoutant un domaine personnalisé. AEM as a Cloud Service est fourni avec un domaine par défaut. Vous pouvez le personnaliser selon vos besoins.

## Avant de commencer

* Vous devez disposer d’un certificat TLS ou SSL multi-SAN (subject Alternative Name).
* Le certificat SSL doit avoir des SAN distincts par rapport au certificat mappé pour le niveau de publication dans le même domaine.
* La stratégie de certificat doit se conformer à la politique Validation étendue (EV) ou Validation d’organisation (OV), et non à la politique Validation de domaine (DV).


## Configuration d’un domaine personnalisé pour le niveau de publication

1. Accédez à **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL Aperçu du programme]** > **[!UICONTROL Certificats SSL]** et ajoutez votre certificat SSL.
   ![image](/help/assets/assets/ssl-certificate.png)
Découvrez comment ajouter le [certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) dans Adobe Cloud Manager.

1. Après avoir ajouté le certificat SSL, ajoutez un domaine personnalisé. Cliquez sur **[!UICONTROL Paramètres de domaine]** et spécifiez le domaine personnalisé par rapport à l’option **[!UICONTROL Service Publish]** .
En savoir plus sur [domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Ajoutez deux [enregistrements CNAME](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) dans votre enregistrement DNS correspondant aux domaines de publication.
La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.

1. Consignez un cas de support pour faciliter la configuration du domaine personnalisé, en vous assurant qu’il dirige vers le niveau de diffusion.

>[!NOTE]
>
Ajoutez le domaine personnalisé à la liste des URL de redirection autorisées. La liste se trouve dans le client IMS pour le sélecteur de ressources.<br>Coordination avec l’équipe d’Adobe respective pour exécuter cette tâche en fournissant la chaîne de domaine personnalisée.
