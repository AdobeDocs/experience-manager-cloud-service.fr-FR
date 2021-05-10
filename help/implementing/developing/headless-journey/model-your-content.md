---
title: Comment modéliser votre contenu
description: Dans cette partie du Parcours de développement AEM sans en-tête, apprenez à modéliser votre contenu pour une diffusion sans en-tête AEM à l’aide de la modélisation de contenu à l’aide de modèles de fragments de contenu et de fragments de contenu.
hide: true
hidefromtoc: true
index: false
exl-id: f872839b-2401-4ea4-9e09-e5dda18afd09
translation-type: tm+mt
source-git-commit: 787af0d4994bf1871c48aadab74d85bd7c3c94fb
workflow-type: tm+mt
source-wordcount: '1830'
ht-degree: 4%

---

# Comment modéliser votre contenu {#model-your-content}

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette partie du [Parcours de développement AEM sans tête](overview.md), vous pouvez apprendre à modéliser votre structure de contenu. Ensuite, réalisez cette structure pour Adobe Experience Manager (AEM) à l’aide de modèles de fragments de contenu et de fragments de contenu, pour réutilisation entre canaux.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Au début [Découvrez la diffusion de contenu sans tête CMS Headless Development](learn-about.md) et pourquoi elle doit être utilisée. Ensuite [Prise en main de AEM sans en-tête en tant que Cloud Service](getting-started.md) décrit AEM sans en-tête dans le contexte de votre propre projet

Dans le document précédent du parcours sans tête, [Chemin vers votre première expérience à l’aide d’AEM sans tête](/help/implementing/developing/headless-journey/path-to-first-experience.md), vous avez ensuite appris les étapes nécessaires à la mise en oeuvre de votre premier projet. Après l&#39;avoir lu, vous devez :

* Comprendre les points importants de la planification pour concevoir votre contenu
* Comprenez les étapes à suivre pour implémenter sans tête en fonction des exigences de votre niveau d’intégration.
* Configurez les outils et les configurations AEM nécessaires.
* Découvrez les meilleures pratiques pour simplifier votre parcours sans tête, optimiser la génération de contenu et garantir la diffusion rapide du contenu.

Cet article s&#39;appuie sur ces principes de base pour vous permettre de comprendre comment préparer votre propre projet AEM sans tête.

## Intention {#objective}

* **Audience** : Début
* **Objectif** : Découvrez comment modéliser votre structure de contenu, puis réalisez-la à l’aide de AEM Modèles de fragments de contenu et de fragments de contenu :
   * Présenter les concepts et la terminologie liés à la modélisation des données/du contenu.
   * Découvrez pourquoi la modélisation de contenu est nécessaire pour la diffusion de contenu sans en-tête.
   * Découvrez comment réaliser cette structure à l’aide de modèles AEM de fragments de contenu (et créez du contenu avec des fragments de contenu).
   * Découvrez comment modéliser votre contenu ; principes avec des exemples de base.

>[!NOTE]
>
>La modélisation des données est un champ très volumineux, car il est utilisé lors du développement de bases de données relationnelles. Il y a beaucoup de livres, et de sources d&#39;information en ligne, disponibles.
>
>Nous ne tiendrons compte que des aspects qui présentent un intérêt lors de la modélisation des données à utiliser avec AEM sans en-tête.

## Modélisation de contenu {#content-modeling}

*C&#39;est un monde grand, mauvais là-bas*.

Peut-être, peut-être pas, mais c&#39;est certainement un grand ***monde complexe*** et la modélisation des données est utilisée pour définir une représentation simplifiée d&#39;une très (très) petite sous-section, en utilisant l&#39;information spécifique nécessaire à un certain but.

>[!NOTE]
>
>Comme AEM traite du contenu, nous faisons référence à la modélisation des données en tant que modélisation du contenu.

Par exemple :

Il y a beaucoup d&#39;écoles, mais elles ont toutes des choses en commun :

