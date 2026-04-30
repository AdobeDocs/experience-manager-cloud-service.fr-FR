---
title: AEM AS A CLOUD SERVICE DEVELOPER CONSOLE - BETA
description: Découvrez AEM as a Cloud Service Developer Console et son ensemble d’outils en lecture seule pour le débogage des environnements cloud.
feature: Developing
role: Admin, Developer
exl-id: 4b0fc3e9-b7c4-4c95-bd97-8b24e4d5cb3d
source-git-commit: 51c14ba3c15e0136911003752253d21ed673a0eb
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 1%

---


# Developer Console AEM as a Cloud Service (Beta) {#developer-console}

AEM as a Cloud Service Developer Console comprend un ensemble d’outils en lecture seule pour le débogage des environnements cloud. Il est accessible par le biais d’un lien spécifique à l’environnement dans Cloud Manager et offre des fonctionnalités permettant d’afficher les lots, les paramètres OSGi, les services et les servlets, etc.

>[!NOTE]
>
>Cet article décrit une expérience repensée pour AEM Cloud Service Developer Console, qui est désormais en version bêta.
>
>* Un nombre limité d’utilisateurs peut accéder à la nouvelle console à l’aide d’un bouton dans la partie supérieure du Developer Console actuel.
>* Adobe vous invite à envoyer vos commentaires à `aemcs-new-devconsole-ui-beta@adobe.com`.
>* Pour consulter la documentation relative à la version actuelle d’AEM Developer Console, reportez-vous [cet article.](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console)
>* Le Developer Console AEM as a Cloud Service ne doit pas être confondu avec le similaire nommé [*Adobe Developer Console*.](https://developer.adobe.com/developer-console/)

>[!TIP]
>
>Le Developer Console est en lecture seule. Si vous travaillez sur un développement local à l’aide de SDK et que vous devez modifier les paramètres OSGi ou le contenu du référentiel, vous pouvez utiliser :
>
>* [CRXDE Lite.](/help/implementing/developing/tools/crxde.md)

<!--
There are multiple ways of accessing it:

1. Launch from Cloud Manager  

1. Type a url that can be determined by adjusting the Author or Publish service urls as follows:
   ```  
   https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com
   ```  

1. As a shortcut, the following Cloud Manager CLI command can be used to launch the AEM as a Cloud Service Developer Console based on an environment parameter described below:    
   ```
   aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>
   ```
-->

## Conditions préalables {#prerequisites}

Developer Console n’est accessible que par les utilisateurs et utilisatrices bénéficiant de certains rôles dans certains programmes.

* Pour les programmes de production, le « Cloud Manager - Rôle de développeur » dans Adobe Admin Console contrôle l’accès au Developer Console.
* Pour les programmes Sandbox, tout utilisateur disposant d’un profil de produit accordant l’accès à AEM peut utiliser Developer Console.
* Pour tous les programmes, la mention « Cloud Manager - Rôle de développeur » est requise pour les vidages de statut et l’accès au navigateur de référentiel.

Pour afficher les données des services de création et de publication, les utilisateurs doivent également être affectés au « Profil de produit Utilisateurs AEM » ou « Profil de produit Administrateurs AEM » sur les deux services.

Pour plus d’informations sur la configuration des autorisations utilisateur, consultez la [Documentation de Cloud Manager.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/users-and-roles)

## Onglet Lots OSGi {#osgi-bundles}

L’onglet **Lots OSGi** donne un aperçu des lots OSGi déployés dans l’environnement sélectionné et permet d’effectuer une recherche de texte intégral.

![Nouvel écran des lots OSGi dans Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* Cet onglet fournit des informations sur l’état réel des lots dans l’environnement, telles que les packages exportés, les packages importés, les services utilisés, etc.
* Il est idéal de vérifier l’état des lots et de voir si le lot fait ce qu’il est censé faire.

**Exemple de cas d’utilisation :** supposons que vous spécifiiez une plage de versions pour une dépendance dans votre lot. Cependant, quelque chose ne fonctionne pas avec la dépendance et vous devez vérifier quelle version de la dépendance est réellement utilisée par le lot. Pour effectuer une vérification, ouvrez le Developer Console et cliquez sur le nom d’un lot dans l’onglet **Lots OSGi** pour accéder aux détails du lot, puis utilisez l’accordéon **Importer des lots** pour vérifier quelle version de lot ou version de package est utilisée au moment de l’exécution. Grâce à ces informations, vous pouvez ajuster votre plage de versions de dépendance Maven ou adapter votre code.

## Onglet Packages Java {#java-packages}

L’onglet **Packages Java** propose un champ de recherche pour rechercher les packages actifs dans le système OSGi de l’environnement.

![Onglet Packages Java dans l’interface utilisateur de Developer Console](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* Vous pouvez voir quelle offre groupée exporte (ou fournit) le package, et vous pouvez voir quelles offres groupées importent (ou utilisent) le package.
* Vous pouvez également vérifier les packages en double (même package, versions différentes), ce qui peut entraîner des problèmes dans certains cas.

**Exemple de cas d’utilisation :** supposons qu’un service personnalisé utilisant le [chargeur de classe dynamique](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html) charge une classe sans spécifier de version. Comme plusieurs lots exportent différentes versions, l’implémentation varie, ce qui entraîne des changements de comportement. Vous souhaitez vérifier quels packages se trouvent dans l’environnement sans analyser le modèle de fonctionnalité. Grâce à cet onglet, vous pouvez rechercher le package et afficher toutes les versions exportées, puis utiliser une meilleure plage de versions.

## Onglet Configurations {#configurations}

L’onglet **Configurations** propose une liste consultable des configurations actives dans l’environnement. Vous pouvez voir les propriétés fournies par chaque configuration en cliquant dessus et en affichant la page de détails.

![Onglet Configurations dans l’interface utilisateur de Developer Console](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* **Exemple de cas d’utilisation :** supposons que vous souhaitiez vous assurer que les configurations que vous avez spécifiées sont réellement présentes dans l’environnement. Si vous recherchez l’onglet **Configurations** dans la console et que la configuration est manquante, vous pouvez vérifier le modèle de fonctionnalité, le mode d’exécution de configuration ou le dossier.

## Onglet Servlets {#servlets}

L’onglet **Servlets** propose un champ de recherche dans lequel vous pouvez spécifier un chemin avec des sélecteurs et une extension avec GET ou POST. Elle fournit ensuite une liste des servlets, par ordre de préférence, qui gèrent la requête dans Sling.

![Onglet Servlets dans l’interface utilisateur de Developer Console](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

**Exemple de cas d’utilisation :** supposons que vous disposez d’un servlet OSGi qui doit s’activer lors d’une demande et imprimer la sortie dans la réponse. Cependant, au lieu de la sortie attendue, vous obtenez une réponse vide. Vous devez vérifier si un autre servlet est prioritaire sur votre servlet en raison de sélecteurs, de `resourceType`, d’extensions ou de classement plus spécifiques. Vous recherchez le chemin d’accès attendu et trouvez un autre servlet actif avec un rang supérieur. Vous pouvez ensuite décider d’augmenter le rang de votre servlet en ajoutant des sélecteurs, par exemple.

## Onglet Services {#services}

L’onglet **Services** donne un aperçu des services présents dans l’environnement sélectionné et permet d’effectuer une recherche de texte intégral.

![Onglet Services dans l’interface utilisateur de Developer Console](/help/implementing/developing/introduction/assets/services-dev-console.png)

Cliquez sur un service pour en afficher les détails.

## Onglet Composants OSGi {#osgi-components}

L’onglet **Composants OSGi** donne un aperçu des composants OSGi présents dans le type d’environnement sélectionné et permet d’effectuer une recherche de texte intégral. Vous pouvez voir l’état actif des composants OSGi dans l’environnement et les services qu’il satisfait, le lot qui le fournit et le type d’activation (immédiate ou différée).

![Onglet Composants OSGi dans l’interface utilisateur de Developer Console](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* **Exemple de cas d’utilisation 1 :** supposons que vous devez vérifier si un composant activé avec une configuration est actif dans un environnement spécifique, car vous rencontrez un comportement inattendu. Il vous suffit de rechercher le composant dans la recherche et de vérifier s’il est actif ou non.
* **Exemple de cas d’utilisation 2 :** supposons que vous souhaitiez voir quels composants prêts à l’emploi sont disponibles dans l’environnement et identifier les services qu’ils prennent en charge afin d’en savoir plus sur Adobe Experience Manager as a Cloud Service. Vous pouvez vérifier les composants dans la liste des composants.

## Onglet Intégrations {#integrations}

L’onglet **Intégrations** permet aux administrateurs de générer, de renommer et de supprimer des informations d’identification de service et des jetons de développement.

![Onglet Intégrations dans l’interface utilisateur de Developer Console](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

## Onglet Référentiel {#repository}

L’onglet **Référentiel** ouvre le [navigateur de référentiel.](/help/implementing/developing/tools/repository-browser.md)

## Onglet Vidages de statut/Requêtes {#status-dumps-queries}

L’onglet **Vidages de statut/requêtes** vous permet de télécharger un vidage de texte intégral ou JSON de l’état actuel des lots, des packages, des configurations, des services, des composants, des tâches Sling ou des définitions Oak.

![Onglet Vidages de statut/Requêtes dans l’interface utilisateur de Developer Console](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

Vous pouvez également ouvrir l’outil [Performances des requêtes](/help/operations/query-and-indexing-best-practices.md#query-performance-tool).

* **Exemple de cas d’utilisation :** cet onglet est particulièrement utile si vous rencontrez un état inattendu et que vous souhaitez le communiquer ou le documenter à d’autres développeurs et développeuses. Le téléchargement de l’image mémoire vous donne un instantané de l’état pour référence ultérieure.
