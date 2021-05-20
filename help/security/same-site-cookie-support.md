---
title: Prise en charge des mêmes cookies de site pour Adobe Experience Manager en tant que Cloud Service
description: Prise en charge des mêmes cookies de site pour Adobe Experience Manager en tant que Cloud Service
exl-id: 2cec7202-4450-456f-8e62-b7ed3791505c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Prise en charge des cookies de site identiques pour Adobe Experience Manager as a Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}

Depuis la version 80, Chrome et Safari ultérieur, ont introduit un nouveau modèle de sécurité des cookies. Ce mode est conçu pour introduire des contrôles de sécurité sur la disponibilité des cookies aux sites tiers, via un paramètre appelé `SameSite`. Pour plus d’informations, voir cet [article](https://web.dev/samesite-cookies-explained/).

La valeur par défaut de ce paramètre (`SameSite=Lax`) peut entraîner le dysfonctionnement de l’authentification entre les instances AEM ou les services. En effet, les domaines ou les structures d’URL de ces services peuvent ne pas être soumis aux contraintes de cette stratégie de cookie.

Pour contourner ce problème, vous devez définir l’attribut de cookie SameSite sur `None` pour le jeton de connexion.

Pour ce faire, procédez comme suit :

1. Installation locale d’une version AEM SDK Quickstart
1. Accédez à la console web à l’adresse `http://serveraddress:serverport/system/console/configMgr`
1. Recherchez et cliquez sur **Gestionnaire d’authentification des jetons Granite Adobe**
1. Définissez l’attribut **SameSite pour le cookie de jeton de connexion** sur `None`, comme illustré dans l’image ci-dessous.
   ![samesite](/help/security/assets/samesite1.png)
1. Cliquez sur Enregistrer
1. Générez les configurations de format JSON pour ce paramètre spécifique en suivant les étapes décrites dans la section [Génération de configurations OSGi à l’aide du démarrage rapide (Quickstart) du SDK AEM](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart)
1. Appliquez les paramètres en suivant les étapes de la documentation OSGi [Format de l’API Cloud Manager pour la définition des propriétés](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties).

Une fois ce paramètre mis à jour et que les utilisateurs sont déconnectés et connectés à nouveau, les cookies `login-token` auront l’attribut `None` défini et seront inclus dans les demandes intersites.
