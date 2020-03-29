---
title: Découvrez comment les microservices de ressources peuvent traiter vos ressources numériques dans le cloud
description: Traitez vos ressources numériques à l’aide de microservices de traitement des ressources natifs et évolutifs en mode cloud.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 68b2214a4c8941365120bdef670e89b4c9058966

---


# Présentation de l’assimilation et du traitement des ressources à l’aide des microservices de ressources {#asset-microservices-overview}

<!--
First half of content at https://git.corp.adobe.com/aklimets/project-nui/blob/master/docs/Project-Nui-Asset-Compute-Service.md is useful for this article.
TBD: Post-GA we will provide detailed information at \help\assets\asset-microservices-configure-and-use.md. However, for GA, all information is added, in short, in this article.
-->

Adobe Experience Manager en tant que service Cloud offre un moyen natif du cloud d’exploiter les applications et les fonctionnalités d’Experience Manager. L&#39;un des éléments clés de cette nouvelle architecture est l&#39;assimilation et le traitement des ressources, alimentés par les microservices de ressources.

Les microservices de ressources offrent un traitement évolutif et résilient des ressources à l’aide des services cloud, qui sont gérés par Adobe pour une gestion optimale des différents types de ressources et des différentes options de traitement. Les principaux avantages sont les suivants :

* Architecture évolutive qui permet un traitement transparent pour les opérations gourmandes en ressources.
* L’indexation et le texte efficaces  les  qui n’affectent pas les performances de votre  Experience Manager.
* Réduisez la nécessité pour les de gérer le traitement des ressources dans le  d’Experience Manager. Cela libère des ressources, réduit la charge sur Experience Manager et offre une évolutivité.
* Amélioration de la résilience du traitement des ressources. Les problèmes potentiels liés à la gestion de fichiers atypiques, tels que des fichiers corrompus ou des fichiers extrêmement volumineux, n’affectent plus les performances du déploiement.
* Configuration simplifiée du traitement des ressources pour les administrateurs.
* La configuration du traitement des ressources est gérée et gérée par Adobe afin de fournir la configuration la plus connue pour la gestion des rendus, des métadonnées et des  texte  pour divers types de fichiers
* Les services natifs de traitement de fichiers Adobe sont utilisés le cas échéant, ce qui permet une sortie haute fidélité et une gestion [efficace des formats](file-format-support.md)propriétaires Adobe.
* Possibilité de configurer le processus de post-traitement pour ajouter des actions et des intégrations spécifiques à l’utilisateur.

Les microservices de ressources permettent d’éviter la nécessité d’outils de rendu tiers (tels que ImageMagick) et de simplifier la configuration du système, tout en fournissant des fonctionnalités prêtes à l’emploi pour les types de fichiers courants.

## Architecture de haut niveau {#asset-microservices-architecture}

Un diagramme d’architecture de haut niveau décrit les éléments clés de l’assimilation et du traitement des actifs et du flux des actifs dans l’ensemble du système.

<!-- Proposed DRAFT diagram for asset microservices overview - see section "Asset processing - high-level diagram" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Importation et traitement des ressources avec](assets/asset-microservices-overview.png "des microservices de ressourcesImportation et traitement des ressources avec des microservices de ressources")

Les étapes clés de l’assimilation et du traitement à l’aide des microservices de ressources sont les suivantes :

* Les clients, tels que les navigateurs Web ou Adobe Asset Link, envoient une demande de téléchargement vers Experience Manager et les  le téléchargement direct du fichier binaire vers le  binaire cloud .
* Une fois le transfert binaire direct terminé, le client en informe Experience Manager.
* Experience Manager envoie une demande de traitement aux microservices de ressources. Le contenu de la requête dépend de la configuration du de traitement dans Experience Manager qui indique quels rendus doivent être générés.
* Le serveur principal des microservices de ressources reçoit la demande, la distribue à un ou plusieurs microservices en fonction de la demande. Chaque microservice accède directement au fichier binaire d’origine depuis le magasin de nuages binaires.
* Les résultats du traitement, tels que les rendus, sont stockés dans le cloud binaire  le.
* Experience Manager est averti que le traitement est terminé avec des pointeurs directs vers les binaires générés (rendus), qui sont ensuite disponibles dans Experience Manager pour la ressource téléchargée

C&#39;est le flux de base de l&#39;assimilation et du traitement des actifs. S’il est configuré, Experience Manager peut également le modèle de flux de travail du client à effectuer le post-traitement de la ressource, par exemple, pour exécuter certaines étapes personnalisées spécifiques à l’ client, comme la récupération des informations des systèmes d’entreprise du client à ajouter aux propriétés de la ressource.

Le flux d’assimilation et de traitement sont des concepts clés de l’architecture des microservices de ressources pour Experience Manager.

* **Accès** binaire direct : Les ressources sont transportées (et téléchargées) vers le magasin binaire Cloud une fois configurées pour Experience Manager  les , puis AEM, les microservices de ressources et enfin les clients ont un accès direct à ces ressources pour accomplir leur travail. Cela réduit la charge sur les réseaux et la duplication des binaires stockés
* **Traitement** externe : Le traitement des ressources s’effectue en dehors du  AEM  et enregistre ses ressources (processeur, mémoire) pour fournir des fonctionnalités clés de gestion des ressources numériques et prendre en charge le travail interactif avec le système pour les utilisateurs finaux.

## Transfert de ressources avec accès binaire direct {#asset-upload-with-direct-binary-access}

Les clients Experience Manager, qui font partie de l’offre de produit, prennent tous en charge le téléchargement avec un accès binaire direct par défaut. Il s’agit notamment du téléchargement à l’aide de l’interface Web, d’Adobe Asset Link et de l’application de bureau AEM.

Vous pouvez utiliser des outils de téléchargement personnalisés, qui fonctionnent directement avec les API HTTP AEM. Vous pouvez utiliser ces API directement ou utiliser et étendre les projets open source suivants qui implémentent le protocole de transfert :

* [Bibliothèque de transfert Open Source](https://github.com/adobe/aem-upload)
* [Outil de ligne de commande Open Source](https://github.com/adobe/aio-cli-plugin-aem)

For more information, see [upload assets](add-assets.md).

## Ajouter post-traitement personnalisé des ressources {#add-custom-asset-post-processing}

Bien que la plupart des clients doivent obtenir tous leurs besoins de traitement des ressources des microservices de ressources configurables, certains peuvent avoir besoin d’un traitement supplémentaire des ressources. Cela est particulièrement vrai si les actifs doivent être traités en fonction des informations provenant d’autres systèmes via des intégrations. Dans de tels cas, vous pouvez utiliser des  de post-traitement personnalisées.

Les  de post-traitement sont des modèles de flux de travaux AEM standard, créés et gérés dans l’éditeur de flux de travaux AEM. Les clients peuvent configurer le pour effectuer d’autres étapes de traitement sur un fichier, y compris l’utilisation des étapes de flux de travail prêtes à l’emploi et des  personnalisées.

Adobe Experience Manager peut être configuré pour déclencher automatiquement le de post-traitement une fois le traitement des ressources terminé.

<!-- TBD asgupta, Engg: Create some asset-microservices-data-flow-diagram.
-->

>[!MORELIKETHIS]
>
>* [Prise en main des microservices de ressources](asset-microservices-configure-and-use.md)
>* [Formats de fichiers pris en charge](file-format-support.md)
>* [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Application de bureau AEM](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html)
>* [Documentation Apache Oak sur l’accès binaire direct](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html)

