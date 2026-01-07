---
Title: How to Connect AEM Adaptive Forms with Azure SQL Storage
Description: Learn how to configure an Azure SQL Database connection in AEM Forms and integrate it with your Adaptive Forms to store or retrieve data efficiently using JDBC.
Keywords: Azure SQL integration with AEM Forms, Connecting Adaptive Forms to Azure SQL Database, JDBC connection for Azure SQL in AEM Forms, Storing Adaptive Form data in Azure SQL
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: 40193d89f2a4ef864a564eb9932403531eaf1ff7
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 4%

---

# Connecter un formulaire adaptatif au stockage Azure SQL

Le Forms adaptatif dans Adobe Experience Manager (AEM) peut s’intégrer à des bases de données externes pour stocker ou récupérer des données.
Cet article explique comment connecter un formulaire adaptatif à une base de données SQL Azure à l’aide de JDBC via AEM as a Cloud Service.

> 
> 
> Ce guide s’applique aux environnements AEM as a Cloud Service hors sandbox pour lesquels la mise en réseau avancée est activée.

## Avantages

L’intégration de Forms adaptatif à Azure SQL offre plusieurs avantages :

* **Interaction des données en temps réel :** permet la lecture et l’écriture en direct de données entre les formulaires et la base de données Azure.
* **Évolutivité :** Azure SQL offre des performances de base de données évolutives adaptées aux applications d’entreprise.
* **Stockage centralisé des données :** permet de conserver en toute sécurité les envois de formulaires et les données récupérées dans un emplacement central.
* **Conformité en matière de sécurité :** exploite le réseau intégré, le pare-feu et les options de chiffrement d’Azure pour garantir une communication sécurisée.
* **Intégration native au cloud :** idéale pour les architectures modernes et primées sur le cloud utilisant AEM as a Cloud Service.

## Conditions préalables

