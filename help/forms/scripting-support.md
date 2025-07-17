---
title: Prise en charge des scripts pour les formulaires HTML5
description: JavaScript, propriétés FormCalc et autres méthodes prises en charge dans les formulaires HTML5.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
feature: HTML5 Forms,Mobile Forms
exl-id: bcb5afc5-2190-4269-aba2-63842db9df3f
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '3916'
ht-degree: 100%

---

# Prise en charge des scripts pour les formulaires HTML5 {#scripting-support-for-html-forms}

Les propriétés JavaScript, FormCalc et les méthodes prises en charge dans les formulaires HTML5 sont les suivantes :

## $event {#event}

<table>
 <tbody>
  <tr>
   <th>Propriété </th>
   <th>Description<br /> </th>
   <th>Exception</th>
  </tr>
  <tr>
   <td><code>prevText</code></td>
   <td>Indique le contenu du champ une fois qu’il a été modifié suite aux actions de l’utilisateur ou utilisatrice. Il est possible de rappeler cette valeur de manière similaire à une fonction d’annulation.</td>
   <td><p>Ne fonctionne pas sur les menus déroulants et les zones de liste. <code>PrevText </code> ne fonctionne pas correctement dans les cas suivants :</p>
    <ul>
     <li>Lorsque vous appuyez sur certaines touches de caractères spéciaux (par exemple $, &amp;, ou @, etc.) dans les champs numériques sur l’iPad, et </li>
     <li>Pour le champ de date (lorsque la date est saisie via le calendrier).<br /> </li>
    </ul> <p>La configuration de la valeur à l’aide du script n’est pas prise en charge.</p> </td>
  </tr>
  <tr>
   <td><code>target</code></td>
   <td>Indique l’objet sur lequel l’événement a une influence.</td>
   <td>La configuration de la valeur à l’aide du script n’est pas prise en charge.<br /> </td>
  </tr>
  <tr>
   <td><code>newtext</code></td>
   <td>Indique le contenu du champ une fois qu’il a été modifié suite aux actions de l’utilisateur.</td>
   <td><p>La propriété <code>newText</code> ne fonctionne pas correctement dans les cas suivants :</p>
    <ul>
     <li>Lorsque vous sélectionnez des textes de remplacement.</li>
     <li>Lorsque vous supprimez, copiez et collez des textes.</li>
     <li>Lorsque vous appuyez sur certaines touches de caractères spéciaux (par exemple, $, &amp; ou @ etc.) dans les champs numériques.<br /> </li>
     <li>Lorsque vous utilisez la combinaison Maj + caractère alphanumérique. </li>
     <li>Lorsque vous utilisez des champs de date et heure</li>
    </ul>
    <div>
      La configuration de la valeur à l’aide du script n’est pas prise en charge.
    </div> </td>
  </tr>
  <tr>
   <td>change</td>
   <td>Indique la valeur saisie ou collée par un utilisateur ou une utilisatrice dans un champ immédiatement après avoir effectué l’action. </td>
   <td><p>La propriété de modification ne fonctionne pas correctement pour les cas suivants :</p>
    <ul>
     <li>Lorsque vous sélectionnez des textes de remplacement.</li>
     <li>Lorsque vous supprimez, copiez et collez des textes.</li>
     <li>Lorsque vous appuyez sur certaines touches de caractères spéciaux (par exemple, $, &amp; ou @ etc.) dans les champs numériques.<br /> </li>
     <li>Lorsque vous utilisez la combinaison Maj + caractère alphanumérique. </li>
     <li>Lorsque vous utilisez des champs de date et heure</li>
    </ul> <p>La configuration de la valeur à l’aide du script n’est pas prise en charge.</p> </td>
  </tr>
  <tr>
   <td>keydown</td>
   <td>Détermine si un utilisateur ou une utilisatrice appuie sur une touche fléchée pour effectuer une sélection. Cette propriété est disponible uniquement pour les zones de liste et les listes déroulantes.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>modifier</td>
   <td>Détermine l’utilisation de la touche de modification (par exemple, Ctrl sous Microsoft® Windows®) lors de l’exécution d’un événement particulier.</td>
   <td>Aucune</td>
  </tr>
 </tbody>
</table>

### $host {#host}

