---
title: Récupération du contenu JSON avec JavaScript
description: Explorez la récupération de contenu JSON à partir de votre environnement d’évaluation à l’aide d’une application CodePen et du client AEM sans affichage pour JavaScript.
hidefromtoc: true
index: false
source-git-commit: 3aff5ef2fb9ecdd815f0bc1a813d3a3982b4e0ed
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 1%

---


# Récupération du contenu JSON avec JavaScript {#fetch-json}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="Récupération du contenu JSON avec JavaScript"
>abstract="Explorez la récupération de contenu JSON à partir de votre environnement d’évaluation à l’aide d’une application CodePen et du client AEM sans affichage pour JavaScript."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="Lancement de l’exemple d’application CodePen"
>abstract="Nous avons créé une application CodePen minimale pour introduire la récupération des données JSON de votre environnement d’évaluation à l’aide de requêtes persistantes GraphQL.<br><br>Lancez l’exemple CodePen en cliquant ci-dessous, puis suivez ce guide pour en savoir plus."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="Dans ce module, vous avez appris à utiliser le client AEM sans affichage pour JavaScript pour récupérer les données JSON de votre environnement d’évaluation à l’aide de requêtes persistantes GraphQL.<br><br>Vous comprenez maintenant comment utiliser ce client pour utiliser les données de votre propre application web."
>abstract=""

## Présentation {#intro}

Vous commencez par l’application CodePen, qui sert d’exemple minimal de récupération des données JSON à l’aide de la variable [AEM client sans affichage pour JavaScript](https://github.com/adobe/aem-headless-client-js). L’exemple d’application est conçu pour effectuer le rendu de tout contenu JSON renvoyé, quelle que soit la structure du modèle de fragment de contenu sous-jacent. L’application CodePen tente d’être détaillée avec les erreurs rencontrées. Vous pouvez donc voir le message d’erreur suivant imprimé dans le volet inférieur de l’application :

```
{
  "status": "Failed to fetch persisted query: your-project/USE-YOUR-QUERY-HERE from publishHost: https://publish-p00000-e12345.adobeaemcloud.com",
  "message": "[AEMHeadless:REQUEST_ERROR] General Request error: Failed to fetch."
}
```

Cette erreur est attendue, car l’application n’est pas encore configurée pour utiliser la requête persistante que vous avez enregistrée et publiée dans un module précédent. Vous allez configurer l’application pour récupérer les données de votre requête spécifique dans les étapes suivantes.

## Présentation détaillée de CodePen {#code-walkthrough}

Le volet JS (JavaScript) sur CodePen contient les cerveaux de l’exemple d’application. À partir de la ligne 2, nous importons le client AEM sans affichage pour JavaScript à partir du réseau de diffusion de contenu Skypack. Skypack est utilisé pour faciliter le développement sans étape de génération, mais vous pouvez également utiliser le client AEM sans tête avec NPM ou Yarn dans vos propres projets. Consultez les instructions d’utilisation dans la section [LISEZMOI](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript) pour plus de détails.

```
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

Sur la ligne 6, nous lisons les détails de votre hôte de publication à partir de la variable `publishHost` paramètre de requête. Il s’agit de l’hôte à partir duquel le client AEM sans affichage récupérera des données. Cela est généralement codé dans votre application, mais nous utilisons un paramètre de requête pour faciliter le travail de l’application CodePen avec différents environnements.

Nous configurons le client AEM sans affichage sur la ligne 12 afin d’utiliser une fonction d’exécution d’Adobe E/S pour proxy afin d’éviter des problèmes de CORS. Cela n’est pas nécessaire pour vos propres projets, mais il l’est pour que l’application CodePen fonctionne avec votre environnement d’évaluation. La fonction proxy est configurée pour utiliser la fonction `publishHost` qui a été fournie dans le paramètre de requête.

```
const aemHeadlessClient = new AdobeAemHeadlessClientJs({
  // Use a proxy to avoid CORS issues
  serviceURL: 'https://102588-505tanocelot.adobeioruntime.net/api/v1/web/aem/proxy',
  headers: {
    'aem-url': publishHost
  }
});
```

Enfin, la fonction `fetchJsonFromGraphQL()` est utilisé pour effectuer la requête de récupération à l’aide du client AEM sans affichage. Il est appelé chaque fois que le code est modifié ou peut être déclenché en appuyant sur le lien &quot;Récupérer&quot;. Le réel `aemHeadlessClient.runPersistedQuery(..)` appel se produit à la ligne 34. Un peu plus tard, nous apporterons une modification à la manière dont ces données JSON sont rendues, mais pour l’instant, nous allons simplement les imprimer sur la page `#output` div à l’aide de `resultToPreTag(queryResult)` fonction .

## Récupérer les données de votre requête persistante {#use-persisted-query}

Sur la ligne 25, nous indiquons à partir de quelle requête GraphQL persistante l’application doit récupérer les données. Le nom de la requête persistante est une combinaison du nom du projet (c.-à-d. `your-project`), suivie d’une barre oblique, puis du nom de la requête.

Mettez à jour le `persistedQueryName` pour utiliser la requête persistante que vous avez créée dans le module précédent. Si vous avez suivi la suggestion de dénomination exactement, vous avez créé une requête conservée nommée `adventures` dans le `your-project` et vous définiriez la variable `persistedQueryName` vers `your-project/adventures`:

```
//
// TODO: Use your persisted query here
//
persistedQueryName = 'your-project/adventures';
```

Une fois cette modification effectuée, l’application doit automatiquement s’actualiser et imprimer la réponse JSON brute de votre requête persistante vers le `#output` div. Si un message d’erreur s’affiche, vérifiez les détails supplémentaires dans la console.

Ce fichier JSON contient-il les propriétés exactes dont votre application a besoin ? Si ce n’est pas le cas, revenez à l’environnement de création AEM, aux outils, à l’éditeur de requêtes GraphQL (ou accédez à la page `/aem/graphiql.html` path) et apportez des modifications à votre requête persistante. N’oubliez pas d’enregistrer et de publier la requête une fois que vous avez terminé.

## Modification du rendu JSON {#change-rendering}

Actuellement, le fichier JSON est rendu tel quel dans une `pre` , ce qui n’est pas très créatif. Nous pouvons changer notre codePen pour utiliser la variable `resultToDom()` pour illustrer comment la réponse JSON peut être itérée afin de créer un résultat plus intéressant.

Pour apporter cette modification, commentez la ligne 37 et supprimez le commentaire de la ligne 40 :

```
// Output the results to a pre tag
//resultToPreTag(queryResult);

// Alternatively, build a colorful div structure with the JSON results and render images inline
resultToDom(queryResult);
```

Cette fonction affiche également toutes les images incluses dans la réponse JSON sous la forme d’une `img` balise . Si les fragments de contenu &quot;Adventure&quot; que vous avez créés n’incluent pas d’images, vous pouvez essayer de basculer pour utiliser la variable `aem-demo-assets/adventures-all` requête persistante en modifiant la ligne 25 :

```
persistedQueryName = 'aem-demo-assets/adventures-all';
```

Cette requête va générer une réponse JSON qui inclut des images, et la variable `resultToDom()` les rend en ligne.

![Résultat de la requête aventures-all et de la fonction de rendu resultToDom](assets/do-not-localize/adventures-all-query-result.png)
