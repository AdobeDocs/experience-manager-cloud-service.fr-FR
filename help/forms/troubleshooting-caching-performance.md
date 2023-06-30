---
title: Résolution des problèmes liés aux performances de mise en cache
seo-title: Troubleshooting caching performance
description: Résolution des problèmes liés aux performances de mise en cache
seo-description: Troubleshooting caching performance
contentOwner: khsingh
exl-id: eae44a6f-25b4-46e9-b38b-5cec57b6772c
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: ht
source-wordcount: '360'
ht-degree: 100%

---

# Performances de mise en cache {#caching-performance}

Vous pouvez rencontrer certains des problèmes suivants lors de la configuration ou de l’utilisation du cache de formulaires adaptatifs dans un environnement Cloud Service :

## Certains formulaires adaptatifs contenant des images ou des vidéos ne sont pas automatiquement invalidés à partir du cache du Dispatcher. {#images-videos-not-invalidated}

Vous pouvez sélectionner et ajouter des images ou des vidéos depuis l’explorateur de ressources à un formulaire adaptatif. Lorsque ces images sont modifiées dans l’éditeur de ressources, la version mise en cache d’un formulaire adaptatif contenant de telles images n’est pas invalidée. Le formulaire adaptatif continue d’afficher des images plus anciennes.

Pour résoudre ce problème, après avoir publié les images et la vidéo, dépubliez et publiez explicitement les formulaires adaptatifs qui font référence à ces ressources.

## Certains formulaires adaptatifs incluant un fragment de contenu ou des fragments d’expérience ne sont pas automatiquement invalidés à partir du cache du Dispatcher. {#content-fragments-experience-fragments-not-invalidated}

Vous pouvez ajouter un fragment de contenu ou un fragment d’expérience à un formulaire adaptatif. Lorsque ces fragments sont modifiés et publiés indépendamment, la version mise en cache d’un formulaire adaptatif contenant ces fragments n’est pas invalidée. Le formulaire adaptatif continue d’afficher des fragments plus anciens.

Pour résoudre ce problème, après avoir publié un fragment de contenu ou un fragment d’expérience mis à jour, dépubliez et publiez explicitement les formulaires adaptatifs qui utilisent ces ressources.

## Seule la première instance de formulaires adaptatifs est mise en cache. {#only-first-instance-cached}

Lorsque l’URL du formulaire adaptatif ne contient aucune information de localisation et que l’option Utiliser les paramètres régionaux du navigateur dans le gestionnaire de configuration est activée, une version localisée du formulaire adaptatif est diffusée et une instance du formulaire adaptatif, basée sur la première requête (paramètres régionaux du navigateur requis), est mise en cache et fournie à chaque utilisateur suivant.

Exécutez les étapes suivantes afin de résoudre ce problème :

1. Ouvrez votre projet Experience Manager.
1. Ouvrez le `dispatcher/scr/conf.d/rewrites/rewrite.rules` pour édition.
1. Ouvrez le `conf.d/httpd-dispatcher.conf` ou tout autre fichier de configuration paramétré pour se charger au moment de l’exécution.
1. Ajoutez le code suivant dans votre fichier et enregistrez-le. Il s’agit d’un exemple de code que vous pouvez modifier en fonction de votre environnement.

```shellscript
    # Handle actual URL convention (just pass through)
    RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]
    
    # Handle selector-based redirection based on browser language
    <VirtualHost *:80>
            # Handle actual URL convention (just pass through)
    RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]

    # Handle selector based redirection basded on browser language
    # The Rewrite Condition is looking for the Accept-Language header and if found takes the first two characters which most likely are the desired language selector.
    RewriteCond %{HTTP:Accept-Language} ^(..).*$ [NC]
    RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
    RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
```

## La mise en cache CDN s’arrête après 300 secondes. {#cdn-caching-stops-working-after-300-seconds}

La mise en cache CDN s’arrête après 300 secondes et toutes les requêtes de mise en cache sur CDN sont redirigées vers le Dispatcher.

Pour résoudre ce problème, définissez l’en-tête d’âge sur 0 :

1. Créez un fichier sur `src\conf.d\available_vhosts`

1. Ajoutez les éléments suivants dans le fichier pour définir l&#39;en-tête d’âge

   ```shellscript
       <IfModule mod_headers.c>
               Header add X-Vhost "publish"
               Header set age 0
       </IfModule>
   ```

1. Enregistrez et fermez le fichier.
1. Modifiez le lien symbolique pour `src\conf.d\enabled_vhosts\default.vhost` afin qu’il pointe vers le nouveau fichier.