<table>
 <tbody>
  <tr>
   <th>Propriété</th>
   <th>Description</th>
   <th>Exception</th>
  </tr>
  <tr>
   <td><code>apptype</code></td>
   <td>Retourne le type d’application de l’hôte. Uniquement disponible pour les applications clientes.</td>
   <td>Renvoie <code>HTML 5</code>.</td>
  </tr>
  <tr>
   <td><code>name</code></td>
   <td>Renvoie le nom de l’application active.</td>
   <td>Renvoie le nom du navigateur et sa version. Par exemple, dans le navigateur Chrome, la valeur renvoyée est <code>Chrome &lt;version&gt;.</code></td>
  </tr>
  <tr>
   <td><code>numPages</code></td>
   <td>Renvoie le nombre de pages que compte le document.</td>
   <td>La politique de pagination des formulaires HTML5 n’est pas identique à celle des formulaires PDF. Les API numPages peuvent renvoyer des valeurs différentes dans les deux cas.</td>
  </tr>
  <tr>
   <td><code>platform</code></td>
   <td>Renvoie une chaîne représentant la plateforme de l’ordinateur qui exécute le script.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>title</code></td>
   <td>Indique le titre du document. Cette méthode est uniquement disponible pour les applications clientes.</td>
   <td>Elle renvoie le titre du document HTML dans un formulaire plutôt que le titre des métadonnées du formulaire comme dans le cas de formulaires PDF.</td>
  </tr>
  <tr>
   <td><code>version</code></td>
   <td>Renvoie une chaîne représentant le numéro de version de l’application active.</td>
   <td>Elle renvoie la version du formulaire.</td>
  </tr>
  <tr>
   <td><code>calculationsEnabled</code></td>
   <td>Indique si les scripts de calcul seront exécutés ou non.<br /> </td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>validationsEnabled</code></td>
   <td>Indique si les scripts de validation seront exécutés ou non.<br /> </td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>pageUp</code></td>
   <td>Permet de revenir à la page précédente.</td>
   <td>Les formulaires HTML5 ne suivent pas la même politique de pagination qu’un formulaire PDF, la page précédente d’un formulaire HTML5 est donc différente de la page précédente d’un formulaire PDF.</td>
  </tr>
  <tr>
   <td><code>pageDown</code></td>
   <td>Atteint la page suivante d’un formulaire. Utilisez la méthode pageDown au moment de l’exécution.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>setFocus</code></td>
   <td>Définit le focus du clavier sur le champ spécifié. Le champ est indiqué sous la forme d’un objet ou par l’expression SOM du champ. Cette méthode est uniquement disponible pour les applications clientes.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>resetdata</code></td>
   <td>Rétablit les valeurs par défaut des champs dans un document.</td>
   <td>Efface toutes les données d’un formulaire en les remplaçant par les données fusionnées plutôt qu’en restaurant les valeurs par défaut.</td>
  </tr>
  <tr>
   <td><code>messageBox</code></td>
   <td>Affiche à l’écran une boîte de dialogue. Cette méthode est uniquement disponible pour les applications clientes.</td>
   <td>La boîte de message de type Oui/Non est convertie en OK/Annuler. La boîte de message avec trois boutons n’est pas prise en charge.</td>
  </tr>
  <tr>
   <td>currentPage</td>
   <td><p>Définit la page active d’un document lors de l’exécution.</p> <p>Les valeurs de page sont de base 0, de sorte que la première page d’un document renvoie la valeur 0.</p> <p>La propriété currentPage est disponible lorsque layout:ready s’exécute sur un client. En revanche, elle n’est pas disponible lorsque l’événement layout:ready s’exécute sur le serveur, car l’exécution de la propriété doit être précédée par celle de la disposition du formulaire.</p> </td>
   <td>Aucune</td>
  </tr>
 </tbody>
</table>

### field {#field}

