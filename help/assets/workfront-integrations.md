---
title: Intégration [!DNL Experience Manager Assets] avec  [!DNL Adobe Workfront]
description: Présentation de l’intégration entre  [!DNL Assets]  et  [!DNL Workfront]
role: Admin,Leader,Architect
feature: Integrations
exl-id: 365de3dc-51db-4dcf-94e2-104b5a5d33a8
source-git-commit: 5da4be3ec9af6a00cce8d80b8eea7f7520754a1d
workflow-type: tm+mt
source-wordcount: '1244'
ht-degree: 99%

---

# Intégration d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] [!DNL Assets] à [!DNL Adobe Workfront] {#assets-integration-overview}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-integrations.html) |
| AEM as a Cloud Service | Cet article |

[!DNL Adobe Workfront] est une application de gestion du travail qui vous permet de gérer l’ensemble du cycle de vie du travail en un seul endroit. L’intégration entre [!DNL Workfront] et [!DNL Adobe Experience Manager Assets] permet aux entreprises d’améliorer la vitesse du contenu et le délai de mise sur le marché en établissant des liens intrinsèques entre le travail et la gestion des ressources numériques. Dans le cadre de la gestion de leur travail dans Workfront, les utilisateurs ont accès aux documents et images requis.

Adobe offre la possibilité d’[intégrer  [!DNL Workfront]  et  [!DNL Adobe Experience Manager Assets]  de manière native (prise en charge d’Assets Essentials et d’Assets as a Cloud Service), ou à l’aide du connecteur amélioré Workfront pour Experience Manager](https://experienceleague.adobe.com/docs/workfront/using/documents/wf-aem-integrations/wf-aem-essentials/aem-asset-integrations.html?lang=fr). Dans le cas d’une intégration native, vous n’avez pas besoin de connecteur pour intégrer les deux solutions.

>[!NOTE]
>
>Adobe ne prend pas en charge l’utilisation en parallèle du connecteur amélioré Workfront pour Experience Manager et de l’intégration d’Experience Manager.

Grâce à l’intégration native d’Experience Manager et au [!DNL Workfront for Experience Manager enhanced connector], vous bénéficiez des fonctionnalités suivantes :

| Fonctionnalités natives d’[!DNL Adobe Experience Manager Assets] | Fonctionnalités de [!DNL Workfront for Experience Manager enhanced connector] |
|---|---|
| <ul><li>Configuration rapide de l’intégration dans Workfront.</li><li>Création automatique de dossiers liés entre Workfront et Experience Manager.</li><li>Synchronisation aisée des métadonnées pour les ressources liées existantes.</li><li>Mettez automatiquement à jour les métadonnées des projets lorsqu’elles sont modifiées dans Workfront.</li><li>Connectez facilement plusieurs référentiels Experience Manager Assets à un environnement Workfront ou plusieurs environnements Workfront à un référentiel Experience Manager Assets en utilisant plusieurs identifiants d’organisation.</li> | <ul><li>Créer automatiquement des dossiers Experience Manager liés dans Workfront et organiser les dossiers en fonction des portfolios, programmes et projets Workfront.</li><li>Synchroniser les métadonnées de projet Workfront avec les dossiers Experience Manager liés.</li><li>Mettre à jour des métadonnées d’Experience Manager avec de nouvelles versions.</li><li>Définir des statuts d’objet Workfront en fonction de conditions configurables à l’aide de workflows Experience Manager.</li><li>Publier des ressources dans l’environnement de publication d’Experience Manager ou dans Brand Portal.</li> |

Consultez les [fonctionnalités prises en charge ci-dessous pour effectuer une comparaison](#feature-parity-matrix) entre une intégration native ou une intégration à l’aide de connecteurs entre les deux solutions.



Consultez les sections relatives à la prise en charge de la plateforme et aux [conditions préalables pour le connecteur amélioré](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe requiert le déploiement et la configuration du [!DNL Adobe Workfront for Experience Manager enhanced connector] uniquement par le biais de partenaires certifiés ou d’[!DNL Adobe Professional Services]. S’il est déployé et configuré sans partenaire certifié ou sans [!DNL Adobe Professional Services], il n’est pas pris en charge par Adobe.
>
>* Adobe peut publier des mises à jour d’[!DNL Adobe Workfront] et d’[!DNL Adobe Experience Manager] qui rendent ce connecteur redondant ; si cela se produit, les clients peuvent être amenés à cesser d’utiliser ce connecteur.
>
>* Adobe prend en charge les versions 1.7.4 et supérieures du connecteur. Les versions précédentes et personnalisées ne sont pas prises en charge. Pour vérifier la version du connecteur amélioré, consultez l’étape 5(a) des [instructions d’installation du connecteur amélioré](workfront-connector-install.md).
>
>* Consultez la section [Examen de certification des partenaires pour Workfront pour le connecteur amélioré Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Pour plus d’informations sur l’examen, consultez le [Guide d’examen](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).


## Comparer les différentes intégrations entre [!DNL Assets] et [!DNL Workfront] {#feature-parity-matrix}

Vous trouverez ci-dessous les détails des fonctionnalités disponibles à travers différents types d’intégrations entre [!DNL Assets] et [!DNL Workfront].

| Fonctionnalité | Description | [!DNL Workfront] et [!DNL Assets Essentials] *Aucun connecteur (OOTB)* | [!DNL Workfront for Experience Manager enhanced connector] *Nécessite un connecteur* | Workfront et [!DNL Experience Manager as a Cloud Service] *Aucun connecteur (OOTB)* |
|----|----|----|-----|-----|
| Méthodes de déploiement | Approprié pour quelle offre [!DNL Assets]. | Assets Essentials | Adobe Managed Services, On-Premise | Cloud Service |
| **Général** |
| Envoyer des fichiers numériques depuis [!DNL Workfront] vers [!DNL Assets] | La dernière version d’un document WF peut être chargée vers AEM Assets, et sera liée en tant que nouvelle version du document. | ✓ | ✓ | ✓ |
| Lier manuellement des dossiers AEM à des objets Workfront | Les dossiers AEM existants peuvent être liés en tant que dossier Workfront. Ses ressources enfants sont liées en tant que nouveaux documents Workfront. | ✓ | ✓ | ✓ |
| Lier [!DNL Assets] aux objets Workfront | Les ressources existantes dans AEM peuvent être liées à un nouveau document Workfront ou à une nouvelle version d’un document existant. | ✓ | ✓ | ✓ |
| Envoyer automatiquement à AEM les ressources ajoutées aux dossiers liés | Si le document est ajouté à un dossier lié, la ressource associée est automatiquement chargée dans AEM Assets en tant que nouvelle ressource. | ✓ | ✓ | ✓ |
| Télécharger des ressources AEM Assets liées à partir de Workfront | Lorsqu’une ressource est liée dans Workfront, l’utilisateur peut télécharger les octets de la ressource. | ✓ | ✓ | ✓ |
| Rechercher des ressources AEM Assets à partir de Workfront | Le sélecteur AEM Assets de Workfront permet de rechercher des ressources en texte intégral. | ✓ | ✓ | ✓ |
| Rechercher des dossiers AEM à partir de Workfront | Le sélecteur AEM Assets de Workfront permet de rechercher des dossiers en texte intégral. | ✓ | ✓ | ✓ |
| Afficher et parcourir la hiérarchie des dossiers AEM à partir de Workfront | Le sélecteur AEM Assets de Workfront permet de parcourir la hiérarchie d’AEM Assets limitée par les contrôles d’accès et les autorisations associés à l’utilisateur ou l’utilisatrice définis dans AEM. | ✓ | ✓ | ✓ |
| Suivre les versions des ressources dans les chronologies AEM | Conserve l’historique des versions des documents entre Workfront et AEM. | ✓ | ✓ | ✓ |
| Dissocier des ressources d’AEM Assets dans Workfront | Une ressource liée existante provenant d’AEM peut être dissociée du document Workfront associé. Cela ne supprime pas la ressource d’origine dans AEM. | ✓ | ✓ | ✓ |
| Ajouter une ressource nouvellement versionnée à AEM Assets à partir de Workfront | Lorsqu’une nouvelle version est ajoutée à un document dans Workfront, un utilisateur peut envoyer la nouvelle version à AEM pour remplacer la version existante. | ✓ | ✓ | ✓ |
| Rediriger les utilisateurs vers AEM en cas de clic sur les ressources liées dans Workfront | Les utilisateurs sont redirigés vers AEM pour prévisualiser une ressource liée dans Workfront. | ✓ | ✓ | À venir |
| Créer automatiquement des dossiers AEM liés dans Workfront | Créez automatiquement des dossiers AEM liés dans Workfront à l’aide des statuts de projet. Configurez automatiquement les dossiers AEM en fonction des portfolios, programmes et projets Workfront. | Non | ✓ | Non |
| Naviguer directement vers les référentiels AEM à partir de Workfront | Permet aux utilisateurs et utilisatrices de naviguer vers les référentiels AEM disponibles configurés dans Workfront. | ✓ | Non | ✓ |
| Créer des dossiers AEM liés dans Workfront | Créez manuellement des dossiers AEM liés dans Workfront à l’aide de l’option disponible dans l’onglet Documents. | ✓ | Non | ✓ |
| Synchronisation des commentaires | Synchroniser automatiquement les commentaires des ressources de [!DNL Workfront] vers [!DNL Assets] | Non | ✓ | Non |
| Prendre en charge plusieurs environnements Workfront se connectant à un seul environnement AEM | Les utilisateurs et utilisatrices de plusieurs environnements Workfront peuvent se connecter à un seul environnement AEM. | ✓ | Non | ✓ |
| Prendre en charge plusieurs environnements AEM se connectant à un seul environnement Workfront | Les utilisateurs et utilisatrices d’un seul environnement Workfront peuvent envoyer ou lier des ressources entre plusieurs environnements AEM. | ✓ | ✓ | ✓ |
| **Métadonnées** |
| Mapper les métadonnées des ressources Workfront à AEM Assets | Les propriétés des formulaires personnalisés et des objets Workfront peuvent être mappées aux propriétés des métadonnées des ressources AEM. Les valeurs sont transmises lors du chargement ou de la liaison initial(e). | ✓ | ✓ | ✓ |
| Créer automatiquement des formulaires personnalisés pour les documents dans Workfront | Joignez des formulaires personnalisés aux documents, tâches et problèmes Workfront à l’aide des workflows AEM. | Non | ✓ | Non |
| Mise à jour automatique bidirectionnelle des métadonnées entre AEM Assets et Workfront | Mettez automatiquement à jour les métadonnées entre AEM Assets et Workfront. La ressource doit d’abord être transmise de Workfront à AEM et les métadonnées de la ressource Workfront doivent être mappées à AEM Assets pour que les mises à jour bidirectionnelles des métadonnées fonctionnent correctement. | Non | ✓ | Non |
| Affichage en temps réel dans Workfront des métadonnées mappées à AEM | Affichez les métadonnées mappées et mises à jour sur AEM dans les panneaux Détails du document et Résumé du document de Workfront. | ✓ | Non | ✓ |
| Transmission en temps réel des métadonnées Workfront mises à jour vers AEM | Mettez automatiquement à jour les métadonnées Workfront mappées à AEM sans transmettre à nouveau une ressource ou une nouvelle version d’une ressource. | ✓ | Non | ✓ |
| Mapper les métadonnées de Workfront aux dossiers AEM Assets | Synchronisez les métadonnées des projets Workfront avec les dossiers AEM liés. | Non | ✓ | ✓ |
| Mettre à jour les métadonnées AEM avec de nouvelles versions | Une configuration peut être effectuée dans AEM pour déterminer si une ressource nouvellement versionnée dans Workfront transmet également les modifications apportées à ses métadonnées. | Non | ✓ | Non |
| Mettre automatiquement à jour les métadonnées AEM lors des modifications apportées aux formulaires personnalisés dans Workfront | AEM vous permet de vous abonner aux mises à jour des formulaires de documents dans Workfront. Par conséquent, toute mise à jour apportée aux métadonnées du formulaire personnalisé du document Workfront modifie les valeurs des champs de métadonnées AEM mappés. | Non | ✓ | Non |
| **Workflows (prêts à l’emploi)** |
| Créer une version BAT sur les ressources liées | Lors de la liaison d’une ressource dans Workfront, un BAT peut être automatiquement généré. | Non | Personnalisé | Non |
| Définir le statut des objets Workfront | Définissez les statuts des objets Workfront en fonction de conditions configurables à l’aide de workflows AEM. | Non | ✓ | À venir |
| Publier des ressources dans lʼenvironnement de publication AEM ou dans Brand Portal | Cette fonctionnalité permet aux utilisateurs de Workfront de publier automatiquement les ressources liées dans un environnement de publication AEM ou dans Brand Portal. | Non | ✓ | À venir |
