---
title: Guide pratique pour appliquer des actions de gouvernance visant à contrôler les applications connectées | Microsoft Docs
description: Cette rubrique répertorie et décrit toutes les actions de gouvernance qui peuvent être effectuées dans Cloud App Security et les messages de journal qui les suivent.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/7/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3536c0a5-fa56-4931-9534-cc7cc4b4dfb0
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 8339081e7600faf417a35ff4a4318b60d84eece1
ms.sourcegitcommit: a074880eed43cf6e5ae95807640e99655b24d9be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="governing-connected-apps"></a>Gouvernance des applications connectées
La gouvernance vous permet de contrôler en temps réel les actions des utilisateurs dans les applications. Pour les applications connectées, vous pouvez appliquer des actions de gouvernance aux fichiers ou aux activités.
Les actions de gouvernance sont des actions intégrées que vous pouvez exécuter sur des fichiers ou des activités directement à partir de Cloud App Security pour contrôler en temps réel les actions de vos utilisateurs dans les applications connectées. 

> [!NOTE]
> Lorsque Cloud App Security tente d’exécuter une action de gouvernance sur un fichier, mais échoue parce que le fichier est verrouillé, il retente automatiquement l’action de gouvernance. 


### <a name="file-governance-actions"></a>Actions de gouvernance sur des fichiers  

Vous pouvez effectuer les actions de gouvernance suivantes sur un fichier ou un utilisateur spécifique, ou à partir d’une stratégie donnée.
  
-   Notifications  
  
    -   Alertes : Les alertes peuvent se déclencher dans le système et se propager par e-mail et SMS, selon leur niveau de gravité.  
  
    -   Notification par e-mail à l’utilisateur : Les e-mails sont personnalisables et envoyés à tous les propriétaires de fichiers en situation de violation.  
  
    -   Mettre en copie le responsable : Selon l’intégration de l’annuaire des utilisateurs, des notifications par e-mail peuvent également être envoyées au responsable de la personne qui viole une stratégie. (Salesforce uniquement)
  
-   Notifier des utilisateurs spécifiques : Liste spécifique d’adresses e-mail qui reçoivent ces notifications.  
  
-   Notifier le dernier éditeur du fichier : Envoyez des notifications à la dernière personne qui a modifié le fichier.  
  
-   Actions de gouvernance dans les applications  
  
     Des actions précises peuvent être appliquées par application. Ces actions spécifiques varient selon la terminologie de l’application.  
  
    -   Partage de modifications  
  
        -   Supprimer le partage public : Autoriser l’accès uniquement à des collaborateurs désignés, par exemple : Supprimer l’accès public pour G Suite et Supprimer le lien partagé direct pour Box.  
  
        -   Supprimer les utilisateurs externes : Autorisez l’accès uniquement aux utilisateurs de l’entreprise.  
  
        -   Rendre privé : Seul le propriétaire peut accéder au fichier, tous les partages sont supprimés.  
  
        -   Supprimer un collaborateur : Supprimez un collaborateur spécifique du fichier.  

        - Réduire l’accès public : définissez les fichiers publiquement disponibles comme étant accessibles uniquement avec un lien partagé.
  
    -   Quarantaine  
  
        -   Mettre en quarantaine utilisateur : Autorisez le libre-service en déplaçant le fichier vers un dossier de quarantaine contrôlé par l’utilisateur  
  
        -   Mettre en quarantaine administrateur : Le fichier est placé en quarantaine sur le lecteur de l’administrateur, ce dernier devant l’approuver.  
  
-   Hériter des autorisations du parent : cette action de gouvernance vous permet de supprimer un ensemble d’autorisations spécifiques pour un fichier ou un dossier dans Office 365, et de les rétablir ensuite aux autorisations définies pour le dossier parent.
-   Mettre à la corbeille : Déplacez le fichier vers le dossier Corbeille.
  
![policy_create alerts](./media/policy_create-alerts.png "policy_create alerts")  
  
 
### <a name="activity-governance-actions"></a>Actions de gouvernance des activités  

