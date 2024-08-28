---
title: Instructions et bonnes pratiques relatives à l’utilisation de l’outil de transfert de contenu
description: Découvrez les instructions et les bonnes pratiques relatives à l’utilisation de l’outil de transfert de contenu.
exl-id: d1975c34-85d4-42e0-bb1a-968bdb3bf85d
feature: Migration
role: Admin
source-git-commit: e5fd1b351047213adbb83ef1d1722352958ce823
workflow-type: tm+mt
source-wordcount: '1368'
ht-degree: 54%

---


# Bonnes pratiques et instructions pour l’utilisation de l’outil de transfert de contenu {#guidelines}

## Conseils et bonnes pratiques {#best-practices}

<!-- Alexandru: hiding for now

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="Guidelines and Best Practices"
>abstract="Review guidelines and best practices to use the Content Transfer tool including revision cleanup tasks, Disk space considerations and more."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html" text="Important Considerations for using Content Transfer Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/group-migration.md#important-considerations" text="Important Considerations when Migrating Groups" 

-->

L’outil de transfert de contenu intègre le processus de transfert de contenu à Cloud Acceleration Manager. Il est nécessaire d’utiliser cette version (2.0 ou ultérieure, mais la version 3.0 est désormais recommandée) pour bénéficier de tous les avantages qu’elle offre :

* Une méthode en libre-service pour extraire une seule fois un jeu de migration et l’ingérer dans plusieurs environnements en parallèle
* Amélioration de l’expérience utilisateur grâce à l’amélioration des états de chargement, des barrières de sécurité et de la gestion des erreurs
* Conservation des journaux d’ingestion et leur constante disponibilité à des fins de dépannage

Pour commencer à utiliser la version la plus récente, désinstallez les anciennes versions de l’outil de transfert de contenu. Avec les versions 2.0 et ultérieures, vous créez des jeux de migration et réexécutez l’extraction et l’ingestion sur les jeux.
Les versions antérieures à la version 2.0.0 ne sont pas prises en charge et il est conseillé d’utiliser la version la plus récente.

Les conseils et bonnes pratiques suivants s’appliquent à la nouvelle version de l’outil de transfert de contenu :

* Exécutez le [ nettoyage des révisions ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=fr) et les [ contrôles de cohérence de l’entrepôt de données ](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16550.html) sur le référentiel **source** afin que vous puissiez identifier les problèmes potentiels et réduire la taille du référentiel.

* Lors de la phase d’ingestion, Adobe vous recommande d’exécuter l’ingestion en utilisant le mode *Wipe* activé où le référentiel existant (auteur ou Publish) dans l’environnement de Cloud Service Adobe Experience Manager (AEM) cible est supprimé. Ensuite, mettez à jour avec les données du jeu de migration. Ce mode est plus rapide que le mode sans effacement, où le jeu de migration est appliqué en plus du contenu actuel.

* Une fois l’activité de transfert de contenu terminée, une structure de projet appropriée est nécessaire dans l’environnement Cloud Service pour s’assurer que le contenu s’affiche correctement.

* Avant d’exécuter l’outil de transfert de contenu, vous devez vous assurer que l’espace disque disponible dans le sous-répertoire `crx-quickstart` de l’instance AEM source est suffisant. En effet, l’outil de transfert de contenu crée une copie locale du référentiel, ultérieurement chargée dans le jeu de migration.
La formule générale pour calculer l’espace disque disponible requis est la suivante :
  `data store size + node store size * 1.5`

* *volume de stockage des données* : l’outil de transfert de contenu utilise 64 Go, même si l’entrepôt de données en question est plus volumineux.
* *volume de stockage des nœuds* : taille du répertoire de stockage des segments ou taille de la base de données MongoDB.
Ainsi, pour un volume de stockage de segments de 20 Go, l’espace disque disponible requis est de 94 Go.

* Un jeu de migration doit être conservé tout au long de l’activité de transfert de contenu pour prendre en charge les compléments de contenu. Au maximum, 20 jeux de migration par projet dans Cloud Acceleration Manager peuvent être créés et gérés simultanément pendant l’activité de transfert de contenu. Si plus de 20 jeux de migration sont nécessaires, créez un second projet dans Cloud Acceleration Manager. Toutefois, cela nécessite une gestion de projet supplémentaire et une gouvernance hors produit afin d’éviter le remplacement de contenu sur la cible par plusieurs utilisateurs.

* Évitez de modifier le répertoire d’installation de l’outil CTT. Par défaut, l’installation a lieu dans le chemin crx-quickstart/cloud-migration. Cet emplacement spécifique est utilisé en interne par d’autres bibliothèques. La modification de ce chemin peut entraîner des problèmes d’extraction.

## Points importants avant d’utiliser l’outil de transfert de contenu {#important-considerations}

Consultez la section ci-dessous afin de comprendre les points importants à prendre en compte pour l’exécution de l’outil de transfert de contenu :

* La configuration minimale requise pour l’outil de transfert de contenu est AEM 6.3+ et Java™ 8. Si vous utilisez une version d’AEM inférieure, mettez à niveau votre référentiel de contenu vers AEM 6.5 pour utiliser l’outil de transfert de contenu.

* Java doit être configuré dans l’environnement AEM, de sorte que la commande `java` puisse être exécutée par l’utilisateur ou l’utilisatrice démarrant AEM.

* L’outil de transfert de contenu peut être utilisé avec les types de magasin de données suivants : File Data Store, S3 Data Store, Shared S3 Data Store et Azure Blob Store Data Store.

