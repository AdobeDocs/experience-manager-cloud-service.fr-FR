---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 4efac10fe32ef0aa0ab5a4de3f16c3f0dbf91551
workflow-type: tm+mt
source-wordcount: '1619'
ht-degree: 48%

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
La version suivante (2021.11.0) date du 16 décembre 2021.

## Vidéo de publication {#release-video}

Consultez la section [Présentation de la version d’octobre 2021](https://video.tv.adobe.com/v/338253) vidéo pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelle fonctionnalité dans [!DNL Sites] {#sites-features}

* Les modèles de fragment de contenu sont désormais automatiquement définis en lecture seule une fois publiés, afin d’éviter de rompre involontairement les requêtes d’API en direct après la republication d’un modèle modifié. Les utilisateurs sont avertis lorsqu’ils tentent de modifier un modèle publié. La modification est possible lorsque vous acceptez l’avertissement.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* [!DNL Experience Manager] prend désormais en charge la génération automatique de transcriptions de texte à partir des ressources audio et vidéo prises en charge, à l’aide d’un connecteur intégré vers [!DNL Azure Media Services]. Le [types de fichiers pris en charge](/help/assets/file-format-support.md#audio-video-transcription-formats) sont automatiquement transcrites et le texte est stocké au format WebVTT. Les sous-titres WebVTT sont utilisés pour une recherche, un sous-titrage ou une traduction plus efficaces. En outre, la fonctionnalité améliore l’accessibilité, la capacité de découverte et la localisation des ressources.

### Nouvelle fonctionnalité dans la [!DNL Assets] canal prerrelease {#assets-prerelease-features}

* [!DNL Dynamic Media] Le recadrage intelligent d’image et le nuancier sont désormais alimentés par les derniers services Sensei, qui génèrent des recadrages et des échantillons améliorés. Une amélioration a également été lancée afin de générer un contenu de recadrage différent, pour les mêmes proportions mais avec des résolutions différentes. En outre, les modifications manuelles seront conservées lors du retraitement, si la largeur et la hauteur du profil d’image ne changent pas.

* Les balises intelligentes sont automatiquement appliquées aux ressources à l’aide des microservices de ressources, au lieu des services de contenu dynamique. Le modèle sous-jacent est mis à jour afin d’améliorer les résultats du balisage et de réduire les biais. <!-- As it uses asset microservices, it is now possible to develop custom workers using Stock10-based Smart Tags. -->

<!-- Leave this commented.
### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Oct release. Details in CQDOC-18404.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms-oct-2021}

* **Analytics pour formulaires adaptatifs** : vous pouvez désormais capturer et suivre le comportement des utilisateurs connectés et non connectés (anonymes) par le biais d’Adobe Analytics pour formulaires adaptatifs en vue de recueillir des informations relatives aux utilisateurs finaux. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms-oct-2021}

* **Externaliser les données des workflows AEM pour un traitement sécurisé** : vous pouvez stocker les données de workflows AEM (données de variables de workflows AEM) qui contiennent des éléments de données à caractère personnel dans un référentiel géré par le client pour un traitement sécurisé. Les éléments de données et les variables de workflows ne sont pas stockés dans le référentiel AEM et sont récupérés à la demande à partir d’un référentiel géré par le client lors du traitement du workflow.

### Fonctionnalités bêta de [!DNL Forms] {#what-is-new-forms-oct2021-beta}

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API Communications](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) vous permettent de combiner un modèle et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents dans les modes synchrone et par lots. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   * Générer des documents en renseignant les fichiers de modèle (PDF et XDP) avec des données XML
   * Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs

Vous pouvez écrire à [!DNL formscsbeta@adobe.com] pour vous inscrire au programme bêta.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Le module complémentaire CIF prend en charge la dernière version de Commerce v2.4.3 avec de nouvelles API et schémas GraphQL.

* Les auteurs peuvent ajouter des liens vers des pages de produits et de catalogues dans des champs de texte à l’aide de l’éditeur de texte enrichi (RTE). Une icône CIF a été ajoutée à la barre d’outils de l’éditeur de texte enrichi pour ouvrir les sélecteurs afin de rechercher et sélectionner rapidement le produit ou la catégorie sans quitter le contexte.

