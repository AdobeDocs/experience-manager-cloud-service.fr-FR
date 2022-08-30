---
title: Mises à jour de la version d’AEM
description: 'Mises à jour de la version d’AEM '
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: 575be022704e998e63162f19c37ece877efef627
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 29%

---


# Mises à jour de la version d’AEM {#aem-version-updates}

## Présentation  {#introduction}

AEM as a Cloud Service utilise désormais l’intégration continue et la diffusion continue (CI/CD) pour s’assurer que vos projets utilisent la version AEM la plus récente. Cela signifie que les instances de production et d’évaluation sont mises à jour vers la dernière version d’AEM sans interruption de service pour les utilisateurs.

>[!NOTE]
>
>Si la mise à jour de l’environnement de production échoue, Cloud Manager restaure automatiquement l’environnement d’évaluation. Cela permet de s’assurer automatiquement qu’une fois la mise à jour terminée, les environnements d’évaluation et de production se trouvent sur la même version AEM.

Il existe deux types de mises à jour AEM version :

* **AEM mises à jour de maintenance**

   * Elles peuvent être publiées quotidiennement.
   * Sont principalement à des fins de maintenance, y compris les derniers correctifs de bogues et les mises à jour de sécurité.
   * ont un impact minimal, car les modifications sont appliquées régulièrement ;

* **Nouvelles mises à jour de fonctionnalités**

   * Sont publiées selon un calendrier mensuel prévisible.

AEM mises à jour passent par un pipeline de validation de produit intense et entièrement automatisé, impliquant plusieurs étapes, ce qui n’assure aucune interruption de service pour les systèmes en production. Les contrôles d’intégrité servent à surveiller l’état de l’application. Si ces contrôles échouent lors d’une mise à jour d’AEM as a Cloud Service, la version ne sera pas publiée et Adobe examinera les raisons pour lesquelles la mise à jour a provoqué ce comportement inattendu.

[Tests de produit et tests fonctionnels du client,](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) qui empêchent les mises à niveau de produit et les transmissions de code client de casser les systèmes de production, sont également validés lors d’une mise à jour de version d’AEM.

>[!NOTE]
>
>Si vous avez envoyé le code personnalisé pour évaluation, puis que vous l’avez rejeté, la prochaine mise à jour d’AEM supprimera ces modifications afin de refléter la balise git de la dernière version de production réussie du client.

## Magasin de nœuds composites {#composite-node-store}

Dans la plupart des cas, les mises à jour n’entraînent aucune interruption, y compris pour l’instance de création, qui est un cluster de noeuds. Les mises à jour en continu sont possibles en raison de la fonctionnalité de magasin de nœuds composites dans Oak.

Cette fonctionnalité permet à AEM de faire référence à plusieurs référentiels simultanément. Dans un déploiement en continu, la nouvelle version verte AEM contient sa propre version `/libs` (référentiel non modifiable basé sur TarMK), distinct de l’ancienne version bleue de l’AEM, bien que les deux fassent référence à un référentiel modifiable partagé basé sur DocumentMK qui contient des zones comme `/content` , `/conf` , `/etc` et autres. Parce que le bleu et le vert possèdent leur propre version de `/libs`, elles peuvent toutes deux être principales pendant la mise à jour en continu, en prenant toutes deux en charge le trafic jusqu’à ce que le bleu soit complètement remplacé par le vert.
