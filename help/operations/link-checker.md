---
title: Outil de vérification de lien
description: Découvrez comment le vérificateur de liens aide les auteurs et autrices en validant les liens lorsqu’ils sont ajoutés au contenu et les options de configuration qu’il propose.
feature: Operations
role: Admin
source-git-commit: cc8e242715faaef5cda25b428c315947ec3d7e06
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 48%

---


# Outil de vérification de lien {#link-checker}

Découvrez comment le vérificateur de liens aide les auteurs et autrices en validant les liens lorsqu’ils sont ajoutés au contenu et les options de configuration qu’il propose.

## Vue d’ensemble {#overview}

Les auteurs de contenu ne doivent pas avoir à valider chaque lien qu’ils incluent dans leur contenu. Le vérificateur de liens s’exécute automatiquement pour aider les créateurs et créatrices de contenu à gérer leurs liens, en prenant notamment en charge les tâches suivantes :

* La validation des liens lorsqu’ils sont ajoutés au contenu
* L’affichage d’une liste de tous les liens externes dans le contenu
* La réalisation des transformations de lien

Le vérificateur de liens comporte plusieurs [options de configuration](#configuring) telles que la définition de la validation des liens internes, le pouvoir d’omettre certains liens ou certains modèles de liens de la validation et la définition de règles de réécriture de liens.

Le vérificateur de liens valide les [liens internes](#internal) comme les [liens externes.](#external)

>[!NOTE]
>
>Le vérificateur de liens vérifiant les liens de chaque page de contenu, il peut avoir un impact sur les performances des référentiels volumineux. Dans ce cas, vous devrez peut-être [configurer la fréquence d’exécution du vérificateur de liens](#configuring) ou [le désactiver.](#disabling)

## Vérification des liens internes {#internal}

Les liens internes sont des liens vers d’autres contenus de votre référentiel AEM. Il est possible d’ajouter des liens internes à l’aide du sélecteur de chemin, de l’éditeur de texte enrichi ou d’un composant personnalisé. Par exemple :

* Vous créez la page `/content/wknd/us/en/adventures/ski-touring`
* Cette page contient un lien vers `/content/wknd/us/en/adventures/extreme-ironing` dans un [composant de texte.](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/wcm-components/text)

Les liens internes sont validés dès que l’auteur du contenu ajoute un lien de ce type à une page. Si le lien devient non valide :

* Il est supprimé de l’éditeur.
   * Le lien lui-même est supprimé.
   * Le texte du lien est conservé.
* il s’affiche sous la forme d’un lien rompu dans l’interface de création.

![Vérification des liens internes par le vérificateur de liens](assets/link-checker-internal.png)

## Vérification de lien externe {#external}

Les liens externes sont des liens vers du contenu placé en dehors de votre référentiel AEM. Vous pouvez ajouter des liens externes à l’aide de l’éditeur de texte enrichi ou d’un composant personnalisé. Par exemple :

* Vous créez la page `/content/wknd/us/en/adventures/ski-touring`
* Cette page contient un lien vers `https://bunwarmerthermalunderwear.com` dans un [composant de texte.](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/wcm-components/text)

Les liens externes sont validés en termes de syntaxe et de disponibilité. Cette vérification est effectuée de manière asynchrone à un intervalle configurable. Si le vérificateur de liens trouve un lien externe non valide :

* Il est supprimé de l’éditeur.
   * Le lien lui-même est supprimé.
   * Le texte du lien est conservé.
* il s’affiche sous la forme d’un lien rompu dans l’interface de création.

![Vérification des liens externes par le vérificateur de liens](assets/link-checker-external.png)

### Fonctionnement du Vérificateur de lien externe {#external-details}

Le Vérificateur de lien externe repose sur plusieurs services et comprendre leur fonctionnement peut vous aider à comprendre comment [configurer le Vérificateur de lien pour qu’il réponde à vos besoins.](#configuring)

1. Chaque fois qu’un auteur de contenu enregistre un lien vers une page, un gestionnaire d’événements est déclenché.
1. Le gestionnaire d’événements parcourt tout le contenu sous `/content` et recherche les liens nouveaux ou mis à jour et les ajoute à un cache pour le vérificateur de liens.
1. Le **Service de vérification de lien Day CQ** s’exécute ensuite selon un calendrier régulier afin de vérifier les entrées du cache et la validité de leur syntaxe.
1. Les liens validés par la syntaxe s’affichent alors dans la fenêtre [ Vérificateur de lien externe .](#external-using) Cependant, ils auront le statut **En attente**.
1. La **Tâche de vérification de lien Day CQ** s’exécute ensuite régulièrement pour valider les liens en effectuant un appel GET.
1. La **Tâche de vérification de lien Day CQ** met ensuite à jour les entrées de la [fenêtre du Vérificateur de lien externe](#external-using) avec les résultats des appels GET.

### Utilisation du Vérificateur de lien externe {#external-using}

Le Vérificateur de lien externe est une console qui fournit un aperçu de tous les liens externes de votre contenu AEM. Pour utiliser le Vérificateur de lien externe, procédez comme suit :

1. Dans la navigation globale, sélectionnez **Outils** -> **Sites**.
1. Sélectionnez **Vérificateur de lien externe** et une liste de tous les liens externes est affichée.

![ Vérificateur de lien externe ](assets/external-link-checker.png)

Chaque entrée du tableau représente un lien externe détecté par le service Vérificateur de liens. Les colonnes affichées sont les suivantes :

* **Statut** - Le statut de validation du lien, qui peut être l’un des suivants :
   * **Valide** - Le lien externe est accessible par le vérificateur de liens.
   * **En attente** - Le lien externe a été ajouté au contenu du site, mais n’a pas encore été validé par le vérificateur de liens.
   * **Non valide** - Le vérificateur de liens ne peut pas accéder au lien externe.
* **URL** - Lien externe
* **Référent** - Page de contenu contenant le lien externe
   * Celle-ci n’est renseignée que [si elle est configurée.](#configuring)
* **Dernière vérification** - Dernière fois que le vérificateur de lien a validé le lien externe
   * La fréquence de vérification des liens [est configurable.](#configuring)
* **Dernier statut** - Dernier code de statut HTML renvoyé lors de la dernière vérification du lien effectuée sur le lien externe
* **Dernier disponible** - Temps écoulé depuis la dernière fois que le lien était disponible pour le vérificateur de liens
* **Dernier accès** - Temps écoulé depuis le dernier accès à la page contenant le lien externe dans l’interface de création

Vous pouvez manipuler le contenu de la fenêtre à l&#39;aide des deux boutons situés en haut de la liste des liens :

* **Actualiser** - Pour actualiser le contenu de la liste
* **Vérifier** - Pour vérifier un lien externe individuel sélectionné dans la liste

Toutes les autres icônes de la fenêtre Vérificateur de lien externe sont inactives.

## Configuration du Vérificateur de lien {#configuring}

Le Vérificateur de lien est automatiquement disponible dans AEM. Cependant, plusieurs configurations OSGi peuvent être modifiées pour modifier son comportement :

* **Service de stockage d’informations du Vérificateur de lien Day CQ** - Ce service définit la taille du cache du Vérificateur de liens dans le référentiel.
* **Service de vérification de lien Day CQ** - Ce service effectue une vérification asynchrone de la syntaxe des liens externes.
   * Vous pouvez définir la période de vérification et les types de liens qui sont ignorés par le Vérificateur, parmi d’autres options.
* **Tâche de vérification de lien Day CQ** - Ce service effectue la validation GET des liens externes.
   * Il permet de définir des intervalles distincts pour vérifier les liens bons et mauvais, parmi d’autres options.
* **Transformateur du Vérificateur de liens Day CQ** - Ce service convertit les liens en fonction d’un ensemble de règles défini par l’utilisateur.

Consultez le document [Configuration d’OSGi](/help/implementing/deploying/configuring-osgi.md) pour plus d’informations sur la modification des paramètres OSGi.

## Désactivation du Vérificateur de liens {#disabling}

Vous pouvez choisir de désactiver entièrement le Vérificateur de liens. Pour ce faire :

1. ouvrez la console OSGi ;
1. modifiez le **Transformateur du Vérificateur de liens Day CQ** ;
1. cochez la ou les options que vous souhaitez désactiver :
   * **Désactiver la vérification** - Pour désactiver la validation des liens
   * **Désactiver la réécriture** - Pour désactiver les transformations des liens
