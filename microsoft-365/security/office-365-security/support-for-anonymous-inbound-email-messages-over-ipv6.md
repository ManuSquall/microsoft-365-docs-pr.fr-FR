---
title: Ajout de la prise en charge des messages entrants anonymes sur IPv6
f1.keywords:
- NOCSH
author: chrisda
ms.author: chrisda
manager: chrisda
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: b68df621-0a5f-4824-8abc-41e0c4fd1398
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: L’administrateur peut apprendre à configurer la prise en charge des messages électroniques entrants anonymes provenant de sources IPv6 dans Exchange Online et Exchange Online Protection.
ms.openlocfilehash: 7384c1044cc02ec20079dc03068c2ca99e68d2c2
ms.sourcegitcommit: e12fa502bc216f6083ef5666f693a04bb727d4df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46826776"
---
# <a name="add-support-for-anonymous-inbound-email-over-ipv6-in-microsoft-365"></a>Ajouter la prise en charge du courrier électronique entrant anonyme sur IPv6 dans Microsoft 365

Les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online et les organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online prennent en charge les messages électroniques entrants anonymes sur IPv6. Le serveur de messagerie IPv6 source doit respecter les deux conditions suivantes :

- L’adresse IPv6 source doit avoir un enregistrement DNS de recherche inversée (PTR) valide qui permet à la destination de trouver le nom de domaine à partir de l’adresse IPv6.

- L'expéditeur doit répondre aux exigences de l'étape de vérification SPF (définie dans le fichier [RFC 7208](https://tools.ietf.org/html/rfc7208)) ou de l'étape de [vérification DKIM](https://dkim.org/) (définie dans le fichier [RFC 6376](https://www.rfc-editor.org/rfc/rfc6376.txt)).

Pour que votre organisation puisse recevoir des messages électroniques entrants anonymes sur IPv6, un administrateur doit contacter le support Microsoft et lui demander. Pour obtenir des instructions sur l’ouverture d’une demande de support, voir [contacter le support pour les entreprises-aide de l’administrateur](../../admin/contact-support-for-business-products.md).

Une fois que la prise en charge des messages IPv6 entrants anonymes est activée dans votre organisation, le message passe par le filtre de messages normal fourni par le service.

## <a name="troubleshooting"></a>Résolution des problèmes

- Si le serveur de messagerie source ne dispose pas d’un enregistrement de recherche DNS inversée IPv6, les messages seront rejetés avec l’erreur suivante :

  > 450 4.7.25 Service indisponible, envoi de l’adresse IPv6 [2a01:111 : F200:2004 :: 240] doit avoir un enregistrement DNS inverse.

- Si l’expéditeur ne passe pas la validation SPF ou DKIM, les messages sont rejetés avec l’erreur suivante :

  > 450 4.7.26 Service indisponible, le message envoyé via IPv6 [2a01:111 : F200:2004 :: 240] doit transmettre la validation SPF ou DKIM.

- Si vous tentez de recevoir des messages IPv6 anonymes avant d’avoir choisi, le message sera rejeté avec l’erreur suivante :

  > 550 5.2.1 Service indisponible, [contoso.com] n’accepte pas le courrier électronique sur IPv6.

## <a name="related-topics"></a>Rubriques connexes

[Prise en charge de la validation des messages signés DKIM](support-for-validation-of-dkim-signed-messages.md)