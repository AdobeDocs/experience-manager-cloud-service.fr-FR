---
title: Sauvegarde et restauration dans AEM as a Cloud Service
description: Sauvegarde et restauration dans AEM as a Cloud Service
exl-id: 469fb1a1-7426-4379-9fe3-f5b0ebf64d74
source-git-commit: 706d33e4a07eb95c578996ffe8989fafeebaa06c
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 85%

---

# Sauvegarde et restauration dans AEM as a Cloud Service

>[!CONTEXTUALHELP]
>id="aemcloud_golive_backuprestore"
>title="Sauvegarde et restauration"
>abstract="AEM as a Cloud Service peut restaurer l’application complète (code et contenu) d’un client à des heures spécifiques prédéterminées au cours des sept derniers jours, en remplaçant ce qui était en production. Cette fonction ne doit être utilisée que lorsqu’il existe de graves problèmes de code ou de contenu. Les données récentes entre l’exécution de la sauvegarde restaurée et le moment présent seront perdues. L’évaluation sera également restaurée vers l’ancienne version."

En cas de corruption de contenu ou de données, AEM as a Cloud Service peut restaurer l’application complète (code et contenu) d’un client à des heures spécifiques prédéterminées au cours des sept derniers jours, en remplaçant ce qui était en production.
Si le déploiement d’un client, c’est-à-dire le code de l’application déployée, est endommagé ou affecté par un bogue, il est préférable de le corriger et de le restaurer dans une nouvelle version plutôt que de le restaurer à partir de la sauvegarde. La sauvegarde est effectuée de manière à n’avoir aucune incidence sur les performances d’exécution d’une application.

>[!CAUTION]
>
>Cette fonction ne doit être utilisée que lorsqu’il existe de graves problèmes de code ou de contenu. Les données récentes entre l’exécution de la sauvegarde restaurée et le moment présent seront perdues. L’évaluation sera également restaurée vers l’ancienne version.

## Utilisation

Les clients doivent déposer un ticket d’assistance, décrivant le problème rencontré. L’assistance d’Adobe procédera alors à une investigation qui déterminera si une restauration est nécessaire.

AEM as a Cloud Service prend en charge :

* La récupération à un point dans le temps sur 24 heures, ce qui signifie que le système peut être restauré à n’importe quel stade au cours des dernières 24 heures.
* La restauration à partir d’un horodatage spécifique défini par l’Adobe, prélevé deux fois par jour pendant les 7 derniers jours.  Tous les messages de réplication (suppressions, mises à jour, création) seront conservés.

Dans tous les cas, la version du code personnalisé est la version capturée à partir du dernier déploiement réussi avant le point de restauration.

L’objectif de temps de récupération (RTO) varie en fonction de la taille du référentiel, mais en règle générale, la séquence de récupération doit prendre entre 30 minutes et plusieurs heures.

Après une restauration, la version AEM est mise à jour vers la version la plus récente.

>[!CAUTION]
>
>Les données des environnements supprimés sont définitivement perdues et ne peuvent pas être récupérées.
