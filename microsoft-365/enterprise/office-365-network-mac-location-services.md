---
title: Microsoft 365 Services de localisation de connectivité réseau
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 Services de localisation de connectivité réseau
ms.openlocfilehash: ed78d7ba48cd9666ce1aae1af5478e3b7536e1e1
ms.sourcegitcommit: fb6c5e04ade1e82b26b2f911577b5ac721f1c544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2021
ms.locfileid: "52470447"
---
# <a name="microsoft-365-network-connectivity-location-services"></a>Microsoft 365 Services de localisation de connectivité réseau

Le Microsoft 365 Admin Center affiche désormais **les recommandations** en matière de performances et d’informations réseau, qui sont des mesures de performances en direct collectées à partir de Microsoft 365 client. Ces mesures ne peuvent être vues que par les utilisateurs administratifs de votre client. La connectivité réseau organisationnelle est conçue par emplacement de bureau via un emplacement de sortie réseau vers Internet. Microsoft 365 client utilise cet itinéraire, puis via Internet vers les serveurs de porte du service Microsoft. L’identification des emplacements de bureau est essentielle pour pouvoir afficher ces informations réseau.

## <a name="location-in-network-measurements"></a>Emplacement dans les mesures réseau

L’administrateur d’une organisation peut choisir d’inclure l’emplacement dans les mesures réseau utilisées par cette fonctionnalité. Cela permet la découverte automatique de la ville où se trouve chaque bureau. Les informations d’emplacement ne sont pas précises et sont obscurcies à 300 m et classées par ville. Au moment où l’emplacement est capturé sur un Windows,  l’appareil affiche une icône Emplacement en cours d’utilisation dans la boîte à outils. Les administrateurs peuvent vouloir informer les utilisateurs de l’apparence de cette icône. Avec ce traitement, l’emplacement est traité comme l’emplacement du bureau de l’organisation et non comme l’emplacement d’une personne ou d’un appareil. Des informations réseau peuvent être affichées dans ces villes d’emplacements de bureau découvertes. Si vous souhaitez obtenir une meilleure précision dans les recommandations, vous pouvez entrer des adresses de bureau spécifiques. Les informations réseau seront regroupées à ces emplacements à la place. Office’emplacements ne peuvent pas être agrégés plus près de 300 mètres.

## <a name="location-in-the-microsoft-365-admin-center"></a>Emplacement dans le Centre d’administration Microsoft 365 de gestion

Dans le Microsoft 365 d’administration, Bing de carte sont utilisés pour afficher l’emplacement des bureaux de l’organisation. Les contrôles indiquent également la topologie de périmètre réseau pour un emplacement de bureau sélectionné. Lorsqu’un administrateur ajoute des détails d’adresse spécifiques pour les bureaux, Bing Cartes est également utilisé pour suggérer des adresses pour faciliter la saisie de données.

## <a name="terms-of-use"></a>Conditions d’utilisation

Tout contenu fourni par le biais Bing Cartes, y compris les géocodes, ne peut être utilisé que dans le produit par le biais duquel le contenu est fourni. L’utilisation par le client de la fonctionnalité des services de localisation du centre  d’administration Microsoft 365, optimisée par Bing Cartes, est régie par les conditions d’utilisation Bing Cartes End-User disponibles dans et la déclaration de confidentialité <https://go.microsoft.com/?linkid=9710837> De [Microsoft](https://go.microsoft.com/fwlink/?LinkID=248686).

Cette fonctionnalité, fournie via Bing Cartes, est également prise en charge par **TomTom**. Plus d’informations sur les produits et services de TomTom sont disponibles sur [https://www.tomtom.com/legal](https://www.tomtom.com/legal) .

## <a name="related-topics"></a>Voir aussi

[Connectivité réseau dans le Centre d’administration Microsoft 365 (prévisualisation)](office-365-network-mac-perf-overview.md)

[Microsoft 365 informations sur les performances du réseau (aperçu)](office-365-network-mac-perf-insights.md)

[Microsoft 365'évaluation réseau (prévisualisation)](office-365-network-mac-perf-score.md)

[Microsoft 365 test de connectivité dans le Centre d’administration Microsoft 365 (prévisualisation)](office-365-network-mac-perf-onboarding-tool.md)
