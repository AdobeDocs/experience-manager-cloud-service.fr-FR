---
title: API HTTP Assets
description: Créer, lire, mettre à jour, supprimer et gérer des ressources numériques à l’aide de l’API HTTP dans [!DNL Experience Manager Assets].
contentOwner: AG
feature: Assets HTTP API
role: Developer, Architect, Admin
exl-id: a3b7374d-f24b-4d6f-b6db-b9c9c962bb8d
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1737'
ht-degree: 76%

---

# Gestion des ressources numériques à l’aide de l’API HTTP [!DNL Adobe Experience Manager Assets]{#assets-http-api}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime et Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouvelle</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Intégration d’AEM Assets à Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Extensibilité de l’interface utilisateur</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Nouveau</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Activation de Dynamic Media Prime et Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Bonnes pratiques de recherche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Bonnes pratiques relatives aux métadonnées</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Hub de contenus</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Fonctionnalités Dynamic Media avec OpenAPI</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Documentation de développement pour AEM Assets</b></a>
        </td>
    </tr>
</table>

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/extending/mac-api-assets.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

## Prise en main de l’API HTTP [!DNL Assets] d’AEM {#overview}

L’API HTTP [!DNL Assets] d’AEM permet d’effectuer des opérations CRUD (créer, lire, mettre à jour et supprimer) sur des ressources numériques par le biais d’une interface REST disponible à l’adresse /`api/assets`. Ces opérations s’appliquent aux métadonnées, rendus et commentaires des ressources. Elle comprend la [prise en charge des fragments de contenu](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
> Une implémentation OpenAPI modernisée de l’API de gestion des fragments de contenu est disponible. Pour consulter la documentation complète, voir [API de gestion des fragments de contenu](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/). Il est recommandé d’utiliser la nouvelle implémentation d’OpenAPI. L’utilisation existante de l’API HTTP Assets pour les fragments de contenu doit être migrée vers la nouvelle API ouverte de gestion des fragments de contenu.

Pour accéder à l’API :

1. Ouvrez le document du service API à l’adresse `https://[hostname]:[port]/api.json`.
1. Suivez le lien du service [!DNL Assets] pointant vers `https://[hostname]:[server]/api/assets.json`.

La réponse de l’API est un fichier JSON pour certains types MIME et un code de réponse pour tous les types MIME. La réponse JSON est facultative et peut ne pas être disponible, par exemple pour les fichiers PDF. Fiez-vous au code de réponse pour une analyse ou des actions supplémentaires.

>[!NOTE]
>
>Tous les appels d’API liés au chargement ou à la mise à jour des ressources ou des fichiers binaires en général (tels que les rendus) sont obsolètes pour un déploiement d’[!DNL Experience Manager] as a [!DNL Cloud Service]. Pour charger des fichiers binaires, utilisez plutôt des [API de chargement binaire direct](developer-reference-material-apis.md#asset-upload).

## Gestion des fragments de contenu {#content-fragments}

Un [fragment de contenu](/help/assets/content-fragments/content-fragments.md) est une ressource structurée qui stocke du texte, des nombres et des dates. Comme il existe plusieurs différences avec les ressources `standard` (telles que les images ou les documents), certaines règles supplémentaires s’appliquent pour gérer les fragments de contenu.

Pour plus d’informations, consultez [Prise en charge de fragments de contenu dans l’API HTTP d’ [!DNL Experience Manager Assets] ](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
>Consultez [API AEM pour la diffusion et la gestion de contenu structuré](/help/headless/apis-headless-and-content-fragments.md) pour un aperçu des différentes API disponibles et une comparaison de certains des concepts impliqués.
>
>Les [OpenAPI de modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.

## Examiner le modèle de données {#data-model}

L’API HTTP [!DNL Assets] expose principalement deux éléments : des dossiers et des ressources standard. Elle fournit également des éléments détaillés pour les modèles de données personnalisés utilisés dans les fragments de contenu. Pour plus d’informations, voir Modèles de données de fragments de contenu. Pour plus d’informations, consultez [Modèles de données de fragments de contenu](/help/assets/content-fragments/assets-api-content-fragments.md#content-models-and-content-fragments).

>[!NOTE]
>
>Les [OpenAPI de modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.

### Gestion des dossiers {#folders}

Les dossiers sont comparables aux répertoires dans les systèmes de fichiers traditionnels. Les dossiers peuvent contenir des ressources, des sous-dossiers, ou les deux. Les dossiers se composent des éléments suivants :

**Entités** : les entités d’un dossier sont ses éléments enfants qui peuvent, à leur tour, être des dossiers et des ressources.

**Propriétés** :

* `name` : nom du dossier (dernier segment du chemin de l’URL, sans l’extension).
* `title` : un titre facultatif s’affiche à la place du nom du dossier.

>[!NOTE]
>
>Certaines propriétés de dossier ou de ressource sont associées à un préfixe différent. Le préfixe `jcr` de `jcr:title`, `jcr:description` et `jcr:language` est remplacé par le préfixe `dc`. Par conséquent, dans le JSON renvoyé, `dc:title` et `dc:description` contiennent respectivement les valeurs de `jcr:title` et `jcr:description`.

Les dossiers **Liens** présentent trois liens :

* `self` : lien vers le dossier lui-même.
* `parent` : lien vers le dossier parent.
* `thumbnail` (facultatif) : lien vers une image miniature de dossier.

### Gestion des ressources {#assets}

Dans [!DNL Experience Manager], une ressource contient les éléments suivants :

* **Propriétés et métadonnées :** informations descriptives sur la ressource.
* **Fichier binaire :** fichier chargé à l’origine.
* **Rendus :** plusieurs rendus configurés (images de différentes tailles, différents codages vidéo ou pages extraites de fichiers PDF/Adobe InDesign, par exemple).
* **Commentaires (facultatif) :** remarques fournies par l’utilisateur.

Pour plus d’informations sur les éléments des fragments de contenu, voir [Prise en charge de fragments de contenu dans l’API HTTP Experience Manager Assets](/help/assets/content-fragments/assets-api-content-fragments.md).

>[!NOTE]
>
>Les [OpenAPI de modèle de fragment de contenu et de fragment de contenu](/help/headless/content-fragment-openapis.md) sont également disponibles.

Dans [!DNL Experience Manager], un dossier comprend les composants suivants :

* Entités : les enfants des ressources sont ses rendus.
* Propriétés.
* Liens.

## Explorer les opérations d’API disponibles {#available-features}

L’API HTTP d’[!DNL Assets] offre les fonctionnalités suivantes :

* [Récupérer une liste de dossiers](#retrieve-a-folder-listing)
* [Créer un dossier](#create-a-folder)
* [Créer une ressource (obsolète)](#create-an-asset)
* [Mettre à jour le fichier binaire d’une ressource (obsolète)](#update-asset-binary)
* [Mettre à jour les métadonnées d’une ressource](#update-asset-metadata)
* [Créer un rendu de ressource](#create-an-asset-rendition)
* [Mettre à jour un rendu de ressource](#update-an-asset-rendition)
* [Créer un commentaire de ressource](#create-an-asset-comment)
* [Copier un dossier ou une ressource](#copy-a-folder-or-asset)
* [Déplacer un dossier ou une ressource](#move-a-folder-or-asset)
* [Supprimer un dossier, une ressource ou un rendu](#delete-a-folder-asset-or-rendition)

>[!NOTE]
>
>Pour faciliter la lecture, les notations cURL complètes ne sont pas utilisées dans les exemples suivants. La notation correspond à [Resty](https://github.com/micha/resty) qui est un wrapper de script pour cURL.

<!-- TBD: The Console Manager is not available now. So how to configure the below? 

**Prerequisites**

* Go to `https://[aem_server]:[port]/system/console/configMgr`.
* Navigate to **Adobe Granite CSRF Filter**.
* Make sure the property **Filter Methods** includes: POST, PUT, DELETE.
-->

## Récupérer une liste de dossiers {#retrieve-a-folder-listing}

Récupère une représentation Siren d’un dossier existant et de ses entités enfants (sous-dossiers ou ressources).

**Requête** : `GET /api/assets/myFolder.json`

**Codes de réponse** : les codes de réponse sont les suivants :

* 200 – OK – succès.
* 404 – INTROUVABLE – le dossier n’existe pas ou n’est pas accessible.
* 500 – ERREUR INTERNE DU SERVEUR – si une autre erreur s’est produite.

**Réponse** : la classe de l’entité renvoyée est une ressource ou un dossier. Les propriétés des entités contenues représentent un sous-ensemble du jeu complet des propriétés de chaque entité. Pour obtenir une représentation complète de l’entité, la clientèle doit récupérer le contenu de l’URL vers laquelle pointe le lien avec l’élément `rel` `self`.

## Créer un dossier {#create-a-folder}

Crée un dossier `sling` : `OrderedFolder` à l’emplacement indiqué. Si `*` est indiqué au lieu d’un nom de nœud, le servlet utilisera le nom du paramètre comme nom de nœud. La requête accepte l’une des conditions suivantes :

* Représentation Siren du nouveau dossier
* Ensemble de paires nom-valeur, codées sous la forme `application/www-form-urlencoded` ou `multipart`/ `form`- `data`. Ces fonctions sont utiles pour créer un dossier directement à partir d’un formulaire HTML.

Les propriétés du dossier peuvent, en outre, être spécifiées en tant que paramètres de requête URL.

Un appel d’API échoue avec un code de réponse `500` si le nœud parent du chemin d’accès fourni n’existe pas. Un appel renvoie un code de réponse `409` si le dossier existe.

**Paramètres** : `name` est le nom du dossier.

**Requête**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Codes de réponse** : les codes de réponse sont les suivants :

* 201 – CRÉÉ – en cas de réussite de la création.
* 409 – CONFLIT – si un dossier existe.
* 412 – ÉCHEC DE LA PRÉCONDITION – si la collection racine est introuvable ou inaccessible.
* 500 – ERREUR INTERNE DU SERVEUR – si une autre erreur s’est produite.

## Créer une ressource  {#create-an-asset}

La création de ressources n’est pas prise en charge via cette API HTTP. Pour la création de ressources, utilisez l’API [chargement de ressources](developer-reference-material-apis.md).

## Mettre à jour un fichier binaire de ressource {#update-asset-binary}

Pour plus d’informations sur la mise à jour de fichiers binaires de ressources, consultez [Chargement de ressources](developer-reference-material-apis.md). Vous ne pouvez pas mettre à jour un fichier binaire de ressources à l’aide de l’API HTTP.

## Mettre à jour les métadonnées d’une ressource {#update-asset-metadata}

Cette opération met à jour les métadonnées de la ressource. Lors de la mise à jour des propriétés dans l’espace de noms `dc:`, la propriété `jcr:` correspondante est mise à jour. Toutefois, l’API ne synchronise pas les propriétés sous les deux espaces de noms.

**Requête** : `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**Codes de réponse** : les codes de réponse sont les suivants :

* 200 – OK – si la ressource a été mise à jour avec succès.
* 404 – INTROUVABLE – si la ressource n’a pas été trouvée ou est inaccessible à l’aide de l’URI fourni.
* 412 – ÉCHEC DE LA PRÉCONDITION – si la collection racine est introuvable ou inaccessible.
* 500 – ERREUR INTERNE DU SERVEUR – si une autre erreur s’est produite.

## Créer un rendu de ressource {#create-an-asset-rendition}

Créer un rendu pour une ressource. Si le nom de paramètre de requête n’est pas fourni, le nom de fichier est utilisé comme nom du rendu.

**Paramètres** : les paramètres sont les suivants :

`name` : pour le nom du rendu.
`file` : fichier binaire pour le rendu comme référence.

**Requête**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Codes de réponse**

* 201 – CRÉÉ – si le rendu a été créé avec succès.
* 404 – INTROUVABLE – si la ressource n’a pas été trouvée ou est inaccessible à l’aide de l’URI fourni.
* 412 – ÉCHEC DE LA PRÉCONDITION – si la collection racine est introuvable ou inaccessible.
* 500 – ERREUR INTERNE DU SERVEUR – si une autre erreur s’est produite.

## Mettre à jour un rendu de ressource {#update-an-asset-rendition}

Met à jour et remplace le rendu d’une ressource par les nouvelles données binaires.

**Requête** : `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Codes de réponse** : les codes de réponse sont les suivants :

* 200 – OK – si le rendu a été mis à jour avec succès.
* 404 – INTROUVABLE – si la ressource n’a pas été trouvée ou est inaccessible à l’aide de l’URI fourni.
* 412 – ÉCHEC DE LA PRÉCONDITION – si la collection racine est introuvable ou inaccessible.
* 500 – ERREUR INTERNE DU SERVEUR – si une autre erreur s’est produite.

## Ajouter un commentaire pour une ressource {#create-an-asset-comment}

**Paramètres** : les paramètres sont `message` pour le corps de message du commentaire et `annotationData` pour les données d’annotation au format JSON.

**Requête** : `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Codes de réponse** : les codes de réponse sont les suivants :

* 201 – CRÉÉ – si le commentaire a été créé avec succès.
* 404 – INTROUVABLE – si la ressource n’a pas été trouvée ou est inaccessible à l’aide de l’URI fourni.
* 412 – ÉCHEC DE LA PRÉCONDITION – si la collection racine est introuvable ou inaccessible.
* 500 – ERREUR INTERNE DU SERVEUR – si une autre erreur s’est produite.

## Copier un dossier ou une ressource {#copy-a-folder-or-asset}

Copie un fichier ou une ressource disponible à l’emplacement indiqué vers une nouvelle destination.

**En-têtes de la requête** : les paramètres sont les suivants :

* `X-Destination` – un nouvel URI de destination appartenant à la portée de la solution d’API pour copier la ressource.
* `X-Depth` – `infinity` ou `0`. L’utilisation du code `0` entraîne la copie exclusive de la ressource et de ses propriétés, mais pas de ses enfants.
* `X-Overwrite` – utilisez le code `F` pour éviter le remplacement d’une ressource à la destination existante.

**Requête** : `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Codes de réponse** : les codes de réponse sont les suivants :

* 201 – CRÉÉ – si le dossier ou la ressource a été copié vers une destination inexistante.
* 204 – AUCUN CONTENU – si le dossier ou la ressource a été copié vers une destination existante.
* 412 – ÉCHEC DE LA PRÉCONDITION – s’il manque un en-tête de requête.
* 500 – ERREUR INTERNE DU SERVEUR – si une autre erreur s’est produite.

## Déplacer un dossier ou une ressource {#move-a-folder-or-asset}

Déplace un dossier ou une ressource de l’emplacement indiqué vers une nouvelle destination.

**En-têtes de la requête** : les paramètres sont les suivants :

* `X-Destination` – un nouvel URI de destination appartenant à la portée de la solution d’API pour copier la ressource.
* `X-Depth` – `infinity` ou `0`. L’utilisation du code `0` entraîne la copie exclusive de la ressource et de ses propriétés, mais pas de ses enfants.
* `X-Overwrite` – Utiliser soit `T` pour forcer la suppression d’une ressource existante, soit `F` pour éviter le remplacement d’une ressource existante.

**Requête** : `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

**Codes de réponse** : les codes de réponse sont les suivants :

* 201 – CRÉÉ – si le dossier ou la ressource a été copié vers une destination inexistante.
* 204 – AUCUN CONTENU – si le dossier ou la ressource a été copié vers une destination existante.
* 412 – ÉCHEC DE LA PRÉCONDITION – s’il manque un en-tête de requête.
* 500 – ERREUR INTERNE DU SERVEUR – si une autre erreur s’est produite.

## Supprimer un dossier, une ressource ou un rendu {#delete-a-folder-asset-or-rendition}

Supprime une ressource (arborescence) pour le chemin indiqué.

**Requête**

* `DELETE /api/assets/myFolder`
* `DELETE /api/assets/myFolder/myAsset.png`
* `DELETE /api/assets/myFolder/myAsset.png/renditions/original`

**Codes de réponse** : les codes de réponse sont les suivants :

* 200 – OK – si le dossier a été supprimé avec succès.
* 412 – ÉCHEC DE LA PRÉCONDITION – si la collection racine est introuvable ou inaccessible.
* 500 – ERREUR INTERNE DU SERVEUR – si une autre erreur s’est produite.

## Respect des bonnes pratiques et des limites de notes {#tips-limitations}

* Assets et ses rendus ne sont plus disponibles via l’interface web [!DNL Assets] et l’API HTTP lorsque l’heure de [!UICONTROL &#x200B; est atteinte] L’API renvoie une erreur 404 si l’[!UICONTROL Heure d’activation] est dans le futur ou l’[!UICONTROL Heure de désactivation] est dans le passé.

* L’API HTTP Assets renvoie uniquement un sous-ensemble de métadonnées. Les espaces de noms sont codés en dur et seuls ces espaces de noms sont renvoyés. Pour obtenir des métadonnées complètes, consultez le chemin d’accès à la ressource `/jcr_content/metadata.json`.

* Certaines propriétés de dossier ou de ressource sont associées à un préfixe différent lors de la mise à jour à l’aide d’API. Le préfixe `jcr` de `jcr:title`, `jcr:description` et `jcr:language` est remplacé par le préfixe `dc`. Par conséquent, dans le JSON renvoyé, `dc:title` et `dc:description` contiennent respectivement les valeurs de `jcr:title` et `jcr:description`.

**Explorer les ressources associées**

* [Traduire les ressources](translate-assets.md)
* [Formats de fichiers pris en charge par Assets](file-format-support.md)
* [Rechercher des ressources](search-assets.md)
* [Ressources connectées](use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](asset-reports.md)
* [Schémas de métadonnées](metadata-schemas.md)
* [Télécharger des ressources](download-assets-from-aem.md)
* [Gestion des métadonnées](manage-metadata.md)
* [Facettes de recherche](search-facets.md)
* [Gérer les collections](manage-collections.md)
* [Import des métadonnées en bloc](metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Documentation de référence pour le développement pour [!DNL Assets]](/help/assets/developer-reference-material-apis.md)
