---
title: Intégration à Adobe Target
description: 'Intégration à Adobe Target '
feature: Administering
role: Admin
exl-id: cf243fb6-5563-427f-a715-8b14fa0b0fc2
source-git-commit: a2fa676de0d6ca6d7cde3beedd5cc63850966b56
workflow-type: ht
source-wordcount: '1035'
ht-degree: 100%

---

# Intégration à Adobe Target{#integrating-with-adobe-target}

Dans le cadre d’Adobe Experience Cloud, Adobe Target vous permet d’améliorer la pertinence du contenu en effectuant un ciblage et des mesures sur tous les canaux. L’intégration d’Adobe Target et d’AEM as a Cloud Service nécessite :

* d’utiliser l’interface utilisateur tactile pour créer une configuration Target dans AEM as a Cloud Service (configuration IMS requise) ;
* d’ajouter et de configurer Adobe Target en tant qu’extension dans [Adobe Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/get-started/quick-start.html?lang=fr).

Adobe Launch est nécessaire afin de gérer les propriétés côté client pour Analytics et Target dans les pages AEM (bibliothèques/balises JS). Cela dit, l’intégration à Launch est nécessaire au « ciblage d’expérience ». Pour l’exportation des fragments d’expérience dans Target, vous n’avez besoin que de la configuration Adobe Target et d’IMS.

>[!NOTE]
>
>Les clients Adobe Experience Manager as a Cloud Service qui ne disposent pas d’un compte Target existant peuvent demander l’accès au Target Foundation Pack pour Experience Cloud. Le Foundation Pack offre une utilisation limitée en volume de Target.

## Création de la configuration Adobe Target {#create-configuration}

1. Accédez à **Outils** → **Services cloud**.
   ![Navigation](assets/cloudservice1.png "Navigation")
2. Sélectionnez **Adobe Target**.
3. Cliquez sur le bouton **Créer**.
   ![Créer](assets/tenant1.png "Créer")
4. Renseignez les détails (voir ci-dessous), puis sélectionnez **Connexion**.
   ![Connexion](assets/open_screen1.png "Connexion")

### Configuration IMS {#ims-configuration}

