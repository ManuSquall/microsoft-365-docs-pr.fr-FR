---
title: Comment SPF (Sender Policy Framework) empêche l’usurpation
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 12/15/2016
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 3aff33c5-1416-4867-a23b-e0c0c5b4d2be
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment Microsoft 365 utilise l’enregistrement TXT SPF (Sender Policy Framework) dans DNS pour s’assurer que les systèmes de messagerie de destination font confiance aux messages envoyés à partir de votre domaine personnalisé.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 972f283f6138bafcebd877a19f0bfc429e0eed03
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204190"
---
# <a name="how-microsoft-365-uses-sender-policy-framework-spf-to-prevent-spoofing"></a>Comment Microsoft 365 utilise SPF (Sender Policy Framework) pour éviter l’usurpation

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 **Résumé :** Cet article explique comment Microsoft 365 utilise l’enregistrement TXT SPF (Sender Policy Framework) dans DNS pour s’assurer que les systèmes de messagerie de destination font confiance aux messages envoyés à partir de votre domaine personnalisé. Cela s’applique aux messages sortants envoyés Microsoft 365. Les messages envoyés Microsoft 365 à un destinataire au sein Microsoft 365 passeront toujours SPF.

Un enregistrement TXT SPF est un enregistrement DNS qui permet d'éviter l' usurpation et le hameçonnage en vérifiant le nom du domaine à partir duquel les messages électroniques sont envoyés. SPF valide l'origine des messages électroniques en vérifiant l'adresse IP de l'expéditeur par rapport à celle du prétendu propriétaire du domaine d'expédition.

> [!NOTE]
> Les types d'enregistrement SPF ont été déconseillés par le groupe de travail IETF (Internet Engineering Task Force) en 2014. À la place, veillez à utiliser des enregistrements TXT dans le système DNS pour publier vos informations SPF. Le reste de cet article utilise le terme « enregistrement TXT SPF » pour plus de clarté.

Les administrateurs de domaine publient des informations SPF dans les enregistrements TXT au sein du système DNS. Les informations SPF identifient les serveurs de messagerie sortants autorisés. Les systèmes de messagerie électronique de destination vérifient que les messages proviennent de serveurs de messagerie sortants autorisés. Si vous êtes déjà familiarisé avec SPF, ou si vous avez un déploiement simple et que vous avez simplement besoin de savoir ce qu’il faut inclure dans votre enregistrement TXT SPF dans DNS pour Microsoft 365, vous pouvez passer à Configurer [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md)dans Microsoft 365 pour éviter l’usurpation. Si vous n’avez pas de déploiement entièrement hébergé dans Microsoft 365 ou si vous souhaitez plus d’informations sur le fonctionnement de SPF ou sur la résolution des problèmes de SPF pour Microsoft 365, continuez à lire.

> [!NOTE]
> Auparavant, vous deviez ajouter un autre enregistrement TXT SPF à votre domaine personnalisé si vous utilisiez également SharePoint Online. Cela n'est plus nécessaire. Ce changement doit réduire le risque que les messages de notification SharePoint Online terminent dans le dossier Courrier indésirable. Vous n’avez pas besoin d’apporter de modifications immédiatement, mais si vous recevez l’erreur « Trop de recherche », modifiez votre enregistrement TXT SPF comme décrit dans Configurer [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md)dans Microsoft 365 pour éviter l’usurpation.

## <a name="how-spf-works-to-prevent-spoofing-and-phishing-in-microsoft-365"></a>Fonctionnement de SPF pour empêcher l’usurpation et le hameçonnage dans Microsoft 365
<a name="HowSPFWorks"> </a>

SPF détermine si un expéditeur est autorisé à envoyer des messages au nom d'un domaine. Si l'expéditeur n'y est pas autorisé, autrement dit, si la vérification SPF du message électronique échoue sur le serveur de réception, la stratégie de courrier indésirable configurée sur ce serveur détermine l'action à entreprendre avec le message.

