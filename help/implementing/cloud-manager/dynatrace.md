---
title: Dynatrace
description: Découvrez comment utiliser la synchronisation avec AEM as a Cloud Service
exl-id: b58c8b82-a098-4d81-bc36-664e890c8f66
source-git-commit: a234f2a00c51bcb23b0c52feac9971259d26b8c3
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# Dynatrace {#dynatrace}

Adobe permet d’utiliser Dynamic pour surveiller AEM as a Cloud Service dans le cadre du déploiement en entreprise, identifier la cause de tout problème potentiel et prendre des mesures pour y remédier, le cas échéant.

Avec Dynatrace, vous pouvez obtenir une observabilité transparente pour toutes vos applications AEM. La synchronisation offre une visibilité complète sur l’expérience de l’utilisateur final en détectant automatiquement vos applications AEM et en visualisant leurs dépendances du site web au conteneur vers le service cloud. Liées aux traces de bout en bout à tous les niveaux et à la surveillance des utilisateurs réels, redirigez vos expériences AEM basées sur le contenu vers le niveau suivant sans espaces ni angles morts. En cas d’anomalies, Dynatrace les diagnostique en temps réel avec le moteur Davis AI et identifie la cause principale jusqu’au code rompu avant que vos clients ne soient affectés, ce qui réduit le temps moyen de réparation.

Pour en savoir plus sur la synchronisation, voir [Intégration d’Adobe AEM Cloud Service](https://www.dynatrace.com/hub/detail/adobe-experience-manager-1/).

![AEM des mesures de performances de création et d’éditeur](/help/implementing/cloud-manager/assets/dynatrace-performance-metrics.png)

## Intégration de la synchronisation avec AEM as a Cloud Service {#integrating-dynatrace-with-aem-as-a-cloud-service}

Les clients de Dynamic Media peuvent surveiller leurs environnements AEM en demandant la connectivité par le biais d’un ticket d’assistance clientèle.

Les détails requis pour les demandes de connectivité sont décrits ci-dessous :

| **Champ** | **Description** |
|---|---|
| URL de l’environnement de synchronisation | URL de votre environnement de synchronisation.<br><br>Pour les clients Dynamic Media, le format est `https://<your-environment-id>.live.dynatrace.com`.<br><br>Pour les clients gérés par Dynamic Tag Management, le format est `https://<your-managed-url>/e/<environmentId>` |
| ID d’environnement de synchronisation | Identifiant de votre environnement de synchronisation. Veuillez consulter [Obtention des informations sur l’environnement de synchronisation](#get-dynatrace-env-info) pour savoir comment obtenir ceci. |
| Jeton d’environnement de synchronisation | Jeton d’environnement de synchronisation. Veuillez consulter [Obtention des informations sur l’environnement de synchronisation](#get-dynatrace-env-info) pour savoir comment obtenir ceci.<br><br>Cela doit être considéré comme un secret. Utilisez donc les pratiques de sécurité appropriées. Par exemple, un mot de passe le protège dans un site web tel que **zerobin.net**, à laquelle le ticket d’assistance clientèle peut faire référence, ainsi que le mot de passe. |
| Jeton d’accès de l’API de synchronisation | Jeton d’accès API de votre environnement de synchronisation.  Veuillez consulter [Création d’un jeton d’accès à l’API de synchronisation](#create-dynatrace-access-token) pour savoir comment créer ceci.<br><br>Ce secret doit être considéré comme un secret. Utilisez donc les pratiques de sécurité appropriées. Par exemple, un mot de passe le protège dans un site web tel que **zerobin.net**, à laquelle le ticket d’assistance clientèle peut faire référence, ainsi que le mot de passe.<br><br>Remarque : Cela n’est nécessaire que pour Dynatrace Managed. |
| Synchronisation du port ActiveGate | Votre port Dynamic ActiveGate auquel l’intégration d’AEM doit se connecter.<br><br>Remarque : Cela n’est nécessaire que pour Dynatrace Managed. |
| Synchronisation de la zone réseau ActiveGate | Votre [Synchronisation de la zone de réseau ActiveGate](https://docs.dynatrace.com/docs/manage/network-zones) pour acheminer efficacement les données de surveillance AEM entre les centres de données et les régions de réseau.<br><br>Remarque : Une zone de réseau Dynamic ActiveGate est facultative. |
| AEM ID d’environnement | Les identifiants d’environnement AEM que Dynamic doit surveiller. |

>[!NOTE]
>
>Une fois la synchronisation intégrée, les données ne sont plus transmises à d’autres outils APM tels que New Relic, si elles ont été activées auparavant.


## Création d’un jeton d’accès à l’API de synchronisation {#create-dynatrace-access-token}

1. Connectez-vous à votre environnement de synchronisation.
1. Dans le menu Synchronisation, accédez à Gérer > Accéder aux jetons.
1. Sélectionnez Générer un nouveau jeton.
1. Définissez un nom de jeton.

1. Facultatif : définissez une date d’expiration. Veillez à générer un nouveau jeton avant son expiration.
1. Définissez la portée du jeton sur Intégration PaaS - Téléchargement du programme d’installation
1. Sélectionnez Générer un jeton.
1. Copiez le jeton d’accès généré et stockez-le dans un emplacement sécurisé.


## Obtention des informations sur l’environnement de synchronisation {#get-dynatrace-env-info}

1. Exécutez la requête d’API suivante sur votre environnement de synchronisation :

`curl -X GET "<environmentUrl>/api/v1/deployment/installer/agent/connectioninfo" -H "accept: application/json" -H "Authorization: Api-Token <accessToken>"`

Remplacer \&lt;environmenturl> avec l’URL de votre environnement de synchronisation et \&lt;accesstoken> avec votre jeton d’accès API créé.

1. Copiez le \&lt;environmentid> et \&lt;environmenttoken> à partir du payload de la réponse et stockez-les dans un emplacement sécurisé.

```
{
   "tenantUUID": "<environmentId>",
   "tenantToken": "<environmentToken>",
   "communicationEndpoints": [
   ... 
   ],
   "formattedCommunicationEndpoints": "<endpoints>" 
}
```


