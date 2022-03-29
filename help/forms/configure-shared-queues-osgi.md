---
title: Configurer les files d’attente partagées
seo-title: Configure shared queues
description: Découvrez comment utiliser les files d’attente partagées pour les processus orientés formulaire dans [!DNL AEM Forms]  on OSGi.
seo-description: Learn how to use shared queues for Forms-centric workflows on [!DNL AEM Forms] on OSGi.
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 100%

---


# Partager et demander l’accès aux éléments de la boîte de réception d’un utilisateur {#share-and-request-access}

Une file d’attente est une liste d’éléments dans une boîte de réception AEM d’un utilisateur. Il peut s’agir d’éléments affectés à un utilisateur ou d’éléments partagés avec le groupe auquel un utilisateur appartient. Vous pouvez accéder à votre boîte de réception pour afficher un l’élément et exécuter une action dessus, par exemple le partager avec un autre utilisateur.

Vous pouvez également partager vos éléments de boîte de réception avec un autre utilisateur. Une fois qu’un autre utilisateur a accès à vos éléments de boîte de réception, il peut demander des éléments partagés et exécuter des actions dessus. De même, vous pouvez demander l’accès aux éléments de boîte de réception à d’autres utilisateurs.

## Conditions préalables {#pre-requisites}

L’utilisateur connecté doit être membre du groupe [!DNL `workflow-users`]. Il peut partager des éléments ou demander l’accès aux éléments uniquement des utilisateurs sur lesquels il dispose d’autorisations en lecture ou uniquement des utilisateurs ayant activé le profil public.

## Partage d’un ou de tous les éléments de votre boîte de réception avec un autre utilisateur

La boîte de réception AEM vous permet de partager un ou tous les éléments avec un autre utilisateur.

### Partage de tous les éléments de la boîte de réception

Pour partager tous les éléments d’une boîte de réception avec un autre utilisateur, procédez comme suit :

1. Connectez-vous à l’instance AEM. Appuyez sur l’icône ![Boîte de réception](assets/bell.svg) et appuyez sur **[!UICONTROL Afficher tout]**. La liste des éléments de votre boîte de réception s’affiche.
1. Appuyez sur l’icône ![Sélecteur de Vue](assets/viewlist.svg) ou ![Sélecteur de Vue](assets/calendar.svg) à côté du bouton **[!UICONTROL Créer]** et appuyez sur **[!UICONTROL Paramètres]**. La boîte de dialogue des paramètres apparaît.
1. Ouvrez l’onglet **[!UICONTROL Partager]** dans la boîte de dialogue des paramètres.
1. Entrez le nom d’un utilisateur dans la zone de texte **[!UICONTROL Accorder l’accès à vos éléments de boîte de réception]** et appuyez sur **[!UICONTROL Accorder]**. Répétez l’étape pour ajouter d’autres utilisateurs. Tous les utilisateurs ayant accès à vos éléments apparaissent sous la section **Nom d’utilisateur**.
1. Appuyez sur **[!UICONTROL Enregistrer]**.

>[!NOTE]
>
>(Pour les éléments de processus orienté formulaire uniquement) Activez l’option **[Autoriser les personnes désignées à partager via la boîte de réception](aem-forms-workflow-step-reference.md)** de l’étape **Affecter une tâche** dans le processus. Seuls les éléments pour lesquels cette option est activée s’affichent pour les autres utilisateurs.

### Partage d’éléments individuels

Pour partager un élément de boîte de réception avec un autre utilisateur, procédez comme suit :

1. Connectez-vous à l’instance AEM. Appuyez sur l’icône ![Boîte de réception](assets/bell.svg) et appuyez sur **[!UICONTROL Afficher tout]**. La liste des éléments de votre boîte de réception s’affiche.
1. Sélectionnez un élément et appuyez sur **[!UICONTROL Partager]**. Une boîte de dialogue s’affiche.
1. Saisissez le nom d’un utilisateur dans la zone de texte Ajouter les utilisateurs pour partager cet élément et appuyez sur **[!UICONTROL Ajouter]**. Répétez l’étape pour ajouter d’autres utilisateurs. Tous les utilisateurs ayant accès à vos éléments apparaissent sous la section **[!UICONTROL Nom d’utilisateur]**.
1. Appuyez sur **[!UICONTROL Enregistrer]**.


