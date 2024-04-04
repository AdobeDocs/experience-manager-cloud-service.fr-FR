---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: d07fc976fe9c8e7872468048f80e525fe8484339
workflow-type: tm+mt
source-wordcount: '2584'
ht-degree: 9%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 15787 {#release-15787}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 15787, rendue publique le vendredi 4 avril 2024. La version de maintenance précédente était la version 15575.

L’activation des fonctionnalités de la version 2024.3.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-15787}

* SITES-19059 - Fragments de contenu - OpenAPI - Allow defaultValue pour les champs d’énumération
* SITES-2013 - Fragments de contenu - OpenAPI - WCMScriptHelper doit abandonner le rendu lorsqu’aucun ServletResolver n’est présent
* SITES-19926 - Fragments de contenu - OpenAPI - Améliorations apportées à OnOffTriggerProcessor
* SITES-17945 - Fragments de contenu - OpenAPI - Obtenir les métadonnées de dernière modification pour chaque version
* SITES-17298 - Fragments de contenu - OpenAPI - Autorisations des modèles de fragments de contenu
* SITES-14255 - Fragments de contenu - OpenAPI - Valider l’unicité du champ de texte si un indicateur unique est défini dans le modèle de fragment
* SITES-15557 - Fragments de contenu - OpenAPI - Allow defaultValue pour les champs d’énumération
* SITES-1559 - Fragments de contenu - OpenAPI - Mise à jour de l’API CF List pour permettre la récupération uniquement des fragments de contenu enfant directs (BE)
* SITES-16052 - Fragments de contenu - OpenAPI - Ajoutez l’URL de l’instance où une ressource peut être consommée.
* SITES-17944 - Fragments de contenu - OpenAPI - Correspondance des listes de contrôle d’accès JCR appropriées avec le point de terminaison des autorisations des FC
* SITES-17513 - Plan de contrôle des fragments de contenu - Annulation de la publication des fragments de contenu
* SITES-8831 - Plan de contrôle des fragments de contenu - PUT - Mettre à jour un fragment avec des informations complètes
* SITES-8836 - Fragments de contenu - OpenAPI - Plan de contrôle - Références de GET - Obtention des références parentes d’un fragment (par UUID)
* SITES-8986 - Fragments de contenu - OpenAPI - Publier le modèle de fragment de contenu
* SITES-18073 - Fragments de contenu - OpenAPI - Modèle PreviewURL pour un CFM
* SITES-15242 - Fragments de contenu - OpenAPI - Étendre les événements de publication pour fournir des informations sur le niveau
* SITES-18702 - Fragments de contenu - OpenAPI - [Serveur principal] Possibilité de publier au niveau du dossier
* SITES-20020 - Fragments de contenu - OpenAPI - Supprimer `X-Adobe-Accept-Unsupported-API` avant GA
* SITES-16066 - Fragments de contenu - Éditeur de fragments - Modifier l’URL JS du sélecteur de ressources
* SITES-19326 - Fragments de contenu - Éditeur de fragments - Mise à jour de liens dans l’interface utilisateur d’Assets pour ouvrir les fichiers CF dans le nouvel éditeur de CF
* SITES-10515 - Fragments de contenu - API GraphQL - GraphQL - Problème de performances AbstractFetcher Chargement des fragments de contenu référencé
* SITES-17364 - Fragments de contenu - API GraphQL - Nom complet pour les propriétés Modified by et Published by
* SITES-19165 - Fragments de contenu - API GraphQL - Autoriser l’utilisation, le référencement et l’interrogation des modèles globaux dans tous les points de terminaison GraphQL
* SITES-17768 - Fragments de contenu - API GraphQL - Exposer l’URL Dynamic Media des images via _dmS7Url
* SITES-11057 - Principal principal - Évitez de charger toutes les versions lors de l’ouverture de la chronologie > Versions
* SKYOPS-63033 - HTTPD - Découpage des espaces blancs des variables d’environnement du Dispatcher
* SKYOPS-65518 - HTTPD - Échec du programme de validation s’il existe des noms de fichier illégaux dans le dossier du Dispatcher
* SITES-19626 - Lancements - Fusionner les champs lastUpdate DAM-CFM dans les principaux
* SITES-19251 - Site rapide - Assistant de création - rail latéral de l’interface utilisateur d’administration des sites de prise en charge lorsque la référence au thème n’est pas égale au nom du site
* SITES-15430 - Éditeur universel - Éditeur universel sous AEM domaine
* CQ-4344966 - WCM - Traduction - Créer un framework de base pour la mise à jour structurelle des sites et en mettre à jour un existant pour les ressources
* CQ-4347312 - WCM - Traduction - Créer un workflow pour associer &quot;cq:translation-sourcejcruid&quot; aux copies source et de langue existantes
* CQ-4354509 - WCM - Traduction - Publier les événements de tâche de traduction [OSGi EventAdmin]
* SITES-16318 - Crosswalk - Création basée sur AEM avec des Edge Delivery Services
* FORMS-9889 : l’utilisateur peut ajouter l’URL du POST et la configuration du cloud lors de la configuration de l’action Envoyer vers le point de fin REST.
* Dans l’éditeur de règles, les utilisateurs peuvent :
   * FORMS-12160 : validation d’un champ, d’un panneau ou d’un formulaire dans la section Alors de la condition Lorsque .
   * FORMS-12570 : réinitialisez un champ, un panneau ou un formulaire dans la section Then de la condition When (Lorsque).
   * FORMS-11541 : utilisez des objets de champ et des objets globaux dans l’éditeur de règles par le biais des fonctions personnalisées.
   * FORMS-11714 : définissez des paramètres comme étant facultatifs dans la fonction personnalisée. Par défaut, les paramètres déclarés dans les fonctions personnalisées sont obligatoires.
   * FORMS-11756 : utilisez la mise en cache pour les fonctions personnalisées afin d’améliorer le temps de réponse lors de la récupération de la liste des fonctions personnalisées dans l’éditeur de règles.
   * FORMS-12053 : ajoutez une instruction &#39;else&#39; dans la condition &#39;When&#39; pour mettre en oeuvre des conditions imbriquées.
   * FORMS-11269 : utilisez les fonctions JavaScript ES10 modernes telles que les fonctions de flèches et de flèches dans la fonction personnalisée pour les formulaires basés sur les composants principaux.

