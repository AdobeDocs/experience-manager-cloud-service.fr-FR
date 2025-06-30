---
title: Références du développeur pour  [!DNL Assets]
description: '[!DNL Assets] Les API et le contenu de référence des développeurs vous permettent de gérer des ressources, notamment des fichiers binaires, des métadonnées, des rendus, des commentaires et des [!DNL Content Fragments].'
contentOwner: AG
feature: Assets HTTP API
role: Developer, Architect, Admin
exl-id: c75ff177-b74e-436b-9e29-86e257be87fb
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1870'
ht-degree: 97%

---

# [!DNL Adobe Experience Manager Assets] Cas d’utilisation pour les développeurs, API et documents de référence {#assets-cloud-service-apis}

L’article contient des recommandations, des documents de référence et des ressources pour les développeurs de [!DNL Assets] as a [!DNL Cloud Service]. Il comprend un nouveau module de chargement de ressources, des références d’API et des informations sur la prise en charge fournie dans les workflows de post-traitement.

## [!DNL Experience Manager Assets] API et opérations {#use-cases-and-apis}

[!DNL Assets] as a [!DNL Cloud Service] fournit plusieurs API pour interagir par programmation avec des ressources numériques. Chaque API prend en charge des cas d’utilisation spécifiques, comme indiqué dans le tableau ci-dessous. L’interface utilisateur [!DNL Assets], l’application de bureau [!DNL Experience Manager] et [!DNL Adobe Asset Link] prennent en charge l’ensemble ou une partie des opérations.

>[!CAUTION]
>
>Certaines API existent toujours mais ne sont pas activement prises en charge (signalées par un ×). Dans la mesure du possible, n’utilisez pas ces API.

| Niveau de prise en charge | Description |
| ------------- | --------------------------- |
| ✓ | Pris en charge |
| × | Pas de prise en charge. Ne pas utiliser. |
| - | Non disponible |

