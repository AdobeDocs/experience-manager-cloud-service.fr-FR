---
title: Externalisation d’URL
description: Externalizer est un service OSGi qui vous permet de transformer, par programmation, un chemin d’accès aux ressources en une URL externe et absolue.
exl-id: 06efb40f-6344-4831-8ed9-9fc49f2c7a3f
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 77%

---

# Externalisation d’URL {#externalizing-urls}

Dans AEM, le **Externalizer** est un service OSGi qui vous permet de transformer, par programmation, un chemin d’accès aux ressources (par exemple, `/path/to/my/page`) en une URL externe et absolue (par exemple, `https://www.mycompany.com/path/to/my/page`) en faisant précéder le chemin d’accès d’un DNS préconfiguré.

Étant donné qu’AEM as a Cloud Service ne peut pas connaître son URL visible en externe et qu’il est parfois nécessaire de créer un lien hors de portée de la requête, ce service fournit un emplacement central pour configurer ces URL externes et les créer.

Cet article explique comment configurer le service Externalizer et comment l’utiliser. Pour obtenir des détails techniques sur le service, voir [Javadocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html).

## Comportement par défaut du service Externalizer et comment le contourner {#default-behavior}

Le service Externalizer, prêt à l’emploi, mappe un petit nombre d’identifiants de domaine vers des préfixes d’URL absolus correspondant aux URL des services AEM qui ont été générés pour l’environnement, tels que `author https://author-p12345-e6789.adobeaemcloud.com` et `publish https://publish-p12345-e6789.adobeaemcloud.com`. Les URL de base de chacun de ces domaines par défaut sont lues à partir des variables d’environnement définies par Cloud Manager.

À titre de référence, la configuration OSGi par défaut pour `com.day.cq.commons.impl.ExternalizerImpl.cfg.json` est efficace :

```json
{
   "externalizer.domains": [
      "local $[env:AEM_EXTERNALIZER_LOCAL;default=http://localhost:4502]",
      "author $[env:AEM_EXTERNALIZER_AUTHOR;default=http://localhost:4502]",
      "publish $[env:AEM_EXTERNALIZER_PUBLISH;default=http://localhost:4503]",
      "preview $[env:AEM_EXTERNALIZER_PREVIEW;default=http://localhost:4503]"
   ]
}
```

>[!CAUTION]
>
>Les mappages par défaut des domaines `local`, `author`, `preview` et `publish` du service Externalizer dans la configuration OSGi doivent être préservés avec les valeurs originales `$[env:...]` énumérées ci-dessus.
>
>Le déploiement d’un fichier `com.day.cq.commons.impl.ExternalizerImpl.cfg.json` personnalisé vers AEM as a Cloud Service qui omet l’un de ces mappages de domaine prêts à l’emploi peut entraîner un comportement imprévisible de l’application.

Pour remplacer les valeurs `preview` et `publish`, utilisez les variables d’environnement Cloud Manager comme décrit dans l’article [Configurer OSGi pour AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) et définissez les variables prédéfinies `AEM_CDN_DOMAIN_PUBLISH` et `AEM_CDN_DOMAIN_PREVIEW`.

## Configuration du service Externalizer {#configuring-the-externalizer-service}

Le service Externalizer vous permet de définir, de manière centralisée, le domaine qui peut être utilisé pour préfixer des chemins d’accès aux ressources par programmation. Le service Externalizer ne doit être utilisé que pour les applications à domaine unique.

>[!NOTE]
>
>Comme pour l’application de toutes les configurations [OSGi pour AEM as a Cloud Service](/help/implementing/deploying/overview.md#osgi-configuration), les étapes suivantes doivent être exécutées sur une instance développeur locale, puis validées dans le code de votre projet pour le déploiement.

Pour définir un mappage de domaine pour le service Externalizer, procédez comme suit :

1. Accédez au gestionnaire de configuration via :

   `https://<host>:<port>/system/console/configMgr`

1. Cliquez sur **Day CQ Link Externalizer** pour ouvrir la boîte de dialogue de configuration.

   ![Configuration OSGi du service Externalizer](./assets/externalizer-osgi.png)

   >[!NOTE]
   >
   >Le lien direct vers la configuration est `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

1. Définissez un mappage **Domaines**. Un mappage correspond à un nom unique (qui peut être utilisé dans le code pour référencer le domaine), d’un espace et du domaine :

   `<unique-name> [scheme://]server[:port][/contextpath]`

   Où :

   * **`scheme`** est généralement http ou https, mais peut être un autre protocole.

      * Adobe recommande d’utiliser https pour appliquer les liens https.
      * Il est utilisé si le code client ne remplace pas le schéma lors de la demande d’externalisation d’une URL.

   * **`server`** est le nom d’hôte (un nom de domaine ou une adresse IP).
   * **`port`** (facultatif) est le numéro de port.
   * **`contextpath`** (facultatif) est défini uniquement si AEM est installé en tant qu’application web sous un autre chemin d’accès au contexte.

   Par exemple : `production https://my.production.instance`

   Les noms de mappage suivants sont prédéfinis et doivent toujours être configurés, car AEM en dépend :

   * `local` : instance locale
   * `author` : DNS du système de création
   * `publish` : DNS du site public

   >[!NOTE]
   >
   >Une configuration personnalisée vous permet d’ajouter une nouvelle catégorie, telle que `production`, `staging` ou même des systèmes externes non AEM tels que `my-internal-webservice`. Il est utile d’éviter de coder en dur de telles URL à différents endroits dans le code de base d’un projet.

1. Cliquez sur **Enregistrer** pour enregistrer vos modifications.

### Utilisation du service Externalizer {#using-the-externalizer-service}

Cette section illustre quelques exemples d’utilisation du service Externalizer.

>[!NOTE]
>
>Aucun lien absolu ne doit être créé dans le contexte du code HTML. Par conséquent, n’utilisez pas cet utilitaire dans de tels cas.

* **Pour externaliser un chemin d’accès avec le domaine « publish » :**

  ```java
  String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
  ```

  En prenant le mappage de domaine :

   * `publish https://www.website.com`

   * `myExternalizedUrl` se termine par la valeur :

   * `https://www.website.com/contextpath/my/page.html`

* **Pour externaliser un chemin d’accès avec le domaine « author » :**

  ```java
  String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
  ```

  En prenant le mappage de domaine :

   * `author https://author.website.com`

   * `myExternalizedUrl` se termine par la valeur :

   * `https://author.website.com/contextpath/my/page.html`

* **Pour externaliser un chemin d’accès avec le domaine « local », procédez comme suit :**

  ```java
  String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
  ```

  En prenant le mappage de domaine :

   * `local https://publish-3.internal`

   * `myExternalizedUrl` se termine par la valeur :

   * `https://publish-3.internal/contextpath/my/page.html`

>[!TIP]
>
>Vous trouverez d’autres exemples dans les [Javadocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html).
