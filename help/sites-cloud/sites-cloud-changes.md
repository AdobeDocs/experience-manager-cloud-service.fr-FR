---
title: Modifications notables des sites AEM dans le service AEM Cloud
description: 'Modifications notables des sites AEM dans le service AEM Cloud '
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Modifications notables des sites AEM en tant que service Cloud {#notable-changes}

Les sites AEM en tant que service Cloud offrent des fonctionnalités de gestion d’expérience dans le cadre d’AEM natif au cloud en tant que plateforme de service Cloud. Outre les principaux avantages d’AEM en tant que service Cloud, tels que l’évolutivité native du cloud, le temps de disponibilité et la mise à jour permanente d’AEM Sites en tant que service Cloud, vous pouvez également apporter un certain nombre de modifications et d’ajouts propres aux sites.

>[!NOTE]
>Ce document met en évidence les modifications notables apportées aux sites AEM. Pour les modifications générales d’AEM dans le Cloud, voir :
>
>* [Modifications notables d’Adobe Experience Manager (AEM) en tant que service Cloud](/help/release-notes/aem-cloud-changes.md)


Les modifications et ajouts dans les sites AEM en tant que service Cloud sont les suivants :

* [Opérations de page asynchrones](#asynchronous-page-operations)
* [Nouveau site de référence et didacticiel](#new-reference-site-and-tutorial)

## Opérations de page asynchrones {#asynchronous-page-operations}

Dans le service AEM Cloud, les opérations qui ont traditionnellement bloqué l’interface utilisateur ont été ventilées en tâches plus petites qui s’exécutent en arrière-plan.

* Déplacer des pages
* Pages de déploiement

L’initiateur de telles actions peut vérifier leur état dans une nouvelle interface utilisateur à `/mnt/overlay/dam/gui/content/asyncjobs.html`.

>[!NOTE]
>
>L’utilisateur du système n’a pas besoin de modifier cette nouvelle fonctionnalité pour pouvoir l’utiliser. Il est simplement noté ici comme un changement de comportement par rapport aux versions sur site précédentes d’AEM.

## Nouveau site de référence et didacticiel {#new-reference-site-and-tutorial}

[WKND](https://wknd.site/), un nouveau site de référence AEM, a été mis à jour et publié afin de refléter les meilleures pratiques de création d’un site Web avec AEM, ainsi que l’ensemble complet des fonctionnalités, composants et modèles de déploiement disponibles dans AEM. Le nouveau site de référence et le didacticiel [](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) qui l’accompagne abordent des sujets fondamentaux tels que la configuration de projet, les composants principaux, les modèles modifiables, les bibliothèques client et le développement de composants avec les sites Adobe Experience Manager.

Auparavant, We.Retail était installé par défaut avec AEM (sauf lorsqu’il était démarré en mode de production).  Désormais, aucun site de référence ne sera installé par défaut.  Au lieu de cela, vous trouverez le didacticiel [git repo](https://github.com/adobe/aem-guides-wknd/) et [le didacticiel](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) associé au code du site de référence WKND mis à jour.

## Fonctionnalités non disponibles à l’exécution {#capabilities-not-available-at-runtime}

AEM en tant que service Cloud est toujours activé et toujours à jour. Pour y parvenir, il faut séparer le référentiel AEM du contenu immuable et mutable et interdire l’accès au contenu immuable au moment de l’exécution. Pour plus d&#39;informations sur le contenu mutable ou immuable, reportez-vous à la section Zones [mutables ou immuables du référentiel](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable).

Du fait que le contenu immuable est inaccessible au moment de l’exécution, les opérations de sites AEM suivantes ne sont pas disponibles au moment de l’exécution :

* Traduction du dictionnaire i18n
* Mode développeur dans l’éditeur de page des sites AEM

Ces fonctionnalités peuvent être utilisées par le biais d’instances de développement locales autonomes d’AEM en tant que service Cloud, pour la mise à jour du contenu et du code dans AEM en tant que référentiel GIT de service Cloud, mais pas dans les instances d’exécution hébergées.
