---
title: Expérimentation contextuelle dans AEM as a Cloud Service
description: Découvrez comment utiliser le rail d’expérimentation pour ajouter des fonctionnalités d’expérimentation à votre site.
feature: Administering
role: Admin
exl-id: 420f8d5e-27f9-4081-b174-b2d7752779f7
source-git-commit: 4764d9b3343ca88e0de7506d955741e8cac2f2e1
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 2%

---

# Expérimentation contextuelle dans AEM as a Cloud Service {#contextual-experimentation}

L’expérimentation consiste à tester la conception, les fonctionnalités et le code de votre site afin d’améliorer les performances et de rendre votre site plus efficace et rationalisé. Pour ce faire, vous devez modifier le contenu ou la fonctionnalité, comparer les résultats avec une version antérieure et sélectionner les améliorations qui ont des effets mesurables.

Lorsqu’il est bien fait, il s’agit d’un modèle puissant pour améliorer les conversions, l’engagement et l’expérience des visiteurs. En règle générale, il existe quelques problèmes à éviter lorsque vous envisagez d’adopter cette pratique :

* **Trop peu** : la plupart des entreprises n’expérimentent pas suffisamment, et lorsqu’elles le font, elles expérimentent avec trop peu de trafic pour obtenir des résultats significatifs.
* **Trop lent** : de nombreux frameworks d’expérimentation ralentissent le site à tel point que les nouvelles conversions potentielles ne peuvent pas compenser le trafic perdu et les bounces en raison d’un rendu lent.
* **Trop complexe** : si la configuration d’une nouvelle expérience prend trop de temps, le nombre d’expériences exécutées sera inférieur.

Pour les sites s’exécutant sur Adobe Experience Manager, les développeurs ont la possibilité d’ajouter une nouvelle fonctionnalité d’expérimentation à leurs sites. Trois éléments différencient cette approche des autres frameworks d’expérimentation :

* Il est facile de configurer des tests avec les outils que vos auteurs connaissent déjà et aucune connexion distincte n’est nécessaire.
* Il est profondément intégré au système de diffusion AEM, ne ralentit pas votre site et résiste aux changements de code et de contenu.
* Il permet de tester des modifications de contenu simples et de réaliser des expériences sur la conception, les fonctionnalités et le code.

## Rail d’expérimentation {#experimentation-rail}

