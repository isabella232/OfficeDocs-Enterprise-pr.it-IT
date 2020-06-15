---
title: Fase 2 dell'autenticazione federata a disponibilità elevata configurare i controller di dominio
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: "Riepilogo: configurare i controller di dominio e il server di sincronizzazione della directory per l'autenticazione federata a disponibilità elevata per Microsoft 365 in Microsoft Azure."
ms.openlocfilehash: 6e75b8787fb5d077cf082d5beb47827c5132706e
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711939"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="0f798-103">Fase 2 dell'autenticazione federata a disponibilità elevata: configurare i controller di dominio</span><span class="sxs-lookup"><span data-stu-id="0f798-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

<span data-ttu-id="0f798-104">In questa fase di distribuzione della disponibilità elevata per l'autenticazione federata di Microsoft 365 nei servizi di infrastruttura di Azure, è possibile configurare due controller di dominio e il server di sincronizzazione della directory nella rete virtuale di Azure.</span><span class="sxs-lookup"><span data-stu-id="0f798-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the directory synchronization server in the Azure virtual network.</span></span> <span data-ttu-id="0f798-105">Le richieste Web client per l'autenticazione possono quindi essere autenticate nella rete virtuale di Azure, anziché inviare tale traffico di autenticazione tramite la connessione VPN da sito a sito alla rete locale.</span><span class="sxs-lookup"><span data-stu-id="0f798-105">Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0f798-106">Active Directory Federation Services (AD FS) non è in grado di utilizzare i servizi di dominio di Azure Active Directory come sostituto dei controller di dominio di servizi di dominio Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0f798-106">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Active Directory Domain Services domain controllers.</span></span> 
  
