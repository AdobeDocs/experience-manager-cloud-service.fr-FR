---
title: Modèles de fragment de contenu
description: Découvrez comment les modèles de fragment de contenu constituent la base de votre contenu découplé dans AEM et comment créer des fragments de contenu avec du contenu structuré.
feature: Fragments de contenu
role: User
exl-id: fd706c74-4cc1-426d-ab56-d1d1b521154b
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '2309'
ht-degree: 100%

---

# Modèles de fragment de contenu {#content-fragment-models}

Les modèles de fragment de contenu d’AEM définissent la structure du contenu de vos [fragments de contenu](/help/assets/content-fragments/content-fragments.md) et servent de base à votre contenu découplé.

Pour utiliser des modèles de fragments de contenu, procédez comme suit :

1. [Activez la fonctionnalité Modèle de fragment de contenu pour votre instance.](/help/assets/content-fragments/content-fragments-configuration-browser.md)
1. [Créez](#creating-a-content-fragment-model) et [configurez](#defining-your-content-fragment-model) vos modèles de fragments de contenu.
1. [Activez les modèles de fragments de contenu](#enabling-disabling-a-content-fragment-model) à utiliser pour la création de fragments de contenu.
1. [Autorisez vos modèles de fragments de contenu sur les dossiers de ressources](#allowing-content-fragment-models-assets-folder) en configurant des **stratégies**.

## Création d’un modèle de fragment de contenu {#creating-a-content-fragment-model}

1. Accédez à **Outils**, **Ressources**, puis ouvrez les **modèles de fragment de contenu**.
1. Accédez au fichier adapté votre [configuration](/help/assets/content-fragments/content-fragments-configuration-browser.md).
1. Utilisez le bouton **Créer** pour ouvrir l’assistant.

   >[!CAUTION]
   >
   >Si l’[utilisation des modèles de contenu du fragment n’a pas été activée](/help/assets/content-fragments/content-fragments-configuration-browser.md), l’option **Créer** n’est pas disponible.

1. Spécifiez le **Titre du modèle**. Vous pouvez également ajouter des **balises**, une **description** et sélectionner **Activer le modèle** pour [activer le modèle](#enabling-disabling-a-content-fragment-model), si nécessaire.

   ![titre et description](assets/cfm-models-02.png)

1. Utilisez le bouton **Créer** pour enregistrer le modèle vide. Un message indique que l’action a réussi. Vous pouvez alors sélectionner **Ouvrir** pour publier immédiatement le modèle ou **Terminé** pour revenir à la console.

## Définition de votre modèle de fragment de contenu  {#defining-your-content-fragment-model}

Le modèle de fragment de contenu définit effectivement la structure des fragments de contenu résultants à l’aide d’une sélection de **[Types de données](#data-types)**. Grâce à l’éditeur de modèles, vous pouvez ajouter des instances de types de données, puis les configurer pour créer les champs requis :

>[!CAUTION]
>
>La modification d’un modèle de fragment de contenu existant peut avoir un impact sur les fragments dépendants.

1. Accédez à **Outils**, **Ressources**, puis ouvrez les **modèles de fragment de contenu**.

1. Accédez au dossier contenant votre modèle de fragment de contenu.
1. Ouvrez le modèle requis pour l’**édition**. Utilisez l’action rapide ou sélectionnez le modèle puis l’action dans la barre d’outils.

   Une fois ouvert, l’éditeur de modèles affiche :

   * à gauche : les champs déjà définis
   * à droite : les **types de données** disponibles pour la création des champs (et les **propriétés** à utiliser une fois les champs créés).

   >[!NOTE]
   >
   >Lorsqu’un champ est **obligatoire**, le **libellé** indiqué dans le volet de gauche est signalé par un astérisque (*****).

![propriétés](assets/cfm-models-03.png)

1. **Pour ajouter un champ**

   * Faites glisser un type de données à l’emplacement souhaité pour un champ :

      ![type de données dans le champ](assets/cfm-models-04.png)

   * Une fois qu’un champ a été ajouté au modèle, le panneau de droite affiche les **propriétés** qui peuvent être définies pour ce type de données spécifique. Vous pouvez définir ce qui est obligatoire pour ce champ.

      * De nombreuses propriétés s’expliquent d’elles-mêmes. Pour plus d’informations, voir [Propriétés](#properties).
      * Si vous entrez un **libellé de champ**, le **nom de propriété** est automatiquement renseigné. S’il est vide, il peut être mis à jour manuellement par la suite.

      Par exemple :

      ![propriétés de champ](assets/cfm-models-05.png)


1. **Pour supprimer un champ**

   Sélectionnez le champ, puis cliquez/appuyez sur l’icône représentant une corbeille. Vous serez alors invité à confirmer l’opération.

   ![supprimer](assets/cfm-models-06.png)

1. Ajoutez tous les champs obligatoires et définissez les propriétés connexes, le cas échéant. Par exemple :

   ![save](assets/cfm-models-07.png)

1. Sélectionnez **Enregistrer** pour conserver la définition.

## Types de données {#data-types}

Une sélection de types de données est disponible pour la définition de votre modèle :

* **Une seule ligne de texte**
   * Ajoutez un ou plusieurs champs d’une seule ligne de texte ; il est possible de définir la longueur maximale.
* **Plusieurs lignes de texte**
   * Zone de texte pouvant contenir du texte enrichi, du texte brut ou du texte Markdown.
* **Nombre**
   * Ajoutez un ou plusieurs champs numériques
* **Booléen**
   * Ajoutez une case à cocher booléenne
* **Date et heure**
   * Ajoutez une date et/ou une heure
* **Énumération**
   * Ajoutez un ensemble de cases à cocher, de boutons radio ou de champs déroulants
* **Balises**
   * Permet aux auteurs de fragments d’accéder à des zones de balises et de les sélectionner.
* **Référence de contenu**
   * Fait référence à d’autres contenus, tous types confondus ; peut être utilisée pour [créer du contenu imbriqué](#using-references-to-form-nested-content).
   * Si une image est référencée, vous pouvez choisir d’afficher une miniature.
* **Référence du fragment**
   * Fait référence à d’autres fragments de contenu, tous types confondus ; peut être utilisée pour [créer du contenu imbriqué](#using-references-to-form-nested-content).
   * Le type de données peut être configuré pour permettre aux auteurs de fragments de procéder aux opérations suivantes :
      * Modifier directement le fragment référencé.
      * Créer un fragment de contenu, en fonction du modèle approprié.
* **Objet JSON**
   * Permet à l’auteur du fragment de contenu de saisir la syntaxe JSON dans les éléments correspondants d’un fragment.
      * Permettre à AEM de stocker directement JSON que vous avez copié/collé à partir d’un autre service.
      * Le fichier JSON est transmis et généré sous la forme JSON dans GraphQL.
      * Inclut la mise en surbrillance de la syntaxe JSON, la saisie semi-automatique et la mise en surbrillance des erreurs dans l’éditeur de fragments de contenu.
* **Espace réservé pour tabulation**
   * Permet l’introduction d’onglets à utiliser lors de la modification du contenu du fragment de contenu.
Il s’affiche sous forme de séparateur dans l’éditeur de modèles et permet de séparer les sections de la liste des types de données de contenu. Chaque instance représente le début d’un nouvel onglet.
Dans l’éditeur de fragments, chaque instance s’affiche sous la forme d’un onglet.

      >[!NOTE]
      Ce type de données est uniquement utilisé à des fins de mise en forme. Il est ignoré par le schéma GraphQL AEM.

## Propriétés {#properties}

De nombreuses propriétés s’expliquent d’elles-mêmes. Pour certaines propriétés, les détails supplémentaires sont les suivants :

* **Rendu comme**
Les différentes options permettant de réaliser/rendre le champ dans un fragment. Il est ainsi souvent possible de définir si l’auteur verra une seule instance du champ ou s’il sera autorisé à créer plusieurs instances.

* **Libellé du champ**
La saisie d’un 
**libellé de champ** génère automatiquement un **nom de propriété**, qui peut ensuite être mis à jour manuellement, si nécessaire.

* **Validation**
La validation de base est disponible par le biais de mécanismes tels que la propriété **Requis**. Certains types de données comportent des champs de validation supplémentaires. Voir [Validation](#validation) pour plus de détails.

* Pour le type données **texte multiligne**, il est possible de définir le **type par défaut** en tant que :

   * **Texte enrichi**
   * **Texte (Markdown)**
   * **Texte brut**

   Si elle n’est pas spécifiée, la valeur par défaut **Texte enrichi** est utilisée pour ce champ.

   La modification du **type par défaut** dans un modèle de fragment de contenu prend effet uniquement sur un fragment de contenu existant et lié après l’ouverture et l’enregistrement du fragment dans l’éditeur.

* **Unique**
Le contenu (du champ spécifique) doit être unique dans tous les fragments de contenu créés à l’aide du modèle actuel.

   Cette propriété permet de s’assurer que les auteurs de contenu ne peuvent pas répéter le contenu déjà ajouté dans un autre fragment du même modèle.

   Par exemple, un champ **Une seule ligne de texte** appelé `Country` dans le modèle de fragment de contenu ne peut pas avoir la valeur `Japan` dans deux fragments de contenu dépendants. Un avertissement sera émis en cas de tentative concernant la deuxième instance.

   >[!NOTE]
   L’unicité est assurée par la racine de langue.

   >[!NOTE]
   Les variations peuvent avoir la même valeur *unique* que les variations du même fragment, mais pas la même valeur que celle utilisée dans une variation d’autres fragments.

* **Translatable**
Cocher la case Translatable (Traduisible) d’un champ de l’éditeur de modèles des fragments de contenu entraîne les conséquences suivantes :

   * S’assurer que le nom de la propriété du champ est ajouté à la configuration de traduction, contexte `/content/dam/<sites-configuration>`, s’il n’est pas déjà présent.
   * Pour GraphQL : définir une propriété `<translatable>` du champ Fragment de contenu sur `yes` afin d’autoriser le filtre de requête GraphQL pour la sortie JSON avec du contenu traduisible uniquement.

* Consultez la section **[Référence de contenu](#content-reference)** pour plus d’informations sur ce type de données spécifique et ses propriétés.

* Voir la section **[Référence du fragment (Fragments imbriqués)](#fragment-reference-nested-fragments)** pour plus d’informations sur ce type de données spécifique et ses propriétés.

## Validation {#validation}

Différents types de données incluent désormais la possibilité de définir les exigences de validation lorsque le contenu est saisi dans le fragment résultant :

* **Une seule ligne de texte**
   * Comparaison avec une expression régulière prédéfinie (regex).
* **Nombre**
   * Vérification de valeurs spécifiques.
* **Référence de contenu**
   * Test de types de contenu spécifiques.
   * Seuls peuvent être référencés des fichiers de taille de fichier spécifiée ou inférieure.
   * Seules peuvent être référencées les images d’une plage prédéfinie de largeur et/ou de hauteur (en pixels).
* **Référence du fragment**
   * Test d’un modèle de fragment de contenu spécifique.

## Utilisation de références pour former un contenu imbriqué {#using-references-to-form-nested-content}

Les fragments de contenu peuvent former du contenu imbriqué à l’aide de l’un des types de données suivants :

* **[Référence de contenu](#content-reference)**
   * Fournit une référence simple à un autre contenu, quel que soit son type.
   * Peut être configurée pour une ou plusieurs références (dans le fragment résultant).

* **[Référence du fragment](#fragment-reference-nested-fragments)** (fragments imbriqués)
   * Fait référence à d’autres fragments, en fonction des modèles spécifiques spécifiés.
   * Permet d’inclure/récupérer des données structurées.

      >[!NOTE]
      Cette méthode présente un intérêt particulier en conjonction avec la [Diffusion de contenu découplé utilisant des fragments de contenu à l’aide de GraphQL](/help/assets/content-fragments/content-fragments-graphql.md).
   * Peut être configurée pour une ou plusieurs références (dans le fragment résultant).

>[!NOTE]
AEM dispose d’une protection récurrente pour :
* Références du contenu
Cela empêche l’utilisateur d’ajouter une référence au fragment actif. L’approche peut conduire à une boîte de dialogue vide du sélecteur de référence du fragment.

* Références de fragments dans GraphQL
Si vous créez une requête profonde qui renvoie plusieurs fragments de contenu référencés les uns par les autres, elle renvoie la valeur « null » lors de la première occurrence.


### Référence de contenu {#content-reference}

La référence de contenu permet de générer du contenu à partir d’une autre source, par exemple, une image ou un fragment de contenu.

Outre les propriétés standard, vous pouvez spécifier les éléments suivants :

* Le **chemin racine** pour tout contenu référencé
* Types de contenu pouvant être référencés
* Limites relatives aux tailles de fichier
* Si une image est référencée :
   * Afficher la miniature
   * Limites de hauteur et de largeur pour l’image

![Référence de contenu](assets/cfm-content-reference.png)

### Référence du fragment (fragments imbriqués) {#fragment-reference-nested-fragments}

La référence du fragment fait référence à un ou plusieurs fragments de contenu. Cette fonctionnalité présente un intérêt particulier lors de la récupération de contenu pour une utilisation dans votre application, car elle permet de récupérer des données structurées comportant plusieurs calques.

Par exemple :

* Un modèle définissant les détails d’un employé. Il s’agit notamment des éléments suivants :
   * Référence au modèle qui définit l’employeur (entreprise)

```xml
type EmployeeModel {
    name: String
    firstName: String
    company: CompanyModel
}

type CompanyModel {
    name: String
    street: String
    city: String
}
```

>[!NOTE]
Cette méthode présente un intérêt particulier en conjonction avec la [Diffusion de contenu découplé utilisant des fragments de contenu à l’aide de GraphQL](/help/assets/content-fragments/content-fragments-graphql.md).

Outre les propriétés standard, vous pouvez définir les éléments suivants :

* **Afficher comme** :

   * **multifield** : l’auteur du fragment peut créer plusieurs références individuelles

   * **fragmentreference** : permet à l’auteur du fragment de sélectionner une référence unique à un fragment.

* **Type de modèle**
Il est possible de sélectionner plusieurs modèles. Lors de la création du fragment de contenu, tous les fragments référencés doivent avoir été créés à l’aide de ces modèles.

* **Chemin racine**
Indique un chemin racine pour tout fragment référencé.

* **Autoriser la création de fragments**

   Cette propriété permet à l’auteur du fragment de créer un nouveau fragment en fonction du modèle approprié.

   * **fragmentreferencecomposite** : permet à l’auteur du fragment de créer un composite en sélectionnant plusieurs fragments.

   ![Référence du fragment](assets/cfm-fragment-reference.png)

>[!NOTE]
Un mécanisme de protection contre les répétitions est en place. Il interdit à l’utilisateur de sélectionner le fragment de contenu actif dans la référence au fragment. L’approche peut conduire à une boîte de dialogue vide du sélecteur de référence du fragment.
Il existe également une protection contre les répétitions pour les références de fragments dans GraphQL. Si vous créez une requête profonde entre deux fragments de contenu qui se référencent mutuellement, elle renvoie la valeur « null ».

## Activation ou désactivation d’un modèle de fragment de contenu {#enabling-disabling-a-content-fragment-model}

Pour un contrôle total de l’utilisation de vos modèles de fragments de contenu, ils contiennent un état que vous pouvez définir.

### Activation d’un modèle de fragment de contenu {#enabling-a-content-fragment-model}

Une fois qu’un modèle a été créé, il doit être activé pour :

* Être disponible afin d’être sélectionné lors de la création d’un fragment de contenu.
* Pouvoir être référencé à partir d’un modèle de fragment de contenu.
* Être disponible pour GraphQL ; le schéma est ensuite généré.

Pour activer un modèle marqué comme :

* **Brouillon** : nouveau (jamais activé).
* **Désactivé** : a été spécifiquement désactivé.

Vous utilisez l’option **Activer** de l’une des manières suivantes :

* La barre d’outils supérieure, lorsque le modèle concerné est sélectionné.
* L’action rapide correspondante (placez le pointeur de la souris sur le modèle concerné).

![Activation d’un modèle Brouillon ou Désactivé](assets/cfm-status-enable.png)

### Désactivation d’un modèle de fragment de contenu {#disabling-a-content-fragment-model}

Un modèle peut également être désactivé afin que :

* Le modèle ne soit plus disponible comme base pour la création de *nouveaux* fragments de contenu.
* Toutefois :
   * Le schéma GraphQL continue à être généré et peut toujours être interrogé (pour éviter tout impact sur l’API JSON).
   * Tout fragment de contenu basé sur le modèle peut toujours être interrogé et renvoyé à partir du point d’entrée GraphQL.
* Le modèle ne peut plus être référencé, mais les références existantes sont conservées intactes et peuvent toujours être interrogées et renvoyées à partir du point d’entrée GraphQL.

Pour désactiver un modèle marqué comme **Activé**, utilisez l’option **Désactiver** de l’une des deux manières suivantes :

* La barre d’outils supérieure, lorsque le modèle concerné est sélectionné.
* L’action rapide correspondante (placez le pointeur de la souris sur le modèle concerné).

![Désactiver un modèle activé](assets/cfm-status-disable.png)

## Autorisation de modèles de fragments de contenu dans votre dossier de ressources {#allowing-content-fragment-models-assets-folder}

Pour mettre en œuvre une gouvernance du contenu, vous pouvez configurer des **Stratégies** sur le dossier de ressources pour contrôler les modèles de fragment de contenu autorisés pour la création de fragments dans ce dossier.

>[!NOTE]
Le mécanisme est similaire à [l’autorisation de modèles de page](/help/sites-cloud/authoring/features/templates.md#allowing-a-template-author) pour une page et ses enfants, dans les propriétés avancées d’une page.

Pour configurer les **stratégies** des **modèles de fragments de contenu autorisés** :

1. Recherchez et ouvrez les **Propriétés** pour le dossier de ressources requis.

1. Ouvrez l’onglet **Stratégies** pour configurer les éléments suivants :

   * **Hérité de`<folder>`**

      Les stratégies sont automatiquement héritées lors de la création de dossiers enfants ; il peut se produire une reconfiguration de la stratégie (et une rupture de l’héritage) si des sous-dossiers doivent autoriser des modèles différents du dossier parent.

   * **Modèles de fragments de contenu autorisés par chemin**

      Il est possible d’autoriser plusieurs modèles.

   * **Modèles de fragments de contenu autorisés par balise**

      Il est possible d’autoriser plusieurs modèles.
   ![Stratégie de modèle de fragment de contenu](assets/cfm-model-policy-assets-folder.png)

1. **Enregistrez** les modifications.

Les modèles de fragment de contenu autorisés pour un dossier sont résolus comme suit :
* **Stratégies** pour les **modèles de fragments de contenu autorisés**.
* Si elles sont absentes, essayez de déterminer la stratégie à l’aide des règles d’héritage.
* Si la chaîne d’héritage ne produit pas de résultat, examinez la configuration **Cloud Services** pour ce dossier (directement dans un premier temps, puis par héritage).
* Si aucun des éléments ci-dessus ne donne de résultats, il n’existe aucun modèle autorisé pour ce dossier.

## Suppression d’un modèle de fragment de contenu {#deleting-a-content-fragment-model}

>[!CAUTION]
La suppression d’un modèle de fragment de contenu peut avoir un impact sur les fragments dépendants.

Pour supprimer un modèle de fragment de contenu :

1. Accédez à **Outils**, **Ressources**, puis ouvrez les **modèles de fragment de contenu**.

1. Accédez au dossier contenant votre modèle de fragment de contenu.
1. Sélectionnez votre modèle, puis utilisez l’option **de suppression** de la barre d’outils.

   >[!NOTE]
   Si le modèle est référencé, un avertissement s’affiche. Prenez alors les mesures qui s’imposent.

## Publication d’un modèle de fragment de contenu  {#publishing-a-content-fragment-model}

Les modèles de fragment de contenu doivent être publiés avant ou pendant la publication des fragments de contenu dépendants.

Pour publier un modèle de fragment de contenu :

1. Accédez à **Outils**, **Ressources**, puis ouvrez les **modèles de fragment de contenu**.

1. Accédez au dossier contenant votre modèle de fragment de contenu.
1. Sélectionnez votre modèle, puis l’option de **publication** dans la barre d’outils.
L’état publié sera indiqué dans la console.

   >[!NOTE]
   Si vous publiez un fragment de contenu pour lequel le modèle n’a pas encore été publié, une liste de sélection indique cela, ainsi que le fait que le modèle sera publié avec le fragment.

## Annulation de la publication d’un modèle de fragment de contenu {#unpublishing-a-content-fragment-model}

Les modèles de fragment de contenu peuvent être annulés s’ils ne sont référencés par aucun fragment.

Pour annuler la publication d’un modèle de fragment de contenu :

1. Accédez à **Outils**, **Ressources**, puis ouvrez les **modèles de fragment de contenu**.

1. Accédez au dossier contenant votre modèle de fragment de contenu.
1. Sélectionnez votre modèle, puis l’option **Annuler la publication** dans la barre d’outils.
L’état publié sera indiqué dans la console.

## Modèle de fragment de contenu – Propriétés {#content-fragment-model-properties}

Vous pouvez modifier les **propriétés** d’un modèle de fragment de contenu :

* **De base**
   * **Titre du modèle**
   * **Balises**
   * **Description**
   * **Télécharger l’image**
