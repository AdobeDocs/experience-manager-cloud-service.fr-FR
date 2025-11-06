---
title: Notes de mise à jour de la version 2023.8.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2023.8.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: a0ffa6cf-64ae-468c-93f4-ac6805ef907e
feature: Release Information
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1691'
ht-degree: 100%

---

# Notes de mise à jour de la version 2023.8.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version 2023.8.0 d’[!DNL Experience Manager] as a Cloud Service.

## Date de publication {#release-date}

La date de publication de la version actuelle (2023.8.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le 31 février 2023. La prochaine disponibilité des fonctionnalités (2023.9.0) est prévue pour le 28 mai 2023.

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Aperçu de la version de janvier 2023 pour un résumé des fonctionnalités ajoutées dans la version 2023.8.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3423535/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Experience Manager Sites] {#sites-features}

* La variable [Console de fragments de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=fr) permet désormais aux utilisateurs d’afficher les balises et de rechercher par balises appliquées en tant que métadonnées aux fragments de contenu. Les utilisateurs n’auront plus à passer à l’interface utilisateur d’Assets pour cette fonctionnalité, ce qui réduit le changement de contexte et améliore l’efficacité.

  ![Balisage dans la console de fragments de contenu](/help/assets/content-fragments-console-tags.png)
* Le nouvel éditeur de fragment de contenu est désormais disponible sur AEM as a Cloud Service. Cela permet aux auteurs de contenu d’être plus productifs en rationalisant leurs tâches de création et en réduisant la nécessité de basculer entre différentes applications lors de la modification du contenu.
  ![Boîte de dialogue modale Nouveau fragment de contenu.](/help/release-notes/assets/newCFEditor.png)

Le nouvel éditeur de fragment de contenu offre les avantages suivants, qui ne sont pas disponibles dans l’éditeur d’origine :

* Enregistrement automatique pour une meilleure efficacité de création et pour éviter toute perte accidentelle de modifications.
* Vue hiérarchique d’un fragment de contenu et de ses références à l’aide de l’arborescence Structure pour une navigation rapide au sein d’un fragment profondément structuré.
  ![Arborescence de structure dans l’éditeur de fragments de contenu](/help/release-notes/assets/newCFEditor_StructureTree.png)

* Chargement en ligne de ressources en tant que références de contenu sans devoir d’abord les charger dans la gestion des ressources numériques
* Aperçu ad hoc de l’expérience rendue par le fragment de contenu pour aider les auteurs à visualiser l’aspect du contenu sur l’application frontale
* Publication en 1 clic et annulation de publication du fragment de contenu à partir de l’éditeur
* Affichage et navigation vers des copies de langue lors de la modification d’un fragment de contenu
  ![Copies de langue - Éditeur de fragments de contenu](/help/release-notes/assets/newCFEditor_LanguageCopies.PNG)

* Affichage des versions pour tracker la chronologie d’un fragment de contenu

  ![Versions dans l’éditeur de fragments de contenu](/help/release-notes/assets/newCFEditor_Versionhistory.PNG)

* Affichage des références parentes pour aider les auteurs à comprendre l’impact de leurs modifications

  ![Références parentes dans l’éditeur de fragments de contenu](/help/release-notes/assets/newCFEditor_Parentreferences.PNG)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue Assets {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

* **Importation en bloc de ressources à partir de sources de données**: les administrateurs disposent désormais de la variable [possibilité d’importer un grand nombre de ressources](/help/assets/bulk-import-assets-view.md) d’une source de données vers AEM Assets. Les administrateurs et administratrices n’ont plus besoin de charger des ressources ou des dossiers individuels vers AEM Assets. Les sources de données prises en charge pour l’import en bloc sont Azure, AWS, Google Cloud et Dropbox.

  ![Import de ressources en bloc à partir d’une source de données.](/help/release-notes/assets/bulk-import.png)

* **Outils d’édition d’image optimisés par Adobe Express** : des outils simples et intuitifs [d’édition d’images optimisés par Adobe Express](/help/assets/edit-images-assets-view.md) sont disponibles directement dans AEM Assets pour augmenter la réutilisation du contenu et accélérer sa vitesse de diffusion.

  ![Modification d’images avec Adobe Express.](/help/release-notes/assets/edit-adobe-express.png)

* **Flexibilité lors de l’épinglage d’éléments pour l’accès rapide de Mon espace de travail** : possibilité de sélectionner et d’épingler des éléments pour vous, pour l’ensemble de votre organisation ou pour une liste de groupes afin qu’ils s’affichent dans la [section Accès rapide de Mon espace de travail](/help/assets/my-workspace-assets-view.md) en fonction de votre sélection.

  ![Épinglage d’éléments pour les groupes.](/help/release-notes/assets/pin-items-for-groups.png)

### Nouvelles fonctionnalités de la vue Assets {#admin-view-features}

**Améliorations de la recherche**

* Les administrateurs peuvent désormais [configuration de la taille de lot des ressources](/help/assets/search-assets.md#configure-asset-batch-size) qui s’affichent lorsque vous effectuez une recherche. Les résultats de recherche de ressources s’affichent en multiples de la taille de lot configurée lorsque vous faites défiler la page vers le bas pour charger les résultats. Vous pouvez sélectionner les tailles de lot disponibles (200, 500 et 1 000 ressources). Si vous définissez un nombre de lots inférieur, les temps de réponse de la recherche sont plus rapides.

  ![Configuration de la taille de lot des ressources](/help/release-notes/assets/assets-batch-size-configuration.png)

* Experience Manager Assets inclut désormais la nouvelle version 9 de `damAssetLucene` index. `damAssetLucene-9` modifie le comportement du comptage des facettes Oak Query en [n’évalue plus le contrôle d’accès sur les comptes de facettes](/help/assets/search-assets.md) renvoyée par l’index de recherche sous-jacent, ce qui entraîne des temps de réponse de recherche plus rapides.

### Fonctionnalités de version préliminaire disponibles dans [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media** : [prise en charge de plusieurs sous-titres et pistes audio pour les vidéos dans Dynamic Media](/help/assets/dynamic-media/video.md#about-msma). Vous pouvez désormais facilement ajouter plusieurs sous-titres et plusieurs pistes audio à une vidéo principale. Cette fonctionnalité signifie que vos vidéos sont accessibles à une audience mondiale. Vous pouvez personnaliser une seule vidéo principale publiée pour une audience mondiale dans plusieurs langues et respecter les directives d’accessibilité pour différentes régions géographiques. Les auteurs et autrices peuvent également gérer les sous-titres et les pistes audio à partir d’un seul onglet de l’interface d’utilisation.

  ![Onglet Sous-titres et pistes audio de la page Propriétés d’un contenu vidéo sélectionné.](/help/release-notes/assets/msma-aem-cs.png)*Onglet Sous-titres et pistes audio de la page Propriétés d’un contenu vidéo sélectionné.*

* **Ressources**: possibilité de sélectionner les archives ZIP gérées en Experience Manager et [extraction directe des fichiers dans Experience Manager](/help/assets/manage-digital-assets.md#extract-zip-archives) sans les télécharger.

  ![Épinglage d’éléments pour les groupes.](/help/release-notes/assets/extract-archive.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités disponibles dans [!DNL Forms] {#new-features-available-in-forms-channel}

* [**Support aux entreprises pour Google reCAPTCHA**](/help/forms/captcha-adaptive-forms.md): utilisez Google reCAPTCHA Enterprise dans un formulaire adaptatif pour offrir une meilleure protection contre les activités frauduleuses et les spams, offrant ainsi une expérience utilisateur plus sûre. Grâce à une analyse avancée des risques et à une intégration transparente, les utilisateurs authentiques peuvent facilement envoyer des formulaires lorsque les robots sont effectivement bloqués.


### Fonctionnalités de version préliminaire disponibles dans [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* **Adobe Analytics avec automatisation de la configuration Experience Cloud pour Forms**: vous pouvez désormais activer Adobe Analytics avec l’automatisation de la configuration de l’Experience Cloud à l’aide d’un saut de page de deux boutons. Vous pouvez ainsi connecter AEM Forms as a Cloud Service à des balises Experience Platform et à Adobe Analytics afin de capturer et de suivre les mesures de performances des formulaires que vous avez publiés.

* **Modèle de rapport Adobe Analytics pour Forms adaptatif**: Forms as a Cloud Service fournit désormais un rapport Adobe Analytics prêt à l’emploi. Cela vous permet de comprendre facilement les performances de vos formulaires. Les mesures au niveau du formulaire vous donnent des informations relatives aux performances du formulaire sur plusieurs indicateurs de performances clés (KPI) tels que les rendus, les visiteurs et visiteuses, les envois, le temps de remplissage moyen. En suivant le comportement et les commentaires des utilisateurs et utilisatrices, les analyses peuvent identifier les zones du formulaire sources de frustration ou confusion, ce qui permet d’en améliorer la conception et les fonctionnalités.

  ![Rapport adobe analytics d’engagement des utilisateurs de formulaires adaptatifs](/help/forms/assets/forms-analytics-report.png)

* **[Fragment de formulaire dans Forms adaptatif basé sur les composants principaux](/help/forms/adaptive-form-fragments-core-components.md)** : dites adieu à la duplication, optimisez votre inventaire numérique et améliorez la collaboration lorsque vous augmentez votre expérience de création de formulaires avec les fragments de formulaire. Ces composants réutilisables s’intègrent facilement à plusieurs formulaires, ce qui rationalise la création de formulaires cohérents et d’apparence professionnelle. Les fragments de formulaire assurent la réutilisation, la normalisation et la cohérence de la marque grâce à la fonctionnalité &quot;changer une fois et refléter partout&quot;. Expérimentez une plus grande maintenabilité et une plus grande efficacité, car les mises à jour effectuées à un emplacement donné sont automatiquement propagées à tous les formulaires qui utilisent ces fragments.

* **[Étape de processus Adobe Sign améliorée](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: l’étape Processus Adobe Sign a été améliorée afin d’inclure les éléments suivants :
   * **Amélioration de la sécurité avec l’authentification par pièce d’identité officielle pour Adobe Sign :** l’authentification par pièce d’identité officielle d’Adobe Acrobat Sign offre un niveau supplémentaire de vérification en permettant aux utilisateurs et utilisatrices de s’authentifier à l’aide de pièces d’identité délivrées par l’État (permis de conduire, carte d’identité nationale, passeport). En utilisant des documents d’identification approuvés, cette amélioration ajoute un niveau de confiance supplémentaire au processus de signature, ce qui en fait une solution idéale pour les scénarios qui nécessitent une sécurité, une conformité et une validation des utilisateurs et utilisatrices renforcées.

   * **Amélioration de la transparence avec le journal d’audit pour les documents Adobe Sign** – Utilisez la fonction Journal d’audit pour obtenir des informations détaillées sur le cycle de vie de vos documents Adobe Sign. Grâce au journal d’audit, vous pouvez désormais conserver un enregistrement complet de toutes les actions et interactions liées à vos documents. Cela inclut des détails tels que les personnes qui ont consulté, modifié ou signé le document, ainsi que l’heure et la date de chaque événement. Cette amélioration est essentielle pour maintenir la conformité, résoudre les litiges et assurer l’intégrité de vos accords numériques.

   * **Extension des rôles des personnes destinataires du contrat au-delà de la seule personne signataire :** Adobe Acrobat Sign a la possibilité d’étendre les rôles des personnes destinataires du contrat au-delà de la seule personne signataire afin de mieux répondre aux exigences de leur workflow.Lorsque cette option est activée, le rôle de chaque personne destinataire d’un contrat peut être configuré individuellement, la personne signataire étant la valeur par défaut.

* **[Protect de vos documents avec les API Document Assurance (partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: les API Document Assurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seuls les utilisateurs autorisés peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de garantir la sécurité et la confidentialité des documents Adobe PDF qu’elle diffuse et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seules les personnes destinataires prévues peuvent modifier les documents.

* **Prise en charge du nombre de pages dans les API de communication**: maintenant, en plus de récupérer votre document par le biais des API de communication, vous pouvez également recevoir des informations précieuses sur le nombre de pages contenues dans le document.

* **[Amélioration de la gestion des erreurs avec les gestionnaires d’erreurs personnalisés dans l’éditeur de règles](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)** : vous pouvez désormais appeler une fonction personnalisée (à l’aide de la bibliothèque cliente) en réponse à une erreur renvoyée par un service externe et fournir une réponse personnalisée aux utilisateurs et utilisatrices finaux. Par exemple, vous pouvez appeler un workflow personnalisé dans le serveur principal pour des codes d’erreur spécifiques ou informer le client ou la cliente que le service est indisponible.


### Programme des formulaires adaptatifs découplés destiné aux utilisateurs et utilisatrices précoces {#forms-early-adopter}

Utilisez les [formulaires adaptatifs découplés](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=fr) pour permettre à vos développeurs et développeuses de créer, publier et gérer des formulaires interactifs accessibles via des API, plutôt que par le biais d’une interface utilisateur graphique classique. Les formulaires adaptatifs découplés vous aident à :

* créer des formulaires multicanaux de haute qualité dans le langage de programmation de votre choix ;
* intégrer nativement les formulaires à vos applications de bureau et mobiles, à vos sites web et à vos applications de chat ;
* réutiliser vos composants d’IU propriétaires avec des applications de formulaires ;
* tirer profit de la puissance d’Adobe Experience Manager Forms

Vous pouvez envoyer un e-mail à `aem-forms-headless@adobe.com` à partir de votre ID d’e-mail officiel pour rejoindre le programme d’utilisateurs et utilisatrices précoces.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Journaux de réseau CDN {#cdn-logs}

Téléchargez les journaux CDN à partir de Cloud Manager, ce qui s’avère utile pour l’optimisation du rapport cache-accès et une meilleure visibilité du flux de diffusion de contenu. [En savoir plus](/help/implementing/developing/introduction/logging.md#cdn-log) le format du journal CDN. Cette fonctionnalité sera progressivement déployée auprès des clients début septembre.

### Réseau de diffusion de contenu et règles WAF : programme d’adoption précoce {#waf-early-adopter}

Filtrez le trafic sur le réseau de diffusion de contenu selon :

* en-têtes de requête et propriétés (par exemple, adresse IP) ;
* schémas de trafic connus pour être associés à un trafic malveillant

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoyez un e-mail à **headlessadaptiveforms@adobe.com** à partir de votre ID d’e-mail officiel pour rejoindre le programme d’utilisateurs et utilisatrices précoces. L&#39;espace est limité.

En savoir plus sur la fonctionnalité de l’article [here](/help/security/traffic-filter-rules-including-waf.md).


## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
