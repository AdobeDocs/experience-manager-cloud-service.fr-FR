---
title: 'API HTTP Assets '
description: Créer, lire, mettre à jour, supprimer et gérer des ressources numériques à l’aide de l’API HTTP dans [!DNL Adobe Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8b1cc8af67c6d12d7e222e12ac4ff77e32ec7e0e
workflow-type: tm+mt
source-wordcount: '1475'
ht-degree: 100%

---


# API HTTP Assets {#assets-http-api}

## Présentation {#overview}

L’API HTTP Assets permet d’effectuer des opérations CRUD (créer, lire, mettre à jour, supprimer) sur des ressources numériques, notamment les métadonnées, les rendus et les commentaires, ainsi que sur des contenus structurés grâce à des fragments de contenu [!DNL Experience Manager]. Elle est exposée sous `/api/assets` et est implémentée en tant qu’API REST. Elle inclut [la prise en charge des fragments de contenu](/help/assets/content-fragments/assets-api-content-fragments.md).

Pour accéder à l’API, procédez comme suit :

1. Ouvrez le document du service API à l’adresse `https://[hostname]:[port]/api.json`.
1. Suivez le lien du service Assets pointant vers `https://[hostname]:[server]/api/assets.json`.

La réponse de l’API est un fichier JSON pour certains types MIME et un code de réponse pour tous les types MIME. La réponse JSON est facultative et peut ne pas être disponible, par exemple pour les fichiers PDF. Vous pouvez faire appel au code de réponse pour d’autres analyses ou actions.

Après l’[!UICONTROL heure de désactivation], une ressource et ses rendus ne sont plus disponibles via l’interface web [!DNL Assets] ni par le biais de l’API HTTP. L’API renvoie un message d’erreur 404 si l’[!UICONTROL heure d’activation] se situe dans le futur ou si l’[!UICONTROL heure de désactivation] se situe dans le passé.

>[!NOTE]
>
>Tous les appels d’API liés au chargement ou à la mise à jour des ressources ou des fichiers binaires en général (tels que les rendus) sont obsolètes pour un déploiement d’AEM as a Cloud Service. Pour charger des fichiers binaires, utilisez plutôt des [API de chargement binaire direct](developer-reference-material-apis.md#asset-upload-technical).

## Fragments de contenu {#content-fragments}

Un [fragment de contenu](/help/assets/content-fragments/content-fragments.md) est un type de ressource spécial. Il permet d’accéder aux données structurées, telles que les textes, les nombres, les dates, etc. Comme il existe plusieurs différences de ressources `standard` (telles que les images ou les documents), certaines règles supplémentaires s’appliquent pour gérer les fragments de contenu.

Pour plus d’informations, voir [Prise en charge de fragments de contenu dans l’API HTTP Experience Manager Assets](/help/assets/content-fragments/assets-api-content-fragments.md).

## Modèle de données {#data-model}

L’API HTTP Assets présente deux éléments principaux : des dossiers et des ressources (pour les ressources standard).

Il expose également des éléments plus détaillés pour les modèles de données personnalisés décrivant le contenu structuré dans les fragments de contenu. Pour plus d’informations, voir [Modèles de données de fragments de contenu](/help/assets/content-fragments/assets-api-content-fragments.md#content-models-and-content-fragments).

### Dossiers {#folders}

Les dossiers sont comparables aux répertoires des systèmes de fichiers traditionnels. Ils font office de conteneurs pour d’autres dossiers ou ressources. Les dossiers se composent des éléments suivants :

**Entités** : les entités d’un dossier sont ses éléments enfants qui peuvent, à leur tour, être des dossiers et des ressources.

**Propriétés** :

* `name` est le nom du dossier. Il est identique au dernier segment du chemin d’URL, sans l’extension.
* `title` est un titre facultatif du dossier pouvant être affiché au lieu de son nom.

>[!NOTE]
>
>Certaines propriétés de dossier ou de ressource sont associées à un préfixe différent. Le préfixe `jcr` de `jcr:title`, `jcr:description` et `jcr:language` est remplacé par le préfixe `dc`. Par conséquent, dans le JSON renvoyé, `dc:title` et `dc:description` contiennent respectivement les valeurs de `jcr:title` et `jcr:description`.

Les dossiers **Liens** présentent trois liens :

* `self` : lien vers lui-même.
* `parent` : lien vers le dossier parent.
* `thumbnail` : (facultatif) lien vers une miniature de dossier.

### Ressources {#assets}

Dans [!DNL Experience Manager], une ressource contient les éléments suivants :

* Propriétés et métadonnées de la ressource.
* Plusieurs rendus tels que le rendu d’origine (qui est la ressource chargée initialement), une miniature et divers autres rendus. Les rendus supplémentaires peuvent être des images de tailles différentes, différents codages vidéo ou des pages extraites de fichiers PDF ou Adobe InDesign.
* Commentaires facultatifs.

Pour plus d’informations sur les éléments des fragments de contenu, voir [Prise en charge de fragments de contenu dans l’API HTTP Experience Manager Assets](/help/assets/content-fragments/assets-api-content-fragments.md).

Dans [!DNL Experience Manager], un dossier comprend les composants suivants :

* Entités : les enfants des ressources sont ses rendus.
* Propriétés.
* Liens.

## Fonctionnalités disponibles {#available-features}

L’API Assets HTTP offre les fonctionnalités suivantes :

* Récupérer une liste de dossiers.
* Créer un dossier.
* Créer une ressource (obsolète).
* Mettre à jour le fichier binaire d’une ressource (obsolète).
* Mettre à jour les métadonnées d’une ressource.
* Créer un rendu de ressource.
* Mettre à jour un rendu de ressource.
* Créer un commentaire de ressource.
* Copier un dossier ou une ressource.
* Déplacer un dossier ou une ressource.
* Supprimer un dossier, une ressource ou un rendu.

>[!NOTE]
>
>Pour faciliter la lecture, la notation cURL complète n’est pas utilisée dans les exemples suivants. En fait, la notation est liée à [Resty](https://github.com/micha/resty) qui est un wrapper de script pour `cURL`.

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

* 200 - OK - succès.
* 404 - INTROUVABLE - le dossier n’existe pas ou n’est pas accessible.
* 500 - ERREUR INTERNE DU SERVEUR - si une autre erreur s’est produite.

**Réponse** : la classe de l’entité renvoyée est une ressource ou un dossier. Les propriétés des entités contenues représentent un sous-ensemble du jeu complet des propriétés de chaque entité. Pour obtenir une représentation complète de l’entité, les clients doivent récupérer le contenu de l’URL vers laquelle pointe le lien avec l’élément `rel` `self`.

## Créer un dossier {#create-a-folder}

Crée un dossier `sling` : `OrderedFolder` à l’emplacement indiqué. Si un astérisque (`*`) est indiqué au lieu d’un nom de nœud, le servlet utilisera le nom du paramètre comme nom de nœud. Cela est accepté dans la mesure où les données de la requête consistent en une représentation Siren du nouveau dossier ou un ensemble de paires nom-valeur, codé sous la forme `application/www-form-urlencoded` ou `multipart`/ `form`- `data`, ce qui se révèle utile pour créer directement un dossier à partir d’un formulaire HTML. Les propriétés du dossier peuvent, en outre, être spécifiées en tant que paramètres de requête URL.

Un appel d’API échoue avec un code de réponse `500` si le nœud parent du chemin d’accès fourni n’existe pas. Un appel renvoie un code de réponse `409` si le dossier existe déjà.

**Paramètres** : `name` est le nom du dossier.

**Requête**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Codes de réponse** : les codes de réponse sont les suivants :

* 201 - CRÉÉ - en cas de réussite de la création.
* 409 - CONFLIT - si un dossier existe déjà.
* 412 - ÉCHEC DE LA PRÉCONDITION - si la collection racine est introuvable ou inaccessible.
* 500 - ERREUR INTERNE DU SERVEUR - si une autre erreur s’est produite.

## Créer une ressource {#create-an-asset}

Pour plus d’informations sur la création d’une ressource à l’aide d’API, voir [Chargement de ressources](developer-reference-material-apis.md). La création d’une ressource à l’aide de l’API HTTP est obsolète.

## Mettre à jour un fichier binaire de ressource {#update-asset-binary}

Pour plus d’informations sur la mise à jour de fichiers binaires de ressources à l’aide d’API, voir [Chargement de ressources](developer-reference-material-apis.md). La mise à jour d’un fichier binaire de ressource à l’aide de l’API HTTP est obsolète.

## Mettre à jour les métadonnées d’une ressource {#update-asset-metadata}

Met à jour les propriétés de métadonnées d’une ressource. Si vous mettez à jour une propriété du namespace `dc:`, l’API met à jour cette même propriété dans le namespace `jcr`. L’API ne synchronise pas les propriétés des deux namespaces.

**Requête** : `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**Codes de réponse** : les codes de réponse sont les suivants :

* 200 - OK - si la ressource a été mise à jour avec succès.
* 404 - INTROUVABLE - si la ressource n’a pas été trouvée ou est inaccessible à l’aide de l’URI fourni.
* 412 - ÉCHEC DE LA PRÉCONDITION - si la collection racine est introuvable ou inaccessible.
* 500 - ERREUR INTERNE DU SERVEUR - si une autre erreur s’est produite.

## Créer un rendu de ressource {#create-an-asset-rendition}

Créer un rendu pour une ressource. Si le nom de paramètre de requête n’est pas fourni, le nom de fichier est utilisé comme nom du rendu.

**Paramètres** : les paramètres sont `name` pour le nom du rendu et `file` pour la référence au fichier.

**Requête**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Codes de réponse**

* 201 - CRÉÉ - si le rendu a été créé avec succès.
* 404 - INTROUVABLE - si la ressource n’a pas été trouvée ou est inaccessible à l’aide de l’URI fourni.
* 412 - ÉCHEC DE LA PRÉCONDITION - si la collection racine est introuvable ou inaccessible.
* 500 - ERREUR INTERNE DU SERVEUR - si une autre erreur s’est produite.

## Mettre à jour un rendu de ressource {#update-an-asset-rendition}

Met à jour et remplace le rendu d’une ressource par les nouvelles données binaires.

**Requête** : `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Codes de réponse** : les codes de réponse sont les suivants :

* 200 - OK - si le rendu a été mis à jour avec succès.
* 404 - INTROUVABLE - si la ressource n’a pas été trouvée ou est inaccessible à l’aide de l’URI fourni.
* 412 - ÉCHEC DE LA PRÉCONDITION - si la collection racine est introuvable ou inaccessible.
* 500 - ERREUR INTERNE DU SERVEUR - si une autre erreur s’est produite.

## Ajouter un commentaire pour une ressource {#create-an-asset-comment}

Crée un commentaire de ressource.

**Paramètres** : les paramètres sont `message` pour le corps de message du commentaire et `annotationData` pour les données d’annotation au format JSON.

**Requête** : `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Codes de réponse** : les codes de réponse sont les suivants :

* 201 - CRÉÉ - si le commentaire a été créé avec succès.
* 404 - INTROUVABLE - si la ressource n’a pas été trouvée ou est inaccessible à l’aide de l’URI fourni.
* 412 - ÉCHEC DE LA PRÉCONDITION - si la collection racine est introuvable ou inaccessible.
* 500 - ERREUR INTERNE DU SERVEUR - si une autre erreur s’est produite.

## Copier un dossier ou une ressource {#copy-a-folder-or-asset}

Copie un fichier ou une ressource disponible à l’emplacement indiqué vers une nouvelle destination.

**En-têtes de la requête** : les paramètres sont les suivants :

* `X-Destination` - un nouvel URI de destination appartenant à la portée de la solution d’API pour copier la ressource.
* `X-Depth` - `infinity` ou `0`. L’utilisation du code `0` entraîne la copie exclusive de la ressource et de ses propriétés, mais pas de ses enfants.
* `X-Overwrite` - utilisez le code `F` pour éviter le remplacement d’une ressource à la destination existante.

**Requête** : `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Codes de réponse** : les codes de réponse sont les suivants :

* 201 - CRÉÉ - si le dossier ou la ressource a été copié vers une destination inexistante.
* 204 - AUCUN CONTENU - si le dossier ou la ressource a été copié vers une destination existante.
* 412 - ÉCHEC DE LA PRÉCONDITION - s’il manque un en-tête de requête.
* 500 - ERREUR INTERNE DU SERVEUR - si une autre erreur s’est produite.

## Déplacer un dossier ou une ressource {#move-a-folder-or-asset}

Déplace un dossier ou une ressource de l’emplacement indiqué vers une nouvelle destination.

**En-têtes de la requête** : les paramètres sont les suivants :

* `X-Destination` - un nouvel URI de destination appartenant à la portée de la solution d’API pour copier la ressource.
* `X-Depth` - `infinity` ou `0`. L’utilisation du code `0` entraîne la copie exclusive de la ressource et de ses propriétés, mais pas de ses enfants.
* `X-Overwrite` - Utiliser soit `T` pour forcer la suppression d’une ressource existante, soit `F` pour éviter le remplacement d’une ressource existante.

**Requête** : `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

**Codes de réponse** : les codes de réponse sont les suivants :

* 201 - CRÉÉ - si le dossier ou la ressource a été copié vers une destination inexistante.
* 204 - AUCUN CONTENU - si le dossier ou la ressource a été copié vers une destination existante.
* 412 - ÉCHEC DE LA PRÉCONDITION - s’il manque un en-tête de requête.
* 500 - ERREUR INTERNE DU SERVEUR - si une autre erreur s’est produite.

## Supprimer un dossier, une ressource ou un rendu {#delete-a-folder-asset-or-rendition}

Supprime une ressource (arborescence) pour le chemin indiqué.

**Requête**

* `DELETE /api/assets/myFolder`
* `DELETE /api/assets/myFolder/myAsset.png`
* `DELETE /api/assets/myFolder/myAsset.png/renditions/original`

**Codes de réponse** : les codes de réponse sont les suivants :

* 200 - OK - si le dossier a été supprimé avec succès.
* 412 - ÉCHEC DE LA PRÉCONDITION - si la collection racine est introuvable ou inaccessible.
* 500 - ERREUR INTERNE DU SERVEUR - si une autre erreur s’est produite.
