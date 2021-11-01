---
title: Ajout d’un nom de domaine personnalisé
description: Ajout d’un nom de domaine personnalisé
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 98c137645351c86da8680a31b4929c588863a981
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 81%

---

# Ajout d’un nom de domaine personnalisé {#adding-cdn}

Un utilisateur doit être un propriétaire d’entreprise ou un responsable du déploiement pour pouvoir ajouter un nom de domaine personnalisé dans Cloud Manager.

Les étapes suivantes doivent être effectuées comme indiqué dans le tableau ci-dessous :

| Étape |  | Responsabilité | En savoir plus |
|--- |--- |--- |---|
| Ajout d’un certificat SLL | Ajout d’un certificat SLL | Client | [Ajout d’un certificat SSL](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate.html?lang=en) |
| Vérification de domaine | Ajout d’un enregistrement TXT | Client | [Ajout d’un enregistrement TXT](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/add-text-record.html?lang=en) |
| Vérification du domaine |  | Client |  |
|  | État : Échec de vérification du domaine | Client | [Vérification de l’état du nom de domaine](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-domain-name-status.html?lang=en) |
|  | État : Vérifié, Échec du déploiement | Contact représentant Adobe | [Vérification de l’état du nom de domaine](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-domain-name-status.html?lang=en) |
| Ajout d’enregistrements DNS pointant vers AEM as a Cloud Service en ajoutant des enregistrements CNAME ou APEX | Configuration des paramètres DNS | Client | [Configuration des paramètres DNS](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/configure-dns-settings.html?lang=en) |
| Vérification du statut des enregistrements DNS |  | Client | [Vérification du statut de l’enregistrement DNS](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-dns-record-status.html?lang=en) |
|  | État : Statut DNS non détecté | Client | [Vérification du statut de l’enregistrement DNS](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-dns-record-status.html?lang=en) |
|  | État : Le DNS ne se résout pas correctement | Client |  |


## Points importants {#important-considerations}

* Avant d’ajouter un nom de domaine personnalisé, un certificat SSL valide contenant le nom de domaine personnalisé doit être installé sur votre programme. Consultez la section [Ajout d’un certificat SSL](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) pour en savoir plus.

* Les noms de domaine ne peuvent pas être ajoutés aux environnements tant qu’un pipeline en cours d’exécution est attaché à ces environnements.

* Il n’est possible d’ajouter qu’un seul nom de domaine à la fois. Les domaines personnalisés côté auteur ne sont pas pris en charge.

* AEM as a Cloud Service ne prend pas en charge les domaines génériques.

* Chaque environnement Cloud Manager peut héberger jusqu’à 500 domaines personnalisés.

* Le même nom de domaine ne peut pas être utilisé sur plusieurs environnements.

## Ajout d’un nom de domaine personnalisé à partir de la page Paramètres de domaine {#adding-cdn-settings}

Suivez les étapes ci-dessous pour ajouter un nom de domaine personnalisé à partir de la page Paramètres de domaine :

1. Accédez à l’écran **Environnements** à partir de la page **Aperçu**.

1. Cliquez sur **Paramètres de domaine** dans le menu de navigation de gauche.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Cliquez sur le bouton **Ajouter le domaine** pour ouvrir la boîte de dialogue **Ajouter le nom de domaine**.

   ![](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Entrez le nom de domaine personnalisé dans **Nom de domaine**.

   >[!NOTE]
   >Vous ne devez pas inclure `http://`, `https://` ni d’espace lors de la saisie dans votre domaine.

1. Sélectionnez l’**environnement** dont le service de publication sera associé au nom de domaine.

1. Sélectionnez le service **Publier** ou **Aperçu**.

   >[!NOTE]
   >Les noms de domaine personnalisés sont désormais pris en charge dans Cloud Manager pour les programmes Sites, pour les services de publication et d’aperçu. Chaque environnement Cloud Manager peut héberger jusqu’à 500 domaines personnalisés. Pour en savoir plus sur le service d’aperçu, voir [Service Aperçu](/help/implementing/cloud-manager/manage-environments.md#preview-service).

1. Sélectionnez le **certificat SSL du domaine** dans la liste déroulante et sélectionnez **Continuer**.

1. La boîte de dialogue **Ajouter le nom de domaine** s’affiche. Vous accédez alors à l’écran de vérification du nom de domaine pour votre environnement. Consultez [Ajout d’un enregistrement TXT](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) pour en savoir plus.

   Suivez les instructions fournies pour prouver la propriété du domaine de votre environnement :

1. Cliquez sur **Créer**.
1. Le déploiement CDN nécessite un certificat SSL valide et une vérification TXT réussie. Cela est indiqué par l’état **Vérifié et déployé**.
Accédez à [Vérification de l’état du nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour en savoir plus sur les différents états et sur l’adressage.

   >[!NOTE]
   >Le contrôle du DNS peut prendre jusqu’à quelques heures en raison des retards de propagation de DNS. Cloud Manager vérifie la propriété et met à jour l’état visible dans le tableau des paramètres de domaine. Pour plus d’informations, voir Vérification de l’état du nom de domaine.

## Ajout d’un nom de domaine personnalisé à partir de la page Environnements {#adding-cdn-environments}

1. Accédez à la page Détails de l’environnement pour l’environnement qui vous intéresse.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Utilisez les champs d’entrée situés en haut du tableau Noms de domaine pour envoyer le nom de domaine personnalisé et sélectionnez le certificat SSL dans la liste déroulante. Cliquez sur **+ Ajouter**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Vérifiez les champs de la boîte de dialogue **Ajouter le nom de domaine** et cliquez sur **Continuer**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >N’incluez pas `http://`, `https://` ni d’espace lors de la saisie dans votre domaine.

1. L’écran Vérification du nom de domaine de votre environnement s’affiche.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   Consultez [Vérification du domaine](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) pour en savoir plus. Suivez les instructions fournies pour prouver la propriété du domaine de votre environnement.

1. Cliquez sur **Créer**.

1. Le déploiement Custom Domain Name nécessite un certificat SSL valide et une vérification TXT réussie. Cela est indiqué par l’état **Vérifié et déployé**.

À ce stade, votre nom de domaine personnalisé est prêt pour le test et un `CNAME` pour pointer vers celui-ci. Reportez-vous à la section [État du nom de domaine](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) pour en savoir plus sur les différents états et sur la façon de traiter.

>[!NOTE]
>Le contrôle du DNS peut prendre jusqu’à quelques heures en raison des retards de propagation de DNS. Cloud Manager vérifie la propriété et met à jour l’état visible dans le tableau des paramètres de domaine. Voir Vérification de l’état du nom de domaine pour en savoir plus.
