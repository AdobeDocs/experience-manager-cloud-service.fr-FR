---
title: Contrôle d’accès basé sur les attributs
description: Découvrez comment activer le contrôle d’accès basé sur les attributs pour définir des règles basées sur les métadonnées afin de définir le niveau d’accès aux ressources disponibles dans Content Hub
role: Admin
exl-id: 05f54b05-40b8-4a6c-af8f-5c3f7a2089d4
source-git-commit: 655f84593adb1199bcfc21cb54071feb3c8523c5
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 5%

---

# Contrôle d’accès basé sur les attributs {#attribute-based-access-control}

Le contrôle d’accès basé sur les attributs (ABAC) permet aux administrateurs Content Hub de définir des règles basées sur les métadonnées afin de définir le niveau d’accès aux ressources disponibles dans Content Hub.

Les administrateurs d’une organisation définissent des règles pour les groupes d’utilisateurs, qui sont mappés à un ID de groupe. Les règles sont un mélange d’opérateurs [logiques et de comparaison](#supported-rule-constructs) et les administrateurs peuvent définir autant de règles que nécessaire pour gérer l’accès aux ressources dans Content Hub.

Les règles sont basées sur des métadonnées et si les conditions définies dans la règle correspondent aux métadonnées de la ressource, la ressource est affichée au groupe d’utilisateurs. Content Hub analyse les métadonnées de la ressource, y compris les métadonnées personnalisées de toutes les ressources disponibles dans **Toutes les Assets** et **Collections** afin d’afficher les résultats aux groupes d’utilisateurs.

Par exemple, AUTORISER l’accès à un groupe d’utilisateurs avec un ID de groupe = 1011, lorsque les métadonnées de ressource correspondent à « Marque = Marque X » ET « Région = EMEA OU Amériques ». Content Hub affiche uniquement les ressources pour le groupe d’utilisateurs avec l’ID = 1011 où Marque = `Brand X` et Région = `EMEA` ou `Americas`.

Voici quelques-uns des principaux avantages du contrôle d’accès basé sur les attributs :

* Élimine la dépendance à la structure de dossiers pour les autorisations

* Permet aux administrateurs et administratrices de charger des ressources et de déterminer rétroactivement les structures d’autorisation

* Réduit le nombre de doublons - améliore l’intégrité des ressources. Des doublons sont nécessaires dans les autorisations basées sur des dossiers lorsqu’une même ressource est partagée avec différents groupes.

>[!VIDEO](https://video.tv.adobe.com/v/3475416/?captions=fre_fr&learn=on&enablevpops){transcript=true}

## Comment activer le contrôle d’accès basé sur les attributs ? {#enable-attribute-based-access-control}

Pour l’instant, vous ne pouvez pas créer de règles de contrôle d’accès basé sur les attributs vous-même à l’aide de l’interface utilisateur de Content Hub.

Cliquez sur **Télécharger la feuille de calcul** pour télécharger et définir des règles dans une feuille de calcul. Créez un ticket d’assistance pour Adobe et fournissez à Adobe les règles définies dans la feuille de calcul.

[!BADGE Télécharger la feuille de calcul]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/ABAC_Get_Started_Template.xlsx"}


Définissez des règles dans la feuille de calcul à l&#39;aide des instructions définies dans cet article.

<!--

>[!IMPORTANT]
>
> After defining the rules, navigate to the **Validation Errors** tab of the spreadsheet and click **Run ABAC Validations**. **All validations passed** message confirms that you can provide the defined rules to Adobe.

-->

## Exemple de cas d’utilisation de contrôle d’accès basé sur les attributs {#example-metadata-based-rules}

Pour prendre en charge un déploiement marketing à grande échelle, divers membres des équipes des différentes régions et marques doivent avoir accès aux ressources numériques. Chaque personnage a une portée spécifique basée sur la région et la marque. ABAC applique ces règles automatiquement au moyen des métadonnées des ressources. Le tableau suivant illustre les différents types de personnages pour ce cas d’utilisation et les règles appliquées :

| Personne | Rôle | Description du rôle | ID de groupe | Règle ABAC |
|---------------------|----------------|-----------------|------------|------------|
| John | Responsable marketing EMEA | Supervise l’exécution marketing pour toutes les marques dans la zone EMEA. Nécessite l’accès aux ressources approuvées pour toutes les marques destinées aux marchés EMEA. | group-emea-marketing | région = « EMEA » |
| Mike | Responsable marketing APAC | Supervise l’exécution marketing sur toutes les marques dans APAC. Nécessite l’accès aux ressources approuvées pour toutes les marques destinées aux marchés APAC. | group-apac-marketing | région = « APAC » |
| Sophie | Brand X Manager (EMEA) | Gère l’identité Brand X dans la zone EMEA. Ne doit afficher que le contenu approuvé par Brand X adapté aux marchés de la zone EMEA. | group-emea-brandx | région = « EMEA » et marque = « Brand X » |
| Tom | Brand Y Manager (APAC) | Gère l’identité de la marque Y dans APAC. Ne doit afficher que le contenu approuvé par la marque Y adapté aux marchés APAC. | group-apac-brandy | région = « APAC » et marque = « Marque Y » |

Grâce à ces règles, les administrateurs Content Hub disposent des éléments suivants :

* **Accès granulaire, basé sur des règles** : les utilisateurs voient uniquement les ressources pertinentes pour leur région et leur marque (aucune attribution d’autorisation manuelle).

* **Collaboration mondiale transparente** : les équipes régionales et de marque ont travaillé en parallèle sans conflits d’accès.

* **Autorisations évolutives et pérennes** : à mesure que de nouvelles régions ou marques sont ajoutées, les règles peuvent être mises à jour en fonction des métadonnées.

>[!IMPORTANT]
>
> Par défaut, tous les autres groupes d’utilisateurs, qui ne sont spécifiés par aucune règle dans la [&#x200B; feuille de calcul](#enable-attribute-based-access-control), se voient refuser l’accès. Si un utilisateur ou une utilisatrice ne fait partie d’aucun groupe pour lequel des règles ABAC sont définies, il ou elle ne peut accéder à aucune ressource. Si vous souhaitez que certains utilisateurs aient accès à toutes les ressources (par exemple, les administrateurs), un groupe doté d’un ID de groupe doit être mentionné dans la feuille de calcul avec les détails indiquant que ce groupe spécifique doit avoir accès à toutes les ressources et Adobe le configurera pour vous.


## Éléments de règle pris en charge {#supported-rule-constructs}

* **Opérateurs logiques** :
   * AND : toutes les conditions doivent être vraies
   * OR : au moins une condition doit être vraie
* **Opérateurs de comparaison** :
   * Est égal à (=) : vérifie si un attribut d’utilisateur ou de ressource correspond à une valeur
   * Est différent de (!=) : vérifie si un attribut d’utilisateur ou de ressource ne correspond pas à une valeur

Lorsque les champs de métadonnées des ressources contiennent des tableaux (par exemple, plusieurs régions ou balises), `Equals` fait référence à `contains` logique et `Not Equals` fait référence à `does not contain` logique.

Cela vous permet d’écrire des règles simples et expressives, telles que : ALLOW si region = emea ET assetType != prototype ET balises != confidentiel.

## Directives {#guidelines-attribute-based-access-control}

* Les règles ABAC s’appliquent uniquement aux ressources approuvées pour Content Hub. Pour plus d’informations, voir [&#x200B; Approuver Assets pour Content Hub &#x200B;](/help/assets/approve-assets-content-hub.md).

* Ne donnez pas de règles DENY, mais convertissez toujours DENY en règle ALLOW. Par exemple, les `ALLOW if region = <user-region> DENY if assetType = prototype AND confidential = yes` peuvent être convertis en `ALLOW if region = <user-region> AND (assetType != prototype OR confidential != yes)`.

* Les règles ABAC sont appliquées aux groupes d’utilisateurs à l’aide de l’identifiant de groupe IMS, disponible dans Admin Console.


* Vous pouvez définir la [cible d’approbation](/help/assets/approve-assets-content-hub.md#set-approval-target) pour les ressources à l’aide de l’environnement de création AEM as a Cloud Service. Les règles ABAC sont appliquées aux ressources approuvées avec une cible d’approbation = `Content Hub`, car une cible d’approbation = `Delivery` concerne les ressources disponibles pour `Delivery` + `Content Hub`. Assets marqué comme Cible d’approbation = `Delivery` est visible par tous dans le hub de contenu.

* Vérifiez que les schémas de métadonnées utilisés dans les règles ABAC sont correctement définis et disponibles dans AEM. Fournissez le chemin d’accès complet du ou des schémas de métadonnées dans AEM qui définissent les propriétés référencées dans les règles ABAC. Vous pouvez éventuellement créer un dossier de test avec quelques exemples de ressources dont les valeurs de métadonnées correspondent aux conditions ABAC. Cela permet de vérifier le comportement des règles et d’évaluer l’accès avec précision.

* Saisissez l’intention commerciale de la règle dans le commentaire, que la condition soit correctement écrite ou non, car l’intention nous aide à valider et à corriger la logique, si nécessaire.

* Les fichiers PDF de licence, qui sont définis pour DRM, doivent être visibles par tous, afin que les utilisateurs puissent les voir lorsqu’ils téléchargent la ressource avec licence.