<table>
 <tbody>
  <tr>
   <th><strong><span>Propriété</span></strong></th>
   <th><strong><span>Description<br /> </span></strong></th>
   <th><strong><span>Exception</span></strong></th>
  </tr>
  <tr>
   <td><code>presence</code></td>
   <td>Contrôle la participation de l’objet associé dans différentes phases de traitement. Si l’objet est un conteneur, le contenu du conteneur hérite des restrictions que cette commande applique.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>access</code></td>
   <td>Définit l’accès de l’utilisateur ou de l’utilisatrice au contenu.</td>
   <td>Ne fonctionne pas pour le groupe d’exclusion. De plus, les formulaires HTML5 traitent de la même façon les objets non interactifs et protégés.<br /> </td>
  </tr>
  <tr>
   <td><code>name</code></td>
   <td>Identificateur utilisé pour identifier cet élément dans les expressions de script.</td>
   <td>Les formulaires HTML5 ne permettent pas de définir la propriété de nom des objets. Il s’agit de la propriété en lecture seule pour les formulaires HTML5.</td>
  </tr>
  <tr>
   <td><code>value</code></td>
   <td>Élément de contenu qui inclut une unité unique du contenu de données.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>rawValue</code></td>
   <td>Indique la valeur non formatée de ce champ.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>formattedValue</code></td>
   <td>Indique la valeur formatée de ce champ.</td>
   <td>La configuration de <code>formattedValue</code> dans le script n’est pas prise en charge.</td>
  </tr>
  <tr>
   <td><code>editValue</code></td>
   <td>Indique la valeur de modification de ce champ.</td>
   <td>La configuration de <code>editValue </code> dans le script n’est pas prise en charge.</td>
  </tr>
  <tr>
   <td><code>formatMessage</code></td>
   <td>Indique la chaîne de message pour la validation du format pour ce champ.</td>
   <td>La configuration de <code>formatMessage </code> dans le script n’est pas prise en charge.</td>
  </tr>
  <tr>
   <td><code>fillcolor</code></td>
   <td>Indique la valeur de la couleur d’arrière-plan de ce champ. Vous devez définir la propriété border.fill.presence pour l’afficher séparément.</td>
   <td>La couleur par défaut du champ n’est pas correctement renvoyée.</td>
  </tr>
  <tr>
   <td><code>border</code></td>
   <td>L’objet border décrit la bordure entourant un objet.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>ui</code></td>
   <td>L’objet ui renferme la description d’interface utilisateur d’un objet de formulaire.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>mandatory</code></td>
   <td>Indique la valeur nullTest pour le champ.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>borderColor</code></td>
   <td>Indique la valeur de la couleur de la bordure pour ce champ. Vous devez définir la propriété border.edge.presence pour l’afficher séparément.</td>
   <td>La couleur de la bordure par défaut du champ n’est pas correctement renvoyée.</td>
  </tr>
  <tr>
   <td><code>length</code></td>
   <td>Le nombre d’éléments dans la liste.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>addItem</code></td>
   <td>Ajoute de nouveaux éléments au champ actuel.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>clearItem</code></td>
   <td>Supprime tous les éléments du champ.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>boundItem</code></td>
   <td>Obtient la valeur liée d’un élément d’affichage spécifique dans une liste déroulante ou une zone de liste.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>execCalculate</code></td>
   <td>Exécute le script de calcul du champ.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>execValidate</code></td>
   <td>Exécute le script de validation du champ.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>execEvent</code></td>
   <td>Exécute le script d’événement de l’objet.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>getItemState</code></td>
   <td>Renvoie l’état de sélection de l’élément spécifié.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>setItemState</code></td>
   <td>Définit l’état de sélection de l’élément spécifié.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>getDisplayItem</code></td>
   <td>Récupère le texte d’affichage de l’élément pour l’index d’élément spécifié.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>getSaveItem</code></td>
   <td>Récupère la valeur de données pour l’index d’élément spécifié.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>deleteItem</code></td>
   <td>Supprime l’élément à l’index spécifié.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td><code>setItems</code></td>
   <td>Définit les éléments spécifiés dans le champ actuel. Remplace les éléments préexistants.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>h</td>
   <td>Mesure de la hauteur pour la disposition.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>w</td>
   <td>Mesure indiquant la largeur pour la disposition.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Indique la coordonnée x du point d’ancrage du conteneur par rapport au coin supérieur gauche du conteneur parent lors d’un placement avec une disposition positionnée.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Indique la coordonnée y du point d’ancrage d’un conteneur par rapport au coin supérieur gauche du conteneur parent lors d’un placement avec une disposition positionnée.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>caption</td>
   <td>L’objet caption décrit un libellé descriptif associé à un objet de conception de formulaire.<br /> </td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>L’objet validate contrôle la validation des données fournies par l’utilisateur ou l’utilisatrice sur un formulaire. L’objet validate peut être activé plusieurs fois pendant la durée de vie d’un formulaire.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>parentSubform</td>
   <td>Indique le sous-formulaire (page) parent de ce champ.</td>
   <td>Renvoie toujours le sous-formulaire parent au lieu de renvoyer le premier sous-formulaire parent hors portée.<br /> </td>
  </tr>
  <tr>
   <td>selectedIndex</td>
   <td>Index du premier élément sélectionné.</td>
   <td>Aucune</td>
  </tr>
 </tbody>
</table>

## Formulaire {#form}

| **Propriété** | **Description** | **Exception** |
|---|---|---|
| formNodes | Renvoie une liste de tous les objets de modèle de formulaire liés à un objet de données spécifié. |  |

## InstanceManager {#instancemanager}

| Propriété | Description |
|---|---|
| `name` | Identificateur utilisé pour identifier cet élément dans les expressions de script. |
| `occur` | Décrit les contraintes liées au nombre d’instances autorisées pour son conteneur englobant. |
| `min` | Indique le nombre minimum d’instances qui peuvent être instanciées. |
| `max` | Indique le nombre maximum d’instances qui peuvent être instanciées. |
| `count` | Indique le nombre actuel d’instances instanciées. |
| `setInstances` | Ajoute ou supprime les sous-formulaires ou jeux de sous-formulaires spécifiés de ce nœud. |
| `addInstance` | Ajoute une nouvelle instance d’un sous-formulaire ou d’un jeu de sous-formulaires à ce nœud. |
| `removeInstance` | Supprime un sous-formulaire ou un jeu de sous-formulaires de ce nœud. |
| `moveInstance` | Déplace un objet enfant d’un objet de modèle de formulaire vers un autre emplacement spécifié dans le modèle de formulaire. Les informations de modèle de données correspondantes pour l’objet sont également déplacées dans le modèle de données. |
| `insertInstance` | Insère une nouvelle instance d’un sous-formulaire ou d’un jeu de sous-formulaires à ce nœud. |

## list {#list}

| Propriété | Description |
|---|---|
| `length` | Le nombre d’éléments dans la liste. |
| `item` | Index à base zéro dans la collection. |
| `append` | Ajoute un nœud à la fin de la liste de nœuds. |
| `remove` | Supprime un nœud de la liste. |
| `insert` | Insère un nœud avant un nœud spécifique dans la liste de nœuds. |

## node {#node}

| Propriété | Description | Exception |
|---|---|---|
| createNode | Crée un nœud à partir d’un nom de classe valide. | Aucune |
| `isContainer` | Indique si cet objet est un objet conteneur. | Aucune |
| `isNull` | Indique si la valeur de données actuelle est une valeur nulle. | Aucune |
| `resolveNode` | Évalue l’expression SOM spécifiée, en commençant par l’objet de modèle d’objet de formulaire XML actif, et renvoie la valeur de l’objet spécifié dans l’expression SOM. | Aucune |
| `resolveNodes` | Évalue l’expression SOM spécifiée, en commençant par l’objet de modèle d’objet de formulaire XML actif, et renvoie la valeur de l’objet spécifié dans l’expression SOM. | Aucune |
| oneOfChild | Crée un nœud à partir d’un nom de classe valide. | Aucune |
| getElement | Renvoie un objet enfant spécifié. | Aucune |
| getAttribute | Récupère une valeur de propriété spécifiée. | Aucune |
| setAttribute | Définit la valeur d’une propriété spécifiée. | Aucune |

