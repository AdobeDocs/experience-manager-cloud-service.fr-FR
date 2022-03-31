---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 372e40eb90d87d9ed366e08a3c0117068542680b
workflow-type: tm+mt
source-wordcount: '1427'
ht-degree: 23%

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

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle (2022.3.0) est le 31 mars 2022.
La version suivante (2022.4.0) date du 28 avril 2022.

## Vidéo de mise à jour {#release-video}

Consultez la section [Présentation de la version de mars 2022](https://video.tv.adobe.com/v/341465) vidéo pour un résumé des fonctionnalités ajoutées dans la version 2022.3.0.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* [!DNL AEM Dynamic Media] offre désormais la possibilité de [configuration d’un compte d’alias](/help/assets/dynamic-media/dm-alias-account.md) dans l’interface utilisateur, en veillant à ce que les URL Dynamic Media prêtes à l’emploi et le code intégré de la visionneuse soient mis à jour. Cela a un impact positif sur l’optimisation pour les moteurs de recherche, afin de refléter les mises à jour apportées à votre contexte d’entreprise, telles que le changement de marque.

* Vous pouvez désormais utiliser la variable [!DNL Experience Manager Assets] de l’interface utilisateur à :

   * Configurez la variable [détection des ressources en double](/help/assets/manage-digital-assets.md#detect-duplicate-assets) dans un référentiel.

   * Configurer [ajout de filigranes numériques](/help/assets/watermark-assets.md) aux images.

* Les administrateurs peuvent désormais configurer le service de messagerie pour les téléchargements volumineux. Il permet aux utilisateurs de [activer les notifications par e-mail pour les téléchargements volumineux ;](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) de la [!DNL Experience Manager Assets] . Une fois le processus de téléchargement terminé, l’utilisateur reçoit une notification par courrier électronique contenant le lien de téléchargement du dossier zip archivé.

* Le [Gérer la publication](/help/assets/manage-publication.md) Cette fonctionnalité a été améliorée avec une interface utilisateur améliorée. Les utilisateurs peuvent publier ou annuler la publication de contenu vers et depuis la destination sélectionnée, [Ajouter du contenu](/help/assets/manage-publication.md#add-content) à la liste de publication à partir du référentiel DAM, [Paramètres du dossier d’inclusion](/help/assets/manage-publication.md#include-folder-settings) pour publier le contenu des dossiers sélectionnés et appliquer des filtres, et [planification de la publication](/help/assets/manage-publication.md#publish-assets-later) à une date ou une heure ultérieure.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Assets] {#prerelease-features-assets}

* Vous pouvez [balises de tri](/help/assets/organize-assets.md#use-tags-to-organize-assets) lors de la création de balises intelligentes et de l’application de filtres de recherche à l’aide du prédicat de balises.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms}

* **[!DNL Communications - Document Generation APIs]**: [API de génération de document](/help/forms/aem-forms-cloud-service-communications.md) vous aide à combiner, réorganiser et valider des documents de PDF. Le service vous permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   * Assemblage de documents PDF.
   * Désassemblage de documents PDF.
   * Convertir et valider des documents conformes au PDF/A.

* **Conversion automatique de PDF forms de plus de 15 pages en formulaires adaptatifs**: Vous pouvez désormais utiliser le service automated forms conversion pour convertir des PDF forms de 40 pages au maximum en formulaires adaptatifs. Le service offre désormais la possibilité de convertir des sections de formulaires de plus de 15 pages en fragments de formulaires adaptatifs. Cette option accélère le rendu des formulaires convertis et facilite le chargement de formulaires volumineux dans l’éditeur de formulaires adaptatifs.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms}

* **Utilisation de XCI personnalisé pour générer un document d’enregistrement**: Vous pouvez désormais utiliser un fichier XCI personnalisé pour définir différentes propriétés d’un document d’enregistrement. Il remplace le XCI maître par les modifications personnalisées.

* **Utilisation de CAPTCHA invisible dans un formulaire adaptatif**: Vous pouvez utiliser le CAPTCHA invisible pour montrer le défi CAPTCHA uniquement en cas d&#39;activité suspecte. Si aucune activité suspecte n&#39;est trouvée, le défi CAPTCHA ne s&#39;affiche pas.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Version bêta : AEM le composant principal Recherche CIF prend en charge Commerce LiveSearch
* Optimisation du référencement pour les scénarios multi-magasin : Les formats d’URL pour PDP/PLP peuvent désormais être configurés au niveau du magasin via les propriétés de configuration du cloud CIF.
* Le sélecteur de produits prend en charge les produits intermédiaires par le biais d’une nouvelle option de filtre dans l’interface utilisateur.  Cela permet aux spécialistes du contenu de préparer la gestion de contenu de produit pour les lancements de produits à venir.
* Simplification de la gestion de la configuration et de la gestion des erreurs CIF à l’aide du nom de configuration du cloud CIF au lieu de l’URL du proxy de configuration
* Sélection manuelle de catégories pour la liste de produits et les composants de carrousel. Cela permet aux spécialistes du contenu d’utiliser ces composants sur les pages de contenu, en dehors de l’expérience de catalogue.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Nouveautés {#what-is-new-foundation}

* Pour une résolution plus efficace et plus efficace des problèmes liés aux fonctionnalités personnalisées dans les environnements cloud, nous avons lancé un nouvel outil de développement - [Explorateur de référentiels](/help/implementing/developing/tools/repository-browser.md). Il s’agit d’un navigateur léger, en lecture seule et par HTML que vous pouvez lancer à partir de Developer Console. Visionnez le référentiel de contenu sur les niveaux d’éditeur, d’auteur et d’aperçu, et dans tous les environnements, y compris la production, l’évaluation et le développement. Parcourez la structure de contenu, affichez les propriétés, prévisualisez et téléchargez des fichiers binaires.

   ![repobrowserrelnotes](/help/release-notes/assets/repobrowserrelnotes.png)

* Les informations d’identification utilisées pour authentifier les appels API serveur à serveur (par exemple, pour les demandes d’API GraphQL) peuvent désormais être actualisées avant expiration en libre-service à partir de Developer Console. Voir [documentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) pour plus d’informations.

* Les tâches de maintenance de purge de version et de purge des journaux d’audit, qui n’avaient pas été activées auparavant, seront activées pour les nouveaux environnements. Voir les valeurs associées dans la variable [Tâche de maintenance](/help/operations/maintenance.md) article.

* AEM les outils de Dispatcher du SDK as a Cloud Service prennent désormais en charge les ordinateurs Mac avec la puce M1.

## Cloud Manager {#cloud-manager}

### Date de publication de février {#release-date-cm-feb}

La date de publication de Cloud Manager dans AEM 2022.02.0 as a Cloud Service est le 10 février 2022. La prochaine version est prévue pour le 10 mars 2022.

### Nouveautés {#what-is-new-cm-feb}

* Nouvelle accélération [Pipelines de configuration de niveau web](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) ont été introduites pour déployer exclusivement la configuration HTTPD/dispatcher.
   * Vous devez être sur AEM version `2021.12.6151.20211217T120950Z` ou plus récent et [vous inscrire au mode flexible des outils de Dispatcher ;](/help/implementing/dispatcher/disp-overview.md#validation-debug) pour utiliser cette fonctionnalité.
   * Cette fonctionnalité sera déployée par étapes au cours des deux semaines qui suivront la version 2022.02.0.
* L’expérience de la page d’entrée de Cloud Manager a été actualisée afin d’offrir une navigation améliorée, un basculement aisé entre les vues de grille/mosaïque et des fenêtres contextuelles pour un résumé rapide du programme.
* Un nouveau seuil d’échec (`< D`) a été ajouté à la variable [mesure d’évaluation de la fiabilité.](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)
   * Les clients avec des problèmes de qualité graves qui affectent la stabilité du système, principalement liés à des index et à des processus de workflow non valides, ne pourront pas déployer tant que ces problèmes ne seront pas résolus.
* La gravité de la variable `BannedPath` [règle de qualité](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules) est passé de bloqueur à critique.
* L’assistant de pipeline informe l’utilisateur lorsqu’une mise à jour de l’environnement AEM peut être nécessaire avant de configurer une [Pipelines de configuration de niveau web](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) qui lui est associée.

### Correctifs {#bug-fixes-cm-feb}

* Les anciens mots de passe du référentiel Git sont désormais toujours invalidés lorsqu’un nouveau mot de passe est généré.
* La mise à jour des variables d’environnement via l’API n’interfère plus dans l’exécution d’un pipeline dans de rares cas.

### Date de publication de mars {#release-date-cm-march}

Date de publication de la version 2022.3.0 de Cloud Manager dans AEM as a Cloud Service 10 mars 2022. La prochaine version est prévue pour le 7 avril 2022.

### Nouveautés {#what-is-new-cm-march}

* Vous pouvez accéder au journal AEM environnement à l’aide du rôle Développeur .

### Correctifs {#bug-fixes-cm-march}

* Un sous-ensemble de référentiels Git créés manuellement avait une valeur de nom incorrecte qui empêchait la fonction de réutilisation des artefacts de build d’être efficace. Les noms de ces référentiels ont été modifiés et les utilisateurs verront le nom corrigé dans l’API/interface utilisateur de Cloud Manager.
* Les artefacts de build des pipelines hors production ont été réutilisés de manière inappropriée sur les pipelines de production de pile pleine.
* Lors de l’ajout ou de la modification d’un pipeline de qualité du code, les options permettant de gérer les échecs de mesures ne s’affichent plus.
* Certaines configurations de variable de pipeline inattendues peuvent se présenter dans l’étape de création.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu version v1.9.0 est le 28 février 2022.

### Nouveautés {#what-is-new-ctt}

* Vérifier les barrières de taille : la fonction Taille de contrôle de l’outil de transfert de contenu permet de réduire les transferts de contenu ayant échoué.  Grâce à la fonction Vérifier la taille , les utilisateurs peuvent 1) déterminer s’ils disposent d’un espace disque suffisant dans la variable `crx-quickstart` sous-répertoire avant extraction, et 2) estimer la taille du jeu de migration et vérifier s’il est pris en charge. Si l’une de ces vérifications est enfreinte, les utilisateurs verront des avertissements dans l’interface utilisateur de CTT. Grâce à cette barrière de sécurité, vous pouvez éviter les échecs de transfert de contenu et discuter de manière proactive des options de migration avec l’assistance clientèle d’Adobe. Voir [Détermination de la taille du jeu de migration et de l’espace disque](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en#migration-set-size) pour plus d’informations.

## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de l’analyseur de bonnes pratiques v2.1.26 est le 16 mars 2022.

### Nouveautés {#what-is-new-bpa}

* Capacité à détecter les ressources non traitées. Si des ressources non traitées sont détectées, ces ressources doivent être définies sur traitées ou doivent être supprimées du jeu de migration lors du transfert de contenu afin d’éviter des problèmes lors de l’ingestion de contenu.
* Possibilité de détecter si le contenu comporte plus de 1 000 URL de redirection vers un microsite. L’utilisation d’un nombre élevé d’URL de redirection vers un microsite n’est pas une bonne pratique, car elle charge les serveurs de Dispatcher et de publication.
* Possibilité d’identifier les problèmes liés aux définitions d’index Oak et de détecter les incompatibilités avec AEM as a Cloud Service.
* Possibilité de détecter et de générer des rapports sur l’utilisation des configurations de l’externaliseur. Dans AEM les configurations de l’externaliseur as a Cloud Service sont définies par Cloud Manager, les configurations de l’externaliseur existantes doivent donc être restructurées pour maintenir la compatibilité.

### Correctifs {#bug-fixes-bpa}

* Dans certains scénarios, l’exécution de BPA a échoué en raison d’une erreur d’affirmation de FormsSelectiveFeaturesAnalysis. Ce problème a été résolu.
* Le BPA a rapporté que les résultats liés au modèle de WRK étaient MAJEURS plutôt que CRITIQUES. Ce problème a été résolu.
* La BPA signalait de manière incorrecte les résultats liés aux définitions d’index OAK dans ui.apps comme étant CRITIQUES. Ce problème a été résolu
