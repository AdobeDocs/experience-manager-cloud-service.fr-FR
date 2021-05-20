---
title: Conflits de déploiement
description: Découvrez comment gérer et résoudre les conflits de déploiement de Multi Site Manager.
feature: Multi Site Manager
role: Administrator
exl-id: 733e9411-50a7-42a5-a5a8-4629f6153f10
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 27%

---

# Conflits de déploiement {#msm-rollout-conflicts}

Des conflits peuvent se produire si de nouvelles pages portant le même nom de page sont créées à la fois dans la branche de plan directeur et dans une branche Live Copy dépendante. Ces conflits doivent être gérés et résolus lors du déploiement.

## Gestion des conflits {#conflict-handling}

Lorsqu’il existe des pages en conflit (dans les branches Plan directeur et Live Copy), MSM vous permet de définir comment (ou même si) elles doivent être gérées.

Pour vous assurer que le déploiement n’est pas bloqué, les définitions possibles peuvent inclure :

* Quelle page (plan directeur ou Live Copy) aura la priorité lors du déploiement
* Quelles pages seront renommées (et comment) ?
* Comment cela affecte le contenu publié

Le comportement par défaut d’AEM prêt à l’emploi est que le contenu publié ne sera pas affecté. Ainsi, si une page qui a été créée manuellement dans la branche Live Copy a été publiée, ce contenu sera toujours publié après la gestion et le déploiement des conflits.

Outre les fonctionnalités standard, des gestionnaires de conflit personnalisés peuvent être ajoutés pour mettre en œuvre différentes règles. Elles peuvent également permettre des actions de publication sous forme de processus individuel.

### Exemple de scénario {#example-scenario}

Dans les sections suivantes, nous utilisons l’exemple d’une nouvelle page `b`, créée à la fois dans le plan directeur et la branche Live Copy (créée manuellement), pour illustrer les différentes méthodes de résolution de conflit :

* plan directeur : `/b`

   Un gabarit avec une page enfant, `bp-level-1`

* Live Copy: `/b`

   Page créée manuellement dans la branche Live Copy avec une page enfant, `lc-level-1`

   * Activé lors de la publication sous la forme `/b`, avec la page enfant

#### Avant le déploiement {#before-rollout}

|  | Plan directeur avant le déploiement | Live Copy avant le déploiement | Publication avant déploiement |
|---|---|---|---|
| Valeur | `b` | `b` | `b` |
| Commentaire | Créé dans la branche de plan directeur, prêt pour le déploiement | Création manuelle dans la branche Live Copy | Contient le contenu de la page `b` qui a été créée manuellement dans la branche Live Copy |
| Valeur | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Commentaire |  | Création manuelle dans la branche Live Copy | contient le contenu de la page `child-level-1` qui a été créée manuellement dans la branche Live Copy |

## Gestionnaire de déploiement et gestion des conflits {#rollout-manager-and-conflict-handling}

Le gestionnaire de déploiement permet d’activer ou de désactiver la gestion des conflits.

Pour ce faire, utilisez la [configuration OSGi](/help/implementing/deploying/configuring-osgi.md) de **Day CQ WCM Rollout Manager**. Définissez la valeur **Gérer le conflit avec les pages créées manuellement** ( `rolloutmgr.conflicthandling.enabled`) sur true si le gestionnaire de déploiement doit gérer les conflits d’une page créée dans la Live Copy avec un nom qui existe dans le plan directeur.

