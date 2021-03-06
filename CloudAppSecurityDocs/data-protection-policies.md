---
title: "Créer des stratégies pour surveiller et protéger les fichiers dans vos applications cloud | Microsoft Docs"
description: "Cette rubrique décrit la procédure de configuration d’une stratégie de données pour surveiller et contrôler les données et les fichiers lors de l’usage des applications cloud de votre organisation."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/11/2018
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ac53fbd6-4d31-4bce-b2bc-9dc65ad83b3e
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 63024ea9395c6f765928076a8d6eb9861fa35238
ms.sourcegitcommit: 2f1ccff60194573325afa01f1634eea373c829b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="file-policies"></a>Stratégies de fichier  
Les stratégies de fichier vous permettent d’appliquer une large gamme de processus automatisés en exploitant les API du fournisseur de cloud. Vous pouvez définir des stratégies pour fournir des analyses de conformité en continu, des tâches eDiscovery réglementaires, une protection contre la perte de données (DLP, Data Loss Prevention) au contenu sensible partagé publiquement et de nombreux autres cas d’usage.  <br></br>

Cloud App Security peut surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées (par exemple, niveau d’accès, type de fichier). 
 
**Types de fichiers pris en charge** 

Les moteurs intégrés de protection contre la perte de données (DLP) de Cloud App Security effectuent l’inspection du contenu en extrayant le texte de tous les types de fichiers courants (plus de 100), dont Office, Open Office, les fichiers compressés, différents formats de texte enrichi, XML, HTML et bien plus encore.

Le moteur combine trois aspects sous chaque stratégie :  
  
-   Analyse du contenu basé sur des modèles prédéfinis ou des expressions personnalisées.  
  
-   Filtres de contexte comprenant des rôles d’utilisateur, des métadonnées de fichiers, un niveau de partage, une intégration des groupes d’organisation, un contexte de collaboration et d’autres attributs personnalisables.  
  
-   Actions automatisées pour la gouvernance et la correction. Pour plus d’informations, consultez [Contrôle](control.md).  
  
Une fois activée, la stratégie analyse en permanence votre environnement cloud et identifie les fichiers qui correspondent aux filtres de contenu et de contexte, puis applique les actions automatisées demandées. Ces stratégies détectent et corrigent toutes les violations concernant les informations au repos ou le contenu nouvellement créé. Les stratégies peuvent être surveillées à l’aide d’alertes en temps réel ou de rapports générés par une console.  
  
Voici quelques exemples de stratégies de fichier que vous pouvez créer :  
  
-   Fichiers partagés publiquement : <br></br>
    Recevez une alerte quand un fichier situé dans le cloud est publiquement partagé en sélectionnant tous les fichiers dont le niveau de partage est public.  
  
-   Le nom de fichier publiquement partagé contient le nom de l’organisation : <br></br> Recevez une alerte quand un fichier contient le nom de votre organisation et qu’il est publiquement partagé. Sélectionnez les fichiers dont le nom contient celui de votre organisation et qui sont publiquement partagés.  
  
-   Partage avec des domaines externes :  <br></br>
    Recevez une alerte quand un fichier est partagé avec des comptes appartenant à des domaines externes spécifiques, par exemple, au domaine d’un concurrent. Sélectionnez le domaine externe avec lequel vous voulez limiter le partage.  
  
-   Mettez en quarantaine les fichiers partagés qui n’ont pas été modifiés pendant la dernière période :  <br></br>
    Recevez une alerte sur les fichiers partagés que personne n’a modifié dernièrement, afin de les mettre en quarantaine ou d’activer une action automatisée. Excluez tous les fichiers privés qui n’ont pas été modifiés pendant une plage de dates spécifiée. Sur G Suite, vous pouvez choisir de mettre en quarantaine ces fichiers, en cochant la case « Fichier en quarantaine » dans la page de création de stratégie.  
  
-   Partage avec des utilisateurs non autorisés :  <br></br>
    Recevez une alerte quand des fichiers sont partagés avec un groupe non autorisé d’utilisateurs dans votre organisation. Sélectionnez les utilisateurs pour lesquels le partage n’est pas autorisé.  
  
-   Extension de fichier sensible :  <br></br>
    Recevez une alerte quand des fichiers portant des extensions spécifiques sont potentiellement très exposés. Sélectionnez l’extension spécifique (par exemple, crt pour les certificats) ou le nom de fichier et excluez celles avec le niveau de partage privé.  
  