## model {#model}

| Propriété | Description | Exception |
|---|---|---|
| N/A | N/A | N/A |

## Sous-formulaire {#subform}

<table>
 <tbody>
  <tr>
   <th>Propriété</th>
   <th>Description</th>
   <th>Exception</th>
  </tr>
  <tr>
   <td>instanceIndex</td>
   <td>Spécifie l’index de l’objet, par rapport aux autres instances instanciées.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>execEvent</td>
   <td>Exécute le script d’événement de l’objet.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>getInvalidObjects</td>
   <td>Renvoie une liste de nœuds contenus dans le sous-formulaire (inclus) qui n’ont pas réussi le test de validation.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>border</td>
   <td>L’objet border décrit la bordure entourant un objet.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>borderColor</td>
   <td>Indique la valeur de la couleur de la bordure pour ce champ. Vous devez définir la propriété border.edge.presence pour l’afficher séparément.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>h</td>
   <td>Mesure de la hauteur pour la disposition.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>w</td>
   <td>Mesure indiquant la largeur pour la disposition.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Indique la coordonnée x du point d’ancrage du conteneur par rapport au coin supérieur gauche du conteneur parent lors d’un placement avec une disposition positionnée.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Indique la coordonnée y du point d’ancrage d’un conteneur par rapport au coin supérieur gauche du conteneur parent lors d’un placement avec une disposition positionnée.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>L’objet validate contrôle la validation des données fournies par l’utilisateur ou l’utilisatrice sur un formulaire. L’objet validate peut être activé plusieurs fois pendant la durée de vie d’un formulaire.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>name</td>
   <td>Identificateur utilisé pour identifier cet élément dans les expressions de script.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>presence</td>
   <td>Indique si un objet est visible ou non.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>access</td>
   <td>Définit l’accès de l’utilisateur ou de l’utilisatrice au contenu d’un objet conteneur, tel qu’un sous-formulaire.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>execValidate</td>
   <td>Calcule l’index d’un sous-formulaire ou d’un jeu de sous-formulaires en fonction de son emplacement par rapport à d’autres instances du même objet de formulaire.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>InstanceManager</td>
   <td>L’objet instanceManager gère la création, la suppression et le déplacement de l’instance des objets de modèle de formulaire.<br /> </td>
   <td>Aucune</td>
  </tr>
 </tbody>
</table>

### submit {#submit}

| Propriété | Description |
|---|---|
| target | URL à laquelle les données sont envoyées. L’omission de cet attribut implique que l’application de traitement XFA obtienne l’URI à l’aide d’une technique spécifique au produit, telle que l’accès aux informations spécifiques au produit dans l’objet config. |

## tree {#tree}

<table>
 <tbody>
  <tr>
   <th>Propriété</th>
   <th>Description</th>
   <th>Exception</th>
  </tr>
  <tr>
   <td>nodes</td>
   <td>Renvoie une liste de tous les objets enfants de l’objet actuel.</td>
   <td>
    <ul>
     <li>Non pris en charge pour xfa.nodes, desc.</li>
     <li>Les nombres de nœuds rapportés pour PDF et HTML sont différents. </li>
    </ul> </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Indique le nom de ce nœud.</td>
   <td>La configuration du nom à l’aide de scripts n’est pas autorisée en format HTML.</td>
  </tr>
  <tr>
   <td>parent</td>
   <td>Récupère le parent de ce nœud.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>index</td>
   <td>Renvoie la position de ce nœud dans sa collection de nœuds de même nom, compris dans la plage indiquée, ayant une relation de nœuds enfants identiques.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>somExpression</td>
   <td>Récupère l’expression SOM de ce nœud.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>resolveNode</td>
   <td>Évalue l’expression SOM spécifiée, en commençant par l’objet de modèle d’objet de formulaire XML actif, et renvoie la valeur de l’objet spécifié dans l’expression SOM.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>resolveNodes</td>
   <td>Évalue l’expression SOM spécifiée, en commençant par l’objet de modèle d’objet de formulaire XML actif, et renvoie la valeur de l’objet spécifié dans l’expression SOM.</td>
   <td>Aucune</td>
  </tr>
 </tbody>
</table>

## subformset {#subformset}

| Propriété | Description | Exception |
|---|---|---|
| InstanceManager | L’objet instanceManager gère la création, la suppression et le déplacement de l’instance des objets de modèle de formulaire. | Aucune |

## content {#content}

| **Propriété** | **Description** | **Exception** |
|---|---|---|
| isNull | Indique si la valeur de données actuelle est nulle. |  |

## dataValue {#datavalue}

| **Propriété** | **Description** | **Exception** |
|---|---|---|
| isNull | Indique si la valeur de données actuelle est nulle. |  |

