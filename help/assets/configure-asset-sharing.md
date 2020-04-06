---
title: Partage de ressources, de dossiers et de collections sous forme de lien
description: Cet article décrit le partage de ressources, de dossiers et de collections dans les ressources d’Experience Manager sous forme de lien hypertexte.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Configuration du partage de liens de ressources {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

Pour générer une URL pour les ressources que vous souhaitez partager avec des utilisateurs, utilisez la boîte de dialogue Partage de lien. Les utilisateurs disposant de privilèges d’administrateur ou avec des autorisations de lecture à l’emplacement `/var/dam/share` peuvent afficher les liens partagés avec eux. Le partage de ressources au moyen d’un lien est très pratique dans la mesure où il permet à des tiers d’y accéder sans avoir besoin de se connecter au préalable à AEM Assets.

>[!NOTE]
>
>Si vous souhaitez partager des liens de votre instance de création AEM vers des entités externes, veillez à n’exposer que les URL suivantes pour les requêtes `GET`. Bloquez les autres URL pour garantir la sécurité de votre instance de création AEM.
>* `[aem_server]:[port]/linkshare.html`
>* `[aem_server]:[port]/linksharepreview.html`
>* `[aem_server]:[port]/linkexpired.html`


## Configuration du service de messagerie Day CQ {#configmailservice}

Avant de pouvoir partager des ressources sous forme de liens, configurez le service de messagerie.

1. Cliquez ou appuyez sur le logo AEM, puis accédez à **[!UICONTROL Outils]** > **[!UICONTROL Opérations]** > **[!UICONTROL Console web]**.
1. Dans la liste des services, recherchez le **[!UICONTROL service de messagerie Day CQ]**.
1. Cliquez sur l’icône **[!UICONTROL Modifier]** en regard du service et configurez les paramètres suivants pour le **service de messagerie Day CQ** avec les détails mentionnés en regard de leurs noms :

   * Nom d’hôte du serveur SMTP : nom d’hôte du serveur de messagerie
   * Port du serveur SMTP : port du serveur de messagerie
   * Utilisateur SMTP : nom d’utilisateur du serveur de messagerie
   * Mot de passe SMTP : mot de passe du serveur de messagerie

1. Cliquez/appuyez sur **Enregistrer**.

## Configuration de la taille maximale des données   {#maxdatasize}

Lorsque vous téléchargez des ressources via le lien partagé avec la fonction de partage de lien, AEM compresse l’intégralité de la hiérarchie de cette ressource depuis le référentiel et renvoie la ressource sous forme de fichier ZIP. Toutefois, en l’absence de limite à la quantité de données pouvant être compressées dans un fichier ZIP, il est possible que des volumes de données considérables à compresser entraînent des erreurs d’insuffisance de mémoire dans JVM. Afin de protéger le système contre une potentielle attaque par déni de service (DoS) résultant de cette situation, configurez la taille maximale à l’aide du paramètre **Taille max. de contenu (sans compression)** pour le servlet proxy du partage de ressource adhoc de la gestion des ressources numériques Day CQ dans le gestionnaire de configuration. Si la taille non compressée de la ressource dépasse la valeur configurée, les demandes de téléchargement sont rejetées. La valeur par défaut est de 100 Mo.

1. Cliquez ou appuyez sur le logo AEM puis accédez à **Outils** > **Opérations** > **Console web**.
1. Dans la console web, recherchez la configuration **Day CQ DAM Adhoc Asset Share Proxy Servlet**.
1. Ouvrez la configuration **Day CQ DAM Adhoc Asset Share Proxy Servlet** en mode d’édition, puis modifiez la valeur du paramètre **Taille max. de contenu (sans compression)**.
1. Enregistrez les modifications.

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->
