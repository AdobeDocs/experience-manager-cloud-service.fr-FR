---
title: Sauvegarde et restauration dans AEM en tant que service Cloud
description: 'Sauvegarde et restauration dans AEM en tant que service Cloud '
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e

---


# Sauvegarde et restauration dans AEM en tant que service Cloud

En cas de corruption de contenu ou de données, AEM en tant que service Cloud peut restaurer l’application complète (code et contenu) d’un client à des heures prédéterminées au cours des sept derniers jours, en remplaçant ce qui était en production.
Si le déploiement d’un client, c’est-à-dire que le code de l’application déployée est défectueux ou défectueux, il est préférable de le corriger et de le restaurer dans une nouvelle version plutôt que de le restaurer à partir d’une sauvegarde.

>[!CAUTION]
>
>Cette fonctionnalité ne doit être utilisée que lorsqu’il existe des problèmes graves avec le code ou le contenu. Les données récentes entre le moment de la sauvegarde restaurée et le présent seront perdues. L’évaluation sera également restaurée dans l’ancienne version.

## Procédure d’utilisation

Les clients doivent déposer un ticket d’assistance décrivant le problème rencontré. Le service d’assistance d’Adobe examinera alors si une restauration est nécessaire.

AEM as a Cloud Service prend en charge :

* Récupération 24 heures sur 24, ce qui signifie que le système peut être restauré à n&#39;importe quel point au cours des dernières 24 heures.
* Effectuez une restauration à partir d’un horodatage spécifique défini par Adobe, effectué une fois par jour pendant les 7 derniers jours.  Les messages de réplication (suppressions, mises à jour, création) seront conservés.

Dans tous les cas, la version du code personnalisé sera celle qui sera prise à partir du dernier déploiement réussi avant le point de restauration.

L&#39;objectif de temps de récupération (RTO) varie en fonction de la taille du référentiel, mais comme directive générale, une fois la séquence de restauration commencée, elle devrait prendre environ 30 minutes.

Après une restauration, la version d’AEM sera mise à jour vers la version la plus récente.

**Les données des environnements supprimés sont définitivement perdues et ne peuvent pas être récupérées.**
