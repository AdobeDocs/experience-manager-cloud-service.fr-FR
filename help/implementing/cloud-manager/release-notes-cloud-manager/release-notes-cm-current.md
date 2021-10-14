---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.10.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.10.0
feature: Release Information
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
source-git-commit: 62e9466fdfd6d6ac63dad9a2bc19693f7dc8d098
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.10.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.10.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM 2021.10.0 as a Cloud Service est le 14 octobre 2021.
La prochaine version est prévue pour le 4 novembre 2021.

### Nouveautés {#what-is-new}

* En vue de certaines modifications à venir, les pipelines de déploiement existants seront désormais référencés et étiquetés dans l’interface utilisateur comme étant des pipelines **Pile complète**.

* La carte du pipeline a été actualisée afin d’afficher désormais une seule face intégrée qui affiche les pipelines de production et hors production. L’utilisateur peut sélectionner Exécuter/Pause/Reprendre directement dans le menu d’actions associé à chaque pipeline.

* Un utilisateur disposant du rôle Gestionnaire de déploiement peut désormais supprimer le pipeline de production en libre-service via l’interface utilisateur.

* L’ajout et la modification d’expériences de pipeline ont été actualisés afin d’utiliser désormais des modèles familiers et modernes.

* Les utilisateurs de Cloud Manager peuvent désormais envoyer leurs commentaires directement à partir de l’interface utilisateur via le bouton **Commentaires** en haut à droite de la page d’entrée.

* Les graphiques SLA annuels peuvent désormais être téléchargés à partir de l’interface utilisateur de Cloud Manager.

* Les exécutions de pipeline de qualité de code et hors production utilisent désormais un processus de clonage superficiel plus efficace au cours de l’étape de création, ce qui accélère la création pour les clients disposant de référentiels Git particulièrement volumineux.

* L’assistant Ajouter une Liste autorisée IP informe désormais l’utilisateur si le nombre maximal autorisé de Listes autorisées IP a été atteint.

* La documentation de l’API Cloud Manager comprend désormais un terrain de lecture interactif qui permet aux utilisateurs connectés de tester l’API depuis leur navigateur. Voir [Jeu d’API Cloud Manager](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) pour plus d’informations.

* L’info-bulle de la carte Programme est plus descriptive si une option de sélection sous &quot;Accéder à&quot; est désactivée. Il affiche désormais &quot;Aucun environnement de production n’existe&quot;.

### Correctifs {#bug-fixes}

* Dans de rares cas, lorsqu’un Adobe restaurait l’environnement d’un client, la restauration était considérée comme terminée avant que l’environnement ne soit complètement opérationnel.

* Certaines demandes internes effectuées lors de la création de l’environnement n’ont pas été retraitées.