* FORMS-9014 : Diverses améliorations liées à l’accessibilité au composant Signature tactile


### Problèmes résolus {#fixed-issues-15787}

* Différents problèmes d’accessibilité et d’internationalisation ont été résolus.
* SITES-16966 - AEM : Non localisé &quot;Pas versionné !&quot; chaîne dans Sites > Restaurer > Restaurer l’arborescence
* SITES-16208 - ContentFragmentModelIdentifier expose une propriété de titre trompeuse.
* SITES-18024 - Lorsque l’en-tête If-Match est manquant, la réponse doit être 428
* SITES-18003 - L’utilisateur qui a créé une version n’est pas renvoyé correctement
* SITES-17937 - L’événement Fragment de contenu créé est émis avant la synchronisation des capsules de création
* SITES-18029 - Le pipeline de traitement d’événement se bloque lorsqu’il est averti simultanément par l’observation JCR.
* SITES-17882 - Supprimer la limite de longueur maximale du champ de texte de fragment du schéma
* SITES-19252 - Correction des incohérences liées au code d’état HTTP 406 et 415
* SITES-16964 - [Serveur principal] Le tri par &quot;Modifié par&quot; ne fonctionne pas correctement
* SITES-17519 - Éditeur de propriétés de page de sites - Un nom de page long rend les boutons non cliquables
* SITES-16852 - L’API de publication publie des références avec le NOUVEL état
* SITES-18833 - Contrainte d’unicité non visible dans les points d’entrée OpenAPI
* SITES-15553 - Échec du chargement du panneau latéral de XF si l’URL du XF contient un sélecteur
* SITES-14340 - NPE dans VersioningTimelineEventProvider.accept
* SITES-1605 - [Sites] DeletePageCommand renvoie NPE en cas de chemin source nul
* SITES-16308 - [GB18030]: un message d’avertissement s’affiche lors de la création d’un dossier Sites nommé avec des caractères GB18030.
* SITES-16304 - [GB18030]: un message d’avertissement s’affiche lors de la création d’un dossier de fragments d’expérience nommé avec des caractères GB18030
* SITES-8769 - Amélioration des performances de StyleImpl
* CQ-4343815 - Campagne - Ciblage - La variante par défaut d’un teaser a une URL vide
* CQ-4355889 - Campaign - Ciblage - La demande Créer une audience échoue avec la configuration IMS.
* SITES-12460 - Intégration de Campaign - Intégration de Campaign/AEM Cloud Service rompue
* SITES-11571 - Fragments de contenu - API GraphQL - PersistedQueryServlet doit envoyer 400 s sur des URL incorrectes
* SITES-19946 - Fragments de contenu - API GraphQL - Les modèles ne sont plus analysés au démarrage
* SITES-1605 - Core Backend - DeletePageCommand renvoie NPE en cas de chemin source nul
* SITES-5429 - Principal - ChildrenListServlet itemResourceType permet l’exécution directe du code
* SITES-15553 - Fragments d’expérience - Échec du chargement du panneau latéral de XF si l’URL du fichier XF contient un sélecteur.
* SITES-13666 - Headless - Admin - Error Log False Positive &quot;com.adobe.cq.dam.cfm.headless.ui.impl.models.CFHomeCardModelImpl L’identifiant de configuration ne doit pas être nul&quot;
* SITES-17164 - Éditeur de page - [Cloud, 6.5 Forms] L’aperçu de l’éditeur de thème du formulaire adaptatif est rompu
* SITES-14340 - Interface utilisateur d’administration des sites - NPE dans VersioningTimelineEventProvider.accept
* SKYOPS-68611 - Sling - repoinit - Port sling repoinit créer un correctif de chemin d’accès dans la branche de maintenance
* CQ-4354678 - WCM - Traduction - Les tâches de traduction exportent le contenu traduit
* CQ-4355167 - WCM - Traduction - Pas de fenêtre contextuelle lors du marquage d’une tâche de traduction terminée ou archivée
* CQ-4355913 - WCM - Traduction - cartes de langue du projet de traduction en erreur
* GRANITE-47694 - Workflow - Impossible d’obtenir des sous-tâches dans un workflow sur le cloud pour un utilisateur non administrateur
* ASSETS-31097 - Assets Cloud - Journaux remplis avec l’index Avertissements convertis pour /bin/numberofentitiesinfolders.json
* ASSETS-35860 - Assets Cloud - Incorrect Time Fuseau Conversion in AEM Assets Column View
* SITES-15260 - IU classique (héritée) - Bulkedit ajoute des propriétés EMPTY sur la page si l’importation de feuille est utilisée
* SITES-16834 - IU classique (héritée) - Texte manquant après modification de texte à l’aide de l’éditeur en bloc lorsque le texte contient une virgule.
* SITES-17767 - Fragments de contenu - Admin - Prise en charge autorisée de cf-models également pour les dossiers sans noeud jcr:content
* SITES-17683 - Fragments de contenu - Principal - Les fragments de contenu ne sont pas sérialisables avec l’exportateur Jackson
* SITES-18797 - Fragments de contenu - Principal - Résultats GraphQL dupliqués après personnalisation de l’index
* SITES-18076 - Fragments de contenu - Principal - Le texte à plusieurs valeurs a une @TypeHint incorrecte
* SITES-17856 - Fragments de contenu - Modèles et éditeur de modèles - Modèles CF non affichés si la configuration n’est pas un dossier
* SITES-17071 - Principal principal - Une page spécifique n’affiche pas la version dans la chronologie.
* SITES-17285 - Composants principaux - Le recadrage d’image en ligne est différent sur les instances de création et de publication dans AEMaCS.
* SITES-19187 - Composants principaux - Deux méthodes permettant de placer des ressources dans le composant d’image donnent des résultats différents dans la boîte de dialogue
* SITES-20077 - Composants principaux - Recadrage d’image en ligne - Le recadrage est incorrect et les images sont floues
* SITES-17211 - Fragments d’expérience - Boîte de dialogue de sélecteur de chemin du composant Fragments d’expérience qui affiche les fragments d’expérience supprimés
* SITES-17894 - Lancements - La promotion des lancements imbriqués rétablit le contenu du lancement sur une version à partir de son ancêtre.
* SITES-16042 - MSM - Live Copies - Les annotations s’affichent incorrectement dans la Live Copy après le déploiement
* SITES-16691 - MSM - Live Copies - Lorsque le client sélectionne &quot;déploiement&quot; ou &quot;déploiement vers&quot; à partir de l’icône &quot;déploiement&quot; sur un composant, le bouton &quot;continuer&quot; est grisé.
* SITES-16733 - MSM - Live Copies - La page d’index de plan directeur ne peut pas être déployée lorsque rep:policy est appliqué au noeud
* SITES-17155 - MSM - Live Copies - Les en-têtes et les pieds de page sont traduits en anglais lorsque LiveCopy est renommé
* SITES-17492 - MSM - Live Copies - AEM incohérences de mise en page de Live Copy de la page
* SITES-19316 - MSM - Live Copies - Le lien de référence vers le fragment d’expérience ne se met pas à jour dans la copie de langue
* SITES-19347 - MSM - Live Copies - Lenteur de l’auteur de la production et messages de panne du service - capsules redémarrant fréquemment - alertes d’intégrité
* SITES-19790 - MSM - Live Copies - Informations d’aperçu incorrectes après la création de LiveCopy
* SITES-20086 - MSM - Live Copies - Le déploiement MSM pour CF dans Assets déploie toutes les Live Copies même si une Live Copy est sélectionnée pour être déployée.
* SITES-20088 - MSM - Live Copies - Problème de page vierge Post déploiement XF dans les propriétés - AEM as a Cloud Service
* SITES-16854 - Éditeur de page - Déposer la superposition cible couvre le parsys dans les composants avec la fonction &quot;Sélectionner un panneau&quot;.
* CQ-4355563 - Projets : le paramètre de chemin d’accès est incorrect. Remplissage de &quot;?appId=aemshell&quot; pour le script de recherche de boîte de réception de projet
* SITES-16876 - Site rapide - Déploiement de thème - CSS et JS manquants sur les pages d’aperçu 2
* SITES-18418 - Interface utilisateur d’administration de Sites - La fonctionnalité d’affichage/masquage du widget pathfield ne fonctionne pas correctement lorsque le champ est obligatoire.
* SITES-19534 - Interface utilisateur d’administration des sites - Impossible d’ouvrir la boîte de dialogue Autorisations effectives après AEM mise à niveau vers la version 6.5.19
* SITES-19203 - Éditeur de modèles - Stratégies de modèle modifiables Bouton de suppression Alignement incorrect du texte et chevauchement des styles
* CQ-4354881 - WCM - Traduction - Le chemin des fragments de contenu est défini sur source (en-us) lorsque les fragments de contenu sont traduits dans le cadre d’une page.
* CQ-4355289 - WCM - Traduction : seuls les 40 premiers éléments s’affichent dans les Cloud Service de traduction
* CQ-4355866 - WCM - Traduction - Le workflow de traduction renvoie une erreur pour les pages existantes.
* CQ-4355797 - Workflow - Impossible d’utiliser l’étape de workflow en standard
* GRANITE-48938 - Workflow - Auteur affichant les ressources bloquées dans un état de &quot;publication en attente&quot;. Problème dans le nouveau cache de carte de charge utile persistant.
* GRANITE-49036 - Workflow - Requête de fonctionnalités | Possibilité de planifier et de configurer la purge des modules de workflow
* SITES-17393 - Extensions de workflow - Échec de l’arborescence de contenu de publication lors de l’utilisation de lanceurs de workflow pour cq:Tag
* SITES-17759 - Extensions de workflow - Tree-Activation-Workflow pour les balises qui ne fonctionnent pas dans AEMaaCS
* FORMS-12411 : sur les appareils Android, la variable `Maximum Number of Characters Validation` ne fonctionne pas pour le composant de zone de texte de formulaire adaptatif.
* FORMS-13377 : lorsqu’un utilisateur tente d’ajouter la police personnalisée et d’exécuter le pipeline pour la configurer, l’erreur &quot;ContainersNotReady&quot; échoue.
* FORMS-13267 : lorsqu’un utilisateur ajoute un composant de liste déroulante de formulaire adaptatif, l’identifiant de la liste déroulante ne parvient pas à générer
* FORMS-13544 : lorsqu’un utilisateur ajoute un composant Conteneur de formulaires adaptatifs avec une disposition d’assistant, il ne fonctionne pas correctement lors de la création de formulaires.
* FORMS-13091, FORMS-13414 : si l’utilisateur tente de configurer une URL de domaine personnalisé dans le stockage Azure Blob, il échoue.
* FORMS-13595 : lorsqu’un utilisateur tente d’enregistrer le formulaire à un autre emplacement, il ne peut pas voir les boutons &quot;Sélectionner un dossier&quot; et &quot;Annuler&quot; si la résolution du navigateur est définie sur 100 %. Cependant, l’option est visible lorsque la résolution est définie sur 75 %.
* FORMS-10952 : lorsqu’un utilisateur ajoute un composant de liste déroulante de formulaire adaptatif à un formulaire adaptatif et utilise la propriété &quot;Définir les options&quot; en fonction de diverses règles personnalisées, la propriété &quot;Définir les options&quot; ne fonctionne que pour la dernière règle.
* FORMS-11471 : le chargement différé d’un fragment échoue lorsque l’appel &quot;emitter.json&quot; échoue en raison d’une interruption du réseau.
* FORMS-11786 : lorsqu’un utilisateur bascule entre les mois dans le widget Calendrier, le composant Sélecteur de date affiche une ligne supplémentaire.
* FORMS-12093, FORMS-12093 : lorsqu’un utilisateur coche la case Formulaire adaptatif pour envoyer un formulaire, la valeur incorrecte avec un supplément  `\` est stocké dans la zone de texte
* FORMS-11993 : lorsqu’un utilisateur clique sur une image à l’aide du composant &quot;Prendre une photo&quot; dans le composant Pièce jointe d’un appareil iOS, toutes les images sont ajoutées au dossier portant le même nom.
* FORMS-12555 : lorsqu’un utilisateur tente d’intégrer AEM Forms à une plateforme de messagerie avec une URL publiée AEM, AEM Forms n’ajoute pas method=post lors du rendu de la page. Ce problème se produit même si POST est défini dans l’action d’envoi avec l’URL. La plateforme de messagerie ne reconnaît pas cela comme un formulaire.
* FORMS-12938 : les formulaires HTML5 ne fonctionnent pas ou ne se chargent pas correctement dans le navigateur Microsoft Edge avec le mode de compatibilité IE
* FORMS-12032 : lorsqu’un utilisateur envoie un formulaire, le chemin d’accès de l’action d’envoi ne pointe pas correctement
* FORMS-12445 : les valeurs incorrectes sont capturées dans le modèle de données de formulaire après la modification de l’ordre des options de bouton radio et la publication du formulaire.
* FORMS-12947 : lorsqu’un utilisateur ajoute une nouvelle langue à un dictionnaire existant, il ne fusionne pas ou n’ajoute pas
* FORMS-11363 : lorsqu’un utilisateur envoie un formulaire via Workspace, un problème d’affichage se produit dans les tableaux pendant son rendu.
* FORMS-11756 : lorsqu’un utilisateur ajoute les fonctionnalités JavaScript ES6 telles que `let` et `const` dans les fonctions personnalisées, l’éditeur de règles ne s’ouvre pas. Cette version de maintenance prend en charge ES10
* FORMS-13164 : si l’utilisateur génère un PDF, des lignes vierges inattendues y sont ajoutées après envoi.
* FORMS-13789 : lorsque l’utilisateur tente de générer plusieurs PDF, l’API de lot de sortie échoue
* FORMS-11483 : lorsqu’un utilisateur convertit un PDF en PDF/A-2B ou PDF/A-3B, il ne parvient pas à convertir et affiche une erreur de validation.
* FORMS-10501 : lorsqu’un utilisateur appelle HSM, les documents sont certifiés, mais il n’active pas LTV.
* FORMS-11546 : lorsqu’un auteur de formulaire utilise des panneaux répétés dans un formulaire adaptatif, l’attribut ARIA est absent des balises de HTML. Cela améliore l’accessibilité des panneaux répétés du formulaire adaptatif
* FORMS-11826 : en raison des libellés correspondants Arial® labellisés par et Arial®, les lecteurs d’écran ne sont pas en mesure de faire la distinction entre ces deux étiquettes. Pour résoudre ce problème, le libellé « aria-labelledby » est remplacé par « aria-describedby » pour les champs de formulaire. (F). Cela améliore l’accessibilité du Forms adaptatif
* FORMS-12626, FORMS-13094 : les utilisateurs ne peuvent pas accéder à la barre d’outils à l’aide du clavier pour enregistrer ou modifier du contenu sur la page de l’éditeur de formulaires. Ce problème d’accessibilité a été corrigé.
* FORMS-13102 : au cours du processus de création de formulaire, les icônes disponibles dans la page Forms and Documents ne disposent pas de fonctions descriptives pour les personnes ayant un handicap différent. Ce problème d’accessibilité a été corrigé.

### Problèmes connus {#known-issues-15787}

* SITES-17934 - Fragments de contenu - L’aperçu échoue en raison de la protection du DoS pour une grande arborescence de fragments. Voir [Base](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-23945)

### Fonctionnalités et API obsolètes {#deprecated-15787}

* [Obsolescence des informations d’identification JWT dans Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

Jetez un coup d’oeil à [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md) pour savoir ce qui a été abandonné ou supprimé dans AEM as a Cloud Service.

### Avis de modification {#change-notice-15787}

**Actions requises**

#### Définir la version CM Java sur 11 {#set-java-version-11}

La nouvelle version d’aem-sdk-api contient des classes compilées avec une cible Java 11, qui n’est pas compatible avec le JDK version 1.8 par défaut de l’environnement de génération de Cloud Manager. Cette mise à jour nécessite que Maven soit exécuté à l’aide de JDK 11.

Il est conseillé aux clientes et clients d’ajouter un fichier `.cloudmanager/java-version` à la racine de leur référentiel git avec le contenu : `11`. Voir [Environnement de création/Définition de la version du JDK Maven](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version).


### Technologies intégrées {#embedded-tech-15787}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [API Oak 1.60.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.24.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
