---
title: Ambiente di sviluppo/test della configurazione di base
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Riepilogo: creare una intranet semplificata come ambiente di sviluppo e di testing in Microsoft Azure.'
ms.openlocfilehash: 6d53bb61ea7d325b15590c8aabe0740df3b92750
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193756"
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="f0727-103">Ambiente di sviluppo/test della configurazione di base</span><span class="sxs-lookup"><span data-stu-id="f0727-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="f0727-104">**Riepilogo:** creare una intranet semplificata come ambiente di sviluppo e di testing in Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="f0727-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="f0727-105">In questo articolo vengono fornite istruzioni dettagliate per creare il seguente ambiente di sviluppo/test della configurazione di base in Azure:</span><span class="sxs-lookup"><span data-stu-id="f0727-105">This article provides you with step-by-step instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
<span data-ttu-id="f0727-106">**Figura 1: ambiente di sviluppo/test della configurazione di base**</span><span class="sxs-lookup"><span data-stu-id="f0727-106">**Figure 1: The Base Configuration dev/test environment**</span></span>

![Fase 4 della configurazione base in Azure con la macchina virtuale CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="f0727-p101">L'ambiente di sviluppo/test della configurazione di base nella figura 1 è costituito dalla subnet Corpnet in una rete virtuale di Azure basata solo su cloud denominata TestLab, che simula una intranet privata semplificata connessa a Internet. Contiene tre macchine virtuali Azure che eseguono Windows Server 2016:</span><span class="sxs-lookup"><span data-stu-id="f0727-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It contains three Azure virtual machines running WIndows Server 2016:</span></span>
  
- <span data-ttu-id="f0727-110">DC1 è configurato come un controller di dominio intranet e server Domain Name System (DNS)</span><span class="sxs-lookup"><span data-stu-id="f0727-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="f0727-111">APP1 è configurato come un’applicazione generale e server Web</span><span class="sxs-lookup"><span data-stu-id="f0727-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="f0727-112">CLIENT1 agisce come client intranet</span><span class="sxs-lookup"><span data-stu-id="f0727-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="f0727-113">Questa configurazione consente a DC1 APP1, CLIENT1 e altri computer subnet Corpnet di essere:</span><span class="sxs-lookup"><span data-stu-id="f0727-113">This configuration allows DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="f0727-114">Connessi a Internet per installare gli aggiornamenti, accedere alle risorse Internet in tempo reale e partecipare alle tecnologie basate su cloud pubblico, come Microsoft Office 365 e altri servizi di Azure.</span><span class="sxs-lookup"><span data-stu-id="f0727-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="f0727-115">Gestiti in remoto tramite connessioni da desktop remoto dal proprio computer connesso a Internet o alla rete dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="f0727-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="f0727-116">È possibile utilizzare l'ambiente di test risultante:</span><span class="sxs-lookup"><span data-stu-id="f0727-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="f0727-117">Per lo sviluppo di applicazioni e test.</span><span class="sxs-lookup"><span data-stu-id="f0727-117">For application development and testing.</span></span>
    
- <span data-ttu-id="f0727-118">Come la configurazione iniziale di un ambiente di testing esteso del progetto che include altre macchine virtuali, servizi di Azure o altre offerte cloud Microsoft, ad esempio Office 365 e Enterprise Security + Mobility (EMS).</span><span class="sxs-lookup"><span data-stu-id="f0727-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Security + Mobility (EMS).</span></span>
    
<span data-ttu-id="f0727-119">Esistono quattro fasi per configurare l'ambiente di testing di configurazione di base in Azure:</span><span class="sxs-lookup"><span data-stu-id="f0727-119">There are four phases to setting up the Base Configuration test environment in Azure:</span></span>
  
1. <span data-ttu-id="f0727-120">Creare la rete virtuale.</span><span class="sxs-lookup"><span data-stu-id="f0727-120">Create the virtual network.</span></span>
    
2. <span data-ttu-id="f0727-121">Configurare DC1.</span><span class="sxs-lookup"><span data-stu-id="f0727-121">Configure DC1.</span></span>
    
3. <span data-ttu-id="f0727-122">Configurare APP1.</span><span class="sxs-lookup"><span data-stu-id="f0727-122">Configure APP1.</span></span>
    
4. <span data-ttu-id="f0727-123">Configurare CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="f0727-123">Configure CLIENT1.</span></span>
    
<span data-ttu-id="f0727-p102">Se non si dispone già di un abbonamento Azure, è possibile iscriversi per una versione di valutazione gratuita nella pagina [Crea subito il tuo account Azure gratuito](https://azure.microsoft.com/pricing/free-trial/). Se si dispone di una sottoscrizione MSDN o Visual Studio, vedere [Credito Azure mensile per sottoscrittori di Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="f0727-p102">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="f0727-p103">Le macchine virtuali di Azure in esecuzione comportano un costo. Questo costo viene fatturato in base a sottoscrizione di valutazione, sottoscrizione a MSDN gratuita o a pagamento. Per ulteriori informazioni sui costi dell'esecuzione delle macchine virtuali di Azure, vedere [Prezzi di Macchine virtuali](https://azure.microsoft.com/pricing/details/virtual-machines/) e [Calcolatore prezzi di Azure](https://azure.microsoft.com/pricing/calculator/). Per contenere i costi, vedere [Ridurre al minimo i costi delle macchine virtuali nell’ambiente di testing in Azure](base-configuration-dev-test-environment.md#mincost).</span><span class="sxs-lookup"><span data-stu-id="f0727-p103">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Test Lab Guide nel cloud Microsoft](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="f0727-131">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f0727-131">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-virtual-network"></a><span data-ttu-id="f0727-132">Fase 1: Creare la rete virtuale</span><span class="sxs-lookup"><span data-stu-id="f0727-132">Phase 1: Create the virtual network</span></span>

<span data-ttu-id="f0727-133">Per prima cosa, avviare un prompt di Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0727-133">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f0727-p104">I seguenti comandi consentono di utilizzare la versione più recente di Azure PowerShell. Vedere [Panoramica dei cmdlet di Azure PowerShell](https://docs.microsoft.com/it-IT/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="f0727-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/it-IT/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="f0727-136">Accedere al proprio account Azure con il seguente comando.</span><span class="sxs-lookup"><span data-stu-id="f0727-136">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="f0727-137">Per un file di testo contenente tutti i comandi di PowerShell riportati in questo articolo, fare clic [qui](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d).</span><span class="sxs-lookup"><span data-stu-id="f0727-137">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="f0727-138">Ottenere il nome della sottoscrizione utilizzando il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="f0727-138">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="f0727-p105">Impostare la sottoscrizione di Azure. Sostituire tutto il testo racchiuso tra virgolette, compresi i caratteri < e >, con il nome corretto.</span><span class="sxs-lookup"><span data-stu-id="f0727-p105">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="f0727-p106">In seguito, creare un nuovo gruppo di risorse per il lab di test di configurazione di base. Per determinare un nome del gruppo di risorse univoco, utilizzare questo comando per creare un elenco dei gruppi di risorse esistenti.</span><span class="sxs-lookup"><span data-stu-id="f0727-p106">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="f0727-p107">Creare il nuovo gruppo di risorse con questi comandi. Sostituire tutto il testo racchiuso tra virgolette, compresi i caratteri < e >, con i nomi corretti.</span><span class="sxs-lookup"><span data-stu-id="f0727-p107">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="f0727-145">Successivamente, è possibile creare la rete virtuale TestLab che ospiterà la subnet Corpnet della configurazione di base, proteggendola con un gruppo di sicurezza di rete.</span><span class="sxs-lookup"><span data-stu-id="f0727-145">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

<span data-ttu-id="f0727-146">Questa è la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="f0727-146">This is your current configuration.</span></span>
  
![Fase 1 della configurazione base in Azure con la rete virtuale e subnet](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a><span data-ttu-id="f0727-148">Fase 2: Configurare DC1</span><span class="sxs-lookup"><span data-stu-id="f0727-148">Phase 2: Configure DC1</span></span>

<span data-ttu-id="f0727-149">Nella fase successiva verrà creata la macchina virtuale DC1 e verrà configurata come controller di dominio per il dominio di Windows Server Active Directory (AD) corp.contoso.com e un server DNS per le macchine virtuali della rete virtuale TestLab.</span><span class="sxs-lookup"><span data-stu-id="f0727-149">In this phase, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Windows Server Active Directory (AD) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>
  
<span data-ttu-id="f0727-150">Inserire il nome del gruppo di risorse ed eseguire questi comandi al prompt dei comandi di Azure PowerShell nel computer locale per creare una macchina virtuale di Azure per DC1.</span><span class="sxs-lookup"><span data-stu-id="f0727-150">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType StandardLRS
$diskConfig=New-AzureRmDiskConfig -AccountType StandardLRS -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="f0727-p108">Verrà richiesto nome utente e password dell'account Administrator locale su DC1. Utilizzare una password complessa e annotare nome e password in una posizione sicura.</span><span class="sxs-lookup"><span data-stu-id="f0727-p108">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="f0727-153">Eseguire quindi la connessione alla macchina virtuale DC1.</span><span class="sxs-lookup"><span data-stu-id="f0727-153">Next, connect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a><span data-ttu-id="f0727-154">Connettersi a DC1 usando le credenziali dell'account Administrator locale</span><span class="sxs-lookup"><span data-stu-id="f0727-154">Connect to DC1 using local administrator account credentials</span></span>

1. <span data-ttu-id="f0727-155">Nel [Portale di Azure](https://portal.azure.com), fare clic su **Gruppi di risorse >** [nome del nuovo gruppo di risorse] **> DC1 > Connetti**.</span><span class="sxs-lookup"><span data-stu-id="f0727-155">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [the name of your new resource group] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="f0727-p109">Nel riquadro aperto, fare clic su **Scarica file RDP**. Aprire il file DC1.rdp che viene scaricato e quindi fare clic su **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="f0727-p109">In the open pane, click **Download RDP file**. Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="f0727-158">Specificare il nome dell'account Administrator locale DC1:</span><span class="sxs-lookup"><span data-stu-id="f0727-158">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="f0727-159">Per Windows 7:</span><span class="sxs-lookup"><span data-stu-id="f0727-159">For Windows 7:</span></span>
    
    <span data-ttu-id="f0727-p110">Nella finestra di dialogo **Protezione di Windows**, fare clic su **Utilizza un altro account**. In **Nome utente**, digitare **DC1\\**[nome dell'account Administrator locale].</span><span class="sxs-lookup"><span data-stu-id="f0727-p110">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="f0727-162">Per Windows 8 o Windows 10:</span><span class="sxs-lookup"><span data-stu-id="f0727-162">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="f0727-p111">Nella finestra di dialogo **Sicurezza di Windows**, fare clic su **Ulteriori scelte**, quindi fare clic su **Utilizzare un altro account**. In **Nome utente**, digitare **DC1\\**[nome dell'account Administrator locale].</span><span class="sxs-lookup"><span data-stu-id="f0727-p111">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="f0727-165">In **Password**, digitare la password dell’account Administrator locale, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f0727-165">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="f0727-166">Quando viene richiesto, fare clic su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="f0727-166">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="f0727-167">Aggiungere un ulteriore disco dati come nuovo volume con lettera di unità F: immettendo questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore in DC1.</span><span class="sxs-lookup"><span data-stu-id="f0727-167">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="f0727-p112">Configurare quindi DC1 come controller di dominio e il server DNS per il dominio corp.contoso.com. Eseguire questi comandi al prompt dei comandi di Windows PowerShell a livello di amministratore.</span><span class="sxs-lookup"><span data-stu-id="f0727-p112">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
<span data-ttu-id="f0727-p113">Sarà necessario specificare una password di amministratore in modalità provvisoria. Archiviare la password in un percorso sicuro.</span><span class="sxs-lookup"><span data-stu-id="f0727-p113">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="f0727-172">Si tenga presente che il completamento di questi comandi potrebbe richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="f0727-172">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="f0727-173">Dopo il riavvio di DC1, riconnettersi al computer virtuale DC1.</span><span class="sxs-lookup"><span data-stu-id="f0727-173">After DC1 restarts, reconnect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-domain-credentials"></a><span data-ttu-id="f0727-174">Connettersi a DC1 usando le credenziali di dominio</span><span class="sxs-lookup"><span data-stu-id="f0727-174">Connect to DC1 using domain credentials</span></span>

1. <span data-ttu-id="f0727-175">Nel [Portale di Azure](https://portal.azure.com), fare clic su **Gruppi di risorse >** [nome del nuovo gruppo di risorse] **> DC1 > Connetti**.</span><span class="sxs-lookup"><span data-stu-id="f0727-175">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [your resource group name] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="f0727-176">Eseguire il file DC1.rdp che viene scaricato e quindi fare clic su **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="f0727-176">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="f0727-p114">In **Sicurezza di Windows**, fare clic su **Utilizza un altro account**. In **Nome utente**, digitare **CORP\\**[nome dell'account Administrator locale].</span><span class="sxs-lookup"><span data-stu-id="f0727-p114">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="f0727-179">In **Password**, digitare la password dell’account Administrator locale, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f0727-179">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="f0727-180">Quando viene richiesto, fare clic su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="f0727-180">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="f0727-p115">Successivamente, creare un account utente in Active Directory che verrà utilizzato quando si accede a computer membri del dominio CORP. Eseguire questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore.</span><span class="sxs-lookup"><span data-stu-id="f0727-p115">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="f0727-p116">Tenere presente che questo comando chiede di specificare la password dell'account User1. Poiché questo account verrà utilizzato per le connessioni desktop remote per tutti i computer membri del dominio CORP, scegliere una password complessa. Registrare la password dell'account User1 e archiviarla in una posizione sicura.</span><span class="sxs-lookup"><span data-stu-id="f0727-p116">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="f0727-p117">Configurare quindi il nuovo account User1 come amministratore dell'organizzazione. Eseguire questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore.</span><span class="sxs-lookup"><span data-stu-id="f0727-p117">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="f0727-188">Chiudere la sessione Desktop remoto con DC1, quindi riconnettersi usando l'account CORP\\User1.</span><span class="sxs-lookup"><span data-stu-id="f0727-188">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="f0727-189">Successivamente, per consentire il traffico per lo strumento Ping, eseguire questo comando al prompt dei comandi di Windows PowerShell a livello di amministratore.</span><span class="sxs-lookup"><span data-stu-id="f0727-189">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="f0727-190">Questa è la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="f0727-190">This is your current configuration.</span></span>
  
![Fase 2 della configurazione base in Azure con la macchina virtuale DC1](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a><span data-ttu-id="f0727-192">Fase 3: Configurare APP1</span><span class="sxs-lookup"><span data-stu-id="f0727-192">Phase 3: Configure APP1</span></span>

<span data-ttu-id="f0727-193">APP1 fornisce servizi Web e di condivisione file.</span><span class="sxs-lookup"><span data-stu-id="f0727-193">APP1 provides web and file sharing services.</span></span>

-> [!NOTE]  
<span data-ttu-id="f0727-p118">-> Il seguente set di comandi crea CLIENT1 che esegue Windows Server 2016 Data Center. Tale operazione è possibile per tutti i tipi di sottoscrizione di Azure. Se si dispone di una sottoscrizione di Azure basata su Visual Studio, è possibile creare CLIENT1 che esegue Windows 10 con il [Portale di Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="f0727-p118">-> The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10 with the [Azure portal](https://portal.azure.com).</span></span> 

<span data-ttu-id="f0727-196">Inserire il nome del gruppo di risorse ed eseguire questi comandi al prompt dei comandi di Azure PowerShell nel computer locale per creare una macchina virtuale di Azure per APP1.</span><span class="sxs-lookup"><span data-stu-id="f0727-196">To create an Azure Virtual Machine for APP1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType StandardLRS
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="f0727-197">Successivamente, connettersi alla macchina virtuale APP1 usando il nome e la password dell'account Administrator locale di APP1, quindi aprire un prompt dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0727-197">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="f0727-198">Per controllare la risoluzione del nome e la comunicazione della rete tra APP1 e DC1, eseguire il comando **ping dc1.corp.contoso.com** e verificare che siano presenti quattro risposte.</span><span class="sxs-lookup"><span data-stu-id="f0727-198">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="f0727-199">Unire quindi la macchina virtuale APP1 al dominio CORP immettendo questi comandi nel prompt dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0727-199">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="f0727-200">È necessario fornire le credenziali di un account di dominio CORP\\User1 dopo aver eseguito il comando **Add-Computer**.</span><span class="sxs-lookup"><span data-stu-id="f0727-200">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="f0727-201">Dopo il riavvio di APP1, connettersi utilizzando l'account CORP\\User1 e quindi aprire un prompt dei comandi di Windows PowerShell a livello di amministratore.</span><span class="sxs-lookup"><span data-stu-id="f0727-201">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="f0727-202">Successivamente, modificare APP1 in server Web con questo comando al prompt dei comandi di Windows PowerShell in APP1.</span><span class="sxs-lookup"><span data-stu-id="f0727-202">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="f0727-203">Creare quindi una cartella condivisa e un file di testo all'interno della cartella in APP1 con i comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0727-203">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

<span data-ttu-id="f0727-204">Questa è la configurazione corrente.</span><span class="sxs-lookup"><span data-stu-id="f0727-204">This is your current configuration.</span></span>
  
![Fase 3 della configurazione base in Azure con la macchina virtuale APP1](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a><span data-ttu-id="f0727-206">Fase 4: Configurare CLIENT1</span><span class="sxs-lookup"><span data-stu-id="f0727-206">Phase 4: Configure CLIENT1</span></span>

<span data-ttu-id="f0727-207">CLIENT1 agisce come un portatile, tablet o computer desktop tipico sulla intranet Contoso.</span><span class="sxs-lookup"><span data-stu-id="f0727-207">CLIENT1 acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>
  
<span data-ttu-id="f0727-208">Inserire il nome del gruppo di risorse ed eseguire questi comandi al prompt dei comandi di Azure PowerShell nel computer locale per creare una macchina virtuale di Azure per CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="f0727-208">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType StandardLRS
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="f0727-209">Successivamente, connettersi alla macchina virtuale CLIENT1 usando il nome e la password dell'account Administrator locale di CLIENT1, quindi aprire un prompt dei comandi di Windows PowerShell a livello di amministratore.</span><span class="sxs-lookup"><span data-stu-id="f0727-209">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="f0727-210">Per controllare la risoluzione del nome e la comunicazione della rete tra CLIENT1 e DC1, eseguire il comando **ping dc1.corp.contoso.com** al prompt dei comandi di Windows PowerShell e verificare che siano presenti quattro risposte.</span><span class="sxs-lookup"><span data-stu-id="f0727-210">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and verify that there are four replies.</span></span>
  
<span data-ttu-id="f0727-211">Unire quindi la macchina virtuale CLIENT1 al dominio CORP immettendo questi comandi nel prompt dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0727-211">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="f0727-212">È necessario fornire le credenziali di un account di dominio CORP\\User1 dopo aver eseguito il comando **Add-Computer**.</span><span class="sxs-lookup"><span data-stu-id="f0727-212">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="f0727-213">Dopo il riavvio di CLIENT1, connettersi utilizzando nome e password dell'account CORP\\User1 e quindi aprire un prompt dei comandi di Windows PowerShell a livello di amministratore.</span><span class="sxs-lookup"><span data-stu-id="f0727-213">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="f0727-214">Successivamente, verificare che sia possibile accedere alle risorse Web e di condivisione file in APP1 da CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="f0727-214">Next, verify that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
### <a name="verify-client-access-to-app1"></a><span data-ttu-id="f0727-215">Verificare l'accesso CLIENT ad APP1</span><span class="sxs-lookup"><span data-stu-id="f0727-215">Verify CLIENT access to APP1</span></span>

1. <span data-ttu-id="f0727-216">In Server Manager, nel riquadro della struttura, fare clic su **Server locale**.</span><span class="sxs-lookup"><span data-stu-id="f0727-216">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="f0727-217">In **Proprietà per CLIENT1**, fare clic su **Attiva** accanto a **Configurazione sicurezza avanzata IE**.</span><span class="sxs-lookup"><span data-stu-id="f0727-217">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="f0727-218">In **Configurazione sicurezza avanzata IE**, fare clic su **Disattiva** per **Amministratori** e **Utenti**, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f0727-218">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="f0727-219">Dalla schermata Start, fare clic su **Internet Explorer**, quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="f0727-219">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="f0727-p119">Nella barra degli indirizzi digitare **http:\//app1.corp.contoso.com/**, quindi premere INVIO. Dovrebbe essere possibile visualizzare la pagina Web predefinita di Internet Information Services per APP1.</span><span class="sxs-lookup"><span data-stu-id="f0727-p119">In the Address bar, type http://app1.corp.contoso.com/, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="f0727-222">Dalla barra delle applicazioni del desktop, fare clic sull'icona Esplora File.</span><span class="sxs-lookup"><span data-stu-id="f0727-222">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="f0727-p120">Nella barra degli indirizzi, digitare **\\\\app1\\Files**, quindi premere INVIO. Verrà visualizzata una finestra della cartella con il contenuto della cartella File condivisi.</span><span class="sxs-lookup"><span data-stu-id="f0727-p120">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="f0727-p121">Nella finestra della cartella **File** condivisi, fare doppio clic sul file **Example.txt**. Verrà visualizzato il contenuto del file Example.txt.</span><span class="sxs-lookup"><span data-stu-id="f0727-p121">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="f0727-227">Chiudere **example.txt - Blocco note** e la finestra della cartella **File** condivisi.</span><span class="sxs-lookup"><span data-stu-id="f0727-227">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="f0727-228">Questa è la configurazione finale.</span><span class="sxs-lookup"><span data-stu-id="f0727-228">This is your final configuration.</span></span>
  
![Fase 4 della configurazione base in Azure con la macchina virtuale CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="f0727-230">La configurazione di base di Azure è ora pronta per lo sviluppo e test delle applicazioni o per la creazione di ulteriori ambienti di testing.</span><span class="sxs-lookup"><span data-stu-id="f0727-230">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="f0727-231">Fare clic [qui](http://aka.ms/catlgstack) per consultare una mappa di tutti gli articoli relativi alla guida del laboratorio di testing cloud di One Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f0727-231">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
<span data-ttu-id="f0727-232"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="f0727-232"></span></span>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="f0727-233">Ridurre al minimo i costi delle macchine virtuali nell’ambiente di testing in Azure</span><span class="sxs-lookup"><span data-stu-id="f0727-233">Minimizing the costs of test environment virtual machines in Azure</span></span>

<span data-ttu-id="f0727-234">Per ridurre al minimo i costi dell'esecuzione di macchine virtuali in ambiente di testing, è possibile eseguire una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f0727-234">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="f0727-p122">Creare l'ambiente di testing ed effettuare il test e la dimostrazione necessari al più presto possibile. Al termine, eliminare il gruppo di risorse per l'ambiente di testing.</span><span class="sxs-lookup"><span data-stu-id="f0727-p122">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="f0727-237">Arrestare le macchine virtuali nell’ambiente di testing in uno stato deallocato.</span><span class="sxs-lookup"><span data-stu-id="f0727-237">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="f0727-238">Per arrestare le macchine virtuali con Azure PowerShell, immettere il nome del gruppo di risorse ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="f0727-238">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="f0727-239">Per verificare il corretto funzionamento delle macchine virtuali al loro avvio dallo stato Arrestato (Deallocato), è necessario avviarle nell'ordine seguente:</span><span class="sxs-lookup"><span data-stu-id="f0727-239">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="f0727-240">DC1</span><span class="sxs-lookup"><span data-stu-id="f0727-240">DC1</span></span>
2. <span data-ttu-id="f0727-241">APP1</span><span class="sxs-lookup"><span data-stu-id="f0727-241">APP1</span></span>
3. <span data-ttu-id="f0727-242">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="f0727-242">CLIENT1</span></span>
    
<span data-ttu-id="f0727-243">Per avviare le macchine virtuali con Azure PowerShell, immettere il nome del gruppo di risorse ed eseguire questi comandi.</span><span class="sxs-lookup"><span data-stu-id="f0727-243">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="f0727-244">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f0727-244">See Also</span></span>

- [<span data-ttu-id="f0727-245">Ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="f0727-245">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
- [<span data-ttu-id="f0727-246">DirSync per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="f0727-246">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="f0727-247">Cloud App Security per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="f0727-247">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="f0727-248">Protezione avanzata dalle minacce per l'ambiente di sviluppo/test di Office 365</span><span class="sxs-lookup"><span data-stu-id="f0727-248">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="f0727-249">Adozione del cloud e soluzioni ibride</span><span class="sxs-lookup"><span data-stu-id="f0727-249">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