- Notifications  
  
    -   Alertes : Les alertes peuvent se déclencher dans le système et se propager par e-mail et SMS, selon leur niveau de gravité.  
  
    -   Notification par e-mail à l’utilisateur : Les e-mails sont personnalisables et envoyés à tous les propriétaires de fichiers en situation de violation.  
  
    -   Mettre en copie le responsable : Selon l’intégration de l’annuaire des utilisateurs, des notifications par e-mail peuvent également être envoyées au responsable de la personne qui viole une stratégie. (Salesforce uniquement)
  
    -   Notifier d’autres utilisateurs : Liste spécifique d’adresses e-mail qui reçoivent ces notifications.  
  
- Actions de gouvernance dans les applications  
  
    -   Des actions précises peuvent être appliquées par application. Ces actions spécifiques varient selon la terminologie de l’application.  
  
    -   Suspendre l’utilisateur : Excluez temporairement l’utilisateur de l’application. 
    > [!NOTE] 
    > Si votre Azure Active Directory est défini pour se synchroniser automatiquement avec les utilisateurs de votre environnement local Active Directory, les paramètres de l’environnement local remplacent les paramètres Azure AD et cette action de gouvernance est rétablie. 
  
    -   Demander à l’utilisateur de se reconnecter : déconnectez l’utilisateur et demandez-lui de se reconnecter.  
  
     ![Actions de gouvernance des stratégies d’activité Cloud App Security](./media/activity-policy-ref6.png "stratégie d’activité ref6")  
  

### <a name="governance-conflicts"></a>Conflits de gouvernance

Si vous créez plusieurs stratégies, il peut arriver que les actions de gouvernance se chevauchent. Dans ce cas, Cloud App Security traite les actions de gouvernance comme suit :

#### <a name="conflicts-between-policies"></a>Conflits de stratégies

- Si deux stratégies contiennent des actions qui sont contenues dans l’une et l’autre (par exemple, l’action **Supprimer des partages externes** est incluse dans **Rendre privé**), Cloud App Security résout le conflit et l’action la plus forte est appliquée.
- Si les actions sont complètement indépendantes (par exemple, **Notifier le propriétaire** et **Rendre privé**), les deux actions ont lieu.
- Si les actions sont en conflit, (par exemple **Change owner to user A** [Remplacer le propriétaire par l’utilisateur A] et **Change owner to user B** [Remplacer le propriétaire par l’utilisateur B]), différents résultats peuvent provenir de chaque correspondance. Il est important de modifier vos stratégies pour éviter les conflits, car elles peuvent entraîner des modifications indésirables dans le lecteur qui seront difficiles à détecter.

#### <a name="conflicts-in-user-sync"></a>Conflits de synchronisation d’utilisateur

- Si votre Azure Active Directory est défini pour se synchroniser automatiquement avec les utilisateurs de votre environnement local Active Directory, les paramètres de l’environnement local remplacent les paramètres Azure AD et cette action de gouvernance est rétablie. 

### <a name="governance-log"></a>Journal de gouvernance
Le journal de gouvernance fournit un enregistrement de l’état de chaque tâche que Cloud App Security doit exécuter, dont les tâches manuelles et automatiques. Ces tâches comprennent les tâches que vous définissez dans les stratégies, les actions de gouvernance que vous définissez sur des fichiers et des utilisateurs ainsi que toute autre action que Cloud App Security doit effectuer. Le journal de gouvernance fournit également des informations sur la réussite ou l’échec de ces actions. Vous pouvez choisir de retenter ou de rétablir certaines des actions de gouvernance à partir du journal de gouvernance. 

Le portail Cloud App Security vous permet d’effectuer la liste complète d’actions suivantes. Ces dernières sont activées dans divers emplacements de la console décrits dans la colonne **Emplacement**. Chaque action de gouvernance effectuée est répertoriée dans le journal de gouvernance.
Pour plus d’informations sur la façon dont les actions de gouvernance sont traitées en cas de conflits de stratégies, consultez [Conflits de stratégies](control-cloud-apps-with-policies.md).