Pour créer une stratégie de fichier, procédez comme suit :  
  
1.  Dans la console, cliquez sur **Contrôle**, puis sur **Stratégies**.  
  
2.  Cliquez sur **Créer une stratégie** et sélectionnez la stratégie **Fichier**.  
  
3.  Donnez à votre stratégie un nom et une description. Si vous le souhaitez, vous pouvez la baser sur un modèle ; pour plus d’informations sur les modèles de stratégie, consultez [Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md).  
  
3. Définissez une **Gravité de la stratégie**. Si Cloud App Security est défini pour vous envoyer des notifications en cas de correspondances de stratégie pour un niveau de gravité de stratégie spécifique, votre sélection détermine si les correspondances de cette stratégie déclenchent une notification.

4.  Dans **Catégorie**, liez la stratégie au type de risque le plus approprié. Ce champ est à titre informatif uniquement et vous permet de rechercher ultérieurement des stratégies et alertes spécifiques, selon le type de risque.  Le risque est peut-être déjà présélectionné en fonction de la catégorie pour laquelle vous avez choisi de créer la stratégie. Par défaut, les stratégies de fichier ont la valeur DLP.  
  
5.  Pour définir les applications découvertes qui déclenchent cette stratégie, **Créez un filtre pour les fichiers sur lesquels cette stratégie s’appliquera**. limitez les filtres de stratégie jusqu’à atteindre l’ensemble de fichiers le plus précis sur lequel vous voulez agir. Soyez aussi restrictif que possible pour éviter les faux positifs. Par exemple, si vous voulez supprimer les autorisations publiques, n’oubliez pas d’ajouter le filtre **Public** ; si vous voulez supprimer un utilisateur externe, utilisez le filtre « Externe », etc.  
> [!NOTE] 
> Quand vous utilisez des filtres de stratégie, le filtre **Contains (Contient)** recherche uniquement des mots entiers, séparés par des virgules, points, espaces ou traits de soulignement. Par exemple, si vous recherchez **malware** ou **virus**, il trouve virus_malware_file.exe, mais pas malwarevirusfile.exe. Si vous recherchez **malware.exe**, vous obtenez TOUS les fichiers exe dont le nom contient malware ou exe, tandis que si vous recherchez **"malware.exe"** (avec les guillemets), vous n’obtenez que les fichiers dont le nom contient exactement « malware.exe ». **Equals (Est égal à)** recherche uniquement la chaîne complète ; par exemple, si vous recherchez **malware.exe**, il trouve malware.exe, mais pas malware.exe.txt.  
6.   Sous le premier filtre **Appliquer à**, sélectionnez **dossiers sélectionnés** ou **tous les fichiers excepté les dossiers sélectionnés** pour Box, SharePoint, Dropbox, OneDrive. Vous pouvez ainsi appliquer votre stratégie de fichiers à tous les fichiers de l’application ou à des dossiers spécifiques. Votre êtes redirigé pour vous connecter à l’application cloud. Ajoutez ensuite les dossiers appropriés.  

6. Sous le deuxième filtre **Appliquer à**, sélectionnez **tous les propriétaires de fichiers**, **propriétaires de fichiers de groupes d’utilisateurs sélectionnés** ou **tous les propriétaires de fichiers à l’exception de groupes sélectionnés**, puis sélectionnez les groupes d’utilisateurs appropriés pour déterminer les utilisateurs et les groupes à inclure dans la stratégie.
  
7.  Sélectionnez la **Méthode d’inspection du contenu**. La protection contre la perte de données (DLP) intégrée vous permet de filtrer les fichiers par leur contenu. Pour analyser le contenu des fichiers, sélectionnez ensuite **DLP intégré**. Une fois que l’inspection du contenu est activée, vous pouvez choisir d’utiliser des expressions prédéfinies ou de rechercher d’autres expressions personnalisées, sous forme de sous-chaîne ou d’[expression régulière](working-with-the-regex-engine.md) de votre choix.  <br></br>

    De plus, vous pouvez spécifier une expression régulière pour exclure un fichier des résultats. Cette possibilité s’avère très utile si vous avez des mots clés de classification interne standard à exclure de la stratégie. <br></br> Vous pouvez décider de définir le nombre minimal de violations de contenu à atteindre avant que le fichier ne soit considéré comme une violation. Par exemple, vous pouvez choisir 10 si vous souhaitez être alerté pour les fichiers comportant au moins 10 numéros de carte de crédit détectés dans leur contenu.  <br></br>
    Quand du contenu correspond à l’expression sélectionnée, le texte de la violation est remplacé par des caractères « X ». Par défaut, les violations sont masquées. Seul leur contexte, 100 caractères avant et après la violation, est affiché. Les chiffres dans le contexte de l’expression sont remplacés par des caractères « # » et ne sont jamais stockés dans Cloud App Security. Vous pouvez sélectionner l’option **Montrer les quatre derniers caractères d’une violation** pour annuler le masquage des quatre derniers caractères de la violation elle-même. Il est nécessaire de définir les types de données que l’expression régulière recherche : contenu, métadonnées et/ou nom de fichier. Par défaut, elle recherche le contenu et les métadonnées. Vous devez définir au moins un type de données à rechercher, sinon l’expression régulière ne fonctionne pas et la stratégie ne peut pas être créée. 
  
