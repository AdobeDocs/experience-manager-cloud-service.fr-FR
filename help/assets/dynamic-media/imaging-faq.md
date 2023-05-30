---
title: Imagerie dynamique
description: Découvrez comment l’imagerie intelligente avec l’IA Adobe Sensei applique les caractéristiques de visualisation uniques de chaque utilisateur pour diffuser automatiquement les images optimisées pour leur expérience, ce qui se traduit par des performances accrues et une meilleure interaction.
contentOwner: Rick Brough
feature: Asset Management,Renditions
role: User
mini-toc-levels: 2
exl-id: 863784d9-0c91-4deb-8edd-1354a21581c3
source-git-commit: c48885dc11b0162f0288962a53e1d95574a3d406
workflow-type: tm+mt
source-wordcount: '3536'
ht-degree: 86%

---

# FAQ sur l’imagerie dynamique {#smart-imaging}

## À propos de l’imagerie dynamique

La technologie d’imagerie dynamique applique les fonctionnalités d’intelligence artificielle d’Adobe Sensei et fonctionne avec les « paramètres d’image prédéfinis » existants. Elle permet d’améliorer les performances de la diffusion d’images en optimisant automatiquement le format, la taille et la qualité des images en fonction des fonctionnalités du navigateur client.

De plus, obtenez désormais un meilleur score Google Core Web Vital pour LCP (Large Contentful Paint) grâce à l’amélioration de l’imagerie dynamique, qui s’accompagne désormais de la prise en charge d’AVIF et de WebP.

>[!IMPORTANT]
>
>L’imagerie intelligente nécessite l’utilisation du réseau de diffusion de contenu prêt à l’emploi fourni avec Adobe Experience Manager - Dynamic Media. Aucun autre réseau CDN personnalisé n’est pris en charge avec cette fonctionnalité.

