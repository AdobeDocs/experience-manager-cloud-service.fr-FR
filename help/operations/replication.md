---
title: Réplication
description: Distribution et dépannage de la réplication.
translation-type: tm+mt
source-git-commit: abb45225e880f3d08b9d26c29e243037564acef0
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 100%

---


# Réplication {#replication}

Adobe Experience Manager as a Cloud Service utilise la fonctionnalité de [distribution de contenu Sling](https://sling.apache.org/documentation/bundles/content-distribution.html) pour déplacer le contenu à répliquer vers un service de pipeline s’exécutant sur Adobe I/O, en dehors d’AEM.

>[!NOTE]
>
>Pour en savoir plus, consultez [Distribution](/help/core-concepts/architecture.md#content-distribution).

## Méthodes de publication de contenu {#methods-of-publishing-content}

### Publication/annulation de publication rapide – Publication/annulation de publication planifiée {#publish-unpublish}

Ces fonctionnalités standard d’AEM pour les auteurs sont inchangées avec AEM Cloud Service.

### Heures d’activation et de désactivation – Configuration du déclenchement {#on-and-off-times-trigger-configuration}

Les autres possibilités d’**Heure d’activation** et d’**Heure de désactivation** sont disponibles dans l’[onglet De base des Propriétés de la page](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic).

Pour réaliser la réplication automatique dans ce cas, vous devez activer **Auto Replicate** (Réplication automatique) dans **On Off Trigger Configuration** (Configuration d’activation et de désactivation du déclenchement) de la [configuration OSGi](/help/implementing/deploying/configuring-osgi.md) :

![Configuration OSGi d’activation et de désactivation du déclenchement](/help/operations/assets/replication-on-off-trigger.png)

### Activation d’une arborescence {#tree-activation}

Pour exécuter une activation d’arborescence :

1. Dans le menu Accueil AEM, accédez à **Outils > Déploiement > Distribution**.
2. Sélectionnez la carte **forwardPublisher**.
3. Une fois dans l’interface utilisateur de la console web forwardPublisher, sélectionnez **Distribute** (Distribuer).

   ![Distribuer](assets/distribute.png "Distribuer")
4. Sélectionnez le chemin dans l’explorateur de chemins d’accès, choisissez d’ajouter un nœud, une arborescence ou supprimez-les, si nécessaire, puis sélectionnez **Submit** (Envoyer).

## Dépannage {#troubleshooting}

Pour résoudre les problèmes de réplication, accédez aux files d’attente de réplication dans l’interface utilisateur web du service d’auteur AEM :

1. Dans le menu Accueil AEM, accédez à **Outils > Déploiement > Distribution**.
2. Sélectionnez la carte **forwardPublisher**.
   ![État](assets/status.png "État")
3. Vérifiez l’état de la file d’attente qui doit être de couleur verte.
4. Vous pouvez tester la connexion au service de réplication.
5. Sélectionnez l’onglet **Logs** (Journaux) qui affiche l’historique des publications de contenu.

![Journaux](assets/logs.png "Journaux")

S’il n’a pas été possible de publier le contenu, l’intégralité de la publication est restaurée à partir du service de publication AEM.
Dans ce cas, les files d’attente doivent être examinées afin d’identifier les éléments qui ont provoqué l’annulation de la publication. Suite à un clic sur une file d’attente signalée par un état rouge, celle contenant des éléments en attente s’affiche. Il est possible d’y effacer un ou tous les éléments, si nécessaire.
