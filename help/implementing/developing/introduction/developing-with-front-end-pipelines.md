---
title: Développer des sites avec le pipeline front-end
description: Grâce au pipeline front-end, les développeurs et développeuses front-end bénéficient d’une plus grande indépendance et le processus de développement peut gagner considérablement en rapidité. Ce document décrit certains éléments particuliers du processus de création front-end qui doivent être pris en compte.
exl-id: 996fb39d-1bb1-4dda-a418-77cdf8b307c5
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1169'
ht-degree: 87%

---


# Développer des sites avec le pipeline front-end {#developing-site-with-front-end-pipeline}

[Grâce au pipeline front-end](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) les développeurs front-end bénéficient d’une plus grande indépendance et le processus de développement peut gagner considérablement en rapidité. Ce document décrit le fonctionnement de ce processus, ainsi que certaines considérations à prendre en compte pour tirer pleinement parti de ce processus.

>[!TIP]
>
>Si vous ne connaissez pas encore l’utilisation du pipeline front-end et les avantages qu’il peut apporter, consultez le [parcours de création rapide de site](/help/journey-sites/quick-site/overview.md) pour savoir comment déployer rapidement un nouveau site et personnaliser son thème de manière totalement indépendante du développement back-end.

## Contrat de création front-end {#front-end-build-contract}

Tout comme l’[environnement de création full-stack](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md), le pipeline front-end possède son propre environnement. Les développeurs et développeuses disposent d’une certaine flexibilité concernant l’utilisation de ce pipeline tant que le contrat de création front-end suivant est respecté.

Le pipeline front-end requiert le projet front-end Node.js pour utiliser la directive de script `build` afin de générer la version qu’il déploie. En effet, Cloud Manager utilise la `npm run build` de commande pour générer le projet déployable pour la version front-end.

Le contenu obtenu du dossier `dist` est ce qui est finalement déployé par Cloud Manager, les utilisant comme fichiers statiques. Ces fichiers sont hébergés en externe sur AEM, mais sont disponibles via une URL `/content/...` sur l’environnement déployé.

## Versions de Node {#node-versions}

L’environnement de création front-end prend en charge les versions de Node.js suivantes.

* 12
* 14 (par défaut)
* 16
* 18

Vous pouvez utiliser la `NODE_VERSION` [variable d’environnement](/help/implementing/cloud-manager/environment-variables.md) pour définir la version souhaitée.

## Source unique de vérité {#single-source-of-truth}

Une bonne pratique générale consiste à maintenir une source unique de vérité pour ce qui est déployé vers AEM. L’objectif de Cloud Manager est de rendre cette source unique de vérité évidente. Cependant, comme le pipeline front-end permet de découpler l’emplacement de certains éléments du code, une certaine responsabilité supplémentaire incombe à la configuration correcte des pipelines front-end. Veillez à ne pas créer plusieurs pipelines front-end qui se déploient sur le même site dans le même environnement.

C’est pourquoi, et surtout lorsque plusieurs pipelines front-end sont créés, il est recommandé de maintenir une convention de dénomination systématique telle que la suivante :

* Le nom du module front-end, défini par la propriété `name` du fichier `package.json`, doit contenir le nom du site auquel il s’applique. Par exemple, pour un site situé à l’adresse `/content/wknd`, le nom du module front-end se présente comme suit : `wknd-theme`.
* Lorsqu’un module front-end partage le même référentiel Git avec d’autres modules, le nom de son dossier doit être égal au module front-end ou contenir le même nom. Par exemple, si le module front-end est nommé `wknd-theme`, le nom du dossier englobant se présente comme suit : `wknd-theme-sources`.
* Le nom du pipeline front-end de Cloud Manager doit également contenir le nom du module front-end et ajouter également l’environnement auquel il déploie (production ou développement). Par exemple, pour le module front-end nommé `wknd-theme`, le nom du pipeline peut être `wknd-theme-prod`.

Une telle convention devrait éviter efficacement les erreurs de déploiement suivantes :

* Application d’un module front-end au mauvais site.
* Création de plusieurs modules front-end qui s’appliquent au même site, qui se remplaceraient les uns les autres.
* Création de plusieurs pipelines front-end pour les mêmes sources, ce qui pourrait entraîner des conditions de concurrence, sans garantir l’ordre des déploiements.

## Séparation des préoccupations {#separation-of-concerns}