8.  Choisissez les actions de **gouvernance** que Cloud App Security doit exécuter quand une correspondance est détectée.  
  
9. Une fois que vous avez créé votre stratégie, vous pouvez l’afficher sous l’onglet **Stratégie de fichier**. Vous pouvez toujours modifier une stratégie, ajuster ses filtres ou modifier les actions automatisées. La stratégie est automatiquement activée lors de la création et démarre immédiatement l’analyse de vos fichiers cloud.  Soyez vigilant quand vous définissez des actions de gouvernance. Elles peuvent entraîner une perte irréversible des autorisations d’accès à vos fichiers. Il est recommandé d’affiner les filtres pour représenter exactement les fichiers sur lesquels vous voulez agir, en utilisant plusieurs champs de recherche. Plus les filtres sont précis, mieux c’est. Pour obtenir des instructions, vous pouvez utiliser le bouton **Modifier et afficher un aperçu des résultats** dans la section Filtres.  
  
   ![stratégie de fichier, modifier et afficher un aperçu des résultats](./media/file-policy-edit-and-preview-results.png "stratégie de fichier, modifier et afficher un aperçu des résultats")  
  
10. Pour afficher les correspondances de stratégie de fichier, les fichiers qui sont suspectés d’enfreindre la stratégie, cliquez sur **Contrôle**, puis sur **Stratégies**. Filtrez les résultats pour afficher uniquement les stratégies de fichier avec le filtre **Type** en haut. Pour plus d’informations sur les correspondances pour chaque stratégie, cliquez sur une stratégie. Vous affichez ainsi les fichiers Mise en correspondance maintenant pour la stratégie. Cliquez sur l’onglet **Historique** pour consulter un historique remontant jusqu’à six mois de fichiers correspondant à la stratégie.     
  
## <a name="file-policy-reference"></a>Informations de référence sur les stratégies de fichier  
Cette section fournit des informations de référence sur les stratégies, donne une explication de chaque type de stratégie et décrit les champs que vous pouvez configurer pour chacune d’elles. 
  
Une **stratégie de fichier** est une stratégie basée sur une API qui vous permet de contrôler le contenu de votre organisation dans le cloud, en tenant compte de plus de 20 filtres de métadonnées de fichiers (dont le propriétaire et le niveau de partage), ainsi que des résultats de l’inspection du contenu. Les résultats de la stratégie déterminent les actions de gouvernance applicables. Le moteur d’inspection du contenu peut être étendu par le biais de moteurs DLP tiers, ainsi que de solutions anti-programme malveillant.  
  
Chaque stratégie comprend les éléments suivants :  
  
-   Filtres de fichiers : Vous permettent de créer des conditions précises en fonction des métadonnées.  
  
-   Inspection du contenu : Vous permet de limiter la stratégie, en fonction de résultats de moteur DLP. Vous pouvez inclure une expression personnalisée ou prédéfinie. Vous pouvez définir des exclusions et choisir le nombre de correspondances. Vous pouvez aussi utiliser l’anonymisation pour masquer le nom de l’utilisateur. 
  
-   Actions : La stratégie fournit un ensemble d’actions de gouvernance automatiquement applicables en cas de violations.  Ces actions sont réparties en actions de collaboration, actions de sécurité et actions d’examen.

-   Extensions  
   
    -  L’inspection du contenu peut être effectuée via des moteurs tiers pour améliorer les fonctionnalités DLP ou anti-programme malveillant.  

  
## <a name="see-also"></a>Voir aussi  
[Activités quotidiennes pour protéger votre environnement cloud](daily-activities-to-protect-your-cloud-environment.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  