Chaque enregistrement TXT SPF contient trois parties : la déclaration indiquant qu'il s'agit d'un enregistrement TXT SPF, les adresses IP qui sont autorisées à envoyer des messages à partir de votre domaine et les domaines externes pouvant envoyer des messages au nom de votre domaine, ainsi qu'une règle de mise en œuvre. Ces trois éléments sont obligatoires pour un enregistrement TXT SPF valide. Cet article décrit la façon dont vous formez votre enregistrement TXT SPF et fournit les meilleures pratiques pour l’Microsoft 365. Des liens vers des instructions sur l’utilisation de votre bureau d’enregistrement de domaine pour publier votre enregistrement dans DNS sont également disponibles.

### <a name="spf-basics-ip-addresses-allowed-to-send-from-your-custom-domain"></a>Concepts de base SPF : adresses IP autorisées à envoyer des messages à partir de votre domaine personnalisé
<a name="SPFBasicsIPaddresses"> </a>

Examinez la syntaxe de base pour une règle SPF :

v=spf1 \<IP\>\<enforcement rule\>

Par exemple, supposons que la règle SPF suivante existe pour contoso.com :

v=spf1 \<IP address #1\> \<IP address #2\> \<IP address #3\>\<enforcement rule\>

Dans cet exemple, la règle SPF demande au serveur de messagerie de réception d'accepter uniquement les messages provenant de ces adresses IP pour le domaine contoso.com :

- Adresse IP 1

- Adresse IP 2

- Adresse IP 3

Cette règle SPF indique au serveur de messagerie de réception que si un message provient de contoso.com, mais pas de l'une de ces trois adresses IP, le serveur de réception doit appliquer la règle de mise en œuvre au message. La règle de mise en œuvre est généralement l'une des options suivantes :

- **Échec sévère.** Marquez « échec sévère » dans l'enveloppe du message, puis suivez la stratégie de courrier indésirable configurée du serveur de réception pour ce type de message.

- **Échec partiel.** Marquez « échec partiel » dans l'enveloppe du message. En règle générale, les serveurs de messagerie sont configurés pour remettre ce type de message. La plupart des utilisateurs finaux ne voient pas cette marque.

- **Neutre.** Ne faites rien, autrement dit, ne marquez pas l'enveloppe du message. Cette marque est généralement réservée à des fins de test et est rarement utilisée.

Les exemples suivants montrent comment SPF fonctionne dans plusieurs situations différentes. Dans ces exemples, contoso.com est l’expéditeur et woodgrovebank.com est le destinataire.

### <a name="example-1-email-authentication-of-a-message-sent-directly-from-sender-to-receiver"></a>Exemple 1 : authentification de messagerie d’un message envoyé directement de l’expéditeur au destinataire
<a name="spfExample1"> </a>

SPF fonctionne de manière optimale lorsque le chemin entre l'expéditeur et le destinataire est direct, par exemple :

