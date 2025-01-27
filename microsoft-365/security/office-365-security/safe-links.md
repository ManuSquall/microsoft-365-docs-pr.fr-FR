---
title: Liens sûrs
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
f1_keywords:
- "197503"
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- ZVO160
- ZXL160
- ZPP160
- ZWD160
ms.assetid: dd6a1fef-ec4a-4cf4-a25a-bb591c5811e3
description: Dans cet article, les administrateurs peuvent en savoir plus sur la protection contre les liens sécurisés dans Defender for Office 365 pour protéger leur organisation contre le hameçonnage et d’autres attaques qui utilisent des URL malveillantes.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 240056565d88977aa7019f5a14e2db98a8dbb6db
ms.sourcegitcommit: ac3e9ccb7b43a42e600af8f44e6f30019533faeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2021
ms.locfileid: "52933190"
---
# <a name="safe-links-in-microsoft-defender-for-office-365"></a>Liens sécurisés dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](defender-for-office-365.md). Si vous utilisez Outlook.com, Microsoft 365 Famille ou Microsoft 365 Personnel et que vous recherchez des informations sur les liens sécurisés dans Outlook, voir Sécurité avancée [Outlook.com.](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2)

La fonctionnalité Liens sécurisés de Defender pour [Office 365](defender-for-office-365.md) fournit l’analyse et la réécriture d’URL des messages électroniques entrants dans le flux de messagerie, ainsi que la vérification au moment du clic des URL et des liens dans les messages électroniques et d’autres emplacements. L’analyse des liens sécurisés s’ajoute à la [protection](anti-spam-and-anti-malware-protection.md) régulière contre le courrier indésirable et les programmes malveillants dans les messages électroniques entrants dans Exchange Online Protection (EOP). L’analyse des liens sécurisés peut aider à protéger votre organisation contre les liens malveillants utilisés dans le hameçonnage et d’autres attaques.

La protection des liens sécurisés est disponible aux emplacements suivants :

