---
title: Notes de mise à jour de la version 2022.3.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2022.3.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 761f1605-c421-4f3a-8f90-af23f4f047b1
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 87%

---

# Notes de mise à jour 2022.3.0 pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante décrit les notes de mise à jour des fonctionnalités de la version 2022.3.0 de [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2022.3.0) de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 31 mars 2022.
La prochaine version (2022.4.0) est prévue pour le 5 mai 2022.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo [Aperçu de la version de mars 2022](https://video.tv.adobe.com/v/341465) pour obtenir un résumé des fonctionnalités ajoutées dans la version 2022.3.0.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Sites] {#prerelease-features-sites}

* Les types de données de modèle de contenu peuvent désormais être définis comme traduisibles à l’aide d’une simple case à cocher dans l’éditeur de modèles de contenu. En outre, les règles et configurations de traduction AEM sont automatiquement mises à jour.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* [!DNL AEM Dynamic Media] offre désormais la possibilité de [configurer un compte d’alias](/help/assets/dynamic-media/dm-alias-account.md) dans l’interface utilisateur, garantissant ainsi que les URL Dynamic Media prêtes à l’emploi et le code intégré de la visionneuse soient mis à jour. Cette fonctionnalité offre un impact positif en matière de SEO afin de refléter les mises à jour apportées à votre contexte d’entreprise, telles que sur le changement de marque.

* Vous pouvez désormais utiliser l’interface utilisateur [!DNL Experience Manager Assets] pour :

   * configurer la [détection des ressources en double](/help/assets/manage-digital-assets.md#detect-duplicate-assets) dans un référentiel ;

   * configurer l’[ajout de filigranes numériques](/help/assets/watermark-assets.md) à des images.

* Les administrateurs peuvent désormais configurer le service de messagerie pour les téléchargements volumineux. Cette configuration permet aux utilisateurs d’[activer les notifications par e-mail pour les téléchargements volumineux](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) à partir de l’interface [!DNL Experience Manager Assets]. Une fois le processus de téléchargement terminé, l’utilisateur reçoit une notification par e-mail contenant le lien de téléchargement du dossier zip archivé.

* La fonctionnalité [Gérer la publication](/help/assets/manage-publication.md) a été améliorée par le biais de son interface utilisateur. Les utilisateurs peuvent publier ou dépublier du contenu vers et depuis la destination sélectionnée, [ajouter du contenu](/help/assets/manage-publication.md#add-content) à la liste de publication à partir du référentiel DAM, [inclure des paramètres de dossier](/help/assets/manage-publication.md#include-folder-settings) pour publier le contenu des dossiers sélectionnés et appliquer des filtres, et [planifier une publication](/help/assets/manage-publication.md#publish-assets-later) à une date ou une heure ultérieure.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Assets] {#prerelease-features-assets}

* Vous pouvez désormais [trier les balises](/help/assets/organize-assets.md#use-tags-to-organize-assets) dans la fenêtre du sélecteur de balises, par ordre croissant ou décroissant, en fonction du nom de la balise, de la date de création ou de la date de modification.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* **[!DNL Communications - Document Generation APIs]** : les [API de génération de documents](/help/forms/aem-forms-cloud-service-communications.md) permettent de combiner, de réorganiser et de valider des documents PDF. Le service permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   * Assemblage de documents PDF
   * Désassemblage de documents PDF
   * Conversion et validation de documents conformes à la norme PDF/A

* **Conversion automatique de formulaires PDF de plus de 15 pages en formulaires adaptatifs** : vous pouvez désormais utiliser le service de conversion automatique de PDF pour convertir des formulaires PDF de jusque 40 pages en formulaires adaptatifs. Le service offre désormais la possibilité de convertir des sections de formulaires de plus de 15 pages en fragments de formulaires adaptatifs. Cette option accélère le rendu des formulaires convertis et facilite le chargement de formulaires volumineux dans l’éditeur de formulaires adaptatifs.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **Utilisation de XCI personnalisés pour générer un document d’enregistrement** : vous pouvez désormais utiliser un fichier XCI personnalisé pour définir différentes propriétés d’un document d’enregistrement. Il remplace le XCI maître par les modifications personnalisées.

* **Utilisation d’un CAPTCHA invisible dans un formulaire adaptatif** : vous pouvez paramétrer le CAPTCHA invisible pour qu’il ne présente le test CAPTCHA qu’en cas d’activité suspecte. Si aucune activité suspecte n’est détectée, le test CAPTCHA ne s’affiche pas.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Optimisation du référencement pour les scénarios multi-magasin : les formats d’URL pour les pages d’information ou de recensement produit peuvent désormais être configurés au niveau du magasin grâce aux propriétés de configuration cloud CIF.
* Le sélecteur de produits prend en charge les produits intermédiaires par le biais d’une nouvelle option de filtre dans l’interface utilisateur. Cela permet aux spécialistes du contenu de préparer la gestion de contenu de produit pour les lancements de produits à venir.
* Simplification de la gestion de la configuration et de la gestion des erreurs CIF à l’aide du nom de configuration cloud CIF au lieu de l’URL du proxy de configuration.
* Sélection manuelle de catégories pour la liste de produits et les composants de carrousel. Elle permet aux spécialistes du contenu d’utiliser ces composants sur les pages de contenu, en dehors du catalogue..

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire CIF {#prerelease-features-cif}

* Le composant principal de recherche de CIF AEM prend en charge Commerce LiveSearch.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* Pour une résolution plus efficace et plus efficace des problèmes liés aux fonctionnalités personnalisées dans les environnements cloud, nous avons lancé un nouvel outil de développement - [Explorateur de référentiels](/help/implementing/developing/tools/repository-browser.md). Il s’agit d’un navigateur léger, en lecture seule et par HTML que vous pouvez lancer à partir de Developer Console. Visionnez le référentiel de contenu aux niveaux éditeur, auteur et aperçu, et dans tous les environnements, en production, en évaluation et en développement. Parcourez la structure de contenu, affichez les propriétés, prévisualisez et téléchargez des fichiers binaires.

  ![repobrowserrelnotes](/help/release-notes/assets/repobrowserrelnotes.png)

* Les informations d’identification utilisées pour authentifier les appels API serveur à serveur (par exemple, pour les demandes d’API GraphQL) peuvent désormais être actualisées avant expiration en libre-service à partir de Developer Console. Pour plus d’informations, consultez la [documentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials).

* Les tâches de maintenance de purge de version et de purge des journaux d’audit, qui n’avaient pas été activées auparavant, sont désormais activées pour les nouveaux environnements. Consultez les valeurs associées dans cet article [Tâche de maintenance](/help/operations/maintenance.md).

* Les outils du dispatcher du SDK AEM as a Cloud Service prennent désormais en charge les ordinateurs Mac doté d’une puce M1.

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.9.0 est le 28 février 2022.

### Nouveautés {#what-is-new-ctt}

* Garde-fous de vérification de la taille : la fonctionnalité Vérification de la taille de l’outil de transfert de contenu permet de réduire le nombre de transferts de contenu ayant échoué. Grâce à la fonction Vérifier la taille , les utilisateurs peuvent 1) déterminer s’ils disposent d’un espace disque suffisant dans la variable `crx-quickstart` sous-répertoire avant extraction, et 2) estimer la taille du jeu de migration et vérifier s’il est pris en charge. Si l’une de ces vérifications est enfreinte, les utilisateurs verront apparaître des avertissements dans l’interface utilisateur de CTT. Grâce à ce garde-fous de sécurité, vous pouvez éviter les échecs de transfert de contenu et discuter de manière proactive des options de migration avec l’assistance clientèle d’Adobe. Voir [Détermination de la taille du jeu de migration et de l’espace disque](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr#migration-set-size) pour plus d’informations.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.26 est le 16 mars 2022.

### Nouveautés {#what-is-new-bpa}

* Capacité à détecter les ressources non traitées. Si des ressources non traitées sont détectées, ces ressources doivent être définies sur traitées ou doivent être supprimées du jeu de migration lors du transfert de contenu afin d’éviter des problèmes lors de l’ingestion de contenu.
* Capacité à détecter si le contenu comporte plus de 1 000 URL de redirection vers un microsite. L’utilisation d’un nombre élevé d’URL de redirection vers un microsite n’est pas conforme avec les bonnes pratiques, car elle surcharge les serveurs de Dispatcher et de publication.
* Capacité à identifier les problèmes liés aux définitions d’index Oak et de détecter les incompatibilités avec AEM as a Cloud Service.
* Capacité à détecter et à générer des rapports sur l’utilisation des configurations de l’externaliseur. Dans AEM as a Cloud Service, les configurations de l’externaliseur sont définies par Cloud Manager, les configurations de l’externaliseur existantes doivent donc être restructurées pour garantir la compatibilité.

### Correctifs {#bug-fixes-bpa}

* Dans certains scénarios, l’exécution de l’analyseur de bonnes pratiques échouaient en raison d’une erreur d’affirmation de FormsSelectiveFeaturesAnalysis. Ce problème a été résolu.
* L’analyseur de bonnes pratiques signalait les résultats liés au modèle WRK comme MAJEURS plutôt que CRITIQUES. Ce problème a été résolu.
* L’analyseur de bonnes pratiques signalait de manière incorrecte les résultats liés aux définitions d’index OAK dans ui.apps comme étant CRITIQUES. Ce problème a été résolu
