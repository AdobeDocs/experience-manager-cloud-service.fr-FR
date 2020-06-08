---
title: Réplication
description: Distribution et dépannage de la réplication.
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 4%

---


# Réplication {#replication}

Adobe Experience Manager as a Cloud Service utilise la fonctionnalité de diffusion [de contenu](https://sling.apache.org/documentation/bundles/content-distribution.html) Sling pour déplacer le contenu à répliquer vers un service de pipeline s’exécutant sur les E/S Adobe qui se trouvent en dehors de l’exécution d’AEM.

>[!NOTE]
>
> Consultez [Distribution](/help/core-concepts/architecture.md#content-distribution) pour en savoir plus.

## Méthodes de publication de contenu {#methods-of-publishing-content}

### Désactivation/publication rapide - Annulation/publication planifiée {#publish-unpublish}

Ces fonctionnalités standard d’AEM pour les auteurs ne changent pas avec le service AEM Cloud.

### Activation d’une arborescence {#tree-activation}

Pour exécuter une activation d&#39;arborescence :

1. Dans le menu Début AEM, accédez à **Outils > Déploiement > Distribution**
2. Sélectionner la carte **forwardPublisher**
3. Une fois dans l’interface utilisateur de la console Web forwardPublisher, **sélectionnez Répartir**

   ![](assets/distribute.png "DistributeDistribute")
4. Sélectionnez le chemin d’accès dans le navigateur de chemins d’accès, ajoutez un noeud, une arborescence ou supprimez-le selon les besoins, puis sélectionnez **Envoyer.**

## Résolution des incidents {#troubleshooting}

Pour résoudre les problèmes de réplication, accédez aux files d’attente de réplication dans l’interface Web du service d’auteur AEM :

1. Dans le menu Début AEM, accédez à **Outils > Déploiement > Distribution**
2. Sélectionner la carte **forwardPublisher**
   ![](assets/status.png "StatusStatus")
3. Vérifier l&#39;état de la file d&#39;attente qui doit être verte
4. Vous pouvez tester la connexion au service de réplication.
5. Sélectionnez l&#39;onglet **Journaux** qui affiche l&#39;historique des publications de contenu

![](assets/logs.png "JournauxJournaux")

Si le contenu n’a pas pu être publié, l’intégralité de la publication est restaurée à partir du service de publication AEM.
Dans ce cas, les files d&#39;attente doivent être examinées afin d&#39;identifier les éléments qui ont provoqué l&#39;annulation de la publication. En cliquant sur une file d&#39;attente présentant un état rouge, la file d&#39;attente avec des éléments en attente s&#39;affiche, à partir de laquelle un ou tous les éléments peuvent être effacés si nécessaire.
