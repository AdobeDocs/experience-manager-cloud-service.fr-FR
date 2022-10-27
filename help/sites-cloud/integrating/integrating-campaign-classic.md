---
title: Intégration à Adobe Campaign Classic
description: Découvrez comment intégrer AEM as a Cloud Service à Adobe Campaign Classic afin de créer du contenu attrayant pour vos campagnes.
feature: Administering
role: Admin
exl-id: 23874955-bdf3-41be-8a06-53d2afdd7f2b
source-git-commit: cab630838f5cce3c2a2749c61b0aa7504dc403f7
workflow-type: tm+mt
source-wordcount: '1302'
ht-degree: 100%

---

# Intégration à Adobe Campaign Classic {#integrating-campaign-classic}

En intégrant AEM as a Cloud Service à Adobe Campaign, vous pouvez gérer la diffusion par e-mail, le contenu et les formulaires directement dans AEM as a Cloud Service. Des étapes de configuration aussi bien dans Adobe Campaign Classic que dans AEM as a Cloud Service sont nécessaires pour permettre la communication bidirectionnelle entre ces solutions.

Cette intégration permet à AEM as a Cloud Service et à Adobe Campaign Classic d’être utilisés indépendamment. Les marketeurs peuvent créer des campagnes et utiliser le ciblage dans Adobe Campaign, tandis qu’en parallèle, les créateurs de contenu peuvent travailler sur la conception de contenu dans AEM as a Cloud Service. L’intégration permet à Campaign de cibler et de diffuser du contenu ainsi que de concevoir des campagnes dans AEM.

## Étapes d’intégration {#integration-steps}

L’intégration entre AEM et Campaign requiert un certain nombre d’étapes dans les deux solutions.

