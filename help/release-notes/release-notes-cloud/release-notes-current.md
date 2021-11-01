---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: f89fbf4e693fb1b17e8923dfcc6c9b4de92b536d
workflow-type: tm+mt
source-wordcount: '1928'
ht-degree: 34%

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

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle (2021.9.0) est le 6 octobre 2021.
La version suivante (2021.10.0) date du 4 novembre 2021.

## Vidéo de publication {#release-video}

Consultez la section [Présentation de la version de septembre 2021](https://video.tv.adobe.com/v/337381) vidéo pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelle fonctionnalité dans la [!DNL Sites] canal prerrelease {#sites-prerelease-features}

* Les modèles de fragment de contenu sont désormais automatiquement définis en lecture seule une fois publiés, afin d’éviter de rompre involontairement les requêtes d’API en direct après la republication d’un modèle modifié. Les utilisateurs sont avertis lorsqu’ils tentent de modifier un modèle publié. La modification est possible lorsque vous acceptez l’avertissement.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* L’annotation des fichiers de PDF est désormais prise en charge à l’aide des outils de commentaires et d’annotation natifs de Adobe Document Cloud. Annotez le contenu du PDF en ajoutant du texte, des surbrillances, des post-it et des dessins directement dans la fenêtre d’aperçu du document. Les utilisateurs peuvent également accéder aux pages du PDF qui les intéressent en cliquant sur des commentaires spécifiques.

* Les utilisateurs peuvent désormais trier les ressources affichées dans les résultats de recherche en mode Colonnes et Carte. Le tri fonctionne sur les colonnes Nom, Créé, Modifié ou Aucun.

   ![Trier les résultats de la recherche dans [!DNL Assets] en mode Colonnes et Carte](/help/assets/assets/sort-searched-assets.png)
   *Figure : Trier les résultats de la recherche dans [!DNL Assets] en mode Colonnes et Carte.*

### Nouvelle fonctionnalité dans la [!DNL Assets] canal prerrelease {#assets-prerelease-features}

* [!DNL Assets] comprend désormais un connecteur intégré à [!DNL Azure Media Services] pour la transcription audio et vidéo. Une fois configurés, les fichiers pris en charge sont automatiquement transcrits et générés les fichiers WebVTT. Les sous-titres WebVTT sont utilisés pour une recherche, un sous-titrage ou une traduction plus efficaces à utiliser comme sous-titres.

<!-- TBD: 'Unpublishing' this feature as suggested by engineering.

* To programmatically invoke processing using asset microservices, a new API is introduced. Developers can now apply an existing folder-level processing profile on one or more specific assets in a folder. The processing profile gets applied based on custom metadata properties updates. See `AssetProcessor` in the [[!DNL Experience Manager] API reference](https://www.adobe.io/experience-manager/reference-materials/). As before, it is possible to [use asset microservices from the user interface](/help/assets/asset-microservices-configure-and-use.md).

-->
<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep prerelease channel.
A/V transcription feature via CQ-4303854 has moved to Oct prerelease now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés d’[!DNL Forms]  {#what-is-new-forms-sep-2021}

* **Utilisation des rôles Adobe Sign dans un formulaire adaptatif** : les niveaux de service professionnel et entreprise d’Adobe Sign offrent la possibilité d’étendre les rôles des destinataires du contrat au-delà du simple signataire, afin de mieux répondre aux exigences de leur workflow. Vous pouvez désormais [permettre à chaque destinataire de contrat de configurer son rôle dans un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html#addsignerstoanadaptiveform), avec le rôle Signer par défaut.

* **Analytics pour les formulaires adaptatifs**[ : vous pouvez désormais capturer et suivre le comportement de l’utilisateur final via Adobe Analytics pour les formulaires adaptatifs afin de rassembler les informations sur l’utilisateur final. ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/integrate-aem-forms-with-adobe-analytics.html) Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

* **Connectez facilement AEM Forms à Microsoft Dynamics et à Salesforce** : le service fournit des modèles de données et de configuration de source de données prêts à l’emploi pour Microsoft Dynamics et Salesforce, ce qui permet aux développeurs de configurer [plus rapidement et plus facilement Microsoft Dynamics et Salesforce en tant que sources de données pour un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html?lang=en).

* **Signature électronique d’un formulaire adaptatif à l’aide de DocuSign :**[ vous pouvez utiliser DocuSign pour signer électroniquement un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/integrate-docusign-adaptive-forms.html). Le service fournit une action d’envoi personnalisée pour utiliser DocuSign avec un formulaire adaptatif.

### Fonctionnalités bêta de [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **Connecteur de stockage unifié :** utilisez le connecteur de stockage unifié pour externaliser les données en cours de traitement dans les référentiels gérés par le client. Par exemple, vous pouvez effectuer les actions suivantes : stocker des données de processus AEM en cours de traitement (AEM données de variables de processus) qui contiennent des données personnelles sensibles (SPD) dans un référentiel géré par le client ;

   <!--* Enable Forms Portal’s save and resume functionality and store adaptive forms drafts in a customer-managed data repository.-->

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API de communication](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html?lang=en) vous permettent de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :
   * Générer des documents en complétant des fichiers de modèle avec des données XML
   * Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs
   * Générer des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat

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

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### Nouveautés {#what-is-new-screens}

* Screens as a Cloud Service prend désormais en charge la surveillance de lecture de base. Le lecteur signale désormais diverses mesures de lecture pour chaque ping (30 secondes par défaut). Les mesures permettent de détecter différents cas de figure (lecture bloquée, écran vide, problème de time-code, etc.). Cette fonctionnalité permet à l’équipe concernée de surveiller à distance si un lecteur lit correctement du contenu, d’améliorer sa réactivité en cas d’écran vide ou d’interruption d’expérience et de réduire les risques d’offrir une expérience bancale à l’utilisateur final.
Pour plus d’informations, voir [Suivi de base de la lecture](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html?lang=en#playback-monitoring).

* Prise en charge des miniatures pour les vidéos dans désormais pris en charge dans Screens as a Cloud Service. Un auteur de contenu peut définir une miniature de vidéos afin de pouvoir utiliser l’image en tant qu’espace réservé et de pouvoir tester correctement la lecture et le ciblage du contenu, alors que l’équipe concernée peut s’occuper de la finalisation de la vidéo elle-même. L’image peut également être utilisée au cas où la lecture de la vidéo échouerait.
Pour plus d’informations, voir [Prise en charge des miniatures de vidéos](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html).

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

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] propose désormais plusieurs types de fonctionnalités de mise en réseau avancées, notamment :

* Sortie de port flexible pour libérer le trafic des ports non standard. Maintenant possible sans contacter l’assistance Adobe.
* Adresse IP sortante dédiée pour évacuer le trafic AEM as a Cloud Service à partir d’une adresse IP unique, prenant désormais en charge tous les ports.
* VPN pour sécuriser le trafic entre votre infrastructure et AEM as a Cloud Service.

Lisez le [documentation](/help/security/configuring-advanced-networking.md) pour plus d’informations, notamment sur la manière de mettre en service une mise en réseau avancée à l’aide des API Cloud Manager.

**Optimisations des index**

Pour améliorer les performances des requêtes de recherche et de l’indexation, l’index de texte intégral lucene-2 n’est plus utilisé clé en main dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] de cette version. Afin de supprimer cet index de texte intégral sur les environnements AEM conformément aux clients AEM, Adobe Engineering travaille individuellement et de manière proactive avec les clients pour une suppression douce et durable de l’index de texte intégral Lucene. Veuillez consulter le [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] [documentation](/help/operations/indexing.md#index-optimizations) pour plus d&#39;informations, contactez directement notre service clientèle si vous avez des questions.

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.10.0 et 2021.9.0.

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

## Date de publication {#release-date-cm-sept}

La date de publication de Cloud Manager dans AEM version as a Cloud Service 2021.9.0 est le 9 septembre 2021.

### Correctifs {#bug-fixes-cm-oct}

* Dans de rares cas, lorsqu’un Adobe restaurait l’environnement d’un client, la restauration était considérée comme terminée avant que l’environnement ne soit complètement opérationnel.

* Certaines demandes internes effectuées lors de la création de l’environnement n’ont pas été retraitées.

* Si l’erreur de déploiement échoue à la suite de la vérification du nom de domaine, le message d’erreur a été corrigé afin de demander au client de contacter son représentant Adobe.


### Nouveautés {#what-is-new-cm-sept}

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 30.

* Les cartes de programme de la page d’entrée de Cloud Manager et l’expérience associée ont été actualisées.

* Le journal des étapes de qualité du code comprend désormais des informations de journalisation en mode verbeux sur le processus d’analyse OakPal.

* Les options de menu de la page Activité comprennent désormais une option permettant d’afficher la variable **Journal de téléchargement** pour les exécutions du Générateur de code terminées. Si vous sélectionnez cette option, le journal de l’étape de compilation sera téléchargé.

* Cliquez directement sur la carte Programme pour accéder à la page Aperçu de Cloud Manager.

### Correctifs {#bug-fixes-sept}

* L’utilisateur voit désormais un message plus compréhensible lorsqu’il tente d’ajouter une nouvelle Liste autorisée IP dans un programme qui a atteint le nombre maximal autorisé de Listes autorisées IP configurables.

* Une URL erronée a été copiée lors de la sélection de l’option de menu Copier l’URL dans l’écran Référentiels.

## Cloud Acceleration Manager {#cam}

### Date de publication {#release-date-october-cam}

La date de publication de Cloud Acceleration Manager est le 4 octobre 2021.

### Nouveautés {#what-is-new-cam}

* Cloud Acceleration Manager permet désormais aux utilisateurs d’afficher les rapports BPA dans un aperçu imprimable, ce qui permet une impression ou une impression simples à PDF pour une partageabilité facile. Reportez-vous aux étapes 6 et 7 de la section [Utilisation de la carte d’analyse des bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu v1.6.0 est le 4 octobre 2021.

### Nouveautés {#what-is-new-ctt}

* Amélioration de l’outil de mappage des utilisateurs avec une expérience utilisateur simplifiée, y compris les fonctionnalités suivantes répertoriées ci-dessous. Pour plus d’informations, reportez-vous à la section [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html).
   * Tester la connexion à l’API User Management avant d’exécuter le mappage utilisateur
   * Ignorer les erreurs et poursuivre avec élégance l’activité Mappage des utilisateurs
   * Le mappage utilisateur n’échoue plus si **Jeton d’accès** expire après 24 heures. Le mappage utilisateur peut être exécuté à nouveau à partir de l’endroit où il s’est arrêté pour la dernière fois.

* Pour accroître la robustesse de l’outil de transfert de contenu, le contenu peut être ingéré simultanément sur l’instance d’auteur ou l’instance de publication. Voir [Prise en main de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) pour plus d’informations.

* Lorsque des versions sont incluses, le chemin d’accès `/var/audit` est automatiquement inclus pour migrer les événements de contrôle.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa-latest}

La date de publication de la version 2.1.20 de l’analyseur des bonnes pratiques est le 5 octobre 2021.

### Nouveautés {#what-is-new}

* Possibilité de détecter et de générer des rapports sur la longueur du nom de noeud.

* Capacité à détecter et à générer des rapports sur la taille totale de l’index.

* Possibilité de détecter et de générer des rapports sur les ressources dont le rendu d’origine manque.

