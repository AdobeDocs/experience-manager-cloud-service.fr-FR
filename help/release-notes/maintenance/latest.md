---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: e8ea040ba3f8c73d7ed64c9669ac1d0a22d3a3c8
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 19%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 12441 {#release-12441}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 12441, publiée publiquement le 27 juin 2023. Cette mise à jour de maintenance est une mise à jour de la version de maintenance 12255 précédente.

L’activation des fonctionnalités de la version 2023.7.0 fournit l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-12441}

- SITES-8769 : Amélioration des appels StyleImpl dans ResponsiveGrid
- Forms-5054 : Ajout de la prise en charge de toutes les [statues](https://opensource.adobe.com/acrobat-sign/acrobat_sign_events/webhookeventsagreements.html) pris en charge par Adobe Sign.

### Problèmes résolus {#fixed-issues-12441}

- Diverses mises à jour liées à l’accessibilité
- SITES-12688 : Éditeur de page : Opérateur logique OU ne fonctionnant pas correctement dans la recherche de l’outil de recherche de ressources
- SITES-4951 : Éditeur de page : La recherche de balises dans l’éditeur de page ne trouve pas de sous-balises.
- SITES-12465 : Fragments d’expérience : Touches de flèches ne fonctionnant pas dans la boîte de dialogue du composant Fragment d’expérience
- SITES-12893 : Fragments d’expérience : Application d’une validation de référence circulaire aux fragments d’expérience
- SITES-12715 : Fragments d’expérience : Les configurations de service Cloud appliquées au dossier de fragments Experience ne sont pas conservées.
- SITES-13097 : Fragments d’expérience : Impossible d’ajouter des fragments d’expérience à un projet de traduction
- SITES-13165 : GraphQL : Restaurer le comportement par défaut pour le filtrage des valeurs nulles
- SITES-12577 : Vérificateur de lien : Le transformateur ne réécrit pas les liens par intermittence
- SITES-13559 : MSM : Exception &quot;N’est pas modifiable&quot; générée lors du déploiement du composant
- SITES-11757 : MSM : La configuration du déploiement hérité de Parent n’est pas rétablie pour les pages enfants.
- SITES-14073 : Administration des sites : Le rapport CSV échoue avec 500 lors de la sélection d’aucune propriété à exporter
- Forms-7648 : Impossible de valider le nombre maximal de chiffres dans un composant de zone numérique. Le script de validation ne fonctionne pas.
- Forms-8177 : Lorsque le service Forms est principal, la variable `com.adobe.aem.formsndocuments.publish.AssetReferenceProvider Failed to retrieve asset dependencies` rencontre une erreur.
- Forms-8300 : Lorsqu’un utilisateur tente de déléguer une tâche après l’avoir ouverte, la réponse du délégué recharge la tâche, au lieu d’ouvrir l’interface utilisateur de la boîte de réception d’AEM de l’utilisateur.
- Forms-8500 : Sur le navigateur Microsoft® Edge avec l’option Mode IE activée, HTML5 Forms ne s’ouvre pas.
- Forms-8541 : Lors du rendu d’une Forms adaptative, une exception de pointeur nul se produit.
- Forms-8964 : Lorsqu’un formulaire est ouvert sur un appareil Android™ sur Google Chrome ou Mozilla Firefox, le texte saisi dans le composant de zone de texte ne peut pas être supprimé.
- Forms-9026 : Lorsqu’un utilisateur crée un formulaire adaptatif basé sur un schéma JSON complexe et valide, fait glisser les champs de schéma JSON associés vers l’éditeur de Forms adaptatif pour créer les champs Forms adaptatif et actualise la fenêtre de l’éditeur de Forms adaptatif, tous les champs sont supprimés et l’éditeur de Forms adaptatif apparaît vide.
- Forms-9263 : Lorsque le texte d’affichage d’une case à cocher contient un caractère spécial, les utilisateurs ne peuvent pas cocher de ces cases.
- Forms-8668 : Lors du rendu d’un aperçu du PDF d’un formulaire, certains vidages de pile Java™ non requis apparaissent dans les journaux d’erreurs. Cependant, le rendu du formulaire ne pose aucun problème.
- Forms-8116 : Lorsque des règles sont appliquées au composant Conteneur de Forms adaptatif, les règles appliquées ne sont pas enregistrées.
- Forms-7906 : Lorsqu’un formulaire adaptatif est ajouté à un composant de conteneur AEM Sites, l’éditeur de règles ne s’ouvre pas.
- Forms-8846 : La propriété de référence Bind ne fonctionne pas pour le composant de pièces jointes Adaptive Forms.
- Forms-9072 : Lorsque vous recherchez un schéma lors de la création d’un fragment de formulaire, le résultat de la recherche ne renvoie aucun schéma à sélectionner.
- Forms : Correction de plusieurs bogues liés à l’accessibilité afin d’améliorer l’accessibilité des fonctionnalités d’AEM Forms.

### Problèmes connus {#known-issues-12441}

Aucun.

### Technologies intégrées {#embedded-tech-12441}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.50-T20230405052634-f9df4aa | [API Oak 1.50.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| API SLING AEM | Version 2.27.0 | [API Apache Sling 2.27.0](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.0 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
