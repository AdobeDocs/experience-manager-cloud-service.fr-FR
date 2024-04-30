---
title: Surveillance des personnes en temps réel pour les formulaires Edge Delivery Services
description: La surveillance des personnes en temps réel pour les formulaires Edge Delivery Services implique le suivi et l’analyse continus des interactions des personnes avec les formulaires.
feature: Edge Delivery Services
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
source-git-commit: 2affe155b285986128487043fcc4f2938fc15842
workflow-type: ht
source-wordcount: '701'
ht-degree: 100%

---


# Surveillance des personnes en temps réel pour les formulaires Edge Delivery Services

Adobe Experience Manager utilise la surveillance des utilisateurs et utilisatrices réels (RUM) pour comprendre les interactions des visiteurs et visiteuses avec les sites gérés par Adobe Experience Manager. Cela permet de diagnostiquer les problèmes de performance et d’évaluer l’efficacité des expériences. La surveillance des utilisateurs et utilisatrices réels protège la confidentialité des visiteurs et visiteuses en utilisant les techniques d’échantillonnage, de sorte qu’aucune information personnelle n’est collectée par les sites que vous visitez. Il n’est pas autorisé d’ajouter des données personnelles à la collecte de données RUM. La surveillance des utilisateurs et utilisatrices réels dans Adobe Experience Manager est conçue pour préserver la confidentialité des visiteurs et visiteuses et minimiser la collecte de données.

## Avantages de la surveillance des utilisateurs et utilisatrices en temps réel pour les formulaires Edge Delivery Services {#advantages}

AEM utilise la surveillance des utilisateurs et utilisatrices en temps réel aux fins suivantes :

* Pour identifier et corriger les goulets d’étranglement au niveau des performances sur les sites
* Pour estimer le nombre de pages vues sur les sites des clientes et clients
* Pour comprendre l’interaction d’Adobe Experience Manager avec les bibliothèques d’analyse, de ciblage ou externes sur la même page, ce qui permet d’améliorer la compatibilité.

## Conditions préalables

Vous pouvez afficher le tableau de bord de surveillance des utilisateurs et utilisatrices en temps réel pour les formulaires Edge Delivery Services en accédant à l’URL suivante : https://data.aem.live/?ext=forms

![Écran de connexion RUM pour les formulaires Edge Delivery Services](/help/edge/assets/rum-login-screen.png)

Pour vous connecter à votre tableau de bord de surveillance des utilisateurs et utilisatrices en temps réel pour les formulaires Edge Delivery Services, saisissez les éléments suivants :
* **URL** : l’URL est spécifique au site ou au domaine de l’utilisateur ou de l’utilisatrice. Les utilisateurs et utilisatrices ont la possibilité de filtrer le site ou le domaine pour afficher le tableau de bord en fonction de leurs besoins.
* **Clé domaine** : l’utilisateur ou l’utilisatrice génère manuellement la clé de domaine. Pour plus d’informations, consultez la documentation [Générer la clé de domaine RUM](https://aemcs-workspace.adobe.com/rum/generate-domain-key).

### Tableau de bord de surveillance des utilisateurs et utilisatrices en temps réel pour les formulaires Edge Delivery Services

Une fois l’URL et la clé de domaine saisies dans l’écran de connexion, vous pouvez accéder au tableau de bord de surveillance des utilisateurs et utilisatrices en temps réel pour les formulaires Edge Delivery Services.

L’illustration ci-dessous présente le tableau de bord RUM pour les formulaires Edge Delivery Services :

![Tableau de bord de formulaires RUM](/help/edge/assets/rum-forms-dashboard.png)

### Différentes mesures clés du tableau de bord RUM pour les formulaires {#different-metrics-rum-dashboard-forms}

Vous pouvez évaluer les interactions des visiteurs et visiteuses avec les sites gérés par Adobe Experience Manager à l’aide des mesures clés suivantes :

* **Formviews** : il s’agit du nombre total de formulaires générés pour une URL au cours de la période spécifiée.
* **Formsubmission** : il s’agit du nombre total de formulaires envoyés pour une URL au cours de la période spécifiée.
* **Largest Contentful Paint** : indique la vitesse de chargement de l’URL, soit le temps nécessaire pour afficher l’élément de contenu le plus volumineux visible dans la fenêtre d’affichage à partir du moment où l’utilisateur ou l’utilisatrice demande l’URL. Cet élément de contenu volumineux peut être une image, une vidéo ou un élément de texte de niveau bloc important. Les performances de vitesse de chargement des URL sont classées comme suit :
   * **Bon** : si le temps de chargement est de 2,5 secondes ou moins.
   * **OK** : si le temps de chargement est supérieur à 2,5 secondes mais inférieur ou égal à 4 secondes.
   * **Mauvais** : si le temps de chargement dépasse 4 secondes.

* **Décalage cumulé de disposition** : mesure la somme totale de tous les scores individuels de décalage de la disposition pour chaque décalage de disposition inattendu qui survient tout au long de la durée de vie de la page. Cette mesure joue un rôle essentiel pour déterminer les performances d’une page, car lorsqu’un élément de page se décale lorsqu’un utilisateur ou une utilisatrice tente d’interagir avec celui-ci, cela conduit à une mauvaise expérience d’utilisation. Ce score est compris entre zéro et n’importe quel nombre positif : zéro indique qu’il n’y a pas de décalage, tandis qu’un nombre plus élevé signifie qu’il y a davantage de décalages de la disposition sur la page. Les mesures de performances utilisées pour évaluer les scores de décalages de la disposition sont classées comme suit :

   * **Bon** : si le score de décalage de la mise en page est égal ou inférieur à 0,1.
   * **OK** : si le score de décalage de la mise en page est supérieur à 0,1 mais inférieur à 0,25.
   * **Mauvais** : si le score du décalage de la mise en page dépasse 0,25.

* **Interaction to Next Paint (INP)** : évalue la vitesse de réaction d’une page aux interactions des utilisateurs et des utilisatrices, en tenant compte du temps nécessaire à la page pour répondre aux clics, aux appuis et aux saisies du clavier lors de la visite d’un utilisateur ou d’une utilisatrice sur la page. La valeur finale est l’interaction la plus longue observée, sans tenir compte des anomalies. Les mesures de performances pour Interaction to Next Paint sont classées comme suit :
   * **Bon** : si la durée entre les actions de l’utilisateur ou de l’utilisatrice est de 200 millisecondes (ms) ou moins.
   * **OK** : si la durée est supérieure à 200 ms mais inférieure ou égale à 500 ms.
   * **Mauvais** : si la durée dépasse 500 ms.
