---
title: FAQ sur la diffusion de contenu HTTP/2
description: Découvrez la diffusion de contenu HTTP/2.
role: Admin,User
exl-id: 0a8a5fd8-a341-4e7f-84a5-409e2de97efe
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 100%

---

# FAQ sur la diffusion de contenu HTTP/2{#http-delivery-of-content-faq}

Adobe se réjouit d’annoncer la disponibilité de la diffusion de contenu HTTP/2. Lorsque vous utilisez un protocole en HTTP/2, les performances globales augmentent.

>[!NOTE]
>
>Cette fonctionnalité nécessite l’utilisation du réseau de diffusion de contenu prêt à l’emploi fourni avec Adobe Experience Manager – Dynamic Media. Aucun autre réseau de diffusion de contenu personnalisé n’est pris en charge avec cette fonctionnalité.

## Qu’est-ce que le HTTP/2 ?  {#what-is-http}

Le HTTP/2 améliore la communication entre les navigateurs et les serveurs, en accélérant le transfert d’informations tout en réduisant la puissance de traitement nécessaire.

L’article du site web [What you must know about HTTP/2](https://www.engadget.com/2015-02-24-what-you-need-to-know-about-http-2.html) décrit le HTTP/2 et ses avantages d’une manière brève et simple.

## Quels sont les principaux avantages à la transition vers HTTP/2 pour la diffusion de contenu ?  {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

L’amélioration des performances varie considérablement en fonction de nombreux facteurs. Par exemple, le code de votre site web, la manière dont vous utilisez Dynamic Media, le périphérique, l’écran et l’emplacement du client.

Les tests d’Adobe ont donné les résultats suivants :

* Pour les images, le temps de réponse s’est amélioré de 7 % à 28 % selon l’appareil et le navigateur. Les gains de performance les plus notables ont été enregistrés sur les appareils iOS.
* Pour les visionneuses, les performances en matière de temps de chargement ont augmenté de 15 %.

La démonstration suivante illustre la différence entre le chargement HTTP/1 et le chargement HTTP/2 :

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Puis-je passer à HTTP/2 ? {#am-i-eligible-to-switch-over-to-http}

Pour utiliser HTTP/2, vous devez satisfaire aux exigences suivantes :

* Utilisez le protocole HTTPS sécurisé pour vos demandes de médias riches.
* Utilisez le CDN (réseau de diffusion de contenu) fourni par Adobe dans le cadre de votre licence Dynamic Media Classic.
* Utilisez un domaine dédié (c’est-à-dire `images.company.com` ou `mycompany.scene7.com`), et non un domaine Dynamic Media générique (c’est-à-dire `s7d1.scene7.com`, `s7d2.scene7.com` ou `s7d13.scene7.com`).

   Pour trouver vos domaines, ouvrez l’[application de bureau Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=fr#getting-started), puis connectez-vous à votre compte.

   Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’application]** > **[!UICONTROL Paramètres généraux]**. Recherchez le champ intitulé **Nom du serveur publié**. Si vous utilisez actuellement un domaine Dynamic Media générique, vous pouvez demander une migration vers votre domaine personnalisé dans le cadre de cette transition.

## Quel est le processus d’activation de HTTP/2 pour mon compte Dynamic Media ?  {#what-is-the-process-for-enabling-http-for-my-dm-account}

[Utilisez l’Admin Console pour créer un dossier de support](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html) et demander à passer en HTTP/2 ; ce processus n’est pas automatique.

1. Indiquez les informations suivantes dans votre dossier de support :

   * Nom, adresse électronique et numéro de téléphone du contact principal.
   * Tous les domaines pour lesquels activer HTTP/2. C’est-à-dire, `images.company.com` ou `mycompany.scene7.com`.

   Pour trouver vos domaines, ouvrez l’[application de bureau Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), puis connectez-vous à votre compte.

   Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’application]** > **[!UICONTROL Paramètres généraux]**. Recherchez le champ intitulé **[!UICONTROL Nom du serveur publié]**.

   * Vérifiez que vous utilisez le protocole sécurisé HTTPS pour les demandes de médias riches.
   * Vérifiez que vous utilisez le CDN par le biais d’Adobe et non le CDN géré avec une relation directe.
   * Assurez-vous d’utiliser un domaine dédié. C’est-à-dire `images.company.com` ou `mycompany.scene7.com`, et non d’un domaine Dynamic Media tel que `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

   Pour trouver vos domaines, ouvrez l’[application de bureau Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), puis connectez-vous à votre compte.

   Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’application]** > **[!UICONTROL Paramètres généraux]**. Recherchez le champ intitulé **[!UICONTROL Nom du serveur publié]**. Si vous utilisez actuellement un domaine Dynamic Media générique, vous pouvez demander une migration vers votre domaine personnalisé dans le cadre de cette transition.

   1. Le service clientèle vous ajoute à la liste d’attente des clients HTTP/2 par ordre chronologique d’envoi des demandes.
   1. Lorsqu’Adobe est prêt à traiter votre demande, le service clientèle vous contacte pour coordonner la transition et définir une date cible.
   1. Vous recevez une notification à l’issue du processus et pouvez vérifier que la transition vers HTTP/2 a abouti.



## Quand puis-je espérer passer à HTTP/2 ?  {#when-can-i-expect-to-be-transitioned-over-to-http}

Les demandes sont traitées dans l’ordre dans lequel le service clientèle les reçoit.

>[!NOTE]
>
>Le délai d’exécution est long car la transition vers le HTTP/2 implique l’effacement du cache. Par conséquent, seules quelques transitions client peuvent être traitées simultanément.

## Quels risques présente la transition vers HTTP/2 ? {#what-are-the-risks-with-moving-to-http}

La transition vers HTTP/2 efface le cache au niveau du CDN, car elle implique la définition d’une nouvelle configuration de CDN.

Le contenu non mis en cache atteint directement les serveurs Adobe d’origine jusqu’à ce que le cache soit reconstruit. Grâce à cette action, Adobe prévoit de gérer plusieurs transitions client à la fois. Cette méthode garantit des performances acceptables lors de l’extraction de requêtes à partir de l’origine.

## Comment puis-je vérifier si une URL ou un site web est activé avec HTTP/2 ? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Téléchargez une extension à utiliser avec votre navigateur web. Pour Firefox et Chrome, il existe une extension appelée **[!UICONTROL HTTP/2 and SPDY Indicator]**. Les navigateurs ne prennent en charge HTTP/2 qu’en mode sécurisé. Par conséquent, appelez une URL avec le protocole HTTPS pour vérifier. Si le HTTP/2 est pris en charge, l’extension comprend un symbole Flash de couleur bleue et un en-tête « X-Firefox-Spdy » : « h2 ».
