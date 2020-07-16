---
title: Bénéficiez d’une visibilité sur votre position de sécurité via le score de sécurité Microsoft
description: Décrit comment prendre des mesures pour améliorer votre score de sécurité Microsoft dans le centre de sécurité Microsoft 365.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, Secure score, centre de sécurité, actions d’amélioration
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 0ae1a196f11f383c1d3f9fd2056d5d19e7cdd6da
ms.sourcegitcommit: 09a500a44d8723f8f2be87d9ad4ce7e453c5192b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "45095041"
---
# <a name="gain-visibility-into-your-security-posture-through-microsoft-secure-score"></a>Bénéficiez d’une visibilité sur votre position de sécurité via le score de sécurité Microsoft

Microsoft Secure score est une mesure de la position de sécurité d’une organisation, avec un nombre supérieur indiquant d’autres actions d’amélioration. Vous pouvez https://security.microsoft.com/securescore le trouver dans le [Centre de sécurité Microsoft 365](overview-security-center.md).

Pour vous aider à trouver plus rapidement les informations dont vous avez besoin, les actions d’amélioration de Microsoft sont organisées en groupes :

* Identity (comptes Azure AD & rôles)
* Data (protection des informations Microsoft)
* Appareil (Microsoft Defender ATP, appelé score de [configuration](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configuration-score))
* Application (applications de messagerie et de Cloud, y compris Office 365 et Microsoft Cloud App Security)
* Infrastructure (aucune action d’amélioration pour l’instant)