**Emplacement**|**Type d’objet cible**|**Action de gouvernance**|**Description**|**Connecteurs associés** 
---------|---------|---------|---------|---------
|Comptes|File|Supprimer les collaborations de l’utilisateur|Supprime toutes les collaborations d’un utilisateur spécifique pour tous les fichiers - utile lorsque des personnes quittent l’entreprise.|Box, G Suite|
|Comptes|Compte|Réhabiliter l’utilisateur|Réhabilite l’utilisateur|G Suite, Box, Office, Salesforce|
|Comptes|Compte|Paramètres de compte|Vous permet d’accéder à la page de paramètres de compte dans une application donnée (par exemple, dans Salesforce).|Toutes les applications. Les paramètres de One Drive et SharePoint sont configurés dans Office.|
|Comptes |File|Transférer la possession de tous les fichiers|Dans un compte, vous transférez les fichiers d’un utilisateur vers un nouveau propriétaire que vous sélectionnez. L’ancien propriétaire devient un éditeur et ne peut plus changer les paramètres de partage. Le nouveau propriétaire reçoit une notification du transfert de possession par e-mail.|G Suite|
|Comptes, Stratégie d’activité|Compte|Suspendre l’utilisateur|Définit que l’utilisateur n’a aucun accès ni aucune possibilité de se connecter. S’il est connecté lorsque vous activez cette option, il est immédiatement verrouillé.|G Suite, Box, Office, Salesforce|
|Stratégie d’activité, Comptes|Compte|Demander à l’utilisateur de se reconnecter|Révoque tous les jetons d’actualisation et les cookies de session émis aux applications par l’utilisateur. Cela empêche l’accès aux données de l’organisation et force l’utilisateur à se connecter à toutes les applications.|G Suite|
|Stratégie d’activité, Comptes|Compte|Révoquer les privilèges administratifs|Révoque les privilèges administratifs pour un compte administrateur. Par exemple, avec la définition d’une stratégie de l’activité qui révoque les privilèges administratifs après 10 échecs de tentative de connexion.|G Suite|
|Tableau de bord de l’application > Autorisations d’applications|Autorisations|Un-ban app (Annuler l’exclusion de l’application)|Dans Google et Salesforce : suppriment l’exclusion de l’application et permettent aux utilisateurs d’accorder des autorisations à l’application tierce avec Google et Salesforce. Dans Office 365 : restaure les autorisations d’accès de l’application tierce à Office.|G Suite, Salesforce, Office|
|Tableau de bord de l’application > Autorisations d’applications|Autorisations|Désactiver les autorisations d’application|Révoquent les autorisations d’accès d’une application tierce à Google, Salesforce ou Office. Il s’agit d’une action unique qui se produit sur toutes les autorisations existantes, mais qui n’empêche pas les connexions ultérieures. |G Suite, Salesforce, Office|
|Tableau de bord de l’application > Autorisations d’applications|Autorisations|Activer les autorisations d’application|Accorde les autorisations d’accès d’une application tierce à Google, Salesforce ou Office. Il s’agit d’une action unique qui se produit sur toutes les autorisations existantes, mais qui n’empêche pas les connexions ultérieures. |G Suite, Salesforce, Office|
|Tableau de bord de l’application > Autorisations d’applications|Autorisations|Exclure l’application|Dans Google et Salesforce : révoquent les autorisations d’accès d’une application tierce à Google ou Salesforce et lui interdisent de recevoir des autorisations dans le futur. Dans Office 365 : n’autorise pas les applications tierces à accéder à Office, mais ne les révoque pas.|G Suite, Salesforce, Office|Stratégie de fichier|File|Restreindre aux collaborateurs uniquement|Seuls les collaborateurs répertoriés peuvent accéder au fichier.|Box|
|Tableau de bord de l’application > Autorisations d’applications|Autorisations|Révoquer l’application|Révoque les autorisations d’accès d’une application tierce à Google, Salesforce ou Office. Il s’agit d’une action unique qui se produit sur toutes les autorisations existantes, mais qui n’empêche pas les connexions ultérieures.|G Suite, Salesforce|
|Tableau de bord de l’application > Autorisations d’applications|Compte|Révoquer l’utilisateur de cette application|Vous pouvez révoquer des utilisateurs spécifiques en cliquant sur le nombre sous Utilisateurs. L’écran affiche les différents utilisateurs et vous avez pouvez utiliser la croix (X) pour supprimer les autorisations pour tout utilisateur.|G Suite, Salesforce|
|Découverte > Applications découvertes/Adresses IP/Utilisateurs|Cloud Discovery|Exporter les données de découverte|Crée un fichier CSV à partir de données de découverte.|Découverte|
|Stratégie de fichier|File|Mettre à la corbeille|Met un fichier dans la corbeille de l’utilisateur.|One Drive, SharePoint|
|Stratégie de fichier|File|Notifier le dernier éditeur du fichier|Envoie un e-mail pour notifier la dernière personne qui a modifié le fichier qu’il viole une stratégie.|G Suite, Box|
|Stratégie de fichier|File|Notifier le propriétaire du fichier|Envoie un e-mail au propriétaire quand un fichier ne respecte pas une stratégie. Dans Dropbox, si aucun propriétaire n’est associé à un fichier, la notification est envoyée à l’utilisateur spécifique que vous définissez.|Toutes les applications|
|Stratégie de fichier, Stratégie d’activité|Fichier, Activité|Mettre en copie le responsable du propriétaire/de l’utilisateur|Lorsque le propriétaire du fichier reçoit une notification par e-mail spécifiant que son fichier viole une stratégie, le responsable du propriétaire du fichier/l’utilisateur peut éventuellement être notifié.|Salesforce|
|Stratégie de fichier, Stratégie d’activité|Fichier, Activité|Notifier des utilisateurs spécifiques|Envoie un e-mail pour notifier des utilisateurs spécifiques qu’un fichier viole une stratégie.|Toutes les applications|
|Stratégie de fichier et Stratégie d’activité|Fichier, Activité|Notifier l’utilisateur|Envoie un e-mail aux utilisateurs pour les informer qu’une de leurs actions ou qu’un fichier qu’ils possèdent viole une stratégie. Vous pouvez ajouter une notification personnalisée lui indiquant la violation.|Tous|
|Stratégie de fichiers et fichiers|File|Supprimer la capacité des éditeurs à partager|Dans Google Drive, les autorisations de l’éditeur par défaut d’un fichier permettent également le partage. Cette action de gouvernance restreint cette option et restreint le partage de fichiers au propriétaire.|G Suite|
|Stratégie de fichiers et fichiers|File|[Mettre en quarantaine administrateur](use-case-admin-quarantine.md)|Supprime toutes les autorisations du fichier et déplace le fichier vers un dossier de quarantaine dans un emplacement réservé à l’administrateur. De cette manière, l’administrateur peut examiner le fichier et le supprimer.|Office 365 SharePoint, OneDrive Entreprise, Box|
|Stratégie de fichiers et fichiers|File|Appliquer l’étiquette de classification|Applique automatiquement une étiquette de classification Azure Information Protection à des fichiers, en fonction des conditions définies dans la stratégie.|Box, One Drive, SharePoint|
|Stratégie de fichiers et fichiers|File|Supprimer l’étiquette de classement|Supprime automatiquement une étiquette de classification Azure Information Protection pour des fichiers, en fonction des conditions définies dans la stratégie.|Box, One Drive, SharePoint|
|Stratégie de fichier, Stratégie d’activité, Alertes|Application|Demander aux utilisateurs de se reconnecter|Vous pouvez demander aux utilisateurs de se reconnecter à toutes les applications Office 365 et Azure AD pour corriger de manière rapide et efficace les alertes d’activité suspecte de l’utilisateur et les comptes corrompus. La nouvelle gouvernance se trouve dans les paramètres de stratégie et les pages d’alerte, à côté de l’option Interrompre la synchronisation de l’utilisateur.|Office 365, Azure AD|
|Fichiers|File|Restaurer des fichiers mis en quarantaine utilisateur|Restaure un utilisateur mis en quarantaine.|Box|
|Fichiers|File|M’auto-attribuer des permissions de lecture|Vous accorde des permissions de lecture pour le fichier afin de vous permettre d’y accéder et de déterminer s’il y a eu violation ou non.|G Suite|
|Fichiers|File|Autoriser les éditeurs à partager|Dans Google Drive, les autorisations de l’éditeur par défaut d’un fichier permettent également le partage. Cette action de gouvernance est l’opposé de Supprimer la capacité des éditeurs à partager et permet à l’éditeur de partager le fichier.|G Suite|
|Fichiers|File|Protéger|Protégez un fichier avec Azure Information Protection en appliquant un modèle d’organisation.|Office 365 (SharePoint et OneDrive)|
|Fichiers|File|Révoquer les permissions de lecture pour moi-même|Révoque les permissions de lecture pour le fichier pour vous-même. Cette option est utile lorsque vous vous êtes attribué des permissions pour examiner si un fichier comprend une violation ou non.|G Suite|
|Fichiers, Stratégie de fichier|File|Transférer la possession de fichier|Modifie le propriétaire (vous choisissez un propriétaire spécifique dans la stratégie).|G Suite|
|Fichiers, Stratégie de fichier|File|Réduire l’accès public|Ceci vous permet de définir les fichiers publiquement disponibles comme étant accessibles uniquement avec un lien partagé.|G Suite|
|Fichiers, Stratégie de fichier|File|Supprimer un collaborateur|Supprime un collaborateur donné d’un fichier.|G Suite, Box, One Drive, SharePoint|
|Fichiers, Stratégie de fichier|File|Rendre privé|Rendre le fichier privé (aucun collaborateur, aucun lien public, aucun partage).|G Suite, One Drive, SharePoint|
|Fichiers, Stratégie de fichier|File|Supprimer les utilisateurs externes|Supprime tous les collaborateurs externes - configurés comme internes dans les paramètres en dehors des domaines.|G Suite, Box |
|Fichiers, Stratégie de fichier|File|Attribuer une permission de lecture au domaine|Accorde une permission de lecture pour le fichier sur le domaine spécifié pour tout votre domaine ou un domaine spécifique. Cet accès peut être utile si vous souhaitez supprimer l’accès public après l’octroi d’un accès au domaine des personnes qui doivent y travailler.|G Suite|
|Fichiers, Stratégie de fichier|File|Mettre en quarantaine utilisateur|Supprime toutes les autorisations du fichier et déplace le fichier vers un dossier de quarantaine sur le lecteur racine de l’utilisateur. De cette manière, l’utilisateur peut examiner le fichier et le déplacer. S’il est déplacé manuellement, le partage de fichiers n’est pas restauré.|Box, One Drive, SharePoint|
|Fichiers, Stratégie de fichier|File|Supprimer l’accès public|Si vous êtes propriétaire d’un fichier et y autorisez un accès public, il devient accessible uniquement à toute autre personne disposant d’un droit d’accès au fichier (selon le type d’accès du fichier). |G Suite|
|Fichiers, Stratégie de fichier|File|Supprimer le lien partagé direct|Supprime un lien créé pour le fichier qui est public, mais partagé uniquement avec des personnes spécifiques.|Box|
|Paramètres> Paramètres de Cloud Discovery |Cloud Discovery|Recalculer les scores Cloud Discovery|Recalcule les scores dans le catalogue d’applications cloud après une modification d’une mesure de score.|Découverte|
|Paramètres> Paramètres de Cloud Discovery > Gérer les vues de données|Cloud Discovery|Créer une vue de données de filtre Cloud Discovery|Crée une nouvelle vue de données pour une vue plus détaillée des résultats de découverte. Par exemple, des plages d’adresses IP spécifiques.|Découverte|
|Paramètres> Paramètres de Cloud Discovery > Supprimer les données|Cloud Discovery|Supprimer les données Cloud Discovery|Supprime toutes les données collectées à partir de sources de découverte.|Découverte|
|Paramètres> Paramètres de Cloud Discovery > Charger les journaux manuellement/Charger les journaux automatiquement|Cloud Discovery|Analyser les données Cloud Discovery|Notification que toutes les données de journal ont été analysées.|Découverte|



## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  