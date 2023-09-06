---
title: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
description: Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 6d0e3ee08862030e9eb7d068b251d13bc3e8e08f
workflow-type: tm+mt
source-wordcount: '1926'
ht-degree: 13%

---

# Notes de mise à jour actuelles pour [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour techniques de la version actuelle (la plus récente) d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] la version actuelle des fonctionnalités (2023.8.0) est le 31 août 2023. La prochaine version de la fonctionnalité (2023.9.0) est prévue pour le 28 septembre 2023.

## Vidéo de mise à jour {#release-video}

Regardez la vidéo Aperçu de la version d’août 2023 pour un résumé des fonctionnalités ajoutées dans la version 2023.8.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3423535/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Nouvelles fonctionnalités de [!DNL Experience Manager Sites] {#sites-features}

* La variable [Console de fragments de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=en) permet désormais aux utilisateurs d’afficher les balises et de rechercher par balises appliquées en tant que métadonnées aux fragments de contenu. Les utilisateurs n’auront plus à passer à l’interface utilisateur d’Assets pour cette fonctionnalité, ce qui réduit le changement de contexte et améliore l’efficacité.

  ![Balisage dans la console de fragments de contenu](/help/assets/content-fragments-console-tags.png)
* Le nouvel éditeur de fragment de contenu est désormais disponible sur AEM as a Cloud Service. Cela permet aux auteurs de contenu d’être plus productifs en rationalisant leurs tâches de création et en réduisant la nécessité de basculer entre différentes applications lors de la modification du contenu.
  ![Nouvel éditeur de fragments de contenu](/help/release-notes/assets/newCFEditor.png)

Le nouvel éditeur de fragment de contenu offre les avantages suivants, qui ne sont pas disponibles dans l’éditeur d’origine :
* Enregistrement automatique pour une meilleure efficacité de création et pour éviter toute perte accidentelle de modifications.
* Vue hiérarchique d’un fragment de contenu et de ses références à l’aide de l’arborescence Structure pour une navigation rapide au sein d’un fragment profondément structuré.
  ![Arborescence de structure dans l’éditeur de fragments de contenu](/help/release-notes/assets/newCFEditor_StructureTree.png)

* Chargement en ligne de ressources en tant que références de contenu sans devoir d’abord les charger dans la gestion des ressources numériques
* Aperçu ad hoc de l’expérience rendue par le fragment de contenu pour aider les auteurs à visualiser l’aspect du contenu sur l’application frontale
* Publication en 1 clic et annulation de publication du fragment de contenu à partir de l’éditeur
* Affichage et navigation vers des copies de langue lors de la modification d’un fragment de contenu
  ![Copies de langue dans l’éditeur de fragments de contenu](/help/release-notes/assets/newCFEditor_LanguageCopies.PNG)

* Affichage des versions pour tracker la chronologie d’un fragment de contenu

  ![Versions dans l’éditeur de fragments de contenu](/help/release-notes/assets/newCFEditor_Versionhistory.PNG)

* Affichage des références parentes pour aider les auteurs à comprendre l’impact de leurs modifications

  ![Références parentes dans l’éditeur de fragments de contenu](/help/release-notes/assets/newCFEditor_Parentreferences.PNG)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités dans la vue Assets {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

* **Importation en bloc de ressources à partir de sources de données**: les administrateurs disposent désormais de la variable [possibilité d’importer un grand nombre de ressources](/help/assets/bulk-import-assets-view.md) d’une source de données vers AEM Assets. Les administrateurs n’ont plus besoin de charger des ressources ou des dossiers individuels vers AEM Assets. Les sources de données prises en charge pour l’importation en bloc sont Azure, AWS, Google Cloud et Dropbox.

  ![Importation en bloc de ressources à partir d’une source de données](/help/release-notes/assets/bulk-import.png)

* **Outils de retouche d’images optimisés par Adobe Express**: Facile et intuitive [outils de retouche d’images optimisés par Adobe Express](/help/assets/edit-images-assets-view.md) disponible directement dans AEM Assets pour augmenter la réutilisation du contenu et accélérer la vitesse du contenu.

  ![Modification d’images avec Adobe Express](/help/release-notes/assets/edit-adobe-express.png)

* **Flexibilité lors de l’épinglage d’éléments pour l’accès rapide à My Workspace**: possibilité de sélectionner et d’épingler des éléments pour vous, pour l’ensemble de l’organisation ou pour une liste de groupes afin qu’ils s’affichent dans la variable [Section Accès rapide de My Workspace](/help/assets/my-workspace-assets-view.md) en fonction de votre sélection.

  ![Épingler des éléments pour les groupes](/help/release-notes/assets/pin-items-for-groups.png)

### Nouvelles fonctionnalités dans la vue d’administration {#admin-view-features}

**Améliorations de la recherche**

* Les administrateurs peuvent désormais [configuration de la taille de lot des ressources](/help/assets/search-assets.md#configure-asset-batch-size) qui s’affichent lorsque vous effectuez une recherche. Les résultats de recherche de ressources s’affichent en multiples de la taille de lot configurée lorsque vous faites défiler la page vers le bas pour charger les résultats. Vous pouvez sélectionner les tailles de lot disponibles (200, 500 et 1 000 ressources). Si vous définissez un nombre de lots inférieur, les temps de réponse de la recherche sont plus rapides.

  ![Configuration de la taille de lot des ressources](/help/release-notes/assets/assets-batch-size-configuration.png)

* Experience Manager Assets inclut désormais la nouvelle version 9 de `damAssetLucene` index. `damAssetLucene-9` modifie le comportement du comptage des facettes Oak Query en [n’évalue plus le contrôle d’accès sur les comptes de facettes](/help/assets/search-assets.md) renvoyée par l’index de recherche sous-jacent, ce qui entraîne des temps de réponse de recherche plus rapides.

### Fonctionnalités de préversion disponibles dans [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media**: [Prise en charge du suivi multititre et multiaudio pour les vidéos dans Dynamic Media](/help/assets/dynamic-media/video.md#about-msma): vous pouvez désormais facilement ajouter plusieurs sous-titres et plusieurs pistes audio à une vidéo principale. Cette fonctionnalité signifie que vos vidéos sont accessibles à l’échelle mondiale. Vous pouvez personnaliser une seule vidéo principale publiée pour une audience globale dans plusieurs langues et respecter les directives d’accessibilité pour différentes régions géographiques. Les auteurs peuvent également gérer les sous-titres et les pistes audio à partir d’un seul onglet de l’interface utilisateur.

  ![Onglet Sous-titres et Suivi audio de la page Propriétés d’une ressource vidéo sélectionnée.](/help/release-notes/assets/msma-aem-cs.png)*Onglet Sous-titres et Suivi audio de la page Propriétés d’une ressource vidéo sélectionnée.*

* **Ressources**: possibilité de sélectionner les archives ZIP gérées en Experience Manager et [extraction directe des fichiers dans Experience Manager](/help/assets/manage-digital-assets.md#extract-zip-archives) sans les télécharger.

  ![Épingler des éléments pour les groupes](/help/release-notes/assets/extract-archive.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Fonctionnalités de préversion disponibles dans [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* [**Support aux entreprises pour Google reCAPTCHA**](/help/forms/captcha-adaptive-forms-core-components.md): utilisez Google reCAPTCHA Enterprise dans un formulaire adaptatif pour offrir une meilleure protection contre les activités frauduleuses et les spams, offrant ainsi une expérience utilisateur plus sûre. Grâce à une analyse avancée des risques et à une intégration transparente, les utilisateurs authentiques peuvent facilement envoyer des formulaires lorsque les robots sont effectivement bloqués.

* **Adobe Analytics avec automatisation de la configuration Experience Cloud pour Forms**: vous pouvez désormais activer Adobe Analytics avec l’automatisation de la configuration de l’Experience Cloud à l’aide d’un saut de page de deux boutons. Il vous permet de connecter AEM Forms as a Cloud Service à des balises Experience Platform et à Adobe Analytics afin de capturer et de suivre les mesures de performances des formulaires que vous avez publiés.

* **Modèle de rapport Adobe Analytics pour Forms adaptatif**: Forms as a Cloud Service fournit désormais un rapport Adobe Analytics prêt à l’emploi. Cela vous permet de comprendre facilement les performances de vos formulaires. Les mesures au niveau du formulaire vous donnent des informations relatives aux performances du formulaire sur plusieurs indicateurs de performances clés (KPI) tels que les rendus, les visiteurs et visiteuses, les envois, le temps de remplissage moyen. En suivant le comportement et les commentaires de l’utilisateur, vous pouvez identifier les zones du formulaire qui causent des confusion et guider les améliorations de la conception et de la fonctionnalité du formulaire.

  ![Rapport adobe analytics d’engagement des utilisateurs de formulaires adaptatifs](/help/forms/assets/forms-analytics-report.png)

* **[Fragment de formulaire dans Forms adaptatif basé sur les composants principaux](/help/forms/adaptive-form-fragments-core-components.md)**: dites adieu à la duplication, optimisez votre inventaire numérique et améliorez la collaboration lorsque vous augmentez votre expérience de création de formulaires avec les fragments de formulaire. Ces composants réutilisables s’intègrent facilement à plusieurs formulaires, ce qui rationalise la création de formulaires cohérents et d’apparence professionnelle. Les fragments de formulaire assurent la réutilisation, la normalisation et la cohérence de la marque grâce à la fonctionnalité &quot;changer une fois et refléter partout&quot;. Expérimentez une plus grande maintenabilité et une plus grande efficacité, car les mises à jour effectuées à un emplacement donné sont automatiquement propagées à tous les formulaires qui utilisent ces fragments.

* **[Étape de processus Adobe Sign améliorée](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: l’étape Processus Adobe Sign a été améliorée afin d’inclure les éléments suivants :
   * **Authentification basée sur les ID de gouvernement pour Adobe Sign**: Adobe Acrobat Sign Government ID-Based Authentication offre une couche supplémentaire de vérification en permettant aux utilisateurs d&#39;authentifier leur identité à l&#39;aide de cartes d&#39;identité délivrées par le gouvernement (permis de conduire, carte d&#39;identité nationale, passeport). En exploitant des documents d’identification approuvés, cette amélioration ajoute un degré de confiance supplémentaire au processus de signature, ce qui le rend idéal pour les scénarios qui nécessitent une sécurité renforcée, la conformité et la validation utilisateur.

   * **Journal d’audit des documents Adobe Sign**: utilisez la fonction Journal d’audit pour obtenir des informations détaillées sur le cycle de vie de vos documents Adobe Sign. Grâce au journal d’audit, vous pouvez désormais conserver un enregistrement complet de toutes les actions et interactions liées à vos documents. Cela inclut des détails tels que qui a consulté, modifié ou signé le document, ainsi que des horodatages pour chaque événement. Cette amélioration est essentielle pour maintenir la conformité, résoudre les litiges et assurer l’intégrité de vos accords numériques.

   * **Nouveaux rôles pour les destinataires du contrat au-delà du simple signataire**: Adobe Acrobat Sign a la possibilité de développer les rôles des destinataires du contrat au-delà du simple signataire pour mieux répondre aux exigences de leur workflow. Lorsque cette option est activée, le rôle de chaque destinataire d’un contrat peut être configuré individuellement, le signataire étant la valeur par défaut.

* **[Protect de vos documents avec les API Document Assurance (partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: les API Document Assurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seuls les utilisateurs autorisés peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de protéger la sécurité et la confidentialité des documents Adobe PDF qu’elle distribue et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seuls les destinataires prévus peuvent modifier les documents.

* **Prise en charge du nombre de pages dans les API de communication**: maintenant, en plus de récupérer votre document par le biais des API de communication, vous pouvez également recevoir des informations précieuses sur le nombre de pages contenues dans le document.

* **[Gestion des erreurs avec des gestionnaires d’erreurs personnalisés dans l’éditeur de règles](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)**: vous pouvez désormais appeler une fonction personnalisée en réponse à une erreur renvoyée par un service externe et fournir une réponse personnalisée aux utilisateurs finaux. Par exemple, vous pouvez appeler un workflow personnalisé dans le serveur principal pour des codes d’erreur spécifiques ou informer le client que le service est hors service.

* **[Version 64 bits d’AEM Forms Designer](/help/forms/installing-configuring-designer.md)**: la version 64 bits d’AEM Forms Designer offre des performances, une évolutivité et une gestion de la mémoire améliorées pour vous permettre de créer des formulaires. Grâce à l’architecture 64 bits, vous pouvez réaliser facilement des projets plus volumineux et plus complexes, assurant ainsi des workflows de conception transparents et une efficacité optimisée. Tirez parti de vos capacités de conception de formulaire et embrassez l’avenir d’AEM Forms Designer avec cette version de pointe.


### Programme d&#39;adoption précoce {#forms-early-adopter}

* **[Protect de vos documents avec les API DocAssurance (partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seuls les utilisateurs autorisés peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de protéger la sécurité et la confidentialité des documents Adobe PDF qu’elle distribue et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seuls les destinataires prévus peuvent modifier les documents.

  Vous pouvez connecter la prise en charge des Adobes pour rejoindre le programme d’adoption précoce des API DocAssurance.

* **[Forms adaptatif sans affichage](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=fr)**: utilisez le Forms adaptatif sans affichage pour permettre aux développeurs de créer, publier et gérer des formulaires interactifs accessibles et interactifs via les API, plutôt que par le biais d’une interface utilisateur graphique classique. Les formulaires adaptatifs découplés vous aident à :

   * créer des formulaires multicanaux de haute qualité dans le langage de programmation de votre choix ;
   * intégrer nativement les formulaires à vos applications de bureau et mobiles, à vos sites web et à vos applications de chat ;
   * réutiliser vos composants d’IU propriétaires avec des applications de formulaires ;
   * utiliser la puissance d’Adobe Experience Manager Forms ;

  Vous pouvez envoyer un courrier électronique à `aem-forms-headless@adobe.com` à partir de votre ID de courrier électronique officiel pour rejoindre le programme des premiers adopteurs.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Journaux du réseau de diffusion de contenu {#cdn-logs}

Téléchargez les journaux CDN à partir de Cloud Manager, ce qui s’avère utile pour l’optimisation du rapport cache-accès et une meilleure visibilité du flux de diffusion de contenu. [En savoir plus](/help/implementing/developing/introduction/logging.md#cdn-log) le format du journal CDN. Cette fonctionnalité sera progressivement déployée auprès des clients début septembre.

### Réseau de diffusion de contenu et règles WAF : programme d’adoption précoce {#waf-early-adopter}

Filtrez le trafic sur le réseau de diffusion de contenu selon :
* en-têtes de requête et propriétés (par exemple, adresse IP) ;
* schémas de trafic connus pour être associés à un trafic malveillant

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoi d’un courrier électronique à **aemcs-waf-adopter@adobe.com** à partir de votre ID de courrier électronique officiel pour en savoir plus sur le programme des premiers adopteurs. L&#39;espace est limité.

En savoir plus sur la fonctionnalité de l’article [here](/help/security/cdn-and-waf-rules.md).


## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
