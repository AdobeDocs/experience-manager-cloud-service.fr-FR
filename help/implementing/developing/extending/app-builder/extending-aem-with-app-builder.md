---
title: Extension d’ [!DNL Adobe Experience Manager]  as a Cloud Service à l’aide d’Adobe Developer App Builder.
description: Extension d’ [!DNL Adobe Experience Manager] as a Cloud Service à l’aide d’Adobe Developer App Builder.
exl-id: 50d82745-5deb-4bfa-961b-714842403601
source-git-commit: 430179bf13c1fff077c515eed0676430e9e7f341
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 99%

---

# Extension d’[!DNL Adobe Experience Manager] as a Cloud Service à l’aide d’Adobe Developer App Builder {#extend-using-app-builder}

## Présentation de l’App Builder pour AEM as a Cloud Service {#project-firefly}

Le nouveau développeur d’applications Adobe fournit un framework permettant aux développeurs d’étendre facilement les fonctionnalités d’AEM as a Cloud Service.

L’App Builder fournit une structure tierce unifiée pour l’intégration et la création d’expériences personnalisées pour étendre Adobe Experience Manager. Grâce à ce framework d’extensibilité complet reposant sur l’infrastructure d’Adobe, les développeurs peuvent créer des microservices personnalisés, étendre et intégrer Adobe Experience Manager à travers les solutions d’Adobe et le reste de la pile informatique.

L’App Builder permet aux clients d’étendre facilement les capacités d’Adobe Experience Manager à divers cas d’utilisation :

* Extensibilité des middleware : connectez des systèmes externes à des applications Adobe qui créent des connecteurs personnalisés, ou exploitez la suite d’intégrations préconfigurées.
* Extensibilité des services principaux : étendez les fonctionnalités de l’application principale en étendant le comportement par défaut grâce à des fonctionnalités personnalisées et à la logique métier.
* Extensibilité de l’expérience utilisateur : étendez l’expérience principale pour prendre en charge les besoins de l’entreprise ou créer des propriétés numériques et des applications storefronts et back-office spécifiques aux clients.

Depuis l’été 2020, l’App Builder (précédemment « Project Firefly ») est disponible pour les clients et les partenaires d’entreprise via notre Aperçu du développeur. La disponibilité générale de l’App Builder est prévue pour décembre 2021. Nous invitons les développeurs à tester l’App Builder via notre [Programme d’évaluation](https://adobe.ly/appbuilder-trial).

>[!NOTE]
>
> Pour les clients AEM 6.5 qui souhaitent utiliser le générateur d’applications, accédez à [Extension d’Adobe Experience Manager 6.5 à l’aide d’Adobe Developer App Builder](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/app-builder.html?lang=fr).

## Architecture {#architecture}

Au lieu d’une solution prête à l’emploi, Adobe Developer App Builder fournit une plateforme de développement commune, cohérente et normalisée permettant d’étendre les solutions cloud Adobe telles qu’AEM, parmi les suivantes :

* Adobe Developer Console : pour le développement de microservices et d’extensions personnalisés, permet aux développeurs de créer et de gérer des projets tout en accédant à tous les outils et API dont ils ont besoin pour créer des modules externes et des intégrations.
* Outils de développement : outils Open Source, SDK et bibliothèques permettant aux développeurs de créer facilement des extensions et des intégrations personnalisées. Utilisez React Spectrum (dans la boîte à outils de l’interface utilisateur d’Adobe) pour disposer d’une interface utilisateur commune à toutes les applications d’Adobe.
* Services : E/S d’exécution pour l’hébergement de l’infrastructure sur notre plateforme sans serveur et événements d’E/S pour les intégrations basées sur des événements. Nous fournissons également une prise en charge prête à l’emploi pour le stockage des données et des fichiers.
* Adobe Experience Cloud : les développeurs peuvent soumettre des extensions et des intégrations à publier dans leur organisation Experience Cloud. Les administrateurs système peuvent ensuite examiner, gérer et approuver ces extensions. Une fois la publication effectuée, vos extensions et outils App Builder personnalisés se trouvent aux côtés d’autres applications Adobe Experience Cloud.

Le diagramme suivant illustre la manière dont une application standard créée sur l’App Builder tire parti de ces fonctionnalités :

![Architecture](/help/implementing/developing/extending/assets/firefly-architecture.jpg)

Pour plus d’informations sur l’architecture de l’App Builder, reportez-vous à la section [Présentation de l’architecture](https://www.adobe.io/app-builder/docs/guides/).

## Prise en main de l’App Builder {#additional-resources}

Pour vous aider à prendre en main l’App Builder, nous avons créé une série de documents pour prendre un bon départ :

* [Prise en main de l’App Builder](https://www.adobe.io/app-builder/docs/getting_started/)

## Poursuivre l’apprentissage avec la documentation {#appbuilder-documentation}

L’App Builder fournit des vidéos et de la documentation à l’intention des développeurs, notamment des guides et une documentation de référence pour vous aider à commencer à développer vos propres applications personnalisées :

* [Documentation de l’App Builder](https://www.adobe.io/app-builder/docs/overview/)
* [Vidéos sur l’App Builder](https://www.youtube.com/playlist?list=PLcVEYUqU7VRfDij-Jbjyw8S8EzW073F_o)

## Essayez un des exemples d’application. {#appbuilder-codesamples}

Prêts à développer ? Nous avons de nombreux exemples d’applications pour vous aider à démarrer rapidement :

* [Laboratoires de code de l’App Builder sur le site web du développeur d’Adobe](https://www.adobe.io/app-builder/docs/resources/)

## Assistance {#support}

Pour les demandes de prise en charge des développeurs, nous encourageons les développeurs à utiliser notre [Forum Experience League](https://experienceleaguecommunities.adobe.com/t5/app-builder/ct-p/project-firefly?profile.language=fr).
