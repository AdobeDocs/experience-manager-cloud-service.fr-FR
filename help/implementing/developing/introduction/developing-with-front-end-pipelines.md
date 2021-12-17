---
title: Développement de sites avec le pipeline front-end
description: Avec le pipeline frontal, les développeurs front-end bénéficient d’une plus grande indépendance et le processus de développement peut gagner une vitesse substantielle.
source-git-commit: fd6a17a199b6cae03e91eba2ee938a03a326e612
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 0%

---


# Développement de sites avec le pipeline front-end {#developing-site-with-front-end-pipeline}

[Avec le pipeline front-end,](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) plus d’indépendance est donnée aux développeurs front-end et le processus de développement peut gagner une vitesse substantielle. Ce document décrit le fonctionnement de ce processus, ainsi que certaines considérations à prendre en compte pour tirer pleinement parti de ce processus.

>[!TIP]
>
>Si vous ne savez pas encore comment utiliser le pipeline front-end et quels en sont les avantages, consultez la page [Parcours de création de site rapide](/help/journey-sites/quick-site/overview.md) pour savoir comment déployer rapidement un nouveau site et personnaliser son thème indépendamment du développement principal.

## Source unique de vérité {#single-source-of-truth}

Une bonne pratique générale est de maintenir une source unique de vérité pour ce qui est déployé en AEM. L’objectif de Cloud Manager est de rendre cette source unique de vérité évidente. Cependant, comme le pipeline front-end permet de découpler l’emplacement de parties du code, une responsabilité supplémentaire incombe à la configuration correcte des pipelines front-end. Veillez à ne pas créer plusieurs pipelines front-end qui se déploient sur le même site sur le même environnement.

C’est pourquoi, et surtout lorsque plusieurs pipelines front-end sont créés, il est recommandé de respecter une convention d’affectation des noms systématique telle que :

* Nom du module front-end, défini par la variable `name` de la propriété `package.json` doit contenir le nom du site auquel il s’applique. Par exemple, pour un site situé à l’adresse `/content/wknd`, le nom du module front-end ressemblerait à `wknd-theme`.
* Lorsqu’un module front-end partage le même référentiel Git avec d’autres modules, le nom de son dossier doit être égal au module front-end ou contenir le même nom. Par exemple, si le module front-end est nommé `wknd-theme`, le nom du dossier englobant ressemblerait à `wknd-theme-sources`.
* Le nom du pipeline front-end de Cloud Manager doit également contenir le nom du module front-end et ajouter également l’environnement auquel il déploie (production ou développement). Par exemple, pour le module front-end nommé `wknd-theme`, le nom du pipeline peut être `wknd-theme-prod`.

Une telle convention devrait éviter efficacement les erreurs de déploiement suivantes :

* Application d’un module front-end au mauvais site
* Création de plusieurs modules front-end qui s’appliquent au même site, qui se remplaceraient les uns les autres
* Création de plusieurs pipelines front-end pour les mêmes sources, ce qui pourrait entraîner des conditions de concurrence, sans garantir l’ordre des déploiements

## Séparation des préoccupations {#separation-of-concerns}

Une autre bonne pratique qui s&#39;applique à toute séparation des préoccupations est de mettre une attention particulière dans la manière dont le contrat qui sépare les préoccupations est conçu et géré. Dans le cas du pipeline frontal, le contrat qui sépare ce code du reste est le HTML et le JSON rendus par le site. Si ce HTML et JSON restent stables, le pipeline front-end offre sa valeur maximale en rendant l’équipe front-end complètement indépendante.

Il n’existe actuellement aucune fonctionnalité spécifique pour exécuter le pipeline de pile complète de manière synchrone avec le ou les pipelines front-end. C’est pourquoi, lorsque vous découplez le développement front-end du pipeline full-stack, un soin supplémentaire doit être mis dans le contrat qui sépare ces deux domaines de préoccupation. Ce contrat correspond généralement au HTML et/ou au code JSON généré par Experience Manager. Les modifications apportées à ce contrat doivent donc être bien planifiées par les équipes qui exploitent les différents pipelines afin qu&#39;elles s&#39;entendent sur la séquence des modifications correspondantes.

Les étapes suivantes sont généralement recommandées lorsqu’il est nécessaire d’apporter des modifications au HTML et/ou à la sortie JSON qui affectent les deux domaines de préoccupation.

1. L’équipe principale configure d’abord un environnement de développement avec le nouveau HTML et/ou la sortie JSON.
   1. Par le biais du pipeline de pile complète, ils déploient le code requis pour effectuer le rendu du nouveau HTML et/ou de la sortie JSON souhaitée.
   1. S’il s’agit d’un environnement auquel l’équipe front-end n’avait pas auparavant accès, les étapes suivantes doivent être effectuées.
      1. URL : L’équipe front-end doit connaître l’URL de cet environnement de développement.
      1. ACL : L’équipe front-end doit disposer d’un utilisateur AEM local disposant de droits similaires à ceux des &quot;contributeurs&quot;.
      1. Git : L’équipe front-end doit disposer d’un emplacement Git distinct pour le module front-end qui cible spécifiquement cet environnement de développement.
         * Une pratique courante consiste à créer une `dev` afin que les modifications apportées à l’environnement de développement puissent être facilement fusionnées à nouveau dans la `main` branche à déployer dans l’environnement de production.
      1. Pipeline : L’équipe front-end doit disposer d’un pipeline front-end qui se déploie vers l’environnement de développement. Ce pipeline déployerait le module front-end qui se trouve généralement dans le `dev` , comme décrit dans le point précédent.
1. L’équipe front-end fait ensuite en sorte que le code CSS et JS fonctionne avec l’ancienne et la nouvelle sortie.
   1. Comme d&#39;habitude, pour se développer localement :
      1. Le `npx aem-site-theme-builder proxy` La commande exécutée dans le module front-end lance un serveur proxy qui demande le contenu à partir d’un environnement AEM, tout en remplaçant les fichiers CSS et JS du module front-end par ceux du module local `dist` dossier.
      1. Configuration de la variable `AEM_URL` dans la variable masquée `.env` permet de contrôler à partir de quel environnement AEM le serveur proxy local utilise le contenu.
      1. Modifier la valeur de ceci `AEM_URL` permet donc de basculer entre les environnements de production et de développement afin d’ajuster le CSS et JS de sorte qu’il s’adapte aux deux environnements.
      1. Il doit fonctionner avec l’environnement de développement qui effectue le rendu de la nouvelle sortie et avec l’environnement de production qui effectue le rendu de l’ancienne sortie.
   1. Le travail front-end est terminé lorsque le module front-end mis à jour fonctionne pour les deux environnements et est déployé sur les deux.
1. L’équipe principale peut ensuite mettre à jour l’environnement de production en déployant le code qui effectue le rendu du nouveau HTML et/ou de la sortie JSON via le pipeline de pile complète.
1. L’équipe principale peut ensuite nettoyer ses fichiers CSS et JS et supprimer les éléments qui n’étaient nécessaires que par l’ancienne sortie, en déployant cette dernière mise à jour en production via le pipeline frontal.

## Ressources supplémentaires {#additional-resources}

* [Thèmes du site](/help/sites-cloud/administering/site-creation/site-themes.md) - Découvrez comment AEM thèmes de site peuvent être utilisés pour personnaliser le style et la conception de votre site.
* [AEM Créateur de thèmes de site](https://github.com/adobe/aem-site-theme-builder) - Adobe fournit un Créateur de thèmes de site AEM sous la forme d’un ensemble de scripts pour la création de thèmes de site.
