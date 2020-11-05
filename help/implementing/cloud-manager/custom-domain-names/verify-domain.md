---
title: Vérification du domaine
description: Vérification du domaine
translation-type: tm+mt
source-git-commit: d2a98cf340dc755407250a9a9649addb75ad87d2
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# Vérification du domaine {#verify-domain-name}

Un enregistrement DNS TXT autorise l’hébergement d’un domaine dans un service CDN. Le client doit créer un enregistrement DNS TXT dans la zone qui autorise Cloud Manager à déployer le service CDN avec le domaine personnalisé et à l’associer au service principal. Cette association est entièrement sous le contrôle du client et autorise fortement Cloud Manager à diffuser du contenu du service vers un domaine. Cette autorisation peut être accordée et retirée. L’enregistrement TXT est spécifique au domaine et à l’environnement Cloud Manager.

1. Connectez-vous à votre hôte de domaine et consultez la section des enregistrements DNS.
1. Copiez et collez l’entrée TXT dans la zone DNS où se trouve votre domaine personnalisé, exactement comme elle s’affiche. Si vous avez besoin d&#39;un &quot;nom&quot; pour votre inscription, donnez-le `@`.

>[!NOTE]
>Divers outils de recherche DNS tels que l’outil [de recherche](https://www.ultratools.com/tools/dnsLookup)DNS, Google DoH peuvent être utilisés pour rechercher les entrées d’enregistrement TXT et déterminer si l’enregistrement TXT est manquant ou erroné.
