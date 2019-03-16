---
title: Fase 2 dell'autenticazione federata a disponibilità elevata configurare i controller di dominio
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
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: "Riepilogo: Configurare i controller di dominio e il server DirSync per l'autenticazione federata a disponibilità elevata per Office 365 in Microsoft Azure."
ms.openlocfilehash: 5ca31f33ef75aeb00dee724dfc6bc86df51cbfef
ms.sourcegitcommit: b85d3db24385d7e0bdbfb0d4499174ccd7f573bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "30650129"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="ce030-103">Fase 2 dell'autenticazione federata a disponibilità elevata: configurare i controller di dominio</span><span class="sxs-lookup"><span data-stu-id="ce030-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="ce030-104">**Riepilogo:** Configurare i controller di dominio e il server DirSync per l'autenticazione federata a disponibilità elevata per Office 365 in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="ce030-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="ce030-p101">In questa fase di distribuzione di disponibilità elevata per l'autenticazione federata di Office 365 nei servizi dell'infrastruttura di Azure, si configurano due controller di dominio e il server DirSync nella rete virtuale Azure. Le richieste Web client per l'autenticazione possono quindi essere autenticate nella rete virtuale di Azure, anziché inviare tale traffico di autenticazione tramite la connessione VPN da sito a sito alla rete locale.</span><span class="sxs-lookup"><span data-stu-id="ce030-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ce030-107">In Active Directory Federation Services (AD FS) non è possibile utilizzare Azure Active Directory Domain Services al posto dei controller di dominio di Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="ce030-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Windows Server AD domain controllers.</span></span> 
  
