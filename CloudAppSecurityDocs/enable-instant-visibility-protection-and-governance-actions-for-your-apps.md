---
title: Connecter des applications pour obtenir une visibilité et un contrôle complets avec Cloud App Security | Microsoft Docs
description: Cette rubrique décrit le processus de connexion d’applications à des applications dans le cloud de votre organisation avec des connecteurs d’API.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/10/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3b15ba46-ac9c-4b4f-aefc-137edc903bc1
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e1b39d908f8094c54998c5f3382de3e43f03fd2e
ms.sourcegitcommit: 41fbc8e235befd240ad7a1eed52339cfafb5d906
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2018
ms.locfileid: "35251835"
---
*S’applique à : Microsoft Cloud App Security*


# <a name="connect-apps"></a>Connecter des applications 
Les connecteurs d’applications utilisent les API des fournisseurs d’applications pour que Microsoft Cloud App Security bénéficie d’une plus grande visibilité et d’un plus grand contrôle sur les applications auxquelles vous vous connectez.  

Microsoft Cloud App Security s’appuie sur les API données par le fournisseur de cloud, et chaque service a ses propres infrastructure et limitations d’API. Microsoft Cloud App Security utilise les services pour optimiser l’utilisation des API et pour garantir des performances optimales. Compte tenu des différentes limitations qu’imposent les services aux API (telles que les limites d’API et les fenêtres d’API de décalage temporel dynamique), les moteurs Cloud App Security tirent parti de la capacité autorisée. Certaines opérations, comme l’analyse de tous les fichiers dans le client, nécessitent une grande quantité d’API et sont donc réparties sur une longue période. Il est normal que certaines stratégies s’exécutent pendant plusieurs heures ou jours.  

## <a name="multi-instance-support"></a>Prise en charge de plusieurs instances

Cloud App Security prend en charge plusieurs instances de la même application connectée. Si vous utilisez plusieurs instances, par exemple, Salesforce (une pour le service commercial et une autre pour le département marketing), vous pourrez les connecter à la fois à Cloud App Security et les gérer à partir de la même console pour créer des stratégies granulaires et obtenir une investigation plus approfondie. Cette prise en charge s’applique uniquement aux applications connectées à des API, pas aux applications découvertes dans le cloud ni aux applications connectées à des proxys.

## <a name="how-it-works"></a>Fonctionnement  
Cloud App Security est déployé avec des privilèges d’administrateur système qui autorisent un accès complet à tous les objets de votre environnement.  

Le flux de connecteur d’applications est le suivant :
1. Cloud App Security analyse et enregistre les autorisations d’authentification.
2.  Cloud App Security demande la liste d’utilisateurs. La première fois que cette opération est effectuée, l’analyse peut prendre un certain temps. Une fois l’analyse des utilisateurs terminée, Cloud App Security passe aux activités et aux fichiers. Dès que l’analyse démarre, certaines activités sont disponibles dans Cloud App Security. 
4. Une fois la demande de liste d’utilisateurs effectuée, Cloud App Security analyse périodiquement les utilisateurs, les groupes, les activités et les fichiers. Toutes les activités sont disponibles après la première analyse complète. 

Cette analyse peut prendre du temps, en fonction de la taille du client, du nombre d’utilisateurs, et de la taille et du nombre de fichiers qui doivent être analysés. 

Selon l’application à laquelle vous vous connectez (voir le tableau ci-dessous), la connexion d’API présente les caractéristiques suivantes :  

-   **Informations de compte :**  

     Visibilité des utilisateurs, des comptes, des informations de profil, de l’état (suspendu, actif, désactivé), des groupes et des privilèges.  

-   **Piste d’audit :**  

     Visibilité des activités des utilisateurs, des administrateurs et des connexions.  

-   **Analyse de données :**  

     Analyse des données non structurées à l’aide de deux processus : analyse régulière (toutes les 12 heures) et analyse en temps réel (chaque fois qu’une modification est détectée).  

-   **Autorisations d’application :**  

     Visibilité des jetons émis et de leurs autorisations.  

-   **Gouvernance des comptes :**  

     Possibilité de suspendre les utilisateurs, de révoquer des mots de passe, etc.  

-   **Gouvernance des données :**  

     Possibilité de mettre des fichiers en quarantaine, y compris les fichiers dans la corbeille, et d’écraser des fichiers.  

-   **Gouvernance des autorisations d’application :**  

     Possibilité de supprimer des jetons.  

