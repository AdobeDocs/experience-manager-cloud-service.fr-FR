---
title: Mises à jour de la version d’AEM
description: Découvrez comment Adobe Experience Manager (AEM) as a Cloud Service utilise l’intégration et la diffusion continues (CI/CD) pour que vos projets utilisent la dernière version.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
role: Admin
source-git-commit: 01de7b0c4e0408a3bbc5322e37db5075d43c4c5f
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 10%

---


# Mises à jour de la version d’AEM {#aem-version-updates}

Découvrez comment Adobe Experience Manager (AEM) as a Cloud Service utilise l’intégration et la diffusion continues (CI/CD) pour que vos projets utilisent la dernière version.

## CI/CD {#ci-cd}

AEM as a Cloud Service utilise l’intégration continue et la diffusion continue (CI/CD) pour garantir que vos projets utilisent la version d’AEM la plus récente. Ce processus met à jour vos instances de production, d’évaluation et de développement en toute transparence, sans perturber les utilisateurs.

>[!NOTE]
> Comme les instances de développement sont déjà mises à jour automatiquement, les mises à jour manuelles pour les instances de développement peuvent ne pas être disponibles pour _certains_ de vos programmes. Cette fonctionnalité est en cours de transition vers les mises à jour automatiques.

Avant que vos instances ne soient automatiquement mises à jour, une nouvelle version de maintenance d’AEM est publiée 3 à 5 jours à l’avance. Pendant cette période, votre instance de développement peut être automatiquement mise à jour ou, si elle est disponible, vous pouvez éventuellement [déclencher la mise à jour de vos instances de développement](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment). Les mises à jour de version sont automatiquement appliquées en premier à vos environnements de développement. Si la mise à jour est réussie, le processus de mise à jour se poursuit vers vos instances d’évaluation et de production. Les instances de développement et d’évaluation font office de point de contrôle qualité automatisé, où vos tests écrits et personnalisés sont exécutés avant que la mise à jour ne soit appliquée à votre environnement de production.

### NIMU (mises à jour de maintenance non intrusives) {#nimu}

Les mises à jour de maintenance non intrusives sont des mises à jour automatiques appliquées sans impliquer les pipelines du client.
Grâce à NIMU, le client peut utiliser le pipeline à tout moment, même si une mise à jour de la version d’AEM est planifiée ou en cours et que les mises à jour de maintenance n’apparaissent plus dans l’historique d’exécution du pipeline client, ce qui facilite le suivi de l’historique des déploiements de code.

#### Mettre à jour les activités

La version actuelle d’AEM peut toujours être vérifiée pour chaque environnement, comme auparavant, à l’aide du panneau Environnements de l’interface utilisateur de Cloud Manager . Les mêmes points de contrôle qualité que ceux utilisés dans le pipeline sont utilisés par les mises à jour de maintenance non intrusives, y compris les tests écrits par le client.
Une notification de l’interface utilisateur de Cloud Manager [](/help/implementing/cloud-manager/notifications.md) sera envoyée chaque fois qu’une mise à jour de maintenance non intrusive est appliquée aux environnements de votre programme. Vous pouvez également configurer son envoi à votre adresse e-mail.

>[!NOTE]
>
> Remarque : les mises à jour de maintenance non intrusive seront progressivement activées pour tous les clients en 2024.

## Type de mises à jour {#update-types}

Il existe deux types de mises à jour de la version d’AEM :

* [**Mises à jour de maintenance AEM**](/help/release-notes/maintenance/latest.md)

   * Elles sont principalement destinées à la maintenance et comprennent les derniers correctifs de bugs et les mises à jour de sécurité.
   * L’impact est minimal, car les modifications sont appliquées régulièrement.

* [**Activation de fonctionnalités AEM**](/help/release-notes/release-notes-cloud/release-notes-current.md)

   * Elles sont publiées selon un calendrier mensuel et prévisible.

