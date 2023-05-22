---
title: Bonnes pratiques et instructions pour l’utilisation de l’outil de transfert de contenu  (hérité)
description: Bonnes pratiques et instructions pour l’utilisation de l’outil de transfert de contenu
hide: true
hidefromtoc: true
exl-id: 03449606-0fb4-4a9f-9abb-6b17c27a6046
source-git-commit: eadcf71aa96298383b05e61251dfeb5f345df6b9
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 100%

---

# Bonnes pratiques et instructions pour l’utilisation de l’outil de transfert de contenu  (hérité) {#guidelines}

## Conseils et bonnes pratiques {#best-practices}

Consultez la section ci-dessous pour accéder aux conseils et connaître les bonnes pratiques relatives à l’utilisation de l’outil de transfert de contenu :

* Procédez à un [nettoyage de révision](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=fr) et à des [contrôles de cohérence de l’entrepôt de données](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16550.html?lang=fr) sur le référentiel **source** pour identifier les problèmes potentiels et réduire la taille du référentiel.

* Si la configuration du réseau de diffusion de contenu (CDN) de l’instance de création AEM Cloud est définie pour avoir une liste autorisée d’adresses IP, assurez-vous que les adresses IP de l’environnement source sont également ajoutées à la liste autorisée. Cela permet de s’assurer que l’environnement source et l’environnement AEM Cloud peuvent communiquer entre eux.

* Procédez à l’ingestion en activant le mode d’*effacement* où le référentiel existant (création ou publication) de l’environnement AEM Cloud Service cible sera supprimé, puis mis à jour à l’aide des données du jeu de migration. Ce mode est beaucoup plus rapide que le mode sans effacement, où le jeu de migration est appliqué par-dessus le contenu existant.

* Une fois l’activité de transfert de contenu terminée, une structure de projet appropriée est nécessaire dans l’environnement Cloud Service pour s’assurer que le contenu s’affiche correctement.

* Avant d’exécuter l’outil de transfert de contenu, vous devez vous assurer que l’espace disque disponible dans le sous-répertoire `crx-quickstart` de l’instance AEM source est suffisant. En effet, l’outil de transfert de contenu crée une copie locale du référentiel, ultérieurement chargée dans le jeu de migration.
La formule générale pour calculer l’espace disque disponible requis est la suivante :
   `data store size + node store size * 1.5`

   * *volume de stockage des données* : l’outil de transfert de contenu utilise 64 Go, même si l’entrepôt de données en question est plus volumineux.
   * *volume de stockage des nœuds* : taille du répertoire de stockage des segments ou taille de la base de données MongoDB.
Ainsi, pour un volume de stockage de segments de 20 Go, l’espace disque disponible requis est de 94 Go.

* Un jeu de migration doit être conservé tout au long de l’activité de transfert de contenu pour prendre en charge les compléments de contenu. Étant donné qu’un maximum de dix jeux de migration peuvent être créés et conservés à la fois pendant l’activité de transfert de contenu, il est recommandé de diviser le référentiel de contenu en conséquence. Cela vous permet de ne pas être à court de jeux de migration.

## Points importants avant d’utiliser l’outil de transfert de contenu {#important-considerations}

Consultez la section ci-dessous afin de comprendre les points importants à prendre en compte pour l’exécution de l’outil de transfert de contenu :

* La configuration minimale requise pour l’outil de transfert de contenu est AEM 6.3+ et Java™ 8. Si vous utilisez une version antérieure d’AEM, vous devez mettre à niveau votre référentiel de contenu sur la version AEM 6.5 pour utiliser l’outil de transfert de contenu.

* Java doit être configuré dans l’environnement AEM, de sorte que la commande `java` puisse être exécutée par l’utilisateur ou l’utilisatrice démarrant AEM.

* Désinstallez les anciennes versions de l’outil de transfert de contenu lors de l’installation de la version 1.3.0, car l’outil a subi un changement d’architecture majeur. Avec la version 1.3.0, vous devez également créer des jeux de migration et réexécuter l’extraction et l’ingestion sur les nouveaux jeux de migration.

* L’outil de transfert de contenu peut être utilisé avec les types de magasin de données suivants : File Data Store, S3 Data Store, Shared S3 Data Store et Azure Blob Store Data Store.

* Si vous utilisez un *environnement sandbox*, assurez-vous que celui-ci est à jour et mis à niveau vers la dernière version. Si vous utilisez un *environnement de production*, il est automatiquement mis à jour.

* Pour utiliser l’outil de transfert de contenu, vous devez être un utilisateur administrateur sur votre instance source et appartenir au groupe d’**administrateurs** AEM local dans l’instance Cloud Service vers laquelle vous transférez du contenu. Les utilisateurs et utilisatrices ne disposant pas des privilèges requis ne peuvent pas récupérer le jeton d’accès pour utiliser l’outil de transfert de contenu.

* Lorsque l’option **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est activée, elle supprime l’intégralité du référentiel existant et crée un référentiel dans lequel ingérer du contenu. Ce workflow réinitialise tous les paramètres dont les autorisations sur l’instance Cloud Service cible. Cela concerne même une utilisatrice ou un utilisateur administrateur ajouté au groupe **d’administration**. L’utilisateur ou utilisatrice doit être rajouté au groupe **d’administration** afin de récupérer le jeton d’accès pour l’outil de transfert de contenu.

