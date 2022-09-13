---
title: Création et gestion des offres (console Offres)
description: Utilisez la console Offres pour créer des offres que vous pourrez utiliser dans le cadre d’expériences associées à des activités
exl-id: 81d2fda2-06a9-48f6-820a-dd9e11d94fcc
source-git-commit: 9274496200af93708d5fd95666f969afc71125a6
workflow-type: tm+mt
source-wordcount: '1306'
ht-degree: 67%

---

# Création et gestion d’offres (Console d’offres) {#creating-and-managing-offers}

Le **Offres** La console sera abandonnée à l’avenir. Donc, à partir de maintenant, c&#39;est :

* Uniquement disponibles pour les clients qui ont *hérité* offres déjà définies (c’est-à-dire préexistantes)
* Il est recommandé de convertir de telles offres héritées en offres de fragments d’expérience.
   * Dès que la dernière offre héritée est convertie/supprimée, la variable **Offres** ne sera plus disponible.

![Consoles de personnalisation](/help/sites-cloud/authoring/assets/offers-consoles.png)

>[!NOTE]
>
>Les clients qui disposent d’offres héritées préexistantes peuvent toujours utiliser la variable **Offres** console pour afficher les offres existantes et créer de nouvelles offres héritées.
>
>Les clients qui ne disposent pas d’offres héritées préexistantes ne verront pas la variable **Offres** console.
>
>Tous les clients peuvent utiliser **Offres de fragments d’expérience** pour créer et gérer des offres.

## Conversion d’une offre héritée en fragment d’expérience {#convert-legacy-offer-to-experience-fragment}

A **Convertir en variation de fragment d’expérience** a été implémentée pour vous aider à convertir votre offre héritée en fragment d’expérience :

>[!NOTE]
>
>Il s’agit du processus recommandé pour convertir des offres héritées en fragments d’expérience.

>[!NOTE]
>
>Vous pouvez également créer vous-même un fragment d’expérience, transférer manuellement le contenu de votre offre héritée vers le fragment, puis supprimer l’offre héritée.

>[!CAUTION]
>
>Le **Convertir en variation de fragment d’expérience** est disponible pour tous les composants principaux.
>
>Cette option ne sera pas prise en charge pour les composants personnalisés. Pour ces composants, vous devez convertir manuellement le contenu en fragment d’expérience.

>[!CAUTION]
>
>Dès que la dernière offre héritée est convertie/supprimée :
>
>* Le **Offres** ne sera plus disponible.
>* L’icône cible de la barre d’outils des autres composants concernés n’apparaîtra plus.


1. Ouvrez une page contenant l’offre à modifier.

1. Basculer vers **Ciblage** pour cette page.

1. Sélectionnez **Commencer le ciblage**.

1. Sélectionnez le composant (ciblé) approprié.

1. La barre d’outils du composant fournit une option pour **Convertir en variation de fragment d’expérience**:

   ![Conversion d’une offre héritée en fragment d’expérience](/help/sites-cloud/authoring/assets/offers-convert-legacy-icon.png)

1. Une boîte de dialogue s’affiche. Vous pouvez y sélectionner les **Action**:

   * Créer un fragment d’expérience
   * Ajouter du contenu à un fragment d’expérience existant

   Pour ce scénario, sélectionnez **Création d’un fragment d’expérience**.

   ![Boîte de dialogue Convertir en variation de fragment d’expérience](/help/sites-cloud/authoring/assets/offers-convert-dialog.png)

1. Renseignez les champs requis de la boîte de dialogue :

   * **Chemin d’accès parent**
Définition du chemin parent du nouveau fragment d’expérience
   * **Modèle**
Sélectionnez le modèle à utiliser pour créer le fragment d’expérience.
   * **Titre du fragment**
Indiquez le titre.
   * **Balises de fragment**
Ajoutez des balises, le cas échéant.

1. Confirmer avec **Terminé**.

   Si vous accédez maintenant à la **Offres de fragments d’expérience** , vous verrez votre nouveau fragment d’expérience, ainsi que ses variations associées.

## La console Offres {#offers-console}

