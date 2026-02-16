---
title: Configuration de Dynamic Media
description: Pour installer Dynamic Media, vous devez configurer Dynamic Media et gérer les paramètres prédéfinis d’image et de visionneuse.
contentOwner: Rick Brough
feature: Configuration,Viewer Presets,Image Presets,Dynamic Media
role: Admin,User
exl-id: 83b70b17-7ee3-41cb-be90-c92ca161660e
source-git-commit: 8a8f3d7b17d79791a3ebf6b583ffcccfcf214470
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 60%

---

# Configuration de Dynamic Media {#setting-up-dynamic-media}

{{work-with-dynamic-media}}

[Dynamic Media](https://business.adobe.com/fr/products/experience-manager/assets/dynamic-media.html) facilite la gestion des ressources visuelles de marchandisage et de marketing à la demande, automatiquement dimensionnées pour une utilisation sur le web, les appareils mobiles et les réseaux sociaux. À partir d’un ensemble de ressources de sources originales, Dynamic Media génère et diffuse en temps réel plusieurs variantes d’un même contenu enrichi par le biais de son réseau mondial et évolutif, aux performances optimisées.

<!-- OBSOLETE UNTIL THE INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE

>[!NOTE]
>
>This documentation describes Dynamic Media capabilites, which are integrated directly into [!DNL Experience Manager]. If you are using Dynamic Media Classic (previously called Scene7) integrated into [!DNL Experience Manager], see [Dynamic Media Classic integration documentation](/help/sites-cloud/administering/integrating-scene7.md).
>
>See [Dual Use Scenario](/help/sites-cloud/administering/integrating-scene7.md#dual-use-scenario) for times when you may want to use [!DNL Experience Manager] integrated with Dynamic Media Classic along with Dynamic Media.

-->

Si vous administrez Dynamic Media, les rubriques suivantes peuvent vous intéresser :

* [Configurez Dynamic Media](config-dm.md)
* [Gestion des paramètres d’image prédéfinis](managing-image-presets.md)
* [Gestion des paramètres de visionneuse prédéfinis](managing-viewer-presets.md)
* [Résolution des problèmes liés à Dynamic Media](troubleshoot-dm.md)

Voir aussi les rubriques suivantes :

* [Codage vidéo et profils vidéo](video-profiles.md)
* [Profils d’image](image-profiles.md)

>[!NOTE]
>
>**Si vous effectuez une mise à niveau :**
>
>* Après la mise en service d’Adobe [!DNL Experience Manager], toutes les ressources que vous chargez sont automatiquement activées pour Dynamic Media (à moins que cela n’ait été explicitement désactivé par votre administrateur système). Si vous utilisez une instance de [!DNL Experience Manager] mise à niveau et que Dynamic Media est nouveau pour vous, vous devrez peut-être retraiter vos ressources pour les rendre compatibles avec Dynamic Media. Voir [Retraitement des ressources dans un dossier](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).


## Mise à jour DNS unique requise pour les renouvellements de certificat Dynamic Media {#dns-update-dynamic-media-certificate-renewals}

Si votre domaine utilise un enregistrement DNS CAA (Certification Authority Authorization), vous devez autoriser DigiCert pour permettre le renouvellement continu des certificats TLS/SSL utilisés par les noms d’hôtes Dynamic Media.

Ajoutez l’enregistrement CAA suivant à la racine (apex) de votre domaine :

```
<yourdomain> CAA 0 issue "digicert.com"
```

Il s’agit d’un changement unique.

Vous pouvez vérifier si un enregistrement CAA existe à l’aide des outils de votre fournisseur DNS ou d’un utilitaire de recherche [CAA](https://caatest.co.uk/).

Si un enregistrement CAA existe et que DigiCert n’est pas autorisé, le renouvellement du certificat échoue à l’expiration du certificat actuel, ce qui peut entraîner un temps d’arrêt pour la diffusion d’images et de vidéos. S’il n’existe aucun enregistrement CAA pour votre domaine, aucune action n’est requise.
