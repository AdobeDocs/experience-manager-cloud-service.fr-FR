---
title: Vérification du domaine
description: Vérification du domaine
translation-type: tm+mt
source-git-commit: d2a98cf340dc755407250a9a9649addb75ad87d2
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 100%

---


# Vérification du domaine {#verify-domain-name}

Un enregistrement TXT de DNS permet l’hébergement d’un domaine dans un service CDN. Le client doit créer un enregistrement TXT de DNS dans la zone qui permet à Cloud Manager de déployer le service CDN avec le domaine personnalisé et de l’associer au service d’arrière-plan. Cette association est entièrement contrôlée par le client et permet à Cloud Manager de diffuser du contenu du service vers un domaine. Cette autorisation peut être accordée et retirée. L’enregistrement TXT est spécifique au domaine et à l’environnement Cloud Manager.

1. Connectez-vous à votre hôte de domaine et consultez la section des enregistrements DNS.
1. Copiez et collez l’entrée TXT dans la zone DNS où se trouve votre domaine personnalisé, exactement comme elle apparaît. Si vous avez besoin d’un « nom » pour votre entrée, indiquez `@`.

>[!NOTE]
>Divers outils de recherche DNS tels que [DNS Lookup Tool](https://www.ultratools.com/tools/dnsLookup) et Google DoH peuvent être utilisés pour rechercher les entrées d’enregistrement TXT et déterminer si l’enregistrement TXT est manquant ou erroné.
