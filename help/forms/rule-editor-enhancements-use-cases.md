---
title: Cet article décrit divers cas d’utilisation de l’éditeur de règles dans un formulaire adaptatif basé sur les composants principaux.
description: Cet article explore différents cas d’utilisation de l’éditeur de règles dans un formulaire adaptatif basé sur les composants principaux. Elle décrit également comment les fonctions personnalisées peuvent être utilisées pour créer des règles personnalisées pour les formulaires.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
hide: true
hidefromtoc: true
source-git-commit: 87650caea6eb907093f0f327f1dbc19641098e4a
workflow-type: tm+mt
source-wordcount: '1863'
ht-degree: 0%

---

# Améliorations de l’éditeur de règles et cas d’utilisation

<span class="preview"> Il s’agit de fonctionnalités de version préliminaire disponibles via notre <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features">canal de version préliminaire</a>.

Cet article présente les dernières améliorations apportées à l’éditeur de règles dans le Forms adaptatif. Ces mises à jour sont conçues pour vous aider à définir plus facilement le comportement du formulaire, sans devoir écrire de code personnalisé, et à créer des expériences de formulaire plus dynamiques, plus réactives et plus personnalisées.

Le tableau ci-dessous répertorie les récentes améliorations apportées à l’éditeur de règles dans le Forms adaptatif, ainsi qu’une brève description et les principaux avantages de chaque fonctionnalité.:

| Amélioration | Description | Avantages |
|---|----|---|
| **Validation à l’aide de la méthode `validate()`** | Disponible dans la liste des fonctions pour valider des champs individuels, des panneaux ou l’ensemble du formulaire. | - Validation granulaire au niveau du panneau, du champ ou du formulaire <br> - Meilleure expérience utilisateur avec des <br> de messages d’erreur ciblés - Empêche la progression avec des <br> de données incomplètes - Réduit les erreurs d’envoi de formulaire |
| **Télécharger le document d’enregistrement** | Fonction prête à l’emploi disponible dans l’éditeur de règles pour télécharger le document d’enregistrement (DE). | - Aucun développement personnalisé requis pour le téléchargement des <br> de document d’enregistrement - Expérience de téléchargement cohérente dans tous les formulaires |
| **Variables dynamiques** | Créez des règles à l’aide de variables qui changent en fonction des entrées utilisateur ou d’autres conditions. | - Active des conditions de règle flexibles <br> - Réduit le besoin de <br> logiques en double - Élimine l’exigence de création de champs masqués |
| **Règles personnalisées basées sur un événement** | Définissez des règles qui répondent à des événements personnalisés au-delà des déclencheurs standard. | - Prend en charge les cas d’utilisation avancés <br> - Un meilleur contrôle sur le moment et la manière dont les règles sont exécutées <br> - Améliore l’interactivité |
| **Exécution de panneau répétable contextuelle** | Les règles s’exécutent désormais dans le contexte approprié pour chaque panneau répété, au lieu de la dernière instance uniquement. | - Application précise des règles pour chaque instance de répétition <br> - Réduit les erreurs dans les sections dynamiques <br> - Améliore l’expérience utilisateur avec le contenu répété |
| **Prise en charge des paramètres de chaîne de requête, UTM et de navigateur** | Créez des règles qui adaptent le comportement du formulaire en fonction des paramètres d’URL ou de valeurs spécifiques au navigateur. | - Permet la personnalisation en fonction des <br> de la source ou de l’environnement - Utile pour les flux spécifiques au marketing ou au suivi <br> - Aucun besoin de script ou de personnalisation supplémentaire |

Examinons maintenant en détail chaque méthode avec des cas d’utilisation spécifiques pour vous aider à comprendre comment ces fonctionnalités peuvent être utilisées pour offrir une expérience personnalisée aux utilisateurs et utilisatrices

## Validation de la méthode dans la liste de fonctions

Amélioration des fonctionnalités de validation permettant d’utiliser la méthode **validate()** dans la liste de fonctions pour valider les panneaux, les champs ou les formulaires entiers. Par exemple, dans un formulaire de demande de prêt à plusieurs étapes, vous devez valider différentes sections avant de permettre aux utilisateurs de passer à l’étape suivante.

