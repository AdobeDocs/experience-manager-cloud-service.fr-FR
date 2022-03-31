---
title: Création et gestion des canaux dans Screens as a Cloud Service
description: Cette page décrit comment créer et gérer des canaux dans Screens as a Cloud Service.
exl-id: 3b0bae7a-4a45-485a-ab04-604510ff6578
source-git-commit: afcee8019c9b59f3eb1fdcabd569272eeea76dab
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 50%

---

# Création et gestion d’un canal dans Screens as a Cloud Service {#creating-channels-screens-cloud}

Une fois que vous avez créé un projet AEM Screens, vous devez créer des canaux.
Les ***canaux*** affichent une séquence de contenu (images et vidéos), un site web ou une application d’une seule page.

## Objectif {#objective}

Ce document vous aide à comprendre la création et la gestion de canaux pour votre projet AEM Screens dans le fournisseur de contenu Screens. Après lecture, vous devriez être en mesure de :

* comprendre comment créer des canaux pour le fournisseur de contenu Screens ;
* gérer et modifier du contenu dans vos canaux.
* planning d’activation de vos canaux

## Procédure de création d’un canal de séquence dans Screens as a Cloud Service {#create-new-channel}

>[!NOTE]
>**Prérequis**
>Avant de commencer cette section du guide, consultez la section [Création et gestion de projets dans Screens as a Cloud Service](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md).

Pour créer un canal de séquence dans Screens as a Cloud Service, procédez comme suit :

1. Accédez au fournisseur de contenu Screens.

1. Accédez à votre projet AEM Screens, par exemple *FirstDigitalExperience*.

1. Sélectionnez le dossier **Canaux** de votre projet, par exemple **FirstDigitalExperience** --> **Canaux** et cliquez sur **Créer** dans la barre d’actions.

   ![](/help/screens-cloud/assets/create-content/channel-create1.png)

