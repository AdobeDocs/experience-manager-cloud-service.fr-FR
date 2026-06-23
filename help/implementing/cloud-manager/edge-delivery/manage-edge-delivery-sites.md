---
title: Gestion de sites Edge Delivery dans Cloud Manager
description: Découvrez comment ajouter une configuration de réseau CDN à un site Edge Delivery ou supprimer un site Edge Delivery.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 960aa3c6-27b9-44b1-81ea-ad8c5bbc99a5
source-git-commit: 069e94e230b856fba15c3f465c966a5bf6b0ac46
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 43%

---

# Gestion d’un site Edge Delivery dans Cloud Manager {#manage-edge-delivery-sites}

Découvrez comment gérer des sites Edge Delivery dans Cloud Manager en ajoutant une configuration de réseau CDN à un site existant. Vous pouvez également supprimer un site Edge Delivery.

## Ajouter un mappage de domaine à un site Edge Delivery existant {#add-cdn-to-edge-delivery-site}

Consultez [Ajouter un mappage de domaine](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md).

## Attribution d’un nouveau nom à un site Edge Delivery (#rename-edge-delivery-site)

Dans Adobe Cloud Manager, vous renommez un site Edge Delivery pour plusieurs raisons :

* **Clarté et organisation** : pour mieux décrire l’objectif du site ou son environnement associé (par exemple, production, évaluation).
* **Pour éviter toute confusion** : si plusieurs sites sont en cours d’utilisation, renommer peut permettre de les différencier, ce qui réduit le risque d’appliquer des configurations ou des mises à jour à un site incorrect.
* **Normalisation** : pour respecter une convention de nommage cohérente qui s’aligne sur les directives de votre entreprise pour une gestion et un audit plus simples.

**Pour renommer un site Edge Delivery, procédez comme suit :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme avec Edge Delivery Services configuré, là où vous souhaitez ajouter un site Edge Delivery.
1. Utilisez l’une des méthodes suivantes :

   * Sur la page **Aperçu du programme**, cliquez sur l’onglet **Edge Delivery**. Dans le tableau des sites d’Edge Delivery, cliquez sur les points de suspension à la fin d’une ligne dont vous souhaitez renommer le site.
