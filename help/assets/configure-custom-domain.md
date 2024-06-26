---
title: Configurer un domaine personnalisé pour le niveau de publication
description: Découvrez comment configurer un domaine personnalisé pour le niveau publication dans Adobe Cloud Manager.
source-git-commit: f6c0e8e5c1d7391011ccad5aa2bad4a6ab7d10c3
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 6%

---


# Configurer un domaine personnalisé pour le niveau de publication{#configure-custom-domain}

Dans Adobe Cloud Manager, vous pouvez faire ressortir votre site web en ajoutant un domaine personnalisé. AEM as a Cloud Service est fourni avec un domaine par défaut. Vous pouvez le personnaliser selon vos besoins.

## Avant de commencer

* Vous devez disposer d’un certificat TLS ou SSL multi-SAN (subject Alternative Name).
* Le certificat SSL doit avoir des SAN distincts par rapport au certificat mappé pour le niveau de publication dans le même domaine.
* La stratégie de certificat doit se conformer à la politique Validation étendue (EV) ou Validation d’organisation (OV), et non à la politique Validation de domaine (DV).


## Ajouter un domaine personnalisé

Pour configurer un domaine personnalisé pour le niveau de publication, procédez comme suit :

1. Accédez à **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL Aperçu du programme]** > **[!UICONTROL Certificats SSL]**et ajoutez votre certificat SSL.
   ![image](/help/assets/assets/ssl-certificate.png)
Découvrez comment ajouter [Certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) dans Adobe Cloud Manager.

1. Après avoir ajouté le certificat SSL, ajoutez un domaine personnalisé. Cliquez sur **[!UICONTROL Paramètres de domaine]** et spécifiez le domaine personnalisé par rapport à la propriété **[!UICONTROL Service Publish]** .
En savoir plus sur [domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

1. Ajouter 2 [Enregistrements CNAME](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) dans votre enregistrement DNS correspondant aux domaines de publication.
La vérification DNS peut prendre quelques heures en raison des délais de propagation du DNS.

1. Consignez un cas de support pour faciliter la configuration du domaine personnalisé, en vous assurant qu’il dirige vers le niveau de diffusion.

>[!NOTE]
>
> Veillez à ajouter le domaine personnalisé à la liste des URL de redirection autorisées dans le client IMS pour le sélecteur de ressources.<br>Coordination avec l’équipe d’Adobe respective afin d’exécuter cette tâche en fournissant la chaîne de domaine personnalisée.
