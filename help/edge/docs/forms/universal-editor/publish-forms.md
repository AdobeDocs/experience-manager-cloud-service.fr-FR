---
title: Publiez AEM Forms pour Edge Delivery Services.
description: Publiez vos formulaires Edge Delivery Services rapidement et en toute simplicité.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ba1c608d-36e9-4ca1-b87b-0d1094d978db
source-git-commit: 744f505c8e97b6ca6947b685ddb1eba41b370cfa
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 87%

---

# Publier votre formulaire adaptatif vers Edge Delivery Services

<span class="preview"> Cette fonctionnalité est disponible via le programme d’accès anticipé. Pour demander l’accès, envoyez un e-mail à partir de votre adresse officielle à <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> avec le nom de votre organisation GitHub et le nom du référentiel. Par exemple, si l’URL du référentiel est https://github.com/adobe/abc, le nom de l’organisation est adobe et le nom du référentiel est abc.</span>


Une fois votre formulaire finalisé et prêt à être utilisé, vous pouvez le publier pour le rendre accessible à vos clientes et clients, à des fins de collecte et d’envoi de données. La publication garantit que le formulaire est disponible sur Edge Delivery, ce qui permet aux utilisateurs et utilisatrices d’interagir avec lui de manière transparente. Ce processus permet de remplir et d’envoyer le formulaire en temps réel, ce qui garantit une capture des données efficace et un traitement rationalisé.

## Prérequis

* Formulaire créé à partir du modèle **Edge Delivery Services**. [En savoir plus](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) sur la création d’un formulaire basé sur EDS.

## Publier votre formulaire

Vous pouvez publier n’importe quel **formulaire adaptatif basé sur EDS** vers Edge Delivery en procédant comme suit :

<!--1. Select the **Adaptive Form** that you want to publish and click the **Edit** ![edit icon](/help/forms/assets/edit.svg) icon.
   ![Select EDS-Based Form](/help/forms/assets/select-eds-based-form.png)-->

1. Ouvrez le formulaire adaptatif dans l’éditeur et cliquez sur l’icône **Publier** dans le rail supérieur.
   ![Cliquer sur Publier](/help/forms/assets/publish-icon-eds-form.png)

1. Lorsque vous cliquez sur **Publier**, un écran ou une fenêtre contextuelle s’affiche et montre les ressources de publication, notamment le titre du formulaire. Dans cet exemple, le modèle utilisé est **Wknd_Form**.
   ![Publication en un clic](/help/forms/assets/on-click-publish.png)

1. Cliquez de nouveau sur **Publier** pour afficher une fenêtre contextuelle de confirmation, indiquant que votre formulaire est maintenant publié.
   ![Publication réussie](/help/forms/assets/publish-success.png)

1. Pour vérifier le statut de publication du formulaire, cliquez de nouveau sur **Publier**.
   ![Statut de publication](/help/forms/assets/publish-status.png)

1. Pour **annuler la publication** d’un formulaire, ouvrez-le dans l’éditeur, cliquez sur le menu à trois points dans le coin supérieur droit, puis cliquez sur **Annuler la publication**.
   ![Annuler la publication](/help/forms/assets/unpublish--form.png)

## Activez l’envoi de formulaire sur Edge Delivery en configurant un filtre Référent pour AEM Publisher

Pour garantir un envoi de formulaire sécurisé, vous devez configurer un **filtre Référent** dans AEM Publisher. Ce filtre permet de s’assurer que seules les requêtes Edge Delivery autorisées peuvent effectuer des opérations d’écriture (POST, PUT, DELETE, COPY, MOVE), ce qui empêche toute modification non autorisée. Vous trouverez ci-dessous les étapes à suivre pour configurer un filtre Référent pour AEM Publisher :

### Mettre à jour l’URL de l’instance AEM dans Edge Delivery

Modifiez la valeur `submitBaseUrl` du fichier **constant.js** dans le bloc de formulaire pour spécifier l’URL de l’instance AEM :

**Pour la configuration du cloud :**

```js
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';
```
**Pour le développement local :**

```js
export const submitBaseUrl = 'http://localhost:4503';
```

### Modifier la configuration CORS

Ajustez les **paramètres CORS** pour autoriser les demandes d’envoi de formulaire provenant de domaines Edge Delivery. Pour plus d’informations, consultez le [Guide de configuration CORS](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors).

**Exemple de configuration CORS :**

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Franklin Stage
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  

# Franklin Live
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```
Pour le développement local, reportez-vous à la [documentation](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter) pour activer CORS à partir de votre **URL hôte de l’interface utilisateur de développement**.

### Configurer le filtre Référent

Configurez le **filtre Référent** dans AEM Cloud Service via Cloud Manager. [En savoir plus](https://experienceleague.adobe.com/fr/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) sur la configuration du filtre référent sur une instance AEM Cloud Service à l’aide de Cloud Manager.

**Configuration JSON pour le filtre Référent :**

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

Cette configuration spécifie les méthodes HTTP filtrées, les référents autorisés et les agents utilisateur exclus du filtre. En mettant en œuvre ces configurations, les **envois de formulaires via Edge Delivery** seront sécurisés et limités aux sources autorisées uniquement.

### Accéder au formulaire adaptatif publié

Le formulaire adaptatif est maintenant accessible via **Edge Delivery** dans le format d’URL suivant :

```
https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
```

Par exemple, l’URL de **Wknd-Form** est :

```
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form
```


## Voir également

{{universal-editor-see-also}}

