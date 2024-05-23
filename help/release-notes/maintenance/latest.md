---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: d107f40c4bc43837db9d8fab3d06627d9e930620
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 10%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 16357 {#release-16357}

Vous trouverez ci-dessous un résumé des améliorations continues de la version de maintenance 16357, rendue publique le jeudi 22 mai 2024. La version de maintenance précédente était la version 16145.

L’activation des fonctionnalités de la version 2024.5.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) pour plus d’informations.

### Améliorations {#enhancements-16357}

* SITES-19579 : API Java pour migrer les fragments de contenu d’un modèle à un autre.
* SITES-19698 : [Ouvrir l’API] Créez une opération de lecture pour gérer un schéma d’interface utilisateur par modèle dans la définition OpenAPI.
* SITES-19834 : Adobe I/O des identifiants manquants pour la publication/annulation de publication.
* SITES-20146 : Activer la version d’aperçu / Comparer pour les pages déplacées.
* SITES-19973 : Mise en oeuvre de l’API de recherche CFM.
* SITES-20333 : amélioration de la validation lors de la création de fragments de contenu.
* SITES-20334 : amélioration de la validation lors de la modification des modèles de fragment de contenu.
* SITES-20585 : Améliorez l’API de recherche de fragments de contenu pour filtrer par paramètres régionaux.
* SITES-20594 : renvoie le nom complet de l’utilisateur qui crée/modifie/réplique une ressource.
* SITES-20601 : [OpenAPI] Mettez à jour l’API de recherche CF afin de ne récupérer que les fragments de contenu enfant directs.
* SITES-20656 : [BE] Fournissez une option permettant de faire correspondre la casse lors du remplacement d’une chaîne.
* SITES-20405 : [Xwalk] Prise en charge de mimeType pour la réduction du champ.
* SITES-17854 : Prise en charge de l’UUID pour les références CF et Assets (Pfizer MVP).
* SITES-1955 : API de modèle simple pour le schéma d’interface utilisateur.
* SITES-19611 : [Ouvrir l’API] Créez une opération d’écriture/de mise à jour pour gérer un schéma d’interface utilisateur par modèle dans la définition OpenAPI.
* SITES-19614 : [Xwalk] Pagination des feuilles de calcul / défilement infini.
* SITES-20005 : le pipeline de création doit avoir un délai d’événement configurable.
* SITES-20121 : Autoriser defaultValue pour les champs d’énumération.
* SITES-20342 : [Serveur principal] Publier au niveau du dossier : ajoutez un filtre pour publier uniquement les CF.
* SITES-20355 : suppression des modèles de fragment de contenu et des servlets de l’API d’autorisations.
* SITES-20387 : La navigation dans l’administration des balises calcule toujours l’utilisation des balises.
* SITES-20495 : [BE] Possibilité d’obtenir l’autorisation de publier au niveau du dossier.
* SITES-20653 : [Xwalk] ajoutez experience-start-date et -end-date.
* SITES-20666 : [Xwalk] test doit être désactivé par défaut lors de la création.
* SITES-20752 : [cq-wcm-core] Lancements Apple pour les CF.
* SITES-20946 : Ajoutez une balise en tant que propriété dans le point de terminaison des modèles LIST.
* SITES-20947 : [persistence] récupérer la sous-tâche par l’identifiant du fragment de contenu.
* SITES-21012 : Fusionner le schéma de métadonnées de modèle avec le produit.
* SITES-21769 : utilisez le préfixe /jcr:id/ chemin pour la récupération de ressource par identifiant.
* ASSETS-30379 : la vérification de la licence DRM décrit l’arborescence complète des ressources en cours de téléchargement.
* ASSETS-35535 : [Erreur de l’adaptateur DataS] Les téléchargements de ressources vides doivent être ignorés pour les événements v1.
* SITES-21550 : [Xwalk] Métadonnées personnalisées : nombre, date, date, heure, champs d’heure.
* SITES-20149 : RTC : [cq-wcm-launches-core] Exportez une nouvelle API pour les lancements pour les CF.
* SITES-20150 : RTC : [cq-command] Ajoutez de nouvelles méthodes à l’API existante.
* SITES-20451 : Ajoutez un module externe sidecar à wcm-commons.
* SITES-20499 : [MSM][Async] Extrayez le code de AsyncOperationServlet vers une classe d’utilitaire.
* SITES-20763 : mise à jour des points de terminaison de l’API de diffusion dans l’intégration des sites.
* SITES-20583 : Ajoutez une balise comme propriété dans `LIST`/search fragments.
* CQ-4356445 : Mise en oeuvre du producteur d’événements et du schéma.
* CQ-4356625 : Améliorez le contrôle d’autorisation dans language ecopyrendercondition.jsp.
* CQ-4356629 : Améliorez la condition de rendu isWorkflowUser de l’archivage des autorisations.
* CQ-4356934 : simplifiez l’API RequestProcessor lors de l’utilisation des entités de réponse.
* CQ-4357214 : les processeurs de requêtes ne doivent pas dépendre de la logique de servlet.
* SITES-16392 : La création de lancement ayant échoué ne doit pas laisser le contenu en mémoire vide.
* SITES-20238 : [RTC] Pfizer MVP - Ajoutez l’API CF pour résoudre les chemins CF en identifiants et vice versa.
* SITES-21043 : [CF][launches] Améliorations des performances du port latéral pour Cloud Service.
* SITES-21044 : [CF][launches] Le mode asynchrone du port latéral permet de modifier la mise en oeuvre de la payload vers Cloud Service.
* FORMS-7483 : l’analyseur de schémas JSON AEM Forms prend désormais en charge le schéma JSON (2020-12).
* FORMS-13209 : un gestionnaire est inclus pour remplacer les gestionnaires de succès et d’échec d’envoi par défaut d’Adaptive Forms. Vous pouvez configurer ces gestionnaires via l’éditeur de règles de Forms adaptatif.
* FORMS-13612 : les lecteurs d’écran lisent désormais les messages d’erreur, les descriptions courtes et les descriptions longues des champs dans les Forms adaptatif basés sur les composants principaux. En outre, la prise en charge a été ajoutée pour invalider les entrées de formulaire adaptatif lorsque le formulaire contient des erreurs et n’est pas valide pour envoi.
* FORMS-12052 : un auteur de formulaire peut désormais appliquer des fonctions personnalisées pour prétraiter les données avant envoi.
* FORMS-11295 : ajout de la prise en charge de SHA256 avec l’algorithme ECDSA pour la signature numérique AEM Forms.
* FORMS-9432 : un type de contenu supplémentaire (point de terminaison REST) a été ajouté à la configuration du cloud de la source de données. Elle permet l’envoi de données dans des paires clé-valeur à un point de terminaison authentifié.

