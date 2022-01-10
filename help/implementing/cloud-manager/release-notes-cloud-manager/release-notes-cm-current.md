---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.12.0
description: Il s’agit des notes de mise à jour de Cloud Manager dans AEM version as a Cloud Service 2021.12.0.
feature: Release Information
source-git-commit: 6389dfaf1e4569a0e7bf2c6dbfa30bb003c4db5b
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 40%

---


# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.12.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM 2021.12.0 as a Cloud Service.

>[!NOTE]
>
>Voir [cette page](/help/release-notes/release-notes-cloud/release-notes-current.md) pour les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service.

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM 2021.12.0 as a Cloud Service est le 16 décembre 2021. La prochaine version est prévue pour janvier 2022.

### Nouveautés {#what-is-new}

* Le hachage de validation, déjà visible dans l’interface utilisateur, est désormais également fourni dans l’API.
* La page Activité comprend désormais une fenêtre contextuelle consacrée aux pipelines en cours dʼexécution. Vous pouvez consulter en un coup d’œil un résumé des informations sur le pipeline.
* Ajout de mises à jour pour afficher des informations supplémentaires sur la page Activités.
* L’onglet Apprentissage dans Cloud Manager comprend désormais un accès rapide aux guides des API et aux ressources associées.
* Un utilisateur doté du rôle de Gestionnaire de déploiement peut désormais lancer l’assistant de création de projet/branche pour un référentiel sans branche, à partir du menu Action de la page des référentiels.
* Le Gestionnaire de déploiement, présent dans le workflow d’ajout ou de modification de pipeline, est maintenant informé sur la manière de créer une branche ou un projet si le référentiel sélectionné ne comporte aucune branche.
* Une nouvelle fonctionnalité de libre-service Cloud Manager a été ajoutée pour permettre [ajout de variables et de secrets de forme libre au niveau de l’environnement.](/help/implementing/cloud-manager/environment-variables.md)
* Avec la nouvelle [Module complémentaire de démonstration de référence](/help/journey-sites/demos-add-on/overview.md) (disponible le 17 décembre 2021), les dernières bases de code de démonstration pour les produits AEM peuvent être installées et prêtes à être déployées via la nouvelle [outil de création de site rapide](/help/journey-sites/quick-site/overview.md) dans Sites.
* Les pipelines front-end prennent désormais en charge les variables de pipeline.
* Il est désormais possible d’activer Screens dans la boîte de dialogue Modifier le programme pour tous les environnements de test.
* Les conseils fournis par la carte d’appel à l’action dans la page d’aperçu ont été actualisés afin de refléter précisément son association au pipeline de pile de production.
* Des améliorations ont été apportées à la page Activité pour faire apparaître des détails supplémentaires applicables aux pipelines, notamment le code source, l’ID de validation, etc.
* Une mise à jour mineure a été apportée à l’interface utilisateur lors de la copie d’entrées TXT (&quot;valeur TXT&quot; au lieu de &quot;enregistrement TXT&quot;) pour supprimer toute confusion potentielle.
* [La documentation relative aux erreurs de certificat](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-errors) a été mis à jour afin de fournir des exemples supplémentaires ainsi que des étapes de dépannage.
* Une option est désormais disponible dans l’exécution du pipeline front-end pour rejeter ou approuver avant le déploiement en production.
* L’archétype de projet AEM utilisé par Cloud Manager a été mis à jour à la version 32.


### Correctifs {#bug-fixes}

* Les artefacts de test fonctionnels et d’interface utilisateur n’étaient pas inclus dans le journal de l’étape de création.
* Les journaux des étapes de test du produit, fonctionnel et de l’interface utilisateur n’étaient pas accessibles via l’API publique.
* Dans de rares cas, le lien de la page des détails de l’environnement vers le service de publication ou de prévisualisation n’est pas fonctionnel.
* Le nom des pipelines de production de pile complète reste « Pipeline de production », même si l’utilisateur saisit un nom différent dans le champ du nom.