<span data-ttu-id="0f798-107">È necessario completare questa fase prima di passare alla [fase 3: configurare i server ad FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span><span class="sxs-lookup"><span data-stu-id="0f798-107">You must complete this phase before moving on to [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="0f798-108">Vedere [deploy High Availability Federated Authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) per tutte le fasi.</span><span class="sxs-lookup"><span data-stu-id="0f798-108">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="0f798-109">Creare le macchine virtuali dei controller di dominio in Azure</span><span class="sxs-lookup"><span data-stu-id="0f798-109">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="0f798-110">Per prima cosa, è necessario compilare la colonna **Nome macchina virtuale** della tabella M e modificare le dimensioni della macchina virtuale secondo necessità nella colonna **Dimensioni minime**.</span><span class="sxs-lookup"><span data-stu-id="0f798-110">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="0f798-111">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="0f798-111">**Item**</span></span>|<span data-ttu-id="0f798-112">**Nome macchina virtuale**</span><span class="sxs-lookup"><span data-stu-id="0f798-112">**Virtual machine name**</span></span>|<span data-ttu-id="0f798-113">**Immagine della raccolta**</span><span class="sxs-lookup"><span data-stu-id="0f798-113">**Gallery image**</span></span>|<span data-ttu-id="0f798-114">**Tipo di archiviazione**</span><span class="sxs-lookup"><span data-stu-id="0f798-114">**Storage type**</span></span>|<span data-ttu-id="0f798-115">**Dimensioni minime**</span><span class="sxs-lookup"><span data-stu-id="0f798-115">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="0f798-116">1.</span><span class="sxs-lookup"><span data-stu-id="0f798-116">1.</span></span>  <br/> |![riga](./media/Common-Images/TableLine.png) <span data-ttu-id="0f798-118">______________ (primo controller di dominio, ad esempio DC1)</span><span class="sxs-lookup"><span data-stu-id="0f798-118">(first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="0f798-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0f798-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0f798-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0f798-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0f798-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0f798-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0f798-122">2.</span><span class="sxs-lookup"><span data-stu-id="0f798-122">2.</span></span>  <br/> |![riga](./media/Common-Images/TableLine.png) <span data-ttu-id="0f798-124">______________ (secondo controller di dominio, ad esempio DC2)</span><span class="sxs-lookup"><span data-stu-id="0f798-124">(second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="0f798-125">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0f798-125">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0f798-126">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0f798-126">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0f798-127">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0f798-127">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0f798-128">3.</span><span class="sxs-lookup"><span data-stu-id="0f798-128">3.</span></span>  <br/> |![riga](./media/Common-Images/TableLine.png) <span data-ttu-id="0f798-130">(server di sincronizzazione della directory, esempio DS1)</span><span class="sxs-lookup"><span data-stu-id="0f798-130">(directory synchronization server, example DS1)</span></span>  <br/> |<span data-ttu-id="0f798-131">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0f798-131">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0f798-132">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0f798-132">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0f798-133">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0f798-133">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0f798-134">4.</span><span class="sxs-lookup"><span data-stu-id="0f798-134">4.</span></span>  <br/> |![riga](./media/Common-Images/TableLine.png) <span data-ttu-id="0f798-136">(primo server AD FS, esempio ADFS1)</span><span class="sxs-lookup"><span data-stu-id="0f798-136">(first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="0f798-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0f798-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0f798-138">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0f798-138">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0f798-139">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0f798-139">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0f798-140">5.</span><span class="sxs-lookup"><span data-stu-id="0f798-140">5.</span></span>  <br/> |![riga](./media/Common-Images/TableLine.png) <span data-ttu-id="0f798-142">(secondo server AD FS, ad esempio ADFS2)</span><span class="sxs-lookup"><span data-stu-id="0f798-142">(second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="0f798-143">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0f798-143">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0f798-144">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0f798-144">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0f798-145">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0f798-145">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0f798-146">6.</span><span class="sxs-lookup"><span data-stu-id="0f798-146">6.</span></span>  <br/> |![riga](./media/Common-Images/TableLine.png) <span data-ttu-id="0f798-148">(primo server proxy di applicazione Web, esempio WEB1)</span><span class="sxs-lookup"><span data-stu-id="0f798-148">(first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="0f798-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0f798-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0f798-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0f798-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0f798-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0f798-151">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="0f798-152">7.</span><span class="sxs-lookup"><span data-stu-id="0f798-152">7.</span></span>  <br/> |![riga](./media/Common-Images/TableLine.png) <span data-ttu-id="0f798-154">(secondo server proxy di applicazione Web, ad esempio App2)</span><span class="sxs-lookup"><span data-stu-id="0f798-154">(second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="0f798-155">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="0f798-155">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="0f798-156">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="0f798-156">Standard_LRS</span></span>  <br/> |<span data-ttu-id="0f798-157">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="0f798-157">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="0f798-158">**Tabella M-macchine virtuali per l'autenticazione federata a disponibilità elevata per Microsoft 365 in Azure**</span><span class="sxs-lookup"><span data-stu-id="0f798-158">**Table M - Virtual machines for the high availability federated authentication for Microsoft 365 in Azure**</span></span>
  
<span data-ttu-id="0f798-159">Per l'elenco completo delle dimensioni delle macchine virtuali, vedere [Dimensioni delle macchine virtuali](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span><span class="sxs-lookup"><span data-stu-id="0f798-159">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="0f798-160">Il seguente blocco di comandi di Azure PowerShell consente di creare le macchine virtuali per i due controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="0f798-160">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="0f798-161">Specificare i valori per le variabili, eliminando i \< and > caratteri.</span><span class="sxs-lookup"><span data-stu-id="0f798-161">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="0f798-162">Si noti che il blocco di comandi di Azure PowerShell utilizza i valori indicati nelle tabelle riportate di seguito:</span><span class="sxs-lookup"><span data-stu-id="0f798-162">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="0f798-163">Tabella M, per le macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="0f798-163">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="0f798-164">Tabella R, per i gruppi di risorse</span><span class="sxs-lookup"><span data-stu-id="0f798-164">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="0f798-165">Tabella V, per le impostazioni della rete virtuale</span><span class="sxs-lookup"><span data-stu-id="0f798-165">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="0f798-166">Tabella S, per le subnet</span><span class="sxs-lookup"><span data-stu-id="0f798-166">Table S, for your subnets</span></span>
    
- <span data-ttu-id="0f798-167">Tabella I, per gli indirizzi IP statici</span><span class="sxs-lookup"><span data-stu-id="0f798-167">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="0f798-168">Tabella A, per i set di disponibilità</span><span class="sxs-lookup"><span data-stu-id="0f798-168">Table A, for your availability sets</span></span>
    
<span data-ttu-id="0f798-169">Ricordare che sono state definite le tabelle R, V, S, I e A nella [fase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="0f798-169">Recall that you defined Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0f798-170">[!NOTA] I seguenti comandi consentono di utilizzare la versione più recente di Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f798-170">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="0f798-171">Vedere [Introduzione a PowerShell di Azure](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span><span class="sxs-lookup"><span data-stu-id="0f798-171">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="0f798-172">Una volta forniti tutti i valori corretti, eseguire il blocco risultante nel prompt di Azure PowerShell oppure in PowerShell Integrated Script Environment (ISE) nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="0f798-172">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="0f798-173">Per generare blocchi di comandi di PowerShell pronti per l'esecuzione in base alle impostazioni personalizzate, utilizzare questa [cartella di lavoro di configurazione di Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span><span class="sxs-lookup"><span data-stu-id="0f798-173">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="0f798-p105">Poiché queste macchine virtuali sono per un'applicazione Intranet, non sono assegnate a un indirizzo IP pubblico o a un'etichetta del nome di dominio DNS ed esposte a Internet. Tuttavia, ciò significa anche che non è possibile connettersi a tali macchine virtuali dal portale di Azure. L'opzione **Connetti** non è disponibile quando si visualizzano le proprietà della macchina virtuale. Usare l'accessorio Connessione desktop remoto o un altro strumento Desktop remoto per connettersi alla macchina virtuale usando il relativo indirizzo IP privato o il nome DNS Intranet.</span><span class="sxs-lookup"><span data-stu-id="0f798-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="0f798-178">Configurare il primo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="0f798-178">Configure the first domain controller</span></span>

<span data-ttu-id="0f798-p106">Usare il client desktop remoto di propria scelta e creare una connessione desktop remoto per la macchina virtuale del primo controller di dominio. Usare il nome DNS Intranet o il nome computer e le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="0f798-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="0f798-181">Successivamente, aggiungere il disco dati aggiuntivo al primo controller di dominio con questo comando da un prompt dei comandi di Windows PowerShell **sulla prima macchina virtuale del controller di dominio**:</span><span class="sxs-lookup"><span data-stu-id="0f798-181">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="0f798-182">Successivamente, verificare la connettività del primo controller di dominio per i percorsi della rete aziendale tramite il comando **ping** per i nomi di ping e gli indirizzi IP delle risorse nella rete dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="0f798-182">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="0f798-p107">Questa procedura assicura che la risoluzione dei nomi DNS funziona correttamente (che la macchina virtuale è configurata correttamente con i server DNS locali) e che possono essere inviati pacchetti da e verso la rete virtuale cross-premise. Se il test ha esito negativo, contattare il proprio reparto IT per risolvere i problemi relativi alla risoluzione del nome DNS e al recapito dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="0f798-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="0f798-185">Successivamente, dal prompt dei comandi di Windows PowerShell nel primo controller di dominio, eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="0f798-185">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="0f798-p108">Verrà richiesto di fornire le credenziali di un account di amministratore del dominio. Il computer viene riavviato.</span><span class="sxs-lookup"><span data-stu-id="0f798-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="0f798-188">Configurare il secondo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="0f798-188">Configure the second domain controller</span></span>

<span data-ttu-id="0f798-p109">Usare il client desktop remoto di propria scelta e creare una connessione desktop remoto per la macchina virtuale del secondo controller di dominio. Usare il nome DNS Intranet o il nome computer e le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="0f798-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="0f798-191">Successivamente, è necessario aggiungere il disco dati aggiuntivo al secondo controller di dominio con questo comando da un prompt dei comandi di Windows PowerShell **sul secondo computer virtuale del controller di dominio**:</span><span class="sxs-lookup"><span data-stu-id="0f798-191">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="0f798-192">Quindi, eseguire i seguenti comandi:</span><span class="sxs-lookup"><span data-stu-id="0f798-192">Next, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="0f798-p110">Verrà richiesto di fornire le credenziali di un account di amministratore del dominio. Il computer viene riavviato.</span><span class="sxs-lookup"><span data-stu-id="0f798-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="0f798-195">Successivamente, è necessario aggiornare i server DNS per la rete virtuale in modo che Azure assegni le macchine virtuali agli indirizzi IP dei due nuovi controller di dominio da utilizzare come server DNS.</span><span class="sxs-lookup"><span data-stu-id="0f798-195">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="0f798-196">Inserire le variabili e quindi eseguire questi comandi da un prompt dei comandi di Windows PowerShell nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="0f798-196">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="0f798-p112">Si noti che i due controller di dominio vengono riavviati in modo che non siano configurati con i server DNS locali come server DNS. Trattandosi di due server DNS, sono stati configurati automaticamente con i server DNS locali come server d'inoltro quando sono stati promossi a controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="0f798-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="0f798-p113">Successivamente, è necessario creare un sito di replica di Active Directory per assicurarsi che i server della rete virtuale di Azure utilizzino i controller di dominio locali. Connettersi a uno dei due controller di dominio con un account di amministratore di dominio ed eseguire i comandi seguenti dal prompt dei comandi di Windows PowerShell a livello di amministratore:</span><span class="sxs-lookup"><span data-stu-id="0f798-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a><span data-ttu-id="0f798-201">Configurare il server di sincronizzazione della directory</span><span class="sxs-lookup"><span data-stu-id="0f798-201">Configure the directory synchronization server</span></span>

<span data-ttu-id="0f798-202">Utilizzare il client desktop remoto di propria scelta e creare una connessione Desktop remoto alla macchina virtuale del server di sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="0f798-202">Use the remote desktop client of your choice and create a remote desktop connection to the directory synchronization server virtual machine.</span></span> <span data-ttu-id="0f798-203">Usare il nome DNS Intranet o il nome computer e le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="0f798-203">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="0f798-204">Successivamente, aggiungerlo al dominio AD DS appropriato con questi comandi nel prompt di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f798-204">Next, join it to the appropriate AD DS domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="0f798-205">Di seguito è riportata la configurazione risultante dal completamento corretto di questa fase, con i nomi computer segnaposto.</span><span class="sxs-lookup"><span data-stu-id="0f798-205">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="0f798-206">**Fase 2: i controller di dominio e il server di sincronizzazione della directory per l'infrastruttura di autenticazione federata a disponibilità elevata in Azure**</span><span class="sxs-lookup"><span data-stu-id="0f798-206">**Phase 2: The domain controllers and directory synchronization server for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 2 dell'infrastruttura di autenticazione federata Microsoft 365 a disponibilità elevata in Azure con controller di dominio](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="0f798-208">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="0f798-208">Next step</span></span>

<span data-ttu-id="0f798-209">Utilizzare la [fase 3: configurare i server ad FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) per continuare a configurare il carico di lavoro.</span><span class="sxs-lookup"><span data-stu-id="0f798-209">Use [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0f798-210">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0f798-210">See Also</span></span>

[<span data-ttu-id="0f798-211">Distribuire l'autenticazione federata a disponibilità elevata per Microsoft 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="0f798-211">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="0f798-212">Identità federata per l'ambiente di sviluppo/test di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="0f798-212">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="0f798-213">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="0f798-213">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)


