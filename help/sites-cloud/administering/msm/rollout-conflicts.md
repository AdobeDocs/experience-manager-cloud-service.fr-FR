---
title: Conflits de déploiement
description: Découvrez comment gérer et résoudre les conflits de déploiement en cas de gestion de plusieurs sites.
feature: Multi Site Manager
role: Admin
exl-id: 733e9411-50a7-42a5-a5a8-4629f6153f10
source-git-commit: 78ead5f15c2613d9c3bed3025b43423a66805c59
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 56%

---

# Conflits de déploiement {#msm-rollout-conflicts}

Des conflits peuvent apparaître si de nouvelles pages portant le même nom de page sont créées dans la branche de plan directeur et dans une branche de Live Copy dépendante. Ces conflits doivent être gérés et résolus lors du déploiement.

## Gestion des conflits {#conflict-handling}

Lorsqu’il existe des pages en conflit (dans les branches Plan directeur et Live Copy), MSM vous permet de définir comment (ou même si) elles doivent être gérées.

Pour vous assurer que le déploiement n’est pas bloqué, les définitions possibles peuvent inclure :

* Quelle page (plan directeur ou Live Copy) a la priorité lors du déploiement
* Quelles pages sont renommées et comment
* Comment cela affecte-t-il le contenu publié ?

Le comportement par défaut de Adobe Experience Manager (AEM) est que le contenu publié n’est pas affecté. Ainsi, si une page qui a été créée manuellement dans la branche Live Copy a été publiée, ce contenu est toujours publié après la gestion et le déploiement des conflits.

Outre les fonctionnalités standard, des gestionnaires de conflit personnalisés peuvent être ajoutés pour mettre en œuvre différentes règles. Ils peuvent également permettre des actions de publication sous la forme d’un processus individuel.

### Exemple de scénario {#example-scenario}

Dans les sections suivantes, un exemple de nouvelle page `b` est utilisé, créé à la fois dans le plan directeur et dans la branche Live Copy (créée manuellement), pour illustrer les différentes méthodes de résolution des conflits :

* Plan directeur : `/b`

  un gabarit avec une page enfant, `bp-level-1`

* Live Copy: `/b`

  Une page créée manuellement dans la branche Live Copy avec une page enfant, `lc-level-1`

   * Activé lors de la publication sous la forme `/b`, avec la page enfant

#### Avant le déploiement {#before-rollout}

|  | Plan directeur avant le déploiement | Live Copy avant le déploiement | Publication avant le déploiement |
|---|---|---|---|
| Valeur | `b` | `b` | `b` |
| Commentaire | Création dans la branche du plan directeur, prêt pour le déploiement | Créé manuellement dans la branche Live Copy | Contient le contenu de la page `b` créée manuellement dans la branche Live Copy |
| Valeur | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Commentaire |  | Créé manuellement dans la branche Live Copy | Contient le contenu de la page `child-level-1` créée manuellement dans la branche Live Copy |

## Gestionnaire de déploiement et gestion des conflits {#rollout-manager-and-conflict-handling}

Le gestionnaire de déploiement vous permet d’activer ou de désactiver la gestion des conflits.

Ceci est effectué à l’aide de la [configuration OSGi](/help/implementing/deploying/configuring-osgi.md) du **gestionnaire de déploiement WCM Day CQ**. Définissez la valeur **Gérer un conflit avec des pages créées manuellement** (`rolloutmgr.conflicthandling.enabled` ) sur true si le gestionnaire de déploiement doit gérer les conflits d’une page créée dans la Live Copy qui porte un nom déjà présent dans le plan directeur.

