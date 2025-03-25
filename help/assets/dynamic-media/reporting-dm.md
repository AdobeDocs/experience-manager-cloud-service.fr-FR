---
title: Reporting dans Dynamic Media
description: Découvrez comment demander un rapport d’erreur pour les URL de diffusion Dynamic Media qui échouent.
contentOwner: Rick Brough
feature: Asset Management
role: User
hide: true
hidefromtoc: true
exl-id: 2488f813-df15-4dbb-8747-f827ee5925e1
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Demande d’un rapport d’erreur pour les URL de diffusion Dynamic Media en échec

Vous pouvez demander un rapport d’erreur qui identifie les URL Dynamic Media ayant échoué au moment de l’envoi. Le rapport est une agrégation de données allant jusqu’à cinq jours et est disponible au format CSV. Le rapport d’erreur contient les informations suivantes :

* URL de diffusion Dynamic Media en échec - Une URL en échec est une URL générée par Dynamic Media qui ne peut produire aucun contenu au moment de la diffusion.
* URL du référent - URL du référent à partir de laquelle l’URL de diffusion en échec est appelée.
* Nombre d’échecs : nombre de fois où l’URL de diffusion a été chargée et a provoqué un échec.

Lorsque vous demandez le rapport d’erreur, l’équipe Dynamic Media d’Adobe vous envoie le rapport par e-mail, au format CSV. Il couvre une période de cinq jours à compter du jour où votre demande a été faite.

Vous pouvez demander un rapport d’erreur une fois par mois, pour une société donnée.

**Pour demander un rapport d’erreur concernant les URL de diffusion Dynamic Media qui échouent, procédez comme suit**

1. [Envoyez un e-mail à reports-dynamic-media@adobe.com](mailto:reports-dynamic-media@adobe.com) avec le nom de la société associée à votre compte Dynamic Media.

   Si vous ne connaissez pas le nom de la société, consultez la page [Configuration de Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html?lang=fr#configuring-dynamic-media-cloud-services) dans **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Outils]** > **[!UICONTROL Services cloud]** > **[!UICONTROL Configuration de Dynamic Media]**. Sur la page du navigateur de configuration Dynamic Media, cliquez sur **[!UICONTROL global]**, cochez la case *[Dynamic_Media_folder_icon]*, puis sélectionnez **[!UICONTROL Modifier]**. Vous devez disposer des droits d’administrateur dans AEM pour accéder à la page de configuration de Dynamic Media.

   ![Accès à la page de configuration Dynamic Media.](/help/assets/dynamic-media/assets/reporting-accessdmconfig.png)
