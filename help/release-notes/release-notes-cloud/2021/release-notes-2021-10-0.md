---
title: Notes de mise à jour de la version 2021.10.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour de la version 2021.10.0 d’ [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: ab584923-5f06-4b54-941b-e00bc1158b81
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 93%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes ; par exemple, celles de 2020, 2021 et ainsi de suite.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2021.10.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 4 novembre 2021.
La version suivante (2021.11.0) date du 2 décembre 2021.

## Vidéo de mise à jour {#release-video}

Regardez la vidéo [Aperçu de la mise à jour d’octobre 2021](https://video.tv.adobe.com/v/338253) pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelle fonctionnalité dans [!DNL Sites] {#sites-features}

* Les modèles de fragment de contenu sont désormais automatiquement définis en lecture seule une fois publiés, afin d’éviter de rompre involontairement les requêtes d’API actives après la republication d’un modèle modifié. Les utilisateurs sont avertis lorsqu’ils tentent de modifier un modèle publié. La modification est possible lorsque vous acceptez l’avertissement.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* [!DNL Experience Manager] prend désormais en charge la génération automatique de transcriptions de texte à partir des ressources audio et vidéo prises en charge, à l’aide d’un connecteur intégré à [!DNL Azure Media Services]. Les [types de fichiers pris en charge](/help/assets/file-format-support.md#audio-video-transcription-formats) sont automatiquement transcrits et le texte est stocké au format WebVTT. Les sous-titres WebVTT sont utilisés pour une recherche, un sous-titrage ou une traduction plus efficaces. En outre, la fonctionnalité améliore l’accessibilité, la facilité de découverte et la localisation des ressources.

### Nouvelle fonctionnalité dans le canal de version préliminaire [!DNL Assets] {#assets-prerelease-features}

* Le recadrage intelligent et l’échantillon d’images [!DNL Dynamic Media] sont désormais optimisés par les derniers services d’IA, qui génèrent des recadrages et des échantillons améliorés. Une amélioration a également été lancée afin de générer un contenu de recadrage différent, pour les mêmes proportions mais avec des résolutions différentes. En outre, les modifications manuelles sont conservées lors du retraitement, si la largeur et la hauteur du profil d’image ne changent pas.

* Les balises intelligentes sont automatiquement appliquées aux ressources à l’aide des microservices de ressources, au lieu des services de contenu dynamique. Le modèle sous-jacent est mis à jour afin d’améliorer les résultats du balisage et de réduire les biais. <!-- As it uses asset microservices, it is now possible to develop custom workers using Stock10-based Smart Tags. -->

<!-- Leave this commented.
### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Oct release. Details in CQDOC-18404.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms-oct-2021}

* **Analytics pour Forms adaptative** : vous pouvez désormais capturer et suivre le comportement des utilisateurs connectés et non connectés (anonymes) au moyen d’Adobe Analytics pour Forms adaptatif en vue de recueillir des informations sur les utilisateurs. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience client.

### Nouvelles fonctionnalités disponibles dans le canal de version préliminaire [!DNL Forms] {#prerelease-features-forms-oct-2021}

* **Externaliser les données des workflows AEM pour un traitement sécurisé** : vous pouvez stocker les données de workflows AEM (données de variables de workflows AEM) qui contiennent des éléments de données à caractère personnel dans un référentiel géré par le client pour un traitement sécurisé. Les éléments de données et les variables de workflows ne sont pas stockés dans le référentiel AEM et sont récupérés à la demande à partir d’un référentiel géré par le client lors du traitement du workflow.

### Fonctionnalités Beta de [!DNL Forms]  {#what-is-new-forms-oct2021-beta}

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API Communications](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html?lang=fr) vous permettent de combiner un modèle et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents dans les modes synchrone et par lots. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :

   * Générer des documents en renseignant les fichiers de modèle (PDF et XDP) avec des données XML
   * Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs

Vous pouvez écrire à [!DNL formscsbeta@adobe.com] pour vous inscrire au programme Beta.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Le module complémentaire CIF prend en charge la dernière version de Commerce v2.4.3 avec de nouveaux schémas et API GraphQL.

* Les auteurs peuvent ajouter des liens vers les pages de produits et de catalogues dans les champs de texte à l’aide de l’éditeur de texte enrichi (RTE). Une icône CIF a été ajoutée à la barre d’outils de l’éditeur de texte enrichi pour ouvrir les sélecteurs afin de rechercher et sélectionner rapidement le produit ou la catégorie sans quitter le contexte.

* Les fenêtres pop-up de panier et de passage en caisse existantes ont été remplacées par des pages de panier et de passage en caisse AEM dédiées. Les composants de ces pages sont créés à l’aide des composants Peregrine extensibles d’Adobe Commerce.

* Les commerces peuvent masquer certaines catégories de catalogues de produits lors de la navigation à l’aide du serveur principal de Commerce. Le composant principal de navigation CIF respecte la configuration du serveur principal de Commerce « inclure dans le menu » pour afficher/masquer les catégories dans la navigation.

* Le storefront Venia d’AEM renvoie une erreur HTTP 404 si la catégorie ou page produit est introuvable.

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans la version 2021.10.0. d’AEM as a Cloud Service.

### Date de publication {#release-date-cm-nov}

La date de publication de Cloud Manager dans la version 2021.11.0 d’AEM as a Cloud Service est le 4 novembre 2021.
La prochaine version est prévue pour le 09 décembre 2021.

### Nouveautés {#what-is-new-cm-nov}

* Les utilisateurs et utilisatrices peuvent désormais exploiter les nouveaux pipelines front-end pour déployer exclusivement le code front-end de manière accélérée. Voir [Pipelines frontaux de Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) pour en savoir plus.

  >[!IMPORTANT]
  >Vous devez être sur la version `2021.10.5933.20211012T154732Z` d’AEM pour tirer parti des nouveaux pipelines front-end.

* La durée du pipeline de qualité du code est considérablement réduite en exécutant l’analyse du code de manière plus efficace sans avoir à créer une image AEM entière. Cette modification sera déployée progressivement au cours des semaines qui suivront la publication de la version.

* L’ID de validation Git s’affiche désormais dans les détails d’exécution du pipeline, ce qui facilite le suivi du code créé.

* La création de programme est désormais disponible sur l’API publiquement exposée.

* La création d’environnement est désormais disponible sur l’API publiquement exposée.

* L’en-tête de réponse `x-request-id` est désormais visible dans le laboratoire de l’API sur [www.adobe.io](https://www.adobe.io/). Cet en-tête est utile pour signaler des problèmes à l’assistance clientèle à des fins de dépannage.

* La carte de pipeline affichée dans l’interface ne comporte aucune pipeline. Est-il possible d’obtenir des conseils appropriés ?

* Une nouvelle page d’activité est désormais disponible. Vous pouvez y afficher des activités telles que les exécutions de pipeline et de code, ainsi que les détails associés. Au fil du temps, les activités répertoriées dans cette page s’étendront, de même que les détails fournis.

* Une nouvelle page Pipelines avec une fenêtre contextuelle d’état et de survol permettant d’afficher facilement le résumé des détails est désormais disponible. Il est possible de visualiser les exécutions de pipelines avec les détails associés.

* L’API Modifier un pipeline prend désormais en charge la modification de l’environnement utilisé lors des phases de déploiement.

* Une optimisation du processus d’analyse OakPal a été introduite pour les packages volumineux.

* Le fichier CSV de problème de qualité contient désormais l’horodatage de chaque problème.

### Correctifs {#bug-fixes-nov}

* Certaines configurations de génération non orthodoxes entraînaient le stockage de fichiers inutiles dans le cache d’artefacts Maven du pipeline, ce qui entraînait des E/S réseau superflues lors du démarrage et de l’arrêt du conteneur de génération.

* L’API Pipeline PATCH échoue en l’absence de phase de déploiement.

* La règle de qualité `ClientlibProxyResourceCheck` générait des faux positifs en présence de bibliothèques clientes avec des chemins d’accès de base communs.

* Un message d’erreur indiquant que le nombre maximal de référentiels a été atteint ne précisait pas la raison de l’erreur.

* Dans de rares cas, les pipelines échouaient en raison d’une gestion inappropriée des reprises de certains codes de réponse.


## Date de publication {#release-date-cm-oct}

La date de publication de Cloud Manager dans la version 2021.10.0 d’AEM as a Cloud Service est le 14 octobre 2021.

### Nouveautés {#what-is-new-cm-oct}

* En vue de certaines modifications à venir, les pipelines de déploiement existants seront désormais référencés et étiquetés dans l’interface utilisateur en tant que pipelines **Full Stack**.

* La carte de pipeline a été actualisée afin d’afficher désormais une seule face intégrée qui affiche les pipelines de production et hors production. Vous pouvez sélectionner Exécuter/Arrêter/Reprendre directement dans le menu d’actions associé à chaque pipeline.

* Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service dans l’interface utilisateur.

* L’ajout et la modification des expériences de pipeline ont été actualisées afin d’utiliser désormais des modèles familiers et modernes.

* Les utilisateurs de Cloud Manager peuvent désormais envoyer leurs commentaires directement depuis l’interface utilisateur dans les **Commentaires** en haut à droite de la page de destination.

* Les graphiques SLA annuels peuvent désormais être téléchargés à partir de l’interface utilisateur de Cloud Manager.

* Les exécutions de pipeline de qualité de code et hors production utilisent désormais un processus de clonage superficiel plus efficace au cours de l’étape de création, ce qui accélère la création pour les clients disposant de référentiels Git particulièrement volumineux.

* L’assistant Ajouter une liste d’adresses IP autorisées informe désormais l’utilisateur si le nombre maximal de Listes d’adresses IP autorisées a été atteint.

* La documentation de l’API Cloud Manager comprend désormais un playground interactif qui permet aux utilisateurs connectés de tester l’API depuis leur navigateur. Consultez [Playground de l’API Cloud Manager](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) pour plus d’informations.

* L’info-bulle de la carte Programme offre plus d’informations si une option de sélection sous « Accéder à » est désactivée. Elle affiche désormais « Aucun environnement de production n’existe ».

### Correctifs {#bug-fixes-cm-oct}

* Dans de rares cas, lorsqu’un membre d’Adobe restaurait l’environnement d’un client, la restauration était considérée comme terminée avant que l’environnement ne soit complètement opérationnel.

* Certaines demandes internes effectuées lors de la création de l’environnement n’étaient pas retraitées.

* Si l’erreur de déploiement échouait suite à la vérification du nom de domaine, le message d’erreur a été corrigé afin de demander au client de contacter son représentant Adobe.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa-latest}

La date de publication de l’analyseur de bonnes pratiques v2.1.20 est le 5 octobre 2021.

### Nouveautés {#what-is-new}

* Capacité à détecter et à générer des rapports sur la longueur du nom de nœud.

* Capacité à détecter et à générer des rapports sur la taille totale de l’index.

* Capacité à détecter et à générer des rapports sur les ressources ne disposant pas d’un rendu d’origine.