1. Sélectionnez le modèle, par exemple **Canal de séquence** dans l’assistant **Créer** et cliquez sur **Suivant**.

   ![](/help/screens-cloud/assets/create-content/channel-create2.png)
   >[!NOTE]
   > L’assistant **Créer** fournit différents types de modèles lors de la création d’un canal. Pour plus d’informations, reportez-vous à la section [Modèles disponibles](#available-templates) de l’assistant de création.

1. Saisissez le nom de votre canal de séquence, par exemple **LoopingChannelOne** et cliquez sur **Créer**.

   ![](/help/screens-cloud/assets/create-content/channel-create3.png)

   Un **LoopingChannelOne** apparaît désormais dans le dossier Canaux de votre projet AEM Screens.

   Une fois que vous avez créé le canal, vous pouvez ajouter du contenu à votre canal. Reportez-vous à la section [Ajout de contenu à un canal](#add-content) pour savoir comment ajouter des ressources (images/vidéos) à votre canal.

## Gestion d’un canal {#managing-channels}

Vous pouvez modifier, copier, prévisualiser, supprimer un canal, et afficher ses propriétés et son tableau de bord.

Accédez au canal à partir de votre projet et sélectionnez-le, comme illustré ci-dessous. Dans la barre d’action, vous pouvez désormais sélectionner les options telles que la modification du canal, l’affichage des propriétés, la prévisualisation du contenu, la gestion de la publication ou la suppression du canal.

![](/help/screens-cloud/assets/create-content/channelprop1.png)

### Ajout de contenu à un canal {#add-content}

Pour ajouter du contenu à un canal ou modifier son contenu, suivez les étapes ci-dessous :

1. Sélectionnez le canal que vous souhaitez modifier, tel qu’illustré ci-dessous. Cliquez sur **Modifier** dans l’angle supérieur gauche de la barre d’actions pour ouvrir l’éditeur.

   ![](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. L’éditeur vous permet d’ajouter au canal des ressources/composants que vous souhaitez publier.

1. Faites glisser et déposez les ressources à partir du volet de gauche et ajoutez-les à l’éditeur.

   ![](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >Cliquez sur **Aperçu** pour prévisualiser le contenu de votre canal.
   >![](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## Modèles disponibles dans l’assistant de création {#available-templates}

Les modèles suivants sont disponibles lors de l’utilisation de l’assistant de canal **Créer** :

| Modèles disponibles | Description |
|--- |--- |
| Dossier de canaux | Permet de créer un dossier où stocker une collection de canaux. |
| Canal de séquence | Permet de créer un canal qui lit les composants de manière séquentielle (l’un après l’autre comme une série de diapositives). |
| Canal d’écran partagé barre en L gauche ou droite | Permet aux auteurs de contenus d’afficher différents types de ressources dans des zones de taille appropriée. |

## Utilisation des détails d’attribution par défaut pour les canaux {#default-channels}

Cette fonctionnalité vous permet de définir un planning d’activation par défaut pour un canal et de l’utiliser par défaut pour chaque affectation pour un affichage. Il fournit une méthode permettant de ne pas répéter la définition de planification encombrante.

### Création des détails d’affectation par défaut d’un canal {#create-default}

1. Accédez à la page de détails du canal que vous souhaitez configurer.
1. Recherchez la variable **Détails de l’affectation par défaut** sur la page.

   ![image](/help/screens-cloud/assets/display/Assignment1.png)

1. Cliquez sur **Définition des détails par défaut**.
1. Configurez les détails de l’affectation par défaut, notamment la priorité, les dates de début et de fin, ainsi que les modèles de périodicité pour le canal, puis cliquez sur **Attribuer**.

   ![image](/help/screens-cloud/assets/display/Assignments2.png)

1. Notez que les détails de l’affectation sont affichés dans le **Détails de l’affectation par défaut** mosaïque :

   ![image](/help/screens-cloud/assets/display/Assignments3.png)

Cette mosaïque affiche les informations suivantes :
* Priorité par défaut du canal dans l’affichage.
* Les dates de début et de fin de l’activation lorsque la lecture du canal est planifiée.
* Vue synthétique de la périodicité (horaire/quotidien/hebdomadaire/mensuel/annuel, ainsi que nom donné à cette périodicité).

### Utilisation des détails d’affectation par défaut lors de l’affectation à un affichage {#default-display}

Les canaux dont les détails d’affectation par défaut peuvent être affectés affichent de la même manière que les canaux standard, avec l’option ajoutée pour exploiter les détails d’affectation par défaut au lieu de définir manuellement ceux qui sont personnalisés à chaque fois.

1. Accédez à la page des détails d’affichage à laquelle vous souhaitez attribuer le canal, puis cliquez sur le bouton **Attribuer le canal**.
vous pouvez également sélectionner l’affichage souhaité dans la vue d’inventaire et cliquer sur le bouton **Attribuer le canal**.
1. La boîte de dialogue d’attribution de canaux s’ouvre.

   ![image](/help/screens-cloud/assets/display/Assignments4.png)

1. Sélectionnez le canal souhaité qui comporte les détails d’attribution par défaut dans le sélecteur de canal.
1. Notez les modifications apportées à la boîte de dialogue d’attribution de canal pour vous permettre de choisir les détails d’attribution par défaut ou de sélectionner des détails personnalisés :

   ![image](/help/screens-cloud/assets/display/Assignments5.png)

1. Cliquez sur **Attribuer** pour finaliser l’affectation, ou cliquez sur **Définition des détails d’affectation personnalisée** si vous préférez remplacer les valeurs par défaut par d’autres valeurs dans le contexte de cet affichage particulier.

   ![image](/help/screens-cloud/assets/display/Assignments6.png)

1. Remarquez la variable **Canaux attribués** La mosaïque est mise à jour avec la nouvelle affectation :

   ![image](/help/screens-cloud/assets/display/Assignments7.png)

1. Notez que les canaux auront une icône différente selon qu’ils utilisent des plannings personnalisés (icône de cadenas) ou héritent des détails par défaut (icône représentant une horloge mondiale). Cliquez ensuite sur ces icônes pour afficher les détails de la planification.
1. Notez également que les actions disponibles pour chaque type diffèrent.

   ![image](/help/screens-cloud/assets/display/Assignments8.png)

**Remarque :** Une affectation de canal qui utilise les détails d’attribution par défaut ne sera pas modifiable dans le contexte de l’affichage.

* Si vous devez le modifier en affectation personnalisée, vous devrez d’abord le supprimer, puis le rajouter à l’aide de la fonction **Définition des détails d’affectation personnalisée** .
* Si vous devez modifier les propriétés des détails d’affectation par défaut, vous devrez effectuer cette opération directement à partir de la page des détails du canal.

### Suppression des détails d’attribution par défaut d’un canal {#remove-display}

1. Accédez à la page des détails du canal que vous souhaitez supprimer les détails d’attribution par défaut.
1. Recherchez la variable **Détails de l’affectation par défaut** mosaïque dans la page
1. Cliquez sur le bouton **Supprimer la valeur par défaut**.

   ![image](/help/screens-cloud/assets/display/Assignments9.png)

1. Une boîte de dialogue de confirmation s’affiche et les détails correspondent à l’une des conditions suivantes :
   **a.** Le canal n’est utilisé dans aucun affichage.

   ![image](/help/screens-cloud/assets/display/Assignments10.png)

**b.** Le canal est utilisé dans un seul affichage.

![image](/help/screens-cloud/assets/display/Assignment11.png)

**c.** Le canal est utilisé dans plusieurs affichages.

![image](/help/screens-cloud/assets/display/Assignments12.png)

1. Cliquez sur le bouton *Supprimer* pour valider la modification.

**Remarque :** La suppression des détails d’affectation par défaut d’un canal supprime les affectations correspondantes sur tous les affichages qui l’utilisaient.
Par conséquent, cela peut donner lieu à des écrans vierges s’il n’y a pas de contenu alternatif à lire sur ces écrans.

## Et après ? {#whats-next}

Maintenant que vous avez configuré un canal AEM Screens dans votre projet, vous devez publier votre canal. Reportez-vous à [Publication de canaux dans Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/manage-publish.html?lang=fr) avant de gérer vos lecteurs à partir du fournisseur de services Screens.