- **Messages électroniques**: la protection des liens dans les messages électroniques est contrôlée par les stratégies de liens sécurisés. Il n’existe aucune stratégie de liens sécurisés par défaut, donc pour obtenir la protection des liens sûrs dans les messages électroniques, vous devez créer une ou plusieurs stratégies **de liens sécurisés.** Pour obtenir des instructions, voir [Configurer des stratégies de liens sécurisés dans Microsoft Defender Office 365](set-up-safe-links-policies.md).

  Pour plus d’informations sur la protection des liens sécurisés pour les messages électroniques, consultez la section Paramètres de liens [sécurisés](#safe-links-settings-for-email-messages) pour les messages électroniques plus loin dans cet article.
  
  > [!NOTE]
  > La fonction Liens sécurisés ne fonctionne pas sur les dossiers publics à messagerie.

- **Microsoft Teams** (actuellement en prévisualisation TAP) : la protection des liens sécurisés pour les liens dans les conversations Teams, les conversations de groupe ou à partir de canaux est également contrôlée par les stratégies de liens sécurisés. Il n’existe aucune stratégie de liens sécurisés par défaut, donc pour obtenir la protection des liens sécurisés dans Teams, vous devez créer une ou plusieurs stratégies de liens **sécurisés.**

  Pour plus d’informations sur la protection des liens Teams, voir les [paramètres](#safe-links-settings-for-microsoft-teams) de liens Microsoft Teams la section plus loin dans cet article.

- **Office 365 applications :** la protection des liens sécurisés pour Office 365 applications est disponible dans les applications de bureau, mobiles et web pris en charge. Vous **configurez la** protection des liens Office 365 les applications dans le paramètre global qui ne sont pas des **stratégies** de liens sécurisés. Pour obtenir des instructions, voir [Configurer les paramètres globaux](configure-global-settings-for-safe-links.md)des paramètres de liens sécurisés dans Microsoft Defender pour Office 365 .

  La protection des liens sécurisés pour les applications Office 365 est appliquée à tous les utilisateurs de l’organisation qui sont titulaires d’une licence Defender pour Office 365, que les utilisateurs soient inclus ou non dans les stratégies de liens sécurisés actives.

  Pour plus d’informations sur la protection des liens Office 365 les applications, consultez la section Paramètres de liens Office 365 [applications sécurisées](#safe-links-settings-for-office-365-apps) plus loin dans cet article.

Cet article contient des descriptions détaillées des types de paramètres de liens sécurisés suivants :

- **Paramètres stratégies** de liens sécurisés : ces paramètres s’appliquent uniquement aux utilisateurs inclus dans les stratégies spécifiques, et les paramètres peuvent être différents d’une stratégie à l’autre. Ces paramètres sont les suivants :

  - [Paramètres de liens sécurisés pour les messages électroniques](#safe-links-settings-for-email-messages)
  - [Paramètres de liens sécurisés pour Microsoft Teams](#safe-links-settings-for-microsoft-teams)
  - [« Ne pas réécrire les URL suivantes » dans les stratégies de liens sécurisés](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)

- **Paramètres globaux de liens sécurisés**: ces paramètres sont configurés globalement, et non dans les stratégies de liens sécurisés. Ces paramètres sont les suivants :

  - [Paramètres de liens sécurisés pour Office 365 applications](#safe-links-settings-for-office-365-apps)
  - [Liste « Bloquer les URL suivantes » pour les liens sécurisés](#block-the-following-urls-list-for-safe-links)

Le tableau suivant décrit les scénarios pour les liens sécurisés dans les organisations Microsoft 365 et Office 365 qui incluent Defender pour Office 365 (en d’autres termes, l’absence de licence n’est jamais un problème dans les exemples).

<br>

****

|Scénario|Résultat|
|---|---|
|Jean est membre du service marketing. La protection des liens Office 365 les applications est mise en place dans les paramètres globaux des liens sécurisés, et il existe une stratégie de liens sécurisés qui s’applique aux membres du service marketing. Jean ouvre une présentation PowerPoint dans un message électronique, puis clique sur une URL dans la présentation.|Jean est protégé par des liens sécurisés. <p> Jean est inclus dans une stratégie de liens sécurisés et la protection contre les liens sécurisés pour Office 365 applications est désactivée. <p> Pour plus d’informations sur les conditions requises pour la protection des liens sécurisés dans les applications Office 365, consultez la section Paramètres de liens [sécurisés](#safe-links-settings-for-office-365-apps) pour les applications Office 365 plus loin dans cet article.|
|Aucune stratégie de liens Microsoft 365 E5 n’est configurée pour l’organisation de Chris. Chris reçoit un courrier électronique d’un expéditeur externe qui contient une URL vers un site web malveillant sur qui il clique.|Chris n’est pas protégé par les liens sécurisés. <p> Un administrateur doit créer au moins une stratégie de liens sécurisés pour que tout le monde puisse obtenir la protection des liens sécurisés dans les messages électroniques entrants. Chris doit être inclus dans les conditions de la stratégie pour obtenir la protection contre les liens sécurisés.|
|Dans l’organisation de Pat, aucun administrateur n’a créé de stratégies de liens sécurisés, mais la protection contre les liens Office 365 applications est désactivée. Pat ouvre un document Word et clique sur une URL dans le fichier.|Pat n’est pas protégé par les liens sécurisés. <p> Bien que la protection des liens Office 365 applications sécurisées soit désactivée globalement, Pat n’est pas inclus dans les stratégies de liens sécurisés actives, de sorte que la protection ne peut pas être appliquée.|
|Dans l’organisation de Lee, est configuré dans la liste Bloquer les URL suivantes dans les `https://tailspintoys.com` **paramètres** globaux des liens sécurisés. Une stratégie de liens sécurisés qui inclut Lee existe déjà. Lee reçoit un message électronique qui contient `https://tailspintoys.com/aboutus/trythispage` l’URL. Lee clique sur l’URL.|L’URL peut être automatiquement bloquée pour Lee ; Cela dépend de l’entrée d’URL dans la liste et du client de messagerie Lee utilisé. Pour plus d’informations, voir la section « Bloquer les URL suivantes » pour la section Liens [sécurisés](#block-the-following-urls-list-for-safe-links) plus loin dans cet article.|
|Elle et Julia travaillent toutes les deux pour contoso.com. Il y a longtemps, les administrateurs configuraient des stratégies de liens sécurisés qui s’appliquaient à la fois à Celle-ci et à Julia. Il envoie un e-mail à Julia, sans savoir que le message contient une URL malveillante.|Julia est protégée par  la stratégie de liens sécurisés si la stratégie de liens sécurisés qui s’applique à elle est configurée pour s’appliquer aux messages entre des destinataires internes. Pour plus d’informations, consultez la section Paramètres de liens [sécurisés](#safe-links-settings-for-email-messages) pour les messages électroniques plus loin dans cet article.|
|

## <a name="safe-links-settings-for-email-messages"></a>Paramètres de liens sécurisés pour les messages électroniques

La liens sécurisés analyse le courrier électronique entrant pour les liens hypertexte malveillants connus. Les URL analysées sont réécrites à l’aide du préfixe d’URL standard Microsoft : `https://nam01.safelinks.protection.outlook.com` . Une fois le lien réécrit, il est analysé pour le contenu potentiellement malveillant.

Une fois que les liens sécurisés ont réécrit une  URL, l’URL reste réécrite, même si le message est transmis ou répondu manuellement (à la fois aux destinataires internes et externes). Les liens supplémentaires qui sont ajoutés au message transmis ou à qui une réponse a été répondue ne sont pas réécrits. Toutefois, dans  le cas du forwarding automatique par les règles de boîte de réception ou le transport  SMTP, l’URL ne sera pas réécrite dans le message destiné au destinataire final, sauf si ce destinataire est également protégé par des liens sécurisés ou si l’URL a déjà été réécrite dans une communication précédente. 

Les paramètres des stratégies de liens sécurisés qui s’appliquent aux messages électroniques sont décrits dans la liste suivante :

- **Sélectionnez l’action pour les URL potentiellement malveillantes inconnues** dans les messages : active ou désactive l’analyse des liens sécurisés dans les messages électroniques. La valeur recommandée est **Sur**. L’turning on this setting results in the following actions.

  - L’analyse des liens sécurisés est activée Outlook (C2R) sur Windows.
  - Les URL sont réécrites et les utilisateurs sont acheminés via la protection de liens sécurisés lorsqu’ils cliquent sur les URL des messages.
  - Lorsque vous cliquez dessus, les URL sont vérifiées par rapport à la liste des URL malveillantes connues et à la liste « Bloquer les URL [suivantes](#block-the-following-urls-list-for-safe-links)».
  - Les URL qui n’ont pas de réputation valide sont détonées de manière asynchrone en arrière-plan.

- Appliquer **l’analyse d’URL** en temps réel pour les liens suspects et les liens pointant vers des fichiers : active l’analyse en temps réel des liens, y compris les liens dans les messages électroniques qui pointent vers du contenu téléchargeable. La valeur recommandée est activée.
  - **Attendez que l’analyse de l’URL se termine avant de remettre le message**:
    - Activé : les messages qui contiennent des URL sont maintenus jusqu’à la fin de l’analyse. Les messages ne sont remis qu’une fois que les URL sont confirmées comme sûres. Il s’agit de la valeur recommandée.
    - Désactivé : si l’analyse d’URL ne peut pas se terminer, remettre le message quand même.

- Appliquer des liens sûrs aux **messages** électroniques envoyés au sein de l’organisation : active ou désactive l’analyse des liens sécurisés sur les messages envoyés entre des expéditeurs internes et des destinataires internes au sein de la même Exchange Online organisation. La valeur recommandée est activée.

- **Ne pas suivre les clics** de l’utilisateur : active ou désactive le stockage des données de clic de liens sécurisés pour les URL sur les messages électroniques. La valeur recommandée consiste à laisser ce paramètre non sélectionné (pour suivre les clics de l’utilisateur).

  Le suivi des clics d’URL pour les liens dans les messages électroniques envoyés entre des expéditeurs internes et des destinataires internes n’est actuellement pas pris en charge.

- **N’autorisez pas les utilisateurs** à cliquer sur l’URL d’origine : autorise ou empêche les utilisateurs de cliquer sur la [page](#warning-pages-from-safe-links) d’avertissement vers l’URL d’origine. La valeur recommandée est activée.

- **Afficher la marque de l’organisation sur les pages de notification** et d’avertissement : cette option affiche la marque de votre organisation sur les pages d’avertissement. La branding permet aux utilisateurs d’identifier les avertissements légitimes, car les pages d’avertissement Microsoft par défaut sont souvent utilisées par les attaquants. Pour plus d’informations sur la personnalisation, voir [Personnaliser Microsoft 365 thème pour votre organisation.](../../admin/setup/customize-your-organization-theme.md)

- **Ne réécrivez pas les URL suivantes :** Laisse les URL telles qu’elles sont. Conserve une liste personnalisée d’URL sécurisées qui n’ont pas besoin d’analyse. La liste est unique pour chaque stratégie de liens sécurisés. Pour plus d’informations sur la liste Ne pas réécrire les URL **suivantes,** voir les listes « Ne pas réécrire les URL suivantes » dans la section Stratégies de liens [sécurisés](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies) plus loin dans cet article.

  Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie Standard et Strict pour les stratégies de liens sécurisés, voir Paramètres de [stratégie de liens sécurisés.](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings)

- **Filtres de** destinataires : vous devez spécifier les conditions de destinataire et les exceptions qui déterminent à qui s’applique la stratégie. Vous pouvez utiliser ces propriétés pour les conditions et les exceptions :
  - **Le destinataire est**
  - **Le domaine du destinataire est**
  - **Le destinataire est membre de**

  Vous ne pouvez utiliser une condition ou une exception qu'une seule fois, mais la condition ou l'exception peut contenir plusieurs valeurs. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

- **Priorité**: si vous créez plusieurs stratégies, vous pouvez spécifier l’ordre dans le cas où elles sont appliquées. Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

  Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).
  
### <a name="how-safe-links-works-in-email-messages"></a>Fonctionnement des liens sécurisés dans les messages électroniques

À un niveau élevé, voici comment fonctionne la protection contre les liens sécurisés sur les URL des messages électroniques :

1. Tous les messages électroniques sont envoyés via EOP, où les filtres de protocole Internet (IP) et d’enveloppe, la protection anti-programme malveillant basée sur les signatures, le courrier indésirable et le logiciel anti-programme malveillant filtrent avant que le message ne soit remis à la boîte aux lettres du destinataire.

2. L’utilisateur ouvre le message dans sa boîte aux lettres et clique sur une URL dans le message.

3. La sécurité vérifie immédiatement l’URL avant d’ouvrir le site web :

   - Si l’URL est incluse dans la liste Bloquer les URL **suivantes,** un avertissement [d’URL bloquée](#blocked-url-warning) s’ouvre.

   - Si l’URL pointe vers un site web qui a été déterminé comme malveillant, une page d’avertissement de site [web](#malicious-website-warning) malveillant (ou une autre page d’avertissement) s’ouvre.

   - Si l’URL pointe vers un fichier téléchargeable et que l’analyse des **URL** en temps réel à la recherche de liens suspects et de liens pointant vers le paramètre de fichiers est activée dans la stratégie qui s’applique à l’utilisateur, le fichier téléchargeable est vérifié.

   - Si l’URL est déterminée comme sûre, le site web s’ouvre.

## <a name="safe-links-settings-for-microsoft-teams"></a>Paramètres de liens sécurisés pour Microsoft Teams

> [!IMPORTANT]
> À partir de mars 2020, cette fonctionnalité est disponible en prévisualisation et est disponible uniquement pour les membres du Microsoft Teams d’adoption de technologie (TAP). Pour plus d’informations sur la planification de publication, consultez la [feuille de Microsoft 365 de publication.](https://www.microsoft.com/microsoft-365/roadmap?rtc=1&filters=&searchterms=Safe%2CLinks%2CProtection%2Cfor%2CMicrosoft%2CTeams)

Vous activez ou désactivez la protection contre les liens Microsoft Teams dans les stratégies de liens sécurisés. Plus précisément, vous utilisez l’action Sélectionner pour les URL inconnues ou potentiellement **malveillantes** dans Microsoft Teams paramètre. La valeur recommandée est **Sur**.

Les paramètres suivants dans les stratégies de liens sécurisés qui s’appliquent aux liens dans les messages électroniques s’appliquent également aux liens Teams :

- **Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers**
- **Ne pas suivre les clics de l’utilisateur**
- **Ne pas autoriser les utilisateurs à accéder à l’URL d’origine**

Ces paramètres sont expliqués précédemment dans les paramètres de liens [sécurisés pour les messages électroniques.](#safe-links-settings-for-email-messages)

Une fois que vous avez activer la protection contre les liens sécurisés pour les Microsoft Teams, les URL de Teams sont vérifiées par rapport à la liste des liens malveillants connus lorsque l’utilisateur protégé clique sur le lien (protection au moment du clic). Les URL ne sont pas réécrites. Si un lien est jugé malveillant, les utilisateurs auront les expériences suivantes :

- Si vous avez cliqué sur le lien dans une conversation Teams, une conversation de groupe ou à partir de canaux, la page d’avertissement, comme illustré dans la capture d’écran ci-dessous, s’affiche dans le navigateur web par défaut.
- Si vous avez cliqué sur le lien à partir d’un onglet épinglé, la page d’avertissement s’affiche dans l’interface Teams dans cet onglet. L’option d’ouverture du lien dans un navigateur web est désactivée pour des raisons de sécurité.
- Selon la configuration du paramètre Ne pas autoriser les utilisateurs à accéder à **l’URL** d’origine de la stratégie, l’utilisateur est autorisé ou non à accéder à l’URL d’origine (continuer quand même **(non recommandé)** dans la capture d’écran). Nous vous recommandons d’activer le paramètre Ne pas autoriser les utilisateurs à cliquer sur le paramètre **d’URL** d’origine afin que les utilisateurs ne peuvent pas accéder à l’URL d’origine.

Si l’utilisateur qui a envoyé le lien n’est pas inclus dans une stratégie de liens sécurisés dans laquelle la protection Teams est activée, l’utilisateur est libre de cliquer sur l’URL d’origine sur son ordinateur ou son appareil.

![Une page liens sécurisés pour Teams page signalant un lien malveillant.](../../media/tp-safe-links-for-teams-malicious.png)

Cliquer sur le **bouton Revenir en** arrière dans la page d’avertissement permet de renvoyer l’utilisateur à son contexte d’origine ou à son emplacement d’URL. Toutefois, le fait de cliquer à nouveau sur le lien d’origine entraîne la réassuration de l’URL par la liaison sécurisée, de sorte que la page d’avertissement réapparaît.

### <a name="how-safe-links-works-in-teams"></a>Fonctionnement des liens sécurisés dans Teams

À un niveau élevé, voici comment fonctionne la protection contre les liens sécurisés pour les URL dans Microsoft Teams :

1. Un utilisateur démarre l’Teams’application.

2. Microsoft 365 vérifie que l’organisation de l’utilisateur inclut Microsoft Defender pour Office 365 et que l’utilisateur est inclus dans une stratégie de liens sécurisés active dans laquelle la protection contre Microsoft Teams est activée.

3. Les URL sont validées au moment du clic pour l’utilisateur dans les conversations, les conversations de groupe, les canaux et les onglets.

## <a name="safe-links-settings-for-office-365-apps"></a>Paramètres de liens sécurisés pour Office 365 applications

La protection des liens sécurisés pour les applications Office 365 vérifie les liens dans les documents Office, et non dans les messages électroniques (mais elle peut vérifier les liens dans les documents Office joints dans les messages électroniques une fois le document ouvert).

La protection des liens sécurisés pour Office 365 applications a les exigences client suivantes :

- Microsoft 365 Apps ou Microsoft 365 Business Premium.
  - Les versions actuelles de Word, Excel et PowerPoint sur Windows, Mac ou dans un navigateur web.
  - Office applications sur les appareils iOS ou Android.
  - Visio sur Windows.
  - OneNote dans un navigateur web.

- Office 365 sont configurées pour utiliser l’authentification moderne. Pour plus d’informations, voir Fonctionnement de l’authentification moderne [pour Office 2013, Office 2016 et Office applications clientes 2019.](../../enterprise/modern-auth-for-office-2013-and-2016.md)

- Les utilisateurs sont signés à l’aide de leurs comptes professionnels ou scolaires. Pour plus d’informations, [voir Se Office](https://support.microsoft.com/office/b9582171-fd1f-4284-9846-bdd72bb28426).

Vous configurez la protection des liens Office 365 les applications dans les paramètres globaux des liens sécurisés, et non dans les stratégies de liens sécurisés. La protection est appliquée à tous les utilisateurs de l’organisation titulaires d’une licence Defender pour Office 365, que les utilisateurs soient inclus ou non dans les stratégies de liens sécurisés actives.

Les paramètres de liens sécurisés suivants sont disponibles pour Office 365 applications :

- **Office 365 applications**: active ou désactive l’analyse des liens sécurisés dans les applications Office 365 pris en charge. La valeur par défaut et recommandée est **Sur**.

- Ne pas suivre le moment où les utilisateurs cliquent sur Liens sécurisés : active ou désactive le stockage des données de clic de liens sécurisés pour les URL sur les versions de bureau word, Excel, PowerPoint et Visio. La valeur recommandée est **Off,** ce qui signifie que les clics de l’utilisateur sont suivis.

- Ne laissez pas les utilisateurs cliquer sur des liens sécurisés vers **l’URL** d’origine : permet ou empêche les utilisateurs de cliquer sur la [page](#warning-pages-from-safe-links) d’avertissement vers l’URL d’origine dans les versions de bureau Word, Excel, PowerPoint et Visio. La valeur par défaut et recommandée est **Sur**.

Pour configurer les paramètres de liens sécurisés pour Office 365 applications, voir Configurer la protection des liens sécurisés [pour Office 365 applications.](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal)

Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie Standard et Strict, voir [Paramètres globaux des liens sécurisés.](recommended-settings-for-eop-and-office365.md#global-settings-for-safe-links)

### <a name="how-safe-links-works-in-office-365-apps"></a>Fonctionnement des liens sécurisés dans Office 365 applications

À un niveau élevé, voici comment fonctionne la protection contre les liens sécurisés pour les URL dans Office 365 applications. Les applications Office 365 sont décrites dans la section précédente.

1. Un utilisateur se signe à l’aide de son compte scolaire ou scolaire dans une organisation qui inclut Microsoft 365 Apps ou Microsoft 365 Business Premium.

2. L’utilisateur ouvre et clique sur un lien Office document dans une application Office.

3. La sécurité vérifie immédiatement l’URL avant d’ouvrir le site web cible :

   - Si l’URL est incluse dans la liste qui ignore l’analyse des liens sécurisés (la liste Bloquer les URL **suivantes),** une page d’avertissement [d’URL](#blocked-url-warning) bloquée s’ouvre.

   - Si l’URL pointe vers un site web qui a été déterminé comme malveillant, une page d’avertissement de site [web](#malicious-website-warning) malveillant (ou une autre page d’avertissement) s’ouvre.

   - Si l’URL pointe vers un fichier téléchargeable et que la stratégie de liens sécurisés qui s’applique à l’utilisateur est configurée pour analyser les liens vers le contenu téléchargeable (appliquer l’analyse **d’URL** en temps réel pour les liens suspects et les liens pointant vers des fichiers), le fichier téléchargeable est vérifié.

   - Si l’URL est considérée comme sûre, l’utilisateur est conduit sur le site web.

   - Si l’analyse des liens sécurisés ne parvient pas à se terminer, la protection contre les liens sécurisés ne se déclenche pas. Dans Office clients de bureau, l’utilisateur est averti avant de passer au site web de destination.

> [!NOTE]
> Le début de chaque session peut prendre plusieurs secondes pour vérifier que l’utilisateur dispose de liens Office activés.

## <a name="block-the-following-urls-list-for-safe-links"></a>Liste « Bloquer les URL suivantes » pour les liens sécurisés

La **liste Bloquer les URL suivantes** définit les liens qui sont toujours bloqués par l’analyse des liens sécurisés aux emplacements suivants :

- Messages électroniques.
- Documents dans Office 365 applications dans Windows mac.
- Documents dans Office pour iOS et Android.

Lorsqu’un utilisateur d’une stratégie de liens sécurisés active clique sur un lien bloqué dans une application prise en charge, il est placé sur la page d’avertissement de [l’URL bloquée.](#blocked-url-warning)

Vous configurez la liste des URL dans les paramètres globaux des liens sécurisés. Pour obtenir des instructions, voir Configurer la liste [« Bloquer les URL suivantes](configure-global-settings-for-safe-links.md#configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal)».

**Remarques** :

- Pour obtenir une liste véritablement universelle des URL bloquées partout, voir Gérer la liste d’adresses client [autoriser/bloquer.](tenant-allow-block-list.md)
- Limites pour la **liste Bloquer les URL suivantes** :
  - Le nombre maximal d’entrées est de 500.
  - La longueur maximale d’une entrée est de 128 caractères.
  - Toutes les entrées ne peuvent pas dépasser 10 000 caractères.
- N’incluez pas de barre oblique `/` () à la fin de l’URL. Par exemple, utilisez `https://www.contoso.com` , et non `https://www.contoso.com/` .
- Une URL de domaine uniquement (par exemple ou ) bloque toute `contoso.com` `tailspintoys.com` URL contenant le domaine.
- Vous pouvez bloquer un sous-domaine sans bloquer le domaine complet. Par exemple, bloque toute URL qui contient le sous-domaine, mais il ne bloque pas les URL qui contiennent `toys.contoso.com*` le domaine complet `contoso.com` .
- Vous pouvez inclure jusqu’à trois caractères génériques `*` () par entrée d’URL.

### <a name="entry-syntax-for-the-block-the-following-urls-list"></a>Syntaxe d’entrée pour la liste « Bloquer les URL suivantes »

Le tableau suivant décrit des exemples de valeurs que vous pouvez entrer et leurs résultats :

<br>

****

|Valeur|Résultat|
|---|---|
|`contoso.com` <p> ou <p> `*contoso.com*`|Bloque le domaine, les sous-domaines et les chemins d’accès. Par exemple, `https://www.contoso.com` et `https://sub.contoso.com` sont `https://contoso.com/abc` bloqués.|
|`https://contoso.com/a`|Bloque, `https://contoso.com/a` mais pas les sous-chemins supplémentaires comme `https://contoso.com/a/b` .|
|`https://contoso.com/a*`|Blocs `https://contoso.com/a` et sous-chemins supplémentaires tels que `https://contoso.com/a/b` .|
|`https://toys.contoso.com*`|Bloque un sous-domaine (dans cet exemple), mais autorise les clics vers d’autres `toys` URL de domaine (comme ou `https://contoso.com` `https://home.contoso.com` ).|
|

## <a name="do-not-rewrite-the-following-urls-lists-in-safe-links-policies"></a>« Ne pas réécrire les URL suivantes » dans les stratégies de liens sécurisés

> [!NOTE]
> Si votre organisation utilise des stratégies de liens sécurisés, les listes d’URL **suivantes** ne sont pas réécrites et sont la seule méthode prise en charge pour les tests de hameçonnage tiers.

Chaque stratégie de liens sécurisés contient une liste Ne pas réécrire les URL **suivantes** que vous pouvez utiliser pour spécifier les URL qui ne sont pas réécrites par l’analyse des liens sécurisés. En d’autres termes, la liste permet aux utilisateurs qui sont inclus dans la stratégie d’accéder aux URL spécifiées qui seraient autrement bloquées par des liens sécurisés. Vous pouvez configurer différentes listes dans différentes stratégies de liens sécurisés. Le traitement des stratégies s’arrête après l’application de la première stratégie (probablement la plus haute priorité) à l’utilisateur. Ainsi, une seule ne réécriture pas la liste d’URL suivante est appliquée à un utilisateur qui est inclus dans plusieurs **stratégies** de liens sécurisés actives.

Pour ajouter des entrées à la liste dans les stratégies de liens sécurisés nouvelles ou existantes, voir [Créer](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) des stratégies de liens sécurisés ou [Modifier des stratégies de liens sécurisés.](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-modify-safe-links-policies)

**Remarques** :

- Les clients suivants ne reconnaissent pas la liste Ne pas réécrire les URL suivantes dans les **stratégies** de liens sécurisés. Les utilisateurs inclus dans les polices peuvent être bloqués pour accéder aux URL en fonction des résultats de l’analyse des liens sécurisés dans ces clients :
  - Microsoft Teams
  - Office web apps

  Pour obtenir une liste véritablement universelle d’URL autorisées partout, voir Gérer la liste d’adresses client [autorisées/bloqués.](tenant-allow-block-list.md)

- Envisagez d’ajouter des URL internes couramment utilisées à la liste pour améliorer l’expérience utilisateur. Par exemple, si vous avez des services locaux, tels que Skype Entreprise ou SharePoint, vous pouvez ajouter ces URL pour les exclure de l’analyse.
- Si vous n’avez pas encore réécrit les **entrées d’URL suivantes** dans vos stratégies de liens sécurisés, n’oubliez pas de passer en revue les listes et d’ajouter des caractères génériques si nécessaire. Par exemple, votre liste a une entrée comme celle-ci et vous décidez ultérieurement `https://contoso.com/a` d’inclure des sous-chemins comme `https://contoso.com/a/b` . Au lieu d’ajouter une nouvelle entrée, ajoutez un caractère générique à l’entrée existante afin qu’elle devienne `https://contoso.com/a/*` .
- Vous pouvez inclure jusqu’à trois caractères génériques `*` () par entrée d’URL. Les caractères génériques incluent explicitement des préfixes ou des sous-domaine. Par exemple, l’entrée n’est pas la même que , car elle permet aux utilisateurs de visiter des sous-domaines et des chemins d’accès `contoso.com` `*.contoso.com/*` dans le domaine `*.contoso.com/*` spécifié.
- Si une URL utilise la redirection automatique pour HTTP vers HTTPS (par exemple, la redirection 302 vers ), et que vous essayez d’entrer les entrées HTTP et HTTPS pour la même URL dans la liste, vous remarquerez peut-être que la deuxième entrée d’URL remplace la première `http://www.contoso.com` entrée d’URL. `https://www.contoso.com` Ce comportement ne se produit pas si les versions HTTP et HTTPS de l’URL sont complètement séparées.

### <a name="entry-syntax-for-the-do-not-rewrite-the-following-urls-list"></a>Syntaxe d’entrée pour la liste « Ne pas réécrire les URL suivantes »

Le tableau suivant décrit des exemples de valeurs que vous pouvez entrer et leurs résultats :

<br>

****

|Valeur|Résultat|
|---|---|
|`contoso.com`|Permet d’accéder à des sous-domaine ou à des `https://contoso.com` chemins d’accès, mais pas à des sous-domaine.|
|`*.contoso.com/*`|Permet d’accéder à un domaine, des sous-domaines et des chemins d’accès (par exemple, `https://www.contoso.com` `https://www.contoso.com` , , ou `https://maps.contoso.com` `https://www.contoso.com/a` ). <p> Cette entrée est intrinsèquement meilleure que , car elle n’autorise pas les sites potentiellement `*contoso.com*` frauduleux, comme `https://www.falsecontoso.com` ou `https://www.false.contoso.completelyfalse.com`|
|`https://contoso.com/a`|Permet d’accéder `https://contoso.com/a` à des sous-chemins, mais pas à des sous-chemins comme `https://contoso.com/a/b`|
|`https://contoso.com/a/*`|Autorise l’accès `https://contoso.com/a` à des sous-chemins d’accès et des sous-chemins tels que `https://contoso.com/a/b`|
|

## <a name="warning-pages-from-safe-links"></a>Pages d’avertissement provenant de liens sécurisés

Cette section contient des exemples des différentes pages d’avertissement déclenchées par la protection contre les liens sécurisés lorsque vous cliquez sur une URL.

Notez que plusieurs pages d’avertissement ont été mises à jour. Si vous ne voyez pas déjà les pages mises à jour, vous allez bientôt le faire. Les pages mises à jour incluent un nouveau modèle de couleurs, plus de détails et la possibilité de passer à un site malgré l’avertissement et les recommandations donnés.

### <a name="scan-in-progress-notification"></a>Notification d’analyse en cours

L’URL sur le clic est analysée par des liens sécurisés. Vous devrez peut-être patienter quelques instants avant d’essayer à nouveau le lien.

![Notification « Le lien est en cours d’analyse »](../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png)

La page de notification d’origine ressemble à ceci :

![Notification d’origine « Le lien est en cours d’analyse »](../../media/04368763-763f-43d6-94a4-a48291d36893.png)

### <a name="suspicious-message-warning"></a>Avertissement de message suspect

L’URL cliquée se trouvait dans un message électronique semblable à d’autres messages suspects. Nous vous recommandons de vérifier le message électronique avant de passer au site.

![Avertissement « Un lien a été cliqué à partir d’un message suspect »](../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png)

### <a name="phishing-attempt-warning"></a>Avertissement de tentative de hameçonnage

L’URL cliquée se trouvait dans un message électronique identifié comme une attaque par hameçonnage. Par conséquent, toutes les URL du message électronique sont bloquées. Nous vous recommandons de ne pas passer au site.

![Avertissement « Le lien a été cliqué à partir d’un message de hameçonnage »](../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png)

### <a name="malicious-website-warning"></a>Avertissement de site web malveillant

L’URL cliquée pointe vers un site qui a été identifié comme malveillant. Nous vous recommandons de ne pas passer au site.

![Avertissement « Ce site web est considéré comme malveillant »](../../media/058883c8-23f0-4672-9c1c-66b084796177.png)

La page d’avertissement d’origine ressemble à ceci :

![Avertissement « Ce site web a été classé comme malveillant » d’origine](../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png)

### <a name="blocked-url-warning"></a>Avertissement d’URL bloquée

L’URL cliquée a été bloquée manuellement par un administrateur de votre organisation (la liste Bloquer les URL suivantes dans les **paramètres** globaux de liens sécurisés). Le lien n’a pas été analysé par les liens sécurisés, car il a été bloqué manuellement.

Il existe plusieurs raisons pour lesquelles un administrateur bloque manuellement des URL spécifiques. Si vous pensez que le site ne doit pas être bloqué, contactez votre administrateur.

![Avertissement « Ce site web a été bloqué par votre administrateur »](../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png)

La page d’avertissement d’origine ressemble à ceci :

![Avertissement « Ce site web a été bloqué par la stratégie d’URL de votre organisation »](../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png)

### <a name="error-warning"></a>Avertissement d’erreur

Un type d’erreur s’est produit et l’URL ne peut pas être ouverte.

![Avertissement « Impossible de charger la page à qui vous essayez d’accéder »](../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png)

La page d’avertissement d’origine ressemble à ceci :

![Avertissement d’origine « Cette page web n’a pas pu être chargée »](../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png)
