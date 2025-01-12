---
title: Mises à jour de la version d’AEM
description: Découvrez comment Adobe Experience Manager (AEM) as a Cloud Service l’intégration et la diffusion continues (CI/CD) pour conserver vos projets sur la dernière version.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
role: Admin
source-git-commit: 73fac04561f43a4053e1694da9e096a2ecbc1484
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 11%

---


# Mises à jour de la version d’AEM {#aem-version-updates}

Découvrez comment Adobe Experience Manager (AEM) as a Cloud Service l’intégration et la diffusion continues (CI/CD) pour conserver vos projets sur la dernière version.

## CI/CD {#ci-cd}

AEM as a Cloud Service utilise l’intégration continue et la diffusion continue (CI/CD) pour garantir que vos projets utilisent la version d’AEM la plus récente. Ce processus met à jour en toute transparence vos instances de production, d’évaluation et de développement sans pour autant perturber vos utilisateurs.

>[!NOTE]
> Comme les instances de développement sont déjà automatiquement mises à jour, les mises à jour manuelles des instances de développement peuvent ne pas être disponibles pour _certaines_ de vos programmes. Cette fonctionnalité est en cours de transition vers des mises à jour automatiques.

Avant que vos instances ne soient automatiquement mises à jour, une nouvelle version de maintenance d’AEM est publiée 3 à 5 jours à l’avance. Pendant cette période, votre instance de développement peut être mise à jour automatiquement ou, si elle est disponible, vous pouvez éventuellement [ déclencher la mise à jour de vos instances de développement](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment). Les mises à jour de version sont automatiquement appliquées en premier à vos environnements de développement. Si la mise à jour est réussie, le processus de mise à jour se poursuit vers vos instances d’évaluation et de production. Les instances de développement et d’évaluation agissent comme un point de contrôle de qualité automatisé, où vos tests écrits personnalisés sont exécutés avant l’application de la mise à jour à votre environnement de production.

### NIMU (Mises à jour de maintenance non intrusives) {#nimu}

Les mises à jour de maintenance non intrusives sont des mises à jour automatiques qui sont appliquées sans impliquer les pipelines du client.
Grâce à NIMU, le client peut utiliser le pipeline à tout moment, même si une mise à jour de version d’AEM est planifiée ou en cours et que les mises à jour de maintenance n’apparaîtront plus dans l’historique d’exécution du pipeline client, ce qui facilite le suivi de l’historique des déploiements de code.

#### Mise à jour des activités

La version d’AEM actuelle peut toujours être vérifiée pour chaque environnement, comme auparavant, à l’aide du panneau Environnements de l’interface utilisateur de Cloud Manager . Les mêmes points de contrôle de qualité utilisés dans le pipeline sont utilisés par les mises à jour de maintenance non intrusives, y compris les tests écrits par le client.
Une [notification de l’interface utilisateur de Cloud Manager](/help/implementing/cloud-manager/notifications.md) sera envoyée chaque fois qu’une mise à jour de maintenance non intrusive est appliquée aux environnements de votre programme. Vous pouvez le configurer pour qu’il soit également envoyé à votre email.

>[!NOTE]
>
> Remarque : les mises à jour de maintenance non intrusives seront progressivement activées pour tous les clients en 2024.


## Type de mises à jour {#update-types}

Il existe deux types de mises à jour de la version d’AEM :

* [**Mises à jour de la maintenance**](/help/release-notes/maintenance/latest.md)

   * Ils sont principalement destinés à des fins de maintenance, notamment les derniers correctifs de bogues et les mises à jour de sécurité.
   * Son impact est minimal, car les changements sont appliqués régulièrement.

* [**Activation des fonctionnalités**](/help/release-notes/release-notes-cloud/release-notes-current.md)

   * Ils sont publiés selon un calendrier mensuel prévisible.

