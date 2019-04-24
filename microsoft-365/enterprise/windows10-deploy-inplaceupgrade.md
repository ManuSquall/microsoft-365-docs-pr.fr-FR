---
title: Déployer Windows 10 Entreprise pour les appareils existants en tant que mise à niveau inaltérable
description: Fournit des instructions sur la configuration et le déploiement d'une image Windows 10 entreprise à l'aide de System Center Configuration Manager en tant que mise à niveau sur place.
keywords: Microsoft 365, Microsoft 365 entreprise, documentation Microsoft 365, Windows 10 entreprise, déploiement, mise à niveau sur place, gestionnaire de configuration, System Center Configuration Manager
author: greg-lindsay
localization_priority: Normal
ms.collection: M365-modern-desktop
audience: microsoft-business
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.date: 08/30/2018
ms.author: greglin
ms.openlocfilehash: 31650774a784f1fe784c30b90bc1f9ae579b34fa
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32291611"
---
# <a name="step-2-deploy-windows-10-enterprise-for-existing-devices-as-an-in-place-upgrade"></a>Étape 2: déployer Windows 10 entreprise pour les appareils existants en tant que mise à niveau sur place

*Cet article s'applique à la fois aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/win10enterprise_icon-small.png)

Le chemin le plus simple pour mettre à niveau des PC actuellement exécutant Windows 7 ou Windows 8,1 vers Windows 10 est effectué via une mise à niveau sur place. Vous pouvez utiliser une séquence de tâches System Center Configuration Manager (gestionnaire de configuration) pour automatiser complètement le processus. 

Si des ordinateurs existants exécutent Windows 7 ou Windows 8,1, nous vous recommandons d'utiliser ce chemin d'accès si votre organisation déploie Windows 10. Cela tire parti du programme d'installation de Windows (Setup. exe) pour effectuer une mise à niveau sur place, qui conserve automatiquement toutes les données, les paramètres, les applications et les pilotes à partir de la version du système d'exploitation existant. Cela nécessite le moins d'efforts, car il n'est pas nécessaire d'utiliser une infrastructure de déploiement complexe.

Procédez comme suit pour configurer et déployer une image Windows 10 entreprise à l'aide de Configuration Manager en tant que mise à niveau sur place.

## <a name="part-1-verify-readiness-to-upgrade-windows"></a>Partie 1: vérifier la disponibilité pour mettre à niveau Windows

Tout d'abord, utilisez la fonctionnalité de disponibilité de la mise à niveau de Windows Analytics pour fournir des informations et des recommandations puissantes sur les ordinateurs, les applications et les pilotes de votre organisation, sans coût supplémentaire et sans exigences d'infrastructure supplémentaires. Ce nouveau service vous guide tout au long des projets de mise à niveau et de mise à jour des fonctionnalités à l'aide d'un flux de travail Microsoft recommandé. Les données d'inventaire mises à jour vous permettent d'équilibrer les coûts et les risques dans vos projets de mise à niveau.

