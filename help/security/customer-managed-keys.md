---
title: Clés gérées par le client ou la cliente pour AEM as a Cloud Service
description: Découvrez comment gérer les clés de chiffrement pour AEM as a Cloud Service.
feature: Security
role: Admin
hide: true
hidefromtoc: true
exl-id: 100ddbf2-9c63-406f-a78d-22862501a085
source-git-commit: eb38369ee918851a9f792af811bafff9b2e49a53
workflow-type: ht
source-wordcount: '1167'
ht-degree: 100%

---

# Configuration des clés gérées par le client ou la cliente pour AEM as a Cloud Service {#cusomer-managed-keys-for-aem-as-a-cloud-service}

AEM as a Cloud Service stocke actuellement les données client dans Stockage Blob Azure et MongoDB, en utilisant des clés de chiffrement gérées par le fournisseur par défaut pour sécuriser les données. Bien que cette configuration réponde aux besoins de sécurité de nombreuses organisations, les entreprises des secteurs réglementés ou celles nécessitant une sécurité des données renforcée peuvent chercher à mieux contrôler leurs pratiques de chiffrement. Pour les entreprises qui accordent la priorité à la sécurité des données, à la conformité et à la capacité à gérer leurs clés de chiffrement, la solution de clés gérées par le client ou la cliente (CMK, Customer-Managed Keys) offre une amélioration essentielle.

## Le problème en cours de résolution {#the-problem-being-solved}

Les clés gérées par le fournisseur peuvent créer des problèmes pour les entreprises qui ont besoin d’un surcroît de confidentialité et d’intégrité. Sans contrôle sur la gestion des clés, les entreprises éprouvent des difficultés à respecter les exigences de conformité, à mettre en œuvre des politiques de sécurité personnalisées et à garantir une sécurité complète des données.

L’introduction des clés gérées par le client ou la cliente (CMK) résout ces problèmes en permettant aux clientes et clients d’AEM de contrôler entièrement leurs clés de chiffrement. En s’authentifiant via Microsoft Entra ID (anciennement Azure Active Directory), AEM CS se connecte en toute sécurité au coffre de clés Azure du client ou de la cliente, ce qui leur permet de gérer le cycle de vie de leurs clés de chiffrement (création, rotation et révocation des clés).

La solution CMK offre plusieurs avantages :

* **Contrôle des données et chiffrement de l’application :** renforce la sécurité grâce à la gouvernance directe de votre application AEM et de vos clés de chiffrement des données.
* **Améliorer la confidentialité et l’intégrité :** réduit la probabilité d’accès et de divulgation involontaires de données sensibles ou propriétaires grâce à une gestion complète du chiffrement.
* **Prise en charge d’Azure Key Vault :** Azure Key Vault permet le stockage des clés, le traitement des opérations secrètes et l’exécution des rotations de clés.

En adoptant la solution CMK, les clientes et clients peuvent mieux contrôler leurs pratiques de sécurité et de chiffrement des données, améliorer la sécurité et atténuer les risques, tout en continuant à bénéficier de l’évolutivité et de la flexibilité d’AEM CS.

AEM as a Cloud Service vous permet d’apporter vos propres clés de chiffrement pour chiffrer les données au repos. Ce guide décrit les étapes à suivre pour configurer une clé gérée par le client ou la cliente (CMK) dans Azure Key Vault pour AEM as a Cloud Service.

>[!WARNING]
>
>Après avoir configuré la solution CMK, vous ne pouvez pas revenir aux clés gérées par le système. Il vous incombe de gérer vos clés en toute sécurité et de fournir l’accès à votre coffre de clés, à votre clé et à votre application CMK dans Azure afin d’éviter de perdre l’accès à vos données.

Vous bénéficierez également d’un accompagnement à travers les étapes suivantes pour créer et configurer l’infrastructure requise :

1. Configuration de votre environnement
1. Obtenir un ID de l’application à partir d’Adobe
1. Créer un groupe de ressources
1. Créer un coffre de clés
1. Accorder à Adobe l’accès au coffre de clés
1. Créer une clé de chiffrement

Vous devrez partager l’URL du coffre de clés, le nom de la clé de chiffrement et des informations sur le coffre de clés avec Adobe.

## Configurer votre environnement {#setup-your-environment}