**Scénario :** une institution financière propose un formulaire de demande de prêt à plusieurs étapes où les utilisateurs doivent remplir différentes sections, telles que :

* Détails personnels
* Détails de l’emploi
* Détails du prêt
* Vérifier et envoyer

Avant qu’un utilisateur ne passe d’une étape à l’autre, le formulaire doit valider uniquement les champs de la section active. Par exemple, l’utilisateur ne devrait pas être autorisé à accéder aux « Détails de l’emploi » à moins que tous les champs obligatoires des « Détails personnels » ne soient correctement remplis.

**Implémentation à l’aide de validate() dans l’éditeur de règles**

Un bouton **Suivant** dans chaque panneau déclenche une règle à l’aide de la méthode **validate()**. La règle vérifie si tous les champs du panneau actuel sont valides. Si la validation est réussie, le formulaire accède au panneau suivant. Dans le cas contraire, des messages d’erreur s’affichent, demandant à l’utilisateur de corriger l’entrée.

La capture d’écran ci-dessous affiche la règle appliquée au bouton **Suivant** :

![Bouton Valider le suivant](/help/forms/assets/validate-next.png)

Dans la règle ci-dessus, le bouton **Suivant** vérifie la validité des champs de la section **Détails personnels**. Si les détails ne sont pas valides, le focus se déplace vers le champ **Nom** dans le panneau **Détails personnels**.

![output](/help/forms/assets/valid-output.png)

>[!NOTE]
>
>Vous pouvez utiliser la méthode **validate()** sur des formulaires, des fragments ou des champs individuels. Lorsqu’un fragment est inclus dans un formulaire, le formulaire et le fragment apparaissent tous deux comme des options dans le contexte de validation. Dans ce cas, le fragment fait référence aux champs qu’il contient, tandis que le formulaire fait référence au formulaire parent dans lequel le fragment est incorporé.

## Télécharger Dor en tant que fonction prête à l’emploi dans l’éditeur de règles

L’utilisation de la fonction prête à l’emploi **DownloadDor()** dans l’éditeur de règles permet à l’utilisateur de télécharger le document d’enregistrement , si le formulaire est configuré pour générer le document d’enregistrement.

>[!NOTE]
>
>Si le formulaire n’est pas configuré pour le document d’enregistrement, un message d’erreur s’affiche lorsque la règle utilisant la fonction **downloadDoR()** est appliquée au bouton.

**Scénario** : une agence gouvernementale fournit un formulaire de demande numérique pour l’émission de certificats. Après avoir soumis le formulaire, les demandeurs ont souvent besoin d&#39;une copie du formulaire rempli pour leurs dossiers ou pour le partager avec un autre ministère. Afin d&#39;améliorer l&#39;expérience utilisateur, l&#39;agence souhaite donner aux demandeurs la possibilité de télécharger un document d&#39;enregistrement immédiatement après la soumission ou à tout moment avant la soumission finale.

**Implémentation à l’aide de DownloadDor() dans l’éditeur de règles**

Un bouton **Télécharger** est ajouté au formulaire à l’aide de l’éditeur de règles. Une règle est configurée pour déclencher la fonction **DownloadDor()** lorsque l’utilisateur clique sur le bouton.

La capture d’écran ci-dessous affiche la règle appliquée au bouton **Télécharger** :

![ Règle du bouton Télécharger ](/help/forms/assets/download-button-rule.png)

>[!NOTE]
>
> Le champ **Entrée** permet à l’utilisateur de spécifier le nom de fichier d’un document téléchargeable. Ce paramètre est facultatif.

Si le formulaire est configuré pour la génération du document d’enregistrement, cette fonction génère et télécharge le PDF instantanément, sans nécessiter de fonction personnalisée.

![Document d’enregistrement](/help/forms/assets/download-dor-output.png)

## Prise en charge des variables dynamiques dans les règles

L’éditeur de règles amélioré prend désormais en charge la création et l’utilisation de variables dynamiques (temporaires). Ces variables peuvent être définies et récupérées tout au long du cycle de vie du formulaire à l’aide des fonctions intégrées **Définir la valeur de la variable** et **Obtenir la valeur de la variable**.
Ces variables :

* Ne sont pas envoyés avec les données de formulaire.
* Peut contenir des valeurs intermédiaires ou calculées.
* Peut être utilisé dans une logique conditionnelle et des actions.

