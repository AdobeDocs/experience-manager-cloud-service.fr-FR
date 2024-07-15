---
title: Configuration du mode Chronologie pour AEM Screens
description: Cette page décrit comment configurer une vue de chronologie dans Screens as a Cloud Service.
exl-id: 53afe1f5-8f0b-4cca-a819-d3e9375cbe37
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 19%

---

# Configuration du mode Chronologie pour AEM Screens {#configuring-timelineview-screens}

## Présentation {#introduction}

Cette section décrit comment créer une vue de chronologie pour AEM Screens.

AEM fournit une suite de fonctionnalités qui permet à plusieurs personnes dans des groupes d’une organisation de collaborer à la création, à la gestion et à l’utilisation de canaux.
La chronologie, située dans la barre de gauche, décrit les canaux, l’emplacement ou le cycle de vie d’un dossier d’écran dans l’ordre du jour, en indiquant ce qui lui est arrivé au cours de sa vie. Il peut être filtré par type.
Le rail de la chronologie fournit les fonctionnalités ci-dessous en plus des journaux de cycle de vie.

![Appliquer le profil aux dossiers](/help/screens-cloud/assets/configure/Screens-timeline1.jpg)

![Appliquer le profil aux dossiers](/help/screens-cloud/assets/configure/screens-timeline2.jpg)

Pour créer une vue de chronologie pour AEM Screens, procédez comme suit :

1. Ajouter un commentaire
1. enregistrer une version ;
1. démarrer un workflow.

Les sections suivantes décrivent ces étapes en détail.

### Ajouter un commentaire {#addcomment}

Les commentaires disponibles via la chronologie permettent aux utilisateurs de créer un enregistrement centralisé et historique pour les discussions qui ont lieu sur le canal, l’emplacement ou n’importe quel dossier de l’écran.
Les commentaires offrent un moyen consolidé agréable aux utilisateurs AEM de discuter d’une manière qui peut être conservée, ce qui permet à d’autres de comprendre les décisions clés.

1. Accédez au canal pour lequel vous souhaitez ajouter un commentaire.
1. Sélectionnez le canal.
1. Ouvrez la colonne **Chronologie**.
1. Ajoutez votre commentaire et appuyez sur **Entrée**.

![Ajouter un commentaire](/help/screens-cloud/assets/configure/screen-timeline3.jpg)

Les informations de la chronologie sont mises à jour pour indiquer que le commentaire a été ajouté.

![Ajouter un commentaire](/help/screens-cloud/assets/configure/screens-timeline4.jpg)

### Enregistrer une version {#saveversion}

Le contrôle de version crée un &quot;instantané&quot; d’un canal à un moment donné. Avec le contrôle de version, vous pouvez effectuer les opérations suivantes :
* Créez une version d’un canal.
* Restaurer un canal vers une version précédente ; par exemple :
   * pour annuler une modification que vous avez apportée à la page.
* Comparez la version actuelle d’un canal à une version précédente :
   * pour mettre en évidence les différences de contenu du canal.


#### Créer une version {#createnewversion}

1. Accédez au canal pour lequel vous souhaitez ajouter un commentaire.
1. Sélectionnez le canal.
1. Ouvrez la colonne **Chronologie**.
1. Cliquez sur le bouton (trois points) situé en regard du champ de commentaire au bas de la page.

   ![Ajouter un commentaire](/help/screens-cloud/assets/configure/screens-timeline5.jpg)

1. Sélectionnez **Enregistrer comme version**.
1. Saisissez un **libellé** et un **commentaire** pour la version.

   ![Ajouter un commentaire](/help/screens-cloud/assets/configure/screens-timeline6.jpg)

1. Confirmez la nouvelle version en sélectionnant **Créer**. Les informations de la chronologie sont mises à jour pour indiquer la nouvelle version.

#### Restauration d’une version {#revertversion}

Pour rétablir la version précédente de la page sélectionnée :

