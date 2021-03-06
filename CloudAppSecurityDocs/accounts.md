---
title: Visibilité sur les comptes d’application cloud | Microsoft Docs
description: Dans cette rubrique
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/2/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 7811f23b-6100-427f-93b1-44f5f81f6c76
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: eff1d2246dc220175504911d3cadb1b5591475c5
ms.sourcegitcommit: 9d2a34a2d4145b39d855dd6f596c0fc858b92f9b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37340139"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="accounts"></a>Comptes
Microsoft Cloud App Security vous donne une visibilité sur les comptes de vos applications connectées. Une fois connecté à une application à l’aide du connecteur d’applications, Cloud App Security lit les informations sur le compte qui sont associées aux applications connectées. La page Comptes vous permet d’examiner ces comptes, les autorisations, les groupes dont ils sont membres, leurs alias et les applications qu’ils utilisent. En outre, quand Cloud App Security détecte un nouveau compte qui n’a pas déjà été vu dans l’une des applications connectées (par exemple dans les activités ou le partage de fichiers), le compte est ajouté à la liste des comptes de cette application. Cela vous permet d’avoir une visibilité sur l’activité des utilisateurs externes interagissant avec vos applications cloud.

Les administrateurs peuvent rechercher les métadonnées ou l’activité d’un utilisateur spécifique. La page **Utilisateurs et comptes** vous fournit des détails complets sur l’entité qui sont extraits à partir d’applications cloud connectées. Elle fournit également l’historique d’activité de l’utilisateur et les alertes de sécurité liées à l’utilisateur.

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]


Vous pouvez filtrer la page **Comptes** pour vous permettre de trouver des comptes spécifiques et d’étudier plus en détail différents types de comptes ; par exemple, vous pouvez filtrer tous les comptes externes qui n’ont pas été consultés depuis l’année dernière. 

La page **Comptes** vous permet d’examiner facilement certains points dans vos comptes, notamment les suivants :  

-   Vérifiez si certains comptes ont été inactifs dans un service particulier pendant une longue période (peut-être devez-vous révoquer la licence de cet utilisateur pour ce service)  
-   Vous pouvez filtrer la liste des utilisateurs avec des autorisations d’administrateur  

-   Vous pouvez rechercher des utilisateurs qui ne font plus partie de votre organisation, mais peuvent toujours disposer de comptes actifs  

-   Vous pouvez engager des actions de gouvernance sur les comptes, comme la suspension d’une application, ou accéder à la page des paramètres de compte. Pour obtenir la liste complète des actions de gouvernance, consultez le [journal de gouvernance](governance-actions.md).
    
-   Vous pouvez voir les comptes qui sont inclus dans chaque groupe d’utilisateurs  

-   Vous pouvez voir les applications qui sont consultées par chaque compte et les applications qui sont supprimées pour des comptes spécifiques
    

![écran des comptes](./media/accounts-page.png)

## <a name="account-filters"></a>Filtres de comptes
Vous trouverez ci-dessous une liste des filtres de comptes qui peuvent être appliqués. La plupart des filtres prennent en charge plusieurs valeurs, ainsi que NOT, afin de vous fournir un outil puissant pour créer des stratégies.  
  
- **Nom du compte** : le nom du compte est l’alias principal de l’utilisateur, mais les autres identificateurs d’autres comptes Microsoft (Office 365 et Azure Active Directory) tels que des adresses proxy, des alias, des SID, sont pris en charge et consolidés sous l’alias principal.

- **Affiliation** : l’affiliation est **interne** ou **externe**. Pour définir les utilisateurs et les comptes qui sont internes, sous **Paramètres**, veillez à définir la **plage d’adresses IP** de votre organisation interne. Dans le cas où le compte dispose d’autorisations d’administrateur, l’icône dans la table Comptes s’affiche avec l’ajout de la cravate rouge ![icône d’administration des comptes](./media/accounts-admin-icon.png).

- **Application** : vous pouvez filtrer n’importe quelle application connectée à l’API utilisée par les comptes de votre organisation.

- **Domaine** : vous permet de filtrer des utilisateurs dans des domaines spécifiques.

- **Dernière consultation** : le filtre **Dernière consultation** vous permet de rechercher des comptes qui sont sans mouvement et dont les utilisateurs n’ont effectué aucune activité depuis un certain temps.

- **Organisation/Service** : vous permet de filtrer les membres de certains groupes d’organisation définis dans vos applications connectées.

- **Groupe d’utilisateurs** : vous permet de filtrer les membres des groupes d’utilisateurs dans Cloud App Security, à la fois les groupes d’utilisateurs intégrés et les groupes d’utilisateurs importés.


## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  