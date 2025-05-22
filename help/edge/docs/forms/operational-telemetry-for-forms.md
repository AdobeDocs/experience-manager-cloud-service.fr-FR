---
title: Télémétrie opérationnelle pour Edge Delivery Services pour AEM Forms as a Cloud Service
description: La télémétrie opérationnelle pour Edge Delivery Services pour AEM Forms as a Cloud Service implique le suivi et l’analyse continus des interactions des utilisateurs avec les formulaires.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
source-git-commit: 8be0a9894bb5b3a138c0ec40a437d6c8e4bc7e25
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 83%

---

# Télémétrie opérationnelle pour Edge Delivery Services pour AEM Forms as a Cloud Service

La télémétrie opérationnelle vous permet d’obtenir des informations réelles sur la manière dont les visiteurs interagissent avec vos sites web Adobe Experience Manager (AEM). Cet outil intégré fournit des données précieuses pour comprendre le comportement des utilisateurs et utilisatrices, diagnostiquer les problèmes de performances et mesurer l’efficacité des expériences sur les sites web. La télémétrie opérationnelle va au-delà des tests synthétiques en capturant les interactions d’utilisation réelle, offrant ainsi une image plus précise des performances de votre site.

Cependant, la télémétrie opérationnelle donne la priorité à la confidentialité des visiteurs. Elle emploie donc des techniques d’échantillonnage pour collecter des données auprès d’un sous-ensemble représentatif de personnes, en s’assurant qu’aucune information d’identification personnelle ne soit jamais recueillie. En outre, la télémétrie opérationnelle est conçue en tenant compte de la minimisation des données, en ne collectant que les mesures essentielles requises pour l’analyse des performances. Cette approche vous permet d’optimiser vos sites AEM tout en préservant la confiance des utilisateurs et utilisatrices.


## Conditions préalables

Vous pouvez afficher le tableau de bord de surveillance des Edge Delivery Services d’AEM Forms as a Cloud Service en accédant à l’URL suivante :

https://data.aem.live/?ext=forms

![Écran de connexion à la télémétrie opérationnelle pour Edge Delivery Services for Forms](/help/edge/assets/rum-login-screen.png)

Pour vous connecter au tableau de bord de surveillance des Edge Delivery Services d’AEM Forms as a Cloud Service, saisissez les informations suivantes :

* **URL** : l’URL est spécifique au site ou au domaine de l’utilisateur ou de l’utilisatrice. Les utilisateurs et utilisatrices ont la possibilité de filtrer le site ou le domaine pour afficher le tableau de bord en fonction de leurs besoins.

* **Clé domaine** : l’utilisateur ou l’utilisatrice génère manuellement la clé de domaine. Pour obtenir les clés de domaine de vos formulaires, contactez votre représentant ou représentante Adobe.

### Tableau de bord de surveillance des Edge Delivery Services d’AEM Forms as a Cloud Service

Après avoir saisi l’URL et les clés de domaine dans l’écran de connexion, vous accédez au tableau de bord de surveillance des Edge Delivery Services d’AEM Forms as a Cloud Service.

L’illustration ci-dessous présente le tableau de bord des Edge Delivery Services pour AEM Forms as a Cloud Service :

![ Tableau de bord Forms de télémétrie opérationnelle ](/help/edge/assets/rum-forms-dashboard.png)

### Différentes mesures clés du tableau de bord pour les formulaires {#different-metrics-operational-telemetry-dashboard-forms}

Ce tableau de bord fournit des informations clés sur la manière dont les visiteurs et visiteuses interagissent avec les formulaires de votre site web Adobe Experience Manager (AEM). En surveillant ces mesures, vous pouvez identifier les zones à améliorer et optimiser vos formulaires pour une meilleure expérience client et des taux de conversion supérieurs :

* **Vues de formulaire** : suivre le nombre total d’affichages des formulaires
* **Envois de formulaire** : suivre le nombre total d’envois terminés

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

## Informations exploitables

L’analyse de ces mesures permet d’identifier des opportunités pour ce qui suit :

* Simplifier les formulaires et réduire le nombre de champs.
* Améliorer la précision des formulaires grâce à des instructions et des libellés clairs.
* Optimiser la disposition des formulaires pour une réactivité sur les appareils mobiles.
* Résoudre les problèmes techniques qui ralentissent le chargement des formulaires.

En vous concentrant sur ces domaines, vous pouvez créer des formulaires plus faciles à utiliser et inciter les visiteurs et visiteuses à les remplir, ce qui augmente les taux de conversion.

## Voir également

{{see-more-forms-eds}}
