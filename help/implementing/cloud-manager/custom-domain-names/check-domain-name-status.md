---
title: Vérification de l’état du nom de domaine
description: Vérification de l’état du nom de domaine
translation-type: tm+mt
source-git-commit: ddee11fdfa8cadfcd63472fd3c94cd8af555c856
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 79%

---


# Vérification de l’état du nom de domaine {#check-status}

Vous pouvez déterminer si votre nom de domaine a bien été vérifié en cliquant sur l’icône État du nom de domaine dans le tableau Environnements sur la page Paramètres de domaine.

>[!NOTE]
>Cloud Manager déclenche automatiquement une vérification TXT lorsque vous sélectionnez Enregistrer à l’étape de vérification de l’assistant Ajout de domaine personnalisé. Pour les vérifications suivantes, vous devez sélectionner activement l’icône **Vérifier à nouveau** en regard de l’état.

Cloud Manager vérifie la propriété du domaine via la valeur TXT et affiche l’un des messages d’état suivants :

* **Échec de la vérification du domaine**
La valeur TXT est manquante ou des erreurs ont été détectées. Suivez les instructions et réessayez. Une fois prêt, vous devez sélectionner 
l’icône *Vérifier à nouveau* en face du statut.

* **Vérification du domaine en cours**
Vérification en cours. Ce statut s’affiche généralement une fois que vous avez sélectionné 
l’icône *Vérifier à nouveau* en face du statut.

* **Vérifié, échec du déploiement**
La vérification TXT a réussi. Cependant, le déploiement du CDN a échoué. Un représentant d’Adobe sera automatiquement averti.

* **Domaine vérifié et déployé**
Ce statut indique que votre nom de domaine personnalisé est prêt à être utilisé.
   >[!NOTE]
   >À ce stade, votre nom de domaine personnalisé est prêt à être testé et pointé vers le nom de domaine Cloud Manager. Voir [Configuration des paramètres DNS](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) pour en savoir plus.

* **Suppression**
La suppression du nom de domaine personnalisé est en cours.

* **Échec de la suppression**
La suppression du nom de domaine personnalisé a échoué. Vous devez réessayer. Consultez [Suppression d’un nom de domaine personnalisé](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) pour en savoir plus.


## Configurations CDN préexistantes pour les Listes autorisées IP {#pre-existing-cdn}

Les clients disposant d’environnements qui incluent des configurations CDN préexistantes pour les Listes autorisées IP, les certificats SSL ou les noms de domaine personnalisés voient le message suivant dans les pages de détails **Liste autorisée IP** et **Environnement**.

![](/help/implementing/cloud-manager/assets/ip-allow-list-1.png)

>[!NOTE]
>Pour afficher et gérer les configurations préexistantes, elles doivent être ajoutées via l’interface utilisateur, comme le montre la figure ci-dessous.

![](/help/implementing/cloud-manager/assets/ip-allow-list-2.png)
