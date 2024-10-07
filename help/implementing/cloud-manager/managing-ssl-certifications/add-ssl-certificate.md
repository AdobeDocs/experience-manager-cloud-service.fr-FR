---
title: Ajout d’un certificat SSL
description: Découvrez comment ajouter votre propre certificat SSL ou et Adobe un certificat DV (Domain Validation) géré par à l’aide des outils en libre-service Cloud Manager.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 493c5729c3107f151685a243006b17196b74c1bd
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 7%

---


# Ajout d’un certificat SSL {#add-ssl-cert}

Découvrez comment ajouter votre propre certificat SSL ou un certificat DV (Domain Validation) géré par Adobe à l’aide de Cloud

>[!TIP]
>
>La configuration d’un certificat peut prendre quelques jours. Par conséquent, Adobe recommande que si vous fournissez votre propre certificat, celui-ci soit configuré bien avant toute date limite ou date de mise en service.

## Conditions préalables {#prerequisites}

* Un utilisateur doit être membre du rôle **Propriétaire de l’entreprise** ou **Responsable de déploiement** pour ajouter un certificat.
* Si vous installez votre propre certificat, veillez à consulter les **exigences de certificat** dans [Introduction à la gestion des certificats SSL.](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements)

## Ajout d’un certificat SSL {#add-certificate}

1. Connectez-vous à Cloud Manager à l’adresse [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) et sélectionnez le programme approprié.
1. Sur la console **[Mes programmes](/help/implementing/cloud-manager/navigation.md#my-programs)**, sélectionnez le programme.
1. Dans le coin supérieur gauche de la page, cliquez sur ![Icône Afficher le menu](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) pour afficher le menu latéral.
1. Sous l’en-tête **Services**, cliquez sur ![Icône de verrouillage](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **Certificats SSL**.

   ![Ajout d’un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Dans le coin supérieur droit de la page Certificats SSL, cliquez sur **Ajouter un certificat SSL**.

1. Dans la boîte de dialogue **Ajouter un certificat SSL**, en fonction de [votre cas d’utilisation particulier](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md), effectuez l’une des opérations suivantes :

   | | Cas d’utilisation | Étapes |
   | --- | --- | --- |
   | 1 | **Ajout d’un certificat géré par Adobe (DV)** | **Pour ajouter un certificat géré par Adobe (DV) :**<br> a. Dans la boîte de dialogue **Ajouter un certificat SSL**, sélectionnez le type de certificat **Adobe géré (DV)**.<br>![Ajoutez un certificat DV](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. Dans le champ **Certificate name** , saisissez un nom à associer au certificat.<br>c. Dans la liste déroulante **Sélectionner des domaines**, sélectionnez un ou plusieurs domaines à associer au certificat DV.<br> Aucun domaine à sélectionner ? Si tel est le cas, cela signifie que vous devez ajouter un domaine personnalisé. Voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). Lorsque vous avez terminé d’ajouter un nom de domaine personnalisé, revenez à cette rubrique et recommencez à l’étape 1.<br>d. Passez à l’étape 7. |
   | 2 | **Ajout d’un certificat géré par le client (OV/EV)** | **Pour ajouter un certificat géré par le client (OV/EV) :**<br> a. Dans la boîte de dialogue **Ajouter un certificat SSL**, sélectionnez le type de certificat **Customer managed (OV/EV)**.<br>b. Dans le champ **Certificate name** , saisissez un nom pour votre certificat. Ce champ est fourni à titre d’information uniquement et peut être n’importe quel nom qui vous aide à référencer facilement votre certificat.<br>c. Dans les champs **Certificate**, **Private key** et **Certificate chain** , collez les valeurs requises dans leurs champs respectifs.<br>![Boîte de dialogue Ajouter un certificat SSL](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>Toutes les erreurs détectées dans les valeurs s’affichent. Avant de pouvoir enregistrer votre certificat, vous devez corriger toutes les erreurs. Pour en savoir plus sur la résolution des erreurs courantes, voir [erreurs de certificat](#certificate-errors) .<br>d. Passez à l’étape 7. |

1. Dans l’angle inférieur droit de la boîte de dialogue, cliquez sur **Enregistrer**.

Une fois le certificat émis, il s’affiche avec une coche verte dans la table **SSL Certificates**.

Vous avez maintenant ajouté un certificat SSL fonctionnel pour votre projet. Cette étape est souvent la première à configurer un nom de domaine personnalisé.

* Pour configurer un nom de domaine personnalisé, voir [Ajout d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md).
* Pour en savoir plus sur la mise à jour et la gestion de vos certificats SSL dans Cloud Manager, voir [Gestion des certificats SSL](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

>[!TIP]
>
>Si vous rencontrez des problèmes lors de l&#39;ajout ou de la gestion de vos certificats, consultez le document [Dépannage des erreurs de certificat SSL.](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md)
