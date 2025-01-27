---
title: Préparation de TLS 1.2 dans Office 365 et Office 365 GCC
description: Comment préparer l’utilisation de TLS 1.2 pour toutes les combinaisons client-serveur et navigateur-serveur dans Office 365 et Office 365 GCC après la désactivation de la prise en charge de TLS 1.0 et 1.1.
author: kccross
manager: laurawi
localization_priority: Normal
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: shmehta
ms.reviewer: krowley
appliesto:
- Office 365 Business
ms.openlocfilehash: 331dd1ea510983e57c069f8d142aa0f7d3f7062e
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53226082"
---
# <a name="preparing-for-tls-12-in-office-365-and-office-365-gcc"></a>Préparation de TLS 1.2 dans Office 365 et Office 365 GCC

## <a name="summary"></a>Résumé

Afin d’offrir à ses clients le meilleur chiffrement possible, Microsoft envisage de déclasser les versions 1.0 et 1.1 de Transport Layer Security (TLS) dans Office 365 et Office 365 GCC. Nous savons que la sécurité de vos données est importante et nous nous engageons à assurer la transparence des modifications susceptibles d’affecter votre utilisation du service TLS.

L’[implémentation du service TLS 1.0 de Microsoft](https://support.microsoft.com/help/3117336/schannel-implementation-of-tls-1-0-in-windows-security-status-update-n) ne comporte aucune vulnérabilité de sécurité connue. Toutefois, en raison de la possibilité d’attaques par rétrogradation de protocole et d’autres vulnérabilités TLS dans le futur, nous interrompons la prise en charge de TLS 1.0 et 1.1 dans Microsoft Office 365 et Office 365 GCC.

Pour plus d’informations sur la marche à suivre pour supprimer les dépendances TLS 1.0 et 1.1, consultez le livre blanc suivant : [Solving the TLS 1.0 problem](https://www.microsoft.com/download/details.aspx?id=55266) (en anglais uniquement).

## <a name="more-information"></a>Informations supplémentaires

Nous avons déjà commencé la dépréciation des versions 1.0 et 1.1 de TLS en janvier 2020. Tous les clients, appareils ou services qui se connectent à Office 365 via les protocoles TLS 1.0 ou 1.1 dans nos instances DoD ou GCC High ne seront pas pris en charge. Pour nos clients commerciaux de Office 365, l’annulation de TLS 1.0 et 1.1 commence le 15 octobre 2020 et le déploiement se poursuit au cours des semaines et des mois suivants. 

Assurez-vous que toutes les combinaisons client-serveur et navigateur-serveur utilisent le protocole TLS 1.2 (ou une version plus récente) pour maintenir la connexion aux services Office 365. Il se peut que vous deviez procéder à la mise à jour de certaines combinaisons client-serveur et navigateur-serveur.

Vous devez mettre à jour les applications qui appellent Microsoft 365 API sur TLS 1.0 ou TLS 1.1 pour utiliser TLS 1.2. Par défaut, .NET 4.5 est TLS 1.1. Pour mettre à jour votre configuration .NET, voir [Comment activer TLS (Transport Layer Security) 1.2 sur les clients.](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client)

Les clients suivants ne peuvent pas utiliser TLS 1.2. Mettez à jour vos clients pour garantir un accès illimité au service.

- Android 4.3 et versions antérieures
- Firefox 5.0 et versions antérieures
- Internet Explorer 8 à 10 dans Windows 7 et versions antérieures
- Internet Explorer 10 sur Windows Phone 8
- Safari 6.0.4/OS X10.8.4 et versions antérieures

### <a name="tls-12-for-microsoft-teams-rooms-and-surface-hub"></a>TLS 1.2 pour Salles Microsoft Teams et Surface Hub

Salles Microsoft Teams (précédemment connu sous le nom de Systèmes Skype Room V2 SRS V2) prend en charge le protocole TLS 1.2 depuis décembre 2018. Nous recommandons l’installation de la version 4.0.64.0 ou d’une version plus récente sur les appareils qui utilisent Salles Microsoft Teams. Pour plus d’informations, consultez les [notes de publication](/microsoftteams/room-systems/srs2-release-note). Les modifications sont à compatibilité descendante et ascendante.

Surface Hub a débuté la prise en charge du protocole TLS 1.2 en mai 2019.

La prise en charge de TLS 1.2 pour les produits Salles Microsoft Teams et Surface Hub nécessite également les changements de code côté serveur suivants :

- Les modifiées apportées à Skype Entreprise Online Server ont été effectuées de manière dynamique en avril 2019. Désormais, Skype Entreprise Online prend en charge la connexion des appareils pour Salles Microsoft Teams et pour Surface Hub avec le protocole TLS 1.2.
- Les clients Skype Entreprise Server doivent installer une mise à jour cumulative (CU) pour utiliser TLS 1.2 pour Salles Teams et Surface Hub.

  - Pour Skype Entreprise Server 2015, la mise à jour cumultative CU9 est déjà disponible depuis mai 2019.
  - Pour Skype Entreprise Server 2019, la mise à jour cumulative 1 était initialement prévue pour avril 2019, mais a été reportée au mois de juin 2019.

  > [!NOTE]
  > Les clients locaux de Skype Entreprise ne doivent pas désactiver TLS 1.0/1.1 avant d’installer des mises à jour cumulatives spécifiques pour Skype Entreprise Server.

Si vous utilisez une infrastructure sur site pour des scénarios hybrides ou les services ADFS (Active Directory Federation Services), assurez-vous que l’infrastructure peut prendre en charge les connexions entrantes et sortantes qui utilisent TLS 1.2.

## <a name="references"></a>Références

Les ressources suivantes fournissent des conseils pour vous assurer que vos clients utilisent TLS 1.2 ou une version ultérieure et pour désactiver TLS 1.0 et 1.1.

- Pour les clients Windows 7 qui se connectent à Office 365, assurez-vous que TLS 1.2 est le protocole sécurisé défini par défaut dans WinHTTP sous Windows. Pour plus d’informations, accédez à [KB 3140245 - Mise à jour pour activer TLS 1.1 et TLS 1.2 en tant que protocoles sécurisés par défaut dans WinHTTP sous Windows](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in).
- [Suites de chiffrement TLS pris en charge par Office 365](/microsoft-365/compliance/technical-reference-details-about-encryption#tls-cipher-suites-supported-by-office-365)
- Pour résoudre les problèmes de faible utilisation de TLS en supprimant les dépendances TLS 1.0 et 1.1, accédez à [Prise en charge de TLS 1.2 sous Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- [La nouvelle fonctionnalité IIS](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) facilite la recherche de clients sur [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) et [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334) qui se connectent au service en utilisant des protocoles de sécurité faibles.
- Obtenez plus d’informations sur la résolution du problème [TLS 1.0.](https://www.microsoft.com/download/details.aspx?id=55266)
- Pour plus d’informations sur notre approche de la sécurité, accédez au [Centre de gestion de la confidentialité d'Office 365](https://www.microsoft.com/trustcenter/cloudservices/office365).
- [Preparing for TLS 1.0/1.1 Deprecation - Office 365 Skype for Business](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247) (en anglais uniquement)
- [Exchange Server TLS guidance, part 1: Getting Ready for TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649) (en anglais uniquement)
- [Directives concernant le protocole TLS dans Exchange Server, Partie 2 : Enabling TLS 1.2 and Identifying Clients Not Using It](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761) (en anglais uniquement)
- [Directives concernant le protocole TLS dans Exchange Server, Partie 3 : Désactivation de TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Activation de la prise en charge de TLS 1.1 et TLS 1.2 dans Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
