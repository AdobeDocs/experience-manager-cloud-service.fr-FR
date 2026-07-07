---
title: Intégration du gestionnaire de contenu à Dynamic Media
description: Découvrez comment intégrer le gestionnaire d’accès à Dynamic Media pour permettre aux utilisateurs de parcourir, de prévisualiser et de sélectionner des rendus Dynamic Media à utiliser dans leurs applications et workflows.
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
source-git-commit: d37ebf94f617e8424799757c18037a73e97820b4
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 8%

---

# Intégration à Dynamic Media {#integrate-dynamic-media}

Content Advisor s’intègre à Dynamic Media pour permettre aux utilisateurs de parcourir, de prévisualiser et de sélectionner des rendus Dynamic Media à utiliser dans leurs applications et workflows. Les utilisateurs peuvent choisir parmi les rendus disponibles, les paramètres d’image prédéfinis, les recadrages intelligents et appliquer les modificateurs Dynamic Media pris en charge pour personnaliser la diffusion des ressources. Les sections suivantes décrivent comment traiter les informations de rendu sélectionnées et générer des URL de diffusion Dynamic Media à utiliser dans votre application.

## Création d’URL Dynamic Media à l’aide de selectedMedia {#build-dynamic-media-urls-selectedmedia}

Lorsqu’un utilisateur sélectionne un rendu Dynamic Media dans le panneau de gestion de contenu Dynamic Media, les informations de rendu sélectionnées sont renvoyées dans l’objet `selectedMedia`. L’application hôte doit utiliser ces informations pour générer l’URL de diffusion Dynamic Media appropriée.

>[!NOTE]
>
> L’application hôte doit mettre en œuvre la logique de génération d’URL décrite dans cette section pour utiliser les rendus Dynamic Media sélectionnés à partir du gestionnaire d’accès. Les informations de rendu sélectionnées sont renvoyées sous forme de métadonnées et ne sont pas automatiquement converties en URL de diffusion.

### selectedMedia, objet {#selectedmedia-object}

L’objet `selectedMedia` est ajouté à la ressource sélectionnée et contient des informations sur le rendu Dynamic Media sélectionné par l’utilisateur.

```javascript
'selectedMedia': Array<{
    base?: string;
    preset?: string;
    smartcrop?: string;
    modifiers?: Array<string>;
    apiStyle?: 'scene7' | 'openapi'
}>;
```

L’objet `selectedMedia` contient les propriétés suivantes :

| Propriété | Description |
|---|---|
| `base` | Rendu de base sélectionné. |
| `preset` | Paramètre d’image prédéfini sélectionné. |
| `smartcrop` | Rendu de recadrage intelligent sélectionné. |
| `modifiers` | Un ou plusieurs modificateurs Dynamic Media ajoutés par l’utilisateur. |
| `apiStyle` | Indique si le rendu sélectionné utilise la pile de diffusion Scene7 (`scene7`) ou OpenAPI (`openapi`). |

Par exemple, lorsqu’un utilisateur sélectionne un rendu de base et applique le modificateur `rotate=90`, l’objet renvoyé ressemble à ce qui suit :

```javascript
selectedMedia: {
    apiStyle: "scene7",
    base: "scene7company/image",
    modifiers: ["rotate=90"]
}
```

![Affichage des rendus Dynamic Media](assets/content-advisor-dm-renditions.png)

### Accès à selectedMedia dans le rappel handleSelection {#access-selectedmedia}

Une fois qu’un rendu est sélectionné, l’objet `selectedMedia` est disponible dans la payload `selectedAssets` renvoyée par le rappel `handleSelection`.

```javascript
async function handleSelection(assets) {

    const dmUrls = [];

    assets.forEach((asset) => {

        if(asset?.selectedMedia){

            const dmUrl = createDMUrlFromSelectedMedia(
                asset.selectedMedia,
                asset
            );

            dmUrls.push({ asset, dmUrl });

        }

    });
}
```

