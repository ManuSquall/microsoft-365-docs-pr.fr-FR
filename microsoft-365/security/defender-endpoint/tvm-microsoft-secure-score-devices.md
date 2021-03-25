---
title: Score de sécurité Microsoft pour les appareils
description: Votre score pour les appareils indique l’état de configuration de sécurité collective de vos appareils dans les contrôles d’application, de système d’exploitation, de réseau, de comptes et de sécurité.
keywords: Degré de sécurisation Microsoft pour les appareils, degré de sécurisation Microsoft mdatp pour les appareils, degré de sécurité, score de configuration, gestion des menaces et vulnérabilités, contrôles de sécurité, opportunités d’amélioration, score de configuration de la sécurité au fil du temps, posture de sécurité, ligne de base
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: ellevin
author: levinec
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: d9ccd4f7dcc8b1546772a756aaf850dadfc87905
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51063750"
---
# <a name="microsoft-secure-score-for-devices"></a>Score de sécurité Microsoft pour les appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 


>[!NOTE]
> Le score de configuration fait désormais partie de la gestion des menaces et des vulnérabilités en tant que Degré de sécurisation Microsoft pour les appareils.

Votre score pour les appareils est visible dans le [tableau](tvm-dashboard-insights.md) de bord de gestion des menaces et des vulnérabilités du Centre de sécurité Microsoft Defender. Un niveau de sécurité Microsoft plus élevé pour les appareils signifie que vos points de terminaison sont plus résistants aux attaques contre les menaces de cybersécurité. Elle reflète l’état de configuration de sécurité collective de vos appareils dans les catégories suivantes :

- Application
- Système d’exploitation
- Réseau
- Comptes
- Contrôles de sécurité

Sélectionnez une catégorie pour aller à la page [**Recommandations de sécurité**](tvm-security-recommendation.md) et afficher les recommandations pertinentes.

## <a name="turn-on-the-microsoft-secure-score-connector"></a>Activer le connecteur Score de sécurité Microsoft

Avancez les signaux de Microsoft Defender pour les points de terminaison, ce qui permet à Microsoft Secure Score de se rendre compte de la posture de sécurité de l’appareil. Les données forwardées sont stockées et traitées au même emplacement que vos données du Score de sécurisation Microsoft.

La réflexion des modifications dans le tableau de bord peut prendre jusqu’à quelques heures.

1. Dans le volet de navigation, go to **Settings**  >  **Advanced features** 

2. Faites défiler vers **le bas jusqu’au score de sécurité Microsoft** et basculez le paramètre sur **Sur**.

3. Sélectionnez **Enregistrer les préférences.**

## <a name="how-it-works"></a>Mode de fonctionnement

>[!NOTE]
> Le score de sécurité Microsoft pour les appareils prend actuellement en charge les configurations définies via la stratégie de groupe. En raison de la prise en charge partielle actuelle d’Intune, les configurations qui ont peut-être été définies via Intune peuvent s’afficher comme mal configurées. Contactez votre administrateur informatique pour vérifier l’état réel de la configuration au cas où votre organisation utiliserait Intune pour la gestion de la configuration sécurisée.

Les données de la carte Degré de sécurisation Microsoft pour les appareils sont le produit d’un processus de découverte de vulnérabilité en cours et d’activités. Elle est agrégée aux évaluations de découverte de configuration qui :

- Comparer les configurations collectées aux critères collectés pour découvrir les ressources mal configurées
- Masqué les configurations sur des vulnérabilités qui peuvent être corrigés ou partiellement corrigés (réduction des risques)
- Collecter et gérer les critères de configuration des meilleures pratiques (fournisseurs, flux de sécurité, équipes de recherche internes)
- Collecter et surveiller les modifications de l’état de configuration du contrôle de sécurité de toutes les ressources

## <a name="improve-your-security-configuration"></a>Améliorer votre configuration de la sécurité

Améliorez votre configuration de la sécurité en remédiant aux problèmes de la liste des recommandations de sécurité. À mesure que vous le faites, votre score de sécurité Microsoft pour les appareils s’améliore et votre organisation devient plus résiliente contre les menaces et les vulnérabilités de cybersécurité.

1. À partir de la carte Degré de sécurisation Microsoft pour les appareils dans le tableau de bord de gestion des menaces et des vulnérabilités, sélectionnez l’une des catégories. Vous verrez la liste des recommandations relatives à cette catégorie. Il vous permet d’aller à la page [**Recommandations en matière de sécurité.**](tvm-security-recommendation.md) Si vous souhaitez voir toutes les recommandations de sécurité, une fois que vous êtes sur la page Recommandations de sécurité, effacer le champ de recherche.

2. Sélectionnez un élément dans la liste. Le panneau volant s’ouvre avec les détails relatifs à la recommandation. Sélectionnez **les options de correction.**

   ![Recommandations en matière de sécurité liées aux contrôles de sécurité](images/tvm_security_controls.png)

3. Lisez la description pour comprendre le contexte du problème et ce qu’il faut faire ensuite. Sélectionnez une date d’échéance, ajoutez des notes et sélectionnez Exporter toutes les données d’activité de correction vers **CSV** afin de pouvoir les joindre à un e-mail pour le suivi.

4. **Envoyer une demande**. Vous verrez un message de confirmation vous confirmant que la tâche de correction a été créée.
   ![Confirmation de la création d’une tâche de correction](images/tvm_remediation_task_created.png)

5. Enregistrez votre fichier CSV.
   ![Enregistrer un fichier csv](images/tvm_save_csv_file.png)

6. Envoyez un courrier électronique de suivi à votre administrateur informatique et laissez le temps que vous avez alloué à la correction de se propager dans le système.

7. Examinez **à nouveau la carte Score de sécurité Microsoft** pour les appareils dans le tableau de bord. Le nombre de recommandations en matière de contrôles de sécurité va diminuer. Lorsque vous **sélectionnez les contrôles** de sécurité pour revenir à la page **Recommandations** de sécurité, l’élément que vous avez traité n’y figure plus. Votre score de sécurité Microsoft pour les appareils doit augmenter.

>[!IMPORTANT]
>Pour augmenter les taux de détection de l’évaluation des vulnérabilités, téléchargez les mises à jour de sécurité obligatoires suivantes et déployez-les sur votre réseau :
>- Clients 19H1 | [KB 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)
>- Clients RS5 | [KB 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)
>- Clients RS4 | [KB 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)
>- Clients RS3 | [KB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)
>
>Pour télécharger les mises à jour de sécurité :
>1. Go to [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/home.aspx).
>2. Key-in the security update KB number that you need to download, then click **Search**.  

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de la gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
- [Tableau de bord](tvm-dashboard-insights.md)
- [Score d’exposition](tvm-exposure-score.md)
- [Recommandations de sécurité](tvm-security-recommendation.md)