---
title: Prise en main du scanner local de protection contre la perte de données Microsoft 365 (préversion)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Configurer un scanneur local de protection contre la perte de données Microsoft 365
ms.openlocfilehash: 0390ac48b351b30b75109a3e3a5d18c80847c9d2
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2021
ms.locfileid: "53289198"
---
# <a name="get-started-with-the-data-loss-prevention-on-premises-scanner-preview"></a>Prise en main du scanneur local de protection contre la perte de données (préversion)

Cet article décrit les conditions préalables et la configuration du scanneur de protection contre la perte de données Microsoft 365.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="skusubscriptions-licensing"></a>Licences SKU/abonnements

Avant de commencer à utiliser le scanneur local de DLP, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) et tous les modules complémentaires. Pour participer à la préversion du compte d’administrateur qui définit les règles DLP, une des licences suivantes doit être attribuée :

- Microsoft 365 E5
- Microsoft 365 E5 Conformité
- Microsoft 365 E5, Protection des informations et gouvernance 


Pour plus d’informations sur les licences, consultez [instructions relatives aux licences Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

### <a name="permissions"></a>Autorisations


Les données du scanneur local de protection contre la perte de données peuvent être affichées dans [l’Explorateur d’activités](data-classification-activity-explorer.md). Il existe quatre rôles qui accordent l’autorisation à l’Explorateur d’activités, le compte que vous utilisez pour accéder aux données doit être membre de l’un d’eux.

- Administrateur général
- Administrateur de conformité
- Administrateur de sécurité
- Administrateur de conformité des données

### <a name="dlp-on-premises-scanner-prerequisites"></a>Conditions préalables pour un scanneur local de protection contre la perte de données

- Le scanneur Azure Information Protection (AIP) implémente la correspondance des stratégies DLP et l’application de stratégies. Le scanneur est installé dans le cadre du client AIP. Votre installation doit donc satisfaire toutes les conditions préalables requises pour AIP, le client AIP et le scanneur d’étiquetage unifié AIP.
- Déployer le client et le scanneur AIP. Pour plus d’informations [Installez le client d'étiquetage unifié AIP](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) et consultez [Configuration et installation du scanneur d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install).
- Au moins une étiquette et une stratégie doivent être publiées dans le client, même si toutes vos règles de détection ne sont basées que sur des types d’informations sensibles.

## <a name="deploy-the-dlp-on-premises-scanner"></a>Déployer un scanneur local de protection contre la perte de données

1. Suivez les procédures dans [Installer le client d’étiquetage unifié AIP](/azure/information-protection/rms-client/install-unifiedlabelingclient-app). 
2. Pour terminer l’installation du scanneur, suivez les procédures dans[Configuration et l’installation du scanneur d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install).
    1. La configuration des tâches de découverte réseau est une étape facultative. Vous pouvez l’ignorer et définir des référentiels spécifiques à numériser dans votre travail d’analyse de contenu.
    2. Vous devez créer un travail d’analyse de contenu et spécifier les référentiels qui hébergent les fichiers qui doivent être évalués par le moteur DLP.
    3. Activez les règles DLP dans la tâche d’analyse de contenu créée et définissez l’option **Appliquer** sur **Désactivé**, sauf si vous voulez passer directement à la phase d’application de la DLP.
3. Vérifiez que la tâche d’analyse de contenu est affectée au bon cluster. Si vous n'avez toujours pas créé de tâche d'analyse de contenu, créez-en une nouvelle et affectez-la au cluster qui contient les nœuds d'analyse qui exécutent la version d'aperçu public.

4. Connectez-vous à [Extension Azure Information Protection dans le Portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade) et ajoutez vos référentiels à la tâche d’analyse de contenu qui effectuera l’analyse.

5. Pour exécuter votre analyse, exécutez l’une des analyses suivantes :
    1. définir le planning du scanneur
    1. utiliser l’option manuel **Analyser maintenant** dans le portail
    1. ou exécuter l’applet de commande PowerShell **Start-AIPScan**

   > [!IMPORTANT]
   > N'oubliez pas que le scanneur effectue par défaut une analyse delta du référentiel et que les fichiers qui ont déjà été analysés lors du cycle d'analyse précédent seront ignorés, sauf si le fichier a été modifié ou si vous avez lancé une nouvelle analyse complète. La nouvelle analyse complète peut être lancée en utilisant l'option **Relancer l’analyse de tous les fichiers** dans l'interface utilisateur ou en exécutant **Start-AIPScan-Reset**.

6.  Ouvrez la page de [Protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies) dans le Centre de conformité Microsoft 365.

7. Choisissez **Créer une stratégie** et créez une stratégie DLP de test. Consultez [Créer une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md) si vous avez besoin d’aide pour créer une stratégie. N’oubliez pas de l’exécuter à l’essai jusqu’à ce que vous soyez à l’aise avec cette fonctionnalité. Utilisez les paramètres suivants pour votre stratégie :
    1. Limitez la règle du scanneur local de protection contre la perte de données à des emplacements spécifiques si nécessaire. Si vous définissez les **emplacements** comme **Tous**, tous les fichiers analysés par le scanneur seront soumis à la règle de correspondance et d'application du DLP.
    1. Lorsque vous spécifiez les emplacements, vous pouvez utiliser une liste d’exclusion ou d’inclusion. Pendant la préversion publique, vous ne pouvez pas définir les deux. Vous pouvez soit définir que la règle ne s'applique qu'aux chemins d'accès correspondant à l'un des modèles figurant dans la liste d'inclusion, soit à tous les fichiers, à l'exception des fichiers correspondant au modèle figurant dans la liste d'inclusion. Aucun chemin d’accès local n’est pris en charge. Voici quelques exemples de chemins d’accès valides :
      - \\\server\share
      - \\\server\share\folder1\subfolderabc
      - \*\\dossier1
      - \*secret\*.docx
      - \*secret\*.\*
      - https:// sp2010.local/sites/HR
      - https://\*/HR 
    3. Voici quelques exemples d'utilisation de valeurs inacceptables :
      - \*
      - \*\\a
      - Aaa
      - c:\
      - C:\test

> [!IMPORTANT]
> La liste d'exclusion a la priorité sur la liste d'inclusion.

### <a name="viewing-dlp-on-premises-scanner-alerts-in-dlp-alerts-management-dashboard"></a>Affichage des alertes du scanneur local de protection contre la perte de données dans le tableau de bord de Gestion des alertes DLP

1. Ouvrez la page de [Protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies) dans le Centre de conformité Microsoft 365, puis sélectionnez **Alertes**.

2. Reportez-vous aux procédures décrites dans [Comment configurer et afficher les alertes pour les stratégies DLP](dlp-configure-view-alerts-policies.md) pour afficher les alertes relatives à vos stratégies DLP de point de terminaison.

### <a name="viewing-dlp-on-premises-scanner-in-activity-explorer-and-audit-log"></a>Affichage du scanneur local de protection contre la perte de données dans l’Explorateur d’activités et le journal d’audit

> [!NOTE]
> Le scanneur local nécessite que l’audit soit activé. L’audit Microsoft 365 est activé par défaut.

1. Ouvrez la [Page classification des données](https://compliance.microsoft.com/dataclassification?viewid=overview) pour votre domaine dans le centre de conformité Microsoft 365, puis sélectionnez Explorateur d’activités.

2. Reportez-vous aux procédures décrites dans [Prise en main de l’Explorateur d’activités](data-classification-activity-explorer.md) pour accéder aux données de vos emplacements de scanneur local.

3. Ouvrir le [Journal d'audit dans le Centre de conformité](https://security.microsoft.com/auditlogsearch). Pendant la préversion publique, les correspondances de règle DLP sont disponibles dans l’interface utilisateur du journal d’audit ou accessibles par [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell 


## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous avez déployé une stratégie de test pour les emplacements locaux de protection contre la perte de données et que vous pouvez afficher les données d’activité dans l’Explorateur d’activités, vous êtes prêt à passer à l’étape suivante dans laquelle vous créez des stratégies DLP qui protègent vos éléments sensibles.

- [Utilisation de DLP en local (préversion)](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur le scanneur local de protection contre la perte de données (préversion)](dlp-on-premises-scanner-learn.md)
- [Utiliser le scanneur local de protection contre la perte de données (préversion)](dlp-on-premises-scanner-use.md)
- [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)