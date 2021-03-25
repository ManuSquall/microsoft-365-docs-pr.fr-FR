---
title: Intégration à l’aide de Microsoft Endpoint Configuration Manager
description: Découvrez comment intégrer Microsoft Defender pour endpoint à l’aide de Microsoft Endpoint Configuration Manager
keywords: intégration, configuration, déploiement, déploiement, gestionnaire de configuration de point de terminaison, mdatp, protection avancée contre les menaces, création de collections, réponse de détection de point de terminaison, protection nouvelle génération, réduction de la surface d’attaque, gestionnaire de configuration de point de terminaison Microsoft
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
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 31c946ccad84aca3b2fc86c95655cea9e66e182f
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51186400"
---
# <a name="onboarding-using-microsoft-endpoint-configuration-manager"></a>Intégration à l’aide de Microsoft Endpoint Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


Cet article fait partie du guide de déploiement et agit comme un exemple de méthode d’intégration. 

Dans la [rubrique Planification,](deployment-strategy.md) plusieurs méthodes ont été fournies pour intégrer des appareils au service. Cette rubrique traite de l’architecture de cogestion. 

![Image de l’architecture native du cloud ](images/co-management-architecture.png)
 *Diagramme des architectures d’environnement*


Bien que Defender pour point de terminaison prend en charge l’intégration de différents points de terminaison et outils, cet article ne les traite pas. Pour plus d’informations sur l’intégration générale à l’aide d’autres outils et méthodes de déploiement pris en charge, voir [vue d’ensemble de l’intégration.](onboarding.md)



Cette rubrique guide les utilisateurs dans :
- Étape 1 : intégration d’appareils Windows au service 
- Étape 2 : Configuration de Defender pour les fonctionnalités de point de terminaison

Ces instructions d’intégration vous guident tout au long des étapes de base suivantes que vous devez suivre lors de l’utilisation de Microsoft Endpoint Configuration Manager :
- **Création d’une collection dans Microsoft Endpoint Configuration Manager**
- **Configuration des fonctionnalités de Microsoft Defender pour les points de terminaison à l’aide de Microsoft Endpoint Configuration Manager**

>[!NOTE]
>Seuls les appareils Windows sont couverts dans cet exemple de déploiement. 



## <a name="step-1-onboard-windows-devices-using-microsoft-endpoint-configuration-manager"></a>Étape 1 : Intégrer des appareils Windows à l’aide de Microsoft Endpoint Configuration Manager

### <a name="collection-creation"></a>Création de collection
Pour intégrer des appareils Windows 10 avec Microsoft Endpoint Configuration Manager, le déploiement peut cibler une collection existante ou une nouvelle collection peut être créée pour les tests. 

L’intégration à l’aide d’outils tels que la stratégie de groupe ou la méthode manuelle n’installe aucun agent sur le système. 

Dans la console Microsoft Endpoint Configuration Manager, le processus d’intégration est configuré dans le cadre des paramètres de conformité au sein de la console.

Tout système qui reçoit cette configuration requise conserve cette configuration tant que le client Configuration Manager continue de recevoir cette stratégie à partir du point de gestion. 

Suivez les étapes ci-dessous pour intégrer des points de terminaison à l’aide de Microsoft Endpoint Configuration Manager.

1. Dans la console Microsoft Endpoint Configuration Manager, accédez à **Assets and Compliance \> Overview Device \> Collections**.            

    ![Image de l’Assistant Microsoft Endpoint Configuration Manager1](images/configmgr-device-collections.png)

2. Cliquez avec le bouton **droit sur La collection d’appareils,** puis **sélectionnez Créer une collection d’appareils.**

    ![Image de l’Assistant Microsoft Endpoint Configuration Manager2](images/configmgr-create-device-collection.png)

3. Fournissez **un nom** et **limitez la collection,** puis sélectionnez **Suivant**.

    ![Image de l’Assistant Microsoft Endpoint Configuration Manager3](images/configmgr-limiting-collection.png)

4. Sélectionnez **Ajouter une règle** et choisissez Règle de **requête.**

    ![Image de l’Assistant Microsoft Endpoint Configuration Manager4](images/configmgr-query-rule.png)

5.  Cliquez **sur Suivant** dans **l’Assistant Adhésion directe** et cliquez sur Modifier **l’instruction de requête.**

     ![Image de l’Assistant Microsoft Endpoint Configuration Manager5](images/configmgr-direct-membership.png)

