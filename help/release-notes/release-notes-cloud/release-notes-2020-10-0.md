---
title: Notes de mise à jour de la version 2020.10.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service pour la version 2020.10.0.
translation-type: tm+mt
source-git-commit: 841069f35539a49c6ee67699bf3a476cf1c9da41
workflow-type: tm+mt
source-wordcount: '1039'
ht-degree: 22%

---



# Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 {#release-notes}

La section suivante décrit les Notes de mise à jour générales de [!DNL Experience Manager] en tant que Cloud Service 2020.10.0.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] en tant que Cloud Service 2020.10.0 est le 28 octobre 2020.
La version suivante (2020.11.0) sera publiée le 1er décembre 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service{#sites}

### Nouveautés d’[!DNL Sites] {#what-is-new-sites}

* **[Composants principaux 2.12.0](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)** : aem en tant que Cloud Service bénéficie des mises à jour automatiques de la dernière version des composants principaux. La version 2.12.0 comprend les dernières améliorations apportées par la communauté, telles que [un nouveau gestionnaire de formulaires POST ;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html#post-data) la possibilité d’inclure des balises CSS, JavaScript et [de métadonnées personnalisées par le biais d’une configuration contextuelle ;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading) et un utilitaire [`DataLayerBuilder`](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html#enabling-custom-components) pour simplifier l’intégration de la couche de données Adobe dans les composants personnalisés. Voir la [liste des modifications](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) dans la version 2.12.0.

* **[Archétype de projet 24](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)** : La base recommandée pour début d&#39;un nouveau projet AEM s&#39;est améliorée, incluant désormais la nouvelle couche [ de données du client ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html)Adobe, l&#39;option de  [livraison du site dans AMP,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html) et de nouveaux points  [d&#39;extension pour ajouter le projet CSS/JS.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading)

* **[Dossiers](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)** ContextHub : Possibilité de créer des dossiers d’audience pour organiser, rechercher et sélectionner facilement des segments d’audience à utiliser pour les fonctionnalités de ciblage d’offre ContextHub.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service{#assets}

### Nouveautés d’[!DNL Assets] {#what-is-new-assets}

* **[!DNL Adobe Sensei]balisage** intelligent vidéo optimisé : En exploitant les modèles AI pour analyser le contenu vidéo pour les balises d&#39;objet et d&#39;action, les utilisateurs DAM peuvent passer moins de temps à ajouter des balises et consacrer plus de temps à utiliser les informations riches exposées pour offrir une expérience adaptée aux clients. Voir [Fichiers vidéo de balises actives](/help/assets/smart-tags-video-assets.md).

* **Améliorations** du portail de marque : Les nouvelles fonctionnalités suivantes, entre autres, sont disponibles dans  [!DNL Brand Portal]. Pour plus d’informations, voir [[!DNL Brand Portal] Notes de mise à jour](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [Meilleure ](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) expérience de téléchargement pour des téléchargements rapides et simplifiés. D’autres configurations de téléchargement peuvent être configurées par les administrateurs pour offre d’une expérience qui répond aux besoins des utilisateurs et des entreprises.
   * La navigation en un clic vers les fichiers, [Collections](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/share/brand-portal-share-collection.html) et Liens partagés est désormais possible à partir de n’importe quelle page.
   * Les utilisateurs peuvent [sélectionner et télécharger des rendus spécifiques](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page) maintenant. La nouvelle option de téléchargement de rendu est disponible dans le panneau Rendus de la page Détails du fichier.
   * Un dépassement de délai de 15 minutes pour les sessions d’utilisateur invité garantit une meilleure expérience à tous les utilisateurs simultanés.

* **[!DNL Adobe Asset Link]version 2.1** : Une nouvelle version de  [Adobe Asset ](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) Linkextension pour  [!DNL Adobe Photoshop],  [!DNL Adobe Illustrator]et  [!DNL Adobe InDesign] est disponible. Il ajoute la compatibilité avec les dernières applications [!DNL Adobe Creative Cloud] de la version 2021, publiée en octobre 2020.

* **[!DNL Assets]Prise en charge** des fichiers WebP :  [!DNL Assets] en tant que Cloud Service prend désormais en charge le format d’image WebP. WebP est un nouveau format d’image créé par Google. Les images au format WebP ne peuvent pas être visuellement distinguées des fichiers JPG ou PNG et les fichiers sont beaucoup plus petits. La taille de fichier réduite des ressources réduit les temps de chargement des pages et aide les créateurs de contenu à offrir une expérience Web plus rapide.

<!--
### Bugs Fixed {#bugs-fixed-assets}

Content to come
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Site de référence de CIF Venia - 2020.10.2 qui comprend les derniers composants de base de CIF version 1.4.0. Pour plus de détails, voir [Site de référence de CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2).

* Composants principaux CIF version 1.4.0. Pour plus d&#39;informations, consultez [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0).

### Correctifs {#bug-fixes-commerce}

* Les requêtes GraphQL dans la console de produits et les sélecteurs ont été effectuées via le POST HTTP. Ce problème a été corrigé afin de garantir que le client Apollo GraphQL respecte les paramètres de la configuration OSGi du client GraphQL pour prendre en charge les demandes de GET si elles sont configurées.

* L’interface utilisateur de configuration de CIF Cloud affichait les boutons &quot;Enregistrer et fermer&quot; pour les configurations dans /lib et /apps/. Mais il s’agit de données en lecture seule, ce qui explique pourquoi l’interface utilisateur a corrigé pour afficher uniquement le bouton Fermer.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager en tant que Cloud Service 2020.10.0 en AEM est le 2 octobre 2020.

### Nouveautés d’[!DNL Cloud Manager] {#what-is-new-cm}

* La page Environnements a été repensée.

* Les environnements en veille affichent désormais un état discret dans Cloud Manager.

* Le conteneur de création de Cloud Manager prend désormais en charge la compilation de projets à l’aide de Java 8 ou Java 11. La prise en charge de Java 11 est assurée par le système de chaînes d’outils Maven.


* Le nombre de variables d’environnement par environnement a été porté à 200.

* La carte d’Environnement de la page Aperçu liste désormais jusqu’à trois environnements. Les utilisateurs peuvent sélectionner le bouton **Afficher tout** pour accéder à la page de résumé de l’Environnement et vue d’un tableau avec une liste complète d’environnements.
Consultez [Affichage de l&#39;Environnement](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) pour plus de détails.

### Correctifs {#bug-fixes-cloud-manager}

* Le lien entre Cloud Manager et Developer Console était actif avant la création complète des environnements alors qu’il ne devait pas l’être.

* Le lien direct vers Developer Console à partir de Cloud Manager n’affichait pas l’option permettant de mettre en veille/réactiver un environnement de programme Sandbox.

* Les boutons Annuler et Enregistrer de la page Modification du pipeline hors production n’étaient pas toujours visibles.

* Certaines erreurs liées au u processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Lors de la création d’un programme, le nom suggéré renvoyait parfois un duplicata de nom de programme existant.

* Certains journaux d’étape de pipeline volumineux n’ont pas pu être téléchargés de manière cohérente via l’interface utilisateur.

* La validation des noms d’environnement comportait une erreur de décalage d’une unité.

* La page Environnements affichait parfois des segments de publication et de répartiteur alors qu’aucun segment n’était présent.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* La prise en charge de la recherche des instances de flux de travail a été ajoutée en fonction du titre du flux de travail, du modèle de flux de travail, de l’état, de l’initiateur, du chemin d’accès à la charge et de la date de Début. Voir [Instances de flux de travaux de recherche](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html).

## Outil de transfert de contenu {#content-transfer-tool}

Suivez cette section pour en savoir plus sur les nouveautés et les mises à jour de [Outil de transfert de contenu](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Version v1.1.12.

### Nouveautés {#what-is-new-ctt}

* Amélioration de l’expérience utilisateur des journaux. Horodatages ajoutés aux journaux d&#39;Extraction et d&#39;importation. Message ajouté pour indiquer si les journaux sont vides.

### Correctifs {#ctt-bug-fixes}

* L’outil de transfert de contenu ignorait les fichiers de contenu si le jeu de migration contenait des chemins dont les noms de fichier étaient partiellement similaires. Ce problème a été résolu.

