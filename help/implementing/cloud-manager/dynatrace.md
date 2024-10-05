---
title: Dynatrace
description: Découvrir comment utiliser Dynatrace avec AEM as a Cloud Service
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Architect, Developer
source-git-commit: 500e1b78fb9688601848fc17f312fc23be83bcb0
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 93%

---

# Dynatrace {#dynatrace}

Adobe permet d’utiliser Dynatrace pour surveiller AEM as a Cloud Service dans le cadre d’un déploiement en entreprise, d’identifier la cause de tout problème potentiel et de prendre des mesures pour y remédier, le cas échéant.

Avec Dynatrace, vous profitez d’une observabilité transparente pour toutes vos applications AEM. Dynatrace assure une visibilité complète de l’expérience des utilisateurs finaux en détectant automatiquement vos applications AEM et en visualisant leurs dépendances, du site web vers le conteneur, puis vers le service cloud. Du fait de la liaison avec des traces de bout en bout à tous les niveaux et de la surveillance de l’utilisation en temps réel, vous optimisez vos expériences AEM basées sur du contenu, sans lacunes ni déficiences. En cas d’anomalies, Dynatrace les diagnostique en temps réel avec le moteur d’IA Davis et identifie la cause principale, en allant jusqu’aux erreurs de code, avant que vos clientes et clients ne soient affectés, ce qui réduit le temps moyen de réparation.

Pour en savoir plus sur Dynatrace, voir l’[intégration d’Adobe AEM Cloud Service](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![Mesures des performances de création et de publication d’AEM](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Intégrer Dynatrace à AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

Les clientes et clients de Dynatrace peuvent surveiller leurs environnements AEM en demandant une connectivité par le biais d’un ticket d’assistance clientèle.

Les détails à fournir pour les demandes de connectivité sont décrits ci-dessous :

| **Champ** | **Description** |
|---|---|
| [!DNL Dynatrace Environment URL] | URL de votre environnement Dynatrace.<br><br>Pour les clientes et clients Dynatrace, le format est `https://<your-environment-id>.live.dynatrace.com`.<br><br>Pour les clientes et clients de Dynatrace Managed, le format est `https://<your-managed-url>/e/<environmentId>`. |
| [!DNL Dynatrace Environment ID] | Identifiant de votre environnement Dynatrace. Voir [Comment puis-je obtenir mes détails de connexion Dynatrace ?](#how-do-i-get-my-dynatrace-connection-details) pour savoir comment obtenir ces informations. |
| [!DNL Dynatrace Environment Token] | Jeton de votre environnement Dynatrace. Voir [Comment puis-je obtenir mes détails de connexion Dynatrace ?](#how-do-i-get-my-dynatrace-connection-details) pour savoir comment obtenir ces informations.<br><br>Vous devez traiter ces informations de manière confidentielle. Utilisez donc des pratiques de sécurité appropriées. Par exemple, protégez le système par un mot de passe dans un site web tel que **zerobin.net**, auquel le ticket d’assistance clientèle peut faire référence, mot de passe compris. |
| [!DNL Dynatrace API access token] | Jeton d’accès API de votre environnement Dynatrace. Voir [Création d’un jeton d’accès à l’API Dynatrace](#create-dynatrace-access-token) pour savoir comment le créer.<br><br>Vous devez traiter ces informations de manière confidentielle. Utilisez donc des pratiques de sécurité appropriées. Par exemple, protégez le système par un mot de passe dans un site web tel que **zerobin.net**, auquel le ticket d’assistance clientèle peut faire référence, mot de passe compris.<br><br>Remarque : cela n’est nécessaire que pour Dynatrace Managed. |
| [!DNL Dynatrace ActiveGate Port] | Votre port Dynamic ActiveGate auquel l’intégration d’AEM doit se connecter.<br><br>Remarque : cela n’est nécessaire que pour Dynatrace Managed. |
| [!DNL Dynatrace ActiveGate Network Zone] | Votre [zone de réseau Dynatrace ActiveGate](https://docs.dynatrace.com/docs/manage/network-zones) pour acheminer efficacement les données de surveillance AEM entre les centres de données et les régions de réseau.<br><br>Remarque : une zone de réseau Dynatrace ActiveGate est facultative. |
| [!DNL AEM Environment ID(s)] | Le ou les identifiants d’environnement AEM que Dynatrace doit surveiller. |

>[!NOTE]
>
>Une fois Dynatrace intégré, les données ne sont plus transmises à d’autres outils APM tels que New Relic, s’il a été activé au préalable.

## Questions fréquentes {#faq}

### De quelle licence ai-je besoin pour la surveillance Dynatrace d’AEM ? {#which-license-do-i-need-for-AEM-monitoring}

La surveillance Dynatrace d’AEM nécessite une licence Dynatrace. Les licences Dynatrace AEM sont basées sur [une surveillance full stack pour les conteneurs Kubernetes](https://docs.dynatrace.com/docs/shortlink/dps-hosts#gib-hour-calculation-for-containers-and-application-only-monitoring). Les tailles de la mémoire des conteneurs AEM surveillés (services de création et de publication) sont automatiquement détectées.

Les spécifications de déploiement Adobe par environnement AEM sont les suivantes :

* Production : en moyenne, 4 conteneurs, 16 Go de mémoire chacun.
* Hors production : en moyenne, 4 conteneurs, 8 Go de mémoire chacun.

Pour en savoir plus sur les licences Dynatrace, consultez [Abonnement à la plateforme Dynatrace](https://docs.dynatrace.com/docs/shortlink/dynatrace-platform-subscription).

### Comment obtenir mes informations de connexion Dynatrace ? {#how-do-i-get-my-dynatrace-connection-details}

1. Exécutez la requête d’API suivante sur votre environnement Dynatrace :

   ```
   curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"
   ```


   Remplacez `<environmentUrl>` par l’URL de votre environnement Dynatrace et `<accessToken>` par votre jeton d’accès à l’API créé.

1. Copiez les éléments `<environmentId>` et `<environmentToken>` à partir de la payload de la réponse et stockez-les dans un emplacement sécurisé.

   ```
   {
      "tenantUUID": "<environmentId>",
      "tenantToken": "<environmentToken>",
      "communicationEndpoints": [...]
   }
   ```

### Créer un jeton d’accès à l’API Dynatrace {#create-dynatrace-access-token}

1. Connectez-vous à votre environnement Dynatrace.
1. Accédez à **[!DNL Access tokens]** et sélectionnez **[!DNL Generate new token]**.
1. Définissez un [!DNL token name].
1. Définissez la portée du jeton sur **[!DNL PaaS integration - Installer download]**.
1. Sélectionnez **[!DNL Generate token]**.
1. Copiez le jeton d’accès généré et stockez-le dans un emplacement sécurisé.





