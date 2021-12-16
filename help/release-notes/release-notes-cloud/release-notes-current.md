---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 994ecec88f2724a75d9b11ba38c9c854a6983066
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 52%

---


# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle (2021.11.0) date du 16 décembre 2021.
La version suivante (2022.1.0) a été publiée le 27 janvier 2022.

## Vidéo de publication {#release-video}

Consultez la section [Présentation de la version de décembre 2021](https://video.tv.adobe.com/v/339278) vidéo pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Dynamic Media Image Smart Crop and Swatch est désormais optimisé par les derniers services Sensei, qui génèrent des recadrages et des échantillons améliorés. Une amélioration a également été lancée afin de générer un contenu de recadrage différent, pour les mêmes proportions mais avec des résolutions différentes. En outre, les modifications manuelles seront conservées lors du retraitement, si la largeur et la hauteur du profil d’image ne changent pas.

### Nouvelles fonctionnalités d’ [!DNL Assets] canal prerrelease {#assets-prerelease-features}

* [!DNL Dynamic Media] - Vous pouvez désormais utiliser AEM interface Dynamic Media pour configurer les paramètres généraux et la configuration de publication au lieu d’avoir à passer par l’application de bureau Dynamic Media Classic.

* [!DNL Dynamic Media] prend désormais en charge l’ingestion, la prévisualisation, la lecture et la publication pour les vidéos MXF. Les annotations et les vidéos Shoppable pour les vidéos MXF ne sont pas encore prises en charge.

* Après la configuration d’une connexion entre les déploiements DAM distant et Sites, les ressources sur DAM distant sont disponibles sur le déploiement Sites. Vous pouvez désormais effectuer des opérations de mise à jour, de suppression, de changement de nom et de déplacement sur des ressources ou des dossiers DAM distants. Les mises à jour, avec un certain délai, sont disponibles automatiquement sur le déploiement Sites .

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* **Portail Forms**: Vous pouvez utiliser [Portail Forms](/help/forms/configure-forms-portal.md) pour répertorier vos formulaires adaptatifs publiés sur une page AEM Sites. Cela permet à un visiteur du site de découvrir tous les formulaires disponibles. De plus, le visiteur peut utiliser le portail de formulaires pour enregistrer et accéder au brouillon d’un formulaire adaptatif et consulter la version PDF d’un formulaire adaptatif envoyé.

* **Externaliser les données des workflows AEM pour un traitement sécurisé** : vous pouvez stocker les données de workflows AEM (données de variables de workflows AEM) qui contiennent des éléments de données à caractère personnel dans un référentiel géré par le client pour un traitement sécurisé. Les éléments de données et les variables de workflows ne sont pas stockés dans le référentiel AEM et sont récupérés à la demande à partir d’un référentiel géré par le client lors du traitement du workflow.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API Communications](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) vous permettent de combiner un modèle et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents dans les modes synchrone et par lots. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   * Générer des documents en renseignant les fichiers de modèle (PDF et XDP) avec des données XML
   * Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs

* **Polices personnalisées pour les documents Document d’enregistrement et de PDF créés avec les API de communication**: Vous pouvez désormais utiliser des polices approuvées par la marque dans les documents PDF générés à l’aide des API de communication pour vous conformer aux exigences de votre organisation.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Extension des composants myAccount basés sur les composants Peregrine extensibles de Commerce

![Extension des composants myAccount](/help/assets/CIF/extended-myAccount-components.png)

* Les auteurs peuvent créer des Recommendations de produit Commerce ad hoc à l’aide de types de recommandations supplémentaires.

* Prise en charge des cartes-cadeaux dans AEM Storefront

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.11.0.

### Date de publication {#release-date-cm-nov}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.11.0 est le 04 novembre 2021.
La prochaine version est prévue pour le 09 décembre 2021.

### Nouveautés {#what-is-new-cm-nov}

* Les utilisateurs peuvent désormais tirer parti des nouveaux pipelines front-end pour déployer le code front-end exclusivement de manière accélérée. Voir [Pipelines front-end de Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) pour en savoir plus.

   >[!IMPORTANT]
   >Vous devez être sur AEM version `2021.10.5933.20211012T154732Z` pour tirer parti des nouveaux pipelines front-end.

* La durée du pipeline de qualité du code est considérablement réduite en exécutant l’analyse du code de manière plus efficace sans avoir à créer une image AEM entière. Cette modification sera déployée progressivement au cours des semaines qui suivront la version.

* L’ID d’enregistrement Git s’affiche désormais dans les détails d’exécution du pipeline, ce qui facilite le suivi du code créé.

* La création de programme est désormais disponible via l’API publiquement exposée.

* La création d’environnement est désormais disponible via l’API publiquement exposée.

* L’en-tête de réponse `x-request-id` est désormais visible dans le laboratoire de l’API sur [www.adobe.io](https://www.adobe.io/). Cet en-tête est utile pour signaler des problèmes à l’assistance clientèle à des fins de dépannage.

* En tant qu’utilisateur, je vois une carte Pipeline sans pipeline. Pouvez-vous me fournir des conseils appropriés ?

* Une nouvelle page d’activité est désormais disponible. Vous pouvez y afficher des activités telles que les exécutions de pipeline et de code, ainsi que les détails associés. Au fil du temps, les activités répertoriées dans cette page s’étendront, de même que les détails fournis.

* Une nouvelle page Pipelines avec une fenêtre contextuelle d’état et de survol permettant d’afficher facilement le résumé des détails est désormais disponible. Il est possible de visualiser les exécutions de pipelines avec les détails associés.

* L’API Modifier un pipeline prend désormais en charge la modification de l’environnement utilisé lors des phases de déploiement.

* Une optimisation du processus d’analyse OakPal a été introduite pour les modules volumineux.

* Le fichier CSV de problème de qualité contient désormais l’horodatage de chaque problème.

### Correctifs {#bug-fixes-nov}

* Certaines configurations de génération non orthodoxes entraînaient le stockage de fichiers inutiles dans le cache d’artefacts Maven du pipeline, ce qui entraînait des E/S réseau superflues lors du démarrage et de l’arrêt du conteneur de génération.

* L’API Pipeline PATCH échoue en l’absence de phase de déploiement.

* La règle de qualité `ClientlibProxyResourceCheck` générait des faux positifs en présence de bibliothèques clientes avec des chemins d’accès de base communs.

* Un message d’erreur indiquant que le nombre maximal de référentiels a été atteint ne précisait pas la raison de l’erreur.

* Dans de rares cas, les pipelines échouaient en raison d’une gestion inappropriée des reprises de certains codes de réponse.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.2 de l’analyseur des bonnes pratiques est le 1er décembre 2021.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur la version d’ACS commons utilisée.
* Possibilité de détecter et de générer des rapports sur le nombre d’utilisateurs et de sous-groupes d’un groupe.
* Possibilité de détecter et de générer des rapports sur les valeurs de propriété de noeud dans MongoDB dépassant 16 Mo.

### Correctifs {#bug-fixes-bpa}

* La détection des composants Foundation a été améliorée afin de réduire les faux négatifs.
* Pour les clients AEM Forms, message BPA concernant `EMAIL_PDF_SUBMIT_ACTION` n’étant pas disponible sur AEM as a Cloud Service a été corrigé.
