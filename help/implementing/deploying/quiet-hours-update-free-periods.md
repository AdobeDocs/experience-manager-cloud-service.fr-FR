---
title: Heures calmes et mettre à jour les périodes libres
description: Découvrez comment minimiser l’impact opérationnel des mises à jour automatiques d’AEM as a Cloud Service en utilisant les heures creuses et les périodes sans mise à jour.
feature: Deploying
role: Admin
badge: label="Disponibilité limitée" type="Positive"
exl-id: 54f86a58-eb56-43e6-ab51-7af7466a2d40
source-git-commit: aec58ceffbbc6c7e2921c471d608ed3c381fe2e4
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Heures calmes et Mettre à jour les périodes libres {#quiet-hours-update-free-periods}

>[!NOTE]
>Cette fonctionnalité sera disponible en tant que fonctionnalité **à disponibilité limitée** à partir du 25 septembre. Envoyez un e-mail à [aemcs-update-free@adobe.com](mailto:aemcs-update-free@adobe.com) pour activer la fonctionnalité dans vos programmes.

>[!WARNING]
>Vous ne pouvez utiliser les fonctions Heures calmes et Mettre à jour les périodes libres qu’après avoir intégré les [ Mises à jour de maintenance automatiques ](/help/implementing/deploying/aem-version-updates.md).

Les [mises à jour de maintenance automatique](/help/implementing/deploying/aem-version-updates.md) d’AEM as a Cloud Service garantissent la sécurité de vos instances et les mettent à jour avec les dernières versions de maintenance. Cela dit, dans certains cas (comme les événements de mise en production), vous devrez peut-être « protéger » ces heures de travail critiques contre d’éventuelles perturbations. Ainsi, AEM as a Cloud Service offre la possibilité de définir une période pendant laquelle les mises à jour automatiques ne se produisent pas pour vos programmes en cours.

Vous pouvez configurer ces périodes à l’aide de deux options de planification :

* **Heures calmes** - Vous pouvez définir un intervalle de temps quotidien (jusqu’à 8 heures) où aucune mise à jour n’aura lieu.
* **Mettre à jour les périodes libres** - Vous pouvez définir une période de 7 jours pendant laquelle aucune mise à jour n’aura lieu. Vous pouvez avoir jusqu’à trois périodes de mise à jour gratuite sur une période de 12 mois.

Les fonctionnalités de mise à jour des périodes libres et des heures creuses sont configurées « par programme ».

De plus, pour plus d’informations sur les périodes de maintenance automatique d’AEM as a Cloud Service planifiées, reportez-vous à la page [Feuille de route des versions d’Experience Manager](https://experienceleague.adobe.com/fr/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

## Heures calmes {#quiet-hours}

Grâce à la fonction Heures calmes, vous pouvez définir une fenêtre temporelle pendant la journée sans mise à jour automatique. Toutes les mises à jour de maintenance seront effectuées en dehors de la période configurée. Si, par exemple, une mise à jour est planifiée pendant les heures calmes spécifiées, elle démarre automatiquement après la fin de l’intervalle des heures calmes. L’intervalle configuré ne peut pas dépasser 8 heures, de sorte que les mises à jour puissent toujours avoir lieu tous les jours.

Vous pouvez définir ces heures d’inactivité **par programme** en utilisant votre fuseau horaire local.

### Configuration de l’intervalle d’heures creuses {#configure-quiet-hours}

L’intervalle des heures creuses peut être configuré à l’aide de l’interface d’AEM Cloud Manager comme suit :

Accédez à **Activités > Mises à jour automatiques > Options de mise à jour**.

![Configuration](assets/main-config.png)

1. Assurez-vous que l’option **Empêcher les mises à jour automatiques pendant des heures spécifiques** est activée.
2. Cliquez sur **Modifier**.
3. Définissez l’intervalle d’heures creuses dans la fenêtre de configuration.

![Configuration des heures calmes](assets/quiet-hours.png)

Une fois définies, vos heures de début et de fin spécifiées s’appliqueront à chaque jour calendaire à partir de maintenant. Vous pouvez désactiver ou reconfigurer la valeur des heures creuses selon vos besoins.

## Mettre à jour les périodes libres {#update-free-periods}

En utilisant la fonction de périodes libres de mise à jour , vous pouvez définir une période de 7 jours pendant laquelle les mises à jour n’auront pas lieu. Une fois configurées, toutes les mises à jour de maintenance sont automatiquement transférées en dehors de la période définie. Vous pouvez avoir jusqu’à trois périodes sans mise à jour sur un intervalle de 12 mois. En outre, les périodes libres de mise à jour peuvent être désignées jusqu’à un an à l’avance.

Gardez à l’esprit, lors de la configuration de cette option, qu’un intervalle d’une semaine au moins entre les périodes est obligatoire afin de faciliter les mises à jour automatiques. Par conséquent, cet intervalle d’une semaine est automatiquement appliqué et sera ajouté au calendrier entre les périodes libres de mise à jour que vous avez configurées. Cela peut entraîner l’indisponibilité de certains jours calendaires pour la sélection.

Vous pouvez définir les périodes d’absence de mise à jour **par programme**.

### Configuration des périodes libres de mise à jour {#configure-update-free-periods}

La fonctionnalité de mise à jour des périodes libres peut être configurée à l’aide de l’interface AEM Cloud Manager comme suit :

Accédez à **Activités > Mises à jour automatiques > Options de mise à jour**.

![Configuration](assets/main-config.png)

1. Accédez à la section Mettre à jour les périodes libres .
2. Cliquez sur **Ajouter une période de mise à jour gratuite**.
3. Sélectionnez une période libre de mise à jour d’une semaine dans le calendrier.

![Mettre à jour la configuration des périodes libres](assets/update-free-periods.png)

Une icône **Actif** s’affiche près de la période d’exemption de mise à jour actuellement active et une icône **Terminé** près des périodes d’exemption de mise à jour terminées.
