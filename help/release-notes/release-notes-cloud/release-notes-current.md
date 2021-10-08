---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 5f80ad85ddf9ffdda7cd975d00699eb5085d2365
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 40%

---


# Notes de mise à jour actuelles pour[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour générales de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes. par exemple, pour ceux de 2020, 2021, etc.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] en tant que [!DNL Cloud Service] (2021.9.0) est le 6 octobre 2021.
La version suivante (2021.10.0) date du 28 octobre 2021.

## Vidéo de publication {#release-video}

Regardez la vidéo [Présentation de la version de septembre 2021](https://video.tv.adobe.com/v/337381) pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelle fonctionnalité du canal de version préliminaire [!DNL Sites] {#sites-prerelease-features}

* Les modèles de fragment de contenu sont désormais automatiquement définis en lecture seule une fois publiés, afin d’éviter de rompre involontairement les requêtes d’API en direct après la republication d’un modèle modifié. Les utilisateurs sont avertis lorsqu’ils tentent de modifier un modèle publié. La modification est possible lorsque vous acceptez l’avertissement.

## [!DNL Experience Manager Assets] as a  [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Les utilisateurs peuvent désormais trier les ressources affichées dans les résultats de recherche en mode Colonnes et Carte. Le tri fonctionne sur les colonnes Nom, Créé, Modifié ou Aucun.

   ![Trier les résultats de la recherche  [!DNL Assets] en mode Colonnes et Carte](/help/assets/assets/sort-searched-assets.png)
   *Figure : Triez les résultats de la recherche  [!DNL Assets] en mode Colonnes et Carte.*

<!-- TBD: 'Unpublishing' this feature as suggested by engineering.

* To programmatically invoke processing using asset microservices, a new API is introduced. Developers can now apply an existing folder-level processing profile on one or more specific assets in a folder. The processing profile gets applied based on custom metadata properties updates. See `AssetProcessor` in the [[!DNL Experience Manager] API reference](https://www.adobe.io/experience-manager/reference-materials/). As before, it is possible to [use asset microservices from the user interface](/help/assets/asset-microservices-configure-and-use.md).

-->
<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep beta channel.
A/V transcription feature via CQ-4303854 has moved to Oct beta now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms-sep-2021}

* **Utilisation des rôles Adobe Sign dans un formulaire adaptatif** : les niveaux de service professionnel et entreprise d’Adobe Sign offrent la possibilité d’étendre les rôles des destinataires du contrat au-delà du simple signataire, afin de mieux répondre aux exigences de leur workflow. Vous pouvez désormais [permettre à chaque destinataire de contrat de configurer son rôle dans un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html#addsignerstoanadaptiveform), avec le rôle Signer par défaut.

* **Analytics pour les formulaires adaptatifs** : vous pouvez désormais capturer et suivre le comportement de l’utilisateur final via Adobe Analytics pour les formulaires adaptatifs afin de rassembler les informations sur l’utilisateur final. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

* **Connectez facilement AEM Forms à Microsoft Dynamics et à Salesforce** : le service fournit des modèles de données et de configuration de source de données prêts à l’emploi pour Microsoft Dynamics et Salesforce, ce qui permet aux développeurs de configurer [plus rapidement et plus facilement Microsoft Dynamics et Salesforce en tant que sources de données pour un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html?lang=en).

* **Signer électroniquement un formulaire adaptatif à l’aide de DocuSign :**  vous pouvez utiliser DocuSign pour signer électroniquement un formulaire adaptatif. Le service fournit une action d’envoi personnalisée pour utiliser DocuSign avec un formulaire adaptatif.

### Fonctionnalités bêta de [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **Connecteur de stockage unifié :** utilisez le connecteur de stockage unifié pour externaliser les données en cours de traitement dans les référentiels gérés par le client. Par exemple, vous pouvez effectuer les actions suivantes : stocker des données de processus AEM en cours de traitement (AEM données de variables de processus) qui contiennent des données personnelles sensibles (SPD) dans un référentiel géré par le client ;

   <!--* Enable Forms Portal’s save and resume functionality and store adaptive forms drafts in a customer-managed data repository.-->

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API Communications](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html?lang=en) vous permet de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :
   * Générer des documents en complétant des fichiers de modèle avec des données XML.
   * Générer des formulaires dans divers formats, y compris les flux d’impression PDF non interactifs.
   * Générer des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat.

Vous pouvez écrire à [!DNL formscsbeta@adobe.com] pour vous inscrire au programme bêta.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Le nouvel onglet &quot;Contenu commercial associé&quot; dans l’éditeur de sites améliore l’efficacité de l’auteur en accédant rapidement au contenu produit AEM approprié pour le contexte actuel.

   ![Contenu commercial associé](/help/assets/CIF/associated-commerce-content.png)

* Amélioration de l’interface utilisateur du sélecteur de produits pour une meilleure expérience utilisateur, une efficacité accrue et une prise en charge du catalogue de produits complexe

   ![Nouveau sélecteur de produits](/help/assets/CIF/product-picker.png)

* Respect de la propriété &quot;include_in_menu&quot; dans le composant de navigation

### Correctifs {#bug-fixes-cif}

* Le vidage du cache du menu ne fonctionne pas comme prévu.

* Erreurs JS lors de l’étape de déploiement AEM CS et lorsque vous n’utilisez pas les composants côté client

* Impossible de créer une configuration cloud CIF dans les dossiers comportant un noeud sling:configs

## [!DNL Experience Manager Screens] as a  [!DNL Cloud Service] {#screens}

### Nouveautés {#what-is-new-screens}

* Screens as a Cloud Service prend désormais en charge la surveillance de lecture de base. Le lecteur signale désormais diverses mesures de lecture pour chaque ping (30 secondes par défaut). Les mesures permettent de détecter différents cas de figure (lecture bloquée, écran vide, problème de time-code, etc.). Cette fonctionnalité permet à l’équipe concernée de surveiller à distance si un lecteur lit correctement du contenu, d’améliorer sa réactivité en cas d’écran vide ou d’interruption d’expérience et de réduire les risques d’offrir une expérience bancale à l’utilisateur final.
Voir [Surveillance de lecture de base](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html?lang=en#playback-monitoring) pour plus d’informations.

* Prise en charge des miniatures pour les vidéos dans désormais pris en charge dans Screens as a Cloud Service. Un auteur de contenu peut définir une miniature de vidéos afin de pouvoir utiliser l’image en tant qu’espace réservé et de pouvoir tester correctement la lecture et le ciblage du contenu, alors que l’équipe concernée peut s’occuper de la finalisation de la vidéo elle-même. L’image peut également être utilisée au cas où la lecture de la vidéo échouerait.
Pour plus d’informations, voir [Prise en charge des miniatures pour les vidéos](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html) .

### Correctifs {#bug-fixes-screens}

* Le lecteur n’a pas pu afficher le contenu de la page incorporée et ce problème a été corrigé.

* Une fois la connexion établie, la navigation vers la page par défaut (canaux) a abouti à une page d’erreur interne du serveur.

* Les entrées de balise associées n’ont pas été supprimées lors de la suppression des listes de lecture.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Nouvelles fonctionnalités de [!DNL Experience Manager as a Cloud Service] {#foundation-features}

**Mise en réseau avancée**

>[!INFO]
>
>La fonctionnalité de mise en réseau avancée fait partie de la version 2021.9.0 et sera activée pour les clients à la mi-octobre.

[!DNL Adobe Experience Manager] as a propose  [!DNL Cloud Service] désormais plusieurs types de fonctionnalités de mise en réseau avancées, notamment :

* Sortie de port flexible pour libérer le trafic des ports non standard. Maintenant possible sans contacter l’assistance Adobe.
* Adresse IP sortante dédiée pour évacuer le trafic AEM as a Cloud Service à partir d’une adresse IP unique, prenant désormais en charge tous les ports.
* VPN pour sécuriser le trafic entre votre infrastructure et AEM as a Cloud Service.

Pour plus d’informations, notamment sur la mise en réseau avancée en libre-service à l’aide des API de Cloud Manager, consultez la [documentation](/help/security/configuring-advanced-networking.md) .

**Optimisations des index**

Pour améliorer les performances des requêtes de recherche et de l’indexation, l’index de texte intégral lucene-2 n’est plus inclus dans la balise [!DNL Adobe Experience Manager] de cette version. [!DNL Cloud Service] Afin de supprimer cet index de texte intégral sur les environnements AEM conformément aux clients AEM, Adobe Engineering travaille individuellement et de manière proactive avec les clients pour une suppression douce et durable de l’index de texte intégral Lucene. Pour plus d’informations, consultez la [!DNL Adobe Experience Manager] [!DNL Cloud Service] [documentation](/help/operations/indexing.md#index-optimizations) et contactez directement notre service clientèle si vous avez des questions.

## Cloud Manager  {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.9.0 et 2021.8.0.

## Date de publication {#release-date-cm-sept}

La date de publication de Cloud Manager dans AEM version as a Cloud Service 2021.9.0 est le 9 septembre 2021.
La prochaine version est prévue pour le 7 octobre 2021.

### Nouveautés {#what-is-new-cm-sept}

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 30.

* Les cartes de programme de la page d’entrée de Cloud Manager et l’expérience associée ont été actualisées.

* Le journal des étapes de qualité du code comprend désormais des informations de journalisation en mode verbeux sur le processus d’analyse OakPal.

* Les options de menu de la page Activité comprennent désormais une option **Télécharger le journal** pour les exécutions du Générateur de code terminées. Si vous sélectionnez cette option, le journal de l’étape de compilation sera téléchargé.

* Cliquez directement sur la carte Programme pour accéder à la page Aperçu de Cloud Manager.

### Correctifs {#bug-fixes-sept}

* L’utilisateur voit désormais un message plus compréhensible lorsqu’il tente d’ajouter une nouvelle Liste autorisée IP dans un programme qui a atteint le nombre maximal autorisé de Listes autorisées IP configurables.

* Une URL erronée a été copiée lors de la sélection de l’option de menu Copier l’URL dans l’écran Référentiels.

## Cloud Accelerated Manager {#cam}

### Date de publication {#release-date-october-cam}

La date de publication de Cloud Acceleration Manager est le 4 octobre 2021.

### Nouveautés {#what-is-new-cam}

* Cloud Acceleration Manager permet désormais aux utilisateurs d’afficher les rapports BPA dans un aperçu imprimable, ce qui permet une impression ou une impression simples à PDF pour une partageabilité facile. Reportez-vous aux étapes 6 et 7 de la section [Utilisation de la carte d’analyse des bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu v1.6.0 est le 4 octobre 2021.

### Nouveautés {#what-is-new-ctt}

* Amélioration du mappage des utilisateurs avec une expérience utilisateur simplifiée, y compris les fonctionnalités suivantes répertoriées ci-dessous. Pour plus d’informations, voir [Utilisation de l’outil de mappage utilisateur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr#using-user-mapping-tool).
   * Tester la connexion à l’API User Management avant d’exécuter le mappage utilisateur
   * Ignorer les erreurs et poursuivre avec élégance l’activité Mappage des utilisateurs
   * Le mappage utilisateur n’échoue plus si le jeton d’accès expire (après 24 heures). Le mappage utilisateur peut être exécuté à nouveau à partir de l’endroit où il s’est arrêté pour la dernière fois.

* Pour accroître la robustesse du CTT, le contenu peut être ingéré simultanément sur l’instance d’auteur ou l’instance de publication.

* Lorsque des versions sont incluses, le chemin `/var/audit` est automatiquement inclus pour migrer les événements de contrôle.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa-latest}

La date de publication de la version 2.1.18 de l’analyseur des bonnes pratiques est le 2 septembre 2021.

### Nouveautés {#what-is-new}

* Possibilité de détecter et de générer des rapports sur le nombre total de noeuds.

* Possibilité de détecter et de générer des rapports sur le type et la taille du magasin de noeuds.

### Correctifs {#bug-fixes-bpa}

* BPA détectait faussement la présence de Commerce Integration Framework.
