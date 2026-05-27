---
title: Fragments de contenu visuels
description: Découvrez comment visualiser et publier des fragments de contenu visuel à l’aide de modèles HTML.
feature: Content Fragments
role: User, Developer
source-git-commit: 9ad53c41534c552f485a2d57d3c81c270180dfaf
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---

# Fragments de contenu visuels {#visual-content-fragments}

Les fragments de contenu contiennent du contenu structuré destiné à la sortie JSON, sans conception ni disposition. L’ajout de modèles HTML vous permet de créer des expériences visuelles entièrement décorées avec du contenu structuré au format HTML :

* La visualisation d’un fragment de contenu contribue à l’assurance qualité du contenu, en permettant aux parties prenantes de réviser le contenu avant son utilisation, sans avoir à ouvrir l’éditeur de fragment de contenu

* La diffusion d’un fragment visuel facilite la diffusion omnicanale, pour la réutilisation d’expériences modulaires sur plusieurs canaux tels que le web, les e-mails ou les applications mobiles.

La sortie rendue d’un fragment de contenu AEM qui utilise la disposition et la conception d’un modèle HTML joint est appelée *fragment de contenu visuel*.

<!-- CQDOC-23232 - remove when GA -->

>[!NOTE]
>
>Les fragments de contenu visuel sont actuellement en disponibilité limitée.
>
>Si vous souhaitez participer, veuillez envoyer une demande à partir de votre adresse e-mail officielle à [&#128279;](mailto:experience-production-agent@adobe.com).

Les modèles HTML contiennent des informations de mise en page et de conception, ce qui permet de visualiser les fragments de contenu. La connexion entre un modèle et un fragment de contenu est établie à l’aide de la syntaxe Handlebars pour mapper les balises HTML aux types de données (champs) définis dans le modèle de fragment de contenu. Cette définition permet à du contenu créé dans les champs respectifs de l’éditeur de fragment de contenu d’être affiché aux emplacements appropriés dans le modèle.

Vous ou votre équipe de développement pouvez [créer et personnaliser vos propres modèles HTML](/help/implementing/developing/extending/content-fragments-visualization-templates.md), puis [charger et joindre un ou plusieurs modèles aux modèles de fragment de contenu](#upload-and-assign-your-template) afin que les fragments correspondants puissent être rendus en expériences, [prévisualisés](#preview-your-fragment-with-a-template) et [diffusés selon les besoins](#deliver-your-visual-content-fragment).

>[!NOTE]
>
>Un **modèle générique** est toujours disponible par défaut dans AEM et associé à chaque modèle. Ce modèle permet d’afficher les paires clé/valeur dans du contenu structuré dans un format propre de style tableau afin de prendre en charge les cas d’utilisation d’Assurance de qualité du contenu (AQ).

## Création d’un modèle {#create-a-template}

Les modèles HTML développés à l’aide de Handlebars vous permettent de prévisualiser et de diffuser des fragments de contenu visuel au format HTML. La syntaxe Handlebars.js définit des espaces réservés pour le contenu créé dans les champs de fragment de contenu.

Pour plus d’informations sur le développement de vos propres modèles, voir [Fragments de contenu visuels - Modèles](/help/implementing/developing/extending/content-fragments-visualization-templates.md).

## Chargement et affectation de votre modèle {#upload-and-assign-your-template}

Un modèle est associé à un modèle de fragment de contenu afin de pouvoir être utilisé avec n’importe quel fragment de contenu créé à partir de ce modèle.

Pour charger votre nouveau modèle HTML :

1. Dans la console Fragments de contenu, ouvrez l’onglet **Modèles de fragment de contenu**.
1. Accédez à l’emplacement de votre modèle de fragment.
1. Sélectionnez l’icône d’information (i) pour le modèle requis :

   ![Console Fragments de contenu - Icône Informations](/help/sites-cloud/administering/content-fragments/assets/cfc-information-icon.png)

   Le panneau de droite s’affiche.
1. Faites défiler la page vers le bas pour afficher **Modèles**, le **Modèle générique** est déjà répertorié car il s’agit du modèle par défaut :

   ![Aperçu du fragment avec le modèle HTML générique](/help/sites-cloud/administering/content-fragments/assets/cf-visual-html-template-configure-default.png)

1. Sélectionnez **+** pour charger le modèle à partir d’un fichier HTML (`.html`). Une boîte de dialogue vous permet de **Parcourir** votre système de fichiers local et de sélectionner votre fichier modèle.
1. Une fois le modèle chargé, deux vues du modèle s’affichent pour que vous puissiez les consulter :

   * gauche : rendu du modèle sans contenu
   * droite : code HTML, qui peut également être modifié ici avant l’importation dans AEM

   ![Vérifier le modèle HTML au chargement](/help/sites-cloud/administering/content-fragments/assets/cf-visual-html-template-upload-review.png)

1. Sélectionnez **Suivant** pour continuer.
1. Saisissez un **Nom du modèle** à utiliser dans AEM.
1. Confirmez avec **Créer un modèle**.
1. Le modèle sera créé dans AEM et répertorié sous **Modèles HTML**, dans les propriétés des modèles de fragment de contenu.
Une fois chargé, il peut être utilisé pour [prévisualiser des fragments](#preview-your-fragment-with-a-template). Vous pouvez également **[Télécharger](#download-your-template)** ou **[Supprimer](#download-your-template)** le modèle.

## Prévisualiser votre fragment avec un modèle {#preview-your-fragment-with-a-template}

Pour prévisualiser votre fragment de contenu à l’aide d’un modèle :

>[!NOTE]
>
>Comme le **Modèle générique** est toujours disponible, vous pouvez prévisualiser votre fragment sans charger de modèles personnalisés.

1. Dans la console Fragment de contenu , naviguez jusqu’à l’emplacement de votre fragment.

1. Vous pouvez effectuer les actions suivantes :
   * sélectionnez votre fragment dans la console
   * ouvrez votre fragment dans l’éditeur

1. Sélectionnez **Aperçu** dans la barre d’outils supérieure de :

   * la console Fragments de contenu ;
   * l’éditeur, dans lequel vous pouvez ensuite sélectionner **Modèle**

Dans les deux cas, une nouvelle fenêtre modale s’ouvre.

1. Si aucun modèle personnalisé n’est disponible, AEM utilise le **Modèle générique** pour afficher votre fragment. Le **Modèle générique** :

   * affiche les champs de votre fragment sous forme de tableau (nom et contenu)
   * affiche le contenu entièrement hydraté des fragments référencés dans la même vue

1. Si des modèles personnalisés sont disponibles, vous pouvez sélectionner le modèle que vous souhaitez utiliser (y compris le **Modèle générique**).

1. Si le fragment de contenu est publié, vous pouvez également afficher et copier son **URL d’aperçu** et son **URL de publication**.

Par exemple, prévisualisez avec le **Modèle générique** :

![Aperçu du fragment avec le modèle HTML générique](/help/sites-cloud/administering/content-fragments/assets/cf-visual-html-template-referenced-fragment.png)

## Diffuser votre fragment de contenu visuel {#deliver-your-visual-content-fragment}

Le fragment de contenu visuel peut être diffusé à un éventail de cibles au format HTML.

### Diffuser dans le navigateur {#deliver-to-the-browser}

Copiez l’**URL de prévisualisation** ou l’**URL de publication**. Accédez-y directement à partir de votre navigateur pour afficher votre fragment de contenu visuel.

### Diffuser sur Edge Delivery Services {#deliver-to-edge-delivery-services}

Vous pouvez diffuser votre fragment visuel dans une page Edge Delivery Service (EDS).

1. Accédez à votre projet EDS.
1. Ajoutez ou accédez à un **[Bloc](https://www.aem.live/developer/block-collection)** de type **[incorporer](https://sidekick-library--aem-block-collection--adobe.aem.page/tools/sidekick/library.html?plugin=blocks&path=/block-collection/embed&index=0)**.
1. Collez l’**URL de publication** dans le bloc.
1. Publiez votre page EDS. La représentation HTML de votre fragment s’affiche.

>[!NOTE]
>
>Pour plus d’informations, consultez [Intégration à Edge Delivery Services (bloc intégré)](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#integration-with-edge-services-embed-block)

### Diffuser sur une page AEM {#deliver-to-an-AEM-page}

Vous pouvez diffuser votre fragment de contenu visuel dans une page AEM à l’aide du composant principal : fragment de contenu.

Lors de la configuration d’un composant **Fragment de contenu** [&#x200B; sur votre page](/help/sites-cloud/authoring/fragments/content-fragments.md#adding-a-content-fragment-to-your-page) :

1. Spécifiez le **fragment de contenu** requis.
1. Sélectionnez **Visualisation de fragment de contenu**.
1. Sélectionnez le **Modèle de visualisation** requis dans la liste déroulante.

   ![Configurer le composant Fragment de contenu pour un fragment visuel](/help/sites-cloud/administering/content-fragments/assets/cf-visual-template-aem-page.png)

1. Le fragment visuel s’affiche sur la page.

>[!NOTE]
>
>Pour plus d’informations, consultez [Intégration - AEM Sites avec les composants principaux](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#integration-aem-sites-with-core-components)

## Téléchargez votre modèle {#download-your-template}

Pour télécharger votre modèle HTML à partir d’AEM :

1. Dans la console Fragments de contenu, ouvrez l’onglet **Modèles de fragment de contenu**.
1. Accédez à l’emplacement de votre modèle de fragment.
1. Sélectionnez l’icône d’information (i) pour le modèle requis :

   ![Console Fragments de contenu - Icône Informations](/help/sites-cloud/administering/content-fragments/assets/cfc-information-icon.png)

   Le panneau de droite s’affiche.

1. Faites défiler vers le bas pour afficher **Modèles**.
1. Sélectionnez les points de suspension en fonction du modèle à télécharger.
1. Sélectionnez **Télécharger**.
1. Indiquez le nom et l’emplacement du fichier.
1. Confirmez avec **Enregistrer**.

## Supprimer le modèle {#delete-your-template}

Pour supprimer votre nouveau modèle HTML (à partir d’AEM) :

1. Dans la console Fragments de contenu, ouvrez l’onglet **Modèles de fragment de contenu**.
1. Accédez à l’emplacement de votre modèle de fragment.
1. Sélectionnez l’icône d’information (i) pour le modèle requis :

   ![Console Fragments de contenu - Icône Informations](/help/sites-cloud/administering/content-fragments/assets/cfc-information-icon.png)

   Le panneau de droite s’affiche.
1. Faites défiler vers le bas pour afficher **Modèles**.
1. Sélectionnez les points de suspension en fonction du modèle à télécharger.
1. Sélectionnez **Supprimer**.
1. Dans la boîte de dialogue suivante, confirmez l’action avec **Supprimer**.