* Le panier et le passage en caisse des fenêtres contextuelles existantes ont été remplacés par un panier AEM dédié et des pages de passage en caisse. Les composants de ces pages sont créés à l’aide des composants de périodicité extensibles du Magento.

* Les vendeurs peuvent masquer certaines catégories de catalogues de produits dans la navigation à l’aide du serveur principal Commerce. Le composant principal de navigation CIF respecte la configuration du serveur principal de commerce &quot;inclure dans le menu&quot; pour afficher/masquer les catégories dans la navigation.

* AEM Storefront Venia renvoie une erreur HTTP 404 si la page de catégorie ou de produit est introuvable

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.10.0.

### Date de publication {#release-date-cm-nov}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.11.0 est le 04 novembre 2021.
La prochaine version est prévue pour le 09 décembre 2021.

### Nouveautés {#what-is-new-cm-nov}

* Les utilisateurs peuvent désormais tirer parti des nouveaux pipelines front-end pour déployer le code front-end exclusivement de manière accélérée. Voir [Pipelines front-end de Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) pour en savoir plus.

   >[!IMPORTANT]
   >Vous devez être sur AEM version `2021.10.5933.20211012T154732Z` pour tirer parti des nouveaux pipelines front-end.

* La durée du pipeline de qualité du code est considérablement réduite en exécutant l’analyse du code de manière plus efficace sans avoir à créer une image AEM entière. Cette modification sera déployée progressivement au cours des semaines qui suivront la version.

* L’ID d’enregistrement Git s’affiche désormais dans les détails d’exécution du pipeline, ce qui facilite le suivi du code créé.

* La création de programme est désormais disponible via l’API publiquement exposée.

* La création d’environnement est désormais disponible via l’API publiquement exposée.

* L’en-tête de réponse `x-request-id` est désormais visible dans le laboratoire de l’API sur [www.adobe.io](https://www.adobe.io/). Cet en-tête est utile pour signaler des problèmes à l’assistance clientèle à des fins de dépannage.

* En tant qu’utilisateur, je vois une carte Pipeline sans pipeline. Pouvez-vous me fournir des conseils appropriés ?

* Une nouvelle page d’activité est désormais disponible. Vous pouvez y afficher des activités telles que les exécutions de pipeline et de code, ainsi que les détails associés. Au fil du temps, les activités répertoriées dans cette page s’étendront, de même que les détails fournis.

* Une nouvelle page Pipelines avec une fenêtre contextuelle d’état et de survol permettant d’afficher facilement le résumé des détails est désormais disponible. Il est possible de visualiser les exécutions de pipelines avec les détails associés.

* L’API Modifier un pipeline prend désormais en charge la modification de l’environnement utilisé lors des phases de déploiement.

* Une optimisation du processus d’analyse OakPal a été introduite pour les modules volumineux.

* Le fichier CSV de problème de qualité contient désormais l’horodatage de chaque problème.

### Correctifs {#bug-fixes-nov}

* Certaines configurations de génération non orthodoxes entraînaient le stockage de fichiers inutiles dans le cache d’artefacts Maven du pipeline, ce qui entraînait des E/S réseau superflues lors du démarrage et de l’arrêt du conteneur de génération.

* L’API Pipeline PATCH échoue en l’absence de phase de déploiement.

* La règle de qualité `ClientlibProxyResourceCheck` générait des faux positifs en présence de bibliothèques clientes avec des chemins d’accès de base communs.

* Un message d’erreur indiquant que le nombre maximal de référentiels a été atteint ne précisait pas la raison de l’erreur.

* Dans de rares cas, les pipelines échouaient en raison d’une gestion inappropriée des reprises de certains codes de réponse.


## Date de publication {#release-date-cm-oct}

La date de publication de Cloud Manager dans AEM 2021.10.0 as a Cloud Service est le 14 octobre 2021.

### Nouveautés {#what-is-new-cm-oct}

* En vue de certaines modifications à venir, les pipelines de déploiement existants seront désormais référencés et étiquetés dans l’interface utilisateur comme **Pile complète** pipelines.

* La carte Pipeline a été actualisée afin d’afficher désormais une seule face intégrée qui affiche les pipelines de production et hors production. L’utilisateur peut sélectionner Exécuter/Pause/Reprendre directement dans le menu d’actions associé à chaque pipeline.

* Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service via l’interface utilisateur.

* Les expériences d’ajout et de modification de pipeline ont été actualisées afin d’utiliser désormais des modèles familiers et modernes.

* Les utilisateurs de Cloud Manager peuvent désormais envoyer leurs commentaires directement depuis l’interface utilisateur via le **Commentaires** en haut à droite de la landing page.

* Les graphiques SLA annuels peuvent désormais être téléchargés à partir de l’interface utilisateur de Cloud Manager.

* Les exécutions de pipeline de qualité de code et hors production utilisent désormais un processus de clonage superficiel plus efficace au cours de l’étape de création, ce qui accélère la création pour les clients disposant de référentiels Git particulièrement volumineux.

* L’assistant Ajouter une Liste autorisée IP informe désormais l’utilisateur si le nombre maximal autorisé de Listes autorisées IP a été atteint.

* La documentation de l’API Cloud Manager comprend désormais un laboratoire interactif qui permet aux utilisateurs connectés de tester l’API depuis leur navigateur. Consultez [Laboratoire de l’API Cloud Manager](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) pour plus d’informations.

* L’info-bulle de la carte Programme offre des informations plus détaillées si une option de sélection est désactivée sous Accéder à. Il affiche désormais &quot;Aucun environnement de production n’existe&quot;.

### Correctifs {#bug-fixes-cm-oct}

* Dans de rares cas, lorsqu’un Adobe restaurait l’environnement d’un client, la restauration était considérée comme terminée avant que l’environnement ne soit complètement opérationnel.

* Certaines demandes internes effectuées lors de la création de l’environnement n’ont pas été retraitées.

* Si l’erreur de déploiement échoue à la suite de la vérification des noms de domaine, le message d’erreur a été corrigé afin de demander au client de contacter son représentant Adobe.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa-latest}

