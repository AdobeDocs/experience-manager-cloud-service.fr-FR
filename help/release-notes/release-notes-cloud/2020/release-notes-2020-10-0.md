---
title: Notes de mise à jour de la version 2020.10.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.10.0.
exl-id: ac741744-5b47-47a4-b5af-e1089e92c3f0
source-git-commit: af5eb5aeb34e2f0ead98e0a0acb412b19bcfe517
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 67%

---

# Notes de mise à jour pour [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 {#release-notes}

La section suivante présente les notes de mise à jour générales d’[!DNL Experience Manager] as a Cloud Service version 2020.10.0.

## Date de publication {#release-date}

La date de publication d’[!DNL Adobe Experience Manager] as a Cloud Service version 2020.10.0 est le 28 octobre 2020.
La version suivante (2020.11.0) sera publiée le 1er décembre 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Nouveautés d’[!DNL Sites]  {#what-is-new-sites}

* **[Composants principaux 2.12.0](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr)**: Adobe Experience Manager as a Cloud Service bénéficie de mises à jour automatiques de la dernière version des composants principaux. La version 2.12.0 comprend les dernières améliorations apportées par la communauté. Les améliorations incluent : [un nouveau gestionnaire de formulaires de POST ;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html?lang=fr#post-data) la possibilité d’inclure des CSS, JavaScript et des métadonnées personnalisées ; [balises via une configuration contextuelle ;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html?lang=fr#context-aware-loading) et un [`DataLayerBuilder`](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html?lang=fr#enabling-custom-components) pour simplifier l’intégration de la couche de données d’Adobe dans les composants personnalisés. Voir la [liste des modifications](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) dans la version 2.12.0.

* **[Archétype de projet 24](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr)**: La fondation recommandée pour démarrer un nouveau projet de Experience Manager s’est améliorée. Elle comprend désormais la nouvelle [Adobe de la couche de données client](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=fr), option pour [diffuser le site dans AMP,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html?lang=fr) et nouveau [points d’extension pour ajouter le projet CSS/JS.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading)

* **[Dossiers ContextHub](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)**: Possibilité de créer des dossiers d’audience pour organiser, rechercher et sélectionner facilement des segments d’audience à utiliser pour les fonctionnalités de ciblage des offres ContextHub.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

* **[!DNL Adobe Sensei]balisage intelligent de vidéo optimisé**: En appliquant des modèles d’IA pour analyser le contenu vidéo pour les balises d’objet et d’action spécifiques, les utilisateurs de la gestion des actifs numériques peuvent passer moins de temps à ajouter des balises et passer plus de temps à utiliser les informations riches et exposées. En retour, vous fournissez la bonne expérience aux clients. Voir [Balisage intelligent des ressources vidéo](/help/assets/smart-tags-video-assets.md).

* **Améliorations apportées à Brand Portal** : les nouvelles fonctionnalités suivantes et bien d’autres sont disponibles dans [!DNL Brand Portal]. Pour plus d’informations, voir [[!DNL Brand Portal] Notes de mise à jour](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html?lang=fr).

   * [Expérience de téléchargement améliorée](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html?lang=fr) pour des téléchargements rapides et simplifiés. D’autres configurations de téléchargement peuvent être établies par les administrateurs en vue d’offrir une expérience adaptée aux besoins des utilisateurs et des entreprises.
   * La navigation en un clic vers les fichiers, [Collections](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/share/brand-portal-share-collection.html?lang=fr) et Liens partagés est désormais possible à partir de n’importe quelle page.
   * Les utilisateurs peuvent désormais [sélectionner et télécharger des rendus spécifiques](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html?lang=fr#download-assets-from-asset-details-page). La nouvelle option de téléchargement de rendu est disponible dans le panneau Rendus de la page Détails de la ressource.
   * Un délai de 15 minutes pour les sessions d’utilisateurs invités garantit une meilleure expérience à tous les utilisateurs simultanés.

* **[!DNL Adobe Asset Link]version 2.1** : une nouvelle version de l’extension [Adobe Asset Link](https://helpx.adobe.com/fr/enterprise/using/manage-assets-using-adobe-asset-link.html) pour [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] et [!DNL Adobe InDesign] est disponible. Elle ajoute la compatibilité avec les dernières applications [!DNL Adobe Creative Cloud] dans la version 2021, publiée en octobre 2020.

* Prise en charge des fichiers **[!DNL Assets]WebP** : [!DNL Assets] as a Cloud Service prend désormais en charge le format d’image WebP. WebP est un nouveau format d’image créé par Google. Les images au format WebP ne peuvent pas être distinguées visuellement des fichiers JPG ou PNG et les fichiers sont beaucoup plus petits. La taille de fichier réduite des ressources réduit la durée de chargement des pages et aide les créateurs de contenu à offrir une expérience web plus rapide. Découvrez comment utiliser WebP dans [Création d’un profil de traitement](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nouveautés {#what-is-new-commerce}

* Publication du site de référence de CIF Venia – 2020.10.2 qui comprend les derniers composants principaux de CIF version 1.4.0. Pour plus d’informations, consultez [Site de référence de CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2).

* Publication des composants principaux CIF version 1.4.0. Reportez-vous à [Composants principaux CIF](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0) pour plus de détails.

### Correctifs {#bug-fixes-commerce}

* Les requêtes GraphQL qui se trouvaient dans la console de produits et les sélecteurs étaient effectuées par le biais du POST HTTP. Ce problème a été corrigé afin de s’assurer que le client Apollo GraphQL respecte le paramètre défini dans la configuration OSGi du client GraphQL pour prendre en charge les demandes de GET, le cas échéant.

* L’interface utilisateur de configuration de CIF Cloud affichait les boutons Enregistrer et Fermer pour les configurations dans /lib et /apps/. Toutefois, ces interfaces sont en lecture seule et l’interface utilisateur a été corrigée afin d’afficher uniquement le bouton Fermer.

## Cloud Manager {#cloud-manager}

### Date de publication {#release-date-cm}

La date de publication de Cloud Manager dans Experience Manager as a Cloud Service 2020.10.0 est le 2 octobre 2020.

### Nouveautés d’[!DNL Cloud Manager]  {#what-is-new-cm}

* La page Environnements a été repensée.

* Les environnements en veille affichent désormais un état discret dans Cloud Manager.

* Le &quot;conteneur de génération&quot; de Cloud Manager prend désormais en charge la compilation des projets à l’aide de Java™ 8 ou Java™ 11. La prise en charge de Java™ 11 est assurée par le système de chaînes d’outils Maven.

* Le nombre de variables d’environnement par environnement a été porté à 200.

* La carte Environnement de la page Aperçu répertorie désormais trois environnements au maximum. Les utilisateurs peuvent sélectionner le bouton **Afficher tout** pour accéder à la page de résumé de l’environnement afin d’afficher un tableau avec une liste complète d’environnements.
Voir [Affichage de l’environnement](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) pour plus de détails.

### Correctifs {#bug-fixes-cloud-manager}

* Le lien entre Cloud Manager et Developer Console était actif avant la création complète des environnements alors qu’il ne devait pas l’être.

* Le lien direct vers Developer Console à partir de Cloud Manager n’affichait pas l’option permettant de mettre en veille/réactiver un environnement de programme Sandbox.

* Les boutons Annuler et Enregistrer sur la page Modification d’un pipeline hors production n’étaient pas toujours visibles.

* Certaines erreurs liées au u processus de qualité du code peuvent entraîner la génération incorrecte du fichier journal.

* Lors de la création d’un programme, le nom suggéré renvoyait parfois un doublon d’un nom de programme existant.

* Certains journaux d’étape de pipeline volumineux n’ont pas pu être téléchargés de manière cohérente via l’interface utilisateur.

* La validation des noms d’environnement comportait une erreur de décalage d’une unité.

* La page Environnements affichait parfois des segments de publication et de Dispatcher lorsqu’aucun segment n’était présent.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* La prise en charge de la recherche des instances de workflow a été ajoutée en fonction du titre du workflow, du modèle de workflow, de l’état, de l’initiateur, du chemin d’accès à la charge utile et de la date de début. Voir [Instances des workflows de recherche](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html?lang=fr).

## Outil de transfert de contenu {#content-transfer-tool}

En savoir plus sur les nouveautés et les mises à jour de [Outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr) Version 1.1.12.

### Nouveautés {#what-is-new-ctt}

* Amélioration de l’expérience utilisateur des journaux. Horodatages ajoutés aux journaux d’extraction et d’importation. Message ajouté pour indiquer si les journaux sont vides.

### Correctifs {#ctt-bug-fixes}

* L’outil de transfert de contenu ignorait les fichiers de contenu si le jeu de migration contenait des chemins dont les noms de fichiers étaient partiellement similaires.
