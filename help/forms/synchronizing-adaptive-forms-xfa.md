---
title: Comment synchroniser le Forms adaptatif avec les modèles de formulaire XFA ?
description: Synchronisation des formulaires adaptatifs avec des fichiers XFA/XDP.
uuid: 92818132-1ae0-4576-84f2-ece485a34457
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: dac4539b-804d-4420-9170-68000ebb2638
docset: aem65
source-git-commit: 7a65aa82792500616f971df52b8ddb6d893ab89d
workflow-type: tm+mt
source-wordcount: '1146'
ht-degree: 93%

---


# Synchronisation de formulaires adaptatifs avec des modèles de formulaire XFA{#synchronizing-adaptive-forms-with-xfa-form-templates}

## Présentation {#introduction}

Vous pouvez créer un formulaire adaptatif basé sur un modèle de formulaire XFA (fichier `*.XDP`). Cette réutilisation vous permet de conserver vos investissements dans les formulaires XFA existants. Pour plus d’informations sur l’utilisation d’un modèle de formulaire XFA pour créer un formulaire adaptatif, voir [Création d’un formulaire adaptatif basé sur un modèle](creating-adaptive-form.md).

Vous pouvez réutiliser des champs du fichier XDP dans votre formulaire adaptatif. Ces champs sont appelés champs liés. Les propriétés des champs liés (tels que les scripts, les libellés et le format d’affichage) sont copiées à partir du fichier XDP. Vous pouvez également choisir de remplacer la valeur de certaines de ces propriétés.

[!DNL AEM Forms] permet de conserver les champs des formulaires adaptatifs synchronisés avec les modifications apportées ultérieurement aux champs correspondants du fichier XDP. Cet article explique comment activer cette synchronisation.

![Vous pouvez faire glisser des champs d’un formulaire XFA jusqu’à un formulaire adaptatif.](assets/drag-drop-xfa.gif.gif)

Dans l’environnement de création [!DNL AEM Forms], vous pouvez faire glisser des champs d’un formulaire XFA (à gauche) jusqu’à un formulaire adaptatif (à droite).

## Conditions préalables {#prerequisites}

Pour utiliser les informations fournies dans cet article, il est recommandé de disposer de connaissances dans les domaines suivants :

* [Création d’un formulaire adaptatif](creating-adaptive-form.md)

* XFA (XML Forms Architecture)

