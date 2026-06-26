---
title: Dynatrace
description: Découvrez comment utiliser Dynatrace avec AEM as a Cloud Service.
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Developer
source-git-commit: d007b33ba41a791242c1ea1c8264984b9182fa54
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 44%

---

# Dynatrace {#dynatrace}

Adobe permet d’utiliser Dynatrace pour surveiller AEM as a Cloud Service dans le cadre d’un déploiement en entreprise, d’identifier la cause de tout problème potentiel et de prendre des mesures pour y remédier, le cas échéant.

Avec Dynatrace, vous profitez d’une observabilité transparente pour toutes vos applications AEM. Dynatrace détecte vos applications AEM et affiche leurs chemins, du site web au conteneur en passant par le Cloud Service, pour surveiller l’expérience utilisateur. Associé au suivi de bout en bout à tous les niveaux et à la surveillance réelle des utilisateurs, il améliore vos expériences AEM basées sur le contenu sans lacunes ni limites de surveillance. Si des anomalies surviennent, Dynatrace les diagnostique en temps réel à l’aide du moteur d’IA de Davis. Il identifie la cause du problème avant que vos clients ne soient affectés, ce qui réduit le temps nécessaire à sa résolution.

Pour en savoir plus sur Dynatrace, voir l’[intégration d’Adobe AEM Cloud Service](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![Mesures des performances de création et de publication d’AEM](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Intégration de Dynatrace à AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

Les clients Dynatrace peuvent surveiller leurs environnements AEM en demandant une connectivité via un ticket de service clientèle.

Les détails à fournir pour les demandes de connectivité sont décrits ci-dessous :

| **Champ** | **Description** |
|---|---|
| [!DNL Dynatrace Environment URL] | Votre environnement Dynatrace URL.<br><br>Pour les clients SaaS Dynatrace, le format est `https://<your-environment-id>.live.dynatrace.com`.<br><br>Pour les clients gérés par Dynatrace, le format est `https://<your-managed-url>/e/<environmentId>` |
| [!DNL Dynatrace Environment ID] | Identifiant de votre environnement Dynatrace. Voir [Comment puis-je obtenir mes détails de connexion Dynatrace ?](#how-do-i-get-my-dynatrace-connection-details) pour savoir comment l&#39;obtenir. |
| [!DNL Dynatrace Environment Token] | Jeton de votre environnement Dynatrace. Voir [Comment puis-je obtenir mes détails de connexion Dynatrace ?](#how-do-i-get-my-dynatrace-connection-details) pour savoir comment l&#39;obtenir.<br><br>Ce jeton doit être considéré comme secret. Utilisez donc les pratiques de sécurité appropriées. Par exemple, protégez le système par un mot de passe dans un site web tel que **zerobin.net**, auquel le ticket d’assistance clientèle peut faire référence, mot de passe compris. |
| [!DNL Dynatrace API access token] | Jeton d’accès à l’API de votre environnement Dynatrace. Voir [Création d’un jeton d’accès API Dynatrace](#create-dynatrace-access-token) pour savoir comment le créer.<br><br>Ce jeton doit être considéré comme secret. Utilisez donc les pratiques de sécurité appropriées. Par exemple, protégez-le par mot de passe sur un site web tel que **zerobin.net**, auquel le ticket de service clientèle peut faire référence, ainsi que le mot de passe <br>. |
| [!DNL Dynatrace ActiveGate Port] | Votre port Dynamic ActiveGate auquel l’intégration d’AEM doit se connecter.<br><br>Ce port n’est nécessaire que pour la gestion par Dynatrace. |
| [!DNL Dynatrace ActiveGate Network Zone] | Votre [zone réseau ActiveGate de ](https://docs.dynatrace.com/docs/manage/network-zones) pour acheminer efficacement les données de surveillance d&#39;AEM entre les centres de données et les régions du réseau.<br><br>Remarque : une zone réseau ActiveGate de Dynatrace est facultative. |
| [!DNL AEM Environment IDs] | L’identifiant ou les identifiants d’environnement AEM à surveiller par Dynatrace. |

>[!NOTE]
>
>Une fois Dynatrace intégré, les données ne sont plus transférées vers d’autres outils APM tels que New Relic, si elles ont été activées précédemment.

## Questions fréquentes {#faq}

### De quelle licence ai-je besoin pour la surveillance Dynatrace d’AEM ? {#which-license-do-i-need-for-AEM-monitoring}

La surveillance Dynatrace d’AEM nécessite une licence Dynatrace. Les licences Dynatrace AEM sont basées sur [une surveillance full stack pour les conteneurs Kubernetes](https://docs.dynatrace.com/docs/license/capabilities/app-infra-observability#gib-hour-calculation-for-containers-and-application-only-monitoring). Les tailles de la mémoire des conteneurs AEM surveillés (services de création et de publication) sont automatiquement détectées.

Les spécifications de déploiement Adobe par environnement AEM sont les suivantes :

* Production : en moyenne, 4 conteneurs, 16 Go de mémoire chacun.
* Hors production : en moyenne, 4 conteneurs, 8 Go de mémoire chacun.

Pour en savoir plus sur les licences Dynatrace, consultez [Abonnement à la plateforme Dynatrace](https://docs.dynatrace.com/docs/license).

### Comment obtenir mes informations de connexion Dynatrace ? {#how-do-i-get-my-dynatrace-connection-details}

1. Exécutez la requête d’API suivante sur votre environnement Dynatrace :

   ```
   curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"
   ```


   Remplacez `<environmentUrl>` par l’URL de votre environnement Dynatrace et `<accessToken>` par votre jeton d’accès à l’API créé.

1. Copiez les `<environmentId>` et les `<environmentToken>` de la payload de réponse et stockez-les dans un emplacement sécurisé.

   ```
   {
      "tenantUUID": "<environmentId>",
      "tenantToken": "<environmentToken>",
      "communicationEndpoints": [...]
   }
   ```

### Créer un jeton d’accès à l’API Dynatrace {#create-dynatrace-access-token}

1. Connectez-vous à votre environnement Dynatrace.
1. Accédez à **[!DNL Access tokens]**, puis cliquez sur l’option **[!DNL Generate new token]**.
1. Définissez un [!DNL token name].
1. Définissez la portée du jeton sur **[!DNL PaaS integration - Installer download]**.
1. Sélectionnez **[!DNL Generate token]**.
1. Copiez le jeton d’accès généré et stockez-le dans un emplacement sécurisé.