Cliquez sur **Renommer**.
   * Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral gauche. Sous l’en-tête **Services**, cliquez sur ![Icône Pages web](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
Dans le tableau des sites d’Edge Delivery, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez renommer le site. Cliquez sur **Renommer**.

1. Dans la boîte de dialogue **Modifier le site Edge Delivery**, dans le champ de texte **Nom du site**, saisissez le nouveau nom du site.
1. Cliquez sur **Modifier**.


## Activation du niveau de publication pour un site Edge Delivery (Beta) {#activate-publish-tier-for-eds}

>[!NOTE]
>
>La fonction de publication décrite ici se trouve dans Beta. Pour rejoindre Beta, envoyez un e-mail à l’adresse [grp-beta_xwalk-publish_config@adobe.com](mailto:grp-beta_xwalk-publish_config@adobe.com) avec votre ID d’organisation et votre ID de programme Adobe.

Cette fonctionnalité s’applique uniquement aux sites Edge Delivery créés avec l’option **Création AEM** dans les programmes où la fonctionnalité de niveau publication flexible est activée.

Si votre site Edge Delivery utilise la création AEM, Adobe ne met pas en service le niveau de publication par défaut, car Edge Delivery gère la diffusion de contenu. Cependant, vous pouvez activer le niveau de publication à tout moment si votre site le requiert. Par exemple, si vous devez prendre en charge la publication AEM traditionnelle avec Edge Delivery.

Une fois votre site Edge Delivery créé et son statut affiché dans Cloud Manager, la mention **Vérifié** vous permet de créer et de publier du contenu à l’aide de l’éditeur universel d’AEM.

**Pour accéder à l’éditeur universel à partir de Cloud Manager :**

1. Sous l’onglet Edge Delivery, dans la liste des sites Edge Delivery, recherchez votre site.

   ![Publication de contenu de l’auteur AEM vers Edge Delivery.](/help/implementing/cloud-manager/edge-delivery/assets/eds-content-source-link.png)

1. Cliquez sur le lien Source de contenu **dans la ligne du site.** Le lien ouvre la page de l’éditeur universel d’AEM, à partir de laquelle vous pouvez créer et modifier du contenu pour votre site.—>

**Pour activer le niveau de publication d’un site Edge Delivery :**

1. Sur la page **Présentation du programme**, sous l’onglet **Publier la diffusion**, dans la vignette **Environnement**, cliquez sur l’icône Informations .

1. Dans le pop-up d’information, sous **URL de publication**, sélectionnez **Cliquer pour activer** pour activer la mise en service du niveau de publication dans l’interface utilisateur de Cloud Manager.

   ![Cliquez pour activer la mise en service du niveau de publication](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/click-to-activate-publish-tier-capabilities.png)

1. Dans la boîte de dialogue Activer le niveau de publication, cliquez sur **Activer**.

   ![Boîte de dialogue Activer le niveau de publication](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/activate-publish-tier.png)

   Une fois activé, le niveau de publication est automatiquement configuré. Vous pouvez également configurer le niveau de publication automatiquement si l’auteur tente de publier directement du contenu à partir de l’interface utilisateur d’AEM.

   Une fois le niveau de publication activé et configuré, le lien **Cliquez pour activer** devient désactivé/indisponible.

* **À partir de l’instance de création AEM** — Dans l’interface de création AEM, cliquez sur **Publication rapide** pour publier du contenu directement sur votre site Edge Delivery. Le niveau de publication n’est pas requis pour cette opération lorsque Edge Delivery gère la diffusion.

Après la publication, prévisualisez le contenu dans l’URL `.page` de votre site ou affichez-le en direct à l’URL `.live`.—>

>[!NOTE]
>
>L’activation du niveau de publication ajoute l’infrastructure de publication à votre environnement. Cette fonctionnalité affecte la consommation des ressources de votre programme. Pour configurer si le niveau de publication est requis au niveau du programme, consultez [Niveau de publication flexible (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).


## Suppression d’un site Edge Delivery {#delete-edge-delivery-site}

Si vous supprimez un site Edge Delivery Services, toutes les configurations de réseau CDN associées sont également supprimées. Cette action rompt la connexion entre les domaines personnalisés et le site. Pour plus d’informations, voir Configurations du réseau CDN. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**Pour supprimer un site Edge Delivery, procédez comme suit :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Dans la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme avec Edge Delivery Services configuré, là où vous souhaitez ajouter un site Edge Delivery.
1. Utilisez l’une des méthodes suivantes :

   * Sur la page **Aperçu du programme**, cliquez sur l’onglet **Edge Delivery**. Dans le tableau des sites d’Edge Delivery, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez supprimer le site.
Cliquez sur ![Icône Supprimer le site Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Supprimer**, puis cliquez de nouveau sur **Supprimer** pour confirmer la suppression du site.

     ![Ajout d’un site Edge Delivery depuis l’onglet Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral gauche. Sous l’en-tête **Services**, cliquez sur ![Icône Page web pour les sites Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
Dans le tableau des sites d’Edge Delivery, cliquez sur ![icône Plus](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) à la fin d’une ligne dont vous souhaitez supprimer le site. Cliquez sur ![Icône Supprimer le site Edge Delivery](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Supprimer**, puis cliquez de nouveau sur **Supprimer** pour confirmer la suppression du site.

     ![Ajout d’un site Edge Delivery à partir du bouton Sites Edge Delivery](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Gérer un site Edge Delivery entre Helix 4 et Helix 5

Utilisez le point d’entrée de l’API `/program/{programId}/site/{siteId}` pour migrer un site Edge Delivery entre Helix 4 et Helix 5.

>[!IMPORTANT]
>
>Les configurations de réseau CDN pour les sites web Helix 4 ne peuvent pas être migrées automatiquement vers Helix 5. Cette limitation existe car les sites de production clients s’exécutent toujours sur Helix 4, tandis que leurs versions Helix 5 sont toujours en cours de développement.

**Conditions préalables**

* Le `sitename` doit déjà exister.
* Vous devez connaîtres les valeurs `branchName`, Helix `version` et `repo` appropriées.
* La migration modifie uniquement `branchName`, Helix `version` et `repo`. Le champ de propriétaire ne peut pas être modifié.

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

### Exemple 1 : migrer vers Helix 5

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


### Exemple 2 : migrer vers Helix 4

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

### Exemple 3 : migrer du site repoless vers Helix 5

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
