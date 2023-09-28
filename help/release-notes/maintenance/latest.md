---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: c62ae58240298604e6cd7737678603eb734434b3
workflow-type: tm+mt
source-wordcount: '1363'
ht-degree: 7%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 13665 {#release-13665}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 13665, publiée publiquement le 27 septembre 2023. Cette version de maintenance remplace la version 13420.

2023.10.0 Feature Activation fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-13665}

* Diverses améliorations apportées aux API de fragment de contenu.
* ASSETS-26713 : Tableau de bord des ressources : nouveau tableau de bord de l’interface utilisateur d’Experience est désormais accessible à partir de l’interface utilisateur tactile.
* SITES-11206 : Fragments de contenu : API de recherche de fragments de contenu.
* SITES-11262 : Fragments de contenu : bouton pour passer au nouvel éditeur de fragments de contenu.
* SITES-15447 : Core Components : Version 2.23.4.
* FORMS-9624 : introduction du composant CAPTCHA pour Forms adaptatif basé sur les composants principaux.
* FORMS-9913 : amélioration du service d’appel de l’éditeur visuel en ajoutant la possibilité de valider les champs et d’afficher les messages d’erreur et de succès appropriés.
* FORMS-10106 : API GeneratePDFOutput améliorée pour renvoyer le nombre de pages contenues dans le document généré.
* FORMS-2494 : ajout de la prise en charge des fragments de formulaire pour les Forms adaptatifs basés sur les composants principaux.
* FORMS-9807 : ajout de la prise en charge de la navigation vers une URL de page renvoyée suite à un envoi réussi par le biais de l’éditeur de règles de formulaire adaptatif.
* FORMS-10571 : ajout de la possibilité de définir une URL de redirection de page de remerciement en fonction de la réponse d’un service utilisé dans une action d’envoi personnalisée pour Forms adaptatif basée sur les composants principaux.

### Problèmes résolus {#fixed-issues-13665}

* Différentes mises à jour liées aux traductions.
* CQ-4354428 : Workflows : impossible d’effectuer une tâche dans la boîte de réception.
* SITES-9733 : Fragments de contenu : les références de ressources dans le panneau de référence des fragments de contenu affichent 0 (zéro) référence.
* SITES-14561 : Fragments de contenu : correction et amélioration du HTML de la conversion Markup.
* SITES-14882 : Fragments de contenu : une fois que nous avons modifié le fragment de contenu et fermé l’onglet sans cliquer sur le bouton Enregistrer ou fermer, les valeurs sont stockées.
* SITES-15167 : Fragments de contenu : le correctif d’une variation avec une charge utile non valide ne renvoie pas 400 mais 500.
* SITES-15514 : Fragments de contenu : sortie Markdown incorrecte pour le tableau dans l’éditeur de texte enrichi.
* SITES-15661 : Fragments de contenu : n’utilisez pas de contrainte unique et ne réorganisez pas les éléments dans les champs de référence de l’API Fragments.
* SITES-15730 : Screens : la fonctionnalité Aperçu du canal Screens ne fonctionne pas sur le tableau de bord.
* SITES-15995 : Fragments de contenu : les types MIME des champs de texte long de modèle et de fragment sont codés en dur.
* SITES-16074 : Fragments de contenu : Balisez les champs qui ne sont pas des chaînes[] ne peut pas être récupéré depuis JCR.
* SITES-16084 : Fragments de contenu : le navigateur cible est absent de CFHomeCardModelImpl.
* SITES-14773 : Fragments d’expérience : la référence de lien n’est pas mise à jour dans le fragment d’expérience.
* SITES-14899 : Fragments d’expérience : plusieurs offres créées pour des variations XF dans Target.
* SITES-8590 : GraphQL : problèmes de codage des variables dans les requêtes persistantes.
* SITES-9224 : GraphQL : exception &quot;Writer a déjà été fermé&quot; dans GraphQLServlet.
* SITES-14800 : GraphQL : exception dans les requêtes GraphQL persistantes avec des variables.
* SITES-15586 : GraphQL : problème lié au filtrage de requêtes persistantes avec des valeurs &quot;null&quot;.
* SITES-15622 : GraphQL : problème avec les requêtes persistantes avec les paramètres numériques et bool.
* SITES-15654 : GraphQL : problème avec les unions et propriétés du même nom.
* SITES-15267 : Lancements : la promotion ne sélectionne pas les pages de lancement modifiées avant la modification de la configuration du lancement.
* SITES-15406 : Lancements : impossible d’ajouter une page de lancement.
* SITES-15427 : Lancements : comportement incohérent de la portée &quot;Promouvoir la page active et les sous-pages&quot;.
* SITES-15429 : Lancements : création de pages supprimées lors de la promotion de lancements.
* SITES-15462 : Lancements : le processus de promotion automatique publie des pages hors du cadre de la promotion.
* SITES-15815 : Lancements : la suppression de la page du lancement entraîne la non-promotion de Launch.
* SITES-15223 : Éditeur de page : impossible de redimensionner les composants dans l’émulateur de taille de tablette.
* SITES-15463 : Modèles de page : les modèles ne peuvent pas être publiés.
* FORMS-10700 : lors de l’utilisation du composant de sélecteur de date dans un formulaire adaptatif créé sur les composants principaux :
   * Lorsque l’utilisateur envoie le formulaire sans saisir de composant de date, une erreur est consignée.
   * Lorsque vous utilisez des versions localisées du sélecteur de date, certains mois fonctionnent sans problème, la sélection de certains autres entraîne un dysfonctionnement du composant.
