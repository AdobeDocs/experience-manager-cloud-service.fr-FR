---
title: Bonnes pratiques et instructions pour l’utilisation de l’outil de transfert de contenu
description: Bonnes pratiques et instructions pour l’utilisation de l’outil de transfert de contenu
exl-id: d1975c34-85d4-42e0-bb1a-968bdb3bf85d
source-git-commit: 98b81d918d60722ddb3f1c7736bc5b3506e05f6f
workflow-type: tm+mt
source-wordcount: '1654'
ht-degree: 78%

---

# Bonnes pratiques et instructions pour l’utilisation de l’outil de transfert de contenu {#guidelines}

## Conseils et bonnes pratiques {#best-practices}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_guidelines"
>title="Conseils et bonnes pratiques"
>abstract="Consultez les instructions et les bonnes pratiques relatives à l’utilisation de l’outil de transfert de contenu, notamment les tâches de nettoyage des révisions, les considérations relatives à l’espace disque, etc."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=fr#pre-reqs" text="Points importants concernant l’utilisation de l’outil de transfert de contenu"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr#important-considerations" text="Points importants concernant l’utilisation de l’outil de mappage des utilisateurs"

Une nouvelle version de l’outil de transfert de contenu est disponible, qui intègre le processus de transfert de contenu à Cloud Acceleration Manager. Il est vivement recommandé de passer à cette nouvelle version afin d’exploiter tous les avantages qu’elle offre :

* Méthode en libre-service pour extraire une fois un jeu de migration et l’ingérer dans plusieurs environnements en parallèle
* Amélioration de l’expérience utilisateur grâce à une meilleure gestion des états de chargement, des barrières de sécurité et des erreurs.
* Les journaux d’ingestion sont conservés et sont toujours disponibles pour le dépannage.

Pour commencer à utiliser la nouvelle version (v2.0.10), vous devez désinstaller les anciennes versions de l’outil de transfert de contenu. Cela est nécessaire car la nouvelle version est accompagnée d’un changement architectural majeur. Avec la version 2.0.10, vous devrez créer de nouveaux jeux de migration et relancer l’extraction et l’ingestion sur les nouveaux jeux de migration. Si une migration est déjà en cours, vous pouvez continuer à utiliser la version antérieure du CTT jusqu’à ce que la migration soit terminée.

Les conseils et bonnes pratiques suivants s’appliquent à la nouvelle version de l’outil de transfert de contenu :

