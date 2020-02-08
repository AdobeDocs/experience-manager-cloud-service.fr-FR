---
title: Réplication
description: Répartition et dépannage de la réplication.
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e

---


# Réplication {#replication}

Adobe Experience Manager as a Cloud Service utilise la fonctionnalité de distribution [de contenu](https://sling.apache.org/documentation/bundles/content-distribution.html) Sling pour déplacer le contenu à répliquer vers un service de pipeline exécuté sur des E/S Adobe en dehors du runtime AEM.

>[!NOTE]
>
> Consultez [Distribution](/help/core-concepts/architecture.md#content-distribution) pour en savoir plus.

## Méthodes de publication de contenu {#methods-of-publishing-content}

### Annulation/Publication rapide - Annulation/Publication planifiée {#publish-unpublish}

Ces fonctionnalités AEM standard pour les auteurs ne changent pas avec le service AEM Cloud.

### Activation d’une arborescence {#tree-activation}

Pour activer une arborescence :

1. Dans le menu Démarrer d’AEM, accédez à **Outils > Déploiement > Distribution.**
2. Sélectionner la carte **forwardPublisher**
3. Une fois dans l’interface utilisateur de la console Web de l’Editeur avancé, **sélectionnez Répartir.**
   ![](assets/distribute.png "RépartirRépartir")
4. Sélectionnez le chemin d’accès dans le navigateur de chemins d’accès, ajoutez un noeud, une arborescence ou supprimez-le selon les besoins, puis sélectionnez **Envoyer.**

## Résolution des incidents {#troubleshooting}

Pour résoudre les problèmes de réplication, accédez aux files d’attente de réplication dans l’interface Web du service d’auteur AEM :

1. Dans le menu Démarrer d’AEM, accédez à **Outils > Déploiement > Distribution.**
2. Sélectionner la carte **forwardPublisher**
   ![](assets/status.png "StatusStatus")
3. Vérifiez l’état de la file d’attente qui doit être vert.
4. Vous pouvez tester la connexion au service de réplication
5. Sélectionnez l&#39;onglet **Journaux** qui affiche l&#39;historique des publications de contenu

![Journaux](assets/logs.png "journaux")

Si le contenu n’a pas pu être publié, l’intégralité de la publication est annulée à partir du service de publication AEM.
Dans ce cas, les files d&#39;attente doivent être examinées afin d&#39;identifier les éléments qui ont provoqué l&#39;annulation de la publication. En cliquant sur une file d&#39;attente avec un état rouge, la file d&#39;attente avec des éléments en attente s&#39;affiche, à partir de laquelle un seul ou tous les éléments peuvent être effacés si nécessaire.