6. Sélectionnez **Critères,** puis sélectionnez l’icône étoile.

     ![Image de l’Assistant Microsoft Endpoint Configuration Manager6](images/configmgr-criteria.png)

7. Conservez le type de critère comme **valeur simple,**  choisissez où en tant que système d’exploitation - numéro de **build**, opérateur supérieur ou égal à et valeur **14393** et cliquez sur **OK**.

    ![Image de l’Assistant Microsoft Endpoint Configuration Manager7](images/configmgr-simple-value.png)

8. Sélectionnez **Suivant** et **Fermez.**

    ![Image de l’Assistant Microsoft Endpoint Configuration Manager8](images/configmgr-membership-rules.png)

9. Sélectionnez **Suivant**.

    ![Image de l’Assistant Microsoft Endpoint Configuration Manager9](images/configmgr-confirm.png)


Après avoir effectué cette tâche, vous avez maintenant une collection d’appareils avec tous les points de terminaison Windows 10 dans l’environnement. 


## <a name="step-2-configure-microsoft-defender-for-endpoint-capabilities"></a>Étape 2 : Configurer Microsoft Defender pour les fonctionnalités de point de terminaison 
Cette section vous guide dans la configuration des fonctionnalités suivantes à l’aide de Microsoft Endpoint Configuration Manager sur les appareils Windows :

