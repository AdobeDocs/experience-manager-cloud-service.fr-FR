---
title: Extraction de contenu via l’API GraphQL
description: Découvrez comment utiliser les fragments de contenu et l’API GraphQL en tant que système de gestion de contenu headless.
hidefromtoc: true
index: false
exl-id: f5e379c8-e63e-41b3-a9fe-1e89d373dc6b
source-git-commit: bcab02cbd84955ecdc239d4166ae38e5f79b3264
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---


# Extraction de contenu via l’API GraphQL {#extract-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql"
>title="Extraction de contenu à l’aide de l’API GraphQL"
>abstract="Dans ce module, vous découvrez comment utiliser les fragments de contenu et l’API GraphQL en tant que système de gestion de contenu sans interface."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide"
>title="Lancement de GraphQL Explorer"
>abstract="GraphQL fournit une API basée sur les requêtes qui permet aux applications clientes externes d’interroger AEM uniquement pour le contenu dont elles ont besoin, à l’aide d’un seul appel API. Suivez ce module pour savoir comment exécuter deux types de requêtes différents. Découvrez ensuite comment récupérer le contenu du fragment de contenu que vous avez créé dans le module précédent.<br><br>Lancez ce module dans un nouvel onglet en cliquant ci-dessous."
>additional-url="https://video.tv.adobe.com/v/328618" text="Vidéo Extraction d’une entrée de contenu"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide_footer"
>title="Beau travail ! Vous avez appris les deux types de requêtes de base et comment interroger votre propre contenu. Vous comprenez désormais comment utiliser l’API GraphQL d’AEM pour créer des requêtes efficaces qui diffusent le contenu dans un format que vous attendez de l’application."
>abstract=""

## Requête pour une liste d’exemples de contenu {#list-query}

Cliquez sur le bouton **Lancement de GraphQL Explorer** Le bouton ci-dessus ouvre l’Explorateur GraphQL dans un nouvel onglet.

![GraphQL Query Editor](assets/extract-content/query-editor.png)

L’Explorateur GraphQL vous permet de créer et de valider des requêtes par rapport à votre contenu headless avant de les utiliser pour alimenter le contenu de votre application ou de votre site web. Voyons comment c&#39;est fait !

1. Votre AEM essai sans interface est fourni avec un point de terminaison préchargé avec des fragments de contenu à partir duquel vous pouvez extraire du contenu à des fins de test. Sélectionnez la **AEM des ressources de démonstration** point d’entrée à partir de la fonction **Point d’entrée** menu déroulant dans le coin supérieur droit de l’éditeur.

   ![Sélectionner le point de fin](assets/extract-content/select-endpoint.png)

1. Copiez le fragment de code suivant pour une requête de liste du préchargé. **AEM des ressources de démonstration** point de terminaison . Une requête de liste renvoie une liste de tout le contenu qui utilise un modèle de fragment de contenu spécifique. Les pages de stock et de catégorie utilisent généralement ce format de requête.

   ```text
   {
       adventureList {
         items {
            _path
            adventureTitle
            adventurePrice
            adventureTripLength
            adventurePrimaryImage {
              ... on ImageRef {
               _path
               mimeType
               width
               height
             }
           }
         }
      }
    }
   ```

1. Remplacez le contenu existant dans l’éditeur de requêtes en collant le code copié.

   ![Requête de liste](assets/extract-content/list-query.png)

1. Une fois collé, cliquez sur le bouton **Play** en haut à gauche de l’éditeur de requêtes pour exécuter la requête.

1. Les résultats s’affichent dans le panneau de droite, en regard de l’éditeur de requêtes. Si la requête est incorrecte, une erreur s’affiche dans le panneau de droite.

   ![Liste des résultats de requête](assets/extract-content/list-query-results.png)

Vous venez de valider une requête de liste pour obtenir une liste complète de tous les fragments de contenu. Ce processus permet de s’assurer que la réponse correspond à l’attente de votre application, avec des résultats qui illustrent la manière dont vos applications et sites web récupéreront le contenu créé dans AEM.

## Requête pour un élément spécifique de contenu d’exemple {#bypath-query}

