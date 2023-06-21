---
title: Prise en charge du cookie Same Site pour Adobe Experience Manager as a Cloud Service
description: Prise en charge du cookie Same Site pour Adobe Experience Manager as a Cloud Service
exl-id: 2cec7202-4450-456f-8e62-b7ed3791505c
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 85%

---

# Prise en charge du cookie Same Site pour Adobe Experience Manager as a Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}

Depuis la version 80, Chrome et ultérieurement Safari ont introduit un nouveau modèle de sécurité des cookies. Ce modèle a été conçu pour introduire des contrôles de sécurité dans les sites tiers sur la disponibilité des cookies par le biais d’un paramètre appelé `SameSite`. Pour en savoir plus, consultez cet [article](https://web.dev/samesite-cookies-explained/).

La valeur par défaut de ce paramètre (`SameSite=Lax`) peut entraîner l’échec de l’authentification entre les instances ou services AEM. Ce dysfonctionnement est dû au fait que les domaines ou les structures d’URL de ces services peuvent ne pas être soumis aux contraintes de cette politique de cookies.

Pour contourner ce problème, vous devez définir l’attribut de cookie SameSite sur `None` pour le jeton de connexion.

>[!CAUTION]
>
>Le paramètre `SameSite=None` n’est appliqué que si le protocole est sécurisé (HTTPS).
>
>Si le protocole n’est pas sécurisé (HTTP), le paramètre est ignoré et le serveur affiche ce message d’AVERTISSEMENT :
>
>`WARN com.day.crx.security.token.TokenCookie Skip 'SameSite=None'`

Vous pouvez ajouter ce paramètre en procédant comme suit :

1. Installez localement une version du SDK AEM Quickstart
1. Accédez à la console web à l’adresse `http://serveraddress:serverport/system/console/configMgr`
1. Recherchez et cliquez sur le **gestionnaire d’authentification de jeton Granite Adobe**
1. Définissez l’**attribut SameSite pour le cookie de jeton de connexion** sur `None`, comme illustré dans l’image ci-dessous
   ![samesite](/help/security/assets/samesite1.png)
1. Cliquez sur Enregistrer
1. Générez les configurations de format JSON pour ce paramètre en particulier en suivant les étapes décrites dans la section [Génération de configurations OSGi à l’aide du SDK AEM Quickstart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart)
1. Appliquez les paramètres en suivant les étapes décrites dans le document OSGi [Format d’API Cloud Manager pour la configuration des propriétés](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties).

Une fois ce paramètre mis à jour, les utilisateurs sont connectés et reconnectés, `login-token` Les cookies ont la variable `None` est inclus dans les requêtes intersites.
