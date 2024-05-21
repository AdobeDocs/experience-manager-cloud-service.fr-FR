---
title: Configuration des intégrations IMS pour AEM as a Cloud Service
description: Découvrez comment configurer les intégrations IMS pour AEM as a Cloud Service
source-git-commit: 6945980cac24d4413a84343b035a8380b04e7444
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 3%

---


# Configuration des intégrations IMS pour AEM as a Cloud Service {#setting-up-ims-integrations-for-aemaacs}

>[!NOTE]
>
>Les configurations JWT configurées automatiquement ne doivent pas être migrées manuellement, car elles seront gérées automatiquement par Adobe.

Adobe Experience Manager (AEM) as a Cloud Service peut être intégré à de nombreuses autres solutions d’Adobe. Par exemple, Adobe Target, Adobe Analytics, etc.

Les intégrations utilisent une intégration IMS, configurée avec S2S OAuth.

* Une fois que vous avez créé :

   * [Informations d’identification dans Developer Console](#credentials-in-the-developer-console)

* Vous pouvez ensuite :

   * Créer un (nouveau) [Configuration OAuth](#creating-oauth-configuration)

   * [Migration d’une configuration JWT existante vers une configuration OAuth](#migrating-existing-JWT-configuration-to-oauth)

>[!CAUTION]
>
>Auparavant, les configurations étaient effectuées avec [Informations d’identification JWT désormais obsolètes dans la console Adobe Developer](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md).
>
>Ces configurations ne peuvent plus être créées ni mises à jour, mais peuvent être migrées vers des configurations OAuth.

## Informations d’identification dans Developer Console {#credentials-in-the-developer-console}

Pour commencer, vous devez configurer les informations d’identification OAuth dans la console Adobe Developer.

Pour plus d’informations sur la manière de procéder, consultez la documentation de Developer Console en fonction de vos besoins :

* Aperçu :

   * [Authentification serveur à serveur](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

* Création d’informations d’identification OAuth :

   * [Guide de mise en oeuvre des informations d’identification OAuth Server-to-Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)

* Migration d’informations d’identification JWT existantes vers des informations d’identification OAuth :

   * [Migration des informations d’identification du compte de service (JWT) vers les informations d’identification OAuth serveur à serveur](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)

Par exemple :

![Informations d’identification OAuth dans Developer Console](assets/ims-configuration-developer-console.png)

## Créer une configuration OAuth {#creating-oauth-configuration}

Pour créer une intégration Adobe IMS à l’aide d’OAuth :

1. Dans AEM, accédez à **Outils**, **Sécurité**, **Intégration Adobe IMS**.

1. Sélectionnez **Créer**.

1. Effectuez la configuration en fonction des détails de la variable [Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/). Par exemple :

   ![Créer une configuration OAuth](assets/ims-create-oauth-configuration.png)

1. **Enregistrez** vos modifications.

## Migration d’une configuration JWT existante vers une configuration OAuth {#migrating-existing-JWT-configuration-to-oauth}

Pour migrer une intégration Adobe IMS existante basée sur les informations d’identification JWT :

>[!NOTE]
>
>Cet exemple illustre une configuration IMS de Launch.

1. Dans AEM, accédez à **Outils**, **Sécurité**, **Intégration Adobe IMS**.

1. Sélectionnez la configuration JWT à migrer. Les configurations JWT sont signalées par l’avertissement . **Informations d’identification JWT (obsolète)**.

1. Sélectionner **Propriétés**:

   ![Sélectionner la configuration JWT](assets/ims-migrate-jwt-select-configuration.png)

1. La configuration s’ouvre en lecture seule :

   ![Propriétés de configuration - Lecture seule](assets/ims-migrate-jwt-properties-read-only.png)

1. Sélectionner **OAuth** de la **Type d’authentification** liste déroulante :

   ![Sélectionner le type d’authentification](assets/ims-migrate-jwt-authentication-type.png)

1. Les propriétés disponibles seront mises à jour. Utilisez les détails de Developer Console pour les compléter :

   ![Détails OAuth complets](assets/ims-migrate-jwt-complete-oauth-details.png)

1. Utilisation **Enregistrer et fermer** pour conserver vos mises à jour.
Lorsque vous revenez à la console, **Informations d’identification JWT (obsolète)** l&#39;avertissement a disparu.