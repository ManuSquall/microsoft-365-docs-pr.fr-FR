---
title: Intégrer des appareils Windows 10 à Microsoft Defender ATP via une stratégie de groupe
description: Utilisez la stratégie de groupe pour déployer le package de configuration sur les appareils Windows 10 afin qu’ils soient intégrés au service.
keywords: configurer des appareils à l’aide de la stratégie de groupe, de la gestion des appareils, configurer des appareils Windows ATP, intégrer Microsoft Defender pour les appareils endpoint, stratégie de groupe
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: fc4b17ef96e85d3bacd4e83c2de3f4bb7fbfa5c3
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51166168"
---
# <a name="onboard-windows-10-devices-using-group-policy"></a>Intégrer des appareils Windows 10 à l’aide de la stratégie de groupe 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- Stratégie de groupe
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-configureendpointsgp-abovefoldlink)


> [!NOTE]
> Pour utiliser les mises à jour de stratégie de groupe (GP) pour déployer le package, vous devez être sur Windows Server 2008 R2 ou version ultérieure.
> 
> Pour Windows Server 2019, vous devrez peut-être remplacer NT AUTHORITY\Well-Known-System-Account par NT AUTHORITY\SYSTEM du fichier XML créé par la préférence de stratégie de groupe.

## <a name="onboard-devices-using-group-policy"></a>Intégrer des appareils à l’aide de la stratégie de groupe

