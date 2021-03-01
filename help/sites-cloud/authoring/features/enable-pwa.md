---
title: Activation des fonctionnalités d'application Web progressive
description: AEM Sites permet à l’auteur du contenu d’activer des fonctionnalités d’application Web progressive sur n’importe quel site par le biais d’une configuration simple plutôt que d’un codage.
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 54c4755207d84f6f11effea72e94e20027446ba9
workflow-type: tm+mt
source-wordcount: '2046'
ht-degree: 1%

---


# Activation des fonctionnalités d&#39;application Web progressive {#enabling-pwa}

Grâce à une configuration simple, un auteur de contenu peut désormais activer des fonctionnalités d’application Web progressive (PWA) pour les expériences créées dans AEM Sites.

>[!CAUTION]
>
>Il s’agit d’une fonction avancée qui requiert :
>
>* Connaissance des PWA
>* Connaissance de votre site et de la structure de contenu
>* Compréhension des stratégies de mise en cache
>* Assistance de votre équipe de développement

>
>
Avant d’utiliser cette fonctionnalité, il est recommandé de discuter de cette question avec votre équipe de développement afin de définir le meilleur moyen de l’exploiter pour votre projet.

>[!NOTE]
>
>Les fonctionnalités décrites dans ce document devraient être mises à disposition avec la version de [mars 2021 de AEM en tant que Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)

## Présentation {#introduction}

[Les applications Web progressives (en PWA)](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps) permettent d’offrir des expériences similaires à des applications aux sites AEM en les permettant d’être stockées localement sur l’ordinateur d’un utilisateur et d’être accessibles hors ligne. Un utilisateur peut parcourir un site en déplacement même s’il perd une connexion Internet. Les PWA permettent des expériences homogènes même si le réseau est perdu ou instable.

Au lieu d&#39;exiger un recodage du site, un auteur de contenu peut configurer les propriétés du PWA sous forme d&#39;onglet supplémentaire dans les [propriétés de page](/help/sites-cloud/authoring/fundamentals/page-properties.md) d&#39;un site.

