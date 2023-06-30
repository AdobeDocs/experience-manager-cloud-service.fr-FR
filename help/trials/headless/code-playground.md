---
title: Rendu de votre contenu dans une application simple
description: Explorez la récupération de contenu JSON à partir de votre environnement d’évaluation à l’aide d’un exemple d’application CodePen et du client AEM Headless pour JavaScript.
hidefromtoc: true
index: false
exl-id: b7dc70f2-74a2-49f7-ae7e-776eab9845ae
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 55%

---


# Rendu de votre contenu dans une application simple {#render-content-simple-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="Rendre votre contenu dans une application simple"
>abstract="Explorez la récupération de contenu JSON à partir de votre environnement d’évaluation à l’aide d’un exemple d’application CodePen et du client AEM Headless pour JavaScript."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="Lancer l’exemple d’application CodePen"
>abstract="Ce guide explique en détail comment interroger des données JSON de votre environnement d’évaluation dans une application web JavaScript de base. Vous utilisez les fragments de contenu que vous avez modélisés et créés dans les modules d’apprentissage précédents. Au besoin, consultez ces guides avant de passer à celui-ci."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="Dans ce module, vous avez appris à utiliser le client AEM Headless pour JavaScript afin de récupérer les données JSON de votre environnement d’évaluation à l’aide de requêtes GraphQL persistantes.<br><br>Vous comprenez maintenant comment utiliser ce client pour utiliser les données de votre propre application web."
>abstract=""

## CodePen {#codepen}