* Un emplacement
* Un professeur principal
* Beaucoup d&#39;enseignants
* Nombre de membres du personnel non enseignant
* Nombreux élèves
* Beaucoup d&#39;anciens enseignants
* Beaucoup d&#39;anciens élèves
* Beaucoup de salles de classe
* Beaucoup (beaucoup) de livres
* Beaucoup (beaucoup) d&#39;équipements
* De nombreuses activités extrascolaires
* et ainsi de suite....

Même dans un si petit exemple, la liste peut sembler sans fin. Mais si vous voulez simplement que votre application exécute une tâche simple, vous devez limiter les informations à l&#39;essentiel.

Par exemple, la publicité de événements spéciaux pour toutes les écoles de la région :

* Nom de l&#39;école
* Emplacement scolaire
* Chef enseignant
* Type de Événement
* Date du Événement
* Enseignant organisant le Événement

### Concepts {#concepts}

Ce que vous voulez décrire est appelé **Entités** - en gros les &quot;choses&quot; sur lesquelles nous voulons stocker des informations.

Les informations que nous voulons stocker à leur sujet sont les **attributs** (propriétés), tels que le nom et les qualifications pour les enseignants.

Ensuite, il y a différentes **relations** entre les entités. Par exemple, en général, une école n&#39;a qu&#39;un seul professeur principal, et de nombreux enseignants (et généralement le professeur principal est également enseignant).

Le processus d&#39;analyse et de définition de ces informations, ainsi que les relations entre elles, est appelé **Modélisation de contenu**.

### Concepts de base {#basics}

Souvent, vous devez début en élaborant un **Schéma conceptuel** qui décrit les entités et leurs relations. Il s&#39;agit généralement d&#39;un niveau élevé (conceptuel).

Une fois cette stabilité obtenue, vous pouvez convertir les modèles en **Schéma logique** qui décrit les entités, ainsi que les attributs et les relations. À ce niveau, vous devriez examiner de près les définitions pour éliminer les doublons et optimiser votre conception.

>[!NOTE]
>
>Parfois, ces deux étapes sont fusionnées, souvent en fonction de la complexité de votre scénario.

Par exemple, avez-vous besoin d’entités distinctes pour `Head Teacher` et `Teacher`, ou simplement d’un attribut supplémentaire sur le modèle `Teacher` ?

### Assurer l&#39;intégrité des données {#data-integrity}

L’intégrité des données est nécessaire pour garantir la précision et la cohérence de votre contenu, tout au long de son cycle de vie. Il s’agit notamment de veiller à ce que les auteurs de contenu puissent facilement comprendre où stocker, de sorte que les éléments suivants soient essentiels :

* une structure claire
* une structure aussi concise que possible (sans sacrifier la précision)
* validation de champs individuels
* le cas échéant, limiter le contenu de champs spécifiques à ce qui est significatif

### Élimination de la redondance des données {#data-redundancy}

La redondance des données se produit lorsque la même information est stockée deux fois dans la structure de contenu. Cela doit être évité car cela peut entraîner une confusion lors de la création du contenu et des erreurs lors de l&#39;interrogation ; sans parler de la mauvaise utilisation de l&#39;espace enregistrement.

### Optimisation et performances {#optimization-and-performance}

En optimisant votre structure, vous pouvez améliorer les performances, tant pour la création de contenu que pour l’interrogation.

Tout est un exercice d&#39;équilibre, mais la création d&#39;une structure trop complexe, ou à trop de niveaux, peut :

* Soyez déroutant lorsque les auteurs génèrent le contenu.

* Affecte gravement les performances si la requête doit accéder à plusieurs fragments de contenu imbriqués (référencés) pour récupérer le contenu requis.

## Modélisation de contenu pour AEM sans en-tête {#content-modeling-for-aem-headless}

La modélisation des données est un ensemble de techniques établies, souvent utilisées lors de bases de données de relations développées, alors que signifie la modélisation de contenu pour AEM sans en-tête ?

### Pourquoi ? {#why}

Pour que votre application puisse demander et recevoir de manière cohérente et efficace le contenu requis de AEM, ce contenu doit être structuré.