* Une fois enregistrée ou publiée, cette configuration déclenche un gestionnaire de événements qui écrit les [fichiers manifestes](https://developer.mozilla.org/en-US/docs/Web/Manifest) et [agent de service](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) qui activent les fonctionnalités de PWA sur le site.
* Les mappages Sling sont également conservés afin de garantir que le service worker est servi à partir de la racine de l’application afin d’activer le contenu proxy permettant des fonctionnalités hors ligne dans l’application.

Avec le PWA, l’utilisateur dispose d’une copie locale du site, ce qui lui permet de vivre une expérience similaire à une application, même sans connexion Internet.

>[!NOTE]
>
>Les applications Web progressives sont une technologie en évolution et la prise en charge de l&#39;installation d&#39;applications locales et d&#39;autres fonctionnalités [dépend du navigateur utilisé.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installable_PWAs#Summary)

## Conditions préalables {#prerequisites}

Pour pouvoir utiliser les fonctionnalités de PWA de votre site, l&#39;environnement de votre projet requiert deux éléments :

1. [Utilisez les ](#adjust-components) composants principaux pour tirer parti de cette fonctionnalité
1. [Ajustez les règles de ](#adjust-dispatcher) répartiteur pour exposer les fichiers requis.

Il s&#39;agit d&#39;étapes techniques que l&#39;auteur devra coordonner avec l&#39;équipe de développement. Ces étapes ne sont requises qu&#39;une seule fois par site.

### Utilisez les composants de base.{#adjust-components}

Les composants de base de la version 2.15.0 et des versions ultérieures prennent entièrement en charge les fonctionnalités PWA des sites AEM. Comme AEMaaCS inclut toujours la dernière version des composants principaux, vous pouvez tirer parti des fonctionnalités de PWA prêtes à l’emploi. Votre projet AEMaaCS répond automatiquement à cette exigence.

>[!NOTE]
>
>L&#39;Adobe ne recommande pas d&#39;utiliser les fonctionnalités PWA sur les composants ou composants personnalisés non [étendus à partir des composants principaux.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=fr)
<!--
Your components need to include the [manifest files](https://developer.mozilla.org/en-US/docs/Web/Manifest) and [service worker,](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) which supports the PWA features.

 To do this, the developer will need to add the following link to the `customheaderlibs.html` file of your page component.

```xml
<link rel="manifest" href="/content/<projectName>/manifest.webmanifest" crossorigin="use-credentials"/>
```

The developer will also need to add the following link to the `customfooterlibs.html` file of your page component.

```xml
<script>
        // Check that service workers are supported
        if ('serviceWorker' in navigator) {
            // Use the window load event to make sure the page load performs well
            window.addEventListener('load', () => {
                let serviceWorker = '/<projectName>sw.js';
                navigator.serviceWorker.register(serviceWorker);
            });
        }
</script>
```
-->

### Ajuster votre répartiteur {#adjust-dispatcher}

La fonction de PWA génère et utilise des fichiers `/content/<sitename>/manifest.webmanifest`. Par défaut, [le répartiteur](/help/implementing/dispatcher/overview.md) n&#39;expose pas ces fichiers. Pour exposer ces fichiers, le développeur doit ajouter la configuration suivante à votre projet de site.

```text
File location: [project directory]/dispatcher/src/conf.dispatcher.d/filters/filters.any >

# Allow webmanifest files
/0102 { /type "allow" /extension "webmanifest" /path "/content/*/manifest" }
```

Selon votre projet, vous pouvez inclure différents types d’extensions aux règles de réécriture. L&#39;extension `webmanifest` peut s&#39;avérer utile pour inclure dans les conditions de réécriture lorsque vous avez introduit une règle qui masque et redirige les requêtes vers `/content/<projectName>`.

```text
RewriteCond %{REQUEST_URI} (.html|.jpe?g|.png|.svg|.webmanifest)$
```

## Activation du PWA pour votre site {#enabling-pwa-for-your-site}

Avec [les conditions préalables](#prerequisites) satisfaites, il est très facile pour un auteur de contenu d’activer les fonctionnalités de PWA sur un site. Vous trouverez ci-dessous un aperçu de la façon de procéder. Les options individuelles sont détaillées dans la section [Options détaillées.](#detailed-options)

1. Connectez-vous à AEM.
1. Dans le menu principal, appuyez ou cliquez sur **Navigation** -> **Sites**.
1. Sélectionnez le projet de vos sites et appuyez ou cliquez sur [**Propriétés**](/help/sites-cloud/authoring/fundamentals/page-properties.md) ou utilisez la touche d&#39;accès rapide `p`.
1. Sélectionnez l&#39;onglet **Application Web progressive** et configurez les propriétés applicables. Vous pouvez au minimum :
   1. Sélectionnez l&#39;option **Activer le PWA**.
   1. Définissez l&#39;**URL de démarrage**.

      ![Activer PWA](../assets/pwa-enable.png)

   1. Téléchargez une icône de png de 512 x 512 sur le DAM et référencez-la comme icône de l’application.

      ![Icône Définir un PWA](../assets/pwa-icon.png)

   1. Configurez les chemins d’accès que le collaborateur de services doit emprunter hors connexion. Les chemins types sont les suivants :
      * `/content/<sitename>`
      * `/content/experiencefragements/<sitename>`
      * `/content/dam/<sitename>`
      * Toute référence à une police tierce
      * `/etc/clientlibs/<sitename>`

      ![Définir des chemins hors ligne PWA](../assets/pwa-offline.png)


1. Appuyez/cliquez sur **Enregistrer et fermer**.

Votre site est maintenant configuré et vous pouvez [l&#39;installer en tant qu&#39;application locale.](#using-pwa-enabled-site)

## Utilisation de votre site compatible avec les PWA {#using-pwa-enabled-site}

Maintenant que vous avez [configuré votre site pour prendre en charge le PWA,](#enabling-pwa-for-your-site) vous pouvez l&#39;expérimenter vous-même.

1. Accédez au site dans un navigateur [pris en charge.](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installable_PWAs#Summary)
1. Une nouvelle icône s’affiche dans la barre d’adresse du navigateur, indiquant que le site peut être installé en tant qu’application locale.
   * Selon le navigateur, l’icône peut varier et le navigateur peut également afficher une notification (comme une bannière ou une boîte de dialogue) indiquant qu’il est possible de procéder à l’installation en tant qu’application locale.
1. Installez l’application.
1. L’application sera installée sur l’écran d’accueil de votre périphérique.
1. Ouvrez l’application, parcourez un peu et vérifiez que les pages sont disponibles hors ligne.

## Options détaillées {#detailed-options}

La section suivante fournit plus de détails sur les options disponibles lorsque [vous configurez votre site pour un PWA.](#enabling-pwa-for-your-site)

### Configurer une expérience installable {#configure-installable-experience}

Ces paramètres permettent à votre site de se comporter comme une application native en le rendant installable sur l’écran d’accueil du visiteur et disponible hors connexion.

* **Activer le PWA**  : il s&#39;agit de la bascule principale pour activer le PWA pour le site.
* **URL**  de démarrage : il s’agit de l’ [URL de début ](https://developer.mozilla.org/en-US/docs/Web/Manifest/start_url) préféréeque l’application ouvre lorsque l’utilisateur charge l’application installée localement.
   * Il peut s’agir de n’importe quel chemin dans votre structure de contenu.
   * Il n’est pas nécessaire qu’il s’agisse de la racine et il s’agit souvent d’une page d’accueil dédiée à l’application.
   * Si cette URL est relative, l’URL de manifeste est utilisée comme URL de base pour la résoudre.
   * Lorsqu’elle est vide, la fonction utilise l’adresse de la page Web à partir de laquelle l’application Web a été installée.
   * Il est recommandé de définir une valeur.
* **Mode**  d’affichage : une application activée pour les PWA est toujours un site AEM diffusé par le biais d’un navigateur. [Ces ](https://developer.mozilla.org/en-US/docs/Web/Manifest/display) options d’affichage définissent comment le navigateur doit être masqué ou présenté à l’utilisateur sur le périphérique local.
   * **Autonome**  : le navigateur est complètement masqué par l’utilisateur et il apparaît comme une application native. Il s’agit de la valeur par défaut.
      * Avec cette option, la navigation de l’application doit être entièrement possible par le biais de votre contenu à l’aide de liens et de composants sur les pages du site sans utiliser les commandes de navigation du navigateur.
   * **Navigateur**  : le navigateur s&#39;affiche comme il le ferait normalement lors de la visite du site.
   * **Interface utilisateur**  minimale : le navigateur est généralement masqué, comme une application native, mais les commandes de navigation de base sont exposées.
   * **Plein écran**  - Le navigateur est complètement masqué, comme une application native, mais est rendu en mode plein écran.
      * Avec cette option, la navigation de l’application doit être entièrement possible par le biais de votre contenu à l’aide de liens et de composants sur les pages du site sans utiliser les commandes de navigation du navigateur.
* **Orientation**  de l&#39;écran - En tant qu&#39;application locale, le PWA doit savoir comment gérer les orientations de  [périphérique.](https://developer.mozilla.org/en-US/docs/Web/Manifest/orientation)
   * **Tout**  : l’application s’adapte à l’orientation du périphérique de l’utilisateur. Il s’agit de la valeur par défaut.
   * **Portrait**  : cette option force l’application à s’ouvrir en mode portrait, quelle que soit l’orientation du périphérique de l’utilisateur.
   * **Paysage**  : cette option force l’application à s’ouvrir en mode paysage, quelle que soit l’orientation du périphérique de l’utilisateur.
* **Couleur**  du thème : définit la  [couleur de l&#39;](https://developer.mozilla.org/en-US/docs/Web/Manifest/theme_color) application qui affecte la façon dont le système d&#39;exploitation de l&#39;utilisateur local affiche la barre d&#39;outils native de l&#39;interface utilisateur et les commandes de navigation. Selon le navigateur, elle peut affecter d’autres éléments de présentation de l’application.
   * Utilisez la fenêtre contextuelle de couleurs pour sélectionner une couleur.
   * La couleur peut également être définie par une valeur hexadécimale ou RVB.
* **Couleur**  d&#39;arrière-plan : définit la couleur d&#39; [arrière-plan de l&#39;application, ](https://developer.mozilla.org/en-US/docs/Web/Manifest/background_color) qui s&#39;affiche au chargement de l&#39;application.
   * Utilisez la fenêtre contextuelle de couleurs pour sélectionner une couleur.
   * La couleur peut également être définie par une valeur hexadécimale ou RVB.
   * Certains navigateurs [créent automatiquement un écran de démarrage](https://developer.mozilla.org/en-US/docs/Web/Manifest#Splash_screens) à partir du nom de l’application, de la couleur d’arrière-plan et de l’icône.
* **Icône**  : définit  [l’](https://developer.mozilla.org/en-US/docs/Web/Manifest/icons) icône qui représente l’application sur le périphérique de l’utilisateur.
   * L’icône doit être un fichier PNG de 512 x 512 pixels.
   * L&#39;icône doit être [stockée dans DAM.](/help/assets/overview.md)

### Gestion du cache (avancée) {#offline-configuration}

Ces paramètres rendent des parties de ce site disponibles hors ligne et localement sur votre périphérique visiteur. Cela permet de contrôler le cache de l’application Web afin d’optimiser les demandes réseau et de prendre en charge les expériences hors ligne.

* **Stratégie de mise en cache et fréquence d&#39;actualisation**  du contenu : ce paramètre définit le modèle de mise en cache de votre PWA.
   * **Modérément**  :  [ce paramètre ](https://web.dev/stale-while-revalidate/) est le cas pour la plupart des sites et est la valeur par défaut.
      * Avec ce paramètre, le contenu affiché pour la première fois par l’utilisateur sera chargé à partir du cache et pendant que l’utilisateur consomme ce contenu, le reste du contenu du cache sera revalidé.
   * **Fréquemment**  - C&#39;est le cas pour les sites qui ont besoin de mises à jour pour être très rapides comme les maisons de vente aux enchères.
      * Avec ce paramètre, l’application recherche d’abord le contenu le plus récent via le réseau et, s’il n’est pas disponible, il revient au cache local.
   * **Rarement**  : c&#39;est le cas pour les sites qui sont presque statiques, tels que les pages de référence.
      * Avec ce paramètre, l’application recherche d’abord le contenu dans le cache et, si ce n’est pas le cas, revient au réseau pour le récupérer.
* **Prémise en cache**  des fichiers : ces fichiers hébergés sur l&#39;AEM seront enregistrés dans le cache du navigateur local lorsque le travailleur de services installe et avant son utilisation. Cela garantit que l’application Web est entièrement fonctionnelle lorsqu’elle est hors ligne.
* **Inclusions**  de chemins : les demandes réseau pour les chemins définis sont interceptées et le contenu mis en cache est renvoyé conformément à la stratégie de  **mise en cache configurée et à la fréquence d&#39;actualisation** du contenu.
* **Exclusions**  du cache : ces fichiers ne seront jamais mis en cache, quels que soient les paramètres sous Inclusions **de** chemin et de pré **** mise en cache des fichiers.

>[!TIP]
>
>Votre équipe de développeurs a probablement des informations précieuses sur la configuration de votre configuration hors ligne.

## Limites et Recommendations {#limitations-recommendations}

Toutes les fonctions de PWA ne sont pas disponibles pour AEM Sites. Il s&#39;agit de quelques limitations notables.

* Un utilisateur doit parcourir la page au moins une fois avant d’être mis en cache hors ligne.
* Les pages ne sont pas automatiquement synchronisées ou mises à jour si l’utilisateur n’utilise pas l’application.

Adobe fait également les recommandations suivantes lorsque vous implémentez le PWA.

### Réduisez le nombre de ressources à mettre en cache. {#minimize-precache}

Adobe vous conseille de limiter le nombre de pages à mettre en cache.

* Incorporer des bibliothèques pour réduire le nombre d’entrées à gérer lors de la mise en cache préalable.
* Limitez le nombre de variations d’image à pré-mettre en cache.

### Activez le PWA une fois les scripts et feuilles de style du projet stabilisés. {#pwa-stabilized}

Les bibliothèques clientes sont fournies avec l’ajout d’un sélecteur de cache observant le modèle suivant `lc-<checksumHash>-lc`. Chaque fois qu’un des fichiers (et dépendances) qui compose une modification de bibliothèque, ce sélecteur change. Si vous avez répertorié une bibliothèque cliente à mettre en cache par le service-worker et que vous souhaitez vous référer à une nouvelle version, vous récupérez et mettez à jour manuellement l’entrée. Par conséquent, nous vous conseillons de configurer votre site pour qu&#39;il soit un PWA une fois les scripts et feuilles de style du projet stabilisés.

### Réduisez le nombre de variations d’image. {#minimize-variations}

Le composant d’image des composants principaux AEM détermine l’un des principaux rendus à récupérer. Ce mécanisme inclut également un horodatage correspondant à l&#39;heure de la dernière modification de cette ressource. Ce mécanisme complique la configuration du pré-cache du PWA.

Lors de la configuration du pré-cache, l’utilisateur doit liste toutes les variations de chemin d’accès qui peuvent être récupérées. Ces variations sont composées de paramètres tels que la qualité et la largeur. Il est fortement conseillé de réduire le nombre de ces variations à un maximum de trois - petit, moyen, grand. Vous pouvez le faire via la boîte de dialogue de stratégie de contenu du [composant d&#39;image.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html?lang=fr)

Si elle n&#39;est pas configurée avec précaution, la consommation de mémoire et de réseau peut avoir un impact important sur les performances de votre PWA. De même, si vous avez l’intention de prédéfinir, disons, 50 images et d’avoir 3 largeurs par image, l’utilisateur qui gère le site devra conserver une liste de 150 entrées au maximum dans la section de pré-cache du PWA des propriétés de la page.

Adobe vous conseille également de configurer votre site pour qu’il soit PWA une fois que l’utilisation des images du projet s’est stabilisée.