1. Accédez au canal pour ajouter un commentaire.
1. Sélectionnez le canal.
1. Ouvrez la colonne **Chronologie**.
1. Sélectionnez **Tout afficher** ou **Versions** dans la liste déroulante des filtres. Les versions du canal sélectionné sont répertoriées.
1. Sélectionnez la version à restaurer. Les options possibles s’affichent :

   ![Ajouter un commentaire](/help/screens-cloud/assets/configure/screens-timeline7.jpg)

1. Sélectionnez **Revenir à cette version**. La version sélectionnée est restaurée et les informations de la chronologie mises à jour.

#### Aperçu d’une version {#previewversion}

Vous pouvez prévisualiser une version spécifique :

1. Accédez au canal pour ajouter un commentaire.
1. Sélectionnez le canal.
1. Ouvrez la colonne **Chronologie**.
1. Sélectionnez **Tout afficher** ou **Versions** dans la liste déroulante des filtres. Les versions du canal sélectionné sont répertoriées.
1. Sélectionnez la version à prévisualiser. Les options possibles s’affichent :

   ![Aperçu de la version](/help/screens-cloud/assets/configure/screens-timeline8.jpg)

1. Sélectionnez **Aperçu**. Le canal s’affiche dans un nouvel onglet.

#### Comparaison d’une version avec la version actuelle {#compareversion}

Vous pouvez comparer une version spécifique à la version actuelle :

1. Accédez au canal pour lequel vous souhaitez ajouter un commentaire.
1. Sélectionnez le canal.
1. Ouvrez la colonne **Chronologie**
1. Sélectionnez **Tout afficher** ou **Versions** dans la liste déroulante des filtres. Les versions du canal sélectionné sont répertoriées.
1. Sélectionnez la version à comparer. Les options possibles s’affichent :

   ![Comparer la version](/help/screens-cloud/assets/configure/screens-timeline9.jpg)

1. Sélectionner **Comparer avec la version actuelle**. La fenêtre contextuelle s’ouvre pour afficher les différences.

### Démarrage d’un workflow {#workflowstart}

Lors de la création, vous pouvez appeler des workflows pour agir sur vos canaux. Il est également possible d’appliquer plusieurs workflows.
Lorsque vous appliquez le workflow, vous spécifiez les informations suivantes :

* Workflow à appliquer.
* Éventuellement, un titre qui permet d’identifier l’instance de workflow dans la boîte de réception d’un utilisateur.
* Charge utile du workflow.

#### Démarrage du workflow

1. Accédez au canal pour lequel vous souhaitez ajouter un commentaire.
1. Sélectionnez le canal.
1. Ouvrez la colonne **Chronologie**.
1. Cliquez sur le bouton (trois points) en regard du champ de commentaire en bas de la page.

   ![Démarrer le workflow](/help/screens-cloud/assets/configure/screens-timeline10.jpg)

1. Sélectionnez **Démarrer le workflow**.
1. L’assistant Créer un workflow s’ouvre pour spécifier les détails du workflow.
1. Sélectionnez **Modèle de workflow** dans la liste déroulante et saisissez le titre du workflow.

   ![Démarrer le workflow](/help/screens-cloud/assets/configure/screens-timeline11.jpg)

1. Poursuivez en cliquant sur **Suivant**.
1. À l’étape de la portée, vous pouvez :
   * **Ajouter du contenu** pour ajouter des ressources supplémentaires au workflow.
   * **Inclure les enfants** pour indiquer que les enfants de cette ressource seront inclus dans le workflow.
   * **Supprimer la sélection** pour supprimer cette ressource du workflow.

   ![Démarrer le workflow](/help/screens-cloud/assets/configure/screens-timeline12.jpg)

1. Sélectionnez **Créer** pour fermer l’assistant et créer l’instance de workflow.
1. Vous devrez peut-être effectuer certaines actions supplémentaires pour terminer le workflow en fonction du modèle de workflow sélectionné.

   ![Démarrer le workflow](/help/screens-cloud/assets/configure/screens-timeline13.jpg)