Le rail d’expérimentation est votre principale méthode de configuration des expériences. Il peut être utilisé avec votre projet dans un contexte [&#128279;](/help/edge/overview.md) ou dans l’[éditeur universel](/help/implementing/universal-editor/introduction.md). Par conséquent, vous aurez besoin d’un compte Github, d’un référentiel de contenu tel que SharePoint ou Google Drive, ainsi que du plug-in [AEM Sidekick](https://www.aem.live/docs/sidekick). Si vous souhaitez utiliser l’éditeur universel, vous devez également accéder à un environnement AEM as a Cloud Service [&#128279;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Consultez également la page [Prise en main - Tutoriel de développement de l’éditeur universel](https://www.aem.live/developer/tutorial).

>[!WARNING]
>Le moteur d’expérimentation est requis pour utiliser la fonctionnalité d’expérimentation. Assurez-vous que le moteur est correctement installé et mis à jour avant d’implémenter les étapes ci-dessous. Voir la [page d’installation](https://github.com/adobe/aem-experimentation/tree/v2?tab=readme-ov-file#installation) pour plus d’informations.

### Configuration de l’expérimentation à l’aide d’AEM Sidekick dans Edge Delivery Services

Pour accéder aux fonctionnalités du rail d’expérimentation dans votre projet Edge Delivery Services, vous aurez besoin du plug-in [AEM Sidekick](https://www.aem.live/docs/sidekick). Pour configurer le sidekick, procédez comme suit :

1. Ajoutez l’extension [AEM sidekick](https://chromewebstore.google.com/search/AEM%20Sidekick?hl=en-US&utm_source=ext_sidebar) et épinglez-la dans votre navigateur.
1. Ouvrez la page de votre projet en mode Aperçu.
1. Sur la barre AEM Sidekick, cliquez sur l’icône des paramètres ![Paramètres](/help/sites-cloud/administering/assets/settings-1.png) et sélectionnez **Ajouter ce projet**.
1. Cliquez sur l’onglet Expérimentation pour ouvrir le rail d’expérimentation.

### Configuration de l’expérimentation dans l’éditeur universel

Avant de configurer des expériences, gardez à l’esprit que vous devrez utiliser les sites AEM comme source de contenu pour pouvoir créer dans l’éditeur universel. Si nécessaire, vous pouvez convertir votre projet existant en site AEM en tant que source de contenu en suivant le tutoriel présenté sur la page [Configurer AEM Sites as a Content Source](https://www.aem.live/developer/ue-tutorial). Lorsque vous êtes prêt(e) à configurer des expériences dans l’éditeur universel, procédez comme suit :

1. Ouvrez votre projet dans l’éditeur universel et vérifiez l’extension de l’icône **A/B**. Si l’icône n’est pas visible, vérifiez si vous avez activé la fonctionnalité dans le gestionnaire d’extensions. S’il n’est pas activé, activez-le ou demandez un accès.
   <!--1. Open your GitHub repository and check if the `plugins/experimention` folder exists. If not, you will need to set up the experimentation engine and MFE first (see the note above).-->
1. Pointez votre configuration `fstab.yaml` sur la configuration de votre projet et liez-la à votre instance d’auteur AEM. Voir aussi [Connecter votre code à votre contenu](https://www.aem.live/developer/ue-tutorial#connect-your-code-to-your-content)
1. Ouvrez votre instance AEM et, si votre projet est prêt, ouvrez-le directement dans l’éditeur universel.
1. Ouvrez le projet et la page d’index dans laquelle vous souhaitez exécuter des expériences, puis cliquez sur **Modifier** dans la barre supérieure.
1. Cliquez sur l’icône A/B pour ouvrir l’extension d’expérimentation.

>[!NOTE]
>Si vous rencontrez des problèmes pour configurer l’expérimentation de votre projet, contactez [&#128279;](mailto:aem-contextual-experimentation@adobe.com).

>[!NOTE]
>Pour plus d’informations sur la configuration du moteur d’expérimentation, reportez-vous à la section de documentation du [référentiel](https://github.com/adobe/aem-experimentation/tree/v2-ui) suivant.

## Variantes d’expérience et workflow général {#experiment-variants-workflow}

Avant de suivre le reste du guide de configuration de votre première expérience, vous devez connaître certains termes fréquemment utilisés :

* **Contrôle** : l’expérience avant d’exécuter l’expérience. Toutes les expériences tentent de tester et de démontrer une amélioration par rapport à l’expérience de contrôle.
* **Challenger** : une expérience différente de l’expérience de contrôle et « testée » par rapport à celle-ci ou à côté.
* **Variantes** : le contrôle et le challenger sont tous des variantes d’une expérience.
* **Signification statistique** : évaluer si votre concurrent est vraiment meilleur que le témoin. Le calcul de la signification statistique vous permet d’exclure la chance et de vous concentrer sur les résultats qui ont un effet réel.

En règle générale, lors de la configuration d’une expérience, vous utiliserez une page préexistante comme page de contrôle. En utilisant le rail d’expérimentation, vous allez ensuite créer une page de challenger qui est initialement une copie de la page de contrôle. Dans la page du challenger, vous pouvez tester différents éléments tels que des variantes de contenu, différentes mises en page, call-to-action (CTA), etc. Vous pouvez également utiliser des variantes générées par l’IA à l’aide de la fonctionnalité **Générer la variation** dans le rail d’expérimentation.

Pour chaque expérience, le trafic est initialement réparti 50/50 entre le contrôle et le challenger, mais vous pouvez configurer la manière dont le trafic est réparti selon les besoins. Après avoir activé l’expérience, vous recevrez des données via le service de télémétrie opérationnelle.

Le [service de télémétrie opérationnelle](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) rassemble des données, par exemple le nombre de visiteurs sur la page de contrôle par rapport à la page de défi. Vous utilisez ensuite ces données pour sélectionner les améliorations nécessaires pour votre site. Tant que vous respectez la langue de conception établie de votre site web et que vous utilisez les fonctionnalités existantes, vous devriez être en mesure de configurer une variante d’expérience et de l’envoyer en production en quelques minutes.

>[!NOTE]
>Gardez à l’esprit que le plug-in n’utilise aucune donnée de l’utilisateur final susceptible de conduire à son identification, et n’en conserve aucune. Aucun accord préalable de l’utilisateur final ni consentement des cookies n’est requis lors de l’utilisation de la configuration par défaut qui utilise le [&#x200B; service de télémétrie opérationnelle dans AEM as a Cloud Service &#x200B;](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md).

<!--### Frequently used terms {#frequently-used-terms}

Before following the rest of the guide to set up your first experiment, there are a few frequently used terms that you should be familiar with:

* **Control**: the experience prior to running the experiment. All experiments try to test and demonstrate an improvement over the control experience.
* **Challenger**: an experience that is different from the control experience and is "tested" against it or alongside it.
* **Variants**: control and challenger are all variants of an experiment.
* **Statistical Significance**: Evaluating if your challenger is really better than the control. Calculating statistical significance allows you to rule out luck and concentrate on the results that have a real effect. -->

### Création d’expériences dans l’éditeur universel

Pour utiliser les fonctionnalités d’expérimentation de l’éditeur universel, vous devez d’abord configurer le rail d’expérimentation comme décrit dans les chapitres présentés ci-dessus et vous assurer d’utiliser AEM Sites comme source de contenu. Une fois que tout est configuré, procédez comme suit.

### Commencer à modifier le projet dans l’éditeur universel

Ouvrez votre instance AEM et, si votre projet est prêt, ouvrez-le directement dans l’éditeur universel. Si aucun projet n’est prêt et que les sites AEM sont configurés en tant que source de contenu, créez un projet standard à partir du modèle fourni. Vous pouvez lier votre référentiel ou notre référentiel d’exemple pour le piloter [&#128279;](https://github.com/sudo-buddy/ue-experimentation). Consultez également la page [Configurer AEM Sites as a Content Source](https://www.aem.live/developer/ue-tutorial). Une fois le projet configuré, ouvrez-le, puis ouvrez la page d’index dans laquelle vous souhaitez exécuter des expériences et cliquez sur **Modifier** dans la barre supérieure.

### Lancer l’extension A/B

Cliquez sur l’icône **A/B** pour ouvrir l’extension d’expérimentation. Lors de votre première utilisation, l’interface sera vide. Cliquez sur **Créer** pour démarrer une nouvelle expérience.

![a-b](/help/sites-cloud/administering/assets/a-b.png)

### Configurer les détails de l’expérience

Certaines des valeurs d’expérience sont prédéfinies comme suit :

**Type d’expérience** : test A/B (type uniquement pris en charge pour l’instant)
**Optimisation pour** : conversion (seul le type est pris en charge pour l’instant)

Vous pouvez également renommer votre expérience en un élément plus explicite, par exemple : `homepage-head-experiment`.

![Détails de l’expérience](/help/sites-cloud/administering/assets/exp-values.png)

### Ajouter et modifier des variantes

Assurez-vous de comprendre les concepts de challenger et de variante tels qu’ils sont présentés ci-dessus avant de continuer. Cliquez sur **Ajouter** pour créer une variante de challenger :

* Vous serez redirigé vers la page du challenger dans le même onglet — il s&#39;agit initialement d&#39;une copie de votre contrôle.
* Modifiez la page directement en contexte ou cliquez sur **Générer la variation** pour utiliser l’assistance de l’IA.
* Après avoir apporté des modifications, revenez à l’extension pour continuer.

![Variante-contrôle](/help/sites-cloud/administering/assets/control-variant.png)

### Définir d’autres propriétés et Enregistrer en tant que brouillon

Dans le rail de l’expérimentation, vous pouvez définir une date de début et de fin (facultatives toutes deux). Si aucune date de début n’est fournie, le test commence une fois qu’il est publié. Si aucune date de fin n’est fournie, le test s’exécute indéfiniment. Vous pouvez également ajuster la répartition du trafic. Nous vous recommandons de commencer par une répartition égale de 50/50.

Une fois que vous avez terminé, cliquez sur **Enregistrer** — votre expérience sera enregistrée en tant que brouillon. Notez que l’expérience n’est pas encore active. Vous pouvez revenir à l’aperçu en cliquant sur **Retour à l’expérience** ou vous pouvez rester dans l’interface Modifier pour activer l’expérience.

![Brouillon](/help/sites-cloud/administering/assets/draft-save.png)

### Activer l’expérience

Une fois que vous êtes prêt, cliquez sur **Activer** pour lancer l’expérience et publier la page de l’expérience. Le test commencera à collecter des données de télémétrie opérationnelle (RUM) (voir plus de détails dans les chapitres suivants).

![Activer](/help/sites-cloud/administering/assets/activate.png)

### Surveiller et promouvoir

Une fois que l’expérience a atteint la signification statistique, cliquez sur **Promouvoir** pour faire de la variante souhaitée votre nouveau contrôle. Gardez à l’esprit que vous pouvez promouvoir la variante d’expérience à tout moment après l’activation, même si elle n’atteint pas la signification statistique.

### Utilisation de l’expérimentation avec AEM Sidekick dans Edge Delivery Services

Si AEM sidekick est installé, vous pouvez utiliser le rail d’expérimentation directement avec votre projet dans Edge Delivery Service sans utiliser l’éditeur universel. La fonctionnalité est essentiellement identique au test A/B décrit ci-dessus. Gardez simplement à l’esprit que vous devez être en mode **Aperçu** pour modifier et configurer le test. Une fois la configuration du test terminée, cliquez sur **Activer** pour activer le contrôle et la variante du challenger et commencer à collecter des données de télémétrie.

<!-- ### Experiment Identifier {#experiment-identifier}

Before you start, every experiment should have its own identifier for tracking and analytics purposes. A good starting point is to come up with a good, unique identifier for your experiment which will be the “Experiment ID”. Experiments are often numbered linearly or correlated to their Issue ID in an issue tracker or management system. Experiment IDs often use a prefix for the project, for example: `OPT-0134`, `EXP0004` or `CCX0076`.

### Create your Challenger Page {#create-challenger-page}

By convention, it is recommended to create a folder with a lowercase experiment ID in your `/experiments/ folder` (for example /experiments/ccx0076/). All the pages for the challenger variants are located in this folder. You create this folder in your local repository, for example, Sharepoint or Goggle Drive.

Your experiments folder should look something like this:

![experiments-folder](/help/sites-cloud/administering/assets/experiments-folder.png)

Once the folder is created, put a copy of your control page into that folder, and apply the changes on the page that you would like to test as part of your experiment variant (see video above). As an example let’s assume we have the following page on the website that we want to run an experiment on:

![control-page](/help/sites-cloud/administering/assets/control-page.png)

Your copy of the challenger placed in the experiments/experiment-id folder might look like this:

![challenger-page](/help/sites-cloud/administering/assets/challenger-page.png)

Preview and publish the challenger page using the sidekick and when you are done authoring the challenger page. The URL of the published challenger will be used in the next section - configuring the experiment.

### Configuring the experiment {#configure-experiment}

As soon as the challenger pages are ready to go, you need to go back to the control page and add metadata indicating that the page(s) are now part of the test.

There are two metadata rows that need to be added for an experiment variant.

* **Experiment**: containing your experiment ID.

* **Experiment Variants**: containing URLs for all the challengers of this page, separated by line breaks if you have more than one challenger.

See the example below:

![metadata-page](/help/sites-cloud/administering/assets/metadata-page.png)

For each experiment, the traffic is split between all the variants (control and challengers) and is automatically set to an even distribution. As such, if you have one challenger, there will automatically be an even 50/50 split between control and the challenger. If you have two challengers, you will automatically see a third of the traffic allocated to control and each challenger and so on.

You can override the traffic split by configuring the metadata. For more information on how you can customize the metadata used in your experiments, see the following [page](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring).

### Preview and Stage your Experiment Variants {#preview-stage-experiment}

As soon as you are ready to preview and stage your experiment, click Preview from the side-kick in the upper left side. Whenever you are previewing a page that has a running experiment, you will see the experimentation overlay in your `.aem.page` preview environment. The experimentation overlay lets you switch between the experiment variants and also provides traffic data.

<!--- ![experimentation-overlay](/help/sites-cloud/administering/assets/experimentation-overlay.png)

By using the experimentation overlay, authors can get quick insights on the performance of experiments being run on the production site. These insights are helpful in making a decision about the duration of the experiment, but also about which variant is best suited for production.-->

<!--- The data collection to measure the effectiveness of each variant is based on the [Operational Telemetry service in AEM as a Cloud Service](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md). -->

<!--- ### Send your Experiment Variant to Production {#production-experiment}

Select the experiment pages and click Publish from the side-kick to push both the control and the challenger variant(s) live.

### Use Case Examples {#use-case-examples}

Presented below are several use case examples for experiment variants. Generally speaking, the basic worklflow will be similar to the one described above, with particular changes for each use case (like the number of challenger pages or metadata changes).

#### Full Page Experiment {#full-page}

You use a full page experiment to test between two variants of the same page. This is a full page variant of an a/b test where you have a control and a challenger page. You will replace the whole content of the "original" control page in the challenger variant with a different type of content. Keep in mind that by default the customer traffic is split evenly (50/50), but you can create custom splits if you like. -->

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

Vous trouverez ci-dessous plusieurs aspects à prendre en compte lors de l’utilisation de l’expérimentation contextuelle.

### Conversion {#conversion}

Les expériences sont configurées pour gérer la conversion (suit les éléments cliquables sur votre page). Actuellement, nous prenons en charge les expériences au niveau de la page avec une expérience par page.

<!--### Make sure experiment Variants are not indexed {#experiment-not-indexed}

When running experiments, it is usually best practice to exclude the variants from the sitemap and ensure they are not indexed by search engines. This is because the variant page could be seen as duplicate content and negatively impact SEO.

You can do this by using either of the following two methods:

* If you centralize all experiments in a dedicated folder, like `/experiments`: make sure your bulk `metadata.xlsx` sheet contains a row with `/experiments/**` as path, and a robots column with the values `noindex`, `nofollow`.
* If you keep the experiment control and variants with the regular content: add a robots entry in the page metadata for each variant, with the value `noindex`, `nofollow`.-->

## Ressources du développeur et techniques {#dev-resources}

Adobe Experience Manager utilise la [télémétrie opérationnelle](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) pour collecter les données opérationnelles strictement nécessaires pour découvrir et résoudre les problèmes fonctionnels et les problèmes de performance sur les sites gérés par Adobe Experience Manager. Les données de télémétrie opérationnelle peuvent être utilisées pour diagnostiquer les problèmes de performances. La télémétrie opérationnelle préserve la vie privée des visiteurs par échantillonnage (seule une petite partie de toutes les pages vues sera surveillée).

### Confidentiel {#privacy-experimentation}

Le [service de télémétrie opérationnelle](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) d’AEM as a Cloud Service est conçu pour préserver la confidentialité des visiteurs et minimiser la collecte de données. En tant que visiteur, cela signifie qu’Adobe ne tentera pas de collecter des informations personnelles vous concernant ou des informations qui peuvent être suivies jusqu’à vous. En tant qu’opérateur de site, passez en revue les éléments de données collectés ci-dessous pour comprendre s’ils nécessitent un consentement.
AEM Operational Telemetry n’utilise aucun état ou identifiant côté client, tel que des cookies ou des `localStorage`, des `sessionStorage` ou similaires, pour collecter des mesures d’utilisation. Les données sont envoyées de manière transparente par le biais d’un appel `Navigator.sendBeacon`, et non par le biais de pixels ou de techniques similaires. Il n’existe aucune « empreinte » d’appareils ou d’individus via leur adresse IP, la chaîne de l’agent utilisateur ou toute autre donnée dans le but de capturer des données échantillonnées.

Il n’est pas permis d’ajouter des données personnelles à la collecte de données de télémétrie opérationnelle et les données de télémétrie opérationnelle ne peuvent pas être utilisées dans des cas d’utilisation qui vont au-delà du strict nécessaire.
