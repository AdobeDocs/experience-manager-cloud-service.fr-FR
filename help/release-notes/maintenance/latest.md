---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 1a128e35be06d018ec25fb0e6a479cfd0d242dbd
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 12%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 14227 {#release-14227}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 14227, publiée publiquement le 9 novembre 2023. Cette mise à jour de maintenance est une mise à jour de la version de maintenance 14029 précédente. La version de maintenance 14227 remplace la version 14157 pour corriger un problème.

L’activation des fonctionnalités de la version 2023.11.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-14227}

<!--* ASSETS-29631: Assets Cloud: Use dam:roles for secure delivery/search.-->
* CQ-4354515 : Traductions : option pour supprimer la traduction des ressources référencées.
* FORMS-9993 : définissez les étapes pour déplacer les composants principaux de Forms dans Skyline.
* FORMS-10570 : API intégrées d’EC à API - Premier routeur.
* GRANITE-48143 : mettez à niveau Sling ResourceMerger vers la version 1.4.4.
* SITES-14874 : Eventing : développez l’arborescence CFM pour les événements de modèle afin d’inclure les modifications de métadonnées.
* SITES-2719 : Fragments de contenu : prise en charge du balisage pour les variations de fragments de contenu (réactivée).
* SITES-3619 : Fragments de contenu : les balises de variation CF GraphQL sont générées dans JSON et filtrées par balise de variation (réactivée).
* SITES-13750 : Fragments de contenu : supprimez des balises pour un modèle de fragment de contenu.
* SITES-13920 : Fragments de contenu : prise en charge de la configuration minItems pour plusieurs champs (version préliminaire).
* SITES-14080 : Fragments de contenu : supprimez la balise d’une variation de fragment de contenu.
* SITES-14770 : Fragments de contenu : la variation de fragment doit inclure la propriété fieldTags.
* SITES-15356 : Fragments de contenu : renvoi de l’etag en tant qu’en-tête de réponse lors de la création d’une ressource.
* SITES-15357 : Fragments de contenu : permettent la publication de fragments sans leurs références.
* SITES-15938 : Fragments de contenu : métadonnées de référence de contenu manquantes.
* SITES-16078 : Fragments de contenu : renseignez la propriété result de validation de la variation lorsqu’un fragment est récupéré.
* SITES-16545 : Fragments de contenu : ajoutez un point de terminaison pour récupérer les références de la variation d’un fragment de contenu.
* SITES-16853 : Fragments de contenu : suppression /adobe/sites/cf/fragments/{fragmentId}/variation/{name}point de terminaison /tags.

### Problèmes résolus {#fixed-issues-14227}

