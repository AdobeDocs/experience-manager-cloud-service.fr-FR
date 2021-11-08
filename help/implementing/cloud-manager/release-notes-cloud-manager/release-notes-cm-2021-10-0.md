---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.10.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.10.0
feature: Release Information
exl-id: null
source-git-commit: c6c1d3bef85afda0ff86ec073d0ac91ad532c93b
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 20%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.10.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service 2021.10.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM 2021.10.0 as a Cloud Service est le 14 octobre 2021.


### Nouveautés {#what-is-new}

* En vue de certaines modifications à venir, les pipelines de déploiement existants seront désormais référencés et étiquetés dans l’interface utilisateur comme **Pile complète** pipelines.

* La carte du pipeline a été actualisée afin d’afficher désormais une seule face intégrée qui affiche les pipelines de production et hors production. L’utilisateur peut sélectionner Exécuter/Pause/Reprendre directement dans le menu d’actions associé à chaque pipeline.

* Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service via l’interface utilisateur.

* L’ajout et la modification d’expériences de pipeline ont été actualisés afin d’utiliser désormais des modèles familiers et modernes.

* Les utilisateurs de Cloud Manager peuvent désormais envoyer leurs commentaires directement depuis l’interface utilisateur via le **Commentaires** en haut à droite de la landing page.

* Les graphiques SLA annuels peuvent désormais être téléchargés à partir de l’interface utilisateur de Cloud Manager.

* Code quality and non-production pipeline executions will now use a more efficient shallow cloning process during the build step, leading to a faster build time for customers with especially large git repositories.

* L’assistant Ajouter une Liste autorisée IP informe désormais l’utilisateur si le nombre maximal autorisé de Listes autorisées IP a été atteint.

* The Cloud Manager API documentation now includes an interactive playground that allows logged-in users to experiment with the API from their browser. Voir [Playground de l’API Cloud Manager](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) pour plus d’informations.

* L’info-bulle de la carte Programme est plus descriptive si une option de sélection sous &quot;Accéder à&quot; est désactivée. Il affiche désormais &quot;Aucun environnement de production n’existe&quot;.

### Correctifs {#bug-fixes}

* In rare situations, when an Adobe staff would restore a customer&#39;s environment, the restore was considered complete before the environment was fully operational.

* Certaines demandes internes effectuées lors de la création de l’environnement n’ont pas été retraitées.

* If deployment failed error occurs following domain name verification, the error message has been corrected to request the customer to contact their Adobe representative.

