---
title: Mises à jour des versions AEM
description: 'Mises à jour des versions AEM '
translation-type: tm+mt
source-git-commit: 3d9ed5ea31344bf4e25c37368cca01856cdbbd01
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 38%

---


# AEM Version Updates {#aem-version-updates}

## Présentation {#introduction}

aem en tant que Cloud Service utilise maintenant l&#39;intégration continue et la Diffusion continue (CI/CD) pour s&#39;assurer que vos projets se trouvent sur la version AEM la plus récente. Cela signifie que toutes les opérations de mise à niveau sont entièrement automatisées et ne nécessitent donc aucune interruption de service pour les utilisateurs.

>[!NOTE]
>Si la mise à jour de l’environnement de production échoue, Cloud Manager annule automatiquement l’environnement d’évaluation. Cette opération est effectuée automatiquement pour s’assurer qu’une fois la mise à jour terminée, les environnements d’étape et de production se trouvent sur la même version AEM.

aem mises à jour de version sont de deux types :

* **Mises à jour Push AEM**

   * Peut être publié quotidiennement.

   * Principalement la maintenance, y compris les derniers correctifs de bogues et les mises à jour de sécurité.

      Les modifications étant appliquées régulièrement, l’impact est incrémentiel, ce qui réduit l’impact sur votre service.

* **Nouvelles fonctionnalités mises à jour**

   * Publié selon un calendrier mensuel prévisible.

aem mises à jour passent par un processus de validation de produit intense et entièrement automatisé, impliquant plusieurs étapes permettant de ne pas perturber le service des systèmes en production. Les contrôles d’intégrité servent à surveiller l’état de l’application. Si ces vérifications échouent lors d’un AEM en tant que mise à jour Cloud Service, la version ne sera pas publiée et l’Adobe examinera pourquoi la mise à jour a provoqué ce comportement inattendu.

[Les tests de produit et les tests](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/understand-test-results.html#functional-testing) de fonctionnement du client qui empêchent les mises à niveau de produit et les poussées de code client d’interrompre la production sont également validés lors d’une mise à jour de AEM version.

>[!NOTE]
>
>Si vous avez envoyé le code personnalisé pour évaluation, puis que vous l’avez rejeté, la prochaine mise à jour d’AEM supprimera ces modifications afin de refléter la balise git de la dernière version de production réussie du client.

## Magasin de nœuds composites {#composite-node-store}

Comme mentionné plus haut, les mises à jour n’entraînent dans la plupart des cas aucune interruption, y compris pour l’auteur, qui est une grappe de nœuds. Rolling updates are possible due to the *composite node store* feature in Oak.

Cette fonctionnalité permet à AEM de faire référence à plusieurs référentiels simultanément. Dans un déploiement en continu, la nouvelle version verte d’AEM contient son propre `/libs` (référentiel non modifiable basé sur TarMK), distinct de l’ancienne version bleue d’AEM, bien que les deux fassent référence à un référentiel modifiable partagé et basé sur DocumentMK qui contient des zones comme `/content`, `/conf`, `/etc` et d’autres. Comme les versions bleue et verte possèdent leur propre version de `/libs`, elles peuvent toutes deux être actives pendant la mise à jour en continu, se partageant le trafic jusqu’à ce que la version verte remplace complètement la bleue.