* Différents problèmes d’accessibilité résolus
* ASSETS-31015 : impossible de charger des fichiers vers Assets avec des extensions de fichiers inconnues.
* ASSETS-24739 : Désactivez le point de terminaison d’action personnalisée Frame.io sur Publish.
* CMGR-49845 : Dépassement de contenu : problème lié à l’identification du chemin racine correct pour un point de contrôle donné.
* CMGR-49709 : Dépassement de contenu : mettez à jour le filtre de propriété pour ignorer les propriétés supplémentaires.
* CQ-4354503 : Suppression aléatoire de la configuration Adobe IMS.
* CQ-4354414 : ConfigurationReplicationEventHandler crée de nombreuses actions de vidage individuelles.
* CQ-4354401 : Traductions : la ressource créée par les projets doit être enregistrée avant de commencer le traitement des ressources.
* CQ-4354430 : Traductions : obtention d’une erreur lors de l’ajout de ressources ne faisant pas partie d’une structure de dossiers de langue à un projet de traduction.
* CQ-4354412 : Traductions : suppression du contenu de la tâche de traduction sans supprimer tout le contenu référencé.
* CQ-4354636 : Traductions : la création d’une copie de langue au niveau racine de la langue n’ajuste pas les chemins d’accès dans la page.
* CQ-4354700 : Workflows : l’écran de charge utile de workflow ne se charge pas.
* CQ-4354834 : Workflows : impossible d’ajouter un commentaire dans la tâche de boîte de réception de workflow.
* FORMS-11302 : le titre du composant modifié dans l’éditeur de texte enrichi s’affiche incorrectement dans Éditeur de formulaire adaptatif > Éditeur de règles.
* GRANITE-45706 : l’importation de l’i18n échoue si la valeur de la clé a &quot;Äú)(Äù).
* SITES-14156 : Eventing : les événements de publication ne sont pas toujours envoyés.
* SITES-14520 : GraphQL : performance incorrecte avec les requêtes graphql paginées en raison de FT_SITES-2719.
* SITES-16444 : GraphQL : DataFetchingException pour les champs de même nom manquants dans la requête GraphQL.
* SITES-16225 : GraphQL : les types de contenu des champs de modèle et de fragment d’éditeur de texte enrichi renvoyés par l’API Java ne sont pas corrects.
* SITES-15373 : Fragments de contenu : /adobe/sites/cf/fragments/{fragmentId}/variation/{name}Le point de terminaison /tags n’utilise pas les conventions d’affectation de nom de ressource correctes.
* SITES-15709 : Fragments de contenu : problème de création d’un point de terminaison de modèle lors de la création d’un champ booléen.
* SITES-15727 : Fragments de contenu : le champ de type &quot;Balise&quot; ne peut être ajouté qu’une seule fois dans l’éditeur de modèles.
* SITES-15782 : Fragments de contenu : propriété unique manquante du modèle de champ de type Énumération.
* SITES-15786 : Fragments de contenu : le fragment de contenu ne peut pas être créé dans un dossier contenant &quot;.
* SITES-15790 : Fragments de contenu : mettez à jour l’en-tête de l’emplacement pour la création de version.
* SITES-15923 : Fragments de contenu : l’administrateur CF n’affiche pas tous les dossiers.
* SITES-15987 : Fragments de contenu : obtention de 500 lors de la création d’une variante.
* SITES-16067 : Fragments de contenu : le type MIME du champ de fragment de texte long ne peut pas être modifié.
* SITES-16074 : Fragments de contenu : Balisez les champs qui ne sont pas des chaînes[] ne peut pas être récupéré depuis JCR.
* SITES-16079 : Fragments de contenu : /fragments/{id}/reference a commencé à renvoyer des doublons.
* SITES-16118 : Fragments de contenu : si un fragment est corrigé et qu’un champ de fragment est manquant dans le modèle, une exception est générée.
* SITES-16119 : Fragments de contenu : si les métadonnées de fragment contiennent des champs non reconnus, une exception est générée.
* SITES-16121 : Fragments de contenu : la récupération d’un champ de date de modèle renvoie une exception.
* SITES-16123 : Fragments de contenu : si une ressource n’est pas un fragment de contenu, le point de terminaison get fragments renvoie une exception.
* SITES-16208 : Fragments de contenu : ContentFragmentModelIdentifier expose une propriété de titre trompeuse.
* SITES-16707 : Fragments de contenu : les types de données des modèles de fragment de contenu ne sont pas correctement lus.
* SITES-16818 : Fragments de contenu : effectuez la suppression uniquement en présence de balises.
* SITES-16207 : Fragments de contenu : l’opération du POST /adobe/sites/cf/models renvoie deux codes d’état OK différents.
* SITES-15616 : Fragments de contenu : le point de terminaison de publication ne publie pas parfois toutes les références d’un fragment de contenu.
* SITES-16027 : Fragments de contenu : les informations de référence sur la variation sont manquantes dans la réponse au fragment.
* SITES-16243 : Fragments de contenu : la recherche et le remplacement ne fonctionnent pas avec les champs dont le rendu est : Multiple.
* SITES-16250 : Fragments de contenu : la correction d’un CF renvoie parfois un en-tête d’etag incorrect.
* SITES-16686 : Fragments de contenu : les références de fragments de contenu qui ne sont pas des fragments sont sérialisées lorsque la référence parent est à la profondeur maximale.
* SITES-12880 : Fast-Track : Localisation des correctifs pour Sites > Configuration d’Analytics.
* SITES-16103 : Fragments d’expérience : les options Target ne s’affichent pas sous les Cloud Service en raison d’une erreur de console.
* SITES-16001 : MSM : Possibilité d’exclure des composants à plusieurs champs de la configuration de déploiement lors de la création de Live Copy.
* SITES-16559 : MSM : suppression des configurations de déploiement pendant le processus de déploiement des fragments d’expérience.
* SITES-16797 : MSM : correction de la réactivation de l’héritage pour un champ CF dans l’éditeur.
* SITES-16273 : Éditeur de page : Copier l’erreur de collage dans les pages aem sites à partir du Presse-papiers.
* SITES-16126 : Administration de sites : performances de création ralenties pour les utilisateurs non-administrateurs après SITES-10288.
* FORMS-10534 : une erreur se produit dans l’éditeur de règles lors de la sélection de l’option Opérand booléen.
* FORMS-10248 : dans un formulaire adaptatif, lorsque la valeur de données est de type booléen, les règles ne parviennent pas à définir correctement les valeurs des boutons radio ou des composants de case à cocher.
* FORMS-11361 : le composant déroulant sélectionne automatiquement la première option de la liste par défaut.
* FORMS-11413 : une erreur liée au service de préremplissage du portail Forms est déclenchée par le Forms adaptatif, même lorsque le service n’est pas en cours d’utilisation.
* FORMS-11433 : lorsqu’un composant non-formulaire est inclus dans un formulaire adaptatif, le processus d’envoi échoue.
* FORMS-11206 : lorsqu’un utilisateur tente de planifier un processus de publication pour un formulaire adaptatif, il ne fonctionne pas comme prévu.
* FORMS-11546 : Lighthouse a détecté une étiquette ARIA manquante pour les panneaux répétés dans un formulaire adaptatif, ce qui a une incidence sur l’accessibilité.
* FORMS-11095 : l’attribut ARIA est incorrectement défini pour les champs de numéro de téléphone, d’adresse électronique et de numéro, ce qui entraîne des problèmes d’accessibilité.

### Problèmes connus {#known-issues-14227}

Aucun.

### Technologies intégrées {#embedded-tech-14227}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.56-T20230927085643-189caed | [API Oak 1.56.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
