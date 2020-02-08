---
title: Partage de fichiers, de dossiers et de collections sous forme de lien
description: Cet article décrit le partage de fichiers, de dossiers et de collections dans les ressources d’Experience Manager sous forme d’hyperlien.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Configuration du partage de liens de ressources {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

Pour générer une URL pour les ressources que vous souhaitez partager avec des utilisateurs, utilisez la boîte de dialogue Partage de lien. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Le partage de ressources au moyen d’un lien est très pratique dans la mesure où il permet à des tiers d’y accéder sans avoir besoin de se connecter au préalable à AEM Assets.

>[!NOTE]
>
>Si vous souhaitez partager des liens de votre instance Auteur AEM vers des entités externes, veillez à n’exposer que les URL suivantes pour `GET` les requêtes. Bloquez d’autres URL pour vous assurer que votre instance Auteur AEM est sécurisée.
>* `[aem_server]:[port]/linkshare.html`
>* `[aem_server]:[port]/linksharepreview.html`
>* `[aem_server]:[port]/linkexpired.html`


## Configuration du service de messagerie Day CQ {#configmailservice}

Avant de pouvoir partager des fichiers sous forme de liens, configurez le service de messagerie.

1. Cliquez ou appuyez sur le logo AEM, puis accédez à **[!UICONTROL Outils]** > **[!UICONTROL Opérations]** > **[!UICONTROL Console web]**.
1. Dans la liste des services, recherchez le **[!UICONTROL service de messagerie Day CQ]**.
1. Click the **[!UICONTROL Edit]** icon beside the service, and configure the following parameters for **Day CQ Mail Service]** with the details mentioned against their names:

   * Nom d’hôte du serveur SMTP : nom d’hôte du serveur de messagerie
   * Port du serveur SMTP : port du serveur de messagerie
   * Utilisateur SMTP : nom d’utilisateur du serveur de messagerie
   * Mot de passe SMTP : mot de passe du serveur de messagerie

1. Cliquez/appuyez sur **Enregistrer**.

## Configuration de la taille maximale des données {#maxdatasize}

Lorsque vous téléchargez des ressources via le lien partagé avec la fonction de partage de lien, AEM compresse l’intégralité de la hiérarchie de cette ressource depuis le référentiel et renvoie la ressource sous forme de fichier ZIP. Toutefois, en l’absence de limite à la quantité de données pouvant être compressées dans un fichier ZIP, il est possible que des volumes de données considérables à compresser entraînent des erreurs d’insuffisance de mémoire dans JVM. To secure the system from a potential denial of service attack due to this situation, configure the maximum size using the **Max Content Size (uncompressed)** parameter for Day CQ DAM Adhoc Asset Share Proxy Servlet in Configuration Manager. Si la taille non compressée de l’actif dépasse la valeur configurée, les demandes de téléchargement sont rejetées. La valeur par défaut est de 100 Mo.

1. Cliquez ou appuyez sur le logo AEM puis accédez à **Outils** > **Opérations** > **Console Web**.
1. From the web console, locate the **Day CQ DAM Adhoc Asset Share Proxy Servlet** configuration.
1. Open the **Day CQ DAM Adhoc Asset Share Proxy Servlet** configuration in edit mode, and modify the value of the **Max Content Size (uncompressed)** parameter.
1. Enregistrez les modifications.

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->
