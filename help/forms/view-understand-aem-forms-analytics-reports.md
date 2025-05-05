---
title: Affichage et compréhension des rapports d’analyse Forms adaptatif
description: Adaptive Forms s’intègre de manière transparente à Adobe Analytics pour capturer et suivre les mesures de performances des formulaires et documents que vous avez publiés.
keywords: Affichage et compréhension des rapports d’analyse Forms adaptatif, rapport d’analyse d’Adobe, rapport Forms Analytics
topic-tags: develop
feature: Adaptive Forms
role: Admin, User
level: Intermediate
exl-id: 756dee1f-4685-4783-961d-b172a5bd0692
source-git-commit: 975f767e75a268a1638227ae20a533f82724c80a
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 2%

---

# Affichage et compréhension des rapports d’analyse Forms adaptatif {#viewing-and-understanding-aem-forms-analytics-reports}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Cet article |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/view-understand-aem-forms-analytics-reports.html?lang=fr) |

Dans le paysage en rapide évolution des analyses numériques, il est impératif de rester attentif aux tendances mondiales pour prendre des décisions éclairées et optimiser les expériences numériques. Pour ce faire, Adaptive Forms s’intègre de manière transparente à Adobe Analytics afin de capturer et de suivre les mesures de performances des formulaires et documents que vous avez publiés. L’analyse de ces mesures a pour objectif de prendre des décisions axées sur les données, en utilisant les mesures et analyses pour améliorer la convivialité et l’efficacité des formulaires.

En capturant et en suivant les indicateurs clés de performance, les entreprises peuvent identifier les domaines d’amélioration, optimiser les expériences utilisateur et, en fin de compte, générer de meilleurs résultats pour créer des expériences client exceptionnelles.

## Configuration d’Adobe Analytics vers Forms adaptatif {#setup-adobe-analytics-to-aem-forms}

Pour le rapport AEM Forms Analytics, vous devez d’abord intégrer Adobe Analytics à AEM Forms par le biais de l’automatisation de la configuration des Experience Cloud. L’automatisation de la configuration des Experience Cloud dans Forms adaptatif nécessite une licence Adobe Analytics, une collecte de données (anciennement Adobe Launch) pour gérer les scripts de suivi et une intégration à l’API Experience Platform Launch pour une agrégation et une génération simplifiées de données et d’informations. Visitez la page [Activation d’Adobe Analytics pour un formulaire adaptatif à l’aide de l’automatisation de configuration Experience Cloud](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md) pour obtenir des informations de configuration complètes.

## Afficher le rapport Adobe Analytics d’Forms adaptatif {#view-adobe-analytics-report}

1. Sur votre instance AEM, accédez à **[!UICONTROL Forms]** &quot; **[!UICONTROL Forms and Document]**.
1. Sélectionnez votre formulaire. Vous pouvez constater qu’Adobe Analytics est intégré, comme illustré à gauche, au Forms activé pour Adobe Analytics.

   ![Afficher le rapport](assets/activ-aa.png){width="100%"}

1. Cliquez sur **Adobe Analytics** pour afficher votre rapport et analyser les données de performances.

## Présentation du rapport d’analyse Forms adaptatif {#understanding-aem-forms-analytics-reports}

Adobe Analytics offre un tableau complet de mesures de performances de Forms adaptatif conçues pour fournir des informations précieuses sur l’utilisation des formulaires. Ces mesures sont les suivantes :

### **Comment fonctionne Adaptive Forms ?** {#how-your-adaptive-form-is-performing}

Il contient les mesures Rendus de formulaire, Envois de formulaire, Erreurs de validation et Visiteurs uniques, qui vous permettent d’évaluer l’utilisation et l’efficacité de vos formulaires :

* **Rendus de formulaire** : les rendus de formulaire indiquent le nombre de fois où le formulaire a été rendu ou ouvert.

* **Envois de formulaire** : les envois de formulaire indiquent le nombre de fois où les formulaires adaptatifs sont remplis et envoyés par les utilisateurs.

* **Erreurs de validation** : l’erreur de validation affiche le nombre total d’erreurs liées à la validation qui se sont produites sur les champs des formulaires.