Pour utiliser les ressources fournies pour l’exemple de cet article, téléchargez l’exemple de package, comme expliqué dans la section suivante, voir [Exemple de package](synchronizing-adaptive-forms-xfa.md#p-sample-package-p).

## Exemple de package {#sample-package}

Cet article utilise un exemple pour montrer comment synchroniser le formulaire adaptatif avec un modèle de formulaire XFA mis à jour. Les ressources utilisées dans l’exemple sont disponibles dans un package qui peut être téléchargé à partir de la section [Téléchargements](synchronizing-adaptive-forms-xfa.md#p-downloads-p) de cet article.

Une fois le package chargé, vous pouvez afficher ces ressources dans l’interface utilisateur [!DNL AEM Forms].

Installez le package à l’aide du gestionnaire de packages : `https://<server>:<port>/crx/packmgr/index.jsp`

Le package contient les ressources suivantes :

1. `sample-form.xdp` : modèle de formulaire XFA utilisé comme exemple.

1. `sample-xfa-af` : formulaire adaptatif basé sur le fichier sample-form.xdp. Ce formulaire adaptatif ne contient toutefois aucun champ. Dans l’étape suivante, vous allez ajouter du contenu à ce formulaire adaptatif.

### Ajout de contenu au formulaire adaptatif {#add-content-to-adaptive-form-br}

1. Accédez à https://&lt;serveur>:&lt;port>/aem/forms.html. Entrez vos informations d’identification si nécessaire.
1. Ouvrez le fichier sample-af-xfa pour le modifier en mode création.
1. Dans l’explorateur de contenu de la barre latérale, sélectionnez l’onglet Objets de modèle de données. Faites glisser les champs NumericField1 et TextField1 sur le formulaire adaptatif.
1. Remplacez le titre de NumericField1 de **Numeric Field** par **AF Numeric Field.**

>[!NOTE]
>
>Dans les étapes précédentes, nous avons remplacé une propriété d’un champ du fichier XDP. Cette propriété ne sera donc pas synchronisée si la propriété correspondante du fichier XDP est modifiée ultérieurement.

## Détection des modifications dans le fichier XDP {#detecting-changes-in-xdp-file}

Dès qu’une modification est apportée à un fichier XDP ou un fragment, l’interface utilisateur [!DNL AEM Forms] marque tous les formulaires adaptatifs qui sont basés sur le fichier XDP ou le fragment.

Après la mise à jour d’un fichier XDP, vous devez le charger à nouveau dans l’interface utilisateur [!DNL AEM Forms] pour que les modifications soient marquées.

À titre d’exemple, vous allez mettre à jour le fichier `sample-form.xdp` en procédant comme suit :

1. Accédez à `https://<server>:<port>/projects.html.` Entrez vos informations d’identification si cela vous est demandé.
1. Cliquez sur l’onglet Formulaires à gauche.
1. Téléchargez le fichier `sample-form.xdp` sur votre ordinateur local. Le fichier XDP est téléchargé sous la forme d’un fichier `.zip`, qui peut être extrait à l’aide de n’importe quel utilitaire de décompression de fichiers.

1. Ouvrez le fichier `sample-form.xdp` et remplacez le titre du champ TextField1 de **Text Field** par **My Text Field**.

1. Chargez à nouveau le fichier `sample-form.xdp` dans l’interface utilisateur [!DNL AEM Forms].

Si un fichier XDP est mis à jour, vous voyez une icône dans l’éditeur, lorsque vous modifiez les formulaires adaptatifs basés sur celui-ci. Cette icône indique que les formulaires adaptatifs ne sont pas synchronisés avec le fichier XDP. Dans l’illustration suivante, examinez l’icône en regard de la barre latérale.

![Icône indiquant que le formulaire adaptatif n’est pas synchronisé avec le fichier XDP](assets/sync-af-xfa.png)

## Synchronisation des formulaires adaptatifs avec le fichier XDP le plus récent {#synchronizing-adaptive-forms-with-the-latest-xdp-file}

Lorsqu’un formulaire adaptatif qui n’est pas synchronisé avec le fichier XDP est ouvert en vue de sa création, le message suivant s’affiche :**Le schéma/le modèle de formulaire du formulaire adaptatif a été mis à jour. `Click Here` pour le baser sur la nouvelle version.**

Lorsque vous cliquez sur le message, les champs du formulaire adaptatif sont synchronisés avec les champs correspondants du fichier XDP.

Pour l’exemple utilisé dans cet article, ouvrez le fichier `sample-xfa-af` en mode création. Le message s’affiche dans la partie inférieure du formulaire adaptatif.

![Message vous invitant à synchroniser le formulaire adaptatif avec le fichier XDP](assets/sync-af-xfa-1.png)

### Mise à jour des propriétés {#updating-the-properties}

Toutes les propriétés qui ont été copiées du fichier XDP dans le formulaire adaptatif sont mises à jour, à l’exception des propriétés qui ont été explicitement remplacées dans le formulaire adaptatif (dans la boîte de dialogue Composant) par l’auteur. La liste des propriétés qui ont été mises à jour est disponible dans les journaux du serveur.

Pour mettre à jour les propriétés dans l’exemple de formulaire adaptatif, cliquez sur le lien (intitulé `"Click Here"`) du message. Le titre de TextField1 change de **Text Field** en **My Text Field**.

![update-property](assets/update-property.png)

>[!NOTE]
>
>Le libellé AF Numeric Field n’a pas été modifié, car vous avez remplacé cette propriété dans la boîte de dialogue des propriétés du composant, comme décrit dans la section [Ajout de contenu aux formulaires adaptatifs](synchronizing-adaptive-forms-xfa.md#p-add-content-to-adaptive-form-br-p).

### Ajout de nouveaux champs du fichier XDP au formulaire adaptatif {#adding-new-fields-from-xdp-file-to-adaptive-form-nbsp}

Les champs qui sont ultérieurement ajoutés au fichier XDP d’origine apparaissent dans l’onglet Hiérarchie du formulaire. Vous pouvez les faire glisser jusqu’au formulaire adaptatif.

Il n’est pas nécessaire de cliquer sur le lien du message d’erreur pour mettre à jour les champs dans l’onglet Hiérarchie du formulaire.

### Champs supprimés du fichier XDP {#deleted-fields-in-xdp-file}

Si un champ qui a été copié dans un formulaire adaptatif est supprimé d’un fichier XDP, un message d’erreur s’affiche en mode création indiquant que le champ n’existe pas dans le fichier XDP. Dans ce cas, supprimez manuellement le champ du formulaire adaptatif ou effacez la propriété `bindRef` dans la boîte de dialogue Composant.

Les étapes suivantes illustrent ce flux d’utilisation des ressources dans l’exemple utilisé dans cet article :

1. Mettez à jour le fichier `sample-form.xdp` et supprimez NumericField1.
1. Chargez le fichier `sample-form.xdp` dans l’interface utilisateur [!DNL AEM Forms].
1. Ouvrez le formulaire adaptatif `sample-xfa-af` en vue de sa création. Le message d’erreur suivant s’affiche : Le schéma/le modèle de formulaire du formulaire adaptatif a été mis à jour. `Click Here` pour le baser sur la nouvelle version.

1. Cliquez sur le lien (intitulé « `Click Here` ») du message. Un message d’erreur s’affiche indiquant que le champ n’existe plus dans le fichier XDP.

![Erreur apparaissant lorsque vous supprimez un élément dans le fichier XDP](assets/no-element-xdp.png)

Le champ qui a été supprimé est également signalé par une icône pour indiquer une erreur dans le champ.

![Icône d’erreur dans le champ](assets/error-field.png)

>[!NOTE]
>
>Les champs du formulaire adaptatif ayant une liaison incorrecte (une valeur `bindRef` non valide dans la boîte de dialogue Modifier) sont également considérés comme des champs supprimés. Si l’auteur ne corrige pas ces erreurs et publie le formulaire adaptatif, le champ est traité comme un champ de formulaire adaptatif non lié normal et est inclus dans la section non lié du fichier XML de sortie.

## Téléchargements {#downloads}

Package de contenu pour l’exemple dans cet article

[Obtenir le fichier](assets/sample-xfa-af-sync-1.0.zip)
