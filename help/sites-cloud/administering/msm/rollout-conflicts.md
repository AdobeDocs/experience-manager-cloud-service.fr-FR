---
title: Conflits de déploiement
description: Découvrez comment gérer et résoudre les conflits de déploiement multisite Manager.
translation-type: tm+mt
source-git-commit: 4fc4dbe2386d571fa39fd6d10e432bb2fc060da1
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 26%

---


# Conflits de déploiement {#msm-rollout-conflicts}

Des conflits peuvent survenir si de nouvelles pages portant le même nom de page sont créées à la fois dans la branche du plan directeur et dans une branche Live Copy dépendante. Ces conflits doivent être gérés et résolus lors du déploiement.

## Gestion des conflits {#conflict-handling}

Lorsqu&#39;il existe des pages conflictuelles (dans le plan directeur et les branches Live Copy), MSM vous permet de définir comment (ou même si) elles doivent être gérées.

Pour vous assurer que le déploiement n’est pas bloqué, les définitions possibles peuvent inclure :

* Quelle page (plan ou Live Copy) aura la priorité lors du déploiement
* Quelles pages seront renommées (et comment) ?
* En quoi cela aura une incidence sur le contenu publié

Le comportement par défaut des AEM prêts à l’emploi est que le contenu publié ne sera pas affecté. Ainsi, si une page créée manuellement dans la branche Live Copy a été publiée, ce contenu sera toujours publié après la gestion et le déploiement des conflits.

Outre les fonctionnalités standard, des gestionnaires de conflit personnalisés peuvent être ajoutés pour mettre en œuvre différentes règles. Elles peuvent également permettre des actions de publication sous forme de processus individuel.

### Exemple de scénario {#example-scenario}

Dans les sections suivantes, nous utilisons l&#39;exemple d&#39;une nouvelle page `b`, créée à la fois dans le plan directeur et la branche Live Copy (créée manuellement), pour illustrer les différentes méthodes de résolution des conflits :

* plan directeur : `/b`

   Un gabarit avec 1 page enfant, `bp-level-1`

* Live Copy: `/b`

   Page créée manuellement dans la branche Live Copy avec une page enfant, `lc-level-1`

   * Activé lors de la publication en tant que `/b`, avec la page enfant

#### Avant le déploiement {#before-rollout}

|  | Plan avant le déploiement | Copie en direct avant le déploiement | Publier avant le déploiement |
|---|---|---|---|
| Valeur | `b` | `b` | `b` |
| Commentaire | Créé dans la branche du plan directeur, prêt pour le déploiement | Création manuelle dans la branche Live Copy | Contient le contenu de la page `b` créée manuellement dans la branche LiveCopy |
| Valeur | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Commentaire |  | Création manuelle dans la branche Live Copy | contient le contenu de la page `child-level-1` créée manuellement dans la branche LiveCopy |

## Gestionnaire de déploiement et gestion des conflits {#rollout-manager-and-conflict-handling}

Le gestionnaire de déploiement permet d’activer ou de désactiver la gestion des conflits.

Pour ce faire, [OSGi configuration](/help/implementing/deploying/configuring-osgi.md) de **Day CQ WCM Rollout Manager**. Définissez la valeur **Gérer le conflit avec les pages créées manuellement** ( `rolloutmgr.conflicthandling.enabled`) sur true si le gestionnaire de déploiement doit gérer les conflits d&#39;une page créée dans Live Copy avec un nom qui existe dans le plan.

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

Le gestionnaire de conflits par défaut est `ResourceNameRolloutConflictHandler`

* Avec ce gestionnaire, la page du plan directeur prévaut.
* Le classement des services pour ce gestionnaire est défini bas, c&#39;est-à-dire en dessous de la valeur par défaut de la propriété `service.ranking`, dans la mesure où l&#39;hypothèse est que les gestionnaires personnalisés auront besoin d&#39;un classement plus élevé. Cependant, le classement n’est pas le minimum absolu pour s’assurer de la flexibilité lorsque cela est nécessaire.

Ce gestionnaire de conflits donne la priorité au plan directeur. Par exemple, la page Live Copy `/b` est déplacée dans la branche Live Copy vers `/b_msm_moved`.

* Live Copy: `/b`

   Est déplacé dans la Live Copy vers `/b_msm_moved`. Cela fait office de sauvegarde et permet de s’assurer qu’aucun contenu n’est perdu.

   * `lc-level-1` n’est pas déplacé.

* Plan directeur : `/b`

   Est déployé sur la page Live Copy `/b`.

   * `bp-level-1` est déployé dans Live Copy.

#### Après le déploiement {#after-rollout}

|  | Plan directeur après le déploiement | Copie en direct après le déploiement | Copie en direct après le déploiement | Publier après le déploiement |
|---|---|---|---|---|
| Valeur | `b` | `b` | `b_msm_moved` | `b` |
| Commentaire |  | Contient le contenu de la page du plan directeur `b` qui a été déployée | Contient le contenu de la page `b` créée manuellement dans la branche Live Copy | Aucune modification, contient le contenu de la page d’origine `b` qui a été créée manuellement dans la branche Live Copy et est maintenant appelée `b_msm_moved` |
| Valeur | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Commentaire |  |  | Aucune modification | Aucune modification |

### Gestionnaires personnalisés {#customized-handlers}

Les gestionnaires de conflit personnalisés permettent de mettre en œuvre vos propres règles. À l’aide du mécanisme de classement des services, vous pouvez également définir leur mode d’interaction avec les autres gestionnaires.

Les gestionnaires de conflit personnalisés peuvent être :

* nommés selon vos besoins ;
* Soyez développé/configuré en fonction de vos besoins.
   * Par exemple, vous pouvez développer un gestionnaire de sorte que la page Live Copy soit prioritaire.
* Peut être conçu pour être configuré à l&#39;aide de la configuration [OSGi](/help/implementing/deploying/configuring-osgi.md). En particulier :
   * **Service** Rankingdéfinit l&#39;ordre associé à d&#39;autres gestionnaires de conflit (  `service.ranking`).
      * La valeur par défaut est `0`.

### Comportement lorsque la gestion des conflits est désactivée {#behavior-when-conflict-handling-deactivated}

Si vous désactivez manuellement [la gestion des conflits,](#rollout-manager-and-conflict-handling) AEM ne prend aucune action sur les pages conflictuelles. Les pages non conflictuelles sont déployées comme prévu.

>[!CAUTION]
>
>Lorsque la gestion des conflits est désactivée, AEM ne donne aucune indication que les conflits sont ignorés. Dans de tels cas, ce comportement doit être explicitement configuré, il est supposé correspondre au comportement souhaité.

Dans ce cas, Live Copy a la priorité. La page de plan directeur `/b` n&#39;est pas copiée et la page de Live Copy `/b` reste intacte.

* Plan directeur : `/b`

   N’est pas copié du tout, mais est ignoré.

* Live Copy: `/b`

   Reste le même.

#### Après le déploiement {#after-rollout-no-conflict}

|  | Plan directeur après le déploiement | Copie en direct après le déploiement | Publier après le déploiement |
|---|---|---|---|
| Valeur | `b` | `b` | `b` |
| Commentaire |  | Aucune modification, a le contenu de la page `b` qui a été créée manuellement dans la branche Live Copy | Aucune modification, contient le contenu de la page `b` créée manuellement dans la branche Live Copy |
| Valeur | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Commentaire |  | Aucune modification | Aucune modification |

### Classements des services {#service-rankings}

Le classement des services [OSGi](https://www.osgi.org/) peut être utilisé pour définir la priorité des différents gestionnaires de conflit.
