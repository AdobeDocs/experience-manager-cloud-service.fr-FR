---
title: Ajout d’un site Edge Delivery à Cloud Manager
description: Découvrez comment ajouter un site Edge Delivery à votre programme de production ou à votre programme sandbox.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 3%

---


## Ajout d’un site Edge Delivery à Cloud Manager {#eds-add-site}

Une fois que vous avez ajouté des Edge Delivery Services à un programme de production, votre licence Edge Delivery Services lui est appliquée.

Un onglet cliquable appelé **Edge Delivery** s’affiche sur la page Aperçu. Cliquez sur l’onglet pour afficher un tableau répertoriant chaque site Edge Delivery que vous avez ajouté. Dans le panneau de navigation de gauche, sous le regroupement **Services**, remarquez l’option de menu nommée **Edge Delivery Sites**.

![Page d’aperçu présentant Edge Delivery Sites dans le panneau de navigation de gauche et l’onglet Edge Delivery à droite de l’onglet Diffusion Publish](/help/implementing/cloud-manager/assets/cm-overview-eds.png)

**Pour ajouter un site Edge Delivery à Cloud Manager :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme avec les Edge Delivery Services configurés, où vous souhaitez ajouter un site Edge Delivery.
1. Effectuez l’une des opérations suivantes :
   * Sur la page **Aperçu du programme**, cliquez sur l’onglet **Edge Delivery**. Ensuite, près du coin inférieur droit de la page, cliquez sur **Ajouter un site Edge Delivery**.

     ![Ajouter un site Edge Delivery depuis l’onglet Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

     La **liste de tâches d’Edge Delivery**, comme illustré dans l’image ci-dessus, est un guide de liste de contrôle d’intégration facultatif destiné à vous aider à commencer à utiliser Edge Delivery. Voir [À propos de la liste de tâches Edge Delivery](#ed-todo-list).

   * Dans le coin supérieur gauche de la page, cliquez sur l’icône représentant un hamburger pour afficher le menu de navigation de gauche. Sous l’en-tête **Services**, cliquez sur **Edge Delivery Sites**. Dans le coin supérieur droit de la page, cliquez sur **Ajouter un site**.

     ![Ajouter un site Edge Delivery à partir du bouton Edge Delivery Sites](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. Dans la boîte de dialogue **Ajouter un site Edge Delivery** , procédez comme suit :

   | Champ de texte | Que faire |
   | --- | --- |
   | Nom du site | Saisissez le nom du site Edge Delivery que vous ajoutez. Le nom sert d’identifiant unique au site dans Cloud Manager. |
   | URL du référentiel | Ce champ fait référence au référentiel Git où est stocké le code de votre site web.<br>Entrez l’URL du référentiel Git qui contient les fichiers et ressources nécessaires (tels que HTML, CSS, JavaScript et autres ressources web) pour votre site Edge Delivery. Cette disposition permet à Cloud Manager d’extraire le code de ce référentiel pendant le processus de déploiement. |
   | Description du site (facultative) | Entrez une brève description du site Edge Delivery que vous ajoutez.<br>Cette description permet d’identifier et de différencier le site, ce qui facilite la gestion et la reconnaissance des autres sites que vous avez ajoutés. Vous pouvez inclure des détails sur l’objectif, le contenu ou toute autre information pertinente du site qui peut aider à clarifier sa fonction ou sa portée. |

1. Dans le coin inférieur droit de la boîte de dialogue, cliquez sur **Ajouter**.

1. Dans la boîte de dialogue **Vérifier la propriété du référentiel**, effectuez chacune des opérations suivantes :

   | Étape | Description |
   | --- | --- |
   | 1 | Ajoutez un fichier avec le chemin d’accès à l’emplacement de la branche `main` du référentiel Git répertorié dans le champ **Repository URL** . Si nécessaire, cliquez sur l’icône Copier pour copier le chemin dans le Presse-papiers.<br> Le chemin d’accès à l’emplacement est :<br>`well-known/adobe/cloudmanager-challenge.txt`.<br><br>N&#39;ajoutez *pas* une période au début du chemin de l&#39;emplacement, se trouve dans :<br>`.well-known/adobe/cloudmanager-challenge.txt` |
   | 2 | Ajoutez le code généré au fichier que vous avez créé à l’étape 1. Si nécessaire, cliquez sur l’icône Copier pour copier le code dans le Presse-papiers. |
   | 3 | Dans le référentiel Git, créez une requête de tirage, puis fusionnez-la pour valider le code. |

1. Cliquez sur **Vérifier**. Une fois le référentiel vérifié, son état dans le tableau Edge Deliver Sites passe à un cercle vert avec une coche blanche à l’intérieur.
