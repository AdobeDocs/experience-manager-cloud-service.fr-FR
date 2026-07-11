---
title: Rapport d’activation d’AEM Assets (Beta)
description: Définitions des mesures du rapport d’activation d’AEM Assets (Beta), couvrant les activations (téléchargements, partages) et les distributions (Dynamic Media, Sites). »
role: Admin
hide: true
badgeSaas: label="AEM Assets" type="Positive" tooltip="S’applique à AEM Assets)."
source-git-commit: 0b5e61f75a97bd31da034ebf282779a634217366
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---


# Rapport d’activation AEM Assets (Beta) : définitions des mesures

## Compréhension des mesures de performances des ressources

Chaque ressource de votre système AEM Assets raconte une histoire : du chargement et de l’approbation jusqu’au moment où elle atteint un acheteur sous la forme d’une image de produit, d’un lien partagé ou d’une bannière principale. Ce parcours génère des milliards d’impressions de marque. Il est donc essentiel de comprendre qu’il est essentiel pour libérer la valeur de votre investissement en actifs.

Cet article répartit les mesures sous-jacentes à ce parcours et regroupe la manière dont vos équipes travaillent réellement avec les ressources :

- **Activations (initiées par l’employé et le partenaire)** : téléchargements, partages et activations dans votre AEM Assets (vue Assets et Content Hub).
- **Distributions (externes aux utilisateurs finaux)** : diffusion vers le monde entier via des canaux tels que Dynamic Media et AEM Sites.

Ensemble, ces mesures relient l’activité des ressources internes à la portée et à l’engagement externes, ce qui vous permet de voir comment vos opérations de contenu se traduisent par des résultats commerciaux réels.

Ce n’est que le début de votre parcours avec AEM Assets, et ces mesures continueront à évoluer à ses côtés. Nous serions ravis de connaître vos commentaires au fur et à mesure que vous les utiliserez, afin que nous puissions continuer à rendre ces rapports plus utiles.

**Remarque** : si vous souhaitez les consulter avec le service Produit/Ingénierie d’Adobe ou obtenir des commentaires, envoyez un e-mail à `GRP-AEM-DAM-METRICS-BETA@ADOBE.COM`.

| | Mesure | Définition |
|---|---|---|
| **Activations** | **Téléchargements (vue Assets)** | Le nombre de fois où les ressources sont téléchargées directement à partir de l’environnement AEM Assets principal, par exemple, par des utilisateurs internes qui parcourent et téléchargent des fichiers via l’interface d’affichage d’Assets. |
| | **Partages (vue Assets)** | Le nombre de partages (via des liens partageables générés) depuis la vue AEM Assets afin de donner aux utilisateurs et utilisatrices externes ou non authentifiés un accès direct à des ressources, dossiers ou collections spécifiques sans avoir à se connecter. |
| | **Téléchargements (Content Hub)** | Le nombre de fois où les ressources sont téléchargées par les utilisateurs via Content Hub, l’interface utilisateur en libre-service qui permet aux équipes élargies de parcourir et de télécharger des ressources approuvées et prêtes pour la marque. |
| | **Partages (Content Hub)** | Le nombre de partages (via des liens partageables générés) depuis Content Hub afin de permettre à d’autres utilisateurs et utilisatrices d’accéder directement à des ressources ou collections sélectionnées. |
| | **Activer dans Content Hub** | Action d’approbation/de publication d’une ressource à partir d’AEM Assets afin qu’elle soit disponible pour les utilisateurs finaux dans Content Hub. Seules les ressources approuvées apparaissent dans Content Hub. |
| | **Activer vers Dynamic Media** | Action de publier une ressource à partir d’AEM Assets dans le service Dynamic Media, ce qui permet de la traiter en rendus et de la diffuser en temps réel via le pipeline d’imagerie/vidéo et le réseau CDN de Dynamic Media. |
| **Répartitions** | **Demandes De Diffusion Dynamic Media** | Nombre total de fois où une ressource a été demandée et diffusée sur tous les canaux via Dynamic Media. |
| | Assets unique Dynamic Media diffusée **** | Nombre de ressources distinctes diffusées au moins une fois par le biais de Dynamic Media au cours d’une période donnée, comptabilisées une fois par ressource, quel que soit le nombre de fois où elles ont été demandées ou le nombre de rendus différents qui ont été diffusés. |
| | **Transformations uniques Dynamic Media** | Nombre de variations distinctes de vos ressources diffusées via Dynamic Media au cours d’une période donnée. Cela indique comment votre contenu s’adapte sur les différents appareils, tailles d’écran et cas d’utilisation. |
| | **Publier sur Sites** | Action de publication d’une ressource à partir d’AEM Assets afin qu’elle puisse être utilisée sur des pages AEM Sites actives. |