AEM possède un [comportement prédéfini lorsque la gestion des conflits a été désactivée.](#behavior-when-conflict-handling-deactivated)

## Gestionnaires de conflit {#conflict-handlers}

AEM utilise des gestionnaires de conflit pour résoudre les conflits de page qui existent lors du déploiement de contenu d’un plan directeur vers une Live Copy. Le changement de nom des pages est la méthode habituelle (pas seulement) pour résoudre de tels conflits. Plusieurs gestionnaires de conflit peuvent être opérationnels pour permettre de sélectionner différents comportements.

AEM comporte les éléments suivants :

* [Gestionnaire de conflits par défaut](#default-conflict-handler) :
   * `ResourceNameRolloutConflictHandler`
* Possibilité de mettre en œuvre un [gestionnaire personnalisé](#customized-handlers)
* Le mécanisme de classement des services qui vous permet de définir la priorité de chaque gestionnaire individuel
   * Le service qui possède la valeur la plus élevée est utilisé.

### Gestionnaire de conflits par défaut {#default-conflict-handler}

Le gestionnaire de conflit par défaut est `ResourceNameRolloutConflictHandler`

* Avec ce gestionnaire, la page du plan directeur prévaut.
* Le classement des services pour ce gestionnaire est défini bas, c’est-à-dire sous la valeur par défaut de la propriété `service.ranking`, car il est supposé que les gestionnaires personnalisés auront besoin d’un classement supérieur. Cependant, le classement n’est pas le minimum absolu pour s’assurer de la flexibilité lorsque cela est nécessaire.

Ce gestionnaire de conflits donne la priorité au plan directeur. Par exemple, la page Live Copy `/b` est déplacée dans la branche Live Copy vers `/b_msm_moved`.

* Live Copy: `/b`

   Est déplacé dans la Live Copy vers `/b_msm_moved`. Cela fait office de sauvegarde et permet de s’assurer qu’aucun contenu n’est perdu.

   * `lc-level-1` n’est pas déplacé.

* Plan directeur : `/b`

   est déployé sur la page Live Copy `/b`.

   * `bp-level-1` est déployé sur la Live Copy.

#### Après le déploiement {#after-rollout}

|  | Plan directeur après le déploiement | Live Copy après le déploiement | Live Copy après le déploiement | Publier après le déploiement |
|---|---|---|---|---|
| Valeur | `b` | `b` | `b_msm_moved` | `b` |
| Commentaire |  | Comporte le contenu de la page de plan directeur `b` qui a été déployée | Contient le contenu de la page `b` qui a été créée manuellement dans la branche Live Copy | Aucune modification, contient le contenu de la page d’origine `b` qui a été créée manuellement dans la branche Live Copy et est désormais appelée `b_msm_moved` |
| Valeur | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Commentaire |  |  | Aucune modification | Aucune modification |

### Gestionnaires personnalisés {#customized-handlers}

Les gestionnaires de conflit personnalisés permettent de mettre en œuvre vos propres règles. À l’aide du mécanisme de classement des services, vous pouvez également définir leur mode d’interaction avec les autres gestionnaires.

Les gestionnaires de conflit personnalisés peuvent être :

* nommés selon vos besoins ;
* Soyez développé/configuré en fonction de vos besoins.
   * Par exemple, vous pouvez développer un gestionnaire de sorte que la page Live Copy ait la priorité.
* Peut être conçu pour être configuré à l’aide de la [configuration OSGi](/help/implementing/deploying/configuring-osgi.md). En particulier :
   * **Service** Rankingdéfinit l’ordre associé à d’autres gestionnaires de conflit (  `service.ranking`).
      * La valeur par défaut est `0`.

### Comportement lorsque la gestion des conflits est désactivée {#behavior-when-conflict-handling-deactivated}

Si vous désactivez manuellement [la gestion des conflits, ](#rollout-manager-and-conflict-handling) AEM n’effectue aucune action sur les pages en conflit. Les pages non conflictuelles sont déployées comme prévu.

>[!CAUTION]
>
>Lorsque la gestion des conflits est désactivée, AEM ne donne aucune indication que les conflits sont ignorés. Dans la mesure où, dans ce cas, ce comportement doit être explicitement configuré, il est supposé s’agir du comportement souhaité.

Dans ce cas, la Live Copy a la priorité. La page de plan directeur `/b` n’est pas copiée et la page Live Copy `/b` n’est pas touchée.

* Plan directeur : `/b`

   N’est pas copié du tout, mais est ignoré.

* Live Copy: `/b`

   Reste le même.

#### Après le déploiement {#after-rollout-no-conflict}

|  | Plan directeur après le déploiement | Live Copy après le déploiement | Publier après le déploiement |
|---|---|---|---|
| Valeur | `b` | `b` | `b` |
| Commentaire |  | Aucune modification, contient le contenu de la page `b` qui a été créée manuellement dans la branche Live Copy | Aucune modification, contient le contenu de la page `b` qui a été créée manuellement dans la branche Live Copy |
| Valeur | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Commentaire |  | Aucune modification | Aucune modification |

### Classements des services {#service-rankings}

Le classement des services [OSGi](https://www.osgi.org/) peut être utilisé pour définir la priorité des différents gestionnaires de conflit.
