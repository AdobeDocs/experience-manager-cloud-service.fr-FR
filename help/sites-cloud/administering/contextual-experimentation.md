---
title: Expérimentation contextuelle dans AEM as a Cloud Service
description: Découvrez comment utiliser le plug-in d’expérimentation pour ajouter des fonctionnalités d’expérimentation à votre site.
feature: Administering
role: Admin
badgeSaas: label="AEM Sites" type="Positive" tooltip="S’applique à AEM Sites)."
exl-id: 420f8d5e-27f9-4081-b174-b2d7752779f7
source-git-commit: eed3a4866e3018b2ff6bc6e5c201523ab271c35f
workflow-type: tm+mt
source-wordcount: '1805'
ht-degree: 0%

---

# Expérimentation contextuelle dans AEM as a Cloud Service {#contextual-experimentation}

>[!NOTE]
>Actuellement, la fonctionnalité d’expérimentation contextuelle n’est disponible que via le programme bêta. Contactez l’assistance Adobe ou votre gestionnaire de compte pour accéder au programme bêta.

L’expérimentation consiste à tester la conception, les fonctionnalités et le code de votre site afin d’améliorer les performances et de rendre votre site plus efficace et rationalisé. Pour ce faire, vous devez modifier le contenu ou la fonctionnalité, comparer les résultats avec une version antérieure et sélectionner les améliorations qui ont des effets mesurables.

Lorsqu’il est bien fait, il s’agit d’un modèle puissant pour améliorer les conversions, l’engagement et l’expérience des visiteurs. En règle générale, il existe quelques problèmes à éviter lorsque vous envisagez d’adopter cette pratique :

* **Trop peu** : la plupart des entreprises n’expérimentent pas suffisamment, et lorsqu’elles le font, elles expérimentent avec trop peu de trafic pour obtenir des résultats significatifs.
* **Trop lent** : de nombreux frameworks d’expérimentation ralentissent le site à tel point que les nouvelles conversions potentielles ne peuvent pas compenser le trafic perdu et les bounces en raison d’un rendu lent.
* **Trop complexe** : si la configuration d’une nouvelle expérience prend trop de temps, le nombre d’expériences exécutées sera inférieur.

Pour les sites s’exécutant sur Adobe Experience Manager, il existe un **plug-in d’expérimentation** prêt à l’emploi qui permet aux développeurs d’ajouter une fonctionnalité d’expérimentation à leurs sites. Trois éléments différencient cette approche des autres frameworks d’expérimentation :

* Il est facile de configurer des tests avec les outils que vos auteurs connaissent déjà et aucune connexion distincte n’est nécessaire.
* Il est profondément intégré au système de diffusion AEM, ne ralentit pas votre site et résiste aux changements de code et de contenu.
* Il permet de tester des modifications de contenu simples et de réaliser des expériences sur la conception, les fonctionnalités et le code.

## Avant de commencer {#before-start}

