---
title: Configurer le chargement automatique des journaux pour des rapports continus | Documentation Microsoft
description: Cette rubrique décrit la procédure de configuration du chargement automatique des journaux pour des rapports continus dans Cloud App Security à l’aide d’un Docker sur Ubuntu dans Azure.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9c51b888-54c0-4132-9c00-a929e42e7792
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3eb6f6b5338273abc31d0019a967d269aa51bed4
ms.sourcegitcommit: c7e4351345d55cfeb0517651446490ce5f208651
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2018
ms.locfileid: "37140735"
---
*S’applique à : Microsoft Cloud App Security*

# <a name="set-up-and-configuration-on-ubuntu"></a>Installation et configuration sur Ubuntu


## <a name="technical-requirements"></a>Spécifications techniques

-   Système d’exploitation : Ubuntu 14.04 et 16.04 (pour les versions plus récentes, contactez le support)

-   Espace disque : 250 Go

-   Processeur : 2

-   RAM : 4 Go

-   Configurez votre pare-feu, comme décrit dans [Configuration réseau requise](network-requirements.md#log-collector)

## <a name="log-collector-performance"></a>Performances du collecteur de journaux

Le collecteur de journaux peut gérer correctement une capacité allant jusqu’à 50 Go par heure. Les principaux goulots d’étranglement dans le processus de collecte des journaux sont les suivants :

-   Bande passante réseau : votre bande passante réseau détermine la vitesse de chargement des journaux.

-   Performances d’E/S de la machine virtuelle allouées par votre service informatique : détermine la vitesse à laquelle les journaux sont écrits sur le disque du collecteur de journaux. Le collecteur de journaux dispose d’un mécanisme de sécurité intégré qui surveille le débit auquel les journaux arrivent et le compare au débit de chargement. En cas de congestion, le collecteur de journaux commence à supprimer des fichiers journaux. Si votre configuration dépasse généralement 50 Go par heure, nous vous recommandons de diviser le trafic entre plusieurs collecteurs de journaux.

## <a name="set-up-and-configuration"></a>Installation et configuration  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>Étape 1 : configuration du portail web  - définir les sources de données et les lier à un collecteur de journaux

1. Accédez à la page des paramètres de chargement automatisé :  <br></br>Dans le portail Cloud App Security, cliquez sur l’icône des paramètres ![icône des paramètres](./media/settings-icon.png), puis sur **Collecteurs de journaux**.

2. Pour chaque pare-feu ou proxy à partir desquels vous voulez charger des journaux, créez une source de données correspondante :

   ![ubuntu1](./media/ubuntu1.png)

   a. Cliquez sur **Ajouter une source de données**.

   b. **Nommez** votre proxy ou pare-feu.

   c. Sélectionnez l’appareil dans la liste **Source**. Si vous sélectionnez **Format de journal personnalisé** pour utiliser une appliance réseau qui n’est pas spécifiquement répertoriée, consultez [Utilisation de l’analyseur de journal personnalisé](custom-log-parser.md) pour obtenir des instructions de configuration.

   d. Comparez votre journal à l’exemple de format de journal attendu. Si votre format de fichier journal ne correspond pas à cet exemple, vous devez ajouter votre source de données en tant qu’**Autre**.

   e. Définissez le **Type de récepteur** sur **FTP**, **FTPS**, **Syslog – UDP** ou **Syslog – TCP** ou **Syslog – TLS**.
   >[!NOTE]
   >L’intégration à des protocoles de transfert sécurisés (FTPS et Syslog – TLS) nécessite souvent un paramètre supplémentaire ou votre pare-feu/proxy.

   f. Répétez ce processus pour chaque pare-feu ou proxy dont les journaux peuvent être utilisés pour détecter le trafic sur votre réseau.

3. Accédez à l’onglet **Collecteurs de journaux** en haut.

   a. Cliquez sur **Ajouter un collecteur de journaux**.

   b. Donnez un **nom** au collecteur de journaux.

   c. Entrez **l’adresse IP hôte** de l’ordinateur sur lequel est déployé le Docker. 

    > [!NOTE]
    > L’adresse IP de l’hôte peut être remplacée par le nom de l’ordinateur s’il existe un serveur DNS (ou un équivalent) qui résout le nom d’hôte.

   d. Sélectionnez toutes les **Sources de données** que vous voulez connecter au collecteur, puis cliquez sur **Mettre à jour** pour enregistrer la configuration et consulter les étapes suivantes du déploiement.

   ![ubuntu2](./media/ubuntu2.png)

   > [!NOTE]
   > - Un seul collecteur de journaux peut gérer plusieurs sources de données.
   > - Copiez le contenu de l’écran, car vous aurez besoin des informations lors de la configuration du collecteur de journaux pour communiquer avec Cloud App Security. Si vous avez sélectionné Syslog, ces informations vont inclure des informations sur le port utilisé par l’écouteur Syslog pour écouter.

4. Des informations supplémentaires sur le déploiement s’affichent. **Copiez** la commande d’exécution à partir de la boîte de dialogue. Vous pouvez utiliser l’icône de copie dans le Presse-papiers ![icône de copie dans le Presse-papiers](./media/copy-icon.png).

5. **Exportez** la configuration de sources de données attendue. Cette configuration décrit comment définir l’exportation du journal dans vos appliances.

   ![Créer le collecteur de journaux](./media/windows7.png)

### <a name="step-2--deployment-of-your-machine-in-azure"></a>Étape 2 : déploiement de la machine dans Azure

> [!NOTE]
> La procédure suivante décrit le déploiement dans Ubuntu. Les étapes de déploiement pour d’autres plateformes sont légèrement différentes.


1. Créez une nouvelle machine Ubuntu dans votre environnement Azure. 
2. Une fois la machine configurée, ouvrez les ports ainsi :
   1. Dans l’affichage Ordinateur, accédez à **Réseau** et sélectionner l’interface souhaitée en double-cliquant dessus.
   2. Accédez à **Groupe de sécurité réseau** et sélectionnez le groupe de sécurité réseau qui convient.
   3. Accédez à **Règles de sécurité du trafic entrant** et cliquez sur **Ajouter**,
      
      ![Ubuntu Azure](./media/ubuntu-azure.png)
    
   4. Ajoutez les règles suivantes (en mode **Avancé**) :

   |Nom|Plages du port de destination|Protocol|Source|Destination|
   |----|----|----|----|----|
   |caslogcollector_ftp|21|TCP|<Sous-réseau d’adresse IP de votre appliance>|Indifférent|
   |caslogcollector_ftp_passive|20000-20099|TCP|<Sous-réseau d’adresse IP de votre appliance>|Indifférent|
   |caslogcollector_syslogs_tcp|601-700|TCP|<Sous-réseau d’adresse IP de votre appliance>|Indifférent|
   |caslogcollector_syslogs_udp|514-600|UDP|<Sous-réseau d’adresse IP de votre appliance>|Indifférent|
      
    ![Règles Ubuntu Azure](./media/inbound-rule.png)

3. Revenez à l’ordinateur et cliquez sur **Se connecter** pour ouvrir un terminal dessus.

4. Appliquez les privilèges racines avec `sudo -i`.

5. Si vous acceptez les [termes du contrat de licence logiciel](https://go.microsoft.com/fwlink/?linkid=862492), désinstallez les anciennes versions et installez Docker CE en exécutant la commande suivante :
        
       curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh

     ![Commande Ubuntu Azure](./media/ubuntu-azure-command.png)

6. Dans la fenêtre **Créer un collecteur de journaux** du portail Cloud App Security, copiez la commande pour importer la configuration du collecteur sur la machine hôte :

      ![Ubuntu Azure](./media/windows7.png)

7. Exécutez la commande pour déployer le collecteur de journaux.
     
        (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter

     ![Proxy Ubuntu](./media/ubuntu-proxy.png)

8. Pour vérifier que le collecteur s’exécute correctement, exécutez la commande suivante : `Docker logs <collector_name>`. Vous devriez obtenir les résultats : **Terminé avec succès !**

   ![ubuntu8](./media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>Étape 3 : Configuration locale de vos appliances réseau

Configurez vos pare-feu réseau et proxys pour exporter régulièrement les journaux vers le port Syslog dédié du répertoire FTP selon les instructions données dans la boîte de dialogue, par exemple :

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>Étape 4 : Vérifier la réussite du déploiement dans le portail Cloud App Security

Consultez l’état du collecteur dans le tableau **Collecteur de journaux** et vérifiez que l’état est **Connecté**. Si l’état est **Créé**, il est possible que la connexion du collecteur de journaux et l’analyse ne soient pas effectuées.

 ![ubuntu9](./media/ubuntu9.png)

Vous pouvez aussi accéder au **journal de gouvernance** et vérifier que les journaux sont régulièrement chargés sur le portail.

Si vous rencontrez des problèmes lors du déploiement, consultez [Dépannage de Cloud Discovery](troubleshooting-cloud-discovery.md).

### <a name="optional---create-custom-continuous-reports"></a>Facultatif : Créer des rapports continus personnalisés

Après avoir vérifié que les journaux sont en cours de chargement dans Cloud App Security et que les rapports sont générés, vous pouvez créer des rapports personnalisés. Vous pouvez maintenant créer des rapports de découverte personnalisés basés sur les groupes d’utilisateurs Azure Active Directory. Par exemple, si vous voulez afficher l’utilisation cloud de votre service marketing, vous pouvez importer le groupe marketing à l’aide de la fonctionnalité d’importation des groupes d’utilisateurs, puis créer un rapport personnalisé pour ce groupe. Vous pouvez également personnaliser un rapport en fonction d’une balise d’adresse IP ou de plages d’adresses IP.

1. Dans le portail Cloud App Security, dans les Paramètres (roue crantée), sélectionnez **Paramètres Cloud Discovery**, puis **Gérer les rapports continus**. 
2. Cliquez sur le bouton **Créer un rapport** et renseignez les champs.
3. Sous **Filtres**, vous pouvez filtrer les données par source de données, par [groupe d’utilisateurs importé](user-groups.md) ou par [balises et plages d’adresses IP](ip-tags.md). 

![Rapport continu personnalisé](./media/custom-continuous-report.png)

## <a name="see-also"></a>Voir aussi
[Résolution des problèmes du déploiement docker Cloud Discovery](troubleshoot-docker.md)

[Les clients Premier peuvent également choisir Cloud App Security directement dans le portail Premier.](https://premier.microsoft.com/)

