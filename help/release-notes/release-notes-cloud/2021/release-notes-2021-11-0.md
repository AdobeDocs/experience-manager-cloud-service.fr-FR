---
title: Notes de mise à jour de la version 2021.11.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2021.11.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 86f8ddd1-af51-4874-9111-0935b5a162c1
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 94%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2021.11.0) de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 16 décembre 2021.
La version suivante (2022.1.0) sera publié le 3 février 2022.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo [Présentation de la version de décembre 2021](https://video.tv.adobe.com/v/339278) pour un résumé des fonctionnalités ajoutées dans la version 2021.11.0 (novembre 2021).

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Le recadrage et l’échantillon intelligents d’images Dynamic Media s’appuient désormais sur les derniers services d’IA d’Adobe, qui génèrent des recadrages et des échantillons améliorés. Une amélioration a également été lancée afin de générer un contenu de recadrage différent, pour les mêmes proportions mais avec des résolutions différentes. En outre, les modifications manuelles sont conservées lors du retraitement, si la largeur et la hauteur du profil d’image ne changent pas.

### Nouvelles fonctionnalités dans le [!DNL Assets] canal de version préliminaire {#assets-prerelease-features}

* [!DNL Dynamic Media] - Vous pouvez désormais utiliser l’interface AEM Dynamic Media pour configurer les paramètres généraux et la configuration de publication au lieu d’avoir à passer par l’application de bureau Dynamic Media Classic.

* [!DNL Dynamic Media] prend désormais en charge l’ingestion, la prévisualisation, la lecture et la publication des vidéos MXF. L’annotation et la shoppable vidéo pour les vidéos MXF ne sont pas encore prises en charge.

* Après la configuration d’une connexion entre les déploiements DAM distant et Sites, les ressources du DAM distant sont disponibles sur le déploiement de Sites. Vous pouvez désormais effectuer les opérations suivantes : [mettre à jour, supprimer, renommer et déplacer des opérations](/help/assets/use-assets-across-connected-assets-instances.md) sur les ressources ou dossiers du DAM distant. Les mises à jour, avec un certain retard, sont disponibles automatiquement sur le déploiement Sites.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* **Externaliser les données des workflows AEM pour un traitement sécurisé** : vous pouvez stocker les données de workflows AEM (données de variables de workflows AEM) qui contiennent des éléments de données à caractère personnel dans un référentiel géré par le client pour un traitement sécurisé. Les éléments de données et les variables de workflows ne sont pas stockés dans le référentiel AEM et sont récupérés à la demande à partir d’un référentiel géré par le client lors du traitement du workflow.

### Nouvelles fonctionnalités disponibles dans le [!DNL Forms] canal de version préliminaire {#prerelease-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API Communications](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html?lang=fr) vous permettent de combiner un modèle et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents dans les modes synchrone et par lots. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   * Générer des documents en renseignant les fichiers de modèle (PDF et XDP) avec des données XML
   * Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs

* **Polices personnalisées pour les documents d’enregistrement et les documents PDF créés avec les API communications** : Vous pouvez désormais utiliser des polices approuvées par la marque dans les documents PDF générés à l’aide des API communications pour vous conformer aux exigences de votre organisation.

* **Portail de formulaires** : Vous pouvez utiliser le [Portail de formulaires](/help/forms/configure-forms-portal.md) pour répertorier vos formulaires adaptatifs publiés sur une page AEM Sites. Cela permet à un visiteur du site de découvrir tous les formulaires disponibles. De plus, le visiteur peut utiliser le portail de formulaires pour enregistrer et accéder au brouillon d’un formulaire adaptatif et consulter la version PDF d’un formulaire adaptatif envoyé.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Extension des composants myAccount, basés sur les composants extensibles Peregrine de Commerce

![Extension des composants myAccount](/help/assets/CIF/extended-myAccount-components.png)

* Les auteurs peuvent créer des recommandations de produits Commerce ad hoc à l’aide de types de recommandations supplémentaires.

* Prise en charge des cartes-cadeaux dans le point de vente digital AEM

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.11.0.

### Date de publication {#release-date-cm-nov}

La date de publication de Cloud Manager dans la version 2021.11.0 d’AEM as a Cloud Service est le 4 novembre 2021.
La prochaine version est prévue pour le 09 décembre 2021.

### Nouveautés {#what-is-new-cm-nov}

* Les utilisateurs et utilisatrices peuvent désormais exploiter les nouveaux pipelines front-end pour déployer exclusivement le code front-end de manière accélérée. Voir [Pipelines frontaux de Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) pour en savoir plus.

  >[!IMPORTANT]
  >Vous devez disposer de la version `2021.10.5933.20211012T154732Z` ou ultérieure d’AEM pour utiliser les nouveaux pipelines frontaux.

* La durée du pipeline de qualité du code est considérablement réduite en exécutant l’analyse du code de manière plus efficace sans avoir à créer une image AEM entière. Cette modification sera déployée progressivement au cours des semaines qui suivront la publication de la version.

* L’ID de validation Git s’affiche désormais dans les détails d’exécution du pipeline, ce qui facilite le suivi du code créé.

* La création de programme est désormais disponible sur l’API publiquement exposée.

* La création d’environnement est désormais disponible sur l’API publiquement exposée.

* L’en-tête de réponse `x-request-id` est désormais visible dans le laboratoire de l’API sur [www.adobe.io](https://www.adobe.io/). Cet en-tête est utile pour signaler des problèmes à l’assistance clientèle à des fins de dépannage.

* La carte de pipeline affichée dans l’interface ne comporte aucune pipeline. Est-il possible d’obtenir des conseils appropriés ?

* Une nouvelle page d’activité est désormais disponible. Vous pouvez y afficher des activités telles que les exécutions de pipeline et de code, ainsi que les détails associés. Au fil du temps, les activités répertoriées dans cette page s’étendront, de même que les détails fournis.

* Une nouvelle page Pipelines avec une fenêtre contextuelle d’état et de survol permettant d’afficher facilement le résumé des détails est désormais disponible. Il est possible de visualiser les exécutions de pipelines avec les détails associés.

* L’API Modifier un pipeline prend désormais en charge la modification de l’environnement utilisé lors des phases de déploiement.

* Une optimisation du processus d’analyse OakPal a été introduite pour les packages volumineux.

* Le fichier CSV de problème de qualité contient désormais l’horodatage de chaque problème.

### Correctifs {#bug-fixes-nov}

* Certaines configurations de génération non orthodoxes entraînaient le stockage de fichiers inutiles dans le cache d’artefacts Maven du pipeline, ce qui entraînait des E/S réseau superflues lors du démarrage et de l’arrêt du conteneur de génération.

* L’API Pipeline PATCH échoue en l’absence de phase de déploiement.

* La règle de qualité `ClientlibProxyResourceCheck` générait des faux positifs en présence de bibliothèques clientes avec des chemins d’accès de base communs.

* Un message d’erreur indiquant que le nombre maximal de référentiels a été atteint ne précisait pas la raison de l’erreur.

* Dans de rares cas, les pipelines échouaient en raison d’une gestion inappropriée des reprises de certains codes de réponse.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur des bonnes pratiques v2.1.22 est le 01 décembre 2021.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur la version d’ACS couramment utilisée.
* Possibilité de détecter et de générer des rapports sur le nombre d’utilisateurs et de sous-groupes dans un groupe.
* Possibilité de détecter et de générer des rapports sur les valeurs des propriétés des noeuds dans MongoDB dépassant 16 Mo.

### Correctifs {#bug-fixes-bpa}

* La détection des composants Foundation a été améliorée afin de réduire les faux négatifs.
* Pour les clients AEM Forms, le message BPA concernant `EMAIL_PDF_SUBMIT_ACTION` qui n’est pas disponible sur AEM as a Cloud Service a été corrigé.
