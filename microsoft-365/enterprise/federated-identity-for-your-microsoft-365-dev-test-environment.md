---
title: Identité fédérée pour votre environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: 'Résumé : Configurez l’authentification fédérée pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: c7ff838522c0bd97da4ffff5122454b128f97bf2
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690157"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a><span data-ttu-id="22729-103">Identité fédérée pour votre environnement de test Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="22729-103">Federated identity for your Microsoft 365 test environment</span></span>

<span data-ttu-id="22729-104">*Ce guide de laboratoire de test peut être utilisé pour les environnements de test Microsoft 365 pour les environnements de test d’entreprise et Office 365.*</span><span class="sxs-lookup"><span data-stu-id="22729-104">*This Test Lab Guide can be used for both Microsoft 365 for enterprise and Office 365 Enterprise test environments.*</span></span>

<span data-ttu-id="22729-p101">Microsoft 365 prend en charge l’identité fédérée. Cela signifie qu’au lieu d’effectuer la validation des informations d’identification, Microsoft 365 renvoie l’utilisateur qui se connecte à un serveur d’authentification fédérée approuvé par Microsoft 365. Si les informations d’identification de l’utilisateur sont correctes, le serveur d’authentification fédérée émet un jeton de sécurité que le client envoie ensuite à Microsoft 365 comme preuve d’authentification. L’identité fédérée autorise le déchargement et la montée en charge de l’authentification pour un abonnement Microsoft 365, ainsi que l’authentification avancée et les scénarios de sécurité.</span><span class="sxs-lookup"><span data-stu-id="22729-p101">Microsoft 365 supports federated identity. This means that instead of performing the validation of credentials itself, Microsoft 365 refers the connecting user to a federated authentication server that Microsoft 365 trusts. If the user's credentials are correct, the federated authentication server issues a security token that the client then sends to Microsoft 365 as proof of authentication. Federated identity allows for the offloading and scaling up of authentication for a Microsoft 365 subscription and advanced authentication and security scenarios.</span></span>
  
<span data-ttu-id="22729-109">Cet article explique comment configurer l’authentification fédérée pour votre environnement de test Microsoft 365, en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="22729-109">This article describes how you can configure federated authentication for your Microsoft 365 test environment, resulting in the following:</span></span>