![Diagramme illustrant comment SPF authentifie le courrier électronique lorsqu'il est envoyé directement d'un serveur à l'autre.](../../media/835c20a7-ed4c-49c4-91fe-b8ebb3e452a1.jpg)

Quand woodgrovebank.com reçoit le message, si l'adresse IP 1 se trouve dans l'enregistrement TXT SPF pour contoso.com, le message passe la vérification SPF et est authentifié.

### <a name="example-2-spoofed-sender-address-fails-the-spf-check"></a>Exemple 2 : l’adresse d’expéditeur falsifiée ne passe pas la vérification SPF
<a name="spfExample2"> </a>

Supposons qu'un auteur de hameçonnage trouve un moyen d'usurper contoso.com :

![Diagramme illustrant la façon dont SPF authentifie le courrier électronique envoyé à partir d'un serveur falsifié.](../../media/235dac3d-cdc5-466e-86e0-37b5979de198.jpg)

Étant donné que l'adresse IP 12 n'est pas dans l'enregistrement TXT SPF de contoso.com, le message ne passe pas la vérification SPF et le destinataire peut choisir de le marquer comme courrier indésirable.

### <a name="example-3-spf-and-forwarded-messages"></a>Exemple 3 : messages transférés et SPF
<a name="spfExample3"> </a>

SPF présente un désavantage qui réside dans le fait qu'il ne fonctionne pas lorsqu'un message électronique a été transféré. Par exemple, supposons que l'utilisateur woodgrovebank.com a défini une règle de transfert pour envoyer tous les messages électroniques vers un compte outlook.com :

![Diagramme indiquant comment SPF ne peut pas authentifier le courrier électronique lorsque le message est transféré.](../../media/6e92acd6-463e-4a1b-8327-fb1cf861f356.jpg)

Le message passe d'abord la vérification SPF sur woodgrovebank.com mais il échoue lors de la vérification SPF sur outlook.com, car l'adresse IP 25 ne figure pas dans l'enregistrement TXT SPF de contoso.com. Outlook.com peut ensuite marquer le message comme courrier indésirable. Pour contourner ce problème, utilisez SPF avec d'autres méthodes d'authentification de courrier électronique, comme DKIM et DMARC.

### <a name="spf-basics-including-third-party-domains-that-can-send-mail-on-behalf-of-your-domain"></a>Concepts de base SPF : intégration de domaines tiers pouvant envoyer des messages au nom de votre domaine
<a name="SPFBasicsIncludes"> </a>

En plus des adresses IP, vous pouvez également configurer votre enregistrement TXT SPF pour inclure des domaines en tant qu'expéditeurs. Ces domaines sont ajoutés à l'enregistrement TXT SPF comme des instructions « Include ». Par exemple, contoso.com souhaite peut-être inclure toutes les adresses IP des serveurs de messagerie à partir de contoso.net et de contoso.org qu'il possède également. Pour ce faire, contoso.com publie un enregistrement TXT SPF qui ressemble à ceci :

```text
v=spf1 include:contoso.net include:contoso.org -all
```

Lorsque le serveur de réception voit cet enregistrement dans le DNS, il effectue également une recherche DNS sur l’enregistrement TXT SPF pour contoso.net puis pour contoso.org. S’il trouve une instruction Include supplémentaire dans les enregistrements pour contoso.net ou contoso.org, elle suivra également ces instructions. Afin d’empêcher le refus d’attaque de service, le nombre maximal de recherches DNS pour un seul message est de 10. Chaque instruction Include représente une recherche DNS supplémentaire. Si un message dépasse la limite de 10, le message échoue lors de la vérification SPF. Une fois qu’un message atteint cette limite, en fonction de la façon dont le serveur de réception est configuré, l’expéditeur peut obtenir un message qui indique que le message a généré « trop de recherches » ou que le « nombre maximal de sauts pour le message a été dépassé » (ce qui peut se produire lorsque les recherches bouclent et dépassent le délai d’attente DNS). Pour obtenir des conseils sur la façon d’éviter cela, voir Résolution des problèmes : Meilleures pratiques [pour SPF dans Microsoft 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="requirements-for-your-spf-txt-record-and-microsoft-365"></a>Conditions requises pour votre enregistrement TXT SPF et votre Microsoft 365
<a name="SPFReqsinO365"> </a>

Si vous avez installé le courrier lors de la Microsoft 365, vous avez déjà créé un enregistrement TXT SPF qui identifie les serveurs de messagerie Microsoft comme source légitime de courrier pour votre domaine. Cet enregistrement ressemble probablement à ce qui suit :

```text
v=spf1 include:spf.protection.outlook.com -all
```

Si vous êtes un client entièrement hébergé, c’est-à-dire que vous n’avez aucun serveur de messagerie local qui envoie du courrier sortant, il s’agit du seul enregistrement TXT SPF que vous devez publier pour Office 365.

Si vous avez un déploiement hybride (c’est-à-dire que vous avez certaines boîtes aux lettres en local et d’autres hébergées dans Microsoft 365), ou si vous êtes un client autonome Exchange Online Protection (EOP) (autrement dit, si votre organisation utilise EOP pour protéger vos boîtes aux lettres sur site), vous devez ajouter l’adresse IP sortante de chacun de vos serveurs de messagerie Edge locaux à l’enregistrement TXT SPF dans DNS.

## <a name="form-your-spf-txt-record-for-microsoft-365"></a>Form your SPF TXT record for Microsoft 365
<a name="FormYourSPF"> </a>

Utilisez les informations de syntaxe de cet article afin de formuler l'enregistrement TXT SPF pour votre domaine personnalisé. Bien qu'il existe des options de syntaxe qui ne sont pas mentionnées ici, il s'agit des options les plus fréquemment utilisées. Une fois que vous avez formulé votre enregistrement, vous devez le mettre à jour auprès de votre bureau d'enregistrement de domaine.

Pour plus d’informations sur les domaines que vous devrez inclure pour Microsoft 365, voir enregistrements [DNS](../../enterprise/external-domain-name-system-records.md)externes requis pour SPF . Utilisez les [instructions pas à pas](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md#add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online) pour mettre à jour les enregistrements SPF (TXT) dans votre bureau d'enregistrement de domaines.

### <a name="spf-txt-record-syntax-for-microsoft-365"></a>Syntaxe d’enregistrement TXT SPF pour Microsoft 365
<a name="SPFSyntaxO365"> </a>

Un enregistrement TXT SPF classique pour Microsoft 365 a la syntaxe suivante :

```text
v=spf1 [<ip4>|<ip6>:<IP address>] [include:<domain name>] <enforcement rule>
```

Par exemple :

```text
v=spf1 ip4:192.168.0.1 ip4:192.168.0.2 include:spf.protection.outlook.com -all
```

où :

- **v=spf1** est obligatoire. Cet élément définit l'enregistrement TXT en tant qu'enregistrement TXT SPF.

- **IP4** indique que vous utilisez des adresses IP de version 4. **ip6** indique que vous utilisez des adresses IP de version 6. Si vous utilisez des adresses IP IPv6, remplacez **ip4** par **ip6** dans les exemples de cet article. Vous pouvez également spécifier des plages d'adresses IP à l'aide de la notation CIDR, par exemple **ip4:192.168.0.1/26**.

- _IP address_ est l'adresse IP à ajouter à l'enregistrement TXT SPF. En règle générale, il s'agit de l'adresse IP du serveur de messagerie sortant pour votre organisation. Vous pouvez répertorier plusieurs serveurs de messagerie sortants. Pour plus d’informations, voir l’exemple : enregistrement [TXT SPF](how-office-365-uses-spf-to-prevent-spoofing.md#ExampleSPFMultipleMailServerO365)pour plusieurs serveurs de messagerie locaux et serveurs de messagerie Microsoft 365 .

- _domain name_ est le domaine que vous souhaitez ajouter en tant qu'expéditeur légitime. Pour obtenir la liste des noms de domaine que vous devez Microsoft 365, voir [enregistrements DNS externes requis pour SPF.](../../enterprise/external-domain-name-system-records.md)

- La règle de mise en œuvre est généralement l'une des règles suivantes :

  - -all

    Indique un échec sévère. Si vous connaissez toutes les adresses IP autorisées pour votre domaine, répertoriez-les dans l'enregistrement TXT SPF et utilisez le qualificateur -all (échec sévère). En outre, si vous utilisez uniquement SPF, c'est-à-dire que vous n'utilisez pas DMARC ou DKIM, vous devez utiliser le qualificateur -all. Nous vous recommandons de toujours utiliser ce qualificateur.

  - ~all

    Indique un échec partiel. Si vous n'êtes pas sûr de disposer de la liste complète des adresses IP, utilisez le qualificateur ~all (échec partiel). En outre, si vous utilisez DMARC avec p=quarantine ou p=reject, vous pouvez utiliser ~all. Dans le cas contraire, utilisez -all.

  - ?all

    Indique un résultat neutre. Il est utilisé lors des essais SPF. Nous vous déconseillons d'utiliser ce qualificatif dans votre déploiement.

### <a name="example-spf-txt-record-to-use-when-all-of-your-mail-is-sent-by-microsoft-365"></a>Exemple : enregistrement TXT SPF à utiliser lorsque tous vos messages sont envoyés par Microsoft 365
<a name="ExampleSPFNoSP"> </a>

Si tous vos messages sont envoyés par Microsoft 365, utilisez-le dans votre enregistrement TXT SPF :

```text
v=spf1 include:spf.protection.outlook.com -all
```

### <a name="example-spf-txt-record-for-a-hybrid-scenario-with-one-on-premises-exchange-server-and-microsoft-365"></a>Exemple : enregistrement TXT SPF pour un scénario hybride avec une Exchange Server et une Microsoft 365
<a name="ExampleSPFHybridOneExchangeServer"> </a>

Dans un environnement hybride, si l'adresse IP du serveur Exchange local est 192.168.0.1, afin de définir la règle de mise en œuvre SPF sur échec sévère, formez l'enregistrement TXT SPF comme suit :

```text
v=spf1 ip4:192.168.0.1 include:spf.protection.outlook.com -all
```

### <a name="example-spf-txt-record-for-multiple-outbound-on-premises-mail-servers-and-microsoft-365"></a>Exemple : enregistrement TXT SPF pour plusieurs serveurs de messagerie locaux sortants et Microsoft 365
<a name="ExampleSPFMultipleMailServerO365"> </a>

Si vous avez plusieurs serveurs de messagerie sortants, ajoutez l'adresse IP de chaque serveur de messagerie dans l'enregistrement TXT SPF et séparez chaque adresse IP par un espace suivi par une instruction « ip4: ». Par exemple :

```text
v=spf1 ip4:192.168.0.1 ip4:192.168.0.2 ip4:192.168.0.3 include:spf.protection.outlook.com -all
```

## <a name="next-steps-set-up-spf-for-microsoft-365"></a>Étapes suivantes : Configurer SPF pour Microsoft 365
<a name="SPFNextSteps"> </a>

Une fois que vous avez formulé votre enregistrement TXT SPF, suivez les étapes de la procédure de la procédure Set [up SPF dans Microsoft 365](set-up-spf-in-office-365-to-help-prevent-spoofing.md) pour empêcher l’usurpation pour l’ajouter à votre domaine.

Bien que SPF soit conçu pour éviter l'usurpation, il existe des techniques d'usurpation contre lesquelles SPF ne peut pas vous protéger. Pour vous protéger contre ces problèmes, une fois que vous avez configuré SPF, vous devez également configurer DKIM et DMARC pour Microsoft 365. To get started, see [Use DKIM to validate outbound email sent from your custom domain in Microsoft 365](use-dkim-to-validate-outbound-email.md). Ensuite, consultez la rubrique [Utiliser DMARC pour valider les e-mails dans Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="troubleshooting-best-practices-for-spf-in-microsoft-365"></a>Résolution des problèmes : meilleures pratiques pour SPF dans Microsoft 365
<a name="SPFTroubleshoot"> </a>

Vous ne pouvez créer qu'un seul enregistrement TXT SPF pour votre domaine personnalisé. La création de plusieurs enregistrements entraîne une situation alternée et l'échec de SPF. Pour éviter cela, vous pouvez créer des enregistrements distincts pour chaque sous-domaine. Par exemple, créez un enregistrement pour contoso.com et un autre enregistrement pour bulkmail.contoso.com.

Si un message électronique provoque plus de 10 recherches DNS avant sa livraison, le serveur de messagerie de réception répond avec une erreur permanente, également appelée  _permerror_, et génère l'échec du message lors de la vérification SPF. Le serveur de réception peut également répondre avec une notification d'échec de remise qui contient une erreur semblable à celles-ci :

- Le message a dépassé le nombre de sauts.

- Le message a demandé trop de recherches.

## <a name="avoiding-the-too-many-lookups-error-when-you-use-third-party-domains-with-microsoft-365"></a>Éviter l’erreur « Trop de recherche » lorsque vous utilisez des domaines tiers avec Microsoft 365
<a name="SPFTroubleshoot"> </a>

Certains enregistrements TXT SPF pour les domaines tiers indiquent au serveur de réception d'effectuer un nombre élevé de recherches DNS. Par exemple, au moment de la rédaction, Salesforce.com contient 5 instructions Include dans son enregistrement :

```text
v=spf1 include:_spf.google.com
include:_spfblock.salesforce.com
include:_qa.salesforce.com
include:_spfblock1.salesforce.com
include:spf.mandrillapp.com mx ~all
```

Pour éviter l'erreur, vous pouvez implémenter une stratégie selon laquelle toute personne envoyant des messages électroniques en bloc, par exemple, doit utiliser un sous-domaine spécialement à cette fin. Ensuite, définissez un autre enregistrement TXT SPF pour le sous-domaine comprenant la messagerie électronique en bloc.

 Dans certains cas, comme dans l'exemple salesforce.com, vous devez utiliser le domaine dans votre enregistrement TXT SPF, mais dans d'autres cas, le domaine tiers a peut-être déjà créé un sous-domaine pour votre utilisation. Par exemple, exacttarget.com a créé un sous-domaine que vous devez utiliser pour votre enregistrement TXT SPF :

```text
cust-spf.exacttarget.com
```

Lorsque vous incluez des domaines tiers dans votre enregistrement TXT SPF, vous devez vérifier auprès du tiers le domaine ou le sous-domaine à utiliser pour éviter d'atteindre la limite de 10 recherches.

## <a name="how-to-view-your-current-spf-txt-record-and-determine-the-number-of-lookups-that-it-requires"></a>Comment afficher votre enregistrement TXT SPF et déterminer le nombre de recherches nécessaires
<a name="SPFTroubleshoot"> </a>

Vous pouvez utiliser nslookup pour afficher vos enregistrements DNS, y compris votre enregistrement TXT SPF. Sinon, si vous préférez, il existe plusieurs outils gratuits en ligne que vous pouvez utiliser pour afficher le contenu de votre enregistrement TXT SPF. En consultant votre enregistrement TXT SPF et en suivant la chaîne d'instructions Include et de redirections, vous pouvez déterminer le nombre de recherches DNS dont l'enregistrement a besoin. Certains outils en ligne peuvent même compter et afficher ces recherches pour vous. Le fait d'assurer le suivi de cette donnée permettra d'éviter que les messages envoyés depuis votre organisation ne déclenchent une erreur permanente, appelée permerror, sur le serveur de réception.

## <a name="for-more-information"></a>Pour plus d'informations
<a name="SPFTroubleshoot"> </a>

Besoin d'aide pour ajouter l'enregistrement TXT SPF ? Lisez l’article Créer des enregistrements DNS auprès d’un fournisseur d’hébergement [DNS](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md#add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online) pour Microsoft 365 pour plus d’informations sur l’utilisation de Sender Policy Framework avec votre domaine personnalisé dans Microsoft 365. [Les en-têtes de message anti-courrier](anti-spam-message-headers.md) indésirable incluent la syntaxe et les champs d’en-tête utilisés Microsoft 365 pour les vérifications SPF.