Le plug-in d’expérimentation est utilisé dans le cadre de [Edge Delivery Services](/help/edge/overview.md) vous aurez donc besoin d’un compte Github, d’un référentiel de contenu tel que SharePoint ou Google Drive, ainsi que de [AEM Sidekick](https://www.aem.live/docs/sidekick). Consultez également les pages [Prise en main - Tutoriel de développement de l’éditeur universel](https://www.aem.live/developer/tutorial) et [Prise en main - Tutoriel de développement](https://www.aem.live/developer/tutorial).

Une fois que vous avez tout configuré, **regardez cette vidéo** intitulée [Expérimentation instantanée](https://business.adobe.com/products/experience-manager/sites/testing-optimization.html) pour une courte démonstration sur le fonctionnement du plug-in d’expérimentation.

## Termes fréquemment utilisés {#frequently-used-terms}

Avant de suivre le reste du guide de configuration de votre première expérience, vous devez connaître certains termes fréquemment utilisés :

* **Contrôle** : l’expérience avant d’exécuter l’expérience. Toutes les expériences tentent de tester et de démontrer une amélioration par rapport à l’expérience de contrôle.
* **Challenger** : une expérience différente de l’expérience de contrôle et « testée » par rapport à celle-ci ou à côté.
* **Variantes** : le contrôle et le challenger sont tous des variantes d’une expérience.
* **Signification statistique** : évaluer si votre concurrent est vraiment meilleur que le témoin. Le calcul de la signification statistique vous permet d’exclure la chance et de vous concentrer sur les résultats qui ont un effet réel.

## Variantes d’expérience et workflow général {#experiment-variants-workflow}

En règle générale, lors de la configuration d’une expérience, vous utiliserez une page préexistante comme page de contrôle. Vous allez ensuite créer une page de challenger qui remplacera la page de contrôle pour certains de vos visiteurs. Dans la page du challenger, vous pouvez tester différents éléments tels que des variantes de contenu, différentes mises en page, call-to-action (CTA), etc. Vous pouvez configurer ces variantes d’expérience en ajoutant des paramètres de métadonnées dans la page de contrôle (voir ci-dessous).

Le [service de télémétrie opérationnelle](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) collecte ensuite des données, par exemple le nombre de visiteurs sur la page de contrôle par rapport à la page de défi. Vous utilisez ensuite ces données pour sélectionner les améliorations nécessaires pour votre site. Tant que vous respectez la langue de conception établie de votre site web et que vous utilisez la fonctionnalité de bloc existante, vous devriez être en mesure de configurer une variante d’expérience et de l’envoyer en production en quelques minutes.

>[!NOTE]
>Gardez à l’esprit que le plug-in n’utilise aucune donnée de l’utilisateur final susceptible de conduire à son identification, et n’en conserve aucune. Aucun accord préalable de l’utilisateur final ni consentement des cookies n’est requis lors de l’utilisation de la configuration par défaut qui utilise le [service de télémétrie opérationnelle dans AEM as a Cloud Service](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) .

### Identifiant de l’expérience {#experiment-identifier}

Avant de commencer, chaque expérience doit avoir son propre identifiant à des fins de suivi et d’analyse. Un bon point de départ consiste à trouver un identifiant correct et unique pour votre expérience, qui sera l’« ID d’expérience ». Les expériences sont souvent numérotées linéairement ou corrélées à leur ID de problème dans un système de suivi de problèmes ou de gestion. Les identifiants d’expérience utilisent souvent un préfixe pour le projet, par exemple : `OPT-0134`, `EXP0004` ou `CCX0076`.

### Créer votre page Challenger {#create-challenger-page}

Par convention, il est recommandé de créer un dossier avec un ID d’expérience en minuscules dans votre `/experiments/ folder` (par exemple /experiments/ccx0076/). Toutes les pages pour les variantes de challenger se trouvent dans ce dossier. Créez ce dossier dans votre référentiel local, par exemple SharePoint ou Google Drive.

Votre dossier d’expériences doit ressembler à ceci :

![experiments-folder](/help/sites-cloud/administering/assets/experiments-folder.png)

Une fois le dossier créé, placez une copie de votre page de contrôle dans ce dossier et appliquez les modifications sur la page que vous souhaitez tester dans le cadre de votre variante d’expérience (voir la vidéo ci-dessus). Par exemple, supposons que le site web comporte la page suivante sur laquelle nous voulons exécuter une expérience :

![page-contrôle](/help/sites-cloud/administering/assets/control-page.png)

Votre copie du challenger placée dans le dossier `experiments/<experiment-id>` peut ressembler à ceci :

![page-challenger](/help/sites-cloud/administering/assets/challenger-page.png)

Prévisualisez et publiez la page du challenger à l’aide du sidekick et lorsque vous avez terminé de créer la page du Challenger. L’URL du challenger publié sera utilisée dans la section suivante : configuration de l’expérience.

### Configuration de l’expérience {#configure-experiment}

Dès que les pages de test sont prêtes à être utilisées, vous devez revenir à la page de contrôle et ajouter des métadonnées indiquant que les pages font désormais partie du test.

Deux lignes de métadonnées doivent être ajoutées pour une variante d’expérience.

* **Expérience** : contenant votre identifiant d’expérience.

* **Variantes d’expérience** : contient des URL pour tous les challengers de cette page, séparées par des sauts de ligne si vous avez plusieurs challengers.

Voir l’exemple ci-dessous :

![metadata-page](/help/sites-cloud/administering/assets/metadata-page.png)

Pour chaque expérience, le trafic est réparti entre toutes les variantes (contrôle et challengers) et est automatiquement défini sur une distribution égale. Ainsi, si vous avez un challenger, il y aura automatiquement une répartition égale de 50/50 entre le contrôle et le challenger. Si vous avez deux concurrents, vous verrez automatiquement un tiers du trafic alloué au contrôle et chaque concurrent et ainsi de suite.

Vous pouvez remplacer la répartition du trafic en configurant les métadonnées. Pour plus d’informations sur la personnalisation des métadonnées utilisées dans vos expériences, consultez la [ page suivante ](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring).

### Prévisualiser et préparer vos variantes d’expérience {#preview-stage-experiment}

Dès que vous êtes prêt(e) à prévisualiser et à organiser votre expérience, cliquez sur Aperçu dans le sidekick en haut à gauche. Chaque fois que vous prévisualisez une page qui comporte une expérience en cours d’exécution, la superposition de l’expérience s’affiche dans votre environnement d’aperçu `.aem.page`. Le recouvrement de l’expérience vous permet de basculer entre les variantes d’expérience et fournit également des données de trafic.

<!--- ![experimentation-overlay](/help/sites-cloud/administering/assets/experimentation-overlay.png)

By using the experimentation overlay, authors can get quick insights on the performance of experiments being run on the production site. These insights are helpful in making a decision about the duration of the experiment, but also about which variant is best suited for production.-->

La collecte des données permettant de mesurer l’efficacité de chaque variante repose sur le [service de télémétrie opérationnelle dans AEM as a Cloud Service](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md).

### Envoyer votre variante d’expérience à Production {#production-experiment}

Sélectionnez les pages d’expérience et cliquez sur Publier dans le sidekick pour activer à la fois le contrôle et la ou les variantes de challenger.

### Exemples de cas d’utilisation {#use-case-examples}

Vous trouverez ci-dessous plusieurs exemples de cas d’utilisation de variantes d’expérience. En règle générale, le workflow de base est similaire à celui décrit ci-dessus, avec des modifications particulières pour chaque cas d’utilisation (comme le nombre de pages de défi ou les modifications des métadonnées).

#### Expérience de page complète {#full-page}

Vous utilisez une expérience de page entière pour tester entre deux variantes d’une même page. Il s’agit d’une variante pleine page d’un test A/B où vous avez un contrôle et une page de défi. Vous remplacerez l’ensemble du contenu de la page de contrôle « originale » dans la variante challenger par un autre type de contenu. Gardez à l’esprit que, par défaut, le trafic client est divisé de manière égale (50/50), mais vous pouvez créer des divisions personnalisées si vous le souhaitez.

<!--The metadata on the control page should look like this:

METADATA SETUP

#### Sections of the page Experiment {#sections-of-the-page}

This is experiment is similar to the full page one presented above but now the a/b test will contain changes to a section of the page instead of the whole content. For example, you can modify and test a carousel element, the call to action element and so on. As such, you will have a control and a challenger page, with the challenger page containing the modified elements. The metadata on the control page should look like this:

METADATA SETUP

#### Multi-path Experiment {#multi-path}

By leveraging the experimentation plug-in, you can set up a/b tests on several pages of your website at once. For example, on all product pages, photo galleries, all blog posts and so on.

The configuration logic is the same as above - you will create a control page and one or more challenger variants of that page. What changes in the multi-page use-case, is the following:

• You will create multiple control pages each with one or more variants.
• The control pages must have the same experiment ID in metadata field.

For example: We have 5 different production pages for which we need to set up an a/b test. We create 5 control pages (as detailed in the chapters above) and 5 (or more) challenger variants.

We then create an experiment ID, let’s say `prod-exp` and add this ID in the experiment metadata field for each control page. This basically means that all pages with the same ID are now “grouped”. We then assign the challenger variants for each control page, taking care to sequence them properly in case we have more than one variant for each control.

The metadata on the control page should look like this:

METADATA SETUP

#### Code-level experiments {#code-level}

Note that the examples above assume you have different content variants to serve, but if you want to run a pure code-based a/b test, this is achievable via:

Metadata

Experiment    Hero Test
Experiment Variants    2

This will create just two variants, without touching the content, and you'll be able to target those based on the `experiment-hero-test` and `variant-control/variant-challenger-1/variant-challenger-`2 CSS classes that will be set on the `<body>` element.

#### Browser based audience experiment {#browser-based}

You can create browser based experiments, where you deliver separate challenger pages depending on the browser used. You can, for example, serve a different challenger page to a Firefox user as opposed to a Chrome user. This is achieved by leveraging the audience parameter.

Once you configure the experiment, the target audience will be evaluated based on the context of the browser (client side) and limited to the browser APIs available. As such, you do not need to use server side third-party systems or customer profile data for your experiment.

Before you start authoring this experiment variant, the audience parameter needs to be defined in the project codebase. For more details, see ee the following [page](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring).

Once the audiences have been defined you are ready to author the experiment. As stated previously, let’s say you want to create a Firefox versus Chrome experiment where you will serve different pages depending on the browser.

You need two different challenger pages, so set up the experiment as follows:

1.Duplicate the Control page by right-clicking and copying it to the experiment folder. You need to copies, one for Firefox and one for Chrome.
2.Rename the copies. Give them specific names like “page-for-firefox”.
3.Change the content of the pages depending on what you need to serve on Firefox versus Chrome.
4.Change the metadata as explained in the section below.
5.Click Preview from the side-kick in the upper left side, to preview the changes.

The most important part when authoring this experiment is to change the metadata in the control page. Let’s say you defined the browser audiences in the codebase as: Audience: Firefox and Audience: Chrome. You need to edit the control page and add these audiences and point to the appropriate challenge page you set up previously. It should look similar to this:

Metadata
Title Control Page
Description This is the control page.
Experiment ExpBrowser
Experiment Variants `https://{ref}--{repo}--{org}.hlx.page/my-page-for-firefox https://{ref}--{repo}--{org}.hlx.page/my-page-for-chrome`
Audience: Firefox `https://{ref}--{repo}--{org}.hlx.page/page-for-firefox`
Audience: Chrome `https://{ref}--{repo}--{org}.hlx.page/page-for-chrome`

After this configuration, the users will be triaged based on the browser they connect with and the appropriate challenger page will be served.

Please keep in mind that the names above are only for illustration purposes. You can define the Audiences parameter and the challenger pages according to your needs, for example: Audience (Firefox) or Audience Firefox.-->

## Autres considérations {#other-considerations}

Vous trouverez ci-dessous plusieurs autres aspects à prendre en compte lors de l’utilisation de l’expérimentation contextuelle.

### Conversion {#conversion}

Les expériences sont configurées pour gérer la conversion (suit les éléments cliquables sur votre page). Toutes les expériences doivent être définies pour les éléments suivants :

* Type d’expérience
* À quel bloc d’expérience l’expérience s’appliquera
* Nombre de variantes que l’expérience contiendra
* Quelle est la composition de chaque variante ?

### Assurez-vous que les variantes d’expérience ne sont pas indexées {#experiment-not-indexed}

Lors de l’exécution d’expériences, il est généralement recommandé d’exclure les variantes du plan du site et de s’assurer qu’elles ne sont pas indexées par les moteurs de recherche. Cela est dû au fait que la page de variante peut être considérée comme du contenu en double et avoir un impact négatif sur l’optimisation pour les moteurs de recherche.

Pour ce faire, vous pouvez utiliser l’une des deux méthodes suivantes :

* Si vous centralisez toutes les expériences dans un dossier dédié, comme `/experiments` : assurez-vous que votre feuille de `metadata.xlsx` en masse contient une ligne avec `/experiments/**` comme chemin d’accès et une colonne robots avec les valeurs `noindex`, `nofollow`.
* Si vous conservez le contrôle de l’expérience et les variantes avec le contenu standard : ajoutez une entrée robots dans les métadonnées de la page pour chaque variante, avec la valeur `noindex`, `nofollow`.

## Ressources du développeur et techniques {#dev-resources}

Adobe Experience Manager utilise [la télémétrie opérationnelle]&#x200B;(/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)

) pour collecter les données d’opération strictement nécessaires à la découverte et à la résolution des problèmes fonctionnels et de performances sur les sites gérés par Adobe Experience Manager. Les données de télémétrie opérationnelle peuvent être utilisées pour diagnostiquer les problèmes de performances. La télémétrie opérationnelle préserve la vie privée des visiteurs par échantillonnage (seule une petite partie de toutes les pages vues sera surveillée).

### Confidentiel {#privacy-experimentation}

Le [service de télémétrie opérationnelle](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) d’AEM as a Cloud Service est conçu pour préserver la confidentialité des visiteurs et minimiser la collecte de données. En tant que visiteur, cela signifie qu’Adobe ne tentera pas de collecter des informations personnelles vous concernant ou des informations qui peuvent être suivies jusqu’à vous. En tant qu’opérateur de site, passez en revue les éléments de données collectés ci-dessous pour comprendre s’ils nécessitent un consentement.
AEM Operational Telemetry n’utilise aucun état ou identifiant côté client, tel que des cookies ou des `localStorage`, des `sessionStorage` ou similaires, pour collecter des mesures d’utilisation. Les données sont envoyées de manière transparente par le biais d’un appel `Navigator.sendBeacon`, et non par le biais de pixels ou de techniques similaires. Il n’existe aucune « empreinte » d’appareils ou d’individus via leur adresse IP, la chaîne de l’agent utilisateur ou toute autre donnée dans le but de capturer des données échantillonnées.

Il n’est pas permis d’ajouter des données personnelles à la collecte de données de télémétrie opérationnelle et les données de télémétrie opérationnelle ne peuvent pas être utilisées dans des cas d’utilisation qui vont au-delà du strict nécessaire.

### Questions fréquentes {#faq}

Vous trouverez ci-dessous une liste de questions fréquentes :

Q : Puis-je ajuster le ratio de partage entre les variantes de mon expérience, par exemple 10 % sur le contrôle et 90 % sur le challenger ?

Oui, le ratio de partage peut être configuré via [métadonnées](#configure-experiment).

Q : Puis-je expérimenter à la fois du texte et des images ?

Oui, la variante peut être une page complètement différente, vous pouvez donc même tester les modifications de disposition.