* Créez [Base de données SQL Azure](https://learn.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?view=azuresql&tabs=azure-portal) et assurez-vous que **connexion proxy** est activée.

  >[!NOTE]
  >
  > Accédez à : `Azure Portal → SQL Server → Security → Networking → Connectivity` pour activer **connexion proxy**.

  ![Créer Azure Db](/help/forms/assets/create-azure-db.png)

* Activez [la mise en réseau avancée configurée à l’aide d’une adresse IP de sortie dédiée](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/networking/dedicated-egress-ip-address) pour la base de données Azure créée.

  >[!NOTE]
  >
  >    Après avoir activé l’adresse IP sortante dédiée. Accédez à `Azure Portal → SQL Server → Security → Networking → Public Access` et ajoutez l’adresse IP sortante aux règles de pare-feu.

  ![Adresse IP de sortie](/help/forms/assets/cretae-azure-db-egress-ip.png)

* Définissez le transfert de port dans l’environnement cloud avec :
   * **portOrigin** : entre `30000–30999`
   * **portDest** : `1433` (port par défaut pour Azure SQL)
Par exemple : `portOrigin: 30433 → portDest: 1433`

     > 
     > 
     > Vous pouvez contacter l’assistance Cloud Manager d’Adobe pour configurer le transfert de port.


## Étapes de connexion de Forms adaptatif à Azure SQL

**Étape 1 : clonage du référentiel Git AEM as a Cloud Service**

1. Ouvrez la ligne de commande et sélectionnez un répertoire pour stocker votre référentiel AEM as a Cloud Service, tel que `/cloud-service-repository/`.

1. Exécutez la commande ci-dessous pour cloner le référentiel :

   ```
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<app-id>/
   ```

   **Où trouver ces informations ?**

   Pour obtenir des instructions détaillées sur la localisation de ces détails, reportez-vous à l’article Adobe Experience League « [Accès à Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) ».

   Une fois la commande terminée, un nouveau dossier est créé dans votre répertoire local. Ce dossier porte le nom de votre application.

1. Ouvrez le dossier du référentiel dans un éditeur.

**Étape 2 : ajouter les fichiers JAR requis**

Incluez la dépendance [pilote SQL](https://central.sonatype.com/artifact/com.microsoft.sqlserver/mssql-jdbc/12.8.0.jre11?smo=true) dans le projet AEM via le package `all`. :

>[!NOTE]
>
> Pour inclure la dépendance SQL dans votre projet, reportez-vous à la section [Dépendances des pilotes SQL](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool#mysql-driver-dependencies).

**Étape 3 : ajouter une configuration JDBC**

1. Accédez au répertoire suivant de votre `<application folder>` où doit être placée la configuration OSGi du pool JDBC :

   ```bash
   cd ui.config/src/jcr_root/apps/<application folder>/osgiconfig/config/
   ```

**Étape 4 : créer le fichier de configuration de connexion SQL Azure**

1. Créez le fichier :

   ```bash
   com.day.commons.datasource.jdbcpool.JdbcPoolService~<application folder>-sql.cfg.json
   ```

1. Ajoutez les lignes de code ci-dessous :

   ```json
   {
   "datasource.name": "azuredbshr",
   "jdbc.driver.class": "com.microsoft.sqlserver.jdbc.SQLServerDriver",
   "jdbc.username": "<azureuser>",
   "jdbc.connection.uri": "jdbc:sqlserver://$[env:AEM_PROXY_HOST;default=proxy.tunnel]:30433;database=testdb;user=<azureuser>;password=<azurepassword>;encrypt=true;trustServerCertificate=false;hostNameInCertificate=*.database.windows.net;loginTimeout=30;",
   "jdbc.password": "******",
   "jdbc.validation.query": "SELECT 1"
       }
   ```

   > 
   >
   > Remplacez `jdbc.username` par le nom d’utilisateur Azure réel et `jdbc.password` par le mot de passe sécurisé réel.

**Étape 5 : valider et transmettre les modifications**

Ouvrez le terminal et exécutez les commandes suivantes :

```bash
git add .
git commit -m "<commit message>"
git push 
```

**Étape 6 : déployer les modifications via le pipeline Cloud Manager**

1. Connectez-vous à **AEM Cloud Manager**.
1. Accédez à votre projet et exécutez le pipeline pour déployer les modifications.

**Étape 7 : créer un modèle de données de formulaire (FDM)**

Une fois la configuration d’AEM et d’Azure terminée et les modifications de code déployées :

1. Accédez à l’instance d’auteur AEM.
1. Accédez à **Outils** > **Forms** > **Intégrations de données**.
1. Créez un **modèle de données de formulaire**.
1. Dans l’onglet **Sources de données**, sélectionnez la configuration JDBC créée.
1. Cliquez sur **[!UICONTROL Créer]** et vérifiez la connexion.

![Création d’un modèle de données de formulaire](/help/forms/assets/create-azure-sql-fdm.png)

**Étape 8 : utiliser le FDM créé dans un formulaire adaptatif**

1. Ouvrez un formulaire adaptatif en mode d’édition.
1. Sélectionnez le FDM créé à l’étape précédente comme modèle de données.
1. Utilisez des liaisons de données [ pour connecter les champs de formulaire à la source de données SQL Azure](/help/forms/work-with-form-data-model.md#add-data-model-objects-and-services) et configurez l’action d’envoi.

## Bonnes pratiques

* Utilisez la **gestion des secrets** pour éviter les mots de passe de codage en dur dans les fichiers de configuration.
* Faites régulièrement pivoter les informations d’identification de base de données et mettez à jour la configuration en toute sécurité.
* Surveillez les journaux de connectivité JDBC pour détecter les échecs et la latence.
* Appliquez les bonnes pratiques Azure pour sécuriser les bases de données SQL et les configurations de pare-feu.
* Évitez d’utiliser des comptes de base de données à privilèges élevés pour l’accès aux formulaires.

## Articles connexes

{{af-submit-action}}