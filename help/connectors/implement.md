---
title: Implémentation d’un connecteur AEM
description: Implémentation d’un connecteur AEM
translation-type: tm+mt
source-git-commit: 629de3a9f55d2e4c52ef91c9e0bb5d439aebe84f

---


Implémentation d’un connecteur AEM
=============================

Vous trouverez ci-dessous des références utiles pour la création de connecteurs [](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) AEM. Elles doivent être lues conjointement avec des instructions sur l’ [envoi](submit.md) et la [maintenance](maintain.md) de connecteurs.

Notez qu’une licence de développeur pour AEM peut être obtenue via le programme [](https://marketing.adobe.com/resources/content/resources/exchange-partner-program.html)Adobe Exchange.

Modèles d’intégration courants
---------------------------

AEM est une solution de pointe de gestion de l’expérience Web et offre de nombreux domaines potentiels d’intégration. Les modèles d’intégration courants incluent :

* Extraction de données d’un système externe dans AEM. Par exemple, l’exportation des coordonnées d’un service de gestion de la relation client afin de les rendre accessibles à un public plus large qui consulte un site Web AEM.  Les implémentations doivent utiliser les tâches [planifiées](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs)de Sling, ce qui garantit que la tâche est exécutée même si les conteneurs disparaissent. Le code doit être conçu pour supposer que la tâche peut être déclenchée plusieurs fois.
* Exportation de données d’AEM vers un système externe. Par exemple, les paramètres d’abonnement au bulletin d’information envoyés sur un site Web alimenté par AEM à un service de gestion de la relation client.
* Récupération des ressources d’AEM. Par exemple, un système de gestion de contenu externe (CMS) référençant une ressource stockée dans AEM Assets. Ou, comme autre exemple, un système PIM lié à une image dans les ressources AEM.
* Stockage des ressources dans l’infrastructure AEM. Par exemple, un système de gestion des ressources marketing (MRM) qui stocke une ressource approuvée dans AEM Assets.
* Configuration et rendu d’un composant d’interface utilisateur personnalisé. Par exemple, permettez à un auteur de faire glisser un composant vidéo et de configurer une vidéo spécifique pour qu’elle soit lue sur le site en direct.
* Utilisation d’une ressource avec un service partenaire. Par exemple, l’envoi d’un fichier vers une plateforme vidéo lorsqu’une page est publiée.
* Analyse d’un site, d’une page ou d’un fichier dans la console d’administration AEM. Par exemple, si vous faites des recommandations d’optimisation du référencement pour une page existante ou non publiée.
* Accès au niveau de la page aux données utilisateur gérées par un service externe. Par exemple, tirez parti des informations démographiques pour personnaliser l’expérience du site. Découvrez ContextHub, une structure de stockage, de manipulation et de présentation des données contextuelles.
* Traduction de la copie de site ou des métadonnées de fichier. Consultez le connecteur [d’amorçage d’](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) AEM Translation Framework pour obtenir un exemple de code à l’aide d’AEM Translation Framework, qui est la meilleure implémentation des connecteurs de traduction.


Documentation utile
--------------------

Experience Manager en tant que [documentation](../overview/introduction.md) du service Cloud fournit des informations précieuses sur le développement dans AEM. Vous trouverez ci-dessous quelques rubriques et références techniques spécifiques que vous trouverez utiles lors de l’implémentation d’un connecteur AEM :

* Adobe Consulting Services (ACS) Exemples [d’](http://adobe-consulting-services.github.io/acs-aem-samples/) AEM pour un code bien commenté destiné à aider les développeurs AEM
* Les différents liens de documentation de la section Modèles d’intégration communs de cet article

Ressources de la communauté
--------------------

Outre la documentation statique ci-dessus, Adobe et la communauté AEM proposent des ressources pour aider à commercialiser un connecteur :

* Le forum [AEM de la communauté Adobe](http://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) est un site actif où vos pairs posent des questions et y répondent.
* Des ressources techniques Adobe supplémentaires sont disponibles pour certains niveaux de partenaires. En savoir plus sur le programme [Adobe Exchange](https://marketing.adobe.com/resources/content/resources/exchange-partner-program.html).
* Si votre entreprise souhaite obtenir de l’aide sur l’implémentation, contactez l’équipe des services [](http://www.adobe.com/marketing-cloud/service-support/professional-consulting-training.html) professionnels d’Adobe ou consultez le [Solution Partner Finder](https://solutionpartners.adobe.com/home/partnerFinder.html) pour obtenir la liste des partenaires d’Adobe dans le monde entier.

Règles de structure du package
-----------------------

Afin de prendre en charge les déploiements roulants, les packs AEM as a Cloud Service, dont les connecteurs sont des exemples, comportent une séparation stricte entre le contenu &quot;immuable&quot; et le contenu &quot;mutable&quot;. Les paquets doivent être soigneusement séparés entre ceux qui incluent :

* `/apps`
* `/content` et `/conf`

Les connecteurs doivent se conformer aux directives d’emballage décrites dans [cet article](/help/implementing/developing/introduction/aem-project-content-package-structure.md). Les connecteurs existants doivent également être restructurés pour être conformes.

En outre, seul Adobe doit écrire du code dans `/libs`lequel les clients et les partenaires écrivent `/apps`.

Les connecteurs existants peuvent également être reconfigurés pour déplacer toute configuration qui aurait pu être placée `/etc` dans d’autres dossiers de niveau supérieur, tels que `/conf`. Ceci est décrit dans la documentation [AEM](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/repository-restructuring.html).

Il est recommandé de placer la majorité du code du connecteur sous `/apps/connectors/<vendor>` afin de promouvoir une structure de référentiel propre pour les clients qui ont plusieurs connecteurs.

Configuration des services cloud
-----------------------------

L&#39;un des aspects de l&#39;implémentation du connecteur est le code qui sauvegarde la configuration du connecteur. Ce code entraîne l’affichage d’une carte portant le nom du connecteur sous Outils > Opérations > Services Cloud. Lorsque vous cliquez dessus, un navigateur de configuration s’affiche, où le client sélectionne le dossier parent pour contenir la configuration du connecteur. Le code du connecteur doit générer un formulaire avec toutes les propriétés à configurer, stockant en fin de compte les valeurs dans un dossier de configuration sous `/conf`. Ce dossier peut être sélectionné ultérieurement sous l’onglet Propriétés des sites ou Propriétés des ressources.


Configurations adaptées au contexte
-----------------------------

[Les configurations](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) basées sur le contexte permettent d’associer la configuration à différents dossiers, y compris `/libs`, `/apps`et sous-dossiers sous `/conf` `/conf`. Il prend en charge l’héritage afin qu’un client puisse configurer la configuration globale tout en apportant des modifications spécifiques à chaque microsite. Puisqu’il est possible d’exploiter cette fonctionnalité pour les configurations des services Cloud, le code de connecteur doit référencer la configuration à l’aide de l’API de configuration contextuelle au lieu de référencer un noeud de configuration spécifique.

Si des configurations modifiées sont utilisées dans Connector, architectez le Connector pour gérer l’inclusion/la fusion de toutes les futures mises à jour des configurations par défaut fournies par Connector avec toute configuration client. N’oubliez pas que la modification du contenu ou de la configuration personnalisé (tel que modifié par le client) sans avertissement et sans consentement du client peut rompre (ou créer un comportement inattendu) avec son connecteur.

Meilleures pratiques de codage
----------------------

Etant donné qu’AEM en tant que service Cloud est une solution native de Cloud, certaines directives peuvent avoir un impact sur les stratégies de code d’un connecteur. Voir [AEM as a Cloud Service Development Guidelines](/help/implementing/developing/introduction/development-guidelines.md) pour plus d’informations.

Test du connecteur AEM
-------------------------

De nouveaux connecteurs doivent être créés (ou des connecteurs existants modifiés) à l’aide de techniques de développement local de l’environnement. L’équipe partenaire fournira aux partenaires ISV un environnement de test dans lequel ils pourront déployer leur connecteur AEM sur une application vanille pour s’assurer qu’il fonctionne.
