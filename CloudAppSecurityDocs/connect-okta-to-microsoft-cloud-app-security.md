---
title: "Connecter Okta à Cloud App Security pour la visibilité et le contrôle d’utilisation | Microsoft Docs"
description: "Cette rubrique fournit des informations sur la connexion de votre application Okta à Cloud App Security à l’aide du connecteur API."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9c3673b9-99bd-400c-9da1-5bf809ea5892
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a7aa0ffc06f46307154baf2d6998c6425719097a
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2018
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Connecter Okta à Microsoft Cloud App Security
Cette section fournit des instructions pour connecter Cloud App Security à votre compte Okta existant à l’aide des API du connecteur.  
  
## <a name="how-to-connect-okta-to-cloud-app-security"></a>Comment connecter Okta à Cloud App Security  
  
1.  Nous vous recommandons de créer un compte de service d’administration dans Okta pour Cloud App Security.  
  
     Veillez à utiliser un compte disposant des autorisations de super administrateur.  
  
     Assurez-vous que votre compte Okta est vérifié.  
  
2.  Dans la console Okta, cliquez sur **Admin**.  
  
    -   Cliquez sur **Security** (Sécurité), puis sur **API**.  
  
         ![okta, api](./media/okta-api.png "okta, api")  
  
    -   Cliquez sur **Create Token** (Créer un jeton).  
  
         ![okta, créer un jeton](./media/okta-createtoken.jpg "okta, créer un jeton")  
  
    -   Dans la fenêtre contextuelle **Create Token** (Créer un jeton), nommez votre jeton Cloud App Security et cliquez sur **Create Token** (Créer un jeton).  
  
         ![okta, fenêtre contextuelle de jeton](./media/okta-token-popup.png "okta, fenêtre contextuelle de jeton")  
  
    -   Dans la fenêtre contextuelle **Token created successfully** (Jeton créé), copiez le contenu de **Token value** (Valeur du jeton).  
  
         ![okta, valeur du jeton](./media/okta-token-value.png "okta, valeur du jeton")  
  
3.  Dans la console Cloud App Security, cliquez sur **Examiner**, puis sur **Applications connectées**.  
  
4.  Dans la page **Connecteurs d’application**, cliquez sur le bouton plus (+), puis sur **Okta**.  
  
     ![connecter okta](./media/connect-okta.png "connecter okta")  
  
5.  Dans la fenêtre contextuelle qui s’affiche, dans le champ **Domaine**, entrez votre domaine Okta et collez votre jeton dans le champ **Jeton**.  
  
6.  Cliquez sur **Connect** (Connecter) pour créer le jeton pour Okta dans Cloud App Security.  
  
7.  Vérifiez la connexion en cliquant sur **Test API** (Tester l’API).  
  
     Le test peut prendre quelques minutes. Une fois averti que la connexion a réussi, cliquez sur **Fermer**.  
  
Après avoir connecté Okta, vous recevrez les événements des 60 jours précédant la connexion.
  
## <a name="see-also"></a>Voir aussi  
[Contrôler les applications cloud avec des stratégies](control-cloud-apps-with-policies.md)   

[Les clients Premier peuvent également choisir Cloud App Security directement depuis le portail Premier.](https://premier.microsoft.com/)  
  
  