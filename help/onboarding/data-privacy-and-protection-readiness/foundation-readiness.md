---
title: Règlement sur la protection des données et la confidentialité des données - Adobe Experience Manager en tant que Cloud Service Foundation Readiness
description: 'Découvrez Adobe Experience Manager en tant que support de la Fondation Cloud Service pour les différentes réglementations sur la protection des données et la confidentialité des données ; y compris le règlement général de l''UE sur la protection des données (RGPD), la loi sur la protection des renseignements personnels des consommateurs de Californie et la façon de se conformer lors de la mise en oeuvre d''une nouvelle AEM en tant que projet Cloud Service. '
translation-type: tm+mt
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 32%

---


# Adobe Experience Manager en tant que Cloud Service Foundation Readiness for Data Protection and Data Privacy Regulations {#aem-foundation-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Le contenu de ce document ne constitue pas un conseil juridique et ne se substitue pas à un conseil juridique.
>
>Veuillez consulter le service juridique de votre société pour obtenir des conseils sur les réglementations relatives à la protection des données et à la confidentialité des données.

>[!NOTE]
>
>Pour plus d&#39;informations sur la réponse des Adobes aux questions de confidentialité et sur ce que cela signifie pour vous en tant que client Adobe, consultez le Centre [de confidentialité des](https://www.adobe.com/privacy.html)Adobes.

## Prise en charge de la protection et de la confidentialité des données de AEM Foundation {#aem-foundation-data-privacy-and-protection-support}

Au niveau de AEM Foundation, les données personnelles stockées sont conservées dans le Profil utilisateur. Par conséquent, les informations contenues dans cet article portent principalement sur la manière d’accéder aux profils d’utilisateurs et de les supprimer, afin de répondre respectivement aux demandes d’accès et de suppression.

## Accès à un profil utilisateur {#accessing-a-user-profile}

### Étapes manuelles {#manual-steps}

1. Ouvrez la console d’administration utilisateur en accédant à **[!UICONTROL Outils - Sécurité - Utilisateurs]** ou en accédant directement à `https://<serveraddress>:<serverport>/security/users.html`

<!--
   ![useradmin2](assets/useradmin2.png)
-->

1. Recherchez ensuite l’utilisateur en question en saisissant le nom dans la barre de recherche située en haut de la page :

   ![rechercher un compte](assets/dpp-foundation-01.png)

1. Enfin, ouvrez le profil utilisateur en cliquant dessus, puis consultez les informations sous l’onglet **[!UICONTROL Détails]**.

   ![profil utilisateur](assets/dpp-foundation-02.png)

### API HTTP  {#http-api}

Comme mentionné, Adobe fournit des API pour accéder aux données utilisateur, afin de faciliter l’automatisation. Il existe plusieurs types d’API que vous pouvez utiliser :

**API UserProperties**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**API Sling**

**Découverte du répertoire de base (home) des utilisateurs :**

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**Récupération des données utilisateur:**

Utilisation du chemin d’accès au noeud à partir de la propriété home de la charge utile JSON renvoyée par la commande ci-dessus :

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## Désactivation d’un utilisateur et suppression des profils associés {#disabling-a-user-and-deleting-the-associated-profiles}

### Désactivation d’un utilisateur {#disable-user}

1. Ouvrez la console Administration utilisateur et recherchez l’utilisateur en question, comme décrit ci-dessus.
2. Survolez l’utilisateur avec le curseur, puis cliquez sur l’icône sélectionnée. Le profil devient gris pour indiquer qu’il est sélectionné.

3. Press the **Disable** button in the upper menu to disable the user:

   ![désactiver le compte](assets/dpp-foundation-03.png)

4. Enfin, confirmez l&#39;action.

   L’interface utilisateur indique ensuite que le compte utilisateur a été désactivé en grincant et en ajoutant un verrou à la carte de profil :

   ![compte désactivé](assets/dpp-foundation-04.png)

### Suppression des informations d’un profil utilisateur {#delete-user-profile-information}

>[!NOTE]
>
>Pour AEM en tant que Cloud Service, il n’existe aucune procédure manuelle disponible dans l’interface utilisateur pour la suppression d’un profil utilisateur, car CRXDE n’est pas accessible.

### API HTTP  {#http-api-1}

Les procédures suivantes utilisent l’outil de ligne de commande `curl` pour illustrer comment désactiver l’utilisateur **[!UICONTROL cavery]** `userId` et supprimer ses profils disponibles à l’emplacement par défaut.

**Découverte du répertoire de base (home) des utilisateurs :**

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

**Désactivation de l’utilisateur:**

Utilisation du chemin d’accès au noeud à partir de la propriété home de la charge utile JSON renvoyée par la commande ci-dessus :

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (Data Privacy in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

**Suppression du ou des profils utilisateur**

Utilisation du chemin d’accès au noeud à partir de la propriété home de la charge utile JSON renvoyée par la commande de détection de compte et des emplacements de noeud de profil prêts à l’emploi connus :

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
