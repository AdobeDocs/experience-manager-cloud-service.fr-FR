---
title: Restauration du contenu dans AEM sous forme de Cloud Service
description: Découvrez comment restaurer votre contenu AEM as a Cloud Service à partir de la sauvegarde à l’aide de Cloud Manager.
exl-id: 921d0c5d-5c29-4614-ad4b-187b96518d1f
feature: Operations
role: Admin
source-git-commit: e6bd71cc56db766fcbab3a925baabb5901c97ee8
workflow-type: tm+mt
source-wordcount: '1610'
ht-degree: 20%

---


# Restauration du contenu dans AEM sous forme de Cloud Service {#content-restore}

Vous pouvez restaurer votre AEM en tant que contenu Cloud Service à partir d’une sauvegarde à l’aide de Cloud Manager.



Le processus de restauration en libre-service de Cloud Manager copie les données des sauvegardes système d’Adobe et les restaure dans son environnement d’origine. Une restauration est effectuée pour ramener les données perdues, endommagées ou supprimées accidentellement à leur état d’origine.

Le processus de restauration affecte uniquement le contenu, laissant votre code et votre version d’AEM inchangés. Vous pouvez lancer la restauration de différents environnements à tout moment.

Si vous devez restaurer le code source précédemment déployé de manière simple et rapide, sans avoir besoin de démarrer une nouvelle exécution de pipeline, vous pouvez utiliser [Restaurer le Code](/help/operations/restore-previous-code-deployed.md) déployé précédemment.

Cloud Manager fournit deux types de sauvegardes à partir desquelles vous pouvez restaurer du contenu.

* **Point dans le temps (PIT) :** cette option restaure les sauvegardes continues capturées au cours des dernières 24 heures.
* **Semaine dernière :** ce type effectue une restauration à partir des sauvegardes système au cours des sept derniers jours, à l’exception des 24 heures précédentes.

Dans les deux cas, la version de votre code personnalisé et la version AEM restent inchangées.

>[!TIP]
>
>Il est également possible de restaurer des sauvegardes à l’aide de [l’API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/) publique.

>[!WARNING]
>
>* Cette fonctionnalité ne doit être utilisée que lorsqu’il existe des problèmes sérieux avec le code ou le contenu.
>* La restauration d’une sauvegarde supprime toutes les données ajoutées par la suite. L’évaluation revient également à sa version antérieure.
>* Avant de lancer une restauration de contenu, envisagez d’autres options de restauration sélective de contenu.

## Options de restauration sélective du contenu {#selective-options}

Avant de restaurer une restauration complète du contenu, envisagez ces options pour restaurer votre contenu plus facilement.