Cela signifie que votre application connaît à l&#39;avance la forme de la réponse et, par conséquent, comment la traiter. Il s’agit d’un processus beaucoup plus facile que de recevoir du contenu sous forme libre, qui doit être analysé pour déterminer ce qu’il contient et, par conséquent, comment il peut être utilisé.

### Présentation de Comment ? {#how}

AEM utilise les fragments de contenu pour fournir les structures nécessaires à la diffusion sans en-tête de votre contenu à vos applications.

La structure de votre modèle de contenu est la suivante :

* réalisée par la définition de votre modèle de fragment de contenu,
* utilisé comme base des fragments de contenu utilisés pour la génération de votre contenu.

>[!NOTE]
>
>Les modèles de fragments de contenu sont également utilisés comme base des Schémas GraphQL AEM, utilisés pour récupérer votre contenu - en savoir plus à ce sujet lors d’une session ultérieure.

Les demandes de contenu sont effectuées à l’aide de l’API GraphQL AEM, une implémentation personnalisée de l’API GraphQL standard. L’API GraphQL AEM vous permet d’effectuer des requêtes (complexes) sur vos fragments de contenu, chaque requête étant conforme à un type de modèle spécifique.

Le contenu renvoyé peut alors être utilisé par vos applications.

## Création de la structure avec des modèles de fragments de contenu {#create-structure-content-fragment-models}

Les modèles de fragments de contenu offrent divers mécanismes qui vous permettent de définir la structure de votre contenu.

Un modèle de fragment de contenu décrit une entité.

>[!NOTE]
>Vous devez activer la fonctionnalité Fragment de contenu dans l’explorateur de configuration afin de pouvoir créer de nouveaux modèles.

>[!TIP]
>
>Le modèle doit être nommé de sorte que l’auteur du contenu sache quel modèle sélectionner lors de la création d’un fragment de contenu.

Dans un modèle :

1. **Data** Type vous permet de définir les attributs individuels.
Par exemple, définissez le champ portant le nom d&#39;un enseignant sur **Texte** et ses années de service sur **Nombre**.
1. Les types de données **Référence du contenu** et **Référence du fragment** vous permettent de créer des relations avec d&#39;autres contenus dans AEM.
1. Le type de données **Référence du fragment** vous permet de réaliser plusieurs niveaux de structure en imbriquant vos fragments de contenu (selon le type de modèle). Il s’agit d’un élément essentiel pour la modélisation du contenu.

Par exemple :
![Modélisation de contenu avec des fragments de contenu](assets/headless-modeling-01.png "Modélisation de contenu avec des fragments de contenu")

### Types de données {#data-types}

AEM fournit les types de données suivants pour modéliser votre contenu :

* Une seule ligne de texte
* Plusieurs lignes de texte
* Nombre
* Booléen
* Date et heure
* Énumération
* Balises
* Référence de contenu
* Référence du fragment
* Objet JSON

### Références et contenu imbriqué {#references-nested-content}

Deux types de données fournissent des références au contenu en dehors d’un fragment spécifique :

* **Référence**
du contenuCette section fournit une référence simple à tout autre contenu de n&#39;importe quel type.
Par exemple, vous pouvez référencer une image à un emplacement spécifié.

* **Référence**
sur les fragmentsCette section contient des références à d’autres fragments de contenu.
Ce type de référence est utilisé pour créer du contenu imbriqué, en présentant les relations nécessaires pour modéliser votre contenu.
Le type de données peut être configuré pour permettre aux auteurs de fragments de procéder aux opérations suivantes :
   * Modifier directement le fragment référencé.
   * Créer un fragment de contenu, en fonction du modèle approprié.

### Création de modèles de fragments de contenu {#creating-content-fragment-models}

Au début même où vous devez activer les modèles de fragments de contenu pour votre site, cela se fait dans l’explorateur de configuration ; sous Outils -> Général -> Navigateur de configuration. Vous pouvez choisir de configurer l’entrée globale ou de créer une nouvelle configuration. Par exemple :

