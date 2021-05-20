---
title: Prise en main d’AEM sans tête en tant que Cloud Service
description: Dans cette partie du Parcours de développement AEM sans affichage, découvrez les conditions préalables AEM sans affichage .
source-git-commit: 8e96827f9353d6ffdf1e01645f2bc8bdaac2610f
workflow-type: tm+mt
source-wordcount: '3059'
ht-degree: 4%

---

# Prise en main d’AEM sans affichage en tant que Cloud Service {#getting-started}

Dans cette partie du [Parcours de développement AEM sans affichage,](overview.md) découvrez ce qui est nécessaire pour démarrer votre propre projet avec AEM sans affichage.

## L&#39;histoire jusqu&#39;à présent {#story-so-far}

Dans le document précédent du parcours sans interface utilisateur AEM, [Découvrez le développement sans affichage de CMS](learn-about.md) vous avez appris la théorie de base de ce qu’est un CMS sans interface et vous devez maintenant :

* Présentation des concepts de base et de la terminologie de la diffusion de contenu sans interface utilisateur
* Comprendre pourquoi et quand l’absence de tête est requise
* Découvrez à un haut niveau comment les concepts sans interface sont utilisés et comment ils interagissent

Cet article s’appuie sur ces principes de base afin que vous compreniez comment utiliser AEM pour mettre en oeuvre une solution sans interface utilisateur.

## Intention {#objective}

Ce document vous aide à comprendre AEM sans affichage dans le contexte de votre propre projet. Après lecture, vous devez :

* Comprendre les principes de base des fonctionnalités AEM sans interface.
* Découvrez les conditions préalables requises pour utiliser AEM fonctionnalités sans interface.
* Ayez conscience des niveaux d’intégration AEM sans interface.
* Soyez en mesure de définir votre projet en termes de portée.

## AEM Notions de base {#aem-basics}

Avant de pouvoir définir votre projet sans tête dans AEM, il est important de comprendre certains concepts AEM de base.

### Instance de création {#author}

