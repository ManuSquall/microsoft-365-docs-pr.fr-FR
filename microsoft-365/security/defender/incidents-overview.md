---
title: Incidents dans Microsoft 365 Defender
description: Examinez les incidents rencontrés sur les appareils, les utilisateurs et les boîtes aux lettres dans Microsoft 365 Defender portail.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365, réponse aux incidents, cyber-attaque
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: b6830c77a0c5cc93ea202844a8793c5f69f07650
ms.sourcegitcommit: d904f04958a13a514ce10219ed822b9e4f74ca2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "53028522"
---
# <a name="incidents-in-microsoft-365-defender"></a>Incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> Vous voulez essayer Microsoft 365 Defender ? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).
>

Un incident dans Microsoft 365 Defender est une collection d’alertes corrélées et de données associées qui constitue l’histoire d’une attaque. 

Microsoft 365 et applications créent des alertes lorsqu’ils détectent un événement ou une activité suspect ou malveillant. Les alertes individuelles fournissent des indices précieux sur une attaque terminée ou en cours. Toutefois, les attaques utilisent généralement différentes techniques pour différents types d’entités, telles que les appareils, les utilisateurs et les boîtes aux lettres. Le résultat est plusieurs alertes pour plusieurs entités dans votre client. 

Étant donné que l’agrégation des alertes individuelles pour obtenir des informations sur une attaque peut être complexe et chronophage, Microsoft 365 Defender regroupe automatiquement les alertes et leurs informations associées dans un incident.

:::image type="content" source="../../media/incidents-overview/incidents.png" alt-text="Comment Microsoft 365 Defender des événements d’entités dans un incident":::

Regardez cette courte vue d’ensemble des incidents Microsoft 365 Defender (4 minutes).

<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Le regroupement d’alertes associées dans un incident vous offre une vue complète d’une attaque. Par exemple, vous pouvez voir :

- Point de départ de l’attaque.
- Quelles tactiques ont été utilisées .
- Jusqu’où l’attaque est passée dans votre client.
- Étendue de l’attaque, telle que le nombre d’appareils, d’utilisateurs et de boîtes aux lettres qui ont été touchés. 
- Toutes les données associées à l’attaque.

Si [elle est activée,](m365d-enable.md)Microsoft 365 Defender [peuvent automatiquement](m365d-autoir.md) examiner et résoudre les alertes par le biais de l’automatisation et de l’intelligence artificielle. Vous pouvez également effectuer des étapes de correction supplémentaires pour résoudre l’attaque. 

## <a name="incidents-and-alerts-in-the-microsoft-365-defender-portal"></a>Incidents et alertes dans le portail Microsoft 365 Defender web

