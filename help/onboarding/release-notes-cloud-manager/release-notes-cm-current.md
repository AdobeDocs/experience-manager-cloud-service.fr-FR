---
title: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.7.0
description: Notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.7.0
feature: Informations sur la version
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
source-git-commit: 673ac234f0e9bfc0f5e6878abf5d01d38cbe918f
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 24%

---

# Notes de mise à jour de Cloud Manager dans Adobe Experience Manager as a Cloud Service version 2021.6.0 {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager dans AEM as a Cloud Service version 2021.7.0.

>[!NOTE]
>Pour afficher les notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service, cliquez [ici](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

## Date de publication {#release-date}

La date de publication de Cloud Manager dans AEM as a Cloud Service 2021.7.0 est le 15 juillet 2021.
La prochaine version est prévue pour le 12 août 2021.

### Nouveautés {#what-is-new}

* Les clients peuvent désormais utiliser les JDK Azul 8 et 11 pour leurs processus de génération Cloud Manager et peuvent choisir d’utiliser l’un de ces JDK pour les modules externes Maven compatibles avec les chaînes d’outils *ou* l’exécution complète du processus Maven.

* L’adresse IP sortante sortante sera désormais consignée dans le fichier journal de l’étape de création.

* Les environnements d’évaluation et de production exécutant d’anciennes versions d’AEM signalent désormais l’état &quot;Mise à jour disponible&quot;.

* Le nombre maximal de certificats SSL pris en charge est passé à 20 par programme.

* Augmentation Le nombre maximal de domaines pouvant être configurés est passé à 500 par environnement.

* Les boutons Gérer Git ont été renommés Accéder aux informations Git et la boîte de dialogue a été actualisée visuellement.

### Correctifs {#bug-fixes}

* Dans certains cas, l’aperçu n’était pas une option disponible lors de la liaison d’une Liste autorisée IP à un environnement.

* La navigation manuelle vers la page des détails de l’exécution pour une exécution non existante n’affichait pas d’erreur, juste un écran de chargement sans fin.

* Le message d’erreur affiché lorsque le nombre maximal de certificats SSL a été atteint n’était pas utile.

* Dans certains cas, il peut y avoir une incohérence dans la version affichée dans la carte du pipeline sur la page d’aperçu.

* L’assistant d’ajout de programme indiquait de manière incorrecte que le nom ne peut pas être modifié après la création.

* Dans certains cas, l’aperçu n’était pas une option disponible lors de la liaison d’une Liste autorisée IP à un environnement.

### Problèmes connus {#known-issues}

Les clients qui passent à l’utilisation des JDK Azul doivent savoir que toutes les applications existantes ne seront pas compilées sans erreur sur le JDK Azul. Il est vivement recommandé de tester localement avant de basculer.

