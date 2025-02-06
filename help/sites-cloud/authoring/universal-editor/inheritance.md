---
title: Héritage de contenu dans l’éditeur universel
description: Découvrez comment l’éditeur universel prend en charge l’héritage de contenu pour la gestion multisite et les lancements afin de prendre en charge la réutilisation et la localisation du contenu.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: 2a1b87c2-29b9-4689-9a15-e17942439160
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 4%

---

# Héritage de contenu dans l’éditeur universel {#inheritance}

Découvrez comment l’éditeur universel prend en charge l’héritage de contenu pour la gestion multisite et les lancements afin de prendre en charge la réutilisation et la localisation du contenu.

>[!NOTE]
>
>Cette fonction n’est disponible que pour le contenu stocké dans le référentiel AEM.

## Cas d’utilisation {#use-case}

Pour de nombreux utilisateurs d’AEM, la création d’une page n’est que le début. Pour dimensionner efficacement le contenu, les étapes suivantes sont généralement nécessaires après la création de la page :

1. **Traduisez la page** en utilisant des copies de langue et des workflows de traduction.
1. **Localisez la page** à l’aide de la gestion multisite pour déployer la page traduite sur différents marchés.
1. **Créez de nouvelles versions** en utilisant les lancements pour préparer les itérations futures de la page et en mettant ces modifications en ligne.

Ces étapes peuvent accélérer la vitesse du contenu et assurer la cohérence du contenu. L’éditeur universel prend en charge l’héritage de contenu, qui est le mécanisme sur lequel reposent les copies de langue, la gestion multisite et les lancements.

## Héritage {#what-is-inheritance}

L’héritage est le mécanisme par lequel le contenu peut être lié, de sorte que la modification de l’un modifie automatiquement l’autre.

MSM et les lancements sont des outils puissants qui vous permettent de réutiliser votre contenu à l’aide de l’héritage. Les pages peuvent être copiées à partir d’une source centrale (le plan directeur) pour permettre aux auteurs d’apporter des modifications spécifiques au contexte de ces copies, tandis que le reste du contenu reste hérité du plan directeur. Cela s’avère extrêmement utile lors de la localisation de sites.

Pour modifier le contenu de certaines copies, les auteurs rompent l’héritage sur les composants concernés afin de s’assurer que leurs modifications locales ne sont pas remplacées lorsque les copies sont synchronisées à partir du plan directeur.

## Héritage de contenu et éditeur universel {#universal-editor}

Lorsqu’une page fait partie de MSM ou d’un lancement et que le contenu est modifié à l’aide de l’éditeur universel, l’éditeur désactive automatiquement l’héritage pour toutes les modifications apportées par les auteurs sur cette page, s’assurant que le contenu modifié est conservé lorsque les mises à jour sont synchronisées à partir du plan directeur.

L’auteur n’a pas besoin de cliquer sur un bouton ni de prendre d’autres mesures pour désactiver l’héritage avant d’apporter des modifications locales. Dès qu’une modification est apportée, l’héritage est implicitement annulé. Ce workflow est différent de l’[ Éditeur de page ](/help/sites-cloud/authoring/page-editor/edit-content.md#inherited-components).

L’éditeur universel n’affecte pas le mécanisme sous-jacent de l’héritage. Pour plus d’informations sur le fonctionnement de l’héritage, consultez la documentation suivante.

* [Gestion multisite (MSM)](/help/sites-cloud/administering/msm/overview.md)
* [Lancements](/help/sites-cloud/authoring/launches/overview.md)

## Limites {#limitations}

* Les auteurs ne peuvent pas rétablir l’héritage pour des composants uniques.
   * L’héritage ne peut être rétabli que pour la page entière via le .
      * [Console Vue d’ensemble de la Live Copy](/help/sites-cloud/administering/msm/live-copy-overview.md)
      * [Console de lancements](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)
      * à l’aide du bouton **Réinitialiser** sur l’onglet **Live Copy** de la fenêtre [Propriétés de la page](/help/sites-cloud/authoring/sites-console/page-properties.md).
* Les auteurs n’ont pas de retour visuel pour savoir quels composants ont leur héritage désactivé et lesquels l’ont toujours conservé.
* Ces fonctionnalités sont actuellement limitées aux composants dans les pages et ne s’appliquent pas encore aux [fragments de contenu](/help/sites-cloud/administering/content-fragments/overview.md), bien qu’ils disposent également de fonctionnalités MSM et Launch.