* L’outil de transfert de contenu ne prend pas en charge la fusion de contenu provenant de plusieurs sources dans l’instance Cloud Service cible si le contenu provenant des deux sources est déplacé vers les mêmes chemins d’accès sur la cible. Pour déplacer le contenu provenant de plusieurs sources vers une seule instance de Cloud Service cible, vous devez vous assurer qu’il n’y a pas de chevauchement des chemins de contenu des sources.

* Le jeton d’accès peut expirer périodiquement, soit après une période spécifique, soit après la mise à niveau de l’environnement Cloud Service. Si le jeton d’accès a expiré, vous ne pouvez pas vous connecter à l’instance du Cloud Service. Dans ce cas, vous devez récupérer le nouveau jeton d’accès. L’icône du statut associée à un jeu de migration existant devient un nuage rouge et affiche un message si vous passez votre curseur dessus.

* L’outil de transfert de contenu (CTT) n’effectue aucune analyse avant de transférer le contenu de l’instance source vers l’instance cible. Par exemple, le CTT ne fait pas de distinction entre le contenu publié et le contenu dépublié lors de l’ingestion de contenu dans un environnement de publication. Quel que soit le contenu spécifié dans le jeu de migration, il sera ingéré dans l’instance cible choisie. L’utilisateur ou utilisatrice peut ingérer un jeu de migration dans une instance de création ou de publication, ou les deux. Lors du déplacement du contenu vers une instance de production, installez le CTT sur l’instance de création source pour déplacer le contenu vers l’instance de création cible. De même, installez le CTT sur l’instance de publication source pour déplacer le contenu vers l’instance de publication cible. Pour en savoir plus, consultez [Exécution de l’outil de transfert de contenu sur une instance de publication](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr#running-tool).

* Les utilisateurs, utilisatrices et les groupes transférés par l’outil de transfert de contenu sont uniquement ceux requis en fonction du contenu pour respecter les autorisations. Le processus d’*extraction* copie l’intégralité de `/home` dans le jeu de migration et le processus d’*ingestion* copie tous les utilisateurs et groupes référencés dans les listes de contrôle d’accès du contenu migré. Pour mapper automatiquement les utilisateurs et les groupes existants avec leurs ID IMS, reportez-vous à la section [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html?lang=fr).

* Pendant la phase d’extraction, l’outil de transfert de contenu est exécuté sur une instance source AEM active.

* Après avoir terminé la phase d’*extraction* du processus de transfert de contenu et avant de commencer la *phase d’ingestion* pour ingérer du contenu dans votre instance d’*évaluation* ou de *production* AEM as a Cloud Service, enregistrez un ticket d’assistance. Informez Adobe de votre intention d’exécuter l’*ingestion* afin qu’il puisse garantir l’absence d’interruption pendant le processus d’*ingestion*. Enregistrez le ticket d’assistance une semaine avant la date prévue pour l’*ingestion*. Une fois que vous avez envoyé le ticket d’assistance, l’équipe d’assistance vous conseille sur la démarche à suivre. Enregistrez un ticket d’assistance avec les détails suivants :

   * Date exacte et heure estimée (avec votre fuseau horaire) lorsque vous prévoyez de lancer la phase d’*ingestion*.
   * Type d’environnement (évaluation ou production) dans lequel vous prévoyez d’importer des données.
   * ID de programme.

* La *phase d’ingestion* de l’auteur réduit l’ensemble du déploiement de l’auteur. L’instance de création AEM ne sera donc pas disponible pendant toute la durée du processus d’ingestion. Assurez-vous également qu’aucun pipeline Cloud Manager n’est exécuté pendant que vous exécutez la phase d’*ingestion*.

* Si vous utilisez `Amazon S3` ou `Azure` comme entrepôt de données sur le système AEM source, cet entrepôt doit être configuré de sorte que les objets blob stockés ne puissent pas être supprimés (nettoyage de la mémoire). Cela garantit l’intégrité des données d’index et un échec de ce type de configuration peut entraîner des échecs d’extraction en raison d’un manque d’intégrité de ces données d’index.

* Si vous utilisez des index personnalisés, vous devez veiller à les configurer avec le nœud `tika` avant d’exécuter l’outil de transfert de contenu. Pour plus d’informations, voir la section [Préparation de la nouvelle définition d’index](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=fr#preparing-the-new-index-definition).

* Si vous avez l’intention d’effectuer des exécutions complémentaires, ne modifiez pas la structure du contenu existant entre l’extraction initiale et l’extraction complémentaire. Il est impossible d’effectuer des exécutions complémentaires sur du contenu dont la structure a été modifiée après l’extraction initiale. Veillez à limiter cette opération pendant le processus de migration.

* Si vous envisagez d’inclure différentes versions dans un jeu de migration et effectuez des compléments avec `wipe=false`, vous devez désactiver la purge des versions en raison d’une restriction actuelle de l’outil de transfert de contenu. Si vous préférez conserver la purge de version activée et effectuer des compléments dans un jeu de migration, vous devez effectuer l’ingestion sous la forme `wipe=true`.

## Prochaines étapes {#whats-next}

Une fois que vous avez lu les instructions, les bonnes pratiques et les points importants à prendre en compte pour l’utilisation de l’outil de transfert de contenu, vous êtes prêt à installer et à utiliser l’outil, en commençant par la création d’un jeu de migration. Consultez [Prise en main de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr) pour en savoir plus.
