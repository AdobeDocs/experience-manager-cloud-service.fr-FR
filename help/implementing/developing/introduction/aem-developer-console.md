---
title: AEM AS A CLOUD SERVICE DEVELOPER CONSOLE - BETA
description: En savoir plus sur CRXDE Lite et AEM as a Cloud Service Developer Console.
feature: Developing
role: Admin, Developer
exl-id: 4b0fc3e9-b7c4-4c95-bd97-8b24e4d5cb3d
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 2%

---

# Developer Console AEM as a Cloud Service (Beta) {#developer-console}

>[!NOTE]
>
>Cet article décrit une expérience repensée pour AEM Cloud Service Developer Console, qui est désormais en version bêta. Certains clients peuvent y accéder en cliquant sur un bouton dans la partie supérieure de l’IU classique. Adobe vous invite à envoyer vos commentaires à `aemcs-new-devconsole-ui-beta@adobe.com`. Pour plus d’informations sur AEM Developer Console classique, consultez [cet article](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

AEM as a Cloud Service Developer Console comprend un ensemble d’outils pour le débogage dans les environnements cloud. Il est accessible via un lien spécifique à l’environnement dans Cloud Manager.

>[!NOTE]
>Le Developer Console AEM as a Cloud Service ne doit pas être confondu avec le Adobe Developer Console [*&#128279;*](https://developer.adobe.com/developer-console/).
>


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

Les développeurs peuvent accéder aux fonctionnalités décrites ci-dessous :

## Bundles OSGi {#osgi-bundles}

![Nouvel écran des lots OSGi dans la console de développement](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* Présentation des lots OSGI déployés dans le type d’environnement sélectionné. Elle permet d’effectuer une recherche de texte intégral.
* Il est utile d’obtenir des informations sur l’état réel des lots dans l’environnement. Vous pouvez obtenir des informations telles que les packages exportés, les packages importés, les services utilisés, etc.
* L’équipe de développement souhaite effectuer une vérification sur l’environnement réel et vérifier si le lot fonctionne comme prévu.
* **Exemple de cas d’utilisation :** une plage de versions d’une dépendance est spécifiée dans votre lot. Quelque chose ne fonctionne pas dans la dépendance. Vous souhaitez vérifier quelle version de la dépendance est connectée à votre lot. Pour vérifier, accédez aux détails du bundle et utilisez l’importation de bundles/packages pour vérifier quelle version de bundle ou version de package est utilisée au moment de l’exécution. Grâce à ces informations, vous pouvez ajuster votre plage de versions de dépendance Maven ou adapter votre code.

## Packages Java {#java-packages}

![Onglet Packages Java dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* Une invite de recherche que vous pouvez utiliser pour rechercher des packages actifs dans le système OSGI de l’environnement. À cet emplacement, vous pouvez voir le bundle qui exporte (ou fournit) le package, et vous pouvez voir quel bundle importe (ou utilise) le package. Vous pouvez également vérifier les packages en double (même package, versions différentes), ce qui peut entraîner des problèmes dans certains cas.
* **Exemple de cas d’utilisation :** un service personnalisé utilisant le [chargeur de classe dynamique](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html) charge une classe sans spécifier de version. Comme plusieurs lots exportent différentes versions, l’implémentation varie, ce qui entraîne des changements de comportement. Le développeur souhaite vérifier quels packages se trouvent dans l’environnement sans analyser le modèle de fonctionnalité. Ils recherchent le package et affichent toutes les versions exportées. Cette fonctionnalité leur donne les informations nécessaires pour entrer une meilleure plage de versions.

## Servlets {#servlets}

![Onglet Servlets dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

* Une invite de recherche dans laquelle vous pouvez spécifier un chemin avec des sélecteurs et une extension avec GET ou POST. Il fournit ensuite les résultats des servlets par ordre de préférence, ce qui gère la requête dans Sling.
* **Exemple de cas d’utilisation :** vous disposez d’un servlet OSGI qui doit s’activer lors d’une requête et imprimer la sortie dans la réponse. Cependant, au lieu de la sortie attendue, la réponse renvoie une valeur vide. Vous devez vérifier si un autre servlet est prioritaire sur votre servlet en raison de sélecteurs, de `resourceType`, d’extensions ou de classement plus spécifiques. Vous recherchez le chemin d’accès attendu et découvrez qu’un autre servlet est actif avec un rang supérieur. Ensuite, vous décidez si vous pouvez obtenir votre servlet ci-dessus au rang en ajoutant des sélecteurs, par exemple.

## Services {#services}

![Onglet Services dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/services-dev-console.png)

* Similaire à la vue Composants OSGI, mais basé sur les services. Vous pouvez rechercher rapidement les services fournis avec certaines propriétés.

## Composants OSGi {#osgi-components}

![Onglet Composants OSGi dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* Présentation des composants OSGI présents dans le type d’environnement sélectionné. Elle permet d’effectuer une recherche de texte intégral.
* Vous pouvez obtenir l’état actif des composants OSGI dans l’environnement . Vous pouvez voir quels services elle satisfait, le lot qui la fournit et le type d’activation (immédiate ou différée).
* **Exemple de cas d’utilisation 1 :** en tant que développeur ou développeuse, vous devez vérifier si un composant activé avec une configuration est actif dans un environnement spécifique. La raison en est que le comportement attendu ne se produit pas. Il vous suffit de rechercher le composant dans la recherche et de vérifier s’il est actif ou non.
* **Exemple de cas d’utilisation 2 :** vous souhaitez voir quels composants prêts à l’emploi sont disponibles dans l’environnement et identifier les services qu’ils prennent en charge. Cette fonctionnalité vous permet d’en savoir plus sur Adobe Experience Manager as a Cloud Service. Vous pouvez les extraire dans la liste des composants.

## Intégrations {#integrations}

![Onglet Intégrations dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

* Les administrateurs ont la possibilité de générer, renommer et supprimer des informations d’identification de service et des jetons de développement.

## Référentiel {#repository}

* Ouvre le [navigateur de référentiel](/help/implementing/developing/tools/repository-browser.md).

## Vidages de statut/requêtes {#status-dumps-queries}

![Onglet Vidages de statut/Requêtes dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

* Une image mémoire de texte intégral ou JSON de l’état actuel des lots, des packages, des configurations, des services, des composants, des tâches Sling ou des définitions Oak.
* Utile en particulier si le développeur a découvert un état inattendu et souhaite communiquer ou documenter cet état pour d’autres développeurs. Le téléchargement de l’image mémoire vous donne un instantané de l’état pour référence ultérieure.

## Configurations {#configurations}

![Onglet Configurations dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* Liste consultable des configurations actives dans l’environnement. Vous pouvez voir quelles propriétés sont fournies par les configurations en consultant la page de détails.
* **Exemple de cas d’utilisation :** un développeur souhaite s’assurer que les configurations qu’il a spécifiées sont réellement présentes dans l’environnement. Si la configuration fait défaut, ils peuvent vérifier le modèle de fonction ou le mode ou dossier d’exécution de la configuration.

Pour les programmes de production, la mention « Cloud Manager - Rôle de développeur » dans Adobe Admin Console contrôle l’accès à AEM as a Cloud Service Developer Console. Pour les programmes Sandbox, tout utilisateur disposant d’un profil de produit accordant l’accès à AEM peut utiliser Developer Console. Pour tous les programmes, la mention « Cloud Manager - Rôle de développeur » est requise pour les vidages de statut et l’accès au navigateur de référentiel. Pour afficher les données des services de création et de publication, les utilisateurs doivent également être affectés au profil de produit Utilisateurs AEM ou Administrateurs AEM sur les deux services.

Pour plus d’informations sur la configuration des autorisations des utilisateurs, voir [Documentation de Cloud Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-manager/content/requirements/users-and-roles).

