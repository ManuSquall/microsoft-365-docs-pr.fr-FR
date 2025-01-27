---
title: Planifier votre déploiement de Microsoft Defender pour les points de terminaison
description: Sélectionnez la meilleure stratégie de déploiement de Microsoft Defender pour les points de terminaison pour votre environnement
keywords: déployer, planifier, stratégie de déploiement, cloud natif, gestion, sur site, évaluation, intégration, local, stratégie de groupe, gp, gestionnaire de point de terminaison, mem
search.product: eADQiWindows 10XVcnh
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
ms.technology: mde
ms.openlocfilehash: 8cd670e72bbb4ec0abacd4ed053a9ea9af12608b
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51163574"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>Planifier votre déploiement de Microsoft Defender pour les points de terminaison 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-secopsdashboard-abovefoldlink) 


Planifiez votre déploiement de Microsoft Defender pour endpoint afin d’optimiser les fonctionnalités de sécurité de la suite et de mieux protéger votre entreprise contre les cybermenaces.


Cette solution fournit des conseils sur l’identification de l’architecture de votre environnement, la sélection du type d’outil de déploiement qui répond le mieux à vos besoins et des instructions sur la configuration des fonctionnalités.


![Image du flux de déploiement](images/deployment-guide-plan.png)


## <a name="step-1-identify-architecture"></a>Étape 1 : identifier l’architecture
Comme nous savons que chaque environnement d’entreprise est unique, nous avons fourni plusieurs options pour vous offrir la flexibilité nécessaire pour choisir le déploiement du service.

Selon votre environnement, certains outils conviennent mieux à certaines architectures. 

Utilisez les documents suivants pour sélectionner l’architecture defender pour point de terminaison appropriée qui convient le mieux à votre organisation.

| Item | Description |
|:-----|:-----|
|[![Image miniature de la stratégie de déploiement de Defender for Endpoint](images/mdatp-deployment-strategy.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)<br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)  \| [Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.vsdx) | Le matériel architectural vous aide à planifier votre déploiement pour les architectures suivantes : <ul><li> Cloud-natif </li><li> Cogestion </li><li> Sur site</li><li>Évaluation et intégration locale</li>



## <a name="step-2-select-deployment-method"></a>Étape 2 : Sélectionner la méthode de déploiement
Defender pour le point de terminaison prend en charge divers points de terminaison que vous pouvez intégrer au service. 

Le tableau suivant répertorie les points de terminaison pris en charge et l’outil de déploiement correspondant que vous pouvez utiliser pour planifier le déploiement de manière appropriée.

| Point de terminaison     | Outil de déploiement                       |
|--------------|------------------------------------------|
| **Windows**  |  [Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Gestionnaire de périphériques mobiles](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Scripts VDI](configure-endpoints-vdi.md)   |
| **MacOS**    | [Script local](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JamF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md) |
| **Serveur Linux** | [Script local](linux-install-manually.md) <br> [Sondent](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Basée sur l’application](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 



## <a name="step-3-configure-capabilities"></a>Étape 3 : Configurer les fonctionnalités
Après l’intégration des points de terminaison, configurez les fonctionnalités de sécurité dans Defender pour le point de terminaison afin que vous pouvez optimiser la protection de sécurité robuste disponible dans la suite. Les fonctionnalités sont les suivantes :

- Détection et réponse du point de terminaison
- Protection de nouvelle génération
- Réduction de la surface d'attaque


  
## <a name="related-topics"></a>Voir aussi
- [Phases de déploiement](deployment-phases.md)
