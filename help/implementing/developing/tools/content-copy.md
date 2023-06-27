---
title: Outil de copie de contenu
description: L’outil de copie de contenu permet aux utilisateurs de copier du contenu modifiable à la demande à partir de leurs environnements de production sur AEM as a Cloud Service à des environnements inférieurs à des fins de test.
exl-id: f060821d-d559-45d2-b3b1-1b2277694ec4
source-git-commit: f08048b2378b150210a3fd1168206f4efb0c4f8e
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 40%

---

# Outil de copie de contenu {#content-copy}

L’outil de copie de contenu permet aux utilisateurs de copier du contenu modifiable à la demande à partir de leurs environnements de production sur AEM as a Cloud Service à des environnements inférieurs à des fins de test.

## Présentation {#introduction}

Les données actuelles et réelles sont utiles à des fins de test, de validation et d’acceptation par l’utilisateur. L’outil de copie de contenu vous permet de copier du contenu d’un environnement de production AEM as a Cloud Service vers un environnement d’évaluation, de développement ou [Environnement de développement rapide (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) environnement pour de tels tests.

Le contenu à copier est défini par un jeu de contenu. Un jeu de contenu est constitué d’une liste de chemins JCR qui contiennent le contenu modifiable à copier d’un environnement de service de création de source vers un environnement de service de création cible dans le même programme Cloud Manager. Les chemins d’accès suivants sont autorisés dans un jeu de contenu.

```text
/content
/conf/**/settings/wcm
/conf/**/settings/dam/cfm/models
/conf/**/settings/graphql/persistentQueries
/etc/clientlibs/fd/themes
```

Lors de la copie de contenu, l’environnement source est la source de vérité.

* Si le contenu a été modifié dans l’environnement de destination, il est remplacé par le contenu de la source, si les chemins d’accès sont identiques.
* Si les chemins d’accès sont différents, le contenu de la source est fusionné avec le contenu de la destination.

## Autorisations {#permissions}

Pour utiliser l’outil de copie de contenu, certaines autorisations sont requises dans les environnements source et cible.

| Fonctionnalité copie de contenu | Groupe d’administrateurs AEM | Rôle de responsable de déploiement |
|---|---|---|
| Créer et modifier des [jeux de contenu](#create-content-set) | Requis | Non requis |
| Démarrer ou annuler le [processus de copie de contenu](#copy-content) | Requis | Requis |

## Créer un jeu de contenu {#create-content-set}

Pour qu’un contenu puisse être copié, un jeu de contenu doit être défini. Une fois défini, les jeux de contenu peuvent être réutilisés pour copier le contenu. Suivez ces étapes pour créer un jeu de contenu.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez à la page **Jeux de contenu** à partir de l’écran **Environnements**.

1. Dans le coin supérieur droit de l’écran, cliquez sur **Ajouter un jeu de contenu**.

   ![Jeux de contenu](assets/content-sets.png)

1. Dans l’onglet **Détails** de l’assistant, indiquez le nom et la description du jeu de contenu, puis appuyez ou cliquez sur **Continuer**.

   ![Détails du jeu de contenu](assets/add-content-set-details.png)

1. Dans l’onglet **Chemins d’accès au contenu** de l’assistant, indiquez les chemins d’accès au contenu modifiable à inclure dans le jeu de contenu.

   1. Entrez le chemin dans le champ **Ajouter un chemin d’accès à inclure**.
   1. Cliquez sur **Ajouter un chemin** pour ajouter le chemin d’accès au jeu de contenu.
   1. Cliquez sur **Ajouter un chemin** au besoin.
      * Jusqu’à 50 chemins sont autorisés.

   ![Ajouter des chemins à un jeu de contenu](assets/add-content-set-paths.png)

1. Si vous devez affiner ou restreindre votre jeu de contenu, les sous-chemins peuvent être exclus.

   1. Dans la liste des chemins inclus, cliquez sur **Ajouter des sous-chemins d’exclusion** en regard du chemin que vous souhaitez restreindre.
   1. Entrez le sous-chemin d’accès à exclure sous le chemin d’accès sélectionné.
   1. Appuyez ou cliquez sur **Exclure le chemin**.
   1. Appuyez ou cliquez encore sur **Ajouter des sous-chemins à exclure** pour ajouter d’autres chemins à exclure si nécessaire.
      * Les chemins exclus doivent être relatifs au chemin inclus.
      * Le nombre de chemins exclus n’est pas limité.

   ![Exclusion de chemins](assets/add-content-set-paths-excluded.png)

1. Si nécessaire, vous pouvez modifier les chemins spécifiés.

   1. Cliquez sur le X en regard des sous-chemins exclus pour pouvoir les supprimer.
   1. Cliquez sur le bouton représentant des points de suspension en regard des chemins pour afficher la variable **Modifier** et **Supprimer** options.

   ![Modification de la liste de chemins](assets/add-content-set-excluded-paths.png)

1. Appuyez ou cliquez sur **Créer** pour créer le jeu de contenu.

Le jeu de contenu peut désormais être utilisé pour copier du contenu entre des environnements.

## Modification d’un jeu de contenu {#edit-content-set}

Procédez de la même façon que lors de la création d’une étape de contenu. Au lieu de cliquer sur **Ajouter un jeu de contenu**, sélectionnez un jeu existant dans la console, puis **Modifier** dans le menu points de suspension.

![Modifier le jeu de contenu](assets/edit-content-set.png)

Lors de la modification de votre jeu de contenu, vous pouvez développer les chemins configurés pour afficher les sous-chemins exclus.

## Copie de contenu {#copy-content}

Une fois un jeu de contenu créé, vous pouvez l’utiliser pour copier du contenu. Procédez comme suit pour copier du contenu.

>[!NOTE]
> N’utilisez pas la copie de contenu dans un environnement lorsqu’un [transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md) s’exécute dans cet environnement.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez à la page **Jeux de contenu** à partir de l’écran **Environnements**.

1. Sélectionnez un jeu de contenu dans la console, puis **Copier le contenu** dans le menu représentant des points de suspension.

   ![Copier le contenu](assets/copy-content.png)

   >[!NOTE]
   >
   >Un environnement ne peut pas être sélectionné si :
   >
   >* L’utilisateur ne dispose pas des autorisations appropriées.
   >* Un pipeline en cours d’exécution ou une opération de copie de contenu est en cours dans l’environnement.
   >* L’environnement est en veille ou en train de se développer.

1. Dans la boîte de dialogue **Copier le contenu**, spécifiez la source et la destination de votre action de copie de contenu.

   ![Copie de contenu](assets/copying-content.png)

   * Le contenu ne peut être copié que d’un environnement supérieur vers un environnement inférieur ou entre des environnements de développement/RDE où la hiérarchie des environnements est la suivante (du plus haut au plus bas) :
      * Production
      * Évaluation
      * Développement/RDE

1. Si nécessaire, vous pouvez également choisir de **Inclure les listes de contrôle d’accès** dans votre processus de copie.

1. Appuyez ou cliquez sur **Copier**.

Le processus de copie démarre. Le statut du processus de copie est répercuté dans la console pour le jeu de contenu sélectionné.

## Activité de copie de contenu {#copy-activity}

Vous pouvez surveiller le statut de vos processus de copie à la page **Activité de copie de contenu**.

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation et le programme appropriés.

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Accédez à la page **Activité de copie de contenu** à partir de l’écran **Environnements**.

![Activité de copie de contenu](assets/copy-content-activity.png)

### Statuts de la copie de contenu {#statuses}

Une fois que vous avez commencé à copier du contenu, le processus peut avoir l’un des statuts suivants.

| État | Description |
|---|---|
| En cours | L’opération de copie de contenu est en cours. |
| Échec | L’opération de copie de contenu a échoué. |
| Terminé | L’opération de copie de contenu est terminée avec succès. |
| Annulé | L’utilisateur annule une opération de copie de contenu après l’avoir démarrée |

### Annulation d’un processus de copie {#canceling}

Si vous devez abandonner une opération de copie de contenu après son démarrage, vous pouvez éventuellement l’annuler.

Pour ce faire, sur la page **Copie de l’activité de contenu** , sélectionnez **Annuler** à partir du menu représentant des points de suspension du processus de copie que vous avez démarré précédemment.

![Annuler la copie de contenu](assets/content-copy-cancel.png)

>[!NOTE]
>
>Lorsque vous annulez une opération de copie de contenu, une copie partielle du contenu peut s’afficher dans l’environnement de destination. Cette situation peut rendre l’environnement de destination inutilisable.
>
>Si votre environnement se trouve dans un tel état en raison d’une annulation, contactez l’assistance clientèle Adobe pour obtenir de l’aide.

## Limites {#limitations}

L’outil de copie de contenu présente les limites suivantes.

* Le contenu ne peut pas être copié d’un environnement inférieur vers un environnement supérieur.
* Le contenu ne peut être copié que depuis et vers les services de création.
* Une copie de contenu ne peut pas être effectuée sur plusieurs programmes.
* L’exécution simultanée d’opérations de copie de contenu sur le même environnement n’est pas possible.
* Vous pouvez spécifier jusqu’à 50 chemins par jeu de contenu. Il n’existe aucune limitation sur les chemins exclus.
* L’outil de copie de contenu ne doit pas être utilisé comme outil de clonage ou de mise en miroir, car il ne peut pas effectuer le suivi du contenu déplacé ou supprimé sur la source.
* L’outil de copie de contenu ne dispose d’aucune fonctionnalité de contrôle de version et ne peut pas détecter automatiquement le contenu modifié ou le contenu nouvellement créé dans l’environnement source dans un jeu de contenu depuis la dernière opération de copie de contenu.
   * Si vous souhaitez uniquement mettre à jour votre environnement de destination avec les modifications de contenu, depuis la dernière opération de copie de contenu, vous devez créer un jeu de contenu. Indiquez ensuite les chemins d’accès sur l’instance source où des modifications ont été apportées depuis la dernière opération de copie de contenu.
* Les informations de version ne sont pas incluses dans une copie de contenu.
