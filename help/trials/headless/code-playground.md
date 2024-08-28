---
title: Rendre votre contenu dans une application simple
description: Explorez la récupération de contenu JSON à partir de votre environnement d’évaluation à l’aide d’un exemple d’application CodePen et du client AEM Headless pour JavaScript.
hidefromtoc: true
index: false
exl-id: b7dc70f2-74a2-49f7-ae7e-776eab9845ae
feature: Headless
role: Admin, User, Developer
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 100%

---


# Rendre votre contenu dans une application simple {#render-content-simple-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="Rendre votre contenu dans une application simple"
>abstract="Explorez la récupération de contenu JSON à partir de votre environnement d’évaluation à l’aide d’un exemple d’application CodePen et du client AEM Headless pour JavaScript."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="Lancer l’exemple d’application CodePen"
>abstract="Ce guide explique en détail la façon dont interroger des données JSON de votre environnement d’évaluation dans une application web JavaScript de base. Vous utilisez les fragments de contenu que vous avez modélisés et créés dans les modules de formation précédents. Au besoin, consultez ces guides avant de passer à celui-ci."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="Dans ce module, vous avez appris à utiliser le client AEM Headless pour JavaScript afin de récupérer les données JSON de votre environnement d’évaluation à l’aide de requêtes GraphQL persistantes.<br><br>Vous comprenez maintenant comment utiliser ce client pour utiliser les données de votre propre application web."
>abstract=""

## CodePen {#codepen}