>[!CAUTION]
>
>Cette console sera abandonnée à l’avenir, car elle offre un moyen hérité de personnaliser le contenu.
>
>Tu as du temps pour te préparer. Découvrez comment [convertir vos offres héritées existantes en offre de fragment d’expérience ;](#convert-legacy-offer-to-experience-fragment).

Utilisez la console Offres pour créer des offres que vous pourrez [utiliser dans le cadre d’expériences associées à des activités](/help/sites-cloud/authoring/personalization/targeted-content.md). La création d’offres dans la console Offres permet de gagner du temps lorsque plusieurs expériences nécessitent la même offre :

* Créez l’offre une fois dans la bibliothèque et utilisez-la pour plusieurs expériences associées aux activités de votre marque.
* Modifiez l’offre dans la bibliothèque. Les modifications se répercutent sur toutes les expériences qui l’utilisent.

La console Offres trie les offres par marque. Chaque marque contient une bibliothèque d’offres qui peuvent être utilisées dans les expériences d’une marque. Utilisez des dossiers pour organiser hiérarchiquement les offres dans chaque bibliothèque. Une structure de dossiers logique permet aux auteurs de retrouver facilement des offres en les parcourant. Les outils de balisage et de recherche permettent également aux auteurs de retrouver des offres pertinentes.

### Ajout d’une marque dans la console Offres {#add-a-brand-using-the-offers-console}

Créez une marque à laquelle vos offres sont associées. Ouvrez une marque dans la console Offres pour accéder à la bibliothèque d’offres dans laquelle vous pouvez créer des dossiers et des offres.

Lorsque vous créez une marque à l’aide de la console Offres, elle s’affiche également dans la console [Activités](/help/sites-cloud/authoring/personalization/activities.md) où vous pouvez ajouter et gérer des activités relatives à la marque.

1. Dans la console de navigation, cliquez ou appuyez sur **Personnalisation** > **Offres**.

   ![Accès à la console Offres](/help/sites-cloud/authoring/assets/offers-navigation.png)

1. Cliquez ou appuyez sur **Créer**, puis sur **Créer** **une marque**.
1. Sélectionnez un modèle de marque et cliquez ou appuyez sur **Suivant**.
1. Saisissez un titre pour la marque tel qu’il doit apparaître dans les consoles Offres et Activités. Si vous le souhaitez, saisissez ou sélectionnez une ou plusieurs balises à associer à la marque.
1. Cliquez ou appuyez sur **Créer**.

### Ajout d’un fichier à une bibliothèque d’offres {#add-a-folder-to-an-offer-library}

Ajoutez un dossier à la bibliothèque d’offres d’une marque pour y organiser et y stocker les offres. Vous pouvez créer un dossier sous la marque ou sous d’autres dossiers.

1. Dans la console Offres, ouvrez l’emplacement où vous souhaitez créer le dossier. Par exemple, ouvrez la marque pour créer un dossier de niveau supérieur ou ouvrez un autre dossier de la bibliothèque.
1. Cliquez ou appuyez sur **Créer** > **Créer le dossier ou l’offre**.

   ![Création du dossier d’offres](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Sélectionnez **Dossier**, puis cliquez sur **Suivant**.
1. Entrez un titre pour le dossier tel qu’il doit apparaître dans la bibliothèque d’offres et saisissez ou sélectionnez des balises.

   ![Définition des propriétés du dossier](/help/sites-cloud/authoring/assets/offers-folder-properties.png)

1. Cliquez ou appuyez sur **Créer**.

### Ajout d’une offre à une bibliothèque d’offres {#add-an-offer-to-an-offer-library}

Ajoutez une offre à la bibliothèque d’offres d’une marque afin de pouvoir l’ajouter à des expériences liées à cette marque. Lorsque vous ajoutez une offre, il convient de saisir un titre. Vous pouvez également associer l’offre à une ou plusieurs balises pour optimiser la recherche.

Après avoir créé l’offre, vous pouvez l’ouvrir pour en modifier le contenu.

1. Dans la console Offres, ouvrez l’emplacement où vous souhaitez créer l’offre. Par exemple, ouvrez la marque pour créer une offre de niveau supérieur ou ouvrez un dossier de la bibliothèque.
1. Cliquez ou appuyez sur **Créer** > **Créer le dossier ou l’offre**.

   ![Création du dossier d’offres](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Sélectionnez le modèle **Page d’offre**, puis cliquez ou appuyez sur **Suivant**.
1. Saisissez le titre de l’offre et, le cas échéant, sélectionnez ou entrez une ou plusieurs balises à associer à l’offre, puis cliquez ou appuyez sur **Créer**.
1. Dans la boîte de dialogue de confirmation, pour ouvrir l’offre à modifier, cliquez ou appuyez sur **Ouvrir la page**.

### Modification d’une offre {#editing-an-offer}

Ouvrez une offre et modifiez le contenu tel qu’il doit apparaître dans les expériences qui l’utilisent. Lorsque vous modifiez une offre utilisée dans des expériences, les modifications se répercutent dans les expériences.

Vous pouvez ouvrir une offre à partir d’un dossier d’une bibliothèque d’offres ou à partir des résultats d’une recherche. Vous pouvez le faire à partir d’une expérience qui utilise l’offre en question.

1. Dans la console Offres, cliquez ou appuyez sur l’icône située en regard de l’offre, puis sur **Modifier**.
1. Ajoutez des composants à l’offre et publiez le contenu en suivant la procédure habituelle.

### Suppression d’une offre {#deleting-an-offer}

Supprimez une offre lorsqu’elle n’est plus nécessaire. Si vous essayez de supprimer une offre utilisée dans une expérience, vous êtes invité à confirmer la suppression. La confirmation supprime l’offre et la retire également des expériences.

Vous pouvez supprimer une offre tout en affichant le contenu des dossiers de la bibliothèque d’offres ou les résultats d’une recherche.

1. Dans la console Offres, cliquez ou appuyez sur l’icône située en regard de l’offre, puis sur **Supprimer**.

   Sélectionnez l’offre et cliquez ou appuyez sur **Supprimer**.

1. Dans la boîte de dialogue qui s’affiche, cliquez ou appuyez sur **Supprimer** pour confirmer la suppression.
1. Si l’offre est utilisée dans une ou plusieurs expériences, une boîte de dialogue s’ouvre pour indiquer que l’offre est référencée :

   * Pour supprimer l’offre et la retirer des expériences, cliquez ou appuyez sur **Forcer la suppression**.
   * Pour conserver l’offre, cliquez ou appuyez sur **Annuler**.

### Recherche d’offres {#searching-for-offers}

Recherchez les offres d’une marque quelconque à l’aide de mots-clés correspondant à leur titre.

![Recherche d’une offre](/help/sites-cloud/authoring/assets/offers-search.png)

Les critères de recherche actuels sont visibles en regard des résultats de la recherche. Vous pouvez également trier les résultats par colonne, dans l’ordre croissant ou décroissant. Vous pouvez effectuer une recherche à partir de n’importe quel dossier, dans n’importe quelle bibliothèque d’offres. Les résultats de la recherche restent les mêmes, quel que soit le dossier actif.

Pour rechercher des offres :

1. En haut de la console Offres, cliquez ou appuyez sur l’icône en forme de loupe. Par défaut, la recherche se limite aux offres.
1. Entrez un mot-clé pour rechercher des offres. Faites votre choix parmi les résultats.
