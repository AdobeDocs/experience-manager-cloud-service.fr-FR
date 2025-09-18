---
title: Créer des composants personnalisés pour un formulaire EDS
description: Créer des composants personnalisés pour un formulaire EDS
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 2bbe3f95-d5d0-4dc7-a983-7a20c93e2906
source-git-commit: 9664495d17ad8a8101c886408bee1584b3d48f1e
workflow-type: tm+mt
source-wordcount: '2103'
ht-degree: 4%

---


# Création d’un composant de formulaire personnalisé dans un bloc de formulaire adaptatif

Edge Delivery Services pour AEM Forms offre des possibilités de personnalisation, ce qui permet aux développeurs et développeuses front-end de créer des composants de formulaire personnalisés. Ces composants personnalisés s’intègrent de manière transparente à l’expérience de création WYSIWYG, ce qui permet aux créateurs et créatrices de formulaires de les ajouter, de les configurer et de les gérer facilement dans l’éditeur de formulaires. Grâce aux composants personnalisés, les créateurs et créatrices peuvent améliorer leurs fonctionnalités tout en assurant un processus de création fluide et intuitif.

Ce document décrit les étapes à suivre pour créer des composants personnalisés en mettant en forme les composants de formulaire HTML natifs afin d’améliorer l’expérience client et l’attrait visuel du formulaire.

## Aperçu de l’architecture

Le composant personnalisé du bloc Forms suit un modèle d’architecture **MVC (Model-View-Controller)** :

### Modèle

- Défini par le schéma JSON pour chaque `field/component`.

- Les propriétés de création sont spécifiées dans le fichier JSON correspondant (voir blocs/form/models/form- components).

- Ces propriétés sont disponibles pour les auteurs dans le créateur de formulaires et transmises au composant dans le cadre de la définition de champ (fd).

### Mode

- La structure d’HTML pour chaque type de champ est décrite dans form-field-types.

- Il s’agit de la structure de base de votre composant, qui peut être étendue ou modifiée.

- La structure HTML de base pour chaque composant prêt à l’emploi est documentée dans form-field-types.

### Logique de contrôleur/composant

- Implémenté dans JavaScript, en tant que composants prêts à l’emploi ou personnalisés.  - Situé dans `blocks/form/components` pour les composants personnalisés.

## Composants d’usine

Les composants prêts à l’emploi **OOTB)** qui constituent la base du développement personnalisé :

- Les composants prêts à l’emploi se trouvent dans `blocks/form/models/form-components`.

- Chaque composant prêt à l’emploi comporte un fichier JSON définissant ses propriétés modifiables (par exemple, ` _text-input.json`,`_drop-down.json`).

- Ces propriétés sont disponibles pour les auteurs dans le créateur de formulaires et sont transmises au composant dans le cadre de la définition du champ (fd).

- La structure HTML de base pour chaque composant prêt à l’emploi est documentée dans form-field-types.

L’extension d’un composant prêt à l’emploi existant vous permet de réutiliser sa structure de base, son comportement et ses propriétés tout en le personnalisant en fonction de vos besoins.

- Les composants personnalisés doivent s’étendre à partir d’un ensemble prédéfini de composants prêts à l’emploi.

- Le système identifie le composant prêt à l’emploi à étendre en fonction de la propriété `viewType` dans le fichier JSON du champ.

- Le système conserve un registre des variantes autorisées des composants personnalisés. Seules les variantes répertoriées dans ce registre peuvent être utilisées, par exemple, `customComponents[]` dans `mappings.js`.

- Lors du rendu d’un formulaire, le système vérifie la propriété ou la `:type/fd:viewType` de variante et, si elle correspond à un composant personnalisé enregistré, charge les fichiers JS et CSS correspondants à partir du dossier `blocks/form/components`.

- Le composant personnalisé est ensuite appliqué à la structure HTML de base du composant prêt à l’emploi, ce qui vous permet d’améliorer ou de remplacer son comportement et son apparence.

## Structure du composant personnalisé

Pour créer des composants personnalisés, vous pouvez utiliser l’interface de ligne de commande **Scaffolder CLI** afin de configurer les fichiers et les dossiers requis pour votre composant, puis d’ajouter du code pour votre composant personnalisé.

