---
title: Notes de mise à jour de Cloud Manager 2024.10.0 dans Adobe Experience Manager as a Cloud Service
description: Consultez les notes de mise à jour de Cloud Manager 2024.10.0 dans AEM as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: ht
source-wordcount: '569'
ht-degree: 100%

---

# Notes de mise à jour de Cloud Manager 2024.10.0 dans Adobe Experience Manager as a Cloud Service {#release-notes}

Cette page présente les notes de mise à jour de Cloud Manager version 2024.10.0 dans AEM as a Cloud Service.

>[!NOTE]
>
>Consultez les [notes de mise à jour actuelles d’Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Date de publication {#release-date}

La date de publication de la version 2024.10.0 de Cloud Manager dans AEM as a Cloud Service est le 3 octobre 2024.

La prochaine version est prévue pour le 14 novembre 2024.

## Nouveautés {#what-is-new}

* <!-- BOTH CS & AMS --> La version d’archétype AEM utilisée dans Cloud Manager est désormais mise à jour vers la version 26. Voir [https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases)

<!-- (CMGR-59817) -->

* <!-- CS ONLY --> La méthode de vérification précédente, utilisée pour ajouter un domaine personnalisé, passait par un long processus de validation DNS. Adobe a simplifié ce processus pour sa clientèle. Désormais, il vous suffit de fournir un certificat SSL valide (EV ou OV), qui fait office de preuve de propriété. La mise à jour des enregistrements TXT dans le DNS n’est plus nécessaire.

  >[!NOTE]
  >
  >Seuls les certificats EV et OV gérés par la cliente ou le client sont concernés par cette fonctionnalité. Un enregistrement CNAME reste obligatoire pour les certificats DV gérés par Adobe.

  Consultez [Ajouter un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).

  ![Vérification du domaine pour un certificat EV/OV géré par un client ou une cliente](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png)

* <!-- CS ONLY --> Lorsque vous ajoutez ou modifiez une infrastructure réseau, les valeurs des champs Adresse IP et Masque réseau sont validées selon les règles suivantes :

   * L’espace d’adresses ne doit pas chevaucher les adresses définies dans l’espace d’adresses des connexions.
   * Les adresses DNS doivent appartenir au masque de réseau défini dans l’espace d’adresses des connexions ou être publiques.

  ![Boîte de dialogue Ajouter une infrastructure réseau](/help/implementing/cloud-manager/release-notes/assets/network-infrastructure-add.png)

* <!-- CS ONLY --> Des modifications sont apportées au format des journaux de déploiement de l’environnement pour l’indexation, l’installation de contenu modifiable et la transformation de tâches.

  >[!NOTE]
  >
  >Ce changement devrait être échelonné et achevé en décembre 2024.

  ![Carte Déploiement en production](/help/implementing/cloud-manager/release-notes/assets/deploy-to-production-card.png)

  Le format du journal va passer d’une entrée simple affichée comme suit :

  ![Fichier journal présentant des entrées simples](/help/implementing/cloud-manager/release-notes/assets/log-file-simple-entry.png)

  À une entrée JSON affichée comme suit :

  ![Fichier journal présentant des entrées json](/help/implementing/cloud-manager/release-notes/assets/log-file-json-entry.png)


## Programme d’adoption précoce {#early-adoption}

Prenez part à notre programme d’adoption précoce de Cloud Manager afin de pouvoir tester certaines fonctionnalités à venir.

### Apportez votre propre Git - avec prise en charge de GitLab et Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La fonctionnalité **Apportez votre propre Git** a été étendue pour inclure la prise en charge de référentiels externes tels que GitLab et Bitbucket. Cette nouvelle prise en charge s’ajoute à la prise en charge existante des référentiels GitHub privés et d’entreprise. Lorsque vous ajoutez ces nouveaux référentiels, vous pouvez également les lier directement à vos pipelines. Vous pouvez héberger ces référentiels sur des plateformes cloud publiques ou dans votre infrastructure ou cloud privés. Cette intégration élimine également la nécessité d’une synchronisation constante du code avec le référentiel d’Adobe et permet de valider les requêtes d’extraction avant de les fusionner dans une branche principale.

Voir [Ajouter des référentiels externes dans Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Boîte de dialogue Ajouter un référentiel](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Actuellement, les contrôles de qualité du code des requêtes d’extraction prêts à l’emploi sont exclusifs aux référentiels hébergés par GitHub, mais une mise à jour permettant d’étendre cette fonctionnalité à d’autres fournisseurs Git est en cours.

Si vous souhaitez tester cette nouvelle fonctionnalité et faire part de vos commentaires, envoyez un e-mail à [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) à partir de l’adresse e-mail associée à votre Adobe ID. Veillez à inclure la plateforme Git à utiliser et indiquez si vous utilisez une structure de référentiel privée/publique ou d’entreprise.


<!-- ## Bug fixes




## Known issues {#known-issues} -->
