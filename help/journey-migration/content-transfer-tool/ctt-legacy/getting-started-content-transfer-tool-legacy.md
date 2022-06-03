---
title: Prise en main de l’outil de transfert de contenu (Legacy)
description: Prise en main de l’outil de transfert de contenu
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 77%

---

# Prise en main de l’outil de transfert de contenu (Hérité) {#getting-started-content-transfer-tool}


## Disponibilité {#availability}

Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du [Gestionnaire de modules](/help/implementing/developing/tools/package-manager.md) sur votre instance source Adobe Experience Manager (AEM). Veillez à télécharger la dernière version. Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

>[!NOTE]
>Téléchargez l’outil de transfert de contenu depuis le portail de [distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Connectivité de l’environnement source {#source-environment-connectivity}

L’instance d’AEM source peut se trouver derrière un pare-feu d’où elle ne peut atteindre que certains hôtes qui ont été ajoutés à une liste autorisée. Pour réussir l’exécution d’une extraction, les points d’entrée suivants doivent être accessibles à partir de l’instance AEM en cours d’exécution :

* L’environnement AEM as a Cloud Service cible : `author-p<program_id>-e<env_id>.adobeaemcloud.com`
* Le service d’enregistrement blob Azure : `*.blob.core.windows.net`
* Le point d’entrée de l’IO de mappage des utilisateurs : `usermanagement.adobe.io`

Pour tester la connectivité à l’environnement AEM as a Cloud Service cible, lancez la commande cURL suivante à partir du shell de l’instance source (remplacez `program_id`, `environment_id` et `migration_token`) :

`curl -i https://author-p<program_id>-e<environment_id>.adobeaemcloud.com/api/migration/migrationSet -H "Authorization: Bearer <migration_token>"`

>[!NOTE]
>Si vous recevez un `HTTP/2 200`, la connexion à AEM as a Cloud Service a réussi.

## Exécution de l’outil de transfert de contenu {#running-tool}

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


Consultez cette section pour effectuer une migration du contenu vers AEM as a Cloud Service (auteur/publication) à l’aide de l’outil de transfert de contenu :

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Migration de contenu**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt01.png)

1. Sélectionnez l’option **Transfert de contenu** dans l’assistant **Migration de contenu**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt02.png)


1. La console ci-dessous s’affiche lorsque vous créez le premier jeu de migration. Cliquez sur **Créer un jeu de migration** pour créer un jeu de migration.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt03.png)

   >[!NOTE]
   >Si vous disposez de jeux de migration, la console affiche la liste de ces jeux avec leur état actuel.


