---
title: Notes de mise à jour de la version 2022.1.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2022.1.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 1c40ab67-8fd7-4f29-b8c9-dd98b6d5b490
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 88%

---

# Notes de mise à jour de la version 2022.1.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante décrit les notes de mise à jour des fonctionnalités de la version 2022.1.0 de [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2022.1.0) de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 3 février 2022.
La version suivante (2022.3.0) date du 31 mars 2022.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo [Aperçu de la version de décembre 2022](https://video.tv.adobe.com/v/340120) pour un résumé des fonctionnalités ajoutées dans la version 2022.1.0.

## Adobe Experience Manager Sites as a Cloud Service {#sites}

* Le bouton **[Enable Front End Pipeline](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)** (Activation du pipeline front-end) est disponible dans le rail **Site** de la console Sites pour les sites qui utilisent la version v2 du composant principal Page. Ce bouton configure le site pour charger les thèmes déployés avec le pipeline front-end par-dessus les bibliothèques clientes existantes.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* [!DNL Dynamic Media] - Vous pouvez désormais utiliser l’interface AEM Dynamic Media pour configurer les paramètres généraux et la configuration de publication au lieu d’avoir à passer par l’application de bureau Dynamic Media Classic.

* [!DNL Dynamic Media] prend désormais en charge l’ingestion, la prévisualisation, la lecture et la publication des vidéos MXF. L’annotation et la shoppable vidéo pour les vidéos MXF ne sont pas encore prises en charge.

* Après la configuration d’une connexion entre les déploiements DAM distant et Sites, les ressources du DAM distant sont disponibles sur le déploiement de Sites. Vous pouvez désormais effectuer les opérations suivantes : [mettre à jour, supprimer, renommer et déplacer des opérations](/help/assets/use-assets-across-connected-assets-instances.md) sur les ressources ou dossiers du DAM distant. Les mises à jour, avec un certain retard, sont disponibles automatiquement sur le déploiement Sites.

### Nouvelles fonctionnalités dans le [!DNL Assets] canal de version préliminaire {#assets-prerelease-features}

* [!DNL AEM Dynamic Media] offre désormais la possibilité de [configurer un compte d’alias](/help/assets/dynamic-media/dm-alias-account.md) dans l’interface utilisateur, garantissant ainsi que les URL Dynamic Media prêtes à l’emploi et le code intégré de la visionneuse soient mis à jour. Cette fonctionnalité offre un impact positif en matière de SEO afin de refléter les mises à jour apportées à votre contexte d’entreprise, telles que sur le changement de marque.

* Vous pouvez désormais utiliser l’interface utilisateur [!DNL Experience Manager Assets] pour :

   * configurer la détection des ressources en double dans un référentiel ;

   * configurer l’ajout de filigranes numériques à des images.

* Les administrateurs peuvent désormais configurer le service de messagerie pour les téléchargements volumineux. Cette configuration permet aux utilisateurs d’[activer les notifications par e-mail pour les téléchargements volumineux](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) à partir de l’interface [!DNL Experience Manager Assets]. Une fois le processus de téléchargement terminé, l’utilisateur reçoit une notification par e-mail contenant le lien de téléchargement du dossier zip archivé.


* La fonctionnalité [Gérer la publication](/help/assets/manage-publication.md) a été améliorée par le biais de son interface utilisateur. Les utilisateurs peuvent publier ou dépublier du contenu vers et depuis la destination sélectionnée, [ajouter du contenu](/help/assets/manage-publication.md#add-content) à la liste de publication à partir du référentiel DAM, [inclure des paramètres de dossier](/help/assets/manage-publication.md#include-folder-settings) pour publier le contenu des dossiers sélectionnés et appliquer des filtres, et [planifier une publication](/help/assets/manage-publication.md#publish-assets-later) à une date ou une heure ultérieure.

### Correctifs {#bug-fixes}

* Les ressources non traitées sans rendu d’origine sont envoyées à Asset Compute pour être traitées lors de la migration des ressources à partir d’AEM on-premise vers les services cloud.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API Communications](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html?lang=fr) vous permettent de combiner un modèle et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents dans les modes synchrone et par lots. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   * de générer des documents en complétant des fichiers de modèle avec des données XML ;
   * de générer des formulaires dans divers formats, y compris les flux d’impression PDF non interactifs ;
   * de générer des fichiers PDF d’impression à partir de fichiers PDF de formulaire XFA ;
   * de générer des documents PDF, PostScript, PCL et ZPL en blocs en fusionnant plusieurs jeux de données avec les modèles sources.

* **Polices personnalisées pour les documents d’enregistrement et les documents PDF créés avec les API communications** : vous pouvez désormais utiliser des polices approuvées par la marque dans les documents PDF générés à l’aide des API Communications pour vous conformer aux exigences de votre organisation.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **[API Assembler](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/)** : les API Assembler pour combiner, réorganiser, agrémenter les documents PDF et obtenir des informations à leur propos.


## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Amélioration des composants myAccount
* Le composant de recommandation de produit prend en charge d’autres types de page (page d’accueil, panier, confirmation de commande).
* **Liste de souhaits**
   * Les visiteurs connectés peuvent ajouter des produits à une liste bloquée.
   * La gestion de la liste de attente et de ses produits est possible via myAccount
   * Le bouton &quot;Ajouter à la liste bloquée&quot; peut être activé/désactivé au niveau des composants via une stratégie (exemple de teaser de produit, détails du produit).
   * Disponible en tant que composant principal et dans AEM Venia Storefront

<!-- Image was not found during PR validation despite correct path ![Wishlist](/help/assets/CIF/wantlist.png) -->

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2022.01.0 est le 20 janvier 2022. La prochaine version est prévue pour le 10 février 2022.

### Nouveautés {#what-is-new-cm}

* Cloud Manager [évitera de reconstruire la base de code lorsqu’il détecte que la même validation Git est utilisée](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) dans plusieurs exécutions de pipeline full stack.
* L’accès au journal d’environnement AEM nécessite désormais le profil produit **Gestionnaire de déploiement**. Les utilisateurs ne disposant pas de ce profil voient apparaître un bouton désactivé dans l’interface utilisateur.
* L’interface utilisateur n’autorise pas la configuration du pipeline front-end pour un programme où Sites n’est pas activé en tant que solution.
* Lors de la génération d’un mot de passe Git, la date d’expiration s’affiche.

### Correctifs {#bug-fixes-cm}

* Les exceptions de pointeurs nuls rencontrées par certains déploiements de pipelines front-end ont été corrigées.
* Les variables d’environnement peuvent désormais être ajoutées, mises à jour et supprimées lorsqu’un environnement exécute une version obsolète d’AEM.
* L’étape de création d’image ne sera plus marquée comme ERREUR pour les pipelines qui ont utilisé l’étape planifiée dans de rares cas.
* Pour les programmes ne comportant qu’un seul référentiel, l’écran d’exécution du pipeline affiche désormais le nom du référentiel.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.8.6 est le 03 février 2022.

### Nouveautés {#what-is-new-ctt}

* Validation du contenu : les utilisateurs peuvent déterminer de manière fiable si tout le contenu extrait par l’outil de transfert de contenu a bien été ingéré dans l’instance cible. Pour utiliser cette fonctionnalité, activez-la dans l’ `System Console` de l’environnement d’AEM source. Consultez [Validation des transferts de contenu - Prise en main](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=fr#getting-started) pour plus d’informations.

### Correctifs {#bug-fixes-ctt}

* Certains utilisateurs n’étaient pas mappés, car le mappage des utilisateurs était sensible à la casse. Ce problème a été résolu. Le mappage utilisateur n’est plus sensible à la casse.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.24 est le 1er février 2022.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur le nombre de ressources avec et sans balises intelligentes.
* Possibilité de détecter et de générer des rapports sur la version de composant principal couramment utilisée.
* Possibilité de détecter et de générer des rapports sur le type de niveau source (création ou publication) où l’analyseur de bonne pratique a été exécuté.

### Correctifs {#bug-fixes-bpa}

* La logique de dimensionnement de l’analyseur de bonne pratique a été rendue plus rapide et plus efficace.
* Dans certains scénarios, l’analyseur de bonne pratique n’incrémentait pas le nombre analysé lors de son exécution. Ce problème a été résolu.
