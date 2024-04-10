---
title: Surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms
description: La surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms implique le suivi et l’analyse continus des interactions des utilisateurs avec les formulaires.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# Surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms

Adobe Experience Manager utilise Real User Monitoring (RUM) pour comprendre les interactions des visiteurs avec les sites pilotés par Adobe Experience Manager. Cela permet de diagnostiquer les défis de performance et d’évaluer l’efficacité des expériences. Real User Monitoring protège la confidentialité des visiteurs en utilisant les techniques d&#39;échantillonnage, en s&#39;assurant qu&#39;aucune information personnelle n&#39;est collectée par les sites que vous visitez. Il n’est pas autorisé d’ajouter des données personnelles à la collecte de données RUM. La surveillance réelle des utilisateurs dans Adobe Experience Manager est conçue pour préserver la confidentialité des visiteurs et minimiser la collecte de données.

## Avantages de la surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms {#advantages}

AEM utilise la surveillance des utilisateurs en temps réel pour les éléments suivants :

* Pour identifier et résoudre les goulets d’étranglement en matière de performances sur les sites.
* Pour estimer le nombre de pages vues sur les sites clients
* Comprendre l’interaction de Adobe Experience Manager avec les bibliothèques d’analyse, de ciblage ou externes sur la même page, ce qui améliore la compatibilité.

## Conditions préalables

Vous pouvez afficher le tableau de bord de surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms en accédant à l’adresse URL suivante : https://data.aem.live/?ext=forms

![Écran de connexion RUM pour Edge Delivery Services Forms ](/help/edge/assets/rum-login-screen.png)

Pour vous connecter à votre tableau de bord de surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms, saisissez ce qui suit :
* **URL**: l’URL est spécifique au site ou au domaine de l’utilisateur. Les utilisateurs ont la possibilité de filtrer le site ou le domaine pour afficher le tableau de bord en fonction de leurs besoins.
* **Clé de domaine**: l’utilisateur génère manuellement la clé de domaine. Pour obtenir de l&#39;aide ou des renseignements, consultez le [Générer la clé de domaine RUM](https://aemcs-workspace.adobe.com/rum/generate-domain-key) documentation.

### Tableau de bord de surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms

Après avoir saisi l’URL et la clé de domaine dans l’écran de connexion, vous accédez au tableau de bord de surveillance des utilisateurs en temps réel pour Edge Delivery Services Forms.

L’illustration ci-dessous présente le tableau de bord RUM pour Edge Delivery Services Forms :

![Tableau de bord Forms RUM](/help/edge/assets/rum-forms-dashboard.png)

### Différentes mesures clés du tableau de bord RUM pour Forms {#different-metrics-rum-dashboard-forms}

Vous pouvez évaluer les interactions des visiteurs avec les sites pilotés par Adobe Experience Manager à l’aide des mesures clés suivantes :

* **Formviews**: nombre total de formulaires rendus pour une URL au cours de la période spécifiée.
* **Envoi de formulaire**: il s’agit du nombre total de formulaires envoyés pour une URL au cours de la période spécifiée.
* **Largest Contentful Paint**: indique la vitesse de chargement de l’URL et le temps nécessaire pour afficher l’élément de contenu le plus volumineux dans la fenêtre d’affichage à partir du moment où l’utilisateur demande l’URL. Cet élément de contenu le plus volumineux peut être une image, une vidéo ou un élément de texte substantiel au niveau du bloc. Les performances de la vitesse de chargement des URL sont classées comme suit :
   * **Bon**: si le temps de chargement est de 2,5 secondes ou moins.
   * **Ok**: si le temps de chargement est supérieur à 2,5 secondes, mais inférieur ou égal à 4 secondes.
   * **Mauvais**: si le temps de chargement dépasse 4 secondes

* **Décalage de mise en page cumulé**: il mesure la somme totale de tous les scores de changement de disposition individuels pour chaque changement de disposition inattendu qui se produit tout au long de la durée de vie de la page. Il joue un rôle essentiel dans l’identification des performances d’une page, car lorsque les éléments de page changent pendant qu’un utilisateur ou une utilisatrice tente d’interagir avec eux, cela entraîne une expérience utilisateur médiocre. Ce score va de zéro à n’importe quel nombre positif : zéro indique aucun décalage, tandis qu’un nombre plus élevé indique davantage de décalages de mise en page sur la page. Les mesures de performances utilisées pour évaluer les scores de changement de mise en page sont classées comme suit :

   * **Bon**: si le score du décalage de mise en page est inférieur ou égal à 0,1.
   * **Ok**: si le score du décalage de mise en page est supérieur à 0,1 mais inférieur ou égal à 0,25.
   * **Mauvais**: si le score du décalage de mise en page dépasse 0,25.

* **Interaction avec la peinture suivante**: il évalue la vitesse à laquelle une page réagit aux interactions utilisateur, en prenant en compte le temps nécessaire à la page pour répondre aux clics, aux appuis et aux entrées de clavier lors de la visite d’un utilisateur sur la page. La valeur finale est l’interaction la plus longue observée, en ignorant les anomalies éventuelles. Les mesures de performances d’Interaction avec Next Paint sont classées comme suit :
   * **Bon**: si la durée entre les actions de l’utilisateur est inférieure ou égale à 200 millisecondes.
   * **Ok**: si la durée est supérieure à 200 ms, mais inférieure ou égale à 500 ms.
   * **Mauvais**: si la durée dépasse 500 ms.

