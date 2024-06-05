---
title: Annulation et rétablissement des limites
description: Découvrez les limites des options d’annulation et de rétablissement dans l’éditeur de page d’AEM.
exl-id: 87773f47-5116-4966-9ba4-5deedb7c4fa6
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 92%

---

# Annulation et rétablissement des limites {#undo-redo}

AEM stocke un historique des actions que vous réalisez, ainsi que la séquence selon laquelle vous les réalisez, de sorte que vous puissiez annuler plusieurs actions dans l’ordre dans lequel vous les avez réalisées. Vous pouvez également les rétablir pour appliquer à nouveau une ou plusieurs de ces actions.

Si un élément de la page de contenu est sélectionné (un composant de texte, par exemple), les commandes Annuler et Rétablir s’appliquent à celui-ci.

Le comportement des commandes Annuler et Rétablir est similaire à celui des autres logiciels. Utilisez ces commandes pour restaurer l’état récent de votre page web lorsque vous prenez des décisions sur le contenu. Par exemple, si vous repositionnez un paragraphe de texte sur la page, vous pouvez utiliser la commande Annuler pour le remettre à son emplacement initial. Si vous décidez alors que la position précédente était meilleure, utilisez la commande Rétablir pour « annuler l’annulation ».

Par exemple, vous pouvez effectuer les actions suivantes :

* Rétablir les actions tant que vous n’avez pas effectué de modification de page depuis que vous avez utilisé l’option Annuler.
* Annuler un maximum de 20 actions de modification (paramètre par défaut).
* Utilisez également les [raccourcis clavier](/help/sites-cloud/authoring/sites-console/keyboard-shortcuts.md) pour annuler et rétablir.

Vous pouvez utiliser les options Annuler et Rétablir pour les types de modifications de page suivants :

* Ajout, modification, suppression et déplacement de paragraphes
* Modification sur place du contenu des paragraphes
* Copie, découpe et collage d’éléments dans une page

>[!NOTE]
>
>* Des autorisations spéciales sont nécessaires pour annuler et rétablir des modifications affectant des fichiers et des images.
>* L’historique des modifications apportées aux fichiers et aux images dure au moins dix heures. Au-delà de cette période, l’annulation des modifications n’est toutefois pas garantie. Votre administrateur ou administratrice peut modifier la durée par défaut de dix heures.
>* L’administrateur système peut configurer divers aspects des fonctions Annuler/Rétablir en fonction des exigences de votre instance.