Une configuration IMS pour Launch et Target est nécessaire pour intégrer correctement Target à AEM et Launch. Bien que la configuration IMS de Launch est préconfigurée dans AEM as a Cloud Service, celle de Target doit être créée (une fois Target approvisionné). Reportez-vous à [cette vidéo](https://helpx.adobe.com/fr/experience-manager/kt/sites/using/aem-sites-target-standard-technical-video-understand.html) et à [cette page](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/integration-ims-adobe-io.html?lang=fr) pour savoir comment créer la configuration IMS de Target.

### ID de client Adobe Target et code client Adobe Target {#tenant-client}

Lors de la configuration des champs d’ID client Adobe Target et de code client Adobe Target, tenez compte des points suivants :

1. Pour la plupart des clients, l’ID de client et le code client sont identiques. Cela signifie que les deux champs contiennent les mêmes informations et sont identiques. Veillez à saisir l’identifiant du client dans les deux champs.
2. Pour des raisons d’héritage, vous pouvez également entrer différentes valeurs dans les champs d’ID client et de Code client.

Dans les deux cas, il faut savoir que :

* par défaut, le code client (s’il est ajouté en premier) est également automatiquement copié dans le champ d’ID client ;
* vous avez la possibilité de modifier le jeu d’ID client par défaut.
* Par conséquent, les appels du serveur principal vers Target sont basés sur l’ID client et les appels vers Target côté client sont basés sur le Code client.

Comme nous l’avons indiqué plus haut, le premier cas est le plus courant pour AEM as a Cloud Service. Dans les deux cas, veillez à ce que les **deux** champs contiennent les informations appropriées en fonction de vos besoins.

>[!NOTE]
>
> Si vous souhaitez modifier une configuration Target existante :
>
> 1. saisissez de nouveau l’ID client ;
> 2. reconnectez-vous à Target ;
> 3. enregistrez la configuration.


### Modification de la configuration de Target {#edit-target-configuration}

Pour modifier la configuration de Target, procédez comme suit :

1. Sélectionnez une configuration existante et cliquez sur **Propriétés**.
2. Modifiez les propriétés.
3. Sélectionnez **Reconnecter à Adobe Target**.
4. Sélectionnez **Enregistrer et fermer**.

### Ajout d’une configuration à un site {#add-configuration}

Pour appliquer une configuration d’interface utilisateur tactile à un site, accédez à : **Sites** → **Sélectionner une page de site** → **Propriétés** → **Avancé** → **Configuration** → Sélectionnez le client de configuration.

## Intégration d’Adobe Target dans AEM Sites à l’aide d’Adobe Launch {#integrate-target-launch}

AEM offre une intégration à Experience Platform Launch prête à l’emploi. En ajoutant l’extension Adobe Target à Experience Platform Launch, vous pouvez utiliser les fonctionnalités d’Adobe Target sur les pages web AEM. Les bibliothèques Target ne peuvent être rendues qu’à l’aide de Launch.

>[!NOTE]
>
>Les frameworks existants (hérités) fonctionnent toujours, mais ne peuvent pas être configurés dans l’interface utilisateur tactile. Il est conseillé de recréer les configurations de mappage de variables dans Launch.

En général, les étapes d’intégration sont les suivantes :

1. Créer une propriété Launch
2. Ajouter les extensions requises
3. Créer un élément de données (pour capturer les paramètres du hub contextuel)
4. Créer une règle de page
5. Concevoir et publier

### Création d’une propriété Launch {#create-property}

Une propriété est un conteneur qui est rempli d’extensions, de règles et d’éléments de données.

1. Sélectionnez le bouton **New Property** (Nouvelle propriété).
2. Attribuez un nom à votre propriété.
3. Saisissez comme domaine l’adresse IP/l’hôte sur lequel vous souhaitez charger la bibliothèque Launch.
4. Sélectionnez le bouton **Save** (Enregistrer).
   ![Launchproperty](assets/properties_newproperty1.png "Launchproperty")

### Ajout des extensions requises {#add-extension}

Les **extensions** sont le conteneur qui gère les paramètres de bibliothèque principaux. L’extension Adobe Target prend en charge les implémentations côté client en utilisant le SDK Target JavaScript pour le web moderne, at.js. Vous devez ajouter les extensions **Adobe Target** et **Adobe ContextHub**.

1. Sélectionnez l’option Catalogue des extensions, puis recherchez Target dans le filtre.
2. Sélectionnez **Adobe Target** at.js et cliquez sur l’option Installer.
   ![Recherche de Target](assets/search_ext1.png "Recherche de Target")
3. Sélectionnez le bouton **Configure** (Configurer). Notez la fenêtre de configuration avec les informations d’identification du compte Target importées et la version at.js de cette extension.
4. Sélectionnez **Save** (Enregistrer) pour ajouter l’extension Target à votre propriété Launch. Vous devriez être en mesure de voir l’extension Target répertoriée dans la liste **Installed Extensions** (Extensions installées).
   ![Enregistrer l’extension](assets/configure_extension1.png "Enregistrer l’extension")
5. Répétez les étapes ci-dessus pour rechercher l’extension **Adobe ContextHub** et l’installer (cela est nécessaire pour l’intégration avec les paramètres contexthub, en fonction du ciblage allant être effectué).

### Création d’un élément de données {#data-element}

Les **éléments de données** sont des espaces réservés vers lesquels vous pouvez mapper les paramètres du hub contextuel.

1. Sélectionnez **Data Elements** (Éléments de données).
2. Sélectionnez **Add Data Element** (Ajouter l’élément de données).
3. Fournissez le nom de l’élément de données et mappez-le à un paramètre de hub contextuel.
4. Sélectionnez **Enregistrer**.
   ![Élément de données](assets/data_elem1.png "Élément de données")

### Création d’une règle de page {#page-rule}

Dans **Règle**, définissez et ordonnez une séquence d’actions qui sera exécutée sur le site pour procéder au ciblage.

1. Ajoutez un ensemble d’actions comme illustré dans la capture d’écran.
   ![Actions](assets/rules1.png "Actions")
2. Dans Add Params to All Mboxes (Ajouter les paramètres à tous les mbox), ajoutez l’élément de données configuré précédemment (voir élément de données ci-dessus) au paramètre qui va être envoyé dans l’appel de mbox.
   ![Mbox](assets/map_data1.png "Actions")

### Concevoir et publier {#build-publish}

Pour savoir comment concevoir et publier, reportez-vous à cette [page](https://experienceleague.adobe.com/docs/experience-manager-learn/aem-target-tutorial/aem-target-implementation/using-launch-adobe-io.html?lang=fr).

## Modifications de la structure de contenu entre les configurations de l’interface utilisateur classique et tactile {#changes-content-structure}

<table style="table-layout:auto">
  <tr>
    <th>Modification</th>
    <th>Configuration de l’interface utilisateur classique</th>
    <th>Configuration de l’interface utilisateur tactile</th>
    <th>Conséquences</th>
  </tr>
  <tr>
    <td>Emplacement de la configuration de Target.</td>
    <td>/etc/cloudservices/testandtarget/</td>
    <td>/conf/tenant/settings/cloudservices/target/</td>
    <td> Auparavant, plusieurs configurations étaient présentes sous /etc/cloudservices/testandtarget, mais désormais une seule configuration figure sous un client.</td>
  </tr>
</table>

>[!NOTE]
>
>Les configurations héritées sont toujours prises en charge pour les clients existants (sans possibilité de modifier des configurations ou d’en créer de nouvelle). Les configurations héritées feront partie des modules de contenu chargés par les clients à l’aide de VSTS.
