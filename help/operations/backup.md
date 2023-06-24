---
title: Sauvegarde et restauration dans AEM as a Cloud Service
description: Sauvegarde et restauration dans AEM as a Cloud Service
exl-id: 469fb1a1-7426-4379-9fe3-f5b0ebf64d74
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 45%

---


# Sauvegarde et restauration dans AEM as a Cloud Service {#backup-aemaacs}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_backuprestore"
>title="Sauvegarde et restauration"
>abstract="AEM as a Cloud Service peut restaurer l’application complète (code et contenu) d’un client à des heures spécifiques prédéterminées au cours des sept derniers jours, en remplaçant ce qui était en production. Cette fonction ne doit être utilisée que lorsqu’il existe de graves problèmes de code ou de contenu. Les données récentes entre le moment de la sauvegarde restaurée et le moment présent sont perdues. L’évaluation est également restaurée à l’ancienne version."

En cas de corruption de contenu ou de données, AEM as a Cloud Service peut restaurer l’application complète d’un client (code et contenu). Il est restauré à des heures spécifiques et prédéterminées au cours des sept derniers jours, remplaçant ce qui était en production.
Si le déploiement d’un client, c’est-à-dire le code de l’application déployée, est endommagé ou affecté par un bogue, il est préférable de le corriger et de le restaurer dans une nouvelle version plutôt que de le restaurer à partir de la sauvegarde. La sauvegarde est effectuée de manière à n’avoir aucune incidence sur les performances d’exécution d’une application.

>[!CAUTION]
>
>Cette fonction ne doit être utilisée que lorsqu’il existe de graves problèmes de code ou de contenu. Les données récentes entre le moment de la sauvegarde restaurée et le moment présent sont perdues. L’évaluation est également restaurée à l’ancienne version.

## Utilisation {#how-to-use}

Les clients doivent déposer un ticket d’assistance, décrivant le problème rencontré. Le ticket d’assistance mène généralement à une enquête par l’assistance Adobe qui peut ensuite déterminer si une restauration est nécessaire.

AEM as a Cloud Service prend en charge :

* Sauvegarde et restauration pour les environnements d’évaluation, de production et de développement.
* Récupération ponctuelle de 24 heures, ce qui signifie que le système peut être restauré à n’importe quel moment au cours des dernières 24 heures.
* La restauration à partir d’un horodatage spécifique défini par l’Adobe, prélevé deux fois par jour pendant les sept derniers jours. Tous les messages de réplication (suppressions, mises à jour, création) sont conservés.

Dans tous les cas, la version de code personnalisé est récupérée à partir du dernier déploiement réussi avant le point de restauration.

L’objectif de temps de récupération (RTO) peut varier, mais en règle générale, la séquence de récupération prend en moyenne de 60 à 90 minutes selon plusieurs facteurs, tels que la taille du référentiel. Les environnements d’aperçu et les éditeurs multi-régions peuvent prolonger l’objectif de temps de restauration.

Après une restauration, la version AEM est mise à jour vers la version la plus récente.

>[!CAUTION]
>
>Les données des environnements supprimés sont définitivement perdues et ne peuvent pas être récupérées.

## Sauvegarde hors site {#offsite-backup}

Bien que des sauvegardes régulières couvrent le risque de suppressions accidentelles ou de défaillances techniques dans les services cloud d’AEM, les risques pouvant résulter de l’échec d’une zone géographique doivent également être pris en compte. Outre la disponibilité, le risque le plus important dans ce type de panne est principalement la perte de données.
AEM as a Cloud Service couvre ce risque en standard pour tous les environnements de production AEM. Il copie en permanence l’ensemble du contenu de l’AEM dans une région distante et le rend disponible pour récupération pendant trois mois. Adobe appelle cette fonctionnalité Sauvegarde hors site.
La restauration d’AEM Cloud Services pour les environnements intermédiaires et de production est effectuée par l’ingénierie de fiabilité AEM service en cas de panne de la région de données.
