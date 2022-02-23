---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 2693022e5745b5c2bb2166f0833c6b1af4337815
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 26%

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

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle (2022.1.0) est le 3 février 2022.
La version suivante (2022.2.0) date du 3 mars 2022.

## Vidéo de publication {#release-video}

Consultez la section [Présentation de la version de janvier 2022](https://video.tv.adobe.com/v/340120) vidéo pour un résumé des fonctionnalités ajoutées dans la version 2022.1.0.

## Adobe Experience Manager Sites as a Cloud Service {#sites}

* Le **[Activation du pipeline front-end](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)** est disponible dans la **Site** rail de la console Sites pour les sites qui utilisent la version v2 du composant principal Page. Ce bouton configure le site pour charger les thèmes déployés avec le pipeline front-end au-dessus des bibliothèques clientes existantes.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* [!DNL Dynamic Media] - Vous pouvez désormais utiliser AEM interface Dynamic Media pour configurer les paramètres généraux et la configuration de publication au lieu d’avoir à passer par l’application de bureau Dynamic Media Classic.

* [!DNL Dynamic Media] prend désormais en charge l’ingestion, la prévisualisation, la lecture et la publication pour les vidéos MXF. Les annotations et les vidéos Shoppable pour les vidéos MXF ne sont pas encore prises en charge.

* Après la configuration d’une connexion entre les déploiements DAM distant et Sites, les ressources sur DAM distant sont disponibles sur le déploiement Sites. Vous pouvez désormais effectuer les opérations suivantes : [mettre à jour, supprimer, renommer et déplacer des opérations](/help/assets/use-assets-across-connected-assets-instances.md) sur les ressources ou dossiers DAM distants. Les mises à jour, avec un certain délai, sont disponibles automatiquement sur le déploiement Sites .

### Nouvelles fonctionnalités d’ [!DNL Assets] canal prerrelease {#assets-prerelease-features}

* [!DNL AEM Dynamic Media] offre désormais la possibilité de [configuration d’un compte d’alias](../../assets/dynamic-media/dm-alias-account.md) dans l’interface utilisateur, en veillant à ce que les URL Dynamic Media prêtes à l’emploi et le code intégré de la visionneuse soient mis à jour. Cela a un impact positif sur l’optimisation pour les moteurs de recherche, afin de refléter les mises à jour apportées à votre contexte d’entreprise, telles que le changement de marque.

* Vous pouvez désormais utiliser la variable [!DNL Experience Manager Assets] de l’interface utilisateur à :

   * Configurez la détection des ressources en double dans un référentiel.

   * Configurez l’ajout de filigranes numériques aux images.

* Les administrateurs peuvent désormais configurer le service de messagerie pour les téléchargements volumineux. Il permet aux utilisateurs de [activer les notifications par e-mail pour les téléchargements volumineux ;](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) de la [!DNL Experience Manager Assets] . Une fois le processus de téléchargement terminé, l’utilisateur reçoit une notification par courrier électronique contenant le lien de téléchargement du dossier zip archivé.


* Le [Gérer la publication](/help/assets/manage-publication.md) Cette fonctionnalité a été améliorée avec une interface utilisateur améliorée. Les utilisateurs peuvent publier ou annuler la publication de contenu vers et depuis la destination sélectionnée, [Ajouter du contenu](/help/assets/manage-publication.md#add-content) à la liste de publication à partir du référentiel DAM, [Paramètres du dossier d’inclusion](/help/assets/manage-publication.md#include-folder-settings) pour publier le contenu des dossiers sélectionnés et appliquer des filtres, et [planification de la publication](/help/assets/manage-publication.md#publish-assets-later) à une date ou une heure ultérieure.

### Correctifs {#bug-fixes}

* Les ressources non traitées sans rendu d’origine sont envoyées à l’Asset compute pour traitement lors de la migration des ressources d’AEM on-premise vers les services cloud.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API Communications](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) vous permettent de combiner un modèle et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents dans les modes synchrone et par lots. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   * de générer des documents en complétant des fichiers de modèle avec des données XML ;
   * de générer des formulaires dans divers formats, y compris les flux d’impression PDF non interactifs ;
   * de générer des fichiers PDF d’impression à partir de fichiers PDF de formulaire XFA ;
   * de générer des documents PDF, PostScript, PCL et ZPL en blocs en fusionnant plusieurs jeux de données avec les modèles sources.

* **Polices personnalisées pour les documents Document d’enregistrement et de PDF créés avec les API de communication**: Vous pouvez désormais utiliser des polices approuvées par la marque dans les documents PDF générés à l’aide des API de communication pour vous conformer aux exigences de votre organisation.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **[API Assembler](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/)**: API Assembler pour combiner, réorganiser, agrémenter et obtenir des informations sur les documents PDF.


## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Amélioration des composants myAccount
* Le composant de recommandation de produit prend en charge d’autres types de page (page d’accueil, panier, confirmation de commande).
* **Liste de souhaits**
   * Les visiteurs connectés peuvent ajouter des produits à une liste bloquée.
   * La gestion de la liste des souhaits et de ses produits est possible via myAccount
   * Le bouton &quot;Ajouter à la liste des souhaits&quot; peut être activé/désactivé au niveau des composants via une stratégie (par exemple, teaser de produit, détails de produit).
   * Disponible en tant que composant principal et dans l’AEM Venia Storefront

![Liste de souhaits](/help/assets/CIF/wishlist.png)

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans AEM 2022.01.0 as a Cloud Service est le 20 janvier 2022. La prochaine version est prévue pour le 10 février 2022.

### Nouveautés {#what-is-new-cm}

* Cloud Manager [évitez de reconstruire la base de code lorsqu’il détecte que la même validation git est utilisée.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) dans plusieurs exécutions de pipeline de pile complète.
* L’accès au journal de l’environnement AEM requiert désormais le **Responsable de déploiement** profil de produit. Un bouton désactivé s’affiche dans l’interface utilisateur pour les utilisateurs ne disposant pas de ce profil.
* L’interface utilisateur n’autorise pas la configuration du pipeline frontal pour un programme où Sites n’est pas activé en tant que solution.
* Lors de la génération d’un mot de passe Git, la date d’expiration s’affiche.

### Correctifs {#bug-fixes-cm}

* Les exceptions null pointer rencontrées par certains déploiements de pipeline front-end ont été corrigées.
* Les variables d’environnement peuvent désormais être ajoutées, mises à jour et supprimées lorsqu’un environnement exécute une version obsolète d’AEM.
* L’étape de création d’image ne sera plus marquée comme ERREUR pour les pipelines qui ont utilisé l’étape planifiée dans de rares cas.
* Pour les programmes ne comportant qu’un seul référentiel, l’écran d’exécution du pipeline affiche désormais le nom du référentiel.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.8.6 est le 03 février 2022.

### Nouveautés {#what-is-new-ctt}

* Validation du contenu : les utilisateurs peuvent déterminer de manière fiable si tout le contenu extrait par l’outil de transfert de contenu a bien été ingéré dans l’instance cible. Pour utiliser cette fonctionnalité, vous devez l’activer dans la variable `System Console` de l’environnement d’AEM source. Voir [Validation des transferts de contenu - Prise en main](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=en#getting-started) pour plus d’informations.

### Correctifs {#bug-fixes-ctt}

* Certains utilisateurs n’étaient pas mappés, car le mappage des utilisateurs était sensible à la casse. Ce problème a été résolu. Le mappage utilisateur n’est plus sensible à la casse.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.24 est le 01 février 2022.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur le nombre de ressources avec et sans balises intelligentes.
* Possibilité de détecter et de générer des rapports sur la version du composant principal utilisé.
* Possibilité de détecter et de générer des rapports sur le type de niveau source (auteur ou publication) où l’application d’une seule page a été exécutée.

### Correctifs {#bug-fixes-bpa}

* La logique de dimensionnement des BPA a été rendue plus rapide et plus efficace.
* Dans certains scénarios, BPA n’incrémentait pas le nombre analysé lors de son exécution. Ce problème a été résolu.
