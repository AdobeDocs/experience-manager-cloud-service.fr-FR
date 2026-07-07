---
title: Fragments de contenu visuels - à diffuser avec l’URL de publication
description: Utilisez l’URL de publication pour diffuser des fragments de contenu visuel.
feature: Developing, Content Fragments
role: Admin, Developer
source-git-commit: b0a32380b028ff230ec4904a86b55b8ba0f4558f
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 0%

---


# Fragments de contenu visuels - Diffuser avec l’URL de publication {#visual-content-fragments-deliver-with-the-publish-url}

Lorsqu’un fragment de contenu basé sur un modèle auquel sont associés des modèles HTML est publié, l’HTML rendue de ce fragment est disponible via le niveau de publication Adobe Experience Manager (AEM) as a Cloud Service à une URL avec cette structure :

```html
https://publish-p<programId>-e<envId>.adobeaemcloud.com/adobe/stable/previewtemplates/contentFragments/<templateId>/<fragmentId>/<variation>.html
```

Cette URL renvoie un *document HTML autonome* (y compris une structure et un CSS intégrés) qui peut être incorporé dans n’importe quel contexte web.

## Techniques d’intégration - Aperçu {#embedding-techniques-overview}

Il existe trois approches distinctes pour utiliser HTML à partir d’un fragment de contenu visuel sur une page hôte. Chacun présente des caractéristiques distinctes concernant l’isolation du style, le comportement de la disposition, l’accessibilité et la complexité.

| | Élément intégré | iframe | Élément personnalisé + DOM fantôme |
|--- |--- |--- |--- |
| Mécanisme | `fetch()` l’URL, injectez la réponse HTML dans un `<div>` via `innerHTML` | `<iframe src="publishURL">` | Définir un élément personnalisé, `fetch()` HTML, injecter dans une racine Shadow DOM attachée |
| Isolation de style | Aucun : le fragment CSS est introduit dans la page hôte et le CSS hôte affecte le fragment | Complet : contexte de navigation distinct, isolation CSS complète | Fort : la limite DOM fantôme bloque la cascade CSS hôte ; les styles de fragment restent encapsulés. |
| Mise en page de la participation | Complet : le contenu fait partie du flux normal du document et répond au dimensionnement de la flexbox/grille/conteneur | Aucune : iframe a des dimensions fixes ; nécessite un redimensionnement automatique explicite basé sur `width`/`height` ou JS. | Complet : l’élément personnalisé participe au flux normal du document hôte comme tout autre élément DOM |
| Accessibilité (a11y) | Idéal : le contenu se trouve dans l’arborescence DOM principale, entièrement traversable par les lecteurs d’écran et les technologies d’assistance | Modéré : un contexte de navigation distinct peut dérouter la navigation dans le lecteur d’écran ; requiert un attribut `title` | Bon : le contenu se trouve dans le même document ; le modèle DOM fantôme est traversable par les technologies d’assistance modernes |
| SEO | Médiocre : le contenu chargé via JS `fetch()` n’est pas indexé par la plupart des robots d&#39;exploration | Médiocre : le contenu de l’iframe n’est généralement pas indexé dans le contexte de la page parente | Médiocre : identique au contenu intégré ; le contenu récupéré en JS n’est pas analysable. |
| JavaScript runtime | Partagé : même contexte de fenêtre/document ; risque de collisions de scripts si le fragment contient des balises `<script>` | Isolé — contexte de fenêtre séparé ; aucun risque de collision | Partagé : même contexte de fenêtre, mais étendue à DOM ; les scripts dans la racine fantôme s’exécutent dans le contexte hôte. |
| Prise en charge des origines multiples | Nécessite des en-têtes CORS sur l’URL de publication (le service les configure). | Fonctionne en mode natif : les iFrames chargent du contenu cross-origin sans CORS. | Nécessite des en-têtes CORS sur l’URL de publication (identique à la ligne) |
| Complexité de l’implémentation | Minimale : quelques lignes de JS | ANODIN : zéro JS requis ; HTML pur | Faible : ~20 lignes de JS pour la définition de l’élément personnalisé, réutilisable sur toute la page |
| Mieux adapté à | Prototypage, contenu de même origine approuvé, contextes où l’intégration de la disposition est essentielle et où les conflits CSS sont gérables | Incorporation rapide, contenu en sandbox, scénarios d’origine croisée où CORS n’est pas disponible, contenu qui doit être entièrement isolé | Utilisation en production : équilibre l’isolement, la participation à la mise en page et l’accessibilité (recommandé pour les composants principaux AEM et les sites externes) |