Une autre bonne pratique qui s’applique à toute séparation des préoccupations est d’apporter une attention particulière à la manière dont le contrat qui sépare les préoccupations est conçu et géré. Dans le cas du pipeline front-end, le contrat qui sépare ce code du reste est le HTML et le JSON rendus par le site. Si ce HTML et JSON restent stables, le pipeline front-end offre sa valeur maximale en rendant l’équipe front-end totalement indépendante.

Il n’existe actuellement aucune fonctionnalité spécifique pour exécuter le pipeline de pile complète de manière synchrone avec le ou les pipelines front-end. C’est pourquoi, lorsque vous découplez le développement front-end du pipeline de pile complète, une attention particulière doit être apportée au contrat qui sépare ces deux domaines de préoccupation. Ce contrat correspond généralement au HTML et/ou au code JSON généré par Experience Manager. Les modifications apportées à ce contrat doivent donc être bien planifiées entre les équipes exploitant les différents pipelines afin qu’elles s’accordent sur la manière de séquencer les modifications correspondantes.

Les étapes suivantes sont généralement recommandées lorsqu’il est nécessaire d’apporter des modifications à la sortie HTML et/ou JSON ayant un impact sur les deux domaines de préoccupation.

1. L’équipe back-end configure d’abord un environnement de développement avec la nouvelle sortie HTML et/ou JSON.
   1. Par le biais du pipeline de pile complète, ils déploient le code nécessaire pour effectuer le rendu de la nouvelle sortie HTML et/ou JSON souhaitée.
   1. S’il s’agit d’un environnement auquel l’équipe front-end n’avait pas auparavant accès, les étapes suivantes doivent être effectuées.
      1. URL : l’équipe front-end doit connaître l’URL de cet environnement de développement.
      1. ACL : l’équipe front-end doit disposer d’un utilisateur AEM local disposant de droits similaires à ceux des « Contributeurs ».
      1. Git : l’équipe front-end doit disposer d’un emplacement Git distinct pour le module front-end qui cible spécifiquement cet environnement de développement.
         * Une pratique courante consiste à créer une branche `dev`, afin que les modifications apportées à l’environnement de développement puissent ensuite être facilement fusionnées dans la branche `main` à déployer dans l’environnement de production.
      1. Pipeline : l’équipe front-end doit disposer d’un pipeline front-end qui se déploie vers l’environnement de développement. Ce pipeline déploierait le module front-end qui se trouve généralement dans la branche `dev`, comme décrit dans le point précédent.
1. L’équipe front-end fait ensuite en sorte que le code CSS et JS fonctionne avec l’ancienne et la nouvelle sortie.
   1. Comme d’habitude, à développer localement :
      1. La commande `npx aem-site-theme-builder proxy` exécutée dans le module front-end démarre un serveur proxy permettant de demander le contenu d’un environnement AEM, tout en remplaçant les fichiers CSS et JS du module front-end par ceux du dossier local `dist`.
      1. La configuration de la variable `AEM_URL` dans le fichier caché `.env` permet de contrôler à partir de quel environnement AEM le serveur proxy local consomme le contenu.
      1. La modification de la valeur de l’`AEM_URL` permet donc de basculer entre les environnements de production et de développement, afin d’ajuster les CSS et JS de sorte qu’ils s’adaptent aux deux environnements.
      1. Il doit fonctionner à la fois avec l’environnement de développement qui effectue le rendu de la nouvelle sortie ainsi qu’avec l’environnement de production qui effectue le rendu de l’ancienne sortie.
   1. Le travail front-end est terminé lorsque le module front-end mis à jour fonctionne pour les deux environnements et est déployé sur les deux.
1. L’équipe back-end peut ensuite mettre à jour l’environnement de production en déployant le code qui effectue le rendu de la nouvelle sortie HTML et/ou JSON via le pipeline de pile complète.
1. L’équipe front-end peut alors nettoyer ses CSS et JS et supprimer les éléments uniquement nécessaires à l’ancienne sortie, en déployant cette dernière mise à jour vers la production via le pipeline front-end.

## Ressources supplémentaires {#additional-resources}

* [Thèmes de site](/help/sites-cloud/administering/site-creation/site-themes.md) - Découvrez comment les thèmes de site AEM peuvent être utilisés pour personnaliser le style et la conception de votre site.
* [AEM Créateur de thèmes de site](https://github.com/adobe/aem-site-theme-builder) - Adobe fournit un Créateur de thèmes de site AEM sous la forme d’un ensemble de scripts permettant de créer des thèmes de site.
