---
title: Mises à jour de la version d’AEM
description: Découvrez comment AEM as a Cloud Service utilise l’intégration et la diffusion continues (CI/CD) pour conserver vos projets sur la dernière version.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: dd567c484d71e25de1808f784c455cfb9b124fbf
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 35%

---


# Mises à jour de la version d’AEM {#aem-version-updates}

Découvrez comment AEM as a Cloud Service utilise l’intégration et la diffusion continues (CI/CD) pour conserver vos projets sur la dernière version.

## CI/CD {#ci-cd}

AEM as a Cloud Service utilise l’intégration continue et la diffusion continue (CI/CD) pour garantir que vos projets utilisent la version d’AEM la plus récente. Ce processus met à jour en toute transparence vos instances de production, d’évaluation et de développement sans pour autant perturber vos utilisateurs.

Avant que vos instances ne soient automatiquement mises à jour, une nouvelle version de maintenance d’AEM est publiée 3 à 5 jours à l’avance. Au cours de cette période, vous avez la possibilité de
[déclencher des mises à jour manuelles pour vos instances de développement ;](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment).
Une fois ce temps écoulé, les mises à jour de version sont automatiquement appliquées en premier à vos environnements de développement. Si la mise à jour est réussie, le processus de mise à jour se poursuit vers vos instances d’évaluation et de production. Les instances de développement et d’évaluation agissent comme un point de contrôle de qualité automatisé, où vos tests écrits personnalisés sont exécutés avant l’application de la mise à jour à votre environnement de production.

>[!NOTE]
>
> Remarque : les mises à jour automatiques des environnements de développement seront progressivement activées en 2023 pour tous les clients. Si vos environnements de développement ne sont pas automatiquement mis à jour, vous pouvez utiliser des mises à jour manuelles pour les synchroniser avec vos environnements intermédiaire et de production.


## Type de mises à jour {#update-types}

Il existe deux types de mises à jour de la version d’AEM :

* **Mises à jour de maintenance AEM**

   * Elles peuvent être publiées quotidiennement.
   * Elles sont principalement destinées à la maintenance et comprennent les derniers correctifs de bugs et les mises à jour de sécurité.
   * Elles ont un impact minimal, car les modifications apportées à AEM sont appliquées régulièrement.

* **Mises à jour avec de nouvelles fonctionnalités**

   * Elles sont publiées selon un [calendrier mensuel et prévisible.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr)

## Échec de la mise à jour {#update-failure}

Les mises à jour d’AEM passent par un pipeline de validation de produit avancé et entièrement automatisé, impliquant plusieurs étapes et ne perturbant pas le service des systèmes en production.
Les contrôles d’intégrité servent à surveiller l’état de l’application.
Si ces vérifications échouent lors d’une mise à jour as a Cloud Service AEM, la version ne sera pas publiée et l’Adobe examinera les raisons pour lesquelles la mise à jour a provoqué ce comportement inattendu.

Lorsque vous déployez une nouvelle version d’un code personnalisé de sur vos environnements,
[Tests fonctionnels sur les produits et personnalisés](/help/implementing/cloud-manager/overview-test-results.md#functional-testing)
jouer un rôle essentiel pour s’assurer que les systèmes de production restent stables et fonctionnels même après l’application d’un changement. Ces tests sont également utilisés dans le processus de mise à jour de version d’AEM.

Si la mise à jour de l’environnement de production échoue, Cloud Manager restaurera automatiquement l’environnement d’évaluation. Cela permet de s’assurer automatiquement qu’une fois la mise à jour terminée, les environnements d’évaluation et de production se trouvent tous deux sur la même version AEM.
De même, si une mise à jour automatisée d’un environnement de développement échoue, les environnements d’évaluation et de production ne sont pas mis à jour.

>[!NOTE]
>
>Si du code personnalisé a été soumis à l’évaluation et non à la production, la prochaine mise à jour d’AEM supprimera ces modifications afin de refléter la balise Git de la dernière version de production réussie du client. Par conséquent, le code personnalisé qui n’avait été déployé qu’en phase d’évaluation devra être déployé à nouveau.

## Magasin de nœuds composites {#composite-node-store}

Dans la plupart des cas, les mises à jour n’entraînent aucune interruption, y compris pour l’instance de création, qui est une grappe de noeuds. Les mises à jour en continu sont possibles en raison de [la fonctionnalité de magasin de nœuds composites dans Oak.](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html)

Cette fonctionnalité permet à AEM de faire référence à plusieurs référentiels simultanément. Dans un [déploiement en continu,](/help/implementing/deploying/overview.md#how-rolling-deployments-work) la nouvelle version d’AEM contient sa propre version `/libs` (référentiel non modifiable basé sur TarMK), distinct de l’ancienne version d’AEM, bien que les deux fassent référence à un référentiel modifiable partagé basé sur DocumentMK qui contient des zones comme `/content` , `/conf` , `/etc` et autres.

Parce que les anciennes et les nouvelles versions ont leurs propres versions de `/libs`, ils peuvent être principaux pendant la mise à jour en continu et prendre en charge le trafic jusqu’à ce que l’ancien soit complètement remplacé par le nouveau.
