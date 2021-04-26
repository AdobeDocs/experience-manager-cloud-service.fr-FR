---
title: Prise en main de AEM sans tête en tant que Cloud Service
description: Dans cette partie du Parcours de développement AEM sans tête, découvrez les conditions préalables AEM sans tête.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 9fb18dbe60121f46dba1e11d4133e5264a6d538d
workflow-type: tm+mt
source-wordcount: '3087'
ht-degree: 4%

---


# Prise en main de AEM sans en-tête en tant que Cloud Service {#getting-started}

>[!CAUTION]
>
>TRAVAUX EN COURS - La création de ce document est en cours et ne doit pas être comprise comme complète ou définitive ni être utilisée à des fins de production.

Dans cette partie du [Parcours de développement AEM sans tête,](overview.md) découvrez ce qui est nécessaire pour démarrer votre propre projet avec AEM sans tête.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent de l&#39;parcours sans tête AEM, [En savoir plus sur le développement sans tête de CMS](learn-about.md) vous avez appris la théorie de base de ce qu&#39;est un CMS sans tête et vous devriez maintenant :

* Comprendre les concepts de base et la terminologie de la diffusion de contenu sans en-tête
* Comprendre pourquoi et quand l&#39;absence de tête est requise
* Savoir à un niveau élevé comment les concepts sans tête sont utilisés et comment ils interagissent

Cet article s&#39;appuie sur ces principes de base pour vous aider à comprendre comment utiliser AEM pour mettre en oeuvre une solution sans tête.

## Intention {#objective}

Ce document vous aide à comprendre AEM sans tête dans le contexte de votre propre projet. Après lecture, vous devez :

* Comprenez les principes de base des AEM fonctionnalités sans tête.
* Connaissez les conditions préalables à l&#39;utilisation de AEM fonctions sans tête.
* Gardez à l’esprit AEM niveaux d’intégration sans tête.
* Être capable de définir votre projet en termes de portée.

## Principes de base des AEM {#aem-basics}

Avant de pouvoir définir votre projet sans tête dans AEM, il est important de comprendre certains concepts AEM de base.

### Instance Auteur {#author}