Pour le plus simple, l’AEM se compose d’une instance d’auteur et d’une [instance de publication](#publish) qui travaillent ensemble pour créer, gérer et publier votre contenu.

Le contenu commence sur l’instance de création. C’est là que les auteurs de contenu créent leur contenu. L’environnement de création propose divers outils pour que les auteurs puissent créer, organiser et réutiliser leur contenu.

### Instance de publication {#publish}

Une fois que le contenu est créé dans l’instance d’auteur, il doit être publié pour être disponible pour d’autres services à utiliser. Une instance de publication contient tout le contenu qui a été publié.

### Réplication {#replication}

La réplication est l’acte de transfert de contenu de l’instance de création vers l’instance de publication. Cela est effectué automatiquement par AEM lorsqu’un auteur ou un autre utilisateur disposant des droits appropriés publie du contenu.

### Résumé des AEM de base {#aem-basics-summary}

À son niveau le plus simple, la création d’expériences numériques dans AEM nécessite les étapes suivantes :

1. Vos auteurs de contenu créeront votre contenu sans interface dans l’instance de création.
1. Lorsque ce contenu est prêt, il est répliqué sur l’instance de publication.
1. Les API peuvent ensuite être appelées pour récupérer ce contenu.

AEM’application Headless tire parti de cette base technique en offrant des outils puissants pour gérer le contenu sans tête, qui est [décrit dans la section suivante.](#aem-headless-basics)

## AEM Concepts de base sans affichage {#aem-headless-basics}

Les fonctionnalités sans interface d’AEM sont basées sur quelques fonctionnalités clés. Elles seront expliquées en détail dans les parties ultérieures du parcours. Il est important maintenant de ne connaître que les principes de base de ce qu&#39;ils font et de ce qu&#39;on les appelle.

### Modèles de fragment de contenu {#content-fragment-models}

Les modèles de fragments de contenu définissent la structure des données et du contenu que vous allez créer et gérer dans AEM. Il s’agit en quelque sorte du squelette de votre contenu. Lorsque vous choisissez de créer du contenu, vos auteurs choisissent parmi les modèles de fragment de contenu que vous définissez, ce qui les guide dans la création de contenu.

### Fragments de contenu {#content-fragments}

Les fragments de contenu permettent de concevoir, créer, organiser et publier du contenu indépendant des pages. Ils permettent de préparer le contenu prêt à être utilisé dans des emplacements multiples et sur plusieurs canaux.

Les fragments de contenu contiennent du contenu structuré et peuvent être diffusés au format JSON.

### API GraphQL et REST {#apis}

Pour modifier votre contenu sans interface utilisateur, AEM propose deux API robustes.

* L’API GraphQL permet de créer des requêtes d’accès et de diffusion de fragments de contenu.
* L’API REST Assets permet de créer et de modifier des fragments de contenu (et d’autres ressources).

Vous découvrirez ces API et comment les utiliser dans une partie ultérieure du parcours sans interface AEM. Pour plus d’informations, reportez-vous à la section [Ressources supplémentaires](#additional-resources) ci-dessous.

## Niveaux d’intégration sans affichage {#integration-levels}

AEM prend en charge les modèles complets sans tête et la pile complète ou les modèles avec en-tête d’un CMS. Cependant, AEM offre non seulement ces deux choix exclusifs, mais la possibilité de prendre en charge des modèles hybrides qui combinent les avantages des deux, offrant une flexibilité unique pour votre projet sans interface.

Afin de vous assurer de votre compréhension des concepts sans tête, ce Parcours de développement AEM sans tête se concentre sur le modèle sans tête pur pour vous mettre en service le plus rapidement possible sans codage dans AEM.

Toutefois, vous devez tenir compte des possibilités hybrides supplémentaires qui s’offrent à vous une fois que vous avez compris AEM fonctionnalités sans interface. Nous présentons ces cas ci-dessous pour votre prise de conscience. À la fin du parcours, vous découvrirez plus en détail ces concepts si une telle flexibilité est requise pour votre projet.

### Vous disposez déjà d’une consommation externe de contenu sans affichage, comme une application d’une seule page (SPA). {#already-have-a-spa}

Supposons que votre besoin de base soit au minimum de diffuser du contenu d’AEM vers un service externe existant.

#### Niveau 1 : Intégration de fragments de contenu - Modèle sans affichage traditionnel {#level-1}

Ce niveau d’intégration est le modèle sans interface utilisateur graphique traditionnel. Il permet aux auteurs de contenu de créer du contenu dans AEM et de le diffuser sans réfléchir à un certain nombre de services externes à l’aide de GraphQL ou de les modifier à partir de services externes à l’aide de l’API Assets. Aucun codage n’est requis dans AEM.

Dans ce modèle, AEM n’est utilisé que pour créer et diffuser du contenu à l’aide d’AEM fragments de contenu. Le rendu et l’interaction avec le contenu sont délégués à l’application externe consommatrice, souvent une application d’une seule page (SPA).

#### Niveau 2 : Incorporer le SPA dans AEM - Modèle hybride {#level-2}

Ce niveau d’intégration repose sur le premier niveau, mais permet également à l’application externe (SPA) d’être incorporée dans AEM afin que les auteurs de contenu puissent voir le contenu dans le contexte de l’application externe dans. L’application peut également prendre en charge la modification limitée de l’application externe dans AEM.

Ce niveau a l’avantage de permettre aux auteurs de contenu de créer de manière flexible du contenu dans AEM de manière sécurisée, avec leur contenu présenté en contexte avec un SPA externe intégré, tout en fournissant le contenu sans interface.

#### Niveau 3 : Incorporer et activer entièrement les SPA dans AEM - Modèle hybride {#level-3}

Ce niveau d’intégration repose sur le niveau 2 en permettant à la plupart du contenu de la SPA externe d’être modifiable dans AEM.

### Vous n’avez pas encore de consommateur externe de contenu sans en-tête, tel qu’une application d’une seule page (SPA). {#do-not-have-a-spa}

Si votre objectif est de créer une SPA qui consomme du contenu en toute sécurité à partir d’AEM, vous pouvez utiliser des fonctionnalités telles que les fragments de contenu pour gérer votre contenu sans affichage et créer également un  avec la structure de l’éditeur d’.

À l’aide de l’éditeur de SPA, le SPA consomme non seulement du contenu d’Adobe, mais il est également entièrement modifiable dans l’ par les auteurs de contenu, ce qui vous offre à la fois la flexibilité d’une diffusion sans interface utilisateur et de l’édition dans le contexte d’Adobe.

## Conditions requises et conditions préalables {#requirements-prerequisites}

Un certain nombre d’exigences s’imposent avant de commencer votre projet AEM sans interface utilisateur.

### Connaissances {#knowledge}

* GraphQL
* Expérience de développement créant des SPA avec des structures React ou Angular
* Compétences de base AEM la création de fragments de contenu et l’utilisation de l’éditeur

### Outils {#tools}

* Accès aux environnements de test pour tester le déploiement de votre projet
* Instance de développement locale pour la modélisation et le test des données
* SPA externe existante ou autre consommateur de contenu AEM sans interface utilisateur

## Définition de votre projet {#defining-your-project}

Pour tout projet réussi, il est important de définir clairement non seulement les exigences du projet, mais aussi les rôles et les responsabilités.

### Portée {#scope}

Il est très important de définir clairement la portée du projet. La portée informe les critères d’acceptation et vous permet d’établir une définition de &quot;terminé&quot;.

La première question que vous devez vous poser est : &quot;Qu&#39;est-ce que j&#39;essaie de faire avec AEM sans tête ?&quot; La réponse doit généralement être que vous disposez ou aurez à l’avenir une application d’expérience que vous avez créée avec vos propres outils de développement et non conjointement avec AEM. Cette application d’expérience peut être une application mobile, un site web ou toute autre application d’expérience destinée aux utilisateurs finaux. L’objectif de l’utilisation d’AEM sans affichage est de nourrir votre application d’expérience avec du contenu créé, stocké et géré dans AEM avec des API dernier cri qui appelleraient sans affichage pour récupérer du contenu ou même du contenu entièrement CRUD directement à partir de votre application d’expérience. Si ce n’est pas ce que vous souhaitez faire, vous devrez probablement [revenir à la documentation AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=fr) et trouver la section qui convient le mieux à ce que vous souhaitez accomplir.

### Rôles et responsabilités {#roles-responsibilities}

Les rôles de chaque projet individuel varient, mais les rôles importants à prendre en compte dans le contenu du développement AEM sans interface sont les suivants :

* [Administrateur](#administrator)
* [Auteur de contenu](#content-author)
* [Modéliseur de contenu](#content-modeler)
* [Développeur](#developer)

#### Administrateur {#administrator}

L’administrateur est responsable de la configuration et de la configuration de base de votre système. Par exemple, l’administrateur configure votre organisation dans le système de gestion des utilisateurs Adobe, qui est désigné sous le nom de système Identity Management (IMS). L’administrateur sera le premier utilisateur de l’organisation à recevoir une invitation par courrier électronique de l’Adobe une fois que votre organisation a été créée par Adobe dans IMS. L’administrateur aura la possibilité de se connecter à IMS et d’ajouter des utilisateurs d’autres personnes.

Une fois les utilisateurs configurés par l’administrateur, ils auront les autorisations d’accéder à toutes les ressources AEM pour accomplir leur travail en tant que contributeurs à la diffusion de l’application d’expérience à l’aide d’AEM Headless.

L’administrateur doit être l’utilisateur qui configure AEM environnement d’exécution et le prépare pour permettre aux [auteurs de contenu](#content-author) de créer et de mettre à jour du contenu, et aux [développeurs](#developer) d’utiliser des API qui récupèrent ou modifient du contenu pour leurs applications d’expérience.

#### Auteur de contenu {#content-author}

Les auteurs de contenu créent et gèrent le contenu qui est diffusé sans interface par AEM. Les auteurs de contenu utilisent AEM fonctionnalités telles que les fragments de contenu et la console Ressources pour gérer leur contenu.

Les auteurs de contenu doivent garder à l’esprit les bonnes pratiques suivantes.

#### Planification de la localisation {#localization}

Planifiez la traduction et la localisation dès le début du projet. Considérez &quot;Gestionnaire de projets d’internationalisation&quot; comme une personne distincte dont la responsabilité est de définir quel contenu doit être traduit et ce qui ne l’est pas, et quel contenu traduit peut être modifié par les producteurs de contenu régionaux ou locaux.

Créez un plan sur la localisation de contenu dont vous aurez besoin.

* Avez-vous seulement besoin de différentes langues ou aussi d&#39;une langue pour adopter les spécificités régionales ?
* Avez-vous besoin que le contenu multimédia enrichi tel que les images ou les vidéos soit différent pour différents paramètres régionaux ?

Soyez clair au sujet de votre workflow de mise à jour du contenu. Quel est le processus d’approbation que le système doit prendre en charge ? AEM workflows peuvent-ils être utilisés pour automatiser ce processus ?

Notez que votre [hiérarchie de contenu](#content-hierarchy) peut être utilisée pour faciliter la localisation.

Voir la section [ressources supplémentaires](#additional-resources) pour obtenir de la documentation supplémentaire sur les processus AEM et les outils de localisation.

##### Tirer parti de la hiérarchie du contenu {#content-hierarchy}

La hiérarchie de dossiers peut répondre à deux préoccupations majeures concernant la gestion de contenu :

* [Localisation](#localization)  : AEM gère la localisation du contenu en conservant des copies du contenu dans des dossiers spécifiques aux paramètres régionaux.
* Organisation : les dossiers servent à définir une hiérarchie de contenu nécessaire à la prise en charge des besoins de localisation et à gérer logiquement les fragments de contenu.

AEM permet une structure de contenu très flexible et une hiérarchie peut être arbitrairement volumineuse. Toutefois, il est important de comprendre que toute modification de la structure de dossiers peut avoir des conséquences inattendues sur les requêtes existantes qui [dépendent du chemin d’accès au contenu.](#developer) Par conséquent, une hiérarchie bien définie, clairement définie à l’avance, peut s’avérer extrêmement utile aux auteurs de contenu.

Les dossiers peuvent également être limités de manière à autoriser uniquement certains types de contenu (en fonction des modèles de fragment de contenu). Il est généralement recommandé de toujours spécifier explicitement les modèles autorisés pour tous les dossiers de la hiérarchie. Spécification du contenu autorisé pour un dossier donné :

* Empêche les auteurs de contenu de créer du contenu qui n’appartient pas au dossier.
* Optimise le processus de création de contenu en filtrant les types de contenu autorisés dans le dossier au cours de la création pour n’afficher que les types de contenu valides.

En créant une structure de contenu appropriée, il devient plus facile de coordonner la création de contenu headless sur plusieurs canaux afin d’optimiser la réutilisation du contenu. L’utilisation du contenu sur plusieurs canaux améliore considérablement l’efficacité de la production de contenu et la gestion des modifications.

##### Définition de bonnes conventions d’attribution de noms {#naming-conventions}

Les noms des fragments de contenu doivent être descriptifs pour les auteurs de contenu. AEM gère de manière transparente l’échappement et/ou la troncation des noms utilisés pour les ID au niveau du référentiel. Par conséquent, les noms logiques fournis par les auteurs de contenu doivent toujours être lisibles et représenter le contenu.

* Nom incorrect : `cta_btn_1`
* Nom : `Call To Action Button`

Voir la section [ressources supplémentaires](#additional-resources) pour obtenir de la documentation supplémentaire sur les conventions d’appellation des pages AEM.

##### Ne pas surétendre l’imbrication de contenu {#content-nesting}

[Les ](#content-fragments) fragments de contenu sont utilisés dans AEM pour créer du contenu headless. AEM prend en charge jusqu’à dix niveaux d’imbrication de contenu pour les fragments de contenu. Toutefois, il est important de garder à l’esprit que AEM devra résoudre de manière itérative chaque référence définie dans le fragment de contenu parent, puis vérifier s’il existe des références enfants dans tous les frères. Ces opérations peuvent s’additionner rapidement et devenir une préoccupation de performance.

En règle générale, les références aux fragments de contenu ne doivent pas être imbriquées au-delà de cinq niveaux.

#### Modéliseur de contenu {#content-modeler}

Les modélisateurs de contenu analysent les exigences relatives aux données qui doivent être distribuées sans interface utilisateur et définissent la structure de ces données. Ces structures sont appelées [Modèles de fragment de contenu](#content-fragment-models) dans AEM. Les modèles de fragment de contenu sont utilisés comme base des fragments de contenu créés par les auteurs de contenu.

Une approche utile lors de la définition de modèles de fragment de contenu consiste à créer des modèles qui mappent les composants UX des applications qui consomment le contenu.

Comme les auteurs de contenu interagissent avec les modèles de manière continue lorsqu’ils créent du contenu, l’alignement des modèles avec l’expérience utilisateur les aide à visualiser l’expérience numérique qui en résulte. Pour aller plus loin, vous pouvez attribuer des icônes aux modèles de fragment de contenu qui représentent l’élément UX afin que les auteurs puissent sélectionner intuitivement le bon modèle en fonction des indices visuels.

#### Développeur {#developer}

Les développeurs sont chargés de rassembler le contenu en cours de création sans faire de AEM pour le consommateur de ce contenu, qui peut souvent être une application d’une seule page (SPA), une application web progressive (PWA), une boutique en ligne ou un autre service externe à.

GraphQL sert de &quot;colle&quot; entre AEM et les consommateurs de contenu sans interface. GraphQL est la langue qui interroge AEM contenu nécessaire.

Les développeurs doivent garder à l’esprit quelques recommandations de base lorsqu’ils planifient leurs requêtes :

* Les requêtes ne doivent pas dépendre d’un chemin d’accès fixe (`ByPath`) pour récupérer les fragments de contenu.
   * [Les auteurs de contenu contrôlent complètement la ](#content-hierarchy) hiérarchie des fragments de contenu et peuvent apporter des modifications qui rompraient cette requête.
   * Les requêtes doivent plutôt opter pour les références de modèle de fragment de contenu avec des paramètres de requête dynamiques pour filtrer les résultats afin de générer la charge utile souhaitée.
* Pour de meilleures performances de requête, utilisez toujours des requêtes persistantes dans AEM. Celles-ci sont discutées plus loin dans le parcours.
* GraphQL est conçu pour être déclaratif en suivant la devise &quot;Demandez exactement ce dont vous avez besoin et obtenez exactement cela&quot;. Cela signifie que lors de la création de requêtes GraphQL, évitez toujours les requêtes de type `select *` que vous pouvez créer dans une base de données relationnelle.

Pour une [mise en oeuvre sans interface utilisateur type à l’aide d’AEM,](#level-1) le développeur ne nécessite aucune connaissance en codage d’AEM.

### Exigences de performance {#performance-requirements}

Pour qu’un projet soit une réussite, les performances doivent être prises en compte avant la création d’un contenu.

Vous devez comprendre les attentes de vos utilisateurs/visiteurs et les concevoir pour ceux-ci. Définissez des objectifs de niveau de service (SLO) et mesurez-les pour comprendre si vous répondez aux attentes de votre utilisateur.

#### Modèles de trafic {#traffic-patterns}

Pour comprendre les schémas de trafic et de trafic, commencez par recueillir ce que vous savez du passé, puis projetez vers la croissance attendue au cours des prochaines années. Certaines des variables les plus importantes à prendre en compte :

* Combien d’appels d’API par heure, par jour ou par mois attendez-vous et y a-t-il des pics et des saisons potentiels ?
* Combien y a-t-il d’auteurs de contenu différents ?
* Combien d’auteurs de contenu prévoyez-vous de travailler simultanément ?
* Quelle est la fréquence des mises à jour du contenu ?
* Combien de modèles de contenu sont nécessaires ?
* Combien d’instances de modèles seront nécessaires ?

#### Fréquence de mise à jour {#update-frequency}

Bien souvent, différentes sections d’expériences ont différentes fréquences de mises à jour de contenu. Comprendre cela est important pour pouvoir affiner les configurations du réseau de diffusion de contenu et du cache. Il s’agit également d’une entrée importante pour les [Modélisateurs de contenu](#content-modeler), car ils conçoivent des modèles pour représenter votre contenu. Prenez en compte :

* Certains types de contenu doivent-ils expirer après une certaine période ?
* Certains éléments sont-ils spécifiques à l’utilisateur et ne peuvent donc pas être mis en cache ?

## Suite {#what-is-next}

Maintenant que vous avez terminé cette partie du Parcours de développement AEM sans affichage, vous devez :

* Comprendre les principes de base des fonctionnalités AEM sans interface.
* Découvrez les conditions préalables requises pour utiliser AEM fonctionnalités sans interface.
* Ayez conscience des niveaux d’intégration AEM sans interface.
* Soyez en mesure de définir votre projet en termes de portée.

Continuez votre parcours sans tête AEM en consultant le document [Chemin vers votre première expérience à l’aide d’AEM sans tête](path-to-first-experience.md) dans lequel vous apprendrez à configurer les outils nécessaires et comment commencer à réfléchir à la modélisation de vos données dans l’.

## Ressources supplémentaires {#additional-resources}

Bien qu’il soit recommandé de passer à la partie suivante du parcours de développement sans interface utilisateur en examinant le document [Chemin vers votre première expérience à l’aide d’AEM sans interface utilisateur,](path-to-first-experience.md) les ressources facultatives supplémentaires qui approfondissent certains concepts mentionnés dans ce document, mais qui ne sont pas requises pour continuer sur le parcours sans interface utilisateur.

* [Présentation de l’architecture d’Adobe Experience Manager as a Cloud Service](/help/core-concepts/architecture.md)  - Présentation d’AEM en tant que structure de Cloud Service
* [AEM Tutorials sans affichage](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=fr)  : utilisez ces tutoriels pratiques pour découvrir comment utiliser les différentes options de diffusion de contenu vers des points de terminaison sans interface avec AEM et choisissez ce qui vous convient.
* [Gestion de contenu sans affichage à l’aide des API GraphQL](https://experienceleague.adobe.com/?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses)  : suivez ce cours pour une présentation de l’API GraphQL implémentée dans AEM. L’authentification via Adobe ID est requise.
* [AEM Guides WKND - GraphQL](https://github.com/adobe/aem-guides-wknd-graphql)  - Ce projet GitHub comprend des exemples d’applications qui mettent en évidence AEM API GraphQL.
* [Concepts de création](/help/sites-cloud/authoring/getting-started/concepts.md)  : documentation technique pour l’environnement de création d’AEM, y compris des détails sur la configuration auteur-publication.
* [Publication de pages](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)  : documentation technique pour la publication de contenu sur AEM
* [Conventions de dénomination](/help/implementing/developing/introduction/naming-conventions.md)  : documentation technique des restrictions de dénomination de page dans AEM
* [Multi Site Manager et traduction](/help/sites-cloud/administering/msm-and-translation.md)  - Documentation technique sur AEM puissantes fonctionnalités de traduction
* [AEM workflows](/help/sites-cloud/authoring/workflows/overview.md)  - Documentation technique sur l’automatisation des workflows dans AEM
* [Fragments de contenu](/help/assets/content-fragments/content-fragments.md)  : documentation technique pour les fragments de contenu.
* [Modèles de fragment de contenu](/help/assets/content-fragments/content-fragments-models.md)  : documentation technique pour les modèles de fragment de contenu.
* [Documentation technique GraphQL](https://graphql.org)  - La définition GraphQL (lien externe)
* [API GraphQL](/help/assets/content-fragments/graphql-api-content-fragments.md)  : documentation technique qui explique comment créer des demandes d’accès et de diffusion de fragments de contenu.
* [API REST Assets](/help/assets/content-fragments/assets-api-content-fragments.md)  : documentation technique qui explique comment créer et modifier des fragments de contenu (et d’autres ressources).
* [Requêtes persistantes](/help/assets/content-fragments/graphql-api-content-fragments.md#persisted-queries-caching)  - Documentation technique sur les requêtes persistantes dans AEM
* [Headful and Headless dans AEM](/help/implementing/developing/headful-headless.md)  - Une discussion complète sur les niveaux d’intégration sans tête disponibles dans AEM