>[!NOTE]
>
>(Pour les éléments de processus orienté formulaire uniquement) Activez l’option **[Autoriser les personnes désignées à partager explicitement dans la boîte de réception](aem-forms-workflow-step-reference.md)** de l’étape **Affecter une tâche** dans le processus. Seuls les éléments pour lesquels cette option est activée s’affichent pour les autres utilisateurs.

## Demander l’accès aux éléments de la boîte de réception {#request-access}

Vous pouvez demander l’accès aux éléments de la boîte de réception d’un autre utilisateur. Une fois l’accès accordé, vous pouvez afficher, demander et exécuter des actions appropriées sur les éléments partagés. Pour demander l’accès aux éléments de la boîte de réception d’un autre utilisateur, procédez comme suit :

1. Connectez-vous à l’instance AEM. Appuyez sur l’icône ![Sélecteur de vue](assets/bell.svg), puis sur **[!UICONTROL Afficher tout]**.
1. Appuyez sur l’icône ![Sélecteur de vue](assets/viewlist.svg) ou ![Sélecteur de vue](assets/calendar.svg) en regard du bouton **[!UICONTROL Créer]**, puis sur **[!UICONTROL Paramètres]**. La boîte de dialogue des paramètres apparaît.
1. Saisissez le nom d’un utilisateur dans la zone de texte **[!UICONTROL Demander l’accès aux éléments de la boîte de réception de l’utilisateur]** et appuyez sur **[!UICONTROL Demander]**. Une demande est envoyée à l’utilisateur et le statut de la demande est affiché à côté du nom de l’utilisateur. Répétez l’étape pour ajouter d’autres utilisateurs.
1. Appuyez sur **[!UICONTROL Enregistrer]**. La demande est envoyée en tant qu’élément de boîte de réception aux utilisateurs. L’utilisateur peut sélectionner l’élément et appuyer sur Approuver ou Rejeter pour accorder ou refuser l’accès.


## Demander les éléments partagés par d’autres utilisateurs {#claim-items}

Vous ne pouvez commencer à travailler sur un élément partagé qu’après l’avoir demandé. Cela empêche plusieurs utilisateurs de travailler sur un seul et même élément. Pour demander un élément, procédez comme suit :

1. Connectez-vous à l’instance AEM. Appuyez sur l’icône Boîte de réception ![Boîte de réception](assets/bell.svg), puis sur **[!UICONTROL Afficher tout]**.
1. Appuyez sur l’icône ![Contenu uniquement](assets/railleft.svg) pour ouvrir le sélecteur de filtres.
1. Appuyez sur la liste déroulante **[!UICONTROL Sélectionner le destinataire]** pour afficher et sélectionner les utilisateurs ayant partagé les éléments de leur boîte de réception avec vous.
1. Sélectionnez un élément et appuyez sur **[!UICONTROL Demander]**. L’élément est ajouté à votre boîte de réception.

## Libérer les éléments demandés {#release-items}

Vous ne pouvez travailler sur un élément partagé qu’après l’avoir demandé. Les autres utilisateurs ne peuvent pas afficher ni travailler sur un élément que vous avez demandé. Si vous ne pouvez pas continuer à travailler sur un élément, vous pouvez le remettre dans le pool.   Une fois l’élément libéré, d’autres utilisateurs peuvent le demander et travailler dessus :

Pour libérer un élément, procédez comme suit :

1. Connectez-vous à l’instance AEM. Appuyez sur l’icône Boîte de réception ![Boîte de réception](assets/bell.svg), puis sur **[!UICONTROL Afficher tout]**. La liste des éléments de votre boîte de réception s’affiche.
1. Sélectionnez l’élément à libérer et appuyez sur **[!UICONTROL Annuler la demande]**. L’élément est de nouveau ajouté au pool. D’autres personnes peuvent maintenant le demander.

## Limites {#limitations}

* Le partage d’éléments avec un groupe n’est pas pris en charge.
* Le partage de tâches de projet n’est pas pris en charge.
