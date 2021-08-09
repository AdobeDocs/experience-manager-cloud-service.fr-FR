---
title: Obtention d’un certificat SSL – Gestion des certificats SSL
description: Obtention d’un certificat SSL – Gestion des certificats SSL
exl-id: a3a247e5-164a-4c9c-aeed-bde882635e6f
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: ht
source-wordcount: '253'
ht-degree: 100%

---

# Obtention d’un certificat SSL {#getting-an-ssl-certificate}

Les entreprises utilisent des certificats SSL pour sécuriser leurs sites web et permettre à leurs clients de leur faire confiance. Pour utiliser le protocole SSL, un serveur web nécessite un certificat SSL. Cloud Manager ne fournit pas de certificats SSL ni de clés privées. Ces éléments doivent être obtenus auprès des autorités de certification (AC).

Lorsqu’une entité demande un certificat à une autorité de certification, celle-ci effectue un processus de vérification. Ce processus peut aller de la vérification du contrôle des noms de domaine jusqu’à la collecte de documents d’immatriculation des sociétés et de contrats d’abonnés. Une fois les informations d’une entité vérifiées, l’autorité de certification signe la clé publique à l’aide de sa clé privée. Étant donné que la totalité des principales autorités de certification possèdent des certificats racine dans les navigateurs web, le certificat de l’entité est lié par une *chaîne de confiance* et le navigateur web le reconnaît comme un certificat approuvé.

>[!NOTE]
>AEM as a Cloud Service n’accepte que les certificats OV (validation d’organisation) ou EV (validation étendue). Les certificats DV (Validation de domaine) ou auto-signés ne sont pas acceptés. Les certificats OV et EV apportent aux utilisateurs des informations supplémentaires, validées par l’autorité de certification. Ils peuvent les utiliser pour déterminer si le propriétaire d’un site web, l’expéditeur d’un courrier électronique ou le signataire numérique d’un code exécutable ou de documents PDF est fiable. Les certificats DV sont courants et peu coûteux. Cependant, ils n’autorisent pas la vérification de la propriété.
>De plus, tout certificat doit être de type TLS X.509, délivré par une autorité de certification approuvée (CA) et doté d’une clé privée RSA 2 048 bits correspondante.
