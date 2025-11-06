---
title: Éditeur d’image
description: L’éditeur d’image est un élément essentiel d’AEM qui peut être exploité par des composants pour faciliter la manipulation des images par les personnes créant du contenu.
exl-id: c8ae4f59-75b1-49b4-8dd4-957d2e33000b
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 100%

---

# Éditeur d’image {#image-editor}

L’éditeur d’image est un élément essentiel d’AEM qui peut être exploité par des composants pour faciliter la manipulation des images par les personnes créant du contenu.

## Unités relatives pour la zone cliquable {#relative-units-for-image-map}

L’éditeur d’image conserve les zones cliquables comme unités absolues et relatives. Les unités relatives sont utiles lorsqu’elles sont fournies en tant qu’attributs de données pour redimensionner de manière dynamique une zone cliquable (par rapport à la taille de l’image) côté client dans un composant d’image réactif.

### Propriété imageMap {#imagemap-property}

Les coordonnées de la zone cliquable sont conservées dans le JCR comme propriété `imageMap` par l’éditeur d’image. Leur format est le suivant.

La propriété stocke des zones comme suit :

`[area1][area2][...]`

Format de zone :

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

Exemple :

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## Prise en charge des images SVG {#support-for-svg-images}

Les images SVG (Scalable Vector Graphics) sont pris en charge par l’éditeur d’image.

* Les opérations de glisser-déplacer d’une ressource SVG à partir de DAM et le chargement d’un fichier SVG depuis un système de fichiers local sont pris en charge.

## Activation de modules par type MIME {#enabling-plugins-by-mime-type}

Dans certaines situations, les actions de création doivent être restreintes pour certains types MIME en raison de l’absence de prise en charge du traitement côté serveur. Par exemple, la modification d’images SVG n’est peut-être pas autorisée.

Les modules de l’éditeur d’image peuvent être activés de manière sélective par type MIME en définissant une propriété `supportedMimeTypes` sur le nœud de configuration du module donné.

### Exemple {#example}

Par exemple, supposons que la possibilité de recadrer ne doive être accordée que pour les images GIF, JPEG, PNG, WEBP et TIFF.

La propriété `supportedMimeTypes` doit alors être définie sous la forme d’une chaîne des types MIME autorisés sur le nœud de configuration du module sur le nœud `cq:editConfig` du composant d’image.

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