AEM possède un [comportement prédéfini lorsque la gestion des conflits a été désactivée.](#behavior-when-conflict-handling-deactivated)

## Gestionnaires de conflit {#conflict-handlers}

AEM utilise des gestionnaires de conflit pour résoudre des conflits de page qui émergent lors du déploiement du contenu du plan directeur vers la Live Copy. Le changement de nom des pages est la méthode habituelle (et pas seulement) pour résoudre de tels conflits. Plusieurs gestionnaires de conflit peuvent être opérationnels pour permettre une sélection de comportements différents.

AEM fournit :

* La variable [gestionnaire de conflit par défaut](#default-conflict-handler):
   * `ResourceNameRolloutConflictHandler`
* Possibilité de mettre en œuvre un [gestionnaire personnalisé](#customized-handlers)
* Le mécanisme de classement des services qui permet de définir la priorité de chaque gestionnaire individuel
   * Le service qui possède la valeur la plus élevée est utilisé.

### Gestionnaire de conflits par défaut {#default-conflict-handler}

Le gestionnaire de conflits par défaut est `ResourceNameRolloutConflictHandler`

* Avec ce gestionnaire, la page de plan directeur a la priorité.
* Le classement des services pour ce gestionnaire est défini sur le bas. En d’autres termes, sous la valeur par défaut de la variable `service.ranking` , car il est supposé que les gestionnaires personnalisés ont besoin d’un classement supérieur. Cependant, le classement n’est pas le minimum absolu pour garantir de la flexibilité lorsque cela est nécessaire.

Ce gestionnaire de conflits donne la priorité au plan directeur. Par exemple, la page Live Copy `/b` est déplacé dans la branche Live Copy vers `/b_msm_moved`.

* Live Copy: `/b`

  Est déplacé dans la Live Copy vers `/b_msm_moved`. Cela fait office de sauvegarde et permet de s’assurer qu’aucun contenu n’est perdu.

   * `lc-level-1` n’est pas déplacé.

* Blueprint: `/b`

  Est déployé dans la page Live Copy `/b`.

   * `bp-level-1` est déployé dans Live Copy.

#### Après le déploiement {#after-rollout}

|  | Plan directeur après le déploiement | Live Copy après le déploiement | Live Copy après le déploiement | Publication après le déploiement |
|---|---|---|---|---|
| Valeur | `b` | `b` | `b_msm_moved` | `b` |
| Commentaire |  | Contient le contenu de la page du plan directeur `b` qui a été déployée | Contient le contenu de la page `b` créée manuellement dans la branche Live Copy | Aucune modification ; contient le contenu de la page d’origine. `b` qui a été créé manuellement dans la branche Live Copy et est désormais appelée `b_msm_moved` |
| Valeur | `/bp-level-1` | `/bp-level-1` | `/lc-level-1` | `/lc-level-1` |
| Commentaire |  |  | Aucune modification | Aucune modification |

### Gestionnaires personnalisés {#customized-handlers}

Les gestionnaires de conflit personnalisés permettent de mettre en œuvre vos propres règles. Grâce au mécanisme de classement des services, vous pouvez également définir la manière dont ils interagissent avec d’autres gestionnaires.

Les gestionnaires de conflit personnalisés peuvent :

* nommés selon vos besoins ;
* développés/configurés selon vos besoins.
   * Par exemple, vous pouvez développer un gestionnaire de sorte que la page Live Copy soit prioritaire.
* Il peut être configuré à l’aide de la fonction [Configuration OSGi](/help/implementing/deploying/configuring-osgi.md). En particulier :
   * **Classement des services** définit l’ordre associé aux autres gestionnaires de conflit (`service.ranking`).
      * La valeur par défaut est `0`.

### Comportement lorsque la gestion des conflits est désactivée {#behavior-when-conflict-handling-deactivated}

Si vous [désactivez manuellement la gestion des conflits,](#rollout-manager-and-conflict-handling) AEM n’engage aucune action concernant les pages en conflit. Les pages ne provoquant pas de conflits sont déployées comme prévu.

>[!CAUTION]
>
>Lorsque la gestion des conflits est désactivée, AEM n’indique pas que les conflits sont ignorés. Dans de tels cas, ce comportement doit être explicitement configuré, il est supposé correspondre au comportement souhaité.

Dans ce cas, la Live Copy a la priorité. La page du plan directeur `/b` n’est pas copiée, et la page de la Live Copy `/b` reste intacte.

* Blueprint: `/b`

  Il n’est pas copié du tout, mais il est ignoré.

* Live Copy: `/b`

  Ça reste le même.

#### Après le déploiement {#after-rollout-no-conflict}

|  | Plan directeur après le déploiement | Live Copy après le déploiement | Publication après le déploiement |
|---|---|---|---|
| Valeur | `b` | `b` | `b` |
| Commentaire |  | Aucune modification ; contient le contenu de la page. `b` qui a été créé manuellement dans la branche Live Copy | Aucune modification ; contient le contenu de la page. `b` qui a été créé manuellement dans la branche Live Copy |
| Valeur | `/bp-level-1,` | `/lc-level-1` | `/lc-level-1` |
| Commentaire |  | Aucune modification | Aucune modification |

### Classements des services {#service-rankings}

Le classement des services [OSGi](https://www.osgi.org/) peut être utilisé pour définir la priorité des différents gestionnaires de conflit.
