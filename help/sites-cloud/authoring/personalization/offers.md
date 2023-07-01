---
title: Créer et gérer des offres (console Offres)
description: Utiliser la console Offres pour créer des offres que vous pourrez utiliser dans le cadre d’expériences associées à des activités
exl-id: 81d2fda2-06a9-48f6-820a-dd9e11d94fcc
source-git-commit: a01583483fa89f89b60277c2ce4e1c440590e96c
workflow-type: tm+mt
source-wordcount: '1391'
ht-degree: 52%

---

# Créer et gérer des offres (console Offres) {#creating-and-managing-offers}

La console **Offres** sera abandonnée à l’avenir. Donc, à partir de maintenant :

* Elle n’est disponible que pour les client(e)s qui ont des offres *héritées* déjà définies (c’est-à-dire préexistantes).
* Il est recommandé de convertir de telles offres héritées en offres de fragments d’expérience.
   * Dès que la dernière offre héritée est convertie/supprimée, la console **Offres** n’est plus disponible.

![Consoles de personnalisation](/help/sites-cloud/authoring/assets/offers-consoles.png)

>[!NOTE]
>
>Les client(e)s qui disposent d’offres héritées préexistantes peuvent toujours utiliser la console **Offres** pour afficher les offres existantes et créer de nouvelles offres héritées.
>
>Les client(e)s qui ne disposent pas d’offres héritées préexistantes ne verront pas la console **Offres**.
>
>Tou(te)s les client(e)s peuvent utiliser les **Offres de fragments d’expérience** pour créer et gérer des offres.

## Convertir une offre héritée en fragment d’expérience {#convert-legacy-offer-to-experience-fragment}

Une option et un workflow **Convertir en variation de fragment d’expérience** ont été implémentés pour vous aider à convertir votre offre héritée en fragment d’expérience :

>[!NOTE]
>
>Il s’agit du processus recommandé pour convertir des offres héritées en fragments d’expérience.

>[!NOTE]
>
>Vous pouvez également créer vous-même un fragment d’expérience, transférer manuellement le contenu de votre offre héritée vers le fragment, puis supprimer l’offre héritée.

>[!CAUTION]
>
>L’option **Convertir en variation de fragment d’expérience** est disponible pour tous les composants principaux.
>
>Cette option ne sera pas prise en charge pour les composants personnalisés. Pour ces composants, vous devez convertir manuellement le contenu en fragment d’expérience.

>[!CAUTION]
>
>Dès que la dernière offre héritée est convertie/supprimée :
>
>* La console **Offres** n’est plus disponible.
>* L’icône cible de la barre d’outils des autres composants concernés n’apparaît plus.

1. Ouvrez une page contenant l’offre à modifier.

1. Passez en mode **Ciblage** dans cette page.

1. Sélectionnez **Commencer le ciblage**.

1. Sélectionnez le composant (ciblé) approprié.

1. La barre d’outils du composant fournit une option pour **Convertir en variation de fragment d’expérience** :

   ![Convertir une offre héritée en fragment d’expérience](/help/sites-cloud/authoring/assets/offers-convert-legacy-icon.png)

1. Une boîte de dialogue s’affiche. Vous pouvez y sélectionner l’**action** requise :

   * Créer un nouveau fragment d’expérience
   * Ajouter le contenu à un fragment d’expérience existant

   Pour ce scénario, sélectionnez **Créer un fragment d’expérience**.

   ![Boîte de dialogue Convertir en variation de fragment d’expérience](/help/sites-cloud/authoring/assets/offers-convert-dialog.png)

1. Renseignez les champs requis de la boîte de dialogue :

   * **Chemin d’accès parent**
Définissez le chemin d’accès parent du nouveau fragment d’expérience
   * **Modèle**
Sélectionnez le modèle à utiliser pour créer le fragment d’expérience.
   * **Titre du fragment**
Indiquez le titre.
   * **Balises du fragment**
Ajoutez des balises, le cas échéant.

1. Confirmez avec **Terminé**.

   Si vous accédez maintenant à la console **Offres de fragments d’expérience**, vous verrez votre nouveau fragment d’expérience, ainsi que ses variations associées.

### Ciblage à l’aide du modèle d’offre {#targeting-offers-template}