* Si un package pour le chemin supprimé est disponible, réinstallez-le à l’aide du Gestionnaire de [&#128279;](/help/implementing/developing/tools/package-manager.md)packages.
* Si le chemin supprimé était une page dans Sites, utilisez la fonction[&#x200B; Restaurer l’arborescence](/help/sites-cloud/authoring/sites-console/page-versions.md).
* Si le chemin supprimé était un dossier de ressources et que les fichiers d’origine sont disponibles, rechargez-les via [la console](/help/assets/add-assets.md) Assets.
* Si le contenu supprimé était une ressource, envisagez [de restaurer les versions précédentes des ressources](/help/assets/manage-digital-assets.md).

Si aucune des options ci-dessus ne fonctionne et que le contenu du chemin supprimé est significatif, effectuez une restauration de contenu comme détaillé dans les sections suivantes.

## Créer un rôle utilisateur {#user-role}

Par défaut, aucun utilisateur n’est autorisé à exécuter des restaurations de contenu dans des environnements de développement, de production ou de préparation. Pour déléguer cette autorisation à des utilisateurs ou des groupes spécifiques, procédez comme suit :

1. Créez un profil de produit avec un nom explicite qui fait référence à la restauration de contenu.
1. Fournissez l’autorisation d’accès **au** programme sur le programme requis.
1. Fournir l’autorisation de restauration d’environnement **Créer** sur l’environnement requis ou tous les environnements du programme, selon votre cas d’utilisation.
1. Affectez des utilisateurs à ce profil.

Pour plus d’informations sur la gestion des autorisations, voir [Autorisations personnalisées](/help/implementing/cloud-manager/custom-permissions.md).

## Restauration du contenu d’un environnement {#restoring-content}

>[!NOTE]
>
>Un utilisateur doit disposer [des autorisations](#user-role) appropriées pour lancer une opération de restauration.

**Pour restaurer le contenu d’un environnement :**

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez l’organisation appropriée.

1. Cliquez sur le programme pour lequel vous souhaitez lancer une restauration.

1. Répertoriez tous les environnements pour le programme en effectuant l’une des opérations suivantes :

   * Dans le menu de gauche, sous **Services**, cliquez sur ![l’icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Données Environnements**.

     ![Onglet Environnements](assets/environments-1.png)

   * Dans le menu de gauche, sous Programme **, cliquez** sur **Vue d’ensemble**, puis dans la carte Environnements **, cliquez sur** l’icône![&#x200B; &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg)**Flux de travail Afficher tout**.

     ![Option Tout afficher](assets/environments-2.png)

     >[!NOTE]
     >
     >La **carte Environnements** répertorie uniquement trois environnements. Cliquez sur **Afficher tout** dans la carte pour afficher *tous les* environnements du programme.

1. Dans le tableau Environnements, à droite d’un environnement dont vous souhaitez restaurer le contenu, cliquez sur Icône Plus ou sur ![l’icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) du menu représentant des points de suspension, puis sur **Restaurer le contenu**.

   ![Option de restauration du contenu à partir du menu représentant des points de suspension](/help/operations/assets/environments-ellipsis-menu.png)

1. Sous l’onglet Restaurer le **contenu** de la page de l’environnement, dans la **liste déroulante Durée de la restauration** , sélectionnez la période de restauration.

   ![Onglet Restauration du contenu d’un environnement](/help/operations/assets/environments-content-restore-tab.png)

   * Si vous avez choisi **Dernières 24 heures**, dans le champ Heure **adjacent**, spécifiez l’heure exacte au cours des dernières 24 heures pour la restauration.
   * Si vous avez choisi **Semaine dernière**, dans le champ Jour **adjacent**, sélectionnez une date comprise dans les sept derniers jours, à l’exclusion des 24 heures précédentes.

1. Une fois que vous avez sélectionné une date ou défini une heure, la section **Sauvegardes disponibles** ci-dessous présente une liste des sauvegardes disponibles qui peuvent être restaurées.

1. Cliquez sur ![l’icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Info_18_N.svg) Informations en regard d’une sauvegarde pour afficher sa version de code et AEM version, puis pesez l’impact de la restauration avant de sélectionner une sauvegarde (voir [Choisir la sauvegarde appropriée](#choosing-backup)).

   ![Informations de sauvegarde](assets/backup-info.png)

   L’horodatage affiché pour les options de restauration est basé sur le fuseau horaire de l’ordinateur de l’utilisateur.

1. À l’extrémité droite de la ligne représentant la sauvegarde à restaurer, cliquez sur Faire pivoter CCW en gras ou sur ![Restaurer](https://spectrum.adobe.com/static/icons/workflow_18/Smock_RotateCCWBold_18_N.svg) pour démarrer le processus de restauration.

1. Passez en revue les détails de la boîte de dialogue Restaurer le **contenu** , puis cliquez sur **Restaurer**.

   ![Confirmer la restauration](assets/backup-restore.png)

Le processus de sauvegarde est lancé. Vous pouvez afficher son état dans la liste Restaurer l’activité&#x200B;**[&#128279;](#restore-activity)**. Le temps nécessaire à l’achèvement d’une opération de restauration dépend de la taille et du profil du contenu restauré.

Une fois la restauration terminée, l’environnement procède comme suit :

* Exécute le même code et la même version AEM qu’au moment du lancement de l’opération de restauration.
* Il a le même contenu qui était disponible à l’horodatage de l’instantané choisi, avec les index reconstruits pour correspondre au code actuel.

## Choisissez la bonne sauvegarde {#choosing-backup}

Le processus de restauration en libre-service de Cloud Manager restaure uniquement le contenu dans AEM. Pour cette raison, vous devez examiner attentivement les modifications de code qui ont été apportées entre le point de restauration souhaité et l’heure actuelle. Examinez l’historique de validation entre l’ID d’enregistrement actuel et celui sur lequel la restauration est effectuée.

Il existe plusieurs scénarios.

* Le code personnalisé de l’environnement et la restauration se trouvent sur le même référentiel et la même branche.
* Le code personnalisé de l’environnement et la restauration partagent un référentiel, utilisent une branche distincte et proviennent d’une validation commune.
* Le code personnalisé de l’environnement et la restauration se trouvent dans des référentiels différents.
   * Dans ce cas, aucun ID de validation ne s’affiche.
   * Adobe vous recommande vivement de cloner les deux référentiels et d’utiliser un outil de comparaison pour comparer les branches.

Gardez également à l’esprit qu’une restauration peut entraîner la désynchronisation de vos environnements de production et de préparation. Vous êtes responsable des conséquences de la restauration du contenu.

## Restauration de l’activité {#restore-activity}

La **liste Activité** de restauration affiche l’état des dix demandes de restauration les plus récentes, y compris les opérations de restauration actives.

![Restaurer l’activité](assets/backup-activity.png)

En cliquant sur ![l’icône](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Info_18_N.svg) Informations pour une sauvegarde, vous pouvez télécharger des journaux pour cette sauvegarde et inspecter les détails du code, y compris les différences entre le snapshot et les données au moment où la restauration a été lancée.

## Sauvegarde hors site {#offsite-backup}

Des sauvegardes régulières protègent contre les risques de suppression accidentelle ou de défaillances techniques dans AEM Cloud Services, mais d’autres risques peuvent survenir en cas d’échec d’une région. Outre la disponibilité, le risque le plus important dans ce type de panne est principalement la perte de données.

AEM en tant que Cloud Service atténue ce risque pour tous les environnements de production AEM. C’est-à-dire qu’il copie en permanence tout AEM contenu dans une région distante. Ce processus rend le contenu disponible pour la récupération pendant trois mois. Cette fonctionnalité est appelée sauvegarde hors site.

AEM Service Reliability Engineering restaure les environnements de test et de production AEM Cloud Service à partir de sauvegardes hors site pendant les pannes de la région de données.

## Principes de mappage des régions de données {#data-region-mapping-principles}

Adobe suit un ensemble de directives internes pour déterminer les mappages de régions de données pour **AEM en tant que Cloud Service**. Ces directives sont conçues pour soutenir l’efficacité opérationnelle, assurer la conformité aux exigences réglementaires régionales et fournir une expérience client cohérente sur les marchés mondiaux.

### Transparence du mappage de régions {#region-mapping-transparency}

Adobe ne divulgue pas publiquement des informations cartographiques détaillées d’une région à l’autre.\
Si les clients ont des questions spécifiques ou justifiées concernant le déploiement régional, la résidence des données ou les implications en matière de conformité, il est recommandé de Adobe contacter directement via les canaux de support ou de compte officiels.

### Principes fondamentaux du mappage de régions de données {#core-principles}

Lors de la détermination d’un mappage de région de données approprié, Adobe applique plusieurs critères prioritaires :

1. **Ne quittez pas la région globale**\
   Les déploiements restent dans l’une des principales régions du monde : **APAC,**&#x200B;**EMEA** et **Amériques**.

2. **Ne quittez pas le continent**\
   Dans la mesure du possible, la réplication et le basculement des données restent sur le même continent.

3. **Ne quittez pas le pays**\
   Si cela est techniquement possible, les données restent à l’intérieur des mêmes frontières nationales.

### Gestion des exceptions {#handling-exceptions}

Lorsque les critères ci-dessus ne peuvent être remplis en raison de limitations techniques ou d’infrastructure, Adobe applique des considérations supplémentaires :

* **Ligne directrice spécifique à l’Europe**\
  Les régions de sauvegarde ou secondaires ne doivent pas être situées dans des pays non membres de l’UE.\
  (L’inverse – l’utilisation d’un pays de l’UE comme sauvegarde pour une primaire non européenne – peut être acceptable s’il n’existe pas de meilleure option pour le même pays.)

* **Évitez certaines régions**\
  Les régions présentant des politiques de données restrictives ou un risque réglementaire accru doivent être évitées en tant qu’emplacements de sauvegarde ou de basculement.

Si les clients ont besoin d’éclaircissements ou ont des besoins axés sur la conformité, Adobe recommande de contacter l’équipe de compte Adobe ou l’organisation de support pour obtenir des conseils adaptés à leur scénario spécifique.

## Limites {#limitations}

L’utilisation du mécanisme de restauration en libre-service est soumise aux restrictions suivantes.

* Les opérations de restauration sont limitées à sept jours, ce qui signifie qu’il n’est pas possible de restaurer un instantané antérieur à sept jours.
* Au maximum dix restaurations réussies sont autorisées dans tous les environnements au cours d’un programme par mois calendaire.
* Après la création de l’environnement, il faut six heures pour que le premier instantané de sauvegarde soit créé. Tant que cet instantané n’a pas été créé, aucune restauration ne peut être effectuée sur l’environnement.
* Une opération de restauration n’est pas lancée s’il existe un pipeline de configuration de couche Web ou de pile complète en cours d’exécution pour l’environnement.
* Une restauration ne peut pas être lancée si une autre restauration est déjà en cours d’exécution sur le même environnement.
* Dans de rares cas, en raison de la limite de 24 heures/7 jours des sauvegardes, la sauvegarde sélectionnée peut ne plus être disponible en raison d’un délai entre le moment où elle a été sélectionnée et le moment où la restauration est lancée.
* Les données des environnements supprimés sont définitivement perdues et ne peuvent pas être récupérées.
