---
title: Mises à jour de la version d’AEM
description: 'Mises à jour de la version d’AEM '
translation-type: tm+mt
source-git-commit: 78c0802a0703e81941013347a3f4b57cb106c927
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 100%

---


# Mises à jour de la version d’AEM {#aem-version-updates}

## Introduction {#introduction}

AEM as a Cloud Service utilise maintenant l’intégration et la distribution continues (CI/CD) pour s’assurer que vos projets bénéficient de la version d’AEM la plus récente. Les instances de production et d’évaluation sont donc mises à jour à la dernière version d’AEM sans interruption de service pour les utilisateurs.

>[!NOTE]
>Si la mise à jour de l’environnement de production échoue, Cloud Manager restaure automatiquement l’environnement d’évaluation. Cette opération est effectuée automatiquement pour s’assurer qu’une fois la mise à jour terminée, les environnements d’évaluation et de production se trouvent sur la même version d’AEM.

Les mises à jour de la version d’AEM sont de deux types :

* **Mises à jour Push d’AEM**

   * Elles peuvent être publiées quotidiennement.

   * Il s’agit principalement de maintenance, notamment les derniers correctifs de bogues et les mises à jour de sécurité.

      Les modifications étant appliquées régulièrement, l’impact est incrémentiel, ce qui réduit l’incidence sur votre service.

* **Nouvelles mises à jour de fonctionnalités**

   * Elles sont publiées selon un calendrier mensuel prévisible.

Les mises à jour d’AEM passent par un pipeline de validation de produit intense et entièrement automatisé, impliquant plusieurs étapes permettant de ne pas perturber le service des systèmes en production. Les contrôles d’intégrité servent à surveiller l’état de l’application. Si ces contrôles échouent lors d’une mise à jour d’AEM as a Cloud Service, la version ne sera pas publiée et Adobe examinera les raisons pour lesquelles la mise à jour a provoqué ce comportement inattendu.

[Les tests de produits et les tests fonctionnels du client](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/implementing/developing/understand-test-results.html#functional-testing), qui empêchent que les mises à niveau de produit et les publications de code client interrompent la production, sont également validés lors d’une mise à jour de la version d’AEM.

>[!NOTE]
>
>Si vous avez envoyé le code personnalisé pour évaluation, puis que vous l’avez rejeté, la prochaine mise à jour d’AEM supprimera ces modifications afin de refléter la balise git de la dernière version de production réussie du client.

## Magasin de nœuds composites {#composite-node-store}

Comme mentionné plus haut, les mises à jour n’entraînent dans la plupart des cas aucune interruption, y compris pour l’auteur, qui est une grappe de nœuds. Les mises à jour en continu sont possibles en raison de la *fonctionnalité de magasin de nœuds composites* dans Oak.

Cette fonctionnalité permet à AEM de faire référence à plusieurs référentiels simultanément. Dans un déploiement en continu, la nouvelle version verte d’AEM contient son propre `/libs` (référentiel non modifiable basé sur TarMK), distinct de l’ancienne version bleue d’AEM, bien que les deux fassent référence à un référentiel modifiable partagé et basé sur DocumentMK qui contient des zones comme `/content`, `/conf`, `/etc` et d’autres. Comme les versions bleue et verte possèdent leur propre version de `/libs`, elles peuvent toutes deux être actives pendant la mise à jour en continu, se partageant le trafic jusqu’à ce que la version verte remplace complètement la bleue.