**Scénario** : une société de commerce électronique fournit un formulaire de commande dans lequel les utilisateurs peuvent sélectionner un produit et une méthode d’expédition préférée. Alors que le prix du produit est capturé par le biais d’un champ de formulaire, le coût d’expédition est déterminé dynamiquement en fonction de la méthode sélectionnée et du pays choisi.

Pour que la structure du formulaire reste propre et éviter d’ajouter des champs masqués inutiles, l’entreprise souhaite gérer les frais d’expédition sous la forme d’une valeur temporaire qui prend en charge le calcul en temps réel du montant total.

**Implémentation à l’aide des fonctions Définir la valeur de la variable et Obtenir la valeur de la variable dans l’éditeur de règles**

Une règle est configurée pour définir une variable temporaire nommée **extracharge** à l’aide de la fonction **Définir la valeur de la variable**. La valeur de cette variable dépend du pays sélectionné. Par exemple, si l’utilisateur sélectionne « États-Unis », la valeur est définie sur 50. Pour tout autre pays, il est fixé à 100.

![Définir la valeur de la variable](/help/forms/assets/setvalue.png)

Par la suite, lors du calcul du coût total d&#39;expédition, la fonction **Obtenir la valeur de la variable** récupère la valeur **extracharge** en fonction du pays sélectionné.

![Obtenir la valeur de la variable](/help/forms/assets/getvalue.png)

Cette valeur est ensuite ajoutée aux frais d’expédition du produit et le résultat s’affiche dans le champ **Total des frais d’expédition**.

![output](/help/forms/assets/getsetvalue-output.png)

Cette approche vous permet de calculer et d’afficher les frais supplémentaires de manière dynamique sans les stocker dans un champ visible, ce qui offre une expérience utilisateur nette, réactive et sans code.


## Prise en charge des règles basées sur un événement personnalisé

L’éditeur de règles amélioré prend en charge la gestion des événements personnalisés à l’aide des fonctions **Distribuer l’événement** et **Activer l’événement déclencheur**. Ces fonctions permettent à différentes parties du formulaire de communiquer en émettant et en écoutant des événements personnalisés, ce qui permet une logique modulaire plus épurée sans étroitement lier les actions à des champs spécifiques.

**Scénario** : Un formulaire de candidature est intégré à un système RH externe qui effectue la vérification des antécédents. Une fois la vérification terminée, le système met à jour le formulaire avec le **Vérification en arrière-plan terminée!** le message. Le formulaire doit ajuster dynamiquement ce que le demandeur voit en fonction de ce résultat.

Au lieu de lier directement la logique au champ recevant le statut, le formulaire utilise une approche basée sur un événement personnalisé pour améliorer la modularité et la maintenabilité.

**Implémentation à l’aide de l’événement Dispatch et de l’événement déclencheur On**

Lorsque le statut de vérification de l’arrière-plan est mis à jour, une règle utilise **Distribuer l’événement** pour émettre un événement personnalisé en tant que **bgvmsg** ainsi que le résultat du statut. Une règle distincte écoute cet événement à l’aide de **Activer l’événement déclencheur**.

Les captures d’écran ci-dessous affichent les règles appliquées à l’option « La vérification en arrière-plan est-elle terminée ? » bouton radio et le champ de texte « bgvmsg ».

![répartir l’événement](/help/forms/assets/dispatch-event-rule.png)

![sur événement déclencheur](/help/forms/assets/trigger-event-rule.png)

Lorsque l’événement est détecté, il vérifie le statut et met à jour le formulaire en conséquence. Par exemple :

* Si la vérification d’arrière-plan est réussie, le formulaire affiche un message de confirmation.
* Si d’autres documents sont nécessaires, le formulaire affiche une section demandant au demandeur de télécharger les informations requises, ainsi qu’un message d’alerte.

![Distribuer la sortie d’événement](/help/forms/assets/dispatch-trigger-output.png)

Prise en charge des événements personnalisés permettant aux développeurs et aux développeuses de créer et de déclencher des événements personnalisés pouvant être utilisés comme conditions dans l’éditeur de règles.

## Exécution de règles basée sur le contexte pour les panneaux répétables

