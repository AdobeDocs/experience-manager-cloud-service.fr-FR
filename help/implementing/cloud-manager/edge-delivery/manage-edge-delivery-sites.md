---
title: Gestion de sites Edge Delivery dans Cloud Manager
description: Découvrez comment ajouter une configuration de réseau CDN à un site Edge Delivery ou supprimer un site Edge Delivery.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 960aa3c6-27b9-44b1-81ea-ad8c5bbc99a5
source-git-commit: 4fa8c65d9744b9451089423de0da63b39530973e
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 76%

---

# Gestion d’un site Edge Delivery dans Cloud Manager {#manage-edge-delivery-sites}

Découvrez comment gérer des sites Edge Delivery dans Cloud Manager en ajoutant une configuration de réseau CDN à un site existant. Vous pouvez également supprimer un site Edge Delivery.

## Ajout d’une configuration de réseau CDN à un site Edge Delivery existant {#add-cdn-to-edge-delivery-site}

Voir [Ajout d’une configuration de réseau CDN](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md).

## Attribution d’un nouveau nom à un site Edge Delivery (#rename-edge-delivery-site)

Dans Adobe Cloud Manager, vous pouvez renommer un site Edge Delivery pour plusieurs raisons :

* **Clarté et organisation** : pour mieux décrire l’objectif du site ou son environnement associé (par exemple, production, évaluation).
* **Éviter toute confusion** : si plusieurs sites sont utilisés, le fait de les renommer permet de les différencier facilement, ce qui réduit le risque d’appliquer des configurations ou des mises à jour au mauvais site.
* **Normalisation** : pour respecter une convention de nommage cohérente qui s’aligne sur les directives de votre entreprise pour une gestion et un audit plus simples.

**Pour renommer un site Edge Delivery, procédez comme suit :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme avec Edge Delivery Services configuré, là où vous souhaitez ajouter un site Edge Delivery.
1. Effectuez l’une des opérations suivantes :

   * Dans la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Edge Delivery**. Dans le tableau du site Edge Delivery, cliquez sur les points de suspension en fin de ligne du site que vous souhaitez renommer.
Cliquez sur **Renommer**.
   * Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche. Sous l’en-tête **Services**, cliquez sur ![Icône Pages web](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Sites Edge Delivery**.
Dans le tableau du site Edge Delivery, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez renommer le site. Cliquez sur **Renommer**.

1. Dans la boîte de dialogue **Modifier le site Edge Delivery**, dans le champ de texte **Nom du site**, saisissez le nouveau nom du site.

1. Cliquez sur **Modifier**.

## Suppression d’un site Edge Delivery {#delete-edge-delivery-site}

Si vous supprimez un site Edge Delivery Services, toutes les configurations de réseau CDN associées sont également supprimées. Cette action rompt la connexion entre les domaines personnalisés et le site. Pour plus d’informations, voir Configurations du réseau CDN. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**Pour supprimer un site Edge Delivery, procédez comme suit :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme avec Edge Delivery Services configuré, là où vous souhaitez ajouter un site Edge Delivery.
1. Effectuez l’une des opérations suivantes :

   * Sur la page **Vue d’ensemble du programme**, cliquez sur l’onglet **Edge Delivery**. Dans le tableau du site Edge Delivery, cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez supprimer le site.
Cliquez sur ![Icône Supprimer le site Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Supprimer**, puis cliquez de nouveau sur **Supprimer** pour confirmer la suppression du site.

     ![Ajout d’un site Edge Delivery depuis l’onglet Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Dans le coin supérieur gauche de la page, cliquez sur l’![icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu de gauche. Sous l’en-tête **Services**, cliquez sur ![Icône Page web pour les sites Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Sites Edge Delivery**.
Dans le tableau du site Edge Delivery, cliquez sur ![Icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez supprimer le site. Cliquez sur ![Icône Supprimer le site Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Supprimer**, puis cliquez de nouveau sur **Supprimer** pour confirmer la suppression du site.

     ![Ajout d’un site Edge Delivery à partir du bouton Sites Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Gestion d’un site Edge Delivery entre Helix 4 et Helix 5

Utilisez le point d’entrée de l’API `/program/{programId}/site/{siteId}` pour migrer un site Edge Delivery entre Helix 4 et Helix 5.

>[!IMPORTANT]
>
>Les configurations de réseau CDN pour les sites Web Helix 4 ne peuvent pas être migrées automatiquement vers Helix 5. Cette limitation existe car les sites de production clients peuvent toujours s’exécuter sur Helix 4, tandis que leurs versions Helix 5 sont toujours en cours de développement.

**Conditions préalables**

* Le `sitename` doit déjà exister.
* connaître les valeurs `branchName`, Helix `version` et `repo` appropriées ;
* La migration modifie uniquement `branchName`, Helix `version` et `repo`. Le champ du propriétaire ne peut pas être modifié.

**Format d’API**

```http
PUT /api/program/{programId}/site/{siteId}
```

**Paramètres du corps de la requête**
Crée un remplacement pour un site Edge Delivery afin d’appliquer l’origine spécifiée dans le corps de la requête.

```json
{
  "sitename": "<required site name>",
  "branchName": "<git branch>",
  "version": "v4" | "v5",
  "repo": "<git repository name>"
}
```

### Exemple 1 : migration vers Helix 5

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-site-new-helix5",
  "branchName": "branch",
  "version": "v5",
  "repo": "my-website"
}
```

**Résultat de l’URL d’origine**
Retourne un site Edge Delivery avec l&#39;URL d&#39;origine suivante :

`"origin": "branch--my-website–Teo48.aem.live"`


### Exemple 2 : migration vers Helix 4

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-site-new-helix4",
  "branchName": "branch",
  "version": "v4",
  "repo": "my-website"
}
```

**Résultat de l’URL d’origine**
Renvoie un site Edge Delivery avec l’URL d’origine suivante :

`"origin": "branch--my-website--Teo48.hlx.live"`

### Exemple 3 : migration du site repoless vers Helix 5

**http**

```http
PUT /api/program/{programId}/site/{siteId}
```

**json**

```json
{
  "sitename": "test-reposless-website",
  "branchName": "main",
  "version": "v5",
  "repo": "my-reposless-website"
}
```

**Résultat de l’URL d’origine**
Retourne un site Edge Delivery avec l&#39;URL d&#39;origine suivante :

`"origin": "main--my-repoless-website--Teo48.aem.live"`

## Soumettre un ticket d’assistance {#eds-support-ticket}

{{support-ticket}}
