---
title: Obtention d’un certificat SSL - Gestion des certificats SSL
description: Obtention d’un certificat SSL - Gestion des certificats SSL
translation-type: tm+mt
source-git-commit: b0162640b6d85291aba9c926138f39a0433c0a6e
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# Obtention d’un certificat SSL {#getting-an-ssl-certificate}

Les entreprises utilisent des certificats SSL pour sécuriser leurs sites Web et permettre à leurs clients de leur faire confiance. Pour utiliser le protocole SSL, un serveur Web requiert l’utilisation d’un certificat SSL. Cloud Manager ne fournit pas de certificats SSL ni de clés privées. Ils doivent être obtenus auprès des autorités de certification (AC).

Lorsqu&#39;une entité demande un certificat à une autorité de certification (AC), l&#39;AC termine un processus de vérification. Cela peut aller de la vérification du contrôle des noms de domaine à la collecte des documents d&#39;enregistrement des sociétés et des contrats d&#39;abonnés.

Une fois les informations d&#39;une entité vérifiées, l&#39;AC signera sa clé publique à l&#39;aide de la clé privée de l&#39;AC. Étant donné que toutes les principales autorités de certificats possèdent des certificats racine dans les navigateurs Web, le certificat de l’entité est lié par une *chaîne de confiance* et le navigateur Web le reconnaît comme un certificat approuvé.

