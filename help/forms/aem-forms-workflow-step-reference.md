---
title: Pour quelles étapes de workflow la création d’un workflow ou l’automatisation des processus métier (BPM) sont-elles disponibles sur AEM Forms Cloud Service ?
description: Les processus orientés formulaire vous permettent de créer rapidement des processus basés sur des formulaires adaptatifs. Vous pouvez utiliser Adobe Sign pour signer de manière électronique des documents, créer des processus métier basés sur des formulaires, récupérer et envoyer des données à plusieurs sources de données, et envoyer des notifications par e-mail.
exl-id: e1403ba6-8158-4961-98a4-2954b2e32e0d
google-site-verification: A1dSvxshSAiaZvk0yHu7-S3hJBb1THj0CZ2Uh8N_ck4
keywords: Utiliser des workflows AEM, à l’aide des étapes d’affectation de tâche, convertir en étape PDF/A, générer un document de l’étape enregistrée, utiliser des workflows, signer une étape de document, générer une étape de sortie imprimée, générer une sortie PDF non interactive
feature: Adaptive Forms, Workflow
role: Admin, User
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '7409'
ht-degree: 76%

---


# Utiliser des processus AEM orientés Forms - Guide de référence des étapes pour automatiser les processus métier {#forms-centric-workflow-on-osgi-step-reference}

| Version | Lien de l’article |
| -------- | ---------------------------- |
| AEM 6.5 | [Cliquez ici](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/aem-forms-workflow-step-reference.html?lang=fr) |
| AEM as a Cloud Service | Cet article |

