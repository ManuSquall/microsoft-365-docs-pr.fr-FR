---
title: Recherche et réponse automatiques dans Office 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: Obtenez une vue d’ensemble des fonctionnalités d’analyse et de réponse automatisées dans Office 365 Advanced Threat Protection Plan 2.
ms.custom: air
ms.openlocfilehash: 420143a6a2888900cdc128b22f7b0bcb05adad27
ms.sourcegitcommit: 2859c82b30ae9cbd3a3e4bcdebd65f18444f1a9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "42826402"
---
# <a name="automated-investigation-and-response-air-in-office-365"></a>Recherche et réponse automatiques dans Office 365

À mesure que des alertes de sécurité sont déclenchées, c’est à votre équipe chargée des opérations de sécurité d’examiner ces alertes et de prendre des mesures pour protéger votre organisation. Parfois, les équipes d’opérations de sécurité peuvent être submergées par le volume des alertes déclenchées. Les fonctionnalités d’analyse et de réponse automatiques dans Office 365 peuvent vous aider. AIR permet à votre équipe des opérations de sécurité de fonctionner de manière plus efficace. Les fonctionnalités AIR incluent des processus d’enquête automatisés en réponse à des menaces connues qui existent aujourd’hui. Les actions de correction appropriées attendent l’approbation, ce qui permet à votre équipe des opérations de sécurité de répondre aux menaces détectées. 

Cet article fournit une vue d’ensemble de l’AIR. Lorsque vous êtes prêt à commencer à utiliser AIR, consultez la rubrique [enquêter et répondre aux menaces dans Office 365](office-365-air.md).

## <a name="at-a-high-level"></a>À un niveau élevé

