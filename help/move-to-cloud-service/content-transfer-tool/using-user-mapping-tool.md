---
title: Utilisation de l’outil de mappage des utilisateurs
description: Utilisation de l’outil de mappage des utilisateurs
translation-type: tm+mt
source-git-commit: 664c278494a5ac88362b994946060ab3baa846d8
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 7%

---


# Utilisation de l’outil de mappage utilisateur {#user-mapping-tool}

## Présentation {#overview}

Dans le parcours de transition de l’AEM en tant que Cloud Service, vous devez déplacer les utilisateurs et les groupes de votre système AEM existant vers l’AEM en tant que Cloud Service. Pour ce faire, utilisez l’outil de transfert de contenu.

L’un des changements majeurs apportés à AEM as a Cloud Service est l’utilisation entièrement intégrée des Adobe ID pour l’accès au niveau création.  Pour ce faire, il est nécessaire d’utiliser Adobe Admin Console pour la gestion des utilisateurs et des groupes d’utilisateurs. Les informations utilisateur-profil sont centralisées dans l’Adobe Identity Management System (IMS), qui permet l’authentification unique dans toutes les applications de cloud d’Adobes. Pour plus de détails, reportez-vous à Identity Management. En raison de cette modification, les utilisateurs et groupes existants doivent être mappés à leurs ID IMS pour éviter que des utilisateurs et des groupes de duplicata ne soient associés à l’instance d’auteur du Cloud Service.

## Points importants {#important-considerations}

Il y a quelques cas exceptionnels à examiner. Les cas spécifiques suivants seront consignés et l’utilisateur ou le groupe en question ne sera pas mappé :

1. Si un utilisateur n’a pas d’adresse électronique dans le champ `profile/email` de son noeud jcr.

1. Si le système IMS ne contient aucun courrier électronique pour l’ID d’organisation utilisé (ou si l’ID IMS ne peut pas être récupéré pour une autre raison).

1. Si l’utilisateur est actuellement désactivé, il est traité de la même manière que s’il n’était pas désactivé.  Il sera mappé et migré comme normal et restera désactivé sur l’instance de cloud.

## Utilisation de l’outil de mappage des utilisateurs {#using-user-mapping-tool}

L’outil de mappage utilisateur utilise une API qui lui permet de rechercher les utilisateurs IMS par courrier électronique et de renvoyer leurs ID IMS. Cette API requiert que l’utilisateur crée un ID de client pour son organisation, une clé secrète client et un jeton Jeton d&#39;accès/porteur.

Procédez comme suit pour configurer ce paramètre :

1. Accédez à [Adobe Developer Console](https://console.adobe.io) à l&#39;aide de votre Adobe ID.
1. Créer un projet ou ouvrir un projet existant
1. Ajouter une API
1. Choisir l’API de gestion des utilisateurs
1. Création d’informations d’identification JWT
1. Générer une paire de clés ou Télécharger une clé publique (rsa n&#39;est pas bon)
1. Générez un jeton d&#39;accès (ou jeton JWT ou jeton porteur).
1. Enregistrez toutes ces informations (ID client, clé secrète client, ID de compte technique, adresse électronique du compte technique, ID d’organisation, Jeton d&#39;accès) dans un endroit sûr.