## edge {#edge}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété </strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>couleur</td>
   <td>La propriété de couleur décrit une couleur unique pour l’objet pattern.</td>
   <td>
    <ul>
     <li>La valeur par défaut ne peut pas être récupérée. </li>
     <li>Les modifications sont répercutées dans le modèle et disponibles pour les scripts, mais ne sont pas synchronisées avec les éléments HTML. Par conséquent, les modifications ne sont pas répercutées dans l’interface utilisateur.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## fill {#fill}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>couleur</td>
   <td>Les propriétés de couleur définissent une couleur unique de remplissage.</td>
   <td>
    <ul>
     <li>La valeur par défaut ne peut pas être récupérée. </li>
     <li>Les modifications sont répercutées dans le modèle et disponibles pour les scripts, mais ne sont pas synchronisées avec les éléments HTML. Par conséquent, les modifications ne sont pas répercutées dans l’interface utilisateur.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## linear {#linear}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>couleur</td>
   <td>La propriété de couleur décrit une couleur unique pour un remplissage dégradé linéaire sur un formulaire.</td>
   <td>
    <ul>
     <li>La valeur par défaut ne peut pas être récupérée. </li>
     <li>Les modifications sont répercutées dans le modèle et disponibles pour les scripts, mais ne sont pas synchronisées avec les éléments HTML. Par conséquent, les modifications ne sont pas répercutées dans l’interface utilisateur.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## line {#line}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>L’objet edge décrit un arc, une ligne ou un côté d’une bordure ou d’un rectangle.<br /> </td>
   <td>Les attributs tels que la couleur, la limite, etc. ne sont pas pris en charge.<br /> </td>
  </tr>
 </tbody>
</table>

## pattern {#pattern}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>couleur</td>
   <td>La propriété de couleur décrit une couleur unique pour l’objet pattern. </td>
   <td>
    <ul>
     <li>La valeur par défaut ne peut pas être récupérée. </li>
     <li>Les modifications sont répercutées dans le modèle et disponibles pour les scripts, mais ne sont pas synchronisées avec les éléments HTML. Par conséquent, les modifications ne sont pas répercutées dans l’interface utilisateur.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## radial {#radial}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>couleur</td>
   <td>La propriété de couleur décrit une couleur unique pour l’objet radial.</td>
   <td>
    <ul>
     <li>La valeur par défaut ne peut pas être récupérée. </li>
     <li>Les modifications sont répercutées dans le modèle et disponibles pour les scripts, mais ne sont pas synchronisées avec les éléments HTML. Par conséquent, les modifications ne sont pas répercutées dans l’interface utilisateur.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## stipple {#stipple}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>couleur</td>
   <td>La propriété de couleur décrit une couleur unique pour l’objet stipple.</td>
   <td>
    <ul>
     <li>La valeur par défaut ne peut pas être récupérée. </li>
     <li>Les modifications sont répercutées dans le modèle et disponibles pour les scripts, mais ne sont pas synchronisées avec les éléments HTML. Par conséquent, les modifications ne sont pas répercutées dans l’interface utilisateur.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## draw {#draw}

<table>
 <tbody>
  <tr>
   <td>Propriété</td>
   <td>Description</td>
   <td>Exception</td>
  </tr>
  <tr>
   <td>ui</td>
   <td>L’objet ui renferme la description d’interface utilisateur d’un objet de formulaire.<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td>caption</td>
   <td>L’objet caption décrit un libellé descriptif associé à un objet de conception de formulaire.</td>
   <td> </td>
  </tr>
  <tr>
   <td>presence</td>
   <td>Indique si un objet est visible ou non.</td>
   <td> </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Identificateur qui permet de désigner cet objet ou cet événement dans les expressions de script.</td>
   <td>La définition de la valeur au moment de l’exécution n’est pas prise en charge.</td>
  </tr>
  <tr>
   <td>value</td>
   <td>L’objet value renferme une unité de contenu unique.<br /> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

## corner {#corner}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>couleur</td>
   <td>La propriété de couleur décrit une couleur unique de l’objet corner.</td>
   <td>
    <ul>
     <li>La valeur par défaut ne peut pas être récupérée. </li>
     <li>Les modifications sont répercutées dans le modèle et disponibles pour les scripts, mais ne sont pas synchronisées avec les éléments HTML. Par conséquent, les modifications ne sont pas répercutées dans l’interface utilisateur.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## checkButton {#checkbutton}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>L’objet border décrit la bordure entourant un objet checkButton. </td>
   <td>Les modifications sont répercutées dans le modèle et disponibles pour les scripts, mais ne sont pas synchronisées avec les éléments HTML. Par conséquent, les modifications ne sont pas répercutées dans l’IU.<br /> </td>
  </tr>
 </tbody>
</table>

## choiceList {#choicelist}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété<br /> </strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>L’objet border décrit la bordure entourant un objet choiceList.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## dateTimeEdit {#datetimeedit}

| **Propriété** | **Description** | **Exception** |
|---|---|---|
| border | L’objet border décrit la bordure entourant un objet dateTimeedit. |  |

## Image {#image}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>contentType</td>
   <td>Spécifie le type de contenu présent dans le document référencé, à savoir un type MIME.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>name<br /> </td>
   <td>Identificateur utilisé pour identifier cet élément dans les expressions de script.</td>
   <td>Aucune</td>
  </tr>
 </tbody>
</table>

## imageEdit {#imageedit}