1. Renseignez les champs de l’écran **Créer un jeu de migration** comme décrit ci-dessous.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt04.png)

   1. **Nom** : renseignez le nom du jeu de migration.
      >[!NOTE]
      >Aucun caractère spécial n’est autorisé dans ce nom.

   1. **Configuration de Cloud Service** : renseignez l’URL de destination d’auteur AEM as a Cloud Service.

      >[!NOTE]
      >Vous pouvez créer et gérer un maximum de dix jeux de migration à la fois pendant l’activité de transfert de contenu.
      >En outre, vous devez créer une migration distincte pour chacun des environnements spécifiques : *Stage* (Évaluation), *Development* (Développement) ou *Production*.

   1. **Jeton d’accès** : renseignez le jeton d’accès.

      >[!NOTE]
      >Vous pouvez récupérer le jeton d’accès à l’aide du bouton **Ouvrir le jeton d’accès**. Vous devez vous assurer que vous appartenez au groupe &quot;Administrateurs&quot; dans l’instance de Cloud Service cible.

   1. **Paramètres** : sélectionnez les paramètres suivants pour créer le jeu de migration :

      1. **Inclure les versions** : sélectionnez les options requises. Lorsque différentes versions sont incluses, le chemin d’accès `/var/audit` est automatiquement inclus pour migrer les événements de contrôle.

         ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt05.png)

         >[!NOTE]
         >Si vous envisagez d’inclure différentes versions dans un jeu de migration et effectuez des compléments avec `wipe=false`, vous devez désactiver la purge des versions en raison d’une restriction actuelle de l’outil de transfert de contenu. Si vous préférez conserver la purge de version activée et effectuer des compléments dans un jeu de migration, vous devez effectuer l’ingestion sous la forme `wipe=true`.


      1. **Chemins à inclure** : utilisez le navigateur de chemins pour sélectionner les chemins objets de la migration. Le sélecteur de chemin accepte les entrées effectuées par saisie ou par sélection.

         >[!IMPORTANT]
         >Les chemins suivants sont restreints lors de la création d’un jeu de migration :
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc` (il est possible de sélectionner certains chemins `/etc` dans le CTT)


1. Cliquez sur **Enregistrer** après avoir rempli tous les champs de l’écran **Créer un jeu de migration**.

1. Vous verrez votre jeu de migration dans l’assistant de **Transfert de contenu**, comme illustré dans la figure ci-dessous.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt07.png)

   Tous les jeux de migration existants s’affichent dans l’assistant de **Transfert de contenu** avec leur statut actuel et leurs informations de statut. Certaines des icônes décrites ci-dessous peuvent apparaître.

   * Un *nuage de couleur rouge* indique que vous ne pouvez pas terminer le processus d’extraction.
   * Un *nuage de couleur verte* indique que vous pouvez terminer le processus d’extraction.
   * Une *icône de couleur jaune* indique que vous n’avez pas créé le jeu de migration existant et que celui ainsi indiqué a été créé par un autre utilisateur de la même instance.

1. Sélectionnez un jeu de migration puis cliquez sur **Propriétés** pour voir ou modifier les propriétés du jeu de migration. Lors de la modification des propriétés, il n’est pas possible de changer le **nom du jeu de migration** ou l’**URL du service**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png)

### Détermination de la taille du jeu de migration et de l’espace disque {#migration-set-size}

Après la création d’un jeu de migration, il est vivement recommandé d’exécuter une vérification de taille sur le jeu de migration avant de lancer un processus d’extraction.
En effectuant une vérification de taille sur le jeu de migration, vous pourrez :
* Déterminez s’il y a suffisamment d’espace disque dans la variable `crx-quickstart` pour terminer l’extraction.
* Déterminez si la taille du jeu de migration est conforme aux limites de produit prises en charge et évitez les échecs d’ingestion de contenu.

Pour exécuter une vérification de taille, procédez comme suit :

1. Sélectionnez un jeu de migration et cliquez sur **Vérifier la taille**.

   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image1.png)

1. Cela ouvrira la fenêtre **Vérifier la taille** boîte de dialogue.

   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image2.png)

1. Cliquez sur **Vérifier la taille** pour démarrer le processus. Vous revenez alors à la vue Liste des jeux de migration et un message vous indique que **Vérifier la taille** est en cours d’exécution.

   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image3.png)


1. Une fois **Vérifier la taille** est terminé, l’état devient **FINISHED**. Sélectionnez le même jeu de migration et cliquez sur **Vérifier la taille** pour afficher les résultats.

   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image4.png)

   Voici un exemple : **Vérifier la taille** résultats sans avertissement.

   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image5.png)

1. Si la variable **Vérifier la taille** les résultats indiquent qu&#39;il n&#39;y a pas suffisamment d&#39;espace disque et/ou que le jeu de migration dépasse les limites du produit, **AVERTISSEMENT** s’affiche.

![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)

Voici un exemple : **Vérifier la taille** donne des avertissements.

![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png)


## Prochaines étapes {#whats-next}

Maintenant que vous avez appris à créer un jeu de migration, vous êtes prêt à en apprendre plus sur les processus d’extraction et d’ingestion dans l’outil de transfert de contenu. Avant d’en apprendre plus sur ces processus, vous devez consulter la section [Gestion des référentiels de contenu volumineux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=fr) pour accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu afin de déplacer le contenu vers AEM as a Cloud Service.