>[!CAUTION]
>
>Cette option est disponible uniquement pour les client(e)s qui disposent d’offres héritées préexistantes.
>
>Comme la console **Offres**, elle ne sera plus disponible non plus :
>
>* une fois la dernière offre héritée convertie en fragment d’expérience ;
>* lorsque les offres héritées seront obsolètes (à l’avenir).
>
>Par conséquent, il est recommandé d’utiliser les fragments d’expérience, et non pas cette option.

Pour les clients qui disposent d’offres héritées préexistantes, la variable **Utiliser le modèle d’offre** Les options sont visibles lors du ciblage des composants qui **not** Fragments d’expérience :

![Boîte de dialogue Convertir en variation de fragment d’expérience](/help/sites-cloud/authoring/assets/offers-legacy-target-non-experience-fragment.png)

## La console Offres {#offers-console}

>[!CAUTION]
>
>Cette console sera abandonnée à l’avenir, car elle offre un moyen hérité de personnaliser le contenu.
>
>Vous avez le temps de vous préparer. Découvrez comment [convertir vos offres héritées existantes en offre de fragment d’expérience](#convert-legacy-offer-to-experience-fragment).

Utilisez la console Offres pour créer des offres que vous pouvez [utilisation dans les expériences d’activité](/help/sites-cloud/authoring/personalization/targeted-content.md). La création d’offres dans la console Offres permet de gagner du temps lorsque plusieurs expériences nécessitent la même offre :

* Créez l’offre une fois dans la bibliothèque et utilisez-la pour plusieurs expériences associées aux activités de votre marque.
* La modification de l’offre dans la bibliothèque affecte toutes les expériences qui l’utilisent.

La console Offres classe les offres par marque. Chaque marque contient une bibliothèque d’offres qui peut être utilisée dans les expériences d’une marque. Utilisez des dossiers pour organiser hiérarchiquement les offres dans chaque bibliothèque. Une structure de dossiers logique permet aux auteurs de trouver facilement des offres en naviguant. Les outils de balisage et de recherche permettent également aux auteurs de trouver des offres.

### Ajout d’une marque dans la console Offres {#add-a-brand-using-the-offers-console}

Créez une marque à laquelle vos offres sont associées. Ouvrez une marque dans la console Offres pour accéder à la bibliothèque d’offres dans laquelle vous pouvez créer des dossiers et des offres.

Lorsque vous créez une marque à l’aide de la console Offres, elle apparaît également dans la [Console Activités](/help/sites-cloud/authoring/personalization/activities.md) où vous pouvez ajouter et administrer des activités pour la marque.

1. Dans la console de navigation, cliquez ou appuyez sur **Personnalisation** > **Offres**.

   ![Accès à la console Offres](/help/sites-cloud/authoring/assets/offers-navigation.png)

1. Cliquez ou appuyez sur **Créer**, puis sur **Créer** **une marque**.
1. Sélectionnez le modèle de la marque, puis cliquez ou appuyez sur **Suivant**.
1. Saisissez le titre de la marque tel que vous souhaitez le voir apparaître dans les consoles Offres et Activités . Vous pouvez également saisir ou sélectionner une ou plusieurs balises à associer à la marque.
1. Cliquez ou appuyez sur **Créer**.

### Ajout d’un fichier à une bibliothèque d’offres {#add-a-folder-to-an-offer-library}

Ajoutez un dossier à la bibliothèque d’offres d’une marque pour organiser et stocker les offres. Vous pouvez créer un dossier sous la marque ou sous d’autres dossiers.

1. Dans la console Offres, ouvrez l’emplacement où vous souhaitez créer le dossier. Par exemple, ouvrez la marque pour créer un dossier de niveau supérieur ou ouvrez un autre dossier dans la bibliothèque.
1. Cliquez ou appuyez sur **Créer** > **Créer un dossier ou une offre**.

   ![Création du dossier d’offres](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Sélectionnez **Dossier**, puis cliquez sur **Suivant**.
1. Entrez un titre pour le dossier tel qu’il doit apparaître dans la bibliothèque d’offres et saisissez ou sélectionnez des balises.

   ![Définition des propriétés du dossier](/help/sites-cloud/authoring/assets/offers-folder-properties.png)

1. Cliquez ou appuyez sur **Créer**.

### Ajout d’une offre à une bibliothèque d’offres {#add-an-offer-to-an-offer-library}

Ajoutez une offre à la bibliothèque d’offres d’une marque afin qu’elle puisse être ajoutée aux expériences de la marque. Lorsque vous ajoutez une offre, vous fournissez un titre. Vous pouvez également associer l’offre à une ou plusieurs balises pour améliorer la recherche.

Après avoir créé l’offre, vous pouvez l’ouvrir pour créer le contenu.

1. Dans la console Offres, ouvrez l’emplacement où vous souhaitez créer l’offre. Par exemple, ouvrez la marque pour créer une offre de niveau supérieur ou ouvrez un dossier dans la bibliothèque.
1. Cliquez ou appuyez sur **Créer** > **Créer un dossier ou une offre**.

   ![Création du dossier d’offres](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Sélectionnez la **Page d’offres** modèle , puis cliquez ou appuyez sur **Suivant**.
1. Saisissez un titre pour l’offre et éventuellement sélectionnez ou saisissez une ou plusieurs balises à associer à l’offre, puis cliquez ou appuyez sur . **Créer**.
1. Dans la boîte de dialogue de confirmation, pour ouvrir l’offre à modifier, cliquez ou appuyez sur **Ouvrir la page**.

### Modification d’une offre {#editing-an-offer}

Ouvrez une offre et modifiez le contenu tel que vous souhaitez le voir apparaître dans les expériences qui l’utilisent. Lorsque vous modifiez une offre qui est utilisée dans n’importe quelle expérience, vos modifications apparaissent dans les expériences.

Vous pouvez ouvrir une offre à partir d’un dossier dans une bibliothèque d’offres ou à partir des résultats de recherche. Vous pouvez également ouvrir une offre à partir d’une expérience qui utilise l’offre.

1. Dans la console Offres, appuyez ou cliquez sur l’icône en regard de l’offre, puis cliquez ou appuyez sur **Modifier**.
1. Ajoutez des composants à l’offre et modifiez le contenu du composant comme vous le faites habituellement.

### Suppression d’une offre {#deleting-an-offer}

Supprimez une offre lorsqu’elle n’est plus nécessaire. Lorsque vous tentez de supprimer une offre utilisée dans une expérience, vous êtes invité à confirmer la suppression. Confirmer supprime l’offre et la supprime des expériences.

Vous pouvez supprimer une offre tout en affichant le contenu d’un dossier dans une bibliothèque d’offres ou les résultats de la recherche.

1. Dans la console Offres, appuyez ou cliquez sur l’icône en regard de l’offre, puis cliquez ou appuyez sur **Supprimer**.

   Sélectionnez l’offre et cliquez ou appuyez sur **Supprimer**.

1. Dans la boîte de dialogue qui s’affiche, cliquez ou appuyez sur **Supprimer** pour confirmer la suppression.
1. Si l’offre est utilisée dans une ou plusieurs expériences, une boîte de dialogue s’affiche pour indiquer que l’offre est référencée :

   * Pour supprimer l’offre et la supprimer des expériences, cliquez ou appuyez sur **Forcer la suppression**.
   * Pour conserver l’offre, cliquez ou appuyez sur **Annuler**.

### Recherche d’offres {#searching-for-offers}

Recherchez les offres d’une marque quelconque à l’aide de mots-clés correspondant à leur titre.

![Recherche d’une offre](/help/sites-cloud/authoring/assets/offers-search.png)

Les critères de recherche actuels s’affichent en regard des résultats de recherche. Vous pouvez également trier les résultats par colonne dans l’ordre croissant ou décroissant. Vous pouvez effectuer une recherche à partir de n’importe quel dossier de n’importe quelle bibliothèque d’offres. Les résultats de la recherche sont les mêmes, quel que soit le dossier actif.

Pour rechercher des offres :

1. En haut de la console Offres, cliquez ou appuyez sur l’icône en forme de loupe. Par défaut, la recherche se limite aux offres.
1. Saisissez votre mot-clé pour rechercher des offres. Sélectionnez dans les résultats.
