---
title: Configuration d’un domaine personnalisé pour le niveau de publication
description: Découvrez comment configurer un domaine personnalisé pour le niveau de publication dans Adobe Cloud Manager.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 20%

---

# Configuration d’un domaine personnalisé pour le niveau de publication{#configure-custom-domain}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouvelle</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Fonctionnalités Dynamic Media avec OpenAPI</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

>[!AVAILABILITY]
>
>Le guide de Dynamic Media avec fonctionnalités OpenAPI est désormais disponible au format PDF. Téléchargez l’intégralité du guide et utilisez l’assistant IA Adobe Acrobat pour répondre à vos requêtes.
>
>[!BADGE Guide PDF de Dynamic Media avec fonctionnalités OpenAPI]{type=Informative url="https://helpx.adobe.com/content/dam/help/fr/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

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
Ajoutez le domaine personnalisé à la liste des URL de redirection autorisées . La liste se trouve dans le client IMS pour le sélecteur de ressources.<br>Contactez l’équipe Adobe correspondante pour exécuter cette tâche en fournissant la chaîne de domaine personnalisée.
