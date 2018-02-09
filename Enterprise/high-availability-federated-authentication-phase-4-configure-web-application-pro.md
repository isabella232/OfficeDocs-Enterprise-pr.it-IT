---
title: "Disponibilità elevata federati proxy di applicazione web fase 4 configurare l'autenticazione"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: "Riepilogo: Configurare il server proxy applicazione web per l'autenticazione federata la disponibilità elevata per Office 365 in Microsoft Azure."
ms.openlocfilehash: 3465281c6ba27c52cc7a991e400fb4f4a892b244
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="c696d-103">Fase 4 dell'autenticazione federata a disponibilità elevata: Configurare i proxy dell'applicazione Web</span><span class="sxs-lookup"><span data-stu-id="c696d-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

 <span data-ttu-id="c696d-104">**Riepilogo:** Configurare il server proxy applicazione web per l'autenticazione federata la disponibilità elevata per Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c696d-104">**Summary:** Configure the web application proxy servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="c696d-105">In questa fase di distribuzione di disponibilità elevata per l'autenticazione federata di Office 365 nei servizi infrastruttura di Azure, viene creato un bilanciamento del carico interno e due server AD FS.</span><span class="sxs-lookup"><span data-stu-id="c696d-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="c696d-p101">È necessario completare prima di spostare in questa fase [la disponibilità elevata federati autenticazione fase 5: configurare l'autenticazione federata per Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Per tutte le fasi, vedere [Deploy la disponibilità elevata nell'autenticazione federata per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) .</span><span class="sxs-lookup"><span data-stu-id="c696d-p101">You must complete this phase before moving on to [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="c696d-108">Creare il bilanciatore di carico per traffico Internet in Azure</span><span class="sxs-lookup"><span data-stu-id="c696d-108">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="c696d-109">È necessario creare un bilanciatore di carico per traffico Internet affinché Azure distribuisca il traffico di autenticazione del client in arrivo da Internet uniformemente tra i due server proxy dell'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="c696d-109">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c696d-p102">Il seguente comando consente di utilizzare la versione più recente di Azure PowerShell. Vedere [iniziare a utilizzare i cmdlet PowerShell di Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="c696d-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="c696d-112">Una volta forniti i valori per i gruppi di risorse e il percorso, eseguire il blocco risultante nel prompt dei comandi di Azure PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c696d-112">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="c696d-113">Per un file di testo che contiene tutti i comandi di PowerShell in questo articolo e una cartella di lavoro configurazione Microsoft Excel che genera pronto a portata di blocchi di comandi di PowerShell in base alle impostazioni personalizzate, vedere [autenticazione federata per Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="c696d-113">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzureRmPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzureRmLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="c696d-114">Per visualizzare l'indirizzo IP pubblico assegnato al bilanciatore di carico per traffico Internet, eseguire questi comandi nel prompt dei comandi di Azure PowerShell nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="c696d-114">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="c696d-115">Determinare il nome di dominio completo del servizio federativo e creare record DNS</span><span class="sxs-lookup"><span data-stu-id="c696d-115">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="c696d-p103">È necessario determinare il nome DNS per identificare il nome del servizio federativo su Internet. Azure AD Connect configurerà Office 365 con questo nome nella fase 5, che diventerà parte dell'URL inviato da Office 365 per connettere i client per ottenere token di sicurezza. Un esempio è fs.contoso.com (dove fs è l'acronimo di federation service, cioè servizio federativo).</span><span class="sxs-lookup"><span data-stu-id="c696d-p103">You need to determine the DNS name to identify your federation service name on the Internet. Azure AD Connect will configure Office 365 with this name in Phase 5, which will become part of the URL that Office 365 sends to connecting clients to get a security token. An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="c696d-119">Una volta ottenuto il nome di dominio completo del servizio federativo, creare un record di tipo A del dominio DNS pubblico per il nome di dominio completo che consente di determinare l'indirizzo IP pubblico del bilanciatore di carico per traffico Internet di Azure.</span><span class="sxs-lookup"><span data-stu-id="c696d-119">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="c696d-120">**Name**</span><span class="sxs-lookup"><span data-stu-id="c696d-120">**Name**</span></span>|<span data-ttu-id="c696d-121">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="c696d-121">**Type**</span></span>|<span data-ttu-id="c696d-122">**TTL**</span><span class="sxs-lookup"><span data-stu-id="c696d-122">**TTL**</span></span>|<span data-ttu-id="c696d-123">**Valore**</span><span class="sxs-lookup"><span data-stu-id="c696d-123">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="c696d-124">Nome di dominio completo del servizio federativo</span><span class="sxs-lookup"><span data-stu-id="c696d-124">federation service FDQN</span></span>  <br/> |<span data-ttu-id="c696d-125">A</span><span class="sxs-lookup"><span data-stu-id="c696d-125">A</span></span>  <br/> |<span data-ttu-id="c696d-126">3600</span><span class="sxs-lookup"><span data-stu-id="c696d-126">3600</span></span>  <br/> |<span data-ttu-id="c696d-127">indirizzo IP pubblico del bilanciamento del carico per Internet di Azure (visualizzato dal comando di **Write-Host** nella sezione precedente)</span><span class="sxs-lookup"><span data-stu-id="c696d-127">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="c696d-128">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="c696d-128">Here is an example:</span></span>
  
|<span data-ttu-id="c696d-129">**Name**</span><span class="sxs-lookup"><span data-stu-id="c696d-129">**Name**</span></span>|<span data-ttu-id="c696d-130">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="c696d-130">**Type**</span></span>|<span data-ttu-id="c696d-131">**TTL**</span><span class="sxs-lookup"><span data-stu-id="c696d-131">**TTL**</span></span>|<span data-ttu-id="c696d-132">**Valore**</span><span class="sxs-lookup"><span data-stu-id="c696d-132">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="c696d-133">FS.contoso.com</span><span class="sxs-lookup"><span data-stu-id="c696d-133">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="c696d-134">A</span><span class="sxs-lookup"><span data-stu-id="c696d-134">A</span></span>  <br/> |<span data-ttu-id="c696d-135">3600</span><span class="sxs-lookup"><span data-stu-id="c696d-135">3600</span></span>  <br/> |<span data-ttu-id="c696d-136">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="c696d-136">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="c696d-137">Successivamente, aggiungere un record di indirizzo DNS allo spazio dei nomi DNS privato aziendale che consente di determinare il nome di dominio completo del servizio federativo per l'indirizzo IP privato assegnato al bilanciamento del carico interno per i server AD FS (tabella I, voce 4, colonna Valore).</span><span class="sxs-lookup"><span data-stu-id="c696d-137">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="c696d-138">Creare macchine virtuali per i server proxy delle applicazioni Web in Azure</span><span class="sxs-lookup"><span data-stu-id="c696d-138">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="c696d-139">Utilizzare il seguente blocco di comandi di Azure PowerShell per creare le macchine virtuali per i due server proxy delle applicazioni Web. </span><span class="sxs-lookup"><span data-stu-id="c696d-139">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="c696d-140">Si noti che i seguenti set di comandi di Azure PowerShell utilizzano i valori indicati nelle tabelle riportate di seguito:</span><span class="sxs-lookup"><span data-stu-id="c696d-140">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="c696d-141">Tabella M, per le macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="c696d-141">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="c696d-142">Tabella R, per i gruppi di risorse</span><span class="sxs-lookup"><span data-stu-id="c696d-142">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="c696d-143">Tabella V, per le impostazioni della rete virtuale</span><span class="sxs-lookup"><span data-stu-id="c696d-143">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="c696d-144">Tabella S, per le subnet</span><span class="sxs-lookup"><span data-stu-id="c696d-144">Table S, for your subnets</span></span>
    
- <span data-ttu-id="c696d-145">Tabella I, per gli indirizzi IP statici</span><span class="sxs-lookup"><span data-stu-id="c696d-145">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="c696d-146">Tabella A, per i set di disponibilità</span><span class="sxs-lookup"><span data-stu-id="c696d-146">Table A, for your availability sets</span></span>
    
<span data-ttu-id="c696d-147">Richiamare una definite tabella M in [la disponibilità elevata federati autenticazione fase 2: configurare i controller di dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) e tabelle R, V, S, è possibile e A in [la disponibilità elevata federati autenticazione fase 1: configurare Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="c696d-147">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="c696d-148">Una volta forniti tutti i valori opportuni, eseguire il blocco risultante nel prompt dei comandi di Azure PowerShell o in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c696d-148">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="c696d-p104">Dal momento che queste macchine virtuali sono relative a un'applicazione intranet, non vengono assegnati un indirizzo IP pubblico o un'etichetta nome di dominio DNS ed esposti a Internet. Tuttavia, ciò significa inoltre che non è possibile connettersi a tali dal portale di Azure. Quando si visualizzano le proprietà della macchina virtuale non è disponibile l'opzione **Connetti** . Utilizzare accessorio connessione Desktop remoto o un altro strumento di Desktop remoto per la connessione alla macchina virtuale utilizzando il relativo privata indirizzo IP o intranet DNS nome e le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="c696d-p104">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="c696d-153">Di seguito è riportata la configurazione risultante dal completamento corretto di questa fase, con i nomi computer segnaposto.</span><span class="sxs-lookup"><span data-stu-id="c696d-153">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="c696d-154">**Fase 4: Con connessione Internet carico bilanciamento e server proxy di applicazione web per l'infrastruttura di autenticazione federativa la disponibilità elevata in Azure**</span><span class="sxs-lookup"><span data-stu-id="c696d-154">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 4 dell'autenticazione federata di Office 365 con disponibilità elevata in Azure con i server proxy applicazione](images/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="c696d-156">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="c696d-156">Next step</span></span>

<span data-ttu-id="c696d-157">Utilizzare [la disponibilità elevata federati autenticazione fase 5: configurare l'autenticazione federata per Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) per continuare a configurare questo carico di lavoro.</span><span class="sxs-lookup"><span data-stu-id="c696d-157">Use [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c696d-158">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c696d-158">See Also</span></span>

[<span data-ttu-id="c696d-159">Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="c696d-159">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="c696d-160">Identità federata per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-160">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="c696d-161">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="c696d-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="c696d-162">Identità federata per Office 365</span><span class="sxs-lookup"><span data-stu-id="c696d-162">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


