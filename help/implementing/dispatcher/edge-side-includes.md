---
title: Edge Side Includes
description: Le réseau de diffusion de contenu géré par Adobe prend désormais en charge Edge Side Includes (ESI), un langage de balisage pour l’assemblage de contenu web dynamique de niveau périphérie.
feature: Dispatcher
exl-id: 35093477-2788-4f69-80a9-899f43567cae
role: Admin
source-git-commit: d70a8030ca6687b1839adc0ce1becdf366ec7170
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 2%

---

# Edge Side Includes {#edge-side-includes}

La vitesse de diffusion du contenu bénéficie d’une mise en cache agressive des pages, obtenue en définissant des en-têtes de cache avec des valeurs TTL (durée de vie) élevées. Cela peut s’avérer difficile lorsque les pages incluent du contenu dynamique, qui doit être fréquemment actualisé ou qui ne peut pas du tout être mis en cache. Heureusement, il existe des stratégies pour lesquelles la page d’HTML contenant peut être mise en cache avec un TTL élevé, ce qui entraîne un report de la récupération des fragments de contenu les plus dynamiques à une date ultérieure, que ce soit par le biais du code JavaScript côté client ou du réseau de diffusion de contenu. Cette dernière approche est une norme appelée Edge Side Includes (ESI), qui est prise en charge pour les sites rendus avec publication AEM. L’HTML inclut des balises ESI qui demandent au réseau de diffusion de contenu de différer la diffusion de la page au navigateur jusqu’à ce qu’il évalue ces balises, en récupérant du contenu supplémentaire plus dynamique (TTL inférieur) à partir de l’origine (ou du cache CDN si son délai d’activation n’a pas expiré).

Dans certains cas d’utilisation, les inclusions côté Edge peuvent s’avérer utiles :

* Affichage du nom d’un utilisateur final ou d’autres informations propres à l’utilisateur final.
* Affichage d’une liste d’informations récentes, telles que des articles d’actualité ou des cours des actions.

## Syntaxe ESI {#esi-syntax}

La syntaxe ESI est la suivante, si une page parente `/content/page.html` comprend un extrait de code `content/snippets/mysnippet.html`.

```
<html>
  <head>
      <title>My Site</title>
  </head>
  <body>
    <div id="content">
      <esi:include src="/content/snippets/mysnippet.html" />
    </div>
  </body>
</html>
```

Pour plus d’informations, voir la [spécification ESI](https://www.w3.org/TR/esi-lang/) .

### Considérations {#esi-syntax-considerations}

* Les balises ESI suivantes sont prises en charge : inclure, commenter, supprimer.
* Les balises ESI sont traitées sur le réseau de diffusion de contenu de manière séquentielle plutôt que simultanée. De nombreuses balises ESI sur une page avec de faibles TTL peuvent donc ajouter une latence à l’expérience de l’utilisateur final.
* La profondeur maximale d’ESI : le traitement d’inclusion est de 5.
* ESI total maximal : inclure les fragments de traitement est de 256.


## Configuration Apache {#esi-apache}

Si vous disposez de pages avec des balises ESI, vous devez déclarer les propriétés suivantes dans la configuration Apache :

```
<LocationMatch "/parent-pages/*content/page.html">
   # disable dispatcher compression
   SetEnv no-gzip 1
   # enable esi processing 
   Header set x-aem-esi "on"
   # enable edgeCDN compression
   Header set x-aem-compress "on"

   # typically the main page is cached at the CDN
   Header always set Cache-Control "max-age=300"
 </LocationMatch>


<LocationMatch "/content/snippets/mysnippet.html">
  SetEnv no-gzip 1

  # typically the included page is either set to a lower TTL than the parent page, or not cached at all, as these 2 commented declarations show, respectively:
  #Header always set Cache-Control "no-cache"
  #Header always set Cache-Control "max-age=50"
 </LocationMatch> 
```

Les propriétés configurées se comportent comme suit :

| Propriété | Comportement |
|-----------|--------------------------|
| **no-gzip** | S’il est défini sur 1, la page d’HTML est transmise d’Apache au réseau de diffusion de contenu non compressé. Cela est nécessaire pour l’ESI, car le contenu doit être envoyé sur le CDN sans compression pour que le CDN puisse voir et évaluer les balises ESI.<br/><br/>La page parente et les fragments de code inclus doivent définir no-gzip sur 1.<br/><br/>Ce paramètre remplace le paramètre de compression qu’Apache aurait pu utiliser autrement, en fonction des valeurs `Accept-Encoding` de la requête. |
| **x-aem-esi** | S’il est défini sur &quot;activé&quot;, le réseau de diffusion de contenu évalue les balises ESI de la page d’HTML parente.  Par défaut, l’en-tête n’est pas défini. |
| **x-aem-compress** | S’il est défini sur &quot;activé&quot;, le réseau de diffusion de contenu compresse le contenu du réseau de diffusion de contenu vers le navigateur. Étant donné que la transmission de la page parente d’Apache vers le CDN doit être décompressée pour que l’ESI fonctionne (`no-gzip` défini sur 1), cela peut réduire la latence.<br/><br/>Si cet en-tête n’est pas défini, lorsque le réseau de diffusion de contenu récupère le contenu de l’origine non compressé, il diffusera également le contenu au client non compressé. Il est donc nécessaire de définir cet en-tête si `no-gzip` est défini sur 1 (obligatoire pour ESI) et qu’il est nécessaire de diffuser du contenu compressé à partir du CDN vers le navigateur. |

## Sling Dynamic Include {#esi-sdi}

Bien que cela ne soit pas nécessaire, l’inclusion [Sling Dynamic Include](https://sling.apache.org/documentation/bundles/dynamic-includes.html) (SDI) peut être utilisée pour générer des fragments de code ESI interprétés sur le réseau de diffusion de contenu.
