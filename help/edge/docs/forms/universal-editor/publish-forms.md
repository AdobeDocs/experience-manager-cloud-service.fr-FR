---
title: Publiez AEM Forms pour Edge Delivery Services.
description: Publiez vos formulaires Edge Delivery Services rapidement et en toute simplicité.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: ac005e5bc143c35eb29ba177a26aa6cc33897db4
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Publication de votre formulaire adaptatif dans Edge Delivery Services

Une fois votre formulaire finalisé et prêt à être utilisé, vous pouvez le publier pour le rendre accessible à vos clients à des fins de collecte et d’envoi de données. La publication garantit que le formulaire est disponible sur Edge Delivery, ce qui permet aux utilisateurs et utilisatrices d’interagir avec celui-ci de manière transparente. Ce processus permet aux clients de remplir et d’envoyer le formulaire en temps réel, ce qui garantit une capture des données efficace et un traitement rationalisé.

## Prérequis

* Formulaire créé à l’aide du modèle **Edge Delivery Services (EDS)**. [En savoir plus](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) sur la création d’un formulaire basé sur EDS.

## Publier Votre Formulaire

Vous pouvez publier n’importe quel **formulaire adaptatif basé sur EDS** dans Edge Delivery en procédant comme suit :

<!--1. Select the **Adaptive Form** that you want to publish and click the **Edit** ![edit icon](/help/forms/assets/edit.svg) icon.
   ![Select EDS-Based Form](/help/forms/assets/select-eds-based-form.png)-->

1. Ouvrez votre formulaire adaptatif dans l’éditeur et cliquez sur l’icône **Publier** dans le rail supérieur.
   ![Cliquez sur Publier](/help/forms/assets/publish-icon-eds-form.png)

1. Lorsque vous cliquez sur **Publier**, un écran ou un pop-up s’affiche pour afficher les ressources de publication, y compris le titre du formulaire. Dans cet exemple, le modèle **Wknd_Form** est utilisé.
   ![Sur Clic, Publier](/help/forms/assets/on-click-publish.png)

1. Cliquez de nouveau sur **Publier** et un pop-up de confirmation s’affiche, indiquant que votre formulaire est maintenant publié.
   ![Publication réussie](/help/forms/assets/publish-success.png)

1. Pour vérifier le statut de publication du formulaire, cliquez de nouveau sur **Publier**.
   ![Statut de publication](/help/forms/assets/publish-status.png)

1. Pour **dépublier** un formulaire, ouvrez-le dans l’éditeur, cliquez sur le menu à trois points dans le coin supérieur droit, puis cliquez sur **Dépublier**.
   ![ Dépublier ](/help/forms/assets/unpublish--form.png)

## Activez l’envoi de formulaire sur Edge Delivery en configurant un filtre Référent pour AEM Publisher

Pour garantir un envoi de formulaire sécurisé, vous devez configurer un **filtre Référent** dans AEM Publisher. Ce filtre permet de s’assurer que seules les requêtes Edge Delivery autorisées peuvent effectuer des opérations d’écriture (POST, PUT, DELETE, COPY, MOVE), ce qui empêche toute modification non autorisée. Vous trouverez ci-dessous les étapes à suivre pour configurer un filtre Référent pour AEM Publisher :

### Mettre à jour l’URL de l’instance AEM dans Edge Delivery

Modifiez le `submitBaseUrl` du fichier **constant.js** dans le bloc de formulaire pour spécifier l’URL de l’instance AEM :

**Pour la configuration du cloud :**

```js
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';
```
**Pour le développement local :**

```js
export const submitBaseUrl = 'http://localhost:4503';
```

### Modification de la configuration CORS

Ajustez les **paramètres CORS** pour autoriser les demandes d’envoi de formulaire provenant de domaines Edge Delivery. Pour plus d’informations, consultez le [Guide de configuration CORS](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors).

**Exemple de configuration CORS :**

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Franklin Stage
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  

# Franklin Live
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```
Pour le développement local, reportez-vous à la [documentation](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter) pour activer CORS à partir de votre **URL hôte de l’interface utilisateur de développement**.

### Configuration du filtrage des référents

Configurez le **filtre Référent** dans AEM Cloud Service via Cloud Manager. [En savoir plus](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) sur la configuration du filtre référent sur une instance AEM Cloud Service à l’aide d’un Cloud Manager.

**Configuration JSON pour le filtre Référent :**

```json
{
  "allow.empty": false,
  "allow.hosts": [],
  "allow.hosts.regexp": [
    "https://.*\\.hlx\\.page:443",
    "https://.*\\.hlx\\.live:443"
  ],
  "filter.methods": [
    "POST",
    "PUT",
    "DELETE",
    "COPY",
    "MOVE"
  ],
  "exclude.agents.regexp": [
    ""
  ]
}
```

Cette configuration spécifie les méthodes HTTP filtrées, les référents autorisés et les agents utilisateur exclus du filtre. L’implémentation de ces configurations **envoi de formulaires via Edge Delivery** garantira la sécurité de ces derniers et limitera leur utilisation aux sources autorisées uniquement).

### Accès Au Formulaire Adaptatif Publié

Votre formulaire adaptatif est maintenant accessible via **Edge Delivery** à l&#39;aide du format d&#39;URL suivant :

```
https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
```

Par exemple, l’URL du **Wknd-Form** est :

```
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form
```


















