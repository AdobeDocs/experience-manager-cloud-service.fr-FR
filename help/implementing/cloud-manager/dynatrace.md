---
title: Dynatrace
description: Découvrez comment utiliser Dynatrace avec AEM as a Cloud Service
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
source-git-commit: d6f5a365a48a8b20b69db6895f895c9d172d58a7
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Dynatrace {#dynatrace}

Adobe permet d’utiliser Dynatrace pour surveiller AEM as a Cloud Service dans le cadre du déploiement de l’entreprise, identifier la cause de tout problème potentiel et prendre des mesures pour y remédier si nécessaire.

Avec Dynatrace, vous pouvez obtenir une observabilité transparente pour toutes vos applications AEM. Dynatrace offre une visibilité complète sur l’expérience de l’utilisateur final en détectant automatiquement vos applications AEM et en visualisant leurs dépendances du site web vers le conteneur vers le service cloud. Liées aux traces de bout en bout à tous les niveaux et à la surveillance des utilisateurs réels, redirigez vos expériences AEM basées sur le contenu vers le niveau suivant sans espaces ni angles morts. En cas d’anomalies, Dynatrace les diagnostique en temps réel avec le moteur Davis AI et identifie la cause principale jusqu’au code rompu avant que vos clients ne soient affectés, ce qui réduit le temps moyen de réparation.

Pour en savoir plus sur Dynatrace, voir [Intégration d’Adobe AEM Cloud Service](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![AEM des mesures de performances de création et d’éditeur](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Intégration de Dynatrace à AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

Les clients Dynatrace peuvent surveiller leurs environnements AEM en demandant la connectivité par le biais d’un ticket d’assistance clientèle.

Les détails requis pour les demandes de connectivité sont décrits ci-dessous :

| **Champ** | **Description** |
|---|---|
| [!DNL Dynatrace Environment URL] | URL de votre environnement Dynatrace.<br><br>Pour les clients Dynatrace SaaS, le format est `https://<your-environment-id>.live.dynatrace.com`.<br><br>Pour les clients gérés par Dynatrace, le format est `https://<your-managed-url>/e/<environmentId>` |
| [!DNL Dynatrace Environment ID] | Identifiant de votre environnement Dynatrace. Veuillez consulter [Comment puis-je obtenir mes détails de connexion Dynatrace ?](#how-do-i-get-my-dynatrace-connection-details) pour savoir comment obtenir ceci. |
| [!DNL Dynatrace Environment Token] | Votre jeton d’environnement Dynatrace. Veuillez consulter [Comment puis-je obtenir mes détails de connexion Dynatrace ?](#how-do-i-get-my-dynatrace-connection-details) pour savoir comment obtenir ceci.<br><br>Cela doit être considéré comme un secret. Utilisez donc les pratiques de sécurité appropriées. Par exemple, un mot de passe le protège dans un site web tel que **zerobin.net**, à laquelle le ticket d’assistance clientèle peut faire référence, ainsi que le mot de passe. |
| [!DNL Dynatrace API access token] | Jeton d’accès API de votre environnement Dynatrace.  Veuillez consulter [Création d’un jeton d’accès API Dynatrace](#create-dynatrace-access-token) pour savoir comment créer ceci.<br><br>Ce secret doit être considéré comme un secret. Utilisez donc les pratiques de sécurité appropriées. Par exemple, un mot de passe le protège dans un site web tel que **zerobin.net**, à laquelle le ticket d’assistance clientèle peut faire référence, ainsi que le mot de passe.<br><br>Remarque : Cela n’est nécessaire que pour Dynatrace Managed. |
| [!DNL Dynatrace ActiveGate Port] | Votre port Dynatrace ActiveGate auquel l’intégration AEM doit se connecter.<br><br>Remarque : Cela n’est nécessaire que pour Dynatrace Managed. |
| [!DNL Dynatrace ActiveGate Network Zone] | Votre [Zone réseau Dynatrace ActiveGate](https://docs.dynatrace.com/docs/manage/network-zones) pour acheminer efficacement les données de surveillance AEM entre les centres de données et les régions de réseau.<br><br>Remarque : une zone réseau Dynatrace ActiveGate est facultative. |
| [!DNL AEM Environment ID(s)] | ID d’environnement AEM que Dynatrace doit surveiller. |

>[!NOTE]
>
>Une fois Dynatrace intégré, les données ne sont plus transmises à d’autres outils APM tels que New Relic, s’ils ont été activés auparavant.

## FAQ {#faq}

### De quelle licence ai-je besoin pour Dynatrace AEM Monitoring ? {#which-license-do-i-need-for-AEM-monitoring}

La surveillance d’Dynatrace AEM nécessite une licence Dynatrace. Les licences Dynatrace AEM sont basées sur [surveillance complète des piles pour les conteneurs Kubernetes](https://docs.dynatrace.com/docs/shortlink/dps-hosts#gib-hour-calculation-for-containers-and-application-only-monitoring). Les tailles de mémoire des conteneurs d’AEM surveillés (services de création et d’éditeur) sont automatiquement détectées.

Les spécifications de déploiement Adobe par environnement AEM sont les suivantes :

* Production : en moyenne, 4 conteneurs, 16 Go de mémoire chacun
* Non-production : en moyenne, 4 conteneurs, 8 Go de mémoire chacun

Pour en savoir plus sur les licences Dynatrace, voir [Abonnement à Dynatrace Platform](https://docs.dynatrace.com/docs/shortlink/dynatrace-platform-subscription).

### Comment puis-je obtenir mes détails de connexion Dynatrace ? {#how-do-i-get-my-dynatrace-connection-details}

1. Exécutez la requête d’API suivante sur votre environnement Dynatrace :

`curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"`

Remplacer `<environmentUrl>` avec l’URL de votre environnement Dynatrace et `<accessToken>` avec votre jeton d’accès API créé.

1. Copiez le `<environmentId>` et `<environmentToken>` à partir du payload de la réponse et stockez-les dans un emplacement sécurisé.

```
{
   "tenantUUID": "<environmentId>",
   "tenantToken": "<environmentToken>",
   "communicationEndpoints": [...]
}
```

### Création d’un jeton d’accès API Dynatrace {#create-dynatrace-access-token}

1. Connectez-vous à votre environnement Dynatrace.
1. Accédez à **[!DNL Access tokens]** et sélectionnez **[!DNL Generate new token]**.
1. Définition d’une [!DNL token name].
1. Définissez la portée du jeton sur **[!DNL PaaS integration - Installer download]**.
1. Sélectionner **[!DNL Generate token]**.
1. Copiez le jeton d’accès généré et stockez-le dans un emplacement sécurisé.





