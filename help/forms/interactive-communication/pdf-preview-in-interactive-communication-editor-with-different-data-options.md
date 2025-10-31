---
title: Aperçu PDF dans l’éditeur de communication interactive avec différentes options de données
description: Aperçu PDF dans l’éditeur de communication interactive avec différentes options de données pour prévisualiser les communications interactives de trois manières différentes.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 371838c77beafa8c67259a865b25325632bea0b0
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 13%

---


# Aperçu de PDF dans l’éditeur de communication interactive

>[!NOTE]
>
> La fonctionnalité de communication interactive est disponible dans le cadre du programme destiné aux utilisateurs et utilisatrices précoces. Envoyez un e-mail à `aem-forms-ea@adobe.com` à partir de votre adresse professionnelle pour demander l’accès.

>[!IMPORTANT]
>
> **Documentation sujette à modification** : cette bibliothèque de prompts est en cours de test produit. Elle est sujette à des mises à jour et des révisions. Les prompts, les exemples et les bonnes pratiques peuvent changer à mesure que Forms Experience Builder continue d’évoluer dans le cadre du programme des utilisateurs et utilisatrices initiaux.

La fonction d’aperçu PDF permet aux utilisateurs de prévisualiser les communications interactives de trois manières différentes : sans données, avec des données locales basées sur JSON ou avec des exemples de données provenant du modèle de données configuré.

## Principaux avantages

- Prévisualisez les communications interactives avec des exemples de données pour visualiser l’aspect des données actives lorsqu’elles sont fusionnées avec la communication.

- Chargez les fichiers de données JSON locaux pour générer des aperçus pilotés par les données sans configuration du serveur principal.

- Utilisez les modèles de données de formulaire (FDM) connectés pour simuler l’intégration de données en temps réel avec des exemples de données lors de la conception.

- Basculez facilement entre les options de données (aucune donnée, données locales, FDM) pour valider la disposition, la structure et la personnalisation.

## Aperçu PDF dans l’éditeur de communication interactive avec différentes options de données

Prévisualisez les communications interactives en n’utilisant aucune donnée, donnée locale ou exemple de données à partir du modèle de données configuré pour des tests et une validation flexibles.

+++&#x200B;1. Aperçu sans données.

1.1. Ouvrez votre communication interactive dans l’éditeur IC.

1.2. Utilisez l’option Aperçu PDF et sélectionnez l’option **Aucune donnée** pour afficher une communication sans données.

![Rechercher un document IC](/help/forms/interactive-communication/assets/nodata.png)

+++

+++&#x200B;2. Aperçu avec des données JSON locales

2.1. Préparez un fichier JSON structuré. À titre de référence, vous pouvez copier les données d’exemple du [&#x200B; de schéma JSON (FDM)](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/work-with-form-data-model) utilisé pour la communication.

2.2. Dans l’éditeur IC, accédez à **Aperçu PDF** > Utilisation des données locales.

2.3. Sélectionnez et chargez votre fichier JSON pour effectuer le rendu d’un aperçu PDF avec les données fournies.

![Rechercher un document IC](/help/forms/interactive-communication/assets/localdata.png)

+++

+++&#x200B;3. Aperçu avec le modèle de données 

3.1. Sélectionnez **Utilisation d’un modèle de données** pour utiliser des exemples de données provenant d’un modèle de données de formulaire (FDM) du CI déjà configuré.

3.2. L’aperçu renseigne automatiquement les données des champs de modèle. Assurez-vous que les données d’exemple sont enregistrées dans FDM lors de la première utilisation ou que l’aperçu peut s’afficher comme n’ayant aucune donnée.

![Rechercher un document IC](/help/forms/interactive-communication/assets/datamodel.png)

+++