Pour le plus simple, AEM consiste en une instance d’auteur et une [instance de publication](#publish) qui fonctionnent ensemble pour créer, gérer et publier votre contenu.

Le contenu commence sur l’instance d’auteur. C’est ici que les auteurs de contenu créent leur contenu. L’environnement auteur offre divers outils permettant aux auteurs de créer, organiser et réutiliser leur contenu.

### Instance de publication {#publish}

Une fois le contenu créé dans l’instance d’auteur, il doit être publié pour être disponible à d’autres services. Une instance de publication contient tout le contenu qui a été publié.

### Réplication {#replication}

La réplication est l’acte de transfert de contenu de l’instance d’auteur à l’instance de publication. Cette opération est effectuée automatiquement par AEM lorsqu’un auteur ou un autre utilisateur disposant des droits appropriés publie du contenu.

### Résumé des principes de base des AEM {#aem-basics-summary}

A son niveau le plus simple, la création d’expériences numériques en AEM nécessite les étapes suivantes :

1. Vos auteurs de contenu créeront votre contenu sans en-tête dans l’instance d’auteur.
1. Lorsque ce contenu est prêt, il est répliqué sur l’instance de publication. Les API peuvent ensuite être appelées pour récupérer ce contenu.

AEM Headless tire parti de cette base technique en offrant des outils puissants pour gérer le contenu sans tête [décrit dans la section suivante.](#aem-headless-basics)

## AEM Notions de base sans en-tête {#aem-headless-basics}

Les capacités sans tête de l&#39;AEM sont basées sur quelques caractéristiques clés. Ces informations seront expliquées en détail dans les parties ultérieures du parcours. Il est important maintenant de ne connaître que les bases de ce qu&#39;ils font et de ce qu&#39;on les appelle.

### Modèles de fragment de contenu {#content-fragment-models}

Les modèles de fragments de contenu définissent la structure des données et du contenu que vous allez créer et gérer dans AEM. Il s’agit en quelque sorte du squelette de votre contenu. Lorsque vous choisissez de créer du contenu, vos auteurs choisissent parmi les modèles de fragment de contenu que vous définissez, ce qui les guide dans la création de contenu.

### Fragments de contenu {#content-fragments}

Les fragments de contenu permettent de concevoir, créer, organiser et publier du contenu indépendant des pages. Ils permettent de préparer le contenu prêt à être utilisé dans des emplacements multiples et sur plusieurs canaux.

Les fragments de contenu contiennent du contenu structuré et peuvent être diffusés au format JSON.

### API GraphQL et REST {#apis}

Pour modifier votre contenu sans encombre, AEM offre deux API robustes.

* L’API GraphQL permet de créer des requêtes d’accès et de diffusion de fragments de contenu.
* L’API REST Assets permet de créer et de modifier des fragments de contenu (et d’autres ressources).

Vous découvrirez ces API et comment les utiliser dans une partie ultérieure du parcours sans tête AEM. Pour plus de documentation, consultez la section [ressources supplémentaires](#additional-resources) ci-dessous.

## Niveaux d&#39;intégration sans en-tête {#integration-levels}

AEM prend en charge à la fois l&#39;intégralité de la pile et les modèles traditionnels complets ou en tête d&#39;un CMS. Cependant, AEM offres non seulement ces deux choix exclusifs, mais la possibilité de prendre en charge des modèles hybrides qui combinent les avantages des deux, offrant une flexibilité unique pour votre projet sans tête.

Afin d&#39;assurer votre compréhension des concepts sans tête, ce Parcours de développement AEM sans tête se concentre sur le modèle sans tête pur pour vous mettre en service le plus rapidement possible sans aucun codage en AEM.

Cependant, vous devez être conscient des possibilités hybrides supplémentaires qui s&#39;offrent à vous une fois que vous avez compris AEM caractéristiques sans tête. Nous présentons ces cas ci-dessous pour votre connaissance. À la fin du parcours, vous serez mieux informé de ces concepts au cas où une telle flexibilité serait nécessaire pour votre projet.

### Vous avez déjà une consommation externe de contenu sans en-tête, telle qu&#39;une application d&#39;une seule page (SPA). {#already-have-a-spa}

Supposons que votre besoin de base est au minimum de fournir du contenu de AEM à un service externe existant.

#### Niveau 1 : Intégration de fragments de contenu - Modèle sans en-tête traditionnel {#level-1}

Ce niveau d’intégration est le modèle sans tête traditionnel et permet aux auteurs de contenu de créer du contenu dans AEM et de le diffuser sans encombre à un certain nombre de services externes à l’aide de GraphQL ou de les modifier à partir de services externes à l’aide de l’API Ressources. Aucun codage n&#39;est requis dans AEM.

Dans ce modèle, l’AEM n’est utilisé que pour créer et diffuser le contenu à l’aide d’AEM Fragments de contenu. Le rendu et l’interaction avec le contenu sont délégués à l’application externe consommatrice, souvent une application d’une seule page (SPA).

#### Niveau 2 : Incorporer le SPA dans AEM - Modèle hybride {#level-2}

Ce niveau d’intégration repose sur le premier niveau, mais permet également à l’application externe (SPA) d’être intégrée dans AEM afin que les auteurs de contenu puissent vue le contenu dans le contexte de l’application externe dans l’AEM. L’application peut également prendre en charge une modification limitée de l’application externe dans AEM.

Ce niveau présente l’avantage de permettre aux auteurs de contenu de créer du contenu de manière flexible et en AEM du contenu de manière dynamique, leur contenu étant présenté en contexte avec un SPA externe incorporé, tout en délivrant le contenu sans encombre.

#### Niveau 3 : Incorporer et activer complètement les SPA dans AEM - Modèle hybride {#level-3}

Ce niveau d’intégration s’appuie sur le niveau 2 en permettant de modifier la plupart du contenu du SPA externe dans AEM.

### Vous n&#39;avez pas encore de consommateur externe du contenu sans en-tête tel qu&#39;une application d&#39;une seule page (SPA). {#do-not-have-a-spa}

Si votre objectif est de créer un nouveau SPA qui consomme sans encombre du contenu d’AEM, vous pouvez utiliser des fonctionnalités telles que les fragments de contenu pour gérer votre contenu sans en-tête, et également créer un cadre d’éditeur d’.

Grâce à l’éditeur SPA, le SPA consomme non seulement du contenu de l’AEM, mais il est également entièrement modifiable dans l’ par les auteurs de contenu, ce qui vous permet à la fois de bénéficier d’une diffusion sans en-tête et d’une modification contextuelle au sein de l’.

## Exigences et conditions préalables {#requirements-prerequisites}

Il y a plusieurs exigences avant de commencer votre projet AEM sans tête.

### Connaissances {#knowledge}

* GraphQL
* Expérience de développement création de SPA avec des cadres de réaction ou d&#39;Angular
* Compétences de base en AEM création de fragments de contenu et utilisation de l’éditeur

### Outils {#tools}

* Accès Sandbox pour tester le déploiement de votre projet
* Instance de développement local pour la modélisation et le test des données
* SPA externe existante ou autre consommateur de votre contenu sans tête AEM

## Définition de votre projet {#defining-your-project}

Pour tout projet réussi, il est important de définir clairement non seulement les exigences du projet, mais aussi les rôles et les responsabilités.

### Portée {#scope}

Il est très important de définir clairement la portée du projet. L&#39;étendue informe les critères d&#39;acceptation et vous permet d&#39;établir une définition de &quot;fait&quot;.

La première question que vous devez vous poser est : &quot;Qu&#39;est-ce que j&#39;essaie de faire avec AEM sans tête ?&quot; La réponse devrait être que vous disposez ou disposerez à l’avenir d’une application d’expérience que vous avez créée avec vos propres outils de développement et non avec l’AEM. Cette application d’expérience peut être une application mobile, un site Web ou toute autre application d’expérience destinée aux utilisateurs finaux. L’objectif de l’utilisation de AEM sans-tête est de fournir à votre application d’expérience un contenu créé, stocké et géré dans AEM avec des API ultramodernes qui appelleraient sans-tête pour récupérer le contenu ou même le contenu CRUD complet directement à partir de votre application d’expérience. Si ce n&#39;est pas ce que vous souhaitez faire, vous souhaitez probablement [revenir à la documentation AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr) et trouver la section qui convient le mieux à ce que vous voulez accomplir.

### Rôles et responsabilités {#roles-responsibilities}

Les rôles de chaque projet individuel varieront, mais les rôles importants à prendre en compte dans le contenu de AEM développement sans but lucratif sont les suivants :

* [Administrateur](#administrator)
* [Auteur de contenu](#content-author)
* [Content Modeler](#content-modeler)
* [Développeur](#developer)

#### Administrateur {#administrator}

L&#39;administrateur est responsable de la configuration et de la configuration de base de votre système. Par exemple, l&#39;administrateur va configurer votre organisation dans le système de gestion des utilisateurs de l&#39;Adobe, référencé dans Identity Management System (IMS). L&#39;administrateur sera le premier utilisateur de l&#39;organisation à recevoir une invitation par courrier électronique de l&#39;Adobe une fois votre organisation créée par Adobe dans IMS. L&#39;administrateur aura la possibilité de se connecter à IMS et d&#39;ajouter des utilisateurs d&#39;autres personnes.

Une fois les utilisateurs configurés par l’administrateur, ils se verront accorder les autorisations d’accéder à toutes les ressources AEM pour accomplir leur travail en tant que contributeurs à la diffusion de l’application d’expérience à l’aide d’AEM Headless.

L’administrateur doit être l’utilisateur qui configure AEM et prépare l’environnement d’exécution pour permettre aux [auteurs de contenu](#content-author) de créer et de mettre à jour le contenu et aux [développeurs](#developer) d’utiliser les API qui récupèrent ou modifient le contenu pour leurs applications d’expérience.

#### Auteur de contenu {#content-author}

Les auteurs de contenu créent et gèrent le contenu qui est distribué sans encombre par AEM. Les auteurs de contenu utilisent AEM fonctionnalités telles que les fragments de contenu et la console Ressources pour gérer leur contenu.

Les auteurs de contenu doivent garder à l’esprit les bonnes pratiques suivantes.

#### Plan de Localisation {#localization}

Prévoir la traduction et la localisation dès le début du projet. Considérez le &quot;gestionnaire de projet d&#39;internationalisation&quot; comme une personne distincte dont la responsabilité est de définir quel contenu doit être traduit et ce qui ne l&#39;est pas, et quel contenu traduit peut être modifié par les producteurs de contenu régionaux ou locaux.

Créez un plan sur la localisation de contenu dont vous aurez besoin.

* Avez-vous juste besoin de différentes langues ou aussi des langues pour adopter des spécificités régionales ?
* Avez-vous besoin de contenu multimédia enrichi tel que des images ou des vidéos pour être différent selon les paramètres régionaux ?

Soyez clair quant à votre processus de mise à jour du contenu. Quel est le processus d&#39;approbation que le système doit prendre en charge ? Les workflows AEM pourraient-ils être utilisés pour automatiser ce processus ?

Notez que votre [hiérarchie de contenu](#content-hierarchy) peut être exploitée pour faciliter la localisation.

Consultez la section [ressources supplémentaires](#additional-resources) pour obtenir une documentation supplémentaire sur les workflows AEM et les outils de localisation.

##### Exploitation de la hiérarchie de contenu {#content-hierarchy}

La hiérarchie des dossiers peut résoudre deux problèmes majeurs en ce qui concerne la gestion de contenu :

* [Localisation](#localization)  - AEM gère la localisation du contenu en conservant des copies du contenu dans des dossiers spécifiques aux paramètres régionaux.
* Organisation - Les dossiers servent à définir une hiérarchie de contenu nécessaire à la prise en charge des besoins de localisation et à gérer logiquement les fragments de contenu.

AEM permet une structure de contenu très flexible et une hiérarchie peut être arbitrairement grande. Cependant, il est important de comprendre que toute modification de la structure de dossiers peut avoir des conséquences inattendues pour les requêtes existantes qui [dépendent du chemin d’accès au contenu.](#developer) Par conséquent, une hiérarchie bien définie, clairement définie à l’avance, peut s’avérer extrêmement utile aux auteurs de contenu.

Les dossiers peuvent également être restreints afin de n’autoriser que certains types de contenu (en fonction des modèles de fragments de contenu). Il est généralement recommandé de toujours spécifier explicitement les modèles autorisés pour tous les dossiers de la hiérarchie. Spécification du contenu autorisé pour un dossier donné :

* Empêche les auteurs de contenu de créer du contenu qui n’appartient pas au dossier.
* Optimise le processus de création de contenu en filtrant les types de contenu autorisés dans le dossier au cours de la création pour n’afficher que les types de contenu valides.

En créant une structure de contenu appropriée, il devient plus facile de coordonner la création de contenu sans en-tête sur plusieurs canaux afin d’optimiser la réutilisation du contenu. L’exploitation du contenu sur plusieurs canaux améliorera considérablement l’efficacité de la production de contenu et la gestion des modifications.

##### Définir de bonnes conventions d&#39;attribution de noms {#naming-conventions}

Les noms de fragments de contenu doivent être descriptifs pour les auteurs de contenu. AEM gère de manière transparente l’échappement et/ou la troncature des noms des ID utilisés au niveau du référentiel. Par conséquent, les noms logiques fournis par les auteurs du contenu doivent toujours être lisibles et représenter le contenu.

* Nom incorrect : `cta_btn_1`
* Bon nom : `Call To Action Button`

Consultez la section [ressources supplémentaires](#additional-resources) pour obtenir de la documentation supplémentaire sur les conventions d&#39;appellation des pages AEM.

##### Ne pas surétendre l’imbrication de contenu {#content-nesting}

[Les ](#content-fragments) fragments de contenu sont utilisés dans AEM pour créer du contenu sans en-tête. AEM prend en charge jusqu’à dix niveaux d’imbrication de contenu pour les fragments de contenu. Cependant, il est important de garder à l’esprit que AEM devra résoudre itérativement chaque référence définie dans le fragment de contenu parent, puis vérifier s’il existe des références enfants dans tous les frères et soeurs. Ces opérations peuvent s&#39;additionner rapidement et devenir un problème de performance.

En règle générale, les références au fragment de contenu ne doivent pas être imbriquées au-delà de cinq niveaux.

#### Content Modeler {#content-modeler}

Les modélisateurs de contenu analysent les exigences relatives aux données qui doivent être diffusées sans encombre et définissent la structure de ces données. Ces structures sont appelées [Modèles de fragments de contenu](#content-fragment-models) en AEM. Les modèles de fragments de contenu sont utilisés comme base pour les fragments de contenu créés par les auteurs de contenu.

Une approche utile lors de la définition de modèles de fragments de contenu consiste à créer des modèles qui correspondent aux composants UX des applications qui consommeront le contenu.

Comme les auteurs de contenu interagissent avec les modèles en continu lorsqu’ils créent du contenu, l’alignement des modèles avec l’UX les aide à visualiser l’expérience numérique qui en résulte. En approfondissant cet alignement, vous pouvez affecter des icônes aux modèles de fragments de contenu qui représentent l’élément UX afin que les auteurs puissent intuitivement sélectionner le bon modèle en fonction des indices visuels.

#### Développeur {#developer}

Les développeurs sont chargés de rassembler le contenu créé sans encombre en AEM au consommateur de ce contenu, qui peut souvent être une application d’une seule page (SPA), une application Web progressive (PWA), un site Web ou tout autre service externe à l’AEM.

GraphQL sert de &quot;colle&quot; entre AEM et les consommateurs de contenu sans tête. GraphQL est la langue qui requête le contenu nécessaire.

Les développeurs doivent garder à l’esprit quelques recommandations de base lorsqu’ils planifient leurs requêtes :

* Les requêtes ne doivent pas dépendre d’un chemin d’accès fixe (`ByPath`) pour récupérer les fragments de contenu.
   * [Les auteurs de contenu ont un contrôle total sur la ](#content-hierarchy) hiérarchie des fragments de contenu et peuvent apporter des modifications susceptibles de rompre une telle requête.
   * Les requêtes doivent plutôt opter pour les références de modèles de fragments de contenu avec des paramètres de requête dynamiques pour filtrer les résultats afin de générer la charge utile souhaitée.
* Pour de meilleures performances de requête, utilisez toujours des requêtes persistantes dans AEM. Ces questions sont examinées plus loin dans le parcours.
* GraphQL est conçu pour être déclaratif suivant la devise &quot;Demandez exactement ce dont vous avez besoin, et obtenez exactement cela.&quot; Cela signifie que lors de la création de requêtes GraphQL, évitez toujours les requêtes de type `select *` que vous pouvez créer dans une base de données relationnelle.

Pour une [implémentation sans tête typique utilisant AEM,](#level-1) le développeur ne nécessite aucune connaissance de codage de l&#39;AEM.

### Performances requises {#performance-requirements}

Pour que tout projet soit un succès, les performances doivent être prises en compte avant la création de tout contenu.

Vous devez comprendre les attentes de vos utilisateurs/visiteurs et les concevoir pour ceux-ci. Définissez des objectifs de niveau de service (SLO) et mesurez-les pour comprendre si vous répondez aux attentes de vos utilisateurs.

#### Modèles de trafic {#traffic-patterns}

Pour comprendre les schémas de trafic et de trafic, début de recueillir ce que vous savez du passé et ensuite de projeter vers la croissance prévue au cours des prochaines années. Certaines des variables les plus importantes à prendre en compte :

* Combien d&#39;appels d&#39;API par heure/jour/mois attendez-vous et y a-t-il des pics et des saisons potentiels ?
* Combien y a-t-il d&#39;auteurs de contenu différents ?
* Combien d’auteurs de contenu prévoyez-vous de travailler simultanément ?
* Quelle est la fréquence des mises à jour du contenu ?
* Combien de modèles de contenu sont nécessaires ?
* Combien d&#39;instances de modèles seront nécessaires ?

#### Fréquence de mise à jour {#update-frequency}

Bien souvent, différentes sections d’expériences présentent différentes fréquences de mise à jour du contenu. Comprendre cela est important pour pouvoir affiner les configurations de CDN et de cache. Il s’agit également d’une entrée importante pour les [Modélisateurs de contenu](#content-modeler) lorsqu’ils conçoivent des modèles pour représenter votre contenu. Considérons :

* Certains types de contenu doivent-ils expirer après une certaine période ?
* Existe-t-il des éléments spécifiques à l’utilisateur qui ne peuvent donc pas être mis en cache ?

## Eléments suivants {#what-is-next}

Maintenant que vous avez terminé cette partie du Parcours de développement AEM sans tête, vous devez :

* Comprenez les principes de base des AEM fonctionnalités sans tête.
* Connaissez les conditions préalables à l&#39;utilisation de AEM fonctions sans tête.
* Gardez à l’esprit AEM niveaux d’intégration sans tête.
* Être capable de définir votre projet en termes de portée.

Vous devez poursuivre votre parcours sans tête AEM en examinant ensuite le document [Chemin vers votre première expérience en utilisant AEM Headless](path-to-first-experience.md) où vous apprendrez comment configurer les outils nécessaires et comment commencer à réfléchir à la modélisation de vos données en AEM.

## Ressources supplémentaires {#additional-resources}

Bien qu&#39;il soit recommandé de passer à la partie suivante du parcours de développement sans tête en examinant le document [Chemin vers votre première expérience en utilisant AEM sans tête,](path-to-first-experience.md) voici quelques ressources supplémentaires facultatives qui approfondissent certains concepts mentionnés dans ce document, mais qui ne sont pas nécessaires pour continuer sur le parcours sans tête.

* [Introduction à l&#39;architecture de Adobe Experience Manager en tant que Cloud Service](/help/core-concepts/architecture.md)  - Comprendre l&#39;AEM en tant que Cloud Service
* [AEM Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr)  sans en-tête - Utilisez ces didacticiels pratiques pour découvrir comment utiliser les différentes options de diffusion de contenu vers des points de terminaison sans en-tête avec AEM et choisissez ce qui vous convient.
* [Gestion de contenu sans en-tête utilisant les API](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses)  GraphQL - Suivez ce cours pour une présentation de l&#39;API GraphQL implémentée dans AEM. L’authentification via AdobeID est requise.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql)  - Ce projet GitHub comprend des exemples d&#39;applications qui mettent en évidence les API AEM GraphQL.
* [Concepts](/help/sites-cloud/authoring/getting-started/concepts.md)  de création - Documentation technique pour l’environnement de création d’AEM incluant des détails sur la configuration auteur-publication
* [Publication de pages](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)  - Documentation technique pour la publication de contenu sur AEM
* [Conventions](/help/implementing/developing/introduction/naming-conventions.md)  de dénomination - Documentation technique des restrictions de dénomination de page dans AEM
* [Gestionnaire de sites multiples et traduction](/help/sites-cloud/administering/msm-and-translation.md)  - Documentation technique sur AEM puissantes fonctions de traduction
* [workflows](/help/sites-cloud/authoring/workflows/overview.md)  AEM - Documentation technique sur l&#39;automatisation des workflows en AEM
* [Fragments](/help/assets/content-fragments/content-fragments.md)  de contenu - Documentation technique pour les fragments de contenu.
* [Modèles](/help/assets/content-fragments/content-fragments-models.md)  de fragment de contenu - Documentation technique pour les modèles de fragment de contenu.
* [Documentation](https://graphql.org)  technique GraphQL - Définition GraphQL (lien externe)
* [API](/help/assets/content-fragments/graphql-api-content-fragments.md)  GraphQL - Documentation technique expliquant comment créer des demandes d’accès et diffuser des fragments de contenu
* [API](/help/assets/content-fragments/assets-api-content-fragments.md)  REST Ressources - Documentation technique expliquant comment créer et modifier des fragments de contenu (et d’autres ressources)
* [Requêtes](/help/assets/content-fragments/graphql-api-content-fragments.md#persisted-queries-caching)  persistantes - Documentation technique sur les requêtes persistantes en AEM
* [En tête et sans tête en AEM](/help/implementing/developing/headful-headless.md)  - Une discussion complète sur les niveaux d&#39;intégration sans tête disponibles en AEM