1. [Installer le pack d’intégration AEM dans Campaign](#install-package)
1. [Créer un opérateur pour AEM dans Campaign](#create-operator)
1. [Configurer l’intégration de Campaign à AEM](#campaign-integration)
1. [Configurer l’externaliseur AEM](#externalizer)
1. [Configurer l’utilisateur distant de Campaign dans AEM](#configure-user)
1. [Configurer le compte externe AEM dans Campaign](#acc-setup)

Ce document vous guide de façon détaillée à travers chacune de ces étapes.

## Conditions préalables {#prerequisites}

* Accès des administrateurs à Adobe Campaign Classic
   * Pour effectuer l’intégration, vous avez besoin d’une instance Adobe Campaign Classic opérationnelle, y compris d’une base de données configurée.
   * Si vous avez besoin de détails supplémentaires sur l’installation et la configuration d’Adobe Campaign Classic, veuillez vous reporter à la section [Documentation d’Adobe Campaign Classic,](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=fr) et particulièrement au Guide d’installation et de configuration.

* Accès des administrateurs à AEM as a Cloud Service

## Installer le package d’intégration d’AEM à Campaign {#install-package}

Le package d’**intégration d’AEM** à Adobe Campaign comprend plusieurs configurations standard nécessaires pour se connecter à AEM.

1. En tant qu’administrateur, connectez-vous à l’instance Adobe Campaign à l’aide de la console cliente.

1. Sélectionnez **Outils** > **Avancés** > **Importer un package...**.

   ![Importer un package](assets/import-package.png)

1. Cliquez sur **Installer un package standard** puis cliquez sur **Suivant**.

1. Vérifiez le package d’**intégration d’AEM**.

   ![Installer un package standard](assets/select-package.png)

1. Cliquez sur **Suivant**, et puis sur **Démarrer** pour commencer l’installation.

   ![Progression de l’installation](assets/installation.png)

1. Cliquez sur **Fermer** à la fin de l’installation.

Le package d’intégration est maintenant installé.

## Créer l’opérateur AEM dans Campaign {#create-operator}

Le package d’intégration crée automatiquement l’opérateur `aemserver` qu’AEM utilise pour se connecter à Adobe Campaign. Vous devez définir une zone de sécurité pour cet opérateur et définir son mot de passe.

1. Connectez-vous à Adobe Campaign en tant qu’administrateur à l’aide de la console cliente.

1. Sélectionnez **Outils** -> **Explorateur** dans la barre des menus.

1. Dans l’explorateur, accédez au nœud **Administration** > **Gestion des accès** > **Opérateurs**.

1. Sélectionnez l’opérateur `aemserver`.

1. Sous l’onglet **Modifier** de l’opérateur, sélectionnez le sous-onglet **Droits d’accès** et puis cliquez sur le lien **Modifier les paramètres d’accès...**.

   ![Définir la zone de sécurité](assets/access-rights.png)

1. Sélectionnez la zone de sécurité appropriée et définissez le masque IP de confiance selon vos besoins.

1. Cliquez sur **Enregistrer**.

1. Déconnectez-vous du client Adobe Campaign.

1. Dans le système de fichiers du serveur Adobe Campaign, accédez à l’emplacement d’installation de Campaign et modifiez le fichier `serverConf.xml` en tant qu’administrateur. Ce fichier se trouve généralement sous :
   * `C:\Program Files\Adobe\Adobe Campaign Classic v7\conf` sous Windows.
   * `/usr/local/neolane/nl6/conf/eng` sous Linux.

1. Recherchez `securityZone` et assurez-vous que les paramètres suivants sont définis pour la zone de sécurité de l’opérateur AEM.

   * `allowHTTP="true"`
   * `sessionTokenOnly="true"`
   * `allowUserPassword="true"`.

1. Enregistrez le fichier.

1. Assurez-vous que la zone de sécurité n’est pas écrasée par le paramètre correspondant dans le fichier `config-<server name>.xml`.

   * Si le fichier de configuration contient un paramètre de zone de sécurité distinct, alors définissez l’attribut `allowUserPassword` sur `true`.

1. Si vous souhaitez modifier le port du serveur Adobe Campaign Classic, remplacez `8080` par le port souhaité.

>[!CAUTION]
>
>Par défaut, aucune zone de sécurité n’est configurée pour l’opérateur. Pour qu’AEM se connecte à Adobe Campaign, vous devez sélectionner une zone comme décrit dans les étapes précédentes.
>
>Adobe recommande vivement de créer une zone de sécurité dédiée à AEM afin d’éviter tout problème de sécurité. Pour plus d’informations à ce sujet, reportez-vous à la [documentation d’Adobe Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/security-zones.html?lang=fr).

1. Dans le client Campaign, revenez à l’opérateur `aemserver` et sélectionnez l’onglet **Général**.

1. Cliquez sur le lien **Réinitialiser le mot de passe...**.

1. Indiquez un mot de passe et stockez-le dans un emplacement sécurisé en vue d’une utilisation ultérieure.

1. Cliquez sur **OK** pour enregistrer le mot de passe pour l’opérateur `aemserver`.

## Configurer l’intégration de Campaign dans AEM {#campaign-integration}

AEM utilise [l’opérateur que vous avez déjà configuré dans Campaign](#create-operator) afin de communiquer avec Campaign.

1. Connectez-vous à votre instance de création AEM en tant qu’administrateur.

1. Dans le rail latéral de navigation globale, sélectionnez **Outils** > **Services cloud** > **Services cloud hérités** > **Adobe Campaign**, puis cliquez sur **Configurer maintenant**.

   ![Configurer Adobe Campaign](assets/configure-campaign-service.png)

1. Dans la boîte de dialogue, créez une configuration de service Campaign en saisissant un **Titre** et en cliquant sur **Créer**.

   ![Boîte de dialogue Configurer Campaign](assets/configure-campaign-dialog.png)

1. Une nouvelle fenêtre et boîte de dialogue s’ouvre pour modifier la configuration. Fournissez les informations requises.

   * **Nom d’utilisateur** : il s’agit de [l’opérateur du package d’intégration Adobe Campaign AEM créé à l’étape précédente.](#create-operator) Par défaut, celui-ci est `aemserver`.
   * **Mot de passe** : il s’agit du mot de passe pour [l’opérateur du package d’intégration Adobe Campaign AEM créé à l’étape précédente](#create-operator).
   * **Point de fin d’API** - Il s’agit de l’URL de l’instance Adobe Campaign.

   ![Configurer Adobe Campaign dans AEM](assets/configure-campaign.png)

1. Sélectionnez **Se connecter à Adobe Campaign** pour vérifier la connexion, puis cliquez sur **OK**.

AEM peut désormais communiquer avec Adobe Campaign.

>[!NOTE]
>
>Assurez-vous que votre serveur Adobe Campaign est accessible via Internet. AEM as a Cloud Service ne peut pas accéder aux réseaux privés.

## Configurer AEM Externalizer {#externalizer}

Externalizer est un service OSGi d’AEM qui transforme un chemin d’accès aux ressources en URL externe et absolue, ce qui est nécessaire pour qu’AEM diffuse du contenu que Campaign peut utiliser.

1. Connectez-vous à l’instance de création AEM en tant qu’administrateur.
1. Confirmez l’instance de publication dans la configuration d’Externalizer en consultant l’export de statut des services OSGi dans la [console de développement](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=fr#services-osgi).
1. Si elle n’est pas correcte, apportez les modifications nécessaires dans le référentiel Git de l’instance correspondante, puis [déployez la configuration à l’aide de Cloud Manager](/help/implementing/cloud-manager/deploy-code.md).

```text
Service 3310 - [com.day.cq.commons.externalizer] (pid: com.day.cq.commons.impl.externalizerImpl)",
"  from Bundle 420 - Day Communique 5 Commons Library (com.day.cq.cq-commons), version 5.12.16",
"    component.id: 2149",
"    component.name: com.day.cq.commons.impl.externalizerImpl",
"    externalizer.contextpath: ",
"    externalizer.domains: [local https://author-p17558-e33255-cmstg.adobeaemcloud.com, author https://author-p17558-e33255-cmstg.adobeaemcloud.com,
     publish https://publish-p17558-e33255-cmstg.adobeaemcloud.com]",
"    externalizer.encodedpath: false",
"    externalizer.host: ",
"    feature-origins: [com.day.cq:cq-quickstart:slingosgifeature:cq-platform-model_quickstart_author:6.6.0-V23085]",
"    service.bundleid: 420",
"    service.description: Creates absolute URLs",
"    service.scope: bundle",
"    service.vendor: Adobe Systems Incorporated",
```

>[!NOTE]
>
>L’instance de publication doit être accessible à partir du serveur Adobe Campaign.

## Configurer l’utilisateur campaign-remote dans AEM {#configure-user}

Pour que Campaign puisse communiquer avec AEM, vous devez définir un mot de passe pour l’utilisateur `campaign-remote` dans AEM.

1. Connectez-vous à AEM en tant qu’administrateur.
1. Dans la console de navigation principale, cliquez sur **Outils** dans le rail de gauche.
1. Cliquez ensuite sur **Sécurité** -> **Utilisateurs** pour ouvrir la console d’administration des utilisateurs.
1. Recherchez l’utilisateur `campaign-remote`.
1. Sélectionnez l’utilisateur `campaign-remote` et cliquez sur **Propriétés** pour le modifier.
1. Dans la fenêtre **Modifier les paramètres utilisateur**, cliquez sur **Modifier le mot de passe**.
1. Saisissez un nouveau mot de passe pour l’utilisateur et notez-le dans un emplacement sécurisé en vue d’une utilisation ultérieure.
1. Cliquez sur **Enregistrer** pour enregistrer le changement de mot de passe.
1. Cliquez sur **Enregistrer et fermer** pour enregistrer les modifications apportées à l’utilisateur `campaign-remote`.

## Configurer le compte externe AEM dans Campaign {#acc-setup}

Lors de [l’installation du package **Intégration AEM** dans Campaign,](#install-package) un compte externe est créé pour AEM. En configurant ce compte externe, Adobe Campaign peut se connecter à AEM as a Cloud Service, ce qui permet une communication bidirectionnelle entre les solutions.

1. Connectez-vous à Adobe Campaign en tant qu’administrateur à l’aide de la console cliente.

1. Sélectionnez **Outils** -> **Explorateur** dans la barre de menus.

1. Dans l’explorateur, accédez au nœud **Administration** > **Plateforme** > **Comptes externes**.

   ![Comptes externes](assets/external-accounts.png)

1. Recherchez le compte AEM externe. Il possède par défaut les valeurs suivantes :

   * **Type** : AEM
   * **Libellé** : Instance AEM
   * **Nom interne** : aemInstance

1. Sous l’onglet **Général** de ce compte, saisissez les informations utilisateur que vous avez définies lors de l’étape [Définir le mot de passe de l’utilisateur campaign-remote](#set-campaign-remote-password).

   * **Serveur** : adresse du serveur de création AEM
      * Le serveur de création AEM doit être accessible à partir de l’instance de serveur Adobe Campaign Classic.
      * Assurez-vous que l’adresse du serveur ne se termine **pas** par une barre oblique.
   * **Compte** : par défaut, il s’agit de l’utilisateur `campaign-remote` défini dans AEM lors de l’étape [Définir le mot de passe de l’utilisateur campaign-remote](#set-campaign-remote-password).
   * **Mot de passe** : il est identique à celui défini dans AEM pour l’utilisateur `campaign-remote` lors de l’étape [Définir le mot de passe de l’utilisateur campaign-remote](#set-campaign-remote-password).

1. Cochez la case **Activé**.

1. Cliquez sur **Enregistrer**.

Adobe Campaign peut désormais communiquer avec AEM.

## Étapes suivantes {#next-steps}

Adobe Campaign Classic et AEM as a Cloud Service sont maintenant configurés, ici s’achève donc l’intégration.

Ne vous arrêtez pas en si bon chemin et apprenez à créer une newsletter dans Adobe Experience Manager à l’aide de [ce document](/help/sites-cloud/authoring/campaign/creating-newsletters.md).
