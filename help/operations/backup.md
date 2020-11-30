---
title: Sauvegarde et restauration dans AEM as a Cloud Service
description: 'Sauvegarde et restauration dans AEM as a Cloud Service '
translation-type: tm+mt
source-git-commit: c3af507716ef60541ecca8dafb797651e8ece9d3
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 100%

---


# Sauvegarde et restauration dans AEM as a Cloud Service

En cas de corruption de contenu ou de données, AEM as a Cloud Service peut restaurer l’application complète (code et contenu) d’un client à des heures spécifiques prédéterminées au cours des sept derniers jours, en remplaçant ce qui était en production.
Si le déploiement d’un client, c’est-à-dire le code de l’application déployée, est endommagé ou affecté par un bogue, il est préférable de le corriger et de le restaurer dans une nouvelle version plutôt que de le restaurer à partir de la sauvegarde. La sauvegarde est effectuée de manière à n’avoir aucune incidence sur les performances d’exécution d’une application.

>[!CAUTION]
>
>Cette fonction ne doit être utilisée que lorsqu’il existe de graves problèmes de code ou de contenu. Les données récentes entre l’exécution de la sauvegarde restaurée et le moment présent seront perdues. L’évaluation sera également restaurée vers l’ancienne version.

## Utilisation

Les clients doivent déposer un ticket d’assistance, décrivant le problème rencontré. L’assistance d’Adobe procédera alors à une investigation qui déterminera si une restauration est nécessaire.

AEM as a Cloud Service prend en charge :

* La récupération à un point dans le temps sur 24 heures, ce qui signifie que le système peut être restauré à n’importe quel stade au cours des dernières 24 heures.
* La restauration à partir d’un horodatage spécifique défini par Adobe, capturé une fois par jour pendant les 7 derniers jours.  Tous les messages de réplication (suppressions, mises à jour, création) seront conservés.

Dans tous les cas, la version du code personnalisé est la version capturée à partir du dernier déploiement réussi avant le point de restauration.

L’objectif de temps de récupération (RTO) varie en fonction de la taille du référentiel mais, en règle générale, une fois la séquence de restauration lancée, elle devrait prendre environ 30 minutes.

Après une restauration, la version AEM est mise à jour vers la version la plus récente.

**Les données des environnements supprimés sont définitivement perdues et ne peuvent pas être récupérées.**
