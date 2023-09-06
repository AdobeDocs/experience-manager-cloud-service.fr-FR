---
title: SPA et rendu côté serveur (SSR)
description: L’utilisation du rendu côté serveur dans votre SPA peut accélérer le chargement initial de la page, puis transmettre plus de rendu au client.
exl-id: be409559-c7ce-4bc2-87cf-77132d7c2da1
source-git-commit: 66c9e95f96c8ce181722488a34a175c80f6f917c
workflow-type: tm+mt
source-wordcount: '1518'
ht-degree: 54%

---

# SPA et rendu côté serveur (SSR){#spa-and-server-side-rendering}

Les applications sur une seule page (SPA) peuvent offrir à l’utilisateur une expérience riche et dynamique qui réagit et se comporte de manière familière, souvent tout simplement comme une application native. [Pour ce faire, le client doit charger le contenu à l’avance, puis effectuer la lourde tâche de gérer l’interaction utilisateur.](introduction.md#how-does-a-spa-work). Ce processus minimise la quantité de communication nécessaire entre le client et le serveur, ce qui rend l’application plus réactive.

Toutefois, ce processus peut entraîner des temps de chargement initiaux plus longs, en particulier si le SPA est volumineux et riche en contenu. Pour optimiser les temps de chargement, une partie du contenu peut être rendue côté serveur. L’utilisation du rendu côté serveur (SSR) peut accélérer le chargement initial de la page, puis transmettre plus de rendu au client.

## Quand utiliser le rendu côté serveur {#when-to-use-ssr}

Le rendu côté serveur n’est pas requis pour tous les projets. Bien qu’AEM prenne pleinement en charge le rendu côté serveur JS pour les SPA, Adobe ne recommande pas de le mettre en œuvre systématiquement pour chaque projet.

Lorsque vous décidez de mettre en oeuvre le rendu côté serveur, vous devez d’abord estimer la complexité, les efforts et les coûts supplémentaires que le rendu côté serveur représente de manière réaliste pour le projet, y compris la maintenance à long terme. Une architecture SSR ne doit être choisie que lorsque la valeur ajoutée dépasse clairement les coûts estimés.

Le rendu côté serveur fournit habituellement une certaine valeur lorsque la réponse à l’une ou l’autre des questions suivantes est un « oui » clair :

* **SEO :** Le rendu côté serveur est-il toujours nécessaire pour que votre site soit correctement indexé par les moteurs de recherche qui génèrent du trafic ? Gardez à l’esprit que les principaux robots de moteur de recherche évaluent désormais JS.
* **Vitesse de la page :** le rendu côté serveur améliore-t-il la vitesse de façon mesurable dans les environnements réels et ajoute-t-il à l’expérience globale de l’utilisateur ?

Ce n’est que lorsqu’au moins une de ces deux questions reçoit une réponse &quot;oui&quot; claire pour votre projet que l’Adobe recommande la mise en oeuvre du rendu côté serveur. Les sections suivantes décrivent comment utiliser Adobe I/O Runtime, qui fait partie de [App Builder](https://developer.adobe.com/app-builder).

## Adobe I/O Runtime {#adobe-i-o-runtime}

Si vous [êtes certain(e) que votre projet nécessite la mise en œuvre du rendu côté serveur](#when-to-use-ssr), la solution recommandée par Adobe est d’utiliser Adobe I/O Runtime.

Pour plus d’informations sur Adobe I/O Runtime, voir :

* [https://developer.adobe.com/runtime](https://developer.adobe.com/runtime) - pour une présentation de la fonction Exécution d’App Builder
* [https://developer.adobe.com/app-builder](https://developer.adobe.com/app-builder) - pour plus d’informations sur le produit App Builder complet
* [https://developer.adobe.com/runtime/docs/](https://developer.adobe.com/runtime/docs) - pour une documentation détaillée

Les sections suivantes décrivent comment Adobe I/O Runtime peut être utilisé afin d’implémenter la technologie du rendu côté serveur pour votre SPA dans deux modèles différents :

* [Flux de communication piloté par AEM](#aem-driven-communication-flow)
* [Flux de communication piloté par Adobe I/O Runtime](#adobe-i-o-runtime-driven-communication-flow)

>[!NOTE]
>
>Adobe recommande un espace de travail Adobe I/O Runtime distinct par environnement (évaluation, production, test, etc.). Cela permet d’obtenir des modèles de cycle de vie de développement de systèmes classiques avec différentes versions d’une application unique déployée dans différents environnements. Voir [CI/CD pour les applications App Builder](https://developer.adobe.com/app-builder/docs/guides/deployment/ci_cd_for_firefly_apps/) pour plus d’informations.
>
>Un espace de travail distinct n’est pas nécessaire pour chaque instance (création, publication), sauf s’il existe des différences dans l’implémentation de l’environnement d’exécution (runtime) par type d’instance.

>[!NOTE]
>
>Cloud Manager ne prend pas en charge le déploiement vers Adobe I/O Runtime. Par conséquent, votre propre infrastructure doit être configurée pour déployer le code SSR vers Adobe I/O Runtime.

## Configuration du moteur de rendu distant {#remote-content-renderer-configuration}

AEM doit savoir où le contenu rendu à distance peut être récupéré. Indépendamment de [le modèle que vous choisissez de mettre en oeuvre pour le rendu côté serveur,](#adobe-i-o-runtime) vous devez indiquer pour AEM comment accéder à ce service de rendu distant.

Ce service est effectué au moyen de la fonction **RemoteContentRenderer - service OSGi d’usine de configuration**. Recherchez la chaîne « RemoteContentRenderer » dans la console de configuration de la console web à `http://<host>:<port>/system/console/configMgr`.

![Configuration du moteur de rendu](assets/renderer-configuration.png)

Les champs suivants sont disponibles pour la configuration :

* **Modèle de chemin d’accès au contenu** - Expression régulière pour faire correspondre une partie du contenu, si nécessaire
* **URL du point d’entrée distant** : URL du point d’entrée responsable de la génération du contenu
   * Utilisez le protocole HTTPS sécurisé si ce point d’entrée ne figure pas sur le réseau local.
* **En-têtes de requête supplémentaires** : en-têtes supplémentaires à ajouter à la requête envoyée au point d’entrée distant
   * Modèle : `key=value`
* **Délai d’expiration de la requête** : délai d’expiration de la requête d’hôte distant en millisecondes

>[!NOTE]
>
>Que vous choisissiez de mettre en œuvre le [flux de communication piloté par AEM](#aem-driven-communication-flow) ou le [flux de communication piloté par Adobe I/O Runtime](#adobe-i-o-runtime-driven-communication-flow), vous devez définir une configuration de moteur de rendu de contenu distant.

>[!NOTE]
>
>Cette configuration utilise la variable [Moteur de rendu de contenu distant,](#remote-content-renderer) qui propose des options d’extension et de personnalisation supplémentaires.

## Flux de communication piloté par AEM {#aem-driven-communication-flow}

Avec le rendu côté serveur, le [workflow d’interaction des composants](introduction.md#interaction-with-the-spa-editor) des SPA d’AEM inclut une phase au cours de laquelle le contenu initial de l’application est généré dans Adobe I/O Runtime.

1. Le navigateur demande le contenu du rendu côté serveur à AEM.
1. AEM publie le modèle dans Adobe I/O Runtime.
1. Adobe I/O Runtime renvoie le contenu généré.
1. AEM traite le code HTML renvoyé par Adobe I/O Runtime via le modèle HTL du composant de page de serveur principal.

![AEM Adobe I/O piloté par SSE CMS](assets/ssr-cms-drivenaemnode-adobeio.png)

## Flux de communication piloté par Adobe I/O Runtime {#adobe-i-o-runtime-driven-communication-flow}

La section précédente décrit l’implémentation standard et recommandée du rendu côté serveur concernant les SPA dans AEM, où l’activité d’AEM effectue le démarrage et la diffusion du contenu.

Une autre solution consiste à mettre en œuvre le rendu côté serveur de sorte qu’Adobe I/O Runtime soit responsable du démarrage, ce qui inverse le flux de communication.

Les deux modèles sont valides et pris en charge par AEM. Toutefois, il faut tenir compte des avantages et des inconvénients de chaque modèle avant de mettre en œuvre un modèle particulier.

<table>
 <tbody>
  <tr>
   <th><strong>Démarrage</strong></th>
   <th><strong>Avantages</strong></th>
   <th><strong>Inconvénients</strong></th>
  </tr>
  <tr>
   <th><strong>Via AEM</strong><br /> </th>
   <td>
    <ul>
     <li>AEM gère les bibliothèques d’injection si nécessaire.</li>
     <li>Conserver les ressources sur AEM uniquement<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Solution pouvant être peu connue des développeurs de SPA<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <th><strong>Via Adobe I/O Runtime<br /> </strong></th>
   <td>
    <ul>
     <li>Solution mieux connue des développeurs SPA<br /> </li>
    </ul> </td>
   <td>
    <ul>
     <li>Les ressources clientlib requises par l’application, telles que CSS et JavaScript, doivent être mises à disposition par le développeur AEM au moyen de la fonction <code><a href="/help/implementing/developing/introduction/clientlibs.md">allowProxy</a></code> property<br /> </li>
     <li>Les ressources doivent être synchronisées entre AEM et Adobe I/O Runtime.<br /> </li>
     <li>Afin de permettre de créer la SPA, un serveur proxy pour Adobe I/O Runtime peut être nécessaire.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Planification du rendu côté serveur {#planning-for-ssr}

En règle générale, seule une partie d’une application doit être rendue côté serveur. L’exemple courant est le contenu affiché au-dessus du pli lors du chargement initial de la page rendu côté serveur. Ce processus permet de gagner du temps en diffusant vers le client du contenu déjà rendu. Lorsque l’utilisateur interagit avec la SPA, le contenu supplémentaire est rendu par le client.

Lorsque vous envisagez d’implémenter le rendu côté serveur pour votre SPA, passez en revue les parties de l’application qui sont nécessaires.

## Développement d’une SPA avec le rendu côté serveur {#developing-an-spa-using-ssr}

Les composants SPA peuvent être rendus par le client (dans le navigateur) ou côté serveur. Lorsqu’ils sont rendus côté serveur, les propriétés du navigateur telles que la taille de fenêtre et l’emplacement ne sont pas présentes. Par conséquent, SPA composants doivent être isomorphes, sans présumer de l’emplacement de leur rendu.

Pour utiliser le rendu côté serveur, vous devez déployer votre code dans AEM et sur Adobe I/O Runtime, qui est responsable du rendu côté serveur. La plupart du code est identique, mais les tâches spécifiques au serveur diffèrent.

## Rendu côté serveur pour les SPA dans AEM {#ssr-for-spas-in-aem}

Le rendu côté serveur pour SPA dans AEM nécessite Adobe I/O Runtime, qui est appelé pour le rendu côté serveur de contenu de l’application. Dans le fichier HTL de l’application, une ressource d’Adobe I/O Runtime est appelée pour procéder au rendu du contenu.

Tout comme AEM prend en charge les frameworks Angular et React SPA prêts à l’emploi, le rendu côté serveur est également pris en charge pour les applications Angular et React. Pour plus d’informations, consultez la documentation NPM relative aux deux frameworks.

## Moteur de rendu de contenu distant {#remote-content-renderer}

La configuration du [moteur de rendu de contenu distant](#remote-content-renderer-configuration) requise pour utiliser le rendu côté serveur avec votre SPA dans AEM exploite un service de rendu plus généralisé qui peut être étendu et personnalisé en fonction de vos besoins.

### RemoteContentRenderingService {#remotecontentrenderingservice}

`RemoteContentRenderingService` Un service OSGi pour récupérer le contenu rendu sur un serveur distant, par exemple à partir d’Adobe I/O. Le contenu envoyé au serveur distant est basé sur le paramètre de requête transmis.

`RemoteContentRenderingService` Peut être injecté par inversion de dépendance dans un modèle Sling personnalisé ou un servlet lorsque des manipulations de contenu supplémentaires sont requises.

Ce service est utilisé en interne par le servlet [RemoteContentRendererRequestHandlerServlet](#remotecontentrendererrequesthandlerservlet).

### RemoteContentRendererRequestHandlerServlet {#remotecontentrendererrequesthandlerservlet}

La variable `RemoteContentRendererRequestHandlerServlet` est utilisé pour définir la configuration de la requête par programmation. `DefaultRemoteContentRendererRequestHandlerImpl`, l’implémentation du gestionnaire de requêtes par défaut fournie, vous permet de créer plusieurs configurations OSGi afin que vous puissiez mapper un emplacement de la structure de contenu à un point de terminaison distant.

Pour ajouter un gestionnaire de requêtes personnalisé, implémentez l’interface de `RemoteContentRendererRequestHandler`. Veillez à définir la propriété du composant `Constants.SERVICE_RANKING` sur un nombre entier supérieur à 100, qui correspond au classement du servlet `DefaultRemoteContentRendererRequestHandlerImpl`.

```javascript
@Component(immediate = true,
        service = RemoteContentRendererRequestHandler.class,
        property={
            Constants.SERVICE_RANKING +":Integer=1000"
        })
public class CustomRemoteContentRendererRequestHandlerImpl implements RemoteContentRendererRequestHandler {}
```

### Établir la configuration OSGi du gestionnaire par défaut {#configure-default-handler}

La configuration du gestionnaire par défaut doit être établie comme décrit dans la section [Configuration du moteur de rendu de contenu distant](#remote-content-renderer-configuration).

### Utilisation du moteur de rendu de contenu distant {#usage}

Effectuez une récupération de servlet et renvoyez du contenu injecté dans la page :

1. Vérifiez que votre serveur distant est accessible.
1. Ajoutez l’un des fragments de code suivants au modèle HTL d’un composant AEM.
1. Vous pouvez éventuellement créer ou modifier les configurations OSGi.
1. Parcourir le contenu de votre site.

En général, le modèle HTL d’un composant de page est le principal destinataire d’une telle fonctionnalité.

```html
<sly data-sly-resource="${resource @ resourceType='cq/remote/content/renderer/request/handler'}" />
```

### Conditions requises {#requirements}

Les servlets utilisent l’exportateur de modèle Sling pour sérialiser les données de composant. Par défaut, les composants `com.adobe.cq.export.json.ContainerExporter` et `com.adobe.cq.export.json.ComponentExporter` sont pris en charge en tant qu’adaptateurs de modèle Sling. Si nécessaire, vous pouvez ajouter des classes auxquelles la requête doit être adaptée à l’aide du composant `RemoteContentRendererServlet` et en mettant le composant `RemoteContentRendererRequestHandler#getSlingModelAdapterClasses` en œuvre. Les classes supplémentaires doivent étendre le composant `ComponentExporter`.
