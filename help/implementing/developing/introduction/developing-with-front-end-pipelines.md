---
title: Développement de sites avec le pipeline front-end
description: Le pipeline front-end améliore l’indépendance des développeurs et accélère le processus de développement. Cet article présente les points clés à prendre en compte pour le processus de création front-end afin d’assurer des performances et une efficacité optimales.
exl-id: 996fb39d-1bb1-4dda-a418-77cdf8b307c5
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 248c58c51864a2fead95064d30ea9f438f655eb6
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 28%

---


# Développement de sites avec le pipeline front-end {#developing-site-with-front-end-pipeline}

Le [pipeline front-end](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) donne aux développeurs front-end une plus grande indépendance et accélère considérablement le développement. Cet article explique le fonctionnement du processus et met en évidence les principales considérations pour vous aider à en tirer le meilleur parti.

>[!TIP]
>
>Si vous ne connaissez pas encore l’utilisation du pipeline front-end et ses avantages, consultez le guide [Parcours de création rapide de site](/help/journey-sites/quick-site/overview.md). Il fournit un exemple de déploiement rapide d’un nouveau site et de personnalisation de son thème indépendamment du développement back-end.

## Comprendre la configuration du pipeline front-end et le processus de création dans AEM Cloud Manager {#front-end-build-contract}

Tout comme l’[environnement de création full-stack](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md), le pipeline front-end possède son propre environnement. Les développeurs et développeuses disposent d’une certaine flexibilité avec ce pipeline, à condition de respecter le contrat de création front-end.

Le pipeline front-end nécessite que le projet front-end `Node.js` utilise la directive de script `build` pour générer la version qu’il déploie. Cette exigence existe, car Cloud Manager utilise le `npm run build` de commande pour générer le projet déployable pour la version front-end.

Le contenu obtenu du dossier `dist` est ce que Cloud Manager déploie finalement, les utilisant comme fichiers statiques. Ces fichiers sont hébergés en externe sur AEM, mais sont disponibles par le biais d’une URL `/content/...` dans l’environnement déployé.

## Versions de Node.js prises en charge {#node-versions}

L’environnement de création front-end prend en charge les versions `Node.js` suivantes :

* 23
* 22
* 20
* 18
* 16
* 14 (par défaut)
* 12

Vous pouvez utiliser la `NODE_VERSION` [variable d’environnement](/help/implementing/cloud-manager/environment-variables.md) pour définir la version souhaitée.

## Bonnes pratiques pour nommer et gérer les pipelines front-end dans AEM {#single-source-of-truth}

Une bonne pratique pour les déploiements d’AEM consiste à conserver une source de vérité unique et claire. Cloud Manager est conçu pour renforcer ce principe. Cependant, comme le pipeline front-end permet de découpler des parties du code, une configuration appropriée est essentielle. Pour éviter les conflits, assurez-vous que plusieurs pipelines front-end ne sont pas déployés sur le même site au sein du même environnement.

C’est pourquoi, en particulier lorsque plusieurs pipelines front-end sont créés, Adobe vous recommande de conserver une convention de nommage systématique. Vous pouvez utiliser les recommandations suivantes :

* Le nom du module front-end, défini par la propriété `name` du fichier `package.json`, doit contenir le nom du site auquel il s’applique. Par exemple, pour un site situé à l’adresse `/content/wknd`, le nom du module front-end se présente comme suit : `wknd-theme`.
* Lorsqu’un module front-end partage le même référentiel Git avec d’autres modules, le nom de son dossier doit être égal au module front-end ou contenir le même nom. Par exemple, si le module front-end est nommé `wknd-theme`, le nom du dossier englobant se présente comme suit : `wknd-theme-sources`.
* Le nom du pipeline front-end de Cloud Manager doit également contenir le nom du module front-end et ajouter également l’environnement auquel il déploie (production ou développement). Par exemple, pour le module front-end nommé `wknd-theme`, le nom du pipeline peut être `wknd-theme-prod`.

Une telle convention évite les erreurs de déploiement suivantes :

* Application d’un module front-end au mauvais site.
* Création de plusieurs modules front-end qui s’appliquent au même site, qui se remplaceraient les uns les autres.
* Création de plusieurs pipelines front-end pour les mêmes sources, ce qui pourrait entraîner des conditions de concurrence, sans garantir l’ordre des déploiements.

## Coordonner le développement front-end et back-end pour la stabilité dans AEM {#separation-of-concerns}

