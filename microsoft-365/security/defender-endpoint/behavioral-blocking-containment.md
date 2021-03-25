---
title: Blocage et contenu comportementaux
description: En savoir plus sur les fonctionnalités de blocage du comportement et de blocage dans Microsoft Defender ATP
keywords: Microsoft Defender ATP, EDR en mode blocage, blocage du mode passif
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
localization_priority: Normal
ms.custom:
- next-gen
- edr
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.technology: mde
ms.openlocfilehash: dcad3b7233f2efd444d41c15916eaae195634c8c
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51166232"
---
# <a name="behavioral-blocking-and-containment"></a>Blocage et contenu comportementaux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Vue d’ensemble

Le paysage actuel des menaces est dépassé par les programmes malveillants sans fichier et qui se trouvent en dehors de la région, les menaces hautement polymorphes qui mutent plus rapidement que les solutions traditionnelles peuvent suivre et les attaques gérées par l’homme qui s’adaptent à ce que les adversaires trouvent sur des appareils compromis. [](https://docs.microsoft.com/windows/security/threat-protection/intelligence/fileless-threats) Les solutions de sécurité traditionnelles ne sont pas suffisantes pour arrêter ces attaques ; vous avez besoin de fonctionnalités d’intelligence artificielle (IA) et d’apprentissage des appareils (ML), telles que le blocage du comportement et le contenu, inclus dans [Defender pour point de terminaison.](https://docs.microsoft.com/windows/security) 

Les fonctionnalités de blocage du comportement et de blocage du contenu peuvent aider à identifier et à arrêter les menaces, en fonction de leurs comportements et des arbre de traitement, même lorsque la menace a démarré l’exécution. Les composants et fonctionnalités de protection de nouvelle génération, d’EDR et de Defender pour les points de terminaison fonctionnent ensemble dans les fonctionnalités de blocage du comportement et de contenu. 

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="Blocage et contenu comportementaux":::

Les fonctionnalités de blocage du comportement et de blocage du contenu fonctionnent avec plusieurs composants et fonctionnalités de Defender for Endpoint pour arrêter immédiatement les attaques et empêcher la progression des attaques.

- [La protection nouvelle génération](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) (qui inclut l’Antivirus Microsoft Defender) peut détecter les menaces en analysant les comportements et arrêter les menaces qui ont commencé à s’exécutent.

- [La détection et la réponse](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) des points de terminaison (EDR) reçoivent des signaux de sécurité sur votre réseau, vos appareils et votre comportement du noyau. Lorsque des menaces sont détectées, des alertes sont créées. Plusieurs alertes du même type sont regroupées en incidents, ce qui permet à votre équipe des opérations de sécurité d’examiner et de répondre plus facilement.

- [Defender pour le](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) point de terminaison dispose d’une large gamme d’optiques entre les identités, le courrier électronique, les données et les applications, en plus des signaux de comportement réseau, de point de terminaison et de noyau reçus via EDR. Un composant de [Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-threat-protection), Defender for Endpoint traite et met en corrélation ces signaux, lève des alertes de détection et connecte les alertes associées dans les incidents.

Avec ces fonctionnalités, d’autres menaces peuvent être évitées ou bloquées, même si elles commencent à s’exécutent. Chaque fois qu’un comportement suspect est détecté, la menace est contenue, des alertes sont créées et des menaces sont arrêtées dans leurs pistes. 

L’image suivante montre un exemple d’alerte déclenchée par des fonctionnalités de blocage du comportement et de contenu :

:::image type="content" source="images/blocked-behav-alert.png" alt-text="Exemple d’alerte par blocage et contenu comportementaux":::

## <a name="components-of-behavioral-blocking-and-containment"></a>Composants de blocage et de blocage du comportement

- Règles de réduction de la surface d’attaque sur client et **[pilotée par la stratégie](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/attack-surface-reduction)** L’exécution des comportements d’attaque courants prédéfini est empêchée, conformément à vos règles de réduction de la surface d’attaque. Lorsque de tels comportements tentent de s’exécuter, ils sont visibles dans le Centre de sécurité Microsoft Defender comme des [https://securitycenter.windows.com](https://securitycenter.windows.com) alertes d’information. (Les règles de réduction de la surface d’attaque ne sont pas activées par défaut ; vous configurez vos stratégies dans le Centre de sécurité Microsoft Defender.)

- **[Blocage du comportement client](client-behavioral-blocking.md)** Les menaces sur les points de terminaison sont détectées par le biais de l’apprentissage automatique, puis sont bloquées et corrigés automatiquement. (Le blocage du comportement client est activé par défaut.) 

- **[Le blocage de boucle de commentaires](feedback-loop-blocking.md)** (également appelé protection rapide) les détections de menaces sont observées par l’intelligence comportementale. Les menaces sont arrêtées et empêchées de s’exécutent sur d’autres points de terminaison. (Le blocage de la boucle de commentaires est activé par défaut.) 

- **[Détection et réponse des points de terminaison (EDR) en mode blocage](edr-in-block-mode.md)** Les artefacts ou comportements malveillants observés par le biais de la protection post-violation sont bloqués et contenus. L’EDR en mode blocage fonctionne même si l’Antivirus Microsoft Defender n’est pas la solution antivirus principale. (EDR en mode blocage n’est pas activé par défaut ; vous l’activez dans le Centre de sécurité Microsoft Defender.) 

Attendez-vous à en savoir plus sur le blocage et le blocage du comportement, car Microsoft continue d’améliorer les fonctionnalités et fonctionnalités de protection contre les menaces. Pour voir ce qui est planifié et déployer maintenant, consultez la feuille de route [Microsoft 365.](https://www.microsoft.com/microsoft-365/roadmap)

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>Exemples de blocage comportemental et de blocage en action

Les fonctionnalités de blocage du comportement et de blocage du contenu ont bloqué les techniques de l’attaquant, telles que les suivantes :

- Informations d’identification de LSASS
- Injection entre processus
- Processus d’vidage
- Contournement du contrôle de compte d’utilisateur
- Falsification de l’antivirus (par exemple, désactivation ou ajout d’un programme malveillant en tant qu’exclusion)
- Contacting Command and Control (C&C) to download payloads
- Exploration de pièces
- Modification de l’enregistrement de démarrage
- Attaques par hachage
- Installation du certificat racine
- Tentative d’exploitation pour diverses vulnérabilités

Vous trouverez ci-dessous deux exemples réels de blocage et de blocage du comportement en action.

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>Exemple 1 : attaque par vol d’informations d’identification contre 100 organisations

Comme décrit dans La défense contre les menaces contre les menaces: le blocage basé sur le comportement de [l’IA](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks)arrête les attaques sur leur piste , une attaque par vol d’informations d’identification contre 100 organisations dans le monde a été arrêtée par des fonctionnalités de blocage comportemental et de blocage. Les messages électroniques de harponnage contenant un document leurre ont été envoyés aux organisations ciblées. Si un destinataire a ouvert la pièce jointe, un document distant associé a pu exécuter du code sur l’appareil de l’utilisateur et charger des programmes malveillants Lokibot, qui ouvrent des informations d’identification, des données volées exfiltrées et attendent des instructions supplémentaires d’un serveur de commande et de contrôle. 

Les modèles d’apprentissage des appareils basés sur le comportement dans Defender pour le point de terminaison ont intercepté et arrêté les techniques de l’attaquant à deux points de la chaîne d’attaque :
- La première couche de protection a détecté le comportement d’exploitation. Les classifieurs d’apprentissage des appareils dans le cloud ont correctement identifié la menace et ont immédiatement demandé à l’appareil client de bloquer l’attaque.
- La deuxième couche de protection, qui a permis d’arrêter les cas où l’attaque est passée au-delà de la première couche, a détecté un processus en train de s’arrêter et a supprimé les fichiers correspondants (par exemple, Lokibot). 

Pendant que l’attaque a été détectée et arrêtée, des alertes, telles qu’une « alerte d’accès initial », ont été déclenchées et sont apparues dans le Centre de sécurité Microsoft Defender ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ) :

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="Alerte d’accès initial dans le Centre de sécurité Microsoft Defender":::

Cet exemple montre comment les modèles d’apprentissage des appareils basés sur le comportement dans le cloud ajoutent de nouvelles couches de protection contre les attaques, même après leur exécution.

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>Exemple 2 : relais NTLM - Variante de programme malveillant NTLM

Comme décrit dans le dernier billet de blog, Blocage et contenu comportementaux : transformation de l’optique en [protection,](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection)en janvier 2020, Defender for Endpoint a détecté une activité d’escalade de privilèges sur un appareil d’une organisation. Une alerte appelée « Escalade de privilèges possible à l’aide du relais NTLM » a été déclenchée.

:::image type="content" source="images/NTLMalertjuicypotato.png" alt-text="Alerte NTLM pour les programmes malveillants de la sécurité":::

La menace s’est transformée en programme malveillant . Il s’agissait d’une variante nouvelle, qui n’était pas visible avant, d’un outil de piratage d’ordinateurs, appeléSySerring, qui est utilisé par les attaquants pour obtenir une escalade de privilèges sur un appareil. 

Quelques minutes après le déclenchement de l’alerte, le fichier a été analysé et confirmé comme malveillant. Son processus a été arrêté et bloqué, comme illustré dans l’image suivante :

:::image type="content" source="images/Artifactblockedjuicypotato.png" alt-text="Artefact bloqué":::

Quelques minutes après le blocage de l’artefact, plusieurs instances du même fichier ont été bloquées sur le même appareil, ce qui a empêché d’autres personnes malveillantes ou d’autres programmes malveillants de se déployer sur l’appareil. 

Cet exemple montre qu’avec les fonctionnalités de blocage du comportement et de blocage, les menaces sont détectées, contenues et bloquées automatiquement. 

## <a name="next-steps"></a>Étapes suivantes

- [En savoir plus sur Defender pour le point de terminaison](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)

- [Configurer vos règles de réduction de la surface d’attaque](attack-surface-reduction.md)

- [Activer EDR en mode blocage](edr-in-block-mode.md)

- [Voir l’activité récente des menaces globales](https://www.microsoft.com/wdsi/threats)

- [Obtenir une vue d’ensemble de Microsoft 365 Defender ](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-threat-protection)