| **Propriété** | **Description** | **Exception** |
|---|---|---|
| border | L’objet border décrit la bordure entourant un objet imageEdit. |  |

## numericEdit {#numericedit}

| **Propriété** | **Description** | **Exception** |
|---|---|---|
| border | L’objet border décrit la bordure entourant un objet. | aucune |

## object {#object}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>className</td>
   <td>Détermine le nom de la classe de cet objet.<br /> </td>
   <td>aucune</td>
  </tr>
 </tbody>
</table>

## rectangle {#rectangle}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>L’objet edge décrit un arc, une ligne, ou le côté d’une bordure ou d’un rectangle.<br /> </td>
   <td>Les attributs tels que la couleur, la limite, etc. ne sont pas pris en charge.</td>
  </tr>
 </tbody>
</table>

## textEdit {#textedit}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>L’objet border décrit la bordure entourant un objet.<br /> </td>
   <td>Aucune</td>
  </tr>
 </tbody>
</table>

## exclGroup {#exclgroup}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>disposition</td>
   <td>Indique la stratégie de disposition utilisée par cet objet.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>border</td>
   <td>Indique la bordure entourant ce champ.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>mandatory</td>
   <td>Indique la valeur nullTest pour le champ.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>borderColor</td>
   <td>Indique la valeur de couleur de bordure pour ce champ. Une bordure doit être définie avant de pouvoir modifier la couleur par script.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>borderWidth</td>
   <td>Indique la largeur de la bordure pour ce champ.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>h</td>
   <td>Mesure de la hauteur pour la disposition.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>transient</td>
   <td>Spécifie si l’application de traitement doit enregistrer la valeur du groupe d’exclusion lors de l’envoi du formulaire ou d’une opération de sauvegarde.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>w</td>
   <td>Mesure indiquant la largeur pour la disposition.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Indique la coordonnée x du point d’ancrage du conteneur par rapport au coin supérieur gauche du conteneur parent lors d’un placement avec une disposition positionnée.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Indique la coordonnée y du point d’ancrage d’un conteneur par rapport au coin supérieur gauche du conteneur parent lors d’un placement avec une disposition positionnée.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>caption</td>
   <td>L’objet caption décrit un libellé descriptif associé à un objet de conception de formulaire.<br /> </td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>L’objet validate contrôle la validation des données fournies par l’utilisateur ou l’utilisatrice sur un formulaire. L’objet validate peut être activé plusieurs fois pendant la durée de vie d’un formulaire.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>dataNode</td>
   <td>Obtient le nœud de données auquel est lié un nœud de formulaire après la fusion.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>presence</td>
   <td>Indique si un objet est visible ou non.</td>
   <td> </td>
  </tr>
  <tr>
   <td>access</td>
   <td>Définit l’accès de l’utilisateur ou de l’utilisatrice au contenu d’un objet conteneur, tel qu’un sous-formulaire.</td>
   <td>Pour les éléments individuels dans l’exclgrp, il renvoie toujours ouvert. </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Identificateur qui permet de désigner cet objet ou cet événement dans les expressions de script.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>members</td>
   <td>Indique les membres du groupe d’exclusion. </td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>selectedMember</td>
   <td>Renvoie le membre sélectionné d’un groupe d’exclusion.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>execCalculate</td>
   <td>Exécute tous les scripts sur l’événement calculate de l’objet spécifié, ainsi que tous les objets enfants.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>calculate</td>
   <td>L’objet calculate contrôle le calcul de la valeur d’un champ.<br /> </td>
   <td>Aucune</td>
  </tr>
 </tbody>
</table>

## arc {#arc}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété<strong></strong></strong></td>
   <td><strong>Description<strong></strong></strong></td>
   <td><strong>Exception<strong></strong></strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>L’objet edge décrit un arc, une ligne, ou le côté d’une bordure ou d’un rectangle.<br /> </td>
   <td>Les attributs tels que la couleur, la limite, etc. ne sont pas pris en charge. </td>
  </tr>
 </tbody>
</table>

## bordure {#border}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété<strong></strong></strong></td>
   <td><strong>Description<strong></strong></strong></td>
   <td><strong>Exception<strong></strong></strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>L’objet edge décrit un arc, une ligne, ou le côté d’une bordure ou d’un rectangle.<br /> </td>
   <td>Les attributs tels que la couleur, la limite, etc. ne sont pas pris en charge. </td>
  </tr>
 </tbody>
</table>

## $layout {#layout}

