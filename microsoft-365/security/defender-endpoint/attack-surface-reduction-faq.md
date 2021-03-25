---
title: 'Réduction de la surface d’attaque : forum aux questions (FAQ)'
description: Trouvez des réponses aux questions fréquemment posées sur les règles de réduction de la surface d’attaque de Microsoft Defender ATP.
keywords: Règles de réduction de la surface d’attaque, asr, hips, système de prévention des intrusions hôtes, règles de protection, anti-attaque, attaque, prévention des infections, microsoft defender pour le point de terminaison
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
author: martyav
ms.author: v-maave
ms.reviewer: ''
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.openlocfilehash: 7685bd70d85ecebe759ade762b78ee2c3639cea8
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51061798"
---
# <a name="attack-surface-reduction-frequently-asked-questions-faq"></a>Réduction de la surface d’attaque : forum aux questions (FAQ)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="is-attack-surface-reduction-asr-part-of-windows"></a>La réduction de la surface d’attaque fait-elle partie de Windows ?

Asr était à l’origine une fonctionnalité de la suite de fonctionnalités Exploit Guard introduite en tant que mise à jour majeure de l’Antivirus Microsoft Defender, dans Windows 10, version 1709. L’Antivirus Microsoft Defender est le composant anti-programme malveillant natif de Windows. Toutefois, l’ensemble complet des fonctionnalités asr est disponible uniquement avec une licence d’entreprise Windows. Notez également que les exclusions de règles de la RSA sont gérées séparément des exclusions de l’Antivirus Microsoft Defender.

## <a name="do-i-need-to-have-an-enterprise-license-to-run-asr-rules"></a>Ai-je besoin d’une licence d’entreprise pour exécuter des règles de RSA ?

L’ensemble complet des règles et des fonctionnalités de la fonctionnalité de r asr est uniquement pris en charge si vous disposez d’une licence d’entreprise pour Windows 10. Un nombre limité de règles peut fonctionner sans licence d’entreprise. Si vous avez Microsoft 365 Business, définissez l’Antivirus Microsoft Defender comme solution de sécurité principale et activez les règles via PowerShell. Toutefois, l’utilisation de la RSA sans licence d’entreprise n’est pas officiellement prise en charge et les fonctionnalités complètes de la RSA ne seront pas disponibles.

