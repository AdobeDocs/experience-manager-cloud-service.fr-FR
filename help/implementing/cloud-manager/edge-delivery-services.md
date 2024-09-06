---
title: Assistance Edge Delivery Services dans Cloud Manager
description: Découvrez comment diffuser vos projets Cloud Manager à l’aide de Edge Delivery Services.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4e887b753eaf09e104c68484792f00dcb08ee304
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 6%

---

# Assistance Edge Delivery Services dans Cloud Manager {#edge-delivery-services}

Découvrez comment utiliser votre licence Edge Delivery Services pour créer un site Edge Delivery Services.

<!-- RELEASED TO GA SEPTEMBER 5, 2024
>[!NOTE]
>
>This feature is only available to [the early adopter program](/help/implementing/cloud-manager/release-notes/current.md#early-adoption). -->

## Edge Delivery Services en bref {#edge-overview}

Edge Delivery Services est un ensemble de services composable qui offre une grande flexibilité quant à la manière dont vous créez du contenu sur votre site web. Cette fonctionnalité vous permet d’effectuer les opérations suivantes :

* Créez des sites rapides avec un score Lighthouse parfait.
* Surveillez continuellement les performances grâce à la fonction RUM (surveillance de l’utilisation réelle).
* Augmentez l’efficacité de la création en découplant les sources de contenu.

Vous pouvez utiliser AEM gestion de contenu et la création WYSIWYG à l’aide de l’éditeur universel et de la création basée sur des documents.

Cloud Manager dans AEM as a Cloud Service vous permet d’activer le service Edge Delivery pour votre projet.

>[!TIP]
>
>Pour plus d’informations sur les Edge Delivery Services et leur utilisation avec AEM, consultez le document [Présentation des Edge Delivery Services](/help/edge/overview.md).

## Edge Delivery Services dans Cloud Manager {#edge-in-cloud-manager}

Si vous possédez des Edge Delivery Services sous licence dans Adobe Experience Manager Sites, vous pouvez embarquer sur votre site avec des Edge Delivery Services directement dans Cloud Manager et passer en ligne [ à l’aide d’une expérience guidée en libre-service](/help/implementing/cloud-manager/managing-code/private-repositories.md).

De plus, vous pouvez accéder à une expérience unifiée pour gérer toutes vos propriétés AEM tout en assurant la cohérence entre les workflows clés. Il s’agit notamment de la gestion des noms de domaine, de la gestion des certificats SSL et des mappages CDN.

## Ajout de Edge Delivery Services à un programme de production ou d’environnement de test

Pour ajouter ou modifier des programmes, vous devez être membre du rôle **Propriétaire de l’entreprise** ou être autorisé à le faire.
Votre entreprise doit disposer d’une licence de Edge Delivery Services inutilisée pour pouvoir l’appliquer à un programme de production.

>[!NOTE]
>
>Une fois la licence Edge Delivery Services appliquée ou supprimée d’un programme, la modification prend effet immédiatement sans qu’il soit nécessaire d’exécuter un pipeline. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

Selon votre cas d’utilisation, effectuez l’une des opérations suivantes :

| Cas d’utilisation | Description |
| --- | --- |
| Je veux ajouter des Edge Delivery Services à un nouveau programme de production. | Voir [Création de programmes de production](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).<br>Dans l’assistant, sous l’onglet **Solutions &amp; Add-ons**, sélectionnez **Edge Delivery Services**. |
| Je veux ajouter des Edge Delivery Services à un programme de production existant. | Voir [Modification de programmes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md).<br>Dans la boîte de dialogue **Modifier le programme**, sous l’onglet **Solutions &amp; Add-ons**, sélectionnez **Edge Delivery Services**. |
| Je souhaite ajouter des Edge Delivery Services à un nouveau programme sandbox ou à un programme sandbox existant. | Voir [Création de programmes Sandbox](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).<br>Lorsque vous créez un programme sandbox, des Edge Delivery Services sont ajoutés au programme par défaut ; vous n’avez pas besoin de le sélectionner.<br>Les programmes Sandbox existants héritent automatiquement des Edge Delivery Services. |

## Chemin d’accès recommandé pour les clients sous contrat {#recommended-path-eds}

En tant que client sous contrat, assurez-vous de tirer le meilleur parti de l’Adobe en accédant à et en utilisant votre licence Edge Delivery Services via Cloud Manager. Cette approche vous permet d’utiliser [Adobe managed CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) et de tirer parti des avantages clés tels que la gestion de CDN en libre-service, y compris la configuration et l’installation de certificats DV ou EV/OV. Si vous ne disposez pas d’une licence Edge Delivery Services avec Adobe et que vous décidez de contourner ces avantages, vous ne pouvez utiliser qu’un réseau de diffusion de contenu géré par le client. Cette configuration doit se trouver sur la plateforme aem.live .

Si vous êtes contractuel avec des licences de Edge Delivery Services AEM as a Cloud Service Sites, connectez-vous à Cloud Manager pour vous assurer que vous pouvez effectuer les opérations suivantes :

* Utilisez votre licence sur le programme de votre choix.
* Profitez des avantages [API-first](https://developer.adobe.com/experience-cloud/experience-manager-apis/) pour effectuer des opérations CRUD (créer, lire, mettre à jour, supprimer).
<!-- REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+Self-service+access+to+Edge+Delivery+Services+and+Adobe+Managed+CDN * Access to license dashboard and reporting -->
* Accéder aux rapports SLA (*bientôt disponible*) <!-- ADD LINK TO IT WHEN FINALLY ADDED -->
* Obtenez le soutien des Adobes. Assurez-vous que vos sites Edge Delivery Services sont enregistrés par le biais d’un programme de production dans Cloud Manager pour une reconnaissance et une prise en charge appropriées de la part de l’Adobe.

## Ajout d’un site de Edge Delivery Services {#eds-add-site}

Une fois que vous avez ajouté des Edge Delivery Services à un programme de production, votre licence Edge Delivery Services lui est appliquée.

Un nouvel onglet cliquable appelé **Edge Delivery** s’affiche sur la page Aperçu. Cliquez sur l’onglet pour afficher un tableau répertoriant chaque site Edge Delivery que vous avez ajouté. Dans le panneau de navigation de gauche, sous le regroupement **Services**, vous remarquerez une option de menu nommée **Edge Delivery Sites**.

![Page d’aperçu présentant Edge Delivery Sites dans le panneau de navigation de gauche et l’onglet Edge Delivery à droite de l’onglet Diffusion Publish](/help/implementing/cloud-manager/assets/cm-overview-eds.png)

**Pour ajouter un site Edge Delivery :**

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

## À propos de la liste de tâches d’Edge Delivery {#ed-todo-list}

La **liste de tâches d’Edge Delivery** est une liste de contrôle de tâches d’intégration destinée à vous guider tout au long de l’intégration et de la gestion de votre site Edge Delivery jusqu’à [Go-Live](/help/journey-onboarding/go-live-checklist.md).

|  | Tâche | Description |
| --- | --- | --- |
| 1 | Rejoindre le canal de collaboration de produit | Cliquer sur **Soumettre la demande maintenant** envoie une demande à l’Adobe pour créer un canal pour votre entreprise. Si le canal existe déjà, vous êtes transféré vers le canal de votre entreprise. |
| 2 | Remplir les conditions préalables | Cliquez sur **Afficher le tutoriel de prise en main** pour accéder au [didacticiel de prise en main - développeur](https://www.aem.live/developer/tutorial). |
| 3 | Ajout d’un site Edge Delivery | Voir [Ajout d’un site Edge Delivery](#eds-add-site). |
| 4 | Ajouter un domaine | Voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). |
| 5 | Configurer le CDN | Voir [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md). |
| 6 | Configuration du réseau de diffusion de contenu de votre site Edge Delivery | Voir [Ajout d’une configuration CDN](#add-cdn). |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on) (2 minutes, 13 secondes)

## Ajout d’une configuration CDN à votre site Edge Delivery {#add-cdn}

Voir [Ajout d’une configuration CDN](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md).

## Suppression d’un site Edge Delivery {#eds-site-delete}

>[!IMPORTANT]
>
>Si vous supprimez un site Edge Delivery Services, toutes les configurations de réseau de diffusion de contenu associées sont également supprimées. Cette action rompt la connexion entre les domaines personnalisés et le site. Pour plus d’informations, voir Configurations du réseau de diffusion de contenu. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**Pour supprimer un site Edge Delivery :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme avec les Edge Delivery Services configurés, où vous souhaitez ajouter un site Edge Delivery.
1. Effectuez l’une des opérations suivantes :
   * Sur la page **Aperçu du programme**, cliquez sur l’onglet **Edge Delivery**. Dans le tableau du site Edge Delivery, cliquez sur les points de suspension situés à la fin d’une ligne dont vous souhaitez supprimer le site. Cliquez sur **Supprimer**, puis de nouveau sur **Supprimer** pour confirmer la suppression du site.

     ![Ajouter un site Edge Delivery depuis l’onglet Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Dans le coin supérieur gauche de la page, cliquez sur l’icône représentant un hamburger pour afficher le menu de navigation de gauche. Sous l’en-tête **Services**, cliquez sur **Edge Delivery Sites**. Dans le tableau du site Edge Delivery, cliquez sur les points de suspension situés à la fin d’une ligne dont vous souhaitez supprimer le site. Cliquez sur **Supprimer**, puis de nouveau sur **Supprimer** pour confirmer la suppression du site.


     ![Ajouter un site Edge Delivery à partir du bouton Edge Delivery Sites](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)


<!--
Edge Delivery Services can be enabled when adding a new production program or editing an existing one.

![Add production program with Edge Delivery Services](assets/add-production-program-with-edge.png)

For more information about adding programs, see the following:

* [Create Production programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* [Create Sandbox programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) -->
