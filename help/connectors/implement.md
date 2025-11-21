---
title: Implémentation d’un connecteur AEM
description: Découvrez les connecteurs, ce qu’ils peuvent faire et comment mettre en œuvre ces précieux outils dans Experience Manager.
exl-id: 70024424-8c52-493e-bbc9-03d238b8a5f5
feature: Operations
role: Admin
source-git-commit: a9cec66cf518a19a5a6152d431a052369b5b503a
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 71%

---


Implémentation d’un connecteur AEM
=============================

Vous trouverez ci-dessous des références utiles pour créer des connecteurs AEM. Ils doivent être lus avec des conseils sur la [envoi](submit.md) et la [maintenance](maintain.md) des connecteurs.

Une licence de développeur pour AEM peut être obtenue via le [Programme Adobe Exchange](https://partners.adobe.com/technologyprogram/experiencecloud.html).

Modèles d’intégration courants
---------------------------

AEM est une solution de gestion de l’expérience web haut de gamme qui propose de nombreux domaines d’intégration potentiels. Les modèles d’intégration courants sont les suivants :

* Extraction de données d’un système externe dans AEM ; Par exemple, exporter des informations de contact depuis un système CRM afin de les mettre à la disposition d’un plus grand nombre de personnes qui visitent un site web utilisant la technologie AEM.  Les implémentations doivent utiliser les [tâches planifiées](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs) de Sling, ce qui garantit que la tâche est exécutée même si les conteneurs tombent en panne. Le code doit être conçu de manière à supposer que la tâche peut être déclenchée plusieurs fois.
* Exportation de données d’AEM vers un système externe. Par exemple, les paramètres d’abonnement à une newsletter sont envoyés à un CRM sur un site web optimisé par AEM.
* Récupération de ressources d’AEM. Il peut s’agir, par exemple, d’un système de gestion de contenu (CMS) externe faisant référence à une ressource stockée dans AEM Assets. Autre exemple : un système PIM lié à une image dans AEM Assets.
* Stockage de ressources dans l’infrastructure AEM. Il peut s’agir, par exemple, d’un système de gestion des ressources marketing (MRM) qui stocke une ressource approuvée dans AEM Assets.
* Configuration et rendu d’un composant d’interface utilisateur personnalisé. Vous pouvez, par exemple, autoriser un auteur à faire glisser un composant vidéo et à configurer une vidéo spécifique pour qu’elle soit lue sur le site en direct.
* Utilisation d’une ressource avec un service partenaire. Il s’agit, par exemple, de l’envoi d’une ressource vers une plateforme vidéo lorsqu’une page est publiée.
* Analyser un site, une page ou une ressource dans AEM Admin Console. Il peut s’agir, par exemple, de recommandations d’optimisation du moteur de recherche pour une page existante ou dépubliée.
* Accès au niveau de la page aux données utilisateur gérées par un service externe. Il peut s’agir, par exemple, d’utiliser des informations démographiques pour personnaliser l’expérience sur le site. Apprenez-en plus sur ContextHub, un framework qui permet de stocker, de manipuler et de présenter des données de contexte.
* Traduction d’une copie de site ou de métadonnées de ressource. Rendez-vous sur la page [AEM Translation Framework Bootstrap Connector](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) pour obtenir un exemple qui utilise AEM Translation Framework, l’implémentation privilégiée pour les connecteurs de traduction.


Documentation utile
--------------------

La [documentation](../overview/introduction.md) d’Experience Manager as a Cloud Service contient de précieuses informations sur le développement dans AEM. Vous trouverez, ci-dessous, quelques rubriques et références techniques que vous trouverez utiles lors de l’implémentation d’un connecteur AEM :

* Adobe Consulting Services (ACS) [AEM Samples](https://adobe-consulting-services.github.io/acs-aem-samples/) : code commenté destiné à aider les développeurs AEM
* Divers liens de documentation dans la section Modèles d’intégration courants de cet article

Ressources de la communauté
--------------------

Outre la documentation statique ci-dessus, Adobe et la communauté AEM proposent des ressources destinées à faciliter la commercialisation d’un connecteur :

* Le [forum AEM](https://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) de la communauté Adobe est un site actif sur lequel vous pouvez poser des questions et obtenir des réponses de vos pairs.
* D’autres ressources techniques Adobe sont disponibles pour certains niveaux de partenaire. En savoir plus sur le programme [Adobe Exchange](https://partners.adobe.com/technologyprogram/experiencecloud.html).
* Si votre entreprise souhaite obtenir une assistance en matière d’implémentation, contactez l’équipe [Services professionnels](https://solutionpartners.adobe.com/s/directory) d’Adobe ou utilisez le [Solution Partner Finder](https://solutionpartners.adobe.com/s/directory/) pour obtenir la liste des partenaires d’Adobe dans le monde entier.

Règles de structure du package
-----------------------

Pour faciliter les déploiements en continu, les packages AEM as a Cloud Service, tels que les connecteurs, maintiennent une division stricte entre le contenu « non modifiable » et le contenu « modifiable ». Les modules doivent être clairement organisés de manière à inclure :

* `/apps`
* `/content` et `/conf`

Les connecteurs doivent se conformer à ces directives de conditionnement, qui sont décrites sous [Structure de projet AEM](/help/implementing/developing/introduction/aem-project-content-package-structure.md). Les connecteurs existants doivent également être restructurés pour être conformes.

En outre, seul Adobe doit écrire du code dans `/libs` ; les clients et les partenaires écrivent du code dans `/apps`.

Les connecteurs existants peuvent également être restructurés pour déplacer toute configuration qui aurait pu placer `/etc` dans d’autres dossiers de niveau supérieur, tels que `/conf`. Cette restructuration a été effectuée dans le cadre d’AEM 6.5 et est décrite dans la [documentation d’AEM 6.5](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/implementing/deploying/restructuring/repository-restructuring).

Adobe recommande de placer la plupart du code du connecteur sous `/apps/connectors/<vendor>` pour conserver une structure de référentiel propre, en particulier pour les clients qui utilisent plusieurs connecteurs.

Configuration de Cloud Services
-----------------------------

Un aspect de l’implémentation du connecteur est le code qui soutient la configuration du connecteur. Ce code entraîne l’affichage d’une carte portant le nom du connecteur sous Outils > Opérations > Cloud Services. Lorsque vous cliquez dessus, un [explorateur de configurations](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) apparaît. Il permet au client de sélectionner le dossier parent où sera stockée la configuration du connecteur. Le code du connecteur doit générer un formulaire avec toutes les propriétés à configurer et stocker, au final, les valeurs dans un dossier de configuration sous `/conf`. Ce dossier pourra ensuite être sélectionné sous l’onglet Propriétés de Sites ou Propriétés d’Assets.


Configurations basées sur le contexte
-----------------------------

[Configurations basées sur le contexte](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) vous permettent de superposer une configuration sur différents dossiers, y compris les `/libs`, `/apps`, `/conf` et sous-dossiers situés sous `/conf`. L’héritage est pris en charge, de telle sorte qu’un client puisse définir la configuration globale tout en apportant des modifications spécifiques à chaque microsite. Comme il est possible d’utiliser cette fonctionnalité pour les configurations des services cloud, le code du connecteur doit référencer la configuration à l’aide de l’API de configuration basée sur le contexte au lieu de référencer un nœud de configuration spécifique.

Si des configurations modifiées sont utilisées dans le connecteur, concevez ce dernier de manière à gérer l’inclusion/la fusion des futures mises à jour apportées aux configurations par défaut fournies par le connecteur dans toute configuration client. Gardez à l’esprit que la modification du contenu ou des configurations personnalisés par le client sans préavis ni consentement peut perturber ou provoquer un comportement inattendu dans son connecteur.

Bonnes pratiques en matière de codage
----------------------

AEM as a Cloud Service étant une solution native au cloud, certaines instructions peuvent avoir un impact sur les stratégies de code d’un connecteur. Pour plus d’informations, voir [Directives de développement pour AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md).

Test du connecteur AEM
-------------------------

Pour créer des connecteurs (ou modifier des connecteurs existants), vous devez utiliser les techniques de développement de l’environnement local. L’équipe de partenaires fournit aux partenaires ISV un environnement sandbox dans lequel ils peuvent déployer leur connecteur AEM vers une application classique pour s’assurer qu’il fonctionne.