### Problèmes résolus {#fixed-issues-16357}

* SITES-20608 : la personnalisation du fragment d’expérience activée lorsqu’elle est incluse dans un modèle provoque une boucle infinie.
* SITES-19554 : [Xwalk] Éditeur de feuille de calcul : impossible de vider une cellule.
* SITES-19971 : Application d’un correctif à un CFM contenant des onglets modifie l’ordre des champs.
* SITES-20168 : Modèle de fragment de contenu `locked` champ non correctement mis à jour.
* SITES-20522 : les fragments de contenu corrompus rompent le point de terminaison /adobe/sites/cf/fragments.
* SITES-20816 : CF OpenAPI - Incohérence de sortie avec le modèle manquant pour le fragment référencé.
* SITES-21239 : Suppression de la dépendance circulaire ContentFragmentSearchService.
* SITES-20582 : La recherche et la liste des fragments de contenu doivent permettre une profondeur de 0.
* SITES-20559 : [MSM][XF][Lufthansa] Le déploiement des fragments d’expérience depuis les gabarits/la langue vers le pays/la langue ne met pas à jour les références.
* SITES-17772 : AEM : l’utilisateur avec un groupe d’administrateurs ne peut pas déverrouiller la page verrouillée par un autre utilisateur.
* SITES-20401 : [Xwalk] Les métadonnées de section ne prennent pas en charge les propriétés à plusieurs valeurs.
* SITES-21391 : [OpenAPI Event] Aucun événement n’est déclenché lors de la modification du titre ou des balises (propriétés) d’un modèle de fragment de contenu.
* SKYOPS-73234 : l’augmentation du journal des erreurs lors de la mise à niveau du programme de gestion des actifs numériques globale d’AEM Assets vers AEM version 15553 et l’identifiant de communication 35362.
* SKYOPS-75341 : NoSuchMethodError dans le lot de passerelles de distribution.
* SCRNS-3945 : Skyline : Chaîne &quot;Planifié&quot; non localisée dans Screens.
* SITES-20586 : modèle d’horodatage &quot;publié&quot; non mis à jour.
* SITES-16674 : la case à cocher Hériter des configurations de déploiement ne fonctionne pas sur les propriétés de Live Copy.
* SITES-18680 : impossible d’extraire des variations de référence dans une requête graphique (Apple).
* SITES-21233 : [CoreCmp] Accordéon rompu pour GS1 US après upgrade vers 15860.
* SITES-20367 : problème lié à la suppression des lancements dans AEM.
* CQ-4357161 : l’écran de la payload de la boîte de réception AEM renvoie 404.
* SITES-20214 : AEM problème de séquence de configuration de déploiement sur Enregistrer.
* SITES-20364 : 302 Redirections ne fonctionnant pas avec le sélecteur dans l’URL.
* SITES-20547 : Chemins tronqués dans la liste des chemins exclus Live Copy sur AEM as a Cloud Service.
* SITES-20691 : Restriction du modèle de fragment d’expérience ne tenant pas compte des modèles cq:allowedTemplates.
* SITES-21122 : AEM défaut de Live Copy CS avec des fragments de contenu.
* ASSETS-38723 : NPE généré par MetadataRulesProviderImpl lorsque getReadRulesForMetadataChildNodes() est appelé avant que ce.readRules ne soit initialisé.
* SITES-11727 : [GQL] Les données manquantes sont l’hydratation complète des références aux fragments de contenu.
* SITES-19462 : La recherche de ressources ne fonctionne pas correctement dans AEM Cloud.
* SITES-19994 : verrouillage du bouton Fermer lorsque les utilisateurs tentent de fermer le fragment de contenu.
* SITES-20029 : Les versions de fragments de contenu sont créées juste après leur fermeture, sans modifier le contenu.
* SITES-21316 : Aperçu du fragment : l’aperçu échoue en raison de modifications du code de SITES-11727.
* SITES-20023 : le téléchargement de fichiers ne fonctionne pas pour les ressources distantes (ressources de génération suivante) dans plusieurs champs.
* ASSETS-37611 : le workflow &quot;Demande d’achèvement de l’opération de déplacement&quot; est déclenché pour la ressource non publiée.
* CQ-4357278 : DispatcherServlet renvoie NPE si getRequestBodyType renvoie null.
* CQ-4357279 : le traitement des requêtes échoue lorsqu’il n’existe aucun pathInfo pour une requête.
* SITES-20496 : [Xwalk] Aucune option de propriétés lors de la sélection d’une feuille de calcul dans l’administrateur du site.
* FORMS-13827 : dans l’éditeur de règles de Forms adaptatif, l’opération WHEN ne prend actuellement pas en charge différents types de champs avec des sélecteurs de date.
* FORMS-13786 : dans l’éditeur de règles de Forms adaptatif, la fonctionnalité de glisser-déposer ne fonctionne pas pour les fonctions personnalisées.
* FORMS-13587 : dans l’éditeur de Forms adaptatif, la fonction Émulateur de périphérique ne fonctionne pas correctement pour le Forms adaptatif basé sur les composants principaux.
* FORMS-14376 Lorsqu’un utilisateur appuie sur le bouton Réinitialiser , la console affiche des erreurs si le texte statique est marqué comme non lié.
* FORMS-13801 : même si le composant Conditions générales est désactivé, la case à cocher correspondante reste activée.
* FORMS-11952 : lorsqu’un formulaire est envoyé, l’URL d’envoi générée par le formulaire commence par /content/ au lieu de /portale/, ce qui entraîne un mauvais routage de la requête. Cela empêche la demande d’atteindre les serveurs prévus.
* FORMS-13616 : le sélecteur de date affiche la date actuelle un jour en arrière, probablement en raison d’un problème de fuseau horaire. Il est également difficile de définir le format de date correct en raison de cette incohérence et d’un problème de modèle d’affichage supplémentaire.
* FORMS-13829 : la liste déroulante, contrôlée par des règles pour imiter la fonctionnalité de bouton radio, ne se remplit pas correctement une fois qu’une sélection a été effacée et résélectionnée. Le comportement souhaité consiste à ce que des cases à cocher individuelles agissent comme des boutons radio, ce qui permet une sélection unique à la fois et de désélectionner toutes les options.
* FORMS-14244 : dans un formulaire adaptatif basé sur un XDP avec des scripts intégrés sur des cases à cocher, les scripts ne sont pas exécutés pour les éléments après ces cases à cocher.
* FORMS-14267 : les utilisateurs rencontrent des erreurs de délai d’expiration constantes lors de l’envoi de requêtes d’API dans les environnements de développement, d’évaluation et de production. Ces requêtes sont liées à la génération de PDF, parfois avec des données préremplies à l’aide de la liaison de données. Le problème entraîne un processus de blocage qui finit par expirer, mais réussit à effectuer une nouvelle tentative après l’erreur.
* FORMS-11589 : pour les utilisateurs disposant uniquement de la solution AEM Forms (sans aucune autre solution), le pipeline front-end ne fonctionne pas.
* FORMS-13896 : dans la sortie du document d’enregistrement (DoR), les dates et les nombres sont affichés en arabe, que les données d’entrée soient fusionnées ou non à l’aide de nombres grégoriens.

### Problèmes connus {#known-issues-16357}

Aucun.

### Fonctionnalités et API obsolètes {#deprecated-16357}

Pour savoir ce qui est obsolète ou supprimé dans AEM as a Cloud Service, voir [Fonctionnalités et API obsolètes et supprimées](/help/release-notes/deprecated-removed-features.md).

### Technologies intégrées {#embedded-tech-16357}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.62.0 | [API Oak 1.62.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| API SLING AEM | 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | 2.25.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
