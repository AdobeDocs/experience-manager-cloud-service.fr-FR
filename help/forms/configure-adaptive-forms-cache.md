---
title: Configuration du cache de formulaires adaptatifs
description: Le cache de Forms adaptatif est conçu pour Forms et les documents adaptatifs ayant pour objectif de réduire le temps nécessaire au rendu d’un formulaire ou d’un document adaptatif.
uuid: ba8f79fd-d8dc-4863-bc0d-7c642c45505c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 9fa6f761-58ca-4cd0-8992-b9337dc1a279
source-git-commit: e2f2aa18e2412bc92d1385a125281ecfb81f2ce8
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 55%

---


# Configuration du cache de formulaires adaptatifs {#configure-adaptive-forms-cache}

Un cache est un mécanisme qui permet de raccourcir les temps d’accès aux données, réduire le temps de réponse et améliorer les vitesses d’entrée/sortie (E/S). Le cache de Forms adaptatif stocke uniquement le contenu de HTML et la structure JSON d’un formulaire adaptatif sans enregistrer de données préremplies. Cela permet de réduire le temps nécessaire pour effectuer le rendu d’un formulaire adaptatif sur le client. Il est spécialement conçu pour les formulaires adaptatifs.

## Configuration du cache de formulaires adaptatifs pour les instances d’auteur et de publication {#configure-adaptive-forms-caching-at-author-and-publish-instances}

1. Accédez à la page de configuration de la console web AEM à l’adresse `https://[server]:[port]/system/console/configMgr`.
1. Cliquez sur la **[!UICONTROL configuration de canal web de communication interactive de formulaire adaptatif]** pour éditer ses valeurs de configuration.
1. Dans le [!UICONTROL modifier les valeurs de configuration ;] , indiquez le nombre maximal de formulaires ou documents d’une instance de l’AEM [!DNL Forms Server] peut mettre en cache dans la variable **[!UICONTROL Nombre de Forms adaptatives]** champ . La valeur par défaut est 100.

   >[!NOTE]
   >
   >Pour désactiver le cache, définissez la valeur du champ Nombre de Forms adaptatives sur **0**. Le cache est réinitialisé, et tous les formulaires et documents sont supprimés du cache lorsque vous désactivez ou modifiez la configuration du cache.

   ![Boîte de dialogue de configuration du cache HTML de formulaires adaptatifs](assets/cache-configuration-edit.png)

1. Cliquez sur **[!UICONTROL Enregistrer]** pour enregistrer la configuration.

Votre environnement est configuré pour utiliser le cache de formulaires adaptatifs et de ressources connexes.


## (Facultatif) Configurez le cache de formulaire adaptatif dans Dispatcher. {#configure-the-cache}

Vous pouvez également configurer la mise en cache des formulaires adaptatifs sur Dispatcher pour une amélioration supplémentaire des performances.

### Prérequis {#pre-requisites}

