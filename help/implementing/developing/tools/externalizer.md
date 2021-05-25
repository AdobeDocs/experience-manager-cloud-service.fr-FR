---
title: Externalisation d’URL
description: L’externaliseur est un service OSGi qui vous permet de transformer par programmation un chemin d’accès aux ressources en une URL externe et absolue.
exl-id: 06efb40f-6344-4831-8ed9-9fc49f2c7a3f
source-git-commit: ce43bdc94f14faa69add16139e22ea3f34dfc52f
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 19%

---

# Externalisation d’URL {#externalizing-urls}

Dans AEM, **Externalizer** est un service OSGi qui vous permet de transformer par programmation un chemin de ressource (par exemple, `/path/to/my/page`) dans une URL externe et absolue (par exemple, `https://www.mycompany.com/path/to/my/page`) en ajoutant un préfixe au chemin d’accès avec un DNS préconfiguré.

Étant donné qu’une AEM en tant qu’instance de Cloud Service ne peut pas connaître son URL visible en externe et qu’il est parfois nécessaire de créer un lien en dehors du périmètre de la requête, ce service fournit un emplacement central pour configurer ces URL externes et les créer.

Cet article explique comment configurer le service Externalizer et comment l’utiliser. Pour obtenir des détails techniques sur le service, reportez-vous aux [Javadocs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/Externalizer.html).

## Comportement par défaut de l’externaliseur et comment remplacer {#default-behavior}

Par défaut, le service Externalizer contient des valeurs telles que `author-p12345-e6789.adobeaemcloud.com` et `publish-p12345-e6789.adobeaemcloud.com`.

Pour remplacer ces valeurs, utilisez les variables d’environnement Cloud Manager comme décrit dans l’article [Configuration d’OSGi pour AEM en tant que Cloud Service](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) et définition des variables `AEM_CDN_DOMAIN_AUTHOR` prédéfinies et `AEM_CDN_DOMAIN_PUBLISH` prédéfinies.

## Configuration du service Externalizer {#configuring-the-externalizer-service}

Le service Externalizer vous permet de définir de manière centralisée le domaine qui peut être utilisé pour préfixer par programmation les chemins d’accès aux ressources. Le service Externalizer ne doit être utilisé que pour les applications d’un seul domaine.

>[!NOTE]
>
>Comme lors de l’application de toutes les configurations [OSGi pour AEM en tant que Cloud Service,](/help/implementing/deploying/overview.md#osgi-configuration) les étapes suivantes doivent être exécutées sur une instance de développeur locale, puis validées dans le code de votre projet pour le déploiement.

Pour définir un mappage de domaine pour le service Externalizer, procédez comme suit :

1. Accédez à Configuration Manager via :

   `https://<host>:<port>/system/console/configMgr`

1. Cliquez sur **Day CQ Link Externalizer** pour ouvrir la boîte de dialogue de configuration.

   ![Configuration OSGi de l’externaliseur](./assets/externalizer-osgi.png)

   >[!NOTE]
   >
   >Le lien direct vers la configuration est `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

1. Définissez un mappage **Domaines**. Un mappage se compose d’un nom unique qui peut être utilisé dans le code pour référencer le domaine, un espace et le domaine :

   `<unique-name> [scheme://]server[:port][/contextpath]`

   Où :

   * **`scheme`** est généralement http ou https, mais peut être un autre protocole.

      * Il est recommandé d’utiliser https pour appliquer les liens https.
      * Il sera utilisé si le code client ne remplace pas le schéma lors de la demande d’externalisation d’une URL.
   * **`server`** est le nom d’hôte (nom de domaine ou adresse ip).
   * **`port`** (facultatif) est le numéro de port.
   * **`contextpath`** (facultatif) est défini uniquement si AEM est installé en tant qu’application web sous un autre chemin d’accès au contexte.

   Par exemple : `production https://my.production.instance`

   Les noms de mappage suivants sont prédéfinis et doivent toujours être définis car AEM s’y appuie :

   * `local` - instance locale
   * `author` - le DNS du système de création
   * `publish` - DNS du site web public

   >[!NOTE]
   >
   >Une configuration personnalisée vous permet d’ajouter une nouvelle catégorie, telle que `production`, `staging` ou même des systèmes externes non AEM tels que `my-internal-webservice`. Il est utile d’éviter de coder en dur de telles URL à différents endroits dans le code base d’un projet.

1. Cliquez sur **Enregistrer** pour enregistrer vos modifications.

### Utilisation du service Externalizer {#using-the-externalizer-service}

Cette section illustre quelques exemples d’utilisation du service Externalizer.

>[!NOTE]
>
>Aucun lien absolu ne doit être créé dans le contexte du code HTML. Par conséquent, cet utilitaire ne doit pas être utilisé dans de tels cas.

* **Pour externaliser un chemin d’accès avec le domaine « publish » :**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   En supposant le mappage de domaine :

   * `publish https://www.website.com`

   * `myExternalizedUrl` se termine par la valeur :

   * `https://www.website.com/contextpath/my/page.html`

* **Pour externaliser un chemin d’accès avec le domaine « author » :**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   En supposant le mappage de domaine :

   * `author https://author.website.com`

   * `myExternalizedUrl` se termine par la valeur :

   * `https://author.website.com/contextpath/my/page.html`

* **Pour externaliser un chemin d’accès avec le domaine « local », procédez comme suit :**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   En supposant le mappage de domaine :

   * `local https://publish-3.internal`

   * `myExternalizedUrl` se termine par la valeur :

   * `https://publish-3.internal/contextpath/my/page.html`

>[!TIP]
>
>Vous trouverez d’autres exemples dans les [Javadocs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/Externalizer.html).