Le rappel effectue une itération sur les ressources sélectionnées. Pour chaque ressource contenant un objet `selectedMedia`, l’application génère une URL Dynamic Media à l’aide des informations de rendu sélectionnées.

## Génération d’une URL Dynamic Media {#generate-dynamic-media-url}

La fonction suivante valide les informations de rendu sélectionnées et détermine la pile de diffusion Dynamic Media à utiliser.

```javascript
const DM_OPENAPI_API_STYLE = 'openapi';
const DM_SCENE7_API_STYLE = 'scene7';
const ASSET_REPO_NAME_KEY = 'repo:name';
const ASSET_REPO_ID_KEY = 'repo:id';
const REPO_ID_KEY = 'repo:repositoryId';

export const createDMUrlFromSelectedMedia = (
    selectedMedia,
    repoMetadata
) => {
    if (!selectedMedia || !selectedMedia?.apiStyle) {
        throw new Error(
            'Selected media or api style is not valid'
        );
    }

    if (
        selectedMedia?.apiStyle === DM_OPENAPI_API_STYLE
    ) {
        return buildDMOpenApiUrl(
            selectedMedia,
            repoMetadata
        );
    } else if (
        selectedMedia?.apiStyle === DM_SCENE7_API_STYLE
    ) {
        return buildDMScene7Url(
            selectedMedia,
            repoMetadata
        );
    }
};
```

Cette fonction effectue les actions suivantes :

* Vérifie que le rendu sélectionné contient une valeur `apiStyle`.
* Détermine si le rendu sélectionné utilise Dynamic Media avec des fonctionnalités OpenAPI ou Dynamic Media Scene7.
* Appelle la fonction de génération d’URL appropriée en fonction de la pile de diffusion sélectionnée.

### Création d’une URL OpenAPI Dynamic Media {#build-openapi-url}

La fonction suivante génère une URL OpenAPI Dynamic Media à l’aide des informations de rendu et des métadonnées de référentiel sélectionnées.

