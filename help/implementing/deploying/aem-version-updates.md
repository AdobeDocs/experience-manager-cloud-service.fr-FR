---
title: Mises à jour de la version d’AEM
description: Découvrez comment AEM as a Cloud Service utilise l’intégration et la diffusion continues (CI/CD) pour conserver vos projets sur la dernière version.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 54%

---


# Mises à jour de la version d’AEM {#aem-version-updates}

Découvrez comment AEM as a Cloud Service utilise l’intégration et la diffusion continues (CI/CD) pour conserver vos projets sur la dernière version.

## CI/CD {#ci-cd}

AEM as a Cloud Service utilise l’intégration continue et la diffusion continue (CI/CD) pour s’assurer que vos projets utilisent la version AEM la plus récente. Cela signifie que les instances de production et d’évaluation sont mises à jour vers la version d’AEM la plus récente sans aucune interruption de service pour les utilisateurs et utilisatrices.

Les mises à jour de version sont appliquées automatiquement aux instances de production et d’évaluation uniquement. [AEM mises à jour doivent être appliquées manuellement à toutes les autres instances](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment).

## Type de mises à jour {#update-types}

Il existe deux types de mises à jour de la version d’AEM :

* **Mises à jour de maintenance AEM**

   * Elles peuvent être publiées quotidiennement.
   * Elles sont principalement destinées à la maintenance et comprennent les derniers correctifs de bugs et les mises à jour de sécurité.
   * Elles ont un impact minimal, car les modifications apportées à AEM sont appliquées régulièrement.

* **Mises à jour avec de nouvelles fonctionnalités**

   * Sont publiées sur un [planification mensuelle prévisible.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr)

## Échec de la mise à jour {#update-failure}

Les mises à jour d’AEM passent par un pipeline de validation de produit avancé et entièrement automatisé, impliquant plusieurs étapes et ne perturbant pas le service des systèmes en production. Les contrôles d’intégrité servent à surveiller l’état de l’application. Si ces contrôles échouent lors d’une mise à jour d’AEM as a Cloud Service, la version ne sera pas publiée et Adobe examinera les raisons pour lesquelles la mise à jour a provoqué ce comportement inattendu.

[Les tests de produits et les tests fonctionnels du client](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) qui empêchent que les mises à niveau de produit et les publications de code client interrompent la production, sont également validés lors d’une mise à jour de la version d’AEM.

Si la mise à jour de l’environnement de production échoue, Cloud Manager restaurera automatiquement l’environnement d’évaluation. Cette opération s’effectue automatiquement afin de s’assurer qu’une fois la mise à jour terminée, les environnements d’évaluation et de production utilisent la même version d’AEM.

>[!NOTE]
>
>Si du code personnalisé a été soumis à l’évaluation et non à la production, la prochaine mise à jour d’AEM supprimera ces modifications afin de refléter la balise Git de la dernière version de production réussie du client. Par conséquent, le code personnalisé qui n’avait été déployé qu’en phase d’évaluation devra être déployé à nouveau.

## Magasin de nœuds composites {#composite-node-store}

Dans la plupart des cas, les mises à jour n’entraînent aucune interruption, y compris pour l’instance de création, qui est une grappe de noeuds. Les mises à jour en continu sont possibles en raison des [la fonctionnalité de magasin de noeuds composites dans Oak.](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html)

Cette fonctionnalité permet à AEM de faire référence à plusieurs référentiels simultanément. Dans un [déploiement en continu,](/help/implementing/deploying/overview.md#how-rolling-deployments-work) la nouvelle version d’AEM contient sa propre version `/libs` (référentiel non modifiable basé sur TarMK), distinct de l’ancienne version d’AEM, bien que les deux fassent référence à un référentiel modifiable partagé basé sur DocumentMK qui contient des zones comme `/content` , `/conf` , `/etc` et autres.

Parce que les anciennes et les nouvelles versions ont leurs propres versions de `/libs`, ils peuvent être principaux pendant la mise à jour en continu et prendre en charge le trafic jusqu’à ce que l’ancien soit complètement remplacé par le nouveau.