L’interface de ligne de commande (CLI) Azure est la seule exigence de ce guide. Si l’interface de ligne de commande Azure n’est pas déjà installée, suivez les instructions d’installation officielles [ici](https://learn.microsoft.com/fr-fr/cli/azure/install-azure-cli).

Avant de passer au reste de ce guide, connectez-vous à l’interface en ligne de commande avec `az login`.

>[!NOTE]
>
>Bien que ce guide utilise l’interface de ligne de commande Azure, il est possible d’effectuer les mêmes opérations via la console Azure. Si vous préférez utiliser la console Azure, utilisez les commandes ci-dessous comme référence.

## Obtenir un ID de l’application à partir d’Adobe {#obtain-an-application-id-from-adobe}

Adobe vous fournira un ID d’application Entra dont vous aurez besoin dans la suite de ce guide. Si vous ne disposez pas déjà d’un ID d’application, contactez Adobe pour en obtenir un.

## Créer un groupe de ressources {#create-a-new-resource-group}

Créez un groupe de ressources à l’emplacement de votre choix.

```powershell
# Choose a location and a name for the resource group.
$location="<AZURE LOCATION>"
$resourceGroup="<RESOURCE GROUP>"

# Create the resource group.
az group create --location $location --resource-group $resourceGroup
```

Si vous disposez déjà d’un groupe de ressources, n’hésitez pas à l’utiliser à la place. Dans la suite de ce guide, l’emplacement du groupe de ressources et son nom sont identifiés respectivement par `$location` et `$resourceGroup`.

## Créer un coffre de clés {#create-a-key-vault}

Vous devez créer un coffre de clés pour y stocker votre clé de chiffrement. La protection contre la purge doit être activée pour le coffre de clés. La protection contre la purge est nécessaire pour chiffrer les données au repos d’autres services Azure. L’accès au réseau public doit également être activé pour que le client Adobe puisse accéder au coffre de clés.

>[!IMPORTANT]
>La création du coffre Key Vault avec l’accès réseau public désactivé impose l’exécution de toutes les opérations liées au coffre Key Vault, telles que la création ou la rotation de clés, à partir d’un environnement disposant d’un accès réseau au coffre KeyVault, par exemple, une machine virtuelle pouvant accéder au coffre KeyVault.

```powershell
# Reuse this information from the previous step.
$location="<AZURE LOCATION>"
$resourceGroup="<RESOURCE GROUP>"

# Choose a name for the key vault.
$keyVaultName="<KEY VAULT NAME>"

# Create the key vault.
az keyvault create `
  --location $location `
  --resource-group $resourceGroup `
  --name $keyVaultName `
  --default-action=Deny `
  --enable-purge-protection `
  --enable-rbac-authorization `
  --public-network-access Enabled
```

## Accorder à Adobe l’accès au coffre de clés {#grant-adobe-access-to-the-key-vault}

Au cours de cette étape, vous allez permettre à Adobe d’accéder à votre coffre de clés via une application Entra. L’ID de l’application Entra doit déjà avoir été fourni par Adobe.

Tout d’abord, vous devez créer un principal de service associé à l’application Entra et lui affecter les rôles **Lecteur Key Vault** et **Utilisateur de chiffrement Key Vault**. Les rôles sont limités au coffre de clés créé dans ce guide.

```powershell
# Reuse this information from the previous steps.
$resourceGroup="<RESOURCE GROUP>"
$keyVaultName="<KEY VAULT NAME>"

# The application ID is provided by Adobe.
$appId="<APPLICATION ID>"

# Retrieve the ID of the key vault.
$keyVaultId=(az keyvault show --resource-group $resourceGroup --name $keyVaultName --query id --output tsv)

# Create a new service principal.
$servicePrincipalId=(az ad sp create --id $appId --query id --out tsv)

# Assign the roles to the service principal.
az role assignment create --assignee $servicePrincipalId --role "Key Vault Reader" --scope $keyVaultId
az role assignment create --assignee $servicePrincipalId --role "Key Vault Crypto User" --scope $keyVaultId
```

## Créer une clé de chiffrement {#create-an-ecryption-key}

Enfin, vous pouvez créer une clé de chiffrement dans votre coffre de clés. Notez que vous aurez besoin du rôle **Agent de chiffrement Key Vault** pour effectuer cette étape. Si la personne connectée ne dispose pas de ce rôle, contactez votre administrateur ou administratrice système pour que ce rôle vous soit accordé ou demandez à une personne disposant déjà de ce rôle de terminer cette étape pour vous.

Un accès réseau au coffre de clés est requis pour créer la clé de chiffrement. Vérifiez d’abord que vous pouvez accéder au coffre de clés et continuez à créer la clé :

```powershell
# Reuse this information from the previous steps.
$keyVaultName="<KEY VAULT NAME>"

# Chose a name for your key.
$keyName="<KEY NAME>"

# Create the key.
az keyvault key create --vault-name $keyVaultName --name $keyName
```

## Partager les informations du coffre de clés {#share-the-key-vault-information}

À ce stade, tout est prêt. Il vous suffit de partager certaines informations requises avec Adobe, qui se chargera de la configuration de votre environnement pour vous.

```powershell
# Reuse this information from the previous steps.
$resourceGroup="<RESOURCE GROUP>"
$keyVaultName="<KEY VAULT NAME>"

# Retrieve the URL of your key vault.
$keyVaultUri=(az keyvault show --name $keyVaultName `
    --resource-group $resourceGroup `
    --query properties.vaultUri `
    --output tsv)

# In addition we would need the tenantId and the subscriptionId in order to setup the connection.
$tenantId=(az keyvault show --name $keyVaultName `
    --resource-group $resourceGroup `
    --query properties.tenantId `
    --output tsv)
$subscriptionId="<Subscription ID>"
```


## Implications de la révocation de l’accès aux clés {#implications-of-revoking-key-access}

La révocation ou la désactivation de l’accès au coffre de clés, à la clé ou à l’application CMK peut entraîner des perturbations importantes, notamment des modifications avec rupture des opérations de votre plateforme. Une fois ces clés désactivées, les données de plateforme peuvent devenir inaccessibles et toutes les opérations en aval qui reposent sur ces données cesseront de fonctionner. Il est essentiel de bien comprendre les impacts en aval avant d’apporter des modifications à aux configurations de vos clés.

Si vous décidez de révoquer l’accès de la plateforme à vos données, vous pouvez le faire en supprimant le rôle d’utilisateur ou d’utilisatrice associé à l’application du coffre de clés dans Azure.

## Étapes suivantes {#next-steps}

Contactez Adobe et partagez :

* L’URL de votre coffre de clés. Vous l’avez récupérée au cours de cette étape et enregistrée dans la variable `$keyVaultUri`.
* Le nom de votre clé de chiffrement. Vous avez créé la clé dans une étape précédente et vous l’avez enregistrée dans la variable `$keyName`.
* Le `$resourceGroup`, `$subscriptionId` et `$tenantId` nécessaires pour configurer la connexion au coffre de clés.

<!-- Alexandru: hiding this for now

### Private Link Approvals {#private-link-approvals}

>[!TIP]
>You can also consult the [Azure Documentation](https://learn.microsoft.com/en-us/azure/key-vault/general/private-link-service?tabs=portal#how-to-manage-a-private-endpoint-connection-to-key-vault-using-the-azure-portal) on how to approve a Private Endpoint Connection.

Afterwards, an Adobe Engineer assigned to you will contact you to confirm the creation of the private endpoints, and will request you to approve a set of required Connection Requests. The requests can be approved either using the Azure Portal UI, where you can go to **KeyVault > Settings > Networking > Private Endpoint Connections** and approve the requests with names similar to these: 

`mongodb-atlas-<REGION>-<NUMBER>`, `storage-account-private-endpoint` and `backup-storage-account-private-endpoint`. 

Notify the Adobe Engineer once this process is complete and the Private Endpoints show up as **Approved**. -->

## Clés gérées par le client ou la cliente dans Private Beta {#customer-managed-keys-in-private-beta}

L’équipe d’ingénierie d’Adobe travaille actuellement sur une implémentation améliorée de la fonction CMK exploitant Liaison privée Azure. La nouvelle implémentation permettra de partager votre clé via le réseau principal Azure grâce à une connexion de liaison privée directe entre le client d’Adobe et votre coffre de clés.

Cette implémentation améliorée est actuellement disponible dans Private Beta et peut être activée pour quelques clientes et clients qui acceptent de s’abonner au programme Private Beta et de travailler en étroite collaboration avec l’équipe d’ingénierie d’Adobe. Si Private Beta pour la fonction CMK à l’aide de Private Link vous intéresse, contactez Adobe pour obtenir plus d’informations.