```javascript
export const buildDMOpenApiUrl = (
    selectedMedia,
    repoMetadata
) => {
    const { base, preset, smartcrop, modifiers }
        = selectedMedia;

    const dmDomain =
        repoMetadata?.[REPO_ID_KEY]
            .replace('author-', 'delivery-');

    const assetName =
        repoMetadata?.[ASSET_REPO_NAME_KEY];

    const assetId =
        repoMetadata?.[ASSET_REPO_ID_KEY];

    const seoName =
        assetName?.split('.')[0];

    const assetFormat =
        repoMetadata?.['dc:format'];

    let dmUrl;

    if (
        assetFormat &&
        assetFormat.startsWith('video/')
    ) {

        dmUrl =
`https://${dmDomain}/adobe/assets/${assetId}/play`;

    } else {

        dmUrl =
`https://${dmDomain}/adobe/assets/${assetId}/as/${seoName}.avif`;

        if (base) {
        } else if (preset) {
            dmUrl =
`${dmUrl}?preset=${preset}`;
        } else if (smartcrop) {
            dmUrl =
`${dmUrl}?smartcrop=${smartcrop}`;
        }
    }

    if (modifiers && dmUrl) {

        const modifierString =
            getModifierString(selectedMedia);

        if(base) {
            dmUrl =
`${dmUrl}?${modifierString}`;
        } else {
            dmUrl =
`${dmUrl}&${modifierString}`;
        }
    }

    return dmUrl;
};
```

Cette fonction :

* Récupère les informations du référentiel nécessaires à la construction de l’URL de diffusion.
* Crée l&#39;URL de diffusion OpenAPI de base.
* Ajoute le paramètre prédéfini ou le recadrage intelligent sélectionné à l’URL, le cas échéant.
* Ajoute tous les modificateurs sélectionnés par l’utilisateur.
* Renvoie l’URL de diffusion OpenAPI finale.

Pour les ressources vidéo, la fonction génère l’URL du lecteur vidéo Dynamic Media.

### Création d’une URL Dynamic Media Scene7 {#build-scene7-url}

La fonction suivante génère une URL Dynamic Media en mode Scene7.

```javascript
export const buildDMScene7Url = (
    selectedMedia,
    repoMetadata
) => {

    const {
        base,
        preset,
        smartcrop,
        modifiers
    } = selectedMedia;

    let scene7Domain =
        repoMetadata?.['repo:scene7Domain'];

    const scene7File =
        repoMetadata?.['repo:scene7File'];

    if (!scene7Domain || !scene7File) {
        return null;
    }

    scene7Domain =
        scene7Domain.startsWith('http://')
        ? scene7Domain.replace(
            'http://',
            'https://'
          )
        : scene7Domain;

    scene7Domain =
        scene7Domain?.endsWith('/')
        ? scene7Domain
        : `${scene7Domain}/`;

    let dmUrl;

    if (base) {

        dmUrl =
`${scene7Domain}is/image/${base}`;

    } else if (preset) {

        dmUrl =
`${scene7Domain}is/image/${scene7File}?$${preset}$`;

    } else if (smartcrop) {

        dmUrl =
`${scene7Domain}is/image/${scene7File}:${smartcrop}`;
    }

    if (modifiers && dmUrl) {

        const modifierString =
            getModifierString(selectedMedia);

        if (preset) {
            dmUrl =
`${dmUrl}&${modifierString}`;
        } else {
            dmUrl =
`${dmUrl}?${modifierString}`;
        }
    }

    return dmUrl;
};
```

Cette fonction :

* Récupère le domaine Scene7 et les informations sur les ressources à partir des métadonnées du référentiel.
* Crée une URL pour le rendu de base, le paramètre d’image prédéfini ou le recadrage intelligent sélectionné.
* Ajoute les modificateurs sélectionnés.
* Renvoie l’URL de diffusion Scene7 finale.

## Générer la chaîne des modificateurs {#generate-modifiers-string}

La fonction d’assistance suivante convertit le tableau des modificateurs en une chaîne de requête compatible avec les URL.

```javascript
export const getModifierString = (
    selectedMedia
) => {

    const { modifiers } = selectedMedia;

    if (modifiers) {

        const modifierString =
            modifiers.length > 0
                ? modifiers.join('&')
                : '';

        return modifierString;
    }

    return null;
};
```

La fonction combine tous les modificateurs sélectionnés en une seule chaîne séparée par des esperluettes (`&`).

Par exemple :

```javascript
[
    'rotate=90',
    'width=1200'
]
```

renvoie :

```text
rotate=90&width=1200
```

La chaîne générée est ajoutée à l’URL Dynamic Media finale et applique les transformations sélectionnées lors de la diffusion de la ressource.

**Voir également**

* [Traduire les ressources](/help/assets/translate-assets.md)
* [API HTTP Assets](/help/assets/mac-api-assets.md)
* [Formats de fichiers pris en charge par Assets](/help/assets/file-format-support.md)
* [Rechercher des ressources](/help/assets/search-assets.md)
* [Ressources connectées](/help/assets/use-assets-across-connected-assets-instances.md)
* [Rapports de ressources](/help/assets/asset-reports.md)
* [Schémas de métadonnées](/help/assets/metadata-schemas.md)
* [Télécharger des ressources](/help/assets/download-assets-from-aem.md)
* [Gestion des métadonnées](/help/assets/manage-metadata.md)
* [Gérer les modèles Dynamic Media](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Gérer les rapports](/help/assets/manage-reports-assets-view.md)
* [Facettes de recherche](/help/assets/search-facets.md)
* [Gérer les collections](/help/assets/manage-collections.md)
* [Import des métadonnées en bloc](/help/assets/metadata-import-export.md)
* [Publier des ressources sur AEM et Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

