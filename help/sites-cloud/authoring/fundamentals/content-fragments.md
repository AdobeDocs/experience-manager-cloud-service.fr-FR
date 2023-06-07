---
title: Fragments de contenu
description: Les fragments de contenu d’Adobe Experience Manager as a Cloud Service vous permettent de concevoir, de créer, d’organiser et d’utiliser du contenu indépendant des pages
exl-id: 7a44fc4e-3793-4aa3-8c21-db0567c93244
source-git-commit: 3f7c9240a81062c335c33b0e59971de43cacf87b
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 100%

---

# Fragments de contenu {#content-fragments}

Les fragments de contenu d’Adobe Experience Manager (AEM) as a Cloud Service sont [créés et gérés en tant que ressources indépendantes de la page](/help/sites-cloud/administering/content-fragments/content-fragments.md).

Ils vous permettent de créer du contenu compatible avec tous les canaux, ainsi que des variations (éventuellement spécifiques aux canaux). Vous pouvez ensuite utiliser ces fragments et leurs variantes lors de la création de vos pages de contenu.

En même temps que l’outil d’exportation JSON mis à jour, les fragments de contenu structuré peuvent également être utilisés pour diffuser du contenu AEM via Content Services à des canaux autres que des pages AEM.

>[!NOTE]
>
>Les **fragments de contenu** et les **[fragments d’expérience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)** représentent deux fonctions distinctes d’AEM :
>* Les **fragments de contenu** sont des contenus éditoriaux, avec définition et structure, mais sans conception visuelle et/ou mise en page supplémentaires. Ils permettent d’accéder aux données structurées telles que les textes, les nombres et les dates, entre autres.
>* Les **fragments d’expérience** désignent un contenu parfaitement mis en page : un fragment de page web.
>
>Les fragments d’expérience peuvent être composés de contenu sous la forme de fragments de contenu, mais pas l’inverse.
>
>Pour plus d’informations, voir également [Présentation des fragments de contenu et d’expérience dans AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=fr#content-fragments).

>[!CAUTION]
>
>Cette page doit être consultée en complément de la page [Utilisation de fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments.md) (et des pages annexes), car elle présente la terminologie et les concepts de base, ainsi que la création et la gestion de fragments.

Les fragments de contenu permettent :

* **Stratégie de marketing et de campagne**
   * Examinent le contenu par le biais de fragments de contenu gérés de manière centralisée.
* **Créatrices et créateurs professionnels**
   * Suivi des ressources de création via des collections associées à des fragments de contenu.
* **Rédacteurs et rédactrices**
   * Écrivent dans l’éditeur de fragments de contenu AEM.
   * Peuvent créer des variations de contenu.
   * Peuvent associer du contenu pertinent au fragment de contenu.
   * Peuvent utiliser le contrôle de version/workflow.
   * Peuvent partager un fragment de contenu.
   * Peuvent gérer les traductions de manière centralisée.
* **Producteurs et responsable parcours**
   * Effectuent une sélection à partir de fragments et de variations prédéfinis avec la création dans AEM.
   * Peuvent compter sur la mise à jour en continu des fragments et du contenu associé à mesure que les rédacteurs et les rédactrices, et les créateurs et créatrices, effectuent leurs mises à jour dans des ressources et des fragments gérés de manière centralisée.
   * Peuvent compter sur un contenu multimédia associé traité pour être pertinent.
   * Peuvent créer des variations de contenu ad hoc à la volée tout en s’assurant que celles-ci restent gérées de manière centralisée dans le fragment.

## Ajout d’un fragment de contenu à une page {#adding-a-content-fragment-to-your-page}

1. Ouvrez la page à modifier.
2. Ajoutez le composant **Fragment de contenu** à partir du navigateur **Composants** ou **Insérer un nouveau composant**.
3. Vous pouvez effectuer l’une des actions suivantes :
   * Ouvrir l’explorateur de **ressources** et filtrer sur **Fragments de contenu** (la valeur par défaut est Images). Faire ensuite glisser le fragment requis sur l’instance du composant.
   * Sélectionner le composant de fragment de contenu, puis **Configurer** dans la barre d’outils. Dans la boîte de dialogue, vous pouvez ouvrir la boîte de dialogue de sélection afin de rechercher et de sélectionner le **fragment de contenu** requis.

   >[!NOTE]
   >
   >L’autre méthode consiste à faire glisser un fragment de contenu directement sur la page. Le composant associé est ainsi automatiquement créé (Fragment de contenu).

4. Au début, le contenu des éléments **Principal** et **Maître** (variation) est affiché. Vous pouvez [sélectionner d’autres éléments et/ou variantes](#selecting-the-element-or-variation) en fonction de vos besoins.

   ![Fragments de contenu dans l’explorateur de ressources](/help/sites-cloud/authoring/assets/content-fragments.png)

   >[!NOTE]
   >
   >Pour plus d’informations sur les autres fonctionnalités d’édition, consultez aussi :
   >
   >* [Mise en page réactive](/help/sites-cloud/authoring/features/responsive-layout.md)
   >* [Modification du contenu de la page](/help/sites-cloud/authoring/fundamentals/editing-content.md)


### Sélection de l’élément ou de la variation {#selecting-the-element-or-variation}

Ouvrez la boîte de dialogue **Configuration** du fragment pour configurer le fragment à utiliser dans la page active. La boîte de dialogue peut dépendre du composant utilisé.

>[!NOTE]
>
>Voir aussi [Composants principaux, le composant de fragment de contenu](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=fr)

Dans la boîte de dialogue de configuration appropriée, vous pouvez sélectionner les paramètres disponibles, notamment :

* **Fragment de contenu**
   * Indiquez le fragment à utiliser.
* **Mode d’affichage** :
   * **Un seul élément texte**
   * **Plusieurs éléments**
* **Élément**
   * Une sélection est disponible en fonction du modèle utilisé.

   >[!NOTE]
   >
   >Les éléments disponibles dépendent du modèle utilisé.

* **Variation**
   * Le **maître** par défaut sera toujours disponible.
   * La sélection est disponible si vous avez créé des variations pour le fragment.

* **ID**

   * Attribut d’**identification HTML** à appliquer au composant.

### Connexion rapide à l’éditeur de fragment {#quick-connection-to-fragment-editor}

Vous pouvez ouvrir la source du fragment à modifier (la ressource) à l’aide de l’icône **Modifier** située dans la barre d’outils du composant. Vous pourrez ainsi [modifier et gérer le fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragments.md).

>[!CAUTION]
>
>Comme toujours, la modification de la source du fragment affectera toutes les pages qui font référence à ce fragment de contenu.

### Ajout de contenu intermédiaire {#adding-in-between-content}

Lorsqu’un fragment de contenu spécifique est ajouté à la page, il y a un espace réservé **Faire glisser des composants ici** entre chaque paragraphe de HTML (et en haut/en bas) du fragment.

Vous pouvez ainsi ajouter du contenu supplémentaire [(contenu intermédiaire)](/help/sites-cloud/administering/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) dans le contenu du fragment (à l’un des points disponibles), sans avoir à modifier le fragment racine.

Pour le contenu intermédiaire, vous pouvez :

* Ajouter des composants à partir de l’[explorateur de composants](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).
* Ajouter des ressources à partir de l’[explorateur de ressources](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
* Utiliser du [contenu associé](#using-associated-content) comme source de contenu intermédiaire.

>[!CAUTION]
>
>Le contenu intermédiaire est du contenu de page. Il n’est pas stocké dans le fragment de contenu.

![Insérer le composant](/help/sites-cloud/authoring/assets/content-fragments-insert.png)

>[!NOTE]
>
>Vous pouvez également [insérer des ressources visuelles (images) dans le fragment](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
>
>Les ressources visuelles insérées sont liées au paragraphe précédent dans le fragment. Cela signifie que vous ne pouvez pas placer le contenu intermédiaire entre une ressource visuelle et le paragraphe précédent. Si vous avez besoin de ce niveau de connexion, vous pouvez ajouter l’image au fragment (en tant que [fragment de média mixte](/help/sites-cloud/administering/content-fragments/content-fragments.md#fragments-with-visual-assets)).

>[!CAUTION]
>
>Une fois le contenu intermédiaire ajouté à un fragment de votre page, la modification de la structure du fragment de contenu sous-jacent (c’est-à-dire dans l’éditeur de fragment de contenu) risque de donner lieu à des résultats erronés/inattendus.
>
>Si cela se produit, le contenu intermédiaire est conservé tel quel :
>
>* Les composants intermédiaires ont une position absolue dans la séquence de composants dans le flux du fragment. Cette position ne change pas, même lorsque le contenu des paragraphes du fragment change.
>
>  Cela peut donner l’impression que le positionnement relatif a changé, dans la mesure où les paragraphes intermédiaires n’ont aucune relation contextuelle avec les paragraphes (de fragment) près desquels ils sont placés.
>* À moins que ces deux structures de paragraphes ne soient en conflit ; dans ce cas, le contenu intermédiaire n’est pas affiché (bien qu’il soit toujours présent en interne).


### Utilisation de contenu associé {#using-associated-content}

Si vous avez [associé du contenu](/help/sites-cloud/administering/content-fragments/content-fragments-assoc-content.md) au [fragment de contenu](/help/sites-cloud/administering/content-fragments/content-fragments.md), ces ressources seront disponibles à partir du panneau latéral (après avoir placé le fragment sur la page de contenu). Le contenu associé est en fait une source spéciale de contenu pour le [contenu intermédiaire](/help/sites-cloud/administering/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments).

>[!NOTE]
>
>Vous pouvez ajouter des [ressources visuelles (des images, par exemple)](/help/sites-cloud/administering/content-fragments/content-fragments.md#fragments-with-visual-assets) au fragment et/ou à la page de plusieurs manières différentes.

>[!NOTE]
>
>Si une page contient plusieurs fragments de contenu, l’onglet **Contenu associé** affiche les ressources appropriées à tous les fragments.

Une fois que vous avez ajouté un fragment avec du contenu associé à votre page, un nouvel onglet (**Contenu associé**) s’ouvre dans le panneau latéral.

Dans cet onglet, vous pouvez faire glisser les ressources vers l’emplacement souhaité (un composant existant ou une position où le composant adéquat sera créé) :

![Insertion d’une image](/help/sites-cloud/authoring/assets/content-fragments-image.png)

### Ressources insérées dans le fragment {#assets-inserted-into-the-fragment}

Si des ressources (des images, par exemple) ont été insérées dans le fragment proprement dit (en tant que [fragments de médias mixtes](/help/sites-cloud/administering/content-fragments/content-fragments.md#fragments-with-visual-assets)), les options permettant de les modifier dans l’éditeur de page sont alors limitées.

Dans le cas d’une image, par exemple, vous pouvez effectuer les opérations suivantes :

* Recadrer, faire pivoter ou retourner l’image.
* Ajouter un titre ou un texte secondaire.
* Spécifier une taille.
* Vous pouvez également configurer la mise en page.

D’autres modifications telles que le déplacement, la copie et la suppression, doivent être effectuées dans l’éditeur de fragments.

### Publication {#publishing}

Les fragments doivent être publiés pour pouvoir être utilisés dans les pages web que vous avez publiées :

* Un fragment peut être publié une fois qu’il a été [créé dans la console Fragments de contenu](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#publishing-and-previewing-a-fragment).
* Si un *fragment dépublié* est utilisé dans une page en cours de publication, le fragment peut également être publié à ce moment.

## Exportation de fragments de contenu {#exporting-content-fragments}

Pour l’exportation vers Adobe Target, JSON peut être utilisé pour diffuser le fragment. Voir :

* [Intégration à Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Exportation de fragments de contenu vers Adobe Target](/help/sites-cloud/integrating/content-fragments-target.md)
