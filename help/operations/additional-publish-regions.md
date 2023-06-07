---
title: Autres régions de publication
description: Découvrez comment AEM as a Cloud Service prend en charge des régions de publication supplémentaires pour une disponibilité accrue et une latence réduite.
source-git-commit: 9fccc1672aad243b648115e657396be1ce4ed614
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 1%

---


# Autres régions de publication {#additional-publish-regions}

D’autres régions de publication peuvent être sous licence et activées sur les programmes configurés avec AEM Sites. Lorsqu’il est configuré, le trafic sur les environnements intermédiaire et de production est acheminé vers plusieurs fermes de serveurs de publication, ce qui présente les avantages suivants :

* Latence réduite : les requêtes qui vont du CDN vers les instances de publication AEM sont dirigées vers la région de publication la plus proche, ce qui est avantageux pour les sites web et les applications visitées par les utilisateurs dans plusieurs zones géographiques.
* Disponibilité plus élevée : si aucune région n’est disponible, le réseau de diffusion de contenu dirige le trafic vers les autres régions disponibles.

Les organisations peuvent acquérir sous licence jusqu’à trois régions de publication supplémentaires.

>[!NOTE]
>
>Cette fonctionnalité est actuellement disponible uniquement pour AEM Sites. Il ne peut pas non plus être appliqué aux programmes Sandbox. En outre, sachez que d’autres fonctionnalités de zones de publication nécessitent que votre programme soit mis à jour pour AEM version 12142 ou ultérieure.

## Cas d’utilisation {#use-cases}

Vous trouverez ci-dessous quelques cas d’utilisation dans lesquels les entreprises peuvent bénéficier de la licence de régions de publication supplémentaires.

1. Pour les organisations qui reçoivent un trafic important ou essentiel de la part d’utilisateurs situés loin de la région Principale, des régions de publication supplémentaires peuvent réduire la latence vécue par ces visiteurs.
1. Pour les organisations susceptibles de subir des dommages monétaires ou de réputation importants lorsqu’un site n’est pas disponible, cela peut être atténué en utilisant des régions de publication supplémentaires pour rendre le niveau de publication de l’AEM plus résistant à l’échec régional.
1. Pour les organisations dont les auteurs de contenu se trouvent dans un emplacement géographique éloigné de la majorité des visiteurs de niveau publication, la région Principale peut être choisie près de l’emplacement des auteurs de contenu, tandis que d’autres régions de publication peuvent être configurées près du trafic côté publication, avec les deux audiences qui bénéficient d’une expérience optimisée.

## Activation et configuration {#enabling-and-configuring}

Après la licence d’une région de publication supplémentaire, les régions sont configurées à l’aide de Cloud Manager. Voir [Documentation de Cloud Manager](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) pour obtenir des instructions détaillées.

D’autres régions de publication sont appliquées aux environnements intermédiaire et de production, mais pas aux environnements de développement ou de RDE.

## Points à prendre en compte concernant les réseaux avancés {#advanced-networking-considerations}

Lorsqu’une région de publication supplémentaire est activée sur un programme avec une mise en réseau avancée déjà configurée, le trafic dans la région de publication supplémentaire qui correspond aux règles de mise en réseau avancées traverse par défaut la région Principale. Afin de profiter d&#39;une disponibilité accrue, il est recommandé de mettre en place une mise en réseau avancée sur les régions supplémentaires.

Reportez-vous à la section [Configuration de réseau avancée pour d’autres régions de publication](/help/security/configuring-advanced-networking.md#advanced-networking-configuration-for-additional-publish-regions) pour plus d’informations, notamment sur l’ajout de configurations réseau avancées à d’autres régions sans perte de connectivité.

## Limites {#limitations}

Gardez ces limites à l’esprit lorsque vous envisagez d’utiliser d’autres régions de publication.

* D’autres régions de publication ne peuvent être ajoutées qu’à AEM Sites. Les régions de publication supplémentaires ne s’étendent pas à d’autres solutions AEM ou fonctionnalités connexes déployées dans le même programme (par exemple, AEM Forms ou Adobe Learning Manager).
* D’autres régions ne peuvent être ajoutées que si les droits associés sont disponibles et inutilisés dans le client.
* Vous pouvez ajouter au maximum trois zones de publication supplémentaires à n’importe quel environnement.
* D’autres régions sont disponibles uniquement pour les programmes de production. Cette fonctionnalité n’est pas disponible dans les programmes Sandbox.
* D’autres régions de publication sont appliquées uniquement aux environnements intermédiaire et de production, et non aux environnements de développement ou RDE.
* D’autres régions de publication nécessitent que votre programme soit mis à jour AEM version 12142 ou ultérieure.