Voir [gérer les mises à niveau Windows avec la préparation](https://docs.microsoft.com/windows/deployment/upgrade/manage-windows-upgrades-with-upgrade-readiness) à la mise à niveau pour en savoir plus, commencer, utiliser et résoudre les problèmes de préparation à la mise à niveau.

Ensuite, suivez le guide pour utiliser System Center Configuration Manager (branche actuelle) pour mettre à niveau le système d'exploitation Windows 7 ou une version ultérieure vers Windows 10. Comme pour tout déploiement à haut risque, nous vous recommandons de sauvegarder les données utilisateur avant de poursuivre. Le stockage cloud OneDrive est prêt à être utilisé pour les utilisateurs de Microsoft 365 titulaires d'une licence et peut être utilisé pour stocker leurs fichiers en toute sécurité. Pour plus d'informations, reportez-vous à la rubrique [OneDrive Quick Start Guide](https://aka.ms/ODfBquickstartguide). Pour accéder à cette page, vous devez vous connecter en tant qu'administrateur client ou administrateur global dans un client Office 365 ou Microsoft 365.

Pour obtenir la liste des versions de gestionnaire de configuration et les versions de client Windows 10 correspondantes prises en charge, voir [prise en charge de Windows 10 pour System Center Configuration Manager](https://aka.ms/supportforwin10sccm).

**Pour vérifier la disponibilité pour la mise à niveau de Windows**

Consultez ces conditions préalables avant de commencer le déploiement de Windows 10:

- **Éditions de Windows éligibles pour la mise à niveau** : vos appareils doivent exécuter des éditions de Windows 7 ou Windows 8,1 pouvant être mises à niveau vers Windows 10 entreprise. Pour obtenir la liste des éditions prises en charge, consultez la rubrique [Windows 10 Upgrade Paths](https://aka.ms/win10upgradepaths). 
- **Appareils pris en charge** : la plupart des ordinateurs compatibles avec Windows 8,1 sont compatibles avec Windows 10. Vous devrez peut-être installer des pilotes mis à jour dans Windows 10 pour que vos appareils fonctionnent correctement. Pour plus d'informations, voir [spécifications Windows 10](https://aka.ms/windows10specifications) .
- **Préparation du déploiement** : Assurez-vous que vous disposez des éléments suivants avant de commencer à configurer le déploiement:
    - Support d'installation de Windows 10: le support d'installation doit se trouver sur un lecteur distinct, avec l'ISO déjà monté. Vous pouvez obtenir l'ISO auprès des [Téléchargements réservés aux abonnés MSDN](https://aka.ms/msdn-subscriber-downloads) ou à partir du centre de gestion des [licences en volume](https://aka.ms/mvlsc).
    - Sauvegarde des données utilisateur: bien que les données utilisateur soient migrées dans la mise à niveau, il est recommandé de configurer un scénario de sauvegarde. Par exemple, exportez toutes les données utilisateur vers un compte OneDrive, BitLocker vers le lecteur flash USB ou le serveur de fichiers réseau. Pour plus d'informations, consultez la rubrique [sauvegarder ou transférer des données dans Windows](https://aka.ms/backuptransferdatawindows).
- **Préparation** de l'environnement: vous utiliserez une structure de serveur Configuration Manager existante pour préparer le déploiement du système d'exploitation. En plus de la configuration de base, les configurations suivantes doivent être effectuées dans l'environnement du gestionnaire de configuration:
    1. [Étendez le schéma Active Directory](https://aka.ms/extendadschema) et [créez un conteneur de gestion du système](https://aka.ms/createsysmancontainer).
    2. Activer la découverte de forêt Active Directory et la découverte de système Active Directory. Pour plus d'informations, consultez la rubrique [configure Discovery Methods for System Center Configuration Manager](https://aka.ms/configurediscoverymethods).
    3. Créez des limites de plage IP et un groupe de limite pour l'attribution de contenu et de site. Pour plus d'informations, voir [define site Limits and Boundary Groups for System Center Configuration Manager](https://aka.ms/definesiteboundaries).
    4. Ajoutez et configurez le rôle de point de création de rapports de gestionnaire de configuration. Pour plus d'informations, consultez la rubrique [configuration de la création de rapports dans le gestionnaire de configuration](https://aka.ms/configurereporting).
    5. Créez une structure de dossiers du système de fichiers pour les packages.
    6. Créez une structure de dossiers de la console Configuration Manager pour les packages.
    7. Installez les mises à jour de System Center Configuration Manager (branche actuelle) et les autres éléments prérequis de Windows 10.

## <a name="part-2-add-a-windows-10-os-image-using-configuration-manager"></a>Partie 2: ajout d'une image du système d'exploitation Windows 10 à l'aide du gestionnaire de configuration
À présent, vous devez créer un package de mise à niveau du système d'exploitation qui contient le support d'installation complet de Windows 10. Dans les étapes suivantes, vous allez utiliser le gestionnaire de configuration pour créer un package de mise à niveau pour Windows 10 entreprise x64.

**Pour ajouter une image du système d'exploitation Windows 10 à l'aide de Configuration Manager**

1. À l'aide de la console Configuration Manager, dans l'espace de travail **bibliothèque de logiciels** , cliquez avec le bouton droit sur le nœud **packages de mise à niveau du système d'exploitation** , puis sélectionnez **Ajouter un package de mise à niveau du système d'exploitation**.
2. Sur la page **source de données** , spécifiez le chemin d'accès UNC au support Windows 10 entreprise x64, puis cliquez sur **suivant**.
3. Sur la page **général** , spécifiez **mise à niveau de Windows 10 entreprise x64**, puis cliquez sur **suivant**. 
4. Sur la page **Résumé** , sélectionnez **suivant**, puis **Fermer**. 
5. Cliquez avec le bouton droit sur le package de **mise à jour Windows 10 entreprise x64** créé, puis sélectionnez **distribuer le contenu**. 
6. Choisissez votre point de distribution.

## <a name="part-3-configure-deployment-settings"></a>Partie 3: configurer les paramètres de déploiement
Dans cette étape, vous allez configurer une séquence de tâches de mise à niveau qui contient les paramètres de la mise à niveau de Windows 10. Vous identifiez ensuite les appareils à mettre à niveau, puis déployez la séquence de tâches sur ces appareils.

### <a name="create-a-task-sequence"></a>Créer une séquence de tâches
Pour créer une séquence de tâches de mise à niveau, procédez comme suit:
  
1. Dans la console Configuration Manager, dans l'espace de travail **bibliothèque de logiciels** , développez **systèmes d'exploitation**. 
2. Cliquez avec le bouton droit sur le nœud séquences de **tâches** , puis sélectionnez **créer une séquence de tâches**.
3. Dans la page **créer une nouvelle séquence de tâches** , sélectionnez **mettre à niveau un système d'exploitation à partir du package de mise à niveau**, puis cliquez sur **suivant**.
4. Sur la page informations sur la **séquence de tâches** , spécifiez la **mise à niveau de Windows 10 entreprise x64**, puis cliquez sur **suivant**.
5. Sur la page **mettre à niveau le système d'exploitation Windows** , sélectionnez **Parcourir** , puis choisissez le package de mise à niveau du **système d'exploitation Windows 10 entreprise x64**, sélectionnez **OK**, puis cliquez sur **suivant**.
6. Continuez à parcourir les autres pages de l'Assistant, puis sélectionnez **Fermer**.

### <a name="create-a-device-collection"></a>Créer une collection de périphériques
Après avoir créé la séquence de tâches de mise à niveau, vous devez créer une collection qui contient les périphériques que vous allez mettre à niveau.

> [!NOTE]
> Utilisez les paramètres suivants pour tester le déploiement sur un seul appareil. Vous pouvez utiliser des règles d'appartenance différentes pour inclure des groupes d'appareils lorsque vous êtes prêt. Pour plus d'informations, voir [comment créer des collections dans System Center Configuration Manager](https://aka.ms/sccm-create-collections).

1. Dans la console Configuration Manager, dans l'espace de travail **composants et conformité** , cliquez avec le bouton droit sur **ensembles de périphériques**, puis sélectionnez **créer une collection de périphériques**. 
2. Dans l'assistant créer une collection de périphériques, dans la page **général** , entrez les paramètres suivants, puis cliquez sur **suivant**:
    - Name: mise à niveau de Windows 10 entreprise x64
    - Limitation de la collecte: tous les systèmes
3. Sur la **page règles d'appartenance** , sélectionnez **Ajouter** > une règle de règle**directe** pour lancer l'Assistant Création d'une règle d'adhésion directe.
4. Sur la page d' **Accueil** de l'Assistant Création d'une règle d'adhésion directe, sélectionnez **suivant**.
5. Sur la page **Rechercher des ressources** , entrez les paramètres suivants, en remplaçant le texte de la **valeur** de l'espace réservé par le nom de l'appareil que vous mettez à niveau: 
    - Classe de ressource: ressource système
    - Nom de l'attribut: nom
    - Valeur: *PC0003*
6. Sur la page **Sélectionner les ressources** , sélectionnez votre appareil, puis sélectionnez **suivant**.
7. Terminez l'Assistant Création d'une règle d'adhésion directe et l'assistant créer une collection de périphériques.  
8. Passez en revue la collection de mises à niveau Windows 10 entreprise x64. Ne continuez pas tant que vous n'avez pas affiché les ordinateurs que vous avez ajoutés dans la collection.

### <a name="create-an-operating-system-deployment"></a>Créer un déploiement de système d'exploitation
Procédez comme suit pour créer un déploiement pour la séquence de tâches.

1. Dans la console Configuration Manager, dans l'espace de travail **bibliothèque de logiciels** , cliquez avec le bouton droit sur la séquence de tâches que vous avez créée au cours d'une étape précédente, puis sélectionnez **déployer**.
2. Sur la page **général** , sélectionnez la collection **mise à niveau de Windows 10 entreprise x64** , puis cliquez sur **suivant**.
3. Sur la page **contenu** , sélectionnez **suivant**.
4. Sur la page **paramètres de déploiement** , sélectionnez les paramètres suivants, puis cliquez sur **suivant**:

    > [!NOTE]
    > Pour ce déploiement de test, vous définirez l'objectif sur **disponible**, ce qui nécessite une intervention de l'utilisateur pour démarrer le déploiement. Dans un environnement de production, vous souhaiterez peut-être automatiser le déploiement à l'aide de l'objectif requis, ce qui implique la configuration d'options supplémentaires, telles que la planification lorsque le déploiement est exécuté. 

    - Action: installer
    - Objectif: disponible

5. Sur la page **planification** , acceptez les paramètres par défaut, puis cliquez sur **suivant**.
6. Sur la page **expérience utilisateur** , acceptez les paramètres par défaut, puis cliquez sur **suivant**.
7. Sur la page **alertes** , acceptez les paramètres par défaut, puis cliquez sur **suivant**.
8. Sur la page **Résumé** , sélectionnez **suivant**, puis **Fermer**.

## <a name="part-5-start-the-windows-10-upgrade-task-sequence"></a>Partie 5: démarrage de la séquence de tâches de mise à niveau vers Windows 10
Procédez comme suit pour démarrer la séquence de tâches de mise à niveau de Windows 10 sur l'appareil que vous mettez à niveau.
 
1. Ouvrez une session sur l'ordinateur Windows et démarrez le **Centre de logiciels**.
2. Sélectionnez la séquence de tâches que vous avez créée à une étape précédente, puis sélectionnez **installer**.
3. Lorsque la séquence de tâches commence, elle lance automatiquement le processus de mise à niveau sur place en appelant le programme d'installation Windows (Setup. exe) avec les paramètres de ligne de commande nécessaires pour effectuer une mise à niveau automatisée, qui conserve toutes les données, paramètres, applications et situés.
4. Une fois la séquence de tâches terminée, l'ordinateur sera entièrement mis à niveau vers Windows 10.

Si vous rencontrez des problèmes lors de l’utilisation de Windows 10 dans un environnement d’entreprise, vous pouvez consulter les [principales solutions Support Microsoft pour les problèmes les plus courants](https://docs.microsoft.com/windows/client-management/windows-10-support-solutions). Ces ressources incluent des articles de la Base de connaissances, des mises à jour et des articles de bibliothèque.

Lors du déploiement des mises à jour au sein de votre organisation, utilisez la fonctionnalité de conformité des mises à jour de Windows Analytics pour fournir une vue holistique de la conformité de la mise à jour du système d'exploitation, de la progression du déploiement et du dépannage des problèmes pour les appareils Windows 10. Ce nouveau service utilise des données de diagnostic, notamment la progression de l'installation, la configuration de Windows Update et d'autres informations pour fournir ces informations, sans coût supplémentaire et sans exigences d'infrastructure supplémentaires. Qu'il soit utilisé avec Windows Update pour les entreprises ou d'autres outils de gestion, vous pouvez être assuré que vos appareils sont correctement mis à jour.

Consultez [surveiller les mises à jour Windows et l'antivirus Windows Defender avec la conformité des mises à jour](https://docs.microsoft.com/windows/deployment/update/update-compliance-monitor) pour en savoir plus, commencer et utiliser la conformité des mises à jour.

Comme point de contrôle intermédiaire, consultez les [critères de sortie](windows10-exit-criteria.md#crit-windows10-step2) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step3.png)| [Déployer Windows 10 Entreprise pour des nouveaux appareils avec Windows Autopilot](windows10-deploy-autopilot.md) |



<!--

| Phases | Description |
|:--- |:--- |
| [Phase 1: Consideration phase](#phase-1-consideration-phase) | TBD |
| [Phase 2: Testing phase](#phase-2-testing-phase) | TBD |
| [Phase 3: Deployment phase](#phase-3-deployment-phase) | TBD |

## Phase 1: Consideration phase
Before upgrading an OS in an enterprise environment, take the following technical aspects into account:
* [Infrastructure](#step-1-infrastructure)
* [Apps](#step-2-apps)
* [Governance and business processes](#step-3-governance-and-business-processes)

This guide is meant only to provide Microsoft's best recommendations around these assumptions by providing links to existing documentation.

### Step 1: Infrastructure
Consider your organization's collection of hardware, software, policies, networks, and other related technologies as part of the deployment process.

For in-place upgrade with Configuration Manager, these are the infrastructure you need to take into account:

#### Group Policy
Windows 10 introduces many new features and removes and changes many others in Windows 7 and 8.1, including new Group Policy settings which you need to test and implement as part of a Windows 10 migration. Use the examples from the following resources to assess current group policies for Windows, including Group Policy Objects in the Active Directory structure:
* [Manage Windows 10 with administrative templates](https://go.microsoft.com/fwlink/?linkid=860226) - Get step-by-step info on how to manage Windows 10 with administrative templates
* [Group Policy settings that apply to Windows 10](https://docs.microsoft.com/windows/client-management/group-policies-for-enterprise-and-education-editions) - Find out which Group Policy settings apply only to Windows 10 Enterprise

> [!NOTE]
> If you are considering moving to modern management by using MDM instead of Group Policy to manage device configurations, you can start by using the [MDM Migration Analysis Tool (MMAT)](https://github.com/WindowsDeviceManagement/MMAT) to determine what Group Policies are set on the device and report the corresponding settings, if available.

#### Data management
Although in-place upgrades shouldn’t affect user data and apps, a best practice is to configure a backup scenario and back up user data. For example, export all user data to a OneDrive for Business account, BitLocker To Go-encrypted USB flash drive, or network file server. For more details, see:
* [How to back up or transfer your data on a Windows-based computer](https://go.microsoft.com/fwlink/?linkid=860230) - Get step-by-step info on how to manually back up your personal files and settings.
* [Redirect known folders to OneDrive for Business](https://go.microsoft.com/fwlink/?linkid=846620) - Learn how to set a policy at the domain level to make sure users all sync to the same folder when they install the OneDrive sync client and how you can set additional policies to redirect the Documents folder to that sync location.

#### System Center Configuration Manager
This guide assumes you are following Microsoft recommendations and have one of the following versions of System Center Configuration Manager 2012 onward:
* System Center 2012 Configuration Manager with SP2
* System Center 2012, 2012 R2 Configuration Manager with SP1, Current Branch, 1706
    * [Run an in-place upgrade to the latest Configuration Manager](https://go.microsoft.com/fwlink/?linkid=839406)
    * [Updates for Configuration Manager](https://go.microsoft.com/fwlink/?linkid=620343)
* Core Configuration Manager configuration:
    * CONFIGURATION MANAGER accounts
    * Active Directory permissions
    * Source folder structure
    * Active Directory schema
* Configure the following [necessary Configuration Manager components for Windows 10 deployment](https://go.microsoft.com/fwlink/?linkid=860245):
    * **State migration point** - Stores user state migration data during computer replace scenarios
    * **Distribution point** - Stores all packages in Configuration Manager
    * **Software update point** - Updates an OS as part of the deployment process
    * **Reporting services point** - Monitors the OS deployment process
    * **Boot images** - Are Windows Preinstallation Environment (PE) images used by Configuration Manager to start deployments
    * **OS images** - Denotes the production deployment image (mounted OS)
    * **OS installers** - Creates reference images using Microsoft Deployment Toolkit (MDT) Light Touch
    * **Drivers** - Denotes a repository of managed device drivers
    * **Task Sequence** - Is delivered automatically to the client as a policy

#### Network bandwidth
This guide assumes you have enough network bandwidth to support the deployment of Windows 10 Enterprise and Office 365 ProPlus as a unit. As a bundle, network bandwidth is a significant factor.

#### Client machines and in-place upgrade scenario
* Disk encryption - Third-party disk encryption isn't supported in an in-place upgrade scenario.
* User profiles - Only the standard user profile type is supported.
* Legacy BIOS to Unified Extensible Firmware Interface (UEFI) booting - Changing from legacy BIOS to UEFI booting isn't supported.
* Dual-boot - This scenario is not covered in the guide. If you have the FastTrack Benefit, it only covers devices running a single OS.
* Virtual desktop infrastructure (VDI) environments - This scenario is not covered in the guide. If you have the FastTrack Benefit, it doesn't cover configuration or deployment on VDI environments.
* x64 and x86 - Changing from a 32-bit OS to a 64-bit isn't supported. For more info, see [Windows 10 deployment scenario > In-place upgrade](https://docs.microsoft.com/windows/deployment/windows-10-deployment-scenarios#in-place-upgrade).

### Step 2: Apps

#### Security
Security clients (like antivirus, anti-malware, and anti-spam) are typically found on all PCs within an organization. Because these programs hook into the deeper levels of the OS, you may need to perform a compatibility assessment before starting any Windows 10 migrations. You may need to upgrade, reconfigure, or even replace Some software. Not performing this assessment can lead to:
* Native app compatibility checks failing and preventing an in-place upgrade from starting.
* Broken functionality in the security software.
* Instability after upgrading to Windows 10 (like crashing and reduced performance)

**Antivirus**

Assess current antivirus software. Windows 10 comes with Windows Defender Antivirus to protect devices from malware, viruses, and security threats. We recommend Windows Defender Antivirus. To enable Windows Defender Antivirus, see [Windows Defender Antivirus](windows10-enable-security-features.md#windows-defender-antivirus) and [Protect devices with Windows Defender Antivirus](https://go.microsoft.com/fwlink/?linkid=860254).

To learn about antivirus solutions from other providers, see [Consumer antivirus software providers for Windows](https://go.microsoft.com/fwlink/?linkid=67345).

#### App readiness
Each Windows 10 release provides improved app compatibility. However, some apps may not be compatible. Depending on the app, you may need to only do a simple upgrade or configuration update before upgrading to Windows 10. In other circumstances, you may need to remove an app entirely.

Be sure to assess business critical apps and understand the impact of upgrading to the next OS. Prioritize the workloads that impact the least number of people during deployment. 

See the following Upgrade Readiness resources to help with app inventory, driver compatibility issues, and usage information:
* [Manage Windows Upgrades with Upgrade Readiness](https://go.microsoft.com/fwlink/?linkid=860255) - Learn about the tools to help you plan and manage the upgrade process end to end, which allow you to adopt new Windows releases more quickly.
* [Configure Windows diagnostic data](https://go.microsoft.com/fwlink/?linkid=859970) - Find out about the importance of Windows diagnostic data and how Microsoft protects that data.

> [!NOTE]
> Upgrade Readiness may not be able to assess compatibility for custom and line-of-business (LOB) apps in an organization.

#### Language packs
In-place upgrades have have limitations when it comes to language packs. The language stays consistent throughout the upgrade. Verify the language version and make sure it stays consistent. For example, Windows 7 with English as the default won’t change when upgraded to Windows 10. For more info, see:
* [Default language pack on your OS](https://go.microsoft.com/fwlink/?linkid=860282)
* [Finding language packs on each Windows 10 deployment](https://go.microsoft.com/fwlink/?linkid=860283)

For a Microsoft 365 powered device, you'll also need to download Office 365 ProPlus language packs that applies to the client. These come in 32-bit (x86) or 64-bit (x64). A specific language must be installed as the default. You can install other languages later. For more info, see:
* [Choose between 64-bit or 32-bit version of Office](https://go.microsoft.com/fwlink/?linkid=862361) - Helps you decide which version of Office is right for you.
* [Language accessory pack for Office](https://go.microsoft.com/fwlink/?linkid=860280) - Follow the steps to install the language accessory pack for Office.
* [Add an additional language pack](https://go.microsoft.com/fwlink/?linkid=860281) - Get step-by-step info on adding a language or setting language preferences in Office.

### Step 3: Governance and business processes

#### Windows as a service
Windows 10 introduced the concept of Windows as a service. This greatly changes the frequency and style of updates to Windows. Instead of new versions being released every 3-5 years, a more incremental model is used where two smaller updates (Feature Updates) are released yearly. For more info, see:
* [Windows as a service on the Windows IT Pro Center](https://www.microsoft.com/itpro/windows-10/windows-as-a-service)
* [Overview of Windows as a service](https://go.microsoft.com/fwlink/?linkid=860288)
* [Update Windows 10 in the enterprise](https://go.microsoft.com/fwlink/?linkid=860285)

#### Pilot users and deployment rings
Be sure to have a pilot group of users selected from different parts of the business. If you have Microsoft 365 powered devices, Windows 10 and Office 365 ProPlus users should be in these deployment rings. This affects future Windows updates as well (including features and quality). You need to create and edit device collections by deployment rings to help minimize the effect on network bandwidth and simplify future updates. 

For the group of pilot users, create a device collection on Configuration Manager. The list of devices should correspond to the list of the first users upgraded to Windows 10. 

**Windows 10 deployment rings**

There are three servicing channels for OS deployment rings:
* Windows Insider Program - Provides organizations with the opportunity to test and provide feedback on features that are shipped in the next feature update.
* Semi-Annual Channel - Provides new functionality with twice-per-year feature update releases. Organizations can choose when to deploy updates from the Semi-Annual Channel.
* Long-Term Servicing Channel (LTSC) - Used for specialized devices and receives new feature releases about every three years.

For more info, see:
* [Windows Insider Program, Semi-Annual Channel, and Long-Term Servicing Channel](https://go.microsoft.com/fwlink/?linkid=860293)
* [Build deployment rings for Windows 10 updates](https://go.microsoft.com/fwlink/?linkid=860294)
* [Manage software updates using Intune in Azure Portal](https://docs.microsoft.com/intune/windows-update-for-business-configure)

**Office 365 ProPlus**

For Microsoft 365 powered devices, you must also be able to support the six-month update channel for both IT and business users. One way to do so is to have three groups:
* Current Channel
* Deferred Channel
* First-release for Deferred Channel

Each group has different configuration files, as users from the Current Channel are used as a pilot to test earlier updates. For more info, see:
* [Update process for Office 365 ProPlus](https://go.microsoft.com/fwlink/?linkid=860299)
* [Manage updates to Office 365 ProPlus](https://go.microsoft.com/fwlink/?linkid=860300)
* [Configure update settings for Office 365 ProPlus](https://go.microsoft.com/fwlink/?linkid=860301)
* [Update channels for Office 365 ProPlus](https://go.microsoft.com/fwlink/?linkid=860302)
* [Version and build numbers of update channel releases](https://go.microsoft.com/fwlink/?linkid=860304)

For more info, see [Phase 4: Office 365 ProPlus infrastructure for Microsoft 365 Enterprise](office365proplus-infrastructure.md).

## Phase 2: Testing phase
Once you've completed the scenarios and requirements in [Step 1: Consideration phase](#step-1-consideration-phase), you can move to this stage.
* [Networking](#step-1-networking)
* [Identity](#step-2-identity)
* [Client readiness](#step-3-client-readiness)
* [System Center Configuration Manager](#step-4-system-center-configuration-manager)
* [Diagnostic data](#step-5-diagnostic-data)

### Step 1: Networking
Ports to the client need to be opened for Office 365 ProPlus (for a Microsoft 365 powered device) and Configuration Manager. For more details about setting up your Microsoft 365 Enterprise networking infrastructure, see [Phase 1: Networking](networking-infrastructure.md).

When setting up your networking infrastructure as part your in-place upgrade, make sure you complete these steps:
1. Read the best practices for [network planning and improving migration performance for Office 365](http://go.microsoft.com/fwlink/?LinkId=733655).
2. [Plan for network devices that connect to Office 365 services](http://go.microsoft.com/fwlink/?LinkId=733652).
3. [Review network impact of directory synchronization](http://go.microsoft.com/fwlink/?LinkId=733652).
4. Calculate the number of clients to use per IP address and understand [Network Address Translation (NAT) support with Office 365](http://go.microsoft.com/fwlink/?LinkId=733653) and how it impacts the number of users and client devices you can serve with a single IP address.
5. If your organization restricts computers on your network from connecting to the Internet, you'll need to understand the [endpoints (fully qualified domain names (FQDNs), ports, URLs, IPv4, and IPv6 address ranges)](http://go.microsoft.com/fwlink/?LinkID=280129) that you should include in your outbound allow lists to ensure your computers can successfully use Office 365 services.
6. [Create domain name system records for Office 365 at any Domain Name System hosting provider](http://go.microsoft.com/fwlink/?LinkId=733656).
7. [Reduce mail exchange (MX) DNS record time to live (TTL) value](http://go.microsoft.com/fwlink/?LinkId=733656).

### Step 2: Identity
Intelligent security for Microsoft 365 Enterprise, in which the right users have access to the right resources with an appropriate level of access, begins with identity management. For more details about setting up your Microsoft 365 Enterprise identity infrastructure, see [Phase 2: Identity](identity-infrastructure.md).

When setting up your identity infrastructure as part of your in-place upgrade, make sure you complete these tasks:
1. [Add a domain and users to Office 365](http://go.microsoft.com/fwlink/?LinkID=526338).
2. [Install and run the Office 365 IdFix tool](http://go.microsoft.com/fwlink/?LinkId=733662), which scans your on-premises Active Directory environment and identifies problems that might impact directory synchronization and slow your migration to Office 365.
3. Configure Active Directory for directory synchronization with Office 365 and [integrate on-premises directories with Azure AD](http://go.microsoft.com/fwlink/?LinkId=733661).
4. [Prepare to provision users through directory synchronization to Office 365](http://go.microsoft.com/fwlink/?LinkId=733659).
5. Know the [prerequisites for Azure AD Connect](http://go.microsoft.com/fwlink/?LinkId=733663), then install and run the Azure AD Connect tool to synchronize your on-premises Active Directory to the Azure AD service used by Office 365.
6. Determine custom installation of Azure AD Connect (full version of SQL Server for directory synchronization, if required).
7. [Integrate your on-premises identities with Azure AD](http://go.microsoft.com/fwlink/?LinkID=733485).
8. [Sync a list of required attributes with AD Connect](https://go.microsoft.com/fwlink/?linkid=860363) to get all the features in Office 365 and Windows 10.
9. Activate Windows 10 Enterprise licenses, which are checked based on Azure AD credentials.

    This provides a systematic way to assign licenses to end users and groups in your organization. For more info, see [Windows 10 Subscription Activation](https://go.microsoft.com/fwlink/?linkid=860365) and [Deploy Windows 10 licenses](https://go.microsoft.com/fwlink/?linkid=860367).

### Step 3: Client readiness

#### System requirements for Office 365
Confirm that Windows 10 works with Office 365. Be sure you're using the latest OS version and browsers with Office 365 and have updated them with the latest service packs. For more info on Office requirements, see [System requirements for Office](http://go.microsoft.com/fwlink/?LinkID=394412).

### Step 4: System Center Configuration Manager
See [System Center Configuration Manager](#system-center-configuration-manager).

### Step 5: Diagnostic data
Microsoft uses diagnostic data to help keep Windows devices secure by identifying malware trends and other threats and to help us improve the quality of Windows and Microsoft services. You must ensure that the diagnostics service is enabled at a minimum level of Basic on all endpoints in your organization. **By default, this service is enabled and set to the Enhanced level.** However, it’s good practice to check and ensure that they are receiving sensor data. Setting levels through policies overrides device-level settings. 

**Windows 10 operating system diagnostic data levels**

You can configure your operating system diagnostic data settings using the management tools you’re already using, such as Group Policy, MDM, or Windows Provisioning. You can also manually change your settings using Registry Editor. Setting your diagnostic data levels through a management policy overrides any device level settings.

Use the appropriate value in the table below when you configure the management policy.

| Level | Data gathered | Value |
|:--- |:--- |:--- |
| Security | Security data only. | 0 |
| Basic | Security data, and basic system and quality data. | 1 |
| Enhanced | Security data, basic system and quality data, and enhanced insights and advanced reliability data. | 2 |
| Full | Security data, basic system and quality data, enhanced insights and advanced reliability data, and full diagnostics data. | 3 |

You can enable diagnostics data through these methods:
* Microsoft Intune - If you plan to use Intune to manage your devices, you can create a configuration policy to enable diagnostic data by configuring the <a href="https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry" target="blank">SystemAllowTelemetry</a> system policy. For more info on setting up configuration policies, see [Manage settings and features on your devices with Microsoft Intune policies](https://aka.ms/intuneconfigpolicies).
* Registry Editor - You can use the Registry Editor to manually enable diagnostic data on each device in your organization, or write a script to edit the registry. If a management policy already exists, such as Group Policy or MDM, it will override this registry setting.
* Group Policy - If you do not plan to enroll devices in Intune, you can use a Group Policy object to set your organization’s diagnostic data level.
* Command prompt - You can set Windows 10 diagnostics data and service to automatically start with the command prompt. This method is best if you are testing the service on only a few devices. Enabling the service to start automatically with this command will not configure the diagnostic data level. If you have not configured a diagnostic data level using management tools, the service will operate with the default Enhanced level.

See [Configure Windows diagnostic data in your organization](https://docs.microsoft.com/windows/configuration/configure-windows-diagnostic-data-in-your-organization) to learn more about Windows diagnostic data and how you can enable it based on the method that you choose.

## Phase 3: Deployment phase
When ready, complete these:
* [In-place upgrade to Windows 10 Enterprise](#31-in-place-upgrade-to-windows-10-enterprise)
* [Windows Defender Antivirus](#32-windows-defender-antivirus)

### Step 1: In-place upgrade to Windows 10 Enterprise
1. Integrate System Center Configuration Manager with Microsoft Deployment Tool.

    Be sure to use the Microsoft Deployment Toolkit (MDT) in conjunction with Configuration Manager when deploying an updated version of Windows 10. MDT brings Zero Touch Installation and Light Touch Installation enhancements to help with deployments at no cost to the customer. For more info, see:
    * [Download the latest MDT](https://go.microsoft.com/fwlink/?linkid=860465)
    * [Deploy Windows 10 with the Microsoft Deployment Toolkit](https://go.microsoft.com/fwlink/?linkid=860466)

2. Prepare for zero touch installation.

    As part of zero touch installation, you are responsible for preparing the following:
    * Configuration Manager service accounts
    * Active Directory permissions
    * Source folder structure

    Then, [integrate Configuration Manager with MDT](https://go.microsoft.com/fwlink/?linkid=860035).

3. Create a custom Windows Preinstallation Environment boot image.

    Windows Preinstallation Environment (PE) is a pre-installation environment required for OS deployments. It’s used to prepare a client machine for Windows installation, to copy disk images from a network file server, and to initiate Windows Setup. It’s used for Windows 10 Enterprise editions. For more info, see:
    * [Overview of Windows PE](https://go.microsoft.com/fwlink/?linkid=860468)
    * [Windows PE features, hardware requirements, and limitations](https://go.microsoft.com/fwlink/?linkid=860469)
    * [Create a custom Windows PE boot image with Configuration Manager](https://go.microsoft.com/fwlink/?linkid=860470)

4. Add a Windows 10 OS upgrade image.

    You need to create a Windows 10 reference image with MDT (as needed). Reference images are the foundation of what each of the client machine’s OS looks like. The image should be in a separate folder located with the already-mounted ISO file. The task sequence looks for and then runs “setup.exe”. 

    Follow the steps to create and add a Windows 10 OS upgrade image on Configuration Manager:
    * [Create a Windows 10 reference image](https://go.microsoft.com/fwlink/?linkid=860500)
    * [Add a Windows 10 OS image using Configuration Manager](https://go.microsoft.com/fwlink/?linkid=860501)

5. Create an app to deploy with Windows 10.

    For a Microsoft 365 powered device, you can deploy Office 365 ProPlus with Windows 10 Enterprise using Configuration Manager. You can also add other apps as needed.

    To deploy Office 365 ProPlus, follow the steps in [Phase 4: Office 365 ProPlus infrastructure for Microsoft 365 Enterprise](office365proplus-infrastructure.md). During this phase, make sure you complete these steps:
    
    1. Download the Office 2016 Deployment Tool (ODT) in conjunction with Configuration Manager to help with Office 365 ProPlus deployments. 
    2. Edit the configuration XML file to fit specific deployment needs (like version, language, and product element). 
    
    You can then create apps with Configuration Manager. For more info, see:
    * [Configuration options for ODT](https://go.microsoft.com/fwlink/?linkid=860504)
    * [Create apps in Configuration Manager](https://go.microsoft.com/fwlink/?linkid=761079)
    * [Deploy Office 365 ProPlus with Configuration Manager](https://go.microsoft.com/fwlink/?linkid=860506)

6. Add drivers to a Windows 10 deployment using Windows PE.

    Network drivers need to be created for both Windows PE and Windows 10 to connect deployment shares and storage drivers with local storage on a client computer. Use Configuration Manager to create these drivers required for deployment. For more info, see [Add drivers to a Windows 10 deployment with Windows PE using Configuration Manager](https://go.microsoft.com/fwlink/?linkid=860036).

7. Create a task sequence.

    A task sequence (a collection of commands) is required for MDT Lite Touch Installation (LTI). You need to create and then edit the task sequence for optimal deployment experience. One of the configurations enable support for Unified Extensible Firmware Interface (UEFI). The UEFI environment is a minimal boot OS where devices are booted and the Windows 10 OS runs. For more info, see:
    * [Overview of Windows Boot Manager](https://go.microsoft.com/fwlink/?linkid=860696)
    * [Create the task sequence in Configuration Manager](https://go.microsoft.com/fwlink/?linkid=860697)

8. Finalize the OS configuration for Windows 10 deployment.

    **To finalize the OS configuration**

    1. Enable MDT monitoring
    2. Create and share the Logs folder
    3. Configure the rules
    4. Distribute content to the distribution point (a server running Configuration Manager)
    5. Create a deployment for the task sequence

   For more info, see [Finalize OS configuration with Configuration Manager](https://go.microsoft.com/fwlink/?linkid=860697).

9. Deploy the Windows 10 Enterprise image to a UEFI machine.

    For more info, see [Deploy Windows 10 using Configuration Manager](https://go.microsoft.com/fwlink/?linkid=860697).

10. Monitor the Windows 10 deployment.

    Use Configuration Manager and MDT to monitor your deployment. Deployment Workbench enables access to the computer remotely using the Diagnostics and Recovery Toolset (DaRT) (optional). Deployments can be monitored in Configuration Manager. For more info, see [Monitor the Windows 10 deployment with Configuration Manager](https://go.microsoft.com/fwlink/?linkid=860705).

### Step 2: Windows Defender Antivirus
See [Enable Windows 10 Enterprise security features > Windows Defender Antivirus](windows10-enable-security-features.md#windows-defender-antivirus)

-->
