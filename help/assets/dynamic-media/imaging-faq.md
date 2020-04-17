---
title: Imagerie dynamique
description: L’imagerie dynamique utilise les caractéristiques de visualisation uniques de chaque utilisateur pour diffuser automatiquement les images optimisées pour leur expérience, ce qui se traduit par des performances accrues et une meilleure interaction.
translation-type: ht
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Imagerie dynamique {#smart-imaging}

## Qu’est-ce que l’imagerie dynamique ? {#what-is-smart-imaging}

L’imagerie dynamique utilise les caractéristiques de visualisation uniques de chaque utilisateur pour diffuser automatiquement les images optimisées pour leur expérience, ce qui se traduit par des performances accrues et une meilleure interaction. L’imagerie dynamique fonctionne avec vos paramètres d’image prédéfinis et utilise des informations à la dernière milliseconde de la diffusion pour réduire davantage encore la taille du fichier d’image en fonction de la vitesse de connexion du réseau et du navigateur.

L’imagerie dynamique tire parti d’une parfaite intégration dans un service CDN haut de gamme pour offrir un gain de performance accru. Ce service recherche la route Internet optimale entre les serveurs, réseaux et points d’appairage ; c’est-à-dire la route ayant une latence et/ou un taux de perte de paquets plus faibles que la route par défaut sur Internet.

## Quels sont les principaux avantages de l’imagerie dynamique ? {#what-are-the-key-benefits-of-smart-imaging}

L’imagerie dynamique offre de meilleures performances sur le plan de la diffusion d’images en optimisant automatiquement la taille du fichier d’image en fonction des caractéristiques de l’utilisateur. Les images sont les éléments qui demandent le plus de temps lors du chargement d’une page. Aussi, une amélioration des performances peut-elle avoir des avantages considérables sur les indicateurs IPC, tels qu’un taux de conversion plus élevé, une augmentation du temps passé sur le site, un taux de rebond moins élevé, etc. Adobe a comparé les performances de la diffusion d’images par défaut et de l’imagerie dynamique sur différents formats de fichiers, navigateurs et paramètres de qualité (QLT). De manière générale, vous pouvez vous attendre à une amélioration des performances de l’ordre de 22 à 47 % en fonction de vos paramètres d’image prédéfinis et des caractéristiques utilisateur spécifiques.

![image2017-11-14_133226](/help/assets/dynamic-media/assets/image2017-11-14_133226.png)

## L’imagerie dynamique entraîne-t-elle des frais de licence ? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Non. L’imagerie dynamique est incluse dans votre licence existante Dynamic Media Classic (Scene7) ou Dynamic Media. L’utilisation de cette nouvelle fonctionnalité n’engendre pas de frais supplémentaires.

## Comment fonctionne l’imagerie dynamique ? {#how-does-smart-imaging-work}

La première fois qu’un client demande une image, nous vérifions les caractéristiques utilisateur et nous la convertissons au format approprié en fonction du navigateur. Dans le même temps, nous créons toutes les conversions de format, qui sont ensuite mises en cache sur le réseau CDN. Par la suite, lorsque des clients qui utilisent d’autres navigateurs demandent cette image, le format approprié est automatiquement diffusé à partir du cache du réseau CDN. Ces conversions de format s’effectuent sans perte, ce qui permet de garantir une représentation fidèle. L’imagerie dynamique convertit automatiquement les images dans différents formats en fonction des capacités du navigateur :

* Conversion automatique au format WebP sans perte pour les navigateurs qui prennent en charge le format WebP, comme Chrome, Android et Opera.
* Conversion automatique au format JPEGXR sans perte pour les navigateurs qui prennent en charge le format JPEGXR, comme Internet Explorer 9 et versions ultérieures.
* Conversion automatique au format JPEG2000 sans perte pour les navigateurs prenant en charge le format JPEG2000, comme Safari.
* Pour les navigateurs qui ne prennent pas en charge ces formats, le format d’image demandé initialement est diffusé.

## Quels sont les formats d’image pris en charge ?   {#what-image-formats-are-supported}

Les formats suivants sont pris en charge dans le cadre de l’imagerie dynamique :

* JPEG RVB
* PNG RVB
* TIFF RVB
* JPEG CMJN
* TIFF CMJN

## Comment l’imagerie dynamique fonctionne-t-elle avec les paramètres d’image prédéfinis qui sont déjà utilisés ?   {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

L’imagerie dynamique fonctionne avec vos paramètres d’image prédéfinis existants et conserve pratiquement tous vos paramètres d’image, tels que la taille, la qualité, l’accentuation, etc. Ce qui change, c’est le format d’image ou, dans le cas d’une connexion réseau lente, le paramètre de qualité. Pour la conversion de format, nous conservons la qualité vidéo totale, telle qu’elle est définie par vos paramètres d’image prédéfinis, mais avec une plus petite taille de fichier.

Supposons, par exemple, qu’un paramètre d’image prédéfini soit configuré comme suit : format JPEG, taille de 500 x 500, qualité=85 et masquage flou=0,1,1,5. Lorsque nous détectons que le navigateur Chrome est utilisé, l’image est convertie au format WebP sans perte avec les paramètres suivants : taille de 500 x 500, qualité=85 et masquage flou=0,1,1,5.

## Vais-je devoir modifier des URL ou des paramètres d’image prédéfinis, ou déployer du nouveau code sur mon site pour exploiter l’imagerie dynamique ?   {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Non. L’imagerie dynamique fonctionne parfaitement avec vos paramètres d’image prédéfinis et URL d’image existants. De plus, vous ne devez pas ajouter de code supplémentaire sur votre site web pour détecter les caractéristiques utilisateur différentes (navigateur, bande passante, périphérique, etc.). Tout cela est géré automatiquement par Adobe.

La seule modification qui peut s’avérer nécessaire est la mise à jour du paramètre de **[!UICONTROL délai d’activation (TTL)]**. Ce paramètre définit la période pendant laquelle les ressources sont mises en cache par le réseau CDN. Pour tirer pleinement parti des améliorations de performances de l’imagerie dynamique, Adobe recommande de définir le délai d’expiration sur 24 heures ou plus. Pour modifier ce paramètre :

* Si vous utilisez Dynamic Media Classic, appuyez sur **[!UICONTROL Configuration > Configuration de l’application > Configuration de la publication > Serveur d’images]**. Définissez la valeur **[!UICONTROL Délai d’expiration par défaut du cache de client]** sur 24 ou plus.

* Si vous utilisez Dynamic Media, définissez la valeur **[!UICONTROL Expiration]** sur 24 heures ou plus.

>[!NOTE]
>
>Si vous définissez le paramètre TTL sur une valeur inférieure à 1 heure, l’imagerie dynamique ne fonctionnera pas.

## L’imagerie dynamique est-elle compatible avec le protocole HTTPS ? Et qu’en est-il du protocole HTTP/2 ?   {#does-smart-imaging-working-with-https-how-about-http}

L’imagerie dynamique fonctionne avec les images diffusées sur HTTP ou HTTPS. Elle fonctionne également sur HTTP/2.

## Puis-je utiliser l’imagerie dynamique ? {#am-i-eligible-to-use-smart-imaging}

Pour pouvoir utiliser l’imagerie dynamique, le compte Dynamic Media Classic ou Dynamic Media sur AEM de votre entreprise doit répondre aux conditions suivantes :

* Utiliser le réseau de diffusion de contenu (CDN) fourni par Adobe dans le cadre de votre licence.
* Utiliser un domaine dédié (c’est-à-dire `images.company.com` ou `mycompany.scene7.com`), et non un domaine générique (c’est-à-dire `s7d1.scene7.com`, `s7d2.scene7.com` ou `s7d13.scene7.com`).

   Pour rechercher vos domaines, connectez-vous à votre (vos) compte(s) d’entreprise.

   Appuyez sur **[!UICONTROL Configuration > Configuration de l’application > Paramètres généraux]**. Recherchez le champ intitulé **[!UICONTROL Nom du serveur publié]**. Si vous utilisez actuellement un domaine générique, vous pouvez demander une migration vers votre domaine personnalisé dans le cadre de cette transition.

* Ne pas demander d’images JPEG CMJN. Dans le cadre de son traitement, l’imagerie dynamique convertit les images JPEG CMJN en RVB. Si vous devez obtenir des images JPEG CMJN, vous ne pouvez pas utiliser l’imagerie dynamique.

## Quelle est la marche à suivre pour activer l’imagerie dynamique pour mon compte ? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

Vous devez envoyer la demande d’utilisation de l’imagerie dynamique ; elle n’est pas activée automatiquement.

1. Envoyez une demande de support technique (adresse électronique : s7support@adobe.com).
1. Indiquez les informations suivantes dans votre demande de support :

   1. Nom, adresse électronique et numéro de téléphone du contact principal.
   1. Tous les domaines à activer pour l’imagerie dynamique (c’est-à-dire images.company.com ou mycompany.scene7.com).

      Pour rechercher vos domaines, connectez-vous à votre (vos) compte(s) d’entreprise.

       Cliquez sur **[!UICONTROL Configuration > Configuration de l’application > Paramètres généraux]**.

      Recherchez le champ intitulé **[!UICONTROL Nom du serveur publié]**.
   1. Vérifiez que vous utilisez le CDN via Adobe et non le CDN géré avec une relation directe.
   1. Vérifiez que vous utilisez un domaine dédié, tel que `images.company.com` ou `mycompany.scene7.com`, et non un domaine générique, tel que `s7d1.scene7.com`, `s7d2.scene7.com` ou `s7d13.scene7.com`.

      Pour rechercher vos domaines, connectez-vous à votre (vos) compte(s) d’entreprise.

       Cliquez sur **[!UICONTROL Configuration > Configuration de l’application > Paramètres généraux]**.

      Recherchez le champ intitulé **[!UICONTROL Nom du serveur publié]**. Si vous utilisez actuellement un domaine Dynamic Media Classic générique, vous pouvez demander une migration vers votre domaine personnalisé dans le cadre de cette transition.
   1. Indiquez s’il doit également fonctionner sur HTTP/2.

1. Le support technique vous inscrira sur la liste d’attente des clients de l’imagerie dynamique en se basant sur l’ordre dans lequel les demandes ont été envoyées.
1. Dès qu’Adobe est prêt à traiter votre demande, vous serez contacté par le support technique afin de programmer une date cible.
1. Facultatif : Vous avez la possibilité de tester la fonctionnalité d’imagerie dynamique avant qu’Adobe ne la mette en production.
1. Une fois la procédure achevée, vous en serez informé par l’équipe de support.
1. Pour tirer pleinement parti des améliorations de performances de l’imagerie dynamique, Adobe recommande de définir le délai d’expiration (TTL) sur 24 heures ou plus. Ce paramètre définit la période pendant laquelle les ressources sont mises en cache par le réseau de diffusion de contenu. Pour modifier ce paramètre :

   1. Si vous utilisez Dynamic Media Classic, cliquez sur **[!UICONTROL Configuration > Configuration de l’application > Configuration de la publication > Serveur d’images]**. Définissez la valeur **[!UICONTROL Délai d’expiration par défaut du cache de client]** sur 24 ou plus.
   1. Si vous utilisez Dynamic Media, définissez la valeur **[!UICONTROL Expiration]** sur 24 heures ou plus.

## Dans quel délai puis-je m’attendre à ce que l’imagerie dynamique soit activée pour mon compte ? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

Les demandes sont traitées dans l’ordre dans lequel elles sont reçues par l’équipe du support technique, suivant la liste d’attente.

>[!NOTE]
Le délai d’exécution peut être relativement long, car l’activation de l’imagerie dynamique implique l’effacement du cache. Par conséquent, seul un petit nombre de transitions peuvent être traitées à la fois.

## Quels sont les risques liés au passage à l’imagerie dynamique ?   {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

Le passage à l’imagerie dynamique efface votre cache sur le réseau de diffusion de contenu, dans la mesure où cela suppose une migration vers une nouvelle configuration de Dynamic Media Classic ou Dynamic Media sur AEM.

Au cours de la transition initiale, les images non mises en cache accèdent directement aux serveurs d’origine d’Adobe jusqu’à ce que le cache soit reconstitué. C’est pour cette raison qu’Adobe prévoit de ne gérer que quelques transitions à la fois afin d’offrir des performances acceptables lors de l’extraction des demandes de notre site d’origine. Pour la plupart des utilisateurs, le cache est entièrement reconstitué au niveau du réseau CDN sous 1 à 2 jours.

## Comment puis-je vérifier si l’imagerie dynamique fonctionne comme prévu ? {#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Une fois que l’imagerie dynamique est activée sur votre compte, chargez une URL d’image Dynamic Media Classic (S7)/Dynamic Media sur le navigateur.
1. Ouvrez le volet de Chrome pour les développeurs en cliquant sur **[!UICONTROL Afficher > Développeur > Outils de développement]** dans le navigateur. Vous pouvez également sélectionner l’outil de développement de navigateur de votre choix.

1. Assurez-vous que le cache est désactivé lorsque les outils de développement sont ouverts.

   1. Sous Windows, accédez aux paramètres dans le volet de l’outil de développement, puis cochez la case **[!UICONTROL Désactiver le cache (lorsque les outils de développement sont ouverts)]**.
   1. Sous Mac, sélectionnez **[!UICONTROL désactiver le cache]** dans l’onglet **[!UICONTROL Réseau]** du volet de développement.

1. Sur la requête initiale, l’image ne sera pas optimisée. En règle générale, il faut environ 15 minutes pour renvoyer l’image optimisée si elle ne figure pas dans le cache CDN.
1. Observez que le type de contenu est converti au format approprié. L’écran ci-dessous illustre la conversion dynamique d’une image PNG au format WebP sur Chrome.
1. Répétez ce test sur d’autres navigateurs et avec différentes conditions d’utilisation.

>[!NOTE]
Toutes les images ne sont pas converties. L’imagerie dynamique détermine si la conversion est requise en vue d’améliorer les performances. Dans certains cas, si aucune amélioration des performances n’est attendue, l’image n’est pas convertie.

![image2017-11-14_15398](/help/assets/dynamic-media/assets/image2017-11-14_15398.png)