Vous gérez les incidents à partir **d’incidents & alertes** > incidents sur le lancement rapide du portail Microsoft 365 Defender ([security.microsoft.com](https://security.microsoft.com)). Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Page Incidents dans le portail Microsoft 365 Defender web":::

La sélection d’un nom d’incident affiche un résumé de l’incident et donne accès aux onglets avec des informations supplémentaires.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Exemple de page Résumé d’un incident dans le portail Microsoft 365 Defender web":::

Les onglets supplémentaires pour un incident sont les suivants :

- Alertes 

  Toutes les alertes liées à l’incident et leurs informations.

- Appareils

  Tous les appareils identifiés comme faisant partie ou liés à l’incident.

- Utilisateurs

  Tous les utilisateurs identifiés comme faisant partie ou associés à l’incident.

- Boîtes aux lettres

  Toutes les boîtes aux lettres identifiées comme faisant partie ou liées à l’incident.

- Examens

  Toutes les [enquêtes automatisées](m365d-autoir.md) déclenchées par des alertes dans l’incident.

- Preuve et réponse

  Tous les événements pris en charge et entités suspectes dans les alertes dans l’incident.

- Graph (en prévisualisation)

  Figure montrant la connexion des alertes aux biens touchés dans votre organisation.

Voici la relation entre un incident et ses données et les onglets d’un incident dans le Microsoft 365 Defender web.

:::image type="content" source="../../media/incidents-overview/incidents-security-center.png" alt-text="Relation d’un incident et de ses données avec les onglets d’un incident dans le portail Microsoft 365 Defender web":::

## <a name="example-incident-response-workflow-for-microsoft-365-defender"></a>Exemple de flux de travail de réponse aux incidents pour Microsoft 365 Defender

Voici un exemple de flux de travail pour répondre aux incidents dans Microsoft 365 avec le portail Microsoft 365 Defender web.

:::image type="content" source="../../media/incidents-overview/incidents-example-workflow.png" alt-text="Exemple de flux de travail de réponse aux incidents pour Microsoft 365":::

Identifiez régulièrement les incidents les plus prioritaires pour l’analyse et la résolution dans la file d’attente des incidents et préparez-les à répondre. Il s’agit d’une combinaison de :

- [Tri pour](incident-queue.md) déterminer les incidents les plus prioritaires via le filtrage et le tri de la file d’attente d’incidents.
- [Gestion](manage-incidents.md) des incidents en modifiant leur titre, en les attribuant à un analyste et en ajoutant des balises et des commentaires.

1. Pour chaque incident, lancez une analyse et une analyse d’attaque et [d’alerte](investigate-incidents.md):
 
   1. Affichez le résumé de l’incident pour comprendre sa portée et sa gravité, ainsi que les entités concernées (onglet **Résumé).**

   1. Commencez à analyser les alertes pour comprendre leur origine, leur étendue et leur gravité (onglet **Alertes).**

   1. Si nécessaire, rassemblez des informations sur les appareils, les utilisateurs et les boîtes aux lettres touchés (onglets **Appareils,** Utilisateurs et Boîtes **aux lettres).**

   1. Découvrez comment Microsoft 365 Defender [a automatiquement résolu certaines alertes](m365d-autoir.md) (onglet **Enquêtes).**
   
   1. Si nécessaire, utilisez les informations du jeu de données pour l’incident pour plus d’informations (onglet Preuve **et** réponse).

2. Après ou pendant votre analyse, effectuez un contenu pour réduire tout impact supplémentaire de l’attaque et de l’éradication de la menace de sécurité.

3. Dans la mesure du possible, récupérez à partir de l’attaque en restaurant les ressources de votre client à l’état où elles se sont trouver avant l’incident.

4. [Résolvez](manage-incidents.md#resolve-an-incident) l’incident et prenez le temps d’apprendre après l’incident pour :

   - Comprendre le type de l’attaque et son impact.
   - Recherchez une tendance des attaques de sécurité dans [l’analyse](threat-analytics.md) des menaces et la communauté de sécurité.
   - Rappelez-vous du flux de travail que vous avez utilisé pour résoudre l’incident et mettre à jour vos flux de travail, processus, stratégies et playbooks standard si nécessaire.
   - Déterminez si des modifications sont nécessaires dans votre configuration de sécurité et implémentez-les.

Si vous débutez dans l’analyse de la sécurité, consultez [l’introduction](incidents-overview.md) à la réponse à votre premier incident pour plus d’informations et pour passer au travers d’un exemple d’incident.

Pour plus d’informations sur la réponse aux incidents dans les produits Microsoft, consultez [cet article.](/security/compass/incident-response-overview)

## <a name="example-security-operations-for-microsoft-365-defender"></a>Exemples d’opérations de sécurité pour Microsoft 365 Defender

Voici un exemple d’opérations de sécurité (SecOps) pour Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-operations.png" alt-text="Exemple d’opérations de sécurité pour Microsoft 365 Defender":::

Les tâches quotidiennes peuvent inclure les tâches suivantes :

- [Gestion des](manage-incidents.md) incidents
- Examen des actions [d’investigation et de réponse automatisées (AIR)](m365d-action-center.md) dans le centre de gestion des actions
- Examen de la dernière [analyse des menaces](threat-analytics.md)
- [Réponse aux](investigate-incidents.md) incidents

Les tâches mensuelles peuvent inclure les tâches suivantes :

- Examen des [paramètres AIR](m365d-configure-auto-investigation-response.md)
- Examen de [la gestion des niveaux de sécurité](microsoft-secure-score-improvement-actions.md) et & des [vulnérabilités](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Rapports à votre chaîne de gestion de la sécurité informatique

Les tâches trimestrielles peuvent inclure un rapport et un briefing des résultats de sécurité au directeur de la sécurité des informations (CISO).

Les tâches annuelles peuvent inclure la conduite d’un incident majeur ou d’un exercice de violation pour tester votre personnel, vos systèmes et vos processus. 

Les tâches quotidiennes, mensuelles, trimestrielles et annuelles peuvent être utilisées pour mettre à jour ou affiner des processus, des stratégies et des configurations de sécurité.

### <a name="secops-resources-across-microsoft-products"></a>Ressources SecOps sur les produits Microsoft

Pour plus d’informations sur SecOps dans les produits Microsoft, consultez les ressources ci-après :

- [Capabilities](/security/compass/security-operations-capabilities)
- [Meilleures pratiques](/security/compass/security-operations)
- [Vidéos et diapositives](/security/compass/security-operations-videos-and-decks)

## <a name="next-steps"></a>Étapes suivantes

**Si vous êtes nouveau dans l’analyse** de la sécurité et la réponse aux incidents :

- Consultez la procédure pas à pas Répondre à votre premier [incident](first-incident-overview.md) pour obtenir une visite guidée d’un processus classique d’analyse, de correction et de révision post-incident dans le portail Microsoft 365 Defender avec un exemple d’attaque.

**Si vous avez de l’expérience en** matière d’analyse de sécurité et de réponse aux incidents :

- Commencer avec la file d’attente des incidents à partir de la page **Incidents** du portail Microsoft 365 Defender web. Ici, vous pouvez :

  - Voir quels incidents doivent [être](incident-queue.md) hiérarchisés en fonction de la gravité et d’autres facteurs. 

  - [Gérer les incidents,](manage-incidents.md)ce qui inclut le changement de nom, l’affectation, la classification et l’ajout de balises et de commentaires en fonction de votre flux de travail de gestion des incidents.

  - Effectuer [des examens](investigate-incidents.md) des incidents.

- Consultez ces manuels de réponse aux incidents pour obtenir des [instructions détaillées](/security/compass/incident-response-playbooks) sur le hameçonnage, la pulvérisation de mots de passe et les attaques d’octroi de consentement d’application.

