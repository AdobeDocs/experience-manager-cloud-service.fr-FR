---
title: Éditeur d’image
description: L’éditeur d’images est un élément d’AEM essentiel qui peut être exploité par des composants pour faciliter la manipulation des images par les auteurs de contenu.
translation-type: tm+mt
source-git-commit: 83c27daae4e8ae2ae6a8f115c9da9527971c6ecb
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 10%

---


# Éditeur d’image {#image-editor}

L’éditeur d’images est un élément d’AEM essentiel qui peut être exploité par des composants pour faciliter la manipulation des images par les auteurs de contenu.

## Unités relatives pour la zone cliquable {#relative-units-for-image-map}

L’éditeur d’images conserve les zones de zone cliquable en tant qu’unités absolues et relatives. Les unités relatives sont utiles lorsqu’elles sont fournies en tant qu’attributs de données pour redimensionner de manière dynamique une zone cliquable (par rapport à la taille de l’image) côté client dans un composant d’image réactif.

### imageMap, propriété {#imagemap-property}

Les coordonnées de la zone cliquable sont conservées dans le JCR en tant que `imageMap` propriété par l’éditeur d’images. Il a le format suivant.

La propriété stocke les zones de mappage comme suit :

`[area1][area2][...]`

Format de zone :

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

Exemple :

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## Prise en charge des images SVG {#support-for-svg-images}

Les graphiques vectoriels évolutifs (SVG) sont pris en charge par l’éditeur d’images.

* Les opérations de glisser-déplacer d’une ressource SVG à partir de DAM et le téléchargement d’un fichier SVG depuis un système de fichiers local sont pris en charge.

## Activation des modules externes par type MIME {#enabling-plugins-by-mime-type}

Dans certains cas, les actions de création doivent être restreintes pour certains types MIME, en raison du manque de prise en charge du traitement côté serveur. Par exemple, la modification d’images SVG peut ne pas être autorisée.

Les modules externes de l’éditeur d’images peuvent être activés de manière sélective par type MIME en définissant une `supportedMimeTypes` propriété sur le noeud de configuration du module externe individuel.

### Exemple {#example}

Par exemple, supposons que la possibilité de recadrer ne soit autorisée que pour les images GIF, JPEG, PNG, WEBP et TIFF.

La `supportedMimeTypes` propriété doit ensuite être définie sous la forme d’une chaîne des types MIME autorisés sur le noeud de configuration du module externe sur le `cq:editConfig` noeud du composant d’image.

`/apps/core/wcm/components/image/v2/image/cq:editConfig`

```xml
 jcr:primaryType="cq:EditConfig">
     <cq:dropTargets jcr:primaryType="nt:unstructured">
         <image ...>
            ...
         </image>
     </cq:dropTargets>
     <cq:inplaceEditing
         jcr:primaryType="cq:InplaceEditingConfig"
         active="{Boolean}true"
         editorType="image">
         <config jcr:primaryType="nt:unstructured">
             <plugins jcr:primaryType="nt:unstructured">
                 <crop
                     jcr:primaryType="nt:unstructured"
                     supportedMimeTypes="[image/gif,image/jpeg,image/png,image/webp,image/tiff]"
                     features="*">
                     <aspectRatios jcr:primaryType="nt:unstructured">
                        ...
                     </aspectRatios>
                 </crop>
                 ...
             </plugins>
             <ui jcr:primaryType="nt:unstructured">
                 ...
             </ui>
         </config>
     </cq:inplaceEditing>
 </jcr:root>
```