| Cas d’utilisation | [aem-upload](https://github.com/adobe/aem-upload) | API Java [Experience Manager / Sling / JCR](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | [Asset Compute Service](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html?lang=fr) | [[!DNL Assets] API HTTP](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html?lang=fr#create-an-asset) | Servlets Sling [GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) / [POST](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) | [GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=fr) |
| ----------------|:---:|:---:|:---:|:---:|:---:|:---:|
| **Binaire original** |  |  |  |  |  |  |
| Créer l’original | ✓ | × | - | × | × | - |
| Lire l’original | - | × | ✓ | ✓ | ✓ | - |
| Mettre à jour l’original | ✓ | × | ✓ | × | × | - |
| Supprimer l’original | - | ✓ | - | ✓ | ✓ | - |
| Copier l’original | - | ✓ | - | ✓ | ✓ | - |
| Déplacer l’original | - | ✓ | - | ✓ | ✓ | - |
| **Métadonnées** |  |  |  |  |  |  |
| Créer des métadonnées | - | ✓ | ✓ | ✓ | ✓ | - |
| Lire les métadonnées | - | ✓ | - | ✓ | ✓ | - |
| Mettre à jour les métadonnées | - | ✓ | ✓ | ✓ | ✓ | - |
| Supprimer les métadonnées | - | ✓ | ✓ | ✓ | ✓ | - |
| Copier les métadonnées | - | ✓ | - | ✓ | ✓ | - |
| Déplacer les métadonnées | - | ✓ | - | ✓ | ✓ | - |
| **Fragments de contenu (CF)** |  |  |  |  |  |  |
| Créer un CF | - | ✓ | - | ✓ | - | - |
| Lire un CF | - | ✓ | - | ✓ | - | ✓ |
| Mettre à jour un CF | - | ✓ | - | ✓ | - | - |
| Supprimer un CF | - | ✓ | - | ✓ | - | - |
| Copier un CF | - | ✓ | - | ✓ | - | - |
| Déplacer un CF | - | ✓ | - | ✓ | - | - |
| **Versions** |  |  |  |  |  |  |
| Créer une version | ✓ | ✓ | - | - | - | - |
| Lire une version | - | ✓ | - | - | - | - |
| Supprimer une version | - | ✓ | - | - | - | - |
| **Dossiers** |  |  |  |  |  |  |
| Créer un dossier | ✓ | ✓ | - | ✓ | - | - |
| Lire un dossier | - | ✓ | - | ✓ | - | - |
| Supprimer un dossier | ✓ | ✓ | - | ✓ | - | - |
| Copier un dossier | ✓ | ✓ | - | ✓ | - | - |
| Déplacer un dossier | ✓ | ✓ | - | ✓ | - | - |

## Chargement de ressources {#asset-upload}

Dans [!DNL Experience Manager] as a [!DNL Cloud Service], vous pouvez charger directement les ressources dans l’espace de stockage cloud à l’aide de l’API HTTP. Pour charger un fichier binaire, procédez comme suit. Exécutez ces étapes dans une application externe et non dans la JVM [!DNL Experience Manager].

1. [Envoyez une requête HTTP](#initiate-upload). Cela permet d’informer le déploiement [!DNL Experience Manage]r de votre intention de charger un nouveau fichier binaire.
1. [Placez (PUT) le contenu du fichier binaire](#upload-binary) sur un ou plusieurs URI fournis par la requête de lancement.
1. [Envoyez une requête HTTP](#complete-upload) pour informer le serveur que le contenu du fichier binaire a bien été chargé.

![Présentation du protocole de chargement binaire direct](assets/add-assets-technical.png)

>[!IMPORTANT]
>
>Exécutez les étapes ci-dessus dans une application externe et non dans la JVM [!DNL Experience Manager].

Cette approche permet une gestion évolutive et plus performante des chargements de ressources. Les différences par rapport à [!DNL Experience Manager] 6.5 sont les suivantes :

* Les fichiers binaires ne passent pas par [!DNL Experience Manager], qui coordonne désormais simplement le processus de chargement avec l’espace de stockage de fichiers binaires configuré pour le déploiement.
* L’espace de stockage de fichiers binaires fonctionne avec un réseau CDN (réseau de diffusion de contenu) ou Edge. Un CDN sélectionne un point d’entrée de chargement plus proche pour un client. Lorsque les données parcourent une distance plus courte jusqu’à un point d’entrée voisin, les performances de chargement et l’expérience utilisateur s’améliorent, en particulier pour les équipes réparties géographiquement.

>[!NOTE]
>
>Consultez le code client pour implémenter cette approche dans la [bibliothèque de chargement aem](https://github.com/adobe/aem-upload) open-source.
>
>[!IMPORTANT]
>
>Dans certains cas, les modifications peuvent ne pas se propager entièrement entre les requêtes à Experience Manager en raison de la nature cohérente du stockage dans Cloud Service. Cela génère des réponses 404 lors de l’initialisation ou de la complétion d’appels de téléchargement en raison de la non-propagation des créations de dossiers requises. Les client(e)s doivent s’attendre à recevoir des réponses 404 et à les gérer en implémentant une nouvelle tentative avec une stratégie backoff.

### Lancement du chargement {#initiate-upload}

Envoyez une requête HTTP POST vers le dossier souhaité. Les ressources sont créées ou mises à jour dans ce dossier. Incluez le sélecteur `.initiateUpload.json` pour indiquer que la requête est de lancer le chargement d’un fichier binaire. Par exemple, le chemin d’accès au dossier dans lequel la ressource doit être créée est `/assets/folder`. La requête POST est `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`.

Le corps de la requête doit être constitué de données de formulaire `application/x-www-form-urlencoded`, contenant les champs suivants :

* `(string) fileName` : obligatoire. Le nom de la ressource tel qu’il apparaît dans [!DNL Experience Manager].
* `(number) fileSize` : obligatoire. La taille de fichier, en octets, de la ressource en cours de chargement.

Une seule requête peut être utilisée afin de lancer des chargements pour plusieurs fichiers binaires, à condition que chaque binaire contienne les champs obligatoires. En cas de succès, la requête renverra un code d’état `201` et un corps contenant des données JSON au format suivant :

```json
{
    "completeURI": "(string)",
    "folderPath": "(string)",
    "files": [
        {
            "fileName": "(string)",
            "mimeType": "(string)",
            "uploadToken": "(string)",
            "uploadURIs": [
                "(string)"
            ],
            "minPartSize": (number),
            "maxPartSize": (number)
        }
    ]
}
```

* `completeURI` (chaîne) : appelez cet URI lorsque le chargement du fichier binaire est terminé. Il peut s’agir d’un URI absolu ou relatif, et les clients doivent être en mesure de gérer l’un ou l’autre. En d’autres termes, la valeur peut être `"https://[aem_server]:[port]/content/dam.completeUpload.json"` ou `"/content/dam.completeUpload.json"` ; voir [Fin du chargement](#complete-upload).
* `folderPath` (chaîne) : chemin d’accès complet au dossier dans lequel le fichier binaire est chargé.
* `(files)` (tableau) : liste des éléments dont la longueur et l’ordre correspondent à la longueur et à l’ordre de la liste des informations binaires fournies dans la requête de lancement.
* `fileName` (chaîne) : nom du fichier binaire correspondant, tel qu’il est fourni dans la requête de lancement. Cette valeur doit être incluse dans la requête de fin.
* `mimeType` (chaîne) : type MIME du fichier binaire correspondant, tel qu’il est fourni dans la requête de lancement. Cette valeur doit être incluse dans la requête de fin.
* `uploadToken` (chaîne) : jeton de chargement du fichier binaire correspondant. Cette valeur doit être incluse dans la requête de fin.
* `uploadURIs` (tableau) : liste des chaînes dont les valeurs sont des URI complets vers lesquels le contenu du fichier binaire doit être chargé (voir [Chargement d’un fichier binaire](#upload-binary)).
* `minPartSize` (nombre) : longueur minimale, en octets, des données pouvant être fournies à l’un des `uploadURIs`, s’il en existe plusieurs.
* `maxPartSize` (nombre) : longueur maximale, en octets, des données pouvant être fournies à l’un des `uploadURIs`, s’il en existe plusieurs.

### Chargement d’un fichier binaire {#upload-binary}

La sortie de lancement d’un chargement comprend une ou plusieurs valeurs d’URI de chargement. Si plusieurs URI sont fournis, le client peut diviser le fichier binaire en plusieurs parties et effectuer des requêtes PUT de chaque partie vers le fichier URI de chargement, dans l’ordre. Si vous choisissez de diviser le fichier binaire en plusieurs parties, suivez les instructions suivantes :

* Chaque partie, à l’exception de la dernière, doit avoir une taille supérieure ou égale à `minPartSize`.
* Chaque partie doit avoir une taille inférieure ou égale à `maxPartSize`.
* Si la taille de votre fichier binaire dépasse `maxPartSize`, divisez le fichier binaire en plusieurs parties pour le charger.
* Vous n’êtes pas tenu d’utiliser tous les URI.

Si la taille de votre fichier binaire est inférieure ou égale à `maxPartSize`, vous pouvez plutôt charger le fichier binaire entier vers un seul URI de chargement. Si plusieurs URI de chargement sont fournis, utilisez le premier et ignorez les autres. Vous n’êtes pas tenu d’utiliser tous les URI.

Les nœuds de bordure CDN permettent d’accélérer le chargement de fichiers binaires requis.

Pour ce faire, la méthode la plus simple consiste à utiliser une partie d’une taille de `maxPartSize`. Le contrat d’API garantit qu’il existe suffisamment d’URI de chargement pour charger le fichier binaire si vous utilisez une partie de cette taille. Pour ce faire, divisez le fichier binaire en parties d’une taille de `maxPartSize`, en utilisant un URI pour chaque partie, dans l’ordre. La dernière partie peut avoir une taille inférieure ou égale à `maxPartSize`. Par exemple, en supposant que la taille totale du fichier binaire soit de 20 000 octets, le `minPartSize` est de 5 000 octets, `maxPartSize` est de 8 000 octets, et le nombre d’URI de chargement est de 5. Procédez comme suit :

* Chargez les 8 000 premiers octets du fichier binaire à l’aide du premier URI de chargement.
* Chargez les 8 000 octets suivants du fichier binaire à l’aide du deuxième URI de chargement.
* Chargez les 4 000 derniers octets du fichier binaire à l’aide du troisième URI de chargement. Puisqu’il s’agit de la dernière partie, elle n’a pas besoin d’être plus grande que `minPartSize`.
* Vous n’avez pas besoin d’utiliser les deux derniers URI de chargement. Vous pouvez les ignorer.

Une erreur courante est de calculer la taille de la partie en fonction du nombre d’URI de chargement fournis par l’API. Le contrat d’API ne garantit pas que cette approche fonctionne et peut effectivement entraîner des tailles de parties qui ne sont pas comprises entre `minPartSize` et `maxPartSize`. Cela peut entraîner des échecs de chargement de fichiers binaires.

Encore une fois, le moyen le plus facile et le plus sûr est d’utiliser simplement des parties de taille égale à `maxPartSize`.

En cas de succès du chargement, le serveur répond à chaque requête avec un code d’état `201`.

>[!NOTE]
>
>Pour plus d’informations sur l’algorithme de chargement, consultez la [documentation officielle sur les fonctionnalités](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html#Upload) et la [documentation de l’API](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/api/binary/BinaryUpload.html) dans le projet Apache Jackrabbit Oak.

### Fin du chargement {#complete-upload}

Après avoir chargé toutes les parties d’un fichier binaire, envoyez une requête HTTP POST à l’URI complet fourni par les données d’initialisation. Le corps de la requête doit être constitué de données de formulaire `application/x-www-form-urlencoded`, contenant les champs suivants.

| Champs | Type | Requis ou non | Description |
|---|---|---|---|
| `fileName` | Chaîne | Requis | Nom de la ressource, tel qu’il est fourni par les données de lancement. |
| `mimeType` | Chaîne | Requis | Type de contenu HTTP du binaire, tel qu’il est fourni par les données de lancement. |
| `uploadToken` | Chaîne | Requis | Jeton de chargement du binaire, tel qu’il est fourni par les données de lancement. |
| `createVersion` | Booléen | Facultatif | Si la valeur est définie sur `True` et qu’il existe une ressource portant le nom spécifié, [!DNL Experience Manager] crée une nouvelle version de la ressource. |
| `versionLabel` | Chaîne | Facultatif | Si une version est créée, le libellé associé à la nouvelle version d’une ressource. |
| `versionComment` | Chaîne | Facultatif | Si une version est créée, les commentaires associés à la version. |
| `replace` | Booléen | Facultatif | Si `True` et qu’une ressource portant le nom spécifié existe, [!DNL Experience Manager] supprime la ressource, puis la recrée. |
| `uploadDuration` | Nombre | Facultatif | Durée totale (en millisecondes) nécessaire pour charger le fichier dans son intégralité. Si spécifié, la durée de chargement est incluse dans les fichiers journaux du système pour l’analyse du taux de transfert. |
| `fileSize` | Nombre | Facultatif | Taille, en octets, du fichier. Si spécifié, la taille du fichier est incluse dans les fichiers journaux du système pour l’analyse du taux de transfert. |

>[!NOTE]
>
>Si la ressource existe et que ni `createVersion` ni `replace` n’est spécifié, [!DNL Experience Manager] met à jour la version actuelle de la ressource avec le nouveau fichier binaire.

Comme c’est le cas pour le processus de lancement, les données de la requête de fin peuvent contenir des informations pour plusieurs fichiers.

Le processus de chargement d’un binaire n’est pas terminé tant que l’URL complète n’est pas appelée pour le fichier. Une ressource est traitée une fois le processus de chargement terminé. Le traitement ne commence pas même si le fichier binaire de la ressource est complètement chargé, mais que le processus de chargement n’est pas terminé. Si le téléchargement aboutit, le serveur répond avec un code d’état `200`.

### Exemple de script Shell pour charger des ressources dans AEM as a Cloud Service {#upload-assets-shell-script}

Le processus de chargement en plusieurs étapes pour un accès binaire direct dans AEM as a Cloud Service est illustré dans l’exemple de `aem-upload.sh` shell-script suivant :

```bash
#!/bin/bash

# Check if pv is installed
if ! command -v pv &> /dev/null; then
    echo "Error: 'pv' command not found. Please install it before running the script."
    exit 1
fi

# Check if jq is installed
if ! command -v jq &> /dev/null; then
    echo "Error: 'jq' command not found. Please install it before running the script."
    exit 1
fi

# Set DEBUG to true to enable debug statements
DEBUG=true

# Function for printing debug statements
function debug() {
    if [ "${DEBUG}" = true ]; then
        echo "[DEBUG] $1"
    fi
}

# Function to check if a file exists
function file_exists() {
    [ -e "$1" ]
}

# Function to check if a path is a directory
function is_directory() {
    [ -d "$1" ]
}

# Check if the required number of parameters are provided
if [ "$#" -ne 4 ]; then
    echo "Usage: $0 <aem-url> <asset-folder> <file-to-upload> <bearer-token>"
    exit 1
fi

AEM_URL="$1"
ASSET_FOLDER="$2"
FILE_TO_UPLOAD="$3"
BEARER_TOKEN="$4"

# Extracting file name or folder name from the file path
NAME=$(basename "${FILE_TO_UPLOAD}")

# Step 1: Check if "file-to-upload" is a folder
if is_directory "${FILE_TO_UPLOAD}"; then
    echo "Uploading files from the folder recursively..."
    
    # Recursively upload files in the folder
    find "${FILE_TO_UPLOAD}" -type f | while read -r FILE_PATH; do
        FILE_NAME=$(basename "${FILE_PATH}")
        debug "Uploading file: ${FILE_PATH}"
        
        # You can choose to initiate upload for each file here
        # For simplicity, let's assume you use the same ASSET_FOLDER for all files
        ./aem-upload.sh "${AEM_URL}" "${ASSET_FOLDER}" "${FILE_PATH}" "${BEARER_TOKEN}"
    done
else
    # "file-to-upload" is a single file
    FILE_NAME="${NAME}"

    # Step 2: Calculate File Size
    FILE_SIZE=$(stat -c %s "${FILE_TO_UPLOAD}")

    # Step 3: Initiate Upload
    INITIATE_UPLOAD_ENDPOINT="${AEM_URL}/content/dam/${ASSET_FOLDER}.initiateUpload.json"

    debug "Initiating upload..."
    debug "Initiate Upload Endpoint: ${INITIATE_UPLOAD_ENDPOINT}"
    debug "File Name: ${FILE_NAME}"
    debug "File Size: ${FILE_SIZE}"

    INITIATE_UPLOAD_RESPONSE=$(curl -X POST \
        -H "Authorization: Bearer ${BEARER_TOKEN}" \
        -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
        -d "fileName=${FILE_NAME}" \
        -d "fileSize=${FILE_SIZE}" \
        ${INITIATE_UPLOAD_ENDPOINT})

    # Continue with the rest of the script...
fi


# Check if the response body contains the specified HTML content for a 404 error
if echo "${INITIATE_UPLOAD_RESPONSE}" | grep -q "<title>404 Specified folder not found</title>"; then
    echo "Folder not found. Creating the folder..."

    # Attempt to create the folder
    CREATE_FOLDER_ENDPOINT="${AEM_URL}/api/assets/${ASSET_FOLDER}"

    debug "Creating folder..."
    debug "Create Folder Endpoint: ${CREATE_FOLDER_ENDPOINT}"

    CREATE_FOLDER_RESPONSE=$(curl -X POST \
        -H "Content-Type: application/json" \
        -H "Authorization: Bearer ${BEARER_TOKEN}" \
        -d '{"class":"'${ASSET_FOLDER}'","properties":{"title":"'${ASSET_FOLDER}'"}}' \
        ${CREATE_FOLDER_ENDPOINT})

    # Check the response code and inform the user accordingly
    STATUS_CODE_CREATE_FOLDER=$(echo "${CREATE_FOLDER_RESPONSE}" | jq -r '.properties."status.code"')
    case ${STATUS_CODE_CREATE_FOLDER} in
        201)
            echo "Folder created successfully. Initiating upload again..."

            # Retry Initiate Upload after creating the folder
            INITIATE_UPLOAD_RESPONSE=$(curl -X POST \
                -H "Authorization: Bearer ${BEARER_TOKEN}" \
                -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
                -d "fileName=${FILE_NAME}" \
                -d "fileSize=${FILE_SIZE}" \
                ${INITIATE_UPLOAD_ENDPOINT})
            ;;
        409)
            echo "Error: Folder already exists."
            ;;
        412)
            echo "Error: Precondition failed. Root collection cannot be found or accessed."
            exit 1
            ;;
        500)
            echo "Error: Internal Server Error. Something went wrong."
            exit 1
            ;;
        *)
            echo "Error: Unexpected response code ${STATUS_CODE_CREATE_FOLDER}"
            exit 1
            ;;
    esac
fi

# Extracting values from the response
FOLDER_PATH=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.folderPath')
UPLOAD_URIS=($(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].uploadURIs[]'))
UPLOAD_TOKEN=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].uploadToken')
MIME_TYPE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].mimeType')
MIN_PART_SIZE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].minPartSize')
MAX_PART_SIZE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].maxPartSize')
COMPLETE_URI=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.completeURI')

# Extracting "Affinity-cookie" from the response headers
AFFINITY_COOKIE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | grep -i 'Affinity-cookie' | awk '{print $2}')

debug "Folder Path: ${FOLDER_PATH}"
debug "Upload Token: ${UPLOAD_TOKEN}"
debug "MIME Type: ${MIME_TYPE}"
debug "Min Part Size: ${MIN_PART_SIZE}"
debug "Max Part Size: ${MAX_PART_SIZE}"
debug "Complete URI: ${COMPLETE_URI}"
debug "Affinity Cookie: ${AFFINITY_COOKIE}"
if $DEBUG; then
    i=1
    for UPLOAD_URI in "${UPLOAD_URIS[@]}"; do
        debug "Upload URI $i: "$UPLOAD_URI
        i=$((i+1))
    done
fi


# Calculate the number of parts needed
NUM_PARTS=$(( (FILE_SIZE + MAX_PART_SIZE - 1) / MAX_PART_SIZE ))
debug "Number of Parts: $NUM_PARTS"

# Calculate the part size for the last chunk
LAST_PART_SIZE=$(( FILE_SIZE % MAX_PART_SIZE ))
if [ "${LAST_PART_SIZE}" -eq 0 ]; then
    LAST_PART_SIZE=${MAX_PART_SIZE}
fi

# Step 4: Upload binary to the blob store in parts
PART_NUMBER=1
for i in $(seq 1 $NUM_PARTS); do
    PART_SIZE=${MAX_PART_SIZE}
    if [ ${PART_NUMBER} -eq ${NUM_PARTS} ]; then
        PART_SIZE=${LAST_PART_SIZE}
        debug "Last part size: ${PART_SIZE}"
    fi

    PART_FILE="/tmp/${FILE_NAME}_part${PART_NUMBER}"

    # Creating part file 
    SKIP=$((PART_NUMBER - 1))
    SKIP=$((MAX_PART_SIZE * SKIP))
    dd if="${FILE_TO_UPLOAD}" of="${PART_FILE}"  bs="${PART_SIZE}" skip="${SKIP}" count="${PART_SIZE}" iflag=skip_bytes,count_bytes  > /dev/null 2>&1
    debug "Creating part file: ${PART_FILE} with size ${PART_SIZE}, skipping first ${SKIP} bytes."

    
    UPLOAD_URI=${UPLOAD_URIS[$PART_NUMBER-1]}

    debug "Uploading part ${PART_NUMBER}..."
    debug "Part Size: $PART_SIZE"
    debug "Part File: ${PART_FILE}"
    debug "Part File Size: $(stat -c %s "${PART_FILE}")"
    debug "Upload URI: ${UPLOAD_URI}"

    # Upload the part in the background
    if command -v pv &> /dev/null; then
        pv "${PART_FILE}" | curl --progress-bar -X PUT --data-binary "@-" "${UPLOAD_URI}" &
    else
        curl -# -X PUT --data-binary "@${PART_FILE}" "${UPLOAD_URI}" &
    fi

    PART_NUMBER=$((PART_NUMBER + 1))
done

# Wait for all background processes to finish
wait

# Step 5: Complete the upload in AEM
COMPLETE_UPLOAD_ENDPOINT="${AEM_URL}${COMPLETE_URI}"

debug "Completing the upload..."
debug "Complete Upload Endpoint: ${COMPLETE_UPLOAD_ENDPOINT}"

RESPONSE=$(curl -X POST \
    -H "Authorization: Bearer ${BEARER_TOKEN}" \
    -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
    -H "Affinity-cookie: ${AFFINITY_COOKIE}" \
    --data-urlencode "uploadToken=${UPLOAD_TOKEN}" \
    --data-urlencode "fileName=${FILE_NAME}" \
    --data-urlencode "mimeType=${MIME_TYPE}" \
    "${COMPLETE_UPLOAD_ENDPOINT}")
    
debug $RESPONSE

echo "File upload completed successfully."
```

### Bibliothèque de chargement Open Source {#open-source-upload-library}

Pour en savoir plus sur les algorithmes de chargement ou pour créer vos propres scripts et outils de chargement, Adobe fournit des bibliothèques et des outils Open Source :

* [Bibliothèque de chargement AEM Open Source](https://github.com/adobe/aem-upload).
* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem).

>[!NOTE]
>
>La bibliothèque de téléchargement d’AEM et l’outil de ligne de commande utilisent tous deux la [bibliothèque node-httptransfer](https://github.com/adobe/node-httptransfer/)

### API de chargement de ressources obsolètes {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

La nouvelle méthode de chargement n’est prise en charge que pour [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]. Les API de [!DNL Adobe Experience Manager] 6.5 sont obsolètes. Les méthodes liées au chargement ou à la mise à jour de ressources ou de rendus (tout chargement de binaires) sont obsolètes dans les API suivantes :

* [API HTTP des ressources Experience Manager](mac-api-assets.md)
* `AssetManager` API Java, comme `AssetManager.createAsset(..)`, `AssetManager.createAssetForBinary(..)`, `AssetManager.getAssetForBinary(..)`, `AssetManager.removeAssetForBinary(..)`, `AssetManager.createOrUpdateAsset(..)`, `AssetManager.createOrReplaceAsset(..)`

>[!MORELIKETHIS]
>
>* [Bibliothèque de chargement AEM Open Source](https://github.com/adobe/aem-upload).
>* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem).
>* [Documentation Apache Jackrabbit Oak pour le chargement direct](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html#Upload).

## Workflows de traitement et de post-traitement des ressources {#post-processing-workflows}

Dans [!DNL Experience Manager], le traitement des ressources est basé sur la configuration des **[!UICONTROL Profils de traitement]** qui utilise des [microservices de ressources](asset-microservices-configure-and-use.md#get-started-using-asset-microservices). Le traitement ne nécessite pas d’extensions de développeur.

Pour la configuration du workflow de post-traitement, utilisez les workflows standard avec des extensions pour les étapes personnalisées.

## Prise en charge des étapes d’un workflow de post-traitement {#post-processing-workflows-steps}

Si vous effectuez une mise à niveau à partir d’une version précédente d’[!DNL Experience Manager], vous pouvez utiliser les microservices de ressources pour traiter les ressources. Les microservices de ressources natifs en mode cloud sont plus simples à configurer et à utiliser. Certaines étapes appliquées dans le workflow [!UICONTROL Ressource de mise à jour de la gestion des actifs numériques (DAM)] de la version précédente ne sont pas prises en charge. Pour plus d’informations sur les classes prises en charge, consultez [Référence de l’API Java ou Javadocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

Les modèles de workflow techniques suivants ont été remplacés par des microservices de ressources ou la prise en charge n’est pas disponible :

* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.switchengine.process.SwitchEngineHandlingProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`

<!-- Commenting the previous list documented at the time of GA. Replacing it with the updated list via cqdoc-18231.

* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.ScheduledPublishBPProcess`
* `com.day.cq.dam.core.process.ScheduledUnPublishBPProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
-->

<!-- PPTX source: slide in add-assets.md - overview of direct binary upload section of
https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

**Voir également**

* [Traduire les ressources](translate-assets.md)
* [API HTTP Assets](mac-api-assets.md)
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
>* [[!DNL Experience Cloud] as a [!DNL Cloud Service] SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).