![L’authentification fédérée pour l’environnement de test Microsoft 365](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
<span data-ttu-id="22729-111">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="22729-111">This configuration consists of:</span></span> 
  
- <span data-ttu-id="22729-112">Un abonnement à la version d’évaluation ou de production de Microsoft 365 E5.</span><span class="sxs-lookup"><span data-stu-id="22729-112">A Microsoft 365 E5 trial or production subscription.</span></span>
    
- <span data-ttu-id="22729-113">Un intranet d’organisation simplifié et connecté à Internet, composé de cinq machines virtuelles sur un sous-réseau d’un réseau virtuel Azure (DC1, APP1, CLIENT1, ADFS1 et PROXY1).</span><span class="sxs-lookup"><span data-stu-id="22729-113">A simplified organization intranet connected to the Internet, consisting of five virtual machines on a subnet of an Azure virtual network (DC1, APP1, CLIENT1, ADFS1, and PROXY1).</span></span> <span data-ttu-id="22729-114">Azure AD Connect s’exécute sur APP1 pour synchroniser la liste des comptes dans le domaine des services de domaine Active Directory avec Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="22729-114">Azure AD Connect runs on APP1 to synchronize the list of accounts in the Active Directory Domain Services domain to Microsoft 365.</span></span> <span data-ttu-id="22729-115">PROXY1 reçoit les demandes d’authentification entrantes.</span><span class="sxs-lookup"><span data-stu-id="22729-115">PROXY1 receives the incoming authentication requests.</span></span> <span data-ttu-id="22729-116">ADFS1 valide les informations d’identification avec DC1 et émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="22729-116">ADFS1 validates credentials with DC1 and issues security tokens.</span></span>
    
<span data-ttu-id="22729-117">Les cinq phases de configuration de cet environnement de test sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="22729-117">There are five phases to setting up this test environment:</span></span>
  
1. <span data-ttu-id="22729-118">Création de l’environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="22729-118">Create the simulated enterprise test environment with password hash synchronization.</span></span>
    
2. <span data-ttu-id="22729-119">Créez le serveur AD FS (ADFS1).</span><span class="sxs-lookup"><span data-stu-id="22729-119">Create the AD FS server (ADFS1).</span></span>
    
3. <span data-ttu-id="22729-120">Créez le serveur proxy web (PROXY1).</span><span class="sxs-lookup"><span data-stu-id="22729-120">Create the web proxy server (PROXY1).</span></span>
    
4. <span data-ttu-id="22729-121">Créez un certificat auto-signé et configurez ADFS1 et PROXY1.</span><span class="sxs-lookup"><span data-stu-id="22729-121">Create a self-signed certificate and configure ADFS1 and PROXY1.</span></span>
    
5. <span data-ttu-id="22729-122">Configurez Microsoft 365 pour l’identité fédérée.</span><span class="sxs-lookup"><span data-stu-id="22729-122">Configure Microsoft 365 for federated identity.</span></span>
    
> [!NOTE]
> <span data-ttu-id="22729-123">Vous ne pouvez pas configurer cet environnement de test avec un abonnement à la version d’évaluation d’Azure.</span><span class="sxs-lookup"><span data-stu-id="22729-123">You cannot configure this test environment with an Azure Trial subscription.</span></span> 
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a><span data-ttu-id="22729-124">Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="22729-124">Phase 1: Configure password hash synchronization for your Microsoft 365 test environment</span></span>

<span data-ttu-id="22729-p103">Suivez les instructions fournies dans l’article [Synchronisation de hachage de mot de passe pour Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Voici la configuration que vous obtenez.</span><span class="sxs-lookup"><span data-stu-id="22729-p103">Follow the instructions in [password hash synchronization for Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Here is your resulting configuration.</span></span>
  
![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
<span data-ttu-id="22729-128">Cette configuration se compose des éléments suivants : </span><span class="sxs-lookup"><span data-stu-id="22729-128">This configuration consists of:</span></span> 
  
- <span data-ttu-id="22729-129">Un abonnement d’évaluation ou payant Microsoft 365 E5.</span><span class="sxs-lookup"><span data-stu-id="22729-129">A Microsoft 365 E5 trial or paid subscriptions.</span></span>
- <span data-ttu-id="22729-130">Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.</span><span class="sxs-lookup"><span data-stu-id="22729-130">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span> <span data-ttu-id="22729-131">Azure AD Connect s’exécute sur APP1 pour synchroniser le domaine TESTLAB AD DS avec le client Azure AD de vos abonnements Microsoft 365 de manière périodique.</span><span class="sxs-lookup"><span data-stu-id="22729-131">Azure AD Connect runs on APP1 to synchronize the TESTLAB AD DS domain to the Azure AD tenant of your Microsoft 365 subscriptions periodically.</span></span>

## <a name="phase-2-create-the-ad-fs-server"></a><span data-ttu-id="22729-132">Phase 2 : Création du serveur AD FS</span><span class="sxs-lookup"><span data-stu-id="22729-132">Phase 2: Create the AD FS server</span></span>

<span data-ttu-id="22729-133">Un serveur AD FS fournit une authentification fédérée entre Microsoft 365 et les comptes dans le domaine corp.contoso.com hébergé sur DC1.</span><span class="sxs-lookup"><span data-stu-id="22729-133">An AD FS server provides federated authentication between Microsoft 365 and the accounts in the corp.contoso.com domain hosted on DC1.</span></span>
  
<span data-ttu-id="22729-134">Pour créer une machine virtuelle Azure pour ADFS1, indiquez le nom de votre abonnement et de votre groupe de ressources, ainsi que l’emplacement Azure de votre configuration de base, puis exécutez ces commandes à l’invite de commandes Azure PowerShell sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="22729-134">To create an Azure virtual machine for ADFS1, fill in the name of your subscription and the resource group and Azure location for your Base Configuration, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```powershell
$subscrName="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
Connect-AzAccount
Select-AzSubscription -SubscriptionName $subscrName
$staticIP="10.0.0.100"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="22729-135">Ensuite, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle ADFS1 à l’aide du nom de compte d’administrateur local ADFS1 et de votre mot de passe, puis ouvrez une invite de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22729-135">Next, use the [Azure portal](https://portal.azure.com) to connect to the ADFS1 virtual machine using the ADFS1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="22729-136">Pour vérifier la résolution du nom et la communication réseau entre ADFS1 et DC1, exécutez la commande **ping dc1.corp.contoso.com** et vérifiez qu’il y a quatre réponses.</span><span class="sxs-lookup"><span data-stu-id="22729-136">To check name resolution and network communication between ADFS1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="22729-137">Ensuite, associez la machine virtuelle ADFS1 au domaine CORP avec ces commandes à l’invite Windows PowerShell sur ADFS1.</span><span class="sxs-lookup"><span data-stu-id="22729-137">Next, join the ADFS1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on ADFS1.</span></span>
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="22729-138">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="22729-138">Here is your resulting configuration.</span></span>
  
![Le serveur AD FS ajouté à la synchronisation d’annuaire pour l’environnement de test Microsoft 365](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
## <a name="phase-3-create-the-web-proxy-server"></a><span data-ttu-id="22729-140">Phase 3 : création du serveur proxy web (PROXY1)</span><span class="sxs-lookup"><span data-stu-id="22729-140">Phase 3: Create the web proxy server</span></span>

<span data-ttu-id="22729-141">PROXY1 permet le traitement proxy des messages d’authentification entre les utilisateurs tentant de s’authentifier et ADFS1.</span><span class="sxs-lookup"><span data-stu-id="22729-141">PROXY1 provides proxying of authentication messages between users trying to authenticate and ADFS1.</span></span>
  
<span data-ttu-id="22729-142">Pour créer une machine virtuelle Azure pour PROXY1, indiquez le nom de votre groupe de ressources et l’emplacement Azure, puis exécutez ces commandes à l’invite de commande Azure PowerShell sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="22729-142">To create an Azure virtual machine for PROXY1, fill in the name of your resource group and Azure location, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
$staticIP="10.0.0.101"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="22729-143">Une adresse IP publique statique est affectée à PROXY1, car vous créez un enregistrement DNS public qui pointe vers celle-ci et elle ne doit pas être modifiée lorsque vous redémarrez la machine virtuelle PROXY1.</span><span class="sxs-lookup"><span data-stu-id="22729-143">PROXY1 is assigned a static public IP address because you will create a public DNS record that points to it and it must not change when you restart the PROXY1 virtual machine.</span></span> 
  
<span data-ttu-id="22729-p105">Ensuite, ajoutez une règle au groupe de sécurité réseau pour le sous-réseau CorpNet afin d’autoriser le trafic entrant non sollicité provenant d’Internet et allant vers l’adresse IP privée de PROXY1 et le port TCP 443. Exécutez ces commandes dans l’invite de commande Azure PowerShell sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="22729-p105">Next, add a rule to the network security group for the CorpNet subnet to allow unsolicited inbound traffic from the Internet to PROXY1's private IP address and TCP port 443. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

<span data-ttu-id="22729-146">Ensuite, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle PROXY1 à l’aide du nom de compte d’administrateur local PROXY1 et de votre mot de passe, puis ouvrez une invite de commande Windows PowerShell sur PROXY1.</span><span class="sxs-lookup"><span data-stu-id="22729-146">Next, use the [Azure portal](https://portal.azure.com) to connect to the PROXY1 virtual machine using the PROXY1 local administrator account name and password, and then open a Windows PowerShell command prompt on PROXY1.</span></span>
  
<span data-ttu-id="22729-147">Pour vérifier la résolution du nom et la communication réseau entre PROXY1 et DC1, exécutez la commande **ping dc1.corp.contoso.com** et vérifiez qu’il y a quatre réponses.</span><span class="sxs-lookup"><span data-stu-id="22729-147">To check name resolution and network communication between PROXY1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="22729-148">Ensuite, associez la machine virtuelle PROXY1 au domaine CORP avec ces commandes à l’invite Windows PowerShell sur PROXY1.</span><span class="sxs-lookup"><span data-stu-id="22729-148">Next, join the PROXY1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on PROXY1.</span></span>
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="22729-149">Affichez l’adresse IP publique de PROXY1 avec ces commandes Azure PowerShell sur votre ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="22729-149">Display the public IP address of PROXY1 with these Azure PowerShell commands on your local computer:</span></span>
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

<span data-ttu-id="22729-p106">Ensuite, utilisez votre fournisseur DNS public et créez un enregistrement A DNS public pour **fs.testlab.**\<your DNS domain name> qui renvoie l’adresse IP affichée par la commande **Write-Host**. **fs.testlab.**\<your DNS domain name> est désigné ci-après en tant que *nom de domaine complet du service FS (Federation Service)*.</span><span class="sxs-lookup"><span data-stu-id="22729-p106">Next, work with your public DNS provider and create a new public DNS A record for **fs.testlab.**\<your DNS domain name> that resolves to the IP address displayed by the **Write-Host** command. The **fs.testlab.**\<your DNS domain name> is hereafter referred to as the  *federation service FQDN*.</span></span>
  
<span data-ttu-id="22729-154">Ensuite, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle DC1 à l’aide des informations d’identification de CORP\\User1, puis exécutez les commandes suivantes à une invite de commande Windows PowerShell de niveau administrateur :</span><span class="sxs-lookup"><span data-stu-id="22729-154">Next, use the [Azure portal](https://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then run the following commands at an administrator-level Windows PowerShell command prompt:</span></span>
  
```powershell
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
<span data-ttu-id="22729-155">Ces commandes créent un enregistrement A DNS interne afin que les machines virtuelles sur le réseau virtuel Azure puissent résoudre le nom de domaine complet du service FS (Federation Service) sur l’adresse IP privée d’ADFS1.</span><span class="sxs-lookup"><span data-stu-id="22729-155">These commands create an internal DNS A record so that virtual machines on the Azure virtual network can resolve the internal federation FQDN to ADFS1's private IP address.</span></span>
  
<span data-ttu-id="22729-156">Voici la configuration finale.</span><span class="sxs-lookup"><span data-stu-id="22729-156">Here is your resulting configuration.</span></span>
  
![Le serveur proxy d’application web ajouté à la synchronisation d’annuaire pour l’environnement de test Microsoft 365](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a><span data-ttu-id="22729-158">Phase 4 : création d’un certificat auto-signé et configuration d’ADFS1 et de PROXY1</span><span class="sxs-lookup"><span data-stu-id="22729-158">Phase 4: Create a self-signed certificate and configure ADFS1 and PROXY1</span></span>

<span data-ttu-id="22729-159">Au cours de cette phase, vous créez un certificat numérique auto-signé pour votre nom de domaine complet du service FS (Federation Service) et vous configurez ADFS1 et PROXY1 en tant que batterie de serveurs AD FS.</span><span class="sxs-lookup"><span data-stu-id="22729-159">In this phase, you create a self-signed digital certificate for your federation service FQDN and configure ADFS1 and PROXY1 as an AD FS farm.</span></span>
  
<span data-ttu-id="22729-160">Tout d’abord, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle DC1 à l’aide des informations d’identification de CORP\\User1, puis ouvrez une invite de commande Windows PowerShell de niveau administrateur.</span><span class="sxs-lookup"><span data-stu-id="22729-160">First, use the [Azure portal](https://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="22729-161">Ensuite, créez un compte de service AD FS avec cette commande à l’invite de commande Windows PowerShell sur DC1 :</span><span class="sxs-lookup"><span data-stu-id="22729-161">Next, create AD FS service account with this command at the Windows PowerShell command prompt on DC1:</span></span>
  
```powershell
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```
<span data-ttu-id="22729-p107">Notez que cette commande vous invite à indiquer le mot de passe du compte. Choisissez un mot de passe fort et enregistrez-le dans un emplacement sécurisé. Vous en aurez besoin pour cette phase et la phase 5.</span><span class="sxs-lookup"><span data-stu-id="22729-p107">Note that this command prompts you to supply the account password. Choose a strong password and record it in a secured location. You will need it for this phase and Phase 5.</span></span>
  
<span data-ttu-id="22729-p108">Utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle ADFS1 à l’aide des informations d’identification de CORP\\User1. Ouvrez une invite de commande Windows PowerShell de niveau administrateur sur ADFS1, indiquez votre nom de domaine complet du service FS (Federation Service), puis exécutez ces commandes pour créer un certificat auto-signé :</span><span class="sxs-lookup"><span data-stu-id="22729-p108">Use the [Azure portal](https://portal.azure.com) to connect to the ADFS1 virtual machine using the CORP\\User1 credentials. Open an administrator-level Windows PowerShell command prompt on ADFS1, fill in your federation service FQDN, and then run these commands to create a self-signed certificate:</span></span>
  
```powershell
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

<span data-ttu-id="22729-167">Ensuite, utilisez ces étapes pour enregistrer le nouveau certificat auto-signé en tant que fichier.</span><span class="sxs-lookup"><span data-stu-id="22729-167">Next, use these steps to save the new self-signed certificate as a file.</span></span>
  
1. <span data-ttu-id="22729-168">Cliquez sur **Démarrer**, tapez **mmc.exe**, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="22729-168">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="22729-169">Cliquez sur **Fichier > Ajouter/Supprimer un composant logiciel enfichable**.</span><span class="sxs-lookup"><span data-stu-id="22729-169">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="22729-170">Dans **Ajouter ou supprimer des composants logiciels enfichables**, double-cliquez sur **Certificats** dans la liste des composants logiciels enfichables disponibles, cliquez sur **Compte d’ordinateur**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-170">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="22729-171">Dans **Sélectionner un ordinateur**, cliquez sur **Terminer**, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="22729-171">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="22729-172">Dans le volet d’arborescence, ouvrez **Certificats (ordinateur local) > Personnel > Certificats**.</span><span class="sxs-lookup"><span data-stu-id="22729-172">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="22729-173">Cliquez sur le certificat avec votre nom de domaine complet du service FS (Federation Service) avec le bouton droit de la souris, cliquez sur **Toutes les tâches**, puis sur **Exporter**.</span><span class="sxs-lookup"><span data-stu-id="22729-173">Right-click the certificate with your federation service FQDN, click **All tasks**, and then click **Export**.</span></span>
    
7. <span data-ttu-id="22729-174">Dans la page **Bienvenue**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-174">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="22729-175">Sur la page \*\*Exporter la clé privée \*\*, cliquez sur **Oui**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-175">On the **Export Private Key** page, click **Yes**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="22729-176">Sur la page **Format du fichier d’exportation**, cliquez sur **Exporter toutes les propriétés étendues**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-176">On the **Export File Format** page, click **Export all extended properties**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="22729-177">Sur la page **Sécurité**, cliquez sur **Mot de passe** et saisissez un mot de passe dans **Mot de passe** et dans **Confirmer le mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="22729-177">On the **Security** page, click **Password** and type a password in **Password** and **Confirm password.**</span></span>
    
11. <span data-ttu-id="22729-178">Sur la page **Fichier à exporter**, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="22729-178">On the **File to Export** page, click **Browse**.</span></span>
    
12. <span data-ttu-id="22729-179">Accédez au dossier **C:\\Certs**, saisissez **SSL** dans **Nom de fichier**, puis cliquez sur **Enregistrer.**</span><span class="sxs-lookup"><span data-stu-id="22729-179">Browse to the **C:\\Certs** folder, type **SSL** in **File name**, and then click **Save.**</span></span>
    
13. <span data-ttu-id="22729-180">Sur la page **Fichier à exporter**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-180">On the **File to Export** page, click **Next**.</span></span>
    
14. <span data-ttu-id="22729-p109">Sur la page **Fin de l’Assistant Exportation de certificat**, cliquez sur **Terminer**. À l’invite, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="22729-p109">On the **Completing the Certificate Export Wizard** page, click **Finish**. When prompted, click **OK**.</span></span>
    
<span data-ttu-id="22729-183">Ensuite, installez le service AD FS avec cette commande à l’invite de commande Windows PowerShell sur ADFS1 :</span><span class="sxs-lookup"><span data-stu-id="22729-183">Next, install the AD FS service with this command at the Windows PowerShell command prompt on ADFS1:</span></span>
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

<span data-ttu-id="22729-184">Attendez la fin de l’installation.</span><span class="sxs-lookup"><span data-stu-id="22729-184">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="22729-185">Ensuite, configurez le service AD FS en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="22729-185">Next, configure the AD FS service with these steps:</span></span>
  
1. <span data-ttu-id="22729-186">Cliquez sur **Démarrer**, puis sur l’icône **Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="22729-186">Click **Start**, and then click the **Server Manager** icon.</span></span>
    
2. <span data-ttu-id="22729-187">Dans le volet d’arborescence du Gestionnaire de serveur, cliquez sur **AD FS**.</span><span class="sxs-lookup"><span data-stu-id="22729-187">In the tree pane of Server Manager, click **AD FS**.</span></span>
    
3. <span data-ttu-id="22729-188">Dans la barre d’outils en haut de l’écran, cliquez sur le symbole d’avertissement orange, puis sur **Configurez le service FS (Federation Service) sur ce serveur**.</span><span class="sxs-lookup"><span data-stu-id="22729-188">In the tool bar at the top, click the orange caution symbol, and then click **Configure the federation service on this server**.</span></span>
    
4. <span data-ttu-id="22729-189">Sur la page d’**accueil** de l’Assistant Configuration des services de fédération Active Directory (AD FS), cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-189">On the **Welcome** page of the Active Directory Federation Services Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="22729-190">Sur la page **Connexion à AD FS**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-190">On the **Connect to AD DS** page, click **Next**.</span></span>
    
6. <span data-ttu-id="22729-191">Sur la page **Spécifier les propriétés de service** :</span><span class="sxs-lookup"><span data-stu-id="22729-191">On the **Specify Service Properties** page:</span></span>
    
  - <span data-ttu-id="22729-192">Pour **Certificat SSL**, cliquez sur la flèche vers le bas, puis sur le certificat avec votre nom de domaine complet du service FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="22729-192">For **SSL Certificate**, click the down arrow, and then click the certificate with the name of your federation service FQDN.</span></span>
    
  - <span data-ttu-id="22729-193">Dans **Nom complet du service FS**, saisissez le nom de votre organisation fictive.</span><span class="sxs-lookup"><span data-stu-id="22729-193">In **Federation Service Display Name**, type the name of your fictional organization.</span></span>
    
  - <span data-ttu-id="22729-194">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-194">Click **Next**.</span></span>
    
7. <span data-ttu-id="22729-195">Sur la page **Spécifier un compte de service**, cliquez sur **Sélectionner** pour **Nom du compte**.</span><span class="sxs-lookup"><span data-stu-id="22729-195">On the **Specify Service Account** page, click **Select** for **Account name**.</span></span>
    
8. <span data-ttu-id="22729-196">Dans **Sélectionner l’utilisateur ou le compte de service**, saisissez **ADFS-Service**, cliquez sur **Vérifier les noms**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="22729-196">In **Select User or Service Account**, type **ADFS-Service**, click **Check Names**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="22729-197">Dans **Mot de passe de compte**, saisissez le mot de passe du compte ADFS-Service, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-197">In **Account Password**, type the password for the ADFS-Service account, and then click **Next**.</span></span>
    
10. <span data-ttu-id="22729-198">Sur la page **Spécifier une base de données de configuration**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-198">On the **Specify Configuration Database** page, click **Next**.</span></span>
    
11. <span data-ttu-id="22729-199">Sur la page **Examiner les options**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-199">On the **Review Options** page, click **Next**.</span></span>
    
12. <span data-ttu-id="22729-200">Sur la page **Vérifications des conditions préalables**, cliquez sur **Configurer**.</span><span class="sxs-lookup"><span data-stu-id="22729-200">On the **Pre-requisite Checks** page, click **Configure**.</span></span>
    
13. <span data-ttu-id="22729-201">Sur la page **Résultats**, cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="22729-201">On the **Results** page, click **Close**.</span></span>
    
14. <span data-ttu-id="22729-202">Cliquez sur **Démarrer**, puis sur l’icône de démarrage, choisissez **Redémarrer**, puis **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="22729-202">Click **Start**, click the power icon, click **Restart**, and then click **Continue**.</span></span>
    
<span data-ttu-id="22729-203">À partir du [portail Azure](https://portal.azure.com), connectez-vous à PROXY1 avec les informations d’identification du compte CORP\\User1.</span><span class="sxs-lookup"><span data-stu-id="22729-203">From the [Azure portal](https://portal.azure.com), connect to PROXY1 with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="22729-204">Ensuite, suivez ces étapes pour installer le certificat auto-signé sur **PROXY1 et APP1**.</span><span class="sxs-lookup"><span data-stu-id="22729-204">Next, use these steps to install the self-signed certificate on **both PROXY1 and APP1**.</span></span>
  
1. <span data-ttu-id="22729-205">Cliquez sur **Démarrer**, tapez **mmc.exe**, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="22729-205">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="22729-206">Cliquez sur **Fichier > Ajouter/Supprimer un composant logiciel enfichable**.</span><span class="sxs-lookup"><span data-stu-id="22729-206">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="22729-207">Dans **Ajouter ou supprimer des composants logiciels enfichables**, double-cliquez sur **Certificats** dans la liste des composants logiciels enfichables disponibles, cliquez sur **Compte d’ordinateur**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-207">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="22729-208">Dans **Sélectionner un ordinateur**, cliquez sur **Terminer**, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="22729-208">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="22729-209">Dans le volet d’arborescence, ouvrez **Certificats (ordinateur local) > Personnel > Certificats**.</span><span class="sxs-lookup"><span data-stu-id="22729-209">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="22729-210">Cliquez avec le bouton droit sur **Personnel**, cliquez sur **Toutes les tâches**, puis sur **Importer**.</span><span class="sxs-lookup"><span data-stu-id="22729-210">Right-click **Personal**, click **All tasks**, and then click **Import**.</span></span>
    
7. <span data-ttu-id="22729-211">Dans la page **Bienvenue**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-211">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="22729-212">Sur la page **Fichier à importer**, saisissez **\\\\adfs1\\certs\\ssl.pfx**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-212">On the **File to Import** page, type **\\\\adfs1\\certs\\ssl.pfx**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="22729-213">Sur la page **Protection de clé privée**, saisissez le mot de passe du certificat dans **Mot de passe**, puis cliquez sur **Suivant.**</span><span class="sxs-lookup"><span data-stu-id="22729-213">On the **Private key protection** page, type the certificate password in **Password**, and then click **Next.**</span></span>
    
10. <span data-ttu-id="22729-214">Sur la page **Magasin de certificats**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-214">On the **Certificate store** page, click **Next.**</span></span>
    
11. <span data-ttu-id="22729-215">Sur la page **Achèvement**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="22729-215">On the **Completing** page, click **Finish**.</span></span>
    
12. <span data-ttu-id="22729-216">Sur la page **Magasin de certificats**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-216">On the **Certificate Store** page, click **Next**.</span></span>
    
13. <span data-ttu-id="22729-217">À l’invite, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="22729-217">When prompted, click **OK**.</span></span>
    
14. <span data-ttu-id="22729-218">Cliquez sur **Certificats** dans le volet d’arborescence.</span><span class="sxs-lookup"><span data-stu-id="22729-218">Click **Certificates** in the tree pane.</span></span>
    
15. <span data-ttu-id="22729-219">Cliquez sur le certificat avec le bouton droit de la souris, puis cliquez sur **Copier**.</span><span class="sxs-lookup"><span data-stu-id="22729-219">Right-click the certificate, and then click **Copy**.</span></span>
    
16. <span data-ttu-id="22729-220">Dans le volet d’arborescence, ouvrez **Autorités de certification racines de confiance > Certificats**.</span><span class="sxs-lookup"><span data-stu-id="22729-220">In the tree pane, open **Trusted Root Certification Authorities > Certificates**.</span></span>
    
17. <span data-ttu-id="22729-221">Placez le pointeur de la souris au-dessous de la liste des certificats installés, cliquez avec le bouton droit, puis cliquez sur **Coller**.</span><span class="sxs-lookup"><span data-stu-id="22729-221">Move your mouse pointer below the list of installed certificates, right-click, and then click **Paste**.</span></span>
    
<span data-ttu-id="22729-222">Ouvrez une invite de commande PowerShell de niveau administrateur et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="22729-222">Open an administrator-level PowerShell command prompt and run the following command:</span></span>
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

<span data-ttu-id="22729-223">Attendez la fin de l’installation.</span><span class="sxs-lookup"><span data-stu-id="22729-223">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="22729-224">Suivez ces étapes pour configurer le service de proxy d’application web de manière à ce qu’il utilise ADFS1 comme serveur de fédération :</span><span class="sxs-lookup"><span data-stu-id="22729-224">Use these steps to configure the web application proxy service to use ADFS1 as its federation server:</span></span>
  
1. <span data-ttu-id="22729-225">Cliquez sur **Démarrer**, puis sur **Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="22729-225">Click **Start**, and then click **Server Manager**.</span></span>
    
2. <span data-ttu-id="22729-226">Dans le volet d’arborescence, cliquez sur **Accès distant**.</span><span class="sxs-lookup"><span data-stu-id="22729-226">In the tree pane, click **Remote Access**.</span></span>
    
3. <span data-ttu-id="22729-227">Dans la barre d’outils en haut de l’écran, cliquez sur le symbole d’avertissement orange, puis sur **Ouvrir l’Assistant Proxy d’application web**.</span><span class="sxs-lookup"><span data-stu-id="22729-227">In the tool bar at the top, click the orange caution symbol, and then click **Open the Web Application Proxy Wizard**.</span></span>
    
4. <span data-ttu-id="22729-228">Sur la page d’**accueil** de l’Assistant Configuration de proxy d’application web, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-228">On the **Welcome** page of the Web Application Proxy Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="22729-229">Sur la page **Serveur de fédération** :</span><span class="sxs-lookup"><span data-stu-id="22729-229">On the **Federation Server** page:</span></span>
    
  - <span data-ttu-id="22729-230">Saisissez votre nom de domaine complet du service FS (Federation Service) dans **Nom du service FS (Federation Service)**.</span><span class="sxs-lookup"><span data-stu-id="22729-230">Type your federation service FQDN in **Federation service name**.</span></span>
    
  - <span data-ttu-id="22729-231">Saisissez **CORP\\User1** dans **Nom d’utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="22729-231">Type **CORP\\User1** in **User name**.</span></span>
    
  - <span data-ttu-id="22729-232">Saisissez le mot de passe du compte User1 dans **Mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="22729-232">Type the password for the User1 account in **Password**.</span></span>
    
  - <span data-ttu-id="22729-233">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-233">Click **Next**.</span></span>
    
6. <span data-ttu-id="22729-234">Sur la page **Certificats de proxy AD FS**, cliquez sur la flèche vers le bas, cliquez sur le certificat avec votre nom de domaine complet du service FS (Federation Service), puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-234">On the **AD FS Proxy Certificate** page, click the down arrow, click the certificate with your federation service FQDN, and then click **Next**.</span></span>
    
7. <span data-ttu-id="22729-235">Sur la page **Confirmation**, cliquez sur **Configurer**.</span><span class="sxs-lookup"><span data-stu-id="22729-235">On the **Confirmation** page, click **Configure**.</span></span>
    
8. <span data-ttu-id="22729-236">Sur la page **Résultats**, cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="22729-236">On the **Results** page, click **Close**.</span></span>

    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a><span data-ttu-id="22729-237">Phase 5: configuration de Microsoft 365 pour l’identité fédérée</span><span class="sxs-lookup"><span data-stu-id="22729-237">Phase 5: Configure Microsoft 365 for federated identity</span></span>

<span data-ttu-id="22729-238">Utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle APP1 avec les informations d’identification du compte CORP\\User1.</span><span class="sxs-lookup"><span data-stu-id="22729-238">Use the [Azure portal](https://portal.azure.com) to connect to the APP1 virtual machine with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="22729-239">Suivez ces étapes pour configurer Azure AD Connect et votre abonnement Microsoft 365 pour l’authentification fédérée :</span><span class="sxs-lookup"><span data-stu-id="22729-239">Use these steps to configure Azure AD Connect and your Microsoft 365 subscription for federated authentication:</span></span>
  
1. <span data-ttu-id="22729-240">Sur le bureau, double-cliquez sur **Azure AD Connect**.</span><span class="sxs-lookup"><span data-stu-id="22729-240">From the desktop, double-click **Azure AD Connect**.</span></span>
    
2. <span data-ttu-id="22729-241">Sur la page **Bienvenue dans Azure AD Connect**, cliquez sur **Configurer**.</span><span class="sxs-lookup"><span data-stu-id="22729-241">On the **Welcome to Azure AD Connect** page, click **Configure**.</span></span>
    
3. <span data-ttu-id="22729-242">Sur la page **Tâches supplémentaires**, cliquez sur **Modifier la connexion utilisateur**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-242">On the **Additional tasks** page, click **Change user sign-in**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="22729-243">Sur la page **Connexion à Azure AD**, tapez le nom de votre compte d’administrateur général et le mot de passe, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-243">On the **Connect to Azure AD** page, type your global administrator account name and password, and then click **Next**.</span></span>
    
5. <span data-ttu-id="22729-244">Sur la page **Connexion utilisateur**, cliquez sur **Fédération avec AD FS**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-244">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="22729-245">Sur la page **Batterie de serveurs AD FS**, cliquez sur **Utiliser une batterie de serveurs AD FS existante**, saisissez **ADFS1** dans **Nom du serveur**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-245">On the **AD FS farm** page, click **Use an existing AD FS farm**, type **ADFS1** in **Server Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="22729-246">Lorsque vous êtes invité à entrer les informations d’identification du serveur, saisissez les informations d’identification du compte CORP\\User1, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="22729-246">When prompted for server credentials, enter the credentials of the CORP\\User1 account, and then click **OK**.</span></span>
    
8. <span data-ttu-id="22729-247">Sur la page des informations d’identification **Administrateur de domaine**, saisissez **CORP\\User1** dans **Nom d’utilisateur** et le mot de passe du compte dans **Mot de passe**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-247">On the **Domain Administrator** credentials page, type **CORP\\User1** in **Username** and the account password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="22729-248">Sur la page **Compte de service AD FS**, saisissez **CORP\\ADFS-Service** dans **Nom d’utilisateur du domaine** et le mot de passe du compte dans **Mot de passe utilisateur du domaine**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-248">On the **AD FS service account** page, type **CORP\\ADFS-Service** in **Domain Username** and the account password in **Domain User Password**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="22729-249">Sur la page **Domaine Azure AD**, dans **Domaine**, sélectionnez le nom du domaine que vous avez précédemment créé et ajouté à votre abonnement à la phase 1 lors de la phase 1, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="22729-249">On the **Azure AD Domain** page, in **Domain**, select the name of the domain you previously created and added to your subscription in Phase 1, and then click **Next**.</span></span>
    
11. <span data-ttu-id="22729-250">Sur la page **Prêt à configurer**, cliquez sur **Configurer**.</span><span class="sxs-lookup"><span data-stu-id="22729-250">On the **Ready to configure** page, click **Configure**.</span></span>
    
12. <span data-ttu-id="22729-251">Sur la page **Installation terminée**, cliquez sur **Vérifier**.</span><span class="sxs-lookup"><span data-stu-id="22729-251">On the **Installation complete** page, click **Verify**.</span></span>
    
    <span data-ttu-id="22729-252">Vous devriez voir des messages vous indiquant que les configurations intranet et Internet ont été vérifiées.</span><span class="sxs-lookup"><span data-stu-id="22729-252">You should see messages indicating that both the intranet and Internet configuration was verified.</span></span>
    
13. <span data-ttu-id="22729-253">Sur la page **Installation terminée**, cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="22729-253">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="22729-254">Pour vérifier que l’authentification fédérée fonctionne, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="22729-254">To demonstrate that federated authentication is working:</span></span>
  
1. <span data-ttu-id="22729-255">Ouvrez une nouvelle instance privée de votre navigateur sur votre ordinateur local et accédez à [https://admin.microsoft.com](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="22729-255">Open a new private instance of your browser on your local computer and go to [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
    
2. <span data-ttu-id="22729-256">Pour les informations d’identification de connexion, tapez **user1@**\<the domain created in Phase 1>.</span><span class="sxs-lookup"><span data-stu-id="22729-256">For the sign-in credentials, type **user1@**\<the domain created in Phase 1>.</span></span> 
    
    <span data-ttu-id="22729-p110">Par exemple, si votre domaine de test est **testlab.contoso.com**, vous tapez « user1@testlab.contoso.com ». Appuyez sur la touche de tabulation ou autorisez Microsoft 365 à vous rediriger automatiquement.</span><span class="sxs-lookup"><span data-stu-id="22729-p110">For example, if your test domain is **testlab.contoso.com**, you would type "user1@testlab.contoso.com". Press TAB or allow Microsoft 365 to automatically redirect you.</span></span>
    
    <span data-ttu-id="22729-p111">Une page **Votre connexion n’est pas privée** devrait s’afficher. Cette page s’affiche, car vous avez installé sur ADFS1 un certificat auto-signé que votre ordinateur de bureau ne peut pas valider. Dans un déploiement de production d’authentification fédérée, vous utiliseriez un certificat provenant d’une autorité de certification approuvée et vos utilisateurs ne verraient pas cette page.</span><span class="sxs-lookup"><span data-stu-id="22729-p111">You should now see a **Your connection is not private** page. You are seeing this because you installed a self-signed certificate on ADFS1 that your desktop computer cannot validate. In a production deployment of federated authentication, you would use a certificate from a trusted certification authority and your users would not see this page.</span></span>
    
3. <span data-ttu-id="22729-262">Sur la page **Votre connexion n’est pas privée**, cliquez sur **Avancé**, puis sur **Continuer avec \<your federation service FQDN>**.</span><span class="sxs-lookup"><span data-stu-id="22729-262">On the **Your connection is not private** page, click **Advanced**, and then click **Proceed to \<your federation service FQDN>**.</span></span> 
    
4. <span data-ttu-id="22729-263">Sur la page contenant le nom de votre organisation fictive, connectez-vous avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="22729-263">On the page with the name of your fictional organization, sign in with the following:</span></span>
    
  - <span data-ttu-id="22729-264">**CORP\\User1** pour le nom ;</span><span class="sxs-lookup"><span data-stu-id="22729-264">**CORP\\User1** for the name</span></span>
    
  - <span data-ttu-id="22729-265">le mot de passe du compte User1.</span><span class="sxs-lookup"><span data-stu-id="22729-265">The password for the User1 account</span></span>
    
    <span data-ttu-id="22729-266">Vous devez voir la **page d’accueil Microsoft Office**.</span><span class="sxs-lookup"><span data-stu-id="22729-266">You should see the **Microsoft Office Home** page.</span></span>
    
<span data-ttu-id="22729-p112">Cette procédure montre que votre abonnement d’évaluation est fédéré avec le domaine corp.contoso.com AD DS hébergé sur DC1. Voici les principes de base du processus d’authentification :</span><span class="sxs-lookup"><span data-stu-id="22729-p112">This procedure demonstrates that your trial subscription is federated with the AD DS corp.contoso.com domain hosted on DC1. Here are the basics of the authentication process:</span></span>
  
1. <span data-ttu-id="22729-269">Lorsque vous utilisez le domaine fédéré que vous avez créé à la phase 1 dans le nom de compte de connexion, Microsoft 365 redirige votre navigateur vers le nom de domaine complet de votre service FS (Federation Service) et PROXY1.</span><span class="sxs-lookup"><span data-stu-id="22729-269">When you use the federated domain that you created in Phase 1 within the sign-in account name, Microsoft 365 redirects your browser to your federation service FQDN and PROXY1.</span></span>
    
2. <span data-ttu-id="22729-270">PROXY1 envoie la page de connexion de l’entreprise fictive à votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="22729-270">PROXY1 sends your local computer the fictional company sign-in page.</span></span>
    
3. <span data-ttu-id="22729-271">Lorsque vous envoyez CORP\\User1 et le mot de passe à PROXY1, il les transfère à ADFS1.</span><span class="sxs-lookup"><span data-stu-id="22729-271">When you send CORP\\User1 and the password to PROXY1, it forwards them to ADFS1.</span></span>
    
4. <span data-ttu-id="22729-272">ADFS1 valide CORP\\User1 et le mot de passe avec DC1 et envoie un jeton de sécurité à votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="22729-272">ADFS1 validates CORP\\User1 and the password with DC1 and sends your local computer a security token.</span></span>
    
5. <span data-ttu-id="22729-273">Votre ordinateur local envoie le jeton de sécurité à Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="22729-273">Your local computer sends the security token to Microsoft 365.</span></span>
    
6. <span data-ttu-id="22729-274">Microsoft 365 confirme que le jeton de sécurité a été créé par ADFS1 et autorise l’accès.</span><span class="sxs-lookup"><span data-stu-id="22729-274">Microsoft 365 validates that the security token was created by ADFS1 and allows access.</span></span>
    
<span data-ttu-id="22729-p113">Votre abonnement d’évaluation est désormais configuré avec l’authentification fédérée. Vous pouvez utiliser cet environnement de développement/test pour les scénarios d’authentification avancés.</span><span class="sxs-lookup"><span data-stu-id="22729-p113">Your trial subscription is now configured with federated authentication. You can use this dev/test environment for advanced authentication scenarios.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="22729-277">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="22729-277">Next step</span></span>

<span data-ttu-id="22729-278">Lorsque vous êtes prêt à déployer l’authentification fédérée prête pour la production et la haute disponibilité pour Microsoft 365 dans Azure, consultez la rubrique [Deploy High Availability Federated Authentication for microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="22729-278">When you are ready to deploy production-ready, high availability federated authentication for Microsoft 365 in Azure, see [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).</span></span>
  