La date de publication de la version 2.1.20 de l’analyseur des bonnes pratiques est le 5 octobre 2021.

### Nouveautés {#what-is-new}

* Possibilité de détecter et de générer des rapports sur la longueur du nom de noeud.

* Capacité à détecter et à générer des rapports sur la taille totale de l’index.

* Possibilité de détecter et de générer des rapports sur les ressources dont le rendu d’origine manque.


## Analyseur des bonnes pratiques {#bpa-release}

### Date de publication {#release-date-bpa}

La date de publication de la version 2.1.2 de l’analyseur des bonnes pratiques est le 1er décembre 2021.

### Nouveautés {#what-is-new-bpa}

* Possibilité de détecter et de générer des rapports sur la version d’ACS commons utilisée.
* Possibilité de détecter et de générer des rapports sur le nombre d’utilisateurs et de sous-groupes d’un groupe.
* Possibilité de détecter et de générer des rapports sur les valeurs de propriété de noeud dans MongoDB dépassant 16 Mo.

### Correctifs {#bug-fixes-bpa}

* La détection des composants Foundation a été améliorée afin de réduire les faux négatifs.
* Pour les clients AEM Forms, message BPA concernant `EMAIL_PDF_SUBMIT_ACTION` n’étant pas disponible sur AEM as a Cloud Service a été corrigé.

## Outil de transfert de contenu {#ctt-release}

### Date de publication {#release-date-ctt}

La date de publication de l’outil de transfert de contenu v1.7.10 est le 8 décembre 2021.

### Nouveautés {#what-is-new-ctt}

* Activation/désactivation de l’ajout à la phase d’ingestion dans l’outil de transfert de contenu pour permettre aux utilisateurs de désactiver [pre-copy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr) pendant l’ingestion. Pour des vitesses d’ingestion optimales, la pré-copie lors de l’ingestion doit être désactivée pour les petits jeux de migration ou si seulement quelques objets Blob ont été ajoutés depuis la dernière ingestion.
* Mappage des utilisateurs mis à jour afin d’utiliser une API de gestion des utilisateurs améliorée qui lui permet d’obtenir 2 000 utilisateurs à la fois, ce qui améliore considérablement les performances.
