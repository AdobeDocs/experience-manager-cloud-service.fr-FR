---
title: Prise en charge des mêmes cookies de site pour Adobe Experience Manager en tant que Cloud Service
description: Prise en charge des mêmes cookies de site pour Adobe Experience Manager en tant que Cloud Service
translation-type: tm+mt
source-git-commit: 4f25aa54bd40644912e0e430a81f1a17d545e3f8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# Prise en charge des mêmes cookies de site pour Adobe Experience Manager en tant que Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}

Depuis la version 80, Chrome et Safari ultérieur, a introduit un nouveau modèle de sécurité des cookies. Ce mode est conçu pour introduire des contrôles de sécurité sur la disponibilité des cookies sur les sites tiers, par le biais d&#39;un paramètre appelé `SameSite`. Pour plus d&#39;informations, consultez cet [article](https://web.dev/samesite-cookies-explained/).

La valeur par défaut de ce paramètre (`SameSite=Lax`) peut entraîner l’échec de l’authentification entre les instances ou services AEM. Cela est dû au fait que les domaines ou les structures d’URL de ces services peuvent ne pas être soumis aux contraintes de cette stratégie de cookies.

Pour contourner ce problème, vous devez définir l’attribut de cookie Site sur `None` pour le jeton de connexion.

Pour ce faire, procédez comme suit :

1. Installer une version du AEM SDK Quickstart localement
1. Accédez à la console Web à l&#39;adresse `http://serveraddress:serverport/system/console/configMgr`
1. Recherchez et cliquez sur le **gestionnaire d’authentification de jeton Granite Adobe**.
1. Définissez l’attribut **MêmeSite pour le cookie de jeton de connexion** sur `None`, comme illustré dans l’image ci-dessous.
   ![samesite](/help/security/assets/samesite1.png)
1. Cliquez sur Enregistrer
1. Générez les configurations de format JSON pour ce paramètre particulier en suivant les étapes décrites dans la section [Génération de configurations OSGi à l’aide de l’AEM SDK Quickstart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart)
1. Appliquez les paramètres en suivant les étapes décrites dans le document [Cloud Manager API Format for Setting Properties](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) OSGi.

Une fois ce paramètre mis à jour et que les utilisateurs sont déconnectés et reconnectés, les cookies `login-token` auront l&#39;attribut `None` défini et seront inclus dans les requêtes intersites.