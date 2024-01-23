---
title: Sauvegarde et restauration dans AEM as a Cloud Service
description: En savoir plus sur la sauvegarde et la restauration dans AEM as a Cloud Service
exl-id: 469fb1a1-7426-4379-9fe3-f5b0ebf64d74
source-git-commit: b77ee0697e8f6f4aeaa6651336588f1c5321abd1
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 92%

---


# Sauvegarde et restauration dans AEM as a Cloud Service {#backup-aemaacs}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_backuprestore"
>title="Sauvegarde et restauration"
>abstract="AEM as a Cloud Service peut restaurer l’application complète (code et contenu) d’un client à des heures spécifiques prédéterminées au cours des sept derniers jours, en remplaçant ce qui était en production. Cette fonction ne doit être utilisée que lorsqu’il existe de graves problèmes de code ou de contenu. Les données récentes entre l’exécution de la sauvegarde restaurée et le moment présent sont perdues. L’évaluation est également restaurée vers l’ancienne version."

En cas de corruption de contenu ou de données, AEM as a Cloud Service peut restaurer l’application complète d’un client ou d’une cliente (code et contenu). Elle est restaurée à des heures spécifiques et prédéfinies au cours des sept derniers jours, remplaçant ce qui était en production.
Si le déploiement d’un client, c’est-à-dire le code de l’application déployée, est endommagé ou affecté par un bogue, il est préférable de le corriger et de le restaurer dans une nouvelle version plutôt que de le restaurer à partir de la sauvegarde. La sauvegarde est effectuée de manière à n’avoir aucune incidence sur les performances d’exécution d’une application.

>[!CAUTION]
>
>Cette fonction ne doit être utilisée que lorsqu’il existe de graves problèmes de code ou de contenu. Les données récentes entre l’exécution de la sauvegarde restaurée et le moment présent sont perdues. L’évaluation est également restaurée à l’ancienne version. Si des données récentes sont conservées, elles doivent être exportées par le biais d’un package de contenu avant la restauration, puis réinstallées sur le référentiel restauré.

## Utilisation {#how-to-use}

Les clients doivent déposer un ticket d’assistance, décrivant le problème rencontré. Le ticket d’assistance mène généralement à une enquête par l’assistance Adobe qui peut ensuite déterminer si une restauration est nécessaire.

AEM as a Cloud Service prend en charge :

* La sauvegarde et la restauration des environnements d’évaluation, de production et de développement.
* La récupération à un point dans le temps sur 24 heures, ce qui signifie que le système peut être restauré à n’importe quel stade au cours des dernières 24 heures.
* La restauration à partir d’un horodatage spécifique défini par Adobe, exécuté deux fois par jour pendant les sept derniers jours. Tous les messages de réplication (suppressions, mises à jour, créations) sont conservés.

Dans tous les cas, la version du code personnalisé est la version capturée à partir du dernier déploiement réussi avant le point de restauration.

L’objectif de temps de récupération (RTO) peut varier, mais en règle générale, la séquence de récupération prend entre 60 et 90 minutes en moyenne en fonction de plusieurs facteurs, tels que la taille du référentiel. Les environnements d’aperçu et les éditeurs multi-régions peuvent prolonger l’objectif de temps de restauration.

Après une restauration, la version AEM est mise à jour vers la version la plus récente.

>[!CAUTION]
>
>Les données des environnements supprimés sont définitivement perdues et ne peuvent pas être récupérées.

## Sauvegarde hors site {#offsite-backup}

Bien que des sauvegardes régulières couvrent le risque de suppressions accidentelles ou de défaillances techniques dans les services cloud d’AEM, les risques pouvant résulter de l’échec d’une zone géographique doivent également être pris en compte. Outre la disponibilité, le risque le plus important dans ce type de panne est principalement la perte de données.
AEM as a Cloud Service protège contre ce risque en standard pour tous les environnements de production AEM. Il copie en permanence l’ensemble du contenu d’AEM dans une région distante et le rend disponible pour récupération pendant trois mois. Adobe appelle cette fonctionnalité Sauvegarde hors site.
La restauration des services cloud d’AEM pour les environnements d’évaluation et de production est effectuée par l’ingénierie en charge de la fiabilité des services AEM en cas de pannes liées aux données dans certaines zones géographiques.
