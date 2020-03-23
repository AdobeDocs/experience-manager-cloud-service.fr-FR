---
title: Fragments de contenu Configuration des composants pour le rendu
description: Fragments de contenu Configuration des composants pour le rendu
translation-type: tm+mt
source-git-commit: 312e047265c55a7f43c559cd2e9bd9831db0513a

---


# Fragments de contenu Configuration des composants pour le rendu{#content-fragments-configuring-components-for-rendering}

Il existe plusieurs services [](#definition-of-advanced-services-that-need-configuration) avancés liés au rendu des fragments de contenu. Pour utiliser ces services, les types de ressources de ces composants doivent se faire connaître à la structure des fragments de contenu.

Pour ce faire, configurez le service [OSGi - Configuration](#osgi-service-content-fragment-component-configuration)du composant Fragment de contenu.

Ces informations sont requises lorsque :

* Vous devez mettre en oeuvre votre propre composant basé sur les fragments de contenu,
* Et il faut utiliser les services avancés.

Il est toutefois recommandé d’utiliser les composants principaux.

>[!CAUTION]
>
>* **Si vous n’avez pas besoin des services[](#definition-of-advanced-services-that-need-configuration)**avancés décrits ci-dessous, vous pouvez ignorer cette configuration.
   >
   >
* **Lorsque vous étendez ou utilisez des composants prêts à l’emploi,** il n’est pas recommandé de modifier la configuration OSGi.
   >
   >
* **Vous pouvez créer un composant à partir de zéro qui utilise uniquement l’API Fragments de contenu, sans services** avancés. Cependant, dans ce cas, vous devrez développer votre composant afin qu’il traite le traitement approprié.
>
>
Il est donc recommandé d’utiliser les composants principaux.

## Définition des services avancés nécessitant une configuration {#definition-of-advanced-services-that-need-configuration}

Les services qui nécessitent l’enregistrement d’un composant sont les suivants :

* Déterminer correctement les dépendances au cours de la publication (c.-à-d. s’assurer que les fragments et modèles peuvent être publiés automatiquement avec une page s’ils ont été modifiés depuis la dernière publication).
* Prise en charge des fragments de contenu dans la recherche de texte intégral.
* Gestion/gestion du contenu *intermédiaire.*
* Gestion/gestion des fichiers multimédias *mixtes.*
* Le répartiteur vire les fragments référencés (si une page contenant un fragment est republiée).
* Utilisation du rendu basé sur les paragraphes.

Si vous avez besoin d’une ou de plusieurs de ces fonctionnalités, il est alors (généralement) plus facile d’utiliser les services avancés prêts à l’emploi, au lieu de les développer entièrement.

## Service OSGi - Configuration du composant de fragment de contenu {#osgi-service-content-fragment-component-configuration}

La configuration doit être liée au service OSGi **Content Fragment Component Configuration**:

`com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl`

>[!NOTE]
>
>Voir Configuration [](/help/implementing/deploying/overview.md#osgi-configuration) OSGi pour plus d’informations.

Par exemple :

![Configuration du composant Fragment de contenu de configuration OSGi](assets/cf-component-configuration-osgi.png)

La configuration OSGi est la suivante :

<table>
 <thead>
  <tr>
   <td>Libellé</td>
   <td>OSGi Configuration<br /> </td>
   <td>Description</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><strong>Type de ressource</strong></td>
   <td><code>dam.cfm.component.resourceType</code></td>
   <td>le type de ressource à enregistrer; p. ex. <br /> <p><span class="cmp-examples-demo__property-value"><code>core/wcm/components/contentfragment/v1/contentfragment</code></code></p> </td>
  </tr>
  <tr>
   <td><strong>Propriété de référence</strong></td>
   <td><code>dam.cfm.component.fileReferenceProp</code></td>
   <td>nom de la propriété qui contient la référence au fragment ; par ex. <code>fragmentPath</code> ou <code>fileReference</code></td>
  </tr>
  <tr>
   <td><strong>Propriété d’élément(s)</strong></td>
   <td><code>dam.cfm.component.elementsProp</code></td>
   <td>nom de la propriété qui contient le ou les noms des éléments à rendre ; p. ex.<code>elementName</code></td>
  </tr>
  <tr>
   <td><strong>Propriété de variation</strong><br /> </td>
   <td><code>dam.cfm.component.variationProp</code></td>
   <td>nom de la propriété qui contient le nom de la variation à rendre ; p. ex.<code>variationName</code></td>
  </tr>
 </tbody>
</table>

Pour certaines fonctionnalités, votre composant devra respecter les conventions prédéfinies. Le tableau suivant décrit les propriétés à définir, par votre composant, pour chaque paragraphe (c’est-à-dire `jcr:paragraph` pour chaque instance de composant) afin que les services puissent les détecter et les traiter correctement.

<table>
 <thead>
  <tr>
   <td>Nom de la propriété</td>
   <td>Description</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>paragraphScope</code></td>
   <td><p>Propriété de chaîne qui définit le mode de sortie des paragraphes en mode <em>de rendu d’un élément</em>unique.</p> <p>Valeurs:</p>
    <ul>
     <li><code>all</code> : pour rendre tous les paragraphes</li>
     <li><code>range</code> : pour rendre la plage de paragraphes fournie par <code>paragraphRange</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphRange</code></td>
   <td><p>Propriété de chaîne qui définit la plage de paragraphes à générer en mode <em>de rendu pour un élément</em>unique.</p> <p>Format:</p>
    <ul>
     <li><code>1</code> ou <code>1-3</code> ou <code>1-3;6;7-8</code> ou <code>*-3;5-*</code>
     <ul>
       <li><code>-</code> indicateur de plage</li>
       <li><code>;</code> Séparateur </li>
       <li><code>*</code> générique</li>
     </ul>
     </li>
     <li>évalué uniquement si <code>paragraphScope</code> la valeur est définie sur <code>range</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphHeadings</code></td>
   <td>Propriété booléenne qui définit si les en-têtes (par exemple, <code>h1</code>, <code>h2</code>, <code>h3</code>) sont comptés comme des paragraphes (<code>true</code>) ou non (<code>false</code>)</td>
  </tr>
 </tbody>
</table>

## Exemple {#example}

À titre d’exemple, reportez-vous aux sections suivantes (sur une instance AEM prête à l’emploi) :

```
/apps/core/wcm/config/com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl-core-comp-v1.config
```

Contient :

```
dam.cfm.component.resourceType="core/wcm/components/contentfragment/v1/contentfragment"
dam.cfm.component.fileReferenceProp="fragmentPath"
dam.cfm.component.elementsProp="elementName"
dam.cfm.component.variationProp="variationName"
```