Le tableau suivant répertorie, par application cloud, les fonctionnalités prises en charge avec les connecteurs d’applications :  

> [!div class="mx-tableFixed"]
> 
> ||**Office 365**|**Box**|**Okta**|**G Suite**|**ServiceNow**|**Salesforce**|**Dropbox**|**AWS**|  
> |-|-|-|-|-|-|-|-|-|  
> |**Répertorier les comptes**|✔|✔|✔|✔|✔|✔|✔|✔|  
> |**Groupe**|✔|✔|✔|✔|✔|✔|✔|✔|  
> |**Privilèges**|✔|✔|Non prise en charge par le fournisseur|✔|✔|✔|✔||  
> |**Gouvernance des utilisateurs**|✔|✔||✔|Bientôt disponible|Bientôt disponible|Bientôt disponible||  
> |**Activité de connexion**|✔|✔|✔|✔|✔|✔|✔|✔|  
> |**Activité de l’utilisateur**|✔*|✔|✔|✔ - nécessite Google illimité|Partiel|Prise en charge avec Salesforce Shield|✔|Non applicable|  
> |**Activité d’administration**|✔|✔|✔|✔|Partiel|✔|✔|✔|  
> |**Analyse régulière des fichiers**|✔|✔|Non applicable|✔|✔|✔|✔|Non applicable|  
> |**Analyse des fichiers pratiquement en temps réel**|✔|✔|Non applicable|✔ - nécessite Google illimité|||Bientôt disponible||  
> |**Contrôle partagé**|✔|✔|Non applicable|✔|Non applicable||✔||  
> |**Quarantaine**|✔|✔|Non applicable|Bientôt disponible|||Bientôt disponible||  
> |**Voir les autorisations d’application**|✔|Non prise en charge par le fournisseur|Non applicable|✔||✔|Non prise en charge par le fournisseur||  
> |**Révoquer les autorisations d’application**|✔||Non applicable|✔||✔|Non applicable||  
> |**Appliquer des étiquettes Azure Information Protection**|✔|✔||✔|||||  

## <a name="prerequisites"></a>Prérequis  

- Pour certaines applications, vous pouvez être amené à ajouter des adresses IP à la liste verte pour permettre à Cloud App Security de collecter les journaux et de fournir un accès pour la console Cloud App Security. Pour plus d’informations, voir [Configuration requise pour le réseau](network-requirements.md).

- Pour chaque application à connecter avec l’intégration de l’API Cloud App Security, nous recommandons de créer un compte de service d’administration dédié à Cloud App Security.  

> [!NOTE]  
>  Pour obtenir des mises à jour quand des URL et des adresses IP ont changé, abonnez-vous au flux RSS comme expliqué dans [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).  

Pour utiliser des connecteurs d’applications, vous devez vérifier que vous avez les éléments suivants pour chaque application concernée :  

|Application|Type de licence|Utilisateur|  
|---------|------------------|----------|  
|Box|Enterprise|Il est fortement recommandé de vous connecter à Box en tant qu’administrateur. Une connexion en tant que coadministrateur entraînera une visibilité des données partielle seulement. Si vous vous connectez en tant que coadministrateur, veillez à sélectionner toutes les autorisations.|  
|G Suite|G Suite Unlimited de préférence<br /><br /> G Suite Enterprise (au minimum)|Super administrateur|  
|Office 365||Administrateur général|  
|AWS||Utilisateur récemment créé|  
|Dropbox|Business/Entreprises|Administrateur|  
|Okta|Enterprise (pas la version d’essai)|Administrateur|  
|Exchange||Administrateur général|  
|ServiceNow|Eureka et au-dessus|Administrateur + rôle RestAPI|  
|Salesforce||Administrateur|  


**ExpressRoute**  

Cloud App Security est déployé dans Azure et entièrement intégré à [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/). Toutes les interactions avec les applications Cloud App Security et le trafic envoyé vers Cloud App Security, notamment le chargement des journaux de découverte, sont acheminés via l’**homologation publique** ExpressRoute pour améliorer la latence, les performances et la sécurité. Aucune étape de configuration n’est nécessaire côté client.  
Pour plus d’informations sur l’homologation publique, consultez [Circuits ExpressRoute et domaines de routage](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/).  

## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  


## <a name="check-out-this-video"></a>Regardez cette vidéo !
[Microsoft Cloud App Security – API REST et jetons](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)  
