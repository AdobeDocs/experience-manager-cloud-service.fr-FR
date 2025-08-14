---
title: Notes de mise à jour de la version 2023.9.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la version 2023.9.0 d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: d747f58b-8d6c-418d-9d2b-ec3ae4b6dc03
feature: Release Information
role: Admin
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '1440'
ht-degree: 84%

---


# Notes de mise à jour de la version 2023.9.0 d’[!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

La section suivante concerne les notes de mise à jour de la version 2023.9.0 d’[!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>À partir de là, vous pouvez accéder aux notes de mise à jour des versions précédentes, telles que 2021 ou 2022.
>
>Consultez la section [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour en savoir plus sur les activations de fonctionnalités à venir pour [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Voir [Mises à jour récentes de la documentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=fr) pour plus d’informations sur les mises à jour de la documentation qui ne sont pas directement liées à une version.

## Date de publication {#release-date}

La date de publication de la version actuelle (2023.9.0) d’[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] est le vendredi 28 septembre 2023. La prochaine disponibilité des fonctionnalités (2023.10.0) est prévue pour le vendredi 26 octobre 2023.

## Notes de mise à jour de la maintenance {#maintenance}

Vous trouverez les dernières notes de mise à jour de maintenance [ici](/help/release-notes/maintenance/latest.md).

## Vidéo de mise à jour {#release-video}

Consultez la vidéo Vue d’ensemble de la version de septembre 2023 pour obtenir un résumé des fonctionnalités ajoutées dans la version 2023.9.0 :

>[!VIDEO](https://video.tv.adobe.com/v/3424826/?quality=12)

## AEM Edge Delivery Services {#edge-delivery}

Edge Delivery est un nouvel ensemble de services composables visant à optimiser l’impact du contenu afin de générer des résultats commerciaux mesurables au moment de l’interaction client.

En savoir plus sur Edge Delivery Services dans l’article [ici](/help/edge/overview.md).

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Nouvelles fonctionnalités de la vue Assets {#assets-view-features}

**Attribuer un formulaire de métadonnées à un dossier**

Vous pouvez désormais affecter un formulaire de métadonnées à un dossier spécifique dans votre déploiement . Toutes les ressources du dossier, y compris les ressources des sous-dossiers, affichent les propriétés définies dans le formulaire de métadonnées attribué.

![Attribution d’un formulaire de métadonnées à un dossier.](/help/release-notes/assets/assign-to-folder.png)

### Nouvelles fonctionnalités de la vue d’administration {#admin-view-features}

* **Intégrer AEM Assets as a Cloud Service à la création basée sur les documents pour Edge Delivery Services** : intégrez AEM Assets à la création basée sur les documents pour Edge Delivery Services pour permettre aux auteurs de sites web d’[utiliser les images disponibles dans les référentiels AEM Assets lors de la création de documents dans Microsoft Word ou Google Docs](/help/edge/overview.md).

* **Extraction des archives ZIP** : possibilité de sélectionner des archives ZIP gérées dans Experience Manager et [d’extraire les fichiers directement dans Experience Manager](/help/assets/manage-digital-assets.md#extract-zip-archives) sans les télécharger.

  ![Épinglage d’éléments pour les groupes.](/help/release-notes/assets/extract-archive.png)

### Fonctionnalités de pré-version disponibles dans [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media** : [prise en charge de plusieurs sous-titres et pistes audio pour les vidéos dans Dynamic Media](/help/assets/dynamic-media/video.md#about-msma). Vous pouvez désormais facilement ajouter plusieurs sous-titres et plusieurs pistes audio à une vidéo principale. Cette fonctionnalité signifie que vos vidéos sont accessibles à une audience mondiale. Vous pouvez personnaliser une seule vidéo principale publiée pour une audience mondiale dans plusieurs langues et respecter les directives d’accessibilité pour différentes régions géographiques. Les auteurs et autrices peuvent également gérer les sous-titres et les pistes audio à partir d’un seul onglet de l’interface d’utilisation.

  ![Onglet Sous-titres et pistes audio de la page Propriétés d’un contenu vidéo sélectionné.](/help/release-notes/assets/msma-aem-cs.png)*Onglet Sous-titres et pistes audio de la page Propriétés d’un contenu vidéo sélectionné.*

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Nouvelles fonctionnalités de [!DNL Experience Manager Forms] {#forms-features}

* [**Support aux entreprises pour Google reCAPTCHA**](/help/forms/captcha-adaptive-forms-core-components.md): utilisez Google reCAPTCHA Enterprise dans un formulaire adaptatif pour offrir une meilleure protection contre les activités frauduleuses et les spams, offrant ainsi une expérience utilisateur plus sûre. Grâce à une analyse avancée des risques et à une intégration transparente, les utilisateurs authentiques peuvent facilement envoyer des formulaires lorsque les robots sont effectivement bloqués.

* [**Adobe Analytics avec automatisation de la configuration Experience Cloud pour Forms**](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md): vous pouvez désormais activer Adobe Analytics avec l’automatisation de la configuration de l’Experience Cloud à l’aide d’un saut de page de deux boutons. Vous pouvez ainsi connecter AEM Forms as a Cloud Service à des balises Experience Platform et à Adobe Analytics afin de capturer et de suivre les mesures de performances des formulaires que vous avez publiés.

  >[!VIDEO](https://video.tv.adobe.com/v/3424577/enable-adobe-analytics/?quality=12&learn=on)

* [**Modèle de rapport Adobe Analytics pour Forms adaptatif**](/help/forms/view-understand-aem-forms-analytics-reports.md): Forms as a Cloud Service fournit désormais un rapport Adobe Analytics prêt à l’emploi. Cela vous permet de comprendre facilement les performances de vos formulaires. Les mesures au niveau du formulaire vous donnent des informations relatives aux performances du formulaire sur plusieurs indicateurs de performances clés (KPI) tels que les rendus, les visiteurs et visiteuses, les envois, le temps de remplissage moyen. En suivant le comportement et les commentaires des utilisateurs et utilisatrices, les analyses peuvent identifier les zones du formulaire sources de frustration ou confusion, ce qui permet d’en améliorer la conception et les fonctionnalités.

  ![Rapport adobe analytics d’engagement des utilisateurs de formulaires adaptatifs](/help/forms/assets/forms-analytics-report.png)

* **[Fragment de formulaire dans Forms adaptatif basé sur les composants principaux](/help/forms/adaptive-form-fragments-core-components.md)**: dites adieu à la duplication, optimisez votre inventaire numérique et améliorez la collaboration lorsque vous augmentez votre expérience de création de formulaires avec les fragments de formulaire. Ces composants réutilisables s’intègrent facilement à plusieurs formulaires, ce qui rationalise la création de formulaires cohérents et d’apparence professionnelle. Les fragments de formulaire assurent la réutilisation, la normalisation et la cohérence de la marque grâce à la fonctionnalité &quot;changer une fois et refléter partout&quot;. Expérimentez une plus grande maintenabilité et une plus grande efficacité, car les mises à jour effectuées à un emplacement donné sont automatiquement propagées à tous les formulaires qui utilisent ces fragments.

* **[Étape de processus Adobe Sign améliorée](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: l’étape Processus Adobe Sign a été améliorée afin d’inclure les éléments suivants :
   * **Amélioration de la sécurité avec l’authentification par pièce d’identité officielle pour Adobe Sign :** l’authentification par pièce d’identité officielle d’Adobe Acrobat Sign offre un niveau supplémentaire de vérification en permettant aux utilisateurs et utilisatrices de s’authentifier à l’aide de pièces d’identité délivrées par l’État (permis de conduire, carte d’identité nationale, passeport). En utilisant des documents d’identification approuvés, cette amélioration ajoute un niveau de confiance supplémentaire au processus de signature, ce qui en fait une solution idéale pour les scénarios qui nécessitent une sécurité, une conformité et une validation des utilisateurs et utilisatrices renforcées.

   * **Amélioration de la transparence avec le journal d’audit pour les documents Adobe Sign** – Utilisez la fonction Journal d’audit pour obtenir des informations détaillées sur le cycle de vie de vos documents Adobe Sign. Grâce au journal d’audit, vous pouvez désormais conserver un enregistrement complet de toutes les actions et interactions liées à vos documents. Cela inclut des détails tels que les personnes qui ont consulté, modifié ou signé le document, ainsi que l’heure et la date de chaque événement. Cette amélioration est essentielle pour maintenir la conformité, résoudre les litiges et assurer l’intégrité de vos accords numériques.

   * **Extension des rôles des personnes destinataires du contrat au-delà de la seule personne signataire :** Adobe Acrobat Sign a la possibilité d’étendre les rôles des personnes destinataires du contrat au-delà de la seule personne signataire afin de mieux répondre aux exigences de leur workflow.Lorsque cette option est activée, le rôle de chaque personne destinataire d’un contrat peut être configuré individuellement, la personne signataire étant la valeur par défaut.

* **Prise en charge du nombre de pages dans les API de communication**: maintenant, en plus de récupérer votre document par le biais des API de communication, vous pouvez également recevoir des informations précieuses sur le nombre de pages contenues dans le document.

* **[Amélioration de la gestion des erreurs avec les gestionnaires d’erreurs personnalisés dans l’éditeur de règles](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)** : vous pouvez désormais appeler une fonction personnalisée (à l’aide de la bibliothèque cliente) en réponse à une erreur renvoyée par un service externe et fournir une réponse personnalisée aux utilisateurs et utilisatrices finaux. Par exemple, vous pouvez appeler un workflow personnalisé dans le serveur principal pour des codes d’erreur spécifiques ou informer le client ou la cliente que le service est indisponible.

* Version **[64 bits d’AEM Forms Designer](/help/forms/installing-configuring-designer.md)** : la version 64 bits d’AEM Forms Designer offre des performances, une évolutivité et une gestion de la mémoire améliorées pour renforcer votre expérience de création de formulaires. Grâce à l’architecture 64 bits, vous pouvez aborder facilement des projets plus volumineux et plus complexes, assurant ainsi des workflows de conception transparents et une efficacité optimisée. Améliorez encore vos capacités de conception de formulaire et accueillez l’avenir d’AEM Forms Designer avec cette version de pointe.

### Programme d’adoption précoce {#forms-early-adopter}

* **[Protégez vos documents avec les API DocAssurance (qui font partie des API de communication)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)** : les API DocAssurance vous permettent de protéger les informations sensibles en signant et en chiffrant les documents. Grâce au chiffrement, le contenu d’un document est transformé en un format illisible, ce qui garantit que seules les personnes autorisées peuvent y accéder. Cette couche renforcée de protection protège non seulement les données précieuses des yeux non autorisés, mais offre également une certaine tranquillité d’esprit. Les API Signature permettent à votre entreprise de garantir la sécurité et la confidentialité des documents Adobe PDF qu’elle diffuse et reçoit. Ce service utilise les signatures numériques et la certification pour s’assurer que seules les personnes destinataires prévues peuvent modifier les documents.

  Vous pouvez écrire à `aem-forms-ea@adobe.com` depuis votre adresse e-mail officielle pour rejoindre le programme d’adoption précoce et demander l’accès à la fonctionnalité.

* **[Forms adaptative découplée](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=fr)** : utilisez le Forms adaptatif découplé pour permettre à vos développeurs et développeuses de créer, publier et gérer des formulaires interactifs accessibles et interactifs via des API, plutôt que par le biais d’une interface utilisateur graphique classique. Les formulaires adaptatifs découplés vous aident à :

   * créer des formulaires multicanaux de haute qualité dans le langage de programmation de votre choix ;
   * intégrer nativement les formulaires à vos applications de bureau et mobiles, à vos sites web et à vos applications de chat ;
   * réutiliser vos composants d’IU propriétaires avec des applications de formulaires ;
   * tirer profit de la puissance d’Adobe Experience Manager Forms

  Vous pouvez envoyer un e-mail à `aem-forms-headless@adobe.com` à partir de votre ID d’e-mail officiel pour rejoindre le programme d’utilisateurs et utilisatrices précoces.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Nouveau comportement de mise en cache CDN pour les paramètres d’URL liés à la campagne {#cache-url-params}

Pour les nouveaux environnements, le réseau CDN supprime par défaut les paramètres de requête liés au marketing afin d’augmenter les performances des campagnes marketing et les taux d’accès au cache. Les environnements existants ne sont pas affectés. [En savoir plus](/help/implementing/dispatcher/caching.md#marketing-parameters).

### Programme de règles de filtrage du trafic (y compris les règles WAF) destiné aux utilisateurs et utilisatrices précoces {#waf-early-adopter}

Filtrez le trafic sur le réseau de diffusion de contenu selon :

* en-têtes de requête et propriétés (par exemple, adresse IP) ;
* schémas de trafic connus pour être associés à un trafic malveillant

Vous souhaitez tester la fonctionnalité et partager vos commentaires ? Envoyez un e-mail à **headlessadaptiveforms@adobe.com** à partir de votre ID d’e-mail officiel pour rejoindre le programme d’utilisateurs et utilisatrices précoces. L&#39;espace est limité.

En savoir plus sur la fonctionnalité de l’article [here](/help/security/traffic-filter-rules-including-waf.md).

## Cloud Manager {#cloud-manager}

Vous trouverez la liste complète des versions mensuelles de Cloud Manager [ici](/help/implementing/cloud-manager/release-notes/current.md).

## Outils de migration {#migration-tools}

Vous trouverez une liste complète des versions des outils de migration [ici](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