CodePen est un éditeur de code en ligne et un terrain de jeu pour le développement web front-end. Il vous permet d’écrire du code HTML, CSS et JavaScript dans votre navigateur et de voir presque instantanément les résultats de votre travail. Vous pouvez également enregistrer votre travail et le partager avec d’autres personnes. Adobe a créé une application dans CodePen que vous pouvez utiliser pour récupérer les données JSON de votre environnement d’évaluation à l’aide de la fonction [AEM client sans affichage pour JavaScript](https://github.com/adobe/aem-headless-client-js). Vous pouvez utiliser cette application en l’état ou la dupliquer dans votre compte CodePen pour la personnaliser davantage.

Cliquez sur le bouton **Lancement de l’exemple d’application CodePen** à partir du test, vous accédez à l’application dans CodePen. L’application sert d’exemple minimal pour récupérer des données JSON avec JavaScript. L’exemple d’application est conçu pour effectuer le rendu de tout contenu JSON renvoyé, quelle que soit la structure du modèle de fragment de contenu sous-jacent. Par défaut, l’application récupère les données d’une `aem-demo-assets` requête persistante incluse dans votre environnement d’évaluation. Vous devriez voir une réponse JSON similaire à ce qui suit :

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

Si une erreur s’affiche à la place de cette réponse, recherchez plus de détails dans la console du navigateur ou contactez des personnes [sur Slack](https://adobe-dx-support.slack.com).

Maintenant que vous connaissez un peu CodePen, vous allez configurer l’application pour récupérer les données de la requête persistante que vous avez créée dans un module précédent.

## Présentation du code JavaScript {#code-walkthrough}

Le **JS** Le volet situé à droite de CodePen contient le code JavaScript de l’exemple d’application. À partir de la ligne 2, vous importez le client AEM sans affichage pour JavaScript à partir du réseau de diffusion de contenu Skypack. Nous utilisons Skypack pour faciliter le développement sans étape de création, mais vous pouvez également utiliser le client AEM Headless avec NPM ou Yarn dans vos propres projets. Consultez les instructions d’utilisation dans la section [LISEZ-MOI](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript) pour plus de détails.

```javascript
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

Sur la ligne 6, les détails de votre hôte de publication ont été lus à partir du `publishHost` paramètre de requête. Ce paramètre est l’hôte à partir duquel le client AEM sans affichage récupère les données. Cette fonctionnalité est généralement codée dans votre application, mais vous utilisez un paramètre de requête pour faciliter le travail de l’application CodePen avec différents environnements.

Configurez le client AEM sans affichage à la ligne 12 :

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
>Le **serviceURL** est défini pour utiliser une fonction Adobe I/O Runtime proxy afin d’éviter les problèmes de CORS. Ce proxy n’est pas nécessaire pour vos propres projets, mais il est nécessaire pour que l’application CodePen fonctionne avec votre environnement d’évaluation. La fonction proxy est configurée pour utiliser la valeur **publishHost** qui a été fournie dans le paramètre de requête.

Enfin, la fonction `fetchJsonFromGraphQL()` sert à effectuer la requête de récupération à l’aide du client AEM Headless. Elle est appelée chaque fois que le code est modifié, ou peut être déclenchée en cliquant sur le lien **Récupérer à nouveau**. L’appel de `aemHeadlessClient.runPersistedQuery(..)` se produit à la ligne 34. Un peu plus tard, vous modifiez le mode de rendu de ces données JSON, mais vous pouvez désormais les imprimer sur la page `#output` div à l’aide de `resultToPreTag(queryResult)` fonction .

## Récupérer des données à partir de votre requête persistante {#use-persisted-query}

Sur la ligne 25, vous indiquez à partir de quelle requête GraphQL persistante l’application doit récupérer les données. Le nom de la requête persistante est une combinaison du nom du point de terminaison (c’est-à-dire : `your-project` ou `aem-demo-assets`), suivie d’une barre oblique, puis du nom de la requête. Si vous avez suivi exactement les instructions précédentes du module, la requête que vous avez créée est dans la variable `your-project` point de terminaison .

1. Mettez à jour le `persistedQueryName` afin qu’elle utilise la requête persistante que vous avez créée dans le module précédent. Si vous avez suivi la suggestion de dénomination, vous avez créé une requête persistante nommée `adventure-list` dans le point d’entrée `your-project`, et vous avez défini la variable `persistedQueryName` sur `your-project/adventure-list` :

   ```javascript
   //
   // TODO: Use your persisted query here
   //
   persistedQueryName = 'your-project/adventure-list';
   ```

1. Une fois cette modification effectuée, l’application doit automatiquement s’actualiser et imprimer la réponse JSON brute de votre requête persistante vers le div `#output`. Si un message d’erreur s’affiche, recherchez des détails supplémentaires dans la console. Contactez des personnes [sur Slack](https://adobe-dx-support.slack.com) si vous rencontrez toujours des problèmes avec cette étape.

1. Ce fichier JSON contient-il les propriétés exactes dont votre application a besoin ? Si ce n’est pas le cas, revenez au guide d’apprentissage [Extraction de contenu à l’aide de l’API GraphQL](https://experience.adobe.com/experiencemanager/learn/extract_content_using_graphql) pour apporter des modifications. N’oubliez pas d’enregistrer et de publier votre requête une fois que vous avez terminé.

## Modification du rendu JSON {#change-rendering}

Le fichier JSON est rendu tel quel dans une `pre` , qui n’est pas trop créative. Vous pouvez changer CodePen pour utiliser la variable `resultToDom()` pour illustrer comment la réponse JSON peut être itérée afin de créer un résultat plus intéressant.

1. Pour apporter cette modification, commentez la ligne 37 et supprimez le commentaire de la ligne 40 :

   ```javascript
   // Output the results to a pre tag
   //resultToPreTag(queryResult);
   
   // Alternatively, build a colorful div structure with the JSON results and render images inline
   resultToDom(queryResult);
   ```

1. Cette fonction effectue le rendu des images incluses dans la réponse JSON en tant que `img` balise . Si les fragments de contenu **Adventure** que vous avez créés n’incluent pas d’images, vous pouvez essayer de basculer pour utiliser la requête persistante `aem-demo-assets/adventures-all` en modifiant la ligne 25 :

   ```javascript
   persistedQueryName = 'aem-demo-assets/adventures-all';
   ```

Cette requête génère une réponse JSON qui inclut des images et la variable `resultToDom()` les rend en ligne.

![Résultat de la requête aventures-all et de la fonction de rendu resultToDom](assets/do-not-localize/adventures-all-query-result.png)

Maintenant que vous avez terminé le travail de création des modèles et des requêtes, votre équipe de contenu peut prendre le relais facilement. Dans le module suivant, vous affichez le flux de l’auteur de contenu.
