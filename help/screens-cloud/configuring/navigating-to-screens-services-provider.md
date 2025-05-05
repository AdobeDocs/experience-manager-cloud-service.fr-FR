---
title: Accès au fournisseur de services Screens
description: Cette page décrit comment accéder au fournisseur de services Screens.
exl-id: 9eff6fe8-41d4-4cf3-b412-847850c4e09c
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 58%

---

# Accès au fournisseur de services Screens {#setup-screens-services-provider}

## Présentation {#introduction}

**Le fournisseur de services Screens** permet à l’auteur, aux développeurs et aux administrateurs de contenu de gérer les affichages et les lecteurs pour la lecture de contenu une fois le contenu ajouté aux canaux. Une fois que les utilisateurs ont accès à AEM Cloud Service, ils doivent pouvoir se connecter au fournisseur de services Screens.

Cette section décrit comment configurer le fournisseur de services Screens.


## Objectif {#objective}

La section suivante explique comment configurer le fournisseur de services Screens.

## Procédure de configuration du fournisseur de services Screens {#screens-services-provider}

Suivez les étapes ci-dessous pour configurer le fournisseur de services Screens :

1. Accédez au [fournisseur de services Screens](https://experience.adobe.com/screens).

   >[!CAUTION]
   >Si vous avez accès à plusieurs organisations, vérifiez que votre connexion est établie avec la bonne organisation. Pour modifier votre organisation, cliquez sur le nom de l’organisation dans le coin supérieur droit de l’écran et sélectionnez l’organisation à laquelle vous avez besoin d’accéder.

1. Cliquez sur l’icône d’engrenage en regard de Projet (coin supérieur gauche)

   ![image](/help/screens-cloud/assets/configure/configure-screens0.png)

1. Saisissez les informations suivantes dans la boîte de dialogue Modifier les paramètres.
   * **URL de publication** - URL de publication AEM (par exemple, `https://publish-p12345-e12345.adobeaemcloud.com`)
   * **URL de création** - URL de création AEM (par exemple, `https://author-p12345-e12345.adobeaemcloud.com`)

   >[!NOTE]
   >Veillez à créer et publier au moins un canal d’écran AEM avant de configurer l’AEM sous Fournisseur de services Screens. Pour créer un canal, accédez à /screens.html sur votre fournisseur de contenu.

   ![Image](/help/screens-cloud/assets/configure/configure-screens4.png)

1. Cliquez sur **Enregistrer** pour vous connecter au fournisseur de contenu Screens.

1. Si vous avez configuré l’instance de publication AEM de manière à autoriser l’accès uniquement aux adresses IP de confiance par la fonction Cloud Manager de Liste autorisée IP, vous devez configurer un en-tête avec une valeur clé dans la boîte de dialogue des paramètres, comme illustré ci-dessous.
Les adresses IP qui doivent être whitelistées doivent également être déplacées vers le fichier de configuration et [non appliquées](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/apply-allow-list) depuis les paramètres de Cloud Manager.

   ![image](/help/screens-cloud/assets/configure/configure-screens20b.png)
La même clé doit être configurée à AEM configuration du réseau de diffusion de contenu.  Il est recommandé de ne pas placer la valeur d’en-tête directement dans GITHub et d’utiliser une [référence secrète](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-credentials-authentication#rotating-secrets).
Voici un exemple de [configuration CDN](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/security/traffic-filter-rules-including-waf) :

   ```kind: "CDN"
       version: "1"
       metadata:
         envTypes: ["dev", "stage", "prod"]
       data:
         trafficFilters:
           rules:
             - name: "block-request-from-not-allowed-ips"
               when:
                 allOf:
                   - reqProperty: clientIp
                     notIn: ["101.41.112.0/24"]
                    reqProperty: tier
                     equals: publish
               action: block
             - name: "allow-requests-with-header"
               when:
                 allOf:
                   - reqProperty: tier
                     equals: publish
                   - reqProperty: path
                     equals: /screens/channels.json
                   - reqHeader: x-screens-allowlist-key
                     equals: $\
       {CDN_HEADER_KEY}
               action:
                 type: allow
   ```

1. Sélectionnez **Canaux** dans la barre de navigation de gauche et cliquez sur **Ouvrir dans le fournisseur de contenu**.

   ![Image](/help/screens-cloud/assets/configure/configure-screens1.png)

1. Le fournisseur de contenu Screens s’ouvre dans un autre onglet qui vous permet de créer votre contenu.

   ![image](/help/screens-cloud/assets/configure/configure-screens2.png)





## Prochaines étapes {#whats-next}

Une fois que vous avez appris à configurer le fournisseur de services Screens, accédez à [Utilisation du fournisseur de contenu Screens](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=fr#screens-content-provider) pour plus d’informations.