[![Image du PDF montrant les différents chemins de déploiement](images/onboard-gp.png)](images/onboard-gp.png#lightbox)

Consultez le [pdf ou](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)  [Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.vsdx) pour voir les différents chemins d’accès dans le déploiement de Defender pour Endpoint. 



1. Ouvrez le fichier .zip du package de configuration *gp (WindowsDefenderATPOnboardingPackage.zip)* que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir du [Centre de sécurité Microsoft Defender](https://securitycenter.windows.com/):
 
    1. Dans le volet de navigation, sélectionnez **Intégration** des  >  **paramètres.**

    1. Sélectionnez Windows 10 comme système d’exploitation.
    
    1. Dans le **champ Méthode de déploiement,** sélectionnez **Stratégie de groupe.**
    
    1. Cliquez **sur Télécharger le package** et enregistrez le fichier .zip.

2. Extrayez le contenu du fichier .zip dans un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un dossier appelé *OptionalParamsPolicy* et le fichier *WindowsDefenderATPOnboardingScript.cmd*.

3. Ouvrez [la Console](https://docs.microsoft.com/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

4. Dans **l’Éditeur de gestion des stratégies** de groupe, allez à **Configuration** ordinateur, puis **Préférences,** puis **paramètres du panneau de configuration.**

5. Cliquez avec le bouton droit **sur Tâches programmées,** pointez sur **Nouveau,** puis cliquez sur **Tâche immédiate (Au moins Windows 7).**

6. Dans la **fenêtre** Tâche qui s’ouvre, allez dans **l’onglet** Général. Sous **Options de sécurité,** **cliquez sur Modifier** l’utilisateur ou le groupe, puis tapez SYSTEM, puis cliquez sur Vérifier **les noms,** **puis OK.** NT AUTHORITY\SYSTEM apparaît en tant que compte d’utilisateur que la tâche exécutera.

7. Sélectionnez **Exécuter, que l’utilisateur soit** connecté ou non et cochez la case Exécuter avec **les privilèges les plus élevés.**

8. Go to the **Actions** tab and click **New...** **Assurez-vous que démarrer un programme** est sélectionné dans le champ **Action.** Entrez le nom de fichier et l’emplacement du fichier *WindowsDefenderATPOnboardingScript.cmd* partagé.

9. Cliquez **sur OK** et fermez toutes les fenêtres GPMC ouvertes.

>[!TIP]
> Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier que l’appareil est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un appareil [Defender for Endpoint nouvellement intégré.](run-detection-test.md)

## <a name="additional-defender-for-endpoint-configuration-settings"></a>Paramètres de configuration defender supplémentaires pour les points de terminaison
Pour chaque appareil, vous pouvez déterminer si des échantillons peuvent être collectés à partir de l’appareil lorsqu’une demande est faite par le biais du Centre de sécurité Microsoft Defender pour soumettre un fichier pour analyse approfondie.

Vous pouvez utiliser la stratégie de groupe (GP) pour configurer des paramètres, tels que les paramètres de l’exemple de partage utilisé dans la fonctionnalité d’analyse approfondie.

### <a name="configure-sample-collection-settings"></a>Configurer des paramètres de collection d’exemples
1.  Sur votre appareil de gestion de la gp, copiez les fichiers suivants à partir du package de configuration :

    - Copier _AtpConfiguration.admx_ dans _C : Windows \\ \\ PolicyDefinitions_

    - Copier _AtpConfiguration.adml_ dans _C : Windows \\ \\ PolicyDefinitions \\ en-US_

    Si vous utilisez un magasin central pour les [modèles](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra)d’administration de stratégie de groupe, copiez les fichiers suivants à partir du package de configuration :
    
    - Copier _AtpConfiguration.admx_ dans _\\ \\ \<forest.root\> \\ SysVol \\ \<forest.root\> \\ Policies \\ PolicyDefinitions_

    - Copier _AtpConfiguration.adml_ dans _\\ \\ \<forest.root\> \\ SysVol \\ \<forest.root\> \\ Policies \\ PolicyDefinitions \\ en-US_

2.  Ouvrez la [Console de gestion des stratégies](https://docs.microsoft.com/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11)de groupe, cliquez avec le bouton droit sur l’GPO que vous souhaitez configurer, puis cliquez sur **Modifier.**

3.  Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration de l’ordinateur.**

4.  Cliquez **sur Stratégies,** **puis Modèles d’administration.**

5.  Cliquez **sur Composants Windows,** **puis Windows Defender ATP**.

6.  Choisissez d’activer ou de désactiver le partage d’exemples à partir de vos appareils.

>[!NOTE]
> Si vous ne définissez pas de valeur, la valeur par défaut consiste à activer la collection d’exemples.


## <a name="other-recommended-configuration-settings"></a>Autres paramètres de configuration recommandés

### <a name="update-endpoint-protection-configuration"></a>Mettre à jour la configuration de la protection des points de terminaison

Après avoir configuré le script d’intégration, continuez à modifier la même stratégie de groupe pour ajouter des configurations de protection des points de terminaison. Effectuez des modifications de stratégie de groupe à partir d’un système exécutant Windows 10 ou Server 2019 pour vous assurer que vous avez toutes les fonctionnalités requises de l’Antivirus Microsoft Defender. Vous devrez peut-être fermer et rouvrir l’objet de stratégie de groupe pour inscrire les paramètres de configuration de Defender ATP.

Toutes les stratégies se trouvent sous `Computer Configuration\Policies\Administrative Templates` .

**Emplacement de la stratégie :** \Composants Windows\Windows Defender ATP

Stratégie | Setting 
:---|:---
Enable\Disable Sample collection|   Activé : vérification « Activer la collecte d’exemples sur les ordinateurs »

<br/>

**Emplacement de la stratégie :**  \Windows Components\Windows Defender Antivirus

Stratégie | Setting 
:---|:---
Configurer la détection pour les applications potentiellement indésirables | Activé, Bloquer

<br/>

**Emplacement de la stratégie :** \Composants Windows\Windows Defender Antivirus\MAPS

Stratégie | Setting 
:---|:---
Rejoindre Microsoft MAPS | Enabled, Advanced MAPS
Envoyer des exemples de fichiers lorsque des analyses plus approfondies sont requises | Activé, Envoyer des exemples sûrs

<br/>

**Emplacement de la stratégie :** \Composants Windows\Windows Defender Antivirus\Protection en temps réel

Stratégie | Setting 
:---|:---
Désactiver la protection en temps réel|Désactivé
Activer l’analyse du comportement|Activé
Analyser tous les fichiers et pièces jointes téléchargés|Activé
Surveiller l’activité des fichiers et des programmes sur votre ordinateur|Activé

<br/>

**Emplacement de la stratégie :**  \Composants Windows\Windows Defender Antivirus\Analyse

Ces paramètres configurent des analyses périodiques du point de terminaison. Nous vous recommandons d’effectuer une analyse rapide hebdomadaire, autorisant les performances.

Stratégie | Setting 
:---|:---
Recherchez les dernières informations sur la sécurité des virus et logiciels espions avant d’exécution d’une analyse programmée |Activé


<br/>

**Emplacement de la stratégie :** \Composants Windows\antivirus Windows Defender\Windows Defender Exploit Guard\Réduction de la surface d’attaque

Obtenir la liste actuelle des GUID de réduction de la surface d’attaque à partir des règles de personnalisation de la [réduction de la surface d’attaque](customize-attack-surface-reduction.md)

1. Ouvrez la **stratégie Configurer la Réduction de la surface d’attaque.**

1. Sélectionnez **Activé**.

1. Sélectionnez le **bouton** Afficher.

1. Ajoutez chaque GUID dans le **champ Nom de** la valeur avec la valeur 2.

   Chacun d’eux est alors uniquement mis en place pour l’audit.

   ![Image de la configuration de réduction de la surface d’attaque](images/asr-guid.png)



Stratégie | Setting 
:---|:---
Configurer l’accès contrôlé aux dossiers| Activé, mode Audit



## <a name="offboard-devices-using-group-policy"></a>Appareils de tableau de bord à l’aide de la stratégie de groupe
Pour des raisons de sécurité, le package utilisé pour la sortie des appareils expirera 30 jours après la date de téléchargement. Les packages de offboarding expirés envoyés à un appareil seront rejetés. Lorsque vous téléchargez un package de déclassage, vous êtes informé de la date d’expiration des packages et il est également inclus dans le nom du package.

> [!NOTE]
> Les stratégies d’intégration et deboarding ne doivent pas être déployées sur le même appareil en même temps, sinon cela provoquera des collisions imprévisibles.

1. Obtenez le package deboarding à partir du [Centre de sécurité Microsoft Defender](https://securitycenter.windows.com/):

    1. Dans le volet de navigation, sélectionnez **Paramètres**  >  **Deboarding**.

    1. Sélectionnez Windows 10 comme système d’exploitation.
    
    1. Dans le **champ Méthode de déploiement,** sélectionnez **Stratégie de groupe.**

    1. Cliquez **sur Télécharger le package** et enregistrez le fichier .zip.

2. Extrayez le contenu du fichier .zip dans un emplacement partagé en lecture seule accessible par l’appareil. Vous devez avoir un fichier nommé *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Ouvrez [la Console](https://docs.microsoft.com/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) de gestion des stratégies de groupe (GPMC), cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

4. Dans **l’Éditeur de gestion des stratégies** de groupe, allez à **Configuration ordinateur,** puis **Préférences,** puis **paramètres du panneau de configuration.**

5. Cliquez avec le bouton droit **sur Tâches programmées,** pointez sur **Nouveau,** puis cliquez sur **Tâche immédiate.**

6. Dans la **fenêtre** Tâche qui s’ouvre, allez dans **l’onglet** Général. Choisissez le compte d’utilisateur SYSTÈME local (BUILTIN\SYSTEM) sous **Options de sécurité.**

7. Sélectionnez **Exécuter, que l’utilisateur soit** connecté ou non, puis cochez la case Exécuter avec les privilèges les plus **élevés.**

8. Go to the **Actions** tab and click **New...**. **Assurez-vous que démarrer un programme** est sélectionné dans le champ **Action.** Entrez le nom de fichier et l’emplacement du fichier *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd.*

9. Cliquez **sur OK** et fermez toutes les fenêtres GPMC ouvertes.

> [!IMPORTANT]
> Laboarding empêche l’appareil d’envoyer des données de capteur au portail, mais les données de l’appareil, y compris la référence aux alertes qu’il a eues, seront conservées pendant 6 mois.


## <a name="monitor-device-configuration"></a>Surveiller la configuration de l’appareil
Avec la stratégie de groupe, il n’existe pas d’option pour surveiller le déploiement des stratégies sur les appareils. La surveillance peut être effectuée directement sur le portail ou à l’aide des différents outils de déploiement.

## <a name="monitor-devices-using-the-portal"></a>Surveiller les appareils à l’aide du portail
1. Go to [Microsoft Defender Security Center](https://securitycenter.windows.com/).
2. Cliquez **sur Liste des appareils.**
3. Vérifiez que les appareils apparaissent.

> [!NOTE]
> L’affichage des appareils dans la liste Appareils peut prendre plusieurs **jours.** Cela inclut le temps qu’il faut pour que les stratégies soient distribuées à l’appareil, le temps qu’il faut avant que l’utilisateur se connecte et le temps qu’il faut au point de terminaison pour commencer à créer des rapports.


## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows 10 à l’aide de Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md)
- [Intégrer les appareils Windows 10 utilisant un script local](configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.](configure-endpoints-vdi.md)
- [Exécuter un test de détection sur un microsoft Defender pour les appareils de point de terminaison nouvellement intégré](run-detection-test.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)