CodePen est un éditeur de code en ligne et un terrain de jeu pour le développement web front-end. Il vous permet d’écrire du code HTML, CSS et JavaScript dans votre navigateur et d’afficher les résultats de votre travail presque instantanément. Vous pouvez également enregistrer votre travail et le partager avec d’autres personnes. Adobe a créé une application dans CodePen que vous pouvez utiliser pour récupérer des données JSON de votre environnement d’évaluation à l’aide du [client AEM Headless pour JavaScript](https://github.com/adobe/aem-headless-client-js). Vous pouvez utiliser cette application en l’état ou la dupliquer dans votre compte CodePen pour la personnaliser davantage.

Cliquez sur le bouton **Lancement de l’exemple d’application CodePen** à partir de l’évaluation pour accéder à l’application dans CodePen. L’application sert d’exemple minimal pour récupérer des données JSON avec JavaScript. L’exemple d’application est conçu pour effectuer le rendu de tout contenu JSON renvoyé, quelle que soit la structure du modèle de fragment de contenu sous-jacent. Par défaut, l’application récupère les données d’une requête persistante `aem-demo-assets` incluse dans votre environnement d’évaluation. Vous devriez voir une réponse JSON similaire à ce qui suit :

```json
{
  "data": {
    "adventureList": {
      "items": [
        {
          "_path": "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp",
          "title": "Bali Surf Camp",
          "price": "$5000 USD",
          ...
```

Si une erreur s’affiche à la place de cette réponse, recherchez plus de détails dans la console du navigateur ou contactez l’assistance [par e-mail](mailto:aem-headless-trials-support@adobe.com?subject=AEM%20Trials%20support%20request).

Maintenant que vous connaissez un peu CodePen, vous allez configurer l’application pour récupérer les données de la requête persistante que vous avez créée dans un module précédent.

## Présentation du code JavaScript {#code-walkthrough}

Le panneau **JS** situé à droite dans CodePen contient le code JavaScript de l’exemple d’application. À partir de la ligne 2, vous importez le client AEM Headless pour JavaScript à partir du réseau CDN Skypack. Nous utilisons Skypack pour faciliter le développement sans étape de création, mais vous pouvez également utiliser le client AEM Headless avec NPM ou Yarn dans vos propres projets. Consultez les instructions d’utilisation dans la section [LISEZ-MOI](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript) pour plus de détails.

```javascript
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

Sur la ligne 6, les détails de votre hôte de publication ont été lus à partir du paramètre de requête `publishHost`. Ce paramètre est l’hôte à partir duquel le client AEM Headless récupère les données. Cette fonctionnalité est généralement codée dans votre application, mais vous utilisez un paramètre de requête pour faciliter le fonctionnement de l’application CodePen avec différents environnements.

Vous configurez le client AEM Headless à la ligne 12 :

```javascript
const aemHeadlessClient = new AdobeAemHeadlessClientJs({
  // Use a proxy to avoid CORS issues
  serviceURL: 'https://102588-505tanocelot.adobeioruntime.net/api/v1/web/aem/proxy',
  headers: {
    'aem-url': publishHost
  }
});
```

>[!NOTE]
>
>**serviceURL** est défini pour utiliser une fonction d’exécution Adobe IO par proxy afin d’éviter les problèmes de CORS. Ce proxy n’est pas nécessaire pour vos propres projets, mais il permet ici que l’application CodePen fonctionne avec votre environnement d’évaluation. La fonction proxy est configurée pour utiliser la valeur **publishHost** qui a été fournie dans le paramètre de requête.

Enfin, la fonction `fetchJsonFromGraphQL()` sert à effectuer la requête de récupération à l’aide du client AEM Headless. Elle est appelée chaque fois que le code est modifié, ou peut être déclenchée en cliquant sur le lien **Récupérer à nouveau**. L’appel de `aemHeadlessClient.runPersistedQuery(..)` se produit à la ligne 34. Vous modifiez un peu plus tard le rendu de ces données JSON, mais pour l’instant, imprimez-les sur le div `#output` à l’aide de la fonction `resultToPreTag(queryResult)`.

## Récupérer des données à partir de votre requête persistante {#use-persisted-query}

Sur la ligne 25, vous indiquez à partir de quelle requête GraphQL persistante l’application doit récupérer les données. Le nom de la requête persistante est une combinaison du nom du point d’entrée (c’est-à-dire `your-project` ou `aem-demo-assets`), suivie d’une barre oblique, puis du nom de la requête. Si vous avez suivi à la lettre les instructions du module précédent, la requête persistante que vous avez créée se trouve dans le point d’entrée `your-project`.

1. Mettez à jour la variable `persistedQueryName` pour qu’elle utilise la requête persistante que vous avez créée dans le module précédent. Si vous avez suivi la suggestion de dénomination, vous avez créé une requête persistante nommée `adventure-list` dans le point d’entrée `your-project`, et vous avez défini la variable `persistedQueryName` sur `your-project/adventure-list` :

   ```javascript
   //
   // TODO: Use your persisted query here
   //
   persistedQueryName = 'your-project/adventure-list';
   ```

1. Une fois cette modification effectuée, l’application doit automatiquement s’actualiser et imprimer la réponse JSON brute de votre requête persistante vers le div `#output`. Si un message d’erreur s’affiche, recherchez des détails supplémentaires dans la console. Contactez l’assistance [par e-mail](mailto:aem-headless-trials-support@adobe.com?subject=AEM%20Trials%20support%20request) si vous rencontrez toujours des problèmes avec cette étape.

1. Ce fichier JSON contient-il les propriétés exactes dont votre application a besoin ? Si ce n’est pas le cas, revenez au guide d’apprentissage [Extraction de contenu à l’aide de l’API GraphQL](https://experience.adobe.com/experiencemanager/learn/extract_content_using_graphql) pour apporter des modifications. N’oubliez pas d’enregistrer et de publier votre requête une fois que vous avez terminé.

## Modification du rendu JSON {#change-rendering}

Le fichier JSON est rendu tel quel dans une balise `pre`, ce qui n’est pas très créatif. Vous pouvez changer le CodePen pour utiliser la fonction `resultToDom()` afin d’illustrer la façon dont la réponse JSON peut être itérée pour créer un résultat plus intéressant.

1. Pour apporter cette modification, commentez la ligne 37 et supprimez le commentaire de la ligne 40 :

   ```javascript
   // Output the results to a pre tag
   //resultToPreTag(queryResult);
   
   // Alternatively, build a colorful div structure with the JSON results and render images inline
   resultToDom(queryResult);
   ```

1. Cette fonction effectue le rendu de toutes les images incluses dans la réponse JSON sous la forme d’une balise `img`. Si les fragments de contenu **Adventure** que vous avez créés n’incluent pas d’images, vous pouvez essayer de basculer pour utiliser la requête persistante `aem-demo-assets/adventures-all` en modifiant la ligne 25 :

   ```javascript
   persistedQueryName = 'aem-demo-assets/adventures-all';
   ```

Cette requête génère une réponse JSON qui inclut des images, et la fonction `resultToDom()` effectue leur rendu en ligne.

![Résultat de la requête aventures-all et de la fonction de rendu resultToDom](assets/do-not-localize/adventures-all-query-result.png)

Maintenant que vous avez terminé le travail de création des modèles et des requêtes, votre équipe de contenu peut prendre le relais facilement. Dans le module suivant, vous affichez le flux du créateur ou de la créatrice de contenu.
