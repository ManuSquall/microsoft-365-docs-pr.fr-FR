---
title: Configurer un connecteur pour archiver les données réseau Verizon dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver des SMS MMS et des données MMS à partir du réseau Verizon dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: c72f17c21439827cf0c00e32a427eb1d6fd0c20c
ms.sourcegitcommit: 50908a93554290ff1157b58d0a868a33e012513c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52821390"
---
# <a name="set-up-a-connector-to-archive-verizon-network-data"></a>Configurer un connecteur pour archiver les données réseau Verizon

Utilisez le connecteur TeleMessage dans le centre de conformité Microsoft 365 pour importer et archiver des données de service de messagerie courte (SMS) et mmS (Multimedia Messaging Service) à partir de Verizon Network. Après avoir configuré et configuré un connecteur, il se connecte au réseau Verizon de votre organisation une fois par jour et importe des données SMS et MMS dans des boîtes aux lettres dans Microsoft 365.

Une fois que les données du connecteur réseau Verizon sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention Microsoft 365 aux données Verizon. Par exemple, vous pouvez rechercher des messages Verizon SMS et MMS à l’aide de la recherche de contenu ou associer la boîte aux lettres qui contient les données réseau Verizon à un dépositaire dans un cas Advanced eDiscovery dossier. L’utilisation d’un connecteur réseau Verizon pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-verizon-network-data"></a>Vue d’ensemble de l’archivage des données réseau Verizon

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données du réseau Verizon dans Microsoft 365.

![Flux de travail d’archivage du réseau Verizon](../media/VerizonNetworkConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage et Verizon pour configurer un connecteur réseau Verizon. Pour plus d’informations, voir [Verizon Network Archiver](https://www.telemessage.com/office365-activation-for-verizon-network-archiver/).

2. Une fois toutes les 24 heures, SMS et MMS du réseau Verizon de votre organisation sont copiés sur le site TeleMessage.

3. Le connecteur réseau Verizon que vous créez dans le centre de conformité Microsoft 365 se connecte au site TeleMessage tous les jours et transfère les messages SMS et MMS des 24 heures précédentes vers un emplacement stockage Azure sécurisé dans le cloud Microsoft. Le connecteur convertit également le contenu des messages SMS mms au format de message électronique.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé **Verizon SMS/MMS Network Archiver** est créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y sont importés. Le connecteur fait ce mappage à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur. Chaque SMS mms contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message.

   Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur, vous pouvez également implémenter un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient le numéro de téléphone mobile et l’adresse Microsoft 365 courrier électronique correspondante pour les utilisateurs de votre organisation. Si vous activez à la fois le mappage utilisateur automatique et le mappage personnalisé, pour chaque élément Verizon, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide correspondant au numéro de téléphone mobile d’un utilisateur, le connecteur utilise les valeurs de la propriété d’adresse de messagerie de l’élément qu’il tente d’importer. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété d’adresse de messagerie de l’élément Verizon, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

Certaines des étapes d’implémentation requises pour archiver les données du réseau Verizon sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer un connecteur dans le centre de conformité.

- Commandez [le service Verizon Network Archiver à partir de TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) et obtenez un compte d’administration valide pour votre organisation. Vous devrez vous inscrire à ce compte lorsque vous créerez le connecteur dans le centre de conformité.

- Obtenez les détails de votre compte réseau Verizon et de votre contact de facturation pour pouvoir remplir les formulaires d’intégration TeleMessage et commander le service d’archivage des messages auprès de Verizon.

- Enregistrez tous les utilisateurs qui nécessitent l’archivage SMS Verizon et MMS dans le compte TeleMessage. Lors de l’inscription des utilisateurs, n’oubliez pas d’utiliser la même adresse de messagerie que celle utilisée pour Microsoft 365 compte.

- Vos employés doivent avoir des téléphones mobiles d’entreprise et de responsabilité d’entreprise sur le réseau mobile Verizon. L’archivage des messages Microsoft 365 n’est pas disponible pour les appareils BYOD (Bring Your Own Devices) ou d’employés.

- Le rôle Importation/Exportation de boîte aux lettres doit être attribué à l’utilisateur qui crée un connecteur réseau Verizon dans Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **Connecteurs** de données dans le centre Microsoft 365 conformité. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

- Ce connecteur de données est disponible dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 gouvernement américain. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui sont en dehors de l’infrastructure Microsoft 365 et qui, par conséquent, ne sont pas couverts par les engagements en matière de conformité et de protection des données Microsoft 365. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="create-a-verizon-network-connector"></a>Créer un connecteur réseau Verizon

Une fois que vous avez rempli les conditions préalables décrites dans la section précédente, vous pouvez créer un connecteur réseau Verizon dans le centre Microsoft 365 conformité. Le connecteur utilise les informations que vous fournissez pour vous connecter au site TeleMessage et transférer des messages SMS et MMS vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and then click Data **connectors**  >  **Verizon Network**.

2. Dans la page **description du produit Verizon Network,** cliquez sur Ajouter un **connecteur**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Dans la page **Connexion à TeleMessage,** sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.
  
   - **Nom d’utilisateur :** Votre nom d’utilisateur TeleMessage.

   - **Mot de passe :** Votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre pop-up et passer à la page suivante.

6. Dans la page **Mappage des utilisateurs,** activez le mappage utilisateur automatique et cliquez sur **Suivant**. Si vous avez besoin d’un mappage personnalisé, téléchargez un fichier CSV, puis cliquez sur **Suivant**.

7. Examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Go to the Connectors tab in **Data connectors** page to see the progress of the import process for the new connector.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.