Vous utilisez des modèles de workflow . Un modèle permet de définir et d’exécuter une série d’étapes. Vous pouvez également définir des propriétés de modèle pour déterminer, par exemple, si le processus est transitoire ou s’il utilise plusieurs ressources. Vous pouvez [inclure diverses étapes d’un processus AEM dans un modèle pour appliquer la logique métier](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=fr#extending-aem).

## Étapes orientées formulaire {#forms-workflow-steps}

Les étapes de workflows basés sur l’utilisation de Forms effectuent des opérations spécifiques à AEM Forms dans un workflow AEM. Ces étapes vous permettent de créer rapidement sur OSGi un processus basé sur l’utilisation de Forms et basé sur le Forms adaptatif. Ces processus peuvent être utilisés pour développer des processus de révision et d’approbation de base, des processus métier internes et sur le pare-feu. Vous pouvez également suivre les étapes de processus de Forms pour :

* créer des processus métier, des processus après envoi et des processus back-end pour gérer les processus d’inscription ;

* créer et affecter des tâches à un utilisateur ou à un groupe ;

* utiliser [!DNL Adobe Sign] dans un processus AEM pour envoyer un document pour signature ;

* générer un document d’enregistrement à la demande ou lors de l’envoi du formulaire ;

* connecter un modèle de processus à diverses sources de données pour enregistrer et récupérer facilement des données ;

* utiliser l’étape d’e-mail pour envoyer des notifications par e-mail et d’autres pièces jointes lors de l’achèvement d’une action et au début ou à la fin d’un processus.

>[!NOTE]
>
>Si le modèle de workflow est marqué pour un stockage externe, alors pour toutes les étapes de Forms Workflow, vous pouvez sélectionner uniquement l’option de variable pour stocker ou récupérer les fichiers de données et les pièces jointes.

## Étape Affecter une tâche {#assign-task-step}

L’étape Affecter une tâche crée un élément de travail et l’affecte à un utilisateur ou à un groupe. Lors de l’affectation de la tâche, le composant spécifie également le formulaire adaptatif ou le fichier PDF non interactif de la tâche. Le formulaire adaptatif est requis pour accepter une saisie des utilisateurs et un fichier PDF non interactif ou un formulaire adaptatif en lecture seule est utilisé pour les processus de révision uniquement.

Vous pouvez également utiliser le composant pour contrôler le comportement de la tâche. Par exemple : lors de la création d’un document d’enregistrement automatique, lors de l’affectation de la tâche à un utilisateur ou un groupe spécifique, lors de l’indication du chemin d’accès des données envoyées, lors de l’indication du chemin d’accès des données pré-renseignées et des actions par défaut. L’étape Affecter une tâche possède les propriétés suivantes :

* **[!UICONTROL Titre :]** titre de la tâche. Le titre s’affiche dans la boîte de réception AEM.
* **[!UICONTROL Description :]** description des opérations en cours dans la tâche. Ces informations sont utiles pour d’autres développeurs de processus lorsque vous travaillez dans un environnement de développement partagé.

* **[!UICONTROL Chemin d’accès de la vignette :]** chemin d’accès de la vignette de la tâche. Si aucun chemin n’est spécifié, une vignette par défaut s’affiche pour un formulaire adaptatif et une icône par défaut s’affiche pour un document d’enregistrement.
* **[!UICONTROL Phase de processus :]** un processus peut avoir plusieurs étapes. Ces phases sont affichées dans la boîte de réception AEM. Vous pouvez définir ces phases dans les propriétés du modèle (Sidekick > Page > Propriétés de la page > Phases).
* **[!UICONTROL Priorité :]** la priorité sélectionnée s’affiche dans la boîte de réception AEM. Les options disponibles sont les suivantes : Élevée, Moyenne et Faible. La valeur par défaut est Moyenne.
* **[!UICONTROL Date d’expiration :]** spécifiez le nombre de jours ou d’heures restant avant que la tâche soit affichée comme En retard. Si vous sélectionnez **[!UICONTROL Désactivé]**, la tâche n’est jamais marquée comme En retard. Vous pouvez également spécifier un gestionnaire de dépassement de délai pour effectuer des tâches spécifiées dès que la tâche est marquée comme En retard.

* **[!UICONTROL Jours :]** le nombre de jours restants pour terminer la tâche. Le nombre de jours est calculé à partir du jour de l’affectation de la tâche à un utilisateur. Si une tâche n’est pas terminée et dépasse le nombre de jours spécifié dans le champ Jours , alors si elle est sélectionnée, un gestionnaire de dépassement de délai est déclenché après la date d’échéance.
* **[!UICONTROL Heures :]** le nombre d’heures restantes pour terminer la tâche. Le nombre d’heures est calculé à partir de l’heure de l’affectation de la tâche à un utilisateur. Si une tâche n’est pas terminée et dépasse le nombre d’heures spécifié dans le champ Heures, alors si elle est sélectionnée, un gestionnaire de dépassement de délai est déclenché après l’heure d’échéance.
* **[!UICONTROL Expiration après l’échéance :]** sélectionnez cette option pour activer le champ Sélection du gestionnaire de dépassement de délai.
* **[!UICONTROL Gestionnaire de dépassement de délai :]** sélectionnez le script à exécuter lorsque l’étape Affecter une tâche dépasse l’échéance. Les scripts placés dans le référentiel CRX à l’emplacement [apps]/fd/dashboard/scripts/timeoutHandler peuvent être sélectionnés. Le chemin d’accès spécifié n’existe pas dans le référentiel CRX. Un administrateur crée le chemin d’accès avant de l’utiliser.
* **[!UICONTROL Sélectionner l’action et ajouter un commentaire depuis la dernière tâche dans Détails de la tâche :]** sélectionnez cette option pour afficher la dernière action qui a été effectuée et le dernier commentaire reçu dans la section Détails de la tâche.
* **[!UICONTROL Type :]** sélectionnez le type de document à remplir lors du lancement du processus. Vous pouvez sélectionner un formulaire adaptatif, un formulaire adaptatif en lecture seule, un document PDF non interactif.

<!-- , Interactive Communication Agent UI, or Interactive Communication Web Channel Document. -->


* **[!UICONTROL Utiliser un formulaire adaptatif :]** spécifiez la méthode pour localiser le formulaire adaptatif d’entrée. Cette option est disponible si vous sélectionnez les options Formulaire adaptatif ou Formulaire adaptatif en lecture seule dans la liste déroulante Type. Vous pouvez utiliser le formulaire adaptatif envoyé au processus, disponible à un chemin absolu ou disponible à un chemin dans une variable. Vous pouvez utiliser une variable de type chaîne pour spécifier le chemin d’accès.\
  Vous avez la possibilité d’associer plusieurs formulaires adaptatifs à un processus. Par conséquent, vous pouvez préciser un formulaire adaptatif au moment de l’exécution à l’aide des méthodes d’entrée disponibles.

<!-- 

* **[!UICONTROL Use Interactive Communication]**: Specify the method to locate the input interactive communication. You can use the interactive communication submitted to the workflow, available at an absolute path, or available at a path in a variable. You can use a variable of type String to specify the path. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 

> [!NOTE]
>
>You must have cm-agent-users and workflow-users group assignments to access Interactive Communications Agent UI in AEM inbox.  

-->

* **[!UICONTROL Chemin d’accès du formulaire adaptatif]** : indiquez le chemin d’accès du formulaire adaptatif. Vous pouvez utiliser le formulaire adaptatif qui est envoyé au processus, disponible à un chemin absolu, ou récupérer le formulaire adaptatif à partir d’un chemin d’accès stocké dans une variable de type de données Chaîne.
* **[!UICONTROL Sélectionnez le fichier PDF d’entrée en utilisant :]** spécifiez le chemin d’accès d’un document PDF non interactif. Le champ apparaît lorsque vous sélectionnez un document PDF non interactif dans le champ Type. Vous pouvez sélectionner le fichier PDF d’entrée à l’aide du chemin d’accès relatif à la charge utile, enregistré à un chemin absolu ou à l’aide d’une variable de type de données Document. Par exemple, [Répertoire_Charge_utile]/Workflow/PDF/credit-card.pdf. Le chemin n’existe pas dans le référentiel CRX. Un administrateur crée le chemin d’accès avant de l’utiliser. Vous devez activer l’option Document d’enregistrement ou posséder des formulaires adaptatifs basés sur un modèle de formulaire pour utiliser l’option Chemin d’accès du fichier PDF.
* **[!UICONTROL Une fois la tâche terminée, effectuer le rendu du formulaire adaptatif en tant que]** : lorsqu’une tâche est marquée comme terminée, vous pouvez effectuer le rendu du formulaire adaptatif en tant que formulaire adaptatif en lecture seule ou document PDF. Vous devez activer l’option Document d’enregistrement ou posséder des formulaires adaptatifs basés sur un modèle de formulaire pour effectuer le rendu du formulaire adaptatif en tant que Document d’enregistrement.
* **[!UICONTROL pré-renseignés :]** les champs répertoriés ci-dessous servent de données d’entrées pour la tâche :

   * **[!UICONTROL Sélectionner le fichier de données d’entrée en utilisant]** : chemin d’accès du fichier de données d’entrée (.json, .xml, .doc ou modèle de données de formulaire (FDM)). Vous pouvez récupérer le fichier de données d’entrée à l’aide d’un chemin d’accès relatif à la charge utile ou récupérer le fichier stocké dans une variable de type de données Document, XML ou JSON. Par exemple, le fichier contient les données envoyées pour le formulaire via une application de boîte de réception AEM. Voici un exemple de chemin d’accès : [Répertoire_Charge_utile]/workflow/data.
   * **[!UICONTROL Sélectionnez les pièces jointes d’entrée en utilisant :]** les pièces jointes disponibles à l’emplacement sont jointes au formulaire associé à la tâche. Le chemin d’accès peut être relatif à la payload ou récupérer la pièce jointe stockée dans une variable d’un document. Voici un exemple de chemin d’accès : [Payload_Directory]/attachments/. Vous pouvez spécifier des pièces jointes placées par rapport à la payload ou utiliser une variable de type document (Liste de tableaux > Document) pour spécifier une pièce jointe d’entrée pour le formulaire adaptatif.

  <!-- 
    
    * **[!UICONTROL Choose input JSON]**: Select an input JSON file using a path that is relative to payload or stored in a variable of Document, JSON, or Form Data Model (FDM) data type. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list.

    * **[!UICONTROL Choose a custom prefill service]**: Select the prefill service to retrieve the data and prefill the Interactive Communication Web channel document or the Agent UI.  
    
    * **[!UICONTROL Use the prefill service of the interactive communication selected above]**: Use this option to use the prefill service of the Interactive Communication defined in the Use Interactive Communication drop-down list. 
    
    -->

   * **[!UICONTROL Mappage des attributs de requête :]** utilisez la section Mappage des attributs de requête pour définir le [nom et la valeur de l’attribut de requête](work-with-form-data-model.md#bindargument). Récupérez les détails de la source de données en fonction du nom d’attribut et de la valeur spécifiés dans la requête. Vous pouvez définir une valeur d’attribut de requête à l’aide d’une valeur littérale ou d’une variable de type de données Chaîne.

  <!--  
     
     The prefill service and request attribute mapping options are available only if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 
     
     -->

* **[!UICONTROL Informations envoyées :]** les champs répertoriés ci-dessous servent d’emplacement de sortie pour la tâche :

   * **[!UICONTROL Enregistrer le fichier de données de sortie en utilisant]** : enregistrez le fichier de données (.json, .xml, .doc ou modèle de données de formulaire (FDM)). Le fichier de données contient des informations envoyées via le formulaire associé. Vous pouvez enregistrer le fichier de données de sortie à l’aide d’un chemin d’accès relatif à la charge utile ou le stocker dans une variable de type de données Document, XML ou JSON. Par exemple, [Répertoire_Charge_utile]/Workflow/data, où les données correspondent à un fichier.
   * **[!UICONTROL Enregistrez les pièces jointes en utilisant :]** enregistrez les pièces jointes de formulaire fournies dans une tâche. Vous pouvez enregistrer les pièces jointes à l’aide d’un chemin d’accès relatif à la charge utile ou les stocker dans une variable de liste de tableau de type de données Document.
   * **[!UICONTROL Enregistrez le document d’enregistrement en utilisant :]** chemin d’accès pour enregistrer un fichier de document d’enregistrement. Par exemple,[ Répertoire_Charge_utile]/DocumentofRecord/credit-card.pdf. Vous pouvez enregistrer le document d’enregistrement à l’aide d’un chemin d’accès relatif à la charge utile ou le stocker dans une variable de type de données Document. Si vous sélectionnez l’option **[!UICONTROL Relatif à la charge utile]**, le document d’enregistrement n’est pas généré si le champ de chemin d’accès est laissé vide. Cette option est disponible uniquement si vous sélectionnez l’option Formulaire adaptatif dans la liste déroulante Type.

  <!-- 
    
    * **[!UICONTROL Save Web Channel data using]**: Save the Web Channel data file using a path that is relative to the payload or store it in a variable of Document, JSON, or Form Data Model (FDM) data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. c
    * **[!UICONTROL Save PDF document using]**: Save the PDF document using a path that is relative to the payload or store it in a variable of Document data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list.
    <!-- * **[!UICONTROL Save layout template using]**: Save the layout template using a path that is relative to the payload or store it in a variable of Document data type. The [layout template](layout-design-details.md) refers to an XDP file that you create using Forms Designer. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. 
    
    -->

* **[!UICONTROL Personne désignée]** > **[!UICONTROL Options d’affectation]** : indiquez la méthode à utiliser pour affecter la tâche à un utilisateur. Vous pouvez affecter la tâche de manière dynamique à un utilisateur ou un groupe à l’aide du script Programme de sélection des participants ou affecter la tâche à un utilisateur ou à un groupe AEM spécifique.
* **[!UICONTROL Programme de sélection des participants :]** cette option est disponible lorsque l’option **[!UICONTROL Sélectionner de manière dynamique un utilisateur ou un groupe]** est activée dans le champ Options d’affectation. Vous pouvez utiliser un ECMAScript ou un service pour sélectionner un utilisateur ou une utilisatrice, ou un groupe de manière dynamique. Pour plus d’informations, voir [Création d’une étape de participant dynamique Adobe Experience Manager personnalisée](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=fr&CID=RedirectAEMCommunityKautuk).

* **[!UICONTROL Participants]** : le champ est disponible lorsque l’option **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** est sélectionnée dans le champ Programme de **[!UICONTROL sélection des participants]**. Le champ vous permet de sélectionner des utilisateurs, des utilisatrices ou des groupes pour l’option RandomParticipantChooser.

* **[!UICONTROL Personne désignée]** : le champ est disponible lorsque l’option **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]** est sélectionnée dans le champ **[!UICONTROL Programme de sélection des participants]**. Ce champ vous permet de sélectionner une variable de type Chaîne pour définir la personne désignée.

* **[!UICONTROL Arguments :]** le champ est disponible lorsqu’un script autre que le script RandomParticipantChoose est sélectionné dans le champ Programme de sélection des participants. Le champ vous permet de fournir une liste d’arguments séparés par des virgules pour le script sélectionné dans le champ Programme de sélection des participants .

* **[!UICONTROL Utilisateur ou groupe]** : la tâche est affectée à un utilisateur ou à un groupe sélectionné. Cette option est disponible lorsque l’option **[!UICONTROL À un utilisateur ou un groupe spécifique]** est activée dans le champ **[!UICONTROL Options d’affectation]**. Le champ répertorie tous les utilisateurs et groupes du groupe [!DNL workflow-users].\
  Le menu déroulant **[!UICONTROL Utilisateur ou groupe]** répertorie les utilisateurs et les groupes auxquels l’utilisateur connecté a accès. L’affichage du nom d’utilisateur dépend des autorisations d’accès sur le nœud **[!UICONTROL users]** dans le référentiel crx pour cet utilisateur particulier.

* **[!UICONTROL Envoyer une notification par e-mail :]** sélectionnez cette option pour envoyer des notifications par e-mail à la personne désignée. Ces notifications sont envoyées lorsqu’une tâche est affectée à un utilisateur ou à un groupe. Vous pouvez utiliser l’option **[!UICONTROL Adresse électronique du destinataire]** pour spécifier le mécanisme de récupération de l’adresse électronique.

* **[!UICONTROL Adresse e-mail du destinataire]** : vous pouvez stocker une adresse e-mail dans une variable, utiliser un littéral pour spécifier une adresse e-mail permanente ou utiliser l’adresse e-mail par défaut de la personne désignée spécifiée dans son profil. Vous pouvez utiliser le littéral ou une variable pour spécifier l’adresse électronique d’un groupe. L’option de variable permet de récupérer et d’utiliser de manière dynamique une adresse électronique. L’option **[!UICONTROL Utiliser l’adresse électronique par défaut de la personne désignée]** n’est destinée qu’à une seule personne désignée. Dans ce cas, l’adresse e-mail stockée dans le profil utilisateur de la personne désignée est utilisée.

* **[!UICONTROL Modèle d’e-mail HTML]** : sélectionnez le modèle de l’e-mail de notification. Pour modifier un modèle, modifiez le fichier situé à l’emplacement /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt dans le référentiel CRX.
* **[!UICONTROL Autoriser la délégation à :]** la boîte de réception AEM permet à l’utilisateur connecté de déléguer le processus affecté à un autre utilisateur. Vous pouvez déléguer au sein du même groupe ou à l’utilisateur ou l’utilisatrice du workflow d’un autre groupe. Si la tâche est affectée à un seul utilisateur ou une seule utilisatrice et que la fonction **[!UICONTROL Autoriser la délégation aux membres du groupe désigné]** est sélectionnée, alors il n’est pas possible de déléguer la tâche à un autre utilisateur ou une autre utilisatrice ou un autre groupe.
* **[!UICONTROL Paramètres de partage]** : la boîte de réception AEM propose des options permettant de partager une ou toutes les tâches de la boîte de réception avec un autre utilisateur :
   * Lorsque l’option **[!UICONTROL Autoriser les personnes désignées à partager explicitement dans la boîte de réception]** est sélectionnée, l’utilisateur peut sélectionner la tâche dans la boîte de réception AEM et la partager avec un autre utilisateur AEM.
   * Lorsque l’option **[!UICONTROL Autoriser les personnes désignées à partager via le partage de boîte de réception]** est sélectionnée et que les utilisateurs partagent leurs éléments de boîte de réception ou permettent à d’autres utilisateurs d’accéder à leurs éléments de boîte de réception, seules les tâches dont l’option mentionnée précédemment est activée sont partagées avec d’autres utilisateurs.
   * Lorsque **[!UICONTROL Autoriser la personne désignée à déléguer à l’aide des paramètres Absence du bureau]** est sélectionné. La personne désignée peut activer l’option de délégation de la tâche à d’autres utilisateurs, ainsi que d’autres options d’absence du bureau. Toute nouvelle tâche attribuée à l’utilisateur absent du bureau est automatiquement déléguée (affectée) aux utilisateurs mentionnés dans les paramètres d’absence du bureau.

  Il permet à d&#39;autres utilisateurs de sélectionner des tâches affectées alors qu&#39;ils sont absents du bureau et qu&#39;ils ne peuvent pas travailler sur des tâches affectées.

* **[!UICONTROL Actions]** > **[!UICONTROL Actions par défaut]** : les actions Prêt à l’emploi, Envoyer, Enregistrer et Réinitialiser sont disponibles. Par défaut, toutes les actions par défaut sont activées.
* **[!UICONTROL Variable d’itinéraire :]** nom de la variable d’itinéraire. La variable d’itinéraire capture les actions personnalisées qu’un utilisateur sélectionne dans la boîte de réception AEM.
* **[!UICONTROL Itinéraires :]** une tâche peut se composer de plusieurs itinéraires. Lorsque cette option est sélectionnée dans la boîte de réception AEM, l’itinéraire renvoie une valeur et les branches du processus en fonction de l’itinéraire sélectionné. Vous pouvez stocker des itinéraires dans une variable de tableau de types de données Chaîne ou sélectionner **[!UICONTROL Littéral]** pour ajouter manuellement des itinéraires.

* **[!UICONTROL Titre d’itinéraires]** : indiquez le titre de l’itinéraire. Elle s’affiche dans la boîte de réception AEM.
* **[!UICONTROL Icône Coral]** : spécifiez l’attribut HTML d’une icône Coral. La bibliothèque Adobe CoralUI fournit un vaste ensemble d’icônes tactiles. Vous pouvez choisir et utiliser une icône pour l’itinéraire. Elle s’affiche avec le titre dans la boîte de réception AEM. Si vous stockez les itinéraires dans une variable, ils utilisent une icône de corail Balises par défaut.
* **[!UICONTROL Autoriser les personnes désignées à ajouter des commentaires]** : sélectionnez cette option pour activer les commentaires pour la tâche. Une personne désignée peut ajouter des commentaires à partir de la boîte de réception AEM au moment de l’envoi de la tâche.
* **[!UICONTROL Enregistrer le commentaire dans la variable]** : enregistrez le commentaire dans une variable de type de données Chaîne. Cette option s’affiche uniquement si vous cochez la case **[!UICONTROL Autoriser la personne désignée à ajouter un commentaire]**.

* **[!UICONTROL Autoriser la personne désignée à ajouter des pièces jointes à la tâche]** : sélectionnez cette option pour activer les pièces jointes pour la tâche. Une personne désignée peut ajouter des pièces jointes à partir de la boîte de réception AEM au moment de l’envoi de la tâche. Vous pouvez également limiter la taille maximale **[!UICONTROL (Taille maximale du fichier)]** d’une pièce jointe. La taille par défaut est de 2 Mo.

* **[!UICONTROL Enregistrez les pièces jointes de la tâche de sortie en utilisant]** : indiquez l’emplacement du dossier des pièces jointes. Vous pouvez enregistrer les pièces jointes de la tâche de sortie à l’aide d’un chemin d’accès relatif à la charge utile ou dans une variable d’un tableau de types de données de document. Cette option s’affiche uniquement si vous cochez la case **[!UICONTROL Autoriser les personnes désignées à ajouter des pièces jointes à la tâche]** et sélectionnez **[!UICONTROL Formulaire adaptatif]**, **[!UICONTROL Formulaire adaptatif en lecture seule]** ou **[!UICONTROL document PDF non interactif]** dans la liste déroulante **[!UICONTROL Type]**. dans l’onglet **[!UICONTROL Formulaire/Document]**.

* **[!UICONTROL Utiliser des métadonnées personnalisées :]** sélectionnez cette option pour activer le champ de métadonnées personnalisées. Les métadonnées personnalisées sont utilisées dans les modèles de courrier électronique.
* **[!UICONTROL Métadonnées personnalisées :]** sélectionnez une métadonnée personnalisée pour les modèles de courrier électronique. Les métadonnées personnalisées sont disponibles dans le référentiel crx-repository sous apps/fd/dashboard/scripts/metadataScripts. Le chemin d’accès spécifié n’existe pas dans le référentiel CRX. Un administrateur crée le chemin d’accès avant de l’utiliser. Vous pouvez également utiliser un service pour les métadonnées personnalisées. Vous pouvez également étendre l’interface `WorkitemUserMetadataService` afin de fournir des métadonnées personnalisées.
* **[!UICONTROL Afficher les données des étapes précédentes]** : sélectionnez cette option pour permettre aux personnes désignées d’afficher les personnes désignées précédentes, les actions déjà effectuées sur la tâche, les commentaires ajoutés à la tâche et le document d’enregistrement de la tâche terminée, le cas échéant.
* **[!UICONTROL Afficher les données des étapes suivantes :]** sélectionnez cette option pour permettre à la personne actuellement désignée d’afficher l’action effectuée et les commentaires ajoutés à la tâche par les personnes désignées suivantes. Cette option permet également à la personne actuellement désignée d’afficher un document d’enregistrement de la tâche terminée, le cas échéant.
* **[!UICONTROL Visibilité du type de données :]** par défaut, une personne désignée peut afficher un document d’enregistrement, des personnes désignées, une action effectuée et les commentaires des personnes désignées précédentes et suivantes qui ont été ajoutés. Utilisez l’option de visibilité du type de données pour limiter le type de données visibles pour les personnes désignées.

>[!NOTE]
>
>Les options permettant d’enregistrer l’étape Affecter une tâche en tant que brouillon et de récupérer l’historique de l’étape Affecter une tâche sont désactivées lorsque vous configurez un modèle de workflow AEM pour le stockage de données externe. En outre, dans la boîte de réception, l’option d’enregistrement est désactivée.

## Étape Convertir en PDF/A {#convert-pdfa}

Le PDF/A est un format d’archivage prévu pour la conservation à long terme du contenu d’un document, en incorporant les polices et en décompressant le fichier. Par conséquent, un document PDF/A est généralement plus volumineux qu’un document PDF standard. Vous pouvez utiliser l’étape ***Convertir en PDF/A*** dans un workflow AEM pour convertir vos documents PDF au format PDF/A.

L’étape de conversion en PDF/A présente les propriétés suivantes :

**[!UICONTROL Document d’entrée]** : le document d’entrée peut être relatif à la payload, comporter un chemin d’accès absolu, être fourni en tant que payload ou être stocké dans une variable de type de données Document.

**[!UICONTROL Options de conversion]** : cette propriété permet de spécifier les paramètres de conversion des documents PDF en documents PDF/A. Les différentes options disponibles sous cet onglet sont les suivantes :
* **[!UICONTROL Conformité]** : indique la norme à laquelle le document PDF/A de sortie doit se conformer. Différentes normes PDF sont prises en charge, telles que PDF/A-1b, PDF/A-2b ou PDF/A-3b.
* **[!UICONTROL Niveau de résultat]** : indique le niveau de résultat de la sortie de conversion, qui peut être PassFail, Summary ou Detailed.
* **[!UICONTROL Espace colorimétrique]** : indique l’espace colorimétrique prédéfini en tant que S_RGB, COATED_FOGRA27, JAPAN_COLOR_COATED ou SWOP qui peut être utilisé pour les fichiers de sortie au format PDF/A.
* **[!UICONTROL Contenu facultatif]** : autorisez uniquement la visibilité d’objets graphiques et/ou d’annotations spécifiques dans le document PDF/A de sortie lorsqu’un ensemble de critères spécifié est rempli.

**[!UICONTROL Documents de sortie]** : indique l’emplacement d’enregistrement du fichier de sortie. Le fichier de sortie peut être enregistré à un emplacement relatif à la payload, remplace la payload si celle-ci est un fichier, ou dans une variable de type de données Document.


## Étape Envoyer un e-mail {#send-email-step}

Utilisez l’étape Envoyer un courrier électronique pour, par exemple, envoyer un courrier électronique avec un document d’enregistrement, un lien d’une <!-- , link of an interactive communication--> de formulaire adaptatif ou avec un document PDF joint. L’étape Envoyer un e-mail prend en charge l’[e-mail HTML](https://en.wikipedia.org/wiki/HTML_email). Les e-mails HTML sont réactifs et s’adaptent à la taille de l’écran et au client de messagerie du ou de la destinataire. Vous pouvez utiliser un modèle d’e-mail HTML pour définir l’apparence, le modèle de couleurs et le comportement de l’e-mail.

L’étape Envoyer un courrier électronique utilise le service de messagerie Day CQ pour envoyer des messages. Avant d’utiliser l’étape Envoyer un courrier électronique, assurez-vous que le service de messagerie est configuré. Par défaut, seuls les protocoles HTTP et HTTPs sont pris en charge. [Contactez l’équipe d’assistance](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=fr#sending-email) pour activer les ports afin d’envoyer des e-mails et d’activer le protocole SMTP pour votre environnement. La restriction contribue à améliorer la sécurité de la plateforme.

L’étape Envoyer un courrier électronique possède les propriétés suivantes :

**[!UICONTROL Titre :]** le titre de l’étape permet d’identifier l’étape dans l’éditeur du processus.

**[!UICONTROL Description :]** la description est utile pour d’autres développeurs de processus lorsque vous travaillez dans un environnement de développement partagé.

**[!UICONTROL Objet du courrier électronique]** : l’objet peut être récupéré à partir des métadonnées d’un processus, spécifié manuellement ou récupéré à partir de la valeur stockée dans une variable. Faites votre choix parmi les options suivantes :

* **[!UICONTROL Littéral :]** spécifiez manuellement un objet.
* **[!UICONTROL Récupérer à partir des métadonnées du processus]** : récupérez l’objet d’une propriété de métadonnées.
* **[!UICONTROL Variable]** : récupérez l’objet de la valeur stockée dans une variable de type de données Chaîne.

**[!UICONTROL Modèle de courrier électronique HTML]** : modèle HTML pour le courrier électronique. Vous pouvez spécifier des variables dans un modèle de courrier électronique. L’étape Envoyer un courrier électronique extrait et affiche toutes les variables incluses dans un modèle pour les entrées.

**[!UICONTROL Métadonnées du modèle de courrier électronique :]** la valeur des variables du modèle de courrier électronique peut être une valeur spécifiée par l’utilisateur, le chemin d’accès d’un actif sur le serveur de création ou de publication, une image ou une propriété de métadonnées de processus.

* **[!UICONTROL Littéral]** : utilisez cette option lorsque vous connaissez la valeur exacte à spécifier. Par exemple, [example@example.com](mailto:example@example.com).

* **[!UICONTROL Métadonnées de processus :]** utilisez cette option lorsque la valeur à utiliser est enregistrée dans une propriété de métadonnées de processus. Après avoir sélectionné l’option, saisissez le nom de la propriété de métadonnées dans la zone de texte vide sous l’option Métadonnées de workflow. Par exemple, emailAddress.

<!-- 

* **[!UICONTROL Asset URL]**: Use the option to embed a web link of an interactive communication to the email. After selecting the option, browse and choose the interactive communication to embed. The asset can reside on the author or the publish server. 

-->

* **[!UICONTROL Image :]** utilisez cette option pour incorporer une image dans l’e-mail. Après avoir sélectionné cette option, recherchez et sélectionnez l’image. L’option image est uniquement disponible pour les balises d’image (&lt;img src=&quot;&#42;&quot;/>) disponibles dans le modèle d’e-mail.

**[!UICONTROL Adresse e-mail du destinataire/expéditeur]** : sélectionnez l’option **[!UICONTROL Littéral]** pour spécifier manuellement une adresse e-mail ou sélectionnez l’option **[!UICONTROL Récupérer à partir des métadonnées de processus]** pour récupérer l’adresse e-mail d’une propriété de métadonnées. Vous pouvez également spécifier une liste de tableaux de propriété de métadonnées pour l’option **[!UICONTROL Récupérez à partir des métadonnées de processus]**. Sélectionnez l’option **[!UICONTROL Variable]** pour récupérer l’adresse électronique à partir de la valeur stockée dans une variable de type de données Chaîne.

* **[!UICONTROL La pièce jointe du fichier :]** l’actif disponible à l’emplacement spécifié est joint au courrier électronique. Le chemin d’accès de l’actif peut être lié à la charge utile ou au chemin d’accès absolu. Voici un exemple de chemin d’accès : [Répertoire_Charge_utile]/attachments/.

Sélectionnez l’option **[!UICONTROL Variable]** pour récupérer le fichier joint stocké dans une variable de type de données Document, XML ou JSON.

**[!UICONTROL Nom de fichier :]** nom du fichier de la pièce jointe au courrier électronique. L’étape Envoyer un courrier électronique remplace le nom de fichier original de la pièce jointe par le nom de fichier spécifié. Le nom peut être spécifié manuellement ou récupéré à partir d’une propriété de métadonnées de processus ou d’une variable. Utilisez l’option **[!UICONTROL Littéral]** lorsque vous connaissez la valeur exacte à spécifier. Utilisez l’option **[!UICONTROL Variable]** pour récupérer le nom du fichier à partir de la valeur stockée dans une variable de type de données Chaîne. Utilisez l’option **[!UICONTROL Récupérer à partir des métadonnées de processus]** lorsque la valeur à utiliser est enregistrée dans une propriété de métadonnées de processus.

## Etape Générer un document d’enregistrement {#generate-document-of-record-step}

Lorsqu’un formulaire est rempli ou envoyé, vous pouvez conserver un enregistrement du formulaire, au format imprimé ou au format de document. Ici, il s’agit de document d’enregistrement (DOR). Vous pouvez utiliser l’étape Générer un document d’enregistrement pour créer une version PDF interactive ou en lecture seule d’un formulaire adaptatif. La version PDF contient des informations remplies dans le formulaire avec la mise en page du formulaire adaptatif.

L’étape Document d’enregistrement possède les propriétés suivantes :

**[!UICONTROL Utiliser un formulaire adaptatif]** : spécifiez la méthode pour localiser le formulaire adaptatif d’entrée. Vous pouvez utiliser le formulaire adaptatif envoyé au processus, disponible à un chemin absolu ou disponible à un chemin dans une variable. Vous pouvez utiliser une variable de type de données Chaîne pour spécifier le chemin d’accès dans le champ **[!UICONTROL Sélectionner la variable à résoudre]**.\
Vous avez la possibilité d’associer plusieurs formulaires adaptatifs à un processus. Par conséquent, vous pouvez préciser un formulaire adaptatif au moment de l’exécution à l’aide des méthodes d’entrée disponibles.

**[!UICONTROL Chemin d’accès du formulaire adaptatif]** : indiquez le chemin d’accès du formulaire adaptatif. Le champ est disponible lorsque vous sélectionnez l’option **[!UICONTROL Disponible à un chemin d’accès absolu]** dans le champ **[!UICONTROL Utiliser le formulaire adaptatif]**.

**[!UICONTROL Sélectionnez le chemin d’accès des données d’entrée :]** chemin d’accès des données d’entrée pour le formulaire adaptatif. Vous pouvez conserver les données à un emplacement relatif à la charge utile, spécifier un chemin d’accès absolu aux données ou récupérer les données stockées dans une variable de type Document, JSON ou XML. Les données d’entrée sont fusionnées avec le formulaire adaptatif pour créer un document d’enregistrement.

**[!UICONTROL Sélectionnez le chemin de pièce jointe d’entrée en utilisant]** : chemin des pièces jointes. Ces pièces jointes sont incluses dans le document d’enregistrement. Vous pouvez conserver les pièces jointes à un emplacement relatif à la charge utile, spécifier un chemin absolu pour les pièces jointes ou récupérer les pièces jointes stockées dans une variable de tableau de type de données Document.

Si vous spécifiez le chemin d’accès d’un dossier (des pièces jointes, par exemple), tous les fichiers directement disponibles dans le dossier sont joints au document d’enregistrement. Si des fichiers sont présents dans les dossiers directement disponibles dans le chemin d’accès de la pièce jointe spécifiée, les fichiers sont inclus dans le document d’enregistrement en tant que pièces jointes. Les dossiers présents dans les dossiers directement disponibles ces fichiers sont ignorés.

**[!UICONTROL Enregistrez Chemin d’accès du document d’enregistrement généré :]** spécifiez l’emplacement pour conserver un fichier de document d’enregistrement. Vous pouvez choisir de remplacer le dossier de payload, de placer le document d’enregistrement à un emplacement du répertoire de payload ou de stocker le document d’enregistrement dans une variable de type de données Document.

**[!UICONTROL Paramètres régionaux]** : spécifiez la langue du document d’enregistrement. Sélectionnez **[!UICONTROL Littéral]** pour sélectionner les paramètres régionaux dans une liste déroulante ou **[!UICONTROL Variable]** pour récupérer les paramètres régionaux à partir de la valeur stockée dans une variable de type de données Chaîne. Vous devez définir le code des paramètres régionaux lors du stockage de la valeur du paramètre régional dans une variable. Par exemple, spécifiez **en_US** pour l’anglais et **fr_FR** pour le français.

## Étape Invoquer DDX {#invokeddx}

DDX (Document Description XML) est un langage de marquage déclaratif dont les éléments représentent des blocs de création de documents. Ces blocs de création comportent des documents PDF et XDP, ainsi que d’autres éléments tels que des commentaires, des signets et du texte avec style. DDX définit un ensemble d’opérations qui peut être appliqué à un ou plusieurs documents d’entrée pour générer un ou plusieurs documents de sortie. Un DDX unique peut être utilisé avec un éventail de documents source. Vous pouvez suivre l’étape ***Appeler DDX*** dans un workflow AEM pour effectuer différentes opérations, telles que l’assemblage ou le désassemblage de documents, la création et la modification de Forms Acrobat et XFA, etc., décrites dans la documentation de référence [DDX](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf).

L’étape Invoquer DDX présente les propriétés suivantes :

**[!UICONTROL Documents d’entrée]** : utilisée pour définir les propriétés d’un document d’entrée. Les différentes options disponibles sous cet onglet sont les suivantes :
* **[!UICONTROL Spécifier DDX à l’aide de]** : spécifie le document d’entrée relatif à la payload, dispose d’un chemin d’accès absolu, peut être fourni comme payload ou stocké dans une variable de type de données Document.
* **[!UICONTROL Créer le mappage à partir de la payload]** : ajoutez tous les documents dans le dossier de payload au mappage de document d’entrée pour appeler l’API dans Assembler. Le nom du nœud pour chaque document est utilisé comme clé dans le mappage.
* **[!UICONTROL Map de document d’entrée]** : cette option est utilisée pour ajouter plusieurs entrées à l’aide du bouton **[!UICONTROL AJOUTER]**. Chaque entrée représente la clé du document dans le mappage et la source du document.

**[!UICONTROL Options d’environnement]** : cette option est utilisée pour définir les paramètres de traitement de l’étape Invoquer l’API. Les différentes options disponibles sous cet onglet sont les suivantes :
* **[!UICONTROL Valider uniquement]** : vérifie la validité du document DDX d’entrée.
* **[!UICONTROL Échec en cas d’erreur]** : valeur booléenne indiquant si le service d’appel de l’API échoue en cas d’erreur ou non. Par défaut, sa valeur est définie sur False.
* **[!UICONTROL Premier numéro Bates]** : indique le nombre qui s’incrémente automatiquement. Ce nombre qui s’incrémente automatiquement s’affiche automatiquement sur chaque page consécutive.
* **[!UICONTROL Style par défaut]** : définit le style par défaut du fichier de sortie.

>[!NOTE]
>
>Les options d’environnement sont synchronisées avec les API HTTP.

**[!UICONTROL Documents de sortie]** : indique l’emplacement d’enregistrement du fichier de sortie. Les différentes options disponibles sous cet onglet sont les suivantes :
* **[!UICONTROL Enregistrer la sortie dans payload]** : enregistre les documents de sortie sous le dossier de payload, ou remplace la payload, si celle-ci est un fichier.
* **[!UICONTROL Mappage du document de sortie]** : spécifie l’emplacement d’enregistrement explicite de chaque fichier de document en ajoutant une entrée par document. Chaque entrée représente le document et l’emplacement où l’enregistrer. S’il existe plusieurs documents de sortie, cette option est utilisée.

## Étape Invoquer le service de modèle de données de formulaire (FDM) {#invoke-form-data-model-service-step}

Vous pouvez utiliser l’[[!DNL AEM Forms] intégration de données](data-integration.md) pour configurer des sources de données disparates et vous y connecter. Ces sources de données peuvent être un service web, un service REST, un service OData et une solution CRM. L’intégration de données [!DNL AEM Forms] vous permet de créer un modèle de données de formulaire (FDM) regroupant divers services afin d’effectuer des opérations de récupération, d’ajout et de mise à jour de données sur la base de données configurée. Vous pouvez utiliser **[!UICONTROL l’étape Invoquer le service de modèle de données de formulaire]** pour sélectionner un modèle de données de formulaire (FDM) et utiliser les services du FDM pour récupérer, mettre à jour ou ajouter des données aux sources de données disparates.

Pour expliquer les entrées des champs de l’étape, le tableau de base de données et le fichier JSON suivants servent d’exemple :

**[!UICONTROL Exemple de tableau CustomerDetails]**

<table>
 <tbody> 
  <tr> 
   <td>Propriété</td> 
   <td>Valeur<br /> </td> 
  </tr> 
  <tr> 
   <td>Prénom<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>Nom de famille</td> 
   <td>Rose</td> 
  </tr> 
  <tr> 
   <td>ID de cliente</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>Adresse électronique<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**[!UICONTROL Exemple de fichier JSON]**

```json
  { 
    customer: { 
     firstName: "Sarah", 
     lastName:"Rose", 
     customerId: "1", 
     emailAddress:"srose@we.info" 
   }, 
    insurance: {
     customerId: "1", 
    policyType: "Premium,
    policyNumber: "Premium-521499",
    customerDetails: { 
     firstName: "Sarah",
     lastName: "Rose",
     customerId: "1",
     emailAddress: "srose@we.info" 
    }
   }
  }
```

L’étape Invoquer le service de modèle de données de formulaire (FDM) comporte les champs répertoriés ci-dessous pour faciliter les opérations du modèle de données de formulaire (FDM) :

* **[!UICONTROL Titre :]** titre de l’étape. Il permet d’identifier les étapes dans l’éditeur de workflow.
* **[!UICONTROL Description :]** la description est utile pour d’autres développeurs de processus lorsque vous travaillez dans un environnement de développement partagé.

* **[!UICONTROL Chemin d’accès du modèle de données de formulaire]** : recherchez et sélectionnez un modèle de données de formulaire (FDM) présent sur le serveur.

* **[!UICONTROL Erreurs et validations]** : cette option vous permet de capturer des messages d’erreur et de spécifier des options de validation pour les données récupérées et envoyées aux sources de données. Grâce à ces modifications, vous pouvez vous assurer que les données transmises à l’étape du service Invoquer le service de modèle de données de formulaire (FDM) respectent les contraintes de données définies par la source de données. Pour plus d’informations, voir [Validation automatisée des données d’entrée](work-with-form-data-model.md#automated-validation-of-input-data).

* **[!UICONTROL Niveau de validation]** : il existe trois catégories de validation : De base, Complète et Désactivée :

   * Complète : toutes les contraintes sont validées.
   * De base : contraintes obligatoires et nulles uniquement.
   * Désactivée : aucune validation n’a lieu.

* **[!UICONTROL Arrêter le processus en cas d’échec]** : lorsqu’une contrainte n’est pas validée, le processus est arrêté.

* **[!UICONTROL Stocker le code d’erreur dans une variable]** : vous pouvez stocker un code d’erreur dans une [variable de type Chaîne](variable-in-aem-workflows.md).

* **[!UICONTROL Stocker le message d’erreur dans une variable]** : vous pouvez stocker un message d’erreur dans une [variable de type Chaîne](variable-in-aem-workflows.md).

* **[!UICONTROL Stocker les détails de l’erreur dans une variable]** : vous pouvez stocker les détails dune erreur dans une [variable de type JSON](variable-in-aem-workflows.md).

* **[!UICONTROL Service]** : liste des services fournis par le modèle de données de formulaire (FDM) sélectionné.
* **[!UICONTROL Entrée des services]** > **[!UICONTROL Fournir des données d’entrée à l’aide d’un fichier JSON, de l’option Littéral,d’une variable, de métadonnées de processus]** : un service peut avoir plusieurs arguments. Sélectionnez cette option pour obtenir la valeur des arguments de service à partir d’une propriété de métadonnées de processus, d’un objet JSON ou d’une variable, ou saisissez directement la valeur dans la zone prévue à cet effet :

   * **[!UICONTROL Littéral]** : utilisez cette option lorsque vous connaissez la valeur exacte à spécifier. Par exemple, srose@we.info.
   * **[!UICONTROL Variable :]** utilisez cette option pour récupérer la valeur stockée dans une variable.
   * **[!UICONTROL Récupérer à partir des métadonnées de processus :]** utilisez cette option lorsque la valeur à utiliser est enregistrée dans une propriété de métadonnées de processus. Par exemple, emailAddress.

   * **[!UICONTROL Relatif à la charge]** : utilisez cette option pour récupérer le fichier joint enregistré dans un chemin d’accès relatif à la charge. Sélectionnez l’option et indiquez le nom du dossier contenant le fichier joint ou indiquez le nom du fichier joint dans la zone de texte.

     >[!NOTE]
     >
     > L’étape de workflow **Appeler le modèle de données de formulaire** prend en charge les métadonnées côté workflow pour les tableaux de pièces jointes codées en Base64 dans les modèles de données de formulaire basés sur une liste [SharePoint](/help/forms/connect-forms-to-sharepoint-list.md) et permet aux workflows de transmettre, stocker et récupérer des métadonnées telles que le nom de fichier, le type MIME ou les propriétés personnalisées des pièces jointes.
     > ![Pièces jointes de la liste SP](/help/edge/docs/forms/assets/workflow-sp-list.png)
     >
     > Le dossier Relatif à la charge comprend une pièce jointe à l’emplacement `attachment`. Spécifiez `attachment` dans la zone de texte après avoir sélectionné l’option **[!UICONTROL Relatif à la charge]**.

   * **[!UICONTROL JSON Dot Notation :]** utilisez cette option lorsque la valeur à utiliser figure dans un fichier JSON. Par exemple, insurance.customerDetails.emailAddress. L’option JSON Dot Notation est disponible uniquement si l’option Mapper les champs de saisie depuis le fichier JSON d’entrée est sélectionnée.
   * **[!UICONTROL Mapper les champs de saisie depuis le fichier JSON d’entrée]** : spécifiez le chemin d’accès d’un fichier JSON pour obtenir la valeur d’entrée des arguments de service à partir du fichier JSON. Le chemin d’accès du fichier JSON peut être relatif à la charge utile, un chemin absolu, ou vous pouvez sélectionner un document JSON d’entrée à l’aide d’une variable de type JSON ou Modèle de données de formulaire (FDM).

* **[!UICONTROL Entrée des services]** > **[!UICONTROL Fournir des données d’entrée à l’aide d’une variable ou d’un fichier JSON]** : sélectionnez cette option pour obtenir des valeurs pour tous les arguments d’un fichier JSON enregistré à un chemin absolu, à un chemin relatif à la charge utile ou dans une variable.
* **[!UICONTROL Sélectionnez le document JSON d’entrée en utilisant]** : fichier JSON contenant des valeurs pour tous les arguments de service. Le chemin d’accès du fichier JSON peut être **[!UICONTROL relatif à la charge utile]** ou un **[!UICONTROL chemin d’accès absolu]**. Vous pouvez également récupérer le document JSON d’entrée à l’aide d’une variable de type de données JSON ou Modèle de données de formulaire (FDM).

* **[!UICONTROL JSON Dot Notation :]** laissez le champ vide pour utiliser tous les objets du fichier JSON spécifié en tant qu’entrée pour les arguments de service. Pour lire un objet JSON spécifique à partir du fichier JSON spécifié en tant qu’entrée pour des arguments de service, spécifiez la notation par point pour l’objet JSON. Par exemple, si vous avez un fichier JSON identique à l’un des fichiers indiqué au début de la section, spécifiez insurance.customerDetails pour fournir tous les détails d’un client en tant qu’entrée du service.
* **[!UICONTROL Sortie de service]** > **[!UICONTROL Mapper et écrire les valeurs de sortie dans les métadonnées]** : sélectionnez cette option pour enregistrer les valeurs de sortie en tant que propriétés du nœud de métadonnées de l’instance de processus dans le référentiel CRX. Indiquez le nom de la propriété de métadonnées et sélectionnez l’attribut de sortie de service correspondant à mapper avec la propriété de métadonnées, par exemple, mappez la valeur numéro_de_téléphone renvoyé par le service de sortie avec la propriété numéro_de_téléphone des métadonnées du workflow. De même, vous pouvez stocker la sortie dans une variable de type Long. Lorsque vous sélectionnez une propriété pour l’**[!UICONTROL attribut de sortie de service à mapper]**, seules les variables capables de stocker les données de la propriété sélectionnée sont renseignées pour l’option **[!UICONTROL Enregistrer la sortie dans]**.

* **[!UICONTROL Sortie de service]** > **[!UICONTROL Enregistrer la sortie dans une variable ou un fichier JSON]** : sélectionnez cette option pour enregistrer les valeurs de sortie dans un fichier JSON à un chemin absolu, à un chemin relatif à la charge utile ou dans une variable.
* **[!UICONTROL Enregistrez le document JSON de sortie à l’aide des options suivantes :]** enregistrez le fichier JSON de sortie. Le chemin d’accès du fichier JSON peut être relatif à la charge utile ou à un chemin d’accès absolu. Vous pouvez également enregistrer le fichier JSON de sortie à l’aide d’une variable de type de données JSON ou Modèle de données de formulaire (FDM).



## Étape Signer le document {#sign-document-step}

L’étape Signer le document vous permet d’utiliser [!DNL Adobe Sign] pour signer des documents. Lorsque vous utilisez l’étape de processus [!DNL Adobe Sign] pour signer un formulaire adaptatif, le formulaire peut être transmis aux destinataires l’un après l’autre ou envoyé à tous les destinataires simultanément, selon la configuration de l’étape de processus. [!DNL Adobe Sign] les Forms adaptatives activées pour sont envoyées au serveur Experience Manager Forms uniquement une fois que tous les destinataires ont terminé le processus de signature.

Par défaut, le service Planificateur de [!DNL Adobe Sign] vérifie la réponse des destinataires (sondages) toutes les 24 heures. [Vous pouvez modifier l’intervalle par défaut pour votre environnement](adobe-sign-integration-adaptive-forms.md#for-aem-workflows-only-configure-dnl-adobe-acrobat-sign-scheduler-to-sync-the-signing-status-configure-adobe-sign-scheduler-to-sync-the-signing-status).

L’étape Signer le document possède les propriétés suivantes :

* **[!UICONTROL Nom du contrat :]** indiquez le titre du contrat. Le nom du contrat devient une partie de l’objet et du corps du courrier électronique envoyé aux signataires. Vous pouvez soit stocker le nom dans une variable de type de données Chaîne, soit sélectionner **[!UICONTROL Littéral]** pour l’ajouter manuellement.

* **[!UICONTROL Paramètres régionaux]** :  spécifiez la langue pour les options d’e-mail et de vérification. Vous pouvez stocker les paramètres régionaux dans une variable de type de données Chaîne ou sélectionner **[!UICONTROL Littéral]** pour choisir les paramètres régionaux dans la liste des options disponibles. Vous devez définir le code des paramètres régionaux lors du stockage de la valeur de la langue dans une variable. Par exemple, spécifiez **[!UICONTROL en_US]** pour l’anglais et **[!UICONTROL fr_FR]** pour le français.

* **[!UICONTROL Configuration cloud Adobe Sign]** : sélectionnez une configuration cloud [!DNL Adobe Sign]. Si vous n’avez pas configuré [!DNL Adobe Sign] pour [!DNL AEM Forms], voir [Intégration d’Adobe Sign à [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).

* **[!UICONTROL Sélectionner le document à signer en utilisant]** : vous pouvez choisir un document à partir d’un emplacement relatif à la payload, utiliser la payload comme document, spécifier un chemin d’accès absolu au document ou récupérer le document stocké dans une variable de type de données Document.
* **[!UICONTROL Jours avant l’échéance :]** un document est marqué comme dû (délai expiré) lorsqu’il n’y a plus aucune activité sur la tâche pour le nombre de jours spécifié dans le champ **[!UICONTROL Jours avant l’échéance]**. Le nombre de jours est calculé à partir du jour de l’affectation de la documentation à un utilisateur pour signature.
* **[!UICONTROL Fréquence des messages de rappel]** : vous pouvez envoyer un message de rappel à intervalle quotidien ou hebdomadaire. La semaine est comptée à partir du jour de l’affectation de la documentation à un utilisateur pour signature.
* **[!UICONTROL Processus de signature :]** vous pouvez signer un document dans un ordre séquentiel ou parallèle. Dans un ordre séquentiel, un signataire à la fois reçoit le document pour signature. Une fois que le premier signataire a terminé la signature du document, le document est envoyé au second signataire, etc. Dans l’ordre parallèle, plusieurs signataires signent un document en même temps.
* **[!UICONTROL URL de redirection :]** spécifiez une URL de redirection. Une fois le document signé, vous pouvez rediriger la personne désignée vers une URL. En règle générale, cette URL contient un message de remerciement ou d’autres instructions.
* **[!UICONTROL Phase de processus :]** un processus peut avoir plusieurs étapes. Ces phases sont affichées dans la boîte de réception AEM. Vous pouvez définir ces phases dans les propriétés du modèle (**[!UICONTROL Sidekick]** > **[!UICONTROL Page]** > **[!UICONTROL Propriétés de la page]** > **[!UICONTROL Phases]**).
* **[!UICONTROL Sélectionner les destinataires]** : indiquez la méthode utilisée pour sélectionner des destinataires pour le document. Vous pouvez affecter de manière dynamique le workflow à un utilisateur ou utilisatrice ou à un groupe ou ajouter manuellement les informations d’un ou une destinataire. Lorsque vous sélectionnez Manuellement dans la liste déroulante, vous ajoutez les détails du destinataire tels que l’e-mail, le rôle et la méthode d’authentification.

  >[!NOTE]
  >
  >* Dans la section Rôle, vous pouvez indiquer le rôle du destinataire : signataire, approbateur, accepteur, destinataire certifié, utilisateur de formulaire et délégué.
  >* Si vous sélectionnez Délégué dans l&#39;option Rôle , le Délégué peut affecter la tâche de signature à un autre destinataire.
  >* Si vous avez configuré une méthode d’authentification pour [!DNL Adobe Sign], en fonction de votre configuration, vous pouvez sélectionner une méthode d’authentification telle que l’authentification par téléphone, l’authentification basée sur les identités sociales ou gouvernementales et l’authentification basée sur les connaissances.

* **[!UICONTROL Script ou service pour sélectionner les destinataires]** : cette option est disponible uniquement si vous sélectionnez l’option De manière dynamique dans le champ Sélectionner les destinataires . Vous pouvez spécifier un script ECMAScript ou un service pour sélectionner des signataires et des options de vérification pour un document.
* **[!UICONTROL Détails du destinataire]** : cette option est disponible uniquement si l’option Manuellement est sélectionnée dans le champ Sélectionner les destinataires. Spécifiez une adresse e-mail et choisissez un mécanisme de vérification facultatif. Avant de sélectionner une méthode de vérification en 2 étapes, assurez-vous que l’option de vérification correspondante est activée pour le compte [!DNL Adobe Sign] configuré. Vous pouvez utiliser une variable de type Chaîne pour définir des valeurs pour les champs Courriel, Code de pays et Numéro de téléphone. Les champs Code pays et Numéro de téléphone s’affichent uniquement si vous sélectionnez Vérification téléphonique dans la liste déroulante de vérification en 2 étapes.
* **[!UICONTROL Document signé]** : vous pouvez enregistrer le statut du document signé dans la variable. Pour ajouter une piste d’audit de signature électronique à votre document signé, afin d’en améliorer la sécurité et la légalité, vous pouvez inclure un rapport d’audit. Vous pouvez enregistrer le document signé à l’aide de la variable ou du dossier Payload.

  >[!NOTE]
  >
  > Le rapport d’audit est ajouté à la dernière page du document signé.

<!--
## Document Services steps {#document-services-steps}

AEM Document services are a set of services for creating, assembling, and securing PDF Documents. [!DNL AEM Forms] provides a separate AEM Workflow step for each document service.

Similar to other [!DNL AEM Forms] workflow steps, such as Assign Task, Send Email, and Sign Document, you can use variables in all AEM Document services steps. For more information on creating and managing variables, see [Variables in AEM workflows](variable-in-aem-workflows.md).
 
### Apply Document Time Stamp step {#apply-document-time-stamp-step}

Add time stamp to a document. You provide document details such as input document path, input document name, location to store exported data. You may choose to overwrite existing payload file, choose a different file name to store data in a different file under payload folder, provide an absolute path to the data, or store data in a variable of Document data type.

### Convert to image step {#convert-to-image-step}

Converts a PDF document to list of images. Supported image formats are JPEG, JPEG2000, PNG, and TIFF. The following information applies to conversions to TIFF images:

* A multi-page TIFF file is generated.
* Some annotations are not included in TIFF images. Annotations that require Acrobat to generate their appearance are not included.

### Convert to PDF/A step {#convert-to-pdf-a-step}

Converts a PDF document to PDF/A format using the options provided. The PDF/A version of Portable Document Format (PDF) is specialized for archiving and long-term preservation of documents.

### Convert to PS step {#convert-to-ps-step}

Convert PDF documents to PostScript. When converting to PostScript, you can use the conversion operation to specify the source document and whether to convert to PostScript level 2 or 3. The PDF document you convert to a PostScript file must be non-interactive.

### Create PDF from specified type step {#create-pdf-from-specified-type-step}

Generate a PDF document from an input file. The input document can be relative to the payload, have an absolute path, can be payload itself, or stored in a variable of Document data type.

### Create PDF from URL/HTML/ZIP step {#create-pdf-from-url-html-zip-step}

Generates a PDF document from supplied URL, HTML, and ZIP file.

### Export Data step {#export-data-step}

Exports data from a PDF forms or XDP file. It requires you to enter the file path of Input Document and the Export Data Format. The options for Export Data Format are Auto, XDP and XmlData.

### Export PDF to specified type step {#export-pdf-to-specified-type-step}

Converts a PDF document to a selected format.

### Generate Non-Interactive PDF step {#generatenoninteractive}

Generate a Non-Interactive PDF. It provides various customization options.

>[!NOTE]
>
>You can use variables to specify the template file for input documents. Store the path of the template file in a variable of String data type.

### Import Data step {#import-data-step}

Merges form data into a PDF form. You can import form data into a PDF form.

### Invoke DDX step {#invokeddx}

Executes the DDX file on the specified map of input documents and returns the manipulated PDF documents.

>[!NOTE]
>
>You can use variables to specify the DDX file for input documents. Store the DDX file in a variable of Document or XML data type.

### Optimize PDF step {#optimize-pdf-step}

Optimizes PDF files by reducing their size. The result of this conversion is PDF files that may be smaller than their original versions. This operation also converts PDF documents to the PDF version specified in the optimization parameters.

Optimization settings specify how files are optimized. Here are example settings:

* Target PDF version
* Discarding objects such as JavaScript actions and embedded page thumbnails
* Discarding user data such as comments and file attachments
* Discarding invalid or unused settings
* Compressing uncompressed data or using more efficient compression algorithms
* Removing embedded fonts
* Setting transparency values

### Render PDF Form step {#renderpdf}

Renders a form created in Form Designer (XDP) to a PDF form.

>[!NOTE]
>
>You can use variables to specify the template file for input documents. Store the path of the template file in a variable of String data type.

### Secure Document step {#secure-document-step}

Encrypt, Sign, and certify a document. [!DNL AEM Forms] supports both password based and certificate base encryption. You can also choose between various algorithms for signing documents. For example, SHA-256 and SH-512. You can also use the workflow step to reader extend PDF documents. The workflow step provides option to enable barcode decoding, digital signatures, import and export of PDF data, and other options.

### Send to Printer step {#send-to-printer-step}

Send a document directly to a printer. It supports the following printing access mechanisms:

* **[!UICONTROL Direct accessible printer]**: A printer that is installed on the same computer is called a direct accessible printer, and the computer is named printer host. This type of printer can be a local printer that is connected to the computer directly.
* **[!UICONTROL Indirect accessible printer]**: The printer that is installed on a print server is accessed from other computers. Technologies such as the common UNIX&reg; printing system (CUPS) and the Line Printer Daemon (LPD) protocol are available to connect to a network printer. To access an indirect accessible printer, specify the print server's IP or host name. Using this mechanism, you can send a document to an LPD URI when the network has an LPD running. The mechanism lets you route the document to any printer that is connected to the network that has an LPD running.
    -->

## Générer l’étape de sortie imprimée {#generatePrintedOutput}

L’opération génère une sortie PCL, PostScript, ZPL, IPL, TPCL ou DPL à l’aide d’une conception de formulaire et d’un fichier de données. Le fichier de données est fusionné avec la conception de formulaire et mis en forme pour l’impression. La sortie générée par cette étape peut être envoyée directement à une imprimante ou enregistrée en tant que fichier. Il est recommandé d’utiliser cette opération lorsque vous souhaitez utiliser des conceptions de formulaire ou des données à partir d’une application. Si vos conceptions de formulaire se trouvent sur le réseau, un système de fichiers local ou un emplacement HTTP, utilisez l’opération generatePrintedOutput.

Par exemple, votre application requiert la fusion d’une conception de formulaire avec un fichier de données. Les données contiennent des centaines d’enregistrements. En outre, la sortie doit être envoyée à une imprimante prenant en charge ZPL. La conception de formulaire et vos données d’entrée se trouvent dans une application. Utilisez l’opération generatePrintedOutput pour fusionner chaque enregistrement avec une conception de formulaire et envoyer la sortie à une imprimante prenant en charge ZPL.

L’opération Générer une sortie imprimée présente les propriétés suivantes :

**[!UICONTROL Propriétés d’entrée]**

* **[!UICONTROL Sélectionner le fichier de modèle à l’aide de]**: spécifiez le chemin d’accès au fichier de modèle. Vous pouvez sélectionner le fichier de modèle à l’aide du chemin d’accès relatif à la payload, enregistré à un chemin d’accès absolu ou à l’aide d’une variable de type de données Document. Par exemple : [Payload_Directory]/Workflow/data.xml. Si le chemin d’accès n’existe pas dans le référentiel crx, un administrateur peut le créer avant de l’utiliser. De plus, vous pouvez également accepter la payload comme fichier de données d’entrée.

* **[!UICONTROL Sélectionner le document de données à l’aide de]** : spécifiez le chemin d’accès d’un fichier de données d’entrée. Vous pouvez sélectionner le fichier de données d’entrée à l’aide du chemin d’accès relatif à la payload, enregistré à un chemin absolu ou à l’aide d’une variable de type de données Document. Par exemple : [Payload_Directory]/Workflow/data.xml. Si le chemin d’accès n’existe pas dans le référentiel crx, un administrateur peut le créer avant de l’utiliser.

* **[!UICONTROL Printer Format]** : une valeur Print Format qui spécifie la langue de description de page à utiliser lorsqu’un fichier XDC n’est pas fourni, afin de générer le flux de sortie. Si vous fournissez une valeur littérale, sélectionnez l’une de ces valeurs :

   * **[!UICONTROL PCL couleur]** : utilisez cette option pour spécifier un fichier XDC personnalisé pour PCL.
   * **[!UICONTROL PostScript générique]** : utilisez cette option pour spécifier un fichier XDC générique pour PostScript.
   * **[!UICONTROL ZPL 300 DPI]** : utilisez ZPL 300 DPI. Le fichier zpl300.xdc est utilisé.
   * **[!UICONTROL ZPL 600 DPI]** : utilisez ZPL 600 DPI. Le fichier zpl600.xdc est utilisé.
   * **[!UICONTROL IPL 300 DPI]** : utilisez IPL 300 DPI. Le fichier ipl300.xdc est utilisé.
   * **[!UICONTROL IPL 400 DPI]** : utilisez IPL 400 DPI. Le fichier ipl400.xdc est utilisé.
   * **[!UICONTROL TPCL 600 DPI]** : utilisez TPCL 600 DPI. Le fichier tpcl600.xdc est utilisé.
   * **[!UICONTROL PostScript brut]** : utilisez cette option pour spécifier un fichier XDC texte brut pour PostScript.
   * **[!UICONTROL DPL300DPI]** : utilisez DPL 300 DPI. Le fichier dpl300.xdc est utilisé.
   * **[!UICONTROL DPL400DPI]** : utilisez DPL 400 DPI. Le fichier dpl400.xdc est utilisé.
   * **[!UICONTROL DPL600DPI]** : utilisez DPL 600 DPI. Le fichier dpl600.xdc est utilisé.
   * **[!UICONTROL HP_PCL_5e]** : utilisez cette option pour prendre en charge plusieurs appareils Canon.


**[!UICONTROL Propriétés de sortie]**

* **[!UICONTROL Enregistrer le document de sortie à l’aide de]** : indiquez l’emplacement d’enregistrement du fichier de sortie. Vous pouvez enregistrer le fichier de sortie à un emplacement relatif à la payload, dans une variable ou spécifier un emplacement absolu pour enregistrer le fichier de sortie. Si le chemin d’accès n’existe pas dans le référentiel crx, un administrateur peut le créer avant de l’utiliser.

**[!UICONTROL Propriétés avancées]**

* **[!UICONTROL Sélectionner l’emplacement racine du contenu à l’aide de]** : la racine du contenu est une valeur de chaîne qui spécifie l’URI, la référence absolue ou l’emplacement dans le référentiel pour récupérer les ressources relatives utilisées par la conception de formulaire. Par exemple, si la conception de formulaire fait référence à une image, comme `../myImage.gif`, `myImage.gif` doit être dans le référentiel `repository://`. La valeur par défaut est `repository://`, qui pointe vers le niveau racine du référentiel.

  Lorsque vous sélectionnez une ressource dans votre application, le chemin d’URI racine du contenu doit avoir la structure appropriée. Par exemple, si un formulaire est sélectionné à partir d’une application nommée SampleApp et placé dans `SampleApp/1.0/forms/Test.xdp`, l’URI de la racine du contenu doit être spécifié comme `repository://administrator@password/Applications/SampleApp/1.0/forms/` ou `repository:/Applications/SampleApp/1.0/forms/` (lorsque l’autorité est nulle). Lorsque l’URI de la racine de contenu est spécifié de cette manière, les chemins d’accès de toutes les ressources référencées dans le formulaire sont résolus par rapport à cet URI.

* **[!UICONTROL Sélectionner un fichier XCI à l’aide de]** : les fichiers XCI sont utilisés pour décrire les polices et les autres propriétés utilisées pour les éléments de conception de formulaire. Vous pouvez conserver un fichier XCI relatif à la payload, à un chemin d’accès absolu ou à l’aide d’une variable de type de données Document.

* **[!UICONTROL Paramètres régionaux]** : définit la langue utilisée pour générer le document PDF. Si vous fournissez une valeur littérale, sélectionnez une langue dans la liste ou l’une de ces valeurs :
   * **[!UICONTROL Utiliser le serveur par défaut]** :
(par défaut) utilisez les paramètres régionaux qui sont configurés sur le serveur [!DNL AEM Forms]. Le paramètre Paramètre régional est configuré à l’aide de la console d’administration. (Voir l’[aide de Designer](https://helpx.adobe.com/content/dam/help/fr/experience-manager/6-5/forms/pdf/using-designer.pdf).)

   * **[!UICONTROL Pour utiliser une valeur personnalisée]** : 
saisissez le code des paramètres régionaux dans la zone littérale ou sélectionnez une variable de chaîne contenant le code des paramètres régionaux. Pour obtenir une liste complète des codes des paramètres régionaux pris en charge, voir https://docs.oracle.com/javase/1.5.0/docs/guide/intl/locale.doc.html.

* **[!UICONTROL Copies]** : une valeur entière qui spécifie le nombre de copies à générer pour la sortie. La valeur par défaut est 1.

* **[!UICONTROL Duplex Printing]** : une valeur Pagination qui spécifie l’utilisation de l’impression recto verso ou recto. Les imprimantes prenant en charge PostScript et PCL utilisent cette valeur. Si vous fournissez une valeur littérale, sélectionnez l’une de ces valeurs :
   * **[!UICONTROL Duplex Long Edge]** : utiliser l’impression recto verso et imprimer à l’aide de la pagination sur le bord long.
   * **[!UICONTROL Duplex Short Edge]** : utiliser l’impression recto verso et imprimer à l’aide de la pagination sur le bord court.
   * **[!UICONTROL Simplex]** : utiliser l’impression recto.

## Étapes permettant de générer une sortie PDF non interactive   {#generatePDFdocuments}

1. Faites glisser le workflow Générer une sortie de PDF non interactif dans l’onglet Forms Workflow du sidekick.
1. Double-cliquez sur l’étape de workflow ajoutée pour modifier le composant.
1. Dans la boîte de dialogue Modifier le composant, configurez les documents d’entrée, les documents de sortie et d’autres paramètres, puis cliquez sur **[!UICONTROL OK]**.

### Documents d’entrée {#input-documents-3}

* **Fichier modèle** : spécifie l’emplacement du modèle XDP. Ce champ est obligatoire.

* **Document de données** : indique l’emplacement du fichier XML de données à fusionner avec le modèle.

### Document de sortie {#output-document}

**Document de sortie** : spécifie le nom du formulaire PDF généré.

### Paramètres supplémentaires {#additional-parameters-1}

* **Racine du contenu** : spécifie le chemin d’accès au dossier dans le référentiel où sont stockés les fragments ou les images utilisés dans le modèle XDP d’entrée.
* **Paramètres régionaux** : spécifie le paramètre régional par défaut du formulaire PDF généré.
* **Version Acrobat** : spécifie la version Acrobat ciblée pour le formulaire PDF généré.
* **PDF linéarisé** : indique si le PDF généré doit être optimisé pour l’affichage Web.
* **PDF balisé** : spécifie si le PDF généré doit être accessible.
* **Document XCI** : spécifie le chemin d’accès au fichier XCI.

## Voir également {#see-also}

* [Variables dans les workflows AEM basés sur l’utilisation de Forms](/help/forms/variable-in-aem-workflows.md)
* [Configuration du paramètre d’absence du bureau](/help/forms/configure-out-of-office-settings.md)

<!--

>[!MORELIKETHIS]
>
>* [Forms-centric workflow on OSGi](/help/forms/aem-forms-workflow.md)
>* [Use AEM translation workflow to localize Adaptive Forms and Document of Record](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms.md)

-->