* **Visiteurs uniques** : les visiteurs uniques représentent le nombre de fois où le formulaire est rendu par un visiteur. Pour plus d’informations sur les visiteurs uniques, voir [Visiteurs uniques, Visites et comportement du client](https://experienceleague.adobe.com/docs/analytics/components/metrics/visits.html?lang=fr).

  ![Performances de Forms](assets/forms-performance.png){width="100%"}

### **Visiteurs de vos formulaires** {#visitors-to-your-forms}

Cela vous permet d’obtenir des informations précieuses sur l’activité des visiteurs sur vos formulaires :

* **Visites et envois** : il décrit la fréquence des visites de vos formulaires dans une période et le nombre correspondant d’envois de formulaire, pour plus d’informations sur ce clic [Visites](https://experienceleague.adobe.com/docs/analytics/components/metrics/visits.html?lang=fr).
* **Visiteurs uniques et leurs visites totales** : il fait la distinction entre les nouveaux utilisateurs et les utilisateurs réguliers. Par exemple, un visiteur peut se rendre sur votre site tous les jours pendant un mois, mais il est toujours comptabilisé comme un visiteur unique. Visitez [Visiteurs uniques](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=fr) pour obtenir des informations détaillées.

  ![Visiteurs Forms](assets/forms-visitors.png){width="100%"}

### **Type de périphérique** {#device-type}

Le type d’appareil vous permet d’identifier le type d’appareil utilisé pour accéder à vos formulaires. Il classe le type d’appareil comme Type d’appareil mobile. Par exemple, dans ce cas, il s’agit de Type de périphérique mobile : Autre et Type de périphérique mobile : Téléphone mobile. Les différents types d’appareils mobiles sont les suivants : téléphone mobile, tablette, lecteur multimédia, console de jeux, etc.

![Type de périphérique](assets/device-type.png){width="100%"}

### **Répartition géographique** {#geographical-breakdown}

Il indique l’emplacement d’accès à Forms. Il fournit des informations spécifiques à une région sur les utilisateurs de formulaires. Vous pouvez par exemple constater qu’une région d’informations sur un utilisateur de formulaire est l’Inde, comme illustré dans l’image.

![Répartition géographique](assets/geographical-breakdown.png){width="100%"}

### **Principales sources de trafic et formulaires populaires** {#top-sources-of-traffic-and-popular-forms}

Vous pouvez ainsi identifier la source principale ou le lien à partir duquel vos formulaires sont référencés. Par exemple, dans l’image donnée ci-dessous, vous voyez des instances de recherche pour vos formulaires adaptatifs où 18,9 % sont **Tapé/Marqué**, 70,49 % basés sur **Moteurs de recherche** et 24 % proviennent d’**Autres sites Web**. Vous pouvez définir des éléments de dimension en fonction de vos besoins. Vous pouvez également déterminer les formulaires les plus visités ou les plus populaires.

![Sites référents](assets/referred-sites.png){width="100%"}

### **Activité de l’utilisateur sur les principaux formulaires** {#user-activity-on-top-forms}

Une vue d’ensemble exhaustive de l’engagement des utilisateurs avec les visites de champs, les rendus de formulaire, les erreurs de validation, les formulaires abandonnés et les envois de formulaire fournit des informations sur les formulaires les plus actifs. Dans l’image ci-dessous, vous voyez que le formulaire de demande est le plus actif en fonction des mesures d’événement de formulaire.

![Activité utilisateur](assets/user-activity.png){width="100%"}

### **Chronologie de la durée passée sur les formulaires** {#timeline-for-time-spent-on-forms}

Il s’agit du temps que les utilisateurs passent sur vos formulaires au fil du temps, qui vous aide à identifier les schémas d’engagement.

![Durée de consultation des formulaires](assets/time-spent-on-forms.png){width="100%"}

### **Zones où les visiteurs ont besoin d’aide pour remplir le formulaire** {#areas-requiring-assistance}

Des mesures telles que les vues d’aide, les erreurs de validation et les visites de champ indiquent où les utilisateurs ont besoin d’aide ou comment nous pouvons suivre les erreurs dans les champs. Par exemple, dans l’image ci-dessous, vous voyez que dans un formulaire avec des champs tels que **Full Name**, **Phone Number**, **DoB**. Le champ **Nom complet** comporte 12 visites, sur 12 visites 8 ont une erreur de validation et 1 icône d’aide sur laquelle l’utilisateur a cliqué pour afficher de l’aide sur ce champ. Vous pouvez afficher les données de mesure pour d’autres champs de formulaire.

![Assister les zones](assets/assisting-areas.png){width="100%"}

### **Le dernier champ de formulaire que les visiteurs ont affiché avant d’abandonner le formulaire** {#last-form-field-that-visitors-viewed}

Il permet d’analyser les champs de formulaire dans lesquels les utilisateurs ont passé du temps avant d’abandonner le formulaire. Par exemple, dans l’image ci-dessous, sur 5 formulaires abandonnés, 2 ont été laissés sur le champ **Nom complet**, 2 ont été laissés sur le champ **Numéro de téléphone** et 1 ont été laissés sur le champ **Entrée de texte**.

![Visiteurs de champ](assets/field-visitors.png){width="100%"}

## Voir également {#see-also}

* [Activation d’Adobe Analytics pour un formulaire adaptatif à l’aide de l’automatisation de la configuration Experience Cloud](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md)
* [Ajouter un formulaire adaptatif à une page AEM Sites ou un fragment d’expérience](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Intégration d’AEM Forms à Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md)