### Élément intégré (fetch + internalHTML) {#inline-element-fetch-and-innerhtml}

L&#39;approche la plus simple :

1. récupérer l’URL de publication ;
1. injecter l’HTML dans un élément de conteneur

Exemple d’incorporation d’éléments intégrés :

```html
<div id="cf-container"></div>
<script>
  fetch("<publish-url>")
    .then(r => r.ok ? r.text() : Promise.reject(r.status))
    .then(html => {
      document.getElementById("cf-container").innerHTML = html;
    })
    .catch(err => console.error("Failed to load fragment", err));
</script>
```

Quand l’utiliser :

* prototypage rapide ou pages de preuve de concept
* Contextes de même origine dans lesquels vous contrôlez les styles de page hôte et de fragment
* Lorsque la flexibilité maximale de la disposition est plus importante que l’encapsulation de style

>[!CAUTION]
>
>**Risque de collision CSS**
>
>Les styles intégrés du fragment (y compris ses blocs de `<style>`, ses déclarations de police et ses sélecteurs d’éléments) fusionnent dans la cascade de la page hôte.
>
>Cela peut entraîner des remplacements de style involontaires dans les deux directions.
>
>N’utilisez cette technique que lorsque vous pouvez tolérer ou gérer activement ces conflits.

### iframe {#iframe}

Chargez l’URL de publication directement en tant que `src` d’une `<iframe>`. Aucun JavaScript n’est nécessaire.

Exemple d’incorporation d’iframe :

```iframe
<iframe
  src="<publish-url>"
  title="Content Fragment Preview"
  width="100%"
  height="600"
  frameborder="0"
  style="border: none;"
></iframe>
```

Vous pouvez également redimensionner automatiquement l’iframe (facultatif).

Pour dimensionner l’iframe de manière dynamique à sa hauteur de contenu (en évitant les barres de défilement), utilisez un modèle de `postMessage` ou une bibliothèque appropriée.

Voici un exemple d’approche légère :

```iframe
<iframe id="cf-iframe" src="<publish-url>" title="Content Fragment Preview"
  width="100%" frameborder="0" style="border:none; overflow:hidden;"
  onload="this.style.height = this.contentDocument.documentElement.scrollHeight + 'px';"
></iframe>
```

>[!WARNING]
>
>L’approche de redimensionnement automatique `onload` ci-dessus ne fonctionne que pour les iframes **même origine**.
>
>Pour les URL de publication **cross-origin**, vous avez besoin d’une solution basée sur les `postMessage` ou de définir une hauteur fixe.

Quand l’utiliser :

* Bloc incorporé Edge Delivery Services (intégration par défaut, voir la section ci-dessous).
* Contextes dans lesquels l’isolement CSS/JS complet est essentiel
* Incorporation entre origines multiples où CORS n’est pas configuré
* Intégration rapide à code nul (collez simplement l’URL)

### Élément personnalisé + DOM fantôme (recommandé) {#custom-element-and-shadow-dom-recommended}

Définissez un élément personnalisé `<cf-visualization>` réutilisable qui récupère l’URL de publication et injecte l’HTML dans une racine Shadow DOM encapsulée.

Cet élément fournit :

* Isolation DOM fantôme
   * Le balisage et les styles du fragment sont encapsulés dans une racine fantôme, ce qui empêche les conflits avec la cascade CSS de la page hôte.
* Participation à la mise en page en ligne
   * Le contenu rendu participe au flux normal du document hôte, répondant au dimensionnement du conteneur et aux contextes de flexbox/grille sans gestion manuelle des dimensions.
* Contexte de navigation unique
   * Aucun contexte de document secondaire n’est créé ; le contenu du fragment partage le runtime JavaScript de la page et peut être entièrement parcouru par les technologies d’assistance.
* Frais généraux minimaux
   * Un seul appel `fetch` récupère l’HTML prégénérée à partir du niveau de publication. Aucun framework de rendu côté client n’est requis.

>[!IMPORTANT]
>
>Il s’agit de l’approche recommandée pour l’utilisation en production et de la technique utilisée par les composants principaux d’AEM.

Pour définir l’élément personnalisé, incluez le script suivant une fois par page. Toutes les instances `<cf-visualization>` de la page utiliseront cette définition :