<span data-ttu-id="ce030-108">È necessario completare questa fase prima di passare a [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span><span class="sxs-lookup"><span data-stu-id="ce030-108">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="ce030-109">Vedere [Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) per tutte le fasi.</span><span class="sxs-lookup"><span data-stu-id="ce030-109">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="ce030-110">Creare le macchine virtuali dei controller di dominio in Azure</span><span class="sxs-lookup"><span data-stu-id="ce030-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="ce030-111">Per prima cosa, è necessario compilare la colonna **Nome macchina virtuale** della tabella M e modificare le dimensioni della macchina virtuale secondo necessità nella colonna **Dimensioni minime**.</span><span class="sxs-lookup"><span data-stu-id="ce030-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="ce030-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ce030-112">**Item**</span></span>|<span data-ttu-id="ce030-113">**Nome macchina virtuale**</span><span class="sxs-lookup"><span data-stu-id="ce030-113">**Virtual machine name**</span></span>|<span data-ttu-id="ce030-114">**Immagine della raccolta**</span><span class="sxs-lookup"><span data-stu-id="ce030-114">**Gallery image**</span></span>|<span data-ttu-id="ce030-115">**Tipo di archiviazione**</span><span class="sxs-lookup"><span data-stu-id="ce030-115">**Storage type**</span></span>|<span data-ttu-id="ce030-116">**Dimensioni minime**</span><span class="sxs-lookup"><span data-stu-id="ce030-116">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="ce030-117">1.</span><span class="sxs-lookup"><span data-stu-id="ce030-117">1.</span></span>  <br/> |<span data-ttu-id="ce030-118">![](./media/Common-Images/TableLine.png)______________ (primo controller di dominio, ad esempio DC1)</span><span class="sxs-lookup"><span data-stu-id="ce030-118">![](./media/Common-Images/TableLine.png) (first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="ce030-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ce030-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ce030-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ce030-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ce030-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ce030-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ce030-122">2.</span><span class="sxs-lookup"><span data-stu-id="ce030-122">2.</span></span>  <br/> |<span data-ttu-id="ce030-123">![](./media/Common-Images/TableLine.png)______________ (secondo controller di dominio, ad esempio DC2)</span><span class="sxs-lookup"><span data-stu-id="ce030-123">![](./media/Common-Images/TableLine.png) (second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="ce030-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ce030-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ce030-125">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ce030-125">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ce030-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ce030-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ce030-127">3.</span><span class="sxs-lookup"><span data-stu-id="ce030-127">3.</span></span>  <br/> |<span data-ttu-id="ce030-128">![](./media/Common-Images/TableLine.png)(Server DirSync, esempio DS1)</span><span class="sxs-lookup"><span data-stu-id="ce030-128">![](./media/Common-Images/TableLine.png) (DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="ce030-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ce030-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ce030-130">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ce030-130">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ce030-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ce030-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ce030-132">4.</span><span class="sxs-lookup"><span data-stu-id="ce030-132">4.</span></span>  <br/> |<span data-ttu-id="ce030-133">![](./media/Common-Images/TableLine.png)(primo server AD FS, esempio ADFS1)</span><span class="sxs-lookup"><span data-stu-id="ce030-133">![](./media/Common-Images/TableLine.png) (first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="ce030-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ce030-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ce030-135">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ce030-135">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ce030-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ce030-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ce030-137">5.</span><span class="sxs-lookup"><span data-stu-id="ce030-137">5.</span></span>  <br/> |<span data-ttu-id="ce030-138">![](./media/Common-Images/TableLine.png)(secondo server AD FS, ad esempio ADFS2)</span><span class="sxs-lookup"><span data-stu-id="ce030-138">![](./media/Common-Images/TableLine.png) (second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="ce030-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ce030-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ce030-140">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ce030-140">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ce030-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ce030-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ce030-142">6.</span><span class="sxs-lookup"><span data-stu-id="ce030-142">6.</span></span>  <br/> |<span data-ttu-id="ce030-143">![](./media/Common-Images/TableLine.png)(primo server proxy di applicazione Web, esempio WEB1)</span><span class="sxs-lookup"><span data-stu-id="ce030-143">![](./media/Common-Images/TableLine.png) (first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="ce030-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ce030-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ce030-145">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ce030-145">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ce030-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ce030-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="ce030-147">7.</span><span class="sxs-lookup"><span data-stu-id="ce030-147">7.</span></span>  <br/> |<span data-ttu-id="ce030-148">![](./media/Common-Images/TableLine.png)(secondo server proxy di applicazione Web, ad esempio App2)</span><span class="sxs-lookup"><span data-stu-id="ce030-148">![](./media/Common-Images/TableLine.png) (second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="ce030-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="ce030-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="ce030-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="ce030-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="ce030-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="ce030-151">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="ce030-152">**Tabella M-macchine virtuali per l'autenticazione federata a disponibilità elevata per Office 365 in Azure**</span><span class="sxs-lookup"><span data-stu-id="ce030-152">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="ce030-153">Per l'elenco completo delle dimensioni delle macchine virtuali, vedere [Dimensioni delle macchine virtuali](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span><span class="sxs-lookup"><span data-stu-id="ce030-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="ce030-154">Il seguente blocco di comandi di Azure PowerShell consente di creare le macchine virtuali per i due controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="ce030-154">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="ce030-155">Specificare i valori per le variabili, rimuovendo \< i caratteri e >.</span><span class="sxs-lookup"><span data-stu-id="ce030-155">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="ce030-156">Si noti che il blocco di comandi di Azure PowerShell utilizza i valori indicati nelle tabelle riportate di seguito:</span><span class="sxs-lookup"><span data-stu-id="ce030-156">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="ce030-157">Tabella M, per le macchine virtuali</span><span class="sxs-lookup"><span data-stu-id="ce030-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="ce030-158">Tabella R, per i gruppi di risorse</span><span class="sxs-lookup"><span data-stu-id="ce030-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="ce030-159">Tabella V, per le impostazioni della rete virtuale</span><span class="sxs-lookup"><span data-stu-id="ce030-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="ce030-160">Tabella S, per le subnet</span><span class="sxs-lookup"><span data-stu-id="ce030-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="ce030-161">Tabella I, per gli indirizzi IP statici</span><span class="sxs-lookup"><span data-stu-id="ce030-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="ce030-162">Tabella A, per i set di disponibilità</span><span class="sxs-lookup"><span data-stu-id="ce030-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="ce030-163">Tenere presente che le tabelle R, V, S, i e A sono definite in [fase 1 di autenticazione federata a disponibilità elevata: configurare Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="ce030-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="ce030-p104">I seguenti comandi consentono di utilizzare la versione più recente di Azure PowerShell. Vedere [Panoramica dei cmdlet di Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="ce030-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="ce030-166">Una volta forniti tutti i valori corretti, eseguire il blocco risultante nel prompt di Azure PowerShell oppure in PowerShell Integrated Script Environment (ISE) nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="ce030-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
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
$diskSize=<size of the extra disk for Windows Server AD data in GB>

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
$diskSize=<size of the extra disk for Windows Server AD data in GB>

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

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="ce030-p105">Poiché queste macchine virtuali sono per un'applicazione Intranet, non sono assegnate a un indirizzo IP pubblico o a un'etichetta del nome di dominio DNS ed esposte a Internet. Tuttavia, ciò significa anche che non è possibile connettersi a tali macchine virtuali dal portale di Azure. L'opzione **Connetti** non è disponibile quando si visualizzano le proprietà della macchina virtuale. Usare l'accessorio Connessione desktop remoto o un altro strumento Desktop remoto per connettersi alla macchina virtuale usando il relativo indirizzo IP privato o il nome DNS Intranet.</span><span class="sxs-lookup"><span data-stu-id="ce030-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="ce030-171">Configurare il primo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="ce030-171">Configure the first domain controller</span></span>

<span data-ttu-id="ce030-p106">Usare il client desktop remoto di propria scelta e creare una connessione desktop remoto per la macchina virtuale del primo controller di dominio. Usare il nome DNS Intranet o il nome computer e le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="ce030-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="ce030-174">Successivamente, aggiungere il disco dati aggiuntivo al primo controller di dominio con questo comando da un prompt dei comandi di Windows PowerShell **sulla prima macchina virtuale del controller di dominio**:</span><span class="sxs-lookup"><span data-stu-id="ce030-174">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="ce030-175">Successivamente, verificare la connettività del primo controller di dominio per i percorsi della rete aziendale tramite il comando **ping** per i nomi di ping e gli indirizzi IP delle risorse nella rete dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="ce030-175">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="ce030-p107">Questa procedura assicura che la risoluzione dei nomi DNS funziona correttamente (che la macchina virtuale è configurata correttamente con i server DNS locali) e che possono essere inviati pacchetti da e verso la rete virtuale cross-premise. Se il test ha esito negativo, contattare il proprio reparto IT per risolvere i problemi relativi alla risoluzione del nome DNS e al recapito dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="ce030-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="ce030-178">Successivamente, dal prompt dei comandi di Windows PowerShell nel primo controller di dominio, eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="ce030-178">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="ce030-p108">Verrà richiesto di fornire le credenziali di un account di amministratore del dominio. Il computer viene riavviato.</span><span class="sxs-lookup"><span data-stu-id="ce030-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="ce030-181">Configurare il secondo controller di dominio</span><span class="sxs-lookup"><span data-stu-id="ce030-181">Configure the second domain controller</span></span>

<span data-ttu-id="ce030-p109">Usare il client desktop remoto di propria scelta e creare una connessione desktop remoto per la macchina virtuale del secondo controller di dominio. Usare il nome DNS Intranet o il nome computer e le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="ce030-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="ce030-184">Successivamente, è necessario aggiungere il disco dati aggiuntivo al secondo controller di dominio con questo comando da un prompt dei comandi di Windows PowerShell **sul secondo computer virtuale del controller di dominio**:</span><span class="sxs-lookup"><span data-stu-id="ce030-184">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="ce030-185">Quindi, eseguire i seguenti comandi:</span><span class="sxs-lookup"><span data-stu-id="ce030-185">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="ce030-p110">Verrà richiesto di fornire le credenziali di un account di amministratore del dominio. Il computer viene riavviato.</span><span class="sxs-lookup"><span data-stu-id="ce030-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="ce030-188">Successivamente, è necessario aggiornare i server DNS per la rete virtuale in modo che Azure assegni le macchine virtuali agli indirizzi IP dei due nuovi controller di dominio da utilizzare come server DNS.</span><span class="sxs-lookup"><span data-stu-id="ce030-188">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="ce030-189">Inserire le variabili e quindi eseguire questi comandi da un prompt dei comandi di Windows PowerShell nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="ce030-189">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```
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

<span data-ttu-id="ce030-p112">Si noti che i due controller di dominio vengono riavviati in modo che non siano configurati con i server DNS locali come server DNS. Trattandosi di due server DNS, sono stati configurati automaticamente con i server DNS locali come server d'inoltro quando sono stati promossi a controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="ce030-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="ce030-p113">Successivamente, è necessario creare un sito di replica di Active Directory per assicurarsi che i server della rete virtuale di Azure utilizzino i controller di dominio locali. Connettersi a uno dei due controller di dominio con un account di amministratore di dominio ed eseguire i comandi seguenti dal prompt dei comandi di Windows PowerShell a livello di amministratore:</span><span class="sxs-lookup"><span data-stu-id="ce030-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="ce030-194">Configurare il server DirSync</span><span class="sxs-lookup"><span data-stu-id="ce030-194">Configure the DirSync server</span></span>

<span data-ttu-id="ce030-195">Utilizzare il client desktop remoto di propria scelta e creare una connessione Desktop remoto alla macchina virtuale del server DirSync.</span><span class="sxs-lookup"><span data-stu-id="ce030-195">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine.</span></span> <span data-ttu-id="ce030-196">Usare il nome DNS Intranet o il nome computer e le credenziali dell'account di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="ce030-196">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="ce030-197">Successivamente, aggiungerlo al dominio di Windows Server AD appropriato con questi comandi nel prompt dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce030-197">Next, join it to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="ce030-198">Di seguito è riportata la configurazione risultante dal completamento corretto di questa fase, con i nomi computer segnaposto.</span><span class="sxs-lookup"><span data-stu-id="ce030-198">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="ce030-199">**Fase 2: i controller di dominio e il server DirSync per l'infrastruttura dell'autenticazione federata a disponibilità elevata in Azure**</span><span class="sxs-lookup"><span data-stu-id="ce030-199">**Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 2 dell'infrastruttura di autenticazione federata di Office 365 a disponibilità elevata in Azure con controller di dominio](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="ce030-201">Passaggio successivo</span><span class="sxs-lookup"><span data-stu-id="ce030-201">Next step</span></span>

<span data-ttu-id="ce030-202">Utilizzare [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) per continuare a configurare il carico di lavoro.</span><span class="sxs-lookup"><span data-stu-id="ce030-202">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ce030-203">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ce030-203">See Also</span></span>

[<span data-ttu-id="ce030-204">Distribuire l'autenticazione federata ad alta visibilità per Office 365 in Azure</span><span class="sxs-lookup"><span data-stu-id="ce030-204">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="ce030-205">Identità federata per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="ce030-205">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="ce030-206">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="ce030-206">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="ce030-207">Opzioni di autenticazione federata</span><span class="sxs-lookup"><span data-stu-id="ce030-207">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


