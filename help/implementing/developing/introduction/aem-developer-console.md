---
title: Developer Console AEM as a Cloud Service (Bêta)
description: En savoir plus sur CRX/DE Lite et AEM as a Cloud Service Developer Console
feature: Developing
role: Admin, Architect, Developer
source-git-commit: efff267b714c7ebb3a8b547da5b720ec7eca2f48
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 7%

---


# Developer Console AEM as a Cloud Service (Bêta) {#developer-console}

>[!NOTE]
>
>Cet article décrit une expérience repensée pour AEM Cloud Service Developer Console, qui est désormais en version bêta, et disponible pour certains clients en cliquant sur un bouton dans la partie supérieure de l’IU classique. Nous apprécions tout commentaire que vous pouvez envoyer à `aemcs-new-devconsole-ui-beta@adobe.com`. Pour plus d’informations sur Developer Console AEM classique, voir [cet article](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console).

AEM as a Cloud Service Developer Console comprend un ensemble d’outils pour le débogage dans les environnements cloud. Il est accessible par le biais d’un lien par environnement dans Cloud Manager.

>[!NOTE]
>AEM as a Cloud Service Developer Console ne doit pas être confondu avec le [*Adobe Developer Console*](https://developer.adobe.com/developer-console/) du même nom.
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

![Nouvel écran de lots OSGi dans la console de développement](/help/implementing/developing/introduction/assets/osgi-bundles.png)

* Vous obtenez ainsi un aperçu des lots OSGI qui sont déployés sur le type d’environnement sélectionné. Elle active une recherche de texte intégral.
* Il est utile d’obtenir des informations sur l’état réel des lots dans l’environnement. Vous pouvez obtenir des informations telles que les packages exportés, les packages importés, les services utilisés, etc.
* Les développeurs veulent vérifier sur l’environnement réel et vérifier si le lot fait ce qu’ils attendent de lui.
* **Exemple de cas d’utilisation :** Une plage de versions d’une dépendance est spécifiée dans votre lot. Quelque chose ne va pas dans la dépendance. Vous souhaitez vérifier quelle version de la dépendance est connectée à votre lot. Pour vérifier cela, accédez aux détails du lot et utilisez l’importation de bundles / packages pour vérifier la version du lot ou de la version du package utilisée au moment de l’exécution pour le savoir. Grâce à ces informations, vous pouvez ajuster la plage de versions de votre dépendance Maven ou adapter votre code.

## Packages Java {#java-packages}

![Onglet Packages Java dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/java-packages-dev-console-ui.png)

* Vous pouvez ainsi utiliser une invite de recherche pour rechercher les modules actifs dans le système OSGI de l’environnement. Dans cet emplacement, vous pouvez voir quel lot exporte (ou fournit) le package, et vous pouvez voir quel lot importe (ou utilise) le package. Vous pouvez également rechercher des packages en double (même package, différentes versions), ce qui peut entraîner des problèmes dans certains cas.
* **Exemple de cas d’utilisation :** Un service personnalisé qui utilise le [chargeur de classe dynamique](https://sling.apache.org/apidocs/sling9/org/apache/sling/commons/classloader/DynamicClassLoaderManager.html) charge une classe sans spécifier de version, qui est exportée par plusieurs lots avec des versions différentes, ce qui entraîne la différence de l’implémentation et le changement de comportement. Le développeur souhaite savoir quels packages se trouvent dans l’environnement sans analyser le modèle de fonctionnalité. Il recherche donc ce package et voit toutes les versions exportées. Ils disposent ainsi des informations nécessaires pour entrer dans une meilleure plage de versions.

## Servlets {#servlets}

![Onglet Servlets dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/servlets-dev-console-ui.png)

* Vous pouvez ainsi spécifier un chemin avec des sélecteurs et une extension avec un GET ou un POST à l’aide d’une invite de recherche. Il fournit ensuite les résultats des servlets par ordre de préférence qui gérera la requête dans Sling.
* **Exemple de cas d’utilisation :** Vous disposez d’une servlet OSGI qui doit être activée sur une requête et qui doit imprimer quelque chose dans la réponse, mais vous obtenez une réponse vide à la place. Vous devez vérifier si une autre servlet a priorité sur votre servlet en raison de sélecteurs plus spécifiques, `resourceType`, d’extensions ou de classement. Vous recherchez le chemin attendu et découvrez qu’une autre servlet est active avec un rang supérieur. Ensuite, vous décidez si vous pouvez obtenir le classement de votre servlet en ajoutant des sélecteurs, par exemple.

## Services {#services}

![Onglet Services dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/services-dev-console.png)

* Similaire à la vue Composants OSGI, mais en fonction des services. Vous pouvez rechercher rapidement les services fournis avec certaines propriétés.

## Composants OSGi {#osgi-components}

![Onglet Composants OSGi dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/osgi-components-dev-console.png)

* Vous obtenez ainsi un aperçu des composants OSGI présents dans le type d’environnement sélectionné. Elle active une recherche de texte intégral.
* Vous pouvez obtenir l’état actif des composants OSGI dans l’environnement. Vous pouvez voir quels services elle satisfait, le lot qui le fournit et le type d’activation (immédiat ou retardé).
* **Exemple d’utilisation 1 :** En tant que développeur, vous souhaitez vérifier si un composant activé avec une configuration est actif ou non dans un environnement particulier, car vous n’obtenez pas le comportement attendu. Il vous suffit de rechercher le composant dans la recherche et de vérifier s’il est actif ou non.
* **Exemple d’utilisation 2 :** Vous souhaitez savoir quels composants prêts à l’emploi sont présents dans l’environnement et quels services ils satisfont pour en savoir plus sur Adobe Experience Manager as a Cloud Service. Vous pouvez les extraire dans la liste des composants.

## Intégrations {#integrations}

![Onglet Intégrations dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/integrations-dev-console-ui.png)

* Permet aux administrateurs de générer, renommer et supprimer des informations d’identification de service et des jetons de développeur.

## Référentiel {#repository}

* Ouvre le [navigateur de référentiel](/help/implementing/developing/tools/repository-browser.md).

## Images mémoire/requêtes d’état {#status-dumps-queries}

![Onglet Images d’état / Requêtes dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/status-dumps-queries.png)

* Donne un texte intégral ou une image mémoire JSON de l’état actuel des bundles, packages, configurations, services, composants, tâches Sling ou définitions Oak.
* Cela peut s’avérer utile, en particulier si le développeur a découvert un état inattendu et souhaite communiquer ou documenter cela pour d’autres développeurs. Le téléchargement du vidage vous donne un instantané de l’état à des fins de référence ultérieure.

## Configurations {#configurations}

![Onglet Configurations dans l’interface utilisateur de la console de développement](/help/implementing/developing/introduction/assets/configurations-dev-console.png)

* Vous obtenez ainsi une liste consultable des configurations actives dans l’environnement. Vous pouvez voir quelles propriétés sont fournies par les configurations en consultant la page des détails.
* **Exemple de cas d’utilisation :** Un développeur veut s’assurer que les configurations qu’il a spécifiées sont réellement présentes dans l’environnement. Si la configuration est manquante, ils peuvent vérifier le modèle de fonctionnalité ou le mode d’exécution ou le dossier de configuration.

Pour les programmes de production, l’accès à AEM as a Cloud Service Developer Console est défini par &quot;Cloud Manager - Rôle de développeur&quot; dans Adobe Admin Console, tandis que pour les programmes Sandbox, AEM as a Cloud Service Developer Console est disponible pour tout utilisateur disposant d’un profil de produit lui donnant accès à AEM as a Cloud Service. Pour tous les programmes, « Cloud Manager – Rôle de développement » est nécessaire pour les vidages de statut et le navigateur de référentiels. Les utilisateurs et les utilisatrices doivent également être définis dans le profil de produit Utilisateurs et utilisatrices d’AEM ou Administrateurs et administratrices d’AEM sur les services de création et de publication pour afficher les données des deux services. Pour plus d’informations sur la configuration des autorisations des utilisateurs, voir [Documentation de Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=fr).