>[!NOTE]
>
> Vérifiez les dates clés des versions mensuelles sur la [feuille de route des versions Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr#aem-as-cloud-service) et marquez vos calendriers pour vous préparer aux activités clés afin de vous préparer à la version.

## Échec de la mise à jour {#update-failure}

Les mises à jour d’AEM passent par un pipeline de validation de produit avancé et entièrement automatisé, impliquant plusieurs étapes et ne perturbant pas le service des systèmes en production. Les contrôles d’intégrité servent à surveiller l’état de l’application. Si ces vérifications échouent lors d’une mise à jour d’AEM as a Cloud Service, la version ne se poursuit pas et Adobe recherche les raisons pour lesquelles la mise à jour a provoqué ce comportement inattendu.

Lorsque vous déployez une nouvelle version de code personnalisé dans votre environnement, les [tests fonctionnels de produit et personnalisés](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) jouent un rôle crucial. Elles garantissent que les systèmes de production restent stables et fonctionnels même après l’application d’un changement. Ces tests sont également appliqués dans le processus de mise à jour AEM version.

Si la mise à jour de l’environnement de production échoue, Cloud Manager restaure automatiquement l’environnement d’évaluation. Cela permet de s’assurer automatiquement qu’une fois la mise à jour terminée, les environnements d’évaluation et de production se trouvent tous deux sur la même version AEM.
De même, si une mise à jour automatisée d’un environnement de développement échoue, les environnements d’évaluation et de production ne sont pas mis à jour.

>[!NOTE]
>
>Si le code personnalisé a été envoyé vers l’évaluation et non vers la production, la mise à jour AEM suivante supprime ces modifications pour refléter la balise git de la dernière version de production réussie du client. Par conséquent, le code personnalisé qui n’était disponible que lors de l’évaluation doit être déployé à nouveau.

## Bonnes pratiques {#best-practices}

* **Utilisation de l’environnement d’évaluation**
   * Utilisez un environnement différent (pas l’environnement intermédiaire) pour de longs cycles AQ/UAT.
   * Une fois le test d’intégrité terminé sur l’évaluation, déplacez-le pour le vérifier sur l’environnement de production.

* **Pipeline de production**
   * Mettre en pause avant de procéder au déploiement vers Production.
   * L’annulation du pipeline après un déploiement dans l’environnement intermédiaire indique que le code est &quot;un jeton&quot; et qu’il ne s’agit pas d’un candidat valide pour la production, voir [Configuration d’un pipeline de production](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

* **Pipeline hors production**
   * Configurez un [pipeline hors production](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).
   * Accélérer la vitesse/fréquence de diffusion pour les échecs de pipeline de production. Identifiez les problèmes dans les pipelines non prod en activant les tests fonctionnels du produit, les tests fonctionnels personnalisés et les tests d’interface utilisateur personnalisés.

* **Copie de contenu**
   * Utilisez [Copie de contenu](/help/implementing/developing/tools/content-copy.md) pour déplacer des jeux de contenu similaires vers un environnement autre que prod.

* **Tests fonctionnels automatisés**
   * Incluez des tests automatisés dans votre pipeline afin de pouvoir tester les fonctionnalités critiques.
   * Les [tests fonctionnels du client](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) et les [tests d’interface utilisateur personnalisés](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) bloquent, s’ils échouent, la version d’AEM n’est pas déployée.

## Régression {#regression}

Si vous rencontrez un problème lié à la régression, soumettez un cas d’assistance par le biais de l’Admin Console. Si le problème est un bloqueur et son impact sur la production, un P1 doit être soulevé. Indiquez tous les détails nécessaires pour reproduire le problème de régression.

## Magasin de nœuds composites {#composite-node-store}

En règle générale, les mises à jour n’entraînent aucune interruption, y compris pour l’instance de création, qui est un cluster de noeuds. Les mises à jour en continu sont possibles en raison de [la fonctionnalité de magasin de nœuds composites dans Oak.](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html)

Cette fonctionnalité permet à AEM de faire référence à plusieurs référentiels simultanément. Dans un [déploiement en continu](/help/implementing/deploying/overview.md#how-rolling-deployments-work), la nouvelle version d’AEM contient son propre `/libs` (référentiel non modifiable basé sur TarMK). Il est différent de l’ancienne version d’AEM, bien que les deux fassent référence à un référentiel modifiable partagé basé sur DocumentMK qui contient des zones comme `/content` , `/conf` , `/etc` et d’autres.

Comme les anciennes et les nouvelles versions possèdent leurs propres versions de `/libs`, elles peuvent toutes deux être actives pendant la mise à jour en continu. Et les deux peuvent reprendre la circulation jusqu&#39;à ce que l&#39;ancien soit complètement remplacé par le nouveau.

## Informations supplémentaires {#further-information}

Pour plus de détails sur les thèmes connexes :

* [Pipeline CI/CD Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)
* [Notification de l’interface utilisateur de Cloud Manager](/help/implementing/cloud-manager/notifications.md)
* [Architecture d’Adobe Experience Manager as a Cloud Service](/help/overview/architecture.md)
