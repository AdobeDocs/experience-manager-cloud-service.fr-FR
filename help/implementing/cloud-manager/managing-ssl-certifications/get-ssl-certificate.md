---
title: Obtention d’un certificat SSL - Gestion des certificats SSL
description: Obtention d’un certificat SSL - Gestion des certificats SSL
translation-type: tm+mt
source-git-commit: 40119f7b3bdf36af668b79afbcb2802a0b2a6033
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Obtention d’un certificat SSL {#getting-an-ssl-certificate}

Les entreprises utilisent des certificats SSL pour sécuriser leurs sites Web et permettre à leurs clients de leur faire confiance. Pour utiliser le protocole SSL, un serveur Web requiert l’utilisation d’un certificat SSL. Cloud Manager ne fournit pas de certificats SSL ni de clés privées. Ils doivent être obtenus auprès des autorités de certification (AC).

Lorsqu&#39;une entité demande un certificat à une autorité de certification, l&#39;autorité de certification termine un processus de vérification. Cela peut aller de la vérification du contrôle des noms de domaine à la collecte des documents d&#39;enregistrement des sociétés et des contrats d&#39;abonnés. Une fois les informations d&#39;une entité vérifiées, l&#39;AC signera sa clé publique à l&#39;aide de la clé privée de l&#39;AC. Étant donné que toutes les principales autorités de certificats possèdent des certificats racine dans les navigateurs Web, le certificat de l&#39;entité est lié par une *chaîne de confiance* et le navigateur Web le reconnaît comme un certificat approuvé.

>[!NOTE]
>aem en tant que Cloud Service n&#39;acceptera que les certificats OV(validation d&#39;organisation) ou EV(validation étendue). Les certificats DV (Validation de domaine) ou auto-signés ne seront pas acceptés. Les certificats OV et EV fournissent aux utilisateurs des informations supplémentaires validées par l’autorité de certification qu’ils peuvent utiliser pour déterminer si le propriétaire d’un site Web, l’expéditeur d’un courrier électronique ou le signataire numérique d’un code exécutable ou de documents PDF est fiable. Les certificats DV sont courants et peu coûteux. Cependant, elles n&#39;autorisent pas la vérification de la propriété.
>En outre, tout certificat doit être un certificat TLS X.509 d’une autorité de certification approuvée avec une clé privée RSA 2 048 bits correspondante.

