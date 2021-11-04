---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 719ee458fee7d4b19907b8aaf51eb2f2e8062abd
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 17%

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

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle (2021.10.0) a été publiée le 4 novembre 2021.
La version suivante (2021.11.0) date du 2 décembre 2021.

## Vidéo de publication {#release-video}

Consultez la section [Présentation de la version d’octobre 2021](https://video.tv.adobe.com/v/338253) vidéo pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelle fonctionnalité dans [!DNL Sites] {#sites-features}

* Les modèles de fragment de contenu sont désormais automatiquement définis en lecture seule une fois publiés, afin d’éviter de rompre involontairement les requêtes d’API en direct après la republication d’un modèle modifié. Les utilisateurs sont avertis lorsqu’ils tentent de modifier un modèle publié. La modification est possible lorsque vous acceptez l’avertissement.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* [!DNL Experience Manager] prend désormais en charge la génération automatique de transcriptions de texte à partir des ressources audio et vidéo prises en charge, à l’aide d’un connecteur intégré vers [!DNL Azure Media Services]. Les fichiers pris en charge sont automatiquement transcrits et le texte est stocké au format WebVTT. Les sous-titres WebVTT sont utilisés pour une recherche, un sous-titrage ou une traduction plus efficaces. En outre, la fonctionnalité améliore l’accessibilité, la capacité de découverte et la localisation des ressources.

### Nouvelle fonctionnalité dans la [!DNL Assets] canal prerrelease {#assets-prerelease-features}

* [!DNL Dynamic Media] Le recadrage intelligent d’image et le nuancier sont désormais alimentés par les derniers services Sensei, qui génèrent des recadrages et des échantillons améliorés. Une amélioration a également été lancée afin de générer un contenu de recadrage différent, pour les mêmes proportions mais avec des résolutions différentes. En outre, les modifications manuelles seront conservées lors du retraitement, si la largeur et la hauteur du profil d’image ne changent pas.

* Les balises intelligentes sont automatiquement appliquées aux ressources à l’aide des microservices de ressources, au lieu des services de contenu dynamique. Le modèle sous-jacent est mis à jour afin d’améliorer les résultats du balisage et de réduire les biais. <!-- As it uses asset microservices, it is now possible to develop custom workers using Stock10-based Smart Tags. -->

<!-- Leave this commented.
### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Oct release. Details in CQDOC-18404.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés d’[!DNL Forms]  {#what-is-new-forms-oct-2021}

* **Analytics pour Forms adaptatif**: Vous pouvez désormais capturer et suivre le comportement des utilisateurs connectés et non connectés (anonymes) par le biais d’Adobe Analytics pour les Forms adaptatifs afin de rassembler les informations sur les utilisateurs finaux. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms-oct-2021}

* **Externaliser AEM données de workflow pour un traitement sécurisé**: Vous pouvez stocker des données AEM processus (AEM données des variables de processus) qui contiennent des éléments de données personnelles sensibles (SPD) dans un référentiel géré par le client pour un traitement sécurisé. Les éléments de données et les variables de workflow ne sont pas stockés dans AEM référentiel et sont récupérés à la demande à partir d’un référentiel géré par le client lors du traitement du workflow.

### Fonctionnalités bêta de [!DNL Forms] {#what-is-new-forms-oct2021-beta}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [API de communication](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) vous aide à combiner un modèle et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone et par lots. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   * Générez des documents en renseignant les fichiers de modèle (PDF et XDP) avec des données XML.
   * Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs

Vous pouvez écrire sur [!DNL formscsbeta@adobe.com] pour vous inscrire au programme bêta.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Le module complémentaire CIF prend en charge la dernière version de Commerce v2.4.3 avec de nouvelles API et schémas GraphQL.

* Les auteurs peuvent ajouter des liens vers des pages de produits et de catalogues dans des champs de texte à l’aide de l’éditeur de texte enrichi (RTE). Une icône CIF a été ajoutée à la barre d’outils de l’éditeur de texte enrichi pour ouvrir les sélecteurs afin de rechercher et sélectionner rapidement le produit ou la catégorie sans quitter le contexte.

* Le panier et le passage en caisse des fenêtres contextuelles existantes ont été remplacés par un panier AEM dédié et des pages de passage en caisse. Les composants de ces pages sont créés à l’aide des composants de périodicité extensibles du Magento.

* Les vendeurs peuvent masquer certaines catégories de catalogues de produits dans la navigation à l’aide du serveur principal Commerce. Le composant principal de navigation CIF respecte la configuration du serveur principal de commerce &quot;inclure dans le menu&quot; pour afficher/masquer les catégories dans la navigation.

* AEM Storefront Venia renvoie une erreur HTTP 404 si la page de catégorie ou de produit est introuvable

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.10.0.

## Date de publication {#release-date-cm-oct}

La date de publication de Cloud Manager dans AEM 2021.10.0 as a Cloud Service est le 14 octobre 2021.
La prochaine version est prévue pour le 4 novembre 2021.

### Nouveautés {#what-is-new-cm-oct}

* En vue de certaines modifications à venir, les pipelines de déploiement existants seront désormais référencés et étiquetés dans l’interface utilisateur comme **Pile complète** pipelines.

* La carte du pipeline a été actualisée afin d’afficher désormais une seule face intégrée qui affiche les pipelines de production et hors production. L’utilisateur peut sélectionner Exécuter/Pause/Reprendre directement dans le menu d’actions associé à chaque pipeline.

* Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service via l’interface utilisateur.

* L’ajout et la modification d’expériences de pipeline ont été actualisés afin d’utiliser désormais des modèles familiers et modernes.

* Les utilisateurs de Cloud Manager peuvent désormais envoyer leurs commentaires directement depuis l’interface utilisateur via le **Commentaires** en haut à droite de la landing page.

* Les graphiques SLA annuels peuvent désormais être téléchargés à partir de l’interface utilisateur de Cloud Manager.

* Les exécutions de pipeline de qualité de code et hors production utilisent désormais un processus de clonage superficiel plus efficace au cours de l’étape de création, ce qui accélère la création pour les clients disposant de référentiels Git particulièrement volumineux.

* L’assistant Ajouter une Liste autorisée IP informe désormais l’utilisateur si le nombre maximal autorisé de Listes autorisées IP a été atteint.

* La documentation de l’API Cloud Manager comprend désormais un terrain de lecture interactif qui permet aux utilisateurs connectés de tester l’API depuis leur navigateur. Voir [Playground de l’API Cloud Manager](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) pour plus d’informations.

* L’info-bulle de la carte Programme est plus descriptive si une option de sélection sous &quot;Accéder à&quot; est désactivée. Il affiche désormais &quot;Aucun environnement de production n’existe&quot;.

### Correctifs {#bug-fixes-cm-oct}

* Dans de rares cas, lorsqu’un Adobe restaurait l’environnement d’un client, la restauration était considérée comme terminée avant que l’environnement ne soit complètement opérationnel.

* Certaines demandes internes effectuées lors de la création de l’environnement n’ont pas été retraitées.

* Si l’erreur de déploiement échoue à la suite de la vérification du nom de domaine, le message d’erreur a été corrigé afin de demander au client de contacter son représentant Adobe.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa-latest}

La date de publication de la version 2.1.20 de l’analyseur des bonnes pratiques est le 5 octobre 2021.

### Nouveautés {#what-is-new}

* Possibilité de détecter et de générer des rapports sur la longueur du nom de noeud.

* Capacité à détecter et à générer des rapports sur la taille totale de l’index.

* Possibilité de détecter et de générer des rapports sur les ressources dont le rendu d’origine manque.
