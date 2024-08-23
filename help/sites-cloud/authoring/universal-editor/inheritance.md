---
title: Héritage de contenu dans l’éditeur universel
description: Découvrez comment l’éditeur universel prend en charge l’héritage de contenu pour la gestion multisite et les lancements pour prendre en charge la réutilisation et la localisation du contenu.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 773ce75975f4dcc2c5310422bcc377b487ebec25
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 4%

---


# Héritage de contenu dans l’éditeur universel {#inheritance}

Découvrez comment l’éditeur universel prend en charge l’héritage de contenu pour la gestion multisite et les lancements pour prendre en charge la réutilisation et la localisation du contenu.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour le contenu stocké dans le référentiel AEM.

## Cas d’utilisation {#use-case}

Pour de nombreux utilisateurs d’AEM, la création d’une page n’est que le début. Pour dimensionner efficacement le contenu, les étapes suivantes sont généralement impliquées après la création de la page :

1. **Traduisez la page** à l’aide de copies de langue et de workflows de traduction.
1. **Localisez la page** à l’aide de la gestion multisite pour déployer la page traduite sur différents marchés.
1. **Créez de nouvelles versions** à l’aide de lancements pour préparer les itérations futures de la page et mettre en ligne ces modifications.

Ces étapes peuvent accélérer la vitesse du contenu et assurer la cohérence du contenu. L’éditeur universel prend en charge l’héritage du contenu, qui est le mécanisme sur lequel reposent les copies de langue, la gestion multisite et les lancements.

## Héritage {#what-is-inheritance}

L’héritage est le mécanisme par lequel le contenu peut être lié, de sorte que la modification de l’un modifie automatiquement l’autre.

MSM et les lancements sont des outils puissants pour vous aider à réutiliser votre contenu à l’aide de l’héritage. Les pages peuvent être copiées à partir d’une source centrale (le plan directeur) pour permettre aux auteurs d’apporter des modifications spécifiques au contexte de ces copies, tandis que le reste du contenu reste hérité du plan directeur. Cela s’avère extrêmement utile lors de la localisation de sites.

Pour modifier un certain contenu des copies, les auteurs rompent l’héritage sur les composants affectés afin de s’assurer que leurs modifications locales ne sont pas écrasées lorsque les copies sont synchronisées à partir du plan directeur.

## Héritage de contenu et éditeur universel {#universal-editor}

Lorsqu’une page fait partie de MSM ou d’un lancement et que du contenu est modifié avec l’éditeur universel, l’éditeur désactive automatiquement l’héritage pour toutes les modifications apportées par les auteurs sur cette page, en s’assurant que le contenu modifié est conservé lorsque les mises à jour sont synchronisées à partir du plan directeur.

L’auteur n’a pas besoin de cliquer sur un bouton ou de prendre toute autre mesure pour désactiver l’héritage avant d’effectuer des modifications locales. Dès qu’une modification est apportée, l’héritage est implicitement annulé. Ceci contraste avec l’[ éditeur de page.](/help/sites-cloud/authoring/page-editor/edit-content.md#inherited-components)

L’éditeur universel n’affecte pas le mécanisme sous-jacent de l’héritage. Pour plus d’informations sur le fonctionnement de l’héritage, consultez la documentation suivante.

* [Gestion multisite (MSM)](/help/sites-cloud/administering/msm/overview.md)
* [Lancements](/help/sites-cloud/authoring/launches/overview.md)

## Limites {#limitations}

* Les auteurs ne peuvent pas rétablir l’héritage pour les composants uniques.
   * L’héritage ne peut être rétabli que pour la page entière via l’événement
      * [Console Vue d’ensemble de la Live Copy](/help/sites-cloud/administering/msm/live-copy-overview.md)
      * [Console de lancements](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)
      * Utilisation du bouton **Réinitialiser** sur l’onglet **Live Copy** de la fenêtre [ des propriétés de page.](/help/sites-cloud/authoring/sites-console/page-properties.md)
* Les auteurs n’ont pas de commentaires visuels pour voir quels composants ont leur héritage désactivé et lesquels sont toujours conservés.
* Actuellement, ces fonctionnalités sont limitées aux composants des pages et ne s’appliquent pas encore aux [fragments de contenu,](/help/sites-cloud/administering/content-fragments/overview.md) même si ceux-ci disposent également des fonctionnalités MSM et Launch.
