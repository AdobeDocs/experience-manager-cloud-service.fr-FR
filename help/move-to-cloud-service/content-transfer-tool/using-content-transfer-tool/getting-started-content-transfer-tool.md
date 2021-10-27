---
title: Prise en main de l’outil de transfert de contenu
description: Prise en main de l’outil de transfert de contenu
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: fc0628c2bfd345a7846d3d4fbd0fe11a459b10a1
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 59%

---

# Prise en main de l’outil de transfert de contenu {#getting-started-content-transfer-tool}

## Connectivité de l’environnement source

L’instance d’AEM source peut se trouver derrière un pare-feu où elle ne peut atteindre que certains hôtes qui ont été ajoutés à une Liste autorisée. Pour réussir l’exécution d’une extraction, les points de terminaison suivants doivent être accessibles à partir de l’instance AEM en cours d’exécution :

* L&#39;environnement as a Cloud Service AEM cible :
   `author-p<program_id>-e<env_id>.adobeaemcloud.com`
* Le service de stockage blob Azure :
   `*.blob.core.windows.net`
* Point d’entrée User Mapping IO :
   `usermanagement.adobe.io`

Pour tester la connectivité à l’environnement as a Cloud Service AEM cible, lancez la commande cURL suivante à partir du shell de l’instance source (remplacez `program_id`, `environment_id`, et `migration_token`) :

```
 curl -i https://author-p<program_id>-e<environment_id>.adobeaemcloud.com/api/migration/migrationSet -H "Authorization: Bearer <migration_token>"
```

>[!NOTE]
>Si `HTTP/2 200` est reçu, une connexion à AEM as a Cloud Service a réussi.

## Disponibilité {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Télécharger"
>abstract="Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM). Veillez à télécharger la dernière version."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html" text="Notes de mise à jour"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Portail de distribution de logiciels"

Il est possible de télécharger l’outil de transfert de contenu dans un fichier zip à partir du portail de distribution de logiciels. Vous pouvez installer le module par le biais du gestionnaire de modules sur votre instance source Adobe Experience Manager (AEM). Veillez à télécharger la dernière version. Pour plus d’informations sur la dernière version, consultez les [Notes de mise à jour](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=fr).

>[!NOTE]
>Téléchargez l’outil de transfert de contenu depuis le portail de [distribution de logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Exécution de l’outil de transfert de contenu {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Exécution de l’outil de transfert de contenu"
>abstract="Découvrez comment utiliser l’outil de transfert de contenu pour effectuer une migration du contenu vers AEM as a Cloud Service (auteur/publication) à l’aide de l’outil de transfert de contenu."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" Voir Démonstration"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=fr#migration" text="Tutoriel – Utilisation de l’outil de transfert de contenu"

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


Consultez cette section pour effectuer une migration du contenu vers AEM as a Cloud Service (auteur/publication) à l’aide de l’outil de transfert de contenu :

1. Sélectionnez Adobe Experience Manager et accédez à Outils -> **Opérations** -> **Migration de contenu**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt01.png)

1. Sélectionnez l’option **Transfert de contenu** dans l’assistant **Migration de contenu**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt02.png)


1. La console ci-dessous s’affiche lorsque vous créez le premier jeu de migration. Cliquez sur **Create Migration Set** (Créer un jeu de migration) pour créer un jeu de migration.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt03.png)

   >[!NOTE]
   >Si vous disposez de jeux de migration, la console affiche la liste de ces jeux avec leur état actuel.


1. Renseignez les champs de l’écran **Créer un jeu de migration** comme décrit ci-dessous.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt04.png)

   1. **Name** : renseignez le nom du jeu de migration.
      >[!NOTE]
      >Aucun caractère spécial n’est autorisé dans ce nom.

   1. **Cloud Service Configuration** : renseignez l’URL de destination d’auteur AEM as a Cloud Service.

      >[!NOTE]
      >Vous pouvez créer et gérer un maximum de dix jeux de migration à la fois pendant l’activité de transfert de contenu.
      >En outre, vous devez créer une migration distincte pour chacun des environnements spécifiques : *Stage* (Évaluation), *Development* (Développement) ou *Production*.

   1. **Access Token** : renseignez le jeton d’accès.

      >[!NOTE]
      >Vous pouvez récupérer le jeton d’accès à l’aide du bouton **Open access token** (Ouvrir le jeton d’accès). Vous devez vous assurer que vous appartenez au groupe d’administrateurs AEM dans l’instance Cloud Service cible.

   1. **Parameters** : sélectionnez les paramètres suivants pour créer le jeu de migration :

      1. **Include version** : sélectionnez les options requises. Lorsque des versions sont incluses, le chemin d’accès `/var/audit` est automatiquement inclus pour migrer les événements de contrôle.

         ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt05.png)

         >[!NOTE]
         >Si vous envisagez d’inclure des versions dans un jeu de migration et effectuez des compléments avec `wipe=false`, vous devez désactiver la purge de version en raison d’une limitation actuelle de l’outil de transfert de contenu. Si vous préférez conserver la purge de version activée et effectuer des compléments dans un jeu de migration, vous devez effectuer l’ingestion sous la forme `wipe=true`.


      1. **Paths to be included** : utilisez le navigateur de chemins pour sélectionner les chemins objets de la migration. Le sélecteur de chemin accepte les entrées effectuées par saisie ou par sélection.

         >[!IMPORTANT]
         >Les chemins suivants sont restreints lors de la création d’un jeu de migration :
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc` (il est possible de sélectionner certains chemins `/etc` dans le CTT)


1. Cliquez sur **Enregistrer** une fois que vous avez renseigné tous les champs de la variable **Créer un jeu de migration** écran de détails.

1. Vous verrez votre jeu de migration dans la **Transfert de contenu** , comme illustré dans la figure ci-dessous.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt07.png)

   Tous les jeux de migration existants s’affichent sur la page **Transfert de contenu** avec leur état actuel et leurs informations d’état. Certaines des icônes décrites ci-dessous peuvent apparaître.

   * Un *nuage de couleur rouge* indique que vous ne pouvez pas terminer le processus d’extraction.
   * Un *nuage de couleur verte* indique que vous pouvez terminer le processus d’extraction.
   * Une *icône de couleur jaune* indique que vous n’avez pas créé le jeu de migration existant et que celui ainsi indiqué a été créé par un autre utilisateur de la même instance.

1. Sélectionnez un jeu de migration et cliquez sur **Propriétés** pour afficher ou modifier les propriétés du jeu de migration. Lors de la modification des propriétés, il n’est pas possible de modifier la variable **Nom du jeu de migration** ou le **URL du service**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ctt06.png)


## Et après ? {#whats-next}

Une fois que vous avez appris à créer un jeu de migration, vous êtes prêt à en savoir plus sur les processus d’extraction et d’ingestion dans l’outil de transfert de contenu. Avant d’apprendre ces processus, vous devez consulter [Gestion des référentiels de contenu volumineux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) pour accélérer considérablement les phases d’extraction et d’ingestion de l’activité de transfert de contenu afin de déplacer le contenu vers AEM as a Cloud Service.
