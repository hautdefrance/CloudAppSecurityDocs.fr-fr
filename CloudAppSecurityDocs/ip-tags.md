---
title: "Définir des balises et des plages d’adresses IP | Microsoft Docs"
description: "Cette rubrique fournit des instructions sur l’utilisation des balises et des catégories d’adresses IP."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: bbf54f66-4ce2-428c-afc8-b5a64277014f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b3c8c8917606f3c34055eef0334f010d8aab7998
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
#  <a name="IPtagsandRanges"></a> Utilisation des balises et des plages d’adresses IP

Pour identifier facilement les adresses IP connues, telles que les adresses IP physiques de votre bureau, vous devez définir des plages d’adresses IP qui vous permettent de marquer et de classer les adresses de manière appropriée, ainsi que de personnaliser la façon dont les journaux et les alertes sont affichés et examinés.   
Chaque groupe de plages IP peut être classé selon une liste de catégories d’adresses IP prédéfinies ou marqué avec des étiquettes IP créées par vos soins. En outre, ce paramètre vous permet de remplacer les informations de géolocalisation publiques en fonction de votre connaissance du réseau interne.  
  
IPv4 et IPv6 sont pris en charge.  
  
Cloud App Security est préconfiguré avec des balises intégrées pour les adresses IP suivantes : 
- Client natif
- Système d’exploitation obsolète
- Appareils gérés
- Proxy anonyme
- Botnet
- Tor
- Appareil conforme
- Appareil vérifié
- Emprunter l’identité

Pour utiliser ces balises intégrées dans le cadre d’une recherche, reportez-vous à leur ID dans la documentation des API Cloud App Security. 



Dans la barre de menus, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png "icône des paramètres") et sélectionnez **Plages d’adresses IP**. Cliquez sur **Ajouter une plage d’adresses IP** et définissez les éléments suivants :  
  
> [!NOTE]  
>  L’emplacement et l’ISP enregistré remplacent les valeurs par défaut.   
> Toutefois, les étiquettes IP sont ajoutées à l’activité sans remplacer les données.  
  
1.  Affectez un **Nom** à votre plage IP. Le nom n’apparaît pas dans le journal des activités ; il sert uniquement à gérer votre plage IP.  
  
     Pour inclure la plage IP dans une catégorie d’adresses IP, sélectionnez une catégorie dans le menu déroulant.  
  
2.  Entrez la **plage d’adresses IP** que vous souhaitez configurer, puis cliquez sur le bouton « + ». Vous pouvez ajouter autant d’adresses et de sous-réseaux IP que vous le souhaitez en utilisant la notation de préfixe réseau (également appelée notation CIDR), par exemple 192.168.1.0/32.  
  
3.  Dans les champs qui permettent de **remplacer l’emplacement** ou l’ISP de l’organisation associés à ces adresses, entrez la nouvelle valeur. Par exemple, si vous avez une adresse IP publiquement considérée en Irlande, alors qu’elle se trouve aux États-Unis, vous pouvez remplacer ce paramètre.  
  
4.  Entrez un **ISP enregistré**. Cette opération remplace les données dans vos activités.  
  
5.  Pour **étiqueter** les activités liées à ces adresses IP, entrez une étiquette. Il suffit d’entrer un mot dans la zone pour créer l’étiquette. Une fois l’étiquette configurée, vous pouvez l’ajouter facilement à des plages IP supplémentaires en la sélectionnant dans la liste. Vous pouvez ajouter autant d’étiquettes IP que vous le souhaitez pour chaque plage. Vous pouvez utiliser des étiquettes IP quand vous créez des stratégies.  En plus des étiquettes IP que vous configurez, Cloud App Security a des étiquettes prédéfinies qui ne sont pas configurables. Vous pouvez voir la liste des étiquettes sous le [filtre d’étiquettes IP](activity-filters.md).  
  
6.  Les **catégories IP** permettent d’identifier facilement les activités liées aux adresses IP intéressantes. Les catégories sont disponibles dans le portail, mais nécessitent une configuration utilisateur pour déterminer les adresses IP à inclure dans chaque catégorie, à l’exception de la catégorie « Risqué » qui comprend deux balises IP : Proxy anonyme et Tor.  
  
     Les catégories IP suivantes sont disponibles :  
  
    -   **Administratif** : adresses IP de vos administrateurs  
  
    -   **Interne** : adresses IP de votre réseau interne, de vos succursales et adresses d’itinérance Wi-Fi.  
  
    -   **Risqué** : toutes les adresses IP que vous considérez comme risquées. Celles-ci peuvent inclure les adresses IP suspectes déjà constatées, les adresses IP appartenant aux réseaux de vos concurrents, etc.  
  
    -   **VPN** : toutes les adresses IP que vous utilisez pour les télétravailleurs  
  
    -   **Proxy du cloud** : adresse IP de votre proxy dans le cloud  
  
7.  Quand vous avez terminé, cliquez sur **Créer**.  
  
     ![plage de nouvelles adresses IP](./media/newipaddress-range.png "plage de nouvelles adresses IP")  
  
  
    
## <a name="see-also"></a>Voir aussi  
[Configurer Cloud Discovery](set-up-cloud-discovery.md)   
[Pour obtenir un support technique, visitez la page de support assisté Cloud App Security.](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  