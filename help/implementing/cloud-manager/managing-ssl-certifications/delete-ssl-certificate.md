---
title: Suppression d’un certificat SSL – Gestion des certificats SSL
description: Suppression d’un certificat SSL – Gestion des certificats SSL
translation-type: tm+mt
source-git-commit: 99eb33c3c42094f787d853871aee3a3607856316
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 100%

---


# Suppression d’un certificat SSL {#deleting-an-ssl-certificate}

>[!IMPORTANT]
>La suppression de certificats de Cloud Manager est une action permanente qui ne peut pas être annulée. Il est recommandé d’enregistrer les fichiers SSL nécessaires localement avant de les supprimer dans l’interface utilisateur de Cloud Manager.

Un utilisateur doit avoir le rôle Propriétaire de l’entreprise ou Responsable du déploiement pour pouvoir supprimer un certificat SSL dans Cloud Manager. Cloud Manager ne vous permet pas de supprimer un certificat SSL associé à un ou plusieurs domaines. Tous les domaines associés doivent être supprimés avant de supprimer le certificat SSL. Consultez [Suppression d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) pour en savoir plus.

Procédez comme suit pour supprimer un certificat SSL :

1. Accédez à l’écran **Certificats SSL** à partir de la page **Environnements**.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)
1. Identifiez la ligne où figure le nom du certificat SSL que vous souhaitez supprimer.
1. Sélectionnez le menu **...** à l’extrémité droite de la ligne.
1. Sélectionnez **Supprimer**.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete01.png)
1. Confirmez votre envoi à partir de la boîte de dialogue **Supprimer le certificat SSL**.