>[!NOTE]
>
> Vérifiez les dates clés des versions mensuelles de la feuille de route des versions d’[Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr#aem-as-cloud-service) et annotez vos calendriers pour vous préparer aux activités clés afin de vous préparer à la version.

## Échec de la mise à jour {#update-failure}

Les mises à jour d’AEM passent par un pipeline de validation de produit avancé et entièrement automatisé, impliquant plusieurs étapes et ne perturbant pas le service des systèmes en production. Les contrôles d’intégrité servent à surveiller l’état de l’application. Si ces vérifications échouent lors d’une mise à jour d’AEM as a Cloud Service, la publication ne se poursuit pas et Adobe enquête sur les raisons pour lesquelles la mise à jour a provoqué ce comportement inattendu.

Lorsque vous déployez une nouvelle version de code personnalisé sur votre environnement, les [tests fonctionnels de produit et personnalisés](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) jouent un rôle essentiel. Ils garantissent que les systèmes de production restent stables et fonctionnels même après l’application d’une modification. Ces tests sont également appliqués dans le processus de mise à jour de la version d’AEM.

Si la mise à jour de l’environnement de production échoue, Cloud Manager restaurera automatiquement l’environnement d’évaluation. Cette opération s’effectue automatiquement afin de s’assurer qu’une fois la mise à jour terminée, les environnements d’évaluation et de production utilisent la même version d’AEM.
De même, si la mise à jour automatisée d’un environnement de développement échoue, les environnements d’évaluation et de production ne sont pas mis à jour.

>[!NOTE]
>
>Si du code personnalisé a été envoyé à l’évaluation et non à la production, la prochaine mise à jour d’AEM supprime ces modifications afin de refléter la balise Git de la dernière version de production réussie du client. Par conséquent, le code personnalisé qui n’était disponible que lors de l’évaluation doit être déployé à nouveau.

## Bonnes pratiques {#best-practices}

* **Utilisation de l’environnement d’évaluation**
   * Utilisez un autre environnement (et non l’environnement d’évaluation) pour les longs cycles QA/UAT.
   * Une fois le test d’intégrité terminé sur l’environnement d’évaluation, passez à la vérification sur l’environnement de production.

* **Pipeline de production**
   * Mettre en pause avant le déploiement en production.
   * L’annulation du pipeline après un déploiement dans l’environnement intermédiaire indique que le code est « un jetable » et n’est pas un candidat valide pour la production. Voir [Configuration d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

* **Pipeline hors production**
   * Configurez un [pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).
   * Accélérez la vitesse/fréquence de diffusion pour les échecs de pipeline de production. Identifiez les problèmes dans les pipelines hors production en activant les tests fonctionnels du produit, les tests fonctionnels personnalisés et les tests de l’interface utilisateur personnalisés.

* **Copie de contenu**
   * Utilisez [Copie de contenu](/help/implementing/developing/tools/content-copy.md) pour déplacer des jeux de contenu similaires vers un environnement autre que la production.

* **Tests fonctionnels automatisés**
   * Incluez des tests automatisés dans votre pipeline afin de pouvoir tester des fonctionnalités critiques.
   * Les tests fonctionnels du client [Customer Functional Testing](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) et [Custom UI Testing](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) sont bloqués, s’ils échouent, la version d’AEM n’est pas déployée.

## Régression {#regression}

Si vous rencontrez un problème lié à la régression, envoyez un dossier d’assistance par le biais de l’Admin Console. Si le problème est un bloqueur et son impact sur la production, un point P1 doit être soulevé. Fournissez tous les détails requis pour reproduire le problème de régression.

## Magasin de nœuds composites {#composite-node-store}

En règle générale, les mises à jour n’entraînent aucune interruption, y compris pour l’instance de création qui est un cluster de nœuds. Les mises à jour en continu sont possibles en raison de [la fonctionnalité de magasin de nœuds composites dans Oak](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html).

Cette fonctionnalité permet à AEM de faire référence à plusieurs référentiels simultanément. Dans un [déploiement en continu](/help/implementing/deploying/overview.md#how-rolling-deployments-work), la nouvelle version d’AEM contient son propre `/libs` (référentiel non modifiable basé sur TarMK). Il est distinct de l’ancienne version d’AEM, bien que les deux fassent référence à un référentiel modifiable partagé et basé sur DocumentMK qui contient des zones comme `/content` , `/conf` , `/etc` et d’autres.

Comme les anciennes et les nouvelles versions ont leurs propres versions de `/libs`, elles peuvent toutes deux être actives pendant la mise à jour en continu. De plus, les deux peuvent prendre en charge le trafic jusqu’à ce que l’ancien soit complètement remplacé par le nouveau.

## Informations supplémentaires {#further-information}

Pour plus de détails sur les thèmes connexes :

* [Pipeline CI/CD Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)
* [Notification de l’interface utilisateur de Cloud Manager](/help/implementing/cloud-manager/notifications.md)
* [l’architecture d’Adobe Experience Manager as a Cloud Service](/help/overview/architecture.md)