![Définir la configuration](assets/cfm-configuration.png)

>[!NOTE]
>
>Voir Ressources supplémentaires - Fragments de contenu dans l’explorateur de configuration

Ensuite, les modèles de fragments de contenu peuvent être créés et la structure définie. Vous pouvez le faire sous Outils > Ressources > Modèles de fragment de contenu. Par exemple :

![Modèle de fragment de contenu ](assets/cfm-model.png)

>[!NOTE]
>
>Voir Ressources supplémentaires - Modèles de fragments de contenu.

## Utilisation du modèle pour créer du contenu avec des fragments de contenu {#use-content-to-author-content}

Les fragments de contenu reposent toujours sur un modèle de fragment de contenu. Le modèle fournit la structure, le fragment contient le contenu.

### Sélection du modèle approprié {#select-model}

La première étape pour créer réellement votre contenu consiste à créer un fragment de contenu. Pour ce faire, utilisez Créer -> Fragment de contenu dans le dossier requis sous Ressources -> Fichiers. L&#39;assistant vous guidera tout au long des étapes.

Un fragment de contenu est basé sur un modèle de fragment de contenu spécifique que vous sélectionnez comme première étape du processus de création.

### Création et modification de contenu structuré {#create-edit-structured-content}

Une fois votre fragment créé, vous pouvez l’ouvrir dans l’éditeur de fragments de contenu. Vous pouvez effectuer les opérations suivantes :

* Modifiez votre contenu en mode normal ou plein écran.
* Mettez en forme votre contenu sous la forme Texte complet, Texte ordinaire ou Marquage.
* Créez et gérez des variantes de votre contenu.
* Associer le contenu.
* Modifiez les métadonnées.
* Afficher l&#39;arborescence.
* Prévisualisation de la représentation JSON.

### Création de fragments de contenu {#creating-content-fragments}

Après avoir sélectionné le modèle approprié, un fragment de contenu est ouvert pour modification dans l’éditeur de fragments de contenu :

![Éditeur de fragment de contenu](assets/cfm-editor.png)

>[!NOTE]
>
>Voir Ressources supplémentaires - Utilisation de fragments de contenu.

## Prise en main avec quelques exemples {#getting-started-examples}

<!--
tbc...
...and/or see the structures covered for the GraphQL samples...
...will those (ever) be delivered as an official sample package?
-->

Pour obtenir une structure de base en tant qu’exemple, voir Exemple de structure de fragment de contenu.

## Eléments suivants {#whats-next}

Maintenant que vous avez appris à modéliser votre structure et à créer du contenu en fonction de cela, l&#39;étape suivante consiste à [apprendre à utiliser les requêtes GraphQL pour accéder et récupérer votre contenu Fragments de contenu](access-your-content.md). Ceci va présenter et discuter GraphQL, puis regarder quelques exemples de requêtes pour voir comment les choses fonctionnent dans la pratique.

## Ressources supplémentaires {#additional-resources}

* [Utilisation de fragments](/help/assets/content-fragments/content-fragments.md)  de contenu : page de début des fragments de contenu
   * [Fragments de contenu dans l’explorateur](/help/assets/content-fragments/content-fragments-configuration-browser.md)  de configuration - activez la fonctionnalité Fragment de contenu dans l’explorateur de configuration.
   * [Modèles](/help/assets/content-fragments/content-fragments-models.md)  de fragment de contenu - création et modification de modèles de fragment de contenu
   * [Gestion des fragments](/help/assets/content-fragments/content-fragments-managing.md)  de contenu - création et création de fragments de contenu ; cette page vous conduira à d&#39;autres sections détaillées
* [AEM Schémas](/help/implementing/developing/headless-journey/access-your-content.md)  GraphQL - comment GraphQL réalise les modèles
* [Exemple de structure de fragment de contenu](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)
* [Prise en main de AEM sans tête](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=fr)  - Une courte série de didacticiels vidéo présentant l&#39;utilisation des fonctionnalités sans tête AEM, notamment la modélisation de contenu et GraphQL
