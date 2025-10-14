---
title: Héritage de contenu dans l’éditeur universel
description: Découvrez comment l’éditeur universel prend en charge l’héritage de contenu pour la gestion multisite et les lancements afin de prendre en charge la réutilisation et la localisation du contenu.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: 2a1b87c2-29b9-4689-9a15-e17942439160
source-git-commit: 2099a1aecd30eaa2ca3ca33a13729817a30b6c3f
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 4%

---

# Héritage de contenu dans l’éditeur universel {#inheritance}

Découvrez comment l’éditeur universel prend en charge l’héritage de contenu pour la gestion multisite et les lancements afin de prendre en charge la réutilisation et la localisation du contenu.

>[!NOTE]
>
>Cette fonctionnalité n’est disponible que pour le contenu stocké dans le référentiel AEM.

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

L’auteur n’a pas besoin de cliquer sur un bouton ni de prendre d’autres mesures pour désactiver l’héritage avant d’apporter des modifications locales. Dès qu’une modification est apportée, l’héritage est implicitement annulé. Ce workflow est différent de l’[&#x200B; Éditeur de page &#x200B;](/help/sites-cloud/authoring/page-editor/edit-content.md#inherited-components).

L’héritage peut être rétabli pour la page entière via :

* [Console Vue d’ensemble de la Live Copy](/help/sites-cloud/administering/msm/live-copy-overview.md)
* [Console de lancements](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)
* à l’aide du bouton **Réinitialiser** sur l’onglet **Live Copy** de la fenêtre [Propriétés de la page](/help/sites-cloud/authoring/sites-console/page-properties.md).

L’éditeur universel n’affecte pas le mécanisme sous-jacent de l’héritage. Pour plus d’informations sur le fonctionnement de l’héritage, consultez la documentation suivante.

* [Gestion multisite (MSM)](/help/sites-cloud/administering/msm/overview.md)
* [Lancements](/help/sites-cloud/authoring/launches/overview.md)

### Extension AEM Multi-Site-Management (MSM) {#msm-extension}

S’il est installé, l’extension **AEM Multi-Site-Management (MSM)** affiche le statut d’héritage actuel du composant sélectionné et vous permet de rompre ou de rétablir l’héritage au niveau du composant.

Pour plus d’informations sur l’utilisation de cette extension, consultez la documentation de création [&#128279;](/help/sites-cloud/authoring/universal-editor/authoring.md#inheritance).

Pour plus d’informations sur la manière d’activer cette extension, [consultez la documentation d’Extension Manager.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

## Limites {#limitations}

* Pour rétablir l’héritage pour des composants uniques, l’extension **AEM Multi-Site-Management (MSM)** doit être activée.
* Pour que les commentaires visuels indiquent quels composants ont leur héritage désactivé et lesquels l’ont toujours conservé, l’extension **AEM Multi-Site-Management (MSM)** doit être activée.