```javascript
<script>
  class CfVisualization extends HTMLElement {
    connectedCallback() {
      const src = this.getAttribute("src");
      if (!src) return;

      const shadow = this.attachShadow({ mode: "open" });

      fetch(src)
        .then((r) => (r.ok ? r.text() : Promise.reject(r.status)))
        .then((html) => {
          shadow.innerHTML = html;
        })
        .catch((err) => {
          console.error("cf-visualization: failed to load", src, err);
        });
    }
  }

  if (!customElements.get("cf-visualization")) {
    customElements.define("cf-visualization", CfVisualization);
  }
</script>
```

Pour utiliser l’élément personnalisé :

```html
<cf-visualization src="<publish-url>"></cf-visualization>
```

Quand l’utiliser :

* Pages AEM Sites utilisant des composants principaux (il s’agit du comportement intégré)
* Sites web externes/tiers qui nécessitent une intégration propre et réutilisable
* Tout contexte où l’isolation de style et la participation au flux de mise en page sont nécessaires

## Intégration à Edge Delivery Services (bloc intégré) {#integration-with-edge-services-embed-block}

Dans Edge Delivery Services, l’URL de publication est consommée par le biais d’un **[bloc intégré](https://sidekick-library--aem-block-collection--adobe.aem.page/tools/sidekick/library.html?plugin=blocks&path=/block-collection/embed&index=0)**, qui la transforme en `<iframe>`.

1. Assurez-vous que le bloc Incorporer existe dans votre projet.

   Si votre projet EDS n’inclut pas déjà le bloc Incorporer, copiez-le à partir du référentiel aem-block-collection :

   ```cmdline
   # From the aem-block-collection repo, copy blocks/embed/ into your project's blocks/ directory
   cp -r aem-block-collection/blocks/embed/ your-eds-project/blocks/embed/
   ```

1. Créez le code incorporé dans l’éditeur de création de documents (dans Edge Delivery Services).

   Dans la création de documents, les blocs sont représentés sous la forme de tableaux. Pour ajouter un élément visuel Incorporer un fragment de contenu :

   | incorporer |
   |--- |
   | (collez l’URL de publication sous forme de lien hypertexte) |

   Si votre projet ou Sidekick est configuré avec le bloc Incorporer dans sa bibliothèque de blocs, vous pouvez également l’insérer via le menu barre oblique et coller l’URL de publication dans le contenu du bloc.

1. Résultat

   Le bloc Incorporer effectue le rendu de l’URL de publication dans une `<iframe>`. Le contenu du fragment se charge dans une isolation CSS complète dans la mise en page EDS.

## Intégration - AEM Sites avec les composants principaux {#integration-aem-sites-with-core-components}

Le composant principal Fragment de contenu (`core/wcm/components/contentfragment/v1/contentfragment`) offre une prise en charge intégrée du rendu des fragments de contenu visuels à l’aide de la technique [Élément client + DOM fantôme](#custom-element-and-shadow-dom-recommended).

Fonctionnement :

* Mode de création :

  Lorsque la `displayMode` du composant est définie sur `vcf`, la bibliothèque cliente de création (`vcfRenderer.js`) récupère le fragment HTML à partir de l’API d’aperçu et le rend intégré dans la zone de travail de création.

  Voici un exemple de point d’entrée d’aperçu de création :

  ```html
  GET /adobe/sites/cf/fragments/{fragmentId}/preview?templateId={templateId}&variation={variation}
  ```

* Mode de publication :

  Sur la page publiée (`wcmmode.disabled`), le modèle HTL effectue le rendu d’un script intégré qui récupère à partir de l’URL de publication et injecte l’HTML dans une racine DOM fantôme.

  Exemple de fragment de contenu visuel de composant principal (templates.html) :

  ```html
  <div class="cmp-contentfragment cmp-contentfragment--vcf"
     data-cmp-contentfragment-id="{fragmentId}"
     data-cmp-contentfragment-vcf-template="{templateId}"
     data-cmp-contentfragment-variation="{variation}">
    <!-- Only rendered when wcmmode.disabled (publish) -->
    <div data-vcf-url="{vcfPublishUrl}" class="cmp-contentfragment__vcf-loader" style="display:none"></div>
    <script>
        (function() {
            var script = document.currentScript;
            var loader = script.previousElementSibling;
            var el = script.parentElement;
            if (!el || !loader) return;
            var url = loader.dataset.vcfUrl;
            if (!url) return;
            loader.remove();
            var shadow = el.attachShadow({ mode: "open" });
            var body = document.createElement("body");
            body.style.display = "none";
            shadow.appendChild(body);
            fetch(url)
                .then(function(r) { return r.ok ? r.text() : Promise.reject(r.status); })
                .then(function(html) {
                    body.innerHTML = html;
                    body.style.display = "";
                });
        })();
    </script>
  </div>
  ```

  Format de l’URL de publication :

  Le modèle Sling (`ContentFragmentImpl`) crée l’URL de publication selon le modèle suivant :

  ```html
  /adobe/experimental/previewtemplates-expires-20260301/contentFragments/{templateId}/{fragmentId}/{variation}.html
  ```

  Cette URL relative est résolue sur l’hôte de publication au moment de l’exécution.

## Intégration à des sites externes {#integration-with-external-sites}

Pour les sites web autres qu’AEM, utilisez la technique [Élément client + Shadow DOM](#custom-element-and-shadow-dom-recommended). Vous obtenez ainsi une intégration propre et déclarative sans dépendances de framework.

Voici un exemple :

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Product Page</title>
</head>
<body>
  <h1>Product Details</h1>
  <p>Some host-page content here...</p>

  <!-- Embed the Content Fragment visualization -->
  <cf-visualization
    src="https://publish-p12345-e67890.adobeaemcloud.com/adobe/experimental/previewtemplates-expires-20260301/contentFragments/product_template/abc-123/master.html"
  ></cf-visualization>

  <p>More host-page content below the fragment...</p>

  <!-- Custom Element definition (include once) -->
  <script>
    class CfVisualization extends HTMLElement {
      connectedCallback() {
        const src = this.getAttribute("src");
        if (!src) return;
        const shadow = this.attachShadow({ mode: "open" });
        fetch(src)
          .then(r => r.ok ? r.text() : Promise.reject(r.status))
          .then(html => { shadow.innerHTML = html; })
          .catch(err => console.error("cf-visualization: failed to load", src, err));
      }
    }
    if (!customElements.get("cf-visualization")) {
      customElements.define("cf-visualization", CfVisualization);
    }
  </script>
</body>
</html>
```

>[!NOTE]
>
>Vous pouvez placer plusieurs éléments de `<cf-visualization>` sur la même page avec différentes URL `src`. La définition de l’élément personnalisé ne doit être incluse qu’une seule fois.

## Considérations CORS et de sécurité {#cors-and-security-considerations}

| Préoccupation | Détails |
|--- |--- |
| CORS | Le service de visualisation de fragment de contenu configure CORS sur le chemin d’accès `/adobe/**` avec des origines autorisées configurables.<br>Les techniques [Élément intégré (fetch + innerHTML)](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#inline-element-fetch-and-innerhtml) 1 et [Élément client + Shadow DOM](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#custom-element-and-shadow-dom-recommended) (qui utilisent `fetch()`) nécessitent que l’origine de la page hôte soit dans la liste autorisée. <br>La technique [iFrame](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#iframe) ne nécessite pas de CORS. |
| CSP/X-Frame-Options | Le service ne définit pas d’en-têtes `Content-Security-Policy` ou `X-Frame-Options` sur l’HTML publiée. Si le réseau de diffusion de contenu ou Dispatcher ajoute ces en-têtes, vérifiez qu’ils autorisent le cadrage (pour [iFrame](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#iframe)) ou l’accès `fetch()` (pour les DOM intégrés/fantômes) à partir des origines de votre hôte. |
| Fiabilité du contenu | L’HTML publiée est prérendue à partir des données de fragment de contenu créées à l’aide de [modèles Handlebars](/help/implementing/developing/extending/content-fragments-visualization-templates.md) gérés par le service. Il n’inclut pas les scripts générés par l’utilisateur. Cependant, comme pour toute injection HTML interne, assurez-vous de faire confiance à l’origine source. |

### Choisir la technique appropriée {#choose-the-appropriate-technique}

Utilisez les éléments suivants comme guide de décision pour choisir la technique appropriée :

| Scénario | Solution |
|--- |--- |
| Besoin de zéro JavaScript et d&#39;un isolement complet ? | Iframe |
| Besoin d’une participation au flux de mise en page avec isolation de style ? | Élément personnalisé + DOM fantôme (recommandé) |
| Besoin que les conflits de prototype, de même origine et CSS les plus rapides soient acceptables ? | Élément intégré |
| Intégration dans Edge Delivery Services ? | Bloc intégré (iframe sous le capot) |
| Incorporation dans des pages AEM Sites ? | Composant principal (Shadow DOM, intégré) |


## Ressources supplémentaires {#additional-resources}

Des ressources supplémentaires sont disponibles :

* [Documentation sur les fragments de contenu AEM](/help/sites-cloud/administering/content-fragments/overview.md)

* [API de modèles de visualisation de fragments de contenu](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/cvt/)
