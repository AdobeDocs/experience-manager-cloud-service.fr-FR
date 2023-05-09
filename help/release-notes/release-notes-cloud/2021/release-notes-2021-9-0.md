---
title: Notes de mise à jour de la version 2021.9.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2021.9.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 8c12ff09-fbc8-42dd-87c0-46e509604f36
source-git-commit: cc6565121a76f70b958aa9050485e0553371f3a3
workflow-type: tm+mt
source-wordcount: '1572'
ht-degree: 99%

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

La date de publication de la version actuelle de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2021.9.0) est le mercredi 6 octobre 2021.
La version suivante (2021.10.0) date du 4 novembre 2021.

## Vidéo de mise à jour {#release-video}

Regardez la vidéo [Aperçu de la version de septembre 2021](https://video.tv.adobe.com/v/337381) pour un résumé des fonctionnalités ajoutées.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelle fonctionnalité dans le canal de version préliminaire [!DNL Sites] {#sites-prerelease-features}

* Les modèles de fragment de contenu sont désormais automatiquement définis en lecture seule une fois publiés, afin d’éviter de rompre involontairement les requêtes d’API en direct après la republication d’un modèle modifié. Les utilisateurs sont avertis lorsqu’ils tentent de modifier un modèle publié. La modification est possible lorsque vous acceptez l’avertissement.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de [!DNL Assets] {#assets-features}

* Les utilisateurs peuvent désormais trier en vue Colonne et Carte les ressources affichées dans les résultats de recherche. Le tri fonctionne sur les colonnes Nom, Créé, Modifié et Aucune.

   ![Trier les résultats de recherche dans [!DNL Assets] dans les vues Colonne et Carte](/help/assets/assets/sort-searched-assets.png)
   *Image : trier les résultats de recherche dans [!DNL Assets] dans les vues Colonne et Carte.*

* Pour appeler par programmation le traitement à l’aide des microservices de ressources, une nouvelle API est introduite. Les développeurs peuvent désormais appliquer un profil de traitement existant au niveau du dossier à une ou plusieurs ressources spécifiques d’un dossier. Le profil de traitement est appliqué en fonction des mises à jour des propriétés de métadonnées personnalisées. Voir `AssetProcessor` dans la [[!DNL Experience Manager] référence de l’API](https://www.adobe.io/experience-manager/reference-materials/). Comme auparavant, il est possible d’[utiliser les microservices de ressources à partir de l’interface utilisateur](/help/assets/asset-microservices-configure-and-use.md).

<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep beta channel.
A/V transcription feature via CQ-4303854 has moved to Oct beta now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouveautés de [!DNL Forms] {#what-is-new-forms-sep-2021}

* **Utilisation des rôles Adobe Sign dans un formulaire adaptatif** : les niveaux de service professionnel et entreprise d’Adobe Sign offrent la possibilité d’étendre les rôles des destinataires du contrat au-delà du simple signataire, afin de mieux répondre aux exigences de leur workflow. Vous pouvez désormais [permettre à chaque destinataire de contrat de configurer son rôle dans un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html?lang=fr#addsignerstoanadaptiveform), avec le rôle Signer par défaut.

* **Analytics pour les formulaires adaptatifs** : vous pouvez désormais capturer et suivre le comportement de l’utilisateur final via Adobe Analytics pour les formulaires adaptatifs afin de rassembler les informations sur l’utilisateur final. Il permet de prendre des décisions éclairées basées sur les données afin d’améliorer l’expérience de l’utilisateur final.

* **Connectez facilement AEM Forms à Microsoft Dynamics et à Salesforce** : le service fournit des modèles de données et de configuration de source de données prêts à l’emploi pour Microsoft Dynamics et Salesforce, ce qui permet aux développeurs de configurer [plus rapidement et plus facilement Microsoft Dynamics et Salesforce en tant que sources de données pour un formulaire adaptatif](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/use-form-data-model/configure-msdynamics-salesforce.html?lang=fr).

* **Signature électronique d’un formulaire adaptatif à l’aide de DocuSign :** vous pouvez utiliser DocuSign pour signer électroniquement un formulaire adaptatif. Le service fournit une action d’envoi personnalisée pour utiliser DocuSign avec un formulaire adaptatif. Vous pouvez installer le package disponible dans Distribution logicielle pour importer l’action d’envoi.

### Fonctionnalités bêta de [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **Connecteur de stockage unifié :** utilisez le connecteur de stockage unifié pour externaliser les données en cours de traitement dans les référentiels gérés par le client. Par exemple, vous pouvez effectuer les actions suivantes :
   * Activer la fonctionnalité d’enregistrement et de reprise de Forms Portal et stocker les brouillons de formulaires adaptatifs dans un référentiel de données géré par le client.
   * Stocker les données de workflows AEM en cours (données des variables de workflows AEM) qui contiennent des données personnelles sensibles (SPD) dans un référentiel géré par le client.

* **[!DNL AEM Forms as a Cloud Service - Communications]** : les [API de communication](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) vous permettent de combiner des modèles XDP et des données XML pour générer des documents d’impression dans différents formats. Le service vous permet de générer des documents en mode synchrone. Les API vous permettent de créer des applications grâce auxquelles vous pouvez accomplir les actions suivantes :
   * Générer des documents en complétant des fichiers de modèle avec des données XML
   * Générer des formulaires de sortie dans divers formats, y compris les flux d’impression PDF non interactifs
   * Générer des fichiers PDF d’impression à partir d’un formulaire XFA au format PDF et d’un formulaire Adobe Acrobat

Vous pouvez écrire à [!DNL formscsbeta@adobe.com] pour vous inscrire au programme bêta.

## Module complémentaire CIF {#cloud-services-cif}

### Nouveautés {#what-is-new-cif}

* Le nouvel onglet « Contenu commercial associé » dans l’éditeur de sites améliore l’efficacité de la création en permettant d’accéder rapidement au contenu produit AEM approprié pour le contexte actuel.

   ![Contenu commercial associé](/help/assets/CIF/associated-commerce-content.png)

* Amélioration de l’interface utilisateur du sélecteur de produits pour une meilleure expérience utilisateur, et l’optimisation de l’efficacité et de la prise en charge du catalogue de produits complexe

   ![Nouveau sélecteur de produits](/help/assets/CIF/product-picker.png)

* Respect de la propriété « include_in_menu » dans le composant de navigation

### Correctifs {#bug-fixes-cif}

* La purge du cache du menu ne fonctionne pas comme prévu.

* Erreurs JS lors de l’étape de déploiement d’AEM CS et lorsque vous n’utilisez pas les composants côté client

* Impossible de créer une configuration cloud CIF dans les dossiers comportant un nœud sling:configs

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### Nouveautés {#what-is-new-screens}

* Screens as a Cloud Service prend désormais en charge la surveillance de base de la lecture. Le lecteur signale désormais diverses mesures de lecture pour chaque ping (30 secondes par défaut). Les mesures permettent de détecter différents cas de figure (lecture bloquée, écran vide, problème de time-code, etc.). Cette fonctionnalité permet à l’équipe concernée de surveiller à distance si un lecteur lit correctement du contenu, d’améliorer sa réactivité en cas d’écran vide ou d’interruption d’expérience et de réduire les risques d’offrir une expérience bancale à l’utilisateur final.
Pour plus d’informations, voir [Suivi de base de la lecture](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html?lang=fr#playback-monitoring).

* Les miniatures pour les vidéos sont désormais prises en charge dans Screens as a Cloud Service. Un auteur de contenu peut définir une miniature de vidéos afin de pouvoir utiliser l’image en tant qu’espace réservé et de pouvoir tester correctement la lecture et le ciblage du contenu, alors que l’équipe concernée peut s’occuper de la finalisation de la vidéo elle-même. L’image peut également être utilisée au cas où la lecture de la vidéo échouerait.
Pour plus d’informations, voir [Prise en charge des miniatures de vidéos](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html?lang=fr).

### Correctifs {#bug-fixes-screens}

* Le lecteur ne pouvait pas afficher le contenu de la page incorporée et ce problème a été corrigé.

* Une fois la connexion établie, la navigation vers la page par défaut (vers les canaux) aboutissait à une page d’erreur interne du serveur.

* Les entrées de balise associées n’étaient pas supprimées lors de la suppression des listes de lecture.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Nouvelles fonctionnalités de [!DNL Experience Manager as a Cloud Service] {#foundation-features}

**Mise en réseau avancée**

>[!INFO]
>
>La fonctionnalité de mise en réseau avancée fait partie de la version 2021.9.0 et sera activée pour les clients à la mi-octobre.

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] propose désormais plusieurs types de fonctionnalités de mise en réseau avancées, notamment les éléments suivants :

* Une sortie de port flexible pour libérer le trafic des ports non standard. Maintenant possible sans contacter l’assistance Adobe.
* Une adresse IP sortante dédiée pour faire sortir le trafic d’AEM as a Cloud Service à partir d’une adresse IP unique et prenant désormais en charge tous les ports.
* Un VPN pour sécuriser le trafic entre votre infrastructure et AEM as a Cloud Service.

Lisez la [documentation](/help/security/configuring-advanced-networking.md) pour obtenir plus d’informations, notamment sur la manière de mettre en service une mise en réseau avancée à l’aide des API Cloud Manager.

**Optimisations des index**

Pour améliorer les performances des requêtes de recherche et de l’indexation, l’index de texte intégral lucene-2 n’est plus utilisé clé en main dans [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] à partir de cette version. Afin de supprimer cet index de texte intégral dans les environnements AEM en accord avec les clients AEM, l’ingénierie d’Adobe travaille individuellement et de manière proactive avec les clients pour permettre de supprimer de manière fluide et durable de l’index de texte intégral Lucene. Consultez la [documentation](/help/operations/indexing.md#index-optimizations) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] pour obtenir plus d’informations, contactez directement notre service clientèle si vous avez des questions.

## Cloud Manager {#cloud-manager}

Cette section présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.9.0 et 2021.8.0.

## Date de publication {#release-date-cm-sept}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.9.0 est le 9 septembre 2021.
La prochaine version est prévue pour le 7 octobre 2021.

### Nouveautés {#what-is-new-cm-sept}

* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 30.

* Les cartes de programme de la page d’entrée de Cloud Manager et l’expérience associée ont été actualisées.

* Le journal des étapes de qualité du code comprend désormais des informations de journalisation en mode verbeux sur le processus d’analyse OakPal.

* Les options de menu de la page Activité comprennent désormais une option **Télécharger le journal** pour les exécutions du générateur de code terminées. Si vous sélectionnez cette option, le journal de l’étape de compilation sera téléchargé.

* Cliquez directement sur la carte Programme pour accéder à la page Aperçu de Cloud Manager.

### Correctifs {#bug-fixes-sept}

* L’utilisateur voit désormais un message plus compréhensible lorsqu’il tente d’ajouter une nouvelle liste autorisée d’adresses IP dans un programme qui a atteint le nombre maximal autorisé de listes autorisées d’adresses IP configurables.

* Une URL erronée a été copiée lors de la sélection de l’option de menu Copier l’URL dans l’écran Référentiels.

## Cloud Acceleration Manager {#cam}

### Date de publication {#release-date-october-cam}

La date de publication de la mise à jour de Cloud Acceleration Manager est le 4 octobre 2021.

### Nouveautés {#what-is-new-cam}

* Cloud Acceleration Manager permet désormais aux utilisateurs d’afficher les rapports BPA dans un aperçu imprimable, ce qui permet d’exécuter simplement une impression ou une exportation PDF pour les partager facilement. Reportez-vous aux étapes 6 et 7 de la section [Utilisation de la carte d’analyse des bonnes pratiques](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=fr#best-practices-analysis).

## Outil de transfert de contenu {#content-transfer-tool}

### Date de publication {#release-date-ctt-latest}

La date de publication de l’outil de transfert de contenu version v1.6.0 est le 4 octobre 2021.

### Nouveautés {#what-is-new-ctt}

* Amélioration de l’outil de mappage des utilisateurs pour une expérience client simplifiée, notamment grâce aux fonctionnalités suivantes répertoriées ci-dessous. Pour plus d’informations, reportez-vous à la section [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr#using-user-mapping-tool).
   * Test de la connexion à l’API User Management avant d’exécuter le mappage des utilisateurs
   * Ignorer les erreurs de manière appropriée et poursuivre l’activité de mappage des utilisateurs
   * Le mappage des utilisateurs n’échoue plus si le Jeton d’accès expire (après 24 heures). Le mappage des utilisateurs peut être exécuté à nouveau à partir de l’endroit où il s’est arrêté pour la dernière fois.

* Pour améliorer la robustesse de l’outil de transfert de contenu (CTT), le contenu ne peut être ingéré que sur l’instance de création ou sur l’instance de publication au même moment.

* Lorsque différentes versions sont incluses, le chemin d’accès `/var/audit` est automatiquement inclus pour migrer les événements de contrôle.

## Analyseur des bonnes pratiques {#best-practices-analyzer}

### Date de publication {#release-date-bpa-latest}

La date de publication de Best Practices Analyzer v2.1.18 est le 02 septembre 2021.

### Nouveautés {#what-is-new}

* Possibilité de détecter et de générer des rapports sur le nombre total de nœuds.

* Possibilité de détecter et de générer des rapports sur le type et la taille du magasin de nœuds.

### Correctifs {#bug-fixes-bpa}

* BPA détectait faussement la présence de Commerce Integration Framework.
