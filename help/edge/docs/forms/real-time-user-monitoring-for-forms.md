---
title: Surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms
description: La surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms implique le suivi et l’analyse continus des interactions utilisateur avec les formulaires.
feature: Edge Delivery Services
exl-id: 184fc7dc-d583-4a63-9e30-80d324ec9d7e
source-git-commit: 2affe155b285986128487043fcc4f2938fc15842
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---


# Surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms

Adobe Experience Manager utilise la surveillance des utilisateurs réels (RUM) pour comprendre les interactions des visiteurs avec des sites pilotés par Adobe Experience Manager. Cela permet de diagnostiquer les défis de performance et d’évaluer l’efficacité des expériences. La surveillance des utilisateurs réels conserve la confidentialité des visiteurs en utilisant les techniques d’échantillonnage, en s’assurant qu’aucune information personnelle n’est collectée par les sites que vous visitez. Il n’est pas autorisé d’ajouter des données personnelles à la collecte de données RUM. La surveillance des utilisateurs réels dans Adobe Experience Manager est conçue pour préserver la confidentialité des visiteurs et minimiser la collecte de données.

## Avantages de la surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms {#advantages}

AEM utilise la surveillance des utilisateurs en temps réel pour les opérations suivantes :

* Pour identifier et corriger les goulets d’étranglement en termes de performances sur les sites.
* Pour estimer le nombre de pages vues sur les sites des clients
* Pour comprendre l’interaction de Adobe Experience Manager avec des bibliothèques d’analyse, de ciblage ou externes sur la même page, améliorant la compatibilité.

## Conditions préalables

Vous pouvez afficher le tableau de bord de surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms en accédant à l’URL suivante : https://data.aem.live/?ext=forms

![Écran de connexion RUM pour Edge Delivery Services Forms ](/help/edge/assets/rum-login-screen.png)

Pour vous connecter à votre tableau de bord de surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms, saisissez ce qui suit :
* **URL**: l’URL est spécifique au site utilisateur ou au domaine. Les utilisateurs ont la possibilité de filtrer le site ou le domaine pour afficher le tableau de bord en fonction de leurs besoins.
* **Clé domaine**: l’utilisateur génère manuellement la clé de domaine. Pour plus d’informations, reportez-vous à la section [Générer la clé de domaine RUM](https://aemcs-workspace.adobe.com/rum/generate-domain-key) la documentation.

### Tableau de bord de surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms

Après avoir saisi l’URL et la clé de domaine dans l’écran de connexion, vous accédez au tableau de bord de surveillance utilisateur en temps réel pour Edge Delivery Services Forms.

L’illustration ci-dessous présente le tableau de bord RUM pour Edge Delivery Services Forms :

![Tableau de bord RUM Forms](/help/edge/assets/rum-forms-dashboard.png)

### Différentes mesures clés du tableau de bord RUM pour Forms {#different-metrics-rum-dashboard-forms}

Vous pouvez évaluer les interactions des visiteurs avec des sites pilotés par Adobe Experience Manager à l’aide des mesures clés suivantes :

* **Formviews**: il s’agit du nombre total de formulaires générés pour une URL au cours de la période spécifiée.
* **Envoi de formulaire**: il s’agit du nombre total de formulaires envoyés pour une URL au cours de la période spécifiée.
* **Peinture contentée la plus grande**: indique la vitesse de chargement de l’URL, indiquant le temps nécessaire pour afficher le plus grand élément de contenu visible dans la fenêtre d’affichage à partir du moment où l’utilisateur demande l’URL. Cet élément de contenu le plus grand peut être une image, une vidéo ou un élément de texte de niveau bloc important. Les performances de la vitesse de chargement des URL sont classées comme suit :
   * **Bon**: si le temps de chargement est de 2,5 secondes ou moins.
   * **Ok**: si le temps de chargement est supérieur à 2,5 secondes mais inférieur ou égal à 4 secondes.
   * **Mauvais**: si le temps de chargement dépasse 4 secondes

* **Décalage cumulé de la mise en page**: mesure la somme totale de tous les scores de changement de mise en page individuels pour chaque changement de mise en page inattendu qui survient tout au long de la durée de vie de la page. Il joue un rôle essentiel dans l’identification des performances d’une page, car lorsqu’un élément de page change alors qu’un utilisateur tente d’interagir avec lui, cela génère une mauvaise expérience utilisateur. Ce score est compris entre zéro et n’importe quel nombre positif : zéro indique qu’il n’y a pas de changement, tandis qu’un nombre plus élevé signifie davantage de changements de mise en page sur la page. Les mesures de performances utilisées pour évaluer les scores de changement de mise en page sont classées comme suit :

   * **Bon**: si le score de changement de mise en page est de 0,1 ou moins.
   * **Ok**: si le score de changement de mise en page est supérieur à 0,1 mais 0,25 ou moins.
   * **Mauvais**: si le score du changement de mise en page dépasse 0,25.

* **Interaction avec la prochaine peinture**: évalue la vitesse de réaction d’une page aux interactions de l’utilisateur, en tenant compte du temps nécessaire à la page pour répondre aux clics, aux clics et aux entrées de clavier lors de la visite de l’utilisateur sur la page. La valeur finale est l’interaction la plus longue observée, sans tenir compte des anomalies. Les mesures de performances d’ Interaction vers la page suivante sont classées comme suit :
   * **Bon**: si la durée entre les actions de l’utilisateur est de 200 millisecondes (ms) ou moins.
   * **Ok**: si la durée est supérieure à 200 ms mais inférieure à 500 ms.
   * **Mauvais**: si la durée dépasse 500 ms.