* Si vous utilisez un *environnement sandbox*, assurez-vous que celui-ci est à jour et mis à niveau vers la dernière version. Si vous utilisez un *environnement de production*, il est automatiquement mis à jour.

* Pour commencer une ingestion, vous devez appartenir au groupe local AEM **administrateurs** dans l’instance de Cloud Service à laquelle vous transférez du contenu. Les utilisateurs non privilégiés ne peuvent pas démarrer d’ingestion sans fournir manuellement le jeton de migration.

* Lorsque l’option **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est activée, elle supprime l’intégralité du référentiel existant et crée un référentiel dans lequel ingérer du contenu. Cela signifie que tous les paramètres sont réinitialisés, y compris les autorisations relatives à l’instance Cloud Service cible. C’est également le cas pour un utilisateur administrateur ajouté au groupe **administrateurs**. L’utilisateur doit être lu dans le groupe **administrateurs** pour récupérer le jeton d’accès pour l’outil de transfert de contenu.

* Les ingestions ne prennent pas en charge la fusion de contenu provenant de plusieurs sources dans l’instance Cloud Service cible si le contenu provenant des deux sources est déplacé vers les mêmes chemins d’accès sur la cible. Pour déplacer le contenu de plusieurs sources vers une seule instance de Cloud Service cible, assurez-vous qu’il n’y a aucun chevauchement des chemins de contenu des sources.

* La clé d&#39;extraction est valable 14 jours à compter de sa création ou de son renouvellement. Elle peut être renouvelée à tout moment. Si la clé d&#39;extraction a expiré, vous ne pouvez pas effectuer d&#39;extraction.

* L’outil de transfert de contenu (CTT) n’effectue aucune analyse avant de transférer le contenu de l’instance source vers l’instance cible. Par exemple, le CTT ne fait pas de distinction entre le contenu publié et le contenu dépublié lors de l’ingestion de contenu dans un environnement de publication. Quel que soit le contenu spécifié dans le jeu de migration, il sera ingéré dans l’instance cible choisie. Un utilisateur peut ingérer un jeu de migration dans une instance d’auteur ou une instance Publish, ou les deux. Adobe recommande que, lors du déplacement du contenu vers une instance de production, CTT soit installé sur l’instance d’auteur source pour déplacer le contenu vers l’instance d’auteur cible. De même, installez le CTT sur l’instance de publication source pour déplacer le contenu vers l’instance de publication cible. Pour en savoir plus, consultez [Exécution de l’outil de transfert de contenu sur une instance de publication](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr#running-tool).

* Les groupes transférés par l’outil de transfert de contenu sont uniquement ceux qui sont requis par le contenu pour satisfaire aux autorisations. Le processus _Extraction_ copie l’intégralité de `/home/groups` dans le jeu de migration. Pour plus d’informations, voir [Migration de groupe](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md). Le processus _Ingestion_ copie tous les groupes référencés dans les listes de contrôle d’accès du contenu migré. Voir [Migration des groupes d’utilisateurs fermés](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/closed-user-groups-migration.md) pour plus d’informations sur les groupes utilisés dans une stratégie de groupe d’utilisateurs fermé (CUG).

* Pendant la phase d’extraction, l’outil de transfert de contenu est exécuté sur une instance source AEM active.

* La *phase d’ingestion* de l’auteur réduit l’ensemble du déploiement de l’auteur. Cela signifie que l’AEM de création n’est pas disponible pendant l’ensemble du processus d’ingestion. Assurez-vous également qu’aucun pipeline Cloud Manager n’est exécuté pendant que vous exécutez la phase d’*ingestion*.

* Si vous utilisez `Amazon S3` ou `Azure` comme entrepôt de données sur le système AEM source, cet entrepôt doit être configuré de sorte que les objets blob stockés ne puissent pas être supprimés (nettoyage de la mémoire). Cela garantit l’intégrité des données d’index et un échec de ce type de configuration peut entraîner des échecs d’extraction en raison d’un manque d’intégrité de ces données d’index.

* Si vous utilisez des index personnalisés, vous devez veiller à les configurer avec le nœud `tika` avant d’exécuter l’outil de transfert de contenu. Pour plus d’informations, voir [Préparation de la nouvelle définition d’index](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#preparing-the-new-index-definition).

* Si vous envisagez d’effectuer des compléments, la structure de contenu du contenu existant ne doit pas changer du moment de l’extraction initiale au moment de l’exécution de l’extraction de complément. Les compléments peuvent pas être exécutés sur du contenu dont la structure a été modifiée depuis l’extraction initiale. Veillez à limiter cette opération pendant le processus de migration.

* Si vous envisagez d’inclure différentes versions dans un jeu de migration et effectuez des compléments avec `wipe=false`, vous devez désactiver la purge des versions en raison d’une restriction actuelle de l’outil de transfert de contenu. Si vous préférez conserver la purge de version activée et effectuer des compléments dans un jeu de migration, vous devez effectuer l’ingestion sous la forme `wipe=true`.

* Un jeu de migration expire après une longue période d’inactivité, après laquelle ses données ne sont plus disponibles. Pour en savoir plus, veuillez consulter [Expiration du jeu de migration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=fr#migration-set-expiry).

## Prochaines étapes {#whats-next}

Une fois que vous avez lu les instructions, les bonnes pratiques et les points importants à prendre en compte pour l’utilisation de l’outil de transfert de contenu, vous êtes prêt à installer et à utiliser l’outil, en commençant par la création d’un jeu de migration. Voir [Prise en main de l’outil de transfert de contenu](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md).
