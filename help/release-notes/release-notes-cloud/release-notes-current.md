---
title: Current Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service.
description: Current Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service.
translation-type: tm+mt
source-git-commit: 727dfd1d16a80620fba6db00289021ee5efae0fc
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 4%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

The following section outlines the general Release Notes for [!DNL Experience Manager] as a Cloud Service.

## Date de publication {#release-date}

The Release Date for [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 is October 28, 2020.
La version suivante (2020.11.0) sera publiée le 1er décembre 2020.

## [!DNL Adobe Experience Manager Sites]as a Cloud Service{#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

<!-- add when release done: * **Core Components 2.12.0**: With Core Components being on auto-update, benefit from the latest improvements contributed by the community. See list of changes since 2.11.1: Release Notes -->

* **Archétype de projet 24**: La base recommandée pour début d&#39;un nouveau projet AEM s&#39;est améliorée, incluant désormais la nouvelle couche de données client Adobe, l&#39;option de livraison du site dans AMP et de nouveaux points d&#39;extension pour ajouter le projet CSS/JS.

* **Dossiers** ContextHub : Possibilité de créer des dossiers d’audience pour organiser, rechercher et sélectionner facilement des segments d’audience à utiliser pour les fonctionnalités de ciblage d’offre ContextHub.

## [!DNL Adobe Experience Manager Assets]as a Cloud Service{#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* **[!DNL Adobe Sensei]balisage** intelligent vidéo optimisé : En exploitant les modèles AI pour analyser le contenu vidéo pour les balises d&#39;objet et d&#39;action, les utilisateurs DAM peuvent passer moins de temps à ajouter des balises et consacrer plus de temps à utiliser les informations riches exposées pour offrir une expérience adaptée aux clients. Voir Fichiers [vidéo de balises](/help/assets/smart-tags-video-assets.md)dynamiques.

* **Améliorations** du portail de marque : Les nouvelles fonctionnalités suivantes, entre autres, sont disponibles dans [!DNL Brand Portal]. Pour plus d’informations, voir [[!DNL Brand Portal] Notes de mise à jour](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [Expérience](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) de téléchargement améliorée pour des téléchargements rapides et simplifiés. D’autres configurations de téléchargement peuvent être configurées par les administrateurs pour offre d’une expérience qui répond aux besoins des utilisateurs et des entreprises.
   * La navigation en un clic vers les fichiers, les [collections](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/share/brand-portal-share-collection.html)et les liens partagés est désormais possible à partir de n’importe quelle page.
   * Désormais, les utilisateurs peuvent [sélectionner et télécharger des rendus](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page) spécifiques. La nouvelle option de téléchargement de rendu est disponible dans le panneau Rendus de la page Détails du fichier.
   * Un dépassement de délai de 15 minutes pour les sessions d’utilisateur invité garantit une meilleure expérience à tous les utilisateurs simultanés.

* **[!DNL Adobe Asset Link]version 2.1**: Une nouvelle version de l’extension de lien [de ressource](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) d’Adobe pour [!DNL Adobe Photoshop], [!DNL Adobe Illustrator]et [!DNL Adobe InDesign] est disponible. Il ajoute la compatibilité avec les dernières [!DNL Adobe Creative Cloud] applications de la version 2021, publiée en octobre 2020.

* **[!DNL Assets]Prise en charge** des fichiers WebP : [!DNL Assets] en tant que Cloud Service prend désormais en charge le format d’image WebP. WebP est un nouveau format d’image créé par Google. Les images au format WebP ne peuvent pas être visuellement distinguées des fichiers JPG ou PNG et les fichiers sont beaucoup plus petits. La taille de fichier réduite des ressources réduit les temps de chargement des pages et aide les créateurs de contenu à offrir une expérience Web plus rapide. Voir [Création d’un profil](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile)de traitement standard.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Site de référence de CIF Venia - 2020.10.2 qui comprend les derniers composants principaux de CIF version 1.4.0. Consultez le site [de référence de](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2) CIF Venia pour plus de détails.

* Composants principaux CIF version 1.4.0. Pour plus d&#39;informations, reportez-vous à la section Composants [principaux](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0) CIF.

### Correctifs {#bug-fixes-commerce}

* Les requêtes GraphQL dans la console de produits et les sélecteurs ont été effectuées via le POST HTTP. Ce problème a été corrigé afin de garantir que le client Apollo GraphQL respecte les paramètres de la configuration OSGi du client GraphQL pour prendre en charge les demandes de GET si elles sont configurées.

* L’interface utilisateur de configuration de CIF Cloud affichait les boutons &quot;Enregistrer et fermer&quot; pour les configurations dans /lib et /apps/. Mais il s’agit de données en lecture seule, ce qui explique pourquoi l’interface utilisateur a corrigé pour afficher uniquement le bouton Fermer.


## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager en tant que Cloud Service 2020.11.0 est le 12 novembre 2020.

### What is new in [!DNL Cloud Manager] {#what-is-new-cm}

* Une nouvelle option de menu Connexion **locale** est désormais disponible pour les utilisateurs à partir des options du menu environnement sur les pages Carte d&#39;Environnements et Résumé d&#39;Environnements.
Refer to [Managing Environments](/help/implementing/cloud-manager/manage-environments.md##login-locally) for more details.

* L’onglet **Apprendre** de Cloud Manager a été actualisé avec de nouvelles images dans l’interface utilisateur.

### Correctifs {#bug-fixes-cloud-manager}

* Le chargement des dépendances effectuées avant l&#39;exécution de la génération nécessitait le téléchargement d&#39;un module externe Maven.
* Le lien du pied de page de Cloud Manager permettant de sélectionner une langue accède désormais à l’emplacement approprié.
* Parfois, pendant la numérisation du code, le processus SonarQube ne se début pas. Désormais, cette détection sera automatiquement détectée et un redémarrage sera tenté.
* Tous les pipelines de production existants seront automatiquement activés avec l’étape Audit d’expérience.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* La prise en charge de la recherche des instances de flux de travail a été ajoutée en fonction du titre du flux de travail, du modèle de flux de travail, de l’état, de l’initiateur, du chemin d’accès à la charge et de la date de Début. Voir Instances [de processus de](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html)recherche.

## Outil de transfert de contenu {#content-transfer-tool}

Follow this section to learn about what is new and the updates for [Content Transfer Tool](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Release v1.1.12.

### Nouveautés {#what-is-new-ctt}

* Amélioration de l’expérience utilisateur des journaux. Horodatages ajoutés aux journaux d&#39;Extraction et d&#39;importation. Message ajouté pour indiquer si les journaux sont vides.

### Correctifs {#ctt-bug-fixes}

* L’outil de transfert de contenu ignorait les fichiers de contenu si le jeu de migration contenait des chemins dont les noms de fichier étaient partiellement similaires. Ce problème a été résolu.
