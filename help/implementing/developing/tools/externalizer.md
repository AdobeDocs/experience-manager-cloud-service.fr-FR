---
title: Externalisation d’URL
description: Externalizer est un service OSGi qui vous permet de transformer par programmation un chemin de ressource en une URL externe et absolue.
translation-type: tm+mt
source-git-commit: 4c584ceadaa358120d1d4b4cabd7e21ced814b31
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 18%

---


# Externalisation d’URL {#externalizing-urls}

En AEM, le **Externalizer** est un service OSGi qui vous permet de transformer par programmation un chemin de ressources (par ex. `/path/to/my/page`) dans une URL externe et absolue (par exemple, `https://www.mycompany.com/path/to/my/page`) en préfixant le chemin d’accès avec un DNS préconfiguré.

Comme un AEM en tant qu’instance de Cloud Service ne peut pas connaître son URL visible en externe et qu’il est parfois nécessaire de créer un lien en dehors de l’étendue de la demande, ce service fournit un emplacement central pour configurer ces URL externes et les créer.

Cet article explique comment configurer le service Externalizer et comment l&#39;utiliser. Pour les détails techniques du service, veuillez consulter le [Javadocs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/Externalizer.html).

## Comportement par défaut de l’Externaliseur et comment remplacer {#default-behavior}

Le service Externalizer est prêt à l’emploi et comporte des valeurs telles que `author-p12345-e6789.adobeaemcloud.com` et `publish-p12345-e6789.adobeaemcloud.com` déjà définies de sorte que, sans aucune intervention, votre AEM en tant qu’installation Cloud Service utilise votre domaine personnalisé.

Pour remplacer ces valeurs, utilisez les variables d’environnement de Cloud Manager comme décrit dans l’article [Configuration d’OSGi pour AEM en tant que Cloud Service](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) et définition des variables prédéfinies `AEM_CDN_DOMAIN_AUTHOR` et `AEM_CDN_DOMAIN_PUBLISH`.

## Configuration du service Externalizer {#configuring-the-externalizer-service}

Le service Externalizer vous permet de définir de manière centralisée le domaine qui peut être utilisé pour préfixer par programmation les chemins de ressources. Le service Externalizer ne doit être utilisé que pour les applications avec un seul domaine.

>[!NOTE]
>
>Comme lors de l&#39;application de toute configuration [OSGi pour AEM en tant que Cloud Service,](/help/implementing/deploying/overview.md#osgi-configuration) les étapes suivantes doivent être effectuées sur une instance de développeur locale, puis validées dans votre code de projet pour le déploiement.

Pour définir un mappage de domaine pour le service Externalizer, procédez comme suit :

1. Accédez à Configuration Manager via :

   `https://<host>:<port>/system/console/configMgr`

1. Cliquez sur **Externalisateur de liens Day CQ** pour ouvrir la boîte de dialogue de configuration.

   ![Configuration OSGi de Externalizer](./assets/externalizer-osgi.png)

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

   Les noms de mappage suivants sont prédéfinis et doivent toujours être définis en fonction de leur utilisation AEM :

   * `local` - l&#39;instance locale
   * `author` - le DNS du système de création
   * `publish` - DNS du site Web destiné au public

   >[!NOTE]
   >
   >Une configuration personnalisée vous permet d’ajouter une nouvelle catégorie, telle que `production`, `staging` ou même des systèmes externes non AEM tels que `my-internal-webservice`. Il est utile d’éviter de coder en dur de telles URL à différents emplacements de la base de code d’un projet.

1. Cliquez sur **Enregistrer** pour enregistrer vos modifications.

### Utilisation du service Externalizer {#using-the-externalizer-service}

Cette section illustre quelques exemples d’utilisation du service Externalizer.

>[!NOTE]
>
>Aucun lien absolu ne doit être créé dans le contexte du code HTML. Par conséquent, cet utilitaire ne devrait pas être utilisé dans de tels cas.

* **Pour externaliser un chemin d’accès avec le domaine « publish » :**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   En supposant le mappage de domaines :

   * `publish https://www.website.com`

   * `myExternalizedUrl` se termine par la valeur :

   * `https://www.website.com/contextpath/my/page.html`

* **Pour externaliser un chemin d’accès avec le domaine « author » :**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   En supposant le mappage de domaines :

   * `author https://author.website.com`

   * `myExternalizedUrl` se termine par la valeur :

   * `https://author.website.com/contextpath/my/page.html`

* **Pour externaliser un chemin d’accès avec le domaine « local », procédez comme suit :**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   En supposant le mappage de domaines :

   * `local https://publish-3.internal`

   * `myExternalizedUrl` se termine par la valeur :

   * `https://publish-3.internal/contextpath/my/page.html`

>[!TIP]
>
>Vous trouverez d’autres exemples dans les [Javadocs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/Externalizer.html).
