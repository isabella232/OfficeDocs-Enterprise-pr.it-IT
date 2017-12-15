---
title: "Disponibilità elevata federati server ADFS fase 3 configurare l'autenticazione"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid_Top
- Ent_O365
- Ent_O365_Hybrid
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: "Riepilogo: Creare e configurare il server di Active Directory Federation Services (ADFS) per l'autenticazione federata la disponibilità elevata per Office 365 in Microsoft Azure."
ms.openlocfilehash: b3faf7e7ebf25dbcbfd5a0a8d3431d145b540da8
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="769cd-103">Fase 3 dell'autenticazione federata a disponibilità elevata: Configurare i server AD FS</span><span class="sxs-lookup"><span data-stu-id="769cd-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

 <span data-ttu-id="769cd-104">**Riepilogo:** Creare e configurare il server di Active Directory Federation Services (ADFS) per l'autenticazione federata la disponibilità elevata per Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="769cd-104">**Summary:** Create and configure the Active Directory Federation Services (AD FS) servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="769cd-105">In questa fase di distribuzione di disponibilità elevata per l'autenticazione federata di Office 365 nei servizi infrastruttura di Azure, viene creato un bilanciamento del carico interno e due server AD FS.</span><span class="sxs-lookup"><span data-stu-id="769cd-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="769cd-p101">È necessario completare prima di spostare in questa fase [la disponibilità elevata federati autenticazione fase 4: configurare il proxy di applicazione web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Per tutte le fasi, vedere [Deploy la disponibilità elevata nell'autenticazione federata per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) .</span><span class="sxs-lookup"><span data-stu-id="769cd-p101">You must complete this phase before moving on to [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="769cd-108">Creare le macchine virtuali dei server AD FS in Azure</span><span class="sxs-lookup"><span data-stu-id="769cd-108">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="769cd-p102">Utilizzare il seguente blocco di comandi di PowerShell per creare le macchine virtuali per i due server AD FS. Il set di comandi di PowerShell utilizza i valori indicati nelle tabelle riportate di seguito:</span><span class="sxs-lookup"><span data-stu-id="769cd-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="769cd-111">Tabella M, per le macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="769cd-111">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="769cd-112">Tabella R, per i gruppi di risorse</span><span class="sxs-lookup"><span data-stu-id="769cd-112">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="769cd-113">Tabella V, per le impostazioni della rete virtuale</span><span class="sxs-lookup"><span data-stu-id="769cd-113">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="769cd-114">Tabella S, per le subnet</span><span class="sxs-lookup"><span data-stu-id="769cd-114">Table S, for your subnets</span></span>
    
- <span data-ttu-id="769cd-115">Tabella I, per gli indirizzi IP statici</span><span class="sxs-lookup"><span data-stu-id="769cd-115">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="769cd-116">Tabella A, per i set di disponibilità</span><span class="sxs-lookup"><span data-stu-id="769cd-116">Table A, for your availability sets</span></span>
    
<span data-ttu-id="769cd-117">Richiamare una definite tabella M in [la disponibilità elevata federati autenticazione fase 2: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) e tabelle R, V, S, è possibile e A in [la disponibilità elevata federati autenticazione fase 1: configurare Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="769cd-117">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="769cd-p103">Il seguente comando consente di utilizzare la versione più recente di Azure PowerShell. Vedere [iniziare a utilizzare i cmdlet PowerShell di Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="769cd-p103">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="769cd-p104">Creare innanzitutto un servizio di bilanciamento del carico interno Azure per l'annuncio di due server ADFS. Specificare i valori per le variabili, rimuovere il \< e > caratteri. Quando vengono specificati tutti i valori appropriati, eseguire il blocco risultante al prompt dei comandi di PowerShell Azure o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="769cd-p104">First, you create an Azure internal load balancer for the two AD FS servers. Specify the values for the variables, removing the \< and > characters. When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="769cd-123">Per un file di testo che contiene tutti i comandi di PowerShell in questo articolo e una cartella di lavoro configurazione Microsoft Excel che genera pronto a portata di blocchi di comandi di PowerShell in base alle impostazioni personalizzate, vedere [autenticazione federata per Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="769cd-123">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzureRMLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="769cd-124">Successivamente, creare le macchine virtuali dei server AD FS.</span><span class="sxs-lookup"><span data-stu-id="769cd-124">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="769cd-125">Una volta forniti tutti i valori opportuni, eseguire il blocco risultante nel prompt dei comandi di Azure PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="769cd-125">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="769cd-p105">Dal momento che queste macchine virtuali sono relative a un'applicazione intranet, non vengono assegnati un indirizzo IP pubblico o un'etichetta nome di dominio DNS ed esposti a Internet. Tuttavia, ciò significa inoltre che non è possibile connettersi a tali dal portale di Azure. Quando si visualizzano le proprietà della macchina virtuale non è disponibile l'opzione **Connetti** . Utilizzare accessorio connessione Desktop remoto o un altro strumento di Desktop remoto per la connessione alla macchina virtuale con privata IP address o intranet nome DNS.</span><span class="sxs-lookup"><span data-stu-id="769cd-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="769cd-p106">Per ogni macchina virtuale, usare il client desktop remoto di propria scelta e creare una connessione desktop remoto. Usare il nome DNS Intranet o il nome computer e le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="769cd-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="769cd-132">Per ogni macchina virtuale, aggiungerlo al dominio di Windows Server AD appropriato con questi comandi nel prompt dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="769cd-132">For each virtual machine, join them to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="769cd-133">Di seguito è riportata la configurazione risultante dal completamento corretto di questa fase, con i nomi computer segnaposto.</span><span class="sxs-lookup"><span data-stu-id="769cd-133">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="769cd-134">**Fase 3: Server AD FS e servizio di bilanciamento del carico interno per l'infrastruttura di autenticazione federativa la disponibilità elevata in Azure**</span><span class="sxs-lookup"><span data-stu-id="769cd-134">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 3 dell'autenticazione federata di Office 365 con disponibilità elevata in Azure con server AD FS](images/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="769cd-136">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="769cd-136">Next step</span></span>

<span data-ttu-id="769cd-137">Utilizzare [la disponibilità elevata federati autenticazione fase 4: configurare il proxy di applicazione web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) per continuare a configurare questo carico di lavoro.</span><span class="sxs-lookup"><span data-stu-id="769cd-137">Use [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="769cd-138">See Also</span><span class="sxs-lookup"><span data-stu-id="769cd-138">See Also</span></span>

[<span data-ttu-id="769cd-139">Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="769cd-139">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="769cd-140">Identità federata per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="769cd-140">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)