>[!NOTE]
>Dans la version récente de Microsoft Secure score, un modèle de notation amélioré a été publié, ce qui rendait le score de sécurité Microsoft temporairement incompatible avec le score de sécurité d’identité et l’API Graph. [Afficher les détails](microsoft-secure-score.md#incompatibility-with-identity-secure-score-and-graph-api)

Dans la page de présentation de Microsoft Secure score, vous pouvez voir la répartition des points entre ces groupes et les points disponibles. La page de vue d’ensemble est également l’endroit où vous pouvez obtenir une vue d’ensemble du score total, de la tendance historique de votre score de sécurité avec comparaisons de référence et des actions d’amélioration hiérarchisée qui peuvent être prises pour améliorer votre score.

![Page d’accueil du score sécurisé](../../media/secure-score/secure-score-homepage-new.png)

## <a name="check-your-current-score"></a>Vérifier votre score actuel

Pour vérifier votre score actuel, accédez à la page de présentation de Microsoft Secure score et recherchez la vignette indiquant **votre score de sécurité**. Votre score est affiché sous forme de pourcentage, ainsi que le nombre de points que vous avez obtenus sur un total de points possibles.

En outre, si vous sélectionnez le bouton **inclure** en regard de votre score, vous pouvez choisir différentes vues de votre score. Ces différentes vues de score s’affichent dans le graphique sur la vignette de score et le graphique de répartition par points.

Voici les scores que vous pouvez ajouter à votre vue de votre score global afin de vous donner une image plus complète de votre score global :

- **Score planifié**: afficher le score projeté lorsque les actions planifiées sont terminées
- **Score de licence actuel**: affiche le score qui peut être obtenu avec votre licence Microsoft actuelle
- **Score**possible : afficher le score qui peut être obtenu avec vos licences Microsoft et acceptation actuelle des risques

C’est ce qu’il ressemblera si vous avez inclus tous les affichages de score possibles :

![Votre score de sécurité, y compris le score planifié, le score de licence actuel et le score réalisable](../../media/secure-score/your-secure-score.png)

## <a name="take-action-to-improve-your-score"></a>Prendre des mesures pour améliorer votre score

L’onglet **actions d’amélioration** répertorie les recommandations de sécurité qui concernent les surfaces d’attaque possibles, ainsi que leur état (à des adresses, planifiées, des risques acceptés, résolus par des tiers, résolus par une atténuation de substitution et terminées). Vous pouvez rechercher, filtrer et regrouper toutes les actions d’amélioration.  

### <a name="ranking"></a>Placé

Le classement repose sur le nombre de points restants à atteindre, les difficultés d’implémentation, l’impact de l’utilisateur et la complexité. Les actions d’amélioration les plus élevées ont un grand nombre de points restants, avec une faible Difficulté, un impact sur l’utilisateur et une complexité.

### <a name="view-improvement-action-details"></a>Afficher les détails de l’action d’amélioration

Lorsque vous sélectionnez une action d’amélioration spécifique, un menu volant de page entière s’affiche.  

![Exemple de menu contextuel d’action d’amélioration ](../../media/secure-score/secure-score-improvement-action-details.png)
 *figure 2 : exemple de menu contextuel d’action d’amélioration*

Pour terminer l’action, vous disposez de plusieurs options :

* Sélectionnez **gérer** pour accéder à l’écran de configuration et effectuer la modification. Vous obtiendrez ensuite les points que l’action vaut, visible dans le survol. Les points prennent généralement environ 24 heures à mettre à jour.

* Sélectionnez **partager** pour copier le lien direct vers l’action d’amélioration ou choisissez la plateforme pour partager le lien, comme courrier électronique, Microsoft Teams, planificateur Microsoft ou ServiceNow. La sélection de ServiceNow vous permettra de créer un ticket de modification qui sera visible dans ServiceNow et le centre de sécurité Microsoft 365. Pour en savoir plus, consultez la rubrique [Microsoft 365 Security Center and ServiceNow Integration](tickets-security-center.md).

### <a name="choose-an-improvement-action-status"></a>Choisir un état d’action d’amélioration

Choisissez les États et les notes d’enregistrement spécifiques à l’action d’amélioration. Les statues que vous pouvez sélectionner sont les suivants :

* **À résoudre** : vous reconnaissez que l’action d’amélioration est nécessaire et que vous envisagez d’y remédier à un moment donné. Cet État s’applique également aux actions détectées comme partielles, mais pas complètement terminées.
* **Planifié** : des plans concrets sont en place pour effectuer l’action d’amélioration.
* **Risque accepté** : la sécurité doit toujours être équilibrée avec la convivialité et toutes les recommandations ne fonctionnent pas pour votre environnement. Lorsque c’est le cas, vous pouvez choisir d’accepter le risque ou le risque restant et de ne pas appliquer l’action d’amélioration. Vous n’aurez pas de points, mais l’action ne sera plus visible dans la liste des actions d’amélioration. Vous pouvez afficher cette action dans l’historique ou l’annuler à tout moment.
* **Résolu via** un tiers et **résolu par une autre atténuation** : l’action d’amélioration a déjà été traitée par une application ou un logiciel tiers, ou par un outil interne. Vous obtiendrez les points que l’action vaut, afin que votre score reflète mieux votre position de sécurité globale. Si un outil tiers ou interne ne couvre plus le contrôle, vous pouvez choisir un autre État. N’oubliez pas que Microsoft n’aura aucune visibilité sur l’intégralité de la mise en œuvre si l’action d’amélioration est marquée comme l’un de ces statuts.

#### <a name="threat--vulnerability-management-improvement-actions"></a>Actions d’amélioration de la gestion des vulnérabilités & des menaces

Pour les actions d’amélioration dans la catégorie « périphérique », vous ne pouvez pas choisir les statuts. Au lieu de cela, vous serez redirigé vers la [& menace de gestion des vulnérabilités (TVM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation) dans le [Centre de sécurité Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/use) afin de prendre des mesures. L’exception que vous choisissez et la justification que vous écrivez seront spécifiques à ce portail et ne seront pas présentes dans le portail de score de sécurité Microsoft.

#### <a name="completed-improvement-actions"></a>Actions d’amélioration terminées

Les actions d’amélioration ont un état « terminé » une fois que tous les points possibles pour l’action d’amélioration ont été atteints. Les actions d’amélioration terminées sont confirmées via les données Microsoft et vous ne pouvez pas modifier l’État.

### <a name="assess-information-and-review-user-impact"></a>Évaluation des informations et examen de l’impact des utilisateurs

La section **d’un coup d’œil** vous indiquera la catégorie, les attaques contre lesquelles elle peut protéger et le produit.

L' **impact** de l’utilisateur indique ce que les utilisateurs peuvent faire si l’action d’amélioration est effectuée et que les **utilisateurs concernés** affichent les personnes qui l’exécuteront.

### <a name="implement-the-improvement-action"></a>Implémenter l’action d’amélioration

La section **implémentation** présente les conditions préalables, étape par étape pour effectuer l’action d’amélioration, l’état actuel de l’implémentation de l’action d’amélioration, ainsi que d’autres liens en savoir plus.

Les conditions préalables seront les licences à obtenir ou les actions qui doivent être effectuées avant l’exécution de l’action d’amélioration. Assurez-vous que votre licence comporte suffisamment de sièges pour effectuer l’action d’amélioration et que ces licences sont appliquées aux utilisateurs nécessaires.  

## <a name="we-want-to-hear-from-you"></a>Nous souhaitons être informés

Si vous rencontrez des problèmes, indiquez-nous en publiant dans la communauté [Security, Privacy & Compliance](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Nous Surveillez la communauté et vous fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Présentation de Microsoft Secure score](microsoft-secure-score.md)
- [Suivi de votre historique de score sécurisé Microsoft et atteindre les objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Nouveautés](microsoft-secure-score-whats-coming.md)