Comme les alertes sont déclenchées, les règles de sécurité entrent en vigueur. En fonction de la situation, un [processus d’enquête automatisé](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air) peut commencer. Pendant et après une enquête automatisée, les [actions correctives](air-remediation-actions.md) sont recommandées. Aucune action n’est effectuée automatiquement dans Office 365 protection avancée contre les menaces. Votre équipe de gestion des opérations de sécurité examine, puis [approuve ou rejette chaque action de correction](air-review-approve-pending-completed-actions.md), et lorsque cela est fait, chaque enquête se termine. Toutes ces activités sont suivies et affichables dans le centre de conformité Office 365 Security & (voir [afficher les détails d’une enquête](air-view-investigation-results.md#view-details-of-an-investigation)).

Les sections suivantes fournissent plus d’informations sur les alertes, les règles de sécurité et des exemples d’AIR en action.

## <a name="alerts"></a>Alertes

Les [alertes](../../compliance/alert-policies.md#viewing-alerts) représentent des déclencheurs pour les flux de travail d’équipe des opérations de sécurité pour la réponse aux incidents. La définition de la priorité des alertes à droite pour l’enquête, tout en s’assurant qu’aucune menace n’est sans adresse est complexe. Lorsque les enquêtes dans les alertes sont effectuées manuellement, les équipes des opérations de sécurité doivent rechercher et corréler les entités (telles que le contenu, les appareils et les utilisateurs) menacées. Ces tâches et les flux de travail peuvent être très longs et impliquer plusieurs outils et systèmes. Avec AIR, Investigation and Response for Office 365 Security Events is Automated by having Security and Threat Management Alerts déclenchent automatiquement des règles de réponse de sécurité. 

Pour l’AIR, les alertes générées à partir des types de stratégies d’alerte suivants sont analysées automatiquement :  

- Un clic d’URL potentiellement malveillant a été détecté
- Courrier électronique signalé par l’utilisateur comme hameçonnage *
- Messages électroniques contenant des programmes malveillants supprimés après la remise *
- Messages électroniques contenant des URL d’hameçonnage supprimées après la remise *
- Modèles d’envoi de courrier électronique suspects détectés #
- Utilisateur non autorisé à envoyer un message électronique #

> [!NOTE]
> Les alertes signalées par un astérisque (*) sont affectées d’une gravité *informatif* dans les stratégies d’alerte respectives dans le centre de sécurité & conformité, les notifications par courrier étant désactivées. Les notifications par courrier électronique peuvent être activées par le biais de la [Configuration des stratégies d’alerte](../../compliance/alert-policies.md#alert-policy-settings). Les alertes marquées avec un hachage (#) sont généralement des alertes disponibles associées aux règles de préversion publique.

Pour afficher les alertes, dans le centre de sécurité & conformité, sélectionnez **alertes** > **afficher les alertes**. Sélectionnez une alerte pour afficher ses détails, puis, à partir de là, utilisez le lien **consulter l’enquête** pour accéder à l' [enquête](air-view-investigation-results.md#investigation-graph)correspondante.  

> [!NOTE]
> Les alertes d’information sont masquées par défaut dans l’affichage des alertes. Pour les afficher, modifiez le filtrage des alertes de manière à inclure des alertes d’information.

Si votre organisation gère vos alertes de sécurité par le biais d’un système de gestion des alertes, d’un système de gestion des services ou d’un système de gestion des événements et des informations de sécurité (SIEM), vous pouvez envoyer des alertes Office 365 à ce système via une notification par courrier électronique ou via l' [API d’activité de gestion d’office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference). Les notifications d’alerte d’enquête via le courrier électronique ou l’API incluent des liens permettant d’accéder aux alertes dans le centre de sécurité & conformité, ce qui permet à l’administrateur de sécurité affecté de naviguer rapidement dans l’enquête.

![Alertes liées à des enquêtes](../../media/air-alerts-page-details.png) 

## <a name="security-playbooks"></a>Règles de sécurité

Les règles de sécurité sont des stratégies principales qui sont au cœur de l’automatisation dans Office Advanced Threat Protection et Microsoft Threat Protection. Les règles de sécurité fournies dans AIR sont basées sur des scénarios de sécurité réels courants et sont développés en fonction des commentaires des équipes d’opérations de sécurité. Un manuel de sécurité est lancé automatiquement lorsque des alertes spécifiques sont déclenchées au sein de votre organisation. Une fois que l’alerte est déclenchée, le manuel associé est exécuté par le système automatisé d’enquête et de réponse (AIR). L’enquête passe par l’analyse de l’alerte en fonction du manuel de cette alerte en examinant toutes les métadonnées associées (notamment les messages électroniques, les utilisateurs, les objets, les expéditeurs, etc.). En fonction des conclusions du manuel d’enquête, AIR recommande un ensemble d’actions que l’équipe de sécurité de votre organisation peut prendre pour contrôler et atténuer la menace. 

Les règles de sécurité que vous obtenez avec AIR sont conçues pour aborder les menaces les plus fréquentes auxquelles les entreprises rencontrent actuellement des courriers électroniques. Elles sont basées sur les opérations de sécurité et les équipes de réponse aux incidents, notamment celles qui permettent de défendre Microsoft et les ressources de nos clients.

### <a name="security-playbooks-are-rolling-out-in-phases"></a>Les règles de sécurité sont déployées en plusieurs phases

Dans le cadre de l’AIR, les règles de sécurité sont déployées en plusieurs phases. La phase 1 est désormais généralement disponible et comprend plusieurs règles qui fournissent des recommandations pour les actions que les administrateurs de la sécurité peuvent examiner et approuver :
- Message hameçon signalé par l’utilisateur
- URL cliquez sur modifier le verdict
- Détection de programmes malveillants après la livraison (programmes malveillants ZAP)
- Hameçonnage détecté après la livraison ZAP (hameçon ZAP)

La phase 1 prend également en charge les enquêtes de courrier électronique déclenchées par l’administrateur (à l’aide de l' [Explorateur de menaces](threat-explorer.md)).

La phase 2 est désormais en cours avec les règles suivantes en **Aperçu public**, en fournissant des recommandations pour les actions et en aidant les administrateurs de la sécurité à examiner les problèmes :
- Utilisateur signalé comme compromis (préversion publique)

D’autres règles seront publiées au fur et à mesure de leur exécution. Consultez la feuille de [route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour voir les autres éléments planifiés et bientôt disponibles.

### <a name="playbooks-include-investigation-and-recommendations"></a>Les règles incluent une enquête et des recommandations

Dans AIR, chaque manuel de sécurité inclut les éléments suivants : 
- une enquête racine des entités d’un e-mail (fichiers, URL, destinataires, adresses IP, etc.);
- la chasse aux courriels similaires reçus par l’Organisation ; 
- les étapes à suivre pour identifier et corréler les autres menaces potentielles, et 
- actions de correction des menaces recommandées.

Chaque étape de haut niveau inclut un certain nombre de sous-étapes qui sont exécutées pour fournir une réponse approfondie, détaillée et exhaustive aux menaces.

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Exemple : un message hameçon signalé par un utilisateur lance un manuel d’enquête.

Lorsqu’un utilisateur de votre organisation soumet un message électronique et le signale à Microsoft à l’aide du [complément de message de rapport pour Outlook ou Outlook Web App](enable-the-report-message-add-in.md), le rapport est également envoyé à votre système et est visible dans l’Explorateur dans la vue signalée par l’utilisateur. Ce message signalée par l’utilisateur déclenche désormais une alerte d’information basée sur le système, qui lance automatiquement le manuel d’enquête.

Lors de la phase d’enquête de racine, différents aspects du courrier électronique sont évalués. Cela inclut ce qui suit :
- Détermination du type de menace susceptible de se présenter ;
- Expéditeur ;
- Emplacement d’envoi du courrier électronique (infrastructure émettrice);
- Si d’autres instances du courrier électronique ont été remises ou bloquées ;
- Une évaluation de nos analystes ;
- Si le courrier électronique est associé à des campagnes connues ;
- et bien plus encore.

Une fois l’enquête terminée, le manuel fournit une liste des actions recommandées à effectuer sur le courrier électronique d’origine et les entités qui lui sont associées.
  
Ensuite, plusieurs étapes d’enquête sur les menaces et de chasse sont exécutées :

- Les messages électroniques similaires sont identifiés par des recherches de cluster de messagerie.
- Le signal est partagé avec d’autres plateformes, telles que [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Une détermination est effectuée sur le fait que les utilisateurs aient cliqué sur les liens malveillants dans les messages électroniques suspects.
- Une vérification est effectuée dans Office 365 Exchange Online Protection ([EOP](exchange-online-protection-eop.md)) et Office 365 Advanced Threat Protection ([ATP](office-365-atp.md)) pour voir s’il existe d’autres messages similaires signalés par les utilisateurs.
- Une vérification est exécutée pour déterminer si un utilisateur a été compromis. Cette vérification exploite les signaux entre Office 365, [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security)et [Azure Active Directory](https://docs.microsoft.com/azure/active-directory), en mettant en corrélation les anomalies d’activité de l’utilisateur associées. 

Au cours de la phase de chasse, les risques et les menaces sont affectés à différentes étapes de la chasse. 

La correction est la phase finale du manuel. Pendant cette phase, les étapes de correction sont prises, en fonction des phases d’enquête et de chasse. 

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Exemple : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur de menaces

En plus des recherches automatiques déclenchées par une alerte, l’équipe des opérations de sécurité de votre organisation peut déclencher une enquête automatique à partir d’une vue dans l' [Explorateur de menaces](threat-explorer.md).

Par exemple, supposons que vous affichiez des données dans l’Explorateur à propos des messages signalés par l’utilisateur. Vous pouvez sélectionner un élément dans la liste des résultats, puis cliquer sur **Rechercher** dans le menu Action (en supposant que vous disposez des autorisations de correction appropriées).

![Messages signalés par l’utilisateur dans l’Explorateur avec le bouton Rechercher](../../media/Explorer-UserReported-Investigate.png)

Autre exemple : Supposons que vous affichiez des données sur les messages électroniques détectés comme contenant des programmes malveillants, et que plusieurs messages électroniques soient détectés comme contenant des programmes malveillants. Vous pouvez sélectionner l’onglet **courrier électronique** , sélectionner un ou plusieurs messages, puis, dans le menu **actions** , sélectionner **examiner**. 

![Démarrage d’une enquête pour les programmes malveillants dans l’Explorateur](../../media/Explorer-Malware-Email-ActionsInvestigate.png)

À l’instar des règles déclenchées par une alerte, les recherches automatiques déclenchées à partir d’une vue dans l’Explorateur incluent une enquête de racine, des étapes permettant d’identifier et de corréler les menaces, ainsi que les actions recommandées pour atténuer ces menaces.

## <a name="next-steps"></a>Étapes suivantes

- [Prise en main de l’utilisation de l’AIR dans Office 365](office-365-air.md)

- [Consultez la feuille de route Microsoft 365 pour découvrir les éléments bientôt disponibles et à déployer](https://www.microsoft.com/microsoft-365/roadmap?filters=)

