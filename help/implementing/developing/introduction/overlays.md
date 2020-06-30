---
title: Incrustations pour Adobe Experience Manager en tant que Cloud Service
description: AEM en tant que Cloud Service utilise le principe des incrustations pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités.
translation-type: tm+mt
source-git-commit: 58440cb565039becd5b08333994b70f2ea77cc99
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 39%

---


# Incrustations dans AEM en tant que Cloud Service {#overlays-in-aem}

L’Adobe Experience Manager en tant que Cloud Service utilise le principe des incrustations pour vous permettre d’étendre et de personnaliser les consoles et d’autres fonctionnalités (par exemple, la création de pages).

<!--
Adobe Experience Manager as a Cloud Service uses the principle of overlays to allow you to extend and customize the [consoles](/help/sites-developing/customizing-consoles-touch.md) and other functionality (for example, [page authoring](/help/sites-developing/customizing-page-authoring-touch.md)).
-->

Incrustation est un terme qui peut être utilisé dans de nombreux contextes. Dans ce contexte (extension d’AEM en tant que Cloud Service), une incrustation signifie prendre la fonctionnalité prédéfinie et imposer vos propres définitions sur celle-ci (pour personnaliser la fonctionnalité standard).

In a standard instance the predefined functionality is held under `/libs` and it is recommended practice to define your overlay (customizations) under the `/apps` branch. AEM uses a search path to find a resource, searching first the `/apps` branch and then the `/libs` branch (the [search path can be configured](#configuring-the-search-paths)). Ce mécanisme signifie que votre incrustation (et les personnalisations qui y sont définies) est prioritaire.

* L’interface utilisateur tactile utilise des incrustations liées à [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html):

   * Méthode

      * Reconstruct the appropriate `/libs` structure under `/apps`.

         This does not require a 1:1 copy, as the [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) is used to cross-reference the original definitions that are required. Sling Resource Merger propose des services pour accéder à des ressources et les fusionner par le biais de mécanismes de différenciation (diff).

      * Make any changes under `/apps`.
   * Avantages

      * Plus résistant aux modifications sous `/libs`.
      * Vous ne devez redéfinir que ce qui est réellement nécessaire.


<!-- Still links to reference material in 6.5 -->

>[!CAUTION]
>
>[Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) et les méthodes connexes ne peuvent être utilisées qu’avec [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html). Cela signifie que la création d’une incrustation avec une ossature n’est appropriée que pour l’interface utilisateur (IU) tactile standard.

Il est conseillé de recourir aux incrustations pour de nombreuses modifications ; par exemple, pour configurer vos consoles ou créer votre catégorie de sélection dans l’explorateur de ressources dans le panneau latéral (utilisé lors de la création de pages). Elles sont requises pour les raisons suivantes :

<!--
Overlays are the recommended method for many changes, such as [configuring your consoles](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) or [creating your selection category to the asset browser in the side panel](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (used when authoring pages). They are required as:
-->

* You ***must not *make changes in the`/libs`branch **Any changes you do make may be lost, because this branch is liable to changes whenever you:

   * mettez à niveau votre instance ;
   * appliquez un correctif logiciel ;
   * installez un Feature Pack.

* Elles centralisent vos modifications dans un seul emplacement ; cela facilite le suivi, la migration, la sauvegarde et/ou le débogage de vos modifications, suivant les besoins.

## Configuration des chemins de recherche {#configuring-the-search-paths}

Dans le cas des incrustations, la ressource diffusée est un regroupement des ressources et propriétés récupérées, en fonction des chemins de recherche qui peuvent être définis :

* La ressource **Resolver Search Path**, telle qu’elle est définie dans la [configuration OSGi ](/help/implementing/deploying/configuring-osgi.md) pour **Apache Sling Resource Resolver Factory**.

   * L’ordre des chemins de recherche de haut en bas indique leurs priorités respectives.
   * In a standard installation the primary defaults are `/apps`, `/libs` - so the content of `/apps` has a higher priority than that of `/libs` (i.e. it *overlays* it).

* Deux utilisateurs du service ont besoin de l’accès JCR:READ à l’emplacement où les scripts sont stockés. Ces utilisateurs sont : components-search-service (utilisé par les com.day.cq.wcm.coreto access/cache components) et sling-scripting (utilisé par org.apache.sling.servlets.resolver pour trouver des servlets).
* La configuration suivante doit également être configurée en fonction de l&#39;emplacement de vos scripts (dans cet exemple sous /etc, /libs ou /apps).

   ```
   PID = org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl
   resource.resolver.searchpath=["/etc","/apps","/libs"]
   resource.resolver.vanitypath.whitelist=["/etc/","/apps/","/libs/","/content/"]
   ```

* Enfin, le Servlet Resolver doit également être configuré (dans cet exemple pour ajouter /etc également)

   ```
   PID = org.apache.sling.servlets.resolver.SlingServletResolver
   servletresolver.paths=["/bin/","/libs/","/apps/","/etc/","/system/","/index.servlet","/login.servlet","/services/"]
   ```

<!--
## Example of Usage {#example-of-usage}

Some examples are covered when:

* [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
* [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)
-->