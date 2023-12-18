---
title: Synchronisation de OneAgent
description: Découvrez comment utiliser OneAgent de Dynamic avec AEM as a Cloud Service
source-git-commit: 2e70c8be73915bea860b98e02c08772bb4f5dcd2
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Synchronisation de OneAgent {#dynatrace-oneagent}

Adobe permet d’utiliser OneAgent de Dynamics pour surveiller AEM as a Cloud Service dans le cadre d’un déploiement d’entreprise, identifier la cause de tout problème potentiel et prendre des mesures pour y remédier si nécessaire. <!-- When GA, add: Read this [Dynatrace article](https://www.dynatrace.com/hub/detail/adobe-experience-manager/) about AEM monitoring to learn more. -->

## Intégration de OneAgent à AEM as a Cloud Service {#integrating-oneagent-with-aem-as-a-cloud-service}

Les clients Dynamic OneAgent peuvent surveiller leur utilisation AEM en demandant la connectivité par le biais d’un ticket d’assistance clientèle.

Les détails requis pour les demandes de connectivité sont décrits ci-dessous :

| **Champ** | **Description** |
|---|---|
| URL de l’environnement de synchronisation | URL de votre environnement de synchronisation.<br><br>Pour les clients Dynamic Media, le format est `https://<environment>.live.dynatrace.com`.<br><br>Pour les clients gérés par Dynamic Tag Management, le format est `https://<your-managed-url>/e/<environmentId>` |
| ID d’environnement de synchronisation | Votre identifiant d’environnement de synchronisation, qui se trouve dans l’URL de l’environnement. |
| Jeton d’environnement de synchronisation | Votre jeton d’environnement OneAgent. Pour savoir comment créer cette fonctionnalité, consultez la documentation de Dynatrace .<br><br>Cela doit être considéré comme un secret. Utilisez donc les pratiques de sécurité appropriées. Par exemple, un mot de passe le protège dans un site web tel que **zerobin.net**, à laquelle le ticket d’assistance clientèle peut faire référence, ainsi que le mot de passe. |
| Jeton d’accès de l’API de synchronisation | Jeton d’accès API de votre environnement de synchronisation. Pour savoir comment créer cette fonctionnalité, consultez la documentation de Dynatrace .<br><br>Ce secret doit être considéré comme un secret. Utilisez donc les pratiques de sécurité appropriées. Par exemple, un mot de passe le protège dans un site web tel que **zerobin.net**, à laquelle le ticket d’assistance clientèle peut faire référence, ainsi que le mot de passe.<br><br>Remarque : Cela n’est nécessaire que pour Dynatrace Managed. |
| Port de destination de la synchronisation | Port de destination de la synchronisation.<br><br>Remarque : Cela n’est nécessaire que pour Dynatrace Managed. |
| AEM ID d’environnement | ID d’environnement AEM que Dynamic doit surveiller. |