Le Forms adaptatif prend en charge l’exécution de règles contextuelles pour les panneaux répétables. Cela permet aux règles de s’appliquer spécifiquement à l’instance du panneau sur laquelle l’utilisateur interagit, plutôt que d’affecter toutes les instances ou de passer par défaut à la dernière.

**Scénario** : un formulaire de commande de produit permet aux utilisateurs d’ajouter plusieurs produits dans des panneaux distincts. Chaque panneau comprend un champ **Nombre de produits** et un champ **Coût total**. Lorsque l’utilisateur met à jour la quantité d’un produit, le formulaire doit recalculer le prix total, mais uniquement pour ce panneau spécifique, et pas pour tous les autres.

**Implémentation à l’aide de règles contextuelles dans l’éditeur de règles**

Une règle est configurée dans le champ **Nombre de produits** du panneau des produits répétables.

La capture d’écran ci-dessous affiche la règle pour le champ **Nombre de produits** dans le panneau produit répétable :

![nombre de règles de produit](/help/forms/assets/number-of-product-rule.png)

Lorsque la quantité est modifiée, la règle récupère le prix unitaire du produit sélectionné et calcule le coût total pour ce panneau uniquement.

![Sortie de règle contextuelle](/help/forms/assets/context-aware-rule-output.png)

## Règles basées sur des paramètres d’URL et de navigateur dans le Forms adaptatif

Les Forms adaptatives prennent en charge l’exécution dynamique de règles à l’aide de paramètres externes transmis par l’URL du formulaire ou dérivés de l’environnement du navigateur de l’utilisateur. Cela permet d’offrir des expériences de formulaire personnalisées et adaptées au contexte, en fonction de la provenance du visiteur ou de l’appareil qu’il utilise.

## Types de paramètres autorisés

| Type de paramètre | Options prises en charge | Description | Exemple de valeur |
| --- | --- | --- | ---|
| Paramètre de requête | `ref` (valeurs de chaîne uniquement) | Paire clé-valeur générique dans l’URL après `?` | `?ref=partner123` |
| Paramètre UTM | Contenu UTM Source<br>UTM Medium<br>UTM Campaign<br>UTM Term<br>UTM | Paramètres de requête spéciaux utilisés pour le tracking des campagnes | `?utm_source=google&utm_medium=email` |
| Paramètre d&#39;URL | Nom<br>chemin de l’hôte | Extrait les composants structurels de l’URL du formulaire | `hostname=www.example.com`, `path=/signup` |
| Paramètre du navigateur | Browser Agent<br>Browser Language<br>Browser Platform | Valeurs dérivées du navigateur ou de l’appareil de l’utilisateur | `Browser Agent=Mozilla`, `Language=en-US` |

**Scénario** : un formulaire de génération de piste doit adapter son message de bienvenue en fonction de la source de trafic. Lorsque l’utilisateur accède au formulaire par le biais d’une campagne publicitaire Google (à l’aide de utm_source=google dans l’URL), le formulaire doit afficher un message d’accueil personnalisé.

**Implémentation à l’aide du paramètre UTM**

Une règle est configurée sur un champ de texte qui affiche un message personnalisé aux utilisateurs de Google et elle utilise le paramètre **utm_source**.

La capture d’écran ci-dessous affiche la règle configurée pour le message texte :

![règle sur les SMS](/help/forms/assets/utm-param-rule.png)

Si la valeur du paramètre **utm_source** est égale à « google », un message personnalisé comme « Bonjour les utilisateurs de Google, bienvenue dans l’annonce Campaign ! » s’affiche.

![utm-param-output](/help/forms/assets/utm-param-output.png)

Les marketeurs peuvent ainsi diffuser du contenu pertinent aux utilisateurs en fonction de la campagne qui les a amenés dans le formulaire, sans avoir à effectuer une saisie manuelle du champ ni à utiliser un script personnalisé.

Ces améliorations étendent de manière significative les fonctionnalités de l’éditeur de règles du Forms adaptatif, en fournissant aux développeurs et développeuses des outils puissants pour créer des formulaires plus dynamiques, interactifs et intelligents. Chaque amélioration répond à des besoins professionnels spécifiques tout en conservant la facilité d’utilisation qui rend l’éditeur de règles accessible aux utilisateurs et utilisatrices techniques et non techniques.