* FORMS-9598 : le composant d’intégration AEM Forms ne fonctionne pas.
* FORMS-9579 : vous ne pouvez pas transmettre une valeur booléenne à une fonction lors de l’utilisation de l’éditeur de règles.
* FORMS-9916 : le fait de marquer le champ comme non valide déclenche à nouveau un événement de modification sur le même champ. Cet événement inattendu déclenche à nouveau la règle, créant ainsi une boucle qui se répète jusqu’à ce qu’elle atteigne la limite maximale de 10 répétitions.
* FORMS-10243 : l’option Définir la cible d’action ne fonctionne pas correctement pour Forms adaptatif basé sur les composants principaux. En particulier, lorsqu’un bouton radio est activé et que la règle &quot;Définir la cible d’action&quot; est activée pour un objet de zone de texte, elle ne parvient pas à définir la cible d’action comme prévu, bien que d’autres règles fonctionnent correctement.
* FORMS-10416 : pour un formulaire adaptatif sans affichage, lorsque la propriété &quot;:type&quot; est incluse, le composant d’entrée multiligne apparaît comme un composant d’entrée de texte à une seule ligne ordinaire.
* FORMS-10015 : pour un formulaire adaptatif basé sur les composants principaux, dans l’éditeur de règles, lorsque nous choisissons l’objet de formulaire, il transmet l’objet d’instance de champ entier à la fonction personnalisée au lieu de la seule valeur du champ.
* FORMS-9890 : les utilisateurs du groupe d’administrateurs cloud, sans accès utilisateur aux formulaires, peuvent créer des sources de données, des formulaires et un modèle de données de formulaire. Cependant, ils ne peuvent pas afficher les services disponibles dans le système lors de l’utilisation du &quot;service Appeler&quot; dans l’éditeur de règles.
* FORMS-9075 : lors de l’envoi d’un formulaire adaptatif, les lecteurs d’écran n’annoncent pas tous les messages d’erreur pour les champs obligatoires.
* FORMS-9014 : les problèmes d’accessibilité suivants ont été corrigés :
   * Lors de l’ouverture de la zone de signature tactile, le curseur passe au composant suivant, et non à la zone elle-même. Ce comportement a été confirmé comme un problème par l’équipe d’accessibilité.
   * Après la signature, appuyer sur Entrée ne ferme pas la boîte de dialogue ; les utilisateurs doivent cliquer explicitement sur le bouton OK .
   * Après la signature, l’ordre de tabulation est réinitialisé en haut, plutôt que de rester dans le composant de signature ou de passer au suivant.
   * L’option permettant d’effacer la signature, représentée par une icône croisée, ne fait pas partie de l’ordre de tabulation et n’apparaît que lorsque vous survolez.
   * La boîte de dialogue de &quot;confirmation de signature effacée&quot; n’est pas accessible via le clavier.
   * Le libellé du bouton de signature au clavier doit être corrigé pour être plus clair.
   * Les contrôles dans la signature tactile ne présentent pas le rapport de contraste recommandé.
   * L’état inactif du bouton OK/coche doit inclure l’attribut &quot;aria-disabled&quot;.
   * Le lecteur d’écran ne transmet pas le texte utilisé pour créer la signature saisie, ce qui le rend inaccessible aux malvoyants.
* FORMS-9214 : dans le cas d’une Forms adaptative basée sur les composants principaux, la fonction personnalisée n’est pas appelée, sauf si elle est utilisée pour modifier un autre champ, comme la définition de la valeur d’un autre champ.
* Pour les API Document Generation, le chemin &quot;/content&quot; affiche une incohérence dans son utilisation entre le chemin du modèle, la racine de contenu et les données. Il fonctionne correctement dans certains cas, mais pas de manière uniforme.
* FORMS-10718 : ajout de la prise en charge de l’API resolveNode de GuideBridge pour Adaptive Forms basée sur les composants principaux.
* FORMS-9998 : dans Forms adaptatif basé sur les composants principaux, les fonctions &quot;Est vide&quot; et &quot;N’est pas vide&quot; ne fonctionnent pas comme prévu lors de la validation de la saisie de texte via l’éditeur de règles.
* FORMS-10236 : le composant Pièce jointe ne fonctionne pas correctement pour les Forms adaptatifs basés sur les composants principaux. Lors de l’utilisation du composant de pièce jointe, les aperçus de fichier fonctionnent initialement, mais si vous joignez des fichiers supplémentaires de types ou de formats similaires ou différents, l’aperçu ne fonctionne pas correctement.
* FORMS-10470 : dans le composant de case à cocher, lorsque la valeur par défaut non cochée (&#39;off&#39;) et le type de données est String, le bouton d’envoi ne fonctionne pas.
* FORMS-10534 : dans Forms adaptatif basé sur les composants principaux, l’option d’opérande booléenne s’affiche sur le côté gauche, indiquant qu’elle est sélectionnable. Cependant, lorsqu’un utilisateur tente de la sélectionner, une erreur surligne ou une indication d’erreur se produit, ce qui suggère que la sélection ne fonctionne pas comme prévu.
* FORMS-10248 : dans Forms adaptatif basé sur les composants principaux, la définition de la valeur d’un bouton radio ou d’une case à cocher lorsque le type de valeur de données est Booléen ne fonctionne pas comme prévu.
* FORMS-8114 : le sélecteur de date et le modèle ne sont pas correctement lus par le lecteur d’écran NVDA. Plus précisément, lors de l’utilisation du lecteur d’écran NVDA, le sélecteur de date sans modèle est correctement lu. Cependant, lorsqu’un modèle est appliqué au sélecteur de date, il est lu en tant que tableau au lieu d’être interprété correctement.

### Problèmes connus {#known-issues-13665}

Aucun.

### Technologies intégrées {#embedded-tech-13665}

| Technologie | Version | Lien |
|---|---|---|
| AEM Oak | 1.54-T20230817132355-3800a65 | [API Oak 1.54.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