* Il est conseillé de procéder à un [nettoyage de révision](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=fr) et à des [contrôles de cohérence de l’entrepôt de données](https://helpx.adobe.com/fr/experience-manager/kb/How-to-run-a-datastore-consistency-check-via-oak-run-AEM.html) sur le référentiel **source** pour identifier les problèmes potentiels et réduire la taille du référentiel.

* Si le réseau de diffusion de contenu (CDN) de l’instance d’auteur AEM Cloud est configuré pour disposer d’une liste blanche d’adresses IP, il faut s’assurer que les adresses IP de l’environnement source sont aussi ajoutées à la liste autorisée pour que l’environnement source et l’environnement AEM Cloud puissent communiquer entre eux.

* Lors de la phase d’ingestion, il est recommandé d’exécuter l’ingestion en activant le mode d’*effacement*. Dans ce cas, le référentiel existant (auteur ou publication) de l’environnement AEM Cloud Service cible sera complètement supprimé, puis mis à jour à l’aide des données du jeu de migration. Ce mode est beaucoup plus rapide que le mode sans effacement, où le jeu de migration est appliqué par-dessus le contenu existant.

* Une fois l’activité de transfert de contenu terminée, une structure de projet appropriée est nécessaire dans l’environnement Cloud Service pour s’assurer que le contenu s’affiche correctement.

* Avant d’exécuter l’outil de transfert de contenu, vous devez vous assurer que l’espace disque disponible dans le sous-répertoire `crx-quickstart` de l’instance AEM source est suffisant. En effet, l’outil de transfert de contenu crée une copie locale du référentiel, ultérieurement chargée dans le jeu de migration.
La formule générale pour calculer l’espace disque disponible requis est la suivante :
   `data store size + node store size * 1.5`

   * *volume de stockage des données* : l’outil de transfert de contenu utilise 64 Go, même si l’entrepôt de données en question est plus volumineux.
   * *volume de stockage des nœuds* : taille du répertoire de stockage des segments ou taille de la base de données MongoDB.
Ainsi, pour un volume de stockage de segments de 20 Go, l’espace disque disponible requis est de 94 Go.

* Un jeu de migration doit être conservé tout au long de l’activité de transfert de contenu pour prendre en charge les compléments de contenu. Au maximum, cinq jeux de migration par projet dans Cloud Acceleration Manager peuvent être créés et conservés à la fois pendant l’activité de transfert de contenu. Si plus de cinq jeux de migration sont nécessaires, vous devrez créer un second projet dans Cloud Acceleration Manager. Toutefois, cela nécessitera une gestion de projet supplémentaire et une gouvernance hors produit afin d’éviter le remplacement de contenu sur la cible par plusieurs utilisateurs.

## Points importants avant d’utiliser l’outil de transfert de contenu {#important-considerations}

Consultez la section ci-dessous afin de comprendre les points importants à prendre en compte pour l’exécution de l’outil de transfert de contenu :

* La configuration minimale requise pour l’outil de transfert de contenu est AEM 6.3+ et JAVA 8. Si vous utilisez une version antérieure d’AEM, vous devez mettre à niveau votre référentiel de contenu à la version AEM 6.5 pour utiliser l’outil de transfert de contenu.

* Java doit être configuré dans l’environnement AEM, de sorte que la commande `java` puisse être exécutée par l’utilisateur démarrant AEM.

* L’outil de transfert de contenu peut être utilisé avec les types de magasin de données suivants : File Data Store, S3 Data Store, Shared S3 Data Store et Azure Blob Store Data Store.

* Si vous utilisez un *environnement sandbox*, assurez-vous que celui-ci est à jour et mis à niveau vers la dernière version. Si vous utilisez un *environnement de production*, il est automatiquement mis à jour.

* Pour utiliser l’outil de transfert de contenu, vous devez être un utilisateur administrateur sur votre instance source et appartenir au groupe d’**administrateurs** AEM local dans l’instance Cloud Service vers laquelle vous transférez du contenu. Les utilisateurs non privilégiés ne pourront pas commencer des assimilations.

* Lorsque l’option **Effacer le contenu existant sur l’instance cloud avant l’ingestion** est activée, elle supprime l’intégralité du référentiel existant et crée un référentiel dans lequel ingérer du contenu. Cela signifie que tous les paramètres sont réinitialisés, y compris les autorisations relatives à l’instance Cloud Service cible. C’est également vrai pour un utilisateur administrateur ajouté au groupe **administrateurs**. L’utilisateur doit être rajouté au **administrateurs** afin de récupérer le jeton d’accès pour l’outil de transfert de contenu.

* L’outil de transfert de contenu ne prend pas en charge la fusion de contenu provenant de plusieurs sources dans l’instance de Cloud Service cible si le contenu provenant des deux sources est déplacé vers les mêmes chemins d’accès sur la cible. Pour déplacer le contenu de plusieurs sources vers une seule instance de Cloud Service cible, vous devez vous assurer qu’il n’y a pas de chevauchement des chemins de contenu des sources.

* La clé d&#39;extraction est valable 14 jours à compter du moment où elle a été créée/renouvelée. Il peut être renouvelé à tout moment. Si la clé d&#39;extraction a expiré, vous ne pourrez pas effectuer d&#39;extraction.

* L’outil de transfert de contenu (CTT) n’effectue aucune analyse avant de transférer le contenu de l’instance source vers l’instance cible. Par exemple, le CTT ne fait pas de distinction entre le contenu publié et le contenu non publié lors de l’ingestion de contenu dans un environnement de publication. Quel que soit le contenu spécifié dans le jeu de migration, il sera ingéré dans l’instance cible choisie. L’utilisateur peut ingérer un jeu de migration dans une instance d’auteur ou de publication, ou les deux. Il est recommandé, tout en déplaçant le contenu vers une instance de production, d’installer le CTT sur l’instance d’auteur source afin de déplacer le contenu vers l’instance d’auteur cible. De même, il est recommandé d’installer le CTT dans l’instance de publication source pour déplacer le contenu vers l’instance de publication cible. Pour plus d’informations, consultez [Exécution de l’outil de transfert de contenu sur une instance de publication](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=fr#running-ctt-on-publish).

* Les utilisateurs et les groupes transférés par l’outil de transfert de contenu sont uniquement ceux requis en fonction du contenu pour respecter les autorisations. Le processus d’*extraction* copie l’intégralité de `/home` dans le jeu de migration et le processus d’*ingestion* copie tous les utilisateurs et groupes référencés dans les listes de contrôle d’accès du contenu migré. Pour mapper automatiquement les utilisateurs et les groupes existants avec leurs ID IMS, reportez-vous à la section [Utilisation de l’outil de mappage des utilisateurs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=fr#cloud-migration).

* Pendant la phase d’extraction, l’outil de transfert de contenu est exécuté sur une instance source AEM active.

* Après avoir terminé la phase d’*extraction* du processus de transfert de contenu et avant de commencer la phase d’*ingestion* pour ingérer du contenu dans vos instances d’*évaluation* ou de *production* AEM as a Cloud Service, vous devez enregistrer un ticket d’assistance pour informer Adobe de votre intention d’exécuter *Ingestion* afin qu’Adobe puisse s’assurer qu’aucune interruption ne se produise pendant le processus d’*ingestion*. Vous devrez consigner le ticket de support une semaine avant la date d’*Ingestion* prévue. Une fois que vous aurez soumis le ticket d’assistance, l’équipe d’assistance vous donnera des conseils sur les étapes suivantes. Vous pouvez enregistrer un ticket d’assistance avec les détails suivants :

   * Date exacte et heure estimée (avec votre fuseau horaire) lorsque vous prévoyez de lancer la phase d’*ingestion*.
   * Type d’environnement (évaluation ou production) dans lequel vous prévoyez d’importer des données.
   * ID de programme.

* La *phase d’ingestion* de l’auteur réduit l’ensemble du déploiement de l’auteur. L’auteur AEM ne sera donc pas disponible pendant la totalité du processus d’ingestion. Assurez-vous également qu’aucun pipeline Cloud Manager n’est exécuté pendant que vous exécutez la phase d’*ingestion*.

* Si vous utilisez `Amazon S3` ou `Azure` comme entrepôt de données sur le système AEM source, cet entrepôt doit être configuré de sorte que les objets blob stockés ne puissent pas être supprimés (nettoyage de la mémoire). Cela garantit l’intégrité des données d’index et un échec de ce type de configuration peut entraîner des échecs d’extraction en raison d’un manque d’intégrité de ces données d’index.

* Si vous utilisez des index personnalisés, vous devez veiller à les configurer avec le nœud `tika` avant d’exécuter l’outil de transfert de contenu. Pour plus d’informations, voir la section [Préparation de la nouvelle définition d’index](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=fr#preparing-the-new-index-definition).

* Si vous avez l’intention d’effectuer des compléments, il est essentiel que la structure de contenu du contenu existant ne soit pas modifiée du moment où l’extraction initiale est prise au moment de l’exécution de l’extraction de complément. Les compléments peuvent pas être exécutés sur du contenu dont la structure a été modifiée depuis l’extraction initiale. Veillez à limiter cette opération pendant le processus de migration.

* Si vous envisagez d’inclure différentes versions dans un jeu de migration et effectuez des compléments avec `wipe=false`, vous devez désactiver la purge des versions en raison d’une restriction actuelle de l’outil de transfert de contenu. Si vous préférez conserver la purge de version activée et effectuer des compléments dans un jeu de migration, vous devez effectuer l’ingestion sous la forme `wipe=true`.

## Prochaines étapes {#whats-next}

Une fois que vous avez lu les instructions, les bonnes pratiques et les points importants à prendre en compte pour l’utilisation de l’outil de transfert de contenu, vous êtes prêt à installer et à utiliser l’outil, en commençant par la création d’un jeu de migration. Consultez [Prise en main de l’outil de transfert de contenu](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=fr) pour en savoir plus.