- Les composants personnalisés résident dans le dossier `blocks/form/components`.

- Chaque composant personnalisé doit être placé dans son propre dossier, nommé en fonction du composant (cartes, par exemple). Dans le dossier , les fichiers suivants doivent être :

   - **_cards.json** - Fichier JSON qui étend la définition de composant d’un composant prêt à l’emploi, définit ses propriétés de création (modèles[]) et sa structure de contenu au chargement (définitions[].
   - **cards.js** - Fichier JavaScript contenant la logique principale.
   - **cards.css** - facultatif, pour les styles.

- Le nom du dossier et les fichiers JS/CSS doivent correspondre.

### Réutilisation et extension de champs dans des composants personnalisés

Lors de la définition de champs dans le fichier JSON de votre composant personnalisé (pour n’importe quel groupe de champs, de base, de validation, d’aide, etc.), suivez ces bonnes pratiques en matière de maintenabilité et de cohérence :

- Réutilisez les champs standard/partagés en référençant les conteneurs partagés existants ou les définitions de champ (par exemple, `../form-common/_basic-input-placeholder-fields.json#/fields`, `../form-common/_basic- validation-fields.json#/fields`). Vous hériterez ainsi de toutes les options standard sans les dupliquer.

- Ajoutez uniquement des champs nouveaux ou personnalisés explicitement dans votre conteneur . Votre schéma reste ainsi SEC et ciblé.

- Supprimez ou évitez de dupliquer des champs déjà inclus via des références. Ne définissez que les champs qui sont uniques à la logique de votre composant.

- Référencez les conteneurs d’aide et tout autre contenu partagé (par exemple, `../form-common/_help-container.json`) selon les besoins pour garantir la cohérence et la facilité de maintenance.

>[!TIP]
>
> - Ce modèle facilite la mise à jour ou l’extension de la logique à l’avenir et garantit que vos composants personnalisés restent cohérents avec le reste du système de formulaires.
> - Recherchez toujours des conteneurs partagés existants ou des définitions de champ avant d’en ajouter de nouvelles.

### Définition de nouvelles propriétés pour les composants personnalisés

- Si vous devez capturer de nouvelles propriétés pour votre composant personnalisé à partir des auteurs, vous pouvez le faire en définissant un champ dans le tableau `fields[]` du composant dans le fichier JSON du composant.

- Le composant personnalisé est identifié à l’aide de la propriété :type , qui peut être définie comme `fd:viewType` dans le fichier JSON (par exemple, `fd:viewType: cards`). Cela permet au système de reconnaître et de charger le composant personnalisé approprié. Cela est donc obligatoire pour les composants personnalisés

- Toutes les nouvelles propriétés ajoutées dans la définition JSON sont disponibles dans la définition de champ en tant que propriétés. `<propertyName>` dans la logique JS de votre composant

## API JavaScript de composant personnalisé

L’API JavaScript de composant personnalisé définit comment contrôler le comportement, l’apparence et la réactivité de votre composant de formulaire personnalisé.

### Fonction de décoration

La fonction **decoration** est le point d’entrée de votre composant personnalisé. Il initialise le composant, le lie à sa définition JSON et vous permet de manipuler sa structure et son comportement HTML.

>[!NOTE]
>
> Le fichier JavaScript du composant personnalisé doit exporter une fonction par défaut en tant que décoration :

#### Signature de fonction :

```javascript
export default function decorate(element, fieldJson, container, formId) 
{
  // element: The HTML structure of the OOTB component you are extending
  // fieldJson: The JSON field definition (all authorable properties)
  // container: The parent element (fieldset or form)
  // formId: The id of the form

  // ... your logic here ...
}
```

Il peut :

- **Modifier l’élément** : ajoutez des écouteurs d’événement, mettez à jour des attributs ou injectez des balises supplémentaires.

- **Accéder aux propriétés JSON** : utilisez `fd.properties.<propertyName>` pour lire les valeurs définies dans le schéma JSON et les appliquer dans la logique du composant.

## Fonction d&#39;abonnement

La fonction **subscribe** permet à votre composant de réagir aux modifications des valeurs de champ ou des événements personnalisés. Cela garantit que le composant reste synchronisé avec le modèle de données du formulaire et peut mettre à jour dynamiquement son interface utilisateur.

### Signature de fonction :

```javascript
import { subscribe } from '../../rules/index.js';
export default function decorate(fieldDiv, fieldJson, container, formId) {
  // Access custom properties defined in the JSON
  const { initialText, finalText, time } = fieldJson?.properties;

  // ... setup logic ...

  subscribe(fieldDiv, formId, (_fieldDiv, fieldModel) => {
    fieldModel.subscribe(() => {
      // React to custom event (e.g., resetCardOption)
      // ... logic ...
    }, 'resetCardOption');
  });
}
```

Il peut :

- **Enregistrer un rappel** : l’appel **subscribe(element, formId, callback)** enregistre votre rappel à exécuter chaque fois que les données du champ changent. Utilisez deux paramètres de rappel :
   - **element** : élément HTML représentant le champ.
   - **fieldModel** : objet représentant l’API d’état et d’événement du champ.

- **Écouter les modifications ou les événements** : utilisez `fieldModel.subscribe((event) => { ... }, 'eventName')` pour exécuter la logique chaque fois qu’une valeur change ou qu’un événement personnalisé est déclenché. L’objet d’événement contient des détails sur les modifications apportées.

## Création d’un composant personnalisé

Dans cette section, vous découvrirez le processus de création d’un composant personnalisé **cartes de visite** en étendant le composant de bouton radio prêt à l’emploi.

![Composant personnalisé Carte](/help/edge/docs/forms/universal-editor/assets/cc-ue-card-component.png)

### &#x200B;1. Configuration du code

#### 1.1 Fichiers et dossiers

La première étape consiste à configurer les fichiers nécessaires du composant personnalisé et à le connecter au code dans le référentiel. Ce processus est effectué automatiquement par l’**interface de ligne de commande d’AEM Forms Scaffolder**, ce qui accélère la génération de modèles et le câblage des fichiers nécessaires.

>[!VIDEO](https://video.tv.adobe.com/v/3474752)

1. Ouvrez le terminal et accédez à la racine de votre projet de formulaire.
2. Exécutez les commandes suivantes :

```bash
npm install
npm run create:custom-component
```

![Interface de ligne de commande du modèle automatique](/help/edge/docs/forms/universal-editor/assets/scaffolder-cli.png)

Il permettra :

- **Vous inviter à nommer** votre nouveau composant. Par exemple, dans ce cas, utilisez des cartes.
- **Vous demander de choisir** un composant de base (sélectionner un groupe de cases d’option)

Cela crée tous les dossiers et fichiers nécessaires, notamment :

```
blocks/form/
└── components/
  └── cards/
    ├── cards.js
    └── cards.css
    └── _cards.json
```

et le connecte avec le reste du code du référentiel, comme indiqué dans la sortie de l’interface de ligne de commande.
Il exécute automatiquement les fonctionnalités ci-dessous :

- Ajoute des cartes aux filtres pour permettre l’ajout dans le bloc de formulaire adaptatif.
- Met à jour la place sur la liste autorisée de `mappings.js` pour inclure le nouveau composant Cartes.
- Enregistre la définition du composant Cartes sous la liste **Composants personnalisés** dans l’éditeur universel.

>[!NOTE]
>
> Vous pouvez également créer un composant personnalisé à l’aide de la méthode manuelle (héritée). Pour plus d’informations, consultez la section [Méthode manuelle ou héritée](#manual-or-legacy-method-to-create-custom-component) pour créer un composant personnalisé.

#### 1.2 Utilisation du composant dans l’éditeur universel

1. **Actualiser l’éditeur universel** : ouvrez votre formulaire dans l’éditeur universel et actualisez la page pour vous assurer qu’elle charge le code le plus récent du référentiel.

2. **Ajouter le composant personnalisé**

   1. Cliquez sur le bouton **Ajouter (+)** dans la zone de travail du formulaire.
   2. Faites défiler l’écran jusqu’à la section Composants personnalisés .
   3. Sélectionnez le nouveau composant **Cartes** pour l’insérer dans votre formulaire.

      ![Sélectionner le composant personnalisé](/help/edge/docs/forms/universal-editor/assets/select-custom-component.png)

Comme aucun code n’est présent à l’intérieur `cards.js` le composant personnalisé est rendu en tant que groupe de cases d’option.

#### 1.3 Prévisualiser et tester localement

Maintenant que le formulaire contient le composant personnalisé, vous pouvez remplacer le formulaire et y apporter des modifications localement pour voir les modifications :

1. Accédez à votre terminal et exécutez `aem up`.

2. Ouvrez le serveur proxy démarré à l’adresse `http://localhost:3000/{path-to-your-form}` (exemple de chemin : `/content/forms/af/custom-component-form`)


### &#x200B;2. Mise en œuvre du comportement personnalisé de votre composant personnalisé

#### 2.1 Style du composant personnalisé

Ajoutons une classe **card** au composant pour le style et ajoutez une image pour chaque radio. Utilisez le code ci-dessous pour cela.

**Mettre en forme le composant à l’aide de card.js**

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';

export default function decorate(element, fieldJson, container, formId) {
  element.classList.add('card');

  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper) => {
    const image = createOptimizedPicture(
      'https://main--afb--jalagari.hlx.live/lab/images/card.png',
      'card-image'
    );
    radioWrapper.appendChild(image);
  });

  return element;
}
```

**Ajouter un comportement d’exécution à l’aide de cards.css**

```javascript
.card .radio-wrapper {
  min-width: 320px; /* or whatever width fits your design */
  max-width: 340px;
  background: #fff;
  border-radius: 16px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  flex: 0 0 auto;
  scroll-snap-align: start;
  padding: 24px 16px;
  margin-bottom: 0;
  position: relative;
  transition: box-shadow 0.2s;
  display: flex;
  align-items: flex-start;
  gap: 12px;
}
```

Désormais, le composant Cartes se présente comme suit :

![ajout de cartes css et js](/help/edge/docs/forms/universal-editor/assets/add-card-css.png)

#### 2.2 Ajout d’un comportement dynamique à l’aide de la fonction d’abonnement

Lorsque la liste déroulante est modifiée, les cartes sont récupérées et définies dans l’énumération du groupe de cases d’option. Mais actuellement, la vue ne gère pas cela. Il effectue donc le rendu comme illustré ci-dessous :

![fonction subscribe](/help/edge/docs/forms/universal-editor/assets/card-subscribe.png)

Lorsque l’API est appelée, elle définit le modèle de champ et doit écouter les modifications et effectuer le rendu de la vue en conséquence. Pour ce faire, utilisez la fonction **subscribe**.

Convertissons le code d’affichage de l’étape précédente en une fonction et appelons-le dans la fonction subscribe dans `cards.js` comme illustré ci-dessous :

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';
import { subscribe } from '../../rules/index.js';

function createCard(element, enums) {
  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper, index) => {
    if (enums[index]?.name) {
      let label = radioWrapper.querySelector('label');

      if (!label) {
        label = document.createElement('label');
        radioWrapper.appendChild(label);
      }

      label.textContent = enums[index]?.name;
    }

    const image = createOptimizedPicture(
      enums[index]?.image || 'https://main--afb--jalagari.hlx.page/lab/images/card.png',
      'card-image'
    );

    radioWrapper.appendChild(image);
  });
}

export default function decorate(element, fieldJson, container, formId) {
  element.classList.add('card');
  createCard(element, fieldJson.enum);

  subscribe(element, formId, (fieldDiv, fieldModel) => {
    fieldModel.subscribe((e) => {
      const { payload } = e;

      payload?.changes?.forEach((change) => {
        if (change?.propertyName === 'enum') {
          createCard(element, change.currentValue);
        }
      });
    });
  });

  return element;
}
```

**Utilisez la fonction Subscribe pour écouter les changements d’événement dans cards.js**

Désormais, lorsque vous modifiez la liste déroulante, les cartes sont renseignées comme illustré ci-dessous :

![fonction subscribe](/help/edge/docs/forms/universal-editor/assets/card-subscribe-final.png)

#### 2.3 Synchronisation des mises à jour des vues avec le modèle de champ

Pour synchroniser les modifications de la vue avec le modèle de champ, vous devez définir la valeur de la carte sélectionnée. Ajoutez donc l’écouteur d’événement de modification suivant dans cards.js, comme illustré ci-dessous :

**Utilisation de l’API de modèle de champ dans cards.js**

```javascript
import { createOptimizedPicture } from '../../../../scripts/aem.js';
import { subscribe } from '../../rules/index.js';

function createCard(element, enums) {
  element.querySelectorAll('.radio-wrapper').forEach((radioWrapper, index) => {
    if (enums[index]?.name) {
      let label = radioWrapper.querySelector('label');

      if (!label) {
        label = document.createElement('label');
        radioWrapper.appendChild(label);
      }

      label.textContent = enums[index]?.name;
    }

    // Attach index to input element for later reference
    radioWrapper.querySelector('input').dataset.index = index;

    const image = createOptimizedPicture(
      enums[index]?.image || 'https://main--afb--jalagari.hlx.page/lab/images/card.png',
      'card-image'
    );

    radioWrapper.appendChild(image);
  });
}

export default function decorate(element, fieldJson, container, formId) {
  element.classList.add('card');
  createCard(element, fieldJson.enum);

  subscribe(element, formId, (fieldDiv, fieldModel) => {
    fieldModel.subscribe((e) => {
      const { payload } = e;

      payload?.changes?.forEach((change) => {
        if (change?.propertyName === 'enum') {
          createCard(element, change.currentValue);
        }
      });
    });

    element.addEventListener('change', (e) => {
      e.stopPropagation();
      const value = fieldModel.enum?.[parseInt(e.target.dataset.index, 10)];
      fieldModel.value = value.name;
    });
  });

  return element;
}
```

Le composant de carte personnalisée s’affiche maintenant, comme illustré ci-dessous :

![Composant personnalisé Carte](/help/edge/docs/forms/universal-editor/assets/cc-ue-card-component.png)

### &#x200B;3. Valider et envoyer les modifications

Une fois que vous avez implémenté le JavaScript et le CSS de votre composant personnalisé et que vous l’avez vérifié localement, validez et transmettez les modifications à votre référentiel Git.

```bash
git add . && git commit -m "Add card custom component" && git push
```

Vous avez créé un composant de sélection de carte personnalisée complexe en quelques étapes simples.

+++ **Méthode manuelle ou héritée pour créer un composant personnalisé**

Pour ce faire, l’ancienne méthode consiste à suivre manuellement les étapes décrites ci-dessous :

1. **Choisissez un composant prêt à l’emploi** à étendre (par exemple, bouton, liste déroulante, saisie de texte, etc.). Dans ce cas, étendez le composant radio.

2. **Créez un dossier** en `blocks/form/components` avec le nom de votre composant (cartes dans ce cas).

3. **Ajoutez un fichier JS** portant le même nom :
   - `blocks/form/components/cards/cards.js`.

4. (Facultatif) **Ajoutez un fichier CSS** pour les styles personnalisés :
   - `blocks/form/components/cards/cards.css.`

5. **Définissez un nouveau fichier JSON** (par exemple, ` _cards.json`) dans le même dossier que votre **fichier JS de composant** (`blocks/form/components/cards/_cards.json`). Ce fichier JSON doit étendre un composant existant et, dans ses définitions, `fd:viewType` au nom de votre composant (cartes dans ce cas) :

   - Pour tous les groupes de champs (de base, de validation, d’aide, etc.), ajoutez explicitement vos champs personnalisés.

6. **Implémentez la logique JS et CSS :**
   - Exportez une fonction par défaut comme décrit ci-dessus.
   - Utilisez le paramètre **element** pour modifier la structure de base d&#39;HTML.
   - Utilisez le paramètre **fieldJson** si nécessaire pour les données de champ standard.
   - Utilisez la fonction **subscribe** pour écouter les modifications de champ ou les événements personnalisés si nécessaire.

     >[!NOTE]
     >
     >Implémentez la logique JS et CSS de votre composant personnalisé comme expliqué ci-dessus.

7. Enregistrez votre composant en tant que variante dans le créateur de formulaires et définissez la propriété de variante ou
   `fd:viewType/:type` dans le fichier JSON au nom de votre composant, par exemple, ajoutez la valeur `fd:viewType` du `definitions[]` sous forme de cartes au tableau de composants de l’objet avec `id="form`.

   ```
       {
     "definitions": [
       {
         "title": "Cards",
         "id": "cards",
         "plugins": {
           "xwalk": {
             "page": {
               "resourceType": "core/fd/components/form/radiobutton/v1/radiobutton",
               "template": {
                 "jcr:title": "Cards",
                 "fieldType": "radio-button",
                 "fd:viewType": "cards",
                 "enabled": true,
                 "visible": true
               }
             }
           }
         }
       }
     ]
   }
   ```

8. **Mettre à jour mappings.js** : ajoutez le nom de votre composant à la liste **OOTBComponentDecorators** (pour les composants de style OOTB) ou **customComponents** afin qu’il soit reconnu et chargé par le système.

   ```javascript
   let customComponents = ["cards"];
   const OOTBComponentDecorators = [];
   ```

9. **Mettre à jour _form.json** : ajoutez le nom de votre composant au tableau `filters.components` pour le déposer dans l’interface utilisateur de création.

   ```javascript
   "filters": [
   {
       "id": "form",
       "components": [ "cards"]}
       ]
   ```

10. **Mettre à jour _component-definition.json** : dans `models/_component-definition.json`, mettez à jour le tableau au sein du groupe avec `id custom-components` avec un objet de la manière suivante :

   ```javascript
   {
   "...":"../blocks/form/components/cards/_cards.json#/definitions"
   }
   ```

   Cela permet de fournir la référence au nouveau composant de cartes à créer avec le reste des composants

11. **Exécutez le script build:json** : exécutez `npm run build:json` pour compiler et fusionner toutes les définitions JSON des composants dans un seul fichier à diffuser à partir du serveur. Cela garantit que le schéma de votre nouveau composant est inclus dans la sortie fusionnée.

12. Validez et transmettez vos modifications à votre référentiel Git.

Vous pouvez maintenant ajouter le composant personnalisé à votre formulaire.

+++

## Création d’un composant composite

Un composant composite est créé en combinant plusieurs composants.
Par exemple, un composant composite de conditions générales se compose d’un panneau parent qui contient les éléments suivants :

- Champ de texte brut pour afficher les termes

- Case à cocher permettant de capturer le contrat de l’utilisateur

Cette structure de composition est définie comme modèle à l’intérieur du fichier JSON du composant correspondant. L’exemple suivant montre comment définir un modèle pour un composant Termes et conditions :

```javascript
{
  "definitions": [
    {
      "title": "Terms and conditions",
      "id": "tnc",
      "plugins": {
        "xwalk": {
          "page": {
            "resourceType": "core/fd/components/form/termsandconditions/v1/termsandconditions",
            "template": {
              "jcr:title": "Terms and conditions",
              "fieldType": "panel",
              "fd:viewType": "tnc",
              "text": {
                "value": "Text related to the terms and conditions come here.",
                "sling:resourceType": "core/fd/components/form/text/v1/text",
                "fieldType": "plain-text",
                "textIsRich": true
              },
              "approvalcheckbox": {
                "name": "approvalcheckbox",
                "jcr:title": "I agree to the terms & conditions.",
                "sling:resourceType": "core/fd/components/form/checkbox/v1/checkbox",
                "fieldType": "checkbox",
                "required": true,
                "type": "string",
                "enum": [
                  "true"
                ]
              }
            }
          }
        }
      }
    }
  ],
  ...
}
```

## Bonnes pratiques

Gardez les points suivants à l’esprit avant de créer votre propre composant personnalisé :

- **Gardez la logique de votre composant concentrée** : ajoutez/remplacez uniquement ce qui est nécessaire à votre comportement personnalisé

- **Tirer parti de la structure de base** : utilisez l’HTML prête à l’emploi comme point de départ

- **Utiliser des propriétés modifiables :** expose les options configurables via le schéma JSON.

- **Espace de noms de votre CSS** : évitez les collisions de styles en utilisant des noms de classe uniques

## Références

- [form-field-types](/help/edge/docs/forms/eds-form-field-properties.md) : structures et propriétés HTML de base pour tous les types de champ.

- **blocs/form/models/form-components** : définitions des propriétés de composants prêts à l’emploi et personnalisés.

- **blocs/formulaire/composants** : placez pour vos composants personnalisés. Par exemple : `blocks/form/components/countdown-timer/_countdown-timer.json` montre comment étendre un composant de base et ajouter de nouvelles propriétés.
