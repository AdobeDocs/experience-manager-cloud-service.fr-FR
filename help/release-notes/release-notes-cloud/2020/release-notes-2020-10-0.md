---
title: Notes de mise à jour de la version 2020.10.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.10.0.
exl-id: ac741744-5b47-47a4-b5af-e1089e92c3f0
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 100%

---

# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 {#release-notes}

La section suivante présente les notes de mise à jour générales d’[!DNL Experience Manager] as a Cloud Service version 2020.10.0.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.10.0 est le 28 octobre 2020.
La version suivante (2020.11.0) sera publiée le 1er décembre 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nouveautés de [!DNL Sites] {#what-is-new-sites}

* **[Composants principaux 2.12.0](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr)** : AEM as a Cloud Service bénéficie des mises à jour automatiques de la dernière version des composants principaux. La version 2.12.0 comprend les dernières améliorations apportées par la communauté, telles qu’[un nouveau gestionnaire de formulaires POST ;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html?lang=fr#post-data) la possibilité d’inclure des balises CSS, JavaScript et de métadonnées[ personnalisées par le biais d’une configuration contextuelle ;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html?lang=fr#context-aware-loading) ainsi qu’un utilitaire [`DataLayerBuilder`](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html?lang=fr#enabling-custom-components) pour simplifier l’intégration de la couche de données Adobe dans les composants personnalisés. Voir la [liste des modifications](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) dans la version 2.12.0.

* **[Archétype de projet 24](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr)** : la base recommandée pour lancer un nouveau projet AEM a été améliorée, et inclut désormais la nouvelle [couche de données du client Adobe](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=fr), l’option de [livraison du site dans AMP,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html?lang=fr) et de nouveaux [points d’extension pour ajouter le projet CSS/JS.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading)

* **[Dossiers ContextHub](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)** : possibilité de créer des dossiers d’audience pour organiser, rechercher et sélectionner facilement des segments d’audience à utiliser pour les fonctionnalités de ciblage d’offre ContextHub.

## [!DNL Adobe Experience Manager Assets] en tant que Cloud Service {#assets}

* Balisage vidéo intelligent optimisé par **[!DNL Adobe Sensei]** : les utilisateurs de DAM peuvent exploiter des modèles d’IA afin d’analyser le contenu vidéo pour des balises spécifiques aux objets et actions afin de passer moins de temps à ajouter des balises et de consacrer plus de temps à utiliser les nombreuses informations exposées pour offrir une expérience adaptée aux clients. Voir [Balisage intelligent des ressources vidéo](/help/assets/smart-tags-video-assets.md).

* **Améliorations apportées à Brand Portal** : les nouvelles fonctionnalités suivantes et bien d’autres sont disponibles dans [!DNL Brand Portal]. Pour plus d’informations, voir [[!DNL Brand Portal] Notes de mise à jour](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [Expérience de téléchargement améliorée](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) pour des téléchargements rapides et simplifiés. D’autres configurations de téléchargement peuvent être établies par les administrateurs en vue d’offrir une expérience adaptée aux besoins des utilisateurs et des entreprises.
   * La navigation en un clic vers les fichiers, [Collections](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/share/brand-portal-share-collection.html) et Liens partagés est désormais possible à partir de n’importe quelle page.
   * Les utilisateurs peuvent désormais [sélectionner et télécharger des rendus spécifiques](https://docs.adobe.com/content/help/fr-FR/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page). La nouvelle option de téléchargement de rendu est disponible dans le panneau Rendus de la page Détails de la ressource.
   * Un délai de 15 minutes pour les sessions d’utilisateurs invités garantit une meilleure expérience à tous les utilisateurs simultanés.

* **[!DNL Adobe Asset Link]version 2.1** : une nouvelle version de l’extension [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) pour [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] et [!DNL Adobe InDesign] est disponible. Elle ajoute la compatibilité avec les dernières applications [!DNL Adobe Creative Cloud] dans la version 2021, publiée en octobre 2020.

* Prise en charge des fichiers **[!DNL Assets]WebP** : [!DNL Assets] as a Cloud Service prend désormais en charge le format d’image WebP. WebP est un nouveau format d’image créé par Google. Les images au format WebP ne peuvent pas être distinguées visuellement des fichiers JPG ou PNG et les fichiers sont beaucoup plus petits. La taille de fichier réduite des ressources réduit la durée de chargement des pages et aide les créateurs de contenu à offrir une expérience web plus rapide. Découvrez comment utiliser WebP dans [Création d’un profil de traitement](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Publication du site de référence CIF Venia 2020.10.2 qui comprend la dernière version des composants principaux CIF (v1.4.0). Pour plus de détails, voir le [site de référence CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2).

* Publication des composants principaux CIF version 1.4.0. Reportez-vous à [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0) pour plus de détails.

### Correctifs {#bug-fixes-commerce}

* Les requêtes GraphQL dans la console de produits et les sélecteurs étaient effectuées via le POST HTTP. Ce problème a été corrigé afin de garantir que le client Apollo GraphQL respecte les paramètres de la configuration OSGi du client GraphQL pour prendre en charge les requêtes GET si elles sont configurées.

* L’interface utilisateur de configuration de CIF Cloud affichait les boutons Enregistrer et Fermer pour les configurations dans /lib et /apps/. Mais ils sont en lecture seule, si bien que l’interface utilisateur a été corrigée pour afficher uniquement le bouton Fermer.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2020.10.0 est le 2 octobre 2020.

### Nouveautés de [!DNL Cloud Manager] {#what-is-new-cm}

* La page Environnements a été repensée.

* Les environnements en veille affichent désormais un état discret dans Cloud Manager.

* Le conteneur de création de Cloud Manager prend désormais en charge la compilation de projets à l’aide de Java 8 ou Java 11. La prise en charge de Java 11 est assurée par le système de chaînes d’outils Maven.

* Le nombre de variables d’environnement par environnement a été porté à 200.

* La carte d’environnement de la page Aperçu répertorie désormais jusqu’à trois environnements. Les utilisateurs peuvent sélectionner le bouton **Afficher tout** pour accéder à la page de résumé de l’environnement afin d’afficher un tableau avec une liste complète d’environnements.
Voir [Affichage de l’environnement](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) pour plus de détails.

### Correctifs {#bug-fixes-cloud-manager}

* Le lien entre Cloud Manager et Developer Console était actif avant la création complète des environnements alors qu’il ne devait pas l’être.

* Le lien direct vers Developer Console à partir de Cloud Manager n’affichait pas l’option permettant de mettre en veille/réactiver un environnement de programme Sandbox.

* Les boutons Annuler et Enregistrer sur la page Modification d’un pipeline hors production n’étaient pas toujours visibles.

* Certaines erreurs liées au u processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Lors de la création d’un programme, le nom suggéré renvoyait parfois un duplicata de nom de programme existant.

* Certains journaux d’étape de pipeline volumineux n’ont pas pu être téléchargés de manière cohérente via l’interface utilisateur.

* La validation des noms d’environnement comportait une erreur de décalage d’une unité.

* La page Environnements affichait parfois des segments de publication et de répartiteur alors qu’aucun segment n’était présent.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* La prise en charge de la recherche des instances de workflow a été ajoutée en fonction du titre du workflow, du modèle de workflow, de l’état, de l’initiateur, du chemin d’accès à la charge utile et de la date de début. Voir [Recherche d’instances de workflow](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/sites/administering/workflows-administering.html).

## Outil de transfert de contenu {#content-transfer-tool}

Consultez cette section pour découvrir les nouveautés et les mises à jour de l’[outil de transfert de contenu](https://docs.adobe.com/content/help/fr-FR/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) version 1.1.12.

### Nouveautés {#what-is-new-ctt}

* Amélioration de l’expérience utilisateur des journaux. Horodatages ajoutés aux journaux d’extraction et d’importation. Message ajouté pour indiquer si les journaux sont vides.

### Correctifs {#ctt-bug-fixes}

* L’outil de transfert de contenu ignorait les fichiers de contenu si le jeu de migration contenait des chemins dont les noms de fichiers étaient partiellement similaires. Ce problème a été résolu.