* Activez la variable [fusion ou préremplissage des données au niveau du client](prepopulate-adaptive-form-fields.md#prefill-at-client) . Elle permet de fusionner des données uniques pour chaque instance d’un formulaire prérempli.
* [Activation d’un agent de vidage pour chaque instance de publication](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=fr#invalidating-dispatcher-cache-from-a-publishing-instance). Il permet de mieux mettre en cache les performances des formulaires adaptatifs. L’URL par défaut des agents de vidage est `http://[server]:[port]]/etc/replication/agents.publish/flush.html`.

### Remarques concernant la mise en cache de Forms adaptatif sur un Dispatcher {#considerations}

* Lorsque vous utilisez le cache de formulaires adaptatifs, utilisez le [!DNL Dispatcher] AEM pour mettre en cache les bibliothèques cliente (CSS et JavaScript) d’un formulaire adaptatif.
* Lors du développement des composants personnalisés, sur le serveur utilisé pour le développement, gardez le cache de formulaires adaptatifs désactivé.
* Les URL sans extension ne sont pas mises en cache. Par exemple, URL avec modèle `/content/forms/[folder-structure]/[form-name].html` sont mis en cache et la mise en cache ignore les URL avec modèle `/content/dam/formsanddocument/[folder-name]/<form-name>/jcr:content`. Par conséquent, utilisez des URL avec des extensions pour tirer parti des avantages de la mise en cache.
* Considérations relatives aux formulaires adaptatifs :
   * Utilisez le format URL `http://host:port/content/forms/af/<afName>.<locale>.html` pour demander une version localisée d’un formulaire adaptatif au lieu de `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`
   * Désactivez l’utilisation des paramètres régionaux du navigateur <!-- [Disable using browser locale](supporting-new-language-localization.md#how-localization-of-adaptive-form-works) -->pour les URL au format `http://host:port/content/forms/af/<adaptivefName>.html`.
   * Lorsque vous utilisez le format URL `http://host:port/content/forms/af/<adaptivefName>.html` et que l’option **[!UICONTROL Utiliser les paramètres régionaux du navigateur]** dans le gestionnaire de configuration est désactivée, la version non localisée du formulaire adaptatif est diffusée. La langue non localisée est celle utilisée lors du développement du formulaire adaptatif. Les paramètres régionaux configurés pour votre navigateur (paramètres régionaux du navigateur) ne sont pas pris en compte et une version non localisée du formulaire adaptatif est diffusée.
   * Lorsque vous utilisez le format URL `http://host:port/content/forms/af/<adaptivefName>.html` et que l’option **[!UICONTROL Utiliser les paramètres régionaux du navigateur]** dans le gestionnaire de configuration est activée, une version localisée du formulaire adaptatif est diffusée, le cas échéant. La langue du formulaire adaptatif localisé est basée sur les paramètres régionaux configurés pour votre navigateur (paramètres régionaux du navigateur). Cela peut mener à [mise en cache de la première instance d’un formulaire adaptatif]. Pour éviter que le problème ne se produise sur votre instance, voir [Résolution des problèmes](#only-first-insatnce-of-adptive-forms-is-cached).

### Activation de la mise en cache dans Dispatcher

Suivez les étapes ci-dessous pour activer et configurer la mise en cache d’Adaptive Forms sur Dispatcher :

1. Ouvrez l’URL suivante pour chaque instance de publication de votre environnement et configurez l’agent de réplication :
   `http://[server]:[port]]/etc/replication/agents.publish/flush.html`

1. [Ajoutez les éléments suivants à votre fichier dispatcher.any](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#automatically-invalidating-cached-files) :

   ```JSON
      /invalidate
      {
      /0000
      {
      /glob "*"
      /type "deny"
      }
      /0001
      {
      # Consider all HTML files stale after an activation.
      /glob "*.html"
      /type "allow"
      }
      /0002
      {
      # Exclude htmls present in AF directories
      /glob "/content/forms/**/*.html"
      /type "deny"
      }
   ```

   Lorsque vous ajoutez ce qui suit :

   * Un formulaire adaptatif reste en cache jusqu’à ce qu’une version mise à jour du formulaire ne soit pas publiée.

   * Lorsqu’une version plus récente d’une ressource référencée dans un formulaire adaptatif est publiée, le formulaire adaptatif concerné est automatiquement invalidé. Il existe certaines exceptions à l’invalidation automatique des ressources référencées. Pour contourner les exceptions, voir la section [dépannage](#troubleshooting) .
1. [Ajoutez le fichier dispatcher.any des règles ci-dessous ou le fichier de règles personnalisées](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#specifying-the-documents-to-cache). Il exclut les URL qui ne prennent pas en charge la mise en cache. Par exemple, Communication interactive.

   ```JSON
      /0000 {
            /glob "*"
            /type "allow"
      }
      ## Don't cache csrf login tokens
      /0001 {
            /glob "/libs/granite/csrf/token.json"
            /type "deny"
      }
      ## Don't cache IC - print channel
      /0002 {
            /glob "/content/forms/**/channels/print.html"
            /type "deny"
      }
      ## Don't cache IC - web channel
      /0003 {
            /glob "/content/forms/**/channels/web.html"
            /type "deny"
      }
   ```

1. [Ajoutez les paramètres suivants à la liste des paramètres d’URL ignorés](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=fr#ignoring-url-parameters) :

   ```JSON
      /ignoreUrlParams {
      /0001 { /glob "*" /type "deny" }
      # added for AEM forms specific use cases.
      /0003 { /glob "dataRef" /type "allow" }
      }
   ```

Votre environnement AEM est configuré pour mettre en cache des formulaires adaptatifs. Il met en cache tous les types de formulaires adaptatifs. Si vous avez besoin de vérifier les autorisations d’accès utilisateur pour une page avant de diffuser la page mise en cache, reportez-vous à la section [mise en cache de contenu sécurisé](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=fr).

## Résolution des problèmes {#troubleshooting}

### Certaines Forms adaptatives contenant des images ou des vidéos ne sont pas automatiquement invalidées du cache de Dispatcher. {#videos-or-images-not-auto-invalidated}

#### Problème {#issue1}

Lorsque vous sélectionnez et ajoutez des images ou des vidéos par le biais de l’explorateur de ressources à un formulaire adaptatif, et qu’elles sont modifiées dans l’éditeur de ressources, ces ressources ne sont pas automatiquement invalidées à partir du cache de Dispatcher.

#### Solution {#Solution1}

Après avoir publié les images et la vidéo, dépubliez et publiez explicitement les formulaires adaptatifs qui référencent ces ressources.

### Certaines Forms adaptatives contenant des fragments de contenu ou d’expérience ne sont pas automatiquement invalidées du cache de Dispatcher. {#content-or-experience-fragment-not-auto-invalidated}

#### Problème {#issue2}

Lorsque vous ajoutez un fragment de contenu ou un fragment d’expérience à un formulaire adaptatif et que ces ressources sont modifiées et publiées indépendamment, le Forms adaptatif contenant de telles ressources n’est pas invalidé automatiquement à partir du cache de Dispatcher.

#### Solution {#Solution2}

Après la publication d’un fragment de contenu ou d’un fragment d’expérience mis à jour, dépubliez explicitement le Forms adaptatif qui utilise ces ressources.

### Seule la première instance d’un formulaire adaptatif est mise en cache{#only-first-insatnce-of-adptive-forms-is-cached}

#### Problème {#issue3}

Lorsque l’URL de formulaire adaptatif ne contient aucune information de localisation, et **[!UICONTROL Utiliser les paramètres régionaux du navigateur]** dans configuration manager est activé. Une version localisée du formulaire adaptatif est diffusée, et seule la première instance du formulaire adaptatif est mise en cache et diffusée à chaque utilisateur suivant.

#### Solution {#Solution3}

1. Ouvrez le fichier conf.d/httpd-dispatcher.conf ou tout autre fichier de configuration configuré pour se charger au moment de l’exécution.

1. Ajoutez le code suivant dans votre fichier et enregistrez-le. Il s’agit d’un exemple de code que vous pouvez modifier en fonction de votre environnement.

```XML
   <VirtualHost *:80>
        # Set log level high during development / debugging and then turn it down to whatever is appropriate
    LogLevel rewrite:trace6
        # Start Rewrite Engine
    RewriteEngine On
        # Handle actual URL convention (just pass through)
        RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]
 
        # Handle selector based redirection basded on browser language
        # The Rewrite Cond(ition) is looking for the Accept-Lanague header and if found takes the first two characters which most likely is the desired language selector.
        RewriteCond %{HTTP:Accept-Language} ^(..).*$ [NC]
        RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
   </VirtualHost>
```
