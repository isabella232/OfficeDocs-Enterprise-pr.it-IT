---
title: Fase 3 dell'autenticazione federata a disponibilità elevata configurare i server AD FS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: "Riepilogo: creare e configurare i server Active Directory Federation Services (AD FS) per l'autenticazione federata a disponibilità elevata per Office 365 in Microsoft Azure."
ms.openlocfilehash: add154dbce67c76b3f88e205c683711f72cb7b9a
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487848"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="c96d7-103">Fase 3 dell'autenticazione federata a disponibilità elevata: configurare i server AD FS</span><span class="sxs-lookup"><span data-stu-id="c96d7-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

 <span data-ttu-id="c96d7-104">**Riepilogo:** creare e configurare i server Active Directory Federation Services (AD FS) per l'autenticazione federata a disponibilità elevata per Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c96d7-104">**Summary:** Create and configure the Active Directory Federation Services (AD FS) servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="c96d7-105">In questa fase di distribuzione di disponibilità elevata per l'autenticazione federata di Office 365 nei servizi infrastruttura di Azure, viene creato un bilanciamento del carico interno e due server AD FS.</span><span class="sxs-lookup"><span data-stu-id="c96d7-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="c96d7-106">È necessario completare questa fase prima di passare a [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span><span class="sxs-lookup"><span data-stu-id="c96d7-106">You must complete this phase before moving on to [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span></span> <span data-ttu-id="c96d7-107">Vedere [Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) per tutte le fasi.</span><span class="sxs-lookup"><span data-stu-id="c96d7-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="c96d7-108">Creare le macchine virtuali dei server AD FS in Azure</span><span class="sxs-lookup"><span data-stu-id="c96d7-108">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="c96d7-p102">Utilizzare il seguente blocco di comandi di PowerShell per creare le macchine virtuali per i due server AD FS. Il set di comandi di PowerShell utilizza i valori indicati nelle tabelle riportate di seguito:</span><span class="sxs-lookup"><span data-stu-id="c96d7-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="c96d7-111">Tabella M, per le macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="c96d7-111">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="c96d7-112">Tabella R, per i gruppi di risorse</span><span class="sxs-lookup"><span data-stu-id="c96d7-112">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="c96d7-113">Tabella V, per le impostazioni della rete virtuale</span><span class="sxs-lookup"><span data-stu-id="c96d7-113">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="c96d7-114">Tabella S, per le subnet</span><span class="sxs-lookup"><span data-stu-id="c96d7-114">Table S, for your subnets</span></span>
    
- <span data-ttu-id="c96d7-115">Tabella I, per gli indirizzi IP statici</span><span class="sxs-lookup"><span data-stu-id="c96d7-115">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="c96d7-116">Tabella A, per i set di disponibilità</span><span class="sxs-lookup"><span data-stu-id="c96d7-116">Table A, for your availability sets</span></span>
    
<span data-ttu-id="c96d7-117">Ricordare che è stata definita la tabella M nella [fase 2 di autenticazione federata a disponibilità elevata: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) e le tabelle R, V, S, i e a nella [fase 1 di autenticazione federata a disponibilità elevata: configurare Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="c96d7-117">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c96d7-118">[!NOTA] I seguenti comandi consentono di utilizzare la versione più recente di Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c96d7-118">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="c96d7-119">Vedere [Panoramica dei cmdlet di Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="c96d7-119">See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="c96d7-120">Per prima cosa, creare un bilanciamento del carico interno di Azure per i due server AD FS.</span><span class="sxs-lookup"><span data-stu-id="c96d7-120">First, you create an Azure internal load balancer for the two AD FS servers.</span></span> <span data-ttu-id="c96d7-121">Specificare i valori per le variabili, rimuovendo \< i caratteri e >.</span><span class="sxs-lookup"><span data-stu-id="c96d7-121">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="c96d7-122">Una volta forniti tutti i valori opportuni, eseguire il blocco risultante nel prompt dei comandi di Azure PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c96d7-122">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="c96d7-123">Successivamente, creare le macchine virtuali dei server AD FS.</span><span class="sxs-lookup"><span data-stu-id="c96d7-123">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="c96d7-124">Una volta forniti tutti i valori opportuni, eseguire il blocco risultante nel prompt dei comandi di Azure PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c96d7-124">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="c96d7-p105">Poiché queste macchine virtuali sono per un'applicazione Intranet, non sono assegnate a un indirizzo IP pubblico o a un'etichetta del nome di dominio DNS ed esposte a Internet. Tuttavia, ciò significa anche che non è possibile connettersi a tali macchine virtuali dal portale di Azure. L'opzione **Connetti** non è disponibile quando si visualizzano le proprietà della macchina virtuale. Usare l'accessorio Connessione desktop remoto o un altro strumento Desktop remoto per connettersi alla macchina virtuale usando il relativo indirizzo IP privato o il nome DNS Intranet.</span><span class="sxs-lookup"><span data-stu-id="c96d7-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="c96d7-p106">Per ogni macchina virtuale, usare il client desktop remoto di propria scelta e creare una connessione desktop remoto. Usare il nome DNS Intranet o il nome computer e le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="c96d7-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="c96d7-131">Per ogni macchina virtuale, aggiungerli al dominio di servizi di dominio Active Directory (AD DS) appropriato con questi comandi nel prompt di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c96d7-131">For each virtual machine, join them to the appropriate Active Directory Domain Services (AD DS) domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="c96d7-132">Di seguito è riportata la configurazione risultante dal completamento corretto di questa fase, con i nomi computer segnaposto.</span><span class="sxs-lookup"><span data-stu-id="c96d7-132">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="c96d7-133">**Fase 3: i server AD FS e il bilanciamento del carico interno per l'infrastruttura dell'autenticazione federata a disponibilità elevata in Azure**</span><span class="sxs-lookup"><span data-stu-id="c96d7-133">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 3 dell'infrastruttura di autenticazione federata di Office 365 a disponibilità elevata in Azure con i server AD FS](media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="c96d7-135">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="c96d7-135">Next step</span></span>

<span data-ttu-id="c96d7-136">Utilizzare [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) per continuare a configurare il carico di lavoro.</span><span class="sxs-lookup"><span data-stu-id="c96d7-136">Use [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c96d7-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c96d7-137">See Also</span></span>

[<span data-ttu-id="c96d7-138">Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="c96d7-138">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="c96d7-139">Identità federata per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="c96d7-139">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)