<table>
 <tbody>
  <tr>
   <td><strong>Propriété</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Exception</strong></td>
  </tr>
  <tr>
   <td>h</td>
   <td>Détermine la hauteur d’un objet de conception de formulaire donné.<br /> </td>
   <td>
    <ul>
     <li>La propriété de hauteur (h) n’est pas prise en charge pour les zones de page et de contenu. </li>
     <li>Le paramètre « Décalage à partir de la première zone de contenu où l’objet XFA-Form se produit » n’est pas pris en charge.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>w</td>
   <td>Détermine la largeur d’un objet de conception de formulaire donné.</td>
   <td>
    <ul>
     <li>La propriété de largeur (w) n’est pas prise en charge pour les zones de page et de contenu. </li>
     <li>Le paramètre « Décalage à partir de la première zone de contenu où l’objet XFA-Form se produit » n’est pas pris en charge.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>x</td>
   <td>Détermine la coordonnée x d’un objet de conception de formulaire donné par rapport à son objet parent.</td>
   <td>
    <ul>
     <li>La propriété de coordonnée x (x) n’est pas prise en charge pour les zones de page et de contenu. </li>
     <li>Le paramètre « Décalage à partir de la première zone de contenu où l’objet XFA-Form se produit » n’est pas pris en charge.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>y</td>
   <td>Détermine la coordonnée y d’un objet de conception de formulaire donné par rapport à son objet parent.</td>
   <td>
    <ul>
     <li>La propriété de coordonnée y (y) n’est pas prise en charge pour les zones de page et de contenu. </li>
     <li>Le paramètre « Décalage à partir de la première zone de contenu où l’objet XFA-Form se produit » n’est pas pris en charge.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>pagecount</td>
   <td>Détermine le nombre de pages du formulaire actif.</td>
   <td>
    <ul>
     <li>La méthode layout.pageCount() renvoie des valeurs différentes pour les formulaires PDF et HTML.</li>
     <li>Lors de la diminution du nombre de pages en masquant un objet, la méthode abspagecount renvoie une valeur incorrecte.<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <td>pagecontent</td>
   <td>Récupère les types d’objets de conception de formulaire à partir d’une page spécifiée d’un formulaire.</td>
   <td>Aucune</td>
  </tr>
  <tr>
   <td>absPageCount</td>
   <td>Détermine le nombre de pages du formulaire actif.</td>
   <td>
    <ul>
     <li>La méthode layout.pageCount() renvoie des valeurs différentes pour les formulaires PDF et HTML.</li>
     <li>Lors de la diminution du nombre de pages en masquant un objet, la méthode abspagecount renvoie une valeur incorrecte.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## items {#items}

| **Propriété** | **Description** | **Exception** |
|---|---|---|
| presence | Indique si un objet est visible ou non. | Aucune |

## FormCalc {#formcalc}

FormCalc est un langage spécifique à XFA qui permet de créer une logique centrée sur les formulaires électroniques et des racines de calcul. FormCalculation fournit un puissant ensemble de fonctions de création.

### Fonctions FormCalc prises en charge {#formcalc-supported-functions}

### Prise en charge des expressions FormCalc {#formcalc-expression-support}

<table>
 <tbody>
  <tr>
   <td><strong>Catégorie </strong></td>
   <td><strong>Description </strong></td>
   <td><strong>Échantillon </strong></td>
  </tr>
  <tr>
   <td>Expression simple</td>
   <td>Ajouter, soustraire, multiplier, diviser et parenthèses</td>
   <td>(a+b)*3</td>
  </tr>
  <tr>
   <td>Déclaration de variable</td>
   <td>Définir une variable</td>
   <td>var a<br /> var a=3<br /> a=3</td>
  </tr>
  <tr>
   <td>Expression logique</td>
   <td>
    <ul>
     <li>Logique (et/ou)</li>
     <li>Comparaison (supérieur/inférieur/égal)</li>
    </ul> </td>
   <td>A or 1<br /> 1 &lt;&gt; 2<br /> A NE B<br /> A or 1<br /> 1 &lt;&gt; 2<br /> A NE B</td>
  </tr>
  <tr>
   <td>Expression if</td>
   <td><br type="_moz" /> </td>
   <td>if (a&gt;b) then 2 endif</td>
  </tr>
  <tr>
   <td>quelques instants,</td>
   <td><br type="_moz" /> </td>
   <td>while (i lt 5) do i = i + 1 endwhile</td>
  </tr>
  <tr>
   <td>pour</td>
   <td><br type="_moz" /> </td>
   <td>for i = 100 downto 1 <br /> do s = s + i endfor</td>
  </tr>
  <tr>
   <td>for each</td>
   <td><br type="_moz" /> </td>
   <td>for each i in (1, 2, 3) <br /> do s = s + i endfor</td>
  </tr>
  <tr>
   <td>déclaration de fonction</td>
   <td>Définition d’une fonction personnalisée dans FormCalc</td>
   <td>func foo(n) do var f = n endfunc</td>
  </tr>
 </tbody>
</table>

### Prise en charge des API Acrobat {#acrobat-api-support}

1. **Fonctions arithmétiques**

   1. Abs()
   1. Avg()
   1. Ceil()
   1. Décompte()
   1. Floor()
   1. Max()
   1. Min()
   1. Mod()
   1. Round()
   1. Sum()

1. **Fonctions scientifiques**

   1. Acos()
   1. Asin()
   1. Atan()
   1. Atan2()
   1. Cos()
   1. Sin()
   1. Tan()
   1. Exp()
   1. Log()
   1. Pow()
   1. Sqrt()
   1. Deg2Rad()
   1. Rad2Deg()
   1. Pi()

1. **Fonctions financières**

   1. Apr()
   1. Cterm()
   1. Fv()
   1. Ipmt()
   1. Npv()
   1. Pmt()
   1. Ppmt()
   1. Pv()
   1. Rate()
   1. Terme()

1. **Fonctions logiques**

   1. Choose()
   1. If()
   1. Oneof()
   1. Within()

1. **Fonctions de chaîne**

   1. At()
   1. Concat()
   1. Left()
   1. Len()
   1. Lower()
   1. Ltrim()
   1. Remplacer()
   1. Right()
   1. Rtrim()
   1. Space()
   1. Stuff()
   1. Substr()
   1. Upper()
   1. WordNum()