- [**Détection et réponse des points de terminaison**](#endpoint-detection-and-response)
- [**Protection nouvelle génération**](#next-generation-protection)
- [**Réduction de la surface d’attaque**](#attack-surface-reduction)


### <a name="endpoint-detection-and-response"></a>Détection et réponse au point de terminaison
#### <a name="windows-10"></a>Windows 10
À partir du Centre de sécurité Microsoft Defender, il est possible de télécharger la stratégie « .onboarding » qui peut être utilisée pour créer la stratégie dans System Center Configuration Manager et déployer cette stratégie sur les appareils Windows 10.

1. À partir d’un portail centre de sécurité Microsoft Defender, [sélectionnez Paramètres, puis Intégration.](https://securitycenter.windows.com/preferences2/onboarding)



2. Sous Méthode de déploiement, sélectionnez la version prise en charge **de Microsoft Endpoint Configuration Manager.**

    ![Image de l’Assistant Intégration de Microsoft Defender pour les points de terminaison10](images/mdatp-onboarding-wizard.png)

3. Sélectionnez **le package de téléchargement.**

    ![Image de l’Assistant Intégration de Microsoft Defender pour les points de terminaison11](images/mdatp-download-package.png)

4. Enregistrez le package dans un emplacement accessible.
5. Dans Microsoft Endpoint Configuration Manager, accédez à : **Assets and Compliance > Overview > Endpoint Protection > Microsoft Defender ATP Policies**.

6. Cliquez avec le bouton **droit sur Stratégies Microsoft Defender ATP** et **sélectionnez Créer une stratégie Microsoft Defender ATP.**

    ![Image de l’Assistant Microsoft Endpoint Configuration Manager12](images/configmgr-create-policy.png)

7. Entrez le nom et la description, vérifiez **que l’intégration** est sélectionnée, puis sélectionnez **Suivant**.

    ![Image de l’Assistant Microsoft Endpoint Configuration Manager13](images/configmgr-policy-name.png)


8. Cliquez sur **Parcourir**.

9. Accédez à l’emplacement du fichier téléchargé à l’étape 4 ci-dessus.

10. Cliquez sur **Suivant**.
11. Configurez l’agent avec les exemples appropriés (**Aucun** ou **Tous les types de fichiers).**

    ![Image des paramètres de configuration1](images/configmgr-config-settings.png)

12. Sélectionnez la télémétrie appropriée **(Normale** ou **Accélérée),** puis cliquez sur **Suivant**.

    ![Image des paramètres de configuration2](images/configmgr-telemetry.png)

14. Vérifiez la configuration, puis cliquez sur **Suivant.**

     ![Image des paramètres de configuration3](images/configmgr-verify-configuration.png)

15. Cliquez **sur Fermer** une fois l’Assistant terminé.

16.  Dans la console Microsoft Endpoint Configuration Manager, cliquez avec le bouton droit sur la stratégie Defender for Endpoint que vous avez créée et sélectionnez **Déployer.**

     ![Image des paramètres de configuration4](images/configmgr-deploy.png)

17. Dans le panneau droit, sélectionnez la collection créée précédemment et cliquez sur **OK.**

    ![Image des paramètres de configuration5](images/configmgr-select-collection.png)


#### <a name="previous-versions-of-windows-client-windows-7-and-windows-81"></a>Versions précédentes de Windows Client (Windows 7 et Windows 8.1)
Suivez les étapes ci-dessous pour identifier l’ID d’espace de travail Defender pour le point de terminaison et la clé d’espace de travail, qui seront requis pour l’intégration des versions précédentes de Windows.

1. À partir d’un portail centre de sécurité Microsoft Defender, **sélectionnez Paramètres >'intégration.**

2. Sous le système **d’exploitation, choisissez Windows 7 SP1 et 8.1**.

3. Copiez **l’ID d’espace de travail** et la clé **d’espace de travail** et enregistrez-les. Ils seront utilisés plus tard dans le processus.

    ![Image de l’intégration](images/91b738e4b97c4272fd6d438d8c2d5269.png)

4. Installez l’agent de surveillance Microsoft (MMA). <br>
    MMA est actuellement pris en charge (depuis janvier 2019) sur les systèmes d’exploitation Windows suivants :

    -   SSO serveur : Windows Server 2008 SP1 ou plus nouveau

    -   SSO client : Windows 7 SP1 et ultérieur

    L’agent MMA doit être installé sur les appareils Windows. Pour installer l’agent, certains systèmes doivent télécharger la mise à jour pour l’expérience client et la [télémétrie](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry) de diagnostic afin de collecter les données avec MMA. Ces versions système incluent, sans s’y limiter, les éléments suivants :

    -   Windows 8.1

    -   Windows 7

    -   Windows Server 2016

    -   Windows Server 2012 R2

    -   Windows Server 2008 R2

    Plus précisément, pour Windows 7 SP1, les correctifs suivants doivent être installés :

    -   Installer [KB4074598](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)

    -   Installez la [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (ou **ultérieure)** ou 
         [la KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework).
        N’installez pas les deux sur le même système.

5. Si vous utilisez un proxy pour vous connecter à Internet, consultez la section Configurer les paramètres du proxy.

Une fois terminé, vous devriez voir les points de terminaison intégrés dans le portail dans un délai d’une heure.

### <a name="next-generation-protection"></a>Protection de nouvelle génération 
L’antivirus Microsoft Defender est une solution de protection contre les programmes malveillants intégrée qui offre une protection nouvelle génération pour les ordinateurs de bureau, les ordinateurs portables et les serveurs.

1. Dans la console Microsoft Endpoint Configuration Manager, accédez à **Assets and Compliance \> Overview \> Endpoint Protection \> Antimalware Polices** et choisissez Créer une stratégie **anti-programme malveillant.**

    ![Image de la stratégie anti-programme malveillant](images/9736e0358e86bc778ce1bd4c516adb8b.png)

2. Select **Scheduled scans**, **Scan settings**, **Default actions**, **Real-time protection**, Exclusion **settings**, **Advanced**, **Threat overrides**, Cloud Protection **Service** and Security **intelligence updates** and choose **OK**.

    ![Image du volet de protection nouvelle génération1](images/1566ad81bae3d714cc9e0d47575a8cbd.png)

    Dans certains secteurs d’activité ou certains clients d’entreprise, certains peuvent avoir des besoins spécifiques sur la configuration de l’antivirus.

  
    [Analyse rapide par rapport à l’analyse complète et à l’analyse personnalisée](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/scheduled-catch-up-scans-microsoft-defender-antivirus#quick-scan-versus-full-scan-and-custom-scan)

    Pour plus d’informations, voir [Infrastructure de configuration de sécurité Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-configuration-framework/windows-security-configuration-framework)
  
    ![Image du volet de protection nouvelle génération2](images/cd7daeb392ad5a36f2d3a15d650f1e96.png)

    ![Image du volet de protection nouvelle génération3](images/36c7c2ed737f2f4b54918a4f20791d4b.png)

    ![Image du volet de protection nouvelle génération 4](images/a28afc02c1940d5220b233640364970c.png)

    ![Image du volet de protection nouvelle génération5](images/5420a8790c550f39f189830775a6d4c9.png)

    ![Image du volet de protection nouvelle génération6](images/33f08a38f2f4dd12a364f8eac95e8c6b.png)

    ![Image du volet de protection nouvelle génération7](images/41b9a023bc96364062c2041a8f5c344e.png)

    ![Image du volet de protection nouvelle génération8](images/945c9c5d66797037c3caeaa5c19f135c.png)

    ![Image du volet de protection nouvelle génération9](images/3876ca687391bfc0ce215d221c683970.png)

3. Cliquez avec le bouton droit sur la stratégie anti-programme malveillant nouvellement créée et sélectionnez **Déployer.**

    ![Image du volet de protection nouvelle génération10](images/f5508317cd8c7870627cb4726acd5f3d.png)

4. Ciblez la nouvelle stratégie anti-programme malveillant sur votre collection Windows 10, puis cliquez sur **OK.**

     ![Image du volet de protection nouvelle génération11](images/configmgr-select-collection.png)

Après avoir terminé cette tâche, vous avez configuré correctement Windows Defender Antivirus.

### <a name="attack-surface-reduction"></a>Réduction de la surface d’attaque
Le pilier de réduction de la surface d’attaque de Defender pour le point de terminaison inclut l’ensemble de fonctionnalités disponible sous Exploit Guard. Règles de réduction de la surface d’attaque (ASR), Accès contrôlé aux dossiers, Protection du réseau et Exploit Protection. 

Toutes ces fonctionnalités fournissent un mode audit et un mode bloc. En mode audit, il n’y a pas d’impact sur l’utilisateur final. Il s’agit uniquement de collecter des données de télémétrie supplémentaires et de les rendre disponibles dans le Centre de sécurité Microsoft Defender. L’objectif d’un déploiement est de déplacer pas à pas les contrôles de sécurité en mode blocage.

Pour définir des règles de récupération de l’accès en mode audit :

1. Dans la console Microsoft Endpoint Configuration Manager, accédez à **Assets and Compliance \> Overview \> Endpoint Protection \> Windows Defender Exploit Guard** et choisissez Créer une stratégie Exploit **Guard.**

   ![Image de la console Microsoft Endpoint Configuration Manager 0](images/728c10ef26042bbdbcd270b6343f1a8a.png)

2.  Sélectionnez **Réduction de la surface d’attaque.**
   

3. Définissez les règles sur **Audit** et cliquez sur **Suivant.**


    ![Image de Microsoft Endpoint Configuration Manager console1](images/d18e40c9e60aecf1f9a93065cb7567bd.png)

4. Confirmez la nouvelle stratégie Exploit Guard en cliquant sur **Suivant**.

    ![Image de Microsoft Endpoint Configuration Manager console2](images/0a6536f2c4024c08709cac8fcf800060.png)

    
5. Une fois la stratégie créée, cliquez sur **Fermer.**

    ![Image de microsoft Endpoint Configuration Manager console3](images/95d23a07c2c8bc79176788f28cef7557.png)

    ![Image de Microsoft Endpoint Manager console1](images/95d23a07c2c8bc79176788f28cef7557.png)
   

6.  Cliquez avec le bouton droit sur la stratégie nouvellement créée et choisissez **Déployer.**
    
    ![Image de la console Microsoft Endpoint Configuration Manager 4](images/8999dd697e3b495c04eb911f8b68a1ef.png)

7. Ciblez la stratégie sur la collection Windows 10 nouvellement créée et cliquez sur **OK.**

    ![Image de la console Microsoft Endpoint Configuration Manager 5](images/0ccfe3e803be4b56c668b220b51da7f7.png)

Après avoir effectué cette tâche, vous avez correctement configuré les règles de la asr en mode audit.  
  
Vous trouverez ci-dessous des étapes supplémentaires pour vérifier si les règles de réponse aux erreurs sont correctement appliquées aux points de terminaison. (Cela peut prendre quelques minutes)


1. À partir d’un navigateur web, accédez à <https://securitycenter.windows.com> .

2.  Sélectionnez **Gestion de la configuration** dans le menu gauche.

3. Cliquez **sur Aller à la gestion de la surface d’attaque** dans le panneau De gestion de la surface d’attaque. 
    
    ![Image de la gestion de la surface d’attaque](images/security-center-attack-surface-mgnt-tile.png)

4. Cliquez sur **l’onglet Configuration** dans les rapports de règles de réduction de la surface d’attaque. Il présente la vue d’ensemble de la configuration des règles de la asr et l’état des règles de la asr sur chaque appareil.

    ![Capture d’écran des règles de réduction de la surface d’attaque reports1](images/f91f406e6e0aae197a947d3b0e8b2d0d.png)

5. Cliquez sur chaque appareil pour obtenir les détails de configuration des règles asr.

    ![Capture d’écran des règles de réduction de la surface d’attaque rapports2](images/24bfb16ed561cbb468bd8ce51130ca9d.png)

Pour [plus d’informations, voir Optimiser](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-machines-asr)   le déploiement et les détections de règles asr.  


#### <a name="set-network-protection-rules-in-audit-mode"></a>Définissez des règles de protection réseau en mode audit :
1. Dans la console Microsoft Endpoint Configuration Manager, accédez à **Assets and Compliance \> Overview \> Endpoint Protection \> Windows Defender Exploit Guard** et choisissez Créer une stratégie Exploit **Guard.**

    ![Capture d’écran de System Center Configuration Manager1](images/728c10ef26042bbdbcd270b6343f1a8a.png)

2. Sélectionnez **Protection du réseau.**

3. Définissez le paramètre sur **Audit et** cliquez sur **Suivant.** 

    ![Capture d’écran de System Center Confirugatiom Manager2](images/c039b2e05dba1ade6fb4512456380c9f.png)

4. Confirmez la nouvelle stratégie Exploit Guard en cliquant sur **Suivant.**
    
    ![Capture d’écran Exploit GUard policy1](images/0a6536f2c4024c08709cac8fcf800060.png)

5. Une fois la stratégie créée, cliquez sur **Fermer.**

    ![Capture d’écran Exploit GUard policy2](images/95d23a07c2c8bc79176788f28cef7557.png)

6. Cliquez avec le bouton droit sur la stratégie nouvellement créée et choisissez **Déployer.**

    ![Capture d’écran de Microsoft Endpoint Configuration Manager1](images/8999dd697e3b495c04eb911f8b68a1ef.png)

7. Sélectionnez la stratégie pour la collection Windows 10 nouvellement créée et choisissez **OK.**

    ![Capture d’écran de Microsoft Endpoint Configuration Manager2](images/0ccfe3e803be4b56c668b220b51da7f7.png)



Après avoir effectué cette tâche, vous avez correctement configuré la Protection du réseau en mode audit.

#### <a name="to-set-controlled-folder-access-rules-in-audit-mode"></a>Pour définir des règles d’accès contrôlé aux dossiers en mode Audit :

1. Dans la console Microsoft Endpoint Configuration Manager, accédez à **Assets and Compliance \> Overview \> Endpoint Protection \> Windows Defender Exploit Guard** et choisissez Créer une stratégie Exploit **Guard.**

    ![Capture d’écran de Microsoft Endpoint Configuration Manager3](images/728c10ef26042bbdbcd270b6343f1a8a.png)

2. Sélectionnez **Accès contrôlé aux dossiers.**
    
3. Définissez la configuration sur **Audit et** cliquez sur **Suivant.**

    ![Capture d’écran de Microsoft Endpoint Configuration Manager4](images/a8b934dab2dbba289cf64fe30e0e8aa4.png)    
    
4. Confirmez la nouvelle stratégie Exploit Guard en cliquant sur **Suivant**.

    ![Capture d’écran de Microsoft Endpoint Configuration Manager5](images/0a6536f2c4024c08709cac8fcf800060.png)

5. Une fois la stratégie créée, cliquez sur **Fermer.**

    ![Capture d’écran de Microsoft Endpoint Configuration Manager6](images/95d23a07c2c8bc79176788f28cef7557.png)

6. Cliquez avec le bouton droit sur la stratégie nouvellement créée et choisissez **Déployer.**

    ![Capture d’écran de Microsoft Endpoint Configuration Manager7](images/8999dd697e3b495c04eb911f8b68a1ef.png)

7.  Ciblez la stratégie sur la collection Windows 10 nouvellement créée et cliquez sur **OK.**

    ![Capture d’écran de Microsoft Endpoint Configuration Manager8](images/0ccfe3e803be4b56c668b220b51da7f7.png)

Vous avez maintenant configuré l’accès contrôlé aux dossiers en mode audit.

## <a name="related-topic"></a>Rubrique connexe
- [Intégration à l’aide de Microsoft Endpoint Manager](onboarding-endpoint-manager.md)