Une bonne pratique clé pour toute séparation des préoccupations est de concevoir et de gérer le contrat avec soin afin de définir les limites entre les deux. Dans le pipeline front-end, ce contrat correspond à la sortie HTML et JSON générée par le site. Le maintien de la stabilité de cette sortie garantit que le pipeline front-end offre une valeur maximale, ce qui permet à l’équipe front-end de travailler indépendamment.

Il n’existe actuellement aucune fonctionnalité intégrée pour exécuter le pipeline full stack de manière synchrone avec les pipelines front-end. Par conséquent, lors de la séparation du développement front-end du pipeline full-stack, il est essentiel de gérer soigneusement le contrat qui définit ses limites. Ce contrat se compose généralement de l’HTML ou du fichier JSON, ou des deux, rendus par Experience Manager. Toute modification de ce contrat doit être soigneusement coordonnée entre les équipes gérant différents pipelines afin d’assurer une transition fluide et un séquencement correct des mises à jour.

Les étapes suivantes sont généralement recommandées lorsque vous apportez des modifications à la sortie HTML ou JSON, en particulier lorsque les deux zones sont affectées.

1. L’équipe back-end configure d’abord un environnement de développement avec la nouvelle sortie HTML ou JSON.
   1. Par le biais du pipeline full stack, ils déploient le code nécessaire pour effectuer le rendu de la nouvelle sortie HTML ou JSON, ou des deux, selon le choix souhaité.
   1. S’il s’agit d’un environnement auquel l’équipe front-end n’avait pas auparavant accès, les étapes suivantes doivent être effectuées.
      1. URL : l’équipe front-end doit connaître l’URL de cet environnement de développement.
      1. ACL : l’équipe front-end doit disposer d’un utilisateur AEM local disposant de droits similaires à ceux des « Contributeurs ».
      1. Git : l’équipe front-end doit disposer d’un emplacement Git distinct pour le module front-end qui cible spécifiquement cet environnement de développement.

         Une pratique courante consiste à créer une branche `dev` pour gérer les modifications apportées à l’environnement de développement. Cette pratique permet de fusionner plus facilement dans la branche `main`, qui est utilisée pour le déploiement dans l’environnement de production.

      1. Pipeline : l’équipe front-end doit disposer d’un pipeline front-end qui se déploie vers l’environnement de développement. Ce pipeline déploierait le module front-end qui se trouve généralement dans la branche `dev`, comme décrit dans le point précédent.
1. L’équipe front-end fait ensuite en sorte que le code CSS et JS fonctionne avec l’ancienne et la nouvelle sortie.
   1. Comme d&#39;habitude, pour se développer localement, faire ce qui suit :
      1. La commande `npx aem-site-theme-builder proxy` démarre un serveur proxy permettant de récupérer du contenu d’un environnement AEM. Il remplace les fichiers CSS et JS du module front-end par ces fichiers du dossier `dist` local.
      1. La configuration de la variable `AEM_URL` dans le fichier `.env` masqué permet de contrôler à partir de quel environnement AEM le serveur proxy local consomme le contenu.
      1. La modification de la valeur de `AEM_URL` vous permet donc de basculer entre les environnements de production et de développement afin d’ajuster les CSS et JS de sorte qu’ils s’adaptent aux deux environnements.
      1. Il doit fonctionner à la fois avec l’environnement de développement qui effectue le rendu de la nouvelle sortie ainsi qu’avec l’environnement de production qui effectue le rendu de l’ancienne sortie.
   1. Le travail front-end est terminé lorsque le module front-end mis à jour fonctionne pour les deux environnements et est déployé sur les deux.
1. L’équipe back-end peut ensuite mettre à jour l’environnement de production en déployant le code qui effectue le rendu de la nouvelle sortie HTML ou JSON, ou des deux, au moyen du pipeline full-stack.
1. L’équipe front-end peut nettoyer ses CSS et JS, supprimer les éléments nécessaires uniquement à l’ancienne sortie et déployer la mise à jour finale en production à l’aide du pipeline front-end.

## Ressources supplémentaires {#additional-resources}

* Découvrez comment les thèmes de site AEM peuvent être utilisés pour personnaliser le style et la conception de votre site.

  Voir [Thèmes de site](/help/sites-cloud/administering/site-creation/site-themes.md).

* Adobe fournit un Créateur de thèmes de site AEM sous la forme d’un ensemble de scripts permettant de créer des thèmes de site.

  Voir [Créateur de thèmes de site AEM](https://github.com/adobe/aem-site-theme-builder).