Pour en savoir plus sur les licences Windows, voir [Licences Windows 10](https://www.microsoft.com/licensing/product-licensing/windows10?activetab=windows10-pivot:primaryr5) et obtenir le guide des licences en [volume pour Windows 10.](https://download.microsoft.com/download/2/D/1/2D14FE17-66C2-4D4C-AF73-E122930B60F6/Windows-10-Volume-Licensing-Guide.pdf)

## <a name="is-asr-supported-if-i-have-an-e3-license"></a>La RSA est-elle prise en charge si j’ai une licence E3 ?

Oui. La RSA est prise en charge pour Windows Entreprise E3 et les applications supérieures. 

## <a name="which-features-are-supported-with-an-e5-license"></a>Quelles fonctionnalités sont pris en charge avec une licence E5 ?

Toutes les règles prise en charge avec E3 sont également pris en charge avec E5.

E5 a également ajouté une meilleure intégration avec Defender pour endpoint. Avec E5, vous pouvez utiliser [Defender pour](https://docs.microsoft.com/microsoft-365/security/defender/monitor-devices?view=o365-worldwide&preserve-view=true#monitor-and-manage-asr-rule-deployment-and-detections) point de terminaison pour surveiller et examiner l’analyse des alertes en temps réel, affiner les exclusions de règles, configurer des règles de la asr. et afficher des listes de rapports d’événements.

## <a name="what-are-the-currently-supported-asr-rules"></a>Quelles sont les règles de asr actuellement pris en charge ?

La asr actuellement prend en charge toutes les règles ci-dessous :

* [Bloquer le contenu exécutable du client de messagerie et de la messagerie web](attack-surface-reduction.md#block-executable-content-from-email-client-and-webmail)
* [Empêcher toutes les applications Office de créer des processus enfants](attack-surface-reduction.md#block-all-office-applications-from-creating-child-processes)
* [Empêcher les applications Office de créer du contenu exécutable](attack-surface-reduction.md#block-office-applications-from-creating-executable-content)
* [Empêcher les applications Office d’injecter du code dans d’autres processus](attack-surface-reduction.md#block-office-applications-from-injecting-code-into-other-processes)
* [Empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé](attack-surface-reduction.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content)
* [Bloquer l’exécution de scripts potentiellement obscurcis](attack-surface-reduction.md#block-execution-of-potentially-obfuscated-scripts)
* [Bloquer les appels d’API Win32 à partir d’une macro Office](attack-surface-reduction.md#block-win32-api-calls-from-office-macros)
* [Utiliser la protection avancée contre les ransomware](attack-surface-reduction.md#use-advanced-protection-against-ransomware)
* [Bloquer le vol d’informations d’identification du](attack-surface-reduction.md#block-credential-stealing-from-the-windows-local-security-authority-subsystem) sous-système d’autorité de sécurité locale Windows (lsass.exe)
* [Bloquer les créations de processus provenant de commandes PSExec et WMI](attack-surface-reduction.md#block-process-creations-originating-from-psexec-and-wmi-commands)
* [Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB](attack-surface-reduction.md#block-untrusted-and-unsigned-processes-that-run-from-usb)
* [Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à des critères de prévalence, d’âge ou de listes fiables](attack-surface-reduction.md#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)
* [Empêcher les applications de communication Office de créer des processus enfants](attack-surface-reduction.md#block-office-communication-application-from-creating-child-processes)
* [Empêcher Adobe Reader de créer des processus enfants](attack-surface-reduction.md#block-adobe-reader-from-creating-child-processes)
* [Bloquer la persistance via un abonnement à des événements WMI](attack-surface-reduction.md#block-persistence-through-wmi-event-subscription)

## <a name="what-are-some-good-recommendations-for-getting-started-with-asr"></a>Quelles sont les bonnes recommandations pour la mise en place de la R ASR ?

Testez l’impact des règles de la récupération automatique sur votre organisation avant de les activer en exécutant des règles asr en mode audit pendant une courte période. Lorsque vous exécutez les règles en mode audit, vous pouvez identifier les applications métiers qui peuvent être bloquées par erreur et les exclure de la récupération automatique.

Les grandes organisations doivent envisager de déployer des règles asr dans des « anneaux » en auditant et en activant des règles dans des sous-ensembles d’appareils de plus en plus larges. Vous pouvez organiser les appareils de votre organisation en anneaux à l’aide d’Intune ou d’un outil de gestion des stratégies de groupe.

## <a name="how-long-should-i-test-an-asr-rule-in-audit-mode-before-enabling-it"></a>Combien de temps dois-je tester une règle asr en mode audit avant de l’activer ?

Conservez la règle en mode audit pendant environ 30 jours pour obtenir une bonne planification du fonctionnement de la règle une fois qu’elle est en cours de fonctionnement dans toute votre organisation. Pendant la période d’audit, vous pouvez identifier les applications métiers qui peuvent être bloquées par la règle et configurer la règle pour les exclure.

## <a name="im-making-the-switch-from-a-third-party-security-solution-to-defender-for-endpoint-is-there-an-easy-way-to-export-rules-from-another-security-solution-to-asr"></a>Je passe d’une solution de sécurité tierce à Defender for Endpoint. Existe-t-il un moyen « simple » d’exporter des règles à partir d’une autre solution de sécurité vers la RSA ?

Dans la plupart des cas, il est plus facile et préférable de commencer avec les recommandations de référence suggérées par [Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection) que d’essayer d’importer des règles à partir d’une autre solution de sécurité. Ensuite, utilisez des outils tels que le mode audit, la surveillance et l’analyse pour configurer votre nouvelle solution en fonction de vos besoins uniques. 

La configuration par défaut de la plupart des règles asr, combinée avec la protection en temps réel de Defender pour endpoint, protège contre un grand nombre d’attaques et de vulnérabilités.

À partir de Defender for Endpoint, vous pouvez mettre à jour vos défenses avec des indicateurs personnalisés, pour autoriser et bloquer certains comportements logiciels. La asr permet également une certaine personnalisation des règles, sous la forme d’exclusions de fichiers et de dossiers. En règle générale, il est préférable d’auditer une règle pendant un certain temps et de configurer des exclusions pour toutes les applications métiers qui peuvent être bloquées.

## <a name="does-asr-support-file-or-folder-exclusions-that-include-system-variables-and-wildcards-in-the-path"></a>La RSA prend-elle en charge les exclusions de fichiers ou de dossiers qui incluent des variables système et des caractères génériques dans le chemin d’accès ?

Oui. Pour plus d’informations sur l’exclusion des fichiers ou des dossiers des règles de la asr, voir Exclure des fichiers et des [dossiers](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) des règles de la asr. Pour plus d’informations sur l’utilisation de variables système et de caractères génériques dans les chemins d’accès aux fichiers exclus, voir Exclure des fichiers et des [dossiers](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-extension-file-exclusions-microsoft-defender-antivirus#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) en fonction de l’extension de fichier et de l’emplacement des dossiers.

## <a name="do-asr-rules-cover-all-applications-by-default"></a>Les règles DER couvrent-ils toutes les applications par défaut ?

Cela dépend de la règle. La plupart des règles DER couvrent le comportement des produits et services Microsoft Office, tels que Word, Excel, PowerPoint et OneNote, ou Outlook. Certaines règles de la astérisation, telles que bloquer l’exécution de scripts potentiellement *obscurcis,* sont plus générales.

## <a name="does-asr-support-third-party-security-solutions"></a>La RSA prend-elle en charge des solutions de sécurité tierces ?

La asr utilise l’Antivirus Microsoft Defender pour bloquer les applications. Il n’est pas possible de configurer la asr pour qu’elle utilise une autre solution de sécurité pour le blocage pour le moment.

## <a name="i-have-an-e5-license-and-enabled-some-asr-rules-in-conjunction-with-defender-for-endpoint-is-it-possible-for-an-asr-event-to-not-show-up-at-all-in-defender-for-endpoints-event-timeline"></a>J’ai une licence E5 et j’ai activé certaines règles asr en association avec Defender for Endpoint. Est-il possible qu’un événement ASR ne s’affiche pas du tout dans la chronologie des événements de Defender for Endpoint ?

Chaque fois qu’une notification est déclenchée localement par une règle ASR, un rapport sur l’événement est également envoyé au portail Defender for Endpoint. Si vous avez des difficultés à trouver l’événement, vous pouvez filtrer la chronologie des événements à l’aide de la zone de recherche. Vous pouvez également afficher les événements de la surface d’attaque en visitant La gestion de la **surface** d’attaque, à partir de l’icône Gestion de la **configuration** dans la barre des tâches du Centre de sécurité. La page de gestion de la surface d’attaque inclut un onglet pour les détections de rapports, qui inclut la liste complète des événements de règle de la surface d’attaque signalés à Defender pour le point de terminaison.

## <a name="i-applied-a-rule-using-gpo-now-when-i-try-to-check-the-indexing-options-for-the-rule-in-microsoft-outlook-i-get-a-message-stating-access-denied"></a>J’ai appliqué une règle à l’aide d’un GPO. Maintenant, lorsque j’essaie de vérifier les options d’indexation de la règle dans Microsoft Outlook, je reçois un message indiquant « Accès refusé ».

Essayez d’ouvrir les options d’indexation directement à partir de Windows 10.

1. Sélectionnez **l’icône** Rechercher dans la barre des tâches Windows.

1. Entrez **les options d’indexation** dans la zone de recherche.

## <a name="are-the-criteria-used-by-the-rule-block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion-configurable-by-an-admin"></a>Les critères utilisés par la règle« Bloquer l’exécution des fichiers exécutables, sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance », peuvent-ils être configurés par un administrateur ?

Non. Les critères utilisés par cette règle sont tenus à jour par la protection cloud de Microsoft, afin de maintenir la liste de confiance constamment à jour avec les données recueillies dans le monde entier. Les administrateurs locaux n’ont pas accès en écriture pour modifier ces données. Si vous cherchez à configurer cette règle pour l’adapter à votre entreprise, vous pouvez ajouter certaines applications à la liste d’exclusions pour empêcher le déclenchement de la règle.

## <a name="i-enabled-the-asr-rule-block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion-after-some-time-i-updated-a-piece-of-software-and-the-rule-is-now-blocking-it-even-though-it-didnt-before-did-something-go-wrong"></a>J’ai activé l’exécution de la règle asr, Bloquer les fichiers *exécutables,* sauf s’ils répondent à un critère de prévalence, d’âge ou de liste de confiance. Après un certain temps, j’ai mis à jour un logiciel et la règle le bloque, même si ce n’était pas le cas auparavant. Un problème s’est-il passé ?

Cette règle repose sur la réputation connue de chaque application, telle que mesurée par la prévalence, l’âge ou l’inclusion dans une liste d’applications de confiance. La décision de la règle de bloquer ou d’autoriser une application est déterminée par l’évaluation de ces critères par la protection cloud de Microsoft.

En règle générale, la protection cloud peut déterminer qu’une nouvelle version d’une application est suffisamment similaire aux versions précédentes qu’elle n’a pas besoin d’être réévaluée en longueur. Toutefois, la construction de la réputation de l’application après le changement de version peut prendre un certain temps, en particulier après une mise à jour majeure. En attendant, vous pouvez ajouter l’application à la liste d’exclusions, afin d’empêcher cette règle de bloquer les applications importantes. Si vous êtes fréquemment mis à jour et que vous travaillez avec de nouvelles versions d’applications, vous pouvez choisir d’exécuter cette règle en mode audit.

## <a name="i-recently-enabled-the-asr-rule-block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe-and-i-am-getting-a-large-number-of-notifications-what-is-going-on"></a>J’ai récemment activé la règle de reconnaissance automatique des informations d’identification, bloquer le vol d’informations d’identification du sous-système d’autorité de sécurité locale *Windows (lsass.exe)* et j’ai reçu un grand nombre de notifications. Que se passe-t-il?

Une notification générée par cette règle n’indique pas nécessairement une activité malveillante ; Toutefois, cette règle est toujours utile pour bloquer les activités malveillantes, car les programmes malveillants ciblent souvent lsass.exe pour obtenir un accès illégal aux comptes. Le processus lsass.exe stocke les informations d’identification de l’utilisateur en mémoire après qu’un utilisateur s’est connecté. Windows utilise ces informations d’identification pour valider les utilisateurs et appliquer des stratégies de sécurité locales.

Étant donné que de nombreux processus légitimes tout au long d’une journée classique appelleront lsass.exe d’informations d’identification, cette règle peut être particulièrement bruyante. Si une application légitime connue génère un nombre excessif de notifications pour cette règle, vous pouvez l’ajouter à la liste d’exclusions. La plupart des autres règles asr génèrent un nombre de notifications relativement plus petit, par rapport à celle-ci, car l’appel sur lsass.exe est caractéristique du fonctionnement normal de nombreuses applications.

## <a name="is-it-a-good-idea-to-enable-the-rule-block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe-alongside-lsa-protection"></a>Est-il bon d’activer la règle, bloquer le vol d’informations d’identification du sous-système de l’autorité de sécurité locale *Windows (lsass.exe)* et la protection LSA ?

L’activation de cette règle ne fournira pas de protection supplémentaire si vous avez également activé la [protection LSA.](https://docs.microsoft.com/windows-server/security/credentials-protection-and-management/configuring-additional-lsa-protection#BKMK_HowToConfigure) La règle et la protection LSA fonctionnent de la même manière, de sorte que leur exécution en même temps serait redondante. Toutefois, il se peut que vous ne soyez pas en mesure d’activer la protection LSA. Dans ce cas, vous pouvez activer cette règle pour fournir une protection équivalente contre les programmes malveillants qui ciblent lsass.exe.

## <a name="see-also"></a>Voir aussi

* [Vue d’ensemble de la réduction de la surface d’attaque](attack-surface-reduction.md)
* [Évaluer les règles de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)
* [Personnaliser les règles de réduction de la surface d’attaque](customize-attack-surface-reduction.md)
* [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)
* [Compatibilité de Microsoft Defender avec d’autres antivirus/logiciels anti-programme malveillant](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)