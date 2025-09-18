---
title: Création d’URL de redirection à l’aide de Dynamic Media avec les fonctionnalités OpenAPI
description: Utilisez les fonctionnalités OpenAPI de Dynamic Media pour transformer vos URL de diffusion de ressources longues en URL de redirection courtes de marque. Une URL Vanity est une version courte, propre, facile à mémoriser et lisible de votre URL de diffusion complexe. Vous pouvez inclure le nom de votre marque, les noms de produits et les mots-clés pertinents dans l’URL Vanity pour améliorer la visibilité de votre marque et l’interaction client
role: Admin
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: c72966bff9220b681f8c1e4c534f19cb4b950700
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 0%

---


# Utiliser des URL de redirection vers un microsite ?{#vanity-urls}

Utilisez [!DNL Dynamic Media OpenAPI capabilities] pour transformer vos URL de diffusion de ressources longues en URL de redirection courtes de marque. Les URL de diffusion de ressources standard incluent les UUID de ressources générés par le système qui rendent l’URL de diffusion complexe, difficile à mémoriser et à partager. Remplacez ces UUID de ressources par des identifiants simples (ID de redirection) pour générer une URL de redirection. Une URL de redirection est une version courte, propre et lisible de votre URL de diffusion complexe.

Consultez les formats d’URL suivants pour comprendre leur différence :
* [URL de diffusion standard](#standard-urls)
* [URL de redirection](#vanity-url)

Les URL de diffusion standard utilisent `aaid` suivi d’un UUID, tandis que les URL de redirection utilisent `avid` suivi d’un identifiant personnalisé (identifiant de redirection).

Utilisez des identifiants de redirection courts et simples pour rendre votre URL de diffusion courte, propre, lisible, facile à mémoriser et à partager. Utilisez votre nom de marque, vos noms de produit et vos mots-clés pertinents comme ID de redirection pour améliorer la visibilité de votre marque et l’engagement des utilisateurs.

Lorsque l’utilisateur clique sur votre URL Vanity, [!DNL Dynamic Media with OpenAPI] mappe automatiquement à l’emplacement de la ressource d’origine au moment de l’ingestion et les résout correctement au moment de la diffusion afin de la diffuser à l’utilisateur.

Découvrez comment [créer des URL de redirection](#create-vanity-urls).

## URL de diffusion standard{#standard-urls}

L’URL de diffusion de ressources [!DNL Dynamic Media with OpenAPI] standard comprend un identifiant unique généré par le système et suit le format suivant.

***Format:*** `https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:aaid:aem:<asset-uuid>/as/<seoname>.<format>`

L’URL de diffusion standard comprend `aaid` (*identifiant réel de la ressource*) après `urn:` et un UUID compris entre `urn:aaid:aem:` et `/as/<seoname>.<format>`.

***Exemple :*** `https://delivery-p30902-e145436.adobeaemcloud.com/adobe/assets/urn:aaid:aem:43341ab1-4086-44d2-b7ce-ee546c35613b/as/check.jpeg`

Dans l’exemple ci-dessus, `43341ab1-4086-44d2-b7ce-ee546c35613b` est l’UUID.

## URL de redirection{#vanity-url}

Les URL de redirection vers un microsite comprennent un identifiant de redirection vers un microsite à la place de l’UUID de ressource et suivent le format suivant.

***Format:*** `https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:avid:aem:<vanity-id>/<seoname>.<format>`

L’URL de redirection vers un microsite comprend `avid` (*identifiant de redirection vers un microsite*) après `urn:` et votre ID de redirection vers un microsite entre `urn:avid:aem:` et `/<seoname>.<format>`.

***Exemple :*** `https://delivery-p30902-e145436.adobeaemcloud.com/adobe/assets/urn:avid:aem:VanityCheck/as/check.jpeg`

Dans l’exemple ci-dessus, `VanityCheck` est l’ID Vanity qui a remplacé l’UUID.

## Explorer les fonctionnalités et avantages clés{#capabilities-and-benefits-of-vanity-urls}

L’utilisation d’identifiants Vanity significatifs pour personnaliser les URL de diffusion de ressources standard offre plusieurs avantages et un impact mesurable. Voici quelques-unes des principales fonctionnalités et avantages des URL de redirection vers un microsite.

### Fonctionnalités essentielles{#key-capabilities}

* **Personnalisation de l’URL :** remplacez les identifiants longs (UUID de ressource) dans l’URL de diffusion par d’autres identifiants plus courts, alignés sur la marque, afin de générer une URL de diffusion plus propre.
* **Redirection en temps réel :** les URL Vanity redirigent vers les UUID des ressources d’origine au moment de l’exécution sans interrompre les workflows. Les utilisateurs voient des URL propres dans la barre d’adresse pendant que le système gère le routage technique.
* **Gestion facile des liens :** personnalisez vos URL de redirection à tout moment sans affecter les performances de diffusion des ressources.

### Principaux avantages{#key-benefits}

* **Améliore l’expérience utilisateur :** les URL de redirection épurées et plus courtes sont lisibles, conviviales, faciles à mémoriser et à partager.

* **Améliore l’interaction client :** les URL de marque renforcent la confiance client. Les utilisateurs sont plus susceptibles de cliquer sur des liens professionnels de marque, ce qui entraîne des taux de clics publicitaires plus élevés.

* **Optimisation du référencement :** URL qui incluent des mots-clés pertinents améliorent les classements des moteurs de recherche et la capacité de découverte.

* **Visibilité améliorée de la marque :** les URL spécifiques à la marque renforcent la présence de la marque sur tous les canaux marketing, y compris les e-mails, les médias sociaux et les campagnes publicitaires.
En outre, l’utilisation cohérente des URL de marque dans toutes les communications renforce l’identité et la reconnaissance de la marque.

* **Suivi et analyse des campagnes :** utilisez des URL de redirection uniques pour différentes campagnes et différents canaux afin d’obtenir des informations détaillées sur les sources de trafic et les performances de conversion.

## Conditions préalables{#prerequisites-for-creating-vanity-id}

Pour créer l’URL de redirection vers un microsite, vérifiez que vous avez [approuvé les ressources pour la diffusion publique](/help/assets/manage-organize-assets-view.md#manage-asset-status).

## Création d’URL de redirection{#create-vanity-urls}

Pour créer des URL de redirection vers un microsite, procédez comme suit :
1. [Configurer les métadonnées des ressources](#set-up-asset-metadata)
1. [Créer et mapper une variable d’environnement Cloud Manager](#map-cloud-manager-environment-variable)
1. [Approuver les ressources nécessitant une URL de redirection pour la diffusion](/help/assets/manage-organize-assets-view.md#manage-asset-status)
1. [Générer des URL Vanity](#generate-vanity-urls)

### Configurer les métadonnées des ressources{#set-up-asset-metadata}

Exécutez la procédure suivante pour configurer l’ID de redirection dans le formulaire de métadonnées de votre ressource :
1. Accédez à la page de détails du dossier contenant vos ressources pour [!DNL Dynamic Media with OpenAPI] diffusion.
1. [Modifiez ce formulaire de métadonnées](/help/assets/metadata-assets-view.md#edit-metadata-forms) en effectuant l’une des opérations suivantes :
   * Ajoutez un nouveau champ de métadonnées et spécifiez l’ID de redirection requis en tant que valeur de ce champ.
   * Mettez à jour le champ existant en remplaçant la valeur d’une propriété de métadonnées existante par l’ID de redirection requis. Découvrez les [bonnes pratiques](#best-practices) pour créer l’ID de redirection.
     ![ID de redirection](/help/assets/assets/vanity-id-metadata.png)
En savoir plus sur les [schémas de métadonnées](/help/assets/metadata-schemas.md).

     >[!NOTE]
     >
     > Une seule ressource peut avoir plusieurs ID de redirection vers un microsite. [Contactez l’assistance Adobe](https://helpx.adobe.com/in/contact.html) et envoyez une demande pour générer les identifiants de redirection requis.

Après avoir configuré votre ID de redirection dans le formulaire de métadonnées de ressource, [mappez ce champ de métadonnées au mécanisme de diffusion du système](#map-cloud-manager-environment-variable).

### Créer et mapper une variable d’environnement Cloud Manager{#map-cloud-manager-environment-variable}

Exécutez les étapes suivantes pour créer une variable d’environnement et la mapper au champ de métadonnées contenant l’ID de redirection :

1. [Accédez à la page des configurations de votre environnement Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) puis procédez comme suit :
   1. Ajoutez la variable `ASSET_DELIVERY_VANITY_ID` . C&#39;est la clé.
   1. Utilisez le champ de valeur pour mapper la propriété de métadonnées qui contient l’ID de redirection. Le mappage suit le format `dc:<your-metadata-property>`, où le préfixe de mappage des métadonnées (tel que dc:) varie en fonction de votre propriété de configuration des métadonnées.
      ![Variable ASSET_DELIVERY_VANITY_ID](/help/assets/assets/environment-config.png)
1. Enregistrez vos modifications pour redémarrer les capsules dans votre environnement.

### Valider les ressources à diffuser{#approve-assets-for-delivery}

Après avoir mappé la variable `ASSET_DELIVERY_VANITY_ID` dans votre environnement Cloud Manager à la propriété de métadonnées de ressource qui contient l’ID de redirection, [approuvez les ressources qui nécessitent une URL de redirection pour la diffusion](/help/assets/manage-organize-assets-view.md#manage-asset-status).

### Générer des URL de redirection{#generate-vanity-urls}

Effectuez les remplacements suivants dans votre URL de diffusion standard pour la transformer en URL Vanity :

* Remplacez **UUID** par votre **ID Vanity**.
* Remplacez `aaid` par `avid`.

Consultez la section [Transformation d’une URL standard en URL Vanity](#standard-urls) ci-dessus.
Découvrez comment [copier Dynamic Media avec des URL de diffusion OpenAPI](/help/assets/approve-assets.md#copy-delivery-url-for-approved-assets) pour vos ressources.

Lorsque l’utilisateur clique sur l’URL de redirection, [!DNL Dynamic Media with OpenAPI] mappe automatiquement l’ID de redirection vers l’UUID de ressource d’origine au moment de l’ingestion et le résout correctement au moment de la diffusion afin de diffuser la ressource à l’utilisateur sans délai. Vous pouvez personnaliser l’URL Vanity en temps réel sans affecter les performances de diffusion des ressources.

[Améliorez l’impact de vos URL de redirection grâce aux fonctionnalités de personnalisation avancées d’AEM Cloud Service.](#scale-using-vanity-url)

## Mise à l’échelle à l’aide d’URL de redirection vers un microsite{#scale-using-vanity-url}

AEM as a Cloud Service vous permet de [personnaliser les noms DNS et de réseau CDN](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/introduction) au sein de vos adresses web. Utilisez ces fonctionnalités AEMCS avec vos URL de redirection pour les transformer en adresses web uniques, propres, descriptives, de marque, intuitives et offrant les [avantages mentionnés ci-dessus](#key-benefits).

Consultez l’URL Vanity suivante et ses composants personnalisables :

**Format d’URL Vanity :**

`https://delivery-<tenant>.adobeaemcloud.com/adobe/assets/urn:avid:aem:<vanity-id>/<seoname>.<format>`

<table style="border-collapse:collapse; table-layout:auto; width:auto;">
<tr valign="top">
<td style="padding:0 4px; white-space:nowrap; text-align:center;">
<div style="text-align:left;"><code>https://delivery&#8209;&lt;tenant&gt;.adobeaemcloud.com</code></div>
<div style="text-align:center;">↓</div>
<div style="text-align:center;"><a href="#customize-dns">Personnaliser ce DNS</a></div>
</td>
<td style="padding:0 6px; white-space:nowrap; text-align:center;">/</td>
<td style="padding:0 4px; white-space:nowrap; text-align:center;">
<div style="text-align:left;"><code>adobe/assets/urn:avid:aem:</code></div>
<div style="text-align:center;">↓</div>
<div style="text-align:center;"><a href="#rewrite-cdn-rules">Personnaliser l’URL avec des règles de réécriture</a></div>
</td>
<td style="padding:0 4px; white-space:nowrap; text-align:center;">
<div style="text-align:left;"><code>&lt;vanity-id&gt;</code></div>
<div style="text-align:center;">↓</div>
<div style="text-align:center;"><a href="#create-vanity-urls">Créer un ID de redirection</a></div>
</td>
<td style="padding:0 4px; white-space:nowrap; text-align:left; width:1%;">
<code>/&lt;seoname&gt;.&lt;format&gt;</code>
</td>
</tr>
</table>

**Format d’URL Vanity avec noms DNS et CDN personnalisés :**

`https://<custom-dns>` `/` `dam/assets/` `<vanity-id>` `/<seoname>.<format>`

**Composants d’URL personnalisables**

* ***[Nom DNS (nom d’hôte) :](#customize-DNS)*** `https://delivery-<tenant>.adobeaemcloud.com` est le domaine de serveur qui héberge vos ressources. [Personnalisez le DNS pour modifier le nom d’hôte](#customize-DNS).
* ***[Règles de réécriture du réseau CDN :](#rewrite-cdn-rules)*** `adobe/assets/urn:avid:aem:` est la structure de chemin d’accès qui identifie les types de ressources et les méthodes de diffusion. [Réécrivez les règles du réseau CDN](#rewrite-cdn-rules) pour modifier le chemin d’accès au domaine.

### Personnaliser le DNS{#customize-dns}

[Envoyez une demande à l’assistance Adobe](https://helpx.adobe.com/in/contact.html) pour générer le DNS personnalisé requis pour le niveau de votre diffusion. Suivez ces [bonnes pratiques](#best-practices) pour créer des noms DNS personnalisés.

### Réécrire les règles du réseau CDN{#rewrite-cdn-rules}

Exécutez les étapes suivantes pour réécrire les règles de réseau CDN pour la diffusion :

1. Accédez à votre référentiel AEM pour créer un fichier de configuration YAML.
2. Exécutez les étapes de la section [configuration](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-error-pages#setup) pour configurer les règles du réseau CDN et déployer la configuration via votre pipeline de configuration Cloud Manager.
Suivez ces [bonnes pratiques](#best-practices) pour créer le chemin d’accès au domaine.
   [En savoir plus sur les règles de réécriture CDN](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#request-transformations).

Vous trouverez ci-dessous des exemples de règles de réécriture pour ajouter des noms de fichiers avec des extensions dans les URL Vanity. Personnalisez ces règles de réécriture en fonction de vos besoins. [Contactez l’assistance Adobe](https://helpx.adobe.com/in/contact.html) pour obtenir de l’aide :

```- name: cdn-rewrite-rule
  when:
    allOf:
      - reqProperty: tier
        equals: delivery
```

#### Pour SVG, GIF et PDF {#svg-gif-pdf}

```
    type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.(?:svg|gif|pdf|docx|xlsx))(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/original/as/\1\2
```

#### Pour la vidéo{#video}

Pour les vidéos comprenant MP4, MOV, AVI et MKV

```
type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.(?:mp4|mov|avi|mkv))(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/play\2
```

#### Pour l’image{#image}

Pour tous les types d’images, à l’exclusion de SVG.

```
type: transform
      reqProperty: path
      op: replace
      match: ^/dam/assets/([^/]+\.[^/]+)(\?.*)?$
      replacement: /adobe/assets/urn:avid:aem:\1/as/\1\2
```

## Suivez les bonnes pratiques pour créer des URL de redirection propres{#best-practices}

Suivez ces bonnes pratiques pour créer des identifiants de redirection, des DNS personnalisés et des noms de domaine :

1. N’utilisez pas de caractères spéciaux dans les identifiants de redirection, tels que des espaces, des barres obliques, des tirets, etc. Le système remplace les caractères spéciaux dans les ID de redirection à l’aide d’un mappage prédéfini.
1. Utilisez votre nom de marque, vos noms de produit et les mots-clés pertinents dans vos identifiants de redirection, vos noms DNS personnalisés et vos noms de domaine pour améliorer la visibilité de votre marque et l’engagement des utilisateurs.
1. Utilisez des mots ou des chaînes courts et descriptifs qui véhiculent du sens.
1. Utilisez des textes qui invitent les utilisateurs à cliquer.
