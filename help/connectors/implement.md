---
title: Implémentation d’un connecteur AEM
description: Implémentation d’un connecteur AEM
translation-type: ht
source-git-commit: 629de3a9f55d2e4c52ef91c9e0bb5d439aebe84f

---


Implémentation d’un connecteur AEM
=============================

Les informations fournies ci-dessous vous seront d’une grande utilité pour la création de [connecteurs AEM](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html). Elles doivent être lues parallèlement aux conseils sur l’[envoi](submit.md) et la [maintenance](maintain.md) des connecteurs.

Notez qu’une licence de développeur pour AEM peut être obtenue via le [programme Adobe Exchange](https://marketing.adobe.com/resources/content/resources/exchange-partner-program.html).

Modèles d’intégration courants
---------------------------

AEM est une solution de gestion de l’expérience web haut de gamme qui propose de nombreux domaines d’intégration potentiels. Les modèles d’intégration courants sont les suivants :

* Extraction de données d’un système externe dans AEM ; par exemple, exporter des informations de contact depuis un système CRM afin de les mettre à la disposition d’un plus grand nombre de personnes qui visitent un site web utilisant la technologie AEM. Les implémentations doivent utiliser les [tâches planifiées](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs) de Sling, ce qui garantit que la tâche est exécutée même si les conteneurs tombent en panne. Le code doit être conçu de manière à supposer que la tâche peut être déclenchée plusieurs fois.
* Exportation de données d’AEM vers un système externe. Il peut s’agir, par exemple, des paramètres d’abonnement à des newsletters envoyés à un système CRM sur un site web utilisant la technologie AEM.
* Récupération de ressources d’AEM. Il peut s’agir, par exemple, d’un système de gestion de contenu (CMS) externe faisant référence à une ressource stockée dans AEM Assets. Autre exemple : un système PIM lié à une image dans AEM Assets.
* Stockage de ressources dans l’infrastructure AEM. Il peut s’agir, par exemple, d’un système de gestion des ressources marketing (MRM) qui stocke une ressource approuvée dans AEM Assets.
* Configuration et rendu d’un composant d’interface utilisateur personnalisé. Vous pouvez, par exemple, autoriser un auteur à faire glisser un composant vidéo et à configurer une vidéo spécifique pour qu’elle soit lue sur le site en direct.
* Utilisation d’une ressource avec un service partenaire. Il s’agit, par exemple, de l’envoi d’une ressource vers une plate-forme vidéo lorsqu’une page est publiée.
* Analyse d’un site, d’une page ou d’une ressource dans AEM Admin Console. Il peut s’agir, par exemple, de recommandations d’optimisation du moteur de recherche pour une page existante ou non publiée.
* Accès au niveau de la page aux données utilisateur gérées par un service externe. Il peut s’agir, par exemple, de l’exploitation d’informations démographiques pour personnaliser l’expérience sur le site. Apprenez-en plus sur ContextHub, un framework qui permet de stocker, de manipuler et de présenter des données de contexte.
* Traduction d’une copie de site ou de métadonnées de ressource. Rendez-vous sur la page [AEM Translation Framework Bootstrap Connector](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) pour obtenir un exemple qui utilise AEM Translation Framework, l’implémentation privilégiée pour les connecteurs de traduction.


Documentation utile
--------------------

La [documentation](../overview/introduction.md) d’Experience Manager as a Cloud Service contient de précieuses informations sur le développement dans AEM. Vous trouverez, ci-dessous, quelques rubriques et références techniques que vous trouverez utiles lors de l’implémentation d’un connecteur AEM :

* Adobe Consulting Services (ACS) [AEM Samples](http://adobe-consulting-services.github.io/acs-aem-samples/) : code commenté destiné à aider les développeurs AEM
* Divers liens de documentation dans la section Modèles d’intégration courants de cet article

Ressources de la communauté
--------------------

Outre la documentation statique ci-dessus, Adobe et la communauté AEM proposent des ressources destinées à faciliter la commercialisation d’un connecteur :

* Le [forum AEM](http://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) de la communauté Adobe est un site actif sur lequel vous pouvez poser des questions et obtenir des réponses de vos pairs.
* D’autres ressources techniques Adobe sont disponibles pour certains niveaux de partenaire. En savoir plus sur le programme [Adobe Exchange](https://marketing.adobe.com/resources/content/resources/exchange-partner-program.html).
* Si votre entreprise souhaite obtenir une assistance en matière d’implémentation, contactez l’équipe [Services professionnels](http://www.adobe.com/fr/marketing-cloud/service-support/professional-consulting-training.html) d’Adobe ou utilisez le [Solution Partner Finder](https://solutionpartners.adobe.com/home/partnerFinder.html) pour obtenir la liste des partenaires d’Adobe dans le monde entier.

Règles de structure du module
-----------------------

Afin de prendre en charge les déploiements continus, les modules AEM as a Cloud Service, dont les connecteurs sont des exemples, présentent une séparation stricte entre le contenu « non modifiable » et le contenu « modifiable ». Les modules doivent être clairement séparés entre ceux qui incluent :

* `/apps`
* `/content` et `/conf`

Les connecteurs doivent respecter les directives de conditionnement décrites dans [cet article](/help/implementing/developing/introduction/aem-project-content-package-structure.md). Les connecteurs existants doivent également être restructurés pour être conformes.

En outre, seul Adobe doit écrire du code dans `/libs` ; les clients et les partenaires écrivent du code dans `/apps`.

Les connecteurs existants peuvent également être restructurés pour déplacer toute configuration qui aurait pu placer `/etc` dans d’autres dossiers de niveau supérieur, tels que `/conf`. Cela est décrit dans la [documentation d’AEM](https://helpx.adobe.com/fr/experience-manager/6-5/sites/deploying/using/repository-restructuring.html).

Il est recommandé de placer la majorité du code du connecteur sous `/apps/connectors/<vendor>` afin de promouvoir une structure de référentiel nette pour les clients qui ont plusieurs connecteurs.

Configuration de Cloud Services
-----------------------------

Le code sur lequel est basée la configuration du connecteur constitue l’un des aspects de son implémentation. Ce code entraîne l’affichage d’une carte portant le nom du connecteur sous Outils > Opérations > Cloud Services. Lorsque vous cliquez dessus, un navigateur de configuration s’affiche. Il permet au client de sélectionner le dossier parent où sera stockée la configuration du connecteur. Le code du connecteur doit générer un formulaire avec toutes les propriétés à configurer et stocker, au final, les valeurs dans un dossier de configuration sous `/conf`. Ce dossier pourra ensuite être sélectionné sous l’onglet Propriétés de Sites ou Propriétés d’Assets.


Configurations basées sur le contexte
-----------------------------

L’API [Context-Aware Configuration](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) permet de superposer la configuration entre différents dossiers, dont `/libs`, `/apps` et `/conf`, et sous-dossiers sous `/conf`. L’héritage est pris en charge, de telle sorte qu’un client puisse définir la configuration globale tout en apportant des modifications spécifiques à chaque microsite. Puisqu’il est possible d’exploiter cette fonctionnalité pour les configurations Cloud Services, le code de connecteur doit faire référence à la configuration à l’aide de l’API Context-Aware Configurations au lieu de faire référence à un nœud de configuration spécifique.

Si des configurations modifiées sont utilisées dans le connecteur, concevez ce dernier de manière à gérer l’inclusion/la fusion des futures mises à jour apportées aux configurations par défaut fournies par le connecteur dans toute configuration client. Pour rappel, modifier la configuration ou le contenu personnalisé (tel que modifié par le client) sans en avertir le client ou obtenir son accord est de nature à entraîner la défaillance du connecteur (ou à provoquer un comportement inattendu).

Bonnes pratiques en matière de codage
----------------------

AEM as a Cloud Service est une solution basée dans le cloud. Certaines directives peuvent donc avoir une incidence sur les stratégies de code d’un connecteur. Pour plus d’informations, voir [Directives de développement pour AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md).

Test du connecteur AEM
-------------------------

Pour créer des connecteurs (ou modifier des connecteurs existants), vous devez utiliser les techniques de développement de l’environnement local. L’équipe en charge des partenaires mettra à la disposition des partenaires ISV un environnement de test dans lequel ils pourront déployer leur connecteur AEM sur une application Vanilla pour s’assurer qu’il fonctionne.
