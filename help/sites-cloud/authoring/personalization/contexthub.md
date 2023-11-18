---
title: Aperçu des pages à l’aide des données ContextHub
description: La barre d’outils ContextHub affiche les données ContextHub, vous permet de modifier les données de la boutique, et se révèle utile pour prévisualiser le contenu.
exl-id: 9c0536c5-900e-4814-9e31-f9fee5adc17c
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 84%

---

# Aperçu des pages à l’aide des données ContextHub  {#previewing-pages-using-contexthub-data}

La barre d’outils ContextHub affiche les données ContextHub et vous permet de modifier les données de la boutique. La barre d’outils ContextHub est utile pour prévisualiser le contenu déterminé par les données d’un magasin ContextHub.

La barre d’outils se compose d’une série de modes d’UI qui contiennent un ou plusieurs modules d’UI.

* Les modes d’UI sont des icônes qui s’affichent sur le côté gauche de la barre d’outils. Lorsque vous sélectionnez une icône, la barre d’outils affiche les modules d’IU qu’elle contient.
* Les modules d’UI affichent les données d’un ou de plusieurs magasins ContextHub. Certains modules d’UI permettent également de manipuler les données du magasin.

ContextHub installe plusieurs modes d’IU et modules d’IU. Votre administrateur ou administratrice a peut-être [configuré ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md) pour en afficher d’autres.

## Affichage de la barre d’outils ContextHub {#revealing-the-contexthub-toolbar}

La barre d’outils ContextHub est disponible en mode Aperçu. La barre d’outils est disponible uniquement sur les instances d’auteur et uniquement si l’administrateur l’a activée.

![Barre d’outils ContextHub](/help/sites-cloud/authoring/assets/contexthub-toolbar.png)

1. Lorsque la page est ouverte pour modification, sélectionnez Aperçu dans la barre d’outils.

   ![Bouton Prévisualiser](/help/sites-cloud/authoring/assets/contexthub-preview-button.png)

1. Pour afficher la barre d’outils, sélectionnez l’icône ContextHub .

   ![Bouton ContextHub](/help/sites-cloud/authoring/assets/contexthub-button.png)

## Fonctionnalités du module d’IU {#ui-module-features}

Chaque module d’UI fournit un ensemble de fonctionnalités différent, mais les types de fonctionnalités suivants sont communs. Comme les modules d’UI peuvent être étendus, votre développeur ou développeuse peut mettre en œuvre d’autres fonctionnalités selon les besoins.

### Contenu de la barre d’outils {#toolbar-content}

Les modules d’IU peuvent afficher des données d’une ou de plusieurs boutiques ContextHub sur la barre d’outils. Les modules d’IU utilisent une icône et un titre pour s’identifier.

![Icône personnages ContextHub](/help/sites-cloud/authoring/assets/contexthub-persona-button.png)

### Contenu de la fenêtre contextuelle {#popup-content}

Certains modules d’IU affichent une fenêtre contextuelle lorsque l’utilisateur clique ou appuie dessus. En règle générale, cette fenêtre contextuelle contient des informations supplémentaires complétant les informations affichées sur la barre d’outils.

![Informations sur le profil ContextHub](/help/sites-cloud/authoring/assets/contexthub-profile.png)

### Formulaires dans une fenêtre contextuelle {#popup-forms}

La fenêtre contextuelle d’un module peut inclure des éléments de formulaire qui vous permettent de modifier les données dans le magasin ContextHub. Si le contenu de la page est déterminé par les données du magasin, vous pouvez utiliser le formulaire et observer les modifications apportées au contenu de la page.

### Mode Plein écran {#fullscreen-mode}

Les fenêtres contextuelles peuvent inclure une icône que vous choisissez pour développer le contenu de la fenêtre contextuelle afin de couvrir l’intégralité de la fenêtre ou de l’écran du navigateur.

![Bouton Plein écran](/help/sites-cloud/authoring/assets/contexthub-fullscreen.png)
