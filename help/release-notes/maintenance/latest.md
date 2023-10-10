---
title: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Notes de mise à jour de la maintenance actuelle d’ [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 3fbdb150a9a1c133b4910603682e37f1c5d885d2
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 32%

---

# Notes de mise à jour de la maintenance {#maintenance-release-notes}

La section suivante décrit les notes de mise jour techniques de maintenance actuelle d’Experience Manager as a Cloud Service.

## Version 13804 {#release-13804}

Vous trouverez ci-dessous un résumé des améliorations continues apportées à la version de maintenance 13804, qui a été publiée publiquement le 10 octobre 2023. Cette mise à jour de maintenance est une mise à jour de la version de maintenance 13665 précédente.

2023.10.0 Feature Activation fournira l’ensemble des fonctionnalités de cette version de maintenance. Voir [Feuille de route des versions du Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=fr) pour plus d’informations.

### Améliorations {#enhancements-13804}

* GRANITE-47238 : Maintenance du journal d’audit - Purger les tâches de conversion pour utiliser la configuration du client.
* GRANITE-47123 : Publier (Sling) - Améliorez le temps de démarrage en initialisant le cache du chemin d’accès Vanity de manière asynchrone par défaut.
* GRANITE-46618 : Publier (réplication) - Amélioration de la vitesse de démarrage de la publication par le traitement par lot des messages d’état de réplication.
* GRANITE-47136 : Indexation (Téléchargement) - Amélioration de la vitesse de téléchargement du nouveau téléchargeur d’index parallèle (en désactivant la validation de la somme de contrôle).
* GRANITE-47211 : Publier (infrara) - Amélioration du découplage des déploiements de niveau Publication (en stockant et en récupérant le nom de révision de la banque de segments).
* GRANITE-47267 : Mise à jour vers Apache Felix Http Jetty 4.2.18 (comprend un correctif de bogue pour la gestion des paramètres de requête ([FELIX-6625](https://issues.apache.org/jira/browse/FELIX-6625)) avec des performances améliorées pour les développements locaux et RDE).
* GRANITE-47247 : Mise à jour du résolveur de servlets Sling 2.9.14 avec améliorations des performances de la résolution du servlet.

### Problèmes résolus {#fixed-issues-13804}

* GRANITE-47376 : Auteur (infrara) - Correction des erreurs DiscoveryTopologyUndefined après le redémarrage en continu.
* CQ-4353436 : AEM console web (Sling) - Configurations vides dans ServiceUserMapperImpl Validators (Principal/Utilisateur) interrompt AEM instance ([SLING-11912](https://issues.apache.org/jira/browse/SLING-11912)).
* SKYOPS-63925 : Tâche de transformation - Éviter les échecs TransformJob avec JDK 11 - ZipException : erreurs d’en-tête CEN non valides (avec indicateur JVM disableZip64ExtraFieldValidation ).
* SKYOPS-63361 : Tâche de transformation (journalisation) Amélioration de la journalisation avec Tâches de transformation (sous-produit CUSTOMER_EXTRACT).
* SKYOPS-64103 : outil FACT (journalisation) - Réduire ou tronquer les messages d’erreur et d’avertissement de compilation clientlib.
* SKYOPS-65109 : outil FACT (gestion des erreurs) - Les packages de contenu avec des dépendances non résolues génèrent une erreur correctement signalée.
* SKYOPS-65368 : FACT Tool (Error Handling) - L’outil s’exécute dans un cycle d’inclusion sans fin et finit par expirer sur les incorporations circulaires des bibliothèques clientes.
* SKYOPS-64031 : RDE - ComponentCacheImpl peut devenir incohérent en raison d’un enregistrement ResourceResolverFactory en double ([SLING-12019](https://issues.apache.org/jira/browse/SLING-12019)).
* ASSETS-29105 : RDE - Fournisseur de restriction manquant dans le modèle de fonctionnalité SecurityProviderRegistration requiredServicePids dans RDE .
* GRANITE-44674 : CoralUI - La fonctionnalité de champ obligatoire du sélecteur de date est incorrecte.

### Problèmes connus {#known-issues-13804}

Aucun.

### Technologies intégrées {#embedded-tech-13804}

| Technologie | Version | Lien |
|---|---|---|
| AEM OAK | 1.56-T20230927085643-189caed | [API Oak 1.56.0](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| API SLING AEM | Version 2.27.2 | [API Apache Sling 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Spécification du modèle de langage HTML](https://github.com/adobe/htl-spec) |
| Composants principaux d’AEM | Version 2.23.4 | [Composants principaux de la gestion de contenu web d’AEM](https://github.com/adobe/aem-core-wcm-components) |