>[!TIP]
>
>Testez et découvrez les avantages des modificateurs d’image Dynamic Media et de l’imagerie dynamique à l’aide de Dynamic Media. [_Instantané_](https://snapshot.scene7.com/).
>
> L’instantané est un outil de démonstration visuel, conçu pour illustrer la puissance de Dynamic Media pour une diffusion d’images optimisée et dynamique. Testez des images de test ou des URL Dynamic Media afin d’observer visuellement la sortie de divers modificateurs d’image Dynamic Media et d’optimiser l’imagerie dynamique pour les éléments suivants :
>* Taille de fichier (avec diffusion WebP et AVIF)
>* Bande passante réseau
>* RGPD (rapport des pixels de l’appareil)
>
>Pour savoir à quel point il est facile d’utiliser Snapshot, lisez la [Vidéo de formation instantanée](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html?lang=en) (3 minutes et 17 secondes).

L’imagerie dynamique tire parti de sa parfaite intégration dans le meilleur service premium CDN (réseau de diffusion de contenu) de sa catégorie proposé par Adobe afin d’offrir un gain de performance accru. Ce service trouve l’itinéraire Internet optimal entre les serveurs, les réseaux et les points de connexion. Au lieu d’utiliser l’itinéraire par défaut sur Internet, le service établit celui possédant la latence et le taux de perte de paquets les plus faibles.

Les exemples de ressources d’image suivants illustrent l’optimisation supplémentaire qu’apporte l’imagerie dynamique :

| Image(URL) | Miniature | Taille (JPEG) | Taille (WebP) avec l’imagerie dynamique | Taille (AVIF) avec l’imagerie dynamique | % de réduction avec WebP | % de réduction avec AVIF |
|---|---|---|---|---|---|---|
| [Image 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture1](/help/assets/assets-dm/picture1.png) | 145 Ko | 106 Ko | 90,2 Ko | 26,89 % | 37,79 % |
| [Image 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture2](/help/assets/assets-dm/picture2.png) | 412 Ko | 346 Ko | 113 Ko | 16,01 % | 72,57 % |
| [Image 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture3](/help/assets/assets-dm/picture3.png) | 221 Ko | 189 Ko | 87,1 Ko | 14,47 % | 60,58 % |
| [Image 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture4](/help/assets/assets-dm/picture4.png) | 594 Ko | 545 Ko | 286 Ko | 8,25 % | 51,85 % |

Comme ci-dessus, Adobe a également exécuté un test avec un ensemble d’échantillons plus grand. Le format AVIF a permis une réduction supplémentaire de 20 % de la taille par rapport au WebP, qui lui-même a permis une réduction de 27 % par rapport au JPEG. Tout cela avec la même qualité visuelle. Au total, l’AVIF offre une réduction de taille moyenne de 41 % par rapport au JPEG.

Comparez WebP et AVIF à PNG, vous pouvez constater une réduction de la taille de 84 % avec WebP et de 87 % avec AVIF. Et, puisque les formats WebP et AVIF prennent en charge la transparence et plusieurs animations d’images, ils remplacent efficacement les fichiers PNG et de GIF transparents.

Consultez également la section [Optimisation des images avec des formats d’image de nouvelle génération (WebP et AVIF)](https://blog.developer.adobe.com/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4).

<!-- HIDDEN ON MAY 19, 2022 BASED ON CQDOC-19280 On the mobile web, the challenges are compounded by two factors:

* Large variety of devices with different form factors and high-resolution displays.
* Constrained network bandwidth.

In terms of images, the goal is to serve the best quality images as efficiently as possible. -->

**Avantages de l’imagerie dynamique**

L’imagerie dynamique offre de meilleures performances de diffusion d’images en optimisant automatiquement la taille du fichier image en fonction du navigateur client utilisé, de l’affichage de l’appareil et des conditions réseau. Les images sont les éléments qui demandent le plus de temps lors du chargement d’une page. Aussi, toute amélioration des performances peut-elle avoir une incidence considérable sur les indicateurs IPC, tels que des taux de conversion plus élevés, une augmentation du temps passé sur le site et un taux de rebond moindre.

Les principaux avantages de la dernière technologie d’imagerie dynamique sont les suivants :

* Le format AVIF de nouvelle génération est désormais pris en charge.
* La conversion avec perte des PNG en WebP et AVIF est désormais possible. Le format PNG étant sans perte, les WebP et AVIF étaient auparavant livrés sans perte.
* [Conversion au format du navigateur](#bfc)
* [Rapport pixel de l’appareil](#dpr)
* [Bande passante réseau](#bandwidth)

### À propos de la conversion au format du navigateur {#bfc}

L’activation de la conversion au format du navigateur en ajoutant `bfc=on` dans l’URL de l’image convertit automatiquement les JPEG et PNG en AVIF avec perte, WebP avec perte, JPEGXR avec perte, JPEG2000 avec perte, en fonction des différents navigateurs. Pour les navigateurs qui ne prennent pas en charge ces formats, l’imagerie dynamique continue de délivrer le JPEG ou le fichier PNG. Avec le format , la qualité du nouveau format est recalculée par l’imagerie dynamique.

L’imagerie dynamique peut également être désactivée en ajoutant `bfc=off` à l’URL de l’image.

Consultez également la section [bfc](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-bfc.html?lang=fr) dans l’API de diffusion et de rendu d’images Dynamic Media.

### A propos de l’optimisation du rapport des pixels de périphérique {#dpr}

Le rapport pixel d’appareil (DPR), également appelé rapport pixel CSS, est la relation entre les pixels physiques et les pixels logiques d’un appareil. Surtout avec l’avènement des écrans Retina, la résolution en pixels des appareils mobiles modernes augmente à un rythme rapide.

L’activation de l’optimisation du rapport de pixels de l’appareil rend l’image à la résolution native de l’écran, ce qui la rend nette.

Actuellement, la densité en pixels de l’affichage provient des valeurs d’en-tête du CDN Akamai.

| Valeurs autorisées dans l’URL d’une image | Description |
|---|---|
| `dpr=off` | Désactivez l’optimisation du DPR au niveau de l’URL d’une image individuelle. |
| `dpr=on,dprValue` | Remplacez la valeur DPR détectée par l’imagerie intelligente par une valeur personnalisée (telle que détectée par une logique côté client ou par d’autres moyens). La valeur autorisée pour `dprValue` est n’importe quel nombre supérieur à 0. |

>[!NOTE]
>
>* Vous pouvez utiliser `dpr=on,dprValue` même si le paramètre DPR au niveau de la société est désactivé.
>* Avec l’optimisation du DPR, lorsque l’image créée est supérieure au paramètre MaxPix Dynamic Media, la largeur MaxPix est toujours reconnue en conservant les proportions de l’image. -->


| Taille de l’image demandée | Valeur de Ratio pixel de l’appareil (dpr) | Taille de l’image diffusée |
|---|---|---|
| 816 x 500 | 1 | 816 x 500 |
| 816 x 500 | 2 | 1632 x 1000 |

Consultez également la section [Lorsque vous utilisez des images](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-images) et [Lorsque vous utilisez le recadrage intelligent](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

### À propos de l’optimisation de la bande passante du réseau {#bandwidth}

L’activation de la bande passante réseau ajuste automatiquement la qualité de l’image diffusée en fonction de la bande passante réseau réelle. Lorsque la bande passante réseau est insuffisante, l’optimisation du DPR est automatiquement désactivée, même si elle est déjà activée.

Si vous le souhaitez, votre entreprise peut se désabonner de l’optimisation de la bande passante du réseau au niveau de l’image individuelle en ajoutant `network=off` à l’URL de l’image.

| Valeur autorisée dans l’URL d’une image | Description |
|---|---|
| `network=off` | Désactive l’optimisation du réseau au niveau de l’URL d’une image individuelle. |

Les valeurs DPR et de bande passante réseau sont basées sur les valeurs côté client détectées du réseau de diffusion de contenu groupé. Ces valeurs sont parfois inexactes. Par exemple, l’iPhone5 avec un DPR=2 et l’iPhone12 avec un `dpr=3` affichent tous deux un `dpr=2`. Néanmoins, pour les appareils haute résolution, envoyer un `dpr=2` est préférable à envoyer un `dpr=1`. La meilleure façon de surmonter cette inexactitude consiste toutefois à utiliser le RPD côté client, pour obtenir des valeurs parfaitement précises. Cette méthode fonctionne pour n’importe quel appareil, qu’il s’agisse d’Apple ou de tout autre appareil existant. Consultez la section [Utilisation de l’imagerie dynamique avec Rapport pixel d’appareil côté client](/help/assets/dynamic-media/client-side-dpr.md).

**Autres principaux avantages de l’imagerie dynamique**

* Amélioration du classement d’optimisation du référencement Google pour les pages web qui utilisent la technologie d’imagerie dynamique la plus récente.
* Diffusion immédiate de contenus optimisés (au moment de l’exécution).
* Mise en œuvre de la technologie Adobe Sensei pour effectuer la conversion en fonction de la qualité (`qlt`) spécifiée dans la demande d’image.
* Indépendance vis-à-vis du temps de vie (TTL). Auparavant, un TTL minimal de 12 heures était obligatoire pour le fonctionnement de l’imagerie dynamique.
* Auparavant également, les images d’origine et dérivées étaient mises en cache et un processus en deux étapes était nécessaire pour invalider le cache. Avec la technologie d’imagerie dynamique la plus récente, seules les images dérivées sont mises en cache, ce qui rend possible un processus d’invalidation du cache en une seule étape.
* Les clients qui utilisent des en-têtes personnalisés dans leur jeu de règles bénéficient de la version de l’imagerie dynamique la plus récente, car ces en-têtes ne sont pas bloqués, contrairement à la version précédente. Par exemple, « Timing Allow Origin », « X-Robot » comme suggéré dans [Ajout d’une valeur d’en-tête personnalisée aux réponses d’image Dynamic Media Classic](https://helpx.adobe.com/fr/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html).

## Fonctionnement de l’imagerie dynamique

Lorsqu’un client demande une image, l’imagerie dynamique vérifie les caractéristiques utilisateur et les convertit au format approprié en fonction du navigateur utilisé. Ces conversions de format s’effectuent de manière à garantir une représentation fidèle. L’imagerie dynamique convertit automatiquement les images dans différents formats en fonction des capacités du navigateur de la manière suivante.

* Conversion automatique au format AVIF si le navigateur prend en charge le format
* Conversion automatique au format WebP si la conversion AVIF n’a pas été bénéfique ou si le navigateur ne prend pas en charge l’AVIF
* Conversion automatique vers le JPEG2000 si Safari ne prend pas en charge le WebP
* Conversion automatique vers le JPEGXR pour IE 9+ ou si Edge ne prend pas en charge WebP\
   | Format d’image | Navigateurs pris en charge |
|---|---|
| AVIF | [https://caniuse.com/avif](https://caniuse.com/avif) |
| WebP | [https://caniuse.com/webp](https://caniuse.com/webp) |
| JPEG 2000 | [https://caniuse.com/jpeg2000](https://caniuse.com/jpeg2000) |
| JPEGXR | [https://caniuse.com/jpegxr](https://caniuse.com/jpegxr) |
* Pour les navigateurs qui ne prennent pas en charge ces formats, le format d’image demandé initialement est diffusé.

Si la taille de l’image d’origine est inférieure à celle produite par l’imagerie dynamique, l’image d’origine est diffusée.

## Prise en charge du format d’image dans l’imagerie dynamique

Les formats suivants sont pris en charge dans le cadre de l’imagerie dynamique :

* JPEG
* PNG

Pour le format de fichier image JPEG, la qualité du nouveau format est recalculée par l’imagerie dynamique.

Pour les formats de fichiers image qui prennent en charge la transparence, tels que le PNG, vous pouvez configurer l’imagerie dynamique pour qu’elle diffuse des fichiers AVIF et WebP avec perte. Pour la conversion en formats avec perte, l’imagerie dynamique utilise la qualité mentionnée dans l’URL de l’image, ou la qualité configurée dans le compte d’entreprise Dynamic Media.

## Prise en charge des commandes du service d’images dans l’imagerie dynamique

Commandes de diffusion d’images `fmt` et `qlt` ne sont pas prises en charge ; toutes les commandes restantes sont prises en charge.

## Questions fréquentes sur l’imagerie dynamique

+++**L’imagerie dynamique entraîne-t-elle des coûts de licence ?**

Non. L’imagerie dynamique est incluse dans votre licence existante. Cette règle est vraie pour Dynamic Media Classic ou pour Experience Manager Dynamic Media (On-premise, AMS et Experience Manager as a Cloud Service).

>[!IMPORTANT]
>
>L’imagerie dynamique n’est pas disponible pour les utilisateurs Dynamic Media – Hybrid.

+++

+++**Est-il possible de désactiver l’imagerie dynamique quelle que soit la raison ?**

Oui. Vous pouvez désactiver l’imagerie dynamique en ajoutant l’un des modificateurs suivants :

* `bfc=off` pour désactiver la conversion au format du navigateur. Consultez également la section [Conversion au format du navigateur](#bfc).
* `dpr=off` pour désactiver le rapport pixel de l’appareil. Consultez également la section [Rapport pixel de l’appareil](#dpr).
* `network=off` pour désactiver la bande passante réseau. Consultez également la section [Bande passante réseau](#network).

+++

+++**Est-il possible d’&quot;ajuster&quot; l’imagerie dynamique ?**

Oui. L’imagerie dynamique offre trois options que vous pouvez activer ou désactiver.

* [Conversion au format du navigateur](#bfc)
* [Rapport pixel de l’appareil](#dpr)
* [Bande passante réseau](#network)

+++

+++**L’imagerie dynamique fonctionne-t-elle avec mes paramètres d’image prédéfinis existants ?**

Oui. L’imagerie dynamique fonctionne avec vos paramètres prédéfinis d’image existants et conserve tous vos paramètres d’image. Ce qui change, c’est le format de l’image, ou le paramètre de qualité, ou les deux. Pour la conversion de format, l’imagerie dynamique conserve la qualité vidéo totale, telle qu’elle est définie par vos paramètres prédéfinis d’image, mais avec une plus petite taille de fichier.

Supposons, par exemple, qu’un paramètre prédéfini d’image soit configuré comme suit : format JPEG, taille de 500 x 500, qualité=85 et accentuation=0,1,1,5. Lorsque l’imagerie dynamique détecte qu’un utilisateur se trouve dans un navigateur Chrome, l’image est convertie au format WebP, avec une taille de 500 x 500. De plus, le masque flou = 0,1,1,5 est d’une qualité WebP qui correspond à une qualité de JPEG de 85 aussi proche que possible. L’empreinte de cette conversion WebP est comparée au JPEG, et la plus petite des deux est renvoyée.

+++

+++**Dois-je modifier des URL, des paramètres d’image prédéfinis ou déployer du nouveau code sur mon site ?**

Non. L’imagerie dynamique fonctionne parfaitement avec vos paramètres d’image prédéfinis et URL d’image existants. En outre, l’imagerie dynamique n’exige pas que vous ajoutiez du code sur votre site web pour détecter le navigateur d’un utilisateur. Tout cela est géré automatiquement.

<!-- Smart Imaging works seamlessly with your existing image URLs and image presets if you configure Smart Imaging on your existing custom domain. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. It is all handled automatically.

In case you must configure a new custom domain to use Smart Imaging, the URLs must be updated to reflect this custom domain.

To understand pre-requisites for Smart Imaging, see [Am I eligible to use Smart Imaging?](#am-i-eligible-to-use-smart-imaging) -->

<!-- OLD As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. -->

+++

+++**L’imagerie dynamique est-elle compatible avec le protocole HTTPS ? Et qu’en est-il du protocole HTTP/2 ?**

Oui, aux deux questions. L’imagerie dynamique fonctionne avec les images diffusées sur HTTP ou HTTPS. Elle fonctionne également sur HTTP/2.

+++

+++**Puis-je utiliser l’imagerie intelligente ?**

Ça dépend. Pour pouvoir utiliser l’imagerie dynamique, le compte Dynamic Media Classic ou Dynamic Media sur Experience Manager de votre entreprise doit répondre aux conditions suivantes :

* Utiliser le réseau de diffusion de contenu (CDN) fourni par Adobe dans le cadre de votre licence.
* Utiliser un domaine dédié (par exemple, `images.company.com` ou `mycompany.scene7.com`), plutôt qu’un domaine générique (par exemple, `s7d1.scene7.com`, `s7d2.scene7.com` ou `s7d13.scene7.com`).

Pour trouver vos domaines, ouvrez l’[application de bureau Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=fr#getting-started), puis connectez-vous à un ou plusieurs comptes de votre entreprise.

Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’application]** > **[!UICONTROL Paramètres généraux]**. Recherchez le champ intitulé **[!UICONTROL Nom du serveur publié]**. Si vous utilisez actuellement un domaine générique, vous pouvez demander à passer à votre propre domaine personnalisé. Faites cette demande de transition lorsque vous soumettez un dossier de support.

Votre premier domaine personnalisé n’entraîne aucun coût supplémentaire avec une licence Dynamic Media.

+++

+++**Puis-je activer l’imagerie dynamique pour mon compte ?**

Nombre Vous devez envoyer la demande d’utilisation d’imagerie dynamique ; celle-ci n’est pas activée automatiquement.

Créez un dossier de support, comme décrit ci-dessous. Dans votre demande, veillez à mentionner la ou les fonctionnalités d’imagerie dynamique suivantes que vous souhaitez activer sur votre compte :

* WebP
* AVIF
* Optimisation du Ratio pixel de l’appareil et de la bande passante réseau
* PNG vers AVIF avec perte ou WebP avec perte

Si l’imagerie dynamique est déjà activée en WebP, mais que vous souhaitez d’autres nouvelles fonctionnalités comme indiqué ci-dessus, vous devez créer un dossier de support.

**Pour créer un dossier de support permettant d’activer l’imagerie dynamique sur votre compte :**

1. [Utilisez l’Admin Console pour commencer la création d’un nouveau dossier de support.](https://helpx.adobe.com/fr/enterprise/using/support-for-experience-cloud.html).
1. Indiquez les informations suivantes dans votre dossier de support :

   * nom, adresse électronique et numéro de téléphone du contact principal.

   * Répertoriez les fonctionnalités d’imagerie dynamique suivantes que vous souhaitez activer sur votre compte :
      * WebP
      * AVIF
      * Optimisation du Ratio pixel de l’appareil et de la bande passante réseau
      * PNG vers AVIF avec perte ou WebP avec perte
   * Tous les domaines à activer pour l’imagerie intelligente (c’est-à-dire `images.company.com` ou `mycompany.scene7.com`).

      Pour trouver vos domaines, ouvrez l’[application de bureau Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=fr#getting-started), puis connectez-vous à un ou plusieurs comptes de votre entreprise.

      Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’application]** > **[!UICONTROL Paramètres généraux]**.

      Recherchez le champ intitulé **[!UICONTROL Nom du serveur publié]**.

   * Vérifiez que vous utilisez le CDN via Adobe et non le CDN géré avec une relation directe.

   * Vérifiez que vous utilisez un domaine dédié, tel que `images.company.com` ou `mycompany.scene7.com`, et non un domaine générique, tel que `s7d1.scene7.com`, `s7d2.scene7.com` ou `s7d13.scene7.com`.

      Pour trouver vos domaines, ouvrez l’[application de bureau Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=fr#getting-started), puis connectez-vous à un ou plusieurs comptes de votre entreprise.

      Accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’application]** > **[!UICONTROL Paramètres généraux]**.

      Recherchez le champ intitulé **[!UICONTROL Nom du serveur publié]**. Si vous utilisez actuellement un domaine Dynamic Media Classic générique, vous pouvez demander une migration vers votre domaine personnalisé dans le cadre de cette transition.

   * Indiquez si vous souhaitez qu’il fonctionne en HTTP/2.


1. Le service clientèle Adobe vous inscrira sur la liste d’attente des clients pour l’imagerie dynamique en se basant sur l’ordre dans lequel les demandes ont été envoyées.
1. Dès qu’Adobe est prêt à traiter votre demande, vous serez contacté par le service clientèle afin de programmer une date cible.
1. **Facultatif** : Vous avez la possibilité de tester l’imagerie intelligente dans le cadre de l’évaluation avant qu’Adobe ne mette la nouvelle fonctionnalité en production.
1. Une fois la procédure achevée, vous en serez informé par l’équipe du service clientèle.
1. Pour tirer pleinement parti des améliorations de performances de l’imagerie dynamique, Adobe recommande de définir le délai d’expiration (TTL) sur 24 heures ou plus. Ce paramètre définit la période pendant laquelle les ressources sont mises en cache par le réseau de diffusion de contenu. Pour modifier ce paramètre :

   1. Si vous utilisez Dynamic Media Classic, accédez à **[!UICONTROL Configuration]** > **[!UICONTROL Configuration de l’application]** > **[!UICONTROL Configuration de la publication]** > **[!UICONTROL Serveur d’images]**. Définissez la valeur **[!UICONTROL Délai d’expiration par défaut du cache de client]** sur 24 ou plus.
   1. Si vous utilisez Dynamic Media, [procédez comme suit](config-dm.md). Définissez la valeur **[!UICONTROL Expiration]** sur 24 heures ou plus.

+++

+++**Quand mon compte est-il activé avec l’imagerie dynamique ?**

Les demandes sont traitées dans l’ordre de réception par l’équipe du service clientèle, suivant la liste d’attente.

>[!NOTE]
>
>Le délai d’exécution peut être relativement long, car l’activation de l’imagerie dynamique implique qu’Adobe efface le cache. Seul un petit nombre de transitions peut donc être traité simultanément.

+++

+++**Existe-t-il des risques liés à l’utilisation de l’imagerie dynamique ?**

La page web d’un client ne présente aucun risque. Cependant, la transition à l’imagerie dynamique efface votre cache CDN. Cette opération implique de passer à une nouvelle configuration de Dynamic Media Classic ou Dynamic Media sur Experience Manager.

Au cours de la transition initiale, les images non mises en cache accèdent directement aux serveurs d’origine d’Adobe jusqu’à ce que le cache soit reconstitué. C’est pour cette raison qu’Adobe prévoit de ne gérer que quelques transitions à la fois afin d’offrir des performances acceptables lors de l’extraction des demandes du site d’origine. Pour la plupart des clients, le cache est entièrement reconstitué sur le réseau de diffusion de contenu dans un délai d’environ un à deux jours.

+++

+++**Puis-je vérifier si l’imagerie dynamique fonctionne ?**

Oui. Vous pouvez effectuer les opérations suivantes :

1. Une fois que l’imagerie intelligente est activée sur votre compte, chargez une URL d’image Dynamic Media Classic ou Adobe Experience Manager – Dynamic Media sur le navigateur.
1. Ouvrez le volet de Chrome pour les développeurs en accédant à **[!UICONTROL Afficher]** > **[!UICONTROL Développeur]** > **[!UICONTROL Outils de développement]** dans le navigateur. Vous pouvez également sélectionner l’outil de développement de navigateur de votre choix.

1. Assurez-vous que le cache est désactivé lorsque les outils de développement sont ouverts.

   * Sous Windows®, accédez aux paramètres dans le volet de l’outil de développement, puis cochez la case **[!UICONTROL Désactiver le cache (lorsque les outils de développement sont ouverts)]**.
   * Sous macOS, sélectionnez **[!UICONTROL désactiver le cache]** dans l’onglet **[!UICONTROL Réseau]** du volet de développement.

1. Vérifiez que le type de contenu est converti au format approprié. L’écran ci-dessous illustre la conversion dynamique d’une image PNG au format WebP sur Chrome. Si l’AVIF est activé pour votre domaine, vous pouvez également vous attendre à voir AVIF dans le type de contenu.
1. Répétez ce test sur différents navigateurs et conditions utilisateur.

>[!NOTE]
>
>Toutes les images ne sont pas converties. L’imagerie dynamique détermine si la conversion peut améliorer les performances. Parfois, si aucune amélioration des performances n’est attendue, ou que le format n’est pas JPEG ou PNG, l’image n’est pas convertie.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

+++

+++**Existe-t-il un moyen de connaître les avantages de l’imagerie dynamique ?**

Oui. L’en-tête d’imagerie dynamique détermine les avantages de l’imagerie dynamique. Lorsque l’imagerie dynamique est activée, après avoir demandé une image, vous pouvez voir `-X-Adobe-Smart-Imaging` sous le titre **[!UICONTROL En-têtes de réponse]**, comme illustré dans l’exemple en surbrillance suivant :

![En-tête d’imagerie dynamique](/help/assets/dynamic-media/assets/smartimagingheader.png)

Cet en-tête vous indique ce qui suit :

* L’imagerie dynamique fonctionne pour l’entreprise.
* Une valeur positive signifie que la conversion a réussi. Dans ce cas, une nouvelle image WebP est renvoyée.
* Une valeur négative signifie que la conversion a échoué. Dans ce cas, l’image demandée d’origine est renvoyée (en JPEG par défaut, si le format n’est pas spécifié).
* Une valeur positive indique la différence en octets entre l’image demandée et la nouvelle image. Dans l’exemple ci-dessus, les octets enregistrés sont `75048`, soit environ 75 Ko pour une image.
* Une valeur négative signifie que l’image demandée est plus petite que la nouvelle image. La différence de taille négative s’affiche, mais l’image diffusée reste l’image d’origine demandée.

>[!NOTE]
>
>**X-Adobe-Smart-Imaging = -1 avec diffusion en WebP**
>
>Si la valeur de `X-Adobe-Smart-Imaging` est -1 et que le WebP est toujours en cours de diffusion, cela signifie que l’imagerie dynamique fonctionne, mais que les gains de taille n’ont pas été calculés en raison de l’ancien cache. Vous pouvez utiliser `cache=update` (une seule fois) dans l’URL de l’image pour résoudre ce problème.
>Exemple d’utilisation du modificateur :
>`https://smartimaging.scene7.com/is/image/SmartImaging/sample1?cache=update`
>Pour invalider l’intégralité du cache, vous devez créer un dossier de support.

+++

+++**Puis-je désactiver l’optimisation AVIF dans l’imagerie dynamique ?**

Oui. Si vous souhaitez revenir au service WebP par défaut, créez un dossier de support de la même façon. Vous pouvez comme d’habitude désactiver l’imagerie dynamique en ajoutant le paramètre `bfc=off` à l’URL de l’image. Cependant, vous ne pouvez pas sélectionner le format WebP ou AVIF dans le modificateur d’URL pour l’imagerie dynamique. Cette fonctionnalité est conservée au niveau du compte de votre société.

+++

+++**Pourquoi ma requête échoue-t-elle lorsque je dispose d’une URL avec fmt=tif sur le navigateur web Chrome ?**

Cette erreur ne se produit pas si l’imagerie dynamique n’est pas activée sur votre compte. L’imagerie dynamique fonctionne uniquement avec les formats JPEG ou PNG.

Pour éviter cette erreur, vous pouvez effectuer l’une des opérations suivantes :

* Spécifiez JPEG ou PNG.
* N’utilisez pas le modificateur `fmt`.
* Utilisez un format de navigateur préféré tel que défini par l’imagerie dynamique. Par exemple, vous pouvez utiliser le WebP pour le navigateur web Chrome.

+++

+++**Puis-je télécharger une image de TIFF à partir de l’URL d’une image ?**

Oui. Ajoutez `fmt=tif` et `bfc=off` au chemin d’URL de l’image.

+++

+++**L’imagerie dynamique gère-t-elle le format d’image et les paramètres de qualité d’image ?**

Oui. L’imagerie dynamique utilise le format et la qualité. Le reste des paramètres restent inchangés, tels que prévus pour l’URL de l’image.

+++

+++**Puis-je définir un paramètre de qualité minimal et maximal ?**

Nombre Il n’existe actuellement aucune configuration de ce type.

+++

+++**L’imagerie dynamique ajuste-t-elle le paramètre de sortie de qualité en pourcentage ?**

Oui. L’imagerie dynamique ajuste automatiquement le pourcentage de qualité. Ce pourcentage de qualité est déterminé à l’aide d’un algorithme de machine learning développé par Adobe. Ce pourcentage n’est pas spécifique à la plage.

+++

+++**Est-ce que seuls JPEG et PNG sont remplacés par l’imagerie dynamique ?**

Oui. Cette fonctionnalité fonctionne uniquement pour les JPEG et PNG.

+++

+++**Pourquoi le JPEG est-il parfois renvoyé à Chrome au lieu de WebP ?**

L’imagerie dynamique détermine si la conversion apporte ou non un bénéfice. Elle renvoie la nouvelle image uniquement si la conversion est bénéfique.

+++

+++**Pourquoi le rapport des pixels de l’appareil (dpr) ne fonctionne-t-il pas avec les images composites ?**

Si une image composite implique un trop grand nombre de calques, la fonctionnalité dpr peut être affectée lors de l’utilisation d’un modificateur de position. Ce problème est connu et sera corrigé dans les prochaines versions de l’imagerie dynamique. Si d’autres fonctionnalités d’imagerie dynamique ne fonctionnent pas comme prévu, vous pouvez créer un dossier de support pour signaler le problème.

+++

+++**Pourquoi l’imagerie dynamique PNG est-elle convertie en WebP/AVIF sans perte ?**

Comme le format PNG est un format sans perte, les fichiers WebP et AVIF étaient auparavant livrés sans perte, avec une taille plus grande que prévu. L’imagerie dynamique prend désormais en charge la conversion avec perte. Vous pouvez utiliser le modificateur `cache=update` (une seule fois) dans une demande d’image pour résoudre ce problème. Exemple d’utilisation de ce modificateur :

`https://smartimaging.scene7.com/is/image/SmartImaging/sample1?cache=update`

Pour invalider l’intégralité du cache, vous devez créer un dossier de support à cet effet.

+++

+++**Puis-je continuer à utiliser PNG pour une conversion sans perte dans l’imagerie dynamique ?**

Oui. L’imagerie dynamique prend désormais en charge la conversion avec perte en fonction du niveau de qualité. Pour continuer à utiliser une conversion sans perte, vous pouvez utiliser la qualité 100 définie soit par la configuration de votre entreprise, soit par le biais de l’URL de l’image en ajoutant `qlt=100` dans le chemin.

+++



























<!-- ## If Smart Imaging manages the quality settings, are there minimums and maximums I can set? For example, is it possible to set "no lower than 60" and "no greater than 80 quality"? {#minimum-maximum}

There is no such provisioning ability in the current Smart Imaging. -->

<!-- ## Sometimes a JPEG image is returned to Chrome instead of a WebP image. Why does that change happen? {#jpeg-webp}

Smart Imaging determines if the conversion is beneficial or not. It returns the new image only if the conversion results in a smaller file size with comparable quality.

How does Smart Imaging DPR optimization work with Adobe Experience Manager Sites components and Dynamic Media viewers?

* Experience Manager Sites Core Components are configured by default for DPR optimization. To avoid oversized images owing to server-side Smart Imaging DPR optimization, `dpr=off` is always added to Experience Manager Sites Core Components Dynamic Media images.
* Given Dynamic Media Foundation Component is configured by default for DPR optimization, to avoid oversized images owing to server-side Smart Imaging DPR optimization, `dpr=off` is always added to Dynamic Media Foundation Component images. Even if customer deselects DPR optimization in DM Foundation Component, server-side Smart Imaging DPR does not kick in. In summary, in the DM Foundation Component, DPR optimization comes into effect based on DM Foundation Component level setting only.
* Any viewer side DPR optimization works in tandem with server-side Smart Imaging DPR optimization, and does not result in over-sized images. In other words, wherever DPR is handled by the viewer, such as the main view only in a zoom-enabled viewer, the server-side Smart Imaging DPR values are not triggered. Likewise, wherever viewer elements, such as swatches and thumbnails, do not have DPR handling, the server-side Smart Imaging DPR value is triggered.

See also [When working with images](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-images) and [When working with Smart Crop](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

>[!MORELIKETHIS]
>
>* [Image optimization with next generation image formats WebP and AVIF.](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4) -->
>