L’exécution d’une requête byPath vous permet de récupérer du contenu pour un fragment de contenu spécifique. Les pages Détails du produit et les pages qui se concentrent sur un ensemble spécifique de contenu nécessitent généralement ce type de requête. Voyons comment ça marche !

1. Copiez le fragment de code suivant pour une requête byPath du préchargé. **AEM des ressources de démonstration** point de terminaison .

   ```text
    {
     adventureByPath(
       _path: "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp"
     ) {
       item {
         _path
         adventureTitle
         adventureDescription {
           json
         }
         adventurePrimaryImage {
           ... on ImageRef {
             _path
             width
             height
           }
         }
       }
     }
   }
   ```

1. Remplacez le contenu existant dans l’éditeur de requêtes en collant le code copié.

   ![requête byPath](assets/extract-content/bypath-query.png)

1. Une fois collé, cliquez sur le bouton **Play** en haut à gauche de l’éditeur de requêtes pour exécuter la requête.

1. Les résultats s’affichent dans le panneau de droite, en regard de l’éditeur de requêtes. Si la requête est incorrecte, une erreur s’affiche dans le panneau de droite.

   ![résultats de la requête byPath](assets/extract-content/bypath-query-results.png)

Vous venez de valider une requête byPath pour récupérer un fragment de contenu spécifique identifié par le chemin d’accès de ce fragment.

## Interrogation de votre propre contenu {#own-queries}

Maintenant que vous avez exécuté les deux Principaux types de requêtes, vous êtes prêt à interroger votre propre contenu !

1. Pour exécuter des requêtes sur vos propres fragments de contenu, modifiez le point de terminaison à partir du **AEM des ressources de démonstration** vers le dossier **Votre projet** dossier.

   ![Sélectionner votre propre point de terminaison](assets/extract-content/select-endpoint.png)

1. Supprimez tout le contenu existant dans l&#39;éditeur de requêtes. Saisissez ensuite un crochet ouvert. `{` et appuyez sur Ctrl+Espace ou Option+Espace pour obtenir la liste à saisie automatique des modèles définis dans votre point de terminaison. Sélectionnez le modèle que vous avez créé et qui se termine par `List` dans les options.

   ![Modèles de saisie automatique dans l’éditeur de requêtes](assets/extract-content/auto-complete-models.png)

1. Définissez les éléments que la requête doit contenir pour le modèle de fragment de contenu que vous avez sélectionné. Encore une fois, tapez crochet ouvert. `{`, puis appuyez sur Ctrl+Espace ou Option+Espace pour obtenir une liste à saisie automatique. Sélectionner `items` dans les options.

   ![Remplissage automatique des éléments dans l’éditeur de requêtes](assets/extract-content/auto-complete-items.png)

1. Définissez les champs que la requête doit contenir pour le modèle de fragment de contenu que vous avez sélectionné. Une fois de plus, saisissez un crochet ouvert. `{`, puis appuyez sur Ctrl+Espace ou Option+Espace pour obtenir une liste de saisie automatique des champs disponibles dans le modèle de fragment de contenu. Sélectionnez dans la liste les champs de votre modèle.

   ![Remplir automatiquement les champs dans l’éditeur de requêtes](assets/extract-content/auto-complete-fields.png)

1. Délimitez plusieurs champs à l’aide d’une virgule (`,`) ou espace et appuyez à nouveau sur Ctrl+Espace ou Option+Espace pour sélectionner des champs supplémentaires.

1. Au fur et à mesure que vous travaillez, vous pouvez appuyer ou cliquer sur le bouton **Prettify** pour formater automatiquement votre code afin qu’il soit plus facile à lire.

   ![Prettify](assets/extract-content/prettify.png)

1. Une fois l’opération terminée, appuyez ou cliquez sur l’icône **Play** en haut à gauche de l’éditeur pour exécuter la requête.

   ![Résultats de votre propre requête](assets/extract-content/custom-query-results.png)

1. Les résultats s’affichent dans le panneau de droite, en regard de l’éditeur de requêtes.

C’est ainsi que votre contenu peut être diffusé aux expériences numériques omnicanal.
