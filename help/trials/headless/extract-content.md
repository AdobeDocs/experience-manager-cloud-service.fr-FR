---
title: Extraction de contenu via l’API GraphQL
description: Découvrez comment utiliser les fragments de contenu et l’API GraphQL en tant que système de gestion de contenu sans interface.
hidefromtoc: true
index: false
exl-id: f5e379c8-e63e-41b3-a9fe-1e89d373dc6b
source-git-commit: 9997e0ea1d78ab2c8bab46a95a664e8537f16b13
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---


# Extraction de contenu via l’API GraphQL {#extract-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql"
>title="Extraire du contenu grâce à l’API GraphQL"
>abstract="Dans ce module, vous découvrez comment utiliser les fragments de contenu et l’API GraphQL en tant que système de gestion de contenu sans interface."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide"
>title="Lancement de GraphQL Explorer"
>abstract="GraphQL fournit une API basée sur les requêtes qui permet aux applications clientes externes d’interroger AEM uniquement pour le contenu dont elles ont besoin, à l’aide d’un seul appel API. Suivez ce module pour savoir comment exécuter deux types de requêtes différents. Découvrez ensuite comment récupérer le contenu du fragment de contenu que vous avez créé dans le module précédent.<br><br>Lancez ce module dans un nouvel onglet en cliquant ci-dessous."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_graphql_guide_footer"
>title="Beau travail ! Vous avez appris les deux types de requêtes de base et comment interroger votre propre contenu. Vous comprenez désormais comment utiliser l’API GraphQL d’AEM pour créer des requêtes efficaces qui diffusent le contenu dans un format que vous attendez de l’application."
>abstract=""

## Requête pour une liste d’exemples de contenu {#list-query}

Vous démarrez dans l’Explorateur GraphQL dans un nouvel onglet. Ici, vous pouvez créer et valider des requêtes par rapport à votre contenu headless avant de les utiliser pour alimenter le contenu de votre application ou site web.

1. Votre AEM essai sans interface est fourni avec un point de terminaison préchargé avec des fragments de contenu à partir duquel vous pouvez extraire du contenu à des fins de test. Assurez-vous que la variable **AEM des ressources de démonstration** le point de fin est sélectionné dans la variable **Point d’entrée** menu déroulant dans le coin supérieur droit de l’éditeur.

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

1. Une fois collé, cliquez sur le bouton **Play** en haut à gauche de l’éditeur de requêtes pour exécuter la requête.

1. Les résultats s’affichent dans le panneau de droite, en regard de l’éditeur de requêtes. Si la requête est incorrecte, une erreur s’affiche dans le panneau de droite.

   ![Requête de liste](assets/do-not-localize/list-query-1-3-4-5.png)

Vous venez de valider une requête de liste pour obtenir une liste complète de tous les fragments de contenu. Ce processus permet de s’assurer que la réponse correspond à l’attente de votre application, avec des résultats qui illustrent la manière dont vos applications et sites web récupéreront le contenu créé dans AEM.

## Requête pour un élément spécifique de contenu d’exemple {#bypath-query}

L’exécution d’une requête byPath vous permet de récupérer du contenu pour un fragment de contenu spécifique. Les pages Détails du produit et les pages qui se concentrent sur un ensemble spécifique de contenu nécessitent généralement ce type de requête.

1. Copiez le fragment de code suivant pour une requête byPath du préchargé. **AEM des ressources de démonstration** point de terminaison .

   ```text
    {
     adventureByPath(
       _path: "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp"
     ) {
       item {
         _path
         title
         description {
           json
         }
         primaryImage {
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

1. Une fois collé, cliquez sur le bouton **Play** en haut à gauche de l’éditeur de requêtes pour exécuter la requête.

1. Les résultats s’affichent dans le panneau de droite, en regard de l’éditeur de requêtes. Si la requête est incorrecte, une erreur s’affiche dans le panneau de droite.

   ![résultats de la requête byPath](assets/do-not-localize/bypath-query-2-3-4.png)

Vous venez de valider une requête byPath pour récupérer un fragment de contenu spécifique identifié par le chemin d’accès de ce fragment.

## Interrogation de votre propre contenu {#own-queries}

Maintenant que vous avez exécuté les deux Principaux types de requêtes, vous êtes prêt à interroger votre propre contenu.

1. Pour exécuter des requêtes sur vos propres fragments de contenu, modifiez le point de terminaison à partir du **AEM des ressources de démonstration** vers le dossier **Votre projet** dossier.

1. Supprimez tout le contenu existant dans l&#39;éditeur de requêtes. Saisissez ensuite un crochet ouvert. `{` et appuyez sur Ctrl+Espace ou Option+Espace pour obtenir la liste à saisie automatique des modèles définis dans votre point de terminaison. Sélectionnez le modèle que vous avez créé et qui se termine par `List` dans les options.

   ![Démarrage d’une requête personnalisée](assets/do-not-localize/custom-query-1-2.png)

1. Définissez les éléments que la requête doit contenir pour le modèle de fragment de contenu que vous avez sélectionné. Encore une fois, tapez crochet ouvert. `{`, puis appuyez sur Ctrl+Espace ou Option+Espace pour obtenir une liste à saisie automatique. Sélectionner `items` dans les options.

1. Appuyez ou cliquez sur le bouton **Prettify** pour formater automatiquement votre code afin qu’il soit plus facile à lire.

1. Une fois l’opération terminée, appuyez ou cliquez sur l’icône **Play** en haut à gauche de l’éditeur pour exécuter la requête. L’éditeur complète automatiquement la variable `items` et la requête s’exécute.

1. Les résultats s’affichent dans le panneau de droite, en regard de l’éditeur de requêtes.

   ![Exécution d’une requête personnalisée](assets/do-not-localize/custom-query-3-4-5-6.png)

C’est ainsi que votre contenu peut être diffusé aux expériences numériques omnicanal.