1. **Date et heure**

   1. Date()
   1. num2date()
   1. DateFmt()

<table>
 <tbody>
  <tr>
   <td><strong>API</strong></td>
   <td><strong>Description</strong></td>
   <td><strong>Aberration</strong></td>
  </tr>
  <tr>
   <td>console.println()</td>
   <td>Cette API Acrobat transfère la sortie vers la console JavaScript.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.alert()</td>
   <td>Cette API Acrobat envoie un message d’alerte via une boîte de dialogue contextuelle JavaScript.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.beep()</td>
   <td>Entraîne l’émission d’un son par le système.</td>
   <td>Aucune action n’est effectuée.</td>
  </tr>
  <tr>
   <td>app.execDialog()</td>
   <td>Affiche une boîte de dialogue modale à l’utilisateur ou à l’utilisatrice. Les boîtes de dialogue modales doivent être fermées par l’utilisateur ou l’utilisatrice avant que l’application hôte ne puisse être directement utilisée à nouveau.</td>
   <td>Aucune action n'est effectuée.<br /> </td>
  </tr>
  <tr>
   <td>app.launchURL()</td>
   <td>Lance une URL dans une fenêtre du navigateur.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.setInterval()</td>
   <td>Spécifie un script JavaScript et une période. Le script est exécuté chaque fois que la période s’écoule. La valeur renvoyée par cette méthode doit être conservée dans une variable JavaScript. Dans le cas contraire, l’objet interval est soumis au nettoyage de la mémoire, ce qui entraînerait l’arrêt de l’horloge. Pour terminer l’exécution périodique, transmettez l’objet interval renvoyé à clearInterval.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.setTimeOut()</td>
   <td>Spécifie un script JavaScript et une période. Le script est exécuté une seule fois, une fois la période écoulée. La valeur renvoyée par cette méthode doit être contenue dans une variable JavaScript. Dans le cas contraire, l’objet timeout est soumis au nettoyage de la mémoire, ce qui entraînerait l’arrêt de l’horloge. Pour annuler l’événement timeout, transmettez l’objet timeout renvoyé à clearTimeOut.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.clearInterval()</td>
   <td>Annule un intervalle précédemment enregistré et initialement défini par la méthode setInterval.</td>
   <td>Dans les formulaires HTML5, l’API ne fonctionne pas correctement.</td>
  </tr>
  <tr>
   <td>app.clearTimeOut()</td>
   <td>Annule un intervalle timeout précédemment enregistré. Un tel intervalle est initialement défini par setTimeOut.</td>
   <td>Dans les formulaires HTML5, l’API ne fonctionne pas correctement.<br /> </td>
  </tr>
  <tr>
   <td>app.eval()</td>
   <td>Exécute un script donné.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.activeDocs</td>
   <td>Tableau contenant l’objet Doc de chaque document actif. Si aucun document n’est actif, activeDocs ne renvoie rien, c’est-à-dire qu’il adopte le même comportement que d = new Array(0) dans le code JavaScript principal.</td>
   <td>Renvoie un tableau vide pour les formulaires HTMl5.</td>
  </tr>
  <tr>
   <td>app.calculate</td>
   <td>Si la valeur est true (valeur par défaut), les calculs peuvent être effectués. Si la valeur est false, les calculs ne sont pas autorisés.</td>
   <td>Toujours true pour les formulaires HTMl5.</td>
  </tr>
  <tr>
   <td>app.constants</td>
   <td>Un objet enveloppant pour différentes valeurs constantes. Actuellement, cette propriété renvoie un objet avec une seule propriété : align.</td>
   <td>Les formulaires HTML5 renvoient un objet d’alignement vide.</td>
  </tr>
  <tr>
   <td>app.focusRect</td>
   <td>Active ou désactive le rectangle ciblé. Le rectangle ciblé correspond au léger trait en pointillés autour des boutons, des cases à cocher, des boutons radio et des signatures pour indiquer que le champ de formulaire est ciblé par le clavier. La valeur true est activée sur le rectangle ciblé.</td>
   <td>Toujours true pour les formulaires HTML5.</td>
  </tr>
  <tr>
   <td>app.formsVersion</td>
   <td>Numéro de version du logiciel de la visionneuse de formulaires. Vérifiez cette propriété pour déterminer si des objets, des propriétés ou des méthodes dans les versions plus récentes du logiciel sont disponibles si vous souhaitez préserver la compatibilité ascendante dans vos scripts.</td>
   <td>Toujours 11.001.</td>
  </tr>
  <tr>
   <td>app.language</td>
   <td>Langue de la visionneuse Acrobat en cours d’exécution.</td>
   <td>Toujours « ENU » pour les formulaires HTMl5.</td>
  </tr>
 </tbody>
</table>

## Événements XFA pris en charge {#supported-xfa-events}

Les événements XFA côté client suivants sont pris en charge :

* Initialiser
* Valider
* Calculer
* Cliquez sur
* Enter
* Quitter
* Modification
* ValidationState

>[!NOTE]
>
>Les formulaires HTML5 sont rendus côté client (navigateur). Utilisez des scripts **validate** et **calculate** côté client au lieu des scripts côté serveur.
