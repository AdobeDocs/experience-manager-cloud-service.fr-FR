---
title: Autres régions de publication
description: Découvrez comment AEM as a Cloud Service prend en charge des régions de publication supplémentaires pour une disponibilité accrue et une latence réduite.
exl-id: b9ac3c6a-eb8b-461d-8f1d-a0356046a3f9
feature: Operations
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 71%

---


# Autres régions de publication {#additional-publish-regions}

D’autres régions de publication peuvent être sous licence et activées sur les programmes configurés avec AEM Sites. Lorsqu’il est configuré, le trafic sur les environnements d’évaluation et de production est acheminé vers plusieurs fermes de publication, ce qui présente les avantages suivants :

* Latence réduite : les requêtes qui vont du réseau CDN vers les instances de publication AEM sont dirigées vers la région de publication la plus proche, ce qui est avantageux pour les sites web et les applications visitées par les personnes utilisatrices de plusieurs zones géographiques.
* Disponibilité plus élevée : si aucune région n’est disponible, le réseau CDN dirige le trafic vers les autres régions disponibles.

Les organisations peuvent acquérir sous licence jusqu’à trois régions de publication supplémentaires.

>[!NOTE]
>
>* Cette fonctionnalité est disponible pour les solutions Sites et Forms.
>* Cette fonctionnalité ne peut pas être appliquée aux [programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).
>* Cette fonctionnalité nécessite que votre programme soit mis à jour vers la version AEM 12142 ou ultérieure.

## Cas d’utilisation {#use-cases}

Vous trouverez ci-dessous quelques cas d’utilisation dans lesquels les entreprises peuvent bénéficier de la licence de régions de publication supplémentaires.

1. Pour les organisations qui reçoivent un trafic important ou essentiel de la part de personnes utilisatrices situées loin de la région principale, des régions de publication supplémentaires peuvent réduire la latence expérimentée.
1. Pour les organisations susceptibles de subir des dommages monétaires ou de réputation importants lorsqu’un site n’est pas disponible, il est possible d’atténuer ces effets en utilisant des régions de publication supplémentaires pour rendre le niveau de publication d’AEM plus résistant à l’échec régional.
1. Pour les organisations dont les auteurs et autrices de contenu se trouvent dans un emplacement géographique éloigné de la majorité des visiteurs et visiteuses du niveau publication, la région principale peut être choisie près de l’emplacement des auteurs et autrices de contenu, tandis que d’autres régions de publication peuvent être configurées près du trafic côté publication, les deux audiences bénéficiant ainsi d’une expérience optimisée.

## Activation et configuration {#enabling-and-configuring}

Après l’attribution de licence à une région de publication supplémentaire, les régions sont configurées à l’aide de Cloud Manager. Voir la [documentation Cloud Manager](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) pour plus d’informations.

D’autres régions de publication sont appliquées aux environnements d’évaluation et de production, mais pas aux environnements de développement ou de RDE.

Dans le cas où une région devient indisponible, les clients n’ont pas besoin de gérer le routage du trafic vers les régions disponibles, car il est géré par le réseau CDN d’Adobe.

Comme décrit dans la section Considérations relatives à la mise en réseau avancée ci-dessous, il est recommandé aux clients qui utilisent la mise en réseau avancée de la configurer pour chaque région de publication supplémentaire afin que la disponibilité soit maintenue si une région devient indisponible.


## Points à prendre en compte concernant la mise en réseau avancée {#advanced-networking-considerations}

Lorsqu’une région de publication supplémentaire est activée sur un programme avec une mise en réseau avancée déjà configurée, le trafic dans la région de publication supplémentaire qui correspond aux règles de mise en réseau avancée traverse par défaut la région principale. Pour bénéficier d’une disponibilité accrue, il est recommandé de mettre en place une mise en réseau avancée sur les régions supplémentaires.

Pour plus d’informations, notamment sur l’ajout de configurations de mise en réseau à d’autres régions sans perte de connectivité, consultez la section [Configuration de la mise en réseau avancée pour d’autres régions de publication](/help/security/configuring-advanced-networking.md#advanced-networking-configuration-for-additional-publish-regions) dans la documentation sur la mise en réseau avancée.

## Journalisation {#logging}

Si d’autres régions de publication sont activées, des journaux distincts pour chaque région sont disponibles via Cloud Manager. Pour plus d’informations, consultez [Accès aux journaux et leur gestion](/help/implementing/cloud-manager/manage-logs.md) et [Journaux des régions Publish supplémentaires](/help/implementing/developing/introduction/logging.md#logs-for-additional-publish-regions).

## Limites {#limitations}

Gardez à l’esprit les limites suivantes lorsque vous envisagez d’utiliser des régions de publication supplémentaires.

* Des régions de publication supplémentaires peuvent uniquement être ajoutées à AEM Sites ou AEM Forms.
   * Les régions de publication supplémentaires ne s’étendent pas à d’autres solutions AEM ou fonctionnalités associées déployées dans le même programme (par exemple, AEM Assets ou Adobe Learning Manager).
   * Cependant, ces solutions peuvent être ajoutées à un programme tant qu’il dispose d’au moins une solution Sites ou Forms qui s’y applique.
* D’autres régions ne peuvent être ajoutées que si les droits associés sont disponibles et inutilisés dans le client.
* Vous pouvez ajouter au maximum trois régions de publication supplémentaires à n’importe quel environnement.
* D’autres régions sont disponibles uniquement pour les programmes de production. Cette fonctionnalité n’est pas disponible dans les programmes sandbox.
* D’autres régions de publication sont appliquées uniquement aux environnements d’évaluation et de production, et non aux environnements de développement ou RDE.
* D’autres régions de publication nécessitent que votre programme soit mis à jour vers AEM version 